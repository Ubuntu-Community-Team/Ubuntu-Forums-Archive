---
title: "Installing from Android phone"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by lunchbox3 on 2014-06-21
Hello there, I am having some issues with installing Lubuntu, I have a Compaq Presario CQ57 with a 1.5 Ggz processor and 2 GBs of Ram, I have Windows 7 installed but since my Laptop is so old it is having a hard time running it, so I was told by a classmate about this specific flavor of Ubuntu and that it was made for laptops just like mine, I have able to live boot it off of my android phone with the desktop Iso with Lubuntu 14,04, however whenever I tried to install it, and reboot it I was not able to dual boot into Lubuntu, so I tried to reinstall it, and it seemed to work, well... not really what happened was it looks like Grub did not install right so I booted back to live boot, and proceeded to use Boot-repair, however I am getting this error: Please enable a repository containing the [linux] packages in the software sources of Ubuntu 14.04 LTS (sda3). Then try again. and honestly I have no clue what that means, so I tried it again, and same error occurred. So I am on this forum seeking assistance from the Linux masters who are more knowledgeable than I am. Here is a link that Boot repair gave me, I hope this helps: [http://paste.ubuntu.com/7678618/](http://paste.ubuntu.com/7678618/)
Thank you for your time, I am not worthy!

---

### Post by Impavidus on 2014-06-21
```
=================== No kernel in /mnt/boot-sav/sda3/boot:
abi-3.13.0-24-generic
config-3.13.0-24-generic
grub
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-3.13.0-24-generic
```That explains your problem: your system was not completely installed. I would suspect the live disk. I don't know whether there's anything special about live booting from an android phone – I have only used cds, dvds and simple usb drives – but I would first [check the md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of your .iso and compare it to [the correct value]("https://help.ubuntu.com/community/UbuntuHashes"). Then create [a new live disk]("https://help.ubuntu.com/community/Installation/FromUSBStick"). Then try again.

Use "something else" when asked about partitioning. You don't have a swap partition yet, which may be good to have with only 2GiB ram, so I suggest you delete the existing (primary) ext4 partition and create a logical ext4 partition of 35GiB with mount point / and a logical swap partition of 2GiB. Don't touch your Windows partitions.

It may also be possible to fix your current Lubuntu install, but with those strange install errors you never know what else is wrong. Best to try installing again.

---

### Post by LastDino on 2014-06-21
What software did you use to make your android phone live bootable? What kind of SD card is inside?

---

### Post by lunchbox3 on 2014-06-21
I've been using Droid drive to mount the. Is,  and it's coming from an internal memory with a file system to emulate an SD card.

---

### Post by LastDino on 2014-06-21
And what software did you use on windows to turn that into Ubuntu bootable? 

I use SD cards to do this as well, but I use card readers. If you're going to do this with SD cards, might as well try card reader.

---

### Post by Rob Sayer on 2014-06-21
Also, your compaq is probably actually an HP, which usually means a separate partition with all the HP bloatware crap on it.  This leads to too many partitions.  I had that issue with an old compaq presario cq56.  The "install ubuntu alongside windows" option wasn't there, just, I think, "install ubuntu *within* windows", which is quite different.

I just deleted that partition in windows and then installed properly.

I don't know if that really applies to you but ....

---

### Post by Impavidus on 2014-06-21
> **Rob Sayer said:**
> Also, your compaq is probably actually an HP, which usually means a separate partition with all the HP bloatware crap on it.  This leads to too many partitions.  I had that issue with an old compaq presario cq56.  The "install ubuntu alongside windows" option wasn't there, just, I think, "install ubuntu *within* windows", which is quite different.

I just deleted that partition in windows and then installed properly.

I don't know if that really applies to you but ....

No, that does not apply here. The boot info summary indicates two primary Windows partitions and one primary Linux partition.

I've never heard of that way of creating live disks. But then, I don't own any android devices.

---

### Post by lunchbox3 on 2014-06-21
> **lunchbox3 said:**
> I've been using Droid drive to mount the. Is,  and it's coming from an internal memory with a file system to emulate an SD card.
I didn't use any program to turn the is into a Bootable,  the instructions with the app said that was not needed

---

### Post by LastDino on 2014-06-21
Hmm, I've my doubts about that working out well as you're about the only person I know who has tried it. So, best way to check is you trying different method. 

If you've USB stick or Any card reader, please put it to use. This time, please use 
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Or something similar. 

That way we will have better chance of narrowing down the actual problem.

---

### Post by lunchbox3 on 2014-06-21
I didn't mean to quote myself,  I was trying to quote Latino,  but u am currently using my phone to reply.

---

### Post by lunchbox3 on 2014-06-21
So I tried the suggestion that Impavidus gave me,  now I am getting an error stating "An attempt to configure apt to install additional packages from CD failed"  I am not sure what is going on but I'll try using a thumb drive,  I was having issues where I had used my thumb drive to install lubuntu but when I chose it as a boot device it just went to Windows

---

### Post by LastDino on 2014-06-21
Probably because it was not actually converted to bootable thumb drive.

---

