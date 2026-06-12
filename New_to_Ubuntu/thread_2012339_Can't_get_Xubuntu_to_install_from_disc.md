---
title: "Can't get Xubuntu to install from disc"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by ebonygeek45 on 2012-06-29
After Installing Xubuntu to my laptop, I want to try it on my desktop. 
X
It is running XP and if you try to work on it you will be sitting all day looking at a screen that is stuck no matter how many times you reboot it. 

It has never really worked right and I tried adding memory and hard drive. I really think it is the operating system. 

I dug it out the closet and tried to load Xubuntu on it. I already knew that with how old it is it probably can't handle Ubuntu. 

Problem is I can't get it to install from boot. XP keep loading. I even tried disabling the hard drive it still won't boot from the cd I burned. The CD is fine, it is the same one I use to install Xubuntu to my desktop. 

Is there a way to manually install it without the CD??

Maybe an older verion that will install directly on the computer. Then update that version to Xubuntu?

I am really hoping someone can help with this.

---

### Post by BBQdave on 2012-06-29
> **ebonygeek45 said:**
> Problem is I can't get it to install from boot. XP keep loading.

Usually there is a key such as **ESC** or **F12** that will allow you to enter into the bios at boot and select what you would like to boot from (hard drive, cd drive, usb).

Sometimes you may have to arrange the order of boot in bios:
*boot first from cd drive*
*boot second from hard drive*

Ordering in this way will let your system first check the cd drive (for bootable cd), then if it finds nothing it will continue on (second choice) to boot from the hard drive.

---

### Post by Bucky Ball on 2012-06-29
> **BBQdave said:**
> Usually there is a key such as **ESC** or **F12** that will allow you to enter into the bios at boot and select what you would like to boot from (hard drive, cd drive, usb).

Sometimes you may have to arrange the order of boot in bios:
*boot first from cd drive*
*boot second from hard drive*

Ordering in this way will let your system first check the cd drive (for bootable cd), then if it finds nothing it will continue on (second choice) to boot from the hard drive.

+1. You need to change the setting for the boot device in BIOS. When you start the machine you need to hit F2 or Delete (it varies depending on the BIOS). 

That gets you to the BIOS. You need to find the first boot device setting and set that to CD. Make sure the CD is in then hit F10 to save and exit.

PS: Hard to install Ubuntu if you have the hard drive out of the box, if that is the only one you had in there ...

---

### Post by ebonygeek45 on 2012-06-29
Thank you BBQdave, 

Usually there is a key such as **ESC** or **F12** that will allow you to enter into the bios at boot and select what you would like to boot from (hard drive, cd drive, usb).

*>>This particular computer use  *F1 to get to bios.

Sometimes you may have to arrange the order of boot in bios:
*boot first from cd drive*
*boot second from hard drive*

*>>I ordered my CD rom to boot first , same thing when I tried a zip drive.  Just for kicks after trying a few time I disabled the hard drive  and put the cd rom for all four positions, Didn't work. *

Ordering in this way will let your system first check the cd drive (for  bootable cd), then if it finds nothing it will continue on (second  choice) to boot from the hard drive.

Could it be something with the system. Is going into bios and boot the only way to configure how a computer boot?


Thank you Bucky Ball,

PS: PS: Hard to install Ubuntu if you have the hard drive out of the box, if that is the only one you had in there ... 	

I added a hard drive to the one in the box. Could that have something to do with it?

I do have an external drive (1 tb). Theoretically, If the computer is compatible with it (My mother took it home with her by mistake so I don't have it with me) Is it possible to load it to that and have it use that as the operating system without a hard drive?? 

Or load it with another computer and get it working to specs and use it on this computer as the hard drive?

---

