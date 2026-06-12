---
title: "Wireless not working"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-08-27
I just got a new laptop today and installed Ubuntu. For some reason my wireless internet is not working. On the front of the laptop there is a little slider that turns it on or off manualy. This light is orange(off) instead of blue(on) in both positions. I cannot connect to the internet and this is bugging me. If anyone knows how to fix this it would be awesome, or if anyone has had problems before.

It is a brand new HP Pavillion dv9700t with "Intel(R) PRO/Wireless 4965AGN Network Connection"

---

### Post by Crafty Kisses on 2008-08-27
Can you post the results of this: ```
dmesg | grep
```

---

### Post by djb6 on 2008-08-27
Try this, I have the same thing with the slider and orange and blue lights.  This worked out perfectly...of course, you need to be connected to the internet to make this work, but good luck.

[http://ubuntuforums.org/showthread.php?t=769990]("http://ubuntuforums.org/showthread.php?t=769990")

Mine is an HP Presario v6000 so same brand of laptop makes me think this might help.

---

### Post by Codemastadink on 2008-08-27
> **Codename said:**
> Can you post the results of this: ```
dmesg | grep
```

```
Usage: grep[OPTION]... PATERN[FILE]...
Try 'grep --help' for more information.
```

So idk if thats right lol

---

### Post by Codemastadink on 2008-08-27
> **djb6 said:**
> Try this, I have the same thing with the slider and orange and blue lights.  This worked out perfectly...of course, you need to be connected to the internet to make this work, but good luck.

[http://ubuntuforums.org/showthread.php?t=769990]("http://ubuntuforums.org/showthread.php?t=769990")

Mine is an HP Presario v6000 so same brand of laptop makes me think this might help.

HHmm i think this is for broadcom. My wireless in Intel. I dount think it will work. Idk i may try if nothing else works

---

### Post by djb6 on 2008-08-28
Yeah I didn't see that in your post, I stopped reading it too soon :).  Who knows though, it might work.

---

### Post by Codemastadink on 2008-08-28
> **djb6 said:**
> Yeah I didn't see that in your post, I stopped reading it too soon :).  Who knows though, it might work.

Well that link u gave me says ```
Note: If the output for “lspci | grep Broadcom” is :

“03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)”

Then this tutorial will work (baring some bug or alternate configuration you have tried to set up already).
```

Mine doesnt have any output..

---

### Post by Crafty Kisses on 2008-08-28
Sorry I actually meant to post the results of:
```
dmesg | grep iw
```

---

### Post by Codemastadink on 2008-08-28
> **Codename said:**
> Sorry I actually meant to post the results of:
```
dmesg | grep iw
```

Ok it has a lot of output so i'll have to get it wired real quick so i can copy/paste it. gimme a sec

---

### Post by Crafty Kisses on 2008-08-28
> **Codemastadink said:**
> Ok it has a lot of output so i'll have to get it wired real quick so i can copy/paste it. gimme a sec

OK thanks, also just one more, sorry for all this:
```
lshw -C network
```

---

### Post by Codemastadink on 2008-08-28
```
dmesg | grep iw
```
Output:```
[   33.409866] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   33.409870] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   33.409960] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   34.812858] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   34.813738] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   71.000684] iwl4965: Radio Frequency Kill Switch is On:
[   74.606411] iwl4965: Radio Frequency Kill Switch is On:
[   87.329323] iwl4965: Radio Frequency Kill Switch is On:
[   93.496937] iwl4965: Error sending REPLY_STATISTICS_CMD: time out after 500ms.
[  107.462954] iwl4965: Radio Frequency Kill Switch is On:
[  118.586387] iwl4965: Radio Frequency Kill Switch is On:
[  132.152105] iwl4965: Error sending REPLY_STATISTICS_CMD: time out after 500ms.
[  142.383771] iwl4965: Radio Frequency Kill Switch is On:
[  148.247662] iwl4965: Radio Frequency Kill Switch is On:
[  150.286719] iwl4965: Radio disabled by HW RF Kill switch

```


> **Codename said:**
> OK thanks, also just one more, sorry for all this:
```
lshw -C network
```

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:5d:31:43
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:b9:da:71
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.2 latency=0 module=r8169 multicast=yes

```

---

### Post by Codemastadink on 2008-08-28
Anyone?....

---

### Post by Codemastadink on 2008-08-29
Please help me out if anyone can guys, i'd really like to get this working.

---

### Post by nicedude on 2008-08-29
Ok guy I did some googling using your exact mini pci adapter and found that there is a guide by someone in these forums for that exact adapter, here is the link.

[http://ubuntuforums.org/showthread.php?t=769990&highlight=BCM94311MCG](http://ubuntuforums.org/showthread.php?t=769990&highlight=BCM94311MCG)

If after looking at what the person there says to do if you can't figure this out then I will try to help you do what it says.

Please just PM me ( click on my name and select "send private message" ) if you need help so that I will know you do without checking this thead to see that you do, also it helps because if I am not in the forums I will still get an email telling me I have a PM and therefore can respond much quicker.


nicedude

---

