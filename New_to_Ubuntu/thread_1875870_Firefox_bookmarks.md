---
title: "Firefox bookmarks"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by Autodave on 2011-11-05
Where are the bookmarks for Firefox saved on the hard drive on Ubuntu 10.04?  I have a corrupted system after a recent update and need to save them before I reinstall 10.04.

---

### Post by Frogs Hair on 2011-11-05
I don' t know what version of Firefox you are using . I use this  method ,  open Bookmarks > Unsorted Bookmarks > Import and Backup .

Export and the bookmarks as .html , include the document with your backup to be imported later from Import and Backup .

---

### Post by WasMeHere on 2011-11-05
I run 10.04 and it is located according to the following text in the terminal
```
**~/.mozilla/firefox/zuvg6pxg.default**$ ls bookmark*
bookmarks.html

bookmarkbackups:
bookmarks-2011-10-30.json  bookmarks-2011-11-01.json  bookmarks-2011-11-03.json
bookmarks-2011-10-31.json  bookmarks-2011-11-02.json  bookmarks-2011-11-04.json

```the string [FONT="Courier New"][SIZE="3"]zuvg6pxg[/SIZE][/FONT] is probably something else in your computer

---

### Post by mike555 on 2011-11-05
Probably easiest to just copy the hidden .Mozilla file from your old /home to new install , that way you will get bookmarks and passwords ,etc.

---

### Post by Zimrie on 2011-11-05
use xmarks

---

### Post by lovinglinux on 2011-11-05
The bookmarks are located in the *places.sqlite* database file, under your Firefox profile folder ~/.mozilla/firefox/<profilefolder>. Copying it or the entire .mozilla folder to your new installation should do it. As others already mentioned, doing a backup restore works as well.

---

### Post by kaldor on 2011-11-05
> **mike555 said:**
> Probably easiest to just copy the hidden .Mozilla file from your old /home to new install , that way you will get bookmarks and passwords ,etc.

Yes- copy the entire .mozilla directory. This will retain all settings from Firefox.

---

### Post by cap10Ibraim on 2011-11-05
you should consider firefox sync too (built in feature now) 
[http://www.mozilla.org/en-US/mobile/sync/](http://www.mozilla.org/en-US/mobile/sync/) 
on 10.04 if you still in firefox 3.6 you can have it as an add on from 
[https://addons.mozilla.org/en-US/firefox/addon/firefox-sync/](https://addons.mozilla.org/en-US/firefox/addon/firefox-sync/)

---

### Post by dFlyer on 2011-11-05
I usually backup the whole /home/username/.mozilla folder.

---

