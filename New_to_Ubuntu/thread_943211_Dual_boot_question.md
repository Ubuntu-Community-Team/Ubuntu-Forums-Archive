---
title: "Dual boot question"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Firedfox on 2008-10-10
So I'm downloading Ubuntu 8.04 right now, I plan to install it tomorrow morning. The thing is, I can't back up my files (or I'm lazy to buy blank DVDs to do it). I'm using a Toshiba Satelite A215 running Vista SP1. And I want to install Ubuntu so that I can dual boot and I want to keep them (Vista and Ubuntu) separate from each other. Is there any way I can do this safely?

EDIT: I'm guessing is there any way to split a hard drive before installing ubuntu?
and then installing ubuntu on that part of your hard drive, and will this prevent any risks?

---

### Post by namegame on 2008-10-10
Unfortunately, there is no way to prevent ALL risks. I'm currently running a dual-boot with Vista on my laptop.

You can partition your hard-drive from within Vista, however I would recommend downloading a live image of G-Parted. I personally don't like how restrictive the Vista partition manager is.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It allows you to partition your hard-drive. You will need to download the .iso and burn it to a CD/DVD and boot from it.

When you decide to install Ubuntu, be sure to select the correct partition. You will need to be very careful here to not choose your Vista partition.

---

### Post by Firedfox on 2008-10-10
Thanks for the response... I've just read up on partitioning and I partitioned 12GB in Vista. I just did it with the default settings.

I suppose you mean, in terms of restrictive, that Vista doesn't allow much... but don't worry, 12GB is enough for me, the max was around thirty GB.

So if I install ubuntu on my 12GB partition, it won't interfere with vista and vice-versa?

I'll figure out which is the right Partition as I know that Linux does not use C, D, E, etc.

---

### Post by kansasnoob on 2008-10-10
> **Firedfox said:**
> So I'm downloading Ubuntu 8.04 right now, I plan to install it tomorrow morning. The thing is, I can't back up my files (or I'm lazy to buy blank DVDs to do it). I'm using a Toshiba Satelite A215 running Vista SP1. And I want to install Ubuntu so that I can dual boot and I want to keep them (Vista and Ubuntu) separate from each other. Is there any way I can do this safely?

EDIT: I'm guessing is there any way to split a hard drive before installing ubuntu?
and then installing ubuntu on that part of your hard drive, and will this prevent any risks?

So you're downloading the Live CD, you've never run the Live Cd, but you're ready to install???????????????

Bad, bad idea!!!!!!!!!!!!!!

First run the live CD, and then run it some more!

Then when you're convinced you want to install look here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by namegame on 2008-10-10
They will leave each other alone. Although, I think Ubuntu has the NTFS package installed by default. This means you'll be able to see/edit/copy files from your windows partition. It will just show up as another drive, similar to an external hard-drive.

About your partitions. Linux doesn't see them as letters, I believe Linux shows them as /dev/sda1, /dev/sda2, etc.

When you select your desired partition, you will be able to see the size of it. Just make sure to pick the 12 GB partition and you should be fine.

---

### Post by Firedfox on 2008-10-10
> **kansasnoob said:**
> So you're downloading the Live CD, you've never run the Live Cd, but you're ready to install???????????????

Bad, bad idea!!!!!!!!!!!!!!

First run the live CD, and then run it some more!

Then when you're convinced you want to install look here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Thanks for the advice but I was planning to boot Ubuntu from the CD first if that's what you mean. :popcorn:

---

### Post by namegame on 2008-10-10
> **kansasnoob said:**
> So you're downloading the Live CD, you've never run the Live Cd, but you're ready to install???????????????

Bad, bad idea!!!!!!!!!!!!!!


It's not that bad. Heck some distributions don't even have Live CDs. If you are careful and read documentation and take your time, you should be fine.

---

### Post by WWSmith36 on 2008-10-10
Vista resizing must be done with Vista rather than gparted.  Gparted is good for preparing you linux partition (typically primary / and extented swap)

Check the md5sum of your downloaded Ubuntu .iso image file
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and compare with 
[http://releases.ubuntu.com/8.04.1/MD5SUMS](http://releases.ubuntu.com/8.04.1/MD5SUMS)

Burn it on a CD rom with low speed 4X and then check the md5sum of the burnt CD

And finally "Check CD for defects" to be sure the CD is read without errors by the destination PC CD rom driver.

This is just best practices

---

### Post by Firedfox on 2008-10-10
Thanks guys.... so when I'm planning to install Ubuntu, I'll go with this... I didn't realize the installation has such an easy layout.

[IMG]http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Vista_first__images/ubuntu_05.jpg[/IMG]

since my 12GB is 11.9GB Free

or should I go manual....

---

### Post by namegame on 2008-10-10
Manual can be a bit tricky for new users.

I would use what you have selected.

---

### Post by Xnst on 2008-10-10
Hi,

I have partioned seveeral computers with both XP and Vista with GParted from the ubuntu liveCD and it work perfectly eash time. Now, if you have sensitive data on your Vista you really should wait one day to install which gives you time to go out and buy DVDs and do backup.

As I remember, The Vista computer I installed Hardy on allready had two partitions (or was it three?), it also was a Toshiba Satellite of some kind. I resized the two blocks and left a large partition free for my lovely ubuntu install. I do not know anything about Vista, but in the end I could use it. The computer was not for me, hence the dual boot. 

One thing that made me nervous was that booting into Vista the first time after resizing took a really long time, I thought the whole thing had crashed but it was just confused.

So I say, probably everything will work just fine with GParted, but you will never know until the end.

---

