---
title: "corrupt graphics"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by gimmejimmy on 2008-11-09
I'm experiencing corrupt graphics on some screensavers and games such as SuperTux 2.  Here's an example:
[IMG]http://img.photobucket.com/albums/v440/jcmoral/Screenshot-1.jpg[/IMG]
Can I reinstall video drivers?  How do I do it?  I'm using Intel 82810E onboard graphics.  Thanks.

Is the image too big?  I'll fix it if it is.

---

### Post by Peter09 on 2008-11-09
Boot into recovery mode and select the XFIX option. That should set up your driver again.

IF you still have problems post the output of

```
lshw - C display
```

---

### Post by gimmejimmy on 2008-11-09
Here it is:
```
*-display               
       description: VGA compatible controller
       product: 82810E DC-133 (CGC) Chipset Graphics Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810

```

---

### Post by Peter09 on 2008-11-09
Well looks like you have the correct driver installed.

---

