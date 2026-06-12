---
title: "[SOLVED] firefox always offline"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by fr.theo on 2008-06-17
hello, all.

I am using Firefox 3 and every time I open the application, whether or not I am log on to the internet it is off line, I was wondering if anyone knows how to set it to online permanently.

Kind regards 

FR. T.

---

### Post by iaculallad on 2008-06-17
Try to open your Firefox application, click on "File" menu and uncheck (if checked) the "Work Offline" option.

---

### Post by gtdaqua on 2008-06-17
I think fr.theo wanted a 'permanent' solution. It was happening in my Firefox 3 on hardy until yesterday which was irritating whenever you close and open again. But since this morning it has vanished and its 'online' permanently.

---

### Post by Corrupt3d on 2008-06-17
This seems to be a well documented bug for Linux and Unix users.

[quote=]
Linux and Unix
===============
* Users on a PPP connection (dialup or DSL) may find that Firefox always starts in "Offline" mode. 
Toggle File > Work Offline as a work around (bug 424626) 
[_Link_]("http://www.mozilla.com/en-US/firefox/3.0rc2/releasenotes/#issues") [/quote]

Theres a discussion page [_here_]("https://bugzilla.mozilla.org/show_bug.cgi?id=424626"), and it appears the problems results from Firefox dependence on Network Manager to determine if theres an internet connection.

It seems that patch is [_being developed_]("https://bugzilla.mozilla.org/attachment.cgi?id=322620"). 

In the meantime, depending on how much of a problem it is, you could try and disable Network Manager and see if it solves the problem.
[_How to set your connection Manual without Network Manager_]("http://ubuntuforums.org/showthread.php?t=684495")

---

