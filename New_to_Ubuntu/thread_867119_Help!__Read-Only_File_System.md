---
title: "Help!  Read-Only File System"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by evlutn on 2008-07-22
Help Me Ubuntu Community!

Yesterday, my girlfriend accidentally turned off our laptop in the middle of an update and when it restarted it said it could not login to X.  I ran sudo dpkg-reconfigure xserver-xorg but it freezes.  When I go the the terminal on recovery mode, it keeps saying that the file system is read-only.  I ran e2fsck and fsck using the live CD and no errors are reported.  I also ran the file system check on the partition manager on the live CD and it didn't help either.

I have been able to fix the problems I've encountered since I've been using Ubuntu but I haven't found an answer to this problem.  How can I fix this?  I have a few important things on the drive that I need.  Has anyone had this same problem and what did you do to fix it?

Thanks for your help,

Angel
Loyal User of Ubuntu since May 2006

---

### Post by Potatoj316 on 2008-07-22
if you use a live cd you probably can mount the drive and copy the needed files to some removable storage.  have you tried
```
sudo dpkg --configure -a
```

---

### Post by bumanie on 2008-07-22
sudo dpkg-reconfigure xserver-xorg has been updated to the easier to remember > xfixTry that instead - it only applies to hardy, previous versions use the former command you already used. Or see if there are broken packages.

---

### Post by evlutn on 2008-07-22
Potatoj316, my first reaction was to just copy the files I need and just reinstall the OS but when I tried, it says I don't have permission to open the home folder and it has a locked icon on it.  I forgot to say but I did also try sudo dpkg --configure -a as well as sudo apt-get -f install and neither have helped.

Bumaine, I didn't know anything about xfix, so I'll give that a shot and see if it works.

Anything else I can try, just in case xfix doesn't work?

By the way, when I ran sudo aptitude safe-upgrade and sudo dhclient wlan0, it keeps telling me that nothing is being permanently done/written because the file system is read-only.

---

### Post by bumanie on 2008-07-22
Got no idea if it'll work or not - was just letting you know that xfix has superceeded sudo dpkg-reconfigure xserver-xorg. I guess you will have to run xfix as root. I doubt it will fix the filesystem.

---

### Post by evlutn on 2008-07-23
Hey all,

So I didn't really fix the problem but I was able to get the files I needed by installing Hardy 8.04.1 on the unused space on the hard-drive.  That gave me access to the files I needed.  I gave it a shot to see if it would work and it did, though I still can't access that portion of the drive if I try to boot into it but so what.  I got my files and that's all I needed and I reinstalled the OS.

Angel

---

