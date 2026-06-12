---
title: "Foresight Linux 0.9.8"
date: 2006-09-25
forum: Other OS Talk
---

### Post by Rumor on 2006-09-25
This evening I downloaded and burned the dvd iso file for the latest release of Foresight Linux [http://www.foresightlinux.com/](http://www.foresightlinux.com/)
One note beforee proceeding, I have not been able to get to the Foresight Forum page, it keeps timing out.

I was curious about it since it is one of a very few distros that is currently packing gnome 2.16 as seen (or maybe not) in the screenshot I took below:

[http://img.photobucket.com/albums/v304/WhirledPeas/Screenshot.png](http://img.photobucket.com/albums/v304/WhirledPeas/Screenshot.png)

Booting to the dvd gave me two options, one for text-based installation and one for graphical installation. I chose the graphical installer and it launched the Anaconda installer. It correctly identified my video card, asked me to set the root password and came to the disc partitionging after a few basic screens. I chose to use the Disc Druid app to put Foresight in my "distro testing" partition. All it required was that I set the / mount point.

At the boot loader screen, I chose the advanced options, putting grub in the boot partition rather than the mbr so as not to mass up my current Ubuntu / Arch / Whatever-I-am-testing configuration on my computer.

It went from there to formatting and installing packages. Once that was done it said it was running some post install scripts.

Once that was done, it ejected the dvd and rebooted. I added Foresight to my current grub and booted in to the next stage of the install which consisted of creating a normal user and configuring the display. I was able to choose my monitor and set my resolution and color depth. I clicked finish and came to the login manager.

I had to manually configure my network after I got to the desktop. Once I did that, I fired up the rPath appliance agent and checked for system updates. There were none.

Epiphany and Firefox are both installed, as is openoffice.org and evolution. For multimedia, I have banshee, cowbell music organizer (which I've never heard of) and three other little apps.

The only hitch I have hit at this point is installing my printer. I have a HP deskJet printer that is hooked to lpt1. There was no option for lpt1 in the cups page. Lots of USB options, or serial options, even a scsi option, but no lpt1. I thought it odd.

I am posting this from Foresight. I'll have to play with it some more to learn about how it handles mp3 and dvd out of the box.

---

