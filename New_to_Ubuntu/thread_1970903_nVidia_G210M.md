---
title: "nVidia G210M"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Goffer on 2012-05-01
let me start out by saying that this is my first experience with Linux...12.04. so far it is outstanding! i've only ran into one problem so far and that is with my gpu's. I have an Asus UL80VT that has the Intel 4500 integrated and an nVidia G210M. on Windows, it switched between the two depending on what I had on for settings. I understand that this won't happen on ubuntu. However, im wondering how to enable the G210M? under Details, it said that the graphics were unknown until I installed mesa utilities, now it says that the Intel 4500 is running. I should also note that the battery life is more in line with what it would be on windows with the G210M enabled...which is odd?

I should also note that Brightness doesn't work either.

---

### Post by 3rdalbum on 2012-05-01
The Additional Drivers program that's installed on Ubuntu should allow the Nvidia GPU to be used.

---

### Post by Goffer on 2012-05-01
nope. no drivers found.

---

### Post by papibe on 2012-05-01
Could you post the result of these commands?
```
lspci -nn | grep -i vga

sudo lshw -C display
```
Regards.

---

### Post by Goffer on 2012-05-01
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce G210M] [10de:0a74] (rev a2)

---

### Post by papibe on 2012-05-01
You have an special configuration.

You have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

### Post by Goffer on 2012-05-01
Thank you, it does. But on the contrary, this laptop does not have Optimus technology. In Windows, I have to manually switch between cards with a hardware button or have it so they switch depending on battery or ac power. They don't automatically switch according to demand. I will mess around in the BIOS and see if I can have the G210M on by default instead. Thanks again, completely forgot about going into the BIOS!

---

### Post by tomsecret on 2012-05-08
Hi Goffer! I have ul30vt, which is very similar to your laptop. In bios you can switch between "Enhanced" and "Compatible" under the IDE configuration. Having "Enhanced" enables both nvidia and the intel card - the nvidia card will draw power even though you're using your intel card in ubuntu. You can change the setting to "Compatible", then only the nvidia card will be enabled, and power usage will drop a little. If you wan't to only use the intel card you have to use the enhanced configuration, and load a module that turns off the nvidia card, look here in case you're interested: [http://ubuntuforums.org/showthread.php?t=1366605]("http://ubuntuforums.org/showthread.php?t=1366605"). There have also been done some work on switching dynamically between the two cards in linux, but this I haven't tested myself, for more information you can check out [https://launchpad.net/~asus-ul30]("https://launchpad.net/~asus-ul30"). Hope this points you in the right direction :)

---

