---
title: "applets turning upside down"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by shemdroid on 2011-12-18
ok i have a toshiba satellite walmart special laptop. completely wiped and repartitioned the drive and installed ubuntu 10.04 then updated to 10.10. . 
i installed KDE and GNOME 3.  up to this point all is well then a proprietary ATI grapgics card driver. this is when things started getting funny! 
first thing i noticed was  the window borders were all scrambly then every applet i would open would flip upside down when i tried to use it. 
this was on the gnome3, the default ubunu desktop had a few issues but they cleared up after a reboot. kde had no problems at all.
should i uninstall gnome3 if so how? a lil help please :)

---

### Post by shemdroid on 2011-12-19
yes  im a super noob!

---

### Post by flemur13013 on 2011-12-19
try 

```
sudo synaptic
```and search for "gnome", and perhaps re-install the appropriate package(s) you have installed. (Rt-click on the package name).  Click the left-most column title (looks like $ or up/down arrow) to put installed ones at the top.

Be careful of "Remove" or "Complete Removal" followed by "install".

Edit: it sounds like the prop. driver is the problem, not gnome, but maybe gnome will behave better if (re)installed after the driver.

---

### Post by Seq on 2011-12-19
A screenshot of the 'upside down' issue would help. Pressing the 'Print Screen' button when in Gnome should prompt to save a screenshot (hopefully that dialog will be usable)

---

### Post by shemdroid on 2011-12-20
> **flemur13013 said:**
> try 

```
sudo synaptic
```and search for "gnome", and perhaps re-install the appropriate package(s) you have installed. (Rt-click on the package name).  Click the left-most column title (looks like $ or up/down arrow) to put installed ones at the top.

Be careful of "Remove" or "Complete Removal" followed by "install".

Edit: it sounds like the prop. driver is the problem, not gnome, but maybe gnome will behave better if (re)installed after the driver.


 i dont think the screenshot button worked. where does it save to? i tried hitting it then ctrl-v onto an office doc. 
 i tried reinstalling first just the gnome3 session pkg, then i reinstalled ALL gnome pkgs. both efforts to no avail! 
the whole window will actually turn upsidedown some of the time or just the icons inside the window will turn usd. sometimes all of the icons sometimes just like half of them and sometimes just the one my mouse pointer is on. 
sometimes it almost seems as if the usd is following the pointer but its too inconsistant to say that it is.

---

### Post by Ms. Daisy on 2011-12-20
I'll have to pose this question to more experienced folks out there, but could this be a graphics card problem- his graphics card doesn't meet the minimum requirements?  I had similar issues and had to install an upgraded graphics card to display Ubuntu properly.

---

### Post by shemdroid on 2011-12-20
well ivwouldnt think so  i mean it is only a year old but now that you mention it i havent been able to install any version of linux except ubuntu10.04 without issues. fedora16 boots riht up on my old desktop but wont do squat on the laptop. mint12 will install but freezes up constantly.

---

### Post by Ms. Daisy on 2011-12-20
So if the machine is only a year old, it's more likely to be a lack of drivers instead of an outdated graphics card (like flemur13013 mentioned).  This is out of my limited realm of expertise I'm afraid, so hopefully others can give you guidance as to how to find the appropriate drivers.

I do know it would make it easier to know exactly what graphics card is installed. 
```
sudo lshw
``` will give you the details.

---

### Post by shemdroid on 2011-12-20
thanx, ill check that out when i get home.  
im not sure how i neglected to mention this previously but in the lower right hand corner there is a approx: 2"x2" square that says; " AMD not supported hardware".    
sorry if that was crucial information that i left out. i get a lil excited about certain things...... computer and phone glitches are among these lol. yet i still persist on messing with the inner workings of such things ;)

---

### Post by QIII on 2011-12-20
It seems a bit odd that KDE would work, but other DEs would not.

Anyway, your last tidbit of information is valuable.  There are scads of posts regarding the AMD watermark.

Can you give us a little info about the machine specs?

Does it run on an APU or a CPU with integrated graphics on the motherboard?

---

### Post by shemdroid on 2011-12-20
p { margin-bottom: 0.08in; }  i know this is alot of txt but...................
 


description: Notebook 
     product: Satellite C655D 
     vendor: TOSHIBA 
     version: PSC0YU-001001 
     serial: ZA280250Q 
     width: 32 bits 
     capabilities: smbios-2.7 dmi-2.7 
     configuration: boot=normal chassis=notebook uuid=89B2D6D0-0A08-11E0-B541-00266C9D8A0E 
   [SIZE=4]***-core **[/SIZE]
  description: Motherboard 
        product: Portable PC 
        vendor: TOSHIBA 
        physical id: 0 
        version: Base Board Version 
        serial: Base Board Serial Number 
        slot: Base Board Chassis Location
 [SIZE=4]***-firmware **[/SIZE]
           description: BIOS 
           vendor: Insyde Corp. 
           physical id: 0 
           version: 1.30 (12/07/2010) 
           size: 64KiB 
           capacity: 1984KiB 
           capabilities: pci pnp upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi usb              agp ls120boot smartbattery biosbootspecification netboot 
  [SIZE=4]***-memory**[/SIZE] 
           description: System Memory 
           physical id: 8 
           slot: System board or motherboard 
           size: 3GiB 
    [SIZE=4]***-bank:0 **[/SIZE]
              description: SODIMM Synchronous 1066 MHz (0.9 ns) 
              product: M471B2873FHS-CH9 
              vendor: Samsung 
              physical id: 0 
              serial: 86FAEEBD 
              slot: DIMM0 
              size: 1GiB 
              width: 8 bits 
              clock: 1066MHz (0.9ns) 
 [SIZE=4]***-cpu **[/SIZE]
           description: CPU 
           product: AMD E-240 Processor 
           vendor: Advanced Micro Devices [AMD] 
           physical id: 14 
           bus info: cpu@0 
           version: 15.1.0 
           serial: NotSupport 
           slot: Socket FT1 
           size: 1500MHz 
           capacity: 1500MHz 
           width: 64 bits 
           clock: 100MHz 
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc up nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save cpufreq 
         [SIZE=4]***-cache:0 **[/SIZE]
              description: L1 cache 
              physical id: 15 
              slot: L1 Cache 
              size: 64KiB 
              capacity: 64KiB 
              capabilities: pipeline-burst internal write-back unified 
         [SIZE=4]***-cache:1 **[/SIZE]
              description: L2 cache 
              physical id: 16 
              slot: L2 Cache 
              size: 512KiB 
              capacity: 512KiB 
              capabilities: pipeline-burst internal write-back unified 
  [SIZE=4]***-display **[/SIZE]
              description: VGA compatible controller 
              product: ATI Technologies Inc 
              vendor: ATI Technologies Inc 
              physical id: 1 
              bus info: pci@0000:00:01.0 
              version: 00 
              width: 32 bits 
              clock: 33MHz 
              capabilities: pm pciexpress msi vga_controller bus_master cap_list rom 
              configuration: driver=fglrx_pci latency=0 
              resources: irq:43 memory:c0000000-cfffffff ioport:4000(size=256) memory:d0300000-d033fff 

honestly i would just use KDE if it wasnt completely disorganized

---

### Post by QIII on 2011-12-20
I wouldn't say disorganized.  Differently organized.  Having some trouble with my cell right now, so I'll check in later.  I think this is simply a matter of current driver.

---

### Post by shemdroid on 2011-12-20
kk........    i cant seem to find anything in kde lol  i really really like the de in fedora16 which i believe is gnome3 i which is why i wanted it on my ubuntu lol    any help you can give me with my driver issue would be greatly appreciated :D

---

### Post by shemdroid on 2011-12-21
i have searched around a bit and checked toshibas support pages for a driver with no luck

---

