---
title: "cvs [import aborted]: received abort signal"
date: 2009-03-01
forum: Programming Talk
---

### Post by huangyingw on 2009-03-01
hello, everyone:
   My environment infos:
   (CVS) 1.12.13 (server)
   (CVSNT) 2.5.03 (Scorpio) Build 2382 (client)
   I met the following error when I trying to run this command in windows:
=================================================================
   C:\Documents and Settings\huangyingw\c#\MusicManagement>cvs im -m "add MusicManagement" c#/MusicManagement huangyingw start
=================================================================
   At the end of output, is the error, as shown bellow:
=================================================================
cvs import: Importing /cvsroot/c#/MusicManagement/reference
N c#/MusicManagement/reference/CSID3Lib-0.2.src.zip
cvs: import.c:635: process_import_file: Assertion `entdata->options[0] == '-' &&
 entdata->options[1] == 'k'' failed.
cvs [import aborted]: received abort signal
=================================================================
Any help greatly appreciated.

---

