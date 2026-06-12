---
title: "Terminal Command to view Graphics Driver"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by RussW210 on 2008-10-07
Hello everyone,

Is there a terminal command I can type in Ubuntu Hardy to view which current graphics driver I am using?  I have been having problems with my ATI Accelerated Graphics Driver... particularly I can't view things like Google Earth or play games like Super Tux Kart because the screen will either freeze or glitch.  Super Tux Kart is weird because whenever I put my mouse over it the window freezes and the music turns off.

I want to find out which graphics driver I am currently using so I can look at other available drivers.

FYI, I am using an ATI Radeon HD 2400 graphics card.

---

### Post by pieisgood4589 on 2008-10-07
You don't need to use terminal-
There's a system tool called sysinfo. If you don't have it you can install it via add/remove applications. That will show you all your hardware. And in system - administration you can find Hardware Drivers.

Maybe you could try "fglrxinfo" in the terminal, but it sometimes just says "Command not found."

---

### Post by RussW210 on 2008-10-07
OK, I installed sysinfo and went to the hardware tab then selected "graphic card"... everything came up blank.

fglrxinfo just told me the type of Graphics card I am using, not the graphics driver.

---

### Post by RussW210 on 2008-10-07
Also, when I go to system - administration - hardware drivers, all it says is "ATI accelerated graphics driver" but it doesn't give me a version number.

---

### Post by RideBMX on 2008-10-07
You can try ```
sudo lshw -c display
```

---

### Post by RussW210 on 2008-10-07
Hmm, that didn't work.  All that spit out was:

> Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


---

### Post by RussW210 on 2008-10-07
My friend actually recommended I try lspci and it gave me (amongst other things):

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

Is "RV610 video device" the name/model number of my graphics driver?

---

### Post by Tatty on 2008-10-07
lsmod will list all the kernel modules which are currently loaded.  You can then simply pipe this to grep to try looking for drivers.  

For example, on my machine I have a nvidia card, to check if the proprietry nvidia driver is loaded:
```
lsmod | grep nvidia
nvidia               8115088  26 
i2c_core               28544  2 nvidia,i2c_nforce2
```

So yes the proprietry nvidia driver is loaded in this case.


I dont know of a more elegant way of doing this, though I would be keen to find one.

---

### Post by mlnoone on 2010-01-11
This worked for me ```
hwinfo -gfxcard
``` Check the "Driver Info" section in the output.

---

### Post by nerdy_kid on 2010-01-11
lspci -k
will do it

---

### Post by philinux on 2010-01-11
> **RussW210 said:**
> Hello everyone,

Is there a terminal command I can type in Ubuntu Hardy to view which current graphics driver I am using?  I have been having problems with my ATI Accelerated Graphics Driver... particularly I can't view things like Google Earth or play games like Super Tux Kart because the screen will either freeze or glitch.  Super Tux Kart is weird because whenever I put my mouse over it the window freezes and the music turns off.

I want to find out which graphics driver I am currently using so I can look at other available drivers.

FYI, I am using an ATI Radeon HD 2400 graphics card.

Install the gui app hardinfo, [apt:hardinfo]("apt:hardinfo").

The menu item appears in apps>system tools as System profiler and Benchmark. Then choose the Display tab. Really useful app.

---

