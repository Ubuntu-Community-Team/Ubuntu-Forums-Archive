---
title: "How to dual boot Ubuntu and Windows XP without changing the Windows MBR"
date: 2005-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by celticmonkey on 2005-08-13
How to dual boot Windows and linux without changing the Windows Master Boot Record:

(I'm assuming you've read other FAQs on how to install linux to your partition of choice. I recommend creating a partition on a second hard drive. That's the risk free option if you don't want to destoy Windows on your primary partition. But you should be able to create a partition on your primary hard drive by using software that can non-detructively resize your Windows partition. QTParted is a good program which can be downloaded if you're running the ubunut live CD. Back up though. It doesn't always work. I don't think the partition resizer in the ubuntu installer can do non-destructive.)

When installing ubuntu, install the boot loader (GRUB) to a floppy disk instead of the MBR. ie. when prompted for grub location enter: /dev/fd0

Boot into ubuntu with the floppy.

Open a terminal window.

Copy your bootloader from the floppy to a file called bootsect.lnx with this command:
dd if=/dev/fd0 of=bootsect.lnx bs=512 count=1

Save that file somewhere that you can access from within Windows. ie a FAT partition, a USB drive, a floppy (but not your boot floppy!) Don't try saving it to an NTFS Windows XP partition from within linux. (Bad!)

Reboot into Windows. (hint: take the floppy out of the drive. Keep it somewhere as a rescue boot floppy.)

Copy bootsect.lnx from wherever you had stored it to c:\bootsect.lnx

Open a file called c:\boot.ini
(It's normally a hidden read-only file, so you may have to change the folder and file options.)

After opening boot.ini add the following line to the end of it and save it:
c:\bootsect.lnx=”Linux”

Reboot your system.

You will be prompted to boot either Windows or Linux and your MBR hasn't been changed at all!

It's magic!
I use this setup to boot ubuntu from the third partition of my second hard drive. As ubuntu is on a second drive I haven't made any changes to my Windows partition at all! Risk free.

(If you do screw up your MBR and can't get into Windows try booting your Windows rescue CD and then type 'fdisk /mbr' to restore it. If you already have ubuntu installed I think you can make a boot floppy this way, but I"m not 100% certain: In a console, type grub-intall /dev/fd0.)

I apologize if to anyone who's already read this in the installation forum but someone suggested it would be more useful to post this here.

James.

---

### Post by varunus on 2005-08-13
Good guide; is there any way to do this without a boot floppy?  Ubuntu installs GRUB onto its own partition if you don't use the MBR, right?  Can you somehow get the first section of the drive you install Ubuntu onto?

Contrary to popular belief, the Ubuntu installer can resize NTFS and FAT32.  Here's a guide on how to do this, with pictures:
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

### Post by celticmonkey on 2005-08-13
I thought that would work to. That was what I tried first. I tried writing GRUB to the boot sector of my root linux partition and then grabbing the data from there, but I couln't get it to work. I also tried writing it to the boot sector of the first partition of the second drive. Coping the data from there didn't work either. But I coudn't boot from directly from there either by changing my BIOS settings. It has something to do with chain loaders and BIOS drive mapping that I don't really undertand. But I was able to get my system going from a floppy and I was able to extract what I needed from there.

---

### Post by Slicedbread on 2005-08-13
Is there a way to to repair the MBR and do this after you have installed linux?

---

### Post by psterrett on 2005-08-14
[QUOTE=celticmonkey]I tried writing GRUB to the boot sector of my root linux partition and then grabbing the data from there, but I couln't get it to work. [/QUOTE]

So, 

```
dd if=/dev/hda6 bs=512 count=1 of=/linux.bin
``` 

doesn't work with Ubuntu? This is the method I used to set up dual booting on my laptop--which doesn't have a floppy disc--under Kanotix/Knoppix et. al. I copied the linux.bin file to my c:\ directory and then appended an entry for Linux to c:\boot.ini.

I'm glad I stumbled into this forum before trying to install Ubuntu. I would have been livid!

---

### Post by Slicedbread on 2005-08-14
Do you think it would be possible to install grub to another created partition then boot from the live cd and copy the config from there? THen boot to windows and do the rest?

I tried to do a new installation and install grub to floppy (/dev/fd0 like you said) and got a fatal erorr. Floppy and floppy drive function normally in windows.

---

### Post by celticmonkey on 2005-08-16
I hope I haven't misinformed anybody with my FAQ. I absolutely know that you should be able to write the grub to a hard disk and copy the info from there. Other people have done it. It just didn't work with my computer.

On my work computer I have two harddrives. I installed linux to the second along with the boot loader. Then I changed the BIOS to boot from the second and then from the boot menu could pick either linux or windows. 

When I tried that at home it wouldn't work. I've got some wierd BIOS issues I think. Something to do with drive mappings being switched? I don't know exactly. I also ran into trouble installing the boot loader to the MBR. Windows wouldnt' boot then. (If you ever screw up your MBR, user the windows rescue CD and "fdisk /mbr". Or get a hold of the "The Ultimate Boot CD". It has tools for restored a MBR as well as some other cool stuff. [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)) Anyway, then I moved on to the above method. I didn't have any luck copying from my hard drive partition, but I think that relates in some way that I don't understand to my wierd BIOS issues. The boot loader gets confused about what drive it is booting because BIOS has switched the drive mapping maybe? I don't know. There's a lot I don't undertand about booting. But it did boot off the floppy. So that's what I did and that's where I copied the loader from. I foolishly assumed that everyone still has a floppy these days, which of course they don't. Mabye that solution won't work for everyone.

---

### Post by BiggoCharley on 2005-08-18
[QUOTE=celticmonkey]How to dual boot Windows and linux without changing the Windows Master Boot Record:


When installing ubuntu, install the boot loader (GRUB) to a floppy disk instead of the MBR. ie. when prompted for grub location enter: /dev/fd0

Boot into ubuntu with the floppy.


James.[/QUOTE]

I've installed Ubuntu 5.04 a couple of times now and I have never been prompetd for a location to install grub --what am I missing?
Charley

---

### Post by GreyFox503 on 2005-08-18
[QUOTE=BiggoCharley]I've installed Ubuntu 5.04 a couple of times now and I have never been prompetd for a location to install grub --what am I missing?
Charley[/QUOTE]

I wondered about this too, but I think it depends on whether GRUB is already installed on the MBR.

When I installed Ubuntu for the first time, it prompted me for where to install GRUB.  However, the second time (I experimented a little too much) it didn't ask me.

---

### Post by celticmonkey on 2005-08-23
I tried this again on another machine and was prompted for a location to install grub. The installer autodetected another OS and asked where I wanted grub. It may be, however, that if grub is already on the MBR you need to do something else.

I should have said that none of this works for Windows 95 and 98. You need 2000, NT or XP.

---

### Post by arnoct on 2005-08-24
Also, if your BIOS supports it (most should,) if you have two drives and Linux is on the secondary drive (like I have,) you can install GRUB on the secondary drive and then simply set your BIOS to boot from the second drive whenever you want to run Linux. it's what I do currently.

---

### Post by tritch on 2005-09-02
First off I want to thank all of you for posting to this forum.  It helped me tremendously with loading Ubuntu, which I just discovered yesterday =).  I was using RH, but this blows it outta the water!

After some trouble, I was able to configure the dual boot on my dell inspiron 6000 -- which doesn't have a floppy drive.  To hopefully save some potential installers of the trouble I faced, I'm posting my solution here.

Things needed:   Ubuntu Installer CD, Ubuntu Live CD, and 2 usb drives or 2 sd cards with two readers, etc. (I used my creative c100 mp3 player and it's expandable sd memory card).

During the installation's partitioning have the two usb drives
formatted as follows:

dev name:               /dev/sdb1      /dev/sdc1
use as:                       fat32             ext3
mount point:               none            none
mount option:            default         default
Bootable:                     off                 on   <-- not sure if it needs to be on, but it worked for me.

Please note that your dev names could be different from mine.

When selecting where in install GRUB, enter the dev name that corresponds to the ext3 file system.  If you choose the fat32 usb drive, this procedure will not work. In my case I entered: /dev/sdc1

When the installation completes install the Ubuntu Live CD and reboot.  When the Ubuntu Live CD finishes booting your USB drives should be recognized... at least mine were.  From here open a terminal window.

Now enter:  dd if=/dev/sdc1 of=/media/usbdrive/bootsect.lnx bs=512 count=1 
Where /media/usbdrive is the location of your fat32 formatted usb drive and /dev/sdc1 is your ext3 formatted usb drive.

Now you can follow the remainder of celticmonkey's instructions in order to place the bootsect.lnx file on windows.

This is definitely a sticky work around, but it beat buying a floppy drive. Hope this helps and happy hackin!

P.S.  I couldn't use my hard drive to save GRUB because when using the Live CD to run dd the hard drive is in accessable.

---

### Post by Irony on 2005-09-02
Could this bootsect.lnx file be posted somewhere - what I mean is, is it a relatively simple file that can be configured manually?

---

### Post by Heliode on 2005-09-03
> I don't think the partition resizer in the ubuntu installer can do non-destructive.

It is a little known fact that you, indeed, **can** non-destructively resize ntfs with the Ubuntu installer. I have tested it in VMWare, and afterwards both the Windows and the Ubuntu installation were bootable, so I would say it works just fine
( [https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning) )

---

### Post by FeTT on 2005-09-19
I just tried this but i already had grub installed so I installed it from a terminal to a floppy, created the bootsect.lnx in my home directory and switched that over to another floppy. Booted to Windows and copied the bootsect.lnx as per instructions and added the c:\bootsect.lnx=”Linux” to my boot.ini but when i choose Linux from the boot menu all i get is GRUB GRUB and a blinking _ and it goes no further. Id love to get this working as its a pain having to go into the bios and switch boot drives everytime i want to switch OS. Any body have any ideas.

Thanks

FeTT

---

### Post by oblib on 2005-10-01
Here is a way to get it working with an already installed Ubuntu and no floppy.

I have two drives that I am working with (hda and hdb). When I installed Ubuntu, I unplugged hda because I did not want it to mess with Windows or the MBR on that drive. So it installed grub to hdb. Anyway, when I wanted to use NTLDR to boot to linux, I could not figure out how to get a good floppy to read the boot record from, so I ended up using the advice on [http://jaeger.morpheus.net/linux/ntldr.php]("http://jaeger.morpheus.net/linux/ntldr.php").

For Ubuntu what I did was install lilo from Synaptic, and then I ran liloconfig. I told it to install to hdb1, which is my *root* location. You can find your root by looking at /etc/fstab. (It's the entry with \ as the location :) ). I did not let it do anything to the MBR of that drive. After installation was complete, I modified /etc/lilo.conf as recommended on the linked page, then ran lilo. It updated the boot record to reflect my changes. From there, I was able to use 'dd' and all the rest as described by the first post here.

Now I can either instruct my BIOS to boot hdb directly, in which case GRUB boots Ubuntu, or wait until NTLDR asks which Windows or Linux I want to boot too, in which case LILO boots Ubuntu.

My lilo.conf is below:
```
# Generated by liloconfig
# This allows booting from any partition on disks with more than 1024
# cylinders.
lba32
# Specifies the boot device
boot=/dev/hdb1
# Specifies the device that should be mounted as root.
# If the special name CURRENT is used, the root device is set to the
# device on which the root file system is currently mounted. If the root
# has been changed with  -r , the respective device is used. If the
# variable ROOT is omitted, the root device setting contained in the
# kernel image is used. It can be changed with the rdev program.
root=/dev/hdb1
# Bitmap configuration for /boot/debianlilo.bmp
bitmap=/boot/debianlilo.bmp
bmp-colors=1,,0;9,,0
bmp-table=106p,144p,2,9,144p
bmp-timer=514p,144p,6,8,0
# Enables map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the map
# smaller. Using COMPACT is especially recommended when booting from a
# floppy disk.
# compact
# Install the specified file as the new boot sector.
# LILO supports built in boot sectory, you only need
# to specify the type, choose one from 'text', 'menu' or 'bitmap'.
# new: install=bmp      old: install=/boot/boot-bmp.b
# new: install=text     old: install=/boot/boot-text.b
# new: install=menu     old: install=/boot/boot-menu.b or boot.b
# default: 'menu' is default, unless you have a bitmap= line
# Note: install=bmp must be used to see the bitmap menu.
# install=menu
install=bmp
# Specifies the number of _tenths_ of a second LILO should
# wait before booting the first image.  LILO
# doesn't wait if DELAY is omitted or if DELAY is set to zero.
# delay=20
# Prompt to use certaing image. If prompt is specified without timeout,
# boot will not take place unless you hit RETURN
#prompt
#timeout=50
# Specifies the location of the map file. If MAP is
# omitted, a file /boot/map is used.
map=/boot/map
# Specifies the VGA text mode that should be selected when
# booting. The following values are recognized (case is ignored):
#   NORMAL  select normal 80x25 text mode.
#   EXTENDED  select 80x50 text mode. The word EXTENDED can be
#     abbreviated to EXT.
#   ASK  stop and ask for user input (at boot time).
#   <number>  use the corresponding text mode. A list of available modes
#     can be obtained by booting with  vga=ask  and pressing [Enter].
vga=normal
# These images were automagically added. You may need to edit something.
image=/boot/vmlinuz-2.6.10-5-386
label="Linux 2.6.10-0"
initrd=/boot/initrd.img-2.6.10-5-386
read-only
#image=/boot/vmlinuz-2.6.11-1-386
#       label="Linux 2.6.11-1"
#       initrd=/boot/initrd.img-2.6.11-1-386
#       read-only
#image=/boot/vmlinuz-2.6.11-1-686
#       label="Linux 2.6.11-2"
#       initrd=/boot/initrd.img-2.6.11-1-686
#       read-only
#image=/boot/memtest86+.bin
#       label="Memory Test+"
#       read-only
# If you have another OS on this machine (say DOS),
# you can boot if by uncommenting the following lines
# (Of course, change /dev/hda2 to wherever your DOS partition is.)
# other=/dev/hda2
#   label="MS Windows"

```

Also:
[QUOTE=Irony]Could this bootsect.lnx file be posted somewhere - what I mean is, is it a relatively simple file that can be configured manually?[/QUOTE]
No, it is a binary file, not a simple configuration file. If you know the inner workings of the boot loader, maybe you could edit it.

---

### Post by tepaks on 2006-05-23
Hello everyone,

I tryed everithing on this and other forums but without success. Quickly resumed my first installation of ubuntu ended with "GRUB loading, please wait"
 regardles of booting from hdd, floppy or usb stick. The bootloader.lnx method ended with "can't locate hal.dll" ?!? this is MS ins't it? It looks like my PC is not compatible with anythig else than MS which works fine but ...
Is there any other way to load ubuntu than GRUB or LILO? 
n.b. clean install of ubuntu ends with same mesage.

---

### Post by seshomaru samma on 2006-05-25
Hi
I followed the first post and everything seemed fine ,until the part where I had to boot into Ubuntu using the floppy. It appears the floppy had some problem in it and the file didn't actually got written into it or something (now I cannot mount the floppy in both linux and XP). Furthermore ,it appears like something went wrong with XP as well ,which I had to reinstall (fdiskmbr didnt work as well as various other MS tools). What I got now is a new XP which I can boot into and a new Ubuntu which I can't. Is there a way to copy the boot loader file from another Ubuntu machine ? if so how?
thanks

---

### Post by jacoby on 2006-06-27
BRACE YOURSELF- HOLY CRAP ITS LONG!
The gist is at the top and bottom

How to dual boot Windows and linux without changing the Windows Master Boot Record (My Version):

#####################

Pieces taken from [http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")

#########################

Afterthoughts that should have been forethoughts:

###################################
I should have backed up and done it on a fresh install anyways.  
Ever since trying vista, things have been working strangely.
--------------------------------------------------
I should have done more research.
-------------------------------------------------
I should have done it while rested. as it was and is, I've been awake for, well, it's 
11:27pm here, and I have been awake since about 8:am the previous day. 
 I made a lot of blunders that could have been avoided. This guide is slimmed down from my notes.  If you think this is long, you should see my legal pad.
------------------------------------------------------------
This is my first guide type thing on this forum. It might not work for you, but if it doesn't, maybe you can work from it and adapt it to you're needs.  I know it's long and all,  but I feel that the info regarding my mistakes is important as it may prevent someone else from making them.  I'm not a polished writer, I know this is VERY rough and ugly, and prolly confusing, and  I will edit and refine this as i have time to experiment and refine it. Give me a break, I'm tired. Good thing i have virtualpc for that.  If you can clean it up, then please do and post it as a revision in this thread.
-------------------------------------------------------------
I realize now why the flash drive didnt work.  It is a usb-hdd format, not usb-floppy.  Would'nt have mattered, as all of mine are.  I could have used the original guide if I had a usb-floppy emulated flash drive, i think.  just enable the option in the bios, install grub to THAT, and substitute it for fd0 in:

dd if=/dev/fd0 of=bootsect.lnx bs=512 count=
--------------------------------------------------------------------
I could have done without the 3rd install, but I wanted to be REALLY sure of my actions.

To do this if you already have GRUB on your mbr::
*boot to live cd*
*open terminal*

**sudo su**
**grub**

**root (hd0,2)**  @@<--- was my mount point, your's may differ
**setup (hd0,2)**  @@ < --- same as above
**quit**

**dd if=/dev/sda3 of=bootsect.lnx bs=512 count=1**

**CHANGE THE MENU.LST IN "/boot/grub" AS STATED FARTHER DOWN**

copy this file from your home folder to your XP root (c:\) and edit the boot.ini as mentioned.

reboot and insert xp cd

enter rescue mode, select your windows install, enter admin password for that install, and type  at the prompt
**fixboot c:**
**fixmbr** at the prompt

Reboot

This should work, but I havent tested it.)


```
#########

THE MEAT OF IT ALL:

I wanted to dual boot WinXP and Dapper, without going through two boot loaders to get to XP.  Nothing against Ubuntu there, as I use it a lot, but I use XP more, for school and games. So, I wanted to get to XP a bit quicker, and deal with Dapper booting slower.

The instructions in the link above are great, but I had to figure out some other things.  I've been at it for about 20 hours, with 3 hours off for mowing the grass and meals.  I've hosed my system twice, and had to use Knoppix to recover my files. But goddammit I did it.

My problem was I have no floppy drive.  I saw some other people using usb flash drives to install grub to and create bootsect.lnx.  (NOTE -- see afterthoughts / forethoughts above) This did not work for me.  The second time it might have, but I goofed and forgot to edit my menu.lst in /boot/grub.

So then, to the details.

Hardware: P4 3ghz, 1.5GB DDR Dual Channel.  Intel 915GAG Mobo, ATI X1600 Pci-e 512mb, a 200gb sata hdd, and 2 DVD burners, plus misc flash drives and usb hdd's.

I tried the above guide, installed grub to (hd0,0), went into the live cd to make the bootsect.lnx (dd if=/dev/sda of=bootsect.lnx bs=512 count=1  -- Note: sda was my mount point, yours may differ).  Whoopsie!!!!  That Windows Vista Beta2 that I uninstalled from a dual boot warped my mbr!  HOSED!  Time for my trusty KNOPPIX DVD!  (Note: I tried rescue mode from my xp cd to use fixmbr, and also tried fixboot, to no avail)

Effort 2:

Well, I learned something, that this will work better if I pay attention to the changes vista makes to my hdd.  Frsh install of xp on a 135gb ntfs part, a 10gb fat32 os share part, and the rest for a fresh install of dapper.

I installed dapper, and when grub install came around, i installed it to a flash drive (formatted ext3, marked bootable.)  After install, I unmounted and remounted the flash drive, and made a bootsect.lnx with "dd if=/dev/sdb of=bootsect.lnx bs=512 count=1".  I copied it to the fat32 share partition, booted into xp, and put the bootsect.lnx in my c:\ root, and modified boot.ini by adding this at the end:

"c:\bootsect.lnx=&#8221;Ubuntu Linux v6.06 - Dapper Drake&#8221;

################################

Time to reboot!

I reboot and select Dapper from the NT Bootloader, and get "GRUB hard disk error" and a freeze. 

Well, shoot. So close, yet so far.

######################

Random thought, I put the flash drive in and rebooted again.  Now come error 17. Well, that's easy, right?  The menu.lst file is pointing in the wrong direction.
(Note- once I got it working I thought that the usb key would be a cool security thing, but a hassle)

So, I go to a live cd, system/administration/disks and look at my mount points, and translated them to GRUB lingo ;-)

########################
mnt     fs                              GRUBby
------------------------------------------------------
sda1 - ntfs                             (hd0,0)
sda2 - fat32                (hd0,1)
sda3 - ext3                (hd0,2)  I stopped here.
sda4 - extended
sda5 - linux swap inside the extended
###########################

and my flash drive

sdb  -ext3                (hd1,0)

##########################
handy information, eh?  To the menu.lst!

Note : irrelevant portions of the file have been excluded.
       changer have a ***@@@*** and a space at the beginning of the line., and marked notes and changes with ***@@@[message]@@@***

############menu.lst#######################

*** (Note - this is not neccessary, but a personalization)***
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
* @@@ *timeout        30 ***@@@<-change@@@***

(Note - this is not neccessary, but a personalization)
# Pretty colours
* @@@* color cyan/blue white/blue ***@@@<-change  uncommented@@@***

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

[I]
** @@@IMPORTANT SECTION@@@**[/I]

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
*** @@@*** # kopt=root=/dev/sda3 ***@@@<-change@@@*** ro  

** @@@VERY IMPORTANT@@@**

## default grub root device
## e.g. groot=(hd0,0)
@*@@* # groot=(hd0,2)  ***@@@<-change  ***

*** (@@@Note - this is not neccessary, but a personalization)@@@***
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
*** @@@***#  howmany=3  ***@@@<-change*** 

## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-23-386
*** @@@*** root    (hd0,2)***@@@<-change@@@***
*** @@@*** kernel    /boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash **@*@@<-change@@@***
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
@@@ root    (hd0,2)***@@@<-change@@@***
@@@ kernel    /boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ***@@<-change@@@*** ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
*** @@@*** root        (hd0,2) ***@@@<-change@@@***
kernel        /boot/memtest86+.bin 
boot

*** @@@The following is just the end of the file to help show structure@@@***

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

** ###############end menu.lst#########**

REBOOT!  SELECT DAPPER!  HOLY COW IT BOOTS (only with usb flash drive plugged in, otherwise i get GRUB hard disc error, cool for security maybe, but undesired)

###########################

Well golly this has gone on long enough.

The good part:

I didnt' reinstall all of my stuff into my xp or dapper installs.  they were just fresh vanilla installs.

Now to put it all together into a working solution!!! YAY! FINALLY!!!

##############################
```
FRESH INSTALL

Install xp yet again (fresh install for you, as you dont need to do any of the above)
- leave some free space for 'nix partitions.

install dapper from live cd as normal. (same goes as above)

WHEN YOU GET TO THE GRUB INSTALL --- 

I installed to /dev/sda3 (remember that I use sda2 as a fat32 file transfer between the os's.

Finish the install, and stay in the live cd environment. DONT REBOOT!

Go to the system menu / administration  /  disks manager

I selected the first hard disk, sda, and went to the partitions tab.

partition sda3 wasn't mounted so i had to do it.

click [change] next to "access path".

I selected "Filesystem" in the left pane, and created a folder called "temp" in the right pane.
select the "temp" folder and click the [open] button on the bottom.

now click {enable}

The partition is now mounted.  Open a terminal

sudo su  @@<--- so you dont have to use sudo alot

now enter:

dd if=/dev/sda3 of=bootsect.lnx bs=512 count=1

the bootsect.lnx file should be created and be in your home folder.  copy it to a fat or fat32 usb drive or a fat32 sharing partition, so you can use it in windows.


edit you're menu.lst in /temp/boot/grub:

type:

cd /temp/boot/grub
pico menu.lst
@@Edit this file so as to suit your needs and mountpoints as I have done above.@@

reboot.

since grub isn't on the mbr, you should go right into xp.

copy the bootsect.lnx file to "c:\" as stated above.

edit your boot.ini file in "c:\" as stated above.

reboot again, and select Dapper.

It worked for me!

---

### Post by simone.brunozzi on 2006-06-30
Hi there!
I have a problem: I don't find "boot.ini" under my C:\

I am using a Thinkpad T42p, with a strange recovery tool from ibm preinstalled... maybe I don't find boot.ini because of it?

Thanks for any help

Cheers,

[edited] I solved it... the file was very well hidden. Thanks.

---

### Post by temis01 on 2006-09-24
boot.ini is a hidden file of xp

you can write in boot.ini using xp this way

system properties > advanced tab > then startup and recovery at the bottom + click button to modify > here you can decide which default OS to boot first + click button under the 2 combo boxes to modifiy boot.ini

reboot and you have a new choice line to boot ubuntu ...

ur done !

---

### Post by odobenus on 2006-12-02
Hi,
I am trying to install ubuntu 6.10 for dual boot, with no succes.

  I followed the steps suggested by [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)
which are similar to those in this forum at [http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)
My PC has a motherboard with 2 IDE controllers and 4 SATA drive sockets.  The first IDE has one drive with windows XP installed on it.
The second IDE controller has 2 DVD devices
The SATA slots have 2 hard drives, for a total of 3 drives in the PC.  I tried to install Ubuntu on the 3rd drive.
During installation, I chose to manually edit the part table.  
GParted referred to my primary drive as /dev/hda, the first SATA as /dev/sda, and the second SATA as /dev/sdb 
I created partitions on the 3rd drive as follows:
- 24 GB primary part starting at 0, fs type ext3, gparted called this /dev/sdb1
- 5 GB extended part with logical part of type linux-swap (/dev/sdb5)
- 4GB primary part, fs type fat32, called /dev/sdb3
- rest of drive unallocated.

I run into my first problem:
The instructions say that during ubuntu installtion, I will be prompted to specify the location for the GRUB loader.
This did not quite happen, instead the installer displayed a summary page of pre-install configuration settings,
with the ability to change the GRUB location.  I changed this from "hd0" to "hd2,0", but this probably didnt work.
Should I have changed this to "sdb0" or "sd1" or just "hd2" ?

After the ubuntu installation, I rebooted and the system came up in windows XP.
Next I rebooted with the  System Rescue CD ([http://www.sysresccd.org/Main_Page)](http://www.sysresccd.org/Main_Page)), and ran QtParted.
QTparted started up showing a single drive /dev/hda in the left pane. No other drive!
I clicked on the HD icon, a progress bar popped up, froze and QTParted died, the command prompt froze
 (or echoed garbage at other attempts)
I tried to browse the /dev directory for any signs of my sata drive, it showed device files for hda and sda,
but none for sdb or anything that might be a 3rd drive.

I changed the BIOS to boot from the 3rd HD, and rebooted.
The system displayed a list of OSs to boot - about 3 different Linuxes, and Windows XP
None worked Continued.....

---

### Post by odobenus on 2006-12-02
I changed the BIOS to boot from the 3rd HD, and rebooted.  At boot the system displayed a list of OSs to boot - about 3 different Linuxes, and Windows XP.
None worked.
Help!
Sanjeev

---

### Post by zebzeb on 2006-12-18
Congrats on a simple and effective way to dual boot.
Worked for me with Edgy Eft.
I am a complete novice, hadn't touched linux till a few days ago, had not done anything manually with an OS since powermenu and ms-dos 3.x (ah the good old days, looks wistfully into the middle-distance).

For other novices,
terminal seems a little like dos prompt and I found in in applications-accessories (you can just cut and paste stuff in)
Once I created bootsect.lnx I had to find it but it turns out it was automatically put in Places-home folder, handy eh!
I have windows on a FAT32 partition so I could just copy and paste it to the C: drive (it appears as a weird symbol drive -boxes with 1s and 0s- from within ubuntu)

Other things I did,
I was hit with a wave of confidence so I edited boot.ini a bit more, changing the default to linux and reducing the wait time to 5s. The GRUB (I love these new linux acronyms) does then offer me a few boot options including going back to windows which puts me back to the previous screen.

Question,
I installed Windows on a Fat32 partition (a small 7GB one), I think this will give me more options, being able to tinker  with windows files from within Ubuntu, being able to use free space on the windows drive as write-read space for Ubuntu. Am I write or is there a more pressing advantage to NTFS for Windows. I don't want to use windows much now anyway, mostly need it to run the scanner and for guests.

---

### Post by orionMX on 2007-01-05
what is the problem overwriting the MBR.  maybe a ultra nube query, but will that cause unforseen issues?

---

### Post by gozzerd on 2007-01-12
Once you start horsing around with the MBR, you should be prepared to do all of the tasks needed for maintaining it. You should be able to save a copy as a back-up, and then be able to restore it with that copy. If you have windows, you should also be able to use the windows console tools  to restore it to a usable windows only state. If your MBR is messed up, you likely won't be able to easily access anything on the drive. So if something goes wrong installing grub to the MBR, it can be quite a headache. Linux has really wonderful tools for recovering from errors, but its going to take hours and hours and your going to learn an awful lot about computers. 

 The main issue is  with the most common dual-boot scenario, where you already have windows installed, and are installing Ubuntu second, to try it out, and you install grub to the MBR. If you remove Ubuntu without restoring the MBR first, grub will no longer be there to boot windows - your windows partition will no longer be accessible. The MBR contains several critical bits of info, one of which is the sector where the rest of the boot instructions are being stored. If Grub is installed to the MBR, it still gets most of its info from files in /boot/grub. When these are gone, and grub is still the bootloader in the MBR, there are no longer any instructions to boot from, no menu list, nothing. The part on the MBR doesn't even know where windows is. All it knew was where the info it needed in /boot/grub was. 

So leaving windows in first position and its own MBR code intact is a more easily reversible situation, and allows you to horse around with the rest of your partitions to your hearts content without breaking your drive's current bootable state. 

Adding one small binary to your windows root directory, and one line to  boot.ini should be pretty harmless, and easily reversible, even if it doesn't work.

---

### Post by gozzerd on 2007-01-12
Zebzeb - your plan is good. NTFS is a very good file system, but for smaller partitions on single user machines, FAT32 is good enough, and sometimes even outperforms it for speed. FAT32 gets bogged down when the number of files gets very high and the size of the partition is large. I think the speed break-even point is about 8 gigs. Being able to write to your windows partition in a dual-boot machine is definitely the better way to go, imo.

---

### Post by haganerei on 2007-02-01
Success story with one flash drive.

I wanted to set up MythTV in Ubuntu on a second hard disk in my HTPC currently running MCE 2005. It was important to be able to work on the MythTV install at my own newbie pace while the girlfriend wasn't watching TV ;).

1) Connected a 512MB USB 2.0 flash drive
2) Booted with an Ubuntu (6.10, desktop, i386) install CD
3) Formatted the USB drive with ext3 and set the boot flag with GParted during install (It's worth noting that I tried this process without setting the boot flag and it didn't succeed)
4) Created a small (2GB) FAT32 partition (hdb1) at the beginning of the second drive
5) Specified the partitions for swap (hdb2), system (hdb3) and storage (hdb4)
6) Specified the flash drive formatted with ext3 as the GRUB install source (/dev/sda1)
7) Completed install, but stayed in the LiveCD environment
8) Mounted the flash drive (mkdir /media/usbdrive & mount /dev/sda1 /media/usbdrive) and the FAT32 partition (mkdir /media/osshare & mount /dev/hdb1 /media/osshare) from a terminal
9) Copied the GRUB partition to the FAT32 partition (dd if=/dev/sda1 of=/media/osshare/bootsect.lnx bs=512 count=1)
10) Booted into MCE
11) Copied bootsect.lnx from the FAT32 partition on the second disk to C:\
12) Added a line to boot.ini "C:\bootsect.lnx="Ubuntu MythTV" and lowered the wait time from 30 seconds to 3 seconds

Worked like a champ. Thanks for all the info especially celticmonkey and tritch.

Now the girlfriend can enjoy the system I know how to run while I work on the one I don't know how to run yet at my leisure.

---

### Post by kissaten on 2007-03-10
I've been trying to accomplish this all night without success.  After directing GRUB to install on a EXT3 formatted flash drive, GRUB looks like it writes something to the drive.  However, when I perform the "dd if= of=" command, the resulting bootsect.lnx file is 0 bytes.    When I view the flash drive in a file manager, all I see is a Lost & Found folder.  What am I doing wrong?

I do not want to use GRUB because I use Norton GoBack on my WindowsXP partition  and it will not work with another boot loader present.  I want to dual boot from laptop so I can learn more about Linux.  I currently have Xubuntu installed on a portable USB hard drive, but found that I didn't use it much because I'm too lazy to hook it up to my laptop.

---

### Post by jrcanedo on 2007-03-11
**Hello everyone.**

These are the steps that I've done to my computer by dual booting with Windows XP and Ubuntu 6.10.
[LIST=1]
[*]Make sure that you set the BIOS of your motherboard to boot first at CD-ROM or DVD ROM Drive.
[*]Partitioned the hard drive into at least equal size, say: 120GB Sata divided in to 60GB for Windows XP and 60GB for Ubuntu 6.10.
[*]To partition the hardisk..just use the fdisk of Windows XP and format the drive C: and create a logical partition called drive D:
[*]In drive C:....choose the NTFS file system instead of FAT32 for better stability of the Windows XP.
[*]Don't format the Drive D: because during the installation of Ubuntu 6.10, the drive D: will be erased and formated into linux filesystem, like: Ext3 or equivalent.
[*]Install first the MS Windows XP in drive C: and required drivers for video, sound, lan, etc....But it is possible not to install all drivers first for Windows XP settings so that when something wrong happens during the installation...your time spend for Windows XP Installation will not be wasted.
[*]Once your done with Windows XP installation, then install the Ubuntu 6.10 at drive D:.....in this situation, you are going to erase the windows logical partition then install Ubuntu 6.10 in non-wizard way.
[*]See to it that you set for /boot, /home, /  ---as root and /swap partitions....make sure that the size of the /swap partition is twice the size of your RAM, i.e. if 512MB for Physical Memory...then the /swap partition must be 1024MB or 1GB.
[*]Then follow the procedures or instructions based on the Ubuntu 6.10
[*]Sad to say, in this case the GRUB will be installed in the active partition or MBR of windows for loading either Windows XP and Ubuntu 6.10. By default, Ubuntu 6.10 is the first level of selection then follow the Windows XP...however you can edit it if you want Windows XP to be  at first level of selection in the OS menu.
[*]Once the installation was done perfectly....try to reboot the computer and observe the activity of Linux Boot loader and you will notice that Windows OS is at the lower level of menu selection.
[*]Make sure that you set the BIOS again of your motherboard to boot from hard drive.
[/LIST]
**Have fun with the installations of two OSes......However, not all details of installation were  discuss here...because of limited internet access....anyway, the core of the installations of both OSes were discussed here.**
**Rule of Thumb:**
***More practice makes perfect.... ***
Thanks.

**Below are my computer set-up:**
[LIST]
[*]OS: Windows XP and Ubuntu 6.10
[*]Processor: AMD Athlon 64 X2 Dual Core 5200+ (2.6 Ghz) Socket AM2 
[*]Motherboard:  Redfox GEForce 6100 AM2,Audio,Video,LAN Socket AM2 
[*]Video Card: Builit-in GeForce 
[*]Hardisk: 120GB SATA Seagate
[*]Memory: 1GB DDR2 PC-667 Dual Channel Kingston
[*]Optical CD Drive : Asus DVD Writer Double Layer 
[*]Monitor: 19 inches ACER LCD Widescreen
[/LIST]

---

### Post by kissaten on 2007-03-14
I finally got Xubuntu installed on my laptop in a dual boot environment early Saturday evening, the culmination of a 16 to 17 hour ordeal.  Here's how I did it.

First, I partitioned my hard drive using GParted from my copy of System Rescue CD ([www.sysresccd.org)](www.sysresccd.org)).  I set the root partition (/) with boot on.

I rebooted my computer using the Xubuntu alternate install CD (allows you to choose where to install GRUB) and installed Xubuntu, choosing to manually setup the partitions I created with GParted.  I chose the Xubunt root directory (/) when asked where I wanted to install GRUB.  When the computer rebooted, I was presented with the GRUB menu asking whether to start Xubuntu or Windows XP.  I selected Xubuntu and once Xubuntu was loaded, I opened a terminal window and issued the following command:

sudo dd if=/dev/sda4 of=/media/usbdisk/xubuntu.bin bs=512 count=1

Before you issue the aforementioned command, mount a FAT32 formatted thumb drive.  SDA4 is the partition of my Xubunt root directory.  Your root directory may have a different designation.  Note, when I tried using the "of=/dev/..." version of the dd command, I always received an error stating no such directory existed.

I then rebooted using my System Rescue CD ([www.sysresccd.org](www.sysresccd.org)) so that I could change the default boot designator from SDA4 (Xubuntu root) to SDA1 (Windows XP partition).

I rebooted my computer and Windows XP loaded.  I copied the xubuntu.bin file from my thumb drive to the root of my C: drive (c:\xubuntu.bin).  I edited boot.ini and added the following line to the very bottom of the file:

c:\xubuntu.bin="Xubuntu Linux"

I saved the changes, rebooted, and now I have a menu asking me whether to boot Windows XP or Xubuntu Linux.  Linux, Windows XP, and Norton GoBack are coexisting nicely.

---

### Post by kissaten on 2007-03-17
My apologies to all.  In my last post, I stated that Windows XP, Linux, and Norton GoBack were coexisting, but that was incorrect.  They coexisted because I had not re-enabled Norton GoBack after installing Xubuntu.  After re-enabling Norton GoBack, I can no longer boot into Xubuntu.  Norton GoBack will not work in a Windows-Linux dual-boot environment even when GRUB is not copied to the MBR.  Oh well, back to using my portable USB hard drive unless I can find a workaround which I doubt exists.

---

### Post by dcstar on 2007-03-19
Everyone should note that only the first 446 bytes of the MBR holds the bootloader code and only these should be backup up/restored.

Doing a full 512 byte sector could well muck up your partition data.

If you have a working Ubuntu system (with Grub), then you can save the MBR that uses Grub with the following command:
```
sudo dd if=/dev/**hda** bs=446 count=1 of=backup-mbr
```

The "**hda**" must be replaced by the boot drive identifier for your particular system!

After a Windows install, boot up off a Ubuntu Live CD, mount the drive where you have saved the backup-mbr file and then do the following in a terminal:

```
sudo dd if=backup-mbr bs=446 count=1 of= /dev/**hda**
```

You will still have to manually add the Windows system to the Grub menu.lst file, but at least your Ubuntu system should boot up as before.

---

### Post by pxwpxw on 2007-03-19
> **dcstar said:**
> 

If you have a working Ubuntu system (with Grub), then you can save the MBR that uses Grub with the following command:


Also worth noting that the same procedure can be used to save a copy 
of the Windows master boot sector in linux before it gets overwritten by grub.
In fact I recall the earlier lilo boot loader used to do this by default, and save it in /boot.

---

### Post by cho on 2007-04-10
Hi, I didn't want to bump a topic up but at the same time I didn't want to make a new one. I've been searching for a while about dual booting XP and Edgy, and I'm somewhat confused.

In my PC I have 2 drives, lets say A and B. Is it possible to install Windows on A, and Edgy on B, and just change the boot priority in bios when I start up? 

Many thanks.

---

### Post by pxwpxw on 2007-04-11
**cho**

> 
In my PC I have 2 drives, lets say A and B. Is it possible to install Windows on A, and Edgy on B, and just change the boot priority in bios when I start up?



Possible but very inconvenient and liable to create problems.

---

### Post by matilda2006 on 2007-06-07
> **psterrett said:**
> So, 

```
dd if=/dev/hda6 bs=512 count=1 of=/linux.bin
``` 

doesn't work with Ubuntu? This is the method I used to set up dual booting on my laptop--which doesn't have a floppy disc--under Kanotix/Knoppix et. al. I copied the linux.bin file to my c:\ directory and then appended an entry for Linux to c:\boot.ini.

I'm glad I stumbled into this forum before trying to install Ubuntu. I would have been livid!
__________________________________________________________________________________

You have not mentioned the entry which you made for Linux to c:\boot.ini and the full path of linux.bin in C:\ drive. Actually, I have a similar situation. I have two haddisk - in primary XP is loaded and in the secondary I have a blank partition (FAT32). Now I want to install Ubuntu in that partition without disturbing the MBR for XP. I want a boot choice as it happens in Win 98 and XP dual boot. I think I have explained my problem clear. If you can help me, it will be great.

---

### Post by breakerr on 2007-08-22
> **arnoct said:**
> Also, if your BIOS supports it (most should,) if you have two drives and Linux is on the secondary drive (like I have,) you can install GRUB on the secondary drive and then simply set your BIOS to boot from the second drive whenever you want to run Linux. it's what I do currently.

Hello guys..Im new to this but I wanna know if UBUNTU will help me to keep away from windows ...so please help me out on this.....

I find that this option ( the option quoted ) is the one that fits better for me since I want to install UBUNTU in a separate hard disk from my  *WinXp Pro Service Pack2* but how do I know without doing it first or without doing the quoted process first ?? I mean..I have a [PT8 Neo-V]("http://www.msimiami.com/spanish/products/detail_spec/PT8-NeoV_spa.htm") that shows me in the BIOS my two hard disk as 

* PRIMARY IDE MASTER ST*****810A  set to AUTO  -  this is my **C:** unit
* PRIMARY IDE SLAVE    ST*****016A  set to AUTO  -  this is my **F:** unit

**_QUESTION A:_** If I install UBUNTU on my Primary IDE _Slave_ / **F:** Ill be able to choose or specify with which one to boot or load on the BIOS settings ???? or I need to physically set/inverse the jumpers in the hard disks manually inside the Pc to set the hard disk with Ubuntu as master everytime I want to use it. ????

**_QUESTION B:_** If I use [WUBI]("http://wubi-installer.org/") Ill have the option to specify installing UBUNTU from my CD to my Secoandary unit or the Wubi applications needs to download Ububntu by its own obligatorily ?????

*[COLOR="Navy"]Thanks in advance guys[/COLOR]*.....

---

### Post by caen1944 on 2007-08-25
Anyone have any success installing ubuntu to a second hard drive. I am about to give it a try and I don't want to mess up my mbr.

I just installed ubuntu on a server for our office, and had it up and running with samba and the works in less than a day. So I thought cool, I'd like to give this a try on my personal computer. However I didn't remember anything during the installation about being asked where to put the grub, but there was only one disk.....

Here is my setup. I have 4 SATA drives, 2 are in RAID 0 with windows XP (games), the third contains windows 2003 (work). I have just installed a fourth one to put ubuntu on. Normally I use the boot menu that is provided by my bios (F8) to switch between XP and 2003. 

How can I install ubuntu so that I can continue to use the bios boot selector? I don't want to touch my MBR (and it might be tricky to fix with the RAID setup). Or do I even have a single MBR, as my bios does the selecting of the boot disk?

Where in the installation should I be asked where to install grub? And where should I install it, /dev/sdc or /dev/sdc1 (assuming my linux drive will be /dev/sdc)?

Thanks All. I'll be sure to post a reply if I get this to work out....

---

### Post by caen1944 on 2007-08-25
> **caen1944 said:**
> Anyone have any success installing ubuntu to a second hard drive. I am about to give it a try and I don't want to mess up my mbr.

I just installed ubuntu on a server for our office, and had it up and running with samba and the works in less than a day. So I thought cool, I'd like to give this a try on my personal computer. However I didn't remember anything during the installation about being asked where to put the grub, but there was only one disk.....

Here is my setup. I have 4 SATA drives, 2 are in RAID 0 with windows XP (games), the third contains windows 2003 (work). I have just installed a fourth one to put ubuntu on. Normally I use the boot menu that is provided by my bios (F8) to switch between XP and 2003. 

How can I install ubuntu so that I can continue to use the bios boot selector? I don't want to touch my MBR (and it might be tricky to fix with the RAID setup). Or do I even have a single MBR, as my bios does the selecting of the boot disk?

Where in the installation should I be asked where to install grub? And where should I install it, /dev/sdc or /dev/sdc1 (assuming my linux drive will be /dev/sdc)?

Thanks All. I'll be sure to post a reply if I get this to work out....

Ok here is an update.

I did the install of ubuntu to the free drive. It was /dev/sdc as predicted. I did a manual partitioning and clicked "advanced" at the end of the partitioning step. This gave me a box where I could type in where I wanted the boot loader installed. I typed in /dev/sdc and away it went. Install completed, seemed fine until I rebooted.

First, windows boots fine. Then I selected the linux drive with my bios boot select, and I am presented with a grub menu asking which OS I want. I have the choice of windows2003 or ubuntu. The ubuntu install saw my RAID as two separate disks that it couldn't read. When I selected 'Ubuntu" I get the error "Error 17 - could not boot the selected partition"

I have no idea where to go from here. At least I didn't mess up my windows disks.

Any ideas

---

### Post by caen1944 on 2007-08-26
> **caen1944 said:**
> Ok here is an update.

I did the install of ubuntu to the free drive. It was /dev/sdc as predicted. I did a manual partitioning and clicked "advanced" at the end of the partitioning step. This gave me a box where I could type in where I wanted the boot loader installed. I typed in /dev/sdc and away it went. Install completed, seemed fine until I rebooted.

First, windows boots fine. Then I selected the linux drive with my bios boot select, and I am presented with a grub menu asking which OS I want. I have the choice of windows2003 or ubuntu. The ubuntu install saw my RAID as two separate disks that it couldn't read. When I selected 'Ubuntu" I get the error "Error 17 - could not boot the selected partition"

I have no idea where to go from here. At least I didn't mess up my windows disks.

Any ideas

Ok, finally got it to work. After the grub error 17, it kicks me out into the grub> prompt. So I did some poking around on the net and it turns out that you can type "find /vmlinuz" at the grub prompt, which returned (hd0,0). My grub boot script said something like "root  (hd2,0) as its first line. Following the grub instructions I edited this line to say (hd0,0) and tada, it boots into ubuntu. 

Here is what I figure. During Ubuntu install, the raid disks are detected as sda and sdb, but grub sees them in the bios as the 3rd disk. So when ubuntu installer built the grub script it thought that I was going to boot from the first partition of the third disk. But in realiity, the linux disk is the first one reported to grub, so the proper boot disk is the first partition of the first disk (hd0,0). 

All I need to do now is to figure out how to permanently alter my grub boot script. No big deal though, I can use ubuntu in the meantime. Interestingly, once in ubuntu the os reports my raid array as /dev/sdb1 and my other windows disk as /dev/sdd1. I don't know what happened to /dev/sdc, but i guess it doesn't matter.

Hope this helps anyone in the same situation

---

### Post by Hyperpc on 2007-10-09
When I tried to install ubuntu it doesn't say where to install the grub i am trying to install ubuntu 7.04 of the live cd

---

### Post by obi.juan on 2007-10-21
It would be nice if in the future Ubuntu has this install option using and configuring automatically the Windows boot loader without modifying the MBR, in a real install of the OS (not loopmounted one). Newbies (in partitioning/OS installation) or fearfuls will appreciate a lot this feature.

---

### Post by sandysandy on 2007-11-03
> **dcstar said:**
> Everyone should note that only the first 446 bytes of the MBR holds the bootloader code and only these should be backup up/restored.

Doing a full 512 byte sector could well muck up your partition data.

If you have a working Ubuntu system (with Grub), then you can save the MBR that uses Grub with the following command:
```
sudo dd if=/dev/**hda** bs=446 count=1 of=backup-mbr
```

The "**hda**" must be replaced by the boot drive identifier for your particular system!

After a Windows install, boot up off a Ubuntu Live CD, mount the drive where you have saved the backup-mbr file and then do the following in a terminal:


```
sudo dd if=backup-mbr bs=446 count=1 of= /dev/**hda**
```

You will still have to manually add the Windows system to the Grub menu.lst file, but at least your Ubuntu system should boot up as before.

[COLOR="Blue"]i typed the following commands[/COLOR]
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=446 count=1 of=backup-mbr
1+0 records in
1+0 records out
446 bytes (446 B) copied, 3.7373e-05 seconds, 11.9 MB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=446 count=1 of=backup-mbr
1+0 records in
1+0 records out
446 bytes (446 B) copied, 3.5752e-05 seconds, 12.5 MB/s


can someone [COLOR="Blue"]advise me where the backup is stored.[/COLOR]
i am using live CD (gutsy installed on first IDE hdd but unable to boot, second hdd (SATA) has win XP)

regards

---

### Post by sandysandy on 2007-11-03
is the backup of MBR in some system folder.
also is it possible to do search for it.

[COLOR="Blue"]edit[/COLOR] i found the backup in the home folder. renamed it to todays date for better identifying at later date.

also for restoring backup the following command worked:-

sudo dd if=full_path_of_your_back_up of=/dev/sda bs=1 count=446 

for example

sudo dd if=/home/ubuntu/03novbackupdevsdb-mbr of=/dev/sdb bs=446

(where 03novbackupdevsdb-mbr is my backup of MBR)

---

### Post by moving_target on 2007-11-03
"It would be nice if in the future Ubuntu has this install option using and configuring automatically the Windows boot loader without modifying the MBR, in a real install of the OS (not loopmounted one). Newbies (in partitioning/OS installation) or fearfuls will appreciate a lot this feature. "

Id like to second and third that.

Ive been a windows user for years. I've also some experince in AIX. Ive programmed a bit. I'm not exactally a novice.  Setting up a dual boot system with the tools provided by the linux community is a nightmare.

If Grub is such a piece of crap...  then why is it included in the distro?

enough ranting.   I like what I see with Ubuntu, and want to have it installed so that I can boot back and forth and possibly transition too it when Im ready.

since the grub boot loader option is a disaster, Im trying the method discussed in this thread.

I have a single OS drive with a 75 gb windows partition. I partitioned the rest of the drive for Ubuntu. Ubuntu installed, but grub failed.

I can boot to the ubuntu CD, fire up a terminal and run grub, but it does not like the /dev/fd0 option.  how do I find out what grub maps my drives too so that I can provide it with the proper syntax.

thanks

---

### Post by Leion on 2007-12-07
i tried with the method,
installed grub into my usb fat32 drive
The grub files are still in my / 

did the copying of the MBR of the usb into windows
it only shows a GRUB and does nothing if my USB drive is not plug in

if it is plug in, i will be able to boot ubuntu.

any idea why?

---

### Post by hbj983 on 2008-01-28
Hello everybody, i'm an italian guy and i'm reading this interesting 3d!
I have windows Vista and i want install Ubuntu 7.10 without Grub,
anybody can (patiently) show me how do?
I never install linux i already use a live distribution!

Thank you so much:)

p.s. i'm sorry for my english..

---

### Post by hbj983 on 2008-01-30
There's anybody there?!?:)

---

### Post by sandysandy on 2008-02-01
i think you will need a bootloader (like GRUB) for booting ubuntu. any reason why u do not want to use GRUB.

regards

---

### Post by Brain_of_J on 2008-03-05
I'm attempting to install ubuntu for the first time as a part of a dual boot system.
I installed windows xp on a logical partition of my HD.
When I attempted to install Ubuntu 7.10 on the remaining partition, it worked completely.  In fact, it installed in the remaining partitioned space without prompting me what so ever...what am I  doing wrong?
(i'm a copmlete and utter newbie at this and know nothing about compiling from files...installing grub...anything...)  i'm trying to learn though.
Ideas?  
Speak slowly in short sentences please :)

---

### Post by jken146 on 2008-03-05
What is the problem you are experiencing?  You say it worked completely.

---

### Post by arashiko28 on 2008-03-05
I guess that you are seeing some error message when you boot up windows about the MBR. Ignore it, that's what I did, after a few days it never showed up and I can use both partitions without any problem. Don't try to fix the MBR because you will delete the GRUB and bye bye Unbuntu partition, will have to reinstall. I guess that this is because that partition was created with some program to do it and not from the fresh install of windows. Also, GRUB has to modify the MBR to allow you to select the OS you feel in the mood of using.
Good luck!

---

### Post by Brain_of_J on 2008-03-05
the installation worked but upon booting, i don't have the option to choose which OS i want to boot into.
It boots directly into XP.

I looked in BIOS and there is only one logical HD listed in the list of boot options...

---

### Post by shedokan on 2008-04-26
what if I set up ubuntu without a boot loader?
can I create it using the live cd?

---

### Post by JarZe on 2008-05-25
Hi, I've installed Ubuntu 8.04 and it works great. 
This is what I've done:

1. I had WinXP Pro installed on hd #1
2. I installed Ubuntu on hd #2
3. I made the ubuntu.bin in a shared partition
4. I copied the file (ubuntu.bin) from the shared partition to the drive where windows is installed (c:\)
5. I created the entry in boot.ini (c:\ubuntu.bin="UBUNTU")

When I reboot I get the menu displaying both entries in the boot.ini file, which is Windows XP Pro and UBUNTU. I can perfectly boot into WinXP, but when I try to boot into UBUNTU it gives me some error and doesn't boot. 
I tried again and it said something like there's a file missing in system32 folder... 

Am I doing something wrong here?
What should I do in order to be able to boot into both systems?
Right now I have to unplug one hard drive (the XP one) to get into Ubuntu, and that's definitely not the best practice...

Thanks in advance,
JarZe

---

### Post by meierfra. on 2008-05-25
This method does not  quite work if Ubuntu and Windows are on separate drives. 

I can show you how to make it work, but it is a little bit tricky and I don't really recommend it. If you can boot of your second hard drive, I would recommend to install grub to the mbr of the second hard drive.


In either case I would need to output of

```
sudo fdisk -l
```
( l is a lowercase L)

to give detailed instructions.
(Boot from the Ubuntu LiveCD and type that command in a terminal (Applications->Accessories->Terminal))

---

### Post by troopii on 2008-06-30
I Think I just messed up my computer pretty bad. First, I was running Ubuntu 8.04 as my only OS, and everything was working perfectly, until I decided to add XP (thanks diablo 2) without consulting any guides beforehand. So, I forgot to back up my grub, which is now gone. Only XP will boot regardless if I select my other partition as boot. Please someone help me reverse engineer this problem so I can get back to my beloved ubuntu.

---

### Post by rated727 on 2008-07-17
> **BiggoCharley said:**
> I've installed Ubuntu 5.04 a couple of times now and I have never been prompetd for a location to install grub --what am I missing?
Charley

In the final screen of the installation there is a button marked "advanced".  This is where you can set the option to install GRUB.  Otherwise, the install uses a default.

---

### Post by bobbyfiend on 2008-09-06
James,

As all the kids seem to be saying (about 10 years ago), you are teh roxXorz. I followed your instructions, and although I had to keep recursively looking up the meanings of the very basic commands you specified, and how ubuntu's file system works, and how to mount and then find floppies and USB drives, I got it done.

In other words, all delays were caused by my need to progress along the basic linux learning curve. No delays caused by bad instructions or even idiosyncratic computer issues.

Everything went exactly as planned. I am now a dual-booting type of person, and my MBR was not messed up. Both XP and ubuntu 8.04 are purring smoothly. Thanks.

--bobbyfiend (complete ubuntu/linux n00b)

---

### Post by Chris Lopez on 2008-10-29
Hi Guys,

Would appreciate your help here.

I'm using Ubuntu 8.04 and I followed the instructions as per using a floppy.

I've managed to get everything over into windows, modified my mbr and sure enough when I start my PC I get the option of choosing Windows or Ubuntu.

However as someone mentioned early in this post, when I select Ubuntu. I get the message " GRUB_ " with the underscore flashing.

I can load both OS's with the floppy in, so I can use them both, however it is a very inelegant solution.

Any advice in Ubuntu noobish would be appreciated.

---

### Post by Chris Lopez on 2008-10-30
Sorry can I bump this. I'm so close to having Ubuntu running perfectly.

---

### Post by caljohnsmith on 2008-10-30
Chris Lopez, is Ubuntu on the same HDD as Windows? Also, I'm just wondering, is there any special reason why you want to use this method? Personally I think this tutorial is a little out-of-date and that there are better methods now, rather than adding Grub to Windows boot loader. For instance, there is Grub4DOS, which you can use entirely in Windows as a replacement for the Windows boot loader, and you can configure it so that you have only one boot screen on start up to boot Windows or any Ubuntu kernel; with the method this tutorial uses, you will always have to go through two boot screens to access Ubuntu, assuming you want to have a choice of kernels. If you let me know what your goals are, I might be able to suggest a better solution than what this tutorial covers. It's up to you though. :)

---

### Post by Chris Lopez on 2008-10-31
> **caljohnsmith said:**
> Chris Lopez, is Ubuntu on the same HDD as Windows? Also, I'm just wondering, is there any special reason why you want to use this method? Personally I think this tutorial is a little out-of-date and that there are better methods now, rather than adding Grub to Windows boot loader. For instance, there is Grub4DOS, which you can use entirely in Windows as a replacement for the Windows boot loader, and you can configure it so that you have only one boot screen on start up to boot Windows or any Ubuntu kernel; with the method this tutorial uses, you will always have to go through two boot screens to access Ubuntu, assuming you want to have a choice of kernels. If you let me know what your goals are, I might be able to suggest a better solution than what this tutorial covers. It's up to you though. :)

Thanks for your reply! :)

Basically when I initially went to install Ubuntu onto my second HDD I had a number of problems. Grub wasn't working properly and I wasn't getting the choice of OS's that I was hoping for. Upon my second attempt I did a bit more research and found this post, which seemed to offer a good solution. Ideally I just want the one screen with two OS options.

Since then I understand a fair bit more, have backed up my windows MBR properly so that if anything does go wrong I can get back to Windows ok.

I should add that my main HDD is Sata and the HDD that Ubuntu is on is an IDE HDD.

Any help you can give me would be much appreciated.

---

### Post by caljohnsmith on 2008-10-31
OK, the fact that you have Ubuntu on a different HDD than Windows is why you couldn't use the method in this tutorial, because you have to install Grub to the boot sector in a special way if Ubuntu is on a different HDD. 

Can you change your BIOS boot order so that the Ubuntu IDE HDD boots first on start up? If you can do that, it is most ideal, because then you can easily leave your Windows drive untouched and just boot Windows or Ubuntu from the Grub menu on your Ubuntu drive. Here is how you can install Grub to the MBR of your Ubuntu drive:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then if you set your BIOS to boot the Ubuntu drive, you should get the Grub menu on start up, but booting either Windows or Ubuntu from the Grub menu probably won't work yet; so when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See if you can get this far, and we will work from here; or let me know if you run into problems. :)

---

### Post by Chris Lopez on 2008-11-01
Cal, you are a legend.

That seemed to work like a charm mate. I don't even know if I need to adjust anything else as I seem to be able to boot everything from GRUB now.

Many Thanks!

---

### Post by caljohnsmith on 2008-11-01
That's great to hear it worked, Chris. :) Did you modify your Grub's menu.lst though with the new change? If you don't, you'll have to do the same temporary menu editing every time you start up. If you haven't edited your menu.lst with the change, then just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change all the Ubuntu entries to use the (hd0,Y) that worked. Also be sure to change the groot line so that it uses the same (hd0,Y):
```
# groot=(hd0,Y)
```
And lastly, do you need to add an entry for Windows in your Grub menu?

---

### Post by Chris Lopez on 2008-11-02
Hi Cal,

Thats the great thing, I didn't have to change anything in the Grub Menu. I changed HDD priority in the BIOS before installing grub and it all seemed to work. When I went to edit the Grub menu it already had the correct settings. Didn't have to do anything and windows worked with no tweaking (well apart from removing the extra info in the MBR).

Great fix mate thank you. Now thinking of installing Ubuntu on my Mum's PC. Gave her a demo today and she loves it. :)

Thanks again buddy!

---

### Post by chippy57 on 2008-11-02
Solved

---

### Post by jdackle on 2008-11-17
> **caljohnsmith said:**
> Personally I think this tutorial is a little out-of-date and that there are better methods now, rather than adding Grub to Windows boot loader. For instance, there is Grub4DOS, which you can use entirely in Windows as a replacement for the Windows boot loader, and you can configure it so that you have only one boot screen on start up to boot Windows or any Ubuntu kernel;


Hi caljohnsmith,

That sounds great! I'm just trying to dual-boot Windows Vista and Ubuntu 8.10 from partitions sda1 and sda7 respectively.
I tried installing GRUB to the MBR and, for the first time since I use Linux, it didn't work (darn, LiLo never failed either when I was using it! lol).
Then again, it is the frist time I try to install Linux to this machine (HP Pavilion dv6710 Notebook) or alongside Windows Vista, so... :mrgreen:

I've poked around and there seems to be several problems with the HP Pavilion dv6000 series, particularly with acpi.

Anyways, I've pretty much finished Grub4dos installation, except I haven't edited the menu.lst file yet.
I will use the LiveCD to edit the menu.lst file in Windows, according to what's on the Ubuntu system's menu.lst to properly boot Ubuntu too.
**Still, I have a question: How will I then update that file when new kernel releases come through Ubuntu? Will I have to do it manually or is there some way to automate it?**

---

### Post by caljohnsmith on 2008-11-17
> **jdackle said:**
> 
Still, I have a question: How will I then update that file when new kernel releases come through Ubuntu? Will I have to do it manually or is there some way to automate it?
Yes, you can automate it by creating a "symbolic link" in your /boot/grub folder that points to the menu.lst in the Vista partition. But before I help you with that, since you have Vista, have you checked out [EasyBCD]("http://neosmart.net/dl.php?id=1")? That's maybe a better alternative for you since you have Vista. And here's a [tutorial]("http://neosmart.net/wiki/display/EBCD/Ubuntu") for adding Ubuntu to Vista's boot loader via EasyBCD. Let me know what you decide to do, and I can give you a hand if you want it. :)

---

### Post by jdackle on 2008-11-19
Thanks for the reply, caljohnsmith. :)

That symlinkin' does make sense... :mrgreen:
However, I gave up on trying to install Intrepid (too many serious problems) and installed Hardy instead - all goes well and, indeed, I can now boot to Vista from Hardy's GRUB (not Grub4dos). More exactly, I boot to the Grub4dos menu, which I'm assuming means I can boot directoly to Vista even without Grub4dos.

The Grub4dos menu does have that handy "Press F8..." for Vista so it might still be handy to me.
But if I decide otherwise, how can I completely remove Grub4dos? I manually  installed it through the instructions in the README.GRUB4DOS file.

---

### Post by caljohnsmith on 2008-11-19
> **jdackle said:**
> 
But if I decide otherwise, how can I completely remove Grub4dos? I manually  installed it through the instructions in the README.GRUB4DOS file.
I think the easiest way to remove Grub4DOS would be to use the EasyBCD program that I mentioned to remove it from your Vista boot menu, and once you've confirmed that works OK, you can delete the "grldr" and "menu.lst" files in your Vista C:\ root directory. Let me know how that goes.

---

### Post by jdackle on 2008-11-20
Ok, so this is how it went...

I installed BCDEdit and it is very easy and handy indeed! 8)
So I removed the Grub4dos entry in the "Add/Remove Entries" section.
And the I went on to snif a little bit of the rest... and ended up, for whatever "reason", just reinstalling Vista's original bootloader! Which, of course, not only did restore my direct bootability to Windows as it also removed any chance of booting to Linux! ](*,)

So, eventually, I did use BCDEdit to be able to boot to Ubuntu and from there, reinstall GRUB to the MBR... 8)
I then just had to go back to BCDEdit to remove the link to booting Ubuntu from the BCD - otherwise, I would have two menu-screens instead of one to boot to Windows.

So, in brief:
Is BCDEdit good for restauring your Vista's bootloader, YES. :)
Is it good to just remove Grub4dos, probably! Only I myself was too dumb to actually properly test that! :lol:
Is it good to restore bootability to Linux once you've removed GRUB from the MBR? DEFINITELY! 8)

And as such, I think it's safe to assume Grub4dos would have been properly removed from the Windows-boot.
Moreover, I actually  got an exact copy of the Grub4dos default-menu when rebooting to Ubuntu the first time. To be able to do this (boot to Linux w/o a Linux loader actually in the MBR), BCDEdit uses "Neogrub", which seems to be in everything similar to Grub4dos, only automated by BCDEdit. 8)
Also, Grub4dos manual installation (which I'd done, see my posts above) is little more than editing Vista's BCD. ;) After it's been cleared off the BCD, all you have to do is remove the menu.lst and grldr and grldr.mbr files from your Windows root-directory - I had to manually do this after running BCDEdit.

---

