---
title: "Torrentflux moved my PostgreSQL folder"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by vixmusic01 on 2008-09-28
-- Please Help PostgrSQL --

This is a general warning to Gutsy users who may try to install torrentflux.
Careful -- it moved required folders on my computer during install and has created a lot of problems with no support.

I posted my problem on their site, but no help has been posted.

[http://www.torrentflux.com/forum/index.php/topic,3904.0.html](http://www.torrentflux.com/forum/index.php/topic,3904.0.html)

I tried to install torrentflux using Synaptic, but it could not find  MySQL even though I have common installed, so I exited the installation.

I received this message during the failed install:

"WARNING: Incude path for php has changed.

libphp-adodb is not longer installed in /usr/share/adodb. New installation path is now usr/share/php/sdodb.

Please update your php.ini file. Maybe you must also change your web-server configuration."
--------------------------------------------

I checked the /usr folder and the file had been moved. Now my internet won't work and I can't move it back. My php.ini folder is not something I want to mess with by myself.

--------------------------------

Since this time I have been waiting for torrentflux to help and messing about. I have the internet working, but the list during boot shows that the PhP dataabase is not found. Gnome is not working properly and random other programs act strangely. 

On boot up "The PostgreSQL 8.2 database server failed to start. Please check log file".

Please help me restore my computer -- I do not care if the torrent program installs at all.

Thanks for any help,

Victoria

---

### Post by teunispeters on 2009-03-12
turns out the issue was tmpfs - torrentflux (likely) installed and misconfigured tmpfs, defaulting to 1K (1024 bytes) free space - which was quickly exhausted, causing system-wide side effects.

---

### Post by vixmusic01 on 2009-03-12
Thanks so much for the help. This computer had been non-functional for months and I would not have been able to get it working again without your assistance.

Extra good karma points for you,

Victoria

---

