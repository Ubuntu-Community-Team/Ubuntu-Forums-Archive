---
title: "[SOLVED] USB startup disk issues"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Shwefty on 2008-11-17
I have two problems, one bigger than the other. I'm using 8.10 with the handy USB startup disk installer.  I got a brand new 8 GB flash drive today to create a boot disk out of, and it ain't working :(.

I grabbed the 8.10 .iso image, checked the md5sum and all that.  I opened up Gparted, formatted the flash drive (kept it in FAT32 for good measure).  Went to the USB startup disk installer (the default one on the 8.10 original install).  It says I need to reformat the flash drive, so I do, then I create the startup disk on the flash drive from the .iso image.

Problem #1, it doesn't work!  I try to boot off of the USB drive, and though the computer recognizes it as a drive labeled as bootable, but that it doesn't have something or other to boot (I tried it at a computer up at school which is much more helpful than my laptop which tries to boot off of it, realizes it can't, then goes straight to Grub.  However, I forgot what it exactly said.).  I've tried it twice, doesn't work still.

Problem #2, the .iso image is <700 MB, why does it take up 4.something on my disk?  What gives?

Now, I know somebody is going to be helpful and say that I need to change my boot order in the BIOS to search for the USB drive first, but...if you just hit the F12 wildly to get to the boot options, and select USB drive, then it shouldn't matter the order, should it?

---

### Post by C.S.Cameron on 2008-11-17
What make of Disk, I've found with Kingston I need to install Ubuntu first with Unetbootin, then erase all the files and use the tool on the disk.
I suggest the reason it is so big on the disk is that your casper-rw file is 3.3 GB, this is where persistence is held.

---

### Post by Shwefty on 2008-11-17
Kingston, good call!  I'm trying your Unetbootin then 8.10 installer way now.

---

### Post by C.S.Cameron on 2008-11-17
Please let me know if it works.

---

### Post by Shwefty on 2008-11-17
Unetbootin worked just fine, didn't even need the 8.10 USB startup disk option...kinda sad that it didn't work for me, but still, your advice works!

Thanks!

---

### Post by Shwefty on 2008-11-17
I say that it works because I'm running off of the USB right now.  So, it really really works.

---

### Post by C.S.Cameron on 2008-11-17
If you should want to make your Unetbootin install persistent, let me know.

---

### Post by Shwefty on 2008-11-17
Why is persistent better?

---

### Post by C.S.Cameron on 2008-11-17
It lets you save your settings and downloaded programs and stuff.
You can set up an account in users and groups and use a password.
If you just want a USB version of the Live CD, what you have is fine.

---

### Post by Shwefty on 2008-11-17
Can you still use the persistent USB disk for an install though?  Frankly, the persistent USB disk would be great to prove Linux is awesome, but if I can't use it to install a base .iso image off of, I'm probably better off with what I have.  Thanks for the answer!

---

### Post by C.S.Cameron on 2008-11-17
Yes, it's still based on the image from the Live CD, just a couple partitions that are persistent, almost as good as a Full install.

From the live CD Start Partition Editor.
Shrink Fat32 partition to the left to about 2-3GB depending on how much space you want as writable from a windows machine, if none leave 750MB.
Create a 3GB ext3 partition to the right of this, label it "casper-rw".
Create a ext3 partition in the remaining space and label it "home-rw".
Close Partition Editor.
Run "gksu nauilus", open filesystem / cdrom and then open syslinux.cfg with text editor.
Add "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
When you reboot you should be persistent.

---

### Post by Shwefty on 2008-11-17
I'll give this a try...tomorrow!  Thanks for the loads of help!

---

### Post by powel212 on 2008-11-21
Had a similar problem with an 8G USB - I created a second partition about one Gig. and installed to the larger partition from a live Ubuntu 8.10. CD. Worked great.

Here are some more details

More info about installing Ubuntu 8.10 on a USB pen drive.



I have now run tests with 

1G

2G

4G and

8G USB drives



Here are the results



Any one of them will do but 



1G is only big enough for install and firefox bookmarks. You can not run updates or install additional software without running out of space really fast.



2G is better if you install a couple of extra apps and Firefox pluggins you will be fine with 2G but still can not run all updates. Will run out of space.



4G can run all the updates and install a a number of programs. But, after I installed Chinese language support I ran out of space again. I guess most people don't need Chinese Support so 4G should be fine for most folks.



8G my current setup. I created a second 1G partition for my files, I find it more convenient to have my personal files on a separate partition.



note:

Please be aware that throughout these tests I have found that if you install and uninstall programs you do not regain much space. that is to say I have found if I install a 25m program and then uninstall it i only get back about 5m after the uninstall. So don't install anything you aren't sure you need. Also language support takes up huge amounts of space so only use what you need.



I also had a problem with the 8G - That is to say I could not install onto an 8G flash drive. I need to get another flash drive to test and see if this is a bug or just the drive i was using, but I solved the problem by creating a second 1G partition and installing the system to the 6.7G remaining.



Also



Be sure to enable universe and multiverse repositories.

I find this tool indispensable

apt-get install compizconfig-settings-manager

it's a GUI for compiz. 



Also need this deb if you want the Open office 3 update

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main



Love running ibex off my USB. Everybody at work is envious of my slick portable system. Can also be used in conjunction with your ipod. ipod can store data, movies, music and rythmbox allows you to play your itunes playlists from within the ipod. Awesome.



enjoy. Powel

---

### Post by powel212 on 2008-11-22
Have now tested with 16G flash drive. 

Successful configuration: first partition 10G for install and second partition 6G for Data
Installed from the live CD without incident.

However
several attempts using varying partition configurations trying to install from non Live CD, From my Ubuntu 8.10 desktop install. Fail, fail fail...every time the installation hits 4.69G and crashes during final stage.

Conclusion: Only use live CD to install persistent USB over 3G

Powel

---

### Post by Meson on 2008-12-25
> **powel212 said:**
> Please be aware that throughout these tests I have found that if you install and uninstall programs you do not regain much space. that is to say I have found if I install a 25m program and then uninstall it i only get back about 5m after the uninstall. So don't install anything you aren't sure you need. 

You need to make sure you uninstall any dependencies and residual files.

```
 sudo apt-get autoremove
sudo apt-get autoclean
```

---

