---
title: "Windows 7 &amp; Ubuntu 11.10 wont work"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by kraziyk on 2012-05-12
I have tried to install Ubuntu 11.10 on my Windows 7 pc. I have the requirements for both OS.

I have installed Ubuntu on my secondary hard drive, which doesn't have Windows 7 installed on it. Everything installed succesfully.

Once I install Ubuntu, and the pc resets, I get a Grub error. Then have to go into Windows, via the Windows OS cd, run a command prompt to repair the Grub file.

How do I install or fix this, so I can dual boot Ubuntu & windows 7 on one machine. Maybe I am skipping a step or something.

Thanks.

---

### Post by carl4926 on 2012-05-12
During the install  process you have to select a location for grub. Typically it will select sda, which would normally be the first boot device.

Here is what I would dp. Make sure the HD you are installing Ubuntu to is set as the first boot device HD in BIOS. Make a note how the installer sees it, either as sda or sdb and be sure to make sure the correct device is set here
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg)

Don't worry about windows HD being  different in boot order. Ubuntu will take care of that.

---

### Post by kraziyk on 2012-05-12
thanks, I'll give this a shot and get back to you.

---

### Post by kdane4 on 2012-05-12
> **kraziyk said:**
> I have tried to install Ubuntu 11.10 on my Windows 7 pc. I have the requirements for both OS.

I have installed Ubuntu on my secondary hard drive, which doesn't have Windows 7 installed on it. Everything installed succesfully.

Once I install Ubuntu, and the pc resets, I get a Grub error. Then have to go into Windows, via the Windows OS cd, run a command prompt to repair the Grub file.

How do I install or fix this, so I can dual boot Ubuntu & windows 7 on one machine. Maybe I am skipping a step or something.

Thanks.


uhm,, just to avoid confusion, this is ubuntu install via WUBI right?

---

### Post by kraziyk on 2012-05-12
No I can never get Wubi to work, so I was using the boot disc I burned from the site.

I've tried Wubi, but it never works. When the boot screen comes up for me to choose between Ubuntu and Windows I choose Ubuntu and it basically says theirs some kind of error and doesn't work. Taking me back to the OS boot loader.

---

### Post by carl4926 on 2012-05-12
Don't use wubi....please
Waste of space...

---

### Post by carl4926 on 2012-05-12
It's simple

Set the Ubuntu HD as first HD in BIOS boot order
Install, making sure the bootloader is to the correct HD MBR

---

### Post by kdane4 on 2012-05-12
> **carl4926 said:**
> Don't use wubi....please
Waste of space...

Its good for a beginner I guess since I started out with a WUBI install myself :)

> **kraziyk said:**
> No I can never get Wubi to work, so I was using the boot disc I burned from the site.

I've tried Wubi, but it never works. When the boot screen comes up for me to choose between Ubuntu and Windows I choose Ubuntu and it basically says theirs some kind of error and doesn't work. Taking me back to the OS boot loader.

OK, can you please edit the WUBI prefix from your thread to avoid confusion? :)

---

