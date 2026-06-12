---
title: "A few questions"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by SimplySerenity on 2012-11-09
So I'm very new here, just installed a dual boot of ubuntu 12.10 a couple of hours ago. Things are kind of off to a rocky start, and I have a few questions. 

My first question is why is it that my graphics card, or the driver isn't recognized? Under the details of my settings it says "Graphics: unknown" and my driver is also unknown. Is this a problem? I was having some graphical artifacts after the install, so I installed the proprietary driver from nvidia, and now that has been resolved.

My second question is about installing skype. I'm having the same issues as in this thread here [http://ubuntuforums.org/showthread.php?t=2075090](http://ubuntuforums.org/showthread.php?t=2075090). I have not been able to resolve it so far. 

Any help is greatly appreciated. ^^

---

### Post by papibe on 2012-11-09
Hi SimplySerenity. Welcome to the forums ):P

Could you post the results of these commands?
```
sudo lshw -C display

lspci -nnk | grep -i vga
```
Regards.

---

### Post by SimplySerenity on 2012-11-09
The first command
```
-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fa000000-fbffffff memory:f0000000-f7ffffff memory:ec000000-efffffff ioport:ec00(size=128) memory:f9f80000-f9ffffff

```

The second
```
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1559]
    Subsystem: eVga.com. Corp. Device [3842:1559]

```

---

### Post by papibe on 2012-11-09
Thanks, it looks that the Nvidia proprietary driver is installed and working.

As for Skype, there's a much simpler way to install it. Take a look at this instructions: [Install Skype]("http://askubuntu.com/questions/7498/how-do-i-install-skype").

Let us know how it goes.
Regards.

---

### Post by grahammechanical on 2012-11-09
> Under the details of my settings it says "Graphics: unknown" and my driver is also unknown. Is this a problem

No. It is not a problem. The Details page works with the open source video driver (Nouveau) sometimes but never with a proprietary driver in my experience since this Details feature was introduced about a year ago.

Regards.

---

### Post by SimplySerenity on 2012-11-09
Got the same error as before.  

```
The following packages have unmet dependencies:

skype: Depends: skype-bin but it is not going to be installed

```

---

### Post by SimplySerenity on 2012-11-09
Ah okay, thanks for the info on that grahammechanical.

---

### Post by SimplySerenity on 2012-11-09
Solved the skype problem after searching around on the forums some more! Thanks for the help guys.

---

