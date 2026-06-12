---
title: "Printer on USB/Parallel adapter not found"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by hounddog32 on 2011-10-11
My laserjet is connected by a usb/parallel adapter cable and worked fine in Natty (and still does if I plug it into my laptop - it's not a lose cable or hardware fault). In natty, when I connect I get this on dmesg

```
[11028.538768] usb 2-1.1: new full speed USB device using ehci_hcd and address 5
[11028.970128] usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[11028.970166] usbcore: registered new interface driver usblp
[11030.185090] usb 2-1.1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[11070.556534] usb 2-1.1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
```

On Oneiric I get no more than the first line. When I try to add the printer via the "printing" dialogue or hplip it is not found, though lsusb shows the parallel port is detected.

```
Bus 002 Device 005: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
```

What should I do to add the printer?

---

### Post by dino99 on 2011-10-11
Natty is not outdated yet, so stay with it; and file a bug against this issue with oneiric.

Maybe you can find some thread(s) related to your laserjet model with Oneiric. (oneiric+model)

---

### Post by nomko on 2011-10-11
> **dino99 said:**
> Natty is not outdated yet, so stay with it; and file a bug against this issue with oneiric.
 
Maybe you can find some thread(s) related to your laserjet model with Oneiric. (oneiric+model)
 
It's not said that the problem is Oneiric or Natty. It can also be that the printer (Laserjet) is not supported anymore or wasn't supported by CUPS/HPLIP.
 
At the topicstarter: What type of Laserjet you have??

---

### Post by hounddog32 on 2011-10-11
It's a LaserJet 1100. I wasn't planning on downgrading having gone through the process to upgrade - 11.10 looks good, this is the only problem I've found. Searching was my first stop and hasn't thrown up anything helpful - if you have better search-fu than me, do link to anything that might help me.

---

### Post by nomko on 2011-10-11
> **hounddog32 said:**
> It's a LaserJet 1100. I wasn't planning on downgrading having gone through the process to upgrade - 11.10 looks good, this is the only problem I've found. Searching was my first stop and hasn't thrown up anything helpful - if you have better search-fu than me, do link to anything that might help me.
 
Take a good look at here: [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1100.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1100.html).

---

### Post by hounddog32 on 2011-10-11
Sorry, I don't understand what I should see there, other than that I can try hplip - which I have and it doesn't find the printer as a USB or parallel printer.
[edit] Also that the printer is no longer supported by HP - though it should install automatically in 11.10.

---

### Post by dino99 on 2011-10-11
the issue might be related to the actual oneiric hplip package. As it is working with natty, recompiling the natty hplip source under oneiric might be the solution.

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1100.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1100.html)
( your laserjet hplip support: end of support)

---

### Post by hounddog32 on 2011-10-11
Seems like it's this bug [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/842823](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/842823) - I'll see if I can get some help there as well.

---

### Post by hounddog32 on 2011-10-11
So based on that, I have a solution that seems to have worked (though I've not restarted, we'll see if it lasts...)

```
sudo modprobe usblp
```

usblp has been deprecated, but putting it back in creates /dev/usblp0, which can then be put in as a URI in the printing settings. The printer is still not auto-detected, but at least it works. I directly typed in the URI into the 'Add printer' dialogue of ```
parallel:/dev/usblp0
```, then selected the correct make and model from the lists - the test page worked. It's a clumsy hack to replace functionality that has been removed.

---

