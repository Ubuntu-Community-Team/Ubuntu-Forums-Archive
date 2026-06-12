---
title: "Installing Drivers from CD/DVD"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by DefendTheHouse on 2013-01-15
I just built a new computer yesterday, and decided to try out Ubuntu on it (full installation, not a partition). Everything works fine, it installed correctly and everything. So I tried putting in the driver disk for he motherboard. It was detected, so I went into it and tried to run the setup.exe file. All it did was try to open Archive Manager and give me an error like "An error occurred when opening in Archive Manager" or something. Then I tried changing the permissions to allow it to be executed, but it doesn't let me. The reason why i can't tell you all these errors is because after a while, the files won't even show up on the disk. I tried other diver disks like the one from my sound card, but the files won't show up. I also don't have Internet connection on this computer yet (I need to use another driver disk to use wireless connection, but that disk has the same problem). How do I install these drivers? (and where did the files on the disks go?)

---

### Post by mikewhatever on 2013-01-15
Setup.exe is a Windows installation file - pretty much what vendors provide on CDs. Why do you think it needs to be installed on Ubuntu, especially since everything works?

---

### Post by DefendTheHouse on 2013-01-15
> **mikewhatever said:**
> Setup.exe is a Windows installation file - pretty much what vendors provide on CDs. Why do you think it needs to be installed on Ubuntu, especially since everything works?

I need to install drivers, and normally Linux downloads them automatically, right? Like I said, this computer doesn't have internet, so Linux can't download the drivers. In order to get internet connection, I need one of these disks to work.

---

### Post by 3rdalbum on 2013-01-15
> **DefendTheHouse said:**
> I need to install drivers, and normally Linux downloads them automatically, right? Like I said, this computer doesn't have internet, so Linux can't download the drivers. In order to get internet connection, I need one of these disks to work.

Linux comes with most drivers you'll need. What makes you think you need to install drivers? Is there something that's not working?

Typically, the only driver you'd want to install on Linux is a graphics card driver, because the default ones on Linux don't have as good performance as the vendor-supplied ones. You're correct in saying that Ubuntu can automatically download them when you have an internet connection, but the better idea is to get an internet connection as you'd have a much better time anyway.

The CD that comes with your computer won't be any use. The drivers contained on it are for Windows, not Linux. .exe files are for Windows and you can't use drivers from these files on Linux.

---

### Post by mikewhatever on 2013-01-15
> **DefendTheHouse said:**
> I need to install drivers, and normally Linux downloads them automatically, right? Like I said, this computer doesn't have internet, so Linux can't download the drivers. In order to get internet connection, I need one of these disks to work.

In most cases, you don't need to install drivers, and no, "Linux [does not download] them automatically".
If you provide info about the networking hardware, we can try helping you, but, let me say it again, there is not way to make "one of these disks to work". They are not made for Ubuntu, and thus will not work on Ubuntu.

---

### Post by squakie on 2013-01-15
We've seen this ageless times on the forum - for all newbies:  the installation disk for your motherboard and other hardware, unless it specifically says Linux, was written only for Windows.  You do not need, and indeed can not, install anything from those disks.  Such things as chipset drivers for Windows are automatically done in Linux.  Things like video, sound and wireless drivers for Windows are useless to Linux.

So, what we need to know from anyone who thinks they need these:

Are you having a specific problem?  If so, please post exactly what the problem is.

If you just think you "have to because I had to in Windows", don't bother putting the disk in your drive.

---

