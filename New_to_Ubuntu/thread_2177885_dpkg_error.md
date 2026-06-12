---
title: "dpkg error"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by fiveeyed on 2013-09-30
So I turned on my system today and attempted to download cheese with apt-get install, but I was given this message;

dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libisccfg90': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

I tried to reinstall the bind package from the software center but it produced the same error message. Any suggestions on repairing the issue?

---

### Post by newb85 on 2013-09-30
You might try:
```
sudo apt-get -f install
```
Post the output so we can see what's going on, please.

---

### Post by fiveeyed on 2013-09-30
larry@larry-Aspire-S3-391:~$ sudo apt-get -f install cheese
Reading package lists... Done
Building dependency tree... 0%
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb kde-l10n-engb libsamplerate0:i386 libspeexdsp1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cheese-common gnome-video-effects libcheese-gtk23 libcheese7
Suggested packages:
  gnome-video-effects-frei0r
The following NEW packages will be installed:
  cheese cheese-common gnome-video-effects libcheese-gtk23 libcheese7
0 upgraded, 5 newly installed, 0 to remove and 8 not upgraded.
Need to get 0 B/3,098 kB of archives.
After this operation, 7,055 kB of additional disk space will be used.
Selecting previously unselected package cheese-common.
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libisccfg90': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by newb85 on 2013-10-01
Look at the instructions here [http://ubuntuforums.org/archive/index.php/t-1232143.html](http://ubuntuforums.org/archive/index.php/t-1232143.html) (the seventh post, by gartss).  They're for a corrupted status file about a different package, but it should work the same way.

---

### Post by fiveeyed on 2013-10-04
Thank you so much, I am still new to linux, but soaking things like this up like a sponge, the issue is now resolved. Thank you for the help.

---

