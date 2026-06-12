---
title: "trouble connecting to encrypted wireless"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by jcl43 on 2008-09-04
Hi all, I have a thinkpad r61 with ubuntu 8.04. It is able to connect to unencrypted wireless, but when I try to connect to my WPA2 encrypted router at home its a no go. All help appreciated Thanks!

---

### Post by crispy_420 on 2008-09-05
What chipset is your wireless?

Security settings for wireless?

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lshw -C network
```

---

### Post by jcl43 on 2008-09-06
Thank you for replying, here are the results of that command:

```

 *-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:d8:0b:d6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=192.168.1.3 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:75:0b:d7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

---

### Post by hyper_ch on 2008-09-06
have you tried to connect to a not-encrypted one? then maybe a wpa one?

---

### Post by jcl43 on 2008-09-06
Yes, it can connect to unencrypted no problem (havent tried changing my setup at home). It connects automatically to hotspots, and my university wireless.

---

### Post by jcl43 on 2008-09-06
i noticed in the output i posted above it shows the logical name as
```

logical name: wmaster0

```

but when i run iwconfig this is what it shows:
```

user@user-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

also i was wondering if IEEE 802.11 N is supported if anyone knows.

Thanks again all.

---

