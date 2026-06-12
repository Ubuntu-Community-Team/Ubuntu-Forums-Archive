---
title: "Screen Resolution Stuck at 1024x768"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by johnny907 on 2013-05-27
**&#8203;**Just installed 12.04 and my screen resolution is stuck at 1024x768 even though the screen can go higher.  In 'Displays' there are no other options even given and I also cannot adjust my screen brightness (which is set to max automatically) and compiz effects don't work either.  All of aforementioned things worked flawlessly when I was using 10.10. 

Specs: 
[COLOR=#000000]Acer Aspire 5336-2524[/COLOR]



[LIST]
[*=left][COLOR=#768696]Processor[/COLOR][COLOR=#39434D]Intel Celeron 900 / 2.2 GHz[/COLOR]
[*=left][COLOR=#768696]Memory[/COLOR][COLOR=#39434D]3.0 GB / 4.0 GB (max)[/COLOR]
[*=left][COLOR=#768696]Hard Drive[/COLOR][COLOR=#39434D]250.0 GB - Serial ATA-150 - 5400.0 rpm[/COLOR]
[*=left][COLOR=#768696]Operating System[/COLOR][COLOR=#39434D]Microsoft Windows 7 Home Premium 64-bit Edition[/COLOR]
[*=left][COLOR=#768696]Display Type[/COLOR][COLOR=#39434D]15.6 in TFT active matrix[/COLOR]
[*=left][COLOR=#768696]Max Resolution[/COLOR][COLOR=#39434D]1366 x 768 ( HD )[/COLOR]
[*=left][COLOR=#768696]Graphics Processor[/COLOR][COLOR=#39434D]Intel GMA 4500M Dynamic Video Memory Technology 5.0[/COLOR]
[*=left][COLOR=#768696]Optical Drive[/COLOR][COLOR=#39434D]DVD±RW (±R DL) / DVD-RAM - Integrated[/COLOR]
[/LIST]

---

### Post by sudodus on 2013-05-27
It may work better with some boot option about video or framebuffer. See these links

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt)

[https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)

---

### Post by johnny907 on 2013-05-27
I'm almost positive it's the intel GMA4500M graphics card.  Everything worked perfectly in 10.10, but since installing both 12.04 and 13.04, I have had nothing but problems. Nomodest issues, screen resolution issues, compiz effects won't work, screen brightness doesn't work,   I've been banging my head against the wall for 3 days since leaving 10.10 because it's no longer supported.  I've tried to update proprietary drivers but none are available.  I dont know what else to do if I cant find any drivers.

---

### Post by johnny907 on 2013-05-27
I think, unfortunatly, I have found an anwer to my problem in [http://ubuntuforums.org/showthread.php?t=2005471](http://ubuntuforums.org/showthread.php?t=2005471).  It seems as though my intel gma4500M does not support Unity 3d.  It seems that this is where Ubuntu and I part ways.  I have loved using their OS, but If I can't adjust anything (graphically wise), I must move on.  They should have never ditched gnome, now I have ditched them; that is unless there are some miracle drivers out ther that I don't know about.

---

### Post by deadflowr on 2013-05-27
> **johnny907 said:**
> I think, unfortunatly, I have found an anwer to my problem in [http://ubuntuforums.org/showthread.php?t=2005471](http://ubuntuforums.org/showthread.php?t=2005471).  It seems as though my intel gma4500M does not support Unity 3d.  It seems that this is where Ubuntu and I part ways.  I have loved using their OS, but If I can't adjust anything (graphically wise), I must move on.  They should have never ditched gnome, now I have ditched them; that is unless there are some miracle drivers out ther that I don't know about.

Have you look at alternative flavors like [kubuntu]("http://www.kubuntu.org/"), [xubuntu]("http://xubuntu.org/"), [lubuntu]("http://lubuntu.net/"), or [ubuntu gnome]("https://wiki.ubuntu.com/UbuntuGNOME")?

---

### Post by MrSteve on 2013-05-28
open up the software center and search for intel gma

on the list is the xorg gma 3600 intel driver
which should work with your gma 4500 ...

also found this its the intel installer for ubuntu gma driver with support for the gma 4000 series
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

just updated the intel gma 3150 driver on my 12.04LTS system via the above link
it worked perfectly and for the first time in system settings > details > graphics i have listed driver details for my GPU ...

---

### Post by johnny907 on 2013-05-30
I was using 13.04 but it was running way too slow for some reason so I replaced it with 12.04.  The slow running problem was fixed, but all the problems still persisted.  I downloaded all alternative drivers and whatever opensource intel drivers i could, still to no avail.  I'm giving up and going to something running Mate or some version of gnome 2 because Unity and Gnome 3 sure don't agree with my hardware. Thanks for all the help though, it is much appreciated.

---

### Post by johnny907 on 2013-05-30
After searching long and hard I have finally found a solution here [http://ubuntuforums.org/showthread.php?t=1840959&page=2](http://ubuntuforums.org/showthread.php?t=1840959&page=2).  It's a simple grub edit:

1. Open Terminal and type:



gksudo gedit /etc/default/grub
[COLOR=#000000]

2. a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:[/COLOR]
[COLOR=#000000]

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian
[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/B]GRUB_CMDLINE_LINUX=""[/COLOR]
[COLOR=#000000]

3. add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line by adding* "*[/COLOR]*[COLOR=#000000]acpi_osi=" [/COLOR]*[COLOR=#000000]:[/COLOR][COLOR=#000000]


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=trueGRUB_TIMEOUT=10GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [FONT=Verdana]acpi_osi=[/FONT]"**
GRUB_CMDLINE_LINUX=""
[/COLOR]
[COLOR=#000000]
4. Save the file and exit gedit

[/COLOR][COLOR=#000000]Now in the terminal, run the following command to update your grub configuration with the new default settings:
[/COLOR][COLOR=#000000]

*sudo update-grub*
[/COLOR]

That should fix the screen resolution problem and make unity 3d fully functional.

---

