---
title: "What do I backup in Ubuntu?"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by Michael_McKenney on 2014-09-29
In Windows, I backup everything.   What do I backup in Ubuntu?  I setup Bacula and picked

/
/home
/var
/var/www
/etc
/srv

My question is does / backup everything under it?  Does /var also backup /var/www?

---

### Post by nerdtron on 2014-09-29
Unless /var and /var/www are on different partitions, then /var/www won't be backed-up.

If your backup software backup is recursive, it will backup everything below the folder. So backing up /var/ will also backup /var/log and /var/www etc. and all folder inside.

In terms on what to backup, that would depend mainly on your data. Do you need files in /var/www? Then create a backup for it.
If you want to backup the whole system, then backup / folder. You may want to exclude /dev, /proc, /tmp.

---

### Post by Michael_McKenney on 2014-09-29
Simple design.  Everything on one drive.  My /var/www web site is 130 GB.  The rest of the box is 3 GB at most.  /dev, /tmp, and /proc are in the exclusions.  

My old Symantec backup would take 2.5 hours to backup /var/www.   Bacula took 5+ hours.   I am looking at the nic setup on the Tape server tonight.  The web site box backup speed was fine on Symantec and Windows XP x64 at 1630 MB/min.  The Tape server has 4 GB on it.  How do I increase the buffers on the NIC?   It is running 1000 Mbps.  I am going to check if full duplex is enabled.

---

### Post by nerdtron on 2014-09-29
You mean you are not satisfied with the speed of transfer/backup. If you backup /var/www and if it has thousands of small files like then transferring data to backup is really long. It is a lot (way,way faster) if you backup a single 130GB file on 1000Mbps link than transferring 130GB of lots of html, docs files. 

You can compress your /var/www to a single zip file and then transfer to backup and see the speed bump.

To determine if your 1000Mbps link is really enabled in ubuntu, use ethtool:
```
 ethtool eth0
```

---

### Post by Michael_McKenney on 2014-09-29
The NIC GUI states 1000 Mbps.  I did not check the command line.  It said DHCP configured. If set to auto duplexing, that could cause full duplex issues with performance.  In Windows, I setup send and receive buffers higher because this box only does backups to tape drives.   I was going to hard set the changes tonight.  The board is a Tyan Thunder K8WE server board with a pair of AMD 280 Opterons and 4GB of RAM.   I was checking to see if hardware compression needed to be enabled on the HP LTO 3 tape drive.  I was considering trying software compression too.   The pictures are 4-15 MB images.   Symantec Backup Exec and Windows XP was 2.5 hours @ 1630 MB/min.  Tonight, I was going to setup only /var/www to backup and compare performance.   That is all I did under Symantec since I did not have a Linux client.  It was a share I backed up.

---

### Post by Michael_McKenney on 2014-09-29
```

root@Tape:/home/michael# ethtool eth1
Settings for eth1:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes


```

---

### Post by Michael_McKenney on 2014-09-29
```

root@Tape:/home/michael# dmesg | grep -i eth
[    1.262337] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.784505] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:e0:81:70:18:0e
[    1.784509] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[    2.308522] forcedeth 0000:80:0a.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:e0:81:70:18:0f
[    2.308529] forcedeth 0000:80:0a.0: highdma csum gbit lnktim desc-v3
[   25.498921] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.498931] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   27.828150] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.107127] forcedeth 0000:00:0a.0 eth0: no link during initialization
[   31.107513] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.107882] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
root@Tape:/home/michael# ^C
root@Tape:/home/michael# 


**[SIZE=1]Integrated Secure Network Processor[/SIZE]**[FONT=Arial,Helvetica,Univers,Zurich BT][SIZE=-2] 
 &#8226; Two IEEE 802.3 Nvidia MAC 1000/100/10
     Ethernet (1st from                                                                                                     nForce&#8482; Prof. 2200, 
     2nd from nForce Prof. 2050) 
 &#8226; Supports WOL and PXE
 &#8226; Supports                                                                                                     Ethernet Jumbo Frames (9018 Bytes)
 &#8226; Full Duplex Gigabit Ethernet support
[/SIZE][/FONT]


```

---

### Post by Michael_McKenney on 2014-09-30
I found information on the Reversed Engineered driver.  Most say it is slow.  Tonight, I am going to Micro Center and getting a Intel PCIe 1x Gigabit NIC.  Same one I used in the other Ubuntu workstation.

---

