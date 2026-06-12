---
title: "Total Newby Needs Some Help Please, with Floppy Disks"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by Salicet on 2013-06-10
I am a total newby,. having just installed Ubuntu for the first time. I did so because I am so fed up with microsoft windows. However as a newby.  I have a load of floppy disks that I need to re-format. I have use the FAQ but can find no reference to formatting disks, be they floppies or other media. Can somebody please inform me how I go about formatting floppy disks please.

Regards

Salicet

---

### Post by 3rdalbum on 2013-06-10
I haven't used floppies since 1998 so don't take my word as Gospel.

I believe you have to temporarily load a kernel module to get access to floppy disks:

```
sudo modprobe floppy
```

Insert your floppy disk. When it appears on the desktop, right-click it and choose "Format...". Set your formatting options and do it.

Afterward, before pressing the eject button on the drive, right-click the floppy and choose "Eject" and then press the eject button.

After you have finished working with floppies, unload the kernel module:

```
sudo modprobe -r floppy
```

If this doesn't work, sorry - I'm basing this off old information that I have never used in practice.

---

### Post by Salicet on 2013-06-10
Hi 3adalbum,

    Thanks for your reply though sadly it does not help me. As I said in my original post I am a total newby. I used linux for the first time in my life about an hour ago. So sadly your advice to load a kernal module meand absolutely nothing to me. How do I go about installing this module and how do I then unload it when I have finished using floppies

Regards

Salicet

---

### Post by philinux on 2013-06-10
> **Salicet said:**
> I am a total newby,. having just installed Ubuntu for the first time. I did so because I am so fed up with microsoft windows. However as a newby.  I have a load of floppy disks that I need to re-format. I have use the FAQ but can find no reference to formatting disks, be they floppies or other media. Can somebody please inform me how I go about formatting floppy disks please.

Regards

Salicet

Open the software center and search for fdutils app. Install it. I've not used it as I've no floppy drive now. I would imaging it then allows right click on floppy and has a context menu to format etc.

Which ubuntu version are you running?

(I've changed your original post title. You''ll get  a better response in future by using a good thread title.) :p

---

### Post by Mark Phelps on 2013-06-10
Here's and old thread I found regarding floppy drives :  [http://ubuntuforums.org/showthread.php?t=1048932&page=2]("http://ubuntuforums.org/showthread.php?t=1048932&page=2")

---

### Post by mastablasta on 2013-06-10
> **Salicet said:**
> Hi 3adalbum,

Thanks for your reply though sadly it does not help me. As I said in my original post I am a total newby. I used linux for the first time in my life about an hour ago. So sadly your advice to load a kernal module meand absolutely nothing to me. How do I go about installing this module and how do I then unload it when I have finished using floppies

Regards

Salicet

open the terminal windows and copy the code he posted in it. first one loads floppy module second one unloads in.

in other words - most users do not need this module so there is no reaosn to keep it loaded but it seems it is there in case you need it.

good luck wiht formatting. 

if you need to destroy data on the floppies then dd command (destroy data) might be better option than format. format doesn't remove anything from floppy. ;-)

---

### Post by Salicet on 2013-06-10
Hi All,

     Thanks for all the replies. Maybe I should explain  that I am using version 13.01 of Ubuntu. When I boot Linux I get an icon for a floppy disk on the desktop. I assume that when Linux boots it checks to see what hardware in installed and loads the necessary software drivers. I can read floppy disks and copy from them no problem. What I can't do is write to them or format them. In an earlier post somebody said that If I right click on the floppy disk icon I would get an option to format. Sadly I do not get that option. 

regards

Salicet

---

### Post by dino99 on 2013-06-10
> **Salicet said:**
> Hi All,

     Thanks for all the replies. Maybe I should explain  that I am using version 13.01 of Ubuntu. When I boot Linux I get an icon for a floppy disk on the desktop. I assume that when Linux boots it checks to see what hardware in installed and loads the necessary software drivers. I can read floppy disks and copy from them no problem. What I can't do is write to them or format them. In an earlier post somebody said that If I right click on the floppy disk icon I would get an option to format. Sadly I do not get that option. 

regards

Salicet

stupid question, sorry, but have you checked first that these floppies are not write protected (hardware lock) ? (its the switch on the bottom left floppy corner)
then to format it, use gparted (the gnome formatting tool): it will first scan and list the devices/partitions, select the one named /dev/fd0 to apply fat32 (or else as you need)

---

### Post by philinux on 2013-06-10
> **Salicet said:**
> Hi All,

     Thanks for all the replies. Maybe I should explain  that I am using version 13.01 of Ubuntu. When I boot Linux I get an icon for a floppy disk on the desktop. I assume that when Linux boots it checks to see what hardware in installed and loads the necessary software drivers. I can read floppy disks and copy from them no problem. What I can't do is write to them or format them. In an earlier post somebody said that If I right click on the floppy disk icon I would get an option to format. Sadly I do not get that option. 

regards

Salicet

I think you may have to install an app called fdutils from the software center as I said before. The icon for software center will be in the launcher on the left hand of your desktop.

---

### Post by SeijiSensei on 2013-06-10
From the command prompt you can use:

```
mkfs -t vfat /dev/fd0
```

If you get a "permission denied," use "sudo mkfs" instead and enter your password when prompted. I"m pretty sure ordinary users can format floppies without root permissions, but it's been a long time since I used a device with a floppy drive.

That command will create a DOS ("vfat") file system onto the floppy.  In Linux, like all Unix systems, devices are referenced just like files.  There is no equivalent of an "A:" drive.  In Linux, if you have one floppy disk drive it is called /dev/fd0.  If you had another drive ("B:"), it would be /dev/fd1.

---

### Post by Salicet on 2013-06-10
I have opened a terminal and entered the code:  mkfs -t vfat /dev/fd0   and I get  the following  /dev/fd0: Persission denied

So no idea what to try now.

---

### Post by sandyd on 2013-06-10
> **Salicet said:**
> I have opened a terminal and entered the code:  mkfs -t vfat /dev/fd0   and I get  the following  /dev/fd0: Persission denied

So no idea what to try now.

try using
```

sudo mkfs -t vfat /dev/fd0
```
Some parts of the system require higher privileges to write to (which is what formatting is, essentially), and sudo allows you to raise your privileges so that you can write to those parts of the system.

Note that sudo will not show you the password you entered (will not even show dots dashes, or anything to indicate you entered a password)

---

### Post by Salicet on 2013-06-10
I have tried sudo mkfs -t vfat /dev/fd0 and sadly it does not work. Is it not possible to format a floppy from the terminal?

---

### Post by dino99 on 2013-06-10
> **Salicet said:**
> I have tried sudo mkfs -t vfat /dev/fd0 and sadly it does not work. Is it not possible to format a floppy from the terminal?

ask again: are your floppies set as "writable" (meaning not locked physicaly by the hardware switch) ??????

---

### Post by Salicet on 2013-06-11
I have spent a lot of time on this problem today and had success with writing to the internal floppy drive. I can read from it perfectly. However earlier today I tried using a external USB floppy drive and it reads and writes perfectly. Howeve I can't format old floppies as I need to know what the device number is, I know the internal drive is df0:  My question is, is it possible using the terminal to find the device number of the various devices installed in the system

---

### Post by Icetoad on 2013-06-11
->Install gparted, go to Gparted option 
->Devices 
->choose the floppy disk(identify by disk size) 
->right click the disk
->choose the formatting options 
->click on the check option on top.

---

### Post by philinux on 2013-06-11
Or search in the Dash for disk utility.

---

### Post by Salicet on 2013-06-12
Thanks for the help, sadly I still have a problem. I have downloaded gparted but can&#8217;t find it on my system. I tried looking at some YouTube videos as to how to use gparted, and I noticed that people start gparted by going to the system directory and then going to accessories  directory and choosing gparted. 

My System directory does not have an accessories option. When I open System I find only 3 options, Gigolo, Ibus and Task Manager. So how do I find gparted? is there a search option on xubuntu 13.04, on can I locate and run gparted from the Terminal?

---

### Post by plucky on 2013-06-12
Try ```
sudo fdformat /dev/fd0
``` from a terminal to format the floppy.

I believe the default is 1.44Mb,but you can use different formats.

Look at ```
man fdformat
``` for other formats.

After the format,you have to put a filesystem on the floppy,that is where the **mkfs** command comes in.

Good Luck

---

### Post by mastablasta on 2013-06-12
> **Salicet said:**
>  So how do I find gparted? is there a search option on xubuntu 13.04, on can I locate and run gparted from the Terminal?


i don't know about search function in Xubuntu at the moment, but 

```
gksu gparted

```
in terminal will run gparted with graphical sudo (i.e. with admin privileges)

otherwise 

```
lsusb
```

will list usb devices.

you can check in 
/dev
/media

directory to see if any new USB media device is plugged in.

> **/media **&#8211; Directory for mounting files systems on removable media like CD-ROM drives, floppy disks, and Zip drives.
**/dev **&#8211; Contains all device files. Linux treats each device as a special file. All such files are located in /dev.


---

### Post by Salicet on 2013-06-12
I have tried entering lsusb as you said and I get as follows:  Bus 005 Device 002: 03ee:6901 Mitsumi SmartDisk FFD  This does not give me the device name that linux needs to format this drive. I know that the internal floppy is seen as fd0 by the system, how do I find out what the system calls the first usb drive. if I could acertain that I am sure my problems would be over.

---

### Post by 3rdalbum on 2013-06-12
Linux numbers things logically (usually): After zero comes one, then two, etc.

So if the first floppy drive is /dev/fd0, the second floppy drive should be /dev/fd1

---

### Post by Salicet on 2013-06-12
I am sorry that does not appear to be the case. when I enter send sudo fformat /dev/fd1 into the terminal I get an error, No such device. I think because internal floppies are as you say fd0  fd1 fd2 etc. I think floppies mounted via usb have a different device name and that's what I am trying to find.

---

### Post by Dennis N on 2013-06-12
> **Salicet said:**
>  **I think floppies mounted via usb have a different device name and that's what I am trying to find.**

I mounted one using an external usb floppy drive, and ran **df -h** which displays all mounted file systems:

```
dn@Kayleigh:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        11G  4.7G  5.2G  48% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            996M  4.0K  996M   1% /dev
tmpfs           201M  864K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1004M  2.7M 1002M   1% /run/shm
none            100M   20K  100M   1% /run/user
/dev/sda9        34G   13G   19G  41% /media/dn/Lubuntu_13.04
/dev/sdb        1.4M 1016K  408K  72% /media/dn/1DD5-2643

```
It is on the bottom identified as **/dev/sdb**. As you can see, it mounts under **/media/<user>**

---

### Post by Salicet on 2013-06-12
Thanks very much for trying to help. When I enter df -h into the terminal I get exactly what is in your reply however when I try to format that device I get an error saying no such file or directory. So having spent two days trying to format a floppy disk I think I'll concede defeat. As the system can dead/write to floppies formatted by windows I'll do just that. It's by far the easyist option.

---

### Post by Dennis N on 2013-06-12
Seems we can read and write to a floppy in a USB drive provided it is already formatted by Windows, but we can't easily format them in Linux. 

The little tool described in this link sounds like what is needed for formatting a floppy **in a USB drive** from Linux. I haven't tried it, so can't say how well it works.

[http://www.geocities.jp/tedi_world/format_usbfdd_e.html](http://www.geocities.jp/tedi_world/format_usbfdd_e.html)

Also, gparted cannot do this job.

---

### Post by Salicet on 2013-06-13
Thanks very much, this likes just what I need. I will download it and give it a try. I'll let you know how things go.

---

### Post by Salicet on 2013-06-13
Joy of Joys !!! Success at last, it all works perfectly and I can now format floppies in a USB drive. Thanks very much for all your help.

---

### Post by Dennis N on 2013-06-13
Thanks for the report and glad to hear that little utility did the job. Reading the directions, I'm wondering what does **/dev/sg*** refer to where it says  "To use this program, both /dev/sd* and /dev/sg* need to be accessible."?

Added:

Tried it myself - works great. Now part of my tool kit in case I need to format a floppy disk.

---

