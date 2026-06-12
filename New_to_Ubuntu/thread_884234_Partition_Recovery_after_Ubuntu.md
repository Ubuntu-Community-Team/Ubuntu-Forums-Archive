---
title: "Partition Recovery after Ubuntu"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by neolifeforever on 2008-08-08
Hey guys,
im a total noob at OS troubleshooting so plz be gentle and help out;)

i installed Ubuntu on one of my PC's 4 partitions and loved it!
soon after i had to install XP on another partition.
i need to know two things
1) how do i activate dual OS access when my PC boots?
2) how can i access the partiton that Ubuntu is installed in from XP as it has suddenly disappeared from My Computer options?

I know this problem will be a breeze for you guys so just help me out here.
Thanks.
--------------
PC Config (if needed)

Intel Original 915GAV Motherboard
Intel Pentium 4, 3Ghz
512 MB RAM
160GB HDD (in 4 partitions)
Currently running WinXP
And all the other goodies that an assembled PC has to offer.

---

### Post by Victormd on 2008-08-08
To setup dual boot you're going to need to use a program called super-grub. You can download it [here]("http://www.supergrubdisk.org/"). You can read a bit more about it [here]("http://www.supergrubdisk.org/wiki/Boot_Problems").

Normally, the suggested order of installation of the OSs is windows then ubuntu. This is because windows does not recognize anything other than microsoft OSs whereas linux recognizes all OSs installed on your computer. That leads to your second question. Since windows does not recognize anything that's not microsoft, it doesn't recognize Ubuntu's ext3 file system and therefore can't read it. There are programs you can install under windows that will grant you access you your ubuntu partition, such as [this]("http://www.diskinternals.com/linux-reader/").

Post back if you run into any problems getting your dual-boot to work.

---

