---
title: "Compiz closing"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by NDW57 on 2012-12-30
Hi, quite frequently my computer has a little "fit" and then I get a dialogue box saying that "compiz" has "closed unexpectedly". I am given the option of relaunching it or continuing - I normally leave it closed. The PC seems to run perfectly well then but obviously this is a little worrying. Should I deal with this and if so how?
The PC is a Packard Bell that used to have a (very corrupt and virus ridden) version of Windows Vista. 2x2Ghz processor (dual core), 160 GB hard drive and 3.7 GB RAM (used to have only 750mB RAM but I upgraded it with 2x2 GB chips). Ubuntu 12.04
Thanks.

---

### Post by vanadium on 2012-12-30
This appears to be compiz crashing, then automatically relaunching despite the dialog - otherwise, you could not continue working normally. Troubleshooting and eventually selectively disabling compiz plugins will not be easy. You may want to switch to Unity 2D, which does not rely on compiz, at the expense of some visual effects.

---

### Post by audiomick on 2012-12-30
I think it might be useful to know what graphics card is on there.

Do
```
sudo lshw -C video
```

in a terminal and post the output here.

---

### Post by NDW57 on 2012-12-30
Ran the command above :


 *-display               
       description: VGA compatible controller
       product: C73 [GeForce 7050 / nForce 610i]
       vendor: NVIDIA Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:23 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:feac0000-feadffff

Is that of any help ?

---

### Post by vanadium on 2012-12-30
This looks like your problem:[https://answers.launchpad.net/ubuntu/+source/compiz/+question/194996](https://answers.launchpad.net/ubuntu/+source/compiz/+question/194996)

A "downgrade" of the driver helped there (see the two last posts). This post was from june, so in the mean time, an upgrade may be the way to go. Someoe owning an nvidia card my help out more specifically.

---

### Post by audiomick on 2012-12-30
Ok, nVidia and it looks like you have installed the nVidia driver.

I'm not really sure what to do next. One thing I might try myself is to see if the additional driver application a different nVidia driver offers and maybe try that. I don't know that this would help, though. I hope that someone else has some better advice...

---

