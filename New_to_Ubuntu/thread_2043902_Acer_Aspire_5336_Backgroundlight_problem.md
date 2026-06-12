---
title: "Acer Aspire 5336 Backgroundlight problem"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by simonshare on 2012-08-17
Hello, i'm trying to install the Ubuntu 12.04 desktop i386 it boot up just fine, but there is no background light on my screen what can i do? I'm downloading alternate version already and will try it in 20 minutes or so... Any1 had simillar problems? Sorry for poor english it's not mine primary language...

---

### Post by 2F4U on 2012-08-17
Seems to be quite a common problem on this model:

[http://ubuntuforums.org/showthread.php?t=1978846](http://ubuntuforums.org/showthread.php?t=1978846)
[http://ubuntuforums.org/showthread.php?t=1742352](http://ubuntuforums.org/showthread.php?t=1742352)

---

### Post by simonshare on 2012-08-17
I still don't get it should i continue install without background light or what? My lights went out as i boot Ubuntu from disk...
It will be a lot harder to install ubuntu without light as i can't see anything on screen

---

### Post by jayismyname on 2013-05-22
I had this issue with 12.10 and 13.04 when you first boot the disk get into the grub boot menu and press F6 and select **nomodeset**. You will be able to install fine no problems and boot up from drive with no problems but the resolution will be out and it will run slow so to fix this you go into grub **sudo gedit /etc/default/grub** then change **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to** GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"** then change **GRUB_CMDLINE_LINUX=""** to **GRUB_CMDLINE_LINUX="acpi_osi=Linux"** make sure you use a cap L in Linux. You need to delete **nomodeset** from the grub script that will sort out the resolution and the slowness but not the back light. After you have done all this press save and exit back to the terminal and run **sudo update-grub** so it is set up for the next time you boot. enter **sudo gedit /etc/rc.local **(you might have to be root for this) then between **does nothing **and **end 0** add **setpci -s 00:02.0 F4.B=00** 

This has completely cured it for me I don't have to do anything to it now and it took me 2 days to sort out running brilliantly with no issues. Just to add you might have read to start it with acpi=off don't as it will disable your WiFi!

---

