---
title: "Wireless Adapter slow or drops"
date: 2016-02-07
forum: New to Ubuntu
---

### Post by Edmondo83 on 2016-02-07
Hello,

I am a total Linux novice, I have a Dell Latitude, when it had Windows XP on it the wireless adapter was a bit flaky, I installed Ubuntu 15 on a brand new SSD and the wi-fi card is still awful which does lead me to believe that there is a problem with the adapter. After running a few commands I discovered I have a Broadcom NetXtreme card which I have done some googling but I still cant get a stable connection on the adapter.

Other devices on my home wi-fi are getting about 20Mbps, but this device only ever gets 1 to 2 Mbps, does anyone have any thoughts on what could solve this? 

Many thanks

---

### Post by Rob Sayer on 2016-02-07
Not enough info.  Copy/paste into the terminal:

sudo lshw -C video

And

lspci -nn -d 14e4:

And copy/paste the output from the terminal here, wrapped in Code tags.

They will show the actual wireless card model and driver in use.

You may want to read the first answer here:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by Edmondo83 on 2016-02-07
Hello, 

Thanks for your input, I have viewed this article already, the Firmware I have isnt listed in that article but here is the output:

>   *-display:0                    description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:f6e00000-f6efffff memory:e0000000-efffffff ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6f00000-f6ffffff




> 09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)

Many thanks for your input.

---

### Post by Geoffrey_Arndt on 2016-02-08
See here:

[http://ubuntuforums.org/showthread.php?t=2312818](http://ubuntuforums.org/showthread.php?t=2312818)

---

### Post by mr-tin-man on 2016-02-08
Don't know if it would help you, but there is a real reasonable usb wifi dongle you can order from Walmart called "Edimax" for $10.77  I've got one and it works great.  My Ubuntu recognized it right off, no hassle.  Here is the link with the info: [http://www.walmart.com/search/?query=edimax%20wifi%20150](http://www.walmart.com/search/?query=edimax%20wifi%20150).


mr-tin-man

---

