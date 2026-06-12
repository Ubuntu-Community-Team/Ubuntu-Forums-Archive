---
title: "[SOLVED] Dunno how to autoload driver at boot"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by _sluimers_ on 2008-08-16
I have to reload the driver at every reboot. It's annoying.
I've tried following these instructions but nothing happens after a reboot.

```

MORE INFORMATION
=================================================================================
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
=======================================================================

```

---

### Post by Cypher on 2008-08-16
If you know the specific name of the driver, you can autoload it by adding it to the "/etc/modules" file.

---

### Post by _sluimers_ on 2008-08-16
> **Cypher said:**
> If you know the specific name of the driver, you can autoload it by adding it to the "/etc/modules" file.

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
rt2870sta

```

Most likely it's rt2870sta as/but that's already in the "/etc/modules" file, so is there a way to find out why this is not working and how it can be fixed?

---

### Post by olejorgen on 2008-08-16
You could do the easy (maybe not the "correct") way, and add the commands you use to set up the driver in /etc/rc.local

---

