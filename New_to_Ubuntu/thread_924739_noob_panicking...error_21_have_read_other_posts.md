---
title: "noob panicking...error 21 have read other posts"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by cautious learner on 2008-09-19
hello
to start, i have read the other posts and have searched google for solutions but i'm afraid that i must be missing something pretty basic.
was working on ubuntu when i had a power outage. attempted to reboot when all was back to normal. following msg: grub 1.5 error 21.
my confusion is that i can't figure out how to get  beyond this message in order to start the fixes posted on other threads. any thoughts? pls? am working from a borrowed laptop that will be due back soon.

---

### Post by Locutus_of_Borg on 2008-09-19
insert livecd
reboot
open terminal
enter grub-install --no-floppy /dev/sda
change sda to your hardware specification
exit
reboot
all should be fine

---

### Post by cautious learner on 2008-09-19
i'm sorry. i must be doing something very wrong. i inserted the live cd, rebboted but i'm not getting anything. just the same error message

---

### Post by Locutus_of_Borg on 2008-09-19
you must set the boot order to boot from cd first

when you turn on the computer there should be a screen with your computer's manufacturer's logo on it, press F2, Esc, or whatever it says to enter SetUp then go to boot options and make cd cdrive first

---

### Post by cautious learner on 2008-09-19
ok. am i going into bios? thank you soooo much for your patience...

---

### Post by Locutus_of_Borg on 2008-09-19
yes, enter the BIOS to set the boot order to cdrom first

you should have had to do this to initially install ubuntu

---

### Post by cautious learner on 2008-09-19
hmmm...on this machine (lenovo desktop Msomething) "automatic start-up sequence" gives me the option of "enabled" for a different start-up sequence(that was the default) or "once" if you want to limit the auto start-up to once each power cycle. doesn't seem right.

---

### Post by Locutus_of_Borg on 2008-09-19
never heard of that

usually there is a tab for boot order in most bios menus

is this a really old computer?

---

### Post by kansasnoob on 2008-09-19
Reboot and just as it's coming back to life press <Del>.

---

### Post by cautious learner on 2008-09-19
ok. found the boot up order. i have diskette a as the first item being accessed during the boot up process. i didn't change it. that's where it was. really sorry for being so 'basic'. i just can't seem to escape that dreaded error 21 screen

---

### Post by cautious learner on 2008-09-19
rebooted and hit delete as it was coming to life. no change. error 21

---

### Post by cautious learner on 2008-09-19
it's actually a very new computer. M8808 is the model (lenovo)

---

### Post by kansasnoob on 2008-09-19
But, if I'm reading you right, you can't boot the live CD, eh?


Try just restarting with the live Cd in.

---

### Post by Therion on 2008-09-19
You're looking for a screen that lets you change what device the PC looks at to boot from first.  
We want it to check the CD/DVD drive first for a bootable disc (i.e. your LiveCD).

When you hit Del to enter setup are you seeing a screen that looks anything like the one in [this pic](http://www.peacefire.org/bypass/booting-from-cd-tutorial/bios_advance.JPG)?

---

### Post by Sef on 2008-09-19
> . really sorry for being so 'basic'.

No need to apologize for being basic.  We all were once where you are now.  


This is GRUB error 21:

> 21 : Selected disk does not existThis error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.       

---

### Post by unutbu on 2008-09-19
Try going into the BIOS menu and puting the CD-ROM in front of the Hard Drive in the boot order. It won't matter if the floppy drive is first as long as you have nothing in the floppy drive. Then with the LiveCD in the CD-ROM drive, try to boot.

---

### Post by cautious learner on 2008-09-19
many  thanks for everyone's help: first kansasnoob...yup tried it...no change, same error
therion: no, no screen like that, the most similar is start-up, start up sequence. from there my options are: diskette drive a; usb fec; usb key; usb ls120; ide hdd:hitachi hds721616pla380-opens; ide cd:hl-dt-stdvd-ram gsa-h60n-(; pci bev:mba v9.4.2.Slot 0300
i can change the order of these. now that i look at it, should i be moving the ide cd:hl-dt-stdvd to the top?

---

### Post by Locutus_of_Borg on 2008-09-19
> **cautious learner said:**
> many  thanks for everyone's help: first kansasnoob...yup tried it...no change, same error
therion: no, no screen like that, the most similar is start-up, start up sequence. from there my options are: diskette drive a; usb fec; usb key; usb ls120; ide hdd:hitachi hds721616pla380-opens; ide cd:hl-dt-stdvd-ram gsa-h60n-(; pci bev:mba v9.4.2.Slot 0300
i can change the order of these. now that i look at it, should i be moving the ide cd:hl-dt-stdvd to the top?

yes

---

### Post by cautious learner on 2008-09-19
well, it looked very promising there for a bit. got the cd going saw the ubuntu logo (yay). now i have [242.751434] buffer I/O error on device fdo, logic block 0.i have no idea....

---

### Post by cautious learner on 2008-09-19
new development. i now have the install sreen up...i know it's probably a silly question but if i install, will i end up with two versions of ubuntu on my system?

---

### Post by Locutus_of_Borg on 2008-09-19
looks like something to do with a floppy drive, do you have a floppy dive?

when you get this error, what happens? does it just freeze? drop to a shell?

can you choose a test mode instead of graphical mode at any point?

try going back into your BIOS and change the diskette boot order to the bottom

---

### Post by Locutus_of_Borg on 2008-09-19
> **cautious learner said:**
> new development. i now have the install sreen up...i know it's probably a silly question but if i install, will i end up with two versions of ubuntu on my system?

yes, unless one overwrite your current one

but all you need to do is repair grub

if you can reach a desktop or even just a shell, enter: grub-install --no-floppy /dev/sda

as long as your drive is sda and not hda

fdisk -l will tell you which it is (that is a lowercase L by the way)

---

### Post by kansasnoob on 2008-09-19
> **cautious learner said:**
> new development. i now have the install sreen up...i know it's probably a silly question but if i install, will i end up with two versions of ubuntu on my system?

Don't reinstall! Just choose to run Ubuntu without making any changes to system!

We might be able to repair your system from there!

---

### Post by kansasnoob on 2008-09-19
> **Locutus_of_Borg said:**
> yes, unless one overwrite your current one

but all you need to do is repair grub

if you can reach a desktop or even just a shell, enter: grub-install --no-floppy /dev/sda

as long as your drive is sda and not hda

fdisk -l will tell you which it is (that is a lowercase L by the way)

That reminds me ........... make sure you have no discs in a floppy drive, or any usb drives plugged in, or odd memory discs inserted (like from cameras)??????????

---

### Post by cautious learner on 2008-09-19
ug. system is now just hanging. suggestions? i'm a bit scared to re-boot

---

### Post by cautious learner on 2008-09-19
ok. i have a terminal. to be perfectly honest, i don't really know if i've re-installed or not. it certainly didn't go the same way it did the first time around. in order to avoid screwing things up even more, i'm just checking again what i should be doing now.

---

### Post by cautious learner on 2008-09-19
ok. just went ahead with grub-install--no-floppy/dev/sda
got:no such file or directory
thoughts?

---

### Post by cautious learner on 2008-09-19
tried fdisk-l
got:command not found
sigh....

---

### Post by Locutus_of_Borg on 2008-09-19
thats fdisk -l (lower case L and a space between the k and the -)
and 
grub-install --no-floppy /dev/sda (with a space after install and after floppy)

also make sure you are root ( sudo -i )

---

### Post by cautious learner on 2008-09-19
so fdisk -l no response
for grub-install --no-floppy /dev/sda i got: mkdir:cannot create directory'/boot/grub':permission denied
thanks for sticking with me :(

---

### Post by Locutus_of_Borg on 2008-09-19
okay you need to be root

input sudo su into the terminal
if nothing, try sudo -i
then try those commands again

---

### Post by cautious learner on 2008-09-19
thanks. fdisk -l indicates that it is sda 
grub install gave me:could not find device for /boot: Not found or not a block device

---

### Post by kansasnoob on 2008-09-19
Post the actual output of 

```
sudo fdisk -l
```

---

### Post by Locutus_of_Borg on 2008-09-19
okay try this

from the fdisk -l you should have gotten a listing of your partition tables

one of them should have said it was of type Linux, it would like like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            2480       14349    95345775    5  Extended
/dev/sda3               1        2479    19912536   83  Linux

```

take note of the one that says Linux, now enter the following:
```
mkdir /fix
mount /dev/sda# /fix
```
change # to the number corresponding to the line that has Linux on it from above

now enter this:
```
grub-install --no-floppy --root-directory=/fix /dev/sda
```

---

### Post by cautious learner on 2008-09-20
i can't see any linux. i get:

Device   Boot   Start   End  Blocks     ID    System
/dev/sda1 *       1    3540  28435018+  7    HPFS/NTFS
/dev/sda2       18919  19457  4329517+  12  Compaq diagnostics

---

### Post by Locutus_of_Borg on 2008-09-20
wait...



have you installed linux at all on this computer?

to fix your windows installation, insert your windows cd and boot into the recovery console (press R at first screen)

now enter fixmbr 



otherwise, install linux by clicking on the install icon

---

### Post by cautious learner on 2008-09-20
yes. up until a few hours ago (before the lights went out) i had a very happy dual boot system (XP and ubuntu). bought it at the university. part of the deal is that you don't actually get the XP disk (i won't say which school it is).

---

### Post by Locutus_of_Borg on 2008-09-20
well it seems to have gotten lost

your fdisk reports a large amount of hard drive space missing (blocks 3541-18918 are unformatted free-space)

looks like you may need to reinstall linux onto that space

i recommend Gentoo Linux

---

### Post by cautious learner on 2008-09-20
many thanks to all for your help. i'll have to think about this some more tomorrow. again, thanks for your patience!

---

### Post by egalvan on 2008-09-20
> **cautious learner said:**
> yes. up until a few hours ago (before the lights went out) i had a very happy dual boot system (XP and ubuntu). bought it at the university. part of the deal is that you don't actually get the XP disk (i won't say which school it is).

Sounds like you lost your Ubuntu partition...

If you can, download PartedMagic LiveCD

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

I have found it easier to use, it has the latest GParted (0.3.9)
and TestDisk, which can recover lost partitions.

It's also a complete Linux Distro, very small, and very fast.
45mb download size.

It will run from RAM in 256mb.

I use it regularly, and donated to the author.
It's worth it.

---

### Post by QenBirQeni on 2008-09-21
Check and see what your partition table is telling you. By you rpost you have no Linux on your system, and somehow it got deleted (maybe). 

For grub errors the best page to check is [GRUB Bootloader Tutorial]("http://www.dedoimedo.com/computers/grub.html#mozTocId976410")

---

