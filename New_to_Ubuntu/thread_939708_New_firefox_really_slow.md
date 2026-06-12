---
title: "New firefox really slow"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-10-06
Firefox 3.03 is really slow and if I have more than 3 tabs open i pretty much can't use it.

Can I downgrade somehow?

Thanks

---

### Post by Sef on 2008-10-06
1) What are your system specs, including ram?

2) Applications > Accessories > Terminal and type/paste in this command:

```
top
```  That will show what processes are using up the cpu and ram.

You can paste the output here.

---

### Post by highlyevolved on 2008-10-06
```
Tasks: 110 total,   7 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 96.9%us,  1.8%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.4%hi,  0.9%si,  0.0%st
Mem:    507096k total,   498908k used,     8188k free,     3136k buffers
Swap:  1485972k total,   141304k used,  1344668k free,    65268k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
27766 adam      20   0  229m 104m  22m R 43.3 21.1   0:11.78 firefox           
 5705 adam      20   0 67956 1944 1936 S 42.8  0.4 595:07.39 evolution-data-   
 5244 root      20   0  394m  55m 7744 S  3.5 11.2  20:40.90 Xorg              
23754 adam      20   0  159m  44m  17m S  3.5  9.0   4:30.60 rhythmbox         
26577 adam      20   0  273m 111m  30m S  2.2 22.6   8:09.19 epiphany-gecko    
 4523 root      24   4     0    0    0 S  0.9  0.0   0:31.94 ktoshkeyd         
 4774 messageb  20   0  2976 1292  764 S  0.9  0.3   0:05.94 dbus-daemon       
 5613 adam      20   0 38600  14m 9312 R  0.9  3.0   0:34.24 gnome-panel       
 5586 adam      20   0 42388 9252 7000 S  0.4  1.8   0:08.32 gnome-settings-   
    1 root      20   0  2844  540  484 S  0.0  0.1   0:01.18 init              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.02 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.60 events/0          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper           
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.46 kblockd/0         
adam@adam-laptop:~$
```

---

### Post by Michael.Godawski on 2008-10-06
If you really want to downgrade you can try these howtos:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=770581](http://ubuntuforums.org/showthread.php?t=770581)
[*][http://www.dailygyan.com/2008/07/downgrading-from-firefox-3-to-firefox-2_01.html](http://www.dailygyan.com/2008/07/downgrading-from-firefox-3-to-firefox-2_01.html)
[/LIST]

The link on that page to download the FF2 is out of date but use this one instead:

[LIST]
[*][http://www.dailygyan.com/2008/07/downgrading-from-firefox-3-to-firefox-2_01.html](http://www.dailygyan.com/2008/07/downgrading-from-firefox-3-to-firefox-2_01.html)
[/LIST]

---

### Post by highlyevolved on 2008-10-06
Does my cpu seem too high?
Anything that shouldn't be there?

---

### Post by Michael.Godawski on 2008-10-06
Can you please post the output of this command so we have a clearer picture of your stats?
```
sudo lshw -short
```

Your free memory seems to be a little low...

---

### Post by highlyevolved on 2008-10-06
```
H/W path           Device      Class       Description
======================================================
                               system      Satellite Pro A120
/0                             bus         Portable PC
/0/0                           memory      128KiB BIOS
/0/4                           processor   Genuine Intel(R) CPU           T1400 
/0/4/12                        memory      64KiB L1 cache
/0/4/13                        memory      2MiB L2 cache
/0/81                          memory      512MiB System Memory
/0/81/0                        memory      512MiB SODIMM Synchronous
/0/81/1                        memory      SODIMM Synchronous [empty]
/0/100                         bridge      Mobile 945GM/PM/GMS, 943/940GML and 9
/0/100/2                       display     Mobile 945GM/GMS, 943/940GML Express 
/0/100/2.1                     display     Mobile 945GM/GMS/GME, 943/940GML Expr
/0/100/1b                      multimedia  82801G (ICH7 Family) High Definition 
/0/100/1c                      bridge      82801G (ICH7 Family) PCI Express Port
/0/100/1c/0        eth0        network     82573L Gigabit Ethernet Controller
/0/100/1c.2                    bridge      82801G (ICH7 Family) PCI Express Port
/0/100/1c.2/0      wifi0       network     AR242x 802.11abg Wireless PCI Express
/0/100/1d                      bus         82801G (ICH7 Family) USB UHCI Control
/0/100/1d.1                    bus         82801G (ICH7 Family) USB UHCI Control
/0/100/1d.2                    bus         82801G (ICH7 Family) USB UHCI Control
/0/100/1d.3                    bus         82801G (ICH7 Family) USB UHCI Control
/0/100/1d.7                    bus         82801G (ICH7 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1e/b                    bridge      PCIxx12 Cardbus Controller
/0/100/1e/b.3                  system      PCIxx12 SDA Standard Compliant SD Hos
/0/100/1f                      bridge      82801GBM (ICH7-M) LPC Interface Bridg
/0/100/1f.2        scsi0       storage     82801GBM/GHM (ICH7 Family) SATA IDE C
/0/100/1f.2/0      /dev/sda    disk        60GB FUJITSU MHV2060B
/0/100/1f.2/0/1    /dev/sda1   volume      54GiB EXT3 volume
/0/100/1f.2/0/2    /dev/sda2   volume      1451MiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5   volume      1451MiB Linux swap / Solaris partitio
/0/100/1f.2/1      /dev/cdrom  disk        DVD-RAM UJ-841S
/1                             power       LP659U

```
..

---

### Post by dineshs on 2008-10-06
I am a beginner I had a problem of delay in getting pages loaded.It started working properly after I installed firestarter.Dont know why

---

