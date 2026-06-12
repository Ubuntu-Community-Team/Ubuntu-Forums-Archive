---
title: "How do I put Ubuntu on a crashed machine?"
date: 2014-08-17
forum: New to Ubuntu
---

### Post by Big_Ted on 2014-08-17
My ma has a 2 yr old laptop that had windows 8 on it ... a Dell .... she does not want it anymore ..... it crashed .... is there a way to put Ubuntu on it?



thanks as always

---

### Post by Karolina.K on 2014-08-17
Can you access bios and such  boot menu?

If you can then you should be able to install ubuntu , from a cd or usb :)

---

### Post by egeezer on 2014-08-17
Windows 8 used the so-called Secure Boot, which was constructed to be secure against Linux.  If you access the BIOS (the UEFI, really) you should be able to turn off Secure Boot, in which case you can install from a CD, DVD, or USB, as miyamoto2 said.

To do that, you will probably need to press some function key (I know Dell used to use F12, but it might be DEL) at the monent the first screen appears (the one that advertises Dell).

---

### Post by Karolina.K on 2014-08-17
the keys that my different computers have had has been esc, f8, f9, f12   (for entering boot menu)  
my last computer had a different button called assist (it had win8, I had no problem installing ubuntu )
:)

---

### Post by MoebusNet on 2014-08-17
You didn't give us much information about the laptop, but this should answer most of the initial questions you will have about installing Ubuntu:

 [https://help.ubuntu.com/14.04/installation-guide/amd64/index.html](https://help.ubuntu.com/14.04/installation-guide/amd64/index.html)

After you've read through this, check back with any questions. Welcome! :)

---

### Post by grahammechanical on 2014-08-17
> [COLOR=#000000]Secure Boot, which was constructed to be secure against Linux. [/COLOR]

I am not sure that statement is accurate. Secure boot certainly does not stop us installing Ubuntu. 

> 
[LIST]
[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[/FONT]
[/LIST]


[https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Regards.

---

### Post by jack96 on 2014-08-17
If you put Ubuntu onto a usb or cd from a seperate machine, assuming you have one, you can install it from the USB if you can access the BIOS and change the boot sequence.  Make USB the priority drive to boot from, reboot the PC, and install linux, with the "format drive and install" option, not sure the exact wording.

---

### Post by Ratscallion on 2014-08-17
Ask for step-by-step help if you need it.

> **jack96 said:**
> If you put Ubuntu onto a usb or cd from a seperate machine, assuming you have one, you can install it from the USB if you can access the BIOS and change the boot sequence.  Make USB the priority drive to boot from, reboot the PC, and install linux, with the "format drive and install" option, not sure the exact wording.

Just adding to this, if you don't have another computer - and can't borrow someone's to make a LiveCD/LiveUSB, you can always order one from the ubuntu website, which you can do from, for instance, a public (library) computer or your phone. I'd also test the liveCD on the computer that you know works, that way when it comes to use it on the 'crashed' computer, you know there's no issue with the disc. By test, I just mean make sure you can boot into it.

---

### Post by ian-weisser on 2014-08-17
> **Big_Ted said:**
> it crashed .... is there a way to put Ubuntu on it?

I suppose it would depend on *why* it crashed.
If Windows crashed, but the hardware is fine, then download an installer image, put it on a USB stick, and run the Live environment to test what works.
If the hardware failed, then probably not. Ubuntu is great, but it's not magic.

---

### Post by newb85 on 2014-08-19
Lots of great suggestions so far.  With the several mentions of using an installation USB or CD, it's worth noting that for recent versions of Ubuntu, the .iso has been too large for a traditional CD, so the options are really USB or DVD.  (Lighter variants like Xubuntu and Lubuntu still fit on CD.)  And of course, the USB drive must be 1GB or larger.

---

### Post by stalkingwolf on 2014-08-19
On the first boot screen there should be a note usually in the bottom right that will tell you which key to use for what. IE use X for boot menu and Y for setup.  if you use the boot menu you can boot from either dvd or usb with out going into setup and changing the order.  Unless you have to change the secure boot setting. if so just do both at once.

---

### Post by dave131 on 2014-08-19
And this is an offer open only to you - so others please don't ask:  if you are in the U.S. and can't get access to the disk, let me know and I'll burn one and send it to you.  Since it is/was a Windows 8 machine it has to be 64-bit (at least as far as I know) so I'll burn the 64-bit version unless you want the 32-bit instead.

Unless this was one of the really inexpensive machines it should already have an optical drive.  As long as the optical drive is working I would use it.  If that fails then try USB.  It may still require going into your BIOS in changing the boot order so the optical drive is first.  As already mentioned, there are various keys depending on the manufacturer and the BIOS maker for getting to your set up.  Some of the more common ones are the DEL key, the DELETE key and lastly F2.  As previously mentioned, when you turn on the laptop it might show some line on how to do this - it will come quick.  Some manufacturers hide this from the user and instead have instructions for getting to the BIOS in their user guide or on online help.

But as already mentioned, the first thing to know is why it crashed before doing any more work.  Does the machine power on?  Does it go through boot but get some error when Windows tries to boot?  What messages do you get?

---

### Post by Ratscallion on 2014-08-19
> **dave131 said:**
>  there are various keys depending on the manufacturer and the BIOS maker for getting to your set up.  Some of the more common ones are the DEL key, the DELETE key and lastly F2.  As previously mentioned, when you turn on the laptop it might show some line on how to do this - it will come quick.  Some manufacturers hide this from the user and instead have instructions for getting to the BIOS in their user guide or on online help

Just adding to this, I've used a machine recently where to even get to the BIOS you had to ESCAPE the boot menu, DELETE, and then SPACEBAR, then select BIOS from a list of options. Definitely look online for your computer's make and model to find out how to get to the BIOS.

---

