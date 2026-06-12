---
title: "installing on usb 500gb h/drive"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by broekskw on 2008-11-22
can i install 8.10 on an external 500gb h/drive that is not partitioned;will the install cd let me setup the correct partition and leave some space for my windows backup file??

also if i do not turn on the usb h/drive with 8.10 on it will windows still boot up as normal 

thanks for any replies

---

### Post by chazn85 on 2008-11-22
As long as you can boot to the device and partition it properly (taking care not to overwrite your backup file) you should be fine

---

### Post by broekskw on 2008-11-22
thanks chazn85; so the live cd will take me threw the correct partitioning??

will give it a try:popcorn:

---

### Post by chazn85 on 2008-11-22
you may want to try partitioning it first with the gparted live CD if your not familiar with the partitioning tool.  once booted just type

```
 gparted 
```

this will give you a partitioner.  alternatley you could give us the output of

```
 sudo fdisk -l 
``` 

if you need further help with partitioning them correctly

Thanks

---

### Post by broekskw on 2008-11-22
chazn85 thanks a lot for the info, just downloading the iso file 8.10 and will be making the cd soon, so in live cd ,in terminal comand just type in "gparted" and this will install the program for me to use?

will give the output of this command "sudo fdisk -l"

thanks

---

### Post by chazn85 on 2008-11-22
there are two different live CD&#347; the ubuntu ISO (the OS obviously) and there is also a seperate one for gparted (always handy to have one just in case) but yeah from the live CD (either will do) let us know the ouput of 

```
 sudo fdisk -l 
```

Thanks

---

### Post by broekskw on 2008-11-22
great will do. I think i have a gparted cd already made up from my other computer down stairs, I think this did need to be put in my cd drive and then reboot?? correct

if so whator how do i partition my 500gb h/drive ??
i need 2 partitions for 8.10 to run??

thanks

---

### Post by louieb on 2008-11-22
>  if i do not turn on the usb h/drive with 8.10 on it will windows still boot up as normal

The default install will put the GRUB stage2 program on the external hard drive and modify the MBR of the internal drive to load GRUB on the external drive. What that means is the computer will not boot unless the the external drive is plugged in and power on. 

There are ways around this. This does require some knowledge of GRUB and partitioning.   The easier way is to let  Ubuntu share the internal drive with windows. The installer does  this well and without you knowing much about partitions and GRUB.

---

### Post by broekskw on 2008-11-22
thanks louieb; the reason i want it on my usb external drive is because i only have about 10gb of space left on my internal drive the one with windows xp on, so if i just let 8.10 install on my internal drive and then let my 500gb external drive work as the swap drive??
still need to partion this external drive?? correct

thanks

---

### Post by broekskw on 2008-11-22
ok have a gparted disc, so rebooted with disc in cd drive and it loaded all the way up to the :force video; my dell dimension 2400 has on board video "i810" chip set so typed in i810 enter then 1024x768 and enter next thing my monitor shut down and could not get back, tower light was green so tower was still on but monitor was off, had to restart system;

is there special instructions for dell and on board video chip sets??

thanks

---

### Post by louieb on 2008-11-22
How big is the internal drive?  10GB is not a lot of free space.  Windows needs some free space in its partition  to keep its files from getting fragmented.     

One of the ways to do what you want is to create a small 5 MB partition on the hard drive and and put GRUB in it.  [IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")  

or you can change the windows boot loader to choose between windows and Ubuntu. If your running Vista look at program called [EasyBCD]("http://neosmart.net/dl.php?id=1")

In either case,  when you install Ubuntu on the external  you will tell it not to use the default GRUB location. You will tell it to put GRUB in the boot sector of install partition.

Do you have the Ubuntu desktop CD?  You can boot it and run it without changing anything on your computer. One of the commands I'd like to see  will list your partition table. to run it open applications>accessories>terminal   and type
```
 sudo fdisk -l 
```(lowercase L)

---

### Post by broekskw on 2008-11-22
louieb just burning the 8.10 cd as we speak,will run the cd and type in the command and post results

thanks
ps the internal h/drive is 40gb 10gb free

---

### Post by louieb on 2008-11-22
> **broekskw said:**
> ok have a gparted disc... is there special instructions for dell and on board video chip sets??

I've had trouble in the past with the Gparted live CD. So now when I want to run Gparted I use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  NIce CD to have around Gparted is just one of the many tools on the CD.

---

### Post by broekskw on 2008-11-22
great i think that i have that also, but not sure;ok loaded the cd (8.10) but would not get past the selection screen erro box came up something about reading disc, so cleaned disc and went into setup and increased video to 8mb,then disc ran for the first time past the selection screen, after about 5min on the ubuntu screen the next screen was all black with endless error messages
"squashfs error :unable to read fragment cache block"
"buffer i/o error on device sro lucical block "

and many more error just kept repeating over and over
had to reboot;'

going to try this cd on my other computer

---

### Post by broekskw on 2008-11-22
ok tried it on my other computer with the same error screen, just keep scrolling error codes page after page;

will try to download iso image from diff site and try new burn new cd

---

### Post by broekskw on 2008-11-23
ok both computer will not work with 8.10 so i am on a 7.10 ubuntu live cd running ok
here is what i get when i open a terminal and type in "sudo fdisk -1

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc84f5ab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by broekskw on 2008-11-23
so from a terminal started gparted, and its running but has yet to detect my h/drives

is this normal to take this long

---

### Post by broekskw on 2008-11-23
so here is the error code i get in a terminal for gparted

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

what dose all this mean:confused:

---

### Post by broekskw on 2008-11-23
here is a screen shot of my desktop showing my usb h/drive; so how com gparted could not see it:confused:

---

### Post by louieb on 2008-11-23
[ATTACH]93824[/ATTACH]/dev/fd0 is you floppy drive. I'd just ignore it.

fdisk does see you external drive thats a good thing. Linux calls it /dev/sdb and fdisk shows it to have 1 500 GB fat32 partition. 

You'll find the partition editor under system>adminstration>partition editor.

Sometimes it takes Gparted a while to detect all you drives. 
Look in the upper right hand corner there is a drop down box open it and select /dev/sdb. 

Lots of ways to use 500GB I'd probably make it look something like this.

---

### Post by broekskw on 2008-11-23
louieb thanks for all your replies;so made a 8.04 live cd and am running from this cd; started gparted and it show both my internal and ext h/drives, so can i in gparted make up the partitions to install ubuntuin;
1st partition will be on my internal drive (5gb)
#2 will be on my ext h/drive what size?? 
#3 also on ext h/drive
#4 will be left over for my windows backup and others

what and how to i partition and also labal them correctly

thanks

---

### Post by louieb on 2008-11-23
1st thing i noticed was the lock on sdb1. right click on that partition and choose the unmount option. that will remove the lock.

All you need on the internal drive is a small partition.  5-10MB or so at the end of the drive.. No need to make it any bigger. Want to  let windows have all the space  you can give it.   

Then partition the external  drive.

If your not sure how to use Gparted heres a couple of pretty good how to.
[Linux.com :: Using Gparted (Linux.com videos)]("http://www.linux.com/feature/114157") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by broekskw on 2008-11-23
in gparted it will not let me resize my ext h/drive, can select it but that all.

any idea how to select it to resize??

---

### Post by broekskw on 2008-11-23
sorry  louieb just got home and did not read your last post before posting about lock h/drive

 again thanks for your help:lolflag:

---

### Post by broekskw on 2008-11-23
hay louieb almost ready to install 8.04;one question in gparted;i have 3 partitions
1= 10 gb  ext3
2 = 1gb linux-swap
3 = 96gb ext3 on my usb h/drive

do or when i install 8.04 will it let me select the 1st ext3 as the boot??

thanks

---

### Post by louieb on 2008-11-23
Ok when you get to the  partition part of the install choose the manual option. click on the  10GB partition and choose the mount point of / (root). 
/ (root) is where Ubuntu will gets installed.  After that click next. 


Did you put the 10GB partition on the internal or external drive? 
Did you make a small 5-10MB partition on the internal drive? 


Would like you post some Gparted screen shots of the internal and external drive.  Have to deal with GRUB and its install.    

On the screen just before the install actually begins you see an advanced button.  Click it and you can change the default Grub install. You will want to use that and tell it to install Grub on** /dev/sdb **also could be written[B] (hd1).   This will put the GRUB stage1 code in the MBR of the external drive. 

[/B]If you do that then the internal drive remains untouched.  

Hopefully your computer lets you choose to boot off a USB device. If it does the you can use it to choose between Ubuntu and windows. If not then we can deal with that later.

---

### Post by broekskw on 2008-11-23
so finished installing ubuntu 8.04 on to my win xp computer, every thing looks good but one small thing NO INTERNET, the system said that i am using a restricted driver "atheros 802.11 wireless lan card" but my card is "d-link wda-1320 wireless,

so now how do i get the correct file or driver to install on my computer that has no internet??
funny thing in live cd every thing worked great had internet:confused::confused:

any help  thanks

---

### Post by louieb on 2008-11-23
Cool for getting it installed. 

I'm pretty clueless when it comes to wireless trouble shooting.  It would probably be best to start a new thread in the networking section of the forum.

---

### Post by broekskw on 2008-11-23
great and thanks for all your help
just an update, loaded live cd and internet works ok and also on my router home page it shows up as ubuntu "active" not like the full install showing ubuntu "inactive"

this nust be my problem:confused: have to try to get it active in my 2700hg-e router

will try some more and if not post a new thread in the network forum

again thanks for all your help:lolflag:

---

### Post by broekskw on 2008-11-23
well did a reboot again and every thing is working now:popcorn:
now for all the updates

:lolflag:

---

