---
title: "[SOLVED] Help fixing GRUB"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Bugsysservant on 2008-07-30
I put EEEXubuntu (basically xubuntu 7.10 with a few modified drivers) on my EEE PC's hard drive, and while I loved it, I was curious about the Ubuntu EEE, which I put on my SD card. Unfortunately, in the install, the MBR of the hard disk was screwed with so that I can no longer get to GRUB without the flashdrive I installed off of being inserted: I just get an "error 21" without. My question: how do I fix GRUB for Xubuntu? I can boot into either OS, but don't want to have to carry around a flash drive with me indefinitely just to use my computer. Also, bear in mind that I don't have a removable drive, and the EEE PC doesn't come with an optical drive, so if it can't be done within the OS itself, I can only do it from a flashdrive. Thanks.

---

### Post by caljohnsmith on 2008-07-30
Sounds like the classic case where your MBR is now pointing to the Ubuntu on your SD card for all its configuration files and menu.lst. Here's how to change the MBR to point back to your EEEXubuntu:

Boot into Ubuntu/EEEXubuntu, pull up a terminal, and do:
```
sudo grub
grub> find /boot/grub/stage1
```
This will return the partitions that have Grub installed, and you want to use the one that is your EEEXubuntu. If it is (hd0,0) for example, then do:
```
grub> root (hd0,0)
grub> setup (hd0)
```
And that will reinstall Grub to the MBR, but it will now point to (hd0,0) for the menu.lst and all the configuration files.

---

### Post by Gtoniser on 2008-07-30
I have a similar problem, but in my case I have ubuntu on my sd card and on my HD only xp/vista dual boot. So how can I put the boot loader on my hard disk, so I can boot the pc without the card in my cardreader?

Regards,
Gtoniser

---

### Post by caljohnsmith on 2008-07-30
> **Gtoniser said:**
> I have a similar problem, but in my case I have ubuntu on my sd card and on my HD only xp/vista dual boot. So how can I put the boot loader on my hard disk, so I can boot the pc without the card in my cardreader?

Regards,
Gtoniser
Gtoniser, you would need to have some place on your HDD for Grub's configuration files, including the menu.lst. You could create a small partition on your HDD for Grub, and install Grub there (and I would probably use ext3 as the filesystem). Then you wouldn't need the SD card in to boot any of your operating systems. My /boot/grub directory is only about 200 KB, so if you don't plan on installing any Grub splash screens, you could make the Grub partition maybe as small as 1 MB I think; but I would give it at least 10 MB just to be safe and since 10 MB is hardly anything anyway. I'm not sure how much "overhead" though that the ext3 file system uses, meaning that if you create a 10 MB ext3 partition, I'm not sure how much of that will actually be free space.

Once you've created a Grub partition on your HDD, you would boot into Ubuntu (the old way still with your SD card), and then from Ubuntu you can install Grub to that newly-created partition. I can give more details if you need, but that's the theory.

---

### Post by Gtoniser on 2008-07-30
Thanks for your reply, I used the mbrfix tool in vista to get rid of grub, so now I can't boot ubuntu anymore, but that isn't a really big problem (had to reinstall it anyways since I wasn't planning on leaving it on my sd card). Major thing is that the pc works as before.

Thx for the help ;)

---

### Post by Bugsysservant on 2008-07-31
Thanks for that, it worked perfectly.

---

