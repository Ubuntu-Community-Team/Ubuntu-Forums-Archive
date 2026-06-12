---
title: "Need help with USB printer and CUPS - requires physical reset for each job!"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by amberluvsit on 2013-07-03
Having a strange USB print problem after upgrading my system. I have an HP Laserjet  4M+ connected to my computer on a USB port. (On the printer, the USB  cable goes into a USB-to-parallel adaptor on the printer's parallel  port). It worked fine before, but now that I have my system upgraded and am running the latest CUPS, I can only print one job. After  that I have to unplug the USB cable and plug it back in before the next  job will print, and I have to do it every time I want to print! (In the new CUPS changelog file there's a lot of notes about adding patches to get USB-to-parallel adaptors to work. But in my case it seems like it's done the opposite!)

Please  let me  know what I should try doing. I have been doing a lot of searches and it  seems that some people have it but there does not seem to be any  answers. Some of the problems go back to 2005, so this must be a  recurring error. When I look at the CUPS web interface,  it always says that there's a percentage of the job that's printed, but  not the whole thing. Or other times it says "Rendering completed":

HP_LaserJet_4_Plus-65     Unknown     Withheld     37k     1      processing since
Tue 02 Jul 2013 01:21:04 PM EDT 
"Rendering completed"

The status of the printer is "(Processing, Accepting Jobs, Not Shared)"

# lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 0557:2006 ATEN International Co., Ltd UC-1284B Printer Port
#

Now at this point I can unplug the USB cable, plug back in, and the status changes: "(Paused, Accepting Jobs, Not Shared)"

I click "Resume printer" on the web interface, and away she goes.

But the device ID has changed:

# lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 012: ID 0557:2006 ATEN International Co., Ltd UC-1284B Printer Port
# 		 	   		  

I also tried this command:

#  lpadmin -p HP_LaserJet_4_Plus -o usb-unidir-default=true

But it did the same thing. So then I tried this:

#  lpadmin -p HP_LaserJet_4_Plus -o usb-no-reattach-default=true

Ditto.

Anything else?

---

### Post by tgalati4 on 2013-07-03
```
dmesg | tail -50
```

Look for entries regarding the parallel port.  Perhaps the upgrade changed the way the parallel port is handled.  What was the before and after version of Ubuntu that you are using?  What version of CUPS are you using?

tgalati4@Mint14-Extensa ~ $ modinfo lp
filename:       /lib/modules/3.5.0-27-generic/kernel/drivers/char/lp.ko
license:        GPL
alias:          char-major-6-*
srcversion:     0946BE622F5ED3946F6D2AA
depends:        parport
intree:         Y
vermagic:       3.5.0-27-generic SMP mod_unload modversions 
parm:           parport:array of charp
parm:           reset:bool
tgalati4@Mint14-Extensa ~ $ modinfo parport
filename:       /lib/modules/3.5.0-27-generic/kernel/drivers/parport/parport.ko
license:        GPL
srcversion:     CC88FD9AB52260B219A4EA7
depends:        
intree:         Y
vermagic:       3.5.0-27-generic SMP mod_unload modversions

---

### Post by amberluvsit on 2013-07-03
Didn't see anything about parallel port in the dmesg, but lots of USB notes. It's CUPS 1.5.3-5 and I think all the changes with USB resets happened in version 1.5.3-2.1.

Here are some of their changelog notes for that:
     - Soft reset specific to the "PRINTER" device class. This allows one to
       reset without reconnecting.
     - When closing the device, it will also get reset to its original
       configuration, before re-attaching the usblp kernel module. Do not
       restore the configuration setting when the old configuration was zero,
       as zero means "unconfigured".
     - Added option "usb-unidir" to force the backend into uni-directional
       mode. This allows one to work around problems with bi-di
       communications, especially also a delay at the end of the job caused by
       closing the read channel (happens only for some devices, LP:#1001028).



# modinfo lp
filename:       /lib/modules/3.2.0-4-amd64/kernel/drivers/char/lp.ko
license:        GPL
alias:          char-major-6-*
depends:        parport
intree:         Y
vermagic:       3.2.0-4-amd64 SMP mod_unload modversions 
parm:           parport:array of charp
parm:           reset:bool
# modinfo parport
filename:       /lib/modules/3.2.0-4-amd64/kernel/drivers/parport/parport.ko
license:        GPL
depends:        
intree:         Y
vermagic:       3.2.0-4-amd64 SMP mod_unload modversions 

Anyway I can print, but it's silly to have to unplug and replug the cable each time. There must be something that happens at the end of the print job to put it in limbo. If I can figure out what, maybe then this bug can be fixed....

---

