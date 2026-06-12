---
title: "Flash 10 64 Alpha problems"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by trashypatches on 2008-11-28
Hello, I have downloaded the alpha release of Flash but I am having troubles once I have unzipped the file onto the desktop.  I am running the newest version of Ubuntu and when I go to watch flash files on youtube or alike, firefox will freeze up and I have to force quit.  How do I go about viewing flash videos on firefox?

---

### Post by jgoguen on 2008-11-28
Here's what I did to get it all working.  Try these commands, pushing Enter after each command.  I'll assume you're starting from just having downloaded the package, for anyone else who comes looking for this thread.  Just ignore anything you've already done.

[LIST]
[*]cd ~/Desktop/
[*] tar zxf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
[*]sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
[*]sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
[*]sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox/plugins/
[/LIST]

After that, close all Firefox windows, open Firefox again, and Flash should work.

Hope that helps.

---

