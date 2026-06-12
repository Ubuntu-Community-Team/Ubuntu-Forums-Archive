---
title: "Will NOT boot up."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Sexraider on 2008-10-25
Hello, Still having the same issue I was having 6 months ago.

I'll order the new Ubuntu disc. I'll insert it. Install, but when it gets to the screen oading up everything (booting for the first time) It'll freeze up and not move. I don't know how to resolve this.

**Specs:**
Intel(R) Celeron(R) 2.0 GHZ 640mb ram.

Any solutions?

---

### Post by cantormath on 2008-10-25
when booting up, press alt+f2 during splash and see what it says.  Any errors?

---

### Post by Sexraider on 2008-10-25
Let me try it and I'll reply here.

---

### Post by Sexraider on 2008-10-25
Interesting. I have it installed and working!

But one question... How to get my Wireless box to work...

I have a Linksys Wireless - G 802.11g Box.

Anywhere to find drivers / whatever to install?

---

### Post by dracayr on 2008-10-25
have you searched the forums? there are very, very many topics about wireless lan...

dracayr

---

### Post by Sexraider on 2008-10-25
Yes I have.

I cannot find a topic that will get my Adapter running <__<

---

### Post by dracayr on 2008-10-25
I found a blog that states that 802.11g should work without further tweaking. Execute 

iwconfig

in a terminal and post the output

dracayr

---

### Post by Sexraider on 2008-10-25
```
syrex@syrex-desktop:~$ iwconfig
lo   no wireless extensions

rausb0   rt2500usb wlan essid: ""
         mode: managed  frequency = 2.412 GHz
         RTS thr: off  fragment thr: off
         link quality= 0/70  signal level:- 120 dBm 
nose level:- 256 dBm
         Rx invalid nwid: 0 Rx invalid crypto: 0 Rx Invalid
frag: 0
         Tx excessive retries: 0 Invalid misc: 0 missed beacon: 0

eth0   No wireless extensions

sit0   No wireless extensions
```

I'm not seeing the problem. I have my box plugged it. The lights on the box are lit up as well.

---

### Post by dracayr on 2008-10-25
iwlist scan rausb0

dracayr

---

### Post by Sexraider on 2008-10-25
> **dracayr said:**
> iwlist scan rausb0

dracayr

I did sudo ifup rausb0

it says
```
password:
ignoring unknown interface rausb0=rausb0
```

and when i did iwlist scan it said

```

lo Interface doesn't support scanning

rausb0 No scan results

eth0 Interface doesn't support scanning

sit0 Interface doesn't support scanning 
```

I don't know what I'm doing wrong =/

---

### Post by dracayr on 2008-10-25
note that it says rausb0 No scan results. this means that it is apparently scanning, but not finding any networks. Are you sure you are somewhere near an Access point? (access point = router/device that sends the wlan signals)

dracayr

---

### Post by Sexraider on 2008-10-25
Yes, I installed Ubuntu on to my home desktop. When I login to my windows, My internet works just fine, when I boot up Ubuntu it won't find it according to you.

---

### Post by dracayr on 2008-10-25
well I'm no wireless expert. Maybe you should post in the Networking&wireless forum or get a mod to move the topic there :P

---

### Post by Sexraider on 2008-10-25
Alrighty,
Thanks.

---

