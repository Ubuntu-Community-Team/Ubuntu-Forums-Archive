---
title: "error on install"
date: 2020-04-20
forum: New to Ubuntu
---

### Post by pettone on 2020-04-20
[COLOR=#222222][FONT=Verdana]Hi, I have an error when I start to install ubuntu (to dual boot) this is the error (see attachment pic) my laptop is a hp omen.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Any Idea of this error¡?[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]regards.[/FONT][/COLOR]

---

### Post by Autodave on 2020-04-20
I don't know about others here, but I cannot read that screen.

---

### Post by yancek on 2020-04-20
Can't make out much on the image other than a reference to an ACPI Error.  Dual booting with what?  Windows 10?  If so, read the information at the Ubuntu site from the link below and post more details on your hardware.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-04-20
I see something about nouveau.
Do you have nVidia?
Then you need nomodeset boot parameter when you boot.
With UEFI, you have to add the nomodeset in place of quiet splash on linux line. And you may need it on first boot after install, if you do not install nVidia proprietary driver during install.

Newer Nvidia graphics drivers are now available to users of Ubuntu&#8217;s Long Term Support LTS) releases, by default, no input required.
[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by him610 on 2020-04-21
> I see something about nouveau.
Yes, it says '...nouveau...stalled...'

---

