---
title: "Bit-banging the uss720 usb to parallel device?"
date: 2007-03-16
forum: Programming Talk
---

### Post by wkulecz on 2007-03-16
I've a usb to parallel port adapter.  Ubuntu recognizes it and reports Lucent uss720 and installs the uss720 module.

I'd like to be able to bit-bang the emulated printer port to read switches and drive relays.  Speed is not a issue.  In fact, the output from dmesg says use this module if you want to bit-bang the port, if you just want to hook up a printer use usblp instead.

Google search found me some info about 2.4 Kernel but none of it matches up with the /proc/sys/ stuff in Ubuntu 6.06 so I'm at a loss as to how to proceed.

On a real parallel port I'd do what I want with outp_b(bitvalues, 0x378) or status=inp_b(0x37a), anybody got any clues as to what the port address would be for the usb emulation or what device to read/write to get/set the printer I/O line states?

--wally.

---

### Post by ziuchkov on 2007-11-08
I'm looking to do the same type of thing.  Did you ever figure this out?

---

### Post by matth45 on 2008-04-18
Does anyone know if this is possible?

Can someone who has one of these devices post the output of 
```

cat /proc/ioports
```

while the port is attached and the kernel module is loaded?

Thanks

---

### Post by wkulecz on 2009-03-24
> **matth45 said:**
> Does anyone know if this is possible?

Can someone who has one of these devices post the output of 
```

cat /proc/ioports
```

while the port is attached and the kernel module is loaded?

Thanks

Old thread, but I'm still interested if its possible.

cat /proc/ioports shows no difference before and after the USB parallel device is plugged in.  Although some "Unknown driver using generic text only driver" doodad pops up in the menubar.

I've since upgraded o 8.04 and this device behaves very differently when inserted now than it did under 6.06.

--wally.

--wally.

---

### Post by Zugzwang on 2009-03-24
> **wkulecz said:**
> cat /proc/ioports shows no difference before and after the USB parallel device is plugged in.  Although some "Unknown driver using generic text only driver" doodad pops up in the menubar.


Of course not. When carefully examining the manual of such devices, you will see that they are *no* full parallel ports but just support printers. That means, interfacing works somewhat different. You may however find some "character device" for that cable somewhere. Search the forums for this.

---

