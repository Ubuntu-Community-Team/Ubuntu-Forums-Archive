---
title: "Internal NTFS drive locks/disappears with Hardy &amp; Opera"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by MisterSanders on 2008-04-29
**Preface**: I've been sharing Opera 9.26  settings (history, passwords, open tabs, etc.) between XP and Ubuntu 7.10 (Gutsy) on a third partition (XP=1st, Ubuntu=2nd) thanks to jmmmp's work found at [http://my.opera.com/community/forums/findpost.pl?id=1579892](http://my.opera.com/community/forums/findpost.pl?id=1579892) (my hero!). All worked well. I even upgraded to Opera 9.5 with all working great. This weekend I upgraded to Ubuntu 8.04 (Hardy) and the fun stopped.

It seems that for whatever reason I can't fathom, Hardy no longer automounts NTFS partitions. I edited my fstab and got it automounting and Opera now loads up with the tabs that were open last time (from XP), with the right skin and everything.

**The Problem**: After a few seconds, or when I close Opera, I get a message reading Can't save file (or the likes) referring to opera6.adr (which is on my NTFS partition, named Docs). To add to the fun, the partition disappears.. kind of. It's still on my desktop, but double-clicking it gives me the message: Couldn't display "/media/Docs".
There is no application installed for this file type

From Places -> Removable Media -> Docs
Could not open location 'file:///media/Docs'
Generic error

Docs no longer shows up in my /media folder either. Typing ```
sudo mount -a
``` makes the desktop icon accessible (I can browse files and open them on the Docs partition), but it's still missing from my /media folder, and other apps can't access them. Of course Opera also can't relaunch because it depends on the Docs partition. This lasts until I reboot.

**Tried solution**: Maybe it's a permission issue? The owner for the Docs partition is listed as ROOT, so, in the command console, I typed 
```
sudo chown -R <my username> /media/Docs/Opera
```
(I didn't want to wait too long for it to do the entire drive, & without the 'sudo' it just told me file by file that it couldn't do it) then
```
 sudo chmod u+w /media/Docs/Opera
```
It seemed to work, but no go. I even 'sudo nautilus'ed and right-clicked my way to ownership and it didn't stick. It let me change things, but when I checked them with a normal Nautilus instance, ROOT was still the owner with everything greyed out.

I have Thunderbird's profile data on the same drive, and TB has no problem fetching and writing without problems. Any ideas would be greatly appreciated.

---

### Post by pastalavista on 2008-04-30
you might try ntfs-config

[sudo apt-get install ntfs-config] then Applications > System tools > NTFS Configuration Tool

My NTFS drives would unmount every time I rebooted, although I didn't have the ownership problem, they remounted easy enough just wouldn't stay mounted, but that simple tool did the trick for me.

---

### Post by MisterSanders on 2008-05-03
Thanks for the reply. I installed ntfs-config and it's made mounting another drive I have work with some mp3s that I have on it. Thanks!

I've managed to take care of the opera6.adr problem -- after running Opera in the terminal, it complained that it was missing java. After installing it no longer complains.

But my main problem is still in my way. After launching Opera, my "Docs" drive becomes inaccessible. If I don't run Opera during a session I have access to the drive, but once I start an instance of Opera I get the following after double-clicking the drive desktop icon:
```
**Couldn't display "/media/Docs".**
There is no application installed for this file type
```
and from the terminal:
```
/$ dir /media
cdrom  cdrom0  Docs  Downloaded  floppy  floppy0  Music  XPOS
/$ dir /media/Docs
dir: cannot access /media/Docs: Transport endpoint is not connected
```

Incidentally, although there's a desktop icon and the terminal above lists it as being in the /media folder, Nautilus doesn't show a Docs folder in /media. If anyone has an idea on what's going on, please let me know.

---

