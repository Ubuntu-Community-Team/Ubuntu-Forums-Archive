---
title: "dual boot on new hard drive"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by tuna_for_lunch on 2008-07-02
I've been meaning to move away from windows for some time and as I am replacing my hard drive, now seems a good time.

 Can anyone advise me on the best way to install dual boot Ubuntu/Windows XP on a new, unformated hard drive (120GB). For example, how should I partition and format the drive?

---

### Post by markjensen on 2008-07-02
Partition what you want to use for Windows, leaving space for Ubuntu (do not partition the "Linux" space, the installer will do that for you).

Install Windows.

Boot Ubuntu CD, and tell it to install itself in the "unused" space.  Let it put GRUB into the MBR.

Done.  :)

---

### Post by anderskitson on 2008-07-02
Well if its a new hardrive install xp first then ubuntu, installing xp 2nd usually causes boot problems that have to be modified afterwards, but if you install ubuntu 2nd dual boot is a piece of cake.

---

### Post by bumanie on 2008-07-02
Do as above, but I would suggest at the ubuntu partitioning stage to choose manual partitioning so that you can set up a separate /home partition. This way if something happens to the ubuntu filesystem, all your data will be safe. Under linux, it is mandatory to have a / partition and a swap partition. / should be 8-10gb, swap 1-2gb and /home as large as you like. If it is your first time installing ubuntu, the way suggested above is easier, but if something goes wrong with the / filesystem, you will lose your saved data as well. It is up to you which way you proceed. Manual partitioning is not hard, but is a bit daunting the first time.

---

### Post by markjensen on 2008-07-02
Oooh!  I didn't even think of this until now (I will blame the lapse on my inexperience dual-booting, since I have been 100% Linux for over 5 years).

Do a normal install of XP (which wants to take the whole drive, anyhow.

Do a "wubi" install of Ubuntu, which won't touch your partitions at all.  It creates a virtual ext3 filesystem as a file on your NTFS drive.

Even more simple, and less risk to partitioning error than having to manually create an XP partition of an arbitrary size (something that the XP installer is not capable of doing, to my knowledge).

I change my opinion to "wubi" at this point. :)

---

### Post by goforlinux on 2008-07-02
The easiest way is the following:
1. Throw in a copy of XP
2. Wait for it to go thru all of its nonsense
3. Parition whatever ammount of space you would like for the windows installation and then another for the Linux installation.
4. Wait for more windows crap to format/install
5.Once windows is installed on 1 parition get a live CD of Ubuntu
6. Throw it in install it on the empty partition you set aside for it
7. Configure GRUB to your desired settings
8. Have fun :)

---

