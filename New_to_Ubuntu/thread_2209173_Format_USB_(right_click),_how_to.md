---
title: "Format USB (right click), how to"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by carter-rowe on 2014-03-04
In my "standard" Ubuntu (13.10) desktop, when I see a USB disc in "files", 
I can right click on it, and have the option to format it appear. 
In other distros based on Ubuntu e.g. Lubuntu, Xubuntu, Kubuntu, Elementary etc I do not get this option.

When I check in 13.10 on "files" in "about" it just says "file 3.8.2" and this is what seems to be the default file handler.

Because I am trying to install on a low powered lap-top (i.e. less than 1gig memory) and this is for an "average" user,
I want to use a resource light distro that has the "right click to format" option enabled.

Obviously I/they could use gparted, 
or "disks" (which says it in "about" is "gnome-disk-utility 3.8.2 UDisks 2.1.0 (built against 2.1.0)")

However they are both complicated and present you with a VERY easy way to format the wrong disc...

One option would be to install Nautilus (which is what I thought was running in Ubuntu) in the distro,
I tried that in Elementary and it seemed to lose the ablility to right click and format, plus I couldn't see it directly in the "apps".

Is the right click thing something I should just be able to somehow enable in non "standard" Ubuntu?
If so which distro, and how?

Thanks very much for your help, sorry if this has been covered elsewhere....

---

### Post by phidia on 2014-03-04
I haven't used this myself but perhaps [this]("http://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/") helps?

---

### Post by carter-rowe on 2014-03-05
Thanks very much for your response.

I had a look at the "add  things to right click" utility, I looks way too advanced for me, I don't  think I could set up any actions that would reliably format the correct  disk without the danger of trashing the system.

Subsequently I  have been installing different desktop environments on my normal  desktop, to try and find something that requires less resources than  "Unity" which is reputed to be very greedy.

In the midst of doing  that the standard "files" (which is part of Nautilus I think) upgraded itself  from 3.8.2 to 3.10.1 and as a consequence suddenly lost the ability to  right click and format a usb drive

This appears to have been as a  result of adding in the PPA  [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) which in turn was  because I was trying to use things from the Gnome desktop.

The  problem I have now is that if I un-install Nautilus (which is probably a  dodgy thing to be doing anyway) remove that PPA and then try and install  Nautilus ( using sudo apt-get install nautilus )
all I get is an  error about unmet or impossible dependencies (the nautilus data is now a  later version than the nautilus I'm trying to install or some such )

Consequently  I've put back the ppa & re-installed Nautilus and of course ended  up back at the later version without the right click facility

So one question is, How do I get back the previous version or even just the right click ability?

I have also tried installing things like "Nemo" another file manager, but that doesn't seem to know about formatting usb's either...

I'm doing well, I've gone from how do I find/install a low powered Linux distro on an old laptop, that can right click & format USB's to "oops how do I fix my proper desktop", without even blinking...

Thanks for anybodies input

---

