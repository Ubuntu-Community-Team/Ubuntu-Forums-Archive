---
title: "[SOLVED] Updates broke Internet fix, Please Help"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by luckylucky on 2008-08-21
Hi,

I had solved a problem as was posted a couple hours ago here in this thread that is currently marked as "solved"
[http://ubuntuforums.org/showthread.php?p=5636582](http://ubuntuforums.org/showthread.php?p=5636582)

I then ran an update, downloading a bunch of updates since I just did the install.  After the update the Internet stopped working.  I tried redoing all the previous steps to get it working as mentioned in the original thread, but nothing seems to work.  The internet is now broken again.

Note that the Network wizard lets me input all the information there, but it is already there anyhow.  It does appear to remember my network settings.  It's just that it doesn't work.  I've tried a bunch of things trying to coax it into working, but I'm now beating head on wall.  Qll I can think of is that the update somehow broke the internet "fix" I did earlier.

Any help will be warmly welcomed.  Thank you in advance.

---

### Post by bobnutfield on 2008-08-21
Most likely that one of the updates was a kernel update.  This will sometimes stop ndiswrapper from working as ndiswrapper is a module assigned to a particular kernel.  Open a terminal and type:

> sudo ndiswrapper -l

See if it returns the driver installed and the device present.

If it does, try:

> sudo modprobe ndiswrapper

to try and load the module again.

---

