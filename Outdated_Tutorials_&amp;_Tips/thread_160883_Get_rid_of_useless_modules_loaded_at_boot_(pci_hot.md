---
title: "Get rid of useless modules loaded at boot (pci_hotplug, sony_acpi, apm, etc.)"
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by geofs on 2006-04-15
If you look at the kernel boot messages (in general you don't notice them they're hidden by the boot splash, in fact the '*quiet*' and '*splash*' kernel options in */boot/grub/menu.lst*) 
```
# less -S /var/log/syslog
```
you might notice that hotplug tries (and fails) to load useless modules.  This perhaps doesn't seem very important but I dislike having ugly messages like this:

```
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5

```

To prevent hotplug from loading such modules (MAKE SURE you don't need them) edit (as root) the file */etc/hotplug/blacklist* and add a line with the name of the module (one module per line)

I always add these on new installs:

```
sony_acpi
pcc_acpi
tsdev
shpchp
pci_hotplug
apm

```

You have to figure out the correct name of the module.  Have a look at
```
# lsmod
```

Note: on my debian sid with hotplug managed by udev (and perhaps on Dapper???) the hotplug package has gone and the blacklist file is in */etc/modprobe.d/blacklist*.  You must add the word 'blacklist' in front of the module name, like this:
```
blacklist shpchp
blacklist tsdev
...
```

---

