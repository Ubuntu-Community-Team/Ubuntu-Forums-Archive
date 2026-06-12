---
title: "[SOLVED] Typo3"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by yorkie107 on 2008-09-24
Hi I'm new to Ubuntu and I'm trying to install Typo3 on my comp I have been following a tut I found on the web at [http://ubuntuforums.org/showthread.php?p=3747082](http://ubuntuforums.org/showthread.php?p=3747082) but I'm having problems with it

1 I set up a database for Typo3 OK, to set up a new user in mysql it says to use - 

mysql> grant all privileges on Typo3.* to New-username@localhost identified by 'typo3';

if I type it into the terminal It returns

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'priveleges on Tyop3.* to New-username@localhost identified by 'typo3'' at line 1

2 After I have installed Typo3 it says  to change ownership rights to use

chown -R -v www-data /var/www/typo3_src-4.1.2
chown -R -v www-data /var/www/cms

but when I try these two commands it fails

chown -R -v www-data /var/www/typo3_src-4.1.2 returns 

failed to change ownership of `/var/www/typo3_src-4.1.2/NEWS.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_diff.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_diff.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_rteapi.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_rteapi.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_htmlmail.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_htmlmail.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_browsetree.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_browsetree.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsstyleconfig.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsstyleconfig.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_sqlengine.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_sqlengine.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_div.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_div.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_syntaxhl.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_syntaxhl.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/GPL.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/GPL.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_treeview.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_treeview.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/thumbs.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/thumbs.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_fullsearch.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_fullsearch.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_softrefproc.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_softrefproc.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_svbase.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_svbase.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_beuserauth.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_beuserauth.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_stdgraphic.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_stdgraphic.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_loaddbgroup.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_loaddbgroup.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_readmail.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_readmail.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_parsehtml.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_parsehtml.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/config_default.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/config_default.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_userauthgroup.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_userauthgroup.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.inline.js': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.inline.js' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsfebeuserauth.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsfebeuserauth.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_cli.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_cli.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_loadmodules.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_loadmodules.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_sqlparser.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_sqlparser.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_recordlist.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_recordlist.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_transferdata.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_transferdata.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/tables.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/tables.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/tbl_be.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/tbl_be.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/tables.sql': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/tables.sql' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/load_ext_tables.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb/load_ext_tables.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/stddb' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.menu.js': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.menu.js' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_exec.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_exec.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.validateform.js': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.validateform.js' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tstemplate.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tstemplate.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_timetrack.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_timetrack.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_extmgm.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_extmgm.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/README.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/README.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_matchcondition.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_matchcondition.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_cs.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_cs.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_iconworks.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_iconworks.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-11.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-11.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-2.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-2.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1258.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1258.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-7.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-7.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1252.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1252.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-14.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-14.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1254.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1254.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/ascii.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/ascii.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1251.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1251.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/shift_jis.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/shift_jis.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/koi8-r.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/koi8-r.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-874.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-874.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/euc-kr.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/euc-kr.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-15.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-15.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-8.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-8.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/big5.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/big5.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-4.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-4.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-10.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-10.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-13.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-13.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1256.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1256.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1257.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1257.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-5.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-5.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-9.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-9.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/readme.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/readme.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-16.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-16.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-6.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-6.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-1.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-1.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/gb2312.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/gb2312.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1255.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1255.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-3.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/iso-8859-3.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1253.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1253.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1250.tbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl/windows-1250.tbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/csconvtbl' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_basicfilefunc.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_basicfilefunc.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_db.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_db.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_page.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_page.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_modsettings.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_modsettings.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_flexformtools.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_flexformtools.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.evalfield.js': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.evalfield.js' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tceforms.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tceforms.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_bedisplaylog.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_bedisplaylog.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_querygenerator.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_querygenerator.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_befunc.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_befunc.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_foldertree.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_foldertree.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsparser_ext.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsparser_ext.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_scbase.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_scbase.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata/UnicodeData.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata/UnicodeData.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata/SpecialCasing.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata/SpecialCasing.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata/Translit.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata/Translit.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/unidata' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.gzip_encode.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.gzip_encode.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_userauth.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_userauth.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/compat_php5.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/compat_php5.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_extobjbase.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_extobjbase.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/index.html': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/index.html' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_transl8tools.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_transl8tools.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.updateform.js': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/jsfunc.updateform.js' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_topmenubase.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_topmenubase.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_arraybrowser.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_arraybrowser.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_admin.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_admin.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_parsehtml_proc.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_parsehtml_proc.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tcemain.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tcemain.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_ajax.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_ajax.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_formmail.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_formmail.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_extfilefunc.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_extfilefunc.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_superadmin.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_superadmin.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/nimbus.ttf': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/nimbus.ttf' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/vera.ttf': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/vera.ttf' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/readme.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/readme.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/index.html': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts/index.html' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/fonts' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_clipboard.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_clipboard.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_xml.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_xml.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_install.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_install.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_refindex.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_refindex.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_pagetree.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_pagetree.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tceforms_inline.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tceforms_inline.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_positionmap.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_positionmap.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsparser.php': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib/class.t3lib_tsparser.php' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/t3lib': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/t3lib' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/INSTALL.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/INSTALL.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2/RELEASE_NOTES.txt': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2/RELEASE_NOTES.txt' to www-data
chown: changing ownership of `/var/www/typo3_src-4.1.2': Operation not permitted
failed to change ownership of `/var/www/typo3_src-4.1.2' to www-data

and chown -R -v www-data /var/www/cms returns

mark@mark-desktop:/var/www/cms$ chown -R -v www-data /var/www/cms
chown: changing ownership of `/var/www/cms/typo3conf/l10n': Operation not permitted
failed to change ownership of `/var/www/cms/typo3conf/l10n' to www-data
chown: changing ownership of `/var/www/cms/typo3conf/ext': Operation not permitted
failed to change ownership of `/var/www/cms/typo3conf/ext' to www-data
chown: changing ownership of `/var/www/cms/typo3conf/localconf.php': Operation not permitted
failed to change ownership of `/var/www/cms/typo3conf/localconf.php' to www-data
chown: changing ownership of `/var/www/cms/typo3conf/index.html': Operation not permitted
failed to change ownership of `/var/www/cms/typo3conf/index.html' to www-data
chown: changing ownership of `/var/www/cms/typo3conf/extTables.php': Operation not permitted
failed to change ownership of `/var/www/cms/typo3conf/extTables.php' to www-data
chown: changing ownership of `/var/www/cms/typo3conf': Operation not permitted
failed to change ownership of `/var/www/cms/typo3conf' to www-data
chown: changing ownership of `/var/www/cms/typo3_src': Operation not permitted
failed to change ownership of `/var/www/cms/typo3_src' to www-data
chown: changing ownership of `/var/www/cms/_.htaccess': Operation not permitted
failed to change ownership of `/var/www/cms/_.htaccess' to www-data
chown: changing ownership of `/var/www/cms/typo3temp': Operation not permitted
failed to change ownership of `/var/www/cms/typo3temp' to www-data
chown: changing ownership of `/var/www/cms/index.php': Operation not permitted
failed to change ownership of `/var/www/cms/index.php' to www-data
chown: changing ownership of `/var/www/cms/clear.gif': Operation not permitted
failed to change ownership of `/var/www/cms/clear.gif' to www-data
chown: changing ownership of `/var/www/cms/uploads/tf': Operation not permitted
failed to change ownership of `/var/www/cms/uploads/tf' to www-data
chown: changing ownership of `/var/www/cms/uploads/media': Operation not permitted
failed to change ownership of `/var/www/cms/uploads/media' to www-data
chown: changing ownership of `/var/www/cms/uploads/index.html': Operation not permitted
failed to change ownership of `/var/www/cms/uploads/index.html' to www-data
chown: changing ownership of `/var/www/cms/uploads/pics': Operation not permitted
failed to change ownership of `/var/www/cms/uploads/pics' to www-data
chown: changing ownership of `/var/www/cms/uploads': Operation not permitted
failed to change ownership of `/var/www/cms/uploads' to www-data
chown: changing ownership of `/var/www/cms/typo3': Operation not permitted
failed to change ownership of `/var/www/cms/typo3' to www-data
chown: changing ownership of `/var/www/cms/README.txt': Operation not permitted
failed to change ownership of `/var/www/cms/README.txt' to www-data
chown: changing ownership of `/var/www/cms/t3lib': Operation not permitted
failed to change ownership of `/var/www/cms/t3lib' to www-data
chown: changing ownership of `/var/www/cms/INSTALL.txt': Operation not permitted
failed to change ownership of `/var/www/cms/INSTALL.txt' to www-data
chown: changing ownership of `/var/www/cms/fileadmin/_temp_/.htaccess': Operation not permitted
failed to change ownership of `/var/www/cms/fileadmin/_temp_/.htaccess' to www-data
chown: changing ownership of `/var/www/cms/fileadmin/_temp_/index.html': Operation not permitted
failed to change ownership of `/var/www/cms/fileadmin/_temp_/index.html' to www-data
chown: changing ownership of `/var/www/cms/fileadmin/_temp_': Operation not permitted
failed to change ownership of `/var/www/cms/fileadmin/_temp_' to www-data
chown: changing ownership of `/var/www/cms/fileadmin/user_upload/_temp_': Operation not permitted
failed to change ownership of `/var/www/cms/fileadmin/user_upload/_temp_' to www-data
chown: changing ownership of `/var/www/cms/fileadmin/user_upload': Operation not permitted
failed to change ownership of `/var/www/cms/fileadmin/user_upload' to www-data
chown: changing ownership of `/var/www/cms/fileadmin': Operation not permitted
failed to change ownership of `/var/www/cms/fileadmin' to www-data
chown: changing ownership of `/var/www/cms/RELEASE_NOTES.txt': Operation not permitted
failed to change ownership of `/var/www/cms/RELEASE_NOTES.txt' to www-data
chown: changing ownership of `/var/www/cms': Operation not permitted
failed to change ownership of `/var/www/cms' to www-data

Any thoughts of what could be wrong would be a great help

Thanks

Yorkie107

---

### Post by Paqman on 2008-09-24
Since you aren't the owner of /var/www you'll have to prefix your chown command with sudo. Like this:
```

sudo chown -R -v www-data /var/www/typo3_src-4.1.2
sudo chown -R -v www-data /var/www/cms

```

---

### Post by Borusa on 2008-09-24
1) Check your spelling of "privilege" in the command - the error message has it spelt wrong.

---

### Post by lian1238 on 2008-09-24
You need super user (administrative) rights. Put "sudo" in front of the code.

---

### Post by yorkie107 on 2008-09-24
Thanks guys sudo was missing

---

### Post by lian1238 on 2008-09-24
Mark as solved please.
Thanks. ;)

---

