---
title: "How to check the size of video card memory?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Olnex on 2008-05-03
if I don't know it, how do I check it?

---

### Post by overdrank on 2008-05-03
> **Olnex said:**
> if I don't know it, how do I check it?

HI and what is the model of the graphics card? Is it integrated graphics? If you use nvidia the you can use nvidia-settings. Sysinfo is also a good application for this.

---

### Post by lazyart on 2008-05-04
A little tool that I like to use-```
sudo apt-get install sysinfo
```It will show up in Applications>System Tools.  Launch Sysinfo and it should tell you what you want to know.

---

### Post by sparvik on 2009-09-25
I tried sysinfo and it only told me the name of my graphics card not the vram.  Any other way to see/change the vram or/and video driver while i'm at it?
Kubuntu 9.04
Trident onboard Video

---

### Post by cgroza on 2009-09-25
run in terminal vmstat

---

### Post by staticextasy on 2009-09-25
> **lazyart said:**
> A little tool that I like to use-```
sudo apt-get install sysinfo
```It will show up in Applications>System Tools.  Launch Sysinfo and it should tell you what you want to know.

Mmm i love me some sysinfo. Thanks Works like a charm.

---

### Post by cgroza on 2009-09-25
or there is another command lspci -vv | less and search for your video card name

---

### Post by ankspo71 on 2009-09-25
Hi, 
You could try installing hardinfo.

```
sudo apt-get install hardinfo
```

You could then run hardinfo by command, or look in your menu for "System Profiler and Benchmark".

It shows my video card memory under pci devices. 
The bad news is it reports mine as a 256mb (shared memory) card, but actually mine is a 512mb pci-e MSI/Nvidia 8400GS. nvidia-settings shows my correct memory. I hope you can find your onboard card memory specs in there too.
James

---

### Post by NightwishFan on 2009-09-25
Short answer, look up your cards model at the manufacturers website. You can find the display card using:
```
lshw -businfo | grep -i display
```

---

### Post by antharr on 2009-09-25
What about the dmidecode command?

> sudo dmidecode --type 10

---

### Post by clipod on 2012-05-01
> **ankspo71 said:**
> Hi, 
You could try installing hardinfo.

```
sudo apt-get install hardinfo
```

You could then run hardinfo by command, or look in your menu for "System Profiler and Benchmark".

It shows my video card memory under pci devices. 
The bad news is it reports mine as a 256mb (shared memory) card, but actually mine is a 512mb pci-e MSI/Nvidia 8400GS. nvidia-settings shows my correct memory. I hope you can find your onboard card memory specs in there too.
James

This is really nice.

---

### Post by oldos2er on 2012-05-01
Old thread closed.

---

