---
title: "Play media files on Ubuntu 12.04 server"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Vistz on 2013-02-17
I recently installed Ubuntu 12.04 on my server. My goal was to put media files (music/videos) on there and then ssh into it and play them. I want to be able to play them from any computer that can use ssh.

I was looking for ways to accomplish this. Any help is appreciated.

---

### Post by MrKaliman on 2013-02-17
Does this help you?

[http://ubuntuforums.org/showthread.php?t=1148203](http://ubuntuforums.org/showthread.php?t=1148203)

---

### Post by Vistz on 2013-02-17
> **MrKaliman said:**
> Does this help you?

[http://ubuntuforums.org/showthread.php?t=1148203](http://ubuntuforums.org/showthread.php?t=1148203)


I think so. Do I need VLC (or another video player) installed on the machine I am ssh'ing from?

---

### Post by tgalati4 on 2013-02-17
Install mpd on the server and choose from one of several clients to control it from other machines:

mpc - command-line tool to interface MPD
mpd - Music Player Daemon
mpd-dbg - Music Player Daemon debugging symbols
mpd-sima - Automagically add titles to MPD playlist
mpdcon.app - MPD controller for GNUstep
mpdcron - add scrobbler, rating, play counts and other functionalities to MPD
mpdris - media player interface (MPRIS) client for MPD
mpdscribble - Last.fm reporting client for mpd
mpdscribble-dbg - Last.fm reporting client for mpd - debugger symbols
mpdtoys - small command line tools and toys for MPD

---

