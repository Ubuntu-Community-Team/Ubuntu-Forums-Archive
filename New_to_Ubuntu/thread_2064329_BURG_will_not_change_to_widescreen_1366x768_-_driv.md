---
title: "BURG will not change to widescreen 1366x768 - driver issue, or incorrect cfg?"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by hmmwhatsthisdo on 2012-09-29
I'm on a laptop that dualboots W7 and 12.04. I installed BURG, but it doesn't seem to want to go into 1366x768 resolution, the full resolution of the laptop monitor. Running "vbeinfo" in the GRUB console doesn't show it as an option, and editing the configuration file and updating BURG does nothing.

My laptop runs an Intel Integrated Graphics chip. (It's a Dell Inspiron n5110)

What should I do?

---

### Post by viper200 on 2012-10-01
try downloading grub customizer and in the burg appearance settings change custom resolution as 1366x768x32 or u can edit GRUB_GFXMODE=1366x768x32 in /etc/default/burg

---

### Post by hmmwhatsthisdo on 2012-10-01
I tried changing it to 1366x768x24 (all the others were x24), and it didn't work. In addition, burg-emu Displays it just fine.

If GRUB was able to display in my display's full resolution, does that necessarily mean BURG will be able to?

---

### Post by mips on 2012-10-01
Does your GPU actually support a framebuffer with that resolution?

From your desktop ress ctrl-alt-f1 to drop to a shell, login and enter,

```
sudo hwinfo --framebuffer
```

If you don't have hwinfo installed then install it before running that command. ctrl-alt-f7 to get back

Post the output here, you could try from a terminal on your desktop as well but I noticed I get different results from the desktop.

Burg should be able to use the same resolution as grub but grub 'might' have been using a different soft framebuffer.

---

### Post by hmmwhatsthisdo on 2012-10-01
Here's the output of sudo hwinfo --framebuffer:

```
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.ku_DuSHewh1
  Hardware Class: framebuffer
  Model: "Intel(R)Sandybridge Mobile Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R)Sandybridge Mobile Graphics Controller"
  SubVendor: "Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xe0000000-0xe3feffff (rw)
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

In addition, the following was also output to the console after the execution of the command (but before the output was given), but didn't get written to the file.

```
process 6217: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files

```

So, it looks like it doesn't list 1366x768x24 in the modes. Is there any hope?

---

### Post by mips on 2012-10-01
> **hmmwhatsthisdo said:**
> Here's the output of sudo hwinfo --framebuffer:

```
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.ku_DuSHewh1
  Hardware Class: framebuffer
  Model: "Intel(R)Sandybridge Mobile Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R)Sandybridge Mobile Graphics Controller"
  SubVendor: "Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xe0000000-0xe3feffff (rw)
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```


So, it looks like it doesn't list 1366x768x24 in the modes. Is there any hope?

Did you do that from the desktop (X) or did you exit X with ctrl-alt-f1? Try it outside of X with sudo hwinfo --framebuffer >fb.txt this will create a text file in your home folder which you can then copy and paste the content of here.

There might be hope with something called 'Uvesafb' but you would have to google it as I've never used it.

Edit: Actually I'm not sure "Uvesafb' will work for burg as I think it only kicks in after burg/grub. Hopefully someone with more knowledge comes along with an answer.

---

### Post by hmmwhatsthisdo on 2012-10-01
That was from outside of X.  Though, the same result was produced when X was loaded and the command was fed into the Terminal.

---

