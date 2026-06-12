---
title: "fsck from util-linux 2.19.1"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by spamanon on 2012-03-07
So I tried to start my computer and it gave me a bunch of options including to start ubuntu or a recovery version or look at the boot menu etc.  I chose to start the regular ubuntu.

Now I get a black screen with yellow words:

fsck from util-linux 2.19.1\/dev/sda1: clean, 278888/2342423432 files, #/# blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
* Starting apparmor profiles
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Checking fro running unattended-upgrades:




That's all it does.  It just hangs here.  WTF?

thanks.




***** UPDATE**********



After waiting for 15 minutes I unplugged the laptop and popped the battery out because that is the only way I could shut it off.  I then turned it on and now it is at a screen that says:


ubuntu 

with the 5 orange dots underneath and it just sits there.  The WiFi light is flashing but nothing else is happening.....


Help me please!






*****Update Again************




Nevermind, I quit!  Too much wasted time trying to keep ubuntu running.  It's been an adventure, and now I am tired of it....

Instead, please point me to a link which shows how I can install Windows from a cd without being able to get ubuntu running...

Thanks!!

---

### Post by NikTh on 2012-03-07
> **spamanon said:**
> So I tried to start my computer and it gave me a bunch of options including to start ubuntu or a recovery version or look at the boot menu etc.  I chose to start the regular ubuntu. 

Those options shows up when you hit the _recovery mode_ from grub menu



> **spamanon said:**
> with the 5 orange dots underneath and it just sits there. 

when sits there hit Ctrl + Atl + F1 login (with username and password) and run the bottom commands one by one 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg-reconfigure -a
sudo update-grub
sudo reboot
```

---

### Post by spamanon on 2012-03-07
Thanks NikTH,

Do you know how I can access the contents of a Windows install disk without being able to get ubuntu working?  I entered the boot menu and set it to boot from CD-ROM but it skips past it.  I would like to install Windows but I can't figure out how to access the disk..


Thanks.

---

### Post by NikTh on 2012-03-07
if the DVD is not corrupted you can go to bios again and select Only CD . Remove 2nd - 3d options. Leave them blank . 

Also you must know that if you install windows now , grub will vanish . Windows will re-write MBR and you will not be able to load ubuntu. To restore grub again you must do something like this -- > [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) . Bootrepair its an automated easy method . I suggest to download it now and write it to CD . I mean now , before install windows. Then when you lose grub you can restore it simple by boot from CD of BootRepair.

---

### Post by Giuseppe33 on 2012-06-15
Hi 
I am having the same problem but when I  hit Ctrl + Atl + F1 I only get  a black screen

---

