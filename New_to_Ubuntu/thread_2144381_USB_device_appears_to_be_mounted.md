---
title: "USB device appears to be mounted"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by simonr93 on 2013-05-12
Hey guys, sorry I know this is probably a really dumb question, but basically when I open the Home Folder down the side it shows that I have a USB device plugged in ( which I don't) called "New Volume"

and when I try to unmount it I'm presented with this error window...


Does anyone know;
1. Why it's there.
2. How to remove it.
3. How do I become the "root".
4. What is the "root"


Thanks in advance guys. 
I'm new here and it seems like a really nice community. 

:-) 

- Simon.

---

### Post by cariboo on 2013-05-12
First you need to determine where the ***New Volume*** is mounted, to do this, press Ctrl-Alt-t to open a terminal, then at the prompt type the following command:

```
df -h
```

the result should look simialr to this:

```
 df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.5G  5.0G  4.1G  55% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  1.2M  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  504K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda3       218G   30G  178G  15% /home
**/dev/sdc1       7.5G  785M  6.8G  11% /media/cariboo/31EA-EBC5**
```

In the example above, my usb thumb drive (/dev/sdc1) is mounted to /media/cariboo/31EA-EBC5. Check the screenshot to see how it shows in the file manager. To umount the drive, in the same terminal type:

```
sudo umount /dev/sdXX
```

where /dev/sdXX = your device, that you determined by running the first command. The **sudo** command elevates your user privileges to the same as the root (administrator in Windows speak) to allow you to unmount your device.

---

### Post by DuckHook on 2013-05-12
Has it always been there from date of first install? If not, when did it show up? Please describe exactly what you were doing (every detail is important, so describe as much as you remember) before it showed up. For example, did you plug in a USB drive and then unplug it without first unmounting? Please open a terminal and cut and paste the following commands into it. Then post output back to this thread:```
lsusb
``````
cat /etc/mtab
``````
sudo blkid
```The last command will require your password. As you type it in, you will get no feedback from the terminal. Not even a series of "***". This is a security feature and perfectly normal behaviour. If the extra drive is not causing trouble, then you should go about trying to get rid of it with caution. It is nice to tidy such things up, but not at the expense of making your system unstable.

Root is the superuser or administrator account in Linux that can do anything at all to the system. Therefore, it is extremely powerful and extremely dangerous. People routinely hose their system running as root, but it is needed for administering your system, so is also indispensible. In Ubuntu, root is disabled by default. Instead, the user is given access to root privileges on a single command-by-command basis by prepending "sudo" to the desired command. My third command above is a typical example. If used carefully, root privileges are powerful and very useful. If you are asking about root, then you will appreciate the following links to read up on Ubuntu and Linux in general:

General Ubuntu Intro:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

The following link is full of further references but can sometimes be overwhelming:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)

"Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

I'm shutting down for the night, and will be busy all day tomorrow. Will try to look in on you in 36 hours. Given that your extra drive seems to be an artefact that is not causing you harm, I trust that a small delay is not unbearable. Hopefully, others will have run across this issue before and render my further involvement unnecessary.

---

### Post by simonr93 on 2013-05-12
Hey, here is my results from those commands you asked me to do. 

[http://imgur.com/a/tBU1D](http://imgur.com/a/tBU1D)

I don't remember how long it's been there, however when ever I do insert a USB drive, I always unmount it before removing it, plus they're normally at the top of the Home Folder for me. This I just recently noticed. The size is not that of any USB drive I own. The only ones I have are 20/80/500GB. 



I also did as cariboo907 asked and this was the result.

[http://i.imgur.com/WSQZFmE.png](http://i.imgur.com/WSQZFmE.png)



I'm quite baffled as to what it could be now.,. Thanks for helping anyway. :)

---

### Post by simonr93 on 2013-05-12
Just to update you all, I managed to terminate the mounted "New Volume" by entering "gksudo nautilus" into terminal. I was then able to unmount it. I'm still confused as to what it was, nearly full and yet "nothing" was in it, even viewing it through terminal using "ls -a".


It is still within my /media file but unmounted, I'm not sure what it is, or why it's there. I only installed Ubuntu as the full stand alone OS on my system yesterday (after days of dual booting failures) so my theory that it could be a dead partition still hanging around probably is foiled... I don't know, can remnants of partitions survive a full HDD wipe?


Either way thanks, I'm not going to deem this as solved just as yet, because I'm intrigued to find if any other members know what it could be, given the information/screenshots above. I will carry out commands if necessary. 


- Simon


(please excuse my awful forum etiquette)

---

### Post by pootan on 2013-05-12
Sometimes a picture is worth a thousand lines typed into a terminal. Find the program called Gparted on your machine, if you have to install it do so, then run it and see what it shows you. 

Actually since its labelling it as sdb1 it looks like you have another drive attached to your computer that is around 65 gig. Make sure you have no usb devices attached and are you sure you only have one internal harddrive?

---

### Post by DuckHook on 2013-05-12
This is nothing more than a crazy guess, but from your lsusb output, it seems that you have a webcam and bluetooth attached to your system. Do you have an android phone/tablet or iPod/iPhone with approximately 64GB storage that is almost full? If so, then it is possible that it is being sensed, and now, every time this device is near your computer, the bluetooth connection automatically gets established and the device shows up as a storage unit. However, you can't browse contents because it isn't syncing properly. Like I said, nothing more than a crazy guess. Another possibility is an SD card that you've left in some card reader.

BTW, your forum etiquette is impeccable as far as I'm concerned. You are a pleasure to help and a model to those seeking such help.

Now, will have to do the grilling thing for all the Moms milling about. Will be off line till they're all happy, stuffed and gone. Happy Mothers' Day to all Moms out there!

---

