---
title: "Ubuntu 8 Persistent Flash Drive Install - Slow Boot"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by KAWill70 on 2008-09-24
I have a Ubuntu 8.04.1 Persistent installation in a USB Flash Drive.

It works fine but I have a couple of issues:

1.  Does Ubuntu 8 have any USB problems that might cause the USB interface to run slowly?  The Flash Drive boot is much slower than the Live CD boot during loading of the Kernel.

2.  Shutdown and Restart do not display much of anything.  There are a number of text line messages put out to a black screen and then I just see a line segment/cursor.  Hitting Carriage Return will move it down.  Eventually it may say something about Restarting but I need to hit the Reset Button on the computer.

3.  Before I realized that my computer could boot using USB-HDD, I formatted the USB drive using Partition 4, 64 heads, 32 sectors per track for USB-ZIP compatibility and booted using USB-ZIP.  I never got that Persistent Installation to work properly.  It would work for at least one boot but then run into problems after that.  Have others had trouble with the USB-ZIP configuration?

Thanks,  Kent

---

### Post by C.S.Cameron on 2008-09-24
I install to USB just the same as to HDD.
(never been quite sure what persistent means, like does it save your changes or not?)
I don't find much difference in speed from a hard disk install.

---

### Post by KAWill70 on 2008-09-24
What I meant is that booting Ubuntu from my USB Flash Stick is much slower than booting Ubuntu from Live CD.

Loading the Kernel is very slow.  The rest of the boot seems to be about the same but I believe that part is hardware detection.

I think I read somewhere that Ubuntu has some USB problems and maybe it is running in a degraded mode.

A Persistent Install is a setup that saves your settings and files.

I used instructions from this site.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Thanks, Kent

---

### Post by C.S.Cameron on 2008-09-25
It is taking me about 55 sec to get from BIOS to username/password and about 65 sec from there to being logged in.
Shutdown takes about 30 sec.

---

### Post by KAWill70 on 2008-09-25
Thanks for passing along your boot and shutdown times.  I assume you are booting from a hard disk.

I am using the Ubuntu 8.04.1 Live CD version of the software installed in my USB drive.  I never set a root password so I don't get a log-in screen.

When the boot process displays "Loading Kernel" it takes only seconds when booting from Live CD but several minutes when booting from my USB drive.  I think that is the crux of the problem.

My shutdown is quite strange from either CD or USB drive as very little of anything is displayed other than some lines of text within a black screen.

Kent

---

### Post by C.S.Cameron on 2008-09-25
The times I gave are for boot from slow USB Flash, (8G Kingston Traveler).
This is with Nvidia drivers etc.
Next time try installing Ubuntu to USB just the same as you would to HDD.
I rant a bit here.
[http://ubuntuforums.org/showthread.php?t=922782](http://ubuntuforums.org/showthread.php?t=922782)
I never had much luck with 
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
could barely follow it.

---

### Post by KAWill70 on 2008-09-25
Thanks once again for the help.

I'll review the hard drive install that you mentioned. One concern in using a Flash Drive as a Disk is that Flash Drives have a limited life based on the number of write cycles.

I think the Persistent Installations such as the one I am using access the Flash Drive less and should see longer life.

---

### Post by snowpine on 2008-09-25
> **KAWill70 said:**
> Thanks once again for the help.

I'll review the hard drive install that you mentioned. One concern in using a Flash Drive as a Disk is that Flash Drives have a limited life based on the number of write cycles.

I think the Persistent Installations such as the one I am using access the Flash Drive less and should see longer life.

Yes this is true, however, flash drives are extremely inexpensive. My 2gb cost about $10 US, so if I have to replace it a year from now, I will not be too sad. I don't however have a swap partition on the drive, seems like that would wear it out the quickest.

---

### Post by C.S.Cameron on 2008-09-25
So does a persistent Thubdrive blink when you open stuff and save stuff, or does everything run in ram and only get saved at the end of a session?
If so I wonder if that could account for the boot/shutdown time?
Mine only seems to blink when I am doing stuff.

I've bricked a couple flash drives, but by abuse not overuse.
Most thumbdrives have warranties of 5 years to life.

My swap history is normally flat line, I only have it in case I ever need to boot some raggedy old computer that could use it.

---

### Post by KAWill70 on 2008-09-26
In terms of watching the LED Indicator on the thumb drives, different devices seem to implement the indicator differently.

My Sandisk Cruzer seems to be illuminated whenever it is activated and it just stays on.  My HP thumb drive has a little indicator that seems to flash on both Reads and Writes.

My assumption is that Reads are not a problem, while Writes have some specification for maximum number of writes over the life of the device.

I don't know at this point when the Persistent Linux files are written to the device and whether it is just once per session.

I think the slow boot might only involve reading of the thumb drive and writing to system memory.  I think USB initially defaults to a slow speed and maybe that is the problem.  Possibly the application is not enabling it to run at full USB2 rates after the initial connection.

Shutdown is quite fast.  I think I measured 18 seconds.

I printed out your post on installing Ubuntu the easy way.  Excellent writeup!  Learned quite a few things.

You're right about the complexity of the instructions on the Pen Drive Linux website.  Even so, I found it interesting, challenging, and somewhat satisfying to use all those Unix commands and eventually get the job done.  However, I worked in Electrical Engineering and enjoy that sort of thing.

Kent

---

### Post by geokker on 2008-12-04
I've got Xubuntu running on a 16GB stick - boot is very slow but once done, the session is fast - but I do have 3GB RAM.

I'm currently trying to work out why I only seem to have 3GB available in my home directory and 10GB available as a mounted volume containing the casper loop but root access only - thus useless to me.

Grr.

---

### Post by timcredible on 2008-12-04
the flash drive has to unsquash the entire 690mb of data on it before anything happens, that's why it's slow to start from flash or cd.  some flash drives are quick, but most are slow as snails, which is why they can take longer than a cd.  nothing wrong with ubuntu.

---

### Post by snowpine on 2008-12-04
You can also install to the flash drive just like a regular hard drive. That way, the file system does not have to be unsquashed at boot. The downside is it takes more space on the drive. Also, when you get to the last step of the installer, be sure to click "advanced options" and install Grub to your flash drive, not your internal hard drive.

---

### Post by Herman on 2008-12-04
I agree with snowpine, and also try installing with the Reiser file system instead of ext2 or ext3.

Flash memory is slow to write to, especially when there are a lot of small files to be written.
ReiserFS is ten to fifteen times faster with small files, and that makes up for the flash memory's slowness to a large extent, so you'll end up with acceptable performance.

ReiserFS features optional 'tail packing', which gives approximately a 6% savings in the space files will occupy in the thumb drive at the expense of some of the speed.
The default is 'notail'. 
To enable tail packing, you simply open /etc/fstab and edit your line for / to remove the 'notail' option. 
(I don't use that myself, but some people might want to try it out especially if they have a small flash memory stick want to squeeze more files into it).

You can also easily turn off file system journaling in ReiserFS by editing /etc/fstab and adding the 'nolog' option, which will give you a slight increase in speed.

For example, (tuned for speed),
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=7911a532-9241-480c-9b1f-fa553ae139b8 / reiserfs **notail**,**nolog**,relatime 0       1

# /dev/sdb2
UUID=4b07c40c-aff3-4454-ae1a-9d809e165034 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```I use a swap area in mine but I set swappiness to zero. That's another tweak for extra speed, although some people use it for saving writes to the flash memory.

Regards, Herman :)

---

