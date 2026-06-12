---
title: "Ubuntu 20.04 LTS: ethernet connection has suddenly stopped to work"
date: 2024-07-20
forum: New to Ubuntu
---

### Post by maketopsite on 2024-07-20
It's ethernet connection from laptop to wifi router. (Wifi works fine.)

```
Jul 20 18:55:54  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 (xid=0xa91d012)
Jul 20 18:55:39  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0xa91d012)
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8673] dhcp4 (eth0): activation: beginning transaction (timeout in 45 seconds)
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8661] device (eth0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8620] device (eth0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8597] device (eth0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8581] device (eth0): Activation: starting connection 'Wireless connection' (xxxxxx)
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8561] policy: auto-activating connection 'Wireless connection' (xxxxxx)
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8530] dhcp4 (eth0): state changed timeout -> done
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8530] dhcp4 (eth0): canceled DHCP transaction
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8383] device (eth0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <warn>  [1721494527.8381] device (eth0): Activation: failed for connection 'Wireless connection'
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8373] device (eth0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <info>  [1721494527.8372] dhcp4 (eth0): state changed unknown -> timeout
Jul 20 18:55:27  maketopsite NetworkManager[63399]: <warn>  [1721494527.8372] dhcp4 (eth0): request timed out
Jul 20 18:55:26  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 (xid=0xa91d012)
Jul 20 18:55:17  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0xa91d012)
Jul 20 18:54:59  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 (xid=0xa91d012)
Jul 20 18:54:49  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0xa91d012)
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8710] dhcp4 (eth0): activation: beginning transaction (timeout in 45 seconds)
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8708] device (eth0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8699] device (eth0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8695] device (eth0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8694] device (eth0): Activation: starting connection 'Wireless connection' (xxxxxx)
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8685] policy: auto-activating connection 'Wireless connection' (xxxxxx)
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8650] dhcp4 (eth0): state changed timeout -> done
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8650] dhcp4 (eth0): canceled DHCP transaction
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8379] device (eth0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <warn>  [1721494482.8375] device (eth0): Activation: failed for connection 'Wireless connection'
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8365] device (eth0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <info>  [1721494482.8364] dhcp4 (eth0): state changed unknown -> timeout
Jul 20 18:54:42  maketopsite NetworkManager[63399]: <warn>  [1721494482.8364] dhcp4 (eth0): request timed out
Jul 20 18:54:29  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20 (xid=0xa91d012)
Jul 20 18:54:19  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0xa91d012)
Jul 20 18:54:04  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0xa91d012)
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8840] dhcp4 (eth0): activation: beginning transaction (timeout in 45 seconds)
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8837] device (eth0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8827] device (eth0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8824] device (eth0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8823] device (eth0): Activation: starting connection 'Wireless connection' (xxxxxx)
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8813] policy: auto-activating connection 'Wireless connection' (xxxxxx)
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8771] dhcp4 (eth0): state changed timeout -> done
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8771] dhcp4 (eth0): canceled DHCP transaction
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8406] device (eth0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <warn>  [1721494437.8404] device (eth0): Activation: failed for connection 'Wireless connection'
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8394] device (eth0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <info>  [1721494437.8393] dhcp4 (eth0): state changed unknown -> timeout
Jul 20 18:53:57  maketopsite NetworkManager[63399]: <warn>  [1721494437.8393] dhcp4 (eth0): request timed out
Jul 20 18:53:54  maketopsite dhclient[70014]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0xa91d012)
Jul 20 18:53:50  maketopsite smartd[1032]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 139 to 133


```

```
03:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E220x Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7d00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at c000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable- Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number xxxxxxx
    Kernel driver in use: alx
    Kernel modules: alx


```

Any idea please ?

---

### Post by maketopsite on 2024-07-22
It works after laptop power OFF and ON.

---

