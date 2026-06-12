---
title: "Mouse freezes when playing Youtube videos"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by Hankbonk on 2015-06-15
[COLOR=#000000]Having worked with Lubuntu 14.04 LTS for a year now, I started to get troubles.  When I start some (not all) youtube clips, My Mouse pointer gets frozen on my screen, it does'nt move anymore ! 

My PC is a HP Compaq DC 7700 SFF Dual core D 945 3400 Mhz/ HDD 80Gb S-ATA / 1536 Mb DDR2 RAM .[/COLOR]
 
[COLOR=#000000]What does <Sysreq> + R,E,I,S,U,B exactly do,besides a quick reboot ? The above problem starts to increase !!!  [/COLOR]

---

### Post by kerry_s on 2015-06-15
what vid card ?

---

### Post by kostkon on 2015-06-15
Also, are you using the Flash or the HTML5 player?

---

### Post by Hankbonk on 2015-06-16
Thanks for your reaction, kerry_s .  I do not know what video card my PC uses, how can I get this info ?

---

### Post by Hankbonk on 2015-06-16
Thanks for your reaction kostkon .  I have Shockwave Flash installed, but I don't know which the youtube clips giving this error uses .  How can I figure that out ?

---

### Post by slickymaster on 2015-06-16
> **Hankbonk said:**
> Thanks for your reaction, kerry_s .  I do not know what video card my PC uses, how can I get this info ?
```
lspci | grep VGA
```or for a more detailed information```
sudo lshw -C video
```

---

### Post by howefield on 2015-06-16
For the video card try getting the output from this terminal command.

```
sudo lspci | grep VGA
```

To enable HTML5 in youtube, try the info on this page [https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by Hankbonk on 2015-06-16
Thanks slickymaster, kerry_s, this is what I get 
after [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C video

[/FONT][/COLOR] 
*-display               
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f0400000-f04fffff memory:e0000000-efffffff ioport:1100(size=8)

---

### Post by Hankbonk on 2015-06-16
Thanks howefield .

Dear konkon, on the [https://www.youtube.com/html5](https://www.youtube.com/html5) page is stated that my Google Chrome browser supports HTML5 player, ok ?

---

### Post by kerry_s on 2015-06-16
in terminal:

gksudo leafpad /usr/share/X11/xorg.conf.d/20-intel.conf

paste this in it:

```

Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection

```

save & reboot.
install zram-config to help with your limited ram.
you might also want to consider using a lighter browser such as midori, grab the ppa version. if you use the adblock it will take longer to start. i use a hosts block list instead, so my midori open instantly.

---

### Post by Hankbonk on 2015-06-16
Thanks kerry_s, I have made that change you mentioned, know I will see if I still get blocked on every Youtube clip I can start . Let's wait and see, thank you !

---

### Post by kerry_s on 2015-06-16
crossing my fingers, hope it works. i have the same vid & driver in my netbook. depending on the *ubuntu version there&#8217;s different tweaks. i figure since lubuntu is pretty basic just the standard tweak. i use ubuntu-mate so different setting, with "uxa" there's no osd display for volume & brightness, so i use "sna" & "tearfree" on mine.

---

### Post by Hankbonk on 2015-06-18
[COLOR=#000000]Dear kerry_s,
 
I sadly inform you that the new /usr/share/X11/xorg.conf.d/20-intel.conf file I created didn't solve the problem .
I still have the same problem : My cursor pointer gets stuck .

When for instance I start the youtube clip in this URL [/COLOR]http://thefreethoughtproject.com/philosophy-bruce-lee/
my mouse pointer still freezes, [COLOR=#000000]and then I use <Alt> + <Sysrq> + R,E,I,S,U,B to reboot the system

Maybe you can examine that particular example URL and tell me your findings ?

Hoping to hear from you soon,

Hankbonk.
[/COLOR]

---

### Post by kerry_s on 2015-06-18
> **Hankbonk said:**
> [COLOR=#000000]Dear kerry_s,
 
I sadly inform you that the new /usr/share/X11/xorg.conf.d/20-intel.conf file I created didn't solve the problem .
I still have the same problem : My cursor pointer gets stuck .

When for instance I start the youtube clip in this URL [/COLOR]http://thefreethoughtproject.com/philosophy-bruce-lee/
my mouse pointer still freezes, [COLOR=#000000]and then I use <Alt> + <Sysrq> + R,E,I,S,U,B to reboot the system

Maybe you can examine that particular example URL and tell me your findings ?

Hoping to hear from you soon,

Hankbonk.
[/COLOR]

yeah, it played fine for me.

what browser did you use ?

---

### Post by Hankbonk on 2015-06-30
I used Google-Chrome

---

