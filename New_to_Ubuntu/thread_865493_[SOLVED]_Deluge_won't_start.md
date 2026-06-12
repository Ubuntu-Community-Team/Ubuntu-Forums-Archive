---
title: "[SOLVED] Deluge won't start"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by barney385 on 2008-07-20
I was using Deluge this morning to download, and I was tweaking it to make it download faster. Nothing was working, and I did a firewall command or two to open up some ports.

Probably a mistake.

Anyway, the command I used was: sudo ufw allow port; and sudo default allow

Now the GUI for Deluge won't even start.


Any ideas would be appreciated, though I think I screwed up my firewall settings or something. And tinkering isn't helping any.

Thanks

---

### Post by Joeb454 on 2008-07-20
Run deluge from a terminal, and see if it gives any errors :)

---

### Post by barney385 on 2008-07-20
Well, I have this one. Thanks for the quick reply BTW...

Starting DHT...
No DHT file to resume
terminate called after throwing an instance of 'asio::system_error'
  what():  Address already in use
Aborted

---

### Post by barney385 on 2008-07-20
I tried doing a reinstall also. I know I borked something. Maybe I should do a complete removal and installation?

---

### Post by barney385 on 2008-07-20
asio::system_error

Does that mean a port is busy?

I'm not a system admin!!

:smile:

This is what I get for tinkering I guess...

I googled the error and came up with nothing.


ETA: I went ahead and did a complete removal of firestarter and deluge.

I'm downloading Azereus right now.

I'm hoping it will use different ports than Deluge. I couldn't figure out what might be using the port Deluge wanted to use.

---

### Post by barney385 on 2008-07-20
I'm getting this error now...

no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin TorrentNotification
Initialising plugin FlexRSS
Initialising plugin DesiredRatio
Initialising plugin TorrentCreator
Initialising plugin Scheduler
Initialising plugin NetworkHealth
Initialising plugin Search
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin MoveTorrent
Initialising plugin WebUi
Initialising plugin NetworkGraph
Initialising plugin BlocklistImport
Initialising plugin WebSeed
Initialising plugin TorrentFiles
Initialising plugin SpeedLimiter
Applying preferences
Starting DHT...
No DHT file to resume
terminate called after throwing an instance of 'asio::system_error'
  what():  Address already in use
Aborted

---

### Post by suprfish on 2008-07-20
[https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/172603](https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/172603)

Did Deluge ever work for you?

---

### Post by barney385 on 2008-07-20
> **suprfish said:**
> [https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/172603](https://bugs.launchpad.net/ubuntu/+source/deluge-torrent/+bug/172603)

Did Deluge ever work for you?

Yes, until I messed with the firewall today. Is there a command that resets ufw to it's default state?

I know it's something I shouldn't have done.

---

### Post by suprfish on 2008-07-20
Try just disabling ufw (sudo ufw disable) or watch for anything interesting in the ufw log messages ("sudo iptables -L -n | grep LOG" after running deluge). You could also try reinstalling ufw (sudo apt-get reinstall ufw).

---

### Post by barney385 on 2008-07-21
> **suprfish said:**
> Try just disabling ufw (sudo ufw disable) or watch for anything interesting in the ufw log messages ("sudo iptables -L -n | grep LOG" after running deluge). You could also try reinstalling ufw (sudo apt-get reinstall ufw).

sudo apt-get wouldn't work for me, so I did:

sudo aptitude reinstall ufw

That worked for me...


Thanks suprfish!!

:smile:

I'll mark this thread solved

:guitar:

---

