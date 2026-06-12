---
title: "Thinking of installing Ubuntu"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by mailmatic on 2013-03-05
I am would like to try Ubuntu on my Windows home premium machine ](*,). My primary hard drive, C, is 80GB of which 27GB is used and 53GB is free. Drive D which I use for back ups is 150GB, 20GB used and 130GB free. Can I install and run Ubuntu from my D drive. If not then what are my options.
Kind regards.
Tom

---

### Post by JLeon85 on 2013-03-05
Is your D drive an internal hard drive or external? Either way, the 27 GB is plenty to install Ubuntu on, and then you can mount the D drive in Ubuntu's file manager to store your files.

---

### Post by Impavidus on 2013-03-05
You can make a proper dual boot of that. Shrink your D partition to make about 30GB unallocated space (doesn't come very precise) using windows tools and install ubuntu alongside it.

---

### Post by Frogs Hair on 2013-03-05
Consider making a cd/dvd and trying the live Ubuntu session. It will be slower than an installation but at least you will find out if it works on your hardware and if you like it. The link suggests other ways to try Ubuntu as well as the live session.  [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by Mark Phelps on 2013-03-05
> **mailmatic said:**
> I am would like to try Ubuntu on my Windows home premium machine ](*,). My primary hard drive, C, is 80GB of which 27GB is used and 53GB is free. Do NOT mess with this partition (what MS calls a "drive").  This contains your Windows OS and if you mess with it, either using Gparted, or the Ubuntu installer, you risk corrupting it and rendering Windows unbootable.
> Drive D which I use for back ups is 150GB, 20GB used and 130GB free. Can I install and run Ubuntu from my D drive.Well, you CAN install to the "D" partition -- but since Ubuntu requires a Linux filesystem (which your "D" partition is not), the only way you can do that is using Wubi -- which personally, I would not recommend.

Best approach is to boot from a LiveCD or LiveUSB , select the Try Ubuntu option, and see how well it works.  It will be slow, because it's running from a virtual drive created in memory and accessing the disk or USB drive often, but that will at least let you see what Ubuntu looks like and how well it recognizes your hardware and installs the proper drivers.

Also, I would strongly recommend, that even if you so decide to install Ubuntu, that for the time being, you do that in dual-boot mode -- with Ubuntu on its own partition.  It will take time to move entirely away from MS Windows, even if that is your goal, and in the meantime you can take your time addressing any problems that develop.

And, do NOT use the Ubuntu installer to shrink Windows partitions to make room for installing Ubuntu.  That risks corrupting Windows.

---

### Post by gordintoronto on 2013-03-06
I hope you will enjoy Linux.

People can give better help when you are very specific. For example, Windows 7 Home Premium or XP? Brand and model of computer? How old is it?

If it's Windows 7, I suggest using Windows tools: first, defrag the D: drive, then shrink it. With any luck, you will get at least 40 GB of free space, and that is plenty to try Linux. A potential complicating factor: if your computer has four primary partitions (as is the case for many HP laptops) that will complicate your life.

You will find Linux different from Windows. First difference: C: and D: were invented by Microsoft, and they are not used by the rest of the world. Second big difference: in Linux, Desktop and desktop are completely different. Windows has trained us very badly about upper and lower case.

Before you do anything, backup your data. Then, backup your data. Sorry if this is tiresome: the next step is to backup your data. Now you are ready to look at Linux.

---

### Post by nwalkey on 2013-03-06
> And, do NOT use the Ubuntu installer to shrink Windows partitions to  make room for installing Ubuntu.  That risks corrupting Windows.

I agree with this but at the same time I do not. If you are new to linux and don't want to futz around too much, letting the ubuntu installer do the resize for you will be the easist option. I would suggest that you make a good backup first or you do risk corrupting your drive. I have used both gparted and/or the ubuntu installer several times to repartition nfts(windows) drives with no negative effect on the windows installation. It is easier and less risky to install both windows and ubuntu from scratch though. Definitely backup to somewhere and give the ubuntu install dvd/usb a go. Good luck with however you install. (You could install wubi but you'll end up wanting to do a proper ubuntu install after anyway and then you have to go through the whole process again. :sad: )

---

