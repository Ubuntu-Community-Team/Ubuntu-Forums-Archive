---
title: "Unable to write to USB or simply cannot use USB in 14.04"
date: 2016-03-27
forum: New to Ubuntu
---

### Post by renjith4 on 2016-03-27
I was trying to fix a read-only USB and ended up in a mess :(

All i need is to put it back to normal. Please help.
I will post all possible screens that i know. Please let me know if you need something additional.

This is what i see when i plug in the device.

  [ATTACH=CONFIG]268021[/ATTACH]



[ATTACH=CONFIG]268022[/ATTACH]


[ATTACH=CONFIG]268023[/ATTACH]

[ATTACH=CONFIG]268024[/ATTACH]


[ATTACH=CONFIG]268025[/ATTACH]

Eventhough i've been using Ubuntu for a long time, i dont have idea on unix commands. 
So it will be helpful if you can explain your answer. thanks.



update --> After removing usbmount
Now i have something new
[ATTACH=CONFIG]268026[/ATTACH]

---

### Post by nerdtron on 2016-03-27
Did you installed the "usbmount" package? This is a package for servers and not intended for desktop installs.
The USB mounting should be done automatically on a desktop system, no further intervention required.

Uninstall the usbmount package, you can use the software center to remove it or via the command line:
>  sudo apt-get remove usbmount 

---

### Post by renjith4 on 2016-03-28
great... thats a new information. removed usbmount and i am getting a new errr message

question updated with it

---

### Post by Bucky Ball on 2016-03-28
Welcome. Please install Gparted and have a look in there. Locate the USB from the drop-down menu at top right of the Gparted GUI, unmount and delete any partitions (if you can delete, if not, continue anyway). Click Device> Create new partition table. Be aware that this method will wipe any data and partitions present on the USB, so if you don't want to do that, read on.

There are other ways to change the permissions and you are getting a bit too complicated with perhaps. Open a terminal and, presuming you are using Ubuntu:

> gksudo nautilus

That will open the file manager as root. Change the permissions to whatever you like, but then close the file manager. One false move in there as root can seriously break things. So be careful and just change the permission on the USB. :)

You can also change it in a terminal with:

```
sudo chown -R username:username /path/to/USB
```

For instance:

```
sudo chown -R renjith4:renjith4 /home/renjith4/USB
```

The location you're chowning should be where you have the USB mounted.

Hope that gives you a few clues.

---

### Post by nerdtron on 2016-03-28
Better if you can reboot your computer.
Just to refresh all  mount/remount all drives.

---

### Post by renjith4 on 2016-03-28
This command really helped me "[COLOR=#111111][FONT=Consolas]sudo mount -o remount,rw,uid=[renju] /dev/sdb1 /media/renju/[/FONT][/COLOR]9F51-B46B".
After executing it, i restarted the machine and that did the trick. 

Now the issue is with the pendrive that i tried to fix. When i tried to execute the same command for that, 
this is what i got!

renju@renjus-notebook:/media/renju$ sudo mount -o remount,rw,uid=[renju] /dev/sdb1 /media/renju/0F9D-5117/
[sudo] password for renju: 
mount: you must specify the filesystem type


using nautilus gave me this error messge.

Sorry, could not change the permissions of &#8220;0F9D-5117&#8221;: Error setting permissions: Read-only file system


result of chown

renju@renjus-notebook:/media/renju$ chown -R renju:renju 0F9D-5117/
chown: changing ownership of &#8216;0F9D-5117/SanDiskSecureAccessV2.0/DownloadForMac_SanDiskSecureAccessV2.0.pdf&#8217;: Read-only file system
chown: changing ownership of &#8216;0F9D-5117/SanDiskSecureAccessV2.0/QuickStartGuide_SanDiskSecureAccessV2.0.pdf&#8217;: Read-only file system
chown: changing ownership of &#8216;0F9D-5117/SanDiskSecureAccessV2.0&#8217;: Read-only file system
chown: changing ownership of &#8216;0F9D-5117/SanDiskSecureAccessV2_win.exe&#8217;: Read-only file system
chown: changing ownership of &#8216;0F9D-5117/Adi Kapyare Kootamani (2016) Malayalam DVDRip 720p x264 AAC 5.1 E-Subs-MBRHDRG.mkv&#8217;: Read-only file system
chown: changing ownership of &#8216;0F9D-5117/&#8217;: Read-only file system


now i believe it is somehting with the pendriwve

---

### Post by nerdtron on 2016-03-28
My experience on read-only pendrives is that:
1. be sure to safely remove it (especially when you use it on linux) before you unplug it.
2. If you did number 1, but the pendrive is still read-only, then try the pendrive on another linux computer (or windows machine) and see if it works.
3. If 1 and 2 fails, then the pendrive is most likely dead.

---

### Post by sudodus on 2016-03-28
Before giving up on the pendrive, you can try to wipe the first megabyte and create a new partition table. See the following link

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by renjith4 on 2016-04-01
> **nerdtron said:**
> My experience on read-only pendrives is that:
1. be sure to safely remove it (especially when you use it on linux) before you unplug it.
2. If you did number 1, but the pendrive is still read-only, then try the pendrive on another linux computer (or windows machine) and see if it works.
3. I**f 1 and 2 fails, then the pendrive is most likely dead**.

Yes, that was dead. I got it replaced by sanddisk.

---

