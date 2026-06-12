---
title: "Intel Wireless WiFi 4965"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by urk_nono on 2008-08-26
Hello!

I've recently installed 8.04 on my new HP Pavilion dv5-1095. Now I can't get my wireless to work. 

I've tried to install iwlwifi, but it was too complicated. Then I tried to follow [this guide]("http://ubuntuforums.org/showthread.php?t=766887"), using the windows drivers, but still no luck!

$ iwconfig

[HTML]lo        no wireless extensions.

eth0      no wireless extensions.[/HTML]

$ iwlist wlan0 scan

[HTML]wlan0     Interface doesn't support scanning.[/HTML]


Does anyone have a word of advice?

---

### Post by urk_nono on 2008-08-26
Hello!

I've recently installed 8.04 on my new HP Pavilion dv5-1095. Now I can't get my wireless to work. 

I've tried to install iwlwifi, but it was too complicated. Then I tried to follow [this guide]("http://ubuntuforums.org/showthread.php?t=766887"), using the windows drivers, but still no luck!

$ iwconfig
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.[/HTML]

$ iwlist wlan0 scan
[HTML]wlan0     Interface doesn't support scanning.[/HTML]


Does anyone have a word of advice?

---

### Post by Tom--d on 2008-08-26
Try this
```
sudo modprobe iwl4965
```

I think (correct my if im wrong) thats the driver for the wireless card.
Once done that, does wireless work?

---

### Post by urk_nono on 2008-08-26
uhm, no :(

---

### Post by jruden on 2008-08-26
hi urk_noko, I just bought the same laptop and have the same problem. I am quite into networking but this is my first laptop. According to the specs the dv5-1095 does have the Intel 4965 wireless controller.

Reading: [https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

I tried:

```
sudo lshw -C network
```

the result is:
*-network UNCLAIMED
     description: Network controller
     product: Intel Corporation
     vendor: Intel Corporation
     physical id: 0
     bus info: pci@0000:02:00.0
     version: 00
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: latency=0

...and then there is an entry for the Ethernet interface (wired).

One thing I also noted was that the lamp indicator is glowing amber, not blue like the other indicators (sound, etc..). Does this mean its off? I recon this one is software controlled cause I can't find a button or function key combination to switch it on.

Any ideas anybody?

---

### Post by jruden on 2008-08-26
The more i read, the more I am starting to believe that it may just be that the wireless controller is deactivated. The question is how to activate it when there button on the laptop case is not working (no drivers for these).

---

### Post by urk_nono on 2008-08-26
Ah! Good point! I wasn't even thinking about turning it on, just trying to find a driver. I'm not a huge fan of opening up laptops in order to flip a switch. There has to be an easier way?

---

### Post by jruden on 2008-08-28
Don't think it is necessary with any switches. It seems to be that the hardware is newer than the included driver. There are at least 3 different 4965 if you look at the PCI device id! Please see the following thread for more discussions about this problem:

[http://ubuntuforums.org/showthread.php?p=5679188#post5679188](http://ubuntuforums.org/showthread.php?p=5679188#post5679188)

---

### Post by huba! on 2008-08-31
i'm having the same prob on my dv5-1040ez... my guess is that the touch sensitive button to turn the wireless on/off is the cause of the problem. this button is not working in ubuntu out of the box and by default, the wlan is disabled. thus, the card is not detected and even using the right driver is of no help. does anybody know how to solve this?

---

