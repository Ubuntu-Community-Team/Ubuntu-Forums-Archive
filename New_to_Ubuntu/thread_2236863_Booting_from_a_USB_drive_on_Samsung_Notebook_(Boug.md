---
title: "Booting from a USB drive on Samsung Notebook (Bought in 2013)"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by bravidonatir on 2014-07-29
Now I know what everyone who reads the title is probably thinking: oh just disable fast BIOS and secure boot then go into CSM OS. The thing is: I'm posting this thread from the Ubuntu-powered laptop that is facing some problems. The point is: I already know how to install linux. It's elementary, it's very easy to install linux, generally. I've installed it on a number of computers for various, different reasons. Here's where I'm running into problems when trying to reinstall ubuntu. I do all the things I'm supposed to, and I've made sure all the drivers are up to date, I've even used all the different USB ports on the laptop (which are all functioning), but I cannot seem to get a USB-boot option to pop up. I press F10 to go into quick boot menu, that does not work; I go into UEFI and try changing boot device priority, also does not work. Yes, I've also tried fiddling around with the USB and just making sure that it is indeed, running a USB-bootable version of ubuntu, which it is. I can boot into it on other computers. I really don't know what the problem could be. Any ideas?

---

### Post by Vladlenin5000 on 2014-07-29
Is it a Intel "Bay Trail" CPU based? If so, bad news: Many manufacturers are shipping systems with a 32-bit UEFI in spite of the 64-bit processor. Such  (absurd) UEFIs aren't currently supported. It may be supported by the time of the 14.10 version but I wouldn't keep my hopes high...

---

### Post by Gordonbp531 on 2014-07-29
Don't know how relevant this is:
I had exactly the same problem with a Lenovo U410, also purchased in 2013.
I eventually discovered that the problem was USB3 ports..
If I created the bootable USB stick using a USB3 port, then the machine wouldn't boot from it at all, no matter whether I used a USB2 or a USB3 port to insert the stick.
If however I created the bootable USB stick on a USB2 port, then all was well!
Strange but true...

---

### Post by Bucky Ball on 2014-07-29
gendibal's suggestion is worth a shot. So you have successfully installed Ubuntu on this machine using this method previously? You mention this is a 'reinstall' ...

PS: If there's a USB stick plugged in to the machine at boot, you would get the option to boot from it, whether it is capable of booting or not. That is by the by. If it's there the machine should see it and try and boot from it ... and fail if necessary. Dumb beasts, computers. ;)

---

### Post by bravidonatir on 2014-07-30
Alright I will try installing it on the USB of laptop from where I wish to install. I'll let you know how it goes! Thank you for all the quick replies and suggestions!

---

### Post by CJ_Hudson on 2014-07-30
It is possible, but extremely unlikely, that the BIOS is infected or somehow corrupted which is affecting the computers ability to detect the Data stick.
However I have only seen this actually happen once in reality and it was on a very old computer (i.e. Pentium IV) that I salvaged from the rubbish tip!
However as that great Sleuth Sherlock Holmes once said, (or would have said, had he been real,) "*When you*'ve *eliminated all other* possibilities whatever *remains, no matter how* *improbable*, *must be the truth*.."

---

### Post by bravidonatir on 2014-07-30
Okay so I gave the USB thing a try, and no luck. I knew it sounded too easy! I looked on current system specs and the OS currently installed is, in fact, a 64-bit OS so I would like to avoid reinstalling with 32-bit. Any other ideas? Some sort of terminal command would be nice for crap like this...

---

### Post by oldfred on 2014-07-30
Some UEFI/BIOS seem to get locked up after too many tries.

Sometimes a total cold reboot. Power down, disconnect and hold on switch to drain residual power. If a laptop remove battery also so all power is gone. Then wait at least 10 sec and plug back in,and see if a total cold boot lets you get into UEFI and select boot device.

---

