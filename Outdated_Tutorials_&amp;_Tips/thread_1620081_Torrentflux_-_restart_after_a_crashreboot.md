---
title: "Torrentflux - restart after a crash/reboot"
date: 2010-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Jethro_uk on 2010-11-12
If you are forced to reboot, or have a crash, and Torrentflux was running, you may get into a state where you cannot resume the torrents that were running. You will see them marked as "INCOMPLETE", in a stopped state. Trying to restart them moves them to "QUEUED" and the eta as "Waiting" ... and then the torrent goes back to a stopped state.

To fix this, go to the download directory, set up in Admin, and look for a .torrents directory. In there, for your interrupted torrents, you will see a file <torrent>.stat

Delete this file, logout and login to torrentflux and you will see the torrents now set to "NEW". When you run the torrents, they will go through "checking existing data" to running again.

---

### Post by Sparky42 on 2011-08-03
Thanks.  I've been wondering how to do this for a long time.  I had been simply deleting ALL of the files and restarting the complete torrent.

---

