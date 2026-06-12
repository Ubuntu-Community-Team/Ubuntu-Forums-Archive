---
title: "[SOLVED] dual boot bootloader messup :l"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by marine63 on 2008-07-12
hello i installed windows on one partition and ubuntu on the other when i boot i go directly to windows instead of grub menu. if anyone can help me with this it'll be appreciated thx

---

### Post by Bachstelze on 2008-07-12
Did you just install your Ubuntu, or did ut just stop working now? It coud either be that GRUB wasn't installed correctly, or that something overwrote it (Windows reinstall?).

---

### Post by miwaypet on 2008-07-12
Did you install Ubuntu after windows. If you install windows after Ubuntu it will not "see" Ubuntu. You have to install ubuntu after the windows partition and installation.

---

### Post by bumanie on 2008-07-12
Suspect you installed ubuntu, followed by windows. Boot live cd and post the output of terminal command > sudo fdisk -l (that's a lower case L)

---

### Post by marine63 on 2008-07-12
i installed ubuntu after i installed windows.

---

### Post by bumanie on 2008-07-12
> i installed ubuntu after i installed windows. 
That's good. 
Grub must not have installed correctly. Usually it can be successfully reinstalled off the live cd. Still need the terminal output of > sudo fdisk -lfrom the ubuntu live cd to be able to help further.

---

### Post by marine63 on 2008-07-12
Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc01ac01a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12187    97892046    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46e978f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19313   155131641    7  HPFS/NTFS
/dev/sdb2           19314       38913   157437000    5  Extended
/dev/sdb5           19314       38156   151356366   83  Linux
/dev/sdb6           38157       38913     6080571   82  Linux swap / Solaris

---

### Post by kansasnoob on 2008-07-12
No answers from me, I'm hoping Bumanie can sort this out.

But I'm curious why the "lst" shows:

/dev/sda1 * 1 12187 97892046 7 HPFS/NTFS

in one place and:

/dev/sdb1 * 1 19313 155131641 7 HPFS/NTFS

Doesn't sda mean drive #1 while sdb means driven #2?

The great thing is that your Windows partition is up and working properly! Everything else can be sorted out. I'm just not sure how to do it.

I'm a "gui" guy! I can usually sort things out using "gui" but I'm worthless with the text from "cli".

---

### Post by Markissocoollike on 2008-07-12
I know this seems quite a stupid answer... but have you tried installing it on the same partition... funnily enough all I did was that and I managed to get the dual boot without any problems I'd call this a simple answer to a simple problem but I dunno if it will work for you... guess I was either lucky or just impatient :P

---

### Post by kansasnoob on 2008-07-12
> **Markissocoollike said:**
> I know this seems quite a stupid answer... but have you tried installing it on the same partition... funnily enough all I did was that and I managed to get the dual boot without any problems I'd call this a simple answer to a simple problem but I dunno if it will work for you... guess I was either lucky or just impatient :P

Install what where?

I was hoping Bumanie would jump back on this because my way is the gui way.

---

### Post by kansasnoob on 2008-07-12
I don't mean to sound grouchy. This looks pretty generic:

> /dev/sdb1 * 1 19313 155131641 7 HPFS/NTFS
/dev/sdb2 19314 38913 157437000 5 Extended
/dev/sdb5 19314 38156 151356366 83 Linux
/dev/sdb6 38157 38913 6080571 82 Linux swap / Solaris

I'm using a pretty clean machine myself, nothing complicated:

[ATTACH]77505[/ATTACH]

Nothing fancy!

---

### Post by kansasnoob on 2008-07-12
What throws me is the "sda" and "sdb" thing:confused:

If this is one hard drive I'm confused:confused:

---

### Post by bumanie on 2008-07-12
Please output > cat /boot/grub/menu.lst

---

### Post by marine63 on 2008-07-12
no such file or directory...

---

### Post by kansasnoob on 2008-07-12
Marine63,

Do you have only one hard drive?

Never mind, me dumb!

---

### Post by bumanie on 2008-07-12
Sorry, I have to go to bed, as I have been at work all night - that's why I had to go earlier as I had work to do. Just remembered you are working off a live cd, the previous command won't work off a live cd. Go to places --> Computer --> File System --> double click boot --> double click grub and search for menu.lst Open it and copy and paste it to the forum. With the rest of the information you have given, someone should be able to help you - as said I have been up all night and must sleep. Good luck.

---

### Post by kansasnoob on 2008-07-12
> **bumanie said:**
> Sorry, I have to go to bed, as I have been at work all night - that's why I had to go earlier as I had work to do. Just remembered you are working off a live cd, the previous command won't work off a live cd. Go to places --> Computer --> File System --> double click boot --> double click grub and search for menu.lst Open it and copy and paste it to the forum. With the rest of the information you have given, someone should be able to help you - as said I have been up all night and must sleep. Good luck.

I appreciate your dedication! You've helped me many times!

---

### Post by marine63 on 2008-07-13
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0c953795-b874-41e3-ab7a-6b01a2a6c6ff ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash xforcevesa

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0c953795-b874-41e3-ab7a-6b01a2a6c6ff ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0c953795-b874-41e3-ab7a-6b01a2a6c6ff ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by marine63 on 2008-07-13
help?

---

### Post by bumanie on 2008-07-14
Boot with live cd. In terminal > sudo grub > root (hd1,4) > setup (hd0) > quitReboot. This should setup in grub in your bootable windows installation. You should now be able to boot and get a choice of booting into windows or ubuntu. Grub set itself up in the wrong windows partition - the partition, I suspect is a data partition. Hope it works. Sorry I didn't see your "Help" earlier. If this doesn't work download super grub disk and give it a try. Go[ here]("http://forjamari.linex.org/frs/?group_id=61&release_id=499") and download the latest .iso and burn the image to a cd-rom, the menu's are self-explanatory.

---

### Post by marine63 on 2008-07-14
when i typed in "root (hd1,4)" it said "no partition existed"
when i typed in " root (hd0,4)" it said okay and then when i rebooted I saw the grub menu but i couldnt go in any of the options ubuntu or windows
i tried super grub disk i went thru the help and i did what it said to get grub to show up and work but i got the same problem as i did above...

ill try reinstalling ubuntu later

---

### Post by bumanie on 2008-07-14
Sorry, misread something it should be > sudo grub > root (hd0,4) > setup (hd0) quit

---

### Post by marine63 on 2008-07-14
> **marine63 said:**
> when i typed in " root (hd0,4)" it said okay and then when i rebooted I saw the grub menu but i couldnt go in any of the options ubuntu or windows

:l

---

### Post by bumanie on 2008-07-14
I will review our whole discussion and see if there is something obvious that I've missed - spread over a few days, one sometimes forgets or misses something from earlier. I can add that I had a computer at one stage that would not boot correctly even when the /boot/grub/menu.lst was correct. Seemed to be a bios issue. Hope that is not the case for you. Have you tried booting ubuntu with the choice to boot GNU/Linux given in super grub disc? That's the only way I could boot that particular computer - it's a bit annoying but it meant I could use ubuntu. Worth a try.

---

### Post by BGFG on 2008-07-14
Hi, when i installed ubuntu i intentionally installed grub to the native hard drive of ubuntu, so when i started, I still booted into windows. Could'nt even see Ubuntu. But like i said, this was my intention. (maybe this occurred in your installation)
Since you're still booting into windows, your windows bootloader is working fine.
There's a free program call EasyBCD that you can use to add grub to the windows bootloader and fix your dual boot. This is how i dual boot.
hope this helps.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by bumanie on 2008-07-14
Boot with live cd. In terminal 

> sudo grub   > root (hd1,4)  > setup (hd0)   > quit   this should be the code as initially stated. The mistake I made was look at kansasnoobs screenshot, so the code is correct. Can you redo this code please and then post a copy of the grub list once finished - I want to see if it has changed. This is getting very frustrating for you I bet. 

Just looked at your fdisk -l output both windows partitions have boot flags on them. Are these both separate windows installations or is one meant to be a data partition?

---

### Post by TheLions on 2008-07-14
> **marine63 said:**
> when i typed in "root (hd1,4)" it said "no partition existed"
when i typed in " root (hd0,4)" it said okay and then when i rebooted I saw the grub menu but i couldnt go in any of the options ubuntu or windows
i tried super grub disk i went thru the help and i did what it said to get grub to show up and work but i got the same problem as i did above...

ill try reinstalling ubuntu later

check this threat:[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

it contains how to reinstall grub from livecd and solves no partition existed" problem!:)

---

### Post by bumanie on 2008-07-14
As you can't boot into either OS, I wonder whether your windows mbr is corrupt. If it is, that would also mess with grub. I suggest you go into recovery console with xp disc and fixboot; followed by fixmbr on your C:\ Then see if windows boots. If windows boots, then boot the live ubuntu cd and put in the last codes given (same as the original ones - which should be correct). Reboot and grub should work. If that doesn't work, I'm out of ideas.

---

### Post by Markissocoollike on 2008-07-14
omg... look all you need to do is install it to your partition drive on the same one as windows xp what is hard about that? 

If you can't understand that try this video:

[http://www.youtube.com/watch?v=n5x9iJWXbUY](http://www.youtube.com/watch?v=n5x9iJWXbUY)

they say you have to install wubi but I have never used this program hope this has helped!

---

### Post by Markissocoollike on 2008-07-14
my god the first sentence he uses is so funny lol!

---

### Post by kansasnoob on 2008-07-14
This is probably a repeat, or maybe even a repeat of a repeat, but if you can burn a Super Grub Disk:

[http://supergrubdisk.org/](http://supergrubdisk.org/)

I'd really try to just see what can and/or can't be "booted" using it.

I have it on CD and Floppy and have used it when I (or someone else) has things really hosed just so I can boot into any OS and see how badly I've hosed things.

Now, just as an FYI, I can't read complex menu.lst's, etc. because it induces seizures! Something about the continuous columns of comment marks: ##
       ###
sets me off into orbit!

It took twice for me to figure that out. It's due to a brain injury, but you learn as time goes along what the "triggers" are.

Anyway, because of that I've resorted more than once to creating a "brand new" separate GRUB partition which can be quite small, but it won't solve everything. It won't make a partition "bootable" if Super Grub Disk won't.

But, if that interests you, I learned how here:

[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

Thanks to:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

Sorry I can't be more help.

---

### Post by Pastortom on 2008-07-14
Im having the same problem as Original Poster kinda.. 

I couldnt get Ubuntu to boot, so after extensive research and forum lurking I found out the following:

It's possible to edit Grub loader if the partition set to load Ubuntu is wrong (i.e. set to HD1,4 when HD0,4 is the correct one)..

Super Grub is an awesome automated program which should fix any issue with GRUB during bootup, and automaticly set the bootup to load GRUB and set the right partition for Ubuntu (in my case 0,4)..

I tried first Super Grub, but it hung at the following line:

Running "embed/boot/grub/e2fs_stage1_5(HD0)"

and the above lines on my screen (didnt write them down :P) said that it found the Ubuntu kernel and the necessary files to make GRUB able to load Ubuntu when chosen to.. so I realised from the above lines that it wasnt HD0,1 which I had thought from before and which Easey BCD tells me, but indeed HD0,4 which Super Grub told me.. 

So I rebooted, went into Grub loader, pushed 'e' to edit the first line and chose: root (HD0,4) instead of (HD2,4) which was implented from before.. then I pushed esc and 'b' to boot the line "root (HD0,4)" and everything worked fine.. I thought.. for about 15 seconds..

I saw the Kubuntu loading screen, and I even saw a mouse arrow come up on the screen, but then total freeze.. I couldnt push num lock, and the HD led was continues lighting.. same as before when Super Grub ran "Running "embed/boot/grub/e2fs_stage1_5(HD0)""..

Now, at least Ive come abit further in my hellroad to learning Ubuntu.. but this is really really annoying guys, its like I hit one wall trying to install Ubuntu, then I found out how to go further, but then hit another wall, then another wall, then another wall.. its like theres no end to all the walls Im supposed to hit before I can finally browse [www.google.no](www.google.no) under OS Ubuntu =(.. 

Help?!

---

### Post by marine63 on 2008-07-14
> **BGFG said:**
> Hi, when i installed ubuntu i intentionally installed grub to the native hard drive of ubuntu, so when i started, I still booted into windows. Could'nt even see Ubuntu. But like i said, this was my intention. (maybe this occurred in your installation)
Since you're still booting into windows, your windows bootloader is working fine.
There's a free program call EasyBCD that you can use to add grub to the windows bootloader and fix your dual boot. This is how i dual boot.
hope this helps.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

i have windows xp not windows vista...

> Boot with live cd. In terminal

Quote:
sudo grub
Quote:
root (hd1,4)
Quote:
setup (hd0)
Quote:
quit
this should be the code as initially stated. The mistake I made was look at kansasnoobs screenshot, so the code is correct. Can you redo this code please and then post a copy of the grub list once finished - I want to see if it has changed. This is getting very frustrating for you I bet.

Just looked at your fdisk -l output both windows partitions have boot flags on them. Are these both separate windows installations or is one meant to be a data partition?
okay i'll do that

> check this threat:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

it contains how to reinstall grub from livecd and solves no partition existed" problem!
thx thats what im trying to do now... but no success

> omg... look all you need to do is install it to your partition drive on the same one as windows xp what is hard about that? 
i know that but it didnt work

> If you can't understand that try this video:

[http://www.youtube.com/watch?v=n5x9iJWXbUY](http://www.youtube.com/watch?v=n5x9iJWXbUY)
i alrdy understand ive installed ubuntu plenty of time b4 using different methods...

> they say you have to install wubi but I have never used this program hope this has helped!
wubi doesnt work for me b/c wubi b/c my monitor doesn't play nice with ubuntu (out of range) and also it never worked for me 
(for several other reasons)


> my god the first sentence he uses is so funny lol! 
bite me

> his is probably a repeat, or maybe even a repeat of a repeat, but if you can burn a Super Grub Disk:

[http://supergrubdisk.org/](http://supergrubdisk.org/)

I'd really try to just see what can and/or can't be "booted" using it.

I have it on CD and Floppy and have used it when I (or someone else) has things really hosed just so I can boot into any OS and see how badly I've hosed things.

Now, just as an FYI, I can't read complex menu.lst's, etc. because it induces seizures! Something about the continuous columns of comment marks: ##
###
sets me off into orbit!

It took twice for me to figure that out. It's due to a brain injury, but you learn as time goes along what the "triggers" are.

Anyway, because of that I've resorted more than once to creating a "brand new" separate GRUB partition which can be quite small, but it won't solve everything. It won't make a partition "bootable" if Super Grub Disk won't.

But, if that interests you, I learned how here:

[http://www.troubleshooters.com/linux...bpartition.htm](http://www.troubleshooters.com/linux...bpartition.htm)

Thanks to:

[http://users.bigpond.net.au/hermanzo...rub_Partition_](http://users.bigpond.net.au/hermanzo...rub_Partition_)

Sorry I can't be more help.
i've already used super grub disk.... though ill try it again later..
> 
Now, at least Ive come abit further in my hellroad to learning Ubuntu.. but this is really really annoying guys, its like I hit one wall trying to install Ubuntu, then I found out how to go further, but then hit another wall, then another wall, then another wall.. its like theres no end to all the walls Im supposed to hit before I can finally browse [www.google.no](www.google.no) under OS Ubuntu =(.. 
yes i also have many problem when both installing and using ubuntu myself...

---

### Post by Pastortom on 2008-07-14
I suggest you read through my last posts mate, as Ive discovered both how to manage the dual boots as well as how to skip the blank/black screen of death when trying to load/install Ubuntu.. 

Good luck..

---

### Post by marine63 on 2008-07-15
finally i got it to work ty everyone +reps for everyone :3

---

### Post by bumanie on 2008-07-15
> finally i got it to work ty everyone +reps for everyone :3 Great!!! Sorry it took so long, but believe it or not, having hassles like this teaches you more than you learn when everything goes smoothly. You should mark the thread as 'solved'

---

