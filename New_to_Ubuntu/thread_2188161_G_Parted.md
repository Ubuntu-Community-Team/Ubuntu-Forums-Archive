---
title: "G Parted"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by wolfen10862 on 2013-11-15
OK guys I can NOT get a windows game to run on Ubuntu with descent fps, I have done everything I am supposed to do so I assume its the Linux graphics drivers, well here's the problem, I DO NOT want to use anything except the Nvidia drivers that come with Ubuntu because they work perfectly on Ubuntu
So......
Since I DO NOT want to reformat my hard drive and install windows first then Ubuntu simply because I don;t want to remove Ubuntu, if I use G parted to create a new partition will I be able to install windows Vista on the new partition without removing Ubuntu?


Only reason I am asking is because I had windows for the past 20 years, and I have had Linux for thee weeks, it took me 20 years to operate windows worth a darn, it took me three days to learn Ubuntu, Yes I AM still terminal phobic, but I am trying to learn that too

---

### Post by monkeybrain20122 on 2013-11-15
You can try the up to date driver from either xorg-edgers or xswat ppa.

---

### Post by Impavidus on 2013-11-15
Yes, you can install Windows without destroying Ubuntu: [https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

Instead of the magic with the dd commands you can run [boot-repair](https://help.ubuntu.com/community/Boot-Repair) from the live disk to recover the Linux boot loader. Also, I've read the advice to instruct the Windows installer to format the ntfs partitions you made for it.

Make some backups nonetheless.

---

### Post by wolfen10862 on 2013-11-16
Thanks, Its not a big deal if I totally loose Ubuntu because it takes e a grand total of three hours to get everything back vs three years with windows, but I only need windows for one thing, and that is only until the local school system fixes their computers so my wife can check he member section

---

### Post by wolfen10862 on 2013-11-16
Just an update, I read all over the internet that windows has ti be in stalled first, and on another site it said that installing windows is easier since it steals the entire hard drive, the one thing I noticed about Ubuntu last time i tried installing both s that if I select run alongside windows Linux splits my hard drive in half, which is exactly what I ant to do, so....since I am not exactly the best at Linux yet I'm gonna use the Seagate disk utility and slick the entire drive, then install windows, then install Ubuntu along side windows that way I can be up and running tomorrow for sure.
Basically I have every app that I have downloaded write down and I can get them all back in about the time it will take me to drink a cup of coffee LOL
GOD Linux is so much better than windows, I can;t figure out why windows is still in buisness

---

### Post by wolfen10862 on 2013-11-19
OK last post on this thread, I have given up on windows, I know that makes a lot of people here happy :) I can NOT get windows to install no matter what I do, its not my computer or my hard drive, its the Vista disk itself, and the old XP disk I have, every single time both o/s's start installing, then go straight to a BSOD and dump everything, reboot and start the cycle all over again, so I guess I don't need G parted to make a partition, I just need it to maintain the 500 gig Ubuntu has for use LOL

---

### Post by oldfred on 2013-11-19
While most say Windows must be first, it can be any primary partition (sda1 thru sda4) and must have boot flag. But also best if not after your extended partition as that sometimes does cause issues.

So you have to use gparted to create a NTFS partition that is primary and has boot flag. From gparted it will be a XP type NTFS partition, but the install of Vista or newer will change the type to be correct. The difference is the PBR or partition boot sector must specify the Windows boot loader or ntldr for XP or bootmgr for Vista or newer.
Some have had to reformat the XP NTFS partition as part of the install.

---

