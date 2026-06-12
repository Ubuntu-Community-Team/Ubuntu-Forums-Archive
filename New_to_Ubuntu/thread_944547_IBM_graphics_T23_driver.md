---
title: "IBM graphics T23 driver"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Russ_H on 2008-10-11
Hi,

I have installed xubuntu and it seems OK on an IBM t23. The default video settings seem quite low resolution. I have tried settings manager and it only shows up to 800*600. Using the sudo lshw command shows me that the graphics card is vga: See below

   *-display UNCLAIMED
                description: VGA compatible controller
                product: SuperSavage IX/C SDR
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 05
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master 

I thought it might not have a driver and googling found one on 

[http://www.math.uakron.edu/~chad/linux_t23.html](http://www.math.uakron.edu/~chad/linux_t23.html)

It is for red hat linux,does this matter?. I tried downloading the files to desktop and running the commands but it did not work. Is this because it is for red hat only or newbie  pilot error?. Either way is there any way to increase the resolution of the screen? Thanks in advance.

Russ

---

### Post by tgalati4 on 2008-10-11
Some old thinkpads have low video memory.  Try 16-bit color.  That should allow you to get to 1024x768 which I believe is the native resolution for those old machines.

The video driver would show up as "s3" or similar.  It's not a screamer so don't expect too much.

---

### Post by Russ_H on 2008-10-12
> **tgalati4 said:**
> Some old thinkpads have low video memory.  Try 16-bit color.  That should allow you to get to 1024x768 which I believe is the native resolution for those old machines.

The video driver would show up as "s3" or similar.  It's not a screamer so don't expect too much.

It worked OK on windows,its the kids machine I am trying to wean them off windows and they are complaining!. I cannot change the colour resolution either.

---

