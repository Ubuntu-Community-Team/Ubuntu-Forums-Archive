---
title: "Getting a USB thumb drive to work"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by ggfile on 2008-08-21
Hello:

I have recently bought a USB thumb drive and the package says it is Linux compatible.  I plugged it into my USB port and nothing happened.   I cannot find the folder anywhere in order to add files to my thumb drive.  When I plugged in my printer into the USB port Ubuntu automatically recognized the printer and gave me the option to install the printer.  Do I need to install a driver or something to make my thumb drive to work?  Has anybody else had this problem with their thumb drive?  I just expected that Ubuntu would have automatically recognized the drive and would have listed it as an available drive... like what happens when I insert a CD or floppy disk into my computer.  The flash drive did light up... but nothing else happened.  Please help.

Peter

---

### Post by tech9 on 2008-08-21
> **ggfile said:**
> Hello:

I have recently bought a USB thumb drive and the package says it is Linux compatible.  I plugged it into my USB port and nothing happened.   I cannot find the folder anywhere in order to add files to my thumb drive.  When I plugged in my printer into the USB port Ubuntu automatically recognized the printer and gave me the option to install the printer.  Do I need to install a driver or something to make my thumb drive to work?  Has anybody else had this problem with their thumb drive?  I just expected that Ubuntu would have automatically recognized the drive and would have listed it as an available drive... like what happens when I insert a CD or floppy disk into my computer.  The flash drive did light up... but nothing else happened.  Please help.

Peter

open a terminal and type this in

```
sudo **mount /dev/sd[COLOR=#FF0000]b[/COLOR]1**
```

---

