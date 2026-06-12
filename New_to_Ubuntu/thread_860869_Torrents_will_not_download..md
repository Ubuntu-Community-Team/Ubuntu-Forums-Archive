---
title: "Torrents will not download."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by parakeets11 on 2008-07-16
I normally am able to get torrent to work on Vista and XP, but I got tired of the super slow speeds with Vista so I am trying to move to Linux.  But I can't seem to get torrents to download with Azureus or Transmisson torrent manager.  Step by step instructions would be most helpful.

Thanks and Cheers

---

### Post by cozmicharlie on 2008-07-16
We would need more info.  What specifically is the problem when you try and download a torrent?  In general downloading torrents in Linux is similar to Windows.  
[LIST=1]
[*]You click on the torrent in Firefox
[*]The download dialog comes up and it asks what you want to do (by default Firefox will open Transmission for torrents).  If you want to use Azurues just select Azurues.
[*]Then follow the dialog just as you do in Windows
[/LIST]
Are you able to open the programs (Transmission or Azureus)?
Are your ports open in your router?
Are you getting any error message?

---

### Post by parakeets11 on 2008-07-16
I am able to run the programs and the ports are open.  It says that it is unable to find the tracker and is unable to connect to peers.

---

### Post by maddog39 on 2008-07-16
Well some ISPs are actively disconnecting torrents (especially at peak times of the day, assuming your in the US). Also you should check to see if your lan IP has changed if you use DHCP because that will affect the port forward on the router.

---

### Post by RomeReactor on 2008-07-16
Hi. Depending on what exactly it is you want to download, you might be trying to connect to private trackers.

Try downloading [this Hardy image]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-desktop-amd64.iso.torrent") (or at least begin the download, to see if it connects properly), or [this Puppy Linux image]("http://linuxtracker.org/download.php?id=1a56baa7fca47625c5d99bca802d983507abd2c8&f=Puppy-4.00-k2.6.21.7-seamonkey.torrent") (only 88 MB).

Are you using FireStarter, UFW, or another firewall?

---

### Post by edwin2105z on 2008-07-16
when i used windows and dwnlded torrents i used frostwire and i know frost wire is avalible for ubuntu.

---

### Post by parakeets11 on 2008-07-20
Awesome it works.  Thanks all.

---

### Post by ejpyle on 2008-07-20
> **parakeets11 said:**
> I normally am able to get torrent to work on Vista and XP, but I got tired of the super slow speeds with Vista so I am trying to move to Linux.  But I can't seem to get torrents to download with Azureus or Transmisson torrent manager.  Step by step instructions would be most helpful.

Thanks and Cheers

U need to get Deluge.....it is great!!

---

### Post by barney385 on 2008-07-20
I get this error message when I try to start deluge from terminal:

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

### Post by wind_dragon on 2008-12-29
I am also having trouble using transmission. It was working fine a few hours ago but not I get this weird error when i try to download:

Failed to open the file /home/toure/.transmission/gtk/lock for writing:
Read-only file system

is there a fix to this i'm really new to ubuntu so any simplified help would be appreciated.

---

### Post by RomeReactor on 2008-12-29
Hi. Close Transmission and try deleting the **.transmission** folder hidden in your user folder:
```
rm -R ~/.transmission
```
Then open Transmission again and see if the problem persists.

NOTE: Doing this will reset all the information about everything you're currently downloading, but won't delete partially downloaded files, which you can resume if you still have the corresponding **.torrent** files.

---

### Post by wind_dragon on 2008-12-30
can't. it says its a read-only file. in fact all my files have magically turned into read-only.:confused:

---

### Post by ikki_72 on 2009-11-28
i had also the same problem. It has been a year and nobody got the slution to this problem?

---

