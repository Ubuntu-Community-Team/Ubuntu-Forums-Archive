---
title: "ndiswrapper"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by lengo on 2008-10-05
How hopelessly aggravating does this have to be?! I have a wireless card that doesn't work "out of the box" (Atheros a/b/g/n AR 5416). So I try to run ndiswrapper. ndiswrapper returns a "FATAL: Module ndiswrapper not found" error. So I learn that the ndiswrapper in the repository doesn't work for 8.04 . . . I download ndiswrapper-1.53.tar.gz and go through the whole rigamarole of learning how to install a tar.gz file (extract, make unistall, make). I get this message: "NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below." and run "make uninstall" about 50 times. Finally, I just run "make". It makes away. I run " ndiswrapper -i NET5416.INF" and then "ndiswrapper -l" and get: "net5416 : driver installed
	device (168C:0024) present"
Finally, I run: modprobe ndiswrapper
and get:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko): Operation not permitted

I JUST WANT WIRELESS!!!! [ . . . sorry . . . I'm frustrated.] Can anyone help with this? I've spent about three hours reading tutorials and am at wits end.

---

### Post by cprofitt on 2008-10-05
Can you do an output of an lspci and ifconfig and iwconfig?

Which of the two machines you listed is this going on? I have both and do not have to load any additional drivers for my wireless to work.

---

### Post by k3lt01 on 2008-10-05
> **lengo said:**
> So I learn that the ndiswrapper in the repository doesn't work for 8.04 . . . I had some difficulty with ndiswrapper when 8.04 first come out but that was fixed within days. 8.04.1 has no problem at all.

What version of Hardy do you have? Maybe you could download the new version in the hard repository and install that.

---

### Post by patrickballeux on 2008-10-05
You simply forgot to run : "sudo modprobe ndiswrapper"

Don't forget to sudo your command since they required root access.

Example:

> make
> sudo make install
> sudo modprobe ndiswrapper

Also, I see that you are running an old version of the kernel.  Do all your updates first, then work on the wireless card.  If you cannot do your updates because don't have network access without the wireless card, then continue with the ndiswrapper compilation...

Current kernel version (AMD64) is 2.6.24.21



Let me know!

---

### Post by lengo on 2008-10-06
> **PrivateVoid said:**
> Can you do an output of an lspci and ifconfig and iwconfig?

Which of the two machines you listed is this going on? I have both and do not have to load any additional drivers for my wireless to work.

First, I just used "sudo modprobe ndiswrapper" and didn't get any errors (thank you partrickballeux). [Aside: when I read a tutorial and they write "enter in the terminal "modprobe ndiswrapper"", are they running as 'root'? and should I be doing the same? and if they're not, it is assumed that every terminal command is preceded by "sudo"? I can't believe I spent two hours fighting that . . . ]

Now, the output of lspci is:
```
user@T61-CTO:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

The output of ifconfig is:
```
user@T61-CTO:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:70:76:39  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe70:7639/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1254874 (1.1 MB)  TX bytes:365915 (357.3 KB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56291 (54.9 KB)  TX bytes:56291 (54.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:68:c2:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7629 (7.4 KB)
          Interrupt:21 Memory:df2f0000-df300000
```

and finally, the output of iwconfig is:
```
user@T61-CTO:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

This is on my T61. I always have to wonder what I'm doing wrong when someone writes, "I have the same machine and it works out of the box" . . . Cause obviously I'm screwing up somewhere! :confused: It looks like I have a wireless card recognised there, but I still can't connect . . . Any help still appreciated!

---

### Post by patrickballeux on 2008-10-06
Did you installed the Network Manager applet so you can use the GUI to configure your access?

Also you can set your configuration in "System - Administration - Network"

We see that you wireless card is recognized, that is a good thing, but no configuration was set (ESSID, encryption if there is...).

Once configured, you should have something like this:
```

eth1      IEEE 802.11g  ESSID:"balleux"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:XX:XX:XX:XX:2A   
          Bit Rate=36 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=86/100  Signal level=-48 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
*Note: Mac adresse was filled wity "XX"...*

You will need to enter your ESSID, your encryption method (WPA, None, etc...) and the password/key to connect (if there is encryption)

As I said, the Network Manager will help you to do that with your mouse and keyboard in a nice GUI...

Good luck!

---

### Post by lengo on 2008-10-06
Thanks, patrickballeux. I was using NM, but the encryption window was hidden behind the umpteen other windows I had open (duh!) So I'm up and running again. Thanks for your help!

---

