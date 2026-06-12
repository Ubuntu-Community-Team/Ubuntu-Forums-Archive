---
title: "No network at all"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Javooo on 2008-11-02
My internet connection isnt working at all for some reason i dont see the network manager, i'm dual booting and i cant connect either in windows xp i dont know what's wrong, please help me.

---

### Post by ugm6hr on 2008-11-02
We need (a lot) more information to help.

[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

Also - why is it not working in XP?  This would seem like it's a hardware issue (perhaps).

---

### Post by Javooo on 2008-11-02
Sorry my post was so vague, but after reading other posts i think i have a problem similar to this one [http://ubuntuforums.org/showthread.php?t=834225](http://ubuntuforums.org/showthread.php?t=834225)
I dont know why but after i run sudo dhclient eth0 i get this:
eth0: ERROR while getting interface flags: No such devide
eth0: ERROR while getting interface flags: No such devide
eth0: ERROR while getting interface flags: No such devide
Bind socket to interface: No such device

---

### Post by ugm6hr on 2008-11-02
You still need to give the information as I linked to.

---

### Post by Javooo on 2008-11-02
1. How were you trying to get online? e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.

wireless router

2. What hardware are you using? The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc. You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).



3. Who is your Internet Service Provider (and in which country)?

prodigy infinitum, Mexico.

4. Which version of Ubuntu are you using? e.g. Ubuntu 8.04, Xubuntu 7.10 etc.

Ubuntu 8.04.1

5. Can you get online with any other method? e.g. if you have a wifi problem, can you connect with ethernet?

None

6. How are you getting online to post on this forum?

I'm using my cousins laptop through wireless router

7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.

```
javier@javier-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) 
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller 
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) 
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller 

```

```
javier@javier-laptop:~$ lsusb 
Bus 005 Device 003: ID 0dd8:6006 Netac Technology Co., Ltd  
Bus 005 Device 001: ID 0000:0000   
Bus 004 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader 
Bus 001 Device 001: ID 0000:0000  

```

```
javier@javier-laptop:~$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED      
       description: Ethernet controller 
       product: 82573L Gigabit Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
  *-network 
       description: Network controller 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=iwl3945 latency=0 module=iwl3945 

```

I tried re installing ubuntu, it didnt work then i've been reading lots of howtos and i just cant fix this, please help me i'd appreciate it alot

---

### Post by Crafty Kisses on 2008-11-02
What are the results of this command?
```
ping google.com
```

---

### Post by Javooo on 2008-11-02
```
javier@javier-laptop:~$ ping google.com
ping: unknown host google.com

```
I really dont know whats going on everything was fine until yesterday.

---

