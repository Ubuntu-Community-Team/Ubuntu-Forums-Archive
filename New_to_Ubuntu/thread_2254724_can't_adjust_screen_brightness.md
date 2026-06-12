---
title: "can't adjust screen brightness"
date: 2014-11-29
forum: New to Ubuntu
---

### Post by Siebrant_Hendriks on 2014-11-29
I recently got a new laptop, the acer aspire E5-551G-T1LD, and installed lubuntu 14.4 trusty tar on it. I got a x64 amd processor and a amd video card. now is the problem that i cant seem to adjust the screen brightness which sort of defies the whole point of why i got lubuntu namely a longer battery time. I tried several programs and solutions found on the internet like the program xbacklight and editing a line in my grub to  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor" note the ''nomodeset'' i already had in the line for fixing a problem where i would get a blackscreen on startup. anyway I think this is as far as I am able to get by myself, since I am fairly new to linux. so I hope someone can help me with this problem, and if anyone has suggestions about any other thing i can do to safe some power feel free to say it.

---

### Post by DarkSapphire on 2014-11-30
Does your laptop have any brightness keys on the keyboard?

---

### Post by Siebrant_Hendriks on 2014-11-30
yes, i am supposed to adjust the brightness with fn+left arrow and fn+right arrow, however they don't seem to work.

---

### Post by Rob Sayer on 2014-12-01
No one can help you without knowing what video card you actually have.  Read this:

[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

You may have to run a bunch of those commands in terminal to get the actual model.

Post results here embedded in [CODE] tags.

---

### Post by Siebrant_Hendriks on 2014-12-02
```

siebrant@Flappy:~$ sudo lshw -C video[sudo] 
password for siebrant: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Kaveri
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0000000-f07fffff ioport:4000(size=256) memory:f0b00000-f0b3ffff memory:f0b60000-f0b7ffff
  *-display UNCLAIMED
       description: Display controller
       product: Opal XT [Radeon R7 M265]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:f0a00000-f0a3ffff ioport:3000(size=256) memory:f0a40000-f0a5ffff
```
Here it is, hope i did it the right way, it kind of looks like i used a command which gave much more information than what would be needed. anyway sorry i didn't gave this earlier, i didn't know i should have posted this, and i hope you can help.

---

### Post by mop2 on 2014-12-10
> **Siebrant_Hendriks said:**
> yes, i am supposed to adjust the brightness with fn+left arrow and fn+right arrow, however they don't seem to work.

Do your other function keys work? If not, try changing the keyboard model in the Keyboard Layour Handler application.

---

### Post by Dennis N on 2014-12-10
If xbacklight is installed, Lubuntu has defined keybindings for that:

**Ctrl+F10** decrease brightness
**Ctrl+F11** increase brightness

Try those.

---

