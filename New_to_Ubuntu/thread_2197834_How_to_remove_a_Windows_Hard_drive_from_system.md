---
title: "How to remove a Windows Hard drive from system"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by kwjorders on 2014-01-05
Hey I just dual booted Ubuntu with window xp and I can see all my NTFS Windows hard drive this is turning into a little problem because I'm accidently installing software on them that I'm assuming will not work because of this.  I don't want to delete the data on these drive just want them to be unseen and untoachable from the linux side of my dual boot.  Any help would be greatly appreciated!!!
-Thanks

---

### Post by flyfisherbryan on 2014-01-05
I would think that anything installed from within Ubuntu will be on the Ubuntu drive (or partition).  Nothing has ever installed on my Widows partition in my dual boot setup, although I have moved some Ubuntu files there to save space on the Ubuntu drive.  Please give us more information on what you are doing.

---

### Post by deadflowr on 2014-01-05
Even though you see them, the NTFS partitions aren't mounted(unless you click on them to be)
So, don't click on them in the file manager and nothing will happen to them.

---

### Post by kwjorders on 2014-01-05
I'm trying to run a old game called X-wing alliance in Wine with some newer updated graphics and more ships to pilot as an add on that I downloaded and installed from a fan community.  The game is old and installed to my C drive and I had to redirect it to the file system.  The upgrade package installs itself with no choice of hard drive selection.  The game crashes every time I run it with the upgrade so I was wondering if the upgrade package was installing on my windows drive and that was the reason it is crashing in wine.  The upgrade package gives you no choice of which drive it installs to.
-Thanks

---

### Post by deadflowr on 2014-01-05
> **kwjorders said:**
> I'm trying to run a old game called X-wing alliance in Wine with some newer updated graphics and more ships to pilot as an add on that I downloaded and installed from a fan community.  The game is old and installed to my C drive and I had to redirect it to the file system.  The upgrade package installs itself with no choice of hard drive selection.  The game crashes every time I run it with the upgrade so I was wondering if the upgrade package was installing on my windows drive and that was the reason it is crashing in wine.  The upgrade package gives you no choice of which drive it installs to.
-Thanks

Sounds like a typical wine problem.
Programs on wine are hit and miss.

wine creates a fake c drive in the folder .wine, which is hidden in your home folder(ctrl +h, will show it in your file manager)
It's completely independent of the windows C drive on the Installed windows side.
You would have to access that through the ubuntu's drive (the z drive in wine) and then the windows drive would have to be mounted, and in the ubuntu drive it would be in the /media directory.
Not exactly easy access.

---

