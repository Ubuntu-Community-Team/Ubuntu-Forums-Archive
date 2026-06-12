---
title: "Super newbie here, in need of some help/tips"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Bkc1014 on 2011-10-14
Hi all! I'm extremely new to the whole of Ubuntu so don't laugh at me too much :)

I've just installed Ubuntu 11.10 alongside Windows 7 and the first thing I notice when I boot Ubuntu is that I'm having trouble connecting to the internet. (I can connect on Windows but not on Ubuntu)

I tried to manually enter my wireless network information and connect but after several minutes of the wifi icon blinking, a dialog box pops up telling me to enter the network password again.

Is this a driver related issue? Or am I simply overlooking something? :confused:

BTW: I'm using a Zonet ZEW1642S pci card

---

### Post by Kobin on 2011-10-14
Did you try opening the "Additional Drivers" to see if a driver is offered there?

If you already did that, then post the output here from:
```
lspci | grep Network
```

Are you typing your SSID manually or choosing it from a list in networkmanager?
Can you see the network you want to connect to in networkmanager?

---

### Post by Bkc1014 on 2011-10-14
I tried opening Additional Drivers, but since I can't connect to the internet, I have no way to check for drivers. I would use an ethernet cable, but my computer is very far from my router :/

brandon@Brandon-A870U3:~$ lspci | grep Network
02:05.0 Network controller: Ralink corp. Device 3062

I manually entered my SSID because no wireless networks were listed.

---

### Post by dFlyer on 2011-10-14
can you connect to the internet using a live cd via wifi? If not you will have to either be hardwired to the internet or download the correct driver and install in manually.

---

### Post by Bkc1014 on 2011-10-14
I downloaded and burned the available .iso file from ubuntu's main site and booted from it before installing. While using it from the disk, I couldnt access the Internet either.

How do I find my driver for ubuntu? The only one available on zonet's site is an exe. Also once I did the ubuntu/Linux driver, how would I go about manually installing it?

---

### Post by d4m1r on 2011-10-14
> **Bkc1014 said:**
> I downloaded and burned the available .iso file from ubuntu's main site and booted from it before installing. While using it from the disk, I couldnt access the Internet either.

How do I find my driver for ubuntu? The only one available on zonet's site is an exe. Also once I did the ubuntu/Linux driver, how would I go about manually installing it?


There might not be a linux version of your network driver...as for installing one if there was one (or if a universal one would work), normally you could run the .bin (linux .exe) by doing ./<name>.bin in terminal (ctrl+alt+t).

---

### Post by Toafan on 2011-10-14
Ignore d4m1r. Move your computer to someplace where you can connect it to physical Ethernet (wire).
It should auto-connect to that, and you'll have Internet access. Then open/run Additional Drivers. If there is a driver for your hardware, it should find it automatically. Then you just have to tell it to use that, and enter you password to tell it that it's O.K. to make those changes.

Sorry if I seem overly blunt or insulting. That's not my intent.

Wasn't that easy once you did it, though?

---

### Post by Bkc1014 on 2011-10-15
> **Toafan said:**
> Ignore d4m1r. Move your computer to someplace where you can connect it to physical Ethernet (wire).
It should auto-connect to that, and you'll have Internet access. Then open/run Additional Drivers. If there is a driver for your hardware, it should find it automatically. Then you just have to tell it to use that, and enter you password to tell it that it's O.K. to make those changes.

Sorry if I seem overly blunt or insulting. That's not my intent.

Wasn't that easy once you did it, though?

That's alright, I don't think you're being blunt or anything. I guess that'd be the easier way. I just hope that Additional Drivers has my wireless driver. Would there be a way to find out exactly if Additional Drivers has the one I need available without connecting to the internet on Ubuntu? I just don't really want to move my computer.

---

### Post by Calerid on 2011-10-15
Also one other thing you may want to check is the BIOS settings. I had an error with Wifi cards not working when switching from windows. The BIOS would reset it, so going into the BIOS and checking for a Wireless on/off option fixed my issues.

---

### Post by XBMC old School on 2011-10-15
Hey Super Newbie, 

Off topic but, if you ever intend to dump the ubuntu install do not delete the partition(if it is a side-by-each install). You will loose your windows boot.ini file if you do and then your semi hooped. dos command repairs required.

Free heads-up

---

### Post by Bkc1014 on 2011-10-15
>  Also one other thing you may want to check is the BIOS settings. I had an error with Wifi cards not working when switching from windows. The BIOS would reset it, so going into the BIOS and checking for a Wireless on/off option fixed my issues. 

Where in my BIOS would I find what you're talking about?

>  Hey Super Newbie, 

Off topic but, if you ever intend to dump the ubuntu install do not delete the partition(if it is a side-by-each install). You will loose your windows boot.ini file if you do and then your semi hooped. dos command repairs required.

Free heads-up 

Thanks for the tip, I think I read about this a bit somewhere. How would I remove my partition without getting rid of my windows boot .ini file?

I'm thinking that I'd still like to try and get Ubuntu 11.10 working before I get rid of it

---

### Post by XBMC old School on 2011-10-15
> **Bkc1014 said:**
> Where in my BIOS would I find what you're talking about?



Thanks for the tip, I think I read about this a bit somewhere. How would I remove my partition without getting rid of my windows boot .ini file?

I'm thinking that I'd still like to try and get Ubuntu 11.10 working before I get rid of it

Ya i just did two totally separate installs on separate drives and then changed the boot order over in my bios. your wifi option might be in your pci plugin thingys. Not every bios is the same. but your wifi card is probably mini pcie unless it is usb?

---

### Post by Bkc1014 on 2011-10-15
Thanks for the help everyone! It turns out that the wrong driver was being used for my system so I had to go and blacklist those and install new ones.

The how-to/solution is here:

[http://ubuntuforums.org/showpost.php?p=10391091&postcount=12](http://ubuntuforums.org/showpost.php?p=10391091&postcount=12)

---

