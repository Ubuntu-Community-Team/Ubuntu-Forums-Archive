---
title: "Live USB"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by hndrk on 2008-11-17
Hi,

is there any tutorial on how to make a Live USB of ubuntu (as well as some documentation on it)? Also, would anyone know what size of flash USB should be used at minimum?


Thanks,

hndrk

---

### Post by skintythe1andonly on 2008-11-17
Are you on Hardy or intrepid?? Intrepid has a build in utility for making a live USB. It is easy to use. It even gives you the choice of saving files then to the USB drive...an option you dont have with a Live CD.

---

### Post by hndrk on 2008-11-17
Hi,

I'm doing a coding project on Hardy through VMWare (I'm new to linux) and in order to make it more portable I can either transfer the VM to hdd (as it will be 8-10GB) or use a Live USB (I have 1GB and 4GB USB drives).

I think the Live USB would be a great option for me and it would save me carrying around a portable hdd.

Is the Live USB feature only in 8.10? I'm downloading the iso right now. Also, is there any documentation on the features of using the Live USB i.e. what are its pros and cons?


Thanks,

hndrk

---

### Post by Zimmer on 2008-11-17
[http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/](http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/)

This site contains numerous tips, tricks and pitfalls and many tutorials for various USB installs. Well worth a read...

---

### Post by C.S.Cameron on 2008-11-17
A Live USB install using USB-Creator uses 700 MB minimum without persistence. (same for Unetbootin).
A Full install starts at a little over 2 GB.

---

### Post by sirjoebob on 2008-11-17
I would use intrepid as it has an option to create a USB boot disk from the administration menu.

---

### Post by skintythe1andonly on 2008-11-17
if you are doing a coding project then a live usb may not be the right option as you will have to install all your packages everytime you boot.... i.e. you will have to install build-essential for a c++ project... you may get away with it if it is python or something. You could do a full install on a USB key provided you had enough space. You may want to remove some packages after to be sure you can fit any extra packages you download, (id take away the games for a start). Unetbootin is good and similar to the utility in intrepid.

---

### Post by C.S.Cameron on 2008-11-17
I am running Virtual Box ok on 4GB and 8GB flash drives created using the usb-creator tool in 8.10.
The 4GB is a bit small for XP with AutoCAD, SketchUp and Rhino, so I stuck the virtual disk on a separate 4GB flash drive, (I'm installing SP3 now).
This is how I set up the persistent drive:

Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted the casper-rw file.
Shutdown, removed CD, rebooted.
Changes were persistent.

---

### Post by C.S.Cameron on 2008-11-17
Oops, I see you want 8.04, I don't think usb-creator works with this.
This method works ok for a Unetbootin install:

Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

If you are installing VMWare to the device you want to make home-rw as large as possible.

---

### Post by hndrk on 2008-11-18
Hi,

I've been told that the libraries and extra files which will be needed for the coding development project will be in excess of 4.0GB just by themselves. I will either have to get a larger 8GB/16GB flash drive or buy a 2.5" hdd enclosure for my spare 20GB 2.5" hdd...



Thanks,

hndrk

---

### Post by saltydog on 2008-11-19
Hi,

I have just done an USB startup disk with usb-creator, and it works fine but I am getting a problem: even if I have selected to have 128MB of persistence, it doesn't save any user info.

I have browsed the USB disk and the file casper-rw is there, but mounting it, it is empty..

---

### Post by C.S.Cameron on 2008-11-19
The casper-rw file saves your newly instaled programs, there should be a home-rw file that saves your settings.
128 MB is not a lot of space but you could try installing something small and see if it is persistent.

---

### Post by saltydog on 2008-11-19
So you mean that using usb-creator with "persistence" doesn't save user data?

How can I create this home-rw file?

---

### Post by C.S.Cameron on 2008-11-19
Your UC created flash drive with persistence should be saving your settings also.
If you want more control try creating persistent partitions as I outlined above.

I may be wrong about UC making a home-rw file, I recall that it once did but I can't find one now.

---

### Post by powel212 on 2008-11-21
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

### Post by Keen101 on 2008-11-22
1gb minimum for live-usb

use this works great. not tutorial needed. simple.


[https://launchpad.net/liveusb](https://launchpad.net/liveusb)

install above deb file onto a live-cd, then run it while usb is plugged in.

---

