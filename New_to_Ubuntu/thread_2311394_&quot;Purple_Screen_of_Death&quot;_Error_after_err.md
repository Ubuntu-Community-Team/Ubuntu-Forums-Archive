---
title: "&quot;Purple Screen of Death&quot; Error after error while trying to fix"
date: 2016-01-26
forum: New to Ubuntu
---

### Post by Hakmed on 2016-01-26
Hello all,

I have decided to turn my old laptop into a fixed Linux & Programming learning computer for myself. I have therefor installed Ubuntu to a brand new SSD. For some reason after the log-in, everything disappears from the screen and I am left with the purple background and my cursor(which also disappears while not using the mouse).
I know the installation was perfectly fine as I could use Ubuntu on my desktop PC with the same SSD. I then started using the SSD on my PC but installed Ubuntu on my HDD for the laptop. Results are still the same purple screen with the cursor..

Here are the specs of my laptop: [COLOR=#000000][FONT=HPRegular]AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-82 2.20GHz, 4GB RAM.

I have attempted to update by pressing 'CTRL+ALT+F1 or F2' at the purple screen and running "sudo apt-get update" which returns the following error on numerous lines just like most of the other "upgrade' or 'install' commands:
W: Failed to fetch ... Temporary failure resolving '...'.

Various tutorials recommended to review the 'resolv.conf' but I cannot open it. There also seems to be an issue with the permissions as I cannot open the 'root' directory either - "permission denied". 

In truth, I am not really interested in GUI as long as I can run the 'vim' command. Since it is not pre installed, I need to install it myself but with the above mentioned errors, it is not possible.

Any help would be highly appreciated.[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-01-26
I am confused. Perhaps you could explain. As I understand from what you have written, you installed Ubuntu on to an SSD that was in a desktop machine and then put the SSD in a laptop machine. Is that correct?

There is one area where such a method would fail. If you installed a proprietary video driver for the desktop machine and the laptop was using a completely different video adapter. Even if the two video adapters were of the same make there could still be a problem. Proprietary video drivers for newer adapters do not necessarily support older video adapters.

Are you getting to a login screen? What is stopping you re-installing Ubuntu on to that laptop with the SSD plugged in?

---

### Post by Hakmed on 2016-01-27
Apologies for the confusion: I first installed Ubuntu on SSD which was in the laptop. It didn't work (purple screen). When I connected the SSD to the PC it worked fine so I just left it there. I then tried to install Ubuntu to the HDD on the laptop. Same failure - purple screen after logging in.

Basically installation goes smoothly (as far as I can see) and the error becomes visible after I log in.

---

### Post by yancek on 2016-01-27
Which releasee of Ubuntu are you using?  The failed to fetch output usually means you are using and outdated or unsupported version.  Could be your network connection, could be the Ubuntu servers down also.

The permission denied is because if you are trying to access/modify anything outside the /home/user directory, you will need root permissions.  Preface any command with 'sudo' and use the password for the primary user.  To get more information you can post here for help, boot the Ubuntu installation medium, open a terminal and enter this command:  inxi -F

---

### Post by Hakmed on 2016-01-27
I think I may have an idea as to the root of the problem: when I ping 8.8.8.8 it pings however, when I try to ping 'Google.com' it returns with "unknown host google.com".

As per 'inxi -F' apparently 'inxi is currently not installed'.

I am using the latest edition - 15.10

---

### Post by Hakmed on 2016-01-27
Just fixed the issue with nameservers by using the following command: sudo apt-get remove -purge resolvconf && sudo apt-get install --reinstall resolvconf

I will now attempt to reinstall the driver

---

### Post by Hakmed on 2016-01-28
Which details from inxi -F would you like me to share?

System: Kernel: 4.2.0-25-generic i686(32 Bit) Console: try 1 Distro: Ubuntu 15.10 wily
CPU: Dual core AMD Turion X2 Ultra Mobile ZM-82
Graphics: 
Card: Advanced Micro Devices [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]
Display Server: X.org 1.17.2 druvers: ati, radeon (unloaded: fbdev, vesa)
 
Please note that I have fixed the issue with the nameservers.
 
Thanks

---

### Post by Geoffrey_Arndt on 2016-01-28
Are you sure you have the correct internet drivers installed for your laptop . . . what network chipset do you have?   That would explain about not accessing or being able to install programs, etc.   The purple screen and so on are tied in to your graphics system and lack of proper driver for that AMD  radeon.

So, first things first, check and fix connectivity (and double check your sources file is correct, all sources matching your distro release),  then install the graphics drivers.

---

