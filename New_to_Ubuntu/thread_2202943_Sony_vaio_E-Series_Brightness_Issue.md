---
title: "Sony vaio E-Series Brightness Issue"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by rajeshwar2 on 2014-01-31
Hello Everyone,

[COLOR=#000000]I hope to find help here!

I installed ubuntu 12.04 on my SONY VAIO E-Series VPCEH16EN Laptop.
My fn+F5([/COLOR][COLOR=#000000]decrease brightness[/COLOR][COLOR=#000000]) and fn+F6(increase brightness) these function keys are not working that means they show on screen to increase and decrease but not effected on screen brightness.
So pl'z help.[/COLOR]

---

### Post by papibe on 2014-01-31
Thread moved to **Absolute Beginners Section**.

---

### Post by Toz on 2014-02-01
Can you open a terminal window, type in the following commands, and post back the results?

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card(s) and drivers:
```
lspci -k | grep -A2 VGA
```

3. Info about your backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```

---

### Post by rajeshwar2 on 2014-02-02
1) [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cmdline
> [/FONT][/COLOR]BOOT_IMAGE=/boot/vmlinuz-3.8.0-35-generic root=UUID=61ceeb6c-7943-4bfe-a28b-d0314dfc0cea ro quiet splash acpi_osi=Linux[COLOR=#000000][FONT=Ubuntu Mono]

2) [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lspci -k | grep -A2 VGA
> [/FONT][/COLOR]01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 410M] (rev a1)	Subsystem: Sony Corporation Device 908b
	Kernel driver in use: nvidia


[COLOR=#000000][FONT=Ubuntu Mono]

3) [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
> [/FONT][/COLOR]/sys/class/backlight/acpi_video015
15
15


[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Toz on 2014-02-02
Try adding:
```
Option         "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of your /etc/X11/xorg.conf file.

You'll need to log out and back in again to test.

---

### Post by rajeshwar2 on 2014-02-02
Yaa man,
it's working nice,
Thank you Toz....:smile:

---

### Post by rajeshwar2 on 2014-09-21
Hey Toz,

I installed fresh copy of Ubuntu 14.04.
In that I followed your steps but i am getting an [IMG]http://i.stack.imgur.com/AiwJH.png[/IMG]

So what can I do can you tell me.

and also

for 

1)cat /proc/cmdline

> BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=a79e36ba-4610-4023-be47-3fff8c4fd903 ro recovery nomodeset


2) lspci -k | grep -A2 VGA

> 01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 410M] (rev a1)
    Subsystem: Sony Corporation Device 908b
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)


3) [COLOR=#000000][FONT=Ubuntu Mono]for  interface in /sys/class/backlight/*; do echo $interface; cat  $interface/max_brightness; cat $interface/actual_brightness; cat  $interface/brightness; done

> /sys/class/backlight/acpi_video0
15
15
15

[/FONT][/COLOR]

---

### Post by Toz on 2014-09-21
It doesn't look like you're system is using the nvidia driver (probably using vesa) in the screenshot and posts above. 

If you don't add the command to your /etc/X11/xorg.conf file, do the graphics start up properly with the nvidia driver?

---

### Post by rajeshwar2 on 2014-09-21
yaa i got it....

---

