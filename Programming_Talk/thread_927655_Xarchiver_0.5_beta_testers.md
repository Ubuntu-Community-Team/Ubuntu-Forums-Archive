---
title: "Xarchiver 0.5 beta testers"
date: 2008-09-23
forum: Programming Talk
---

### Post by colossus73 on 2008-09-23
Hi guys,

I'm the Xarchiver developer, my name is Giuseppe Torelli. I'm about to release the 0.5 with a L O T of improvements but I need your help. Would you like to test it? The current svn code is available on svn xfce server:

$ svn co [http://svn.xfce.org/svn/xfce/xarchiver/trunk](http://svn.xfce.org/svn/xfce/xarchiver/trunk) xarchiver

To compile you need xfce-dev-tools. Please help me to release Xarchiver 0.5 as soon as possible thank you,

---

### Post by colossus73 on 2008-11-07
Released today the 0.5.1 with a bugfix and a new archive support: LZOP.

---

### Post by kung fu buntu on 2008-11-07
I still haven't found a "archiver" frontend that is half as good as winrar.
I've been using file-roller, but I like the new xarchiver 0.5.0 (version 0.5.1 is not in Debian repos yet :p)


Some suggestions:
- make it possible to navigate within the archive, with just the keyboard.
For that you only need to add a ".." entry a the top of the file listing.
Allowing that even at the top level would make it possible to browse and open other archives without having to close the program. Suggestion: change the ".." line color when at the top level, this would work as an alert in order to avoid the user from having to re-open the same file again.

- allow to see the output of the operation. Simple as redirecting the output to a file and opening that file.
Remember to add a keyboard shortcut ;)
Also put a button on the menu or use the green/red light to also show the log file from the last operation.

- an option to have an "OK" dialog box to pop when files have finished extracting. It should be clickable automatically with the enter key (in order to avoid the user from using the mouse to click it)
I know there is the green light... but... I don't know why, but it really doesn't inspire much confidence. My fear is that I end up with corrupt file extractions.
Corrupt files happen with ark (KDE archiver) when there is more than one instance extracting files... very bad!!!

- if you are bored: make possible for the user to set parameters when creating an archive file. For example, setting the compression level on a rar file.
Maybe a simple solution would be to have a "interfaces" file /usr/lib/xarchive.cfg where you could tune this settings. This would you having to make all sort of crazy UI for each archive type.


I really like the fact that:
- there are keyboard shortcuts
- it's possible to show the comment when you open the archive
- you can configure options like icon size, window geometry, etc

---

### Post by colossus73 on 2008-11-07
> **kung fu buntu said:**
> I still haven't found a "archiver" frontend that is half as good as winrar.
I've been using file-roller, but I like the new xarchiver 0.5.0 (version 0.5.1 is not in Debian repos yet :p)


Thank you for your kind appreciation. Regarding the package I asked the maintainer to package it.

> **kung fu buntu said:**
> 
Some suggestions:
- make it possible to navigate within the archive, with just the keyboard.
For that you only need to add a ".." entry a the top of the file listing.
Allowing that even at the top level would make it possible to browse and open other archives without having to close the program. Suggestion: change the ".." line color when at the top level, this would work as an alert in order to avoid the user from having to re-open the same file again.


I will think about this. 

> **kung fu buntu said:**
> 
- allow to see the output of the operation. Simple as redirecting the output to a file and opening that file.
Remember to add a keyboard shortcut ;)
Also put a button on the menu or use the green/red light to also show the log file from the last operation.


You have such option as a menu: CTRL+U

> **kung fu buntu said:**
> 
- if you are bored: make possible for the user to set parameters when creating an archive file. For example, setting the compression level on a rar file.


You have this too. Just click on the Options tab inside the Add dialog.

> **kung fu buntu said:**
> 
Maybe a simple solution would be to have a "interfaces" file /usr/lib/xarchive.cfg where you could tune this settings. This would you having to make all sort of crazy UI for each archive type.
I really like the fact that:
- there are keyboard shortcuts
- it's possible to show the comment when you open the archive
- you can configure options like icon size, window geometry, etc


Press CTRL+F and read the docs then ;)

Thank you for using Xarchiver.

---

