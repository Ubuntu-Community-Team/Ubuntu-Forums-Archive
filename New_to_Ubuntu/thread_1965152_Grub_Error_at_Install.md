---
title: "Grub Error at Install"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by CoDeHacKer on 2012-04-25
Hi, 

I downloaded Ubuntu 11.10 32bit and installed it on my wifes computer.  I liked it so much,
 I decided to put it on mine.  I have a HP DV7 with a I7 Intel processor, and I believe I
remember reading that it was ok to install 32bit on a 64bit system.

I deleted all the partitions on the HDD and set up /boot, /, /Home, /user, and a swap file 
from the install cd.  When it got to grub it gave an error and said it couldn't write it to 
the disk, I tried formatting the drive several different ways, and each time I get the same 
error, and it says something about a grub bug, and gathers information to send to Ubuntu, 
and sends me to launchpad.  I get lost there.   On the last attempt I chose continue 
install without a boot loader.  I wonder if there is a way to get grub installed, it seems I 
read somewhere about a 64 bit bug, I can't remember I've done a lot of reading.

I'm wondering if I just download and install the 64bit version will it work ? 

Thanks

---

### Post by Peter09 on 2012-04-25
Have you just tried using the automated install - without setting up partitions manually?

---

### Post by CoDeHacKer on 2012-04-25
No I have not tried this, just format the drive ext4 and do the install that way ?

---

### Post by Peter09 on 2012-04-25
No need to do anything at the disk level, just click install using entire disk, (if thats what you want to do). It will delete and format your drive for you.

---

### Post by ravinfy on 2012-04-25
Since you are willing to wipe off your existing OS, I`d follow Peter09`s advice and let Ubuntu install using the entire disk. 
NOTE: I am assuming you are ok to get rid of your existing Windows OS since you said you deleted all the partitions.

With a powerful Processor like an i7, it sure does sound like a good idea to use the 64-bit OS. Not that the performance is noticeably better, but, with a 64 bit OS, you are using your hardware better - Google to learn more :) 

Ravi

---

### Post by oldfred on 2012-04-25
With new very large hard drives, if the / (root) partition is too large it can cause problems. But if you have a separate /boot that should not be an issue. I do not normally suggest extra partitions other than /home, but if drive is very large just a full install to the entire drive may only create a large / and swap.

I think Herman only has /, he now uses a swap file rather than a swap partition.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

With an i7 you probably have at least 4GB of RAM and should really have the 64bit version. 

Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

