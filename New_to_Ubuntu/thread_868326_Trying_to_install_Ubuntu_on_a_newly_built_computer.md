---
title: "Trying to install Ubuntu on a newly built computer, getting error"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-07-23
I received my parts today from Newegg and now have the hardware end set up.  I am trying to install Ubuntu, and after choosing either 'install ubuntu' or 'try ubuntu without any changes to your computer', first the Ubuntu bar happens with the orange bar that goes back and forth.  After that, the screen goes black.  In a few seconds, a line like this appears at the top:
```

[184.486406] Buffer I/O error on device fd0, logical block 0

```

There is a flashing underscore on the line below that.  About 15-20 seconds later, another line appears, same message with a higher number in the brackets.  15-20 seconds later, a third line appears under those two, with a larger number within the brackets.  This continues indefinitely.

The message is kind of self-explanatory, but is not very helpful as far as what to do to fix the problem.  The same thing happens for attempts at both 32-bit installation and 64-bit installation.  It is not the Ubuntu cd, because I know that my 32-bit one works.

The computer has an Intel Q9450 processor, Asus P5Q motherboard, 2 Seagate HDs (640 and 250 gig), 2 disk drives, and so on.  I have tried using both disk drives, and have set both hard drives as primary and retried.  Same problem.



I can't make any sense of it since everything is detected in the BIOS.

Any help would be GREATLY appreciated; I just want to get things working on my first desktop build.

---

### Post by halitech on 2008-07-23
check here:

[http://ubuntuforums.org/showthread.php?t=461599](http://ubuntuforums.org/showthread.php?t=461599)

it seems to be a bug with not having a floppy installed but the BIOS thinking you have one.

---

### Post by Separ on 2008-07-23
Check the BIOS and put floppy boot down the list a bit as "fd0" is referring to a floppy drive I think.

EDIT: Check above post

---

### Post by halitech on 2008-07-23
slightly faster fingers and searching ;)

---

### Post by ConMan318 on 2008-07-23
Alright!  Now we're getting somewhere; thank you very much.

BUT

Now, after the orange bar that goes back and forth, I end up in a command line.  it says:
```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

```

Entering help just gives a list of commands like ls, cd, mount, etc.

This is from selecting either 'install' or 'try ubuntu'.  Maybe it's a 64-bit thing?

Any ideas?

---

### Post by halitech on 2008-07-23
what did you get for a video card for this machine and which install were you trying? (32bit or 64?)

---

### Post by ConMan318 on 2008-07-23
The vid card is a GeForce 9800.  Do I have to install a driver for it somehow?  I just tried putting in the driver disk, but it can't be booted from.  So how can I install a driver needed to install the OS without the OS?

And I am trying to install 64-bit.

---

### Post by halitech on 2008-07-23
when you are booting, there should be a safe mode option, try selecting that and see if you can get it to boot. We can install the drivers later if need be.

---

### Post by ConMan318 on 2008-07-23
Alright, at the menu I hit F4 (modes) and chose 'safe graphics mode'.  Selecting 'try ubuntu' and 'install' still both go to that command line, though.

Thank you for your help with this, Halitech.  I'll be extremely happy to get this up and running.

---

### Post by halitech on 2008-07-23
going to go out on a limb here, how do you have your drives hooked up? Is your cd/dvd on a cable by itself or is it hooked up with another drive on the same cable?

---

### Post by ConMan318 on 2008-07-23
The sata ports plugged into the motherboard are seperate, but the power to the 2 disk drives is from one cable.

---

### Post by halitech on 2008-07-23
power cords shouldn't make a difference (unless its really underpowered). So you just have 1 hard drive and 1 cd rom connected right now?

---

### Post by ConMan318 on 2008-07-23
Well no, I have 2 of each.  I thought you were just talking about CD/DVD drives.

---

### Post by halitech on 2008-07-23
ok, try getting rid of 1 of each so you just have 1 hard drive and 1 cd rom (or dvd, whichever the case is)

---

### Post by ConMan318 on 2008-07-23
K, I unplugged one of each from the mobo; it still only boots to the command line though, even in safe graphics mode.  The motherboard doesn't have onboard video, so it seems like I would need to get a driver installed somehow before installing the OS.  I've tried using the 'use driver update cd' mode, but it says 'insert a driver cd and press enter(amd64)'.  When I put in the graphics card driver cd and press enter nothing happens.

---

### Post by halitech on 2008-07-23
I don't know, I can't see needing to load a video driver before loading the OS as the base drive should work. I don't know anything about SATA drives so the problem might be there and we are barking up the wrong tree looking at the video cards. I'm going to bow out for now and hopefully someone else will come along with an idea.

I'll be abck if I think of anything else though

---

### Post by ConMan318 on 2008-07-23
Alright, thanks for your help.

---

### Post by fidamehran on 2008-07-23
What I thnk is that you downloaded an Alternate CD which installs Ubuntu through command line. This version is made for people with a bit older PCs that don't have enough specs and RAM to run the Live CD. I think you could try downloading the actual Live CD ISO once again.

---

### Post by Neo0351 on 2008-07-24
try this, when u boot the cd and it askes u what to do, press F6 and add this after quiet splash
```
all_generic_ide floppy=off irqpoll
```
should look something like this
```
quiet splash all_generic_ide floppy=off irqpoll
```
also u should be able to use the live cd, but u will have to install the drivers for you video card from nvidia.  its not hard, so if u get install i can help you with that.

---

### Post by ConMan318 on 2008-07-24
Thank you!!!  I've been messing with this for hours and haven't gotten anything but the command line; your boot options got me into Ubuntu!  I am installing now, once again, thank you very much.

---

### Post by Neo0351 on 2008-07-24
you're welcome, a lot of people that have sata drives have been having problems 8.04.  to install you're nvidia drivers for your video card, download the driver
[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.05/NVIDIA-Linux-x86_64-173.14.05-pkg2.run")
then do this
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by ConMan318 on 2008-07-24
Hah well another problem cropped up.  After installing (which appeared to be successful), I tried to boot into Ubuntu and it stayed at the loading screen for a pretty long time.  Then it went into that command line again.  Do I have to edit something else to boot into Ubuntu?

Recovery mode also ends up in that command line.

EDIT: Recovery mode gives this message:
```

ALERT! /dev/disl/by-uuid/bb9f9be4-c863-4bdc-9bcc-a8cf06b3198 does not exist.  Dropping to a shell!

```

followed by that command line prompt.

---

### Post by Neo0351 on 2008-07-24
oh man, i totally forgot to tell you to you have to add those boot options in order to boot.  so when you boot, it should say grub 1.5 loading, then start counting down.  hit Esc and select the kernel you want to boot.  then hit "e".  arrow down one to the kernel line and hit "e" again and add ```
all_generic_ide floppy=off irqpoll
```
to the end of the line.  once booted enter in the terminal 
```
sudo gedit /boot/grub/menu.list
```
find the line that looks like this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
edit it to look like this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash all_generic_ide floppy=off irqpoll
```
save your changes and exit, then run
```
sudo update-grub
```

---

### Post by ConMan318 on 2008-07-24
Alright, I can now get into Ubuntu!  Can't connect to the internet, but that's a problem for another thread/day.  Thanks again Neo!

---

### Post by Neo0351 on 2008-07-24
no problem, remember to start a new thread for you network problems

---

### Post by lzyeddie on 2008-07-24
Ok...so I have nearly the same problem as the ConMan.  Completely new build, can't get an Ubuntu 7.1 CD that I've used several times before to install.
First. Specs.

Motherboard: nVidia 680i SLI
CPU: Intel Core 2 Duo
HDD: 2x Hitachi SATA on separate lines
DVD-RW: 2x Lite-On on same line
Video Card: nVidia e-GeForce 8800 GTS
Monitor: Acer AL2016W 20" (1680x1050 res)

Ubuntu autorun leads to install screen.  Selecting install/run and other options with the above command line all have same outcome.  After the bar fills, it prompts to configure monitor and video card or run in safe graphics mode.  If I configure, my monitor is not listed and is recognized as generic plug n play.  If I test a generic LCD as a widescreen with near correct resolution, the test works and continues the config.  When I test the video card with the nVidia driver, it exits the config tool and proceeds to try to start Ubuntu, stalling at the boot scripts step.  Reversing the config order does not change either outcome.  Choosing safe graphics mode at the install screen merely skips the config tool and goes straight to stalling at the boot scripts step.

There seems to be no rhyme or reason at this point, sometimes it completely freezes with the only indication being that NumLock and CapsLock on the keyboard flash, forcing me to cut power at the power supply.  Sometimes it responds to keystrokes, displaying text but not responding to any command except Ctrl+Alt+Del, at which point it unmounts temporary filesystems, deactivates swap, unmounts local filesystems and displays

unmount2:  Device or resource busy  [ok]
unmount:  /cdrom busy - remounted read-only [ok]
Segmentation fault
                                              [fail]
* casper is resynching snapshots and caching reboot files...


Then I'm prompted to remove my disk and hit enter for a reboot.

After that prompt it gives further error messages.

usplash:  Setting mode 640x480 failed
screen init failed

I don't know what to do.  The only other operating system I have at my disposal is Server 2003, which I've successfully installed and thus installed all drivers on my computer before trying to install Ubuntu, except the video card and monitors because their drivers are only compatible with 64-bit OS's.  I tried hunting down compatible drivers with no success.  

Please help.  I'm willing to try anything at this point.

---

### Post by Neo0351 on 2008-07-24
did you try this?

> **Neo0351 said:**
> try this, when u boot the cd and it askes u what to do, press F6 and add this after quiet splash
```
all_generic_ide floppy=off irqpoll
```
should look something like this
```
quiet splash all_generic_ide floppy=off irqpoll
```
also u should be able to use the live cd, but u will have to install the drivers for you video card from nvidia.  its not hard, so if u get install i can help you with that.

also when it asks, choose graphics safe mode.  im not sure, but you may need to use the alternate install cd becuase you are using an 8800 graphics card.  once installed, you will need to install envy and use envy to install the correct drivers for you're video card.

---

### Post by lzyeddie on 2008-07-24
Script did not work.  Did not work with Hardy either.  I'm downloading and burning alternate CD now.  Thanks for suggestions.

---

### Post by mgmiller on 2008-07-24
Using the floppy=off line in the kernel is a work around for your hardware misconfiguration.  Go into your BIOS and find the floppy drive entry and disable it.  Your BIOS is telling the OS there is a floppy drive which doesn't exist.

All this is assuming you do not have a floppy drive, of course.

---

### Post by lzyeddie on 2008-07-24
I had already set BIOS floppy to off.  The script was redundant.  I'm running alternate install for 8.04 now.  Partition made successfully.  45% of install completed before freeze.  No kernel panic.  It choked on gzip.

---

### Post by lzyeddie on 2008-07-24
tried alternate cd to setup command line system again.  Fail at 42% setting up sed.  finally got hold of proper os for all drivers.  will install in separate partition.

---

### Post by mgmiller on 2008-07-25
You have 2 dvd-rw drives sharing the same cable.  Make sure the jumpers on one are set to master and the other set to slave, rather than cable select, which is how they are usually shipped.

---

