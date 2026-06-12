---
title: "Sony Vaio SVT1311 display brightness"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by Flusslauf on 2014-05-23
Hi there,

i have a little problem with the control of the display brightness of my svt1311.... my problem is the keys fn+F5 / fn+F6 that should control the brightness of my screen are not working... 

i tried many solutions i found in similar threads, especially there were many advices to change the /ect/default/grub file with additional commands for example acpi_backlight=vendor acpi_osi=Linux etc... I tried all these changes in all thinkable combinations ever suggested by anyone, but nothing helped...

At the moment the situation is that i am able to change screen brightness with the command```
echo XXXX | sudo tee /sys/class/backlight/intel_backlight/brightness
``` but I dont like this solution and would prefer working function keys.... 
Do you have any ideas how to fix the fn keys? at the moment they are not working at all, but there were situations (after trying some solutions) when i could "change" brigthness which in this case means that a brigthness-icon appeared showing the "actual brightness" that could be changed by fn keys (this had no effect to the actual brightness of the screen..). 

my grub file again is like after installing ubuntu.

thankful for any help :)

---

### Post by jeremy31 on 2014-05-23
> **Flusslauf said:**
> Hi there,

i have a little problem with the control of the display brightness of my svt1311.... my problem is the keys fn+F5 / fn+F6 that should control the brightness of my screen are not working... 

i tried many solutions i found in similar threads, especially there were many advices to change the /ect/default/grub file with additional commands for example acpi_backlight=vendor acpi_osi=Linux etc... I tried all these changes in all thinkable combinations ever suggested by anyone, but nothing helped...

At the moment the situation is that i am able to change screen brightness with the command```
echo XXXX | sudo tee /sys/class/backlight/intel_backlight/brightness
``` but I dont like this solution and would prefer working function keys.... 
Do you have any ideas how to fix the fn keys? at the moment they are not working at all, but there were situations (after trying some solutions) when i could "change" brigthness which in this case means that a brigthness-icon appeared showing the "actual brightness" that could be changed by fn keys (this had no effect to the actual brightness of the screen..). 

my grub file again is like after installing ubuntu.

thankful for any help :)

lspci in terminal, intel graphics?  lsmod, does it show i915?  In lspci does it have 00:02.0 in the line with the graphics card?  cat /var/log/Xorg.0.log | grep backlight results?

---

### Post by Flusslauf on 2014-05-24
Hi, there is an update regarding my fn keys. now the key, as discribed "change" the brightness and the change is displayed but nothing happens.

Here the line 00:02.0 and also the rest of lspci:

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
**00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)**
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)

the cat /var/log/Xorg.0.log gives me:

[     9.578] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')

---

### Post by jeremy31 on 2014-05-24
Ubuntu 14.04?  Have you tried > [COLOR=#333333][FONT=Ubuntu Beta]video.use_native_backlight=1[/FONT][/COLOR] or > [COLOR=#333333][FONT=Ubuntu Beta]video.use_bios_initial_backlight=0[/FONT][/COLOR], you may find that > acpi_backlight=vendor works without the acpi_osi
as kernel options in grub on the same line as quiet splash and inside the quotes, do a > sudo update-grub after saving changes

Another option that may help either kernel option is to create a file named 20-intel.conf in /usr/share/X11/xorg.conf.d and have this in the file
> [COLOR=#333333]Section "Device"[/COLOR]    Identifier  "card0"
    Driver      "intel"
    Option      "Backlight"       "intel_backlight" # use your backlight that works here
    BusID       "PCI:0:2:0" [COLOR=#333333]EndSection[/COLOR]

This file alone should change the result of cat /var/log/Xorg.0.log | grep backlight so that you will see after rebooting
    33.538] (**) intel(0): Option "Backlight" "intel_backlight"
[    33.539] (**) intel(0): found backlight control interface intel_backlight (type 'user')

---

### Post by Flusslauf on 2014-05-24
oh man, great thanks!

i tried everything you posted except the first one
```
[COLOR=#333333][FONT=Ubuntu Beta]video.use_native_backlight=1[/FONT][/COLOR]
```
which actually solved the problem!

im not sure if i tried the last thing with the 20-intel.conf file. i tried something similar from another thread about vaio svt1311 but not sure about the exact things i wrote in there.

Edit: yes i use Ubuntu 14.04

---

### Post by FiremanEd on 2014-05-24
I am having the exact same issues with a Dell Inspiron 15 with the i915 and same brightness issue with the fn key. But, having a problem following the thread to do the fix, could someone compile this thread and post the steps of the final result of Flusslauf's fix?

---

### Post by jeremy31 on 2014-05-24
> **FiremanEd said:**
> I am having the exact same issues with a Dell Inspiron 15 with the i915 and same brightness issue with the fn key. But, having a problem following the thread to do the fix, could someone compile this thread and post the steps of the final result of Flusslauf's fix?

He solved his with (likely steps taken)> gksu gedit /etc/default/grub then you find this line > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" yours may not have "quiet splash" but add > [COLOR=#333333][FONT=Ubuntu Beta]video.use_native_backlight=1[/FONT][/COLOR] inside of the quotes, save the file, exit gedit.  Then enter > sudo update-grub  reboot

This fix will likely only work with Ubuntu 14.04 unless you have the 3.13 kernel installed

---

### Post by FiremanEd on 2014-05-24
Jeremy, thank you very much!  It is fixed with me as well.
You Rock!  Ed

---

