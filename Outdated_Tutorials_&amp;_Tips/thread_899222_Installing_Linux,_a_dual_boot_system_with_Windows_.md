---
title: "Installing Linux, a dual boot system with Windows and Linux"
date: 2008-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by nucleuskore on 2008-08-24
Hi all
This is a Ubuntu only variant of a thread I started [here](http://www.thinkdigit.com/forum/showthread.php?t=96132)

PDF version of this guide - [http://www.mediafire.com/?vuvfmgfm02j](http://www.mediafire.com/?vuvfmgfm02j)
md5sum 42befee063ab7317d5791d8983ca6052
-------------------------------------------------------------------------------------------------------------

Installing linux alongside windows can be quite daunting for new users. The fear of losing data is always there, besides other problems like corrupting your boot record, getting a completely unusable system at the end, etc. The purpose of this tutorial is to simplify the process by the use of screenshots of an actual installation (a picture is equal to a thousand words someone said).

[size=+2]**_Assesing your hard disk, partitions_**[/size]
To install linux on your PC you should first make some free space available on your hard disk for the install. Click
on Start->Control Panel->Performance and Maintainance->Administrative Tools->Computer Management

[[IMG]http://img180.imageshack.us/img180/116/xp1su6.th.png[/IMG]](http://img180.imageshack.us/my.php?image=xp1su6.png) [[IMG]http://img359.imageshack.us/img359/7670/xp2fw4.th.png[/IMG]](http://img359.imageshack.us/my.php?image=xp2fw4.png) [[IMG]http://img519.imageshack.us/img519/4714/xp3ru7.th.png[/IMG]](http://img519.imageshack.us/my.php?image=xp3ru7.png) [[IMG]http://img128.imageshack.us/img128/2121/xp4ux7.th.png[/IMG]](http://img128.imageshack.us/my.php?image=xp4ux7.png) 

Click on Disk Management System

[[IMG]http://img128.imageshack.us/img128/9708/xp5hb3.th.png[/IMG]](http://img128.imageshack.us/my.php?image=xp5hb3.png)

I have covered a few possible scenarios you might face.

[list]
[*]You have a 40 GB hard disk made into four more or less equal partitions. You can see your partitions and their corresponding drive letters (C,D,etc.) in the figure below.

[[IMG]http://img128.imageshack.us/img128/9708/xp5hb3.th.png[/IMG]](http://img128.imageshack.us/my.php?image=xp5hb3.png)

The idea is to free at least 20 GB for our linux install. This might seem like a lot and other's might disagree, but if you are looking for a full experience I'd recommend it. We will need this space later to make three partitons

Swap - Space=1.5 to 2 times your RAM
Root (designated as /) - stores your OS and system files, programs, etc. - Space approx 8GB
Home (designated as /home) - like the Documents and Settings folder of Windows XP. Stores your preferences, bookmarks, wallpaper, My Documents and Desktop. - Space - remaining space

The / is like the base directory in linux, into which all other directories (folders) are incorporated or "mounted". I took a very long time to understand the concept of "mounting". Don't worry about it for now, you will understand when the time is right.

---

### Post by nucleuskore on 2008-08-24
So here you will have to backup the data in the last two partitions by writing it to a CD or DVD or copying to another hard disk, and delete them as shown below

[[IMG]http://img374.imageshack.us/img374/217/xp6tg7.th.png[/IMG]](http://img374.imageshack.us/my.php?image=xp6tg7.png) [[IMG]http://img376.imageshack.us/img376/813/xp7oy8.th.png[/IMG]](http://img376.imageshack.us/my.php?image=xp7oy8.png) [[IMG]http://img523.imageshack.us/img523/6247/xp8mz9.th.png[/IMG]](http://img523.imageshack.us/my.php?image=xp8mz9.png) [[IMG]http://img201.imageshack.us/img201/1411/xp9mp1.th.png[/IMG]](http://img201.imageshack.us/my.php?image=xp9mp1.png)

[*]You have a 40 GB hard disk with only one partition "C". This is the scenario in many laptops. The other partition may be a back up or EISA partition. Now you're in for a rough ride. If you have made the back up CDs and DVDs from the EISA partition using the tool the vendor has provided you, you can delete the EISA partiton but you will have to first backup your data, delete all partition using a partition manager like GParted, make a small C partiton, say 20 GB, with the ntfs filesystem using GParted, and then boot from your recovery cd/dvd and restore the system.

[/list]

Resizing Partitions is something I do not recommend with any tool unless you have uninterrupted power supply in your part of the country/world or a power back up solution that lasts for a few hours.

[size=+2]**_Hardware check_**[/size]
With the advances in Linux and the new kernels this step may not be necessary, but will help you in troubleshooting later if required.
Click on Start->Control Panel->Performance and Maintainance->System
Click on the Hardware tab->Device Manager button
Make a note of the model numbers of your monitor, graphics card (display adapter), and any other devices.

[size=+2]**_Installing Linux_**[/size]
You are now going to install linux to the empty space on your hard disk that you prepared in the earlier step. Linux by itself is not a single monolithic entity unlike some popular operating systems. It is very much a collaborative effort. It consists of a core (also called a kernel) on which the entire system is built on an runs. Linux is modular. As you become more experienced, you will realise that you can add and remove modules depending on your requirement and create a highly customised system, to make a long story short - NO **** is forced down your throat. No hidden agandas, no long cryptic EULAs (the thingy which you blindly scroll down and click "I agree" without batting an eyelid), and no leash up your **** (pardon the bad language but that's exactly how I feel).

[size=+2]**_So let's get started !!_**[/size]

The first step in installing any linux distro involves booting from a live media, usually a CD or DVD.
Ubuntu CDs are available for free from [SHIPIT](https://shipit.ubuntu.com)
You can also download it from Ubuntu website or ask a LUG (Linux User Group) near you. 

To boot from the cd or dvd your bios should have it as the first boot device. Alternatively some bios allow you to select the boot device. The key used for this varies with different manufacturers. To see if your bios has a boot device select menu please refer the manual of your motherboard or take help from a more experienced friend. 

I suggest you try the following - insert the cd or dvd and start your pc. If your pc boots too fast simply restart windows with the cd or dvd in the drive and see what happens. Very often the optical drive would have been set as the first boot device and the system boots from the cd automatically. If it still goes to windows and refuses to boot from your cd or dvd then you will have to adjust your bios settings or search for a boot menu as I described earlier.

_Ubuntu Installation_
If your pc boot successfully from your ubuntu cd you will see this screen

[[IMG]http://img119.imageshack.us/img119/5418/xp13am8.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xp13am8.png)

It is asking you to select the language. Use your arrow keys to select the system language and press ENTER. You will then get this screen

[[IMG]http://img119.imageshack.us/img119/8603/xp14lc7.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xp14lc7.png)

Use the Up and Down arrow keys on your keyboard to select the option Install Ubuntu and press ENTER. The system will start booting.

[[IMG]http://img509.imageshack.us/img509/1696/xp15gg6.th.png[/IMG]](http://img509.imageshack.us/my.php?image=xp15gg6.png) [[IMG]http://img401.imageshack.us/img401/4421/xp16kt4.th.png[/IMG]](http://img401.imageshack.us/my.php?image=xp16kt4.png)

---

### Post by nucleuskore on 2008-08-24
You will see the Welcome screen in your language. Make sure your language selection is right and click forward

[[IMG]http://img390.imageshack.us/img390/2749/xp17bz9.th.png[/IMG]](http://img390.imageshack.us/my.php?image=xp17bz9.png)

Select your timezone from the list, it is arranged by continent, and click forward

[[IMG]http://img87.imageshack.us/img87/9237/xp18hh3.th.png[/IMG]](http://img87.imageshack.us/my.php?image=xp18hh3.png)

Select your keyboard type, most common is US International (see picture below), but make sure and use the test box made available to you to check your selection. Check not only for alphabets, capital and small, but also for special characters like ' " ? / + ; If all these are correct then your choice of keybord layout is fine, click forward

[[IMG]http://img230.imageshack.us/img230/3234/xp19nn2.th.png[/IMG]](http://img230.imageshack.us/my.php?image=xp19nn2.png)

You will now be presented with the partitioning options. Ubuntu "intelligently" offers to resize your windows partition and do everything automatically. I advise AGAINST using this option, and instead select the manual option and click forward

[[IMG]http://img230.imageshack.us/img230/9577/xp20lu4.th.png[/IMG]](http://img230.imageshack.us/my.php?image=xp20lu4.png)

You will now come to a screen which shows you the layout of partiitons on your hard disk. Note the nomenclature used in linux. The first hard disk is labelled as /dev/sda Partitions withing this are labelled as /dev/sda1 /dev/sda2 so on and so forth. Now in this example, there are some numbers missing inbetween as you can see. These have gone for the extended partition. /dev/sda5 is actually my D drive, but as it is not formatted it shows up as an unknown partition. /dev/sda1 is the C drive and has an ntfs filesystem.

[[IMG]http://img295.imageshack.us/img295/7818/xp21rn6.th.png[/IMG]](http://img295.imageshack.us/my.php?image=xp21rn6.png)

Select free space and click on the "New Partition" button as shown below

[[IMG]http://img87.imageshack.us/img87/4752/xp22ze6.th.png[/IMG]](http://img87.imageshack.us/my.php?image=xp22ze6.png)

Select type of partition logical, size 1.5 times your RAM (512 in this example), location for new partition Begining, Use as: swap area, and click OK

[[IMG]http://img116.imageshack.us/img116/7241/xp23lt3.th.png[/IMG]](http://img116.imageshack.us/my.php?image=xp23lt3.png)

---

### Post by nucleuskore on 2008-08-24
The proposed partition table layout will get updated as shown

[[IMG]http://img116.imageshack.us/img116/7940/xp24dt2.th.png[/IMG]](http://img116.imageshack.us/my.php?image=xp24dt2.png) [[IMG]http://img329.imageshack.us/img329/6503/xp25nf7.th.png[/IMG]](http://img329.imageshack.us/my.php?image=xp25nf7.png)

and you will get this

[[IMG]http://img148.imageshack.us/img148/4213/xp26ee2.th.png[/IMG]](http://img148.imageshack.us/my.php?image=xp26ee2.png)

Again select free space and click New Partition. Select type of partition logical, size 8000 MB or more, location for new partition Begining, Use as: Ext 3 journaling file system, mount point: / and click OK

[[IMG]http://img148.imageshack.us/img148/3279/xp27ju6.th.png[/IMG]](http://img148.imageshack.us/my.php?image=xp27ju6.png)

The proposed partition table layout will get updated. Again select free space and click New Partition. Select type of partition logical, size: don't touch anything, let it be as it is, location for new partition Begining, Use as: Ext 3 journaling file system, mount point: /home and click OK. Note that you will manually have to type in the mount point in the box provided as /home

[[IMG]http://img134.imageshack.us/img134/623/xp28du2.th.png[/IMG]](http://img134.imageshack.us/my.php?image=xp28du2.png)

This is how your proposed partition table layout finally looks like. 

[[IMG]http://img355.imageshack.us/img355/4086/xp29oi7.th.png[/IMG]](http://img355.imageshack.us/my.php?image=xp29oi7.png) [[IMG]http://img127.imageshack.us/img127/8548/xp32sk4.th.png[/IMG]](http://img127.imageshack.us/my.php?image=xp32sk4.png)


Remember, nothing has actually happened to your partitions as yet, this is just a proposed layout, so if you make a mistake in your newly created linux partitions you can simply go back and redo the partitioning. **Note the partition table down in a book and keep it safely.** You will require it to rescue your system if need be, and to install the GAG boot loader later (optional but desirable. Click Forward.

You will now be asked some details about yourself. You will have to give a password. Make sure you don't forget it. Click Forward

[[IMG]http://img46.imageshack.us/img46/4590/xp30vt9.th.png[/IMG]](http://img46.imageshack.us/my.php?image=xp30vt9.png)

---

### Post by nucleuskore on 2008-08-24
Import your windows settings. This is optional you can leave it unchecked as shown in the second figure and click forward.

[[IMG]http://img46.imageshack.us/img46/6974/xp31fe3.th.png[/IMG]](http://img46.imageshack.us/my.php?image=xp31fe3.png)

Click Install, the installation will begin with the formatting and copying of files to your hard disk.
[[IMG]http://img171.imageshack.us/img171/3966/xp33fo8.th.png[/IMG]](http://img171.imageshack.us/my.php?image=xp33fo8.png)[[IMG]http://img206.imageshack.us/img206/5447/xp34sj6.th.png[/IMG]](http://img206.imageshack.us/my.php?image=xp34sj6.png)

At the end of installation click on the Restart Now button

[[IMG]http://img122.imageshack.us/img122/2033/xp38go7.th.png[/IMG]](http://img122.imageshack.us/my.php?image=xp38go7.png)

As the system shuts down, you will get a message telling you to remove the cd from the drive and press ENTER to reboot the system which you must do.
[[IMG]http://img99.imageshack.us/img99/1012/xp39by7.th.png[/IMG]](http://img99.imageshack.us/my.php?image=xp39by7.png)

As the system boots for the first time after your installation, you will see this screen. This is the GRUB boot loader from where you can choose between Ubuntu Linux (first entry) and Windows (last entry), using the up and down arrow keys on your keyboard and press ENTER. If you do not respond in 10 seconds it will boot to Ubuntu automatically.

[[IMG]http://img376.imageshack.us/img376/927/xp40kd2.th.png[/IMG]](http://img376.imageshack.us/my.php?image=xp40kd2.png)

Enjoy your Ubuntu Linux!!!
---------------------------------------------------------------------------
Installing the GAG Bootloader

This may be difficult for first time users who have no idea on command line usage in dos or windows. If you are familiar with the cd command to browse directories then you may proceed with Method 1, else use Method 2.

Ubuntu and OpenSUSE by default use the GRUB bootloader which is again, by default, written to the first sector of your hard disk, a location for the Master Boot Record (MBR). If anything happens to this boot record because of a virus attack or a system bug your system simply won't boot. Updating Ubuntu or OpenSUSE over the internet, updates (especially kernel updates) sometimes mess up the boot loader because of wrong entries or pointing. You'll find enough of these instances in the official forums. This can be avoided if you put your GRUB bootloader in your / partition instead of your MBR. In your MBR you can install any third party bootloader like GAG as I have described below. This is optional and if you are happy with GRUB you need not install GAG. If you want to learn more about GRUB go through [this wonderful article](http://www.dedoimedo.com/computers/grub.html).

Download GAG from here

[http://www.mediafire.com/?q1hhft5azyi](http://www.mediafire.com/?q1hhft5azyi)

You can also get the latest version from here
[http://gag.sourceforge.net/download.html](http://gag.sourceforge.net/download.html)

Save it on your linux desktop. 

Installation Method 1: 
Right click on the file and select Extract here. Open a terminal and browse to the folder using the cd command. In that folder enter the linux folder using the cd command.

At prompt type

sudo ./copy-file.sh

and press ENTER

Then type

sudo ./gag-install /dev/sda

and press ENTER. If this does not work (in OpenSUSE), type su and press ENTER to become root, and then type

./gag-install /dev/sda

and press ENTER.

Restart your PC

Installation Method 2 (EASY): 
Right click on the file you just downloaded and select Extract here. Open the folder, you will find a file cdrom.iso in it, write that file to a cd using the default cd writing software in linux (simply double click on it and burn). Restart your PC and boot from the cd.


Whichever of the above you have followed, you will now get this screen

[[IMG]http://img123.imageshack.us/img123/7092/xp48gc6.th.png[/IMG]](http://img123.imageshack.us/my.php?image=xp48gc6.png)

Press 4 to install GAG. You will get this screen next

[[IMG]http://img123.imageshack.us/img123/5369/xp49hk2.th.png[/IMG]](http://img123.imageshack.us/my.php?image=xp49hk2.png)

---

### Post by nucleuskore on 2008-08-24
Select your keyboard (usually 1 in India)

then your language

[[IMG]http://img411.imageshack.us/img411/1084/xp50ra6.th.png[/IMG]](http://img411.imageshack.us/my.php?image=xp50ra6.png)

You will then come to this screen. press S to setup the bootloader

[[IMG]http://img123.imageshack.us/img123/5121/xp51ri0.th.png[/IMG]](http://img123.imageshack.us/my.php?image=xp51ri0.png)

The alphabets you have to press to execute a function are highlighted in red in the GAG set up screen. Keys are case insensitive. Press A to add an operating system

[[IMG]http://img155.imageshack.us/img155/6761/xp53rz0.th.png[/IMG]](http://img155.imageshack.us/my.php?image=xp53rz0.png)

As you can see, partition A is the floppy, B is the first windows partition, so press B

[[IMG]http://img120.imageshack.us/img120/9020/xp54ni5.th.png[/IMG]](http://img120.imageshack.us/my.php?image=xp54ni5.png)

You will now have to type a name, say Windows
[[IMG]http://img155.imageshack.us/img155/9198/xp55kd5.th.png[/IMG]](http://img155.imageshack.us/my.php?image=xp55kd5.png)


You will have to now type a password, optionally, so press ENTER to avoid giving one
[[IMG]http://img155.imageshack.us/img155/8981/xp56io8.th.png[/IMG]](http://img155.imageshack.us/my.php?image=xp56io8.png)


You now have to select an icon, Press C for windows
[[IMG]http://img120.imageshack.us/img120/4530/xp57gs8.th.png[/IMG]](http://img120.imageshack.us/my.php?image=xp57gs8.png)


Now you will come back to this screen
[[IMG]http://img353.imageshack.us/img353/4060/xp58ui9.th.png[/IMG]](http://img353.imageshack.us/my.php?image=xp58ui9.png)

---

### Post by nucleuskore on 2008-08-24
Press A to add an operating system

[[IMG]http://img223.imageshack.us/img223/6342/xp59ym9.th.png[/IMG]](http://img223.imageshack.us/my.php?image=xp59ym9.png)

Now if you remember the first partition you made was swap, so that's D, followed by /, that's E over here (refer the partition table in your notes). So press E (in this example).

You will now have to type a name, say Linux
[[IMG]http://img353.imageshack.us/img353/9378/xp60ro3.th.png[/IMG]](http://img353.imageshack.us/my.php?image=xp60ro3.png)

You will have to now type a password, optionally, so press ENTER to avoid giving one
[[IMG]http://img155.imageshack.us/img155/8981/xp56io8.th.png[/IMG]](http://img155.imageshack.us/my.php?image=xp56io8.png)


You now have to select an icon, Press D for Linux
[[IMG]http://img120.imageshack.us/img120/4530/xp57gs8.th.png[/IMG]](http://img120.imageshack.us/my.php?image=xp57gs8.png)


Now you will come back to this screen
[[IMG]http://img353.imageshack.us/img353/4060/xp58ui9.th.png[/IMG]](http://img353.imageshack.us/my.php?image=xp58ui9.png)


Press H to save in the hard disk, you will get this message, press ENTER

[[IMG]http://img84.imageshack.us/img84/6605/xp61fn0.th.png[/IMG]](http://img84.imageshack.us/my.php?image=xp61fn0.png)

Press R to return to the main menu, you should see this

[[IMG]http://img329.imageshack.us/img329/9237/xp63gf9.th.png[/IMG]](http://img329.imageshack.us/my.php?image=xp63gf9.png)

Extra options in the setup include setting a timer for a default OS to boot.
Read the index.html file in the docs folder of the gag file you downloaded.
All the best !!!

---

### Post by Sef on 2008-08-24
Moved to Community Cafe.

---

### Post by hlamborn on 2008-08-24
THANK YOU nucleuskore ! I'm going to install Kubuntu 8.04.1 KDE4
on a new external HD, 320 Gig, preformatted NTFS. Your Pics
and descriptions answered most of my questions. But I understand
this version of Kubuntu can read and write to NTFS files. So,
I assume I can set up 3 partions for Kubuntu on the new
external usb drive. One is for swap (1. 5 to 2 times RAM)
correct ? and 2 other but I don't understand what size I
should make them and why 2 more ? Since this version of Kubuntu
writes & reads NTFS files can't I make the 2 other linux
partitions NTFS ? I only want to partition a total of 100
Gig on the new external usb HD and leave the balance as
free space for now. see other thread posted today by me,
hlamborn, [email]hlamborn@charter.net[/email]....

---

### Post by confused57 on 2008-08-24
Excellent tutorial, the screenshot illustrations will be extremely helpful to anyone installing Ubuntu for the first time.

---

### Post by voteforpedro36 on 2008-08-24
> **hlamborn said:**
> THANK YOU nucleuskore ! I'm going to install Kubuntu 8.04.1 KDE4
on a new external HD, 320 Gig, preformatted NTFS. Your Pics
and descriptions answered most of my questions. But I understand
this version of Kubuntu can read and write to NTFS files. So,
I assume I can set up 3 partions for Kubuntu on the new
external usb drive. One is for swap (1. 5 to 2 times RAM)
correct ? and 2 other but I don't understand what size I
should make them and why 2 more ? Since this version of Kubuntu
writes & reads NTFS files can't I make the 2 other linux
partitions NTFS ? I only want to partition a total of 100
Gig on the new external usb HD and leave the balance as
free space for now. see other thread posted today by me,
hlamborn, [email]hlamborn@charter.net[/email]....


Don't use NTFS as the filesystem for Kubuntu. While it may work, it's not exactly encouraged. Instead when you're editing the partitions, just select it to format as Ext3.

---

### Post by nucleuskore on 2008-08-24
PDF version of this guide - [http://www.mediafire.com/?b1zushbgmeo](http://www.mediafire.com/?b1zushbgmeo)

---

### Post by nucleuskore on 2008-11-02
Installing linux alongside windows can be quite daunting for new users. The fear of losing data is always there, besides other problems like corrupting your boot record, getting a completely unusable system at the end, etc. 
The purpose of this tutorial is to simplify the process by the use of screenshots of an actual installation of Ubuntu 8.10 (a picture is equal to a thousand words someone said).

[size=+2]**_Assesing your hard disk, partitions_**[/size]
To install linux on your PC you should first make some free space available on your hard disk for the install. Click
on Start->Control Panel->Performance and Maintainance->Administrative Tools->Computer Management

[[IMG]http://img180.imageshack.us/img180/116/xp1su6.th.png[/IMG]](http://img180.imageshack.us/my.php?image=xp1su6.png) [[IMG]http://img359.imageshack.us/img359/7670/xp2fw4.th.png[/IMG]](http://img359.imageshack.us/my.php?image=xp2fw4.png) [[IMG]http://img519.imageshack.us/img519/4714/xp3ru7.th.png[/IMG]](http://img519.imageshack.us/my.php?image=xp3ru7.png) [[IMG]http://img128.imageshack.us/img128/2121/xp4ux7.th.png[/IMG]](http://img128.imageshack.us/my.php?image=xp4ux7.png) 

Click on Disk Management System

[[IMG]http://img128.imageshack.us/img128/9708/xp5hb3.th.png[/IMG]](http://img128.imageshack.us/my.php?image=xp5hb3.png)

I have covered a few possible scenarios you might face.

[list]
[*]You have a 40 GB hard disk made into four more or less equal partitions. You can see your partitions and their corresponding drive letters (C,D,etc.) in the figure below.

[[IMG]http://img128.imageshack.us/img128/9708/xp5hb3.th.png[/IMG]](http://img128.imageshack.us/my.php?image=xp5hb3.png)

The idea is to free at least 20 GB for our linux install. This might seem like a lot and other's might disagree, but if you are looking for a full experience I'd recommend it. We will need this space later to make three partitons

Swap - Space=1.5 to 2 times your RAM
Root (designated as /) - stores your OS and system files, programs, etc. - Space approx 8GB
Home (designated as /home) - like the Documents and Settings folder of Windows XP. Stores your preferences, bookmarks, wallpaper, My Documents and Desktop. - Space - remaining space

The / is like the base directory in linux, into which all other directories (folders) are incorporated or "mounted". I took a very long time to understand the concept of "mounting". Don't worry about it for now, you will understand when the time is right.

---

### Post by nucleuskore on 2008-11-02
So here you will have to backup the data in the last two partitions by writing it to a CD or DVD or copying to another hard disk, and delete them as shown below

[[IMG]http://img374.imageshack.us/img374/217/xp6tg7.th.png[/IMG]](http://img374.imageshack.us/my.php?image=xp6tg7.png) [[IMG]http://img376.imageshack.us/img376/813/xp7oy8.th.png[/IMG]](http://img376.imageshack.us/my.php?image=xp7oy8.png) [[IMG]http://img523.imageshack.us/img523/6247/xp8mz9.th.png[/IMG]](http://img523.imageshack.us/my.php?image=xp8mz9.png) [[IMG]http://img201.imageshack.us/img201/1411/xp9mp1.th.png[/IMG]](http://img201.imageshack.us/my.php?image=xp9mp1.png)

[*]You have a 40 GB hard disk with only one partition "C". This is the scenario in many laptops. The other partition may be a back up or EISA partition. Now you're in for a rough ride. If you have made the back up CDs and DVDs from the EISA partition using the tool the vendor has provided you, you can delete the EISA partiton but you will have to first backup your data, delete all partition using a partition manager like GParted, make a small C partiton, say 20 GB, with the ntfs filesystem using GParted, and then boot from your recovery cd/dvd and restore the system.

[/list]

Resizing Partitions is something I do not recommend with any tool unless you have uninterrupted power supply in your part of the country/world or a power back up solution that lasts for a few hours.

[size=+2]**_Hardware check_**[/size]
With the advances in Linux and the new kernels this step may not be necessary, but will help you in troubleshooting later if required.
Click on Start->Control Panel->Performance and Maintainance->System
Click on the Hardware tab->Device Manager button
Make a note of the model numbers of your monitor, graphics card (display adapter), and any other devices.

[size=+2]**_Installing Linux_**[/size]
You are now going to install linux to the empty space on your hard disk that you prepared in the earlier step. Linux by itself is not a single monolithic entity unlike some popular operating systems. It is very much a collaborative effort. It consists of a core (also called a kernel) on which the entire system is built on an runs. Linux is modular. As you become more experienced, you will realise that you can add and remove modules depending on your requirement and create a highly customised system, to make a long story short - NO **** is forced down your throat. No hidden agandas, no long cryptic EULAs (the thingy which you blindly scroll down and click "I agree" without batting an eyelid), and no leash up your **** (pardon the bad language but that's exactly how I feel).

[size=+2]**_So let's get started !!_**[/size]

The first step in installing any linux distro involves booting from a live media, usually a CD or DVD.
Ubuntu CDs are available for free from [SHIPIT](https://shipit.ubuntu.com)
You can also download it from Ubuntu website or ask a LUG (Linux User Group) near you. 

To boot from the cd or dvd your bios should have it as the first boot device. Alternatively some bios allow you to select the boot device. The key used for this varies with different manufacturers. To see if your bios has a boot device select menu please refer the manual of your motherboard or take help from a more experienced friend. 

I suggest you try the following - insert the cd or dvd and start your pc. If your pc boots too fast simply restart windows with the cd or dvd in the drive and see what happens. Very often the optical drive would have been set as the first boot device and the system boots from the cd automatically. If it still goes to windows and refuses to boot from your cd or dvd then you will have to adjust your bios settings or search for a boot menu as I described earlier.

[size=+2]*_Ubuntu Installation_*[/size]

If your pc boot successfully from your ubuntu cd you will see this screen

[[IMG]http://img119.imageshack.us/img119/5418/xp13am8.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xp13am8.png)

It is asking you to select the language. Use your arrow keys to select the system language and press ENTER. You will then get this screen

[[IMG]http://img119.imageshack.us/img119/8603/xp14lc7.th.png[/IMG]](http://img119.imageshack.us/my.php?image=xp14lc7.png)

Use the Up and Down arrow keys on your keyboard to select the option Install Ubuntu and press ENTER. The system will start booting.

[[IMG]http://img509.imageshack.us/img509/1696/xp15gg6.th.png[/IMG]](http://img509.imageshack.us/my.php?image=xp15gg6.png) [[IMG]http://img401.imageshack.us/img401/4421/xp16kt4.th.png[/IMG]](http://img401.imageshack.us/my.php?image=xp16kt4.png)

---

### Post by nucleuskore on 2008-11-02
You will see the Welcome screen in your language. Make sure your language selection is right and click forward

[[IMG]http://img504.imageshack.us/img504/843/a03cs5.th.png[/IMG]](http://img504.imageshack.us/my.php?image=a03cs5.png)

Select your timezone from the list, it is arranged by continent, and click forward

[[IMG]http://img137.imageshack.us/img137/9566/a04qq8.th.png[/IMG]](http://img137.imageshack.us/my.php?image=a04qq8.png)

Select your keyboard type, most common is US International with AltGr deadkeys (see picture below), but make sure and use the test box made available to you to check your selection. Check not only for alphabets, capital and small, but also for special characters like ' " ? / + ; If all these are correct then your choice of keyboard layout is fine, click forward

[[IMG]http://img143.imageshack.us/img143/6953/a05br1.th.png[/IMG]](http://img143.imageshack.us/my.php?image=a05br1.png)

You will now be presented with the partitioning options. Ubuntu "intelligently" offers to resize your windows partition and do everything automatically. I advise AGAINST using this option, and instead select the manual option and click forward

[[IMG]http://img143.imageshack.us/img143/1231/a07ac6.th.png[/IMG]](http://img143.imageshack.us/my.php?image=a07ac6.png)

You will now come to a screen which shows you the layout of partiitons on your hard disk. Note the nomenclature used in linux. The first hard disk is labelled as /dev/sda Partitions withing this are labelled as /dev/sda1 /dev/sda2 so on and so forth. Now in this example, there are some numbers missing inbetween as you can see. These have gone for the extended partition. Logical partiitons start as /dev/sda5, /dev/sda6, and so on. /dev/sda1 to /dev/sda4 are reserved for primary partitions. Any hard disk can have only four primary partiitons.  /dev/sda5 is actually my D drive with ntfs filesystem. /dev/sda1 is the C drive and has an ntfs filesystem.

[[IMG]http://img205.imageshack.us/img205/7551/a18to9.th.png[/IMG]](http://img205.imageshack.us/my.php?image=a18to9.png)

Select free space and click on the "New Partition" button as shown below

[[IMG]http://img508.imageshack.us/img508/8599/a19om7.th.png[/IMG]](http://img508.imageshack.us/my.php?image=a19om7.png)

Select type of partition logical, size 1.5 times your RAM (512 in this example), location for new partition Begining, Use as: swap area, and click OK

[[IMG]http://img220.imageshack.us/img220/1060/a20uu2.th.png[/IMG]](http://img220.imageshack.us/my.php?image=a20uu2.png)

The proposed partition table layout will get updated as shown

[[IMG]http://img220.imageshack.us/img220/6524/a21fx8.th.png[/IMG]](http://img220.imageshack.us/my.php?image=a21fx8.png)

---

### Post by nucleuskore on 2008-11-02
Again select free space and click New Partition. Select type of partition logical, size 10000 MB or more, location for new partition Begining, Use as: Ext 3 journaling file system, mount point: / and click OK

[[IMG]http://img391.imageshack.us/img391/4653/a22ao2.th.png[/IMG]](http://img391.imageshack.us/my.php?image=a22ao2.png)

The proposed partition table layout will get updated.

[[IMG]http://img391.imageshack.us/img391/5883/a23ou6.th.png[/IMG]](http://img391.imageshack.us/my.php?image=a23ou6.png)

Again select free space and click New Partition. Select type of partition logical, size: don't touch anything, let it be as it is, location for new partition Begining, Use as: Ext 3 journaling file system, mount point: /home and click OK. Note that you will manually have to type in the mount point in the box provided as /home

[[IMG]http://img45.imageshack.us/img45/7917/a24is7.th.png[/IMG]](http://img45.imageshack.us/my.php?image=a24is7.png)

This is how your proposed partition table layout finally looks like. 

[[IMG]http://img383.imageshack.us/img383/6113/a25ac3.th.png[/IMG]](http://img383.imageshack.us/my.php?image=a25ac3.png)

Remember, nothing has actually happened to your partitions as yet, this is just a proposed layout, so if you make a mistake in your newly created linux partitions you can simply go back and redo the partitioning. CLick Forward.

You will now be asked some details about yourself. You will have to give a password. Make sure you don't forget it. Tick the box for auto login if you do not wish to login each time you boot the system. Click Forward

[[IMG]http://img383.imageshack.us/img383/4049/a26ic3.th.png[/IMG]](http://img383.imageshack.us/my.php?image=a26ic3.png)

Import your windows settings. This is optional you can leave it unchecked as shown in the second figure and click forward.

[[IMG]http://img230.imageshack.us/img230/7727/a27wu2.th.png[/IMG]](http://img230.imageshack.us/my.php?image=a27wu2.png)

Click Install, the installation will begin with the formatting and copying of files to your hard disk.
[[IMG]http://img530.imageshack.us/img530/1589/a28rd5.th.png[/IMG]](http://img530.imageshack.us/my.php?image=a28rd5.png) [[IMG]http://img530.imageshack.us/img530/7595/a29ow3.th.png[/IMG]](http://img530.imageshack.us/my.php?image=a29ow3.png)

---

### Post by nucleuskore on 2008-11-02
[[IMG]http://img145.imageshack.us/img145/6176/a30wo6.th.png[/IMG]](http://img145.imageshack.us/my.php?image=a30wo6.png) [[IMG]http://img84.imageshack.us/img84/6581/a31nc9.th.png[/IMG]](http://img84.imageshack.us/my.php?image=a31nc9.png)

At the end of installation click on the Restart Now button

[[IMG]http://img84.imageshack.us/img84/262/a32ye1.th.png[/IMG]](http://img84.imageshack.us/my.php?image=a32ye1.png)

As the system shuts down, you will get a message telling you to remove the cd from the drive and press ENTER to reboot the system which you must do.
[[IMG]http://img338.imageshack.us/img338/2087/a33ig7.th.png[/IMG]](http://img338.imageshack.us/my.php?image=a33ig7.png) [[IMG]http://img91.imageshack.us/img91/9201/a34we3.th.png[/IMG]](http://img91.imageshack.us/my.php?image=a34we3.png)

As the system boots for the first time after your installation, you will see this screen. This is the GRUB boot loader from where you can choose between Ubuntu Linux (first entry) and Windows (last entry), using the up and down arrow keys on your keyboard and press ENTER. If you do not respond in 10 seconds it will boot to Ubuntu automatically.

[[IMG]http://img389.imageshack.us/img389/1473/a35ci3.th.png[/IMG]](http://img389.imageshack.us/my.php?image=a35ci3.png)

Enjoy your Ubuntu !!!

Optional: Installing the GAG Bootloader
Go to post number 23 of this thread or click [here](http://www.thinkdigit.com/forum/showthread.php?t=96132#23)

Your system will boot up and you'll get the login screen, enter your user name and password to login.

[[IMG]http://img508.imageshack.us/img508/8610/a36rl6.th.png[/IMG]](http://img508.imageshack.us/my.php?image=a36rl6.png) [[IMG]http://img521.imageshack.us/img521/7752/a37if0.th.png[/IMG]](http://img521.imageshack.us/my.php?image=a37if0.png)

---

### Post by nucleuskore on 2008-11-02
[[IMG]http://img393.imageshack.us/img393/6686/a38vr6.th.png[/IMG]](http://img393.imageshack.us/my.php?image=a38vr6.png)

This is how your desktop looks like

[[IMG]http://img393.imageshack.us/img393/7857/a39mi8.th.png[/IMG]](http://img393.imageshack.us/my.php?image=a39mi8.png)

Let's explore Ubuntu. On the top left of your screen, you have a menu - "Applications". Click on it.

[[IMG]http://img361.imageshack.us/img361/2233/a40jt8.th.png[/IMG]](http://img361.imageshack.us/my.php?image=a40jt8.png)

Point your mouse to Accessories

[[IMG]http://img395.imageshack.us/img395/5854/a41gd2.th.png[/IMG]](http://img395.imageshack.us/my.php?image=a41gd2.png)

Among others, note these
Terminal - a program to access the linux shell. Used to pass commands to the system.
Tomboy notes - Sticky notes for your desktop

Point to Games

[[IMG]http://img359.imageshack.us/img359/7446/a42nf5.th.png[/IMG]](http://img359.imageshack.us/my.php?image=a42nf5.png)

Point to Graphics

[[IMG]http://img146.imageshack.us/img146/833/a43zv6.th.png[/IMG]](http://img146.imageshack.us/my.php?image=a43zv6.png)

GIMP is a powerful image editor. Use it to manipulate and enhance your photographs.
OpenOffice Draw is a nice drawing program. It is a part of the OpenOffice suite
XSane is a program to help you scan

Point to Internet

[[IMG]http://img146.imageshack.us/img146/8208/a44dx2.th.png[/IMG]](http://img146.imageshack.us/my.php?image=a44dx2.png)

Evolution is an email client like Microsoft Outlook
Firefox is a web browser
Pidgin is a instant messaging program that supports msn, yahoo, icq, gtalk and other protocols

Point to Office. You can see the tools for wordprocessing, presentations and spreadsheets.

[[IMG]http://img120.imageshack.us/img120/1808/a45ik7.th.png[/IMG]](http://img120.imageshack.us/my.php?image=a45ik7.png)

---

### Post by nucleuskore on 2008-11-02
Point to Sound and Video

[[IMG]http://img91.imageshack.us/img91/4200/a46qk5.th.png[/IMG]](http://img91.imageshack.us/my.php?image=a46qk5.png)

Brasero is a CD/DVD writing tool
Movie and audio players also seen

Point to Universal Access
A magnifier is seen

[[IMG]http://img243.imageshack.us/img243/7813/a47uy9.th.png[/IMG]](http://img243.imageshack.us/my.php?image=a47uy9.png)

Point to places
You can see shortcuts to various folders on your system. Documents, Music, pictures and Videos and all subfolders in Home Folder. Home Folder corresponds to /home  :)

[[IMG]http://img91.imageshack.us/img91/9483/a48fl5.th.png[/IMG]](http://img91.imageshack.us/my.php?image=a48fl5.png)

Point to System and then Preferences

[[IMG]http://img91.imageshack.us/img91/8017/a49zc7.th.png[/IMG]](http://img91.imageshack.us/my.php?image=a49zc7.png) [[IMG]http://img354.imageshack.us/img354/1931/a50dz4.th.png[/IMG]](http://img354.imageshack.us/my.php?image=a50dz4.png)


Note Appearance in this menu. Through that you can tweak your theme, desktop background, system fonts, and special effects (compiz).

Point to Administration

[[IMG]http://img201.imageshack.us/img201/3927/a51zt4.th.png[/IMG]](http://img201.imageshack.us/my.php?image=a51zt4.png)

Here you can configure your system, Hardware, drivers, software, networking, etc.

---

### Post by nucleuskore on 2008-11-02
At the top right hand corner is the button to shut down the system

[[IMG]http://img530.imageshack.us/img530/2071/a52dj8.th.png[/IMG]](http://img530.imageshack.us/my.php?image=a52dj8.png) [[IMG]http://img530.imageshack.us/img530/7489/a53hr0.th.png[/IMG]](http://img530.imageshack.us/my.php?image=a53hr0.png)

This may also be done from the system menu

To install multimedia packages (restricted), visit [http://medibuntu.org](http://medibuntu.org)

**For a quick deployment of multimedia packages refer this post**

[http://ubuntuforums.org/showthread.php?t=795859&page=3](http://ubuntuforums.org/showthread.php?t=795859&page=3)

---

