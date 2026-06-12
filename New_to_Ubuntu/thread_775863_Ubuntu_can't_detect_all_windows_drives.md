---
title: "Ubuntu can't detect all windows drives"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Adribhel on 2008-04-30
Hi.

Ubuntu only seem to find one of my windows hard drives, the main Windows one (C:\). But everything I actually need is on a hard drive that linux won't detect. (Actually the one where Linux is installed :S )

Any tips?

Thanks :)

---

### Post by oedha on 2008-04-30
what is the output of : sudo fdisk -lu (type in terminal)
make sure your windows has shutdown properly

---

### Post by Adribhel on 2008-04-30
Here is what i got from running the command:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1b0d1147

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976770143   488385040+   7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04d604d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   143235539    71617738+   7  HPFS/NTFS


Edit: It's the 500GB one I want to access.

---

### Post by oedha on 2008-04-30
how did you install your linux ? 
i didnt see the linux partition
mmmm....how if you install : sudo apt-get install ntfs-config
then find ntfs configuration tools on the menu....mark the 2 boxes there

---

### Post by Adribhel on 2008-04-30
Linux was installed by downloading Iso-image, mounting it in deamontools, and running the installation. After the reboot Ubuntu installed itself and rebooted again.

I did however had problems booting Ubuntu. By some reason, I had to enter Windows and change some numbers in a text file. (Running two disks caused a problem, I can find out exactly what i did)

Quick question: How do I log in as root? I need to do so in order to enter ntfs-config.

Thanks for help so far :)

---

### Post by oedha on 2008-04-30
sudo = super user do
in graphic mode...when you run ntfs conf tool....it will ask your password

---

### Post by Adribhel on 2008-04-30
Never mind, managed to open the ntfs configuration tool and checked the two boxes, didn't solve it though.

---

### Post by oedha on 2008-04-30
ups...sorry then.....it usually work :(

---

### Post by mlentink on 2008-04-30
> **Adribhel said:**
> Linux was installed by downloading Iso-image, mounting it in deamontools, and running the installation. After the reboot Ubuntu installed itself and rebooted again.

Frankly, I don't understand what you're saying here. The usual route is to burn that ISO-image to a disk, boot from that disk and then choose 'install'. In your listing, I don't see the usual linux partition and swap file. If you burn, boot and install from a 8.04 disk, Ubuntu will, after correct installation,  automagically identify your windows disk and enable you to read from, and write to it.

---

### Post by Adribhel on 2008-04-30
Having problems finding back to the thread that described what I had to do to boot Ubuntu. (I got error when trying to boot it after installing)

But i entered the Ubuntu folder trough Windows, navigated to a file I opened with MS Wordpad. There I had to search the document for (hd x,y) I think. The x and y could be either 1 or 0. I simply had to change 0 to 1, or 1 to 0 in x,y wherever i found (hd x,y)

This was due to Ubuntu not using the right disk to boot from or something as it didn't find the files it needed.

---

### Post by Adribhel on 2008-04-30
> **mlentink said:**
> Frankly, I don't understand what you're saying here. The usual route is to burn that ISO-image to a disk, boot from that disk and then choose 'install'. In your listing, I don't see the usual linux partition and swap file. If you burn, boot and install from a 8.04 disk, Ubuntu will, after correct installation,  automagically identify your windows disk and enable you to read from, and write to it.


The only difference from what you're saying and what I did, was that I used a program called Deamontools to emulate a disk. In this way I wouldn't need a real disk, as Deamontools tricks Windows to believe there is a Ubuntu disk in a virtual tray.

---

### Post by mlentink on 2008-04-30
I beginning to suspect you installed Ubuntu through Wubi. That would explain the lack of a ext3 and swap partition. I'm afraid I have only very sketchy experience with Wubi (used it more than 1 1/2 year ago to try out, then went for a real install). But I don't really see why installing that way would prohibit you from seeing a ntfs-partition.

Maybe someone with more knowledge of Wubi can jump in?

---

### Post by mlentink on 2008-04-30
> **Adribhel said:**
> The only difference from what you're saying and what I did, was that I used a program called Deamontools to emulate a disk. In this way I wouldn't need a real disk, as Deamontools tricks Windows to believe there is a Ubuntu disk in a virtual tray.

Actually there's quite a bit of difference. Booting from the cd makes sure that all current filesystems are unmounted at install time. They would have to be, otherwise you could no repartition at all. In your case Ubuntu is not installed in its own partition, but a virtual partition in a windows file on a ntfs-disk. I am not expert enough by far to understand all the consequences of that. Not being able to see the 'mother-partition' might be one of them.

---

### Post by Adribhel on 2008-04-30
> **mlentink said:**
> Actually there's quite a bit of difference. Booting from the cd makes sure that all current filesystems are unmounted at install time. They would have to be, otherwise you could no repartition at all. In your case Ubuntu is not installed in its own partition, but a virtual partition in a windows file on a ntfs-disk. I am not expert enough by far to understand all the consequences of that. Not being able to see the 'mother-partition' might be one of them.

True, as I can "uninstall" Ubuntu from Add/Remove programs in windows.

Edit: By mother-partition you mean where Ubuntu is installed. As that is the case.

---

### Post by byzcath on 2008-04-30
> **Adribhel said:**
> True, as I can "uninstall" Ubuntu from Add/Remove programs in windows.

Edit: By mother-partition you mean where Ubuntu is installed. As that is the case.

I have the same issue, that is not being able to see the windows drive where ubuntu was installed with wubi but here is my workaround.

I created a directory in /mnt named windows (sudo mkdir /mnt/windows)
then I execute the following command, /bin/ntfs-3g /dev/sda1 /mnt/windows

Where /dev/sda1 is the windows drive

I can then see my windows drive in the directory /mnt/windows

Hope this helps you out.


Br. David, O.Carm.

---

### Post by mlentink on 2008-05-01
> **byzcath said:**
> I have the same issue, that is not being able to see the windows drive where ubuntu was installed with wubi but here is my workaround.

I created a directory in /mnt named windows (sudo mkdir /mnt/windows)
then I execute the following command, /bin/ntfs-3g /dev/sda1 /mnt/windows


You should be able to see your windows drive in /host, as per:
[https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)

Good luck!

---

### Post by zetaman_z on 2012-01-20
I have a similar problem.  Its been running well until today. Now I can't detect either external drive & my internal WinXP drives when before all I have to do is mount the drives. Are there any commands or procedures to restore access? 

I'm new to Linux. I love how quick and easy it is to navigate with. I'm using Ocelot on my i7 and Lubuntu on my older Centrino Duo laptop. Until today I never had a problem with Ubuntu 11.10.  


i7-870 2.93GHz
4GB RAM
1TB / 1.5TB HDDs
GeForce 430
ASUS P7H55M mobo

---

