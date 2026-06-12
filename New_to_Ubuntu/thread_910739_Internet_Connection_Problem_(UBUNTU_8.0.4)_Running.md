---
title: "Internet Connection Problem (UBUNTU 8.0.4) Running On VMware Workstation 6.04"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Exc.BluePhoenix on 2008-09-04
Hello,

I started using Ubuntu recently and everything went smoothly. Yesterday though, I lost my internet connectivity.

Firefox says it cannot connect to the server...

I have an icon which is called "Network Connection" , at first it said etho in the connection type and said idle on the status, yet I could not use the internet.

Then I had the great idea of putting lo, and then etho disappeared from my drop down box and still it does not work.

I am running Ubuntu 8.04 (hardy), under VMware Workstation 6.0.4, my main OS is Windows Xp SP2. I use the bridge option in VMware to connect to the internet when making the virtual machine.

I connect to the internet as follows computer -> router -> cable modem. I do not use wireless or USB for internet connection, I mention this because I have read threads where wireless connection is the problem.

I also read the following commands were helpful in figuring out the problem, therefore, I took the liberty of showing the information here:

Command ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:fe:43:2e  
          inet6 addr: fe80::20c:29ff:fefe:432e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386327 (377.2 KB)  TX bytes:468 (468.0 B)
          Interrupt:16 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23900 (23.3 KB)  TX bytes:23900 (23.3 KB)

```

Command sudo mii-tool eth0

```
SIOCGMIIPHY on 'eth0' failed: Operation not supported
```

Command iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

Command lspci

```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware Inc Unknown device 0790 (rev 02)
02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:02.0 USB Controller: VMware Inc Abstract USB2 EHCI Controller

```

Command lshw -class network
```

 *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:fe:43:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical
       configuration: broadcast=yes driver=vmxnet latency=64 maxlatency=255 mingnt=6 module=vmxnet multicast=yes

```

I hope the commands above are helpful in determining any problems pertaining to me having no connection.

I thank you for you time and if anything else is need it, anything needs to be cleaned up, please let me know and I will get to it.

Please note : I don't really know what the information above means, I just read a thread that looked like my problem and I though it could help solve the problem, since the solution that work for that particular user did not work for me.

Also I don't know if it means anything, but every time I start Firefox, its starts offline, I uncheck the box and it will restart again offline, don't know why.

---

