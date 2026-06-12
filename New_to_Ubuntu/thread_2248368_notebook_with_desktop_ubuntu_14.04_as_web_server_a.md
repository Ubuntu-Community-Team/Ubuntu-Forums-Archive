---
title: "notebook with desktop ubuntu 14.04 as web server accessed through wireless"
date: 2014-10-14
forum: New to Ubuntu
---

### Post by koollearn on 2014-10-14
hey, i just installed ubuntu 14.04 on my notebook.
i've installed xampp to get it working as a web server and some site thingy with drupal.

anyway, just wondering..

would it be possible to get other pcs with windows to access the site on the notebook using wireless?
if so, could u please like explain it step by step?

thanks in advance!

---

### Post by sandyd on 2014-10-14
> **koollearn said:**
> hey, i just installed ubuntu 14.04 on my notebook.
i've installed xampp to get it working as a web server and some site thingy with drupal.

anyway, just wondering..

would it be possible to get other pcs with windows to access the site on the notebook using wireless?
if so, could u please like explain it step by step?

thanks in advance!

a) I honestly prefer a LAMP (Linux, Apache, MySQL, PHP), or LNMP (Linux, Nginx, MySQL, PHP) setup because it is easier to debug when things go wrong, but if xampp works for you, thats fine.

b) You can see your network information by running the following command in the terminal.
```

ifconfig
```

From the output, you can see the IP Address of your computer (It usually shows up as wlanX where X is a number). You should be able to use that IP to access the webserver from other computers.

Unfortunately, I am not familiar with xampp, which may require the modification of configuration files in order to set it to listen on your local area network IP Address.

---

### Post by TheFu on 2014-10-14
I've never used xampp.

Why not?

Just connect them to the same network (wired/wifi doesn't matter) that is managed by the same router and point their music player at the webpage which has an M3U file playlist with complete URLs to each audio file for playback. On most systems, visiting the webpage with a normal web browser will be easier, then if they have a helper applications associated with m3u files, it will launch the music player.

For making a streaming music player over the web, this seems much harder than using [gnump3]("http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html") which has been around forever and "just works".  Also - winamp is a client that I know handles m3u playlists.

If you really want to be cool - handle videos too - use Plex Media Server and any DLNA client or web browers can playback audio, photos, video on the LAN.

Step-by-step is beyond me. Sorry.

---

