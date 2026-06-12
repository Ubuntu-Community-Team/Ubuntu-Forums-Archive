---
title: "[SOLVED] Where do my downloads go?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by zaivala on 2008-09-28
I've been using Linux too long to be asking this question, although in most ways I'm still a newbie...

When I download stuff from the Internet, where (what folder) does Ubuntu save those files?  I've been looking all over my system for something recently downloaded, every folder labeled TMP or whatever...  I'm sure this is a stupid question, which should make it easier to get a quick answer.

Moss

---

### Post by forger on 2008-09-28
1) Are you downloading using Firefox? :)
2) If answer in (1) is yes, go to firefox's menu Edit &#8594; Preferences &#8594; Main, there's a "Downloads" section in the preferences, where you set a default folder or choose to ask you every time you download

---

### Post by zaivala on 2008-09-28
Yes, I am downloading using Firefox.  However, Firefox says it is downloading to Desktop... which it does, except when I tell it to use a program to open the package.  In this case, it was a zipped archive I was downloading, and upon extraction, I can't find the archive.

Thanks so much for your help.

---

### Post by jerome1232 on 2008-09-28
In that case if it's not deleted it would probably in in firefox's cache.

Should be under 
~/.mozilla

to browse there with nautilus open up your home directory hit ctrl+h to view hidden files, then have a look around.

---

### Post by zaivala on 2008-09-28
> **jerome1232 said:**
> In that case if it's not deleted it would probably in in firefox's cache.

Should be under 
~/.mozilla

to browse there with nautilus open up your home directory hit ctrl+h to view hidden files, then have a look around.

Thanks for the hint, didn't even know (a) that there were hidden files or (b) how to reveal them... but it wasn't there.  Perhaps the system has deleted the archive?

Under .mozilla I have the folders "extensions" and "firefox".  Extensions has an empty folder with a gobbledygook name, firefox has "izfozp9k.default" which in turn has seven subfolders (all seeming to refer to firefox extensions) and several files, none of which is an archive...

Thanks for trying.  Let me know if you can think of anything else.

Edited to add:  AHA! Found the Cache folder.  Can't believe I was blind... I'll see if I can find the archive here.


Edited yet again to add: Well, it wasn't labeled by the original name, so I sorted on Date and found it.  Thanks yet again.
Moss

---

### Post by forger on 2008-09-29
Temporary files can be also be found in /tmp/ folder:
```
nautilus /tmp
```
"Open files" in Firefox does what it is supposed to do, it previews the file, without actually saving it :)

Also, once you have opened the file, it depends on the program you use, but you usually have a menu File > Save or Save as to save it properly :)

---

