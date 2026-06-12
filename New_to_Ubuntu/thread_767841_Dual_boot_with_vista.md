---
title: "Dual boot with vista"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Nitrox17 on 2008-04-25
I already had vista installed and just now installed hardy heron.
When I turn on my machine it goes straight to ubuntu, how do I get grub or something to show up on powerup so I can select which OS to run

Thanks a bunch! :)

---

### Post by overdrank on 2008-04-25
> **Nitrox17 said:**
> I already had vista installed and just now installed hardy heron.
When I turn on my machine it goes straight to ubuntu, how do I get grub or something to show up on powerup so I can select which OS to run

Thanks a bunch! :)

Hi and first off is the vista partition intact. Use this command 
```
sudo fdisk -l
``` to verify the vista parition. Then you may reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by zaussome on 2008-04-26
z

---

### Post by Nitrox17 on 2008-05-03
The vista partition is in tact and all seems fine...
I re-installed grub but when rebooting it still goes straight into Ubuntu instead of giving me a boot option

Any other ideas?

---

### Post by smile-its-smiley on 2008-05-03
hit esc when turning on the computer i think you have 8 secs to do this then a screen turns up using the arrow keys navigate down to other operating systems and vista should be there. when you get to vista go start>mycomputer>system properties>advance system properties>advance> start up and recovery settings and tick time to display list of operating systems

---

### Post by mrzaius on 2008-05-03
A real answer:

In your /boot/grub/menu.lst file it specifies a timeout in seconds in which you should be able to perform a boot-time OS selection. Windows will be at the bottom of the list. If the below entry is commented out or set to low, just change it and rerun the grub install.

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

---

### Post by Joeb454 on 2008-05-03
> **mrzaius said:**
> A real answer

The above answers were real answers. We're only trying to help. For example to me - it sounds like grub didn't find Windows, so overdrank's suggestion of doing ```
sudo fdisk -l
``` was good, because it allows us to find the Vista partition and recommend the editing of the menu.lst

---

### Post by kirios on 2008-05-03
Post the contents of /boot/grub/menu.lst

---

### Post by reos2day on 2008-05-03
I have a dual vista/Ubuntu system.  To select which OS I want to use I have done a simple edit of the grub menu.  First I opened up Terminal and run the following command.

gksudo gedit /boot/grub/menu.lst

This opens the grub menu so I can edit it.  What follows is the first part of my grub menu.

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

For me the simplest thing to do is comment out the "timeout", which is done by putting "#" in front os it so it looks like this -

# timeout	10

I saved the file with this change hen rebooted.  Now grub patiently waits till I highlight the OS I want to start.  I hope this was useful.

---

