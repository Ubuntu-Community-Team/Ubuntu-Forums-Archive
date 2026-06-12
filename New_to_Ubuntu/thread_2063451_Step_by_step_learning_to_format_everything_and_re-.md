---
title: "Step by step learning to format everything and re-install from scratch"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by cp2819 on 2012-09-27
Hi 

As a complete beginner I realize that I cannot understand everything well without trying to do everything myself from the beginning.

My project is first to help myself to learn and then to help some other people like me, just because I dare not doing a lot of things thnking they will "damage" my system.

So, I will format everything and start from scratch, with all your helps to avoid me to do something wrong.


I just bought a new laptop with Ubuntu already installed from factory , and I want to learn to use Linux and Ubuntu on it...
but I dare not doing things...

_MY PROJECT :_

Now I decide to format everything and reinstall Ubuntu and other systems :

My laptop is :
ASUS 1225C-GRY004U  -- 11.6" LED screen
initially with Ubuntu 12.04 installed
CPU :Intel Atom N2600 / 1.6 GHz 
HDD : 500 Go
Mem : 2 Go DDR3 Sdram
Graphic Proc : Intel GMA 3600 


---------------------------------
1) Install  four systems
windows 7 + Ubuntu 12.04 + Debian + other system

2) configuring Grub2 for a quad boot, changing wallpaper Grub2 and color fonts

3) learn to mount, install everything from the beginning

4) configuring and customizing Ubuntu
----------------------------------

For the first step 
I plan to make partitions of my 500 Go HDD

win 7 : one main partition NTFS + one partition for data ( 100 Go + 70 Go ? what do you think ?)

ubuntu : 3 partitions : Root ,  Home and Swap  (which sizes ?)

Debian : 2 partitions : / and home , share the same swap partition

One other Linux distro (for testing purpose) : same as debian...

So please give me all your advices ... before I format and wipe everything from my new laptop

---

### Post by shreepads on 2012-09-27
The first thing to do would be to use Clonezilla and make a whole disk backup of the factory install on an external HD.

---

### Post by cp2819 on 2012-09-27
ok I will install clonezilla and make a backup of the wholedisk

when I type 
fdisk -l 

I see 3 partitions

/dev/sda1  hidden partition  W95 FAT32
/dev/sda2 Linux
/dev/sda3 swap


I have another little problem
all the texts in Terminal are not in English
because my native language is not English and my laptop is not configured in English

Is it possible to have those texts in English (to post here ) when my configured langiage is not English on my laptop ?

---

### Post by mips on 2012-09-27
Keep in mind that you can only create 4 primary partitions on a hard drive so you would need to create a extended partition if you need more than 4 primary partitions.

---

### Post by cp2819 on 2012-09-27
what do you suggest ? and what size for each partition ?

---

### Post by cp2819 on 2012-09-27
win 7 :  
100 Go primary : system
50 Go extended : data win 7

ubuntu :
100 Go primary :  root
40 Go extended : home

debian :
70 Go primary : root
40 Go extended : home

other system linux for testing
50 Go  primary : root
40 Go extended : home

2 Go : swap


any comment, suggestion or advice ?

---

### Post by davidbilla on 2012-09-27
Hi,

You may not need so much space for / (root) partition. It stores the system files and the various programs and libraries that you install. Less than half of what you've allocated currently would be ample.

---

### Post by davidbilla on 2012-09-27
I have partitioned my laptop as follows:

/ - 40 GB (includes /usr)
/opt - 20 GB 
/home - 270 GB (or as big as you can spare)
/data - 280 GB (for storing my work)
swap - 6 GB

---

### Post by mr-woof on 2012-09-27
I would let the installers sort out the partitioning of the hard drive, me personally I would install Windows 7 first, then Debian and then Ubuntu.

---

### Post by oldos2er on 2012-09-27
My root partition is 25GB, and it's never gone over 20GB actually being used.

Linux is perfectly happy on an extended logical partition (including swap), so you really don't need to use so many primaries.

---

### Post by cp2819 on 2012-09-27
ok great

how about 

ubuntu 

30 Go : primary -  /
100 Go : extended -  / home

all other partitions, later ...
all extended.

by the way, can someone explain about primary and extended ?

---

### Post by oldos2er on 2012-09-27
[http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types](http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types)

---

### Post by Bucky Ball on 2012-09-27
> **cp2819 said:**
> win 7 :  
100 Go primary : system
50 Go extended : data win 7

ubuntu :
100 Go primary :  root
40 Go extended : home

debian :
70 Go primary : root
40 Go extended : home

other system linux for testing
50 Go  primary : root
40 Go extended : home

2 Go : swap


any comment, suggestion or advice ?

???

There's no point in having the Linux / partitions that big in any of the Linux installs. I've never used more than 15Gb for / ; 20Gb would be fine, 30Gb overkill, especially considering you have a separate /home.

The other issue is the separate /home partitions. If the Linux installs are Debian based they can use the same /home or other data partition (using symlinks to achieve the latter). You don't need three separate ones. Redundancy. If you use a separate NTFS data partition, you can store personal stuff from Windows on there also meaning there's no point the Win partition being that big (or having a data partition) either. 

After Clonezilla, something like:

Win install = 40Gb (unless it's XP which I also use 15Gb for)
Extended partition:
   / = Ubuntu = 20Gb
   / = Xubuntu 20Gb
   / = Lubuntu
   /home (formatted EXT4) or /data (formatted NTFS) = large as you like
   /swap = 2Gb

With extended partition, you make it on whatever free space you have, that is considered one partition, but you can put logical drives inside it. Ubuntu can happily go in there.

PS: If you boot into Win there should be some manufacturer app that lets you burn recovery disks. Burn two copies then wipe the drive and away you go.

---

### Post by cp2819 on 2012-09-27
thanks for the info

okay, I will keep 30Go for / = ubuntu

@ Bucky Ball : on my new laptop , I don't have win installed because the laptop is sold with only ubuntu factory installed.

I am keeping the weapons ready : clonezilla is downloaded, I will put it on a usb key bootable
and start to make image of my hdd 
Actually I don't have any external hdd to put the image on, I will try to borrow one from my friend and I am ready to go.


Anyone can answer my other question ?
[I]I have another little problem
all the texts in Terminal are not in English
because my native language is not English and my laptop is not configured in English

Is it possible to have those texts in English (to post here ) when my configured langage is not English on my laptop ?[/I]

---

### Post by mips on 2012-09-27
> **cp2819 said:**
> 
okay, I will keep 30Go for / = ubuntu


20GB would be more than enough, I doubt you would ever come close to filling it.

---

### Post by cp2819 on 2012-09-27
> **mips said:**
> 20GB would be more than enough, I doubt you would ever come close to filling it.


even if I plan to test a lot of programs ?
I guess all the installed programs go there ? right ?

---

### Post by cp2819 on 2012-09-27
ok my friends
problem with Clonezilla

I make an image with clonezilla as a test 
and get an error
"this file is not NOt apartclone image
Partclone image fail"

I do it again and again three times, same error
Download again Clonezilla iso
same problem...

Well, I am not at ease ...

---

### Post by Bucky Ball on 2012-09-27
> **cp2819 said:**
> even if I plan to test a lot of programs ?
I guess all the installed programs go there ? right ?

If you have a separate /home or /data partition which you're using as /home then the apps are on / and their configs, settings, personal data is on /home.

---

### Post by shreepads on 2012-09-28
> **cp2819 said:**
> ok my friends
problem with Clonezilla

I make an image with clonezilla as a test 
and get an error
"this file is not NOt apartclone image
Partclone image fail"

I do it again and again three times, same error
Download again Clonezilla iso
same problem...

Well, I am not at ease ...

Did you get the error while trying to create the image or while trying to test  the image you've created?

If you got the error while trying to create the image then my guess is that you are specifying the wrong options in the Clonezilla text menus. Please have a look at the instructions again carefully, it is a little counterintuitive at times..

---

### Post by cp2819 on 2012-09-28
I got the error while Clonezilla verified the image created
I noticed strangely , the image created was smaller than what I think it should be...
I have done all operations on a test computer with IDE HDD and save to an external HDD
I followed some good tutorials on clonezilla , and it was not too difficult to understand...


I guess I will try to make backup images with Acronis
to be sure
and wait for some more sugggestions about the error I got with clonezilla

---

### Post by cp2819 on 2012-09-28
I have made backup of the whole HDD with acronis

now I have another big problem

I deleted all the partitions and made new partitions
Unfortunately there was a hidden partition that was deleted too
When I reboot I try to go to the bios and I discover there is NO option to boot from usb
only boot from the hdd but the HDD is all formated now
Big trouble ....

Any help or suggestions ?

---

### Post by mips on 2012-09-28
Try this,

1. Boot PC and go into BIOS, think it's F2?
2. Go to "Boot" and disable the "Boot Booster".
3. Save settings and exit.
4. At reboot try and select the boot manager and boot from plugged in usb stick.

---

### Post by cp2819 on 2012-09-28
> **mips said:**
> Try this,

1. Boot PC and go into BIOS, think it's F2?
2. Go to "Boot" and disable the "Boot Booster".
3. Save settings and exit.
4. At reboot try and select the boot manager and boot from plugged in usb stick.

I have read this trick.
but unfortunately there is no "boot booster" in the bios of the Asus 1225c
perhaps this is the case with their newest models right now ?
no luck.. and I thik it is a bad thing from Asus
I really can't believe it !
and I didn't noticed there is no option to boot from usb in the bios menu
I guess the usb stuffs are in the hidden partition wiped away by me ...
So I have a hdd with no system on it and a bios which only have the boot option to boot on the hdd

---

### Post by mips on 2012-09-28
> **cp2819 said:**
> I have read this trick.
but unfortunately there is no "boot booster" in the bios of the Asus 1225c
perhaps this is the case with their newest models right now ?
no luck.. and I thik it is a bad thing from Asus
I really can't believe it !
and I didn't noticed there is no option to boot from usb in the bios menu
I guess the usb stuffs are in the hidden partition wiped away by me ...
So I have a hdd with no system on it and a bios which only have the boot option to boot on the hdd

Is there no boot manager selection on bootup? I know on my pc I can select hard drive and then it will list the sub items which includes usb devices.

Did you try a different USB port as I see that netbook also has usb3 ports. You have to use a usb2 port on the right side to boot from.

---

### Post by cp2819 on 2012-09-30
@ mips

Finally I succeded to boot on the right usb port only and had to flash the bios to get the usb selection came up. Thanks for your help.

I finished installing win7, then ubuntu 12.04 and I made grub configuration for a dual boot for now.

I took out the memtest option, and disabled the os-prober 
because I don't want it to autodetect each time
I prefer configuring manually and add what I want to the grub menu

Finally, I change the grub splash screen
and change also the grub font colors

I tested all the menu options
Everything works great

Next step is installing Debian and add it to the menu


[IMG]http://imageshack.us/photo/my-images/685/80136656.jpg/[/IMG]
[IMG]http://imageshack.us/photo/my-images/685/80136656.jpg/[/IMG]

---

### Post by cmcanulty on 2012-09-30
I have tons of apps installed and several desktops ubuntu, Xubuntu, etc and am using less than half of my 20GB / partition

---

### Post by mips on 2012-09-30
> **cp2819 said:**
> @ mips

Finally I succeded to boot on the right usb port only and had to flash the bios to get the usb selection came up. Thanks for your help.

Finally, I change the grub splash screen
and change also the grub font colors


Glad to see you came right ;)

I like the grub splash screen with the old apple logo, got a link for it?

---

### Post by cp2819 on 2012-09-30
> **mips said:**
> 

I like the grub splash screen with the old apple logo, got a link for it?


of course
here you go

[http://imageshack.us/a/img853/1963/cuir640.jpg](http://imageshack.us/a/img853/1963/cuir640.jpg)

enjoy

---

### Post by mips on 2012-09-30
thx!

---

### Post by Bucky Ball on 2012-10-01
@ cp2819: Just for future reference; from the Code of Conduct:
> 
**Images:** Be prudent in your use of images; they may help to  explain something more clearly or indicate a problem you are  experiencing better but you have to remember that not everyone has the  same bandwidth. If an image is the best way of handling the information,  please use thumbnails or keep your image to a small size and less than  100kb.

You can also attach them using the paperclip icon in 'Go Advanced'. ;)

---

### Post by newb85 on 2012-10-01
> **Bucky Ball said:**
> The other issue is the separate /home partitions. If the Linux installs are Debian based they can use the same /home or other data partition (using symlinks to achieve the latter). You don't need three separate ones. 

Ahem, from someone who has tried it, sharing a /home partition across multiple systems can be messy.  There are hidden system configuration files in there that can cause conflicts.  For example, one system will save a default desktop session that doesn't even exist on an another system.  If you choose a stock wallpaper in one system, that wallpaper won't be available in another system, and you'll have a blank desktop.

Instead, I would recommend having a common data partition that you set up with the same basic file structure as your /home directories, and you can symlink to it from your /home directories  .

---

### Post by Bucky Ball on 2012-10-02
> **newb85 said:**
> Ahem, from someone who has tried it, sharing a /home partition across multiple systems can be messy.  

I do it ... with three Ubuntus, but have used others, with no issue. In the /home partition, you get /home/user1, /home/user2, etc. Each user for each new install (and it's hidden directories for system/app stuff) is not lumped inside a single directory inside /home; about the only way things could get mixed up. Each install makes a /home/user* directory and everything for that user's install goes inside that. The system settings (hidden directories with app config data etc) from each install aren't mixed at all in any way. They are in totally different directories (/home/user*) belonging to their own install (but all three /home/user directories are accessible from any install). ;)

> Instead, I would recommend having a common data partition that you set up with the same basic file structure as your /home directories, and you can symlink to it from your /home directories  .So would I. This is (almost) exactly what I did with an old /home/user partition that had all relevant data when I wanted to kill 10.10. I installed 12.04, linked everything to the directories existing in /home/10.10User, then deleted 10.10.

Not exactly what you describe ... but effectively the same. The bonus is, even though the with the old way you can still access all data from any user, you have one directory serving all three installs rather than three. Sweet, easy, elegantly simple and works for me ... ;)

---

### Post by cp2819 on 2012-10-02
> **Bucky Ball said:**
> I do it ... with three Ubuntus, but have used others, with no issue. In the /home partition, you get /home/user1, /home/user2, etc. 


1) in this case, do you have to give different user names ?
user1 for Linux distro 1
user xx for Linus distro 2
or can you use the same user name for all ?


> **Bucky Ball said:**
> So would I. This is (almost) exactly what I did with an old /home/user  partition that had all relevant data when I wanted to kill 10.10. I  installed 12.04, linked everything to the directories existing in  /home/10.10User, then deleted 10.10. 

2) how can you link afterward to existing directories in /home/XXX
for example: if I have installed Linuxxx with everything in just one partition, 
can I modify easily in "deleting" its /home directory and link it to an existing  /home directory common with all other Linux distro present on my system ?



BTW, sorry for image size , I didn't know that , I will follow your advice
I will try to edit my last post and correct this tonight ...
thanks

---

### Post by Bucky Ball on 2012-10-02
If you have Linux installed on one partition (no separate /home) then you do as has been suggested by newb85 and alluded to by myself; create a separate data partition, create directories named the same as the ones in your /home directory in Linux install, delete the directories in the /home of the Linux install and create links to the directories on the /data partition.

The syntax is like this:

```
ln -s 'location to link to' 'name of symlink'
```So, for example:

```
ln -s /media/data/Documents /home/username/Documents
```I don't remember if you need to add 'sudo' to the beginning of the command to do this so if doesn't work try it. The above code presumes your data partition is mounted as /media/data and has a directory in it called 'Documents' so change accordingly to fit your needs. 

This page explains more:

[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

---

### Post by newb85 on 2012-10-02
> **Bucky Ball said:**
> Each user for each new install (and it's hidden directories for system/app stuff) is not lumped inside a single directory inside /home;

Therein lies the difference in our experiences.  I used the same user for all systems.

---

### Post by Bucky Ball on 2012-10-02
> **newb85 said:**
> Therein lies the difference in our experiences.  I used the same user for all systems.

Got ya. I understand that could cause some serious and bewildering issues and conflicts, yes ...  ;)

---

### Post by newb85 on 2012-10-02
If you follow the scheme in #34, you'll have to give the user write permissions for the folders on the data partition.

---

