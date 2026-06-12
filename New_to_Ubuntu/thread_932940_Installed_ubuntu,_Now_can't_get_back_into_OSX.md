---
title: "Installed ubuntu, Now can't get back into OSX"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by yarrow123 on 2008-09-28
I installed ubuntu on my macbook (white) using bootcamp and thought I set up the partition correctly.  Ubuntu doesn't have much functionality.  No drivers.  Can't connect to the internet.  But much worse, I can't get back into OSx.  When I hold down the cammand key I only get a "windows" picture and it takes me to ubuntu.  Before I installed ubuntu I had the OSX option and windows.  My dad says I wrote over OSX.  I feel like a comlete idiot.  Can someone help me?  At the very least I would like to uninstall Ubuntu and reinstall OS X.

---

### Post by Keen101 on 2008-09-28
I don't have a mac, so don't consider me a mac expert.

If you want to reinstall OSX the OSX cd that came with your mac should be able to handle all that.

But, if you want to make sure about your partitions (or need to make an OSX HFS+ partition) I recommend you try the Gparted Live-CD. It presents a very easy to follow GUI based partition editor/viewer.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You might have wrote over OSX, but it's more likely you just wrote over the mac bootloader. And I have no knowledge about how mac bootloaders work, so i have no advice in that front.

If you use Gparted Live-CD and actually find out that OSX is still there, then you could try to use the Super Grub Disk to restore the GRUB bootloader. Either that, or lean more about how bootcamp works. Bootcamp might be the one that was overwritten.

---

### Post by iponeverything on 2008-09-28
I think it is unlikely that you destroyed your osX install. 

It is easy enough to find out though.  Under Linux just see if your OSX partition still existed, if it does mount it and see if the data is still there. 

sudo fdisk -l   -- will print out your partitions 
sudo mkdir /mnt/osx   -- create a mount point
sudo mount -t hfsplus /dev/hda10 /mnt/osx -- where /dev/hda10 is where you found your partition
then cd to /mnt/osx to see if you data is intact.

---

### Post by Ocxic on 2008-09-29
it's the option key that will take you to the startup manager, that should allow you to choose the proper startup disk.

---

### Post by yarrow123 on 2008-09-29
If I have the OS X CD in and I hit the option key I can get to a start-up manager but when it asks me where I want to install to, there is nothing there to click on.

---

### Post by yarrow123 on 2008-09-29
> **iponeverything said:**
> I think it is unlikely that you destroyed your osX install. 

It is easy enough to find out though.  Under Linux just see if your OSX partition still existed, if it does mount it and see if the data is still there. 

sudo fdisk -l   -- will print out your partitions 
sudo mkdir /mnt/osx   -- create a mount point
sudo mount -t hfsplus /dev/hda10 /mnt/osx -- where /dev/hda10 is where you found your partition
then cd to /mnt/osx to see if you data is intact.
I really don't know anything about linux  which is why I wanted to run obuntu...so I could learn.  I opened up the terminal in Obuntu and typed in the script you mentioned.  I get three listings.  One says Linux, the other says 5 Extended and the other says inux swap / Solaris.  I don't know what this means but I'm thinking it means that OSX is not there.  I'm not sure I am doing this correctly any advice would be welcomed.

---

### Post by iponeverything on 2008-09-29
Humm.. it does look like you have nuked you osX partition.. hope you had backed up your personal stuff. Reinstalling OS is really no biggie and can be good learning experience.

---

### Post by Keen101 on 2008-10-07
> If I have the OS X CD in and I hit the option key I can get to a start-up manager but when it asks me where I want to install to, there is nothing there to click on.

That is probably because your OSX disk does not detect any "OSX" partitions. Which i think is called HFS. You need to either use some OSX partitioner, or use the GPARTED Live-CD. You will need to create an HFS partition so OSX can use it.

---

