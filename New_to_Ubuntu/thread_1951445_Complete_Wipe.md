---
title: "Complete Wipe"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by cc.chapman on 2012-04-02
I started out with SUSE Linux on my Lenovo Thinkpad a few years back. After about a year I switched over to Ubuntu because I found the interface easier to work with. I didn't know much about partitions when I made the switch but I suspect I didn't set things up as efficiently as I could have.

My computer's getting sluggish and I wanted to do a complete wipe of everything, start completely from scratch, hardrive wipe, re-partition, install Ubuntu 12.04, etc. I'm not sure what steps I need to take after I back up all my files. 

This probably comes up fairly often in the forums so if someone could direct me to pages that outline the steps I need to take to re-hab my laptop I would greatly appreciate it.


[IMG]http://dl.dropbox.com/u/70571426/partitions.jpg[/IMG]

---

### Post by Rodney9 on 2012-04-02
When you install Ubuntu you are given the option of erasing the entire drive and Ubuntu will setup the default partions for you automatically.

Very good pictorial Install Guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Rodney

---

### Post by Cheesemill on 2012-04-02
If you are sure that you hve everything backed up then just boot from a Live CD and start gparted, then go to Device > Create Partition Table. This will wipe your hard drive and leave it ready for a new install.

(This doesn't actually wipe all of the data off of your drive, it just makes it think that it is empty. Data recovery may still be possible so if you have confidential data that needs destroying then extra steps need to be taken).

---

### Post by Gleichsnerd on 2012-04-02
Reformatting your hard drive isn't too tricky really. Once you back up everything you want/need, you can pop in the LiveCD and boot into "Try Ubuntu," then just use gparted in there and reformat your drive.

If you don't want the hassle of booting up the trial Ubuntu, the custom partition editor within the installation process would allow you to format/delete the partitions and establish a new partition table.

If you're still shakey on what to do, just boot into the trial mode, hookup your internet, and pull up a formatting guide such as:
[http://www.ehow.com/how_8453693_format-drive-ubuntu-live-cd.html]("http://www.ehow.com/how_8453693_format-drive-ubuntu-live-cd.html")
which really simplifies the whole process into about four clicks or

[http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/]("http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/")
if you REALLY want to get rid of EVERYTHING on your hard drive.

Cheers!

---

### Post by Jake5 on 2012-04-02
Also just FYI, you don't need two Linux swap partitions. If you decide to dual boot again, you can place the swap file at the "far end" of your disk, and any installed OS's will be able to access it. I only know cause I made the mistake too. So don't be embarrassed.

---

### Post by Mark Phelps on 2012-04-02
Couple of points you need to consider (which have been overlooked so far) ...

First, 12.04 just recently entered Beta 2.  There is going to be a Release Candidate before it then goes to the final version.  Installing any pre-release version carries some risk as some stuff simply won't work.  BEFORE you install 12.04, you should read the Release Notes, and also visit the Precise Development forum to get an idea of the problems folks are facing using it.

Second, unless I missed it, none of the approaches so far actually "wipe" a drive. To wipe a drive, you have to OVERLAY the existing contents to the degree that the current contents can NOT be recovered.  Reinstalling, partition removal, reformatting -- NONE of these wipe the drive; instead, they only replace the partition info.  The file contents are still present on the drive, they're just hard to get to.

Wiping is not necessary for a clean install; reformatting is sufficient.  Wiping is only necessary if you want to clean a drive of all the current data -- so that NONE of it can be recovered.

---

### Post by fractalman on 2012-04-02
Well my advice would be....

back up any data you want to keep

then go here and download Dban (Dariks boot and nuke) and burn to disc

[http://www.dban.org/](http://www.dban.org/)

then set your pc to boot from a cd and run dban

depending on the size of your drive and how deep you want to clean it, dban can take a while but if you want to actually remove the data already on the drive then dban should leave it pretty much like new

if you're not too fussed then just re-format the drive

i like to dban my drive every few installs just to reduce any chances of old data interfering with the install or running of of an os

---

### Post by Cheesemill on 2012-04-02
> **fractalman said:**
> Well my advice would be....

back up any data you want to keep

then go here and download Dban (Dariks boot and nuke) and burn to disc

[http://www.dban.org/](http://www.dban.org/)

then set your pc to boot from a cd and run dban

depending on the size of your drive and how deep you want to clean it, dban can take a while but if you want to actually remove the data already on the drive then dban should leave it pretty much like new

if you're not too fussed then just re-format the drive

i like to dban my drive every few installs just to reduce any chances of old data interfering with the install or running of of an os

I find that nearly all of the dban wipes are overkill. All that is needed to prevent recovery of any data is just a simple one pass overwrite with zeros. A simple:
```
dd if=/dev/zero of=/dev/sda
```
Will completely wipe your drive to the point where no data is recoverable.

[SIZE=2][COLOR=Red]***WARNING***[/COLOR][/SIZE] - The above command will completely delete all data on the specified drive. Use at your own risk !!!

---

### Post by Hadaka on 2012-04-02
dd if=/dev/zero of=/dev/sda bs=512
*just to make sure its squeaky clean*

---

