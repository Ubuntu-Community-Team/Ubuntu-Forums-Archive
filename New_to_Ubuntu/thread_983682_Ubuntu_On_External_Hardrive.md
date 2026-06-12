---
title: "Ubuntu On External Hardrive"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by dowell22 on 2008-11-15
is it possible to run ubuntu on an external hardrive?

---

### Post by Keen101 on 2008-11-15
Yes. The system i am typing this on is running Ubuntu on an external 80gb laptop drive in a ide-usb enclosure.

It is easiest to install if you unplug all your internal hard drives before installing ubuntu on your external drive. If you don't the GRUB bootloader might not install to the correct hard drive.

---

### Post by boblemur on 2008-11-15
its more than possible :) im posting from a 2gb usb stick...

i do suggest however you remove ur harddisks (or at least turn them off in bios) so u have no way of accidentaly breaking ur current config... 

also there are a few other things to take into concideration....


sometimes it may not find ur partitions because they are not always in the same place.. ie if u take it to a computer with 2 internal harddisks and u installed it with 1... then it will look for sdb but ur external has now becomes sdc, also ur X11 settings may be a little weird because ur hardware is always changing...

but thats only a problem if you are actualy takeing it to different computers,if you are simply installing it there because thats where ur space is, then it should be an issue...

if u turn of the disks (which i suggest you should) it will then also ensure that grub is installed on the right disk... which can be 1/2 the battle :)

post if u have anymore questions...or if iv been unclear


edit: didnt see you had already suggested turning off ur intenal hdd's but i totaly agree with keen101

---

### Post by cochingeek on 2008-11-16
Yes , easily possible.
  Make sure your motherboard can boot an USB.
  Before installing ubuntu in the external drive it is safer to     disconnect your internal hard drive or disable it in the Bios.
( Hope your external drive has an usb connector)

---

### Post by boblemur on 2008-11-16
Also if you are running it on any type of USB stick(ie not an actual hard disk) you will destory your disk doing this... because of swap + logging + tmp files will slow ur system down and also break ur disk because they cant write as many times as a hard disk.

so if this is the case you need to add the following to ur /etc/fstab

```

tmpfs		/etc/network/run	tmpfs	defaults,noatime	0 0
tmpfs		/tmp		tmpfs	defaults,noatime
tmpfs		/var/lock		tmpfs	defaults,noatime
tmpfs		/var/log		tmpfs	defaults,noatime
tmpfs		/var/run		tmpfs	defaults,noatime
tmpfs		/var/tmp		tmpfs	defaults,noatime

```

Warning: by running /var/log in a tmpfs you will only keep the logs for the current session...

tmpfs is basicly just a section of ram that pretends to be a disk...
so as you would expect its alot faster but you lose it when u shutdown...

it will save ur usb stick :) so i suggest you do it if ur using a usb stick.. or any flash media. also if you really need swap space... u should buy a different stick and mount that (because if u destory an empty stick u dont lose anything)

---

### Post by dowell22 on 2008-11-16
how exactly could i disconnect my hardrive?

is there some way i could put it on the external hard drive without tearing my computer apart?

i'm pretty young and i don't have a laptop yet, so i'm asking all the questions now.

i use ubuntu and i would like to install in on my laptop when i get a one.

if i do my parents will be paying for it, and i don't think they'd be to happy if they knew i was takin up a brand new laptop apart.

---

### Post by caljohnsmith on 2008-11-16
You don't need to disconnect your other HDD; when you go through the Ubuntu installer and select your external HDD to install Ubuntu to, at the last stage of the installation process, just click the "advanced" button and specify /dev/sdb (or whichever is the external drive) to install Grub to. That will install Grub to the MBR (Master Boot Record) of the external drive, so that the installer doesn't touch any of your other drives. That's all you need to do, so if you are careful to do that, you don't need to disconnect any other drives. :)

---

### Post by dowell22 on 2008-11-16
how can i tell which is which?

---

### Post by Jesan Fafon on 2008-11-16
if the external hard-drive is always plugged in, then installation should be normal... but other than that....

The rest of them have it.

---

### Post by dowell22 on 2008-11-17
how do i tell which is my external hard drive or my hard drive?

---

