---
title: "Graphics Card Question"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by gripstock on 2008-11-04
I installed Ubuntu Hardy Heron on an extra computer I have.
The install went just fine.
I have decided I would like to install an AGP Asus ATI 9600se 256MB card I have. It currently has a AGP Nvida 64MB card in it.
I have installed it once and it comes up to a boot screen for a second then goes black.
How do I get the operating system to recognize the card and install new drivers?

---

### Post by Gannon8 on 2008-11-04
The automated install should update the configuration file that makes the graphics system use the driver, so it looks like your driver has a problem...

I can recover from a nVidia card, but I am not sure how to recover from an ATI card...

Try booting from the liveCD, mount your linux partition, and display the contents of your /etc/X11/xorg.conf

---

### Post by roger_1960 on 2008-11-04
Hi

You could try booting into recovery mode (ESC when it gets to GRUB stage...) and then go to the Xfix option.  That should install a basic ATI driver giving you a GUI on normal reboot.  Then you could install and use envyng-gtk from synaptic to get a better ATI driver. I am assuming you have removed the Nvidia card. (But post your xorg.conf file anyway)

---

### Post by gripstock on 2008-11-04
Thanks for the reply.
I don't think I made it clear enough.
After I installed the ASUS card and it would not boot to a desktop I removed the ASUS card and put the Nvida back in.
It is booting just fine now.
I just need to know how to update or replace a previously installed graphics card.

Thanks!

---

### Post by gripstock on 2008-11-04
> **roger_1960 said:**
> Hi

You could try booting into recovery mode (ESC when it gets to GRUB stage...) and then go to the Xfix option.  That should install a basic ATI driver giving you a GUI on normal reboot.  Then you could install and use envyng-gtk from synaptic to get a better ATI driver. I am assuming you have removed the Nvidia card. (But post your xorg.conf file anyway)
Ok.... I need a few minutes to change the card back out.
I know how to get into the GRUB stage I think.
I am not too sure about Xfix option but I'll make a try at it.

---

### Post by gripstock on 2008-11-04
Do you enter xfix at the command line to get there?
I did but it returns Unrecognized command.

---

### Post by gripstock on 2008-11-04
This is my third time to spend about two or three hours each time reading posts, swapping graphics cards, rebooting and still get nothing but a blank screen.
I can hear the start up sound... type in my user name to a blank screen... type in my password but the screen is still blank  and at a desktop.
I have run the xfix option with no results.
I guess I will live with the current Nvida graphics card that works.
There are just too many commands to type in this OS for the average user and too many people with problems in this forum. Responses are brief and the people trying to help assume the newbies understand all their Linux Lingo answers.

---

