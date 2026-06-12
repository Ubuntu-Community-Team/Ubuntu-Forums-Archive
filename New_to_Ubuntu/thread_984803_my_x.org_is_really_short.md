---
title: "my x.org is really short"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by holdie on 2008-11-17
My x-org is really short, I'm trying to figure out what video driver I'm using, but there are like only three entries in Xorg, none of which deal with the video driver...what gives?

---

### Post by handydan918 on 2008-11-17
> **holdie said:**
> My x-org is really short, I'm trying to figure out what video driver I'm using, but there are like only three entries in Xorg, none of which deal with the video driver...what gives?

I feel your pain.
ever since xorg 7.3 came out, I've been suffering from xorg envy.

---

### Post by baeksu on 2008-11-17
The current version of X is pretty good at automatically figuring out things, hence the short xorg.conf. You can still add options there, though.

To see what your X is doing, check out the log file it makes, usually /var/log/Xorg.0.log.

---

### Post by holdie on 2008-11-17
yeah, it automatically works great except for when I try to do anything other than just my normal screen with 2D graphics...still not detecting my TV with an S-video cable, still can't do 3D graphics (and the proprietary driver crashes my computer)...

I at least used to have a nice, big xorg file where I could mess around and further destroy my computer but at least I was pissed at myself and not ubuntu for my woes

---

### Post by starcannon on 2008-11-17
> **holdie said:**
> My x-org is really short, I'm trying to figure out what video driver I'm using, but there are like only three entries in Xorg, none of which deal with the video driver...what gives?

Section "Device" 
is always where your driver goes.

What video card do you have?
```
sudo lshw -C display
```
If you need a proprietary driver, first attempt to use the hardware driver utility:
System>Administration>Hardware Drivers

If you don't succeed at that, then we work from there.

---

### Post by holdie on 2008-11-17
display UNCLAIMED     
       description: VGA compatible controller
       product: M22 [Mobility Radeon X300]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

this is the result of what you suggested I type in...I don't see anything that says what my driver is (specifically if I'm using the open source or proprietary driver)...

Also, I've used the proprietary driver with ibex, it just seems that it is relatively unstable or incompatible with some of the things I want to do (such as use an S-video to connect to a TV)

---

