---
title: "Ethernet not working"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2013-03-11
Hi friends,

here is output of "sudo lshw -class network"

*-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f1800000-f183ffff ioport:2000(size=128)



Please help me install correct driver and get wired network working. If you require output of more commands please tell which commands I should use.

Thanks in advance

---

### Post by sujitrjadhav on 2013-03-11
```
sujit@sujit-inspiron-5420:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
```

---

### Post by steeldriver on 2013-03-11
What version of ubuntu do you have?

```
uname -a
```

iirc chili555 (and maybe others) have recently posted some instructions for these devices, the driver is 'alx' I think and you may need either a compat / backports package or source install

I will check back and if one of the experts does not step up I will try to help

[http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)

---

### Post by sujitrjadhav on 2013-03-11
```
sujit@sujit-inspiron-5420:~$ uname -a
Linux sujit-inspiron-5420 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by sujitrjadhav on 2013-03-11
tried a solution given by [COLOR=#000000]chili555[/COLOR] in thread [http://ubuntuforums.org/showthread.php?t=1810607](http://ubuntuforums.org/showthread.php?t=1810607). But in my case I am getting error when I run make command

---

