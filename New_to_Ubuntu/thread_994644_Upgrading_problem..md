---
title: "Upgrading problem."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by sarum on 2008-11-26
Hello, I have used 7.10 for sometime now. I tried 8.10, but couldn't alter the screen resolution. My hard drive needs to be replaced and I've lost the 7.10CD so I bought another one; but it will not come up on the monitor:-
'Cannot Display this Video Mode'
So I found a CD of 6.10; it worked, and I installed it. So far so good; but I cannot get it to upgrade to 7.10. It tries but says there may be something wrong with the 'net connection and a lot of error 404. I'm on the internet as I type now, and I'm wondering if 6.10 is too out of date to upgrade.
My monitor is a flat screen Dell and was a cheap 2nd hand one, but it certainly worked OK when I installed 7.10(?Dapper) a year ago. I'd be grateful for any help with this.
Also any help on an alternative. Is it possible to transfer the OS to the new Hard Drive. Thanks in advance.......sarum

---

### Post by nhasian on 2008-11-26
If you starting anew, you should install 8.10.  we can help you fix the resolution once its installed if it does not use the correct video driver.  can we get the specs of your computer to make sure you meet the minimum requirements for Ubuntu 8.10?

```
lshw -C memory,cpu,display
```

---

### Post by sarum on 2008-11-27
Thankyou for such a rapid reply, and a useful command to remember. Herewith the result:-
 *-firmware              
       description: BIOS
       vendor: Intel Corp.
       physical id: 0
       version: EA81510A.86A.0031.P07.0009211842 (09/21/2000)
       size: 64KB
       capacity: 448KB
       capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
  *-cpu
       description: CPU
       product: Pentium III (Coppermine)
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.8.3
       slot: J4L1
       size: 733MHz
       capacity: 733MHz
       width: 32 bits
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
     *-cache:0
          description: L1 cache
          physical id: 5
          slot: None
          size: 32KB
          capacity: 32KB
          clock: 25MHz (40ns)
          capabilities: pipeline-burst synchronous internal write-back unified
     *-cache:1
          description: L2 cache
          physical id: 6
          slot: None
          size: 256KB
          capacity: 256KB
          capabilities: synchronous internal write-back unified
  *-memory
       description: System Memory
       physical id: 2f
       slot: System board or motherboard
       size: 512MB
     *-bank:0
          description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
          physical id: 0
          slot: DIMM1
          size: 256MB
          width: 64 bits
          clock: 133MHz (7.5188ns)
     *-bank:1
          description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
          physical id: 1
          slot: DIMM2
          size: 256MB
          width: 64 bits
          clock: 133MHz (7.5188ns)
     *-bank:2
          description: [empty]
          physical id: 2
          slot: DIMM3
  *-display
       description: VGA compatible controller
       product: 82815 CGC [Chipset Graphics Controller]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@00:02.0
       version: 02
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=i810_smbus
       resources: iomemory:f8000000-fbffffff iomemory:ffa80000-ffafffff irq:11. Hope this helps, and many thanks again.....sarum

---

### Post by nhasian on 2008-11-28
looks like you just barely passed the recommended requirements for ubuntu 8.10 :)

So after you do a fresh install of Ubuntu 8.10 you can get to the desktop right?  you just need to adjust the resolution?

---

### Post by sarum on 2008-11-28
Thanks nhasian, the problem seems to be the computer, if its on the border line as you suggest. I bought it secondhand a couple of years ago, and intend to stay with the LT issues of Ubuntu. So my thanks for the excuse for an upgrade....cheers sarum

---

