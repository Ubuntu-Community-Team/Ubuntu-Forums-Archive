---
title: "[SOLVED] I have no device manager!"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by RoyHobbs on 2008-08-21
Hi

I installed ubuntu 8.04 LTS last night as a dual boot on a windows XP pc.  Everything went fine (I think?) until I tried to access the internet through a wireless connection and couldn't.  I went to the user guide and the text says: 

Check for device recognition
Open Device Manager (System &#8594; Preferences &#8594; Hardware Information).

Unfortunately when I go to System - Preferences there is no Hardware option??????  I am writing this paost from another (home) pc so it may take me sometime to respond.  Any help for a newbie on this and wireless networking in general would be most appreciated!

---

### Post by bitninja on 2008-08-21
What wireless chipset are you using?

---

### Post by adult swim on 2008-08-21
he probably cant figure out the wireless chipset without the hardware manager.
roy, if you go to a terminal (applications/accessories/terminal) and type in ```
lspci
``` it will return your hardware information.

---

### Post by bitninja on 2008-08-21
Windows should be able to tell him too, either way.

---

### Post by RoyHobbs on 2008-08-21
> **bitninja said:**
> What wireless chipset are you using?

I "think" I am using the following:

Intel Corp 82562V 10/100 Network Connection (Rev 02)
Atheros Communications Inc AR5413 802.11abs NIC (Rev 01)

---

### Post by bitninja on 2008-08-21
Okay well I've never had any problems with Atheros chipsets...are you sure the hardware manager isn't under System > Administration? I'm not at my Ubuntu system to check at the moment...

---

### Post by cariboo on 2008-08-21
There is no device manager installed by default on hardy, most of us either know to use lspci or they see it here in the forums. Personally I think it should be part of the basic installation, but I know they are running out of room on the install cd's so some things have to be left off. To install gnome-device-manager search for it in either Add/Remove programs or Synaptic Package Manager. Alternately you can install it from the command line.

Jim

---

### Post by DemonBob on 2008-08-21
System -> Administration -> Hardware Driver

Make sure the Atheros driver is enabled. If not enable it, it should require a reboot.

If this does not work. The current driver in Hardy may not support the chip. You can update the driver, by following the steps below.  

Download both: 
[http://ubuntu.cs.utah.edu/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

Put them on a USB stick or CD, the copy them to the Ubuntu desktop

Goto a terminal. 

```

cd Desktop
sudo dpkg -i build-essential_11.3ubuntu1_i386.deb
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-current
sudo make
sudo make install

```

Then reboot.

---

### Post by prshah on 2008-08-21
> **RoyHobbs said:**
> 
Intel Corp 82562V 10/100 Network Connection (Rev 02)
Atheros Communications Inc AR5413 802.11abs NIC (Rev 01)

Pretty detailed thought :)

The Intel is the wired network, you can forget about that.

Atheros is generally supported out-of-the-box, but you may need to enable restricted drivers (The access for which depends on which Ubuntu you are using: Xubuntu, Ubuntu, or Kubuntu, usually Ubuntu). Look under System-Administration-Restricted driver manager (or Hardware drivers), or in case of Xubuntu, it will be under Applications-System-Hardware drivers (or Restricted driver manager). If you find an entry for Atheros, enable it.

Once you have enabled the adapter, you can check as well as start using by following this [simple step-by-step guide]("http://ubuntuforums.org/showpost.php?p=4723545&postcount=1"). Since your card should be already recognized (the guide will tell you how you can find out if it's recognized or not), you can jump straight to step 9. The guide shows expected outputs so you can know what to expect from any command.

Post back here if you run into difficulties.

---

### Post by RoyHobbs on 2008-08-21
> **adult swim said:**
> he probably cant figure out the wireless chipset without the hardware manager.
roy, if you go to a terminal (applications/accessories/terminal) and type in ```
lspci
``` it will return your hardware information.

Hi, when I ran lspci I got the following:

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
03:00.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
03:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:03.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)

---

### Post by RoyHobbs on 2008-08-21
> **DemonBob said:**
> System -> Administration -> Hardware Driver

Make sure the Atheros driver is enabled. If not enable it, it should require a reboot.

If this does not work. The current driver in Hardy may not support the chip. You can update the driver, by following the steps below.  

Download both: 
[http://ubuntu.cs.utah.edu/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

Put them on a USB stick or CD, the copy them to the Ubuntu desktop

Goto a terminal. 

```

cd Desktop
sudo dpkg -i build-essential_11.3ubuntu1_i386.deb
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-current
sudo make
sudo make install

```

Then reboot.

Hi, still didn't work.  When I ran the code I got the following reply:

(Reading database ... 95853 files and directories currently installed.)
Preparing to replace build-essential 11.3ubuntu1 (using build-essential_11.3ubuntu1_i386.deb) ...
Unpacking replacement build-essential ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev is not installed.
  Package libc-dev is not installed.
 build-essential depends on g++ (>= 4:4.1.1); however:
  Package g++ is not installed.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not installed.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential

---

### Post by RoyHobbs on 2008-08-21
> **prshah said:**
> Pretty detailed thought :)

The Intel is the wired network, you can forget about that.

Atheros is generally supported out-of-the-box, but you may need to enable restricted drivers (The access for which depends on which Ubuntu you are using: Xubuntu, Ubuntu, or Kubuntu, usually Ubuntu). Look under System-Administration-Restricted driver manager (or Hardware drivers), or in case of Xubuntu, it will be under Applications-System-Hardware drivers (or Restricted driver manager). If you find an entry for Atheros, enable it.

Once you have enabled the adapter, you can check as well as start using by following this [simple step-by-step guide]("http://ubuntuforums.org/showpost.php?p=4723545&postcount=1"). Since your card should be already recognized (the guide will tell you how you can find out if it's recognized or not), you can jump straight to step 9. The guide shows expected outputs so you can know what to expect from any command.

Post back here if you run into difficulties.

Hi, I started at step 9 but no network was found, so I went to step 1 and at step 2 got the following:

andrei@Home-downstairs:~$ sudo apt-get install ndiswrapper-utils*
[sudo] password for andrei: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils*
andrei@Home-downstairs:~$

---

### Post by sdowney717 on 2008-08-21
lshw lists out everything regarding hardware in the box

---

### Post by RoyHobbs on 2008-08-21
> **sdowney717 said:**
> lshw lists out everything regarding hardware in the box

Hi, I ran lshw and below is the output:

WARNING: you should run this program as super-user.
home-downstairs           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2025MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G70 [GeForce 7600 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82562V 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:18:f3:9c:08:0c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-2 latency=0 module=e1000 multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-multimedia
                description: Multimedia controller
                product: SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 0
                bus info: pci@0000:03:00.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84 module=saa7134
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12 module=ohci1394
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5413 802.11abg NIC
                vendor: Atheros Communications Inc.
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=168 maxlatency=28 mingnt=10
        *-isa
             description: ISA bridge
             product: 82801HH (ICH8DH) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi:0
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@7
       logical name: scsi7
       capabilities: scsi-host
       configuration: driver=usb-storage

---

### Post by prshah on 2008-08-21
> **RoyHobbs said:**
> Hi, I started at step 9 but no network was found, 


Can you post the output of ```
iwconfig
```

---

### Post by RoyHobbs on 2008-08-21
> **prshah said:**
> Can you post the output of ```
iwconfig
```

Output:

andrei@home-downstairs:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

andrei@home-downstairs:~$

---

### Post by adult swim on 2008-08-21
roy it looks like you may  not have all of the repositories enabled and that is why none of the packages you are trying to install are downloading. go to synaptic packagae manager (system/administration/synaptic package manager)  and then click on settings/repositories.  make sure that the first four boxes are checked  then go to the main synaptic package manager screen and click the reload icon in the top left. you can close the synaptic window and then try that walkthrough again.

---

### Post by Kyle1981 on 2008-08-21
no device management. 
if your wireless card work properly, please click the network icon on panel with the left button of mouse, you will see your SSID of wireless.

---

### Post by RoyHobbs on 2008-08-22
> **adult swim said:**
> roy it looks like you may  not have all of the repositories enabled and that is why none of the packages you are trying to install are downloading. go to synaptic packagae manager (system/administration/synaptic package manager)  and then click on settings/repositories.  make sure that the first four boxes are checked  then go to the main synaptic package manager screen and click the reload icon in the top left. you can close the synaptic window and then try that walkthrough again.

I get a connection error when I try this, as the synaptic manager appears to be looking for an internet connection:(

---

### Post by decoherence on 2008-08-22
> I get a connection error when I try this, as the synaptic manager appears to be looking for an internet connection

ah ha!

thing is, i don't think the restricted driver for atheros ships with ubuntu. in other words, you need an internet connection in order to get your internet connection working. silly, eh?

can you get online using your wired ethernet? if so, get connected and run System > Administration -> Update Manager and make sure everything is up to date. During this process you will likely get a popup in the top taskbar telling you restricted drivers are available. If you don't, go to System > Administration > Hardware Drivers and try enabling it again.

---

### Post by RoyHobbs on 2008-08-25
Hi

After hours of frustration and trawelling through the forums I was unable to solve this issue and I was unable to find anyone else who has solved it.  I had an old dynalink wireless usb stick which I plugged in and after playing with the router I was able to do all the updates etc but I still had no luck with the atheros chipset, so I am just going to continue using the wiresless usb.  Thansk to everyone for their help and advice:)

---

### Post by sunnyroy on 2009-04-05
hope this helps I have the same ar5314, couldnt get it to work until I did this:

get the windows driver from [http://www.downloadatoz.com/driver/download_4858.html](http://www.downloadatoz.com/driver/download_4858.html)

locate the .inf file (its in the ABG folder)

put this folder on your desktop (you may have to adjust your privileges in properties to gain access to this file)

goto the synaptic package manager and get "ndisgtk"

when you have done that go to system>administration>windows wireless drivers

select install new driver, when it asks for the location, select your previously downloaded .inf file.

good luck hope it works for you

---

