# Multisite CSV Importer
- Tags: multisite, csv, import, batch, spreadsheet, csv
- Version: 0.1.0
- Author: Crystal Barton
- Description: -



Import posts from CSV files into WordPress.



## Description

This plugin imports posts from CSV (Comma Separated Value) files into your
WordPress blog. It can prove extremely useful when you want to import a bunch
of posts from an Excel document or the like - simply export your document into
a CSV file and the plugin will take care of the rest.



## Features

- Imports post title, body, excerpt, tags, date, categories etc.
- Supports custom fields, custom taxonomies and comments
- Deals with Word-style quotes and other non-standard characters using
  WordPress' built-in mechanism (same one that normalizes your input when you
  write your posts)
- Columns in the CSV file can be in any order, provided that they have correct
  headings
- Multilanguage support



## Screenshots

1.  Plugin's interface



## Installation

Installing the plugin:

1.  Unzip the plugin's directory into `wp-content/plugins`.
1.  Activate the plugin through the 'Plugins' menu in WordPress.
1.  The plugin will be available under Tools -> CSV Importer on
    WordPress administration page.



## Usage

Click on the CSV Importer link on your WordPress network admin page, choose the
file you would like to import and click Import. The `examples` directory
inside the plugin's directory contains several files that demonstrate
how to use the plugin. The best way to get started is to import one of
these files and look at the results.

CSV is a tabular format that consists of rows and columns. Each row in
a CSV file represents a post, page, or link.


### Posts and Pages

__Required Fields__

These four fields are required for all posts and pages.

- _site_ : The slug of the site.
- _type_ : The type of resource to alter.  Valid types are: "post" or "page".
- _action_ : The action to take on the object.  There are a number fo actions that can be taken.  Further details on each of the actions are detailed under the type section.
  - _add_ : Adds a post or page, but does not check for duplicates before
  creation.
  - _update_ : Updates a post or page, if it exists.
  - _replace_ : Replaces a post or page, if it exists, otherwise it creates the 
  post.
  - _prepend_ : Prepends data to a post or page's excerpt and content.
  - _append_ : Appends data to a post or page's excerpt and content.
  - _delete_ : Deletes a post or page.
  - _grep_ : Updates a portion of a post or page using a regex expression and 
  replacement text.
  _Requires the "subject" column._
  Valid subject values: "title", "excerpt", "content", "slug", "guid"
- _title_ : The title of the post or page.


#### Adding Posts or Pages

- _site_ : The slug of the site.
- _type_ : "post" or "page" or custom post type.
- _action_ : "add"
  - _add_ : Adds a post or page, but does not check for duplicates before
  creation.
- _title_ : The title of the post or page.
- _excerpt_ : The excerpt of the post or page.
- _content_ : The content of the post or page.
- _date_ : The creation post datetime.
- _author_ : The post author's username.
- _slug_ : The post's slug or name.
- _guid_ : The GUID for the post.
- _parent_ : The title or the parent post (default: no parent).
- _status_ : The post's status .  Valid options are:  "publish", "pending", "draft", "future", "private", "trash".
- _menu-order_ : The int value given to determine the posts order in the menu.
- _password_ : Password for post (default: no password).
- _categories_ : One or more categories seperated by a comma. _Posts only._
- _tag_ : One or more tags seperated by a comma. _Posts only._
- _taxonomy-{taxonomy-slug}_ : One or more custom taxonomy names separated by a comma.

#### Updating and Replacing Posts or Pages

- _site_ : The slug of the site.
- _type_ : "post" or "page" or custom post type.
- _action_ : "update" or "replace"
  - _update_ : Updates a post or page, if it exists.
  - _replace_ : Replaces a post or page, if it exists, otherwise it creates the 
  post.
- _title_ : The title of the post or page.
- _excerpt_ : The excerpt of the post or page.
- _content_ : The content of the post or page.
- _date_ : The creation post datetime.
- _author_ : The post author's username.
- _slug_ : The post's slug or name.
- _parent_ : The title or the parent post (default: no parent).
- _status_ : The post's status .  Valid options are:  "publish", "pending", "draft", "future", "private", "trash".
- _menu-order_ : The int value given to determine the posts order in the menu.
- _password_ : Password for post (default: no password).
- _categories_ : One or more categories seperated by a comma. _Posts only._
- _tag_ : One or more tags seperated by a comma. _Posts only._

#### Prepending and Appending to Posts or Pages

- _site_ : The slug of the site.
- _type_ : "post" or "page" or custom post type.
- _action_ : "prepend" or "append"
  - _prepend_ : Prepends data to a post or page's excerpt and content.
  - _append_ : Appends data to a post or page's excerpt and content.
- _title_ : The title of the post or page.
- _excerpt_ : The content to pre- or append to the post excerpt.
- _content_ : The content to pre- or append to the post content.

#### Deleting Posts or Pages

- _site_ : The slug of the site.
- _type_ : "post" or "page" or custom post type.
- _action_ : "delete"
  - _delete_ : Deletes a post or page.
- _title_ : The title of the post or page.

#### GREP Posts or Pages

- _site_ : The slug of the site.
- _type_ : "post" or "page" or custom post type.
- _action_ : "grep"
  - _grep_ : Updates a portion of a post or page using a regex expression and 
  replacement text.
  Valid subject values: title, excerpt, content, slug, guid
- _title_ : The title of the post or page.
- _subject_ : The subject of the search and replace.  Valid options are: "title", "excerpt", "content", "slug", or "guid".
- _regex_ : The regex to match against the subject.
- _replace-text_ : The text to replace the matched portion of the subject.


### Links

__Required Fields__

These four fields are required for all links.

- _site_ : The slug of the site.
- _type_ : The type of resource to alter.  Valid types are: post, page, link
- _action_ : The action to take on the object.  There are a number fo actions that can be taken.  Further details on each of the actions are detailed under the type section.
  - _add_ : Adds a link, but does not check for duplicates before creation.
  - _update_ : Updates a link, if it exists.
  - _replace_ : Replaces a link, if it exists, otherwise it creates the link.
  - _delete_ : Deletes a link.
  - _grep_ : Updates a portion of a link using a regex expression and 
  replacement text.
  Requires the "subject" column.
  Valid subject values: "name", "url", "description"
- _name_ : The name/title of the link.


#### Adding Links

- _site_ : The slug of the site.
- _type_ : "link"
- _action_ : "add"
  - _add_ : Adds a post or page, but does not check for duplicates before
  creation.
- _name_ : The name/title of the link.
- _name_ : The name/title of the link.
- _url_ : The url for the anchor link.
- _description_ : The description for the link.
- _target_ : The target for the anchor.  Valid options are: "_blank", "_top", "_none".
- _categories_ : One or more categories seperated by a comma.


#### Updating and Replacing Links

- _site_ : The slug of the site.
- _type_ : "link"
- _action_ : "update" or "replace"
  - _update_ : Updates a link, if it exists.
  - _replace_ : Replaces a link, if it exists, otherwise it creates the link.
- _name_ : The name/title of the link.
- _url_ : The url for the anchor link.
- _description_ : The description for the link.
- _target_ : The target for the anchor.  Valid options are: "_blank", "_top", "_none".
- _categories_ : One or more categories seperated by a comma.


#### Deleting Links

- _site_ : The slug of the site.
- _type_ : "link"
- _action_ : "delete"
  - _delete_ : Deletes a link.
- _name_ : The name/title of the link.


#### GREP Links

- _site_ : The slug of the site.
- _type_ : "link"
- _action_ : "grep"
  - _grep_ : Updates a portion of a link using a regex expression and 
    replacement text.
- _name_ : The name/title of the link.
- _subject_ : The subject of the search and replace.  Valid options are: "name", "url", "description".
- _regex_ : The regex to match against the subject.
- _replace-text_ : The text to replace the matched portion of the subject.


## Custom taxonomies

__New in version 0.3.0__

Once custom taxonomies are set up in your theme's functions.php file or
by using a 3rd party plugin, `csv_ctax_(taxonomy name)` columns can be 
used to assign imported data to the taxonomies.

__Non-hierarchical taxonomies__

The syntax for non-hierarchical taxonomies is straightforward and is essentially
the same as the `csv_post_tags` syntax.

__Hierarchical taxonomies__

The syntax for hierarchical taxonomies is more complicated. Each hierarchical
taxonomy field is a tiny two-column CSV file, where _the order of columns
matters_. The first column contains the name of the parent term and the second
column contains the name of the child term. Top level terms have to be preceded
either by an empty string or a 0 (zero).

Sample `examples/custom-taxonomies.csv` file included with the plugin
illustrates custom taxonomy support. To see how it works, make sure to set up
custom taxonomies from `functions.inc.php`.

Make sure that the quotation marks used as text delimiters in `csv_ctax_`
columns are regular ASCII double quotes, not typographical quotes like “
(U+201C) and ” (U+201D).



## Comments

__New in version 0.3.1__

An example file with comments is included in the `examples` directory.
In short, comments can be imported along with posts by specifying columns
such as `csv_comment_*_author`, `csv_comment_*_content` etc, where * is
a comment ID number. This ID doesn't go into WordPress. It is only there
to have the connection information in the CSV file.



## Frequently Asked Questions


_I have quotation marks and commas as values in my CSV file. How do I tell CSV
Importer to use a different separator?_

It doesn't really matter what kind of separator you use if your file is
properly escaped. To see what I mean by proper escaping, take a look at
`examples/sample.csv` file which has cells with quotation marks and commas.

If the software you use for exporting to CSV is unable to escape quotation
marks and commas, you might want to give [OpenOffice Calc][calc] a try.

[calc]: http://www.openoffice.org/

-

_How can I import characters with diacritics, Cyrillic or Han characters?_

`Make sure to save your CSV file with utf-8 encoding.`

Prior to version 6.0.4, MySQL [did not support][5] some rare Han characters.
As a workaround, you can insert characters such as &#x2028e; (U+2028E) by
converting them to HTML entities - &amp;\#x2028e;

[5]: http://dev.mysql.com/doc/refman/5.1/en/faqs-cjk.html#qandaitem-24-11-1-13

-

_I cannot import anything - the plugin displays "Imported 0 posts in 0.01
seconds."_

Update to version 0.3.1 or greater. Previous versions required write access to
the /tmp directory and the plugin failed if access was denied by PHP's safe
mode or other settings.

-

_I'm importing a file, but not all rows in it are imported and I don't see
a confirmation message. Why?_

WordPress can be many things, but one thing it's not is blazing fast. The
reason why not all rows are imported and there's no confirmation message is
that the plugin times out during execution - PHP decides that it has been
running too long and terminates it.

There are a number of solutions you can try. First, make sure that you're not
using any plugins that may slow down post insertion. For example, a Twitter
plugin might attempt to tweet every post you import - not a very good idea
if you have 200 posts. Second, you can break up a file into smaller chunks 
that take less time to import and therefore will not cause the plugin to time 
out. Third, you can try adjusting PHP's `max_execution_time` option that sets 
how long scripts are allowed to run. Description of how to do it is beyond the
scope of this FAQ - you should search the web and/or use your web host's help
to find out how. However, putting the following line in `.htaccess` file
inside public_html directory works for some people:

`Sets max execution time to 2 minutes. Adjust as necessary.
 php_value max_execution_time 120`

The problem can be approached from another angle, namely instead of giving
scripts more time to run making them run faster. There's not much I can do to
speed up the plugin (you can contact me at dvkobozev at gmail.com if you like
to prove me wrong), so you can try to speed up WordPress. It is a pretty broad
topic, ranging from database optimizations to PHP accelerators such as APC,
eAccelerator or XCache, so I'm afraid you're on your own here.

-

_I receive the following error when I try to import my CSV file: "Invalid CSV
file: header length and/or row lengths do not match". What's wrong with your
plugin/my file?_

Short answer: update to version 0.2.0 or later. Longer answer: the number of
fields (values) in rows in your file does not match the number of columns.
Version 0.2.0 pads such rows with empty values (if there are more columns than
cells in a row) or discards extra fields (if there are less columns than cells
in a row).

-

_I'm getting the following error: `Parse error: syntax error, unexpected
T_STRING, expecting T_OLD_FUNCTION or T_FUNCTION or T_VAR or '}' in .../public_html/wp-content/plugins/csv-importer/File_CSV_DataSource/DataSource.php
on line 61`. What gives?_

This plugin requires PHP5, while you probably have PHP4 or older. Update your
PHP installation or ask your hosting provider to do it for you.



## Credits

This plugin uses [php-csv-parser][3] by Kazuyoshi Tlacaelel.
It was inspired by JayBlogger's [CSV Import][4] plugin.

Contributors:

- Kevin Hagerty (post_author support)
- Edir Pedro (root category option and tableless HTML markup)
- Frank Loeffler (comments support)
- Micah Gates (subcategory syntax)
- David Hollander (deprecation warnings, linebreak handling)

[3]: http://code.google.com/p/php-csv-parser/
[4]: http://www.jayblogger.com/the-birth-of-my-first-plugin-import-csv/



## Changelog

- __0.3.7__
  - Make hierarchical custom taxonomy line splitting more robust
  - Fix deprecation warnings
- __0.3.6__
  - Fix category cleanup bug
- __0.3.5__
  - Added 'greater-than' category syntax
  - Updated the docs
- __0.3.4__
  - Added csv_post_parent column
  - Updated the docs
  - Got rid of a deprecation warning
- __0.3.3__
  - Fixes incompatibility with versions of WordPress prior to 3.0 introduced
    in previous release.
- __0.3.2__
  - Added ability to specify custom post type.
- __0.3.1__
  - Import comments.
  - Updated php-csv-parser - the plugin should no longer create files in /tmp.
- __0.3.0__
  - Custom taxonomies.
- __0.2.4__
  - Root category selection, cleaner HTML.
- __0.2.3__
  - Slight speed increase, support for post_author and post_name.
- __0.2.2__
  - Bugfix release to deal with BOM that may occur in UTF-8 encoded files.
- __0.2.1__
  - Ability to import rows as pages, not posts.
  - Starting with this version, you can also specify category ids instead of
    names.
- __0.2.0__
  - Ability to handle CSV files where the number of cells in rows does not
    match the number of columns
  - Smart date parsing
  - Code cleanup.
- __0.1.3__
  - New option to import posts with published status.
- __0.1.2__
  - Added support for post excerpts.
- __0.1.1__
  - Code cleanup
  - Changed column names for CSV input. Sorry if it breaks anything for you,
    folks, but it had to be done in order to allow for custom fields such as
    `title` ([All in One SEO Pack][1] uses those, for example).
- __v0.1.0__
  - Initial version of the plugin

[1]: http://wordpress.org/extend/plugins/all-in-one-seo-pack/



## Upgrade Notice

- __0.3.7__
  - More robust handling of hierarchical custom taxonomies; removed deprecation
    warnings.
- __0.3.6__
  - Fix for 'Invalid argument supplied for foreach() on line 268' error message
- __0.3.5__
  - Subcategory creation support. Documentation update.
- __0.3.4__
  - Post parent support. Documentation update.
- __0.3.3__
  - Fixes "Call to undefined function post_type_exists()" error for versions of
    Wordpress prior to 3.0
- __0.3.2__
  - Adds support for custom post types. Option to import pages has been removed 
    from the interface. To import a page, add csv_post_type column to your csv 
    file and set it to "page".
- __0.3.1__
  - Adds support for comments
- __0.3.0__
  - Adds support for custom taxonomies




