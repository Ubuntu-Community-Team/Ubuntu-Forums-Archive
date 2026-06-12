---
title: "grub cleanup"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by trucker33377 on 2008-06-22
I would like to cleanup my grub entries i start with (e) on the entry i want to remove do i apply the (d) command to the root there? there are 3 lines

---

### Post by drs305 on 2008-06-22
Install and use StartUp-Manager. You can safely change how long the menu is displayed, the number of kernels seen, splash screen, etc - all without manually editing grub's menu.lst . 

Install it with:
```
sudo aptitude install startupmanager
```

System, Administration, StartUp-Manager.

An explanation of all it's capabilities and how to modify grub:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Come on back if you have any questions.

---

### Post by Sbarton on 2008-06-22
Just follow the post from drs 305 and you will do want you want and more.
regards

---

### Post by trucker33377 on 2008-06-22
i did but its not changing the grub all the entries are still there

---

### Post by ajgreeny on 2008-06-22
You can also, of course, uninstall any kernels you don't want or need any more, though it's always a good idea to keep two versions available from grub just in case.  As an example if you are running hardy, it started with kernel 2.6.24-16, if I remember correctly and has since updated to 2.6.24-19.  This means that without a clean up you will have 9 Ubuntu menu items showing, two for each kernel, and a memtest.  I always get rid of the unwanted kernels except for the last two, so at the moment I have the 18 and 19 versions only on my machine.  This also releases a lot of space, which although I don't really need it, makes me feel better.

---

### Post by drs305 on 2008-06-22
> **trucker33377 said:**
> i did but its not changing the grub all the entries are still there

If ajgreeny's post didn't do it, just tell us what you would like to do and we can help you fix it.

---

### Post by trucker33377 on 2008-06-22
well it looks like uninstall is what needs to be done.

where do i start

---

### Post by drs305 on 2008-06-22
The easiest method is to open synaptic and search for "*linux-image*". You can remove the older kernels from there, but as has been mentioned, it's probably best to keep at least one older one. As you remove the kernels in synaptic the grub menu.lst will also be updated and the old ones will no longer be displayed.

---

### Post by trucker33377 on 2008-06-22
i shoulda just left it alone. i uninstalled the wrong one. so kernel 2.6.22-14 is the newest one i have that will start. and xorg is not liking it at all. plus all the uninstalled kernels are still on the grub list when i do boot but the newer kernels just dont work now... so 1 step forward 2 back

xorg fixed by safeboot xfix. now i can boot 2.6.22-14

---

### Post by drs305 on 2008-06-22
> **trucker33377 said:**
> i shoulda just left it alone. i uninstalled the wrong one. so kernel 2.6.22-14 is the newest one i have that will start. and xorg is not liking it at all. plus all the uninstalled kernels are still on the grub list when i do boot but the newer kernels just dont work now... so 1 step forward 2 back

If you can get to synaptic you should be able to reinstall the latest kernel. Your grub list should have updated. If you get things back to how you want them and then want to post your menu.lst here we can clean it up for you.

Before you mess with it too much you should make a backup:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak1
```

---

### Post by trucker33377 on 2008-06-22
i did make a system backup would that restore the kernel?

---

### Post by drs305 on 2008-06-22
> **trucker33377 said:**
> i did make a system backup would that restore the kernel?

Ubuntu doesn't really have a 'system backup' - you would have to explain how you did that unless you are talking about a windows system backup. Unless you made a copy of the partition or ran some other program... Other than that, can you get into synaptic? What are you able to do at the moment?

---

### Post by trucker33377 on 2008-06-22
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=e16e6e23-fe8b-45d5-9a8e-278ab873ae9b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e16e6e23-fe8b-45d5-9a8e-278ab873ae9b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e16e6e23-fe8b-45d5-9a8e-278ab873ae9b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e16e6e23-fe8b-45d5-9a8e-278ab873ae9b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e16e6e23-fe8b-45d5-9a8e-278ab873ae9b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=e7bf977c-bbeb-4b97-960d-9c9f2b6bf964 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (recovery mode) (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=e7bf977c-bbeb-4b97-960d-9c9f2b6bf964 ro single 
initrd		/boot/initrd.img-2.6.22-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Ubuntu gutsy (development branch), memtest86+ (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

ok there it is let me say this.... I have 2 HD one has win xp and kubuntu
2nd has ubuntu hardy

im not just sure how this works but kubuntu looks to have the newest kernel on grub ubuntu stopped way back ay 22.17 i think

everything seems to be here when i do update it says im updated now but i still have to use the older kernel to boot up on grub

---

### Post by drs305 on 2008-06-22
Your menu.lst shows an older gutsy on sdb2 (second drive, second partition - this is designated as (hd1,1) in grub). It *thinks* the latest hardy kernel installed on your first drive in the first partition (hd0,0). Normally that is where windows is, but this menu.lst doesn't even mention windows.

IF:
Hardy is installed on your first drive in the first partition
AND:
You have kernel 19 installed there

Make sure you've made a backup of menu.lst, then open /boot/grub/menu.lst as root:
```
sudo gedit /boot/grub/menu.lst
```

You should be able to change the the last 3 entries in the last 3 blocks from this
```

savedefault
boot
```

to this:
```

#savedefault
#boot
```

Essentially, comment any lines that say "savedefault" and "boot".


Save this and then reboot and pick the kernel you want to use during boot.

DON'T MAKE THESE CHANGES IF YOU DON'T UNDERSTAND IT. Ask for clarification.

---

### Post by trucker33377 on 2008-06-22
i should just scrap this whole setup and start over...
/dev/sda (465.76 GiB)                ubuntu
/dev/sda1 ext3         455.62 GiB
/dev/sda2 extended      10.14 GiB
/dev/sda5 linux-swap    10.14 GiB 

/dev/sdb 279.46 GiB                    xp and kubuntu
/dev/sdb1 141.40 GiB ntfs           boot (also has a orange triangle with ! on it)
/dev/sdb2 ext3 138 GiB

this is what my partitions look like.

what would you do???

---

### Post by drs305 on 2008-06-22
I didn't mean to scare you off in the last post ;-)

Do you currently have an operating windows system and can you boot to it? Do you want to keep it or reinstall it? 

I haven't set up a dual boot system in several years, and fortunately for me I only had to do it once and it worked first time. Those with experience in these matters tend to agree that dual booting seems to go best when windows is installed first. You might also want to make sure the UUIDs are all correct.  Command "sudo blkid" will show you the actual settings, and they WILL change if you repartition the drives.

I would start fresh. You have bits of gutsy, hardy, kubuntu hanging around.
I would start a new thread with a descriptive title: 'Advice for dual boot setup' or something like that. Include the fstab results as you did here and indicate whether or not you want to preserve your current windows OS or start fresh.

As far as setups, there are as many opinions as there are people. I like having a separate parition for /home and another for /data, but that is just me. I do keep my backups on a separate drive in case of drive failures.

If you want to make the changes I recommended in the previous post I'll monitor this thread to see how it goes. Making the changes should allow you to select the system you want to boot into, assuming the kernel 19 is installed properly. If that doesn't work, you shoud be able to get back to 12 by selecting it.

Best wishes.

---

### Post by trucker33377 on 2008-06-22
all 3 op sys are booting ok its just this one thats outa wack. main reason i was thinking of a fresh start is i dont use windows on this pc anymore its left over from when i first started linux, also kubuntu was just to see how well i liked it and i dont. so that whole drive is a waste of space.
ive change alot on this pc so given the fact that hardy is messed up i dont want windows and kbuntu, it maybe best to boot and nuke. I like 7.10 it was good never had any thing go wrong with it hardy is just not working out as well. 

But i still have the grub to deal with. mepis has a nice looking grub and so does pclinuxos from all ive seen ubuntu has the worst looking layout blk and white.

so its not that you scared me ive been thinking of doing this anyway.

i tinker with with it and tend me mess up along the way at times

---

### Post by ajgreeny on 2008-06-23
This is quite interesting as grub posts go!  When you install ubuntu over an existing install, and already have a linux install on your machine, ubuntu can be a bit too clever, as it sees the original linux install end even if you overwrite that with the new ubuntu install, it still seems to add the old, and now gone, install to the menu.lst.  This can lead to some very strange looking grub menus showing.

This has happened to me several times as I run a small second hard disk to try out distros and there is always more than just ubuntu on my machine,  If I want to clean things up I do it manually, as I can find out what points to what, but it is often easier to delete the old linux partition and make a new ext3 partition before doing another install of ubuntu.  No other linux distro I've tried is as good at adding other installs to the menu, but as I say, it can be a bit confusing if you don't realise what is going on.

Sorry if that is a bit confusing to you but it is just my experience of grub complications that ubuntu can produce by being too good at adding linux OS installs.

---

### Post by trucker33377 on 2008-06-23
well as of now I have deleted the kubuntu and installed 7.10, this got the grub back up so i could get back into my main op sys 8.04. but all the gurb entries show 7.10 and restricted drivers would not work. there were older kernels and i did get to 1 that would allow update to 8.04. system is showing it as being there but theres no image on boot. I tried to update to it thinking at last this is the fix. (NOT) about 3/4 of the way into the upgrade it stopped now all the kernels on that drive are CLI only.

Im moving all my stuff to this drive and will wipe that one and call it a day

i started a new theard on kernel but it not getting me anywhere

---

