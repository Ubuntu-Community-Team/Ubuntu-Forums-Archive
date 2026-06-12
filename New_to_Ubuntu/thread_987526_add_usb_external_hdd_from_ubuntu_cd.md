---
title: "add usb external hdd from ubuntu cd?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by jumpingjaxs on 2008-11-19
hi there,
im new to forums and to ubuntu. 

i previously had windows xp but i had my hd reformatted and chose not to reinstall windows. all my data is on my hd but i have no operating system. a friend lent me a ubuntu 8.04 cd to try which is what im using right now. i decided i want to install ubuntu but i am lost.

i need help to back up my data (i bought a new usb hdd for this), and then to install the os. 

so far, i plugged in my usb hdd but it doesnt seem to show up. 

ive been trying to research and educate myself but ive only about 4 hours free time each week and im very anxious to at least get things rolling. i know there is so much to learn.
can anyone help guide me through this?

thx so much

---

### Post by zzHanks on 2008-11-19
Hello.

If I understand you correctly you want to be able to copy the files you have on your computer to the USB harddrive, using the LiveCD, but you can't see (mount) the drive.

If so, try this: Go to System > Administration > Synaptic Package Manager - Search for ntfs-3g and install that package - Assuming that the drive is formatted in NTFS


Hope this helps.

---

### Post by bobnutfield on 2008-11-19
If you have a desktop from the live cd, go to Places and see if it shown in the list of accessible places.  If not, then go to Applications>Accessories>Terminal.  This will open the terminal for use.  When it is open, type:

> sudo fdisk -l

The USB hard drive will be listed after your internal hard drive, probably as /dev/sdb.  If it does, post the output of fdisk -l back and we can show you how to mount the drive manually.  But, what files do you want to back up?  If there is no operating system, where are the files you want to back up if you are running the desktop from the live cd?

---

### Post by jumpingjaxs on 2008-11-20
thanks for replying!

zzhanks, yes you understand me correctly. however it seems that package is already installed (at least, the only options available are to reinstall/uninstall it). btw how do i know what the drive is formatted in?

bobnutfield, the output of fdisk -l shows only my two internal drives: /dev/sda 41.1gb and /dev/sdb 160 gb. (the 40gb is an irrelevant old drive which i intend to get rid of eventually and the 160 is where my data lives).
but there is nothing produced for my external drive.

---

