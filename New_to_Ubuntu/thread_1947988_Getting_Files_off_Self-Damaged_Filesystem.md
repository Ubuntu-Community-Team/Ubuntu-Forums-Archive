---
title: "Getting Files off Self-Damaged Filesystem"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by chipslinger on 2012-03-27
I have done something so lame that I probably don't deserve to win.....

I had been running a Ubuntu v9 system with a 4 disk raid as a home fileserver for a few years. Although I never bothered to update it to a later version, I did apply updates regularly. I had had some problems with file attributes not being set correctly so I went in and had fixed some samba settings that meant that certain users couldn't access certain files. That worked. Then I went one step too far.

There were some files that had the wrong attributes. Instead of going in to the individual directories and setting them correctly, I just went into my user directory and set all files to attribute 666. Uh. Now the system boots, but can't run any useful programs. I only had one user set up and I did't set up a root password. Now the system gets to the password screen, but immediately logs me out.

Most of the files on the system are backed up, but some camp photos from one of my kids weren't. I'd like to see if I can recover them.

What would be a good strategy for accessing these files? Is there something I can do with a recovery disk, or by mounting the disks on a different machine?

Any suggestions would be greatly appreciated.

---

### Post by TeoBigusGeekus on 2012-03-27
Just boot with a live cd and get all the stuff you care for from the system.

---

### Post by chipslinger on 2012-03-27
I have tried this booting with a Ubuntu Live CD, but what do I have to do to mount the drive array?

I look in \dev\ and a bunch of device show up, but if I try to mount anything (and I'm not exactly sure what I should be mounting), the system replies "/etc/fstab : no such file or directory."

Thanks for helping

---

### Post by TeoBigusGeekus on 2012-03-27
Oops, raid...
Sorry mate, I've no experience with that.
Could [this]("http://www.jeffsplace.net/node/14") be of any help?

---

### Post by chipslinger on 2012-03-27
I think you're on the right track. It doesn't find the drives but I'm pretty sure you're pointing me in the right direction

Does the Live CD have to be for the specific computer for this to work? I'm booting with much more recently created CD....

---

### Post by TeoBigusGeekus on 2012-03-27
Any live cd would do, even a none ubuntu one, as long as it takes you to a working system.

---

