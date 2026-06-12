---
title: "How to FileZilla ftp client - linux port - snapshot"
date: 2006-08-17
forum: Outdated Tutorials &amp; Tips
---

### Post by william_nbg on 2006-08-17
A great free ftp client which a lot of new Linux users will know from Windows. Their next version: 3, will be released including a Linux port, and you can get the beta now. I've been using it for a few days now and it works fine.

Just download the newest snapshot here:

[http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

extract the .bz file, and put the directory whereever you'd like to have it.

If you look in the 'bin' directory you'll find a file, 'filezilla', just double click on this file. You should get a warning about this program not being stable yet - just click OK. That's it! No need to install the thing.:D 

Just put the whole directory where ever you want it, and open your Alacart Menu editor or whatever you use:

File
New entry
In the command line field - path to the filezilla exec file
You'll find the programs icon in the 'resources' directory.

---

### Post by petersjm on 2006-08-20
Nice one. I used FileZilla on WinXP, but now I'm on Ubuntu and figured I couldn't use it, so I'm actually using FireFTP instead. Works a charm.

---

### Post by DC@DR on 2006-08-20
I like FileZilla also, it's kinda neat. Would love to see it ported to Linux. Currently stick with good old gFTP :)

---

### Post by steve8track on 2008-07-29
Nautilus lets you connect via FTP.  Just select "Connect to Server..." from the Places menu and select the correct FTP option.  I like that option because it's integrated with the default file browser, although it lets editing remotely by default with ssh, whereas with FTP you have to change a property in the gconf-editor:

[http://ubuntuforums.org/showthread.php?t=151895]("http://ubuntuforums.org/showthread.php?t=151895")

Also, Konqueror lets you connect to servers using SSH and probably FTP too.  Instead of remotely editing with gedit though, you can use Kate or Kwrite.

I hope this helps,

Steve

---

