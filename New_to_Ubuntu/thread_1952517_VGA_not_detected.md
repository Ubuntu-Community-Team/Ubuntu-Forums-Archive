---
title: "VGA not detected"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by mazell on 2012-04-04
Hello,

I bought a new laptop and installed Ubuntu 10.04.

The laptop:
Asus p53e-SO102X
Intel Core i3 - 2330M, 2.2GHz
2GB RAM
(Delivered with Win7 Pro)

I was looking forward to using my 24"-Monitor (Samsung SyncMaster B2430) but unfortunately the screen's size is the same as on my 15,6"-Laptop-Monitor instead of the complete 24".
xrandr gave me the following output, from which I assumed that the VGA for the external Monitor wasn't detected correctly.

```
$ xrandr
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768        0.0*
```I hope somebody's got an Idea what I can do about it. I appreciate any hint. If any other information is requiered, please ask.

Best
Marcel

---

### Post by Mark Phelps on 2012-04-04
Does this work when you use Win7 Pro?  I would try that to confirm there is not a problem with the monitor connected to the vga port.

IF it does work, there may be nothing you can do in Ubuntu to fix this.

Hate to say it, but the newer the hardware, the less likely that Linux distros will have the proper drivers to support all the hardware functions.

---

### Post by mazell on 2012-04-05
Hello Mark,

I didn't try this with Win 7 Pro but I know that the Monitor works fine. I've got another (much older) laptop and if I use this one everything works great. On that other laptop I also use ubuntu 10.04.

That's really sad. But ok. Maybe I try the latest ubuntu-LTS when it's ready and if that won't work,too, I will use Win 7. (At least until I buy another laptop in a few years :shock:)

Thanks anyway for your help.
Marcel

---

### Post by Mark Phelps on 2012-04-05
It's not a question of the monitor working, the question is does it work OK when you hook it up the same way as you have in Ubuntu?  That would confirm that you're getting a video signal out the VGA port.

---

### Post by cortman on 2012-04-05
With all due respect, Mark Phelps, your post comes across as "Forget Ubuntu, just use Win7", which is a bit odd in a Linux support forum.

To the OP, let's see what hardware you have before we go abandoning Ubuntu. It could very well be that it won't work, but we can at least check.

In a terminal run

```
lspci | grep -i vga
```

and

```
sudo lshw -C video
```

Please post the output here. Thanks!

---

### Post by mazell on 2012-04-05
Hello cortman,

here are the required outputs:
```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
``````
$ sudo lshw -C video
[sudo] password for marcel: 
  *-display               
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:41 memory:ddc00000-ddffffff memory:c0000000-cfffffff ioport:e000(size=64)
```Thanks.

---

### Post by cortman on 2012-04-05
Try running

```
sudo update-pciids
```

Reboot, plug your external monitor in, and run xrandr. Post output. Thanks.

---

### Post by mazell on 2012-04-06
This is the output of xrandr after updating the pciids:
```
$ xrandr
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768        0.0* 
```

---

### Post by cortman on 2012-04-06
> **mazell said:**
> This is the output of xrandr after updating the pciids:
```
$ xrandr
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768        0.0* 
```

THEN it looks as though Mark Phelps is right, and Ubuntu won't support the VGA out. :( It's a problem I'm currently wrestling with as well on my netbook.

---

### Post by Mark Phelps on 2012-04-06
> **cortman said:**
> With all due respect, Mark Phelps, your post comes across as "Forget Ubuntu, just use Win7", which is a bit odd in a Linux support forum.

Yeah ... I reread it and it does come across somewhat defeatist.

Sorry ... not my intent to discourage folks or to put down Ubuntu.  The Ubuntu community does an amazing job of supporting what they can -- especially when you realize that nearly all of us are volunteers!

What I probably SHOULD have said is ... the newest hardware presents the most challenges to Linux distros.  With few exceptions, the hardware suppliers couldn't care less about Linux support, and like with Hybrid Graphics, waste no time developing highly specialized drivers -- which in all to many cases, aren't available for non-Windows folks.

I'm glad you were able to provide some help. 

Sorry that it didn't turn out well in the long run.

---

### Post by cortman on 2012-04-07
> **Mark Phelps said:**
> Yeah ... I reread it and it does come across somewhat defeatist.

Sorry ... not my intent to discourage folks or to put down Ubuntu.  The Ubuntu community does an amazing job of supporting what they can -- especially when you realize that nearly all of us are volunteers!

What I probably SHOULD have said is ... the newest hardware presents the most challenges to Linux distros.  With few exceptions, the hardware suppliers couldn't care less about Linux support, and like with Hybrid Graphics, waste no time developing highly specialized drivers -- which in all to many cases, aren't available for non-Windows folks.

I'm glad you were able to provide some help. 

Sorry that it didn't turn out well in the long run.

No worries, and it turned out you were RIGHT after all. Thanks for your input!

---

### Post by mazell on 2012-04-08
Hey,

thank you very much for your help.
I agree, that the community does an amazing job and I'm glad, that I at least was able to check the problem with your help. Thanks again!

Marcel

---

