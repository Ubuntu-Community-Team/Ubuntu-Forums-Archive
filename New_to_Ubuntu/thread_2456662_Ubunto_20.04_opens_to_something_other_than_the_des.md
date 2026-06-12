---
title: "Ubunto 20.04 opens to something other than the desktop"
date: 2021-01-16
forum: New to Ubuntu
---

### Post by toodumb on 2021-01-16
I have an older HP laptop I have tried to install Ubuntu 20.04LTS on.
I have done this before and it opened to the desktop.
I'm not sure if I did something wrong but when I power it up I get a screen with:

"GNU Grub version 2.04" (shown at the top.)

"Minimal BASH-like file editing is supported."


"For the first word,TAB lists possible command completion.Anywhere else TAB lists possible or file completion."

Then below, it looks like some command line ..ehh... stuff.

grub> _


I'm afraid I know nothing about this and do not know what to do with this. Is there some sort of command I am supposed to use? If this laptop is going to be unusable it is destined to the scrap heap, I just do not know at this point.

Could someone here give me some information as to how to proceed?

---

### Post by CelticWarrior on 2021-01-16
If it's really old then it has BIOS; if not that old, let's say 2010 or newer then it has UEFI.
This firmwares perform the exact same duty but UEFI is newer, tailored for current hardware, more powerful and versatile than the 1981 BIOS.

If BIOS there's only one way to install and boot: The bootloader is installed in the MBR of the one of the drives and that drive should be the first in the booting order defined in BIOS settings. That being the case please check the boot order before anything else.

If UEFI it can be more complex. Better to see details. Please use the 2nd option to install and run Boot Repair in the same USB you used to install Ubuntu. Do NOT apply any repair at this point but create the summary report instead and post it here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2021-01-16
> an older HP laptop I have tried to install Ubuntu 20.04LTS on.

Is this the first boot after installation? Has this been a running operating system before this problem happened? Is this a re-installation? Here are instructions on how to use Boot Repair. As requested above, please create the bootinfo summary and post the pastebin link in this thread so that we can see it.

Regards

---

### Post by toodumb on 2021-01-17
> **grahammechanical said:**
> Is this the first boot after installation? Has this been a running operating system before this problem happened? Is this a re-installation? Here are instructions on how to use Boot Repair. As requested above, please create the bootinfo summary and post the pastebin link in this thread so that we can see it.

Regards Thanks for your reply. 
I had installed the same version some time ago, but it ran so slowly  I gave up on it. I thought I would have another try at it. I downloaded it to a usb stick and used rufus to make it bootable. I'm afraid "bootinfo summary" is Greek to me. Sorry,but a complete beginner here.
I'm thinking of trying it one more time before I drive a screwdriver through the hard drive. As slow as it was before, it did open to the desktop.
I bought this HP laptop new in 2015.
Thanks again.

---

### Post by yancek on 2021-01-17
Go to the link below and read through the page to understand it.  Scroll down on the page and use the instructions under 2nd option to download it to your Ubuntu system.  Then follow the instructions on that page to Create BootInfo Summary and do that.  When it finishes, you will get a link which you can post here and members will be able to see details on your system and boot files and, hopefully help.  You can do this from the Ubuntu install USB if you can get an internet connection.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The error in your first post means the Grub bootloader was not installed correctly.  Is there currently no other operating system on the computer?  Running slowly is often the result of hardware such as a slow processor not enough RAM.

---

### Post by toodumb on 2021-01-18
No other operating system. I will try what you suggest. Thanks again.

---

