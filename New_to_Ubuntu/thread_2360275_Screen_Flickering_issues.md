---
title: "Screen Flickering issues"
date: 2017-05-02
forum: New to Ubuntu
---

### Post by jquit on 2017-05-02
Hi All,

My screen flickers like crazy when I'm not moving my mouse. I was wondering how I can start diagnosing/fixing the problem? I installed ubuntu `16.04 just today.

Thanks

---

### Post by Bucky Ball on 2017-05-03
Welcome. Did you install a driver for your video card? You might not need one, but open a terminal and post the output of this command, please.

```
sudo lshw -C video
```

You will be asked for your password. Use the one you use to log in to Ubuntu. When you type it, it will be invisible. This is normal.

How are you connecting to the screen, HDMI or otherwise? How old is the monitor?

---

### Post by jquit on 2017-05-03
Hi, 

Thanks for your reply. I tried the command in terminal and my screen is still flickering. The following appeared when I ran that in the terminal:

  *-display UNCLAIMED     
       description: 3D controller
       product: GM108M [GeForce 940M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:a0000000-a0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:4000(size=128) memory:a1000000-a107ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:a1400000-a17fffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff

I'm using a laptop screen.

---

### Post by Geoffrey_Arndt on 2017-05-03
The command was not supposed to fix the screen flickering, but is intended just to show some key details about your system.     "I'm using a laptop screen" is not helpful (as there are thousands of different types of laptops along with their graphics systems).

The key question is still:   have you used the "additional drivers" tool to install the nvidia drivers (using the top icon in the launcher - search for "additional drivers").

---

### Post by jquit on 2017-05-06
Hello,

I used the "Additional drivers" tool and installed the nvidia binary driver. I then encountered the following errors:

[http://imgur.com/a/CkShe](http://imgur.com/a/CkShe)

First picture is the first screen.

Second picture contains various options, if I click on any of them and go through the prompts, it goes to a black screen after and I have to hard reset my computer.

Looking for guidance after this step. How do I revert back to my older version? I can't even get into ubuntu right now.

---

### Post by mörgæs on 2017-05-06
Do you have anything of value on the hard disk? If not then I suggest that you do a fresh install of 17.04, erasing everything in the process.

---

### Post by Bucky Ball on 2017-05-06
> **mörgæs said:**
> Do you have anything of value on the hard disk? If not then I suggest that you do a fresh install of 17.04, erasing everything in the process.

Just curious as to why. As far as I know, that card works in 16.04. Perhaps user wants LTS rather than a nine month release. :-k ;)

---

### Post by mörgæs on 2017-05-06
To try the version with the most advanced hardware support. 

As of now it doesn't seem to work in 16.04, neither with open nor closed source drivers.

---

### Post by Geoffrey_Arndt on 2017-05-06
I'm an avid Ubuntu supporter, but right now Arch, Antergos and Solus seem to have a much better handle on using the latest gpu technologies (for multiple reasons).

Solus - after snapshot of 04/18/17 has built in Optimus support for these laptops.   If I had that machine, which was/is clearly designed to run only via Win10, I would consider downloading the latest Solus and giving it a shot.   Here is more detailed info:   [https://solus-project.com/forums/viewtopic.php?f=21&t=4828](https://solus-project.com/forums/viewtopic.php?f=21&t=4828)

And to the OP - - in future, would highly recommend you provide "detailed" hardware specs and your "change management" history in the first post of a thread like this, so the Forum Members have at least a chance to correctly diagnose the problem and offer a solution.   This "change management" history is how did you install Ubuntu in the first place, what changes did you make to the system (is it a dual-boot or single boot, etc.)

---

