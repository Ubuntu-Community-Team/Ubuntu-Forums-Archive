---
title: "Unable to connect, hell I'm even unable to see connections"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Misat on 2008-11-01
Normally, back in 8.04 yesterday, I had the log off button, the volume control, the other stuff, and my connection button (the one with two computers telling me that I rock and I can tell the whole world thanks to the internet).  Now I just feel isolated and lonely.  Please help.

---

### Post by Peter09 on 2008-11-01
Wireless or wired?

---

### Post by whoelse on 2008-11-01
If it is just the icon, just right click on the panel, add an application and choose the network icon.

---

### Post by Misat on 2008-11-01
Wireless is the problem and I tried that.  I can find the network Monitor, but that's it.

---

### Post by Peter09 on 2008-11-01
In a terminal type

```
lshw -C network
```

and

```
ifconfig
```

If you can, post the output. These commands will give you an idea of how your system sees your network devices.

---

### Post by jack_harper2007 on 2008-11-01
That's too bad no one should feel lonely ;) If you don't have the sound control or (i think its called) the connections manager icons on the panel all you have to do is right click on the panel and add the icon's the option in English should be "add to panel..." or something like that  lol. The log off button has been replaced, now if you want to log off or shutdown the computer just click on your username on the panel and select the option that you want (i like it better this way) :)

But you are able connected to the internet right?

---

### Post by Misat on 2008-11-01
description: Wireless interface
product: PRE/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 02
serial: 00:19:d2:8f:0d:bb
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
*-network DISABLED
description: ethernet interface

Jesus that took a long time to type.  Sorry if I missed anything, but that's what showed up on the laptop when I did it there.

---

### Post by Misat on 2008-11-01
> **jack_harper2007 said:**
> That's too bad no one should feel lonely ;) If you don't have the sound control or (i think its called) the connections manager icons on the panel all you have to do is right click on the panel and add the icon's the option in English should be "add to panel..." or something like that  lol. The log off button has been replaced, now if you want to log off or shutdown the computer just click on your username on the panel and select the option that you want (i like it better this way) :)

But you are able connected to the internet right?

I explained poorly; the sound and all of those are still there.  The network even pops up at the beginning, but it quickly looks for wifi, finds it, fails to connect and goes off of the bar for good.  I can't find it in order to add it back.

---

### Post by Peter09 on 2008-11-01
First check that the wireless on/off switch is 'on'. That is often the case for the DISABLED flag on the wireless output.

---

### Post by Misat on 2008-11-01
> **Peter09 said:**
> First check that the wireless on/off switch is 'on'. That is often the case for the DISABLED flag on the wireless output.

I'm not quite that dumb, but I did just double check and it is on still.

---

### Post by Peter09 on 2008-11-01
Have a look at 

System->Preferences->Network Preferences

See if you can do anything in the wireless setup there.

p.s didn't mean to imply that you were dumb - just that it can happen and its worth a check

---

### Post by Martje_001 on 2008-11-01
It's called nm-applet. Try
```
nm-applet
```
in a terminal.

---

### Post by Misat on 2008-11-01
> **Peter09 said:**
> Have a look at 

System->Preferences->Network Preferences

See if you can do anything in the wireless setup there.

p.s didn't mean to imply that you were dumb - just that it can happen and its worth a check

I once spent three hours trying to get a headset to work, turned out I had the mic unplugged.  So I don't really think I am above little mistakes.

---

### Post by Misat on 2008-11-01
> **Martje_001 said:**
> It's called nm-applet. Try
```
nm-applet
```
in a terminal.

(nm-applet:6116): GLib-GObject-WARNING **: can't peek value table for type '<invalid>' which is not currently referenced
Segmentation fault

---

