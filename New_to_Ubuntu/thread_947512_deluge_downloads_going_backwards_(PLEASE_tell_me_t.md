---
title: "deluge downloads going backwards (PLEASE tell me this isn't happening!)"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Gonz_91 on 2008-10-14
Hi


I was doing some big, important bittorrenting on deluge (about 60-70 gigs), and after some updates needed to reboot, and so I did.

After rebooting, I opened deluge, wich complained no having enough space for the huge download, because it was downloading for my secondary partition, which wasn't mounted. So I mount it, force recheck, and it says I've only downloaded 6%, when just before rebooting was at 20%! How the heck is this possible? Is in any way possible to recover the "wasted" download?

plz help.... thanks

---

### Post by Gonz_91 on 2008-10-14
Bump



Really? No ideas??

:(

---

### Post by detroit/zero on 2008-10-14
I used to notice the same behavior in deluge. I'd be at, say 50 or 60% of a download, shut Deluge down for whatever reason, and the next time I ran it I would be at 6 or 10%.

I don't know why Deluge does this, but I can tell you how to avoid it happening.

I have deluge always open on one of my desktops. I also have the Deluge icon set to appear in my panel because of it's handy features (setting up/download speed, etc..)

Before I'm about to shut Deluge down or before I have to reboot my computer for any reason, I made the habit of right-clicking the Deluge icon in the panel and selecting "Pause all", which halts all downloads and (I assume) writes whatever data is left in memory to the disk. Then the next time I load Deluge, once the window appears, it's just a matter of right-clicking the icon again and selecting "Resume all". Everything picks up where it left off.

You could just as easily select all your torrents in the Deluge window and use the Pause/Resume buttons in the toolbar, but however you choose to do it, the important things are:


[LIST]
[*]Pause all before shutting down Deluge
[*]Resume all when you start it back up
[/LIST]
Someone may come by with some technical know-how and tell you to open this file, alter this configuration, re-compile from source, download extra binaries, go on a dependency hunt, blah blah blah.. More power to them (and you) if that's the way you see to tackle the problem.

I'm all about simplicity, and I see my method as a simple solution to a simple problem.

Hope I helped.

---

### Post by forger on 2008-10-14
1) version of deluge?
2) post the output of command in terminal:
```
apt-cache policy deluge-torrent
```
3) you might have some more luck at their IRC channel, [#deluge at freenode irc network]("irc://chat.freenode.net/#deluge")

---

### Post by o.besner on 2008-10-14
[http://deluge-torrent.org/faq.php](http://deluge-torrent.org/faq.php)

In the FAQ, there are indications on how to build Deluge from the SVN (subversion - the development version - cutting edge, it has many names :) )

I've been using it for a few weeks now. It's stable, and much more recent than the one in Synaptic. 

Most recent version is 1.0.2 (stable), and was released october 11th. SVN is up to last night. Latest in Ubuntu repository is 0.5.8.9 !!!!! It's old !

---

### Post by forger on 2008-10-14
> **o.besner said:**
> In the FAQ, there are indications on how to build Deluge from the SVN (subversion - the development version - cutting edge, it has many names :) )


In case you were replying to my post, apt-cache can show the current version of deluge used :P

I'm using 1.0.0, version 1.0.1 was crashing, I'll finish up my downloads and check out the new one

---

### Post by Gonz_91 on 2008-10-14
> **detroit/zero said:**
> I used to notice the same behavior in deluge. I'd be at, say 50 or 60% of a download, shut Deluge down for whatever reason, and the next time I ran it I would be at 6 or 10%.

I don't know why Deluge does this, but I can tell you how to avoid it happening.

I have deluge always open on one of my desktops. I also have the Deluge icon set to appear in my panel because of it's handy features (setting up/download speed, etc..)

Before I'm about to shut Deluge down or before I have to reboot my computer for any reason, I made the habit of right-clicking the Deluge icon in the panel and selecting "Pause all", which halts all downloads and (I assume) writes whatever data is left in memory to the disk. Then the next time I load Deluge, once the window appears, it's just a matter of right-clicking the icon again and selecting "Resume all". Everything picks up where it left off.

You could just as easily select all your torrents in the Deluge window and use the Pause/Resume buttons in the toolbar, but however you choose to do it, the important things are:


[LIST]
[*]Pause all before shutting down Deluge
[*]Resume all when you start it back up
[/LIST]
Someone may come by with some technical know-how and tell you to open this file, alter this configuration, re-compile from source, download extra binaries, go on a dependency hunt, blah blah blah.. More power to them (and you) if that's the way you see to tackle the problem.

I'm all about simplicity, and I see my method as a simple solution to a simple problem.

Hope I helped.

I like keeping it simple, too, so I«ll use your tip for now ;)

```
apt-cache policy deluge-torrent
```
deluge-torrent:
  Installed: 0.5.8.9-0ubuntu1
  Candidate: 0.5.8.9-0ubuntu1
  Version table:
 *** 0.5.8.9-0ubuntu1 0
        500 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status


I'm using 5.8 because my downloads in 1.0 were as slow as possible, like 1kB/sec, and now the same are ate 300-600kB/sec.

---

### Post by mvoncken on 2008-10-17
Force-recheck discards incomplete pieces : 
[http://dev.deluge-torrent.org/wiki/Faq#IlostdataonforcerecheckWhy](http://dev.deluge-torrent.org/wiki/Faq#IlostdataonforcerecheckWhy)

If it's a fat32 drive the 1.03 fat32 bugfix could explain your force-recheck.
[http://dev.deluge-torrent.org/browser/branches/1.0.0_RC/ChangeLog](http://dev.deluge-torrent.org/browser/branches/1.0.0_RC/ChangeLog)

---

