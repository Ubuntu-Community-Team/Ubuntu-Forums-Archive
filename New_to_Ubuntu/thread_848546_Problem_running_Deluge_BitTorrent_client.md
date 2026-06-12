---
title: "Problem running Deluge BitTorrent client"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Dettweiler on 2008-07-03
I tried to run Deluge BitTorrent client for the first time and it worked. When I quit while the download still running and I tried to restart, it went nuts. This is what I get in terminal:

no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin WebUi
Initialising plugin DesiredRatio
Initialising plugin EventLogging
Initialising plugin WebSeed
Initialising plugin TorrentCreator
Initialising plugin TorrentPeers
Initialising plugin MoveTorrent
Initialising plugin BlocklistImport
Initialising plugin TorrentNotification
Initialising plugin FlexRSS
Initialising plugin NetworkGraph
Initialising plugin NetworkHealth
Initialising plugin Scheduler
Initialising plugin Search
Initialising plugin SpeedLimiter
Initialising plugin TorrentFiles
Applying preferences
Starting DHT...
No DHT file to resume
terminate called after throwing an instance of 'asio::system_error'
  what():  Permission denied
Aborted

Any idea, anyone? By the way, I am using deluge-torrent 0.5.9.3-1, downloaded from [www.getdeb.net](www.getdeb.net).

---

### Post by Efros on 2008-07-03
Deluge doesn't always close nicely when it crashes, try killall python. It should run again after that.

---

