---
title: "Cross-device File Synchronization Solutions"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by REDace0 on 2008-10-08
I live on a campus, so I move between computers frequently, and it's convenient to keep a current copy of my course files on a USB Flash Drive (Patriot Xporter 8GB, for the curious). Some of the machines I use on campus are Windows and some run Fedora 9 instead (or both), so I needed the USB stick to be easily readable and writable under both. Failing that, I needed a live Ubuntu setup on it so I could get work done regardless of the platform. Here's what I set up (based on a guide [here]("http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/")):

8GB USB Flash Drive

~770MB partition for Live Hardy
~3000MB ext3 partition for persistent storage
~4000+MB (the rest) FAT32 partition for cross-platform access

Currently I have some primitive shell scripts that do 'cp -ruv' between the folders that need syncing on my USB drive and personal computers. This is not bad, but has its drawbacks. It relies on me to actually remember to do the syncing ](*,). And it doesn't sync when files are deleted. Which is going to be a big problem in the long-term.

From my experience with trying to make links between storage devices, I thought it might be a little tricky getting something to run on both my laptop and desktop to sync my folders on the USB to their counterparts on the hard disks. Both my laptop and desktop are running Dual-boot Hardy 8.4.1 and XP (laptop) or Vista (desktop).

Sorry for a bit of storytelling, anyone have ideas though?

---

### Post by .nedberg on 2008-10-08
For syncing I use unison, it also deletes files. But I think you would still have to run it manually every time...

---

### Post by REDace0 on 2008-10-08
Thanks. I'll give it a try, but I'll keep watching this for anything better.

---

### Post by roger_1960 on 2008-10-08
Hi

Depending how much you have to sync, have a look at [www.getdropbox.com](www.getdropbox.com)  It automatically syncs a special folder and its contents between linux, windows and mac OS, up to 2Gb free.  Very useful!

---

### Post by REDace0 on 2008-10-08
Wow. Dropbox seems to be a fantastic solution to part of my problem. Thank you! I'd like a solution that also works offline, since internet access isn't always guaranteed, but this will ensure that I can get to my files wherever such access is available. I wonder if it will run on a USB stick?

---

