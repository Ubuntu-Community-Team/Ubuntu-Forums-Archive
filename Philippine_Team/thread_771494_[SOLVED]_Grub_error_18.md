---
title: "[SOLVED] Grub error 18"
date: 2008-04-27
forum: Philippine Team
---

### Post by dodimar on 2008-04-27
I tried to install Xubuntu 8.04 yesterday. After rebooting, this is what i got...

Grub loading.....
Error 18

Can't figure how to fix this.. 

I searched the internet about this, it says I have to place GRUB at the "front" which I believe it is in the fron because I chose to install GRUB at the MBR.

Help...

---

### Post by Cresho on 2008-04-27
here are some tools.  look for my explanation of grub and this will help you explain your situation to help us more about your problem.  I had to look for my post first and then when i came back, your post was way down the list and had a hardtime finding it.

[http://ubuntuforums.org/showthread.php?t=726841&highlight=grub](http://ubuntuforums.org/showthread.php?t=726841&highlight=grub)

---

### Post by dodimar on 2008-04-27
Can't do anything because the error shows after reboot from installation. It just stops there and doesn't show me any option.

here's how my hard drive is partitioned (for info)

Partition 1: Primary 60GB ntfs WindowsXP boot
Partition 2: Primary 60GB fat32 shared_data_drive
partition 4: Logical 1GB swap
Partition 5: Logical 32GB ext3 /

---

### Post by indionine on 2008-04-27
have you tried doing that thing on the BIOS? 

[http://ubuntuforums.org/showthread.php?t=6448](http://ubuntuforums.org/showthread.php?t=6448)

---

### Post by dodimar on 2008-04-28
It is really hard to get support either from the forums or the chatroom. This is the second time I was "turned down" by the Linux community.

I hope reformatting my HDD will fix this. If not, have to look for other distro that won't give me the same headaches... or just go back in using Windows...

I'm a beginner in Linux...

Honestly, I am disappointed...

---

### Post by dodimar on 2008-04-28
BTW, thanks to Nhatz for some suggestions and offer to help me fix this problem...

---

### Post by loell on 2008-04-28
> **dodimar said:**
> It is really hard to get support either from the forums or the chatroom. This is the second time I was "turned down" by the Linux community.

I hope reformatting my HDD will fix this. If not, have to look for other distro that won't give me the same headaches... or just go back in using Windows...

I'm a beginner in Linux...

Honestly, I am disappointed...

the is no  guarantee on a free tech support, timing has also something to do with it, if no one had a particular knowledge on a particular problem asked at particular time? then either you continue on asking and wait patiently  or  search for a solution on your own, thats the  way it is.

you can also have the option of a paid support, if you want resolve at the the highest level.

---

### Post by dodimar on 2008-04-28
[http://ubuntuforums.org/showthread.php?t=757903](http://ubuntuforums.org/showthread.php?t=757903)

Daming kumontra when I posted this... pero eto ako ngayun... yung isang post ko regarding shutdown issue nasa page 3 or more na. Eto, pilit ko lang nilalagay sa taas.. baka sakaling may tumulong...

thanks kay nhatz kasi nag-offer siya ng help....

(sentimiento de asukal, hehe)

Paid? hehe,,, di ko kaya... poor lang ako...

Sana maayos ko na, para makapag-migrate na ko "fully" to linux...

---

### Post by |{urse on 2008-04-28
>  Re: Grub error 18
here are some tools. look for my explanation of grub and this will help you explain your situation to help us more about your problem. I had to look for my post first and then when i came back, your post was way down the list and had a hardtime finding it.

[http://ubuntuforums.org/showthread.p...highlight=grub](http://ubuntuforums.org/showthread.p...highlight=grub)

funny thing is, someone actually did try to help you. I was going to give you a wlkthrough on reinstalling grub but after seeing your condemnation of the linux community i was less inspired to help.

---

### Post by dodimar on 2008-04-28
> **|{urse said:**
> funny thing is, someone actually did try to help you. I was going to give you a wlkthrough on reinstalling grub but after seeing your condemnation of the linux community i was less inspired to help.

I think I made a reply for that,, I can't do anything because I can't boot to Linux... it just stops after the message error 18...

"condemnation of the linux community" - when did saying what I experienced a "condemnation". What would you feel if someone said to you "there is nothing we can do about it".

I am not condemning the Linux community (I am part of it), I am just saying what I experienced. Is it "wrong" to express what I felt? If so, my apologies.

---

### Post by |{urse on 2008-04-29
You are forgiven. lol

here's a nice howto on reinstalling grub from the livecd (the ubuntu cd you installed from, assuming it's not the alternate install cd, has a live operating system from which you can administer a non-functioning system). This walkthrough is by catlett, thank them if it works ^^ Please don't be upset, we've all shaken a fist @ linux at one point or another.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dodimar on 2008-04-29
> **|{urse said:**
> You are forgiven. lol

here's a nice howto on reinstalling grub from the livecd (the ubuntu cd you installed from, assuming it's not the alternate install cd, has a live operating system from which you can administer a non-functioning system). This walkthrough is by catlett, thank them if it works ^^ Please don't be upset, we've all shaken a fist @ linux at one point or another.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thank you for forgiving..

Will try this one.. unfortunately, the one I downloaded is the alternate install CD (so I can use it for low spec systems).
Will this work if I use a live cd for earlier version of Ubuntu?

---

### Post by |{urse on 2008-04-29
id say yes but not 100% certain. It would probably be best to use a full cd matching your current version. Anyone else have thoughts on this? pls correct me. lol @ forgiven, why, you're so welcome! :)

---

### Post by dodimar on 2008-04-29
Hmnn.. I'll download the Live CD (just 2 - 3 hrs).. I really don't want to reformat my hard drive now (would take me a week to back up tons of files, reinstall and setup windowsXP - considering my schedule, I don't have enough time).

I hope it would work...

Thanks...

---

### Post by Cresho on 2008-04-29
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

YEs  I remember this one too!  It helped me.!  I had an error 15 or 18 I forgot but I Decided to redoo my hardware for hardy heron with 2 hardrives and ubuntu being sata0 and windowsxp sata1.  Doing this helped me very much but Learning this method was  a good expirience for me as well.

---

### Post by Samhain13 on 2008-04-30
I remember following that guide too when I trashed my Gutsy installation months ago (it left me with no operating system because of a faulty CD drive, but that's another story). It's very helpful.

Anyway, easy ka lang bro. Things like this are very frustrating indeed but it's a situation where you really need to keep your head. :)

---

### Post by dodimar on 2008-04-30
I am almost finished downloading the Live CD (I think it is already finished, don't know, I slept, hehehe.)....

hehehe,,, peace...

---

### Post by lswest on 2008-04-30
if the liveCD doesn't run, you can download the SuperGRUBDisk (google it, i'd post a link but i have to run off to super now atm) - basically a tool to restore GRUB and other bootloaders.

---

### Post by Samhain13 on 2008-04-30
That will come in handy! Thanks. :D
[http://www.supergrubdisk.org](http://www.supergrubdisk.org)

---

### Post by lswest on 2008-04-30
thanks for the thanks, and yes, i find it very useful ;)

---

### Post by dodimar on 2008-04-30
Aaaaahhhhh,, I wish I have time for this.... I won't be home this weekend... And I sleep daytime and work in the evening.... 

Anyways, thanks for the information (I take back my word that it is hard to get support from the forums - throwing it to the trash bin,, hehehe)..

thanks guys, going to post for any updates regarding this...

:guitar:

---

### Post by Samhain13 on 2008-04-30
Aha! Bampira ka din pala! (Apir!) :D

---

### Post by killer_d76 on 2008-04-30
same problem here, boot grub don't show up upon boot, i followed the first procedure only from this link ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)), though now i need to press "ESC" to show this grub;(after doing something stupid on the terminal)..


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=76eabe08-3c4f-46a3-b755-2ece15b19744 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=76eabe08-3c4f-46a3-b755-2ece15b19744 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=76eabe08-3c4f-46a3-b755-2ece15b19744 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



... i have an 80GB hardisk drive, but when i checked the system, Hardy uses 63.9GB only, so i think the remaining 30+Gig is occupied by windows xp, is it possible for me to revive or boot back to windows?

-thanks

---

### Post by Samhain13 on 2008-04-30
**This needs an expert to verify.**

In this section,

```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

comment "hiddenmenu" like so:

```

# hiddenmenu

```

So that the menu will be shown by default. If that's what you like. Anyway, it's a good thing to remember that before making any sort of changes to files like this one, make a backup first. :)

---

### Post by dodimar on 2008-04-30
> **Samhain13 said:**
> Aha! Bampira ka din pala! (Apir!) :D

Hehehe....

---

### Post by killer_d76 on 2008-05-01
mga bossing is it ok for me to install XP to wipe Hardy out of the hard drive and once installedn then i'll just re-install Hardy to dual boot my laptop?.. pede po ba yun?, will i get a new grub and everything?.. thanks 

ps: need to know to your comments or suggestion before i to this procedure on my laptop! [-o<

---

### Post by loell on 2008-05-01
> **killer_d76 said:**
> mga bossing is it ok for me to install XP to wipe Hardy out of the hard drive and once installedn then i'll just re-install Hardy to dual boot my laptop?.. pede po ba yun?, will i get a new grub and everything?.. thanks 

ps: need to know to your comments or suggestion before i to this procedure on my laptop! [-o<

pwede naman, i think you need atleast 3 partitions, one for xp, then for hardy, and your swap.

---

### Post by killer_d76 on 2008-05-01
thanks loell!.. i think i should do that!, okey out of curiosity.. i noticed the first time i removed gutsy and replaced it Hardy i notice this "swap" part on the drive... what is this for? :confused:

---

### Post by loell on 2008-05-01
[swap info :)]("http://people.debian.org/~psg/ddg/node81.html")

---

### Post by killer_d76 on 2008-05-02
i got everything back.. boot grub, power and restart button etal!.. i just format my HDD re-install XP first then install Hardy after!.. now my laptop is as good as new! :guitar:

---

### Post by killer_d76 on 2008-05-03
after browsing asking about "grub" somebody gave me this link which i find very informative!  :guitar:

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by dodimar on 2008-05-04
I tried restoring GRUB using the live CD. But it failed. It still returns Grub Error 18.

Last resort - going to format my HD. But not now, maybe I would be able to do this on June.

Thanks for the tips guys. I appreciate it..

---

### Post by yssida on 2008-05-04
[Source]("http://www.saynotomilk.com/archives/5")

Try reinstalling, create a separate partition of 32 MB, and mount it at /boot.

---

### Post by dodimar on 2008-09-19
Was able to resolve this by formatting my hard drive.

After months of waiting, I was able to finally back up my files.

Now, Ubuntu is booting normally.

Next problem, installing proper drivers for ATI Radeon 9600/x1050 agp video card. that would be a different thread then.

Thanks to those who replied here.

:guitar:

---

### Post by drewdropin on 2008-10-17
I'm having the same grub problem. Error 18... I've used two other ubuntu formats and have never had these errors.

grub help indicates that my drive is too big for the motherboard. Or, that it was expecting a smaller drive it's 15 gig drive and I know this dell optiplex gx150 is able to support a 20 gig. So, that's just plain wrong. I've reinstalled grub too and that's not the problem either.

Can anyone help, right now I'm installing windows and will install ubuntu as a software program.

---

### Post by dodimar on 2008-10-18
> **drewdropin said:**
> I'm having the same grub problem. Error 18... I've used two other ubuntu formats and have never had these errors.

grub help indicates that my drive is too big for the motherboard. Or, that it was expecting a smaller drive it's 15 gig drive and I know this dell optiplex gx150 is able to support a 20 gig. So, that's just plain wrong. I've reinstalled grub too and that's not the problem either.

Can anyone help, right now I'm installing windows and will install ubuntu as a software program.

Hi, I tried reinstalling Grub also, it didn't work. My was working fine before on the same Ubuntu Version. But then, after reinstalling the exact same version, Grub Error 18 came. 

The only work around I found was to:
[LIST]
[*]Back up all your important files (I mean "all" important files)
[*]Wipe out (delete all partition, everything) your hard drive...
[*]Install Windows (if you're going to)
[*]Install Ubuntu..
[*]Restore your files...
[/LIST]

I believe it is not a problem with the BIOS since our BIOS worked perfectly before.

I think it's a problem with the partition of the hard drive. Maybe deleting and creating certain partitions on the hard drive messes up the partition table of the HD.

So, if reinstalling the Grub doesn't solve the problem, try what I did (unless someone can give something that will work).

Just make sure your back is complete and reliable so you won't lose your files.

---

