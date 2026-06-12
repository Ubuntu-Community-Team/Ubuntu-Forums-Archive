---
title: "Is there an Ubuntu Telephone fax app?"
date: 2014-09-03
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-09-03
Is there an Ubuntu Telephone fax app? In other words, a program that can send faxes over the phone line (rather than the over the internet)? I am thinking that sending a fax that includes confidential info over a phone line would be more secure than sending a fax (fteleully or partially) over the internet.

Thanks,

R.

---

### Post by dgriffiths on 2014-09-04
You can try EFax (efax-gtk is the Gnome client).

---

### Post by AbleTassie on 2014-09-04
Thanks d,

I will give this a try.

R.

---

### Post by AbleTassie on 2014-09-04
I tried to fax over the telephone line using **efax-gtk** (with the ethernet cable disconnected) and got the error message below. I am thinking this has to do with the settings. Can anybody tell me how to set my setting so I can fax over the phone line?

   **Error message:** 

Socket running on port 9900

 [COLOR=#c5000b]efax-0.9a: 11:13: 53 Error: can't open serial port/dev[/COLOR]
 [COLOR=#c5000b]ttyS1: permission denied[/COLOR]
 efax-0.9a: 11:13: 53 failed page home/name/faxout/
 Doc1.pdf.001
 [COLOR=#000000]efax-0.9a: 11:13: 53 finished unrecoverable error[/COLOR]



Thanks,

R.

---

### Post by sandyd on 2014-09-04
Try running (where *username* is your username)
```

sudo usermod -a -G dialout *username*
```

Then login/logout.

---

### Post by JKyleOKC on 2014-09-04
To do this, you have to have a fax-capable modem installed, and recently manufactured systems don't seem to have such beasts any more since very few people use dialup connections these days. When you install such a modem, it should walk you through its basic setup steps and create the necessary serial port.

You can buy such a modem that plugs into a USB port for around $50 USD (approximately, the prices vary widely), and some of them claim to be Linux compatible. Beware of those that depend on Windows to do most of the work; many of these aren't compatible at all with any flavor of Linux, and those that are can take many hours of fiddling to get them into operation.

After years of using such fax applications in Windows, I finally went back to using a separate fax machine once I went to an all-Xubuntu office, even though one of my boxes did come from the factory with a fax modem. Unfortunately it was one of the kind that's not compatible with Linux.

---

### Post by AbleTassie on 2014-09-04
> **sandyd said:**
> Try running (where *username* is your username)
```

sudo usermod -a -G dialout *username*
```

I tried this as terminal command, but I get the same error message.

Thanks,

R.

---

### Post by sandyd on 2014-09-04
> **RMcGinnis said:**
> I tried this as terminal command, but I get the same error message.

Thanks,

R.

Did you try logging out/in? (Forgot to add that in...)

---

### Post by AbleTassie on 2014-09-04
> **JKyleOKC said:**
> To do this, you have to have a fax-capable modem installed, and recently manufactured systems don't seem to have such beasts any more since very few people use dialup connections these days. When you install such a modem, it should walk you through its basic setup steps and create the necessary serial port.


J.

Thanks, my PC is over 8 1/2 years old, so maybe it has such a fax-capable modem. It is a Toshiba Satellite L25-S1216. 
Based on looking at pp. 130-131 of the User's Guide see 
( [http://support.toshiba.com/support/staticContentDetail?contentId=1127355&isFromTOCLink=false](http://support.toshiba.com/support/staticContentDetail?contentId=1127355&isFromTOCLink=false) ) which says:[B]
*"Connecting the modem to a telephone line*[/B][I] Before you can communicate using the modem, you need to connect it to a telephone line. Your computer’s built-in modem port provides an RJ-11 jack, allowing you to connect the modem to a standard voice-grade telephone line.        ...   ...  Now you are ready to send a fax or use the modem to connect
to an online service or the Internet." [/I]

It looks like it does have a fax-capable modem.

The specs don't seem to be very helpful, although RJ-11 is listed as the port is apparently for a standard voice grade telephone line.
In the Specs ( [http://support.toshiba.com/support/staticContentDetail?contentId=1250449&isFromTOCLink=false](http://support.toshiba.com/support/staticContentDetail?contentId=1250449&isFromTOCLink=false) ) under ports is says RJ-11 for the modem port. It also says  "Toshiba V.92 software modem" under Communications. And it says the maximum modem speed is 53 kbps. Other than that there is nothing in the specs.

Any comments anybody?

Thanks,

R.

---

### Post by JKyleOKC on 2014-09-04
Yes, RJ-11 is the standard single-line telephone connector. You'll probably need to get a little RJ-11 splitter so you don't have to unplug your landline phone from the jack, and a cord to use with it if the original packed with your computer has gotten away.

The reference to a "software modem" indicates that it has one of the "Winmodem" units, sometimes called a "vampire modem" since it sucks resources out of your main computer. It may, or may not, be compatible with Linux. For starters, enter "sudo lshw" and post the output here between "code" tags; this should tell us the manufacturer and model number of the Winmodem in your machine, and we can go from there. As I said, though, many such modems are totally incompatible and the rest require lots of fiddling to make them work. I got as far as getting mine to **almost** work here but could not get it to use a device name that efax would recognize...

---

### Post by AbleTassie on 2014-09-04
> **sandyd said:**
> Did you try logging out/in? (Forgot to add that in...)

Sandy,

Thanks. I forgot to log out & log in after executing the terminal command you gave me. After logging out and logging back in, I am still getting an error message, but it is somewhat different now. It is:

   Socket running on port 9900
 efax-9.0a: 13:12:14: opened /dev/tty1
 [COLOR=#c5000b]efax-9.0a: 13:12:14: Error: tcgetattr on fd=7 failed:[/COLOR]
 [COLOR=#c5000b]input/output error [/COLOR] 
 [COLOR=#000000]efax-9.0a: 13:12:14 failed page/home/name/faxout/testing.pdf.001[/COLOR]
 [COLOR=#c5000b]efax-9.0a: 13:12:14 Error: fax device write: input/output error [/COLOR] 

Thanks,

R.

---

### Post by AbleTassie on 2014-09-04
> **JKyleOKC said:**
>  For starters, enter "sudo lshw" and post the output here between "code" tags; this should tell us the manufacturer and model number of the Winmodem in your machine, and we can go from there. As I said, though, many such modems are totally incompatible and the rest require lots of fiddling to make them work. I got as far as getting mine to **almost** work here but could not get it to use a device name that efax would recognize...

J.

Thanks, I get a whole LONG list of output. [B]

Regarding modem I get:[/B]

   ```
communication 
              description: Modem 
              product: IXP SB400 AC'97 Modem Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 14.6 
              bus info: pci@0000:00:14.6 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: msi generic bus_master cap_list 
              configuration: driver=snd_atiixp_modem latency=64 mingnt=2 
              resources: irq:17 memory:c0007800-c00078ff
```
[B]
The entire output is below:[/B]

   

```
name                       
     description: Notebook 
     product: Satellite L25 
     vendor: TOSHIBA 
     version: PSL2XU-02400J 
     serial: 16089282W 
     width: 32 bits 
     capabilities: smbios-2.34 dmi-2.34 smp-1.4 smp 
     configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=A096D8F8-08BE-D911-B20F-001636200EBE 
   *-core 
        description: Motherboard 
        product: Satellite L25 
        vendor: TOSHIBA 
        physical id: 0 
        version: Not Applicable 
        serial: 1234567890 
      *-firmware 
           description: BIOS 
           vendor: TOSHIBA 
           physical id: 0 
           version: V1.90 
           date: 01/05/06 
           size: 100KiB 
           capacity: 448KiB 
           capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb smartbattery biosbootspecification 
      *-cpu 
           description: CPU 
           product: Intel(R) Celeron(R) M processor         1.60GHz 
           vendor: Intel Corp. 
           physical id: 4 
           bus info: cpu@0 
           version: 6.13.8 
           slot: U23 
           size: 1600MHz 
           capacity: 1600MHz 
           width: 32 bits 
           clock: 100MHz 
           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts 
         *-cache:0 
              description: L1 cache 
              physical id: 5 
              slot: CACHE1 
              size: 16KiB 
              capacity: 16KiB 
              capabilities: asynchronous internal write-back 
         *-cache:1 
              description: L2 cache 
              physical id: 6 
              slot: CACHE2 
              size: 1MiB 
              capabilities: burst external write-back 
      *-cache 
           description: L2 cache 
           physical id: 7 
           slot: L2 Cache 
           size: 1MiB 
           capacity: 1MiB 
           capabilities: burst internal write-back 
      *-memory 
           description: System Memory 
           physical id: d 
           slot: System board or motherboard 
           size: 1280MiB 
         *-bank:0 
              description: DIMM DRAM Synchronous [empty] 
              physical id: 0 
              slot: J400 
         *-bank:1 
              description: DIMM DRAM Synchronous [empty] 
              physical id: 1 
              slot: J401 
         *-bank:2 
              description: DIMM DRAM Synchronous 
              physical id: 2 
              slot: J501 
              size: 1GiB 
              width: 64 bits 
         *-bank:3 
              description: DIMM DRAM Synchronous 
              physical id: 3 
              slot: J500 
              size: 256MiB 
              width: 64 bits 
      *-pci 
           description: Host bridge 
           product: RC410 Host Bridge 
           vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
           physical id: 100 
           bus info: pci@0000:00:00.0 
           version: 01 
           width: 32 bits 
           clock: 66MHz 
           configuration: latency=64 
         *-pci:0 
              description: PCI bridge 
              product: RC4xx/RS4xx PCI Bridge [int gfx] 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 1 
              bus info: pci@0000:00:01.0 
              version: 00 
              width: 32 bits 
              clock: 66MHz 
              capabilities: pci normal_decode bus_master cap_list 
              resources: ioport:9000(size=4096) memory:c0100000-c01fffff memory:d0000000-dfffffff 
            *-display 
                 description: VGA compatible controller 
                 product: RC410M [Mobility Radeon Xpress 200M] 
                 vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
                 physical id: 5 
                 bus info: pci@0000:01:05.0 
                 version: 00 
                 width: 32 bits 
                 clock: 66MHz 
                 capabilities: pm msi vga_controller bus_master cap_list rom 
                 configuration: driver=radeon latency=66 mingnt=8 
                 resources: irq:17 memory:d0000000-dfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff 
         *-usb:0 
              description: USB controller 
              product: IXP SB4x0 USB Host Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 13 
              bus info: pci@0000:00:13.0 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: msi ohci bus_master cap_list 
              configuration: driver=ohci-pci latency=64 
              resources: irq:19 memory:c0004000-c0004fff 
         *-usb:1 
              description: USB controller 
              product: IXP SB4x0 USB Host Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 13.1 
              bus info: pci@0000:00:13.1 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: msi ohci bus_master cap_list 
              configuration: driver=ohci-pci latency=64 
              resources: irq:19 memory:c0005000-c0005fff 
         *-usb:2 
              description: USB controller 
              product: IXP SB4x0 USB2 Host Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 13.2 
              bus info: pci@0000:00:13.2 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: pm msi ehci bus_master cap_list 
              configuration: driver=ehci-pci latency=64 
              resources: irq:19 memory:c0006000-c0006fff 
         *-serial 
              description: SMBus 
              product: IXP SB4x0 SMBus Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 14 
              bus info: pci@0000:00:14.0 
              version: 82 
              width: 32 bits 
              clock: 66MHz 
              configuration: driver=piix4_smbus latency=0 
              resources: irq:0 ioport:8040(size=16) memory:c0007000-c00073ff 
         *-ide 
              description: IDE interface 
              product: IXP SB4x0 IDE Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 14.1 
              bus info: pci@0000:00:14.1 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: ide msi bus_master cap_list 
              configuration: driver=pata_atiixp latency=64 
              resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8410(size=16) 
         *-isa 
              description: ISA bridge 
              product: IXP SB4x0 PCI-ISA Bridge 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 14.3 
              bus info: pci@0000:00:14.3 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: isa bus_master 
              configuration: latency=0 
         *-pci:1 
              description: PCI bridge 
              product: IXP SB4x0 PCI-PCI Bridge 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 14.4 
              bus info: pci@0000:00:14.4 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: pci subtractive_decode bus_master 
              resources: ioport:a000(size=4096) memory:c0200000-c02fffff memory:48000000-4bffffff 
            *-pcmcia 
                 description: CardBus bridge 
                 product: PCI1510 PC card Cardbus Controller 
                 vendor: Texas Instruments 
                 physical id: 1 
                 bus info: pci@0000:09:01.0 
                 version: 00 
                 width: 32 bits 
                 clock: 33MHz 
                 capabilities: pcmcia bus_master cap_list 
                 configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 
                 resources: irq:20 memory:4c000000-4c000fff ioport:a400(size=256) ioport:a800(size=256) memory:48000000-4bffffff memory:50000000-53ffffff 
            *-network:0 
                 description: Ethernet interface 
                 product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter 
                 vendor: Realtek Semiconductor Co., Ltd. 
                 physical id: 2 
                 bus info: pci@0000:09:02.0 
                 logical name: eth0 
                 version: 10 
                 serial: 00:16:36:20:0e:be 
                 size: 100Mbit/s 
                 capacity: 100Mbit/s 
                 width: 32 bits 
                 clock: 33MHz 
                 capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
                 configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s 
                 resources: irq:21 ioport:a000(size=256) memory:c0210000-c02100ff 
            *-network:1 
                 description: Wireless interface 
                 product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] 
                 vendor: Qualcomm Atheros 
                 physical id: 4 
                 bus info: pci@0000:09:04.0 
                 logical name: wlan0 
                 version: 01 
                 serial: 00:11:f5:df:2e:9f 
                 width: 32 bits 
                 clock: 33MHz 
                 capabilities: pm bus_master cap_list ethernet physical wireless 
                 configuration: broadcast=yes driver=ath5k driverversion=3.13.0-35-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg 
                 resources: irq:22 memory:c0200000-c020ffff 
         *-multimedia 
              description: Multimedia audio controller 
              product: IXP SB400 AC'97 Audio Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 14.5 
              bus info: pci@0000:00:14.5 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: msi bus_master cap_list 
              configuration: driver=snd_atiixp latency=64 mingnt=2 
              resources: irq:17 memory:c0007400-c00074ff 
         *-communication 
              description: Modem 
              product: IXP SB400 AC'97 Modem Controller 
              vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
              physical id: 14.6 
              bus info: pci@0000:00:14.6 
              version: 80 
              width: 32 bits 
              clock: 66MHz 
              capabilities: msi generic bus_master cap_list 
              configuration: driver=snd_atiixp_modem latency=64 mingnt=2 
              resources: irq:17 memory:c0007800-c00078ff 
      *-scsi:0 
           physical id: 1 
           logical name: scsi0 
           capabilities: emulated 
         *-disk 
              description: ATA Disk 
              product: FUJITSU MHV2100A 
              vendor: Fujitsu 
              physical id: 0.0.0 
              bus info: scsi@0:0.0.0 
              logical name: /dev/sda 
              version: 0000 
              serial: NS16T6927PTM 
              size: 93GiB (100GB) 
              capabilities: partitioned partitioned:dos 
              configuration: ansiversion=5 sectorsize=512 signature=000a0d13 
            *-volume:0 
                 description: Windows NTFS volume 
                 physical id: 1 
                 bus info: scsi@0:0.0.0,1 
                 logical name: /dev/sda1 
                 version: 3.1 
                 serial: d44ff3dc-3fec-a24b-ab76-e43e7673ad86 
                 size: 44GiB 
                 capacity: 44GiB 
                 capabilities: primary bootable ntfs initialized 
                 configuration: clustersize=4096 created=2004-03-08 08:55:09 filesystem=ntfs label=SQ003947 modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true 
            *-volume:1 
                 description: Extended partition 
                 physical id: 2 
                 bus info: scsi@0:0.0.0,2 
                 logical name: /dev/sda2 
                 size: 48GiB 
                 capacity: 48GiB 
                 capabilities: primary extended partitioned partitioned:extended 
               *-logicalvolume:0 
                    description: Linux swap / Solaris partition 
                    physical id: 5 
                    logical name: /dev/sda5 
                    capacity: 1149MiB 
                    capabilities: nofs 
               *-logicalvolume:1 
                    description: Linux filesystem partition 
                    physical id: 6 
                    logical name: /dev/sda6 
                    logical name: / 
                    capacity: 47GiB 
                    configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted 
      *-scsi:1 
           physical id: 2 
           logical name: scsi1 
           capabilities: emulated 
         *-cdrom 
              description: DVD reader 
              product: CDW/DVD TS-L462D 
              vendor: TSSTcorp 
              physical id: 0.0.0 
              bus info: scsi@1:0.0.0 
              logical name: /dev/cdrom 
              logical name: /dev/sr0 
              version: MO00 
              capabilities: removable audio cd-r cd-rw dvd 
              configuration: ansiversion=5 status=nodisc 
   *-battery 
        physical id: 1 
        slot: Left Front 
   *-remoteaccess UNCLAIMED 
        vendor: Intel 
        physical id: 2 
        capabilities: inbound
```

---

### Post by JKyleOKC on 2014-09-04
I'm not familiar with that AMD modem so will have to search the web to see if it's at all compatible with Linux. Unfortunately my own system here has gone a bit crazy; one of my network cards has vanished completely for some reason during a reboot within the past half hour! It'll take me a while to get it working again enough to do the search; sorry!!!

---

### Post by sandyd on 2014-09-04
> **RMcGinnis said:**
> Sandy,

Thanks. I forgot to log out & log in after executing the terminal command you gave me. After logging out and logging back in, I am still getting an error message, but it is somewhat different now. It is:

   Socket running on port 9900
 efax-9.0a: 13:12:14: opened /dev/tty1
 [COLOR=#c5000b]efax-9.0a: 13:12:14: Error: tcgetattr on fd=7 failed:[/COLOR]
 [COLOR=#c5000b]input/output error [/COLOR] 
 [COLOR=#000000]efax-9.0a: 13:12:14 failed page/home/name/faxout/testing.pdf.001[/COLOR]
 [COLOR=#c5000b]efax-9.0a: 13:12:14 Error: fax device write: input/output error [/COLOR] 

Thanks,

R.
That error is modem-specific, you will have to make sure that your modem has the propper driver in order for efax to work properly (as efax assumes your modem works)

Edit:
It seems you need slmodem/snd-atiixp-modem ->[https://wiki.debian.org/slmodem](https://wiki.debian.org/slmodem)
On closer inspection, it seems that the driver is already loaded

---

### Post by AbleTassie on 2014-09-04
> **sandyd said:**
> That error is modem-specific, you will have to make sure that your modem has the propper driver in order for efax to work properly (as efax assumes your modem works)

Edit:
It seems you need slmodem/snd-atiixp-modem ->[https://wiki.debian.org/slmodem](https://wiki.debian.org/slmodem)
On closer inspection, it seems that the driver is already loaded

Thanks Sandy,

So it sounds like you beileve I need new hardware, such as a modem that connects to a USB port. Is that correct? 

I think J. said that such modems run about $50.

R.

---

### Post by JKyleOKC on 2014-09-05
Before you rush out to buy another modem, make sure that you have the "*slmodemd*" driver installed in addition to the one that's listed in your "lshw" report. SandyD's link indicates that the *slmodemd* driver controls the modem side of the device while the one that's listed in your report controls the sound side. Both probably need to be present for full operation -- and according to that link, you're one of the lucky people with a device that's compatible with Linux!

EDIT: You may need to play with the configuration of efax to establish communication between the program and the modem, too. That's where I ran into so many problems trying to make my setup work...

I got my system back up after a couple of hours of diagnosis but still haven't found out the root cause, so I may be in and out of this thread before it winds up...

---

### Post by pqwoerituytrueiwoq on 2014-09-05
if you do go out and buy a modem good luck, finding modems with linux support is a real PITA, and getting a 64bit driver is probably impossible, unless the chip's drivers had there source code released even then is ia lily nobody bothered to make one
now if you get a USB 54k modem that is another story (as opposed to a PCI modem), but those cost around 25 usd

---

### Post by AbleTassie on 2014-09-08
> **JKyleOKC said:**
> Before you rush out to buy another modem, **make sure that you have the "*slmodemd*" driver installed in addition to the one that's listed in your "lshw" report.** SandyD's link indicates that the *slmodemd* driver controls the modem side of the device while the one that's listed in your report controls the sound side. Both probably need to be present for full operation -- and according to that link, you're one of the lucky people with a device that's compatible with Linux!

EDIT: You may need to play with the configuration of efax to establish communication between the program and the modem, too. That's where I ran into so many problems trying to make my setup work...

I got my system back up after a couple of hours of diagnosis but still haven't found out the root cause, so I may be in and out of this thread before it winds up...

Thanks J. 

I will look at this and try to make sure I have the "slmodemd" driver installed. It looks like it will take some time for me to be sure I have some understanding of that page at SandyD's link.

R.

---

### Post by AbleTassie on 2014-09-10
> **pqwoerituytrueiwoq said:**
> if you do go out and buy a modem good luck, finding modems with linux support is a real PITA, and getting a 64bit driver is probably impossible, unless the chip's drivers had there source code released even then is ia lily nobody bothered to make one
now if you get a USB 54k modem that is another story (as opposed to a PCI modem), but those cost around 25 usd

Thanks pqwoerituytrueiwoq,

R.

---

### Post by rbmorse on 2014-09-11
As an aside, I was at the local Goodwill store dropping some stuff off for donations and they had a stand-alone Ricoh fax machine on the shelf for $25. Looked nice and clean, probably needed ink refil. if you need fax capability on a regular basis might check the local thrift stored and pawn shops.

---

