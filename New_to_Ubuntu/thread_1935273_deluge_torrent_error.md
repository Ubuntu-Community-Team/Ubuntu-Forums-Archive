---
title: "deluge torrent error"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by wsy28187222 on 2012-03-03
hi everyone, this is my first post here seeking for help. 

I use GTK UI to connect daemon, torrents are working properly when I change download directory to /var/lib/deluge,but this directory is located in system location which is only 10GB. when change directory to /home/(another partition), the status bar shows correct disk space( 200 GB more).but when I adding a torrent to it, it just downloading nothing and shows checking.....  besides that, the server is also running rtorrent in 200GB partition has no problem...

---

### Post by blazemore on 2012-03-06
Sounds like the user that's running the Deluge daemon doesn't have write permissions on the directory it's trying to save to.

---

