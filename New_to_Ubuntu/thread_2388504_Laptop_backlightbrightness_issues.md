---
title: "Laptop backlight/brightness issues"
date: 2018-04-03
forum: New to Ubuntu
---

### Post by depressedwatermelon on 2018-04-03
[COLOR=#000000][FONT=Arial]I have a Dell Inspiron 3162/3164 laptop that refuses to change brightness (using the slider or FN keys) on Xubuntu 16.04 LTS.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have googled endlessly and have narrowed a few things down. I will use this forum post ([/FONT][/COLOR][COLOR=#1155cc]_[https://ubuntuforums.org/showthread.php?t=2182861](https://ubuntuforums.org/showthread.php?t=2182861)_[/COLOR][COLOR=#000000][FONT=Arial]) to help convey information as clearly as possible.[/FONT][/COLOR]
[U][B]
[COLOR=#000000][FONT=Arial]KERNEL PARAMETERS[/FONT][/COLOR][/B][/U]
[COLOR=#000000][FONT=Arial]```
kevin@kevin-Inspiron-11-3162:~$ cat /proc/cmdline
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Arial]BOOT_IMAGE=/boot/vmlinuz-4.13.0-37-generic.efi.signed root=UUID=810b7015-1c13-4482-b265-f5ef8b9c9406 ro acpi_backlight=vendor quiet splash nomodeset vt.handoff=7[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Arial]If I don't have nomodeset in there, I am met with a black screen upon booting no matter what -buntu I use. I don't quite understand why, it was just the solution I found when first installing Linux on this laptop.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]With acpi_backlight=vendor in there, there WILL be a brightness slider when I click on the battery icon, and the brightness FN keys will display the notification of brightness changing, however it will not actually change. If I replace it with acpi_backlight=*anythingelse*, there will be no brightness slider/FN notifications.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I also tried, individually, "acpi_osi=Linux" and "acpi_osi=none" and "acpi_osi=", but they don't seem to do anything.[/FONT][/COLOR]
[U][B]
[COLOR=#000000][FONT=Arial]INFO ABOUT VIDEO CARD(S)[/FONT][/COLOR][/B][/U]
[COLOR=#000000][FONT=Arial]```
kevin@kevin-Inspiron-11-3162:~$ lspci -k | grep -iA3 VGA
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Arial]00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 35)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    DeviceName:  Onboard IGD[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    Subsystem: Dell Device 0725[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    Kernel modules: i915[/FONT][/COLOR]
```
[U][B]
[COLOR=#000000][FONT=Arial]CURRENT BACKLIGHT INTERFACES AND THEIR VALUES[/FONT][/COLOR][/B][/U]

[COLOR=#000000][FONT=Arial]```
kevin@kevin-Inspiron-11-3162:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Arial]/sys/class/backlight/dell_backlight[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]5[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]15[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Arial]If I move the slider, the value returned by the terminal for brightness will change, however the physical brightness of the screen will not. (probably expected, but I'd include this just in case).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When googling for solutions, most people seemed to have "intel_backlight" along with their dell_backlight, acer_backlight or similar[/FONT][/COLOR]
[U][B]
[COLOR=#000000][FONT=Arial]TRYING TO MANUALLY SET BRIGHTNESS VIA TERMINAL[/FONT][/COLOR][/B][/U]
[COLOR=#000000][FONT=Arial]```
kevin@kevin-Inspiron-11-3162:~$ echo 1 > /sys/class/backlight/dell_backlight/brightness
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Arial]bash: /sys/class/backlight/dell_backlight/brightness: Permission denied[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]The screen brightness is very high and is burning my eyes right now, so I tried a value of 1 as it would be impossible to miss.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Permission denied, so I tried the solution in the first reply to this thread ([/FONT][/COLOR][COLOR=#1155cc]_[https://ubuntuforums.org/showthread.php?t=2088043](https://ubuntuforums.org/showthread.php?t=2088043)_[/COLOR][COLOR=#000000][FONT=Arial])

[/FONT][/COLOR]```
kevin@kevin-Inspiron-11-3162:~$ echo 1 | sudo tee /sys/class/backlight/dell_backlight/brightness
[sudo] password for kevin: 
1
```
There is no change in physical brightness of the screen, but if I double check the value

```
kevin@kevin-Inspiron-11-3162:~$ cat /sys/class/backlight/dell_backlight/brightness
1
```
It has indeed changed to 1.

[COLOR=#000000][FONT=Arial]
If I plug the  charger in, sometimes the screen will lower in brightness. If I remove  the charger after this, it will remain at this lowered brightness. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I originally had Lubuntu 16.04 LTS installed on it, and the brightness slider as well as the FN keys to change brightness worked perfectly, but Lubuntu was a bit too "barebones" for me, so I decided to try Xubuntu.

[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]While googling for a solution, I think I read that these issues may be caused by the kernel being too old in comparison to the hardware. I don&#8217;t quite understand the ins and outs of this, but maybe the latest LTS version (which releases on the 26th of this month) can fix my problems![/FONT][/COLOR]

---

### Post by kerry_s on 2018-04-03
if your looking for something as lite as lubuntu, but more refined then xubuntu, have a look at elementary os.
[https://elementary.io/](https://elementary.io/)

it's still based on ubuntu 16 lts, just prettier.

---

### Post by depressedwatermelon on 2018-04-03
> **kerry_s said:**
> if your looking for something as lite as  lubuntu, but more refined then xubuntu, have a look at elementary os.
[https://elementary.io/](https://elementary.io/)

it's still based on ubuntu 16 lts, just prettier.


I'll definitely check elementary OS out. Especially if I can't fix this issue with Xubuntu.

 I'm still trying to find the right distribution for me!

---

### Post by kerry_s on 2018-04-03
yeah, for some reason they all work differently even though they come from the same base os.
you'll find that a lot in linux, where a certain version just matches with your hardware perfectly & other's are hit or miss certain things.

---

