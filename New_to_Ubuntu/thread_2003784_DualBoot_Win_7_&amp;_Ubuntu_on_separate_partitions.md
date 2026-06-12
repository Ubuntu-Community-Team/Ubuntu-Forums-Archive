---
title: "DualBoot Win 7 &amp; Ubuntu on separate partitions"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by marcus121 on 2012-06-14
Hi,

so I got this problem, just reinstalled windows and I have created another partition for Ubuntu (something like [this](http://prntscr.com/alc0j), K drive is ext hdd) and I want to install Ubuntu on E drive. I have burned Ubuntu on DVD and  I know how to boot it up but the next part is where I need Your help. So, all ubuntu files should be ONLY on that E drive and nowhere else, if its possible. 

I'm new to linux so if its not problem I need the whole installing procedure.

  Thank you.

---

### Post by SDX0 on 2012-06-14
During your installation of Ubuntu, you'll want to assign three partitions for Ubuntu's use.  Their names are  **/**, **/home**, and **swap**.  Thus, the first thing you'll want to do is split up E:, be it through Windows' partition manager or Linux's partition manager, whichever is more comfortable for you.

Most Linux distros including Ubuntu work best with at least three partitions to themselves: one for /home, where your personal files are kept; one for swap, which is basically the Linux version of Windows' pagefile; and /, where the rest of the OS is stored.  These three parts of the OS are best kept apart for these reasons:

/home is where your personal files are kept.  Using a separate partition for /home protects it from the rest of the OS should any part of Ubuntu become corrupted.  It also makes switching between Linux distros easier in the future as you are able to reuse your /home partition with almost any distro.

The swap partition acts much in the same way as Windows' pagefile.sys.  It's what Ubuntu will use should you run out of RAM.  It's also used to save the state of your RAM to your hard drive if you decide to make your computer hibernate.  It's kept apart from /home and / because it needs to be formatted differently.

/ is the core of Ubuntu.  The OS itself goes here.

How much space you allot to each partition depends on how you want to use Ubuntu.  For a standard desktop install I would suggest a 12-15 GB /, for swap I multiply the amount of RAM available to the computer by 1.5 and allot that many gigabytes for swap, but that's my preference.  The rest goes to /home.

If D: is where you plan to put your personal files, you'll only need to split E: up into / and swap, in which case use the formula for swap and dump the rest into /.

After partitioning your hard drive again, booting into the Ubuntu DVD, and after the Ubuntu installation program checks your Internet connection  and makes sure you have enough space on your hard drive, it will ask you  how you want Ubuntu installed on your hard drive.  The option you want  is the one on the bottom, "Choose how to partition drive," or something along  those lines.  After you select that, you'll be shown a window much like  this one: 

[IMG]http://radu.cotescu.com/uploads/wpuploads/2009/06/Ubuntu-partitions.png[/IMG]

From here you can choose which partitions Ubuntu will use for which directories.  You'll notice that the partitions are no longer labeled C:, D:, or E:.  This is because Ubuntu uses /sda/sda1 and so on for partitions.  To change how a partition will be used by Ubuntu, click on the partition and then click "Edit partition".  A prompt will come up asking how to use the partition and what filesystem to use.  I suggest:

/ - ext3 or ext4
/home - ext4
swap - swap

to start unless you want to be able to access your personal files from your Windows install.  In that case change /home to NTFS or FAT32.

After you've set up how Ubuntu should use your hard drives, the rest is just usernames, passwords, timezones, and other simple questions.

Welcome to Ubuntu, Marcus, and I'm sorry if I've left anything out.

---

### Post by marcus121 on 2012-06-15
I have sucedeed at this, thank You for your help.

One thing, it wasn't possible to choose ntfs file system for /home dir so I had to put it ext3(or ext4 not sure right now, and i'm running windows) and i have another data partition for windows which is ntfs, so i can copy files from ubuntu to this partition, right?


Thank You very much for your help, greetings :D

---

### Post by LiamOS on 2012-06-15
You should be able to copy to a NTFS partition from Ubuntu, but if not, consider using a FAT32 partition, as FAT32 is easily used by Ubuntu and Windows.

---

