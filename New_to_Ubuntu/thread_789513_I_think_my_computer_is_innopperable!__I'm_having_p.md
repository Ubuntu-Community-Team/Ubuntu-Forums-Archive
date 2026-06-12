---
title: "I think my computer is innopperable!  I'm having problems with grub"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-10
Okay, this is very complicated, but I'll do my best to explain.  The first part of this long story I can shorten.  I installed ubuntu (Hardy heron) using the installation CD that I made by burning the downloaded installation files onto the disk.  I chose full installation, and I was able to dual boot with XP.  A while later I decided i didn't like ubuntu, so I erased the partitions using XP.  Now here's the problem.....when I booted up my computer, it showed the HP startup screen then went strait to grub.  Grub is thne not able to load (error 22), probably because it couldn't find ubuntu.  At this point, it won't let me do anything.  I could probably do stuff if I had the actual XP installation disk, but all I have is the PC manufacturers system recovery disks.  I tried that and all I got was a black screen. I have no other disks that could do anything...other than the ubuntu installation disk of course.  I wasn't able to do a thing, so I tried putting the ubuntu installation disk in.  Now, it started installing ubuntu again.  It's currently completing the new partition.  I'm hoping grub will work now and I can do something to get rid of it.  

Please keep in mind that I do not have the actual xp installation disk.  I also don't care if anything I had in xp is lost.  I juat want to use it again and I want its space back!

note: I realize that you are all going to hate me since I refused the free gift of ubuntu.  Well, I realize it is a great OS...probably the best...I just prefer XP for now.

Update: I think it worked.  Grub is back and I went to XP.  It's doing that check thing it did last time I installed ubuntu.  Now, If I want to get rid of everything correctly, I heard there was some "fixboot" thing I could do, but i think that's if you have the actual XP disk.  Is there any way to use either XP or ubuntu to kill grub?  If there is no way without the XP installation disk, I'm willing to keep ubuntu this time, since i'm using a much smaller portion of my hard drive.  What I would like to do is make it so XP will load on default instead of ubuntu.  Again, my preference would be to completely get rid of ubuntu, unless of course there are no disadvantages to having it (other than lose of some HDD space).  XP seemed to boot slower ever since I got ubuntu, but that could just be my imagination.

---

### Post by alzie on 2008-05-10
I think this link is what you are looking for.  [http://ubuntuforums.org/showthread.php?t=672328](http://ubuntuforums.org/showthread.php?t=672328)

I hope this helps you.

---

### Post by tjwoosta on 2008-05-10
with the pc manufatorors disc you should still be able to reformat completely and reinstall fresh

(at least with all the ones ive used you can)

but there is probably a way to restore the windows xp bootloader to the MBR without the xp install disk i just dont know how exactly

---

### Post by bobnutfield on 2008-05-10
Hello

Don't be too concerned, there is a fix for your problem.  I don't have the link directly available to right now but you can either search the forum or Google for a live CD called Super Grub or any other number of bootable Live Cd programs that will restore the Master Boot Record of your drive.  The command you are looking for is:

fixmbr

and it available on the Super Grub cd if you do not have the Windows installation disk.  This will erase the grub installation from your mbr and restore the windows boot as before.

Hope this helps

Bob

---

### Post by joshsmith on 2008-05-10
it is your imagination that xp boots slower, i promise. the only loss is hard drive space
there is no problem having grub


if you boot into ubuntu, and edit the file /boot/grub/menu.lst, using
```

sudo gedit /boot/grub/menu.lst

```
you can change the timeout of grub, and by moving
"# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
" somehting like this ^^ to above the other ubuntu options, ie just below the line "## ## End Default Options ##"
you will have set xp to be first in the list, and will therefore be the default boot

but, ubuntu is cool. try it more

---

### Post by N.N. on 2008-05-10
There is a detailed guide on uninstalling Ubuntu [here]("http://users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu"). To avoid any mishaps, however, you could simply do as joshsmith suggests (further elaborated [here]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")) and then [hide the GRUB menu during bootup]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu"). :)

---

### Post by annda on 2008-05-10
> **joshsmith said:**
> it is your imagination that xp boots slower, i promise. the only loss is hard drive space
there is no problem having grub


if you boot into ubuntu, and edit the file /boot/grub/menu.lst, using
```

sudo gedit /boot/grub/menu.lst

```
you can change the timeout of grub, and by moving
"# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
" somehting like this ^^ to above the other ubuntu options, ie just below the line "## ## End Default Options ##"
you will have set xp to be first in the list, and will therefore be the default boot

but, ubuntu is cool. try it more

don't just move this. it will be erased by ubuntu kernel updates. count from 0 to your windows entry in the list and at the beginning of the file change "default 0" to "default the_number"

---

### Post by N.N. on 2008-05-10
> **annda said:**
> don't just move this. it will be erased by ubuntu kernel updates. count from 0 to your windows entry in the list and at the beginning of the file change "default 0" to "default the_number"
If you paste the entry above the debian automagic kernels list, the entry shouldn't be erased by Ubuntu kernel updates (according to [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)).

---

### Post by joshsmith on 2008-05-10
@annda
isnt what you have described worse. 
if you are referencing a number, and new kernel options get listed at the top of the list, wont you be referencing something other than what you expect after an upgrade
(im pretty sure if you change the order, ubuntu upgrades dont fiddle with it, i have certainly done that before)

btw, what i said was all irrelevant to the original poster, so im sorry for hijacking your thread Rukaru

---

### Post by annda on 2008-05-10
> **N.N. said:**
> If you paste the entry above the debian automagic kernels list, the entry shouldn't be erased by Ubuntu kernel updates (according to [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)).

@N.N.: thanks for the info. i tried that years ago but probably pasted the entry too low in the file - hence the warning.

@Rukaru: sorry for the confusion.

UPDATE:
@joshsmith: you are right. this was just an insensitive projection of my own experience as a person with multiple (and changing) distros, shifting partitions etc., who always watches her Grub options closely because update-grub doesn't do the job.

---

### Post by Rukaru on 2008-05-10
> **joshsmith said:**
> it is your imagination that xp boots slower, i promise. the only loss is hard drive space
there is no problem having grub


if you boot into ubuntu, and edit the file /boot/grub/menu.lst, using
```

sudo gedit /boot/grub/menu.lst

```
you can change the timeout of grub, and by moving
"# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
" somehting like this ^^ to above the other ubuntu options, ie just below the line "## ## End Default Options ##"
you will have set xp to be first in the list, and will therefore be the default boot

but, ubuntu is cool. try it more

Sorry....no idea what you just.  I'm not good with using all that code stuff.  I'm a mouse guy....I don't use keys unless I'm writing something like a post or an email.  Maybe that's why i don't get along with ubuntu.  Now, is what you just told me a way to make XP boot by default instead of ubuntu?  That's fine...since the only thing having ubuntu is doing is taken 50GB of my 250GB HDD.  I just don't want to have to select XP each time I boot up, though that isn't a huge deal.  In the event that removing ubuntu would be difficult, I plan to just keep ubuntu sitting there until I have time to learn it.  So, I will eventually give it a chance.  

Oh....did I say that it worked?  I just put the ubuntu disk in and it apparently fixed grub so I can get into XP again. I also still have everything in XP.  So, it's all good.

---

### Post by kansasnoob on 2008-05-10
First of all, no one here will hate anyone for choosing one OS over another!

If they expressed hatred I'm sure they'd be gone yesterday, but to the point:

During my early ventures into Linux/Ubuntu, specifically Freespire and gOS, I encountered a problem with getting my HP recovery discs (a three disc set) to restore my puter.

What I had to do was boot the gOS disc into Live CD mode --- you can do this with nearly any Ubuntu derivative --- and find Gparted. If you have a recent Ubuntu Live CD you'll find "Partition Editor" under the Administration menu and then you'll be able to delete any and all partitions until you have one large blank partition left, then be sure to click save (somewhat upper left hand corner of the window as I recall), then just restart and when prompted eject the Live Cd and throw in disc #1 of your Windows recovery set.

Unless you've changed any hardware things should go off without a hitch!

If this doesn't work shout again!

Ubuntu is not for everyone! It's all about choices!

---

### Post by joshsmith on 2008-05-10
ok run
sudo gedit /boot/grub/menu.lst
in terminal

then scroll to the section that look something like:

```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

and change to something like
```

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=3711eba1-05bf-4f02-aebe-5d7d01746850 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



```

ie move the xp bit to the top

---

### Post by annda on 2008-05-10
> **kansasnoob said:**
> First of all, no one here will hate anyone for choosing one OS over another!

If they expressed hatred I'm sure they'd be gone yesterday, but to the point:

During my early ventures into Linux/Ubuntu, specifically Freespire and gOS, I encountered a problem with getting my HP recovery discs (a three disc set) to restore my puter.

What I had to do was boot the gOS disc into Live CD mode --- you can do this with nearly any Ubuntu derivative --- and find Gparted. If you have a recent Ubuntu Live CD you'll find "Partition Editor" under the Administration menu and then you'll be able to delete any and all partitions until you have one large blank partition left, then be sure to click save (somewhat upper left hand corner of the window as I recall), then just restart and when prompted eject the Live Cd and throw in disc #1 of your Windows recovery set.

Unless you've changed any hardware things should go off without a hitch!

If this doesn't work shout again!

Ubuntu is not for everyone! It's all about choices!

although i've had no problem with restoring windows with the recovery CDs before selling my old acer laptop, kansasnoob's solution makes a lot of sense. the partitioning may be confusing the recovery cd, so try that.

---

### Post by kansasnoob on 2008-05-10
Oops, overlapped!

then the phone.............

---

