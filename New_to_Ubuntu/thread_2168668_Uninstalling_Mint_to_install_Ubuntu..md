---
title: "Uninstalling Mint to install Ubuntu."
date: 2013-08-18
forum: New to Ubuntu
---

### Post by Stephane_Coutu on 2013-08-18
Sorry if that's an easy answer to most of you, but i'm new to the linux world.

I just installed Linux Mint on my laptop... the installation must be corrupted or something cause i have all sorts of problems...
A friend showed me Ubuntu that is installed on his laptop, and I must say that I'm impressed of how it look.
Now, I wanna uninstall Mint and put Ubuntu in its place. I must add that i have Windows 7 installed too.
So my question is: How do I uninstall Mint without messing up my windows 7 partition. Someone told me i might have problems with grub or something.

Thanks a lot!

---

### Post by Jonathan Precise on 2013-08-18
Go to:

[http://sourceforge.net/projects/linux-secure/files/?source=navbar\]("http://sourceforge.net/projects/linux-secure/files/?source=navbar")

Click on the 32-bit version. Download, and use it like an ubuntu CD.

Note: If you have UEFI, select 64-bit.

Boot from the ubuntu CD as you normally will, then select "Try without installing". Choose OS uninstaller in the dash, and use it to uninstall Linux Mint.

Note 2: This will erase **Everything** you have on Linux Mint**!!!!!**

Select "Install Ubuntu" in the Dash.

Normally install this as you would install a regular ubuntu installation.

---

### Post by Mark Phelps on 2013-08-19
Laptops are special cases because it's not unusual for the laptop suppliers to use specialized hardware -- that in turn, requires specialized drivers.

So the fact that a Linux distro works fine on one laptop, even if the other is the same brand laptop, says nothing about the ability to install and run a Linux distro on the other laptop.

You should make a LiveUSB of the distro and boot the laptop from that.  That will show how well the Linux distro sees the hardware and installs the right drivers.

---

### Post by BBQdave on 2013-08-19
> **Mark Phelps said:**
> You should make a LiveUSB of the distro and boot the laptop from that.  That will show how well the Linux distro sees the hardware and installs the right drivers.

And if you like Ubuntu, you could simply install it over the Linux Mint installation - that will erase Linux Mint :)

---

### Post by r_avital on 2013-08-19
> **Stephane_Coutu said:**
> How do I uninstall Mint without messing up my windows 7 partition. Someone told me i might have problems with grub or something.

Thanks a lot!
You could uninstall Mint as described above.  Or you could proceed directly to install Ubuntu in the partition that is currently occupied by Mint.  The installation process will tell you what partitions are occupied by what operating systems and let you choose exactly what to do.  You'll probably want to erase Mint and install Ubuntu in its place.

Just in case you need more info on installing Ubuntu on a system where Windows7 is already installed:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

In any case, the idea of trying Ubuntu with a live cd is always a good move.

---

