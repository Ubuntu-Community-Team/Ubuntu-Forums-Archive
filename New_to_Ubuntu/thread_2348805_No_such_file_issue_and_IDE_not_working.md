---
title: "No such file issue and IDE not working"
date: 2017-01-07
forum: New to Ubuntu
---

### Post by kattykat243 on 2017-01-07
Hey so I am fairly new to Ubuntu and seem to have gotten myself in a bit of a pickle.

here is my ls -ad file...can someone help me fix this mess. My computer cant seem to locate anything it just says "no such file" and I can't seem to run any compiler or IDE.

```
total 222908
drwxrwxr-x 26 caitlin caitlin      4096 Jan  7 11:23 .
drwxr-xr-x  3 root    root         4096 Dec 20 23:15 ..
drwx------  3 caitlin caitlin      4096 Jan  4 14:42 .adobe
-rw-rw-r--  1 caitlin caitlin    198384 Jan  7 09:09 andale32.exe
-rw-rw-r--  1 caitlin caitlin    554208 Jan  7 09:08 arial32.exe
-rw-rw-r--  1 caitlin caitlin    168176 Jan  7 09:07 arialb32.exe
-rw-------  1 caitlin caitlin     10362 Jan  7 11:29 .bash_history
-rw-r--r--  1 caitlin caitlin       220 Dec 20 23:15 .bash_logout
-rw-r--r--  1 caitlin caitlin      3771 Dec 20 23:15 .bashrc
drwxrwxr-x  4 caitlin caitlin      4096 Jan  7 00:20 .bluefish
drwxr-xr-x 33 caitlin caitlin      4096 Jan  7 11:22 .cache
-rw-------  1 caitlin caitlin      1403 Jan  4 13:42 C++.bfproject~
-rw-rw-r--  1 caitlin caitlin    246008 Jan  7 09:07 comic32.exe
drwx------  3 caitlin caitlin      4096 Jan  1 20:55 .compiz
drwx------ 32 caitlin caitlin      4096 Jan  7 00:03 .config
-rw-rw-r--  1 caitlin caitlin    646368 Jan  7 09:07 courie32.exe
-rw-r--r--  1 caitlin caitlin        25 Jan  7 00:08 .dmrc
-rw-rw-r--  1 caitlin caitlin         0 Jan  7 10:53 eclipse
drwxrwxr-x  3 caitlin caitlin      4096 Jan  7 00:23 .eclipse
drwx------  4 caitlin caitlin      4096 Jan  7 11:01 .gconf
drwxrwxr-x  2 caitlin caitlin      4096 Jan  5 10:06 .gconf*
-rw-rw-r--  1 caitlin caitlin    392440 Jan  7 09:06 georgi32.exe
drwxr-xr-x 24 caitlin caitlin      4096 Jan  1 20:32 .gimp-2.8
drwxrwxr-x  2 caitlin caitlin      4096 Jan  5 10:06 .gnome*
drwx------  3 caitlin caitlin      4096 Jan  7 11:00 .gnupg
drwx------  2 caitlin caitlin      4096 Dec 21 11:25 .gphoto
-rw-rw-r--  1 caitlin caitlin       120 Jan  5 10:36 hello.cpp~
-rw-------  1 caitlin caitlin      8702 Jan  7 11:00 .ICEauthority
drwx------  3 caitlin caitlin      4096 Dec 21 11:24 .local
drwx------  3 caitlin caitlin      4096 Jan  4 14:42 .macromedia
-rw-rw-r--  1 caitlin caitlin         0 Jan  5 10:55 .markers.snap
drwx------  4 caitlin caitlin      4096 Dec 21 11:26 .mozilla
drwxrwxr-x  2 caitlin caitlin      4096 Jan  4 13:01 .nano
drwxrwxr-x  3 caitlin caitlin      4096 Jan  7 11:22 .netbeans
-rw-rw-r--  1 caitlin caitlin 223882240 Jan  7 11:23 netbeans-8.2-linux.sh
drwxrwxr-x  2 caitlin caitlin      4096 Jan  5 10:06 .old-gnome-config
drwxrwxr-x  2 caitlin caitlin      4096 Jan  5 08:55 .oracle_jre_usage
drwx------  3 caitlin caitlin      4096 Jan  1 20:06 .pki
-rw-r--r--  1 caitlin caitlin       734 Jan  6 22:36 .profile
drwxrwxr-x  3 caitlin caitlin      4096 Jan  5 12:40 Projects
-rw-------  1 caitlin caitlin       256 Jan  1 20:06 .pulse-cookie
drwx------  5 caitlin caitlin      4096 Jan  6 21:02 .purple
-rw-rw-r--  1 caitlin caitlin       504 Jan  5 11:12 Reference.cpp~
drwxrwxr-x  2 caitlin caitlin      4096 Jan  7 00:03 Screenshots
drwxrwxr-x  3 caitlin caitlin      4096 Jan  1 20:51 .steam
lrwxrwxrwx  1 caitlin caitlin        32 Jan  1 20:37 .steampath -> /home/caitlin/.steam/bin32/steam
lrwxrwxrwx  1 caitlin caitlin        30 Jan  1 20:37 .steampid -> /home/caitlin/.steam/steam.pid
-rw-r--r--  1 caitlin caitlin         0 Dec 24 00:06 .sudo_as_admin_successful
-rw-rw-r--  1 caitlin caitlin       162 Jan  4 14:09 test.c~
-rw-rw-r--  1 caitlin caitlin    661728 Jan  7 09:06 times32.exe
-rw-rw-r--  1 caitlin caitlin    357200 Jan  7 09:05 trebuc32(1).exe
-rw-rw-r--  1 caitlin caitlin    357200 Jan  7 09:05 trebuc32.exe
-rw-rw-r--  1 caitlin caitlin     37446 Oct 16  2014 ttf-mscorefonts-installer_3.6_all.deb
-rw-rw-r--  1 caitlin caitlin    351992 Jan  7 09:05 verdan32.exe
-rw-rw-r--  1 caitlin caitlin    185072 Jan  7 09:05 webdin32.exe
-rw-------  1 caitlin caitlin        66 Jan  7 11:00 .Xauthority
-rw-rw-r--  1 caitlin caitlin       131 Jan  6 21:14 .xinputrc
-rw-------  1 caitlin caitlin       154 Jan  7 11:00 .xsession-errors
-rw-------  1 caitlin caitlin       960 Jan  7 11:00 .xsession-errors.old
```


Thank you

---

### Post by QIII on 2017-01-07
Hello!

We need a bit more detail.  To start with, exactly what are you doing when you get the "no such file" message?

---

