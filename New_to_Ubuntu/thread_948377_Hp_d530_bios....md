---
title: "Hp d530 bios..."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Jancarel on 2008-10-15
Dear Ubuntu Friends,

Is there anyone out there with Ubuntu installed on a HP Compaq D530 Desktop computer. If so, could you tell me your BIOS settings of the SATA controler. I am still trying to install Ubuntu on this D530. The installation locks up and it seems that the program does not find the harddisk. The D530 has two IDE controllers. One can be set as SATA or PATA controller. I tried both settings, no success...

Your help is appreciated,

Jan

---

### Post by spiderbatdad on 2008-10-15
please try to configure your sata as ide: load the live cd, select F6 from the startup screen, press esc (if you need to, to clear a dialog box offering option,) delete quiet splash-- from the end of the kernel boot line, replace quiet splash-- with all_generic_ide
This should work...you will, after installation, need to edit the kernel line in the file /boot/grub/menu.lst to include all_generic_ide.

---

### Post by low-res on 2008-10-15
Hi Jan,

It's just a guess but there are probably some other SATA settings in your BIOS like "AHCI". Try enabling and disabling those and check out if that does the trick.

---

### Post by dh@foss on 2011-10-25
Hi,

I am having the same problem and ended up with no sucess after googling for around 2 days.any clue would be quite appreciated!:(

---

### Post by DCheck2 on 2013-03-06
While I realize this post is rather old, I have successfully loaded both an SATA hdd and Ubuntu 12.04 to a HP Compaq d530 sff. I have had very little difficulties thus far, but should anyone encounter any in the future, thought i'd lend my experience as future help. First off have the most _up to date bios BEFORE the install_, checking for this is as simple as going to the manufacturers site and comparing numbers (smart phones make this part nice and easy :P ). If you are replacing the IDE hdd with the SATA you want to set the SATA controller to replace the IDE controller, and change controller boot order to SATA first. 

Oh btw I recommend using a liveusb I used multisystem liveusb tool to set mine up in which you can add the ubuntu iso as a livecd, and also add ultimate boot cd and grub4dos both tools in addition to bitdefender should be used prior to install. My 250gb WD SATA HDD was recycled from a dead laptop and first test ran said to RMA it, used the tools to repair, and all errors were fixed. And there are plenty more useful tools you can get but thats another topic (however the latest version of MultiSystem does not download the packages for you and this can become quite mind numbing).

> [SIZE=5]***"The D530 has two IDE controllers. One can be set as SATA or PATA controller."***[/SIZE]

_[SIZE=4]IF[/SIZE]_ This option exists you need to update bios, you don't want to set IDE controller as SATA but rather replace the IDE with the SATA.

All in all I have liked the install so far, and should any issues arise I always try to solve them myself or figure it out with tips. Feel free to mail me if u need help with similar setups, I am no pro but have several resources that have yet to fail me when used properly.

This Thread *COULD* be set as solved, however there could be multiple setups older than my experience, but I have tried my best to be as descriptive as possible so to make sure others will see this when they need it.

---

### Post by overdrank on 2013-03-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

