---
title: "AutoShutdown on torrent complete"
date: 2013-02-19
forum: Programming Talk
---

### Post by c2tarun on 2013-02-19
I used Kubuntu for a while and its default torrent app, KTorrent has a feature of shutting down my machine on completion of torrent download.
 
My current torrent client is Deluge and installing KTorrent is something I don't want to do.
Is there any way of writing a script which monitors and shutsdown the computer on completion of torrent download?

---

### Post by Vaphell on 2013-02-19
AutoShutdown plugin?
[http://dev.deluge-torrent.org/wiki/Plugins](http://dev.deluge-torrent.org/wiki/Plugins)
[http://forum.deluge-torrent.org/viewtopic.php?f=9&t=41165](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=41165)

---

### Post by ofnuts on 2013-02-19
> **c2tarun said:**
> I used Kubuntu for a while and its default torrent app, KTorrent has a feature of shutting down my machine on completion of torrent download.
 
My current torrent client is Deluge and installing KTorrent is something I don't want to do.
Is there any way of writing a script which monitors and shutsdown the computer on completion of torrent download?
KShutdown can shutdown the system when an application terminates, so if you can make Deluge exit when finished you are in business...

---

### Post by c2tarun on 2013-02-20
> **Vaphell said:**
> AutoShutdown plugin?
[http://dev.deluge-torrent.org/wiki/Plugins](http://dev.deluge-torrent.org/wiki/Plugins)
[http://forum.deluge-torrent.org/viewtopic.php?f=9&t=41165](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=41165)
 
Thanks for autoshutdown plugin, but don't know why Deluge is crashing again and again after 15-20 mins of download. :( 
 
> **ofnuts said:**
> KShutdown can shutdown the system when an application terminates, so if you can make Deluge exit when finished you are in business...
 
KShtudown is again asking for 46MBs of download and will take somewhere around 96MBs, its little too much. :(
 
 
I tried qtbittorrent, its great and have the feature of autoshutdown. But I am still keeping this thread as open, if someone with solution might take a look and reply.

---

### Post by Vaphell on 2013-02-20
do you use separate 'temp' and 'completed' folders? in case of such a setup, you would be able to use a trivial script to check if the temp dir is empty and issue *shutdown -P* if the condition is met.

---

### Post by c2tarun on 2013-02-21
> **Vaphell said:**
> do you use separate 'temp' and 'completed' folders? in case of such a setup, you would be able to use a trivial script to check if the temp dir is empty and issue *shutdown -P* if the condition is met.
 
 
Hmm... this can be tried. I'll go home and try it. :) lets hope this works.

---

