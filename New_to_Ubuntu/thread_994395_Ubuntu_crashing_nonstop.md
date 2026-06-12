---
title: "Ubuntu crashing nonstop"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by compaqowner on 2008-11-26
Hi, I am new to ubuntu. I have a compaq PC, with AMD 3400 Athlon 64bit Processor.  After I installed ubuntu, the system keeps on crashing. The screen would basically freeze, and I would have to power down to reboot.  Is this a hardware issue? I do have 800 mgs of memory.  Can anyone refer me to a diagnostic program to find out if this is in fact a hardware issue or software problem? Thanks.

---

### Post by rhcm123 on 2008-11-26
> **compaqowner said:**
> Hi, I am new to ubuntu. I have a compaq PC, with AMD 3400 Athlon 64bit Processor.  After I installed ubuntu, the system keeps on crashing. The screen would basically freeze, and I would have to power down to reboot.  Is this a hardware issue? I do have 800 mgs of memory.  Can anyone refer me to a diagnostic program to find out if this is in fact a hardware issue or software problem? Thanks.

be sure you downloaded the correct version? Did you download the 32 or 64 bit, and x64 or i386 version?

---

### Post by compaqowner on 2008-11-26
Acutally I am not sure.  I did not know there are different versions. I will download the 64 bit version and start over.  Can I just install over the previous version?

When I checked my version info it says 8.10, intrepid. I did not modify the box for 32 bit or 64 bit version, so I believe I downloaded the 32 bit version by default.  How do I reinstall the 64 bit version over the 32 bit version, thanks.

---

### Post by Olivier2371 on 2008-11-26
Sorry to drop in, 

What is the model of your graphic card?

And yes if you wanted to reinstall Ubuntu you could just reinstall it on top, using the same partitions. Only If you have no documents you want to keep.

---

### Post by halitech on 2008-11-26
before you go and reinstall (which may or may not fix the issue) boot from your cd and select the memtest86+ option and let it test your ram. It might be a bad stick which will not be helped by reinstalling.

---

### Post by compaqowner on 2008-11-26
I checked my hardware profile and it says Sis70. Honestly I don't know what type of graphics card came w/the computer, but it is a compaq presario AMD Athlon 64, +3400, w/1G Ram, and 200G harddrive. I've downloaded ubuntu 8.10 for amd64 and I will run the memtest from the CD first.

---

### Post by halitech on 2008-11-26
if  you open a terminal and type in
```
lshw -C video
```
it will give you the type of video card you have.

---

