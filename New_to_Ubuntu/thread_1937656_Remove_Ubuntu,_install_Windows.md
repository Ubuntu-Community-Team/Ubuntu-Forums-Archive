---
title: "Remove Ubuntu, install Windows"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by The Frenchman on 2012-03-08
I was persuaded to change from windows to Ubuntu by a friend.I'm a plug and play computer user but he told me as long as I downloaded upgrades things would be fine.I have two notebooks that were running 10.10 one I left and the other (the one I'm using now) I took the 11.10 upgrade.10.10 started to have problems shutting down then it started sticking on boot up Once I was lucky enough it booted I tried to upgrade to 11.10 thinking this might solve the problem......wrong,the upgrade failed and now I'm left with a notebook that won't boot and will only give me ubuntu with linux 3.0.0-16-generic the grub version I have is 1.99-12ubuntu5
I just wan't to format the whole computer and reinstall windows so that I can use ubuntu on one and windows xp on the other.Can I format it from grub with the version I have? Thanks in advance.

---

### Post by cortman on 2012-03-08
Welcome to the forums! Sorry the installation is giving you problems.
Boot off of your Ubuntu installation media (whether live CD or USB) and select "Try Ubuntu". It'll boot to a regular desktop environment, from which you can open and run "GParted" which is a disk partitioning utility. With GParted you can format the laptop's HD to NTFS for the Windows installation.

---

### Post by uRock on 2012-03-08
Hello and welcome to the forums. 

I am sorry the upgrade went bad for you. To format the hard drive and reinstall Windows you will first need to create a LiveCD or USB. You can boot the LiveCD in the Try Ubuntu Without Installing selection, then open the menus to System> Administration> Partition Editor or GParted. Using the partition editor/gparted you can delete your current partition, then create an NTFS partition so that Windows can see and install to the hard drive.

---

### Post by The Frenchman on 2012-03-08
I've tried booting windows from a usb (there was a windows partition that was lost when I did first ubuntu download) but I keep getting a drive c corrupt message.I was looking for a root command to totally format the computer so that I can start again with windows on this one.

---

### Post by mörgæs on 2012-03-08
It is likely that the problems you are experiencing come from the upgrade process itself and not Ubuntu. A fresh install might behave well.

---

### Post by mastablasta on 2012-03-08
also grub is a bootloader. it loads before any operating sytsem (such as Ubuntu Linux or Windows) loads. with gparted you will be able to format the disk however you need to boot to it form liveCD/liveUSB.

if you do not know how to create them let us know. Additionally as suggested it's the upgrade process that let you down and a fresh install form such a live media will get the system working again.

i would also ask the friend who gave a suggesiton to switch to Ubuntu to give you a hand in this. it is a really easy process done via graphical interface but you just need to know how to do it.

---

### Post by The Frenchman on 2012-03-09
> **mastablasta said:**
> also grub is a bootloader. it loads before any operating sytsem (such as Ubuntu Linux or Windows) loads. with gparted you will be able to format the disk however you need to boot to it form liveCD/liveUSB.

if you do not know how to create them let us know. Additionally as suggested it's the upgrade process that let you down and a fresh install form such a live media will get the system working again.

i would also ask the friend who gave a suggesiton to switch to Ubuntu to give you a hand in this. it is a really easy process done via graphical interface but you just need to know how to do it.
Sadly he's in UK I'm in Spain.I was hoping there was a root command to format the netbook totally so that I can do a new install from a usb

---

### Post by scrooge_74 on 2012-03-09
Upgrades never worked for me, I always ended doing fresh installs. But since I always put /home in a different partition upgrading has never being an issue

---

