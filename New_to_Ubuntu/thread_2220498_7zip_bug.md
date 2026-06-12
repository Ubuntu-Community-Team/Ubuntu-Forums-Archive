---
title: "7zip bug"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by wjbmd48 on 2014-04-28
Hi:

What's the easiest way to report a possible bug?  

The archive manager in 14.04 Lubuntu doesn't properly compress files in 7zip format, at least on my system; the files won't unzip properly at the receiving end with the standard Windows 7zip application.

The work around is installing 7zip under Wine, but I wonder if this is not a bug with the new distro.


Bill

---

### Post by sudodus on 2014-04-28
I think you should start by testing if the problem is in the archive manager or the underlying tools.

Try compressing with ***7z*** and ***xz*** and check if these command line tools make good compressed files! If you are not familiar with the command line options, read the manual pages

```
man 7z
``` and ```
man xz
```

and if you still have problems, ask for help.

---

### Post by The Spectre on 2014-04-28
You might check to make sure that you have 7zip installed...
[https://apps.ubuntu.com/cat/applications/p7zip-full/](https://apps.ubuntu.com/cat/applications/p7zip-full/)

[ATTACH=CONFIG]252608[/ATTACH]

---

### Post by wjbmd48 on 2014-04-28
Yep, p7zip-full is installed, and the work-around of using Wine/7zPM.exe solves the problem. (Slightly longer, but has the advantage of being able to see the pw.) The thing is, my file recipients had no problems with 7zip files compressed with archive manager before the official 14.04 release/upgrade, so not a real issue, just wanted to raise it if others are reporting it.

Again, you guys are the best, thanx!!

Bill

---

### Post by The Spectre on 2014-04-28
You could try Removing p7zip-full and file-roller and then re-install it to see if that might straiten it out.

Or as an alternative you could use PeaZip...   
[http://peazip.sourceforge.net/peazip-linux.html](http://peazip.sourceforge.net/peazip-linux.html)

---

