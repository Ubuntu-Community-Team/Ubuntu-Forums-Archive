---
title: "HP 2133 Mini-Note"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Alden belmor on 2008-09-12
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#Installing%20from%20a%20USB/SD%20Flash%20Drive](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#Installing%20from%20a%20USB/SD%20Flash%20Drive)

I have been using that guide to install ubuntu but my question is about the Video Driver Installation part.  every thing else work expect this part. 

>  Video and CPU Scaling Fixes -- Back in Terminal, type the following:

sudo gedit /boot/grub/menu.lst

This will bring up the grub boot menu configuration file. Scroll to the bottom of the file and you'll find several boot options. Go to the first, titled "Ubuntu 8.04.1, kernel 2.6.24-19-generic" and in the "kernel" line, delete "xforcevesa". In its place, type:

acpi_osi="!Windows 2006"

I could not find xforcevesa any idea what i did wrong but what i did was put acpi_osi="!Windows 2006" at the end of the kernel line. is that right or wrong?  Does any one have any idea whats wrong here?

thanks.

---

### Post by heretik_85 on 2008-09-12
"xforcevesa" should be there if you chose safe graphics mode when you started the install, or added the option manually. Not too sure why it wasn't there, but it's not going to hurt anything now. To be honest though, I never found that acpi_osi="!Windows 2006" made the slightest bit of difference to my battery life.

---

### Post by Alden belmor on 2008-09-12
> **heretik_85 said:**
> "xforcevesa" should be there if you chose safe graphics mode when you started the install, or added the option manually. Not too sure why it wasn't there, but it's not going to hurt anything now. To be honest though, I never found that acpi_osi="!Windows 2006" made the slightest bit of difference to my battery life.

ok thanks i didn't think it would.  So do you think i should remove the acpi_osi="!Windows 2006" from the kernel line.  BTW i added xforcevesa manually. 

**And let me ask you this every time Ubuntu boots the splash screen after there is a quarter left of the bar it turns different colors.  Do you know why it does that? **

---

### Post by Alden belmor on 2008-09-13
Do you think if I turn off the splash screen it would be better?

---

### Post by heretik_85 on 2008-09-13
> **Alden belmor said:**
> ok thanks i didn't think it would.  So do you think i should remove the acpi_osi="!Windows 2006" from the kernel line.  BTW i added xforcevesa manually. 

**And let me ask you this every time Ubuntu boots the splash screen after there is a quarter left of the bar it turns different colors.  Do you know why it does that? **

Might as well just leave grub the way it is for the time being. I've personally never noticed a difference (and don't bother with it on new installs), but I suppose even if you get another 5 minutes battery life, it's not a bad thing.

As for the coloured progress bar, I think it's just an issue with out-of-date VIA drivers, because it works fine with the vesa drivers as well as the Windows drivers. You'll also notice that you get artifacts with certain colours, sort of like orange blotches, most noticeable on the wallpaper and icons.

I've never found a quick and easy way to fix the graphical errors properly, and it's sort of been a small enough problem to overlook. There's some other threads here as well, like [http://ubuntuforums.org/showthread.php?t=871849](http://ubuntuforums.org/showthread.php?t=871849) and [http://ubuntuforums.org/showthread.php?t=870867](http://ubuntuforums.org/showthread.php?t=870867) where people have had similar issues, and compiled working drivers for the latest kernel version. It might be worth checking that out, if you have more patience than myself :).

---

### Post by Alden belmor on 2008-09-13
So its ok just to leave it the way it is?  I can look past it as long as its not harming anything. that was my main concern.

---

