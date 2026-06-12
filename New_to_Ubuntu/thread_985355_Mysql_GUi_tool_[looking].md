---
title: "Mysql GUi tool [looking]"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by mlotfi on 2008-11-17
Hi,
is there any Mysql GUI tool that come packaged with ubuntu ? what is the best one we can download and install.

thanks

---

### Post by jenkinbr on 2008-11-17
that would depend on what you mean by GUI

I use phpmyadmin, but this will require a webserver and the php5 packages to be installed.

You can also use mysql-admin, mysql-query-browser, and/or mysql-navigator

Install any of them using sudo apt-get install <package list>

replacing <package list> with the package(s) you want to install.

---

### Post by Titan8990 on 2008-11-17
+1 for phpmyadmin, especially if you already have php and apache installed.

---

### Post by mlotfi on 2008-11-17
Thank you,

I just did sudo apt-get install phpmyadmin ,

it said it is installed, BUT where is it ? how can I start it ?
thanks

---

### Post by jenkinbr on 2008-11-17
Browse to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) << this link should work for you directly from this site.

---

### Post by mlotfi on 2008-11-17
I did  [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

but I got NOT FOUND.

I went to /var/www/ there is nothing that says phpmyadmin

---

### Post by jenkinbr on 2008-11-17
Hmmm, 
It wouldn't be in /var/www/ because it creates it's own location at (I beleave) /usr/share/phpmyadmin or something like that.

Do you have apache2 installed? (I'm assuming yes) and if you do, did you have phpmyadmin automatically reconfigure it?

---

### Post by mlotfi on 2008-11-17
Hi and thank you,

Yes I have apache2 installed, I just tested php and it's working.

but I did not understan what do you mean by :
phpmyadmin automatically reconfigure it?


Thanks again

---

### Post by mallegonian on 2008-11-17
I think it installs to /var/www/pma/ , so [http://localhost/pma/](http://localhost/pma/) , not /phpmyadmin/ .

---

### Post by jenkinbr on 2008-11-17
Mine is set up with a folder alias of localhost/phpmyadmin/  and I did nothing to get it like that.  Not sure why it would be different unless apache2 was not autoconfigured...

---

### Post by mlotfi on 2008-11-17
No there is no pma in www,

I did search in folders for phpmyadmin it's in /etc/

---

### Post by Coreigh on 2008-11-17
I SHOULD HAVE POINTED OUT ... I am on 7.10 not 8.10. Sorry for the differences.

You should have /etc/apache2/conf.d/phpmyadmin.conf that defines how/where apache will serve phpmyadmin. By default this also indicates if apache is installed.

try simply [http://localhost/](http://localhost/)

That should show a page that says "It works!"

If that does not work but you do have the files I mentioned above then perhaps apache is not running:
```
sudo /etc/init.d/apache2 start
```
That will either start it or show you an error (also found at /var/log/apache2/error.log)

Finally [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) is the default path

---

### Post by mallegonian on 2008-11-17
I just installed it to check after I posted, let it configure itself for apache2, and it ended up in /var/www/pma/ . *shrug*
8.10, right?

---

### Post by jenkinbr on 2008-11-17
Maybe 8.10 is different - I'll have to check when I go home, but that machine is offline...

just checked the package contents at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and this is what the file listing is:
```
/etc/phpmyadmin/apache.conf
/etc/phpmyadmin/config.footer.inc.php
/etc/phpmyadmin/config.header.inc.php
/etc/phpmyadmin/config.inc.php
/etc/phpmyadmin/lighttpd.conf
/usr/share/doc/phpmyadmin/Documentation.html
/usr/share/doc/phpmyadmin/Documentation.txt.gz
/usr/share/doc/phpmyadmin/README.Debian
/usr/share/doc/phpmyadmin/TODO.Debian
/usr/share/doc/phpmyadmin/changelog.Debian.gz
/usr/share/doc/phpmyadmin/changelog.gz
/usr/share/doc/phpmyadmin/copyright
/usr/share/doc/phpmyadmin/docs.css
/usr/share/doc/phpmyadmin/examples/config.manyhosts.inc.php
/usr/share/doc/phpmyadmin/examples/config.sample.inc.php
/usr/share/doc/phpmyadmin/examples/create_tables.sql.gz
/usr/share/doc/phpmyadmin/examples/create_tables_mysql_4_1_2+.sql.gz
/usr/share/doc/phpmyadmin/examples/signon.php
/usr/share/doc/phpmyadmin/examples/upgrade_tables_mysql_4_1_2+.sql.gz
/usr/share/doc/phpmyadmin/translators.html
/usr/share/phpmyadmin/Documentation.html
/usr/share/phpmyadmin/browse_foreigners.php
/usr/share/phpmyadmin/calendar.php
/usr/share/phpmyadmin/changelog.php
/usr/share/phpmyadmin/chk_rel.php
/usr/share/phpmyadmin/config.footer.inc.php
/usr/share/phpmyadmin/config.header.inc.php
/usr/share/phpmyadmin/config.inc.php
/usr/share/phpmyadmin/config.sample.inc.php
/usr/share/phpmyadmin/db_create.php
/usr/share/phpmyadmin/db_datadict.php
/usr/share/phpmyadmin/db_export.php
/usr/share/phpmyadmin/db_import.php
/usr/share/phpmyadmin/db_operations.php
/usr/share/phpmyadmin/db_printview.php
/usr/share/phpmyadmin/db_qbe.php
/usr/share/phpmyadmin/db_search.php
/usr/share/phpmyadmin/db_sql.php
/usr/share/phpmyadmin/db_structure.php
/usr/share/phpmyadmin/docs.css
/usr/share/phpmyadmin/error.php
/usr/share/phpmyadmin/export.php
/usr/share/phpmyadmin/favicon.ico
/usr/share/phpmyadmin/import.php
/usr/share/phpmyadmin/index.php
/usr/share/phpmyadmin/js/dom-drag.js
/usr/share/phpmyadmin/js/functions.js
/usr/share/phpmyadmin/js/indexes.js
/usr/share/phpmyadmin/js/keyhandler.js
/usr/share/phpmyadmin/js/navigation.js
/usr/share/phpmyadmin/js/querywindow.js
/usr/share/phpmyadmin/js/server_privileges.js
/usr/share/phpmyadmin/js/tbl_change.js
/usr/share/phpmyadmin/js/tooltip.js
/usr/share/phpmyadmin/js/user_password.js
/usr/share/phpmyadmin/lang/add_message.sh
/usr/share/phpmyadmin/lang/add_message_file.sh
/usr/share/phpmyadmin/lang/afrikaans-utf-8.inc.php
/usr/share/phpmyadmin/lang/albanian-utf-8.inc.php
/usr/share/phpmyadmin/lang/arabic-utf-8.inc.php
/usr/share/phpmyadmin/lang/azerbaijani-utf-8.inc.php
/usr/share/phpmyadmin/lang/basque-utf-8.inc.php
/usr/share/phpmyadmin/lang/belarusian_cyrillic-utf-8.inc.php
/usr/share/phpmyadmin/lang/belarusian_latin-utf-8.inc.php
/usr/share/phpmyadmin/lang/bosnian-utf-8.inc.php
/usr/share/phpmyadmin/lang/brazilian_portuguese-utf-8.inc.php
/usr/share/phpmyadmin/lang/bulgarian-utf-8.inc.php
/usr/share/phpmyadmin/lang/catalan-utf-8.inc.php
/usr/share/phpmyadmin/lang/check_lang.sh
/usr/share/phpmyadmin/lang/chinese_simplified-utf-8.inc.php
/usr/share/phpmyadmin/lang/chinese_traditional-utf-8.inc.php
/usr/share/phpmyadmin/lang/croatian-utf-8.inc.php
/usr/share/phpmyadmin/lang/czech-utf-8.inc.php
/usr/share/phpmyadmin/lang/danish-utf-8.inc.php
/usr/share/phpmyadmin/lang/dutch-utf-8.inc.php
/usr/share/phpmyadmin/lang/english-utf-8.inc.php
/usr/share/phpmyadmin/lang/estonian-utf-8.inc.php
/usr/share/phpmyadmin/lang/finnish-utf-8.inc.php
/usr/share/phpmyadmin/lang/french-utf-8.inc.php
/usr/share/phpmyadmin/lang/galician-utf-8.inc.php
/usr/share/phpmyadmin/lang/georgian-utf-8.inc.php
/usr/share/phpmyadmin/lang/german-utf-8.inc.php
/usr/share/phpmyadmin/lang/greek-utf-8.inc.php
/usr/share/phpmyadmin/lang/hebrew-utf-8.inc.php
/usr/share/phpmyadmin/lang/hindi-utf-8.inc.php
/usr/share/phpmyadmin/lang/hungarian-utf-8.inc.php
/usr/share/phpmyadmin/lang/indonesian-utf-8.inc.php
/usr/share/phpmyadmin/lang/italian-utf-8.inc.php
/usr/share/phpmyadmin/lang/japanese-utf-8.inc.php
/usr/share/phpmyadmin/lang/korean-utf-8.inc.php
/usr/share/phpmyadmin/lang/latvian-utf-8.inc.php
/usr/share/phpmyadmin/lang/lithuanian-utf-8.inc.php
/usr/share/phpmyadmin/lang/macedonian_cyrillic-utf-8.inc.php
/usr/share/phpmyadmin/lang/malay-utf-8.inc.php
/usr/share/phpmyadmin/lang/mongolian-utf-8.inc.php
/usr/share/phpmyadmin/lang/norwegian-utf-8.inc.php
/usr/share/phpmyadmin/lang/persian-utf-8.inc.php
/usr/share/phpmyadmin/lang/polish-utf-8.inc.php
/usr/share/phpmyadmin/lang/portuguese-utf-8.inc.php
/usr/share/phpmyadmin/lang/remove_message.sh
/usr/share/phpmyadmin/lang/romanian-utf-8.inc.php
/usr/share/phpmyadmin/lang/russian-utf-8.inc.php
/usr/share/phpmyadmin/lang/serbian_cyrillic-utf-8.inc.php
/usr/share/phpmyadmin/lang/serbian_latin-utf-8.inc.php
/usr/share/phpmyadmin/lang/sinhala-utf-8.inc.php
/usr/share/phpmyadmin/lang/slovak-utf-8.inc.php
/usr/share/phpmyadmin/lang/slovenian-utf-8.inc.php
/usr/share/phpmyadmin/lang/sort_lang.sh
/usr/share/phpmyadmin/lang/spanish-utf-8.inc.php
/usr/share/phpmyadmin/lang/swedish-utf-8.inc.php
/usr/share/phpmyadmin/lang/sync_lang.sh
/usr/share/phpmyadmin/lang/tatarish-utf-8.inc.php
/usr/share/phpmyadmin/lang/thai-utf-8.inc.php
/usr/share/phpmyadmin/lang/translatecount.sh
/usr/share/phpmyadmin/lang/turkish-utf-8.inc.php
/usr/share/phpmyadmin/lang/ukrainian-utf-8.inc.php
/usr/share/phpmyadmin/libraries/.htaccess
/usr/share/phpmyadmin/libraries/Config.class.php
/usr/share/phpmyadmin/libraries/File.class.php
/usr/share/phpmyadmin/libraries/List.class.php
/usr/share/phpmyadmin/libraries/List_Database.class.php
/usr/share/phpmyadmin/libraries/StorageEngine.class.php
/usr/share/phpmyadmin/libraries/Table.class.php
/usr/share/phpmyadmin/libraries/Theme.class.php
/usr/share/phpmyadmin/libraries/Theme_Manager.class.php
/usr/share/phpmyadmin/libraries/auth/config.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/cookie.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/http.auth.lib.php
/usr/share/phpmyadmin/libraries/auth/signon.auth.lib.php
/usr/share/phpmyadmin/libraries/blowfish.php
/usr/share/phpmyadmin/libraries/bookmark.lib.php
/usr/share/phpmyadmin/libraries/charset_conversion.lib.php
/usr/share/phpmyadmin/libraries/check_user_privileges.lib.php
/usr/share/phpmyadmin/libraries/cleanup.lib.php
/usr/share/phpmyadmin/libraries/common.inc.php
/usr/share/phpmyadmin/libraries/common.lib.php
/usr/share/phpmyadmin/libraries/config.default.php
/usr/share/phpmyadmin/libraries/core.lib.php
/usr/share/phpmyadmin/libraries/database_interface.lib.php
/usr/share/phpmyadmin/libraries/db_common.inc.php
/usr/share/phpmyadmin/libraries/db_info.inc.php
/usr/share/phpmyadmin/libraries/db_links.inc.php
/usr/share/phpmyadmin/libraries/db_routines.inc.php
/usr/share/phpmyadmin/libraries/db_table_exists.lib.php
/usr/share/phpmyadmin/libraries/dbg/setup.php
/usr/share/phpmyadmin/libraries/dbi/mysql.dbi.lib.php
/usr/share/phpmyadmin/libraries/dbi/mysqli.dbi.lib.php
/usr/share/phpmyadmin/libraries/display_change_password.lib.php
/usr/share/phpmyadmin/libraries/display_create_database.lib.php
/usr/share/phpmyadmin/libraries/display_create_table.lib.php
/usr/share/phpmyadmin/libraries/display_export.lib.php
/usr/share/phpmyadmin/libraries/display_import.lib.php
/usr/share/phpmyadmin/libraries/display_select_lang.lib.php
/usr/share/phpmyadmin/libraries/display_tbl.lib.php
/usr/share/phpmyadmin/libraries/display_tbl_links.lib.php
/usr/share/phpmyadmin/libraries/engines/bdb.lib.php
/usr/share/phpmyadmin/libraries/engines/berkeleydb.lib.php
/usr/share/phpmyadmin/libraries/engines/binlog.lib.php
/usr/share/phpmyadmin/libraries/engines/innobase.lib.php
/usr/share/phpmyadmin/libraries/engines/innodb.lib.php
/usr/share/phpmyadmin/libraries/engines/memory.lib.php
/usr/share/phpmyadmin/libraries/engines/merge.lib.php
/usr/share/phpmyadmin/libraries/engines/mrg_myisam.lib.php
/usr/share/phpmyadmin/libraries/engines/myisam.lib.php
/usr/share/phpmyadmin/libraries/engines/ndbcluster.lib.php
/usr/share/phpmyadmin/libraries/export/csv.php
/usr/share/phpmyadmin/libraries/export/excel.php
/usr/share/phpmyadmin/libraries/export/htmlexcel.php
/usr/share/phpmyadmin/libraries/export/htmlword.php
/usr/share/phpmyadmin/libraries/export/latex.php
/usr/share/phpmyadmin/libraries/export/ods.php
/usr/share/phpmyadmin/libraries/export/odt.php
/usr/share/phpmyadmin/libraries/export/pdf.php
/usr/share/phpmyadmin/libraries/export/sql.php
/usr/share/phpmyadmin/libraries/export/xls.php
/usr/share/phpmyadmin/libraries/export/xml.php
/usr/share/phpmyadmin/libraries/export/yaml.php
/usr/share/phpmyadmin/libraries/file_listing.php
/usr/share/phpmyadmin/libraries/footer.inc.php
/usr/share/phpmyadmin/libraries/get_foreign.lib.php
/usr/share/phpmyadmin/libraries/grab_globals.lib.php
/usr/share/phpmyadmin/libraries/header.inc.php
/usr/share/phpmyadmin/libraries/header_http.inc.php
/usr/share/phpmyadmin/libraries/header_meta_style.inc.php
/usr/share/phpmyadmin/libraries/header_printview.inc.php
/usr/share/phpmyadmin/libraries/iconv_wrapper.lib.php
/usr/share/phpmyadmin/libraries/import.lib.php
/usr/share/phpmyadmin/libraries/import/README
/usr/share/phpmyadmin/libraries/import/csv.php
/usr/share/phpmyadmin/libraries/import/docsql.php
/usr/share/phpmyadmin/libraries/import/ldi.php
/usr/share/phpmyadmin/libraries/import/sql.php
/usr/share/phpmyadmin/libraries/information_schema_relations.lib.php
/usr/share/phpmyadmin/libraries/ip_allow_deny.lib.php
/usr/share/phpmyadmin/libraries/js_escape.lib.php
/usr/share/phpmyadmin/libraries/kanji-encoding.lib.php
/usr/share/phpmyadmin/libraries/language.lib.php
/usr/share/phpmyadmin/libraries/mcrypt.lib.php
/usr/share/phpmyadmin/libraries/mult_submits.inc.php
/usr/share/phpmyadmin/libraries/mysql_charsets.lib.php
/usr/share/phpmyadmin/libraries/navigation_header.inc.php
/usr/share/phpmyadmin/libraries/ob.lib.php
/usr/share/phpmyadmin/libraries/opendocument.lib.php
/usr/share/phpmyadmin/libraries/parse_analyze.lib.php
/usr/share/phpmyadmin/libraries/plugin_interface.lib.php
/usr/share/phpmyadmin/libraries/relation.lib.php
/usr/share/phpmyadmin/libraries/relation_cleanup.lib.php
/usr/share/phpmyadmin/libraries/sanitizing.lib.php
/usr/share/phpmyadmin/libraries/select_lang.lib.php
/usr/share/phpmyadmin/libraries/select_server.lib.php
/usr/share/phpmyadmin/libraries/server_common.inc.php
/usr/share/phpmyadmin/libraries/server_links.inc.php
/usr/share/phpmyadmin/libraries/session.inc.php
/usr/share/phpmyadmin/libraries/sql_query_form.lib.php
/usr/share/phpmyadmin/libraries/sqlparser.data.php
/usr/share/phpmyadmin/libraries/sqlparser.lib.php
/usr/share/phpmyadmin/libraries/sqlvalidator.class.php
/usr/share/phpmyadmin/libraries/sqlvalidator.lib.php
/usr/share/phpmyadmin/libraries/string.lib.php
/usr/share/phpmyadmin/libraries/string_mb.lib.php
/usr/share/phpmyadmin/libraries/string_native.lib.php
/usr/share/phpmyadmin/libraries/string_type_ctype.lib.php
/usr/share/phpmyadmin/libraries/string_type_native.lib.php
/usr/share/phpmyadmin/libraries/tbl_common.php
/usr/share/phpmyadmin/libraries/tbl_indexes.lib.php
/usr/share/phpmyadmin/libraries/tbl_info.inc.php
/usr/share/phpmyadmin/libraries/tbl_links.inc.php
/usr/share/phpmyadmin/libraries/tbl_properties.inc.php
/usr/share/phpmyadmin/libraries/tbl_replace_fields.inc.php
/usr/share/phpmyadmin/libraries/tbl_triggers.lib.php
/usr/share/phpmyadmin/libraries/tcpdf/CHANGELOG
/usr/share/phpmyadmin/libraries/tcpdf/README
/usr/share/phpmyadmin/libraries/tcpdf/font/README
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans-bold.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans-bold.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans-bold.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavusans.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif-bold.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif-bold.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif-bold.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif.ctg.z
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif.php
/usr/share/phpmyadmin/libraries/tcpdf/font/dejavuserif.z
/usr/share/phpmyadmin/libraries/tcpdf/html_entity_decode_php4.php
/usr/share/phpmyadmin/libraries/tcpdf/tcpdf.php
/usr/share/phpmyadmin/libraries/transformations.lib.php
/usr/share/phpmyadmin/libraries/transformations/README
/usr/share/phpmyadmin/libraries/transformations/TEMPLATE
/usr/share/phpmyadmin/libraries/transformations/TEMPLATE_MIMETYPE
/usr/share/phpmyadmin/libraries/transformations/application_octetstream__download.inc.php
/usr/share/phpmyadmin/libraries/transformations/application_octetstream__hex.inc.php
/usr/share/phpmyadmin/libraries/transformations/generator.sh
/usr/share/phpmyadmin/libraries/transformations/global.inc.php
/usr/share/phpmyadmin/libraries/transformations/image_jpeg__inline.inc.php
/usr/share/phpmyadmin/libraries/transformations/image_jpeg__link.inc.php
/usr/share/phpmyadmin/libraries/transformations/image_png__inline.inc.php
/usr/share/phpmyadmin/libraries/transformations/template_generator.sh
/usr/share/phpmyadmin/libraries/transformations/template_generator_mimetype.sh
/usr/share/phpmyadmin/libraries/transformations/text_plain__dateformat.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__external.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__formatted.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__imagelink.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__link.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__sql.inc.php
/usr/share/phpmyadmin/libraries/transformations/text_plain__substr.inc.php
/usr/share/phpmyadmin/libraries/unzip.lib.php
/usr/share/phpmyadmin/libraries/url_generating.lib.php
/usr/share/phpmyadmin/libraries/zip.lib.php
/usr/share/phpmyadmin/license.php
/usr/share/phpmyadmin/main.php
/usr/share/phpmyadmin/navigation.php
/usr/share/phpmyadmin/pdf_pages.php
/usr/share/phpmyadmin/pdf_schema.php
/usr/share/phpmyadmin/phpinfo.php
/usr/share/phpmyadmin/phpmyadmin.css.php
/usr/share/phpmyadmin/pmd/images/2leftarrow.png
/usr/share/phpmyadmin/pmd/images/2leftarrow_m.png
/usr/share/phpmyadmin/pmd/images/2rightarrow.png
/usr/share/phpmyadmin/pmd/images/2rightarrow_m.png
/usr/share/phpmyadmin/pmd/images/ang_direct.png
/usr/share/phpmyadmin/pmd/images/bord.png
/usr/share/phpmyadmin/pmd/images/bottom.png
/usr/share/phpmyadmin/pmd/images/def.png
/usr/share/phpmyadmin/pmd/images/display_field.png
/usr/share/phpmyadmin/pmd/images/downarrow1.png
/usr/share/phpmyadmin/pmd/images/downarrow2.png
/usr/share/phpmyadmin/pmd/images/downarrow2_m.png
/usr/share/phpmyadmin/pmd/images/exec.png
/usr/share/phpmyadmin/pmd/images/exec_small.png
/usr/share/phpmyadmin/pmd/images/favicon.ico
/usr/share/phpmyadmin/pmd/images/grid.png
/usr/share/phpmyadmin/pmd/images/help.png
/usr/share/phpmyadmin/pmd/images/help_relation.png
/usr/share/phpmyadmin/pmd/images/pdf.png
/usr/share/phpmyadmin/pmd/images/relation.png
/usr/share/phpmyadmin/pmd/images/reload.png
/usr/share/phpmyadmin/pmd/images/resize.png
/usr/share/phpmyadmin/pmd/images/rightarrow1.png
/usr/share/phpmyadmin/pmd/images/rightarrow2.png
/usr/share/phpmyadmin/pmd/images/save.png
/usr/share/phpmyadmin/pmd/images/table.png
/usr/share/phpmyadmin/pmd/images/uparrow2_m.png
/usr/share/phpmyadmin/pmd/scripts/ajax.js
/usr/share/phpmyadmin/pmd/scripts/iecanvas.js
/usr/share/phpmyadmin/pmd/scripts/move.js
/usr/share/phpmyadmin/pmd/styles/default/images/1.png
/usr/share/phpmyadmin/pmd/styles/default/images/2.png
/usr/share/phpmyadmin/pmd/styles/default/images/3.png
/usr/share/phpmyadmin/pmd/styles/default/images/4.png
/usr/share/phpmyadmin/pmd/styles/default/images/5.png
/usr/share/phpmyadmin/pmd/styles/default/images/6.png
/usr/share/phpmyadmin/pmd/styles/default/images/7.png
/usr/share/phpmyadmin/pmd/styles/default/images/8.png
/usr/share/phpmyadmin/pmd/styles/default/images/FieldKey_small.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small_char.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small_date.png
/usr/share/phpmyadmin/pmd/styles/default/images/Field_small_int.png
/usr/share/phpmyadmin/pmd/styles/default/images/Header.png
/usr/share/phpmyadmin/pmd/styles/default/images/Header_Linked.png
/usr/share/phpmyadmin/pmd/styles/default/images/left_panel_butt.png
/usr/share/phpmyadmin/pmd/styles/default/images/left_panel_tab.png
/usr/share/phpmyadmin/pmd/styles/default/images/small_tab.png
/usr/share/phpmyadmin/pmd/styles/default/images/top_panel.png
/usr/share/phpmyadmin/pmd/styles/default/style1.css
/usr/share/phpmyadmin/pmd_common.php
/usr/share/phpmyadmin/pmd_display_field.php
/usr/share/phpmyadmin/pmd_general.php
/usr/share/phpmyadmin/pmd_help.php
/usr/share/phpmyadmin/pmd_pdf.php
/usr/share/phpmyadmin/pmd_relation_new.php
/usr/share/phpmyadmin/pmd_relation_upd.php
/usr/share/phpmyadmin/pmd_save_pos.php
/usr/share/phpmyadmin/print.css
/usr/share/phpmyadmin/querywindow.php
/usr/share/phpmyadmin/readme.php
/usr/share/phpmyadmin/scripts/setup.php
/usr/share/phpmyadmin/server_binlog.php
/usr/share/phpmyadmin/server_collations.php
/usr/share/phpmyadmin/server_databases.php
/usr/share/phpmyadmin/server_engines.php
/usr/share/phpmyadmin/server_export.php
/usr/share/phpmyadmin/server_import.php
/usr/share/phpmyadmin/server_privileges.php
/usr/share/phpmyadmin/server_processlist.php
/usr/share/phpmyadmin/server_sql.php
/usr/share/phpmyadmin/server_status.php
/usr/share/phpmyadmin/server_variables.php
/usr/share/phpmyadmin/show_config_errors.php
/usr/share/phpmyadmin/sql.php
/usr/share/phpmyadmin/tbl_addfield.php
/usr/share/phpmyadmin/tbl_alter.php
/usr/share/phpmyadmin/tbl_change.php
/usr/share/phpmyadmin/tbl_create.php
/usr/share/phpmyadmin/tbl_export.php
/usr/share/phpmyadmin/tbl_import.php
/usr/share/phpmyadmin/tbl_indexes.php
/usr/share/phpmyadmin/tbl_move_copy.php
/usr/share/phpmyadmin/tbl_operations.php
/usr/share/phpmyadmin/tbl_printview.php
/usr/share/phpmyadmin/tbl_relation.php
/usr/share/phpmyadmin/tbl_replace.php
/usr/share/phpmyadmin/tbl_row_action.php
/usr/share/phpmyadmin/tbl_select.php
/usr/share/phpmyadmin/tbl_sql.php
/usr/share/phpmyadmin/tbl_structure.php
/usr/share/phpmyadmin/themes.php
/usr/share/phpmyadmin/themes/darkblue_orange/css/theme_right.css.php
/usr/share/phpmyadmin/themes/darkblue_orange/img/arrow_ltr.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/arrow_rtl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/asc_order.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_bookmark.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_browse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_calendar.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_comment.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_dbstatistics.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_deltbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_docs.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_docsql.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_drop.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_edit.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_empty.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_engine.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_export.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_firstpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_ftext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_help.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_home.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_import.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_index.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_info.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_insrow.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_lastpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_minus.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_newdb.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_newtbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_nextpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_pdfdoc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_plus.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_prevpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_primary.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_print.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_props.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_relations.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_save.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sbrowse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sdb.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_search.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_selboard.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_select.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sql.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sqldoc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_sqlhelp.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblanalyse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblexport.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblimport.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tblops.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tbloptimize.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_tipp.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_unique.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usradd.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usrcheck.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usrdrop.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usredit.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_usrlist.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_view.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/b_views.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_browse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_deltbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_drop.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_empty.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_firstpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_ftext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_index.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_insrow.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_lastpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_nextpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_prevpage.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_primary.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_sbrowse.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_select.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/bd_unique.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/error.ico
/usr/share/phpmyadmin/themes/darkblue_orange/img/item.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/item_ltr.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/item_rtl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/logo_left.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/logo_right.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/php_sym.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/pma_logo2.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_asc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_asci.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_attention.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_cancel.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_cancel2.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_db.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_desc.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_error.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_error2.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_fulltext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_host.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_info.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_lang.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_loggoff.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_notice.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_okay.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_partialtext.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_passwd.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_process.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_really.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_reload.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_rights.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_status.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_tbl.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_theme.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_vars.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_views.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/s_warn.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/spacer.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/tbl_header.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/tbl_th.png
/usr/share/phpmyadmin/themes/darkblue_orange/img/window-new.png
/usr/share/phpmyadmin/themes/darkblue_orange/info.inc.php
/usr/share/phpmyadmin/themes/darkblue_orange/layout.inc.php
/usr/share/phpmyadmin/themes/darkblue_orange/screen.png
/usr/share/phpmyadmin/themes/original/css/theme_left.css.php
/usr/share/phpmyadmin/themes/original/css/theme_print.css.php
/usr/share/phpmyadmin/themes/original/css/theme_right.css.php
/usr/share/phpmyadmin/themes/original/img/arrow_ltr.png
/usr/share/phpmyadmin/themes/original/img/arrow_rtl.png
/usr/share/phpmyadmin/themes/original/img/asc_order.png
/usr/share/phpmyadmin/themes/original/img/b_bookmark.png
/usr/share/phpmyadmin/themes/original/img/b_browse.png
/usr/share/phpmyadmin/themes/original/img/b_calendar.png
/usr/share/phpmyadmin/themes/original/img/b_comment.png
/usr/share/phpmyadmin/themes/original/img/b_dbstatistics.png
/usr/share/phpmyadmin/themes/original/img/b_deltbl.png
/usr/share/phpmyadmin/themes/original/img/b_docs.png
/usr/share/phpmyadmin/themes/original/img/b_docsql.png
/usr/share/phpmyadmin/themes/original/img/b_drop.png
/usr/share/phpmyadmin/themes/original/img/b_edit.png
/usr/share/phpmyadmin/themes/original/img/b_empty.png
/usr/share/phpmyadmin/themes/original/img/b_engine.png
/usr/share/phpmyadmin/themes/original/img/b_export.png
/usr/share/phpmyadmin/themes/original/img/b_firstpage.png
/usr/share/phpmyadmin/themes/original/img/b_ftext.png
/usr/share/phpmyadmin/themes/original/img/b_help.png
/usr/share/phpmyadmin/themes/original/img/b_home.png
/usr/share/phpmyadmin/themes/original/img/b_import.png
/usr/share/phpmyadmin/themes/original/img/b_index.png
/usr/share/phpmyadmin/themes/original/img/b_info.png
/usr/share/phpmyadmin/themes/original/img/b_insrow.png
/usr/share/phpmyadmin/themes/original/img/b_lastpage.png
/usr/share/phpmyadmin/themes/original/img/b_minus.png
/usr/share/phpmyadmin/themes/original/img/b_newdb.png
/usr/share/phpmyadmin/themes/original/img/b_newtbl.png
/usr/share/phpmyadmin/themes/original/img/b_nextpage.png
/usr/share/phpmyadmin/themes/original/img/b_pdfdoc.png
/usr/share/phpmyadmin/themes/original/img/b_plus.png
/usr/share/phpmyadmin/themes/original/img/b_prevpage.png
/usr/share/phpmyadmin/themes/original/img/b_primary.png
/usr/share/phpmyadmin/themes/original/img/b_print.png
/usr/share/phpmyadmin/themes/original/img/b_props.png
/usr/share/phpmyadmin/themes/original/img/b_relations.png
/usr/share/phpmyadmin/themes/original/img/b_save.png
/usr/share/phpmyadmin/themes/original/img/b_sbrowse.png
/usr/share/phpmyadmin/themes/original/img/b_sdb.png
/usr/share/phpmyadmin/themes/original/img/b_search.png
/usr/share/phpmyadmin/themes/original/img/b_selboard.png
/usr/share/phpmyadmin/themes/original/img/b_select.png
/usr/share/phpmyadmin/themes/original/img/b_sql.png
/usr/share/phpmyadmin/themes/original/img/b_sqldoc.png
/usr/share/phpmyadmin/themes/original/img/b_sqlhelp.png
/usr/share/phpmyadmin/themes/original/img/b_tblanalyse.png
/usr/share/phpmyadmin/themes/original/img/b_tblexport.png
/usr/share/phpmyadmin/themes/original/img/b_tblimport.png
/usr/share/phpmyadmin/themes/original/img/b_tblops.png
/usr/share/phpmyadmin/themes/original/img/b_tbloptimize.png
/usr/share/phpmyadmin/themes/original/img/b_tipp.png
/usr/share/phpmyadmin/themes/original/img/b_unique.png
/usr/share/phpmyadmin/themes/original/img/b_usradd.png
/usr/share/phpmyadmin/themes/original/img/b_usrcheck.png
/usr/share/phpmyadmin/themes/original/img/b_usrdrop.png
/usr/share/phpmyadmin/themes/original/img/b_usredit.png
/usr/share/phpmyadmin/themes/original/img/b_usrlist.png
/usr/share/phpmyadmin/themes/original/img/b_view.png
/usr/share/phpmyadmin/themes/original/img/b_views.png
/usr/share/phpmyadmin/themes/original/img/bd_browse.png
/usr/share/phpmyadmin/themes/original/img/bd_deltbl.png
/usr/share/phpmyadmin/themes/original/img/bd_drop.png
/usr/share/phpmyadmin/themes/original/img/bd_empty.png
/usr/share/phpmyadmin/themes/original/img/bd_firstpage.png
/usr/share/phpmyadmin/themes/original/img/bd_ftext.png
/usr/share/phpmyadmin/themes/original/img/bd_index.png
/usr/share/phpmyadmin/themes/original/img/bd_insrow.png
/usr/share/phpmyadmin/themes/original/img/bd_lastpage.png
/usr/share/phpmyadmin/themes/original/img/bd_nextpage.png
/usr/share/phpmyadmin/themes/original/img/bd_prevpage.png
/usr/share/phpmyadmin/themes/original/img/bd_primary.png
/usr/share/phpmyadmin/themes/original/img/bd_sbrowse.png
/usr/share/phpmyadmin/themes/original/img/bd_select.png
/usr/share/phpmyadmin/themes/original/img/bd_unique.png
/usr/share/phpmyadmin/themes/original/img/error.ico
/usr/share/phpmyadmin/themes/original/img/item.png
/usr/share/phpmyadmin/themes/original/img/item_ltr.png
/usr/share/phpmyadmin/themes/original/img/item_rtl.png
/usr/share/phpmyadmin/themes/original/img/logo_left.png
/usr/share/phpmyadmin/themes/original/img/logo_right.png
/usr/share/phpmyadmin/themes/original/img/php_sym.png
/usr/share/phpmyadmin/themes/original/img/pma_logo2.png
/usr/share/phpmyadmin/themes/original/img/s_asc.png
/usr/share/phpmyadmin/themes/original/img/s_asci.png
/usr/share/phpmyadmin/themes/original/img/s_attention.png
/usr/share/phpmyadmin/themes/original/img/s_cancel.png
/usr/share/phpmyadmin/themes/original/img/s_cancel2.png
/usr/share/phpmyadmin/themes/original/img/s_db.png
/usr/share/phpmyadmin/themes/original/img/s_desc.png
/usr/share/phpmyadmin/themes/original/img/s_error.png
/usr/share/phpmyadmin/themes/original/img/s_error2.png
/usr/share/phpmyadmin/themes/original/img/s_fulltext.png
/usr/share/phpmyadmin/themes/original/img/s_host.png
/usr/share/phpmyadmin/themes/original/img/s_info.png
/usr/share/phpmyadmin/themes/original/img/s_lang.png
/usr/share/phpmyadmin/themes/original/img/s_loggoff.png
/usr/share/phpmyadmin/themes/original/img/s_notice.png
/usr/share/phpmyadmin/themes/original/img/s_okay.png
/usr/share/phpmyadmin/themes/original/img/s_partialtext.png
/usr/share/phpmyadmin/themes/original/img/s_passwd.png
/usr/share/phpmyadmin/themes/original/img/s_process.png
/usr/share/phpmyadmin/themes/original/img/s_really.png
/usr/share/phpmyadmin/themes/original/img/s_reload.png
/usr/share/phpmyadmin/themes/original/img/s_rights.png
/usr/share/phpmyadmin/themes/original/img/s_status.png
/usr/share/phpmyadmin/themes/original/img/s_tbl.png
/usr/share/phpmyadmin/themes/original/img/s_theme.png
/usr/share/phpmyadmin/themes/original/img/s_vars.png
/usr/share/phpmyadmin/themes/original/img/s_views.png
/usr/share/phpmyadmin/themes/original/img/s_warn.png
/usr/share/phpmyadmin/themes/original/img/spacer.png
/usr/share/phpmyadmin/themes/original/img/vertical_line.png
/usr/share/phpmyadmin/themes/original/img/window-new.png
/usr/share/phpmyadmin/themes/original/info.inc.php
/usr/share/phpmyadmin/themes/original/layout.inc.php
/usr/share/phpmyadmin/themes/original/screen.png
/usr/share/phpmyadmin/transformation_overview.php
/usr/share/phpmyadmin/transformation_wrapper.php
/usr/share/phpmyadmin/translators.html
/usr/share/phpmyadmin/user_password.php
/usr/share/phpmyadmin/view_create.php
```

No /var/www/pma here.

---

### Post by mallegonian on 2008-11-17
No /var/anything there. I don't have any unofficial repos installed.

On second thought, I just purged it and pma/ is still there. *eyeroll* Stupid unfinished projects. Sorry for confusing everybody. The config in there says that it was generated by something... I usually do config stuff myself...
I moved pma/ and installed the phpmyadmin package, and it didn't create anything in /var/www , so you might be expected to create a link yourself.
OP: 'ln -s /usr/share/phpmyadmin /var/www/phpmyadmin' then [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by kernelhaxor on 2008-11-17
I wouldn't recommend PHPMyAdmin .. yes, it is good but I would recommend it only if u need a GUI into ur mysql server from a remote location .. I wouldn't recommend it just for local use coz it requires PHP, running web server, and other things ..

For a simpler lighter solution:
Try the MySQl GUI tools: 
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

I hav tried them on Windows and they are pretty good .. they seem to be available for Linux as well ..

---

### Post by kernelhaxor on 2008-11-17
Just an FYI, u can convert .rpm to .deb using alien or some other tool

---

### Post by jenkinbr on 2008-11-17
> **kernelhaxor said:**
> Just an FYI, u can convert .rpm to .deb using alien or some other tool
FYI - MySQL Administrator and MySQL Query Browser are in the ubuntu repositories...mysql-admin and mysql-query-browser, respectively.  No need to download and convert RPMs.

---

### Post by kernelhaxor on 2008-11-17
> **jenkinbr said:**
> FYI - MySQL Administrator and MySQL Query Browser are in the ubuntu repositories...mysql-admin and mysql-query-browser, respectively.  No need to download and convert RPMs.

Awesome! then thats the easiest and fastest to have a Mysql gui I guess ..

---

### Post by mlotfi on 2008-11-18
It's working now :

After the installation is over execute the following command to copy the phpmyadmin folder into the /var/www/ directory. (By default it is installed in /usr/share/phpmyadmin/ directory.)

sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin

---

### Post by jenkinbr on 2008-11-18
to remove phpmyadmin:```
sudo apt-get remove phpmyadmin
```
to install mysql administrator and query browser:```
sudo apt-get install mysql-admin mysql-query-browser
```

---

