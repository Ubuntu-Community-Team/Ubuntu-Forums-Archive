---
title: "upgrading"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by Gennu on 2013-01-11
is it normal that when I upgrade every time that msg appears to me which tells that canonical system does not support this release any more and that some files must be removed it appeared when I was upgrading from 11.10 to 12.04.1 LTS

---

### Post by deadflowr on 2013-01-11
Did you read through what was actually being removed, and why?

Every time I first upgrade a system I read through what packages are getting pulled out and what is being put in.

Canonical fully supports 11.10 and 12.04(as of now), so it seems like thats a package specific notification.

---

### Post by vasiliscnisrok on 2013-01-11
please give me screenshot

---

### Post by Gennu on 2013-01-11
I think you are late guyz :P I've been messing with this system for days and now I'm using 12.04.1 LTS and its working good except that the wireless connection is not working and i don't know why :S I don't know where to start 
so please help me :D

---

### Post by GordThompson on 2013-01-11
> **Gennu said:**
> I'm using 12.04.1 LTS and its working good except that the wireless connection is not working
Are you currently using a wired connection from that machine? If so then please open a Terminal window, run the following commands, and reply here with the results:

```
sudo lshw -class network
``````
nm-tool
```

---

### Post by grahammechanical on 2013-01-11
> **Gennu said:**
> is it normal that when I upgrade every time that msg appears to me which tells that canonical system does not support this release any more and that some files must be removed it appeared when I was upgrading from 11.10 to 12.04.1 LTS

For the information of anyone reading this thread.

The upgrade process will also upgrade the default applications such as Libreoffice. Applications that we have installed and that are not supported by Canonical cannot be upgraded during the upgrade process. Those applications are removed because there would be conflicts between the old libraries need by that application and the new libraries that are being brought in.

Ubuntu 11.10 saw the start of the change over from Gnome 2 to Gnome 3. That change over became greater with 12.04. We also gained multi-architecture libraries that help a 32bit application run on a 64bit OS as well as the the 64bit versions of the applications. Before this specific 32bit libraries were needed to run 32bit applications.

This is why we have to re-install some applications after an upgrade and why we get a warning that the application is going to be removed.

Regards.

---

### Post by Gennu on 2013-01-11
> **grahammechanical said:**
> For the information of anyone reading this thread.

The upgrade process will also upgrade the default applications such as Libreoffice. Applications that we have installed and that are not supported by Canonical cannot be upgraded during the upgrade process. Those applications are removed because there would be conflicts between the old libraries need by that application and the new libraries that are being brought in.

Ubuntu 11.10 saw the start of the change over from Gnome 2 to Gnome 3. That change over became greater with 12.04. We also gained multi-architecture libraries that help a 32bit application run on a 64bit OS as well as the the 64bit versions of the applications. Before this specific 32bit libraries were needed to run 32bit applications.

This is why we have to re-install some applications after an upgrade and why we get a warning that the application is going to be removed.

Regards.
okay thanks you've just made everything obvious now :) so thank you

---

### Post by Gennu on 2013-01-11
> **GordThompson said:**
> Are you currently using a wired connection from that machine? If so then please open a Terminal window, run the following commands, and reply here with the results:

```
sudo lshw -class network
``````
nm-tool
```

```
ahmed@ahmed-Inspiron-N4050:~$ sudo lshw -class network
[sudo] password for ahmed: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 78:45:c4:b5:42:ef
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d07fff
ahmed@ahmed-Inspiron-N4050:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        78:45:C4:B5:42:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



```

---

### Post by GordThompson on 2013-01-11
Okay, good. Now please show us the results from the following command:

```
lspci -vvnn | grep 14e4
```

---

### Post by Gennu on 2013-01-12
> **GordThompson said:**
> Okay, good. Now please show us the results from the following command:

```
lspci -vvnn | grep 14e4
```
```

ahmed@ahmed-Inspiron-N4050:~$ lspci -vvnn l grep 14e4
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
```

---

### Post by GordThompson on 2013-01-12
You typed the letter 'l' (lowercase 'L') instead of the pipe character '|' and that's why the previous attempt didn't work. Please try again.

---

### Post by Gennu on 2013-01-12
> **GordThompson said:**
> You typed the letter 'l' (lowercase 'L') instead of the pipe character '|' and that's why the previous attempt didn't work. Please try again.
```

ahmed@ahmed-Inspiron-N4050:~$ lspci -vvnn | grep 14e4
09:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
```

---

### Post by GordThompson on 2013-01-12
> **Gennu said:**
> ```

ahmed@ahmed-Inspiron-N4050:~$ lspci -vvnn | grep 14e4
09:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
```
Your wireless adapter appears to be a Broadcom 43142, and it seems that it is sufficiently new that neither the proprietary Broadcom STA driver ('wl') nor the 'b43' driver will work. You best bet would probably be to try one of the solutions proposed in the AskUbuntu thread here:

[How do I install BCM43142 wireless drivers for Dell Vostro 3460/3560?]("http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560")

---

### Post by Gennu on 2013-01-12
> **GordThompson said:**
> Your wireless adapter appears to be a Broadcom 43142, and it seems that it is sufficiently new that neither the proprietary Broadcom STA driver ('wl') nor the 'b43' driver will work. You best bet would probably be to try one of the solutions proposed in the AskUbuntu thread here:

[How do I install BCM43142 wireless drivers for Dell Vostro 3460/3560?]("http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560")

okay thank you I'll search these solutions to find out

---

### Post by Gennu on 2013-01-18
> **GordThompson said:**
> Your wireless adapter appears to be a Broadcom 43142, and it seems that it is sufficiently new that neither the proprietary Broadcom STA driver ('wl') nor the 'b43' driver will work. You best bet would probably be to try one of the solutions proposed in the AskUbuntu thread here:

[How do I install BCM43142 wireless drivers for Dell Vostro 3460/3560?]("http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560")

non of them worked with me
so what now ??!

---

