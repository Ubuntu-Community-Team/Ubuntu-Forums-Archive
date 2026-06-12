---
title: "How to determine which graphics driver is being used?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by KingTermite on 2008-05-29
The **lspci** command tells me the hardware present (graphics card/chipset), but not what driver Ubuntu is using.

The /etc/X11/xorg.conf file just has what looks like some really generic info in it.

Where can I found out what driver is being used?

---

### Post by philinux on 2008-05-29
One way is

system>admin>hardware driver

---

### Post by quelx on 2008-05-29
```
lsmod |grep agpgart
```

---

### Post by KingTermite on 2008-05-29
> **philinux said:**
> One way is

system>admin>hardware driver

I tried that. It showed up empty (nothing listed in it).

---

### Post by KingTermite on 2008-05-29
> **quelx said:**
> ```
lsmod |grep agpgart
```

I can try that when I get home (at work now). thanks.

---

### Post by lswest on 2008-05-29
you can do ```
lshw -C Display
``` and there should be a line that says "driver=".  For example my output is: > lswest@lswest-laptop:~$ lshw -C Display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GeForce 7150M
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: **driver=nvidia** latency=0 module=nvidia

the bit marked in bold is the relevant line.

---

