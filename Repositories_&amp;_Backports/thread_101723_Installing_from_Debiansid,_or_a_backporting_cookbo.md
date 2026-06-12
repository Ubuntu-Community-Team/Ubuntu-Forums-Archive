---
title: "Installing from Debian/sid, or a backporting cookbook?"
date: 2005-12-10
forum: Repositories &amp; Backports
---

### Post by HippoMan on 2005-12-10
I recently went to the backports forum and posted a request for the newest Debian ports of a couple packages that I 'd like to see backported (runit and runit-run, both of which have much newer versions under Debian). However, it looks like there's a backlog there, and this might not get done for a while. Therefore, I'm wondering if I can get the Debian (sid) packages for these two items and install them directly onto my Ubuntu 5.10 system.
 
Are there differences between standard Debian and Ubuntu packages that would cause this not to work?  If so, is there any documentation that will tell me how to turn a valid Debian package into one that correctly works for Ubuntu? ... in other words, is there some sort of backporting cookbook?

Thanks in advance.

---

### Post by Seth on 2005-12-10
The thing that's going to cause Debian packages not to work on Ubuntu is generally:
[LIST]
[*] Ubuntu-specific patches. Things that have changed for Ubuntu either because Ubuntu is ahead of Debian on fixing things, or because Ubuntu is set up a special way.
*How you can tell: Does the Ubuntu package have an ubuntu# trailer, e.g. 1.3.0-2ubuntu3? Then Ubuntu changes have been made and you will need to merge those in.*
[*]Ubuntu-specific depends. Because of things like modular X, Ubuntu's build dependencies (the packages a program needs to compile successfully) are often different than Debian's.
*How you can tell: if you have satisfied the build-deps listed in debian/control but the package FTBFS, check to see if there are new packages that satisfy the build-deps better. (This may require changelog searches)*[/LIST]I built your packages in the other thread for you, just as a note.

---

