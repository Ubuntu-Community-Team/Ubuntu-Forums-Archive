---
title: "HOWTO: Double Clock Speed Problem"
date: 2005-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-07-30
This is a HOWTO about a problem which can be very annoying and which affects mainly the computers with AMD64 processor (but not only) with some motherboards (e.g. my motherboard: MSI RS480). If you notice that the mouse pointer freezes randomly and everything goes slow then you might be affected by the &#8220;Double Clock Speed&#8221; problem.

Make sure this is your problem:

open:  Applications &#8211; System Tools - "System Monitor" (from the menu in GNOME). If you  have only KDE (then maybe you're using Kubuntu) you should install System Monitor by using Synaptic (as I've noticed &#8220;KSysguard&#8221; in KDE doesn't detect the problem). Click on &#8220;Resources&#8221;: you will see  &#8220;CPU1&#8221;: and the percentage of usage of your processor. If the percentage is high (try this without any programs running), i.e. something like 50% or more then you have this problem.

Another test: play an mp3 in Totem (or another app). If it goes too fast then you have this problem

[COLOR="Red"]UBUNTU 64bit SECTION[/COLOR]

NOTE: this trick works on 64bit systems ONLY (if you want to use Ubuntu 32bit you should look at the end of the page or you will have to patch your kernel, something which will not be dealt in this HOWTO).

I had this problem and I solved it thanks to NickB's help, so all the credits go to him. Thanks again Nick.

Alberto

[You need a kernel 2.6.12.x or higher (and a 64 bit Ubuntu system of course).
The one which comes with Ubuntu Breezy is ok.]
 
1) Launch &#8220;Terminal&#8221; (or &#8220;Konsole&#8221;) (the command line) and prompt:
sudo gedit /boot/grub/menu.lst
(or if you use KDE put kate instead of gedit, or nano if you haven't them, which is unlikely)

look for these lines:

## ## Start Default Options ## ## default kernel options ## default kernel options for automagic boot options ## If you want special options for specific kernels use kopt_x_y_z ## where x.y.z is kernel version. Minor versions can be omitted. ## e.g. kopt=root=/dev/hda1 ro # kopt=root=/dev/hda2 ro console=tty0 [COLOR=Red]no_timer_check [/COLOR]

Just add  [COLOR=Red]no_timer_check[/COLOR] in the kopt line (exactly where you see it in the example above, LEAVE THE REST OF YOUR FILE UNTOUCHED)

3) Save the file and restart your computer (otherwise the trick might not work)

4) After you have restarted your computer open &#8220;Terminal&#8221; (or Konsole) and prompt:

sudo update-grub

5) restart your computer again


Enjoy!

--------------------------------------------------------------------------------------------------------------------------------
[COLOR=Red]UBUNTU 32BIT SECTION[/COLOR]

This trick doesn't work for everyone (it depends on your hardware). For this reason I suggest you to try it on an Ubuntu Livecd


1) 

a) [COLOR="Red"]If you haven't installed Ubuntu 32 bit yet...
[/COLOR]
The only way to find out without installing Ubuntu 32bit is to use an Ubuntu (32-bit) LIVECD and to try to prompt one (and ONLY 1 PER TIME) of the following options at boot:

1) noapic nolapic
OR
2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll


If you don't know how to do it follow these steps:
Boot the Ubuntu live CD
You will see a screen with the Ubuntu logo and the word "boot:" at the bottom of the page (if you don't do anything for several seconds the Livecd will go ahead and you won't be able to type anything)
type (the words will appear beside "root:") "Live + the boot option" (e.g. "Live noapic nolapic") and press Enter

Then the livecd should work as usual.

[COLOR="Blue"]OTHERWISE[/COLOR]

b) [COLOR="Red"]If you have installed Ubuntu...[/COLOR]
If you have installed Ubuntu and you want to see if it works for you:

Turn on your computer and keep pressing "ESC" until you get to the GRUB menu.

Select your kernel with your keyboard arrows (DO NOT PRESS ENTER) and Press "e".
Then you will see 3 lines:
```
root (hd0,0)
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash
initrd	/boot/initrd.img-2.6.12-10-k7
```

Select the line which begins with the word "kernel" and press "e" to edit it.

Add one [ONLY ONE i.e. only 1) or only 2) ] of the following things at the end of the line:

1) noapic nolapic
so that it will look like this:
```
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapic
```
OR
2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll
OR
6) noapic acpi=off
OR
7) noapic acpi=noirq nolapic

Then get off the text field and press "b" to boot the kernel.

See if it works. 
If Ubuntu DOESN'T boot, it hangs or you can't use your internet connection just reboot and follow the instructions again but try with option 2) or 3), 4), etc. until you solve your problem.

When you find the boot options which work for you [ 1), 2) or 3), etc. ] you have to set them permanently (because the options you have jsut set will only last until you reboot).

Follow the first part of the guide (the one about Ubuntu 64 bit) and put the options which work for you (e.g. "noapic nolapic") instead of "no_timer_check".

Enjoy!

Alberto

---

### Post by Orborde on 2005-08-19
I got to step 4 and could not complete it because I got the following at boot:
/dev/hda2 does not exist! Dropping into a shell....
Or something like that.

It works, however, when I boot into 2.6.10 instead of .12 in Grub (that's what I'm doing now), though we still have the glorious 50% problem. I downloaded linux-amd64-generic from the Breezy repositories and its dependencies. This is an HP Pavilion zv6130, if anyone might want to know.

---

### Post by tseliot on 2005-08-19
Can you post your fstab file? You can do it in this way:

Open Terminal or Konsole and type:

sudo gedit /etc/fstab (you can put "kate" instead of "gedit" if you use KDE)

---

### Post by FLeiXiuS on 2005-08-19
[QUOTE=Orborde]I got to step 4 and could not complete it because I got the following at boot:
/dev/hda2 does not exist! Dropping into a shell....
Or something like that.

It works, however, when I boot into 2.6.10 instead of .12 in Grub (that's what I'm doing now), though we still have the glorious 50% problem. I downloaded linux-amd64-generic from the Breezy repositories and its dependencies. This is an HP Pavilion zv6130, if anyone might want to know.[/QUOTE]

/dev/hda2 was his given example.  You have to set /dev/hda2 to whatever your root paritition is.

---

### Post by Orborde on 2005-08-19
[QUOTE=tseliot]Can you post your fstab file? You can do it in this way:

Open Terminal or Konsole and type:

sudo gedit /etc/fstab (you can put "kate" instead of "gedit" if you use KDE)[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0


/dev/hda2 is indeed my root file system.

---

### Post by tseliot on 2005-08-19
Post also /boot/grub/menu.lst (in the same way as before)

---

### Post by Orborde on 2005-08-19
I'm dual-booting Linux  and Windows XP Pro from the same hard drive. Windows is on /dev/hda1.
```
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro console=tty0 no_timer_check

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-6-amd64-generic Default 
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro console=tty0 no_timer_check quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-6-amd64-generic Default (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro console=tty0 no_timer_check single
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic Previous 
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hda2 ro console=tty0 no_timer_check quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic Previous (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hda2 ro console=tty0 no_timer_check single
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-6-amd64-generic 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-6-amd64-generic root=/dev/hda2 ro console=tty0 no_timer_check quiet splash
initrd		/boot/initrd.img-2.6.12-6-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-6-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-6-amd64-generic root=/dev/hda2 ro console=tty0 no_timer_check single
initrd		/boot/initrd.img-2.6.12-6-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda2 ro console=tty0 no_timer_check quiet splash
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda2 ro console=tty0 no_timer_check single
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by tseliot on 2005-08-19
The files look correctly set.

Now, tell me what happened when you tried to boot kernel 2.6.12. You said this happens:

/dev/hda2 does not exist! Dropping into a shell.

What does it happen then? Kernel Panic, a system freeze, or what?

---

### Post by Orborde on 2005-08-19
[QUOTE=tseliot]The files look correctly set.

Now, tell me what happened when you tried to boot kernel 2.6.12. You said this happens:

/dev/hda2 does not exist! Dropping into a shell.

What does it happen then? Kernel Panic, a system freeze, or what?[/QUOTE]

I was a little off on the error message, seeing as I'm doing it from memory.
"Unable to find volume group "hda2"
ALERT! /dev/hda2 does not exist! Dropping to a shell!"

Then I get
"/bin/sh: can't start tty: job management disabled"
and then I get a command line with only # at the beginning of each line; it appears I'm running /bin/sh...somewhere. I can navigate the filesystem a little, but it's a stripped-down filesystem; only the shell and inbuilt commands seem to be there. The /home directory is not there at all, for example, nor any other software. I assume that this is because /dev/hda2 is not mounted at all when it should be mounted at / , so I'm getting the "core" Linux filesystem only. When I go to /dev, ls hda2 and ls hda0 turn up nothing.

Should I type in "exit", we get a kernel panic about attempting to kill init.

---

### Post by tseliot on 2005-08-19
This is weird. And I've come to think it could be related to the Breezy kernel (they can be buggy sometimes).
What I need you to do is to follow my HOWTO about kernel compilation. It's an easy, and step-by-step guide and it doesn't require any experience (you know how to install things in Synaptic orKynaptic and how to open Terminal or Konsole, don't you?  :)  ).

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835) 

Download the latest stable kernel from  "www.kernel.org" (2.6.12-4, I guess) instead of Ubuntu sources (which is recommended in my guide and follow the same steps as the guide.


If you have any problems, please ask me.

---

### Post by Orborde on 2005-08-19
[QUOTE=tseliot]This is weird. And I've come to think it could be related to the Breezy kernel (they can be buggy sometimes).
What I need you to do is to follow my HOWTO about kernel compilation. It's an easy, and step-by-step guide and it doesn't require any experience (you know how to install things in Synaptic orKynaptic and how to open Terminal or Konsole, don't you?  :)  ).

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835) 

Download the latest stable kernel from  "www.kernel.org" (2.6.12-4, I guess) instead of Ubuntu sources (which is recommended in my guide and follow the same steps as the guide.


If you have any problems, please ask me.[/QUOTE]
 Um...what do I change in order to use the 2.6.12 kernel? You use apt-get a lot in that example. Where do I get the 2.6.12 source? I assume I need to add in a repository...

---

### Post by tseliot on 2005-08-20
You have to download it from [www.kernel.org](www.kernel.org) (it's the source)

When you get to Point 3 of the guide and you get to these lines you have to modify them in the following way:

[COLOR=Blue]cd /home/your_username_folder/directory_where_you_put_the_downloaded_kernel[/COLOR] [COLOR=Red](instead of cd /usr/src)[/COLOR] (e.g. "cd /home/alberto/download" in my case)
sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2 [COLOR=Blue]/usr/src[/COLOR] [COLOR=Red](use the name of the file you downloaded)[/COLOR]
sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux [COLOR=Red](use the name of the file you downloaded)[/COLOR]
cd /usr/src/linux

And in point 4:

remember to get to "File Systems"
Select your filesystem, then select "ext3 journalling filesystem support" and press the spacebar (a "*" will appear beside it).

Press the right arrow and select exit.

Then you can go on with the instructions in Point 4.

The rest of the HOWTO is ok.

---

### Post by Orborde on 2005-08-21
Hmm...well, I recompiled the kernel but didn't specify the filesystem type. And that may explain the error message that I'm about to ask you about, at least partially:
"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
And this happens both on my new kernel I just compiled and the old one that I was using, so my Linux installation is now Officially Broken. Would it be possible to use a Live CD to get in, and then mount in the still-intact (I think) filesystem as / and recompile with the correct options?

Or is there an option somewhere I can modify? After all, it does seem to have destroyed all my previously working kernels, instead of just having a problem with the one I compiled myself...

EDIT: It doesn't seem to be working. Ack! Help!
Thanks for all the help so far, though.

---

### Post by tseliot on 2005-08-21
I don't know how to help you. You can use a livecd to recover the files you need (important documents, etc) but I recommend you a reinstallation from scratch. I know it's annoying but I'm sure next time it won't happen again as now you are a bit more expert than before. C'mon don't give in and try again!

---

### Post by wingedlizard on 2005-08-31
[QUOTE=Orborde]I got to step 4 and could not complete it because I got the following at boot:
/dev/hda2 does not exist! Dropping into a shell....
Or something like that.

It works, however, when I boot into 2.6.10 instead of .12 in Grub (that's what I'm doing now), though we still have the glorious 50% problem. I downloaded linux-amd64-generic from the Breezy repositories and its dependencies. This is an HP Pavilion zv6130, if anyone might want to know.[/QUOTE]

I get the same problem on my zv6 with a new breezy colony3 
install.  It worked with 5.04 ( well untill I blew it away with the
new install).  

My /dev/hdx is correct.  

   Decompressing Linux ... done.
   Booting the kernel.
   Unable to find volume group "hda6"
   Alert! /dev/hda6 does not exist  Dropping to a shell!

   BusyBox <blah>
  #

It can't find the partition.  I don't see fdisk or any way I can see
what partitions exist on the drive.

.... Try 3..........

wl


It looks like comp really can't

---

### Post by iserlohn on 2005-09-02
After a lot of searching the web for a solution to this (in the dmesg)

warning: many lost ticks.
Your time source seems to be instable or some driver is hogging interupts
rip default_idle+0x20/0x30

The solution seems to be to put "notsc" in the kernel options line in grub.conf. This will disable the tsc for dual core processors (Athlon X2 3800+ in this case) (which seems to get out of sync). All of my clock problems disappeared after that.

---

### Post by sas13 on 2005-09-06
thanks for the howto, but I've had only partial success.

I have the following laptop-

compaq presario v2311US

Amd turion 64
512 ram
60 Gb HD
ATI radeon xpress 200m 128mb

after following the instructions in the howto (downloading kernel version 2.6.12-8; the only >2.6.12 available now) and updating grub the cpu usage level is solved and the laptop is noticeably faster, but with the following problems:

in the early stages of the boot process I get the error-

sed: unsupported command I
repeated 5-6 times.
later in the boot sequence this message apears:
*FATAL udev is already active on /dev/


startup continues, and completes, but networking is disabled. (and maybe other effects as well)

any ideas??

---

### Post by tseliot on 2005-09-06
[QUOTE=sas13]thanks for the howto, but I've had only partial success.

I have the following laptop-

compaq presario v2311US

Amd turion 64
512 ram
60 Gb HD
ATI radeon xpress 200m 128mb

after following the instructions in the howto (downloading kernel version 2.6.12-8; the only >2.6.12 available now) and updating grub the cpu usage level is solved and the laptop is noticeably faster, but with the following problems:

in the early stages of the boot process I get the error-

sed: unsupported command I
repeated 5-6 times.
later in the boot sequence this message apears:
*FATAL udev is already active on /dev/


startup continues, and completes, but networking is disabled. (and maybe other effects as well)

any ideas??[/QUOTE]


get back to your previous kernel and compile a new one. You can follow my guide, it's for newbies:

[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

You can download and compile kernel 2.6.13 from kernel.org if you wish

---

### Post by sas13 on 2005-09-07
thanks for the response, but I'm still not there yet...

I compiled a new kernel (from a vanilla 2.6.13), according to your HOWTO but with one difference:

in part 3 when I got to 

```
 sudo make menuconfig 
```

I got an error allong the lines of ```
ERROR - your display is not big enough to run menuconfig, at least 80 columns and 19 rows required
```

I checked .config and it looked like it had the correct options selected, so I just did 

```
sudo make config
```

and did the rest acording to the HOWTO (I'm a newbie so I might have done something that doesn't make any sense at all...)

there were no further errors, but when I reboot with the new kernel I get an error similar to the previous post:

```
..MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel Panic - not synching: VFS: unable to mount root fs on unknown block(0,0)
```

luckily, I can still boot with my old kernel. Any ideas?

---

### Post by cholis on 2005-09-07
After reading (almost) all discussion about how to solve double clock speed problem, in this post and others, i really couldn't understand why ubuntu haven't release  official kernel upgrade for amd64.

---

### Post by sas13 on 2005-09-08
RESOLVED -

well updgradig to breezy seems to have done the trick

-I removed all he kernels I had installed (via synaptic or that I compiled myself)

-dist-upgraded to breezy

-installed kernel 2.6.12-8 using synaptic

-applied tseliot's fix to grub


everything seems to be running smoothly now, without the CPU cycles going off the wall...

now if I can only find out how to get ubuntu to support frequency scaling on my Turion processor.....

---

### Post by cokhavim on 2005-09-09
[QUOTE=tseliot]

NOTE: this trick works on 64bit systems ONLY (if you want to use Ubuntu 32bit you will have to patch your kernel, something which will not be dealt in this HOWTO).

[/QUOTE]

anyone care to tell me how to patch my kernel to fix this problem in my 32-bit system?  i know how to compile a kernel (thanks to tselliot's great how-to found elsewhere), but i have no idea what to fix in the kernel to fix the double clock speed problem.

---

### Post by tseliot on 2005-09-09
[QUOTE=cokhavim]anyone care to tell me how to patch my kernel to fix this problem in my 32-bit system?  i know how to compile a kernel (thanks to tselliot's great how-to found elsewhere), but i have no idea what to fix in the kernel to fix the double clock speed problem.[/QUOTE]
The trick works only with kernel 2.6.10 (Ubuntu's default)

as soon as you turn on your computer after the bios you will see a the word "GRUB" etc. press ESC until it gets you to Grub boot menu and select kernel 2.6.10 from the list and press "e" to edit the line and add:
noapic nolapic

then get off the text field and press "b" to boot the kernel.

If it works then follow my guide again and put "noapic nolapic" instead of "no_timer_check" (remember to boot kernel 2.6.10 only)

---

### Post by cokhavim on 2005-09-09
thanks!  it worked!  

btw, i suggest you modify your HOWTO to include the 32-bit people, since it's only a small difference in the procedure.  i searched the forum, and i couldn't find another HOWTO for this problem for 32-bit systems.

---

### Post by tseliot on 2005-09-09
[QUOTE=cokhavim]thanks!  it worked!  

btw, i suggest you modify your HOWTO to include the 32-bit people, since it's only a small difference in the procedure.  i searched the forum, and i couldn't find another HOWTO for this problem for 32-bit systems.[/QUOTE]
Ok I'll add it to the guide

---

### Post by Vladtux on 2005-09-23
Hey Dude I install the kernel and put no_time_check in the grub ...then ROXS

Thanks a lot!!1 and my laptop run faster then before!!!!



:D


Esop

---

### Post by tseliot on 2005-09-23
[QUOTE=Vladtux]Hey Dude I install the kernel and put no_time_check in the grub ...then ROXS

Thanks a lot!!1 and my laptop run faster then before!!!!



:D


Esop[/QUOTE]
I'm happy for you, it's such an annoying problem.

---

### Post by alesdoc on 2005-10-06
Hi, i've  a question.
I've an AMD Turion 64 bit that's affected to this problem. Following the HOWTO i've resolved it. 

I'd like to try a 32-bit Ubuntu version on my laptop. You wrote that the HOWTO for 32-bit works only with the 2.6.10 kernel. Do you mean only wiht this kernel or also with later version?

If i put on my laptop Breezy colony 4, can i use the kernel that i find? or have i to do something recompile and so on?

Thanks.
Bye bye

---

### Post by tseliot on 2005-10-06
[QUOTE=alesdoc]Hi, i've  a question.
I've an AMD Turion 64 bit that's affected to this problem. Following the HOWTO i've resolved it. 
I'd like to try a 32-bit Ubuntu version on my laptop. You wrote that the HOWTO for 32-bit works only with the 2.6.10 kernel. Do you mean only wiht this kernel or also with later version?
If i put on my laptop Breezy colony 4, can i use the kernel that i find? or have i to do something recompile and so on?
Thanks.
Bye bye[/QUOTE]
I have tried it with my previous motherboard (MSI RS480) which was not well supported by Linux and the computer hanged when I tried to boot with the 32-bit trick (noapic) using kernel 2.6.11 or a Breezy kernel. This doesn't mean it won't work for you. I depends on your hardware (your motherboard and its bios). It works flawlessly on my new computer with an Asus a8v Deluxe motherboard. The only way to find out is to use a Breezy colony 4 (32-bit) LIVECD and to try to prompt "noapic nolapic" at boot. If you don't know how to do it follow these steps:
Boot the Ubuntu live CD
You will see a screen with the Ubuntu logo and the word "root:" at the bottom of the page (if you don't do anything for several seconds the Livecd will go ahead and you won't be able to type anything) 
type (the words will appear beside "root:") "Live noapic nolapic" and press Enter

Then the livecd will work as usual.

I might add these steps to the guide so as to make some users' lives easier.

---

### Post by alesdoc on 2005-10-06
...i will try.
I've some problems with my Ubuntu 64-bit version, therefore i'd like to try a 32-bit. I've tried one month ago with a Hoary 32-bit and my laptop worker very slow and i was non able to start gnome.

I swicht to breezy (a 64-bit version) and my laptop worked still slow. I solved the problem with your howto, but how i sad i've some problems.

So i download the live cd. I try it (before without the trick). If it works...i swicht to 32-bit version. If it doesn't work i try with your trick...and if it works i swicht...otherwise i stay with my 64-bit version.

Ti tengo informato....ciao ciao

Thanks

My Laptop:
HP NX6125
AMD Turion 64bit
80GB HD
512 RAM
Video: Integrated ATI Mobility Radeon X300
Audio: Conexant AC '97 CODEC, Integrated 16-bit Sound Blaster Pro-compatible audio

---

### Post by alesdoc on 2005-10-06
i've tried with the Live CD (breezy colony 4 32bit version), but it did'nt work.

Neither without nor with your trick the cd is not able to star gnome. The Laptop stops itself during the splash screen.

I work and i've not so many time. I stay with my 64-bit version and i try to resolv its problem (sound with mp3, suspend_to_ram, etc)

Grazie comunque.

Ciao

---

### Post by tseliot on 2005-10-07
[QUOTE=alesdoc]i've tried with the Live CD (breezy colony 4 32bit version), but it did'nt work.

Neither without nor with your trick the cd is not able to star gnome. The Laptop stops itself during the splash screen.

I work and i've not so many time. I stay with my 64-bit version and i try to resolv its problem (sound with mp3, suspend_to_ram, etc)

Grazie comunque.

Ciao[/QUOTE]
I'm sorry :(  but I'm sure you can enjoy your Ubuntu 64bit.

---

### Post by alesdoc on 2005-10-07
...it's not a problem. I've tried...;)

---

### Post by Orborde on 2005-10-14
To paraphrase [Magical Trevor](http://www.weebls-stuff.com/toons/magical+trevor+2/)...
[i]It's back, and it's got a new trick
The Double Clock Speed Bug is ten times as slick
As the last time
The last time you saw it
Now you will see why we really abhor it.[/i]

So, I decided that 64-bit Ubuntu was too problematic, since nothing actually supports 64-bit yet, and rather than fiddle with 32-bit userlands and so forth, I decided to junk my somewhat damaged installation on my AMD64 laptop and install Breezy 32-bit. Well, the Double Clock Speed/50% CPU bug is back, and this time, it's harder to eradicate. Throwing no_timer_check, noapictimer, and noapic/nolapic all have the same effect: the problem is solved. Unfortunately, my network interface no longer works. D'oh! So I changed it back and have been living with double-speed clocks for the time being.

I'm using the k7 kernel, after installing the i386 distro and installing the k7 via Synaptic. Up-to-date Breezy and all that. So, help? :)

---

### Post by tseliot on 2005-10-14
[QUOTE=Orborde]To paraphrase [Magical Trevor](http://www.weebls-stuff.com/toons/magical+trevor+2/)...
[i]It's back, and it's got a new trick
The Double Clock Speed Bug is ten times as slick
As the last time
The last time you saw it
Now you will see why we really abhor it.[/i]

So, I decided that 64-bit Ubuntu was too problematic, since nothing actually supports 64-bit yet, and rather than fiddle with 32-bit userlands and so forth, I decided to junk my somewhat damaged installation on my AMD64 laptop and install Breezy 32-bit. Well, the Double Clock Speed/50% CPU bug is back, and this time, it's harder to eradicate. Throwing no_timer_check, noapictimer, and noapic/nolapic all have the same effect: the problem is solved. Unfortunately, my network interface no longer works. D'oh! So I changed it back and have been living with double-speed clocks for the time being.

I'm using the k7 kernel, after installing the i386 distro and installing the k7 via Synaptic. Up-to-date Breezy and all that. So, help? :)[/QUOTE]

The problem with the network is caused by "noapic nolapic" as I've said in my guide it doesn't work for everyone. On the other hand the trick for AMD64 (you need Ubuntu 64bit) doesn't cause any problem.

---

### Post by Orborde on 2005-10-14
[QUOTE=tseliot]The problem with the network is caused by "noapic nolapic" as I've said in my guide it doesn't work for everyone. On the other hand the trick for AMD64 (you need Ubuntu 64bit) doesn't cause any problem.[/QUOTE]
Is there any way I can set up the AMD64 kernel and leave everything else 32-bit? I really don't want to have to set up the full amd64 Ubuntu, since then I'd have to muck about with 32-bit chroots and things in order to get stuff working.

---

### Post by tseliot on 2005-10-14
[QUOTE=Orborde]Is there any way I can set up the AMD64 kernel and leave everything else 32-bit? I really don't want to have to set up the full amd64 Ubuntu, since then I'd have to muck about with 32-bit chroots and things in order to get stuff working.[/QUOTE]
I had the same problem with my previous computer. Believe me it's not as hard as it seems, you can set up a new completely functioning (with 32bit apps running through chroot) 64bit system with a bit of tweaking.

AFAIK you can't use a 64bit kernel when using a 32bit system. Sorry.

---

### Post by Orborde on 2005-10-14
[QUOTE=tseliot]I had the same problem with my previous computer. Believe me it's not as hard as it seems, you can set up a new completely functioning (with 32bit apps running through chroot) 64bit system with a bit of tweaking.

AFAIK you can't use a 64bit kernel when using a 32bit system. Sorry.[/QUOTE]
I think you're right. I attempted to compile a 64-bit kernel and run it on my system, but it appears to be no different; I think it may have sneakily compiled as 32-bit despite my instructions. So, can you offer me any advice on running a 64-bit kernel, but using chroot to get into gdm, etc, so that I'm running an entirely (well, as much as possible) 32-bit system on a 64-bit substructure? This is as opposed to setting up each 32-bit app specifically, even though they can't access the system GTK, etc. because it's in 64-bit land.

So I'm thinking I'd install the base system, set up the chroot environment, and then apt-get ubuntu-desktop  into the 32-bit chroot...? I won't move forward until I get feedback on this...

It sure would be nice if this bug got fixed.

---

### Post by tseliot on 2005-10-15
[QUOTE=Orborde]I think you're right. I attempted to compile a 64-bit kernel and run it on my system, but it appears to be no different; I think it may have sneakily compiled as 32-bit despite my instructions. So, can you offer me any advice on running a 64-bit kernel, but using chroot to get into gdm, etc, so that I'm running an entirely (well, as much as possible) 32-bit system on a 64-bit substructure? This is as opposed to setting up each 32-bit app specifically, even though they can't access the system GTK, etc. because it's in 64-bit land.

So I'm thinking I'd install the base system, set up the chroot environment, and then apt-get ubuntu-desktop  into the 32-bit chroot...? I won't move forward until I get feedback on this...

It sure would be nice if this bug got fixed.[/QUOTE]
BTW it's a kernel bug (it's not related to Ubuntu, at least not in particular). There was a user who used chroot to set up 32bit account or sth like that, you should use the search function of this forum.
I haven't tried to chroot an entire account I only used the applications that are 32bit only through chroot (there is a guide about it in this forum) and it worked fine.

---

### Post by ammiel on 2005-11-06
I'd just like to say after doing what you said, it runs considerably better, BUT i still get a cycle where it goes crazy for a few seconds.

---

### Post by tseliot on 2005-11-07
[QUOTE=ammiel]I'd just like to say after doing what you said, it runs considerably better, BUT i still get a cycle where it goes crazy for a few seconds.[/QUOTE]
Ok, perhaps you refer to the fact that the percentage of CPU use seems high when you open "system monitor" but then it decreases (this happens also to computers which are not affected by the double clock speed bug)

---

### Post by punkr0x on 2005-11-13
I appear to have this same problem with my new laptop (32-bit).  noapic and nolapic cause other problems (screen refresh rate is not correct, system locks up on boot...); this being a kernel problem, am I just plain out of luck using linux on this system?

---

### Post by punkr0x on 2005-11-13
Seem to have solved my own problem:  just using "noapictimer" (instead of noapic) seems to have solved my problem...

---

### Post by tseliot on 2005-11-14
[QUOTE=punkr0x]Seem to have solved my own problem:  just using "noapictimer" (instead of noapic) seems to have solved my problem...[/QUOTE]
Thanks for reporting the solution to your problem. It might be useful to other users who have the same problem.

---

### Post by Luke on 2005-11-23
[QUOTE=punkr0x]Seem to have solved my own problem:  just using "noapictimer" (instead of noapic) seems to have solved my problem...[/QUOTE]

thank you, thank you, thank you. seems to have solved my double clock speed on 32 bit laptop (presario m2000) with 2.6.12-10-686 kernel.

(maybe this should be added to the first page?)

---

### Post by Mr. Electric Wizard on 2005-12-15
I'm crossing my fingers on this one...
I always find these cool articles when I first get to work.  Makes it really hard to wait until the end of the day when I can try them out. :) 

The only way I noticed this being an issue was if you watch a DVD with VLC, or Totem-xine, the video is sped up double speed.  And I installed tuxracer last night and it was also unplayably fast.  Then I found this thread...

The one thing that seems really wierd to me about this is that the processor in my HP ze2308wm is a 32 bit Sempron 2800.
I installed the x386 version of Ubuntu, but it seems like this bug would only affect people with 64bit processors, or 64bit Ubuntu installs.
Weird.

[crossing fingers]

---

### Post by Mr. Electric Wizard on 2005-12-15
BTW, I just successfully did this with the vanilla Breezy install on my AMD Sempron 2800 (32 bit) and it worked wonderfully!
Thanks a lot!
:)

---

### Post by wempy on 2005-12-16
AMD Sempron 2800+ laptop 

I had tried all of these settings without success, still getting double clock speed.

I did notice that when trying the noapic, nolapic setting that the machine always locked up while loading the RAID modules (lvm, evlms).

I disabled those as I don't use RAID on this machine and now the noapic, nolapic setting works, the clock is running normally with an offset of around 0.01 secs when updating to a time source.

to stop the raid modules from loading I did:
```

sudo update-rc.d -f mdmadm-raid remove
sudo update-rc.d -f lvm remove
sudo update-rc.d -f evms remove

```

if you need to put it back then: 
```

sudo update-rc.d mdadm-raid start 04 S .
sudo update-rc.d mdadm-raid start 50 0 6 .
sudo update-rc.d lvm start 26 S .
sudo update-rc.d lvm start 50 0 6 .
sudo update-rc.d evms start 27 S .
sudo update-rc.d evms start 49 0 6 .

```

I then discovered BUM which makes the process so much easier:
```

sudo apt-get install bum

```

While trying to fix this problem I have seen all sorts of howtos about it with some mentioning that you need a post 2.6.12 kernel and currently I am running a full upgrade to dapper, the latest kernel for which is 2.6.15-8-k7, but being on the bleeding edge I can't get the ati radeon xpress 200m to work properly and gnome is a little broken at the moment, so I intend this afternoon to do a reinstall of breezy, where I know I got all the hardware working to see if just turning of the raid modules helps.

If this does then I can say goodbye to XP forever - yippee!!

---

### Post by wempy on 2005-12-16
Have now done a clean install of Breezy, and removed the Raid thingies as above.  All is working great EXCEPT that when upgrading to the new kernel 2.6.12-10 the modules were re-enabled (not a show-stopper as it is easy to re-disable them).  But I don't have access to the CD/DVD anymore - whoops.

At least now I have a stable system that I can use.  Will keep this thread updated with anything else I find out.

---

### Post by tseliot on 2005-12-16
Thanks for reporting, all of you! :)

---

### Post by tseliot on 2005-12-16
[QUOTE=wempy]Have now done a clean install of Breezy, and removed the Raid thingies as above.  All is working great EXCEPT that when upgrading to the new kernel 2.6.12-10 the modules were re-enabled (not a show-stopper as it is easy to re-disable them).  But I don't have access to the CD/DVD anymore - whoops.

At least now I have a stable system that I can use.  Will keep this thread updated with anything else I find out.[/QUOTE]
You should start a thread about your cdreader in the Hardware help section

---

### Post by whig on 2005-12-16
AMD64 X2 3800+ CPU
ABIT AN8 ULTRA NF4 Motherboard
ABIT RADEON RX600PRO-128 PCIE Video
Ubuntu 5.10
Using fglrx

Clock was running fast, not 3x at first but instead would start slowly advancing and speeding up until system was rebooted. Tried the no_timer_check and it made no difference. Neither ntpd nor chrony could apparently correct the drift.

Ultimate fix in my case was adding "clock=pmtmr notsc" to the grub menu.lst. Clock stable and happy for over 24 hours for the first time.

---

### Post by tseliot on 2005-12-27
Hey guys, I have updated the guide with a new instruction (which solved the problem on my father's computer).
It's for Ubuntu 32bit. Now noapic won't make your computer hang!


Check it out!

---

### Post by cdhotfire on 2005-12-27
I use noapic acpi=off, with 32bit.  Seems to work all the time.  But stand alone they do not work.

---

### Post by dfava on 2006-02-02
I have an AMD Sempron 3200+ (32 bits) with Ubuntu and the same clock speed issue was happening. I tried "noapic nolapic" and it did solve the clock issue but it significantly slowed down the internet (ssh into the machine became really slow and the web pages served from the computer would get displayed very slowly).
The same happened when I tried noapictimer.
I also tried the flags "clock=pmtmr notsc" but then my computer did not boot at all.
The "noapic acpi=noirq" did not solve the clock speed problem, but it did solve another problem that I had, which was: the computer would power-down but would not reboot when I tried a sudo reboot.

What really solved the problem for me (of both clock speed and rebooting) was "noapic acpi=noirq nolapic"

---

### Post by tseliot on 2006-02-04
Ok thanks for reporting. I'll add both the methods to the guide

EDIT: GUIDE UPDATED!

---

### Post by Absolute on 2006-03-28
Thank you!  I was going out of my mind, with complaints about email messages being sent from dates in the future, my "time tracker" jumping ahead, etc.

The no_timer_check fix seems to have worked perfectly for me; at least after 30 minutes the date is the exact same after I 'rdate' with another server.

Thanks for saving me hours of annoyances!

---

### Post by embsupafly on 2006-05-04
If your hardware clock is good, but your sys clock isnt, couldn't you just set up a cronjob for this command:

hwclock --hctosys

I have mine set to do so every minute, it does work, but could doing this be a bad thing?

---

### Post by jynyl on 2006-10-20
The no_timer_check in /boot/grub/menu.lst didn't work here, but notsc seems to have done it.  Clock was running about 50% fast, ie gained 30 seconds every minute.
System: Kubuntu 6.06, 2.6.15-27-amd64-generic
Intel Core 2 Duo E6600 on Asus P5LD2

---

### Post by tseliot on 2006-10-20
> **jynyl said:**
> The no_timer_check in /boot/grub/menu.lst didn't work here, but notsc seems to have done it.  Clock was running about 50% fast, ie gained 30 seconds every minute.
System: Kubuntu 6.06, 2.6.15-27-amd64-generic
Intel Core 2 Duo E6600 on Asus P5LD2

thanks for reporting

---

### Post by michaeldina on 2007-10-22
I'm running Ubuntu 7.10 AMD 64 x2 with a cheap ole Geforce 6100SM-M motherboard and my sys clock was running 3x the normal speed. I used the 

noapic acpi=off 

option and it solved the problem!!:) Thank you very much for ensuring my Ubuntu experience is the greatest. Amarok will now play at normal speed!!

---

