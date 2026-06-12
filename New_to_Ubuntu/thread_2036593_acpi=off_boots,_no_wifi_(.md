---
title: "acpi=off boots, no wifi :("
date: 2012-08-02
forum: New to Ubuntu
---

### Post by AoFhEkOl on 2012-08-02
Hello, I have a problem with Ubuntu. I can boot with acpi=off but no WiFi. Acpi=ht boots but as soon as it connects to WiFi it restarts. Any ideas? I've tried the basic boot options with no luck.

---

### Post by AoFhEkOl on 2012-08-12
No one? I really want to use Ubuntu. Someone must be able to help me. 
 
Windows works fine, I have to change the processor driver to "Intel proccessor driver" for it to work, otherwise I get the black screens and restarts on windows.
 
Specs 
Intel processor dual core 2.53ghz p8700
ATI mobility radeon 512mb 4650
4.0gb ram
Khlb2 motherboard - compal
 
How can I troubleshoot this?

---

### Post by AoFhEkOl on 2012-08-12
Shall i move my thread?

---

### Post by Bashing-om on 2012-08-12
no, not needed to move thread ,,,, we are all pretty busy right now ... lemme get caught up a nit and I will see waht I can do. Be advised I am not to expierienced with wifi ... but I bet we can muddle throught this togather.
[INDENT]kindly regarding
[/INDENT]

---

### Post by AoFhEkOl on 2012-08-12
Thank you, any help is much appreciated :).

---

### Post by Bashing-om on 2012-08-12
Bowater ;
  I am back .... lets get some additional info in order to assist you.
1. what method did you use to install ubuntu.
2. what version of ubuntu are you using.
3.when you right click on network connection icon, what options are displayed ?
 
[INDENT]awaiting <==BDQ
[/INDENT]

---

### Post by wildmanne39 on 2012-08-12
Hi, acpi=off does turn off the wifi on some computers so you will probably need to find another parameter that you can boot with.

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by AoFhEkOl on 2012-08-13
@Bashing-om
Ok,
i installed using the live cd.
Ubuntu 12.04
wired network - disconnected
Wireless network - disconnected
Connect to hidden wireless network.... (greyed out)
Create new wireless network... (greyed out)
Vpn connections
Ticked - enable networking
Ticked - enable wireless
Connection information (greyed out)
Edit connections

---

### Post by AoFhEkOl on 2012-08-13
@[[COLOR=#DD4814]**wildmanne39**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533")


*************** info trace ****************



**** uname -a ****


Linux tim-desktop 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"


**** lspci ****


0e:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card [1a3b:1026]
    Kernel driver in use: ath5k
--
14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: COMPAL Electronics Inc Device [14c0:003e]
    Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1c7a:0801 LighTuning Technology Inc. Fingerprint Reader
Bus 002 Device 003: ID 04f2:b109 Chicony Electronics Co., Ltd 


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
joydev                 17393  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
vesafb                 13516  1 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174134  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
fglrx                2909855  116 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath5k                 145127  0 
ath                    19387  1 ath5k
uvcvideo               67203  0 
mac80211              436455  1 ath5k
videodev               86588  1 uvcvideo
psmouse                72919  0 
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  3 ath5k,ath,mac80211
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17406  0 
memstick               15857  1 jmb38x_ms
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     No scan results



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search Belkin


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   15.521123] ath5k 0000:0e:00.0: PCI->APIC IRQ transform: INT A -> IRQ 18
[   15.521135] ath5k 0000:0e:00.0: setting latency timer to 64
[   15.521181] ath5k 0000:0e:00.0: registered as 'phy0'
[   16.026543] ath: EEPROM regdomain: 0x60
[   16.026545] ath: EEPROM indicates we should expect a direct regpair map
[   16.026548] ath: Country alpha2 being used: 00
[   16.026550] ath: Regpair used: 0x60
[   16.032189] Registered led device: ath5k-phy0::rx
[   16.032233] Registered led device: ath5k-phy0::tx
[   16.032243] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   16.452730] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.453879] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************

---

### Post by AoFhEkOl on 2012-08-13
So what's next? :D

---

### Post by wildmanne39 on 2012-08-13
Hi, that is very strange output, are you still booting with acpi=off? if so try with nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
acpi=off is the last option you want to try because it will most likely disable your fans too.
Thanks

---

### Post by AoFhEkOl on 2012-08-14
ok sorry...
 
[http://www.2shared.com/document/BvThpfrt/netinfo.html](http://www.2shared.com/document/BvThpfrt/netinfo.html)
 
I just had enough time to do that before it black screened and restarted....

---

### Post by Bashing-om on 2012-08-14
Bowater;

 I am looking....
1. Are you on a router ... (gateway addressing set for what is a router address)?
2. IF you do not have a router on your LAN where did you get the DNS (is your router providing this service[I would find this unusual in a small environment ]? However; I would not expect the DNS sloppyation to drop the connection, just not able to find any web sites.
 Just to try and shorten a long process ... can you bring up your wireless access from the command line ?.... if so can you ping any outside servers ?
 Let me look over the links you provided and see if I can get an idea as to what is going on...

Talk to you later.

---

### Post by Bashing-om on 2012-08-14
Bowater;

  I am confused as to the originating nature of your present problem.
Is the present situation as a result of attempting to install the Share2 protocol ?

  If so are you certain you downloaded for ubuntu ? As I found this:[http://www.2shared.com/file/V9bsXqim/filestorrentwordpresscomubuntu.html](http://www.2shared.com/file/V9bsXqim/filestorrentwordpresscomubuntu.html)

please advise us
[INDENT]kindest regards <===BDQ
[/INDENT]

---

### Post by AoFhEkOl on 2012-08-14
Yes am using a router, im in norway so im using the default dns.
 
All ive done is install ubuntu, that i downloaded from the ubuntu website.
 
the only boot command i can use where the laptop stays on is acpi=off, so its difficult to do anything with with the command nomodeset. It blackscreens then reboots. What other commands are there?

---

### Post by wildmanne39 on 2012-08-14
Hi, you need to deal with the acpi issue first then your wireless and many other things should work, you can unplug your wired connection and see if your wireless will come on then but I doubt it.

You will probably have to start a new thread for just the acpi issue but you can post the output of:
```
dmesg | grep -i acpi
dmesg | grep -i error
dmesg | grep -i warn 
```
here by clicking on new reply and click # then paste the information between the brackets.
Thanks

---

### Post by AoFhEkOl on 2012-08-16
```
tim@tim-desktop:~$ dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 00000000bdf55000 - 00000000bdf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bdfe4000 - 00000000bdffd000 (ACPI data)
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=fa16961b-8316-4938-a1b7-f17f0fb506b7 ro quiet splash acpi=off vt.handoff=7
[    0.257850] PM: Registering ACPI NVS region at bdf55000 (303104 bytes)
[    0.261086] ACPI: Interpreter disabled.
[    0.290306] pnp: PnP ACPI: disabled
[   17.881126] [fglrx] ACPI is disabled on this system

tim@tim-desktop:~$ dmesg | grep -i error
[   16.709553] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

tim@tim-desktop:~$ dmesg | grep -i warn
Nothing
```

That was with acpi=off.  I will try with nomodeset but it depends how long it will stay on

---

### Post by AoFhEkOl on 2012-08-16
```
tim@tim-desktop:~$ dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 00000000bdf55000 - 00000000bdf9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bdfe4000 - 00000000bdffd000 (ACPI data)
[    0.000000] ACPI: RSDP 000f6ad0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bdff70ab 0007C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP bdfe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bdfe9000 05A6F (v02 Intel  CANTIGA  06040000 INTL 20060608)
[    0.000000] ACPI: FACS bdf8efc0 00040
[    0.000000] ACPI: APIC bdffcd1e 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET bdffcd86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bdffcdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIX bdffcdfa 00176 (v01 Compal JHL00_90 06040000 TBD  00000001)
[    0.000000] ACPI: APIC bdffcf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bdffcfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: TCPA bdfef000 00032 (v00                 00000000      00000000)
[    0.000000] ACPI: SSDT bdfe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bdfe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bdfe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.008786] ACPI: Core revision 20110623
[    0.153835] PM: Registering ACPI NVS region at bdf55000 (303104 bytes)
[    0.153835] ACPI: bus type pci registered
[    0.156992] ACPI: Added _OSI(Module Device)
[    0.156994] ACPI: Added _OSI(Processor Device)
[    0.156996] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.156998] ACPI: Added _OSI(Processor Aggregator Device)
[    0.158382] ACPI: EC: Look up EC in DSDT
[    0.161847] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.162198] ACPI: SSDT bdf1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.162532] ACPI: Dynamic OEM Table Load:
[    0.162535] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.162656] ACPI: SSDT bdf18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.162973] ACPI: Dynamic OEM Table Load:
[    0.162976] ACPI: SSDT   (null) 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.224302] ACPI: SSDT bdf19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.224659] ACPI: Dynamic OEM Table Load:
[    0.224662] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.256143] ACPI: SSDT bdf19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.256479] ACPI: Dynamic OEM Table Load:
[    0.256482] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.280768] ACPI: Interpreter enabled
[    0.280768] ACPI: (supports S0 S3 S4 S5)
[    0.280768] ACPI: Using IOAPIC for interrupt routing
[    0.280859] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.322476] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.322623] ACPI: No dock devices found.
[    0.322630] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.322884] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.340262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.340415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.340460] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.340597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.340652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.340685] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.340722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.340766]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.340769]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.340771] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.346395] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.346444] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.346491] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.346539] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.346588] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.346633] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.346678] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.346722] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.347258] PCI: Using ACPI for IRQ routing
[    0.360072] pnp: PnP ACPI init
[    0.360089] ACPI: bus type pnp registered
[    0.360493] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.360601] pnp 00:01: Plug and Play ACPI device, IDs ENE0100 (active)
[    0.360651] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.360782] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.360826] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.360950] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.360993] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.380123] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.380169] pnp 00:08: Plug and Play ACPI device, IDs SYN070b SYN0700 SYN0002 PNP0f13 (active)
[    0.380409] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.380492] pnp 00:0a: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.380605] pnp: PnP ACPI: found 11 devices
[    0.380606] ACPI: ACPI bus type pnp unregistered
[    0.380610] PnPBIOS: Disabled by ACPI PNP
[    0.459882] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.460081] ACPI: AC Adapter [ACAD] (on-line)
[    0.460213] ACPI: Lid Switch [LID0]
[    0.460256] ACPI: Power Button [PWRB]
[    0.460299] ACPI: Power Button [PWRF]
[    0.462290] ACPI: acpi_idle registered with cpuidle
[    0.480577] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.480585] ACPI: Battery Slot [BAT1] (battery present)
[    0.500299] ACPI: Battery Slot [BAT1] (battery present)
[   13.774610] acpi device:02: registered as cooling_device2
[   13.774736] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)

tim@tim-desktop:~$ dmesg | grep -i error
[   14.142360] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

tim@tim-desktop:~$ dmesg | grep -i warn
nothing
```
that was nomodeset

---

### Post by wildmanne39 on 2012-08-16
Hi, you have a bio's bug, can you update your bio's? if not you might be able to fix the issue by upgrading the kernel but for those things you need to start a new thread for just one of them issues, then we can work on your wireless after you get that resolved.
Thanks

---

### Post by AoFhEkOl on 2012-08-16
ok, cool. I thought it must be the bios and i have updated it to the latest version a while ago.  That's why changing the processor driver worked in windows, it didn't make any sense why that would work.

So what should i do now? try and update it again? I've done this more than once, updating the bios using a usb key (the only way i can update it).  

The bios files are on the [www.compal.com](www.compal.com) website, 

[http://ftp.compal.com/Download/NB/KHLBX/BIOS/HLB0107.zip](http://ftp.compal.com/Download/NB/KHLBX/BIOS/HLB0107.zip)

but like i said, i have that one installed and have done so many times.

I used this guide to make the key bootable 

[http://forum.notebookreview.com/sager-clevo/246530-how-flash-your-bios-dos-using-usb-stick.html](http://forum.notebookreview.com/sager-clevo/246530-how-flash-your-bios-dos-using-usb-stick.html)

---

### Post by wildmanne39 on 2012-08-16
Hi, if there is not an update for the bio's besides the one you have installed then I would try to upgrade the kernel and see if that helps but start a new thread on upgrading the kernel please.
Thanks

---

### Post by AoFhEkOl on 2012-08-16
ok, thanks for your help :)

---

### Post by wildmanne39 on 2012-08-16
Your welcome!

---

### Post by madrian on 2013-06-14
> **Bowater said:**
> No one? I really want to use Ubuntu. Someone must be able to help me. 
 
Windows works fine, I have to change the processor driver to "Intel proccessor driver" for it to work, otherwise I get the black screens and restarts on windows.
 
Specs 
Intel processor dual core 2.53ghz p8700
ATI mobility radeon 512mb 4650
4.0gb ram
Khlb2 motherboard - compal
 
How can I troubleshoot this?

We have exactly the same problem in both Windows and Linux but I'm using Fedora though. I have the same processor as well. I couldn't fix the Windows. I have to disable the processors in device manager to avoid the random restarts or run in safe mode. How did you fix yours? What's the "Intel processor driver" you used? My current driver is:

Provider: Microsoft
Date: 21/6/2006
Version: 6.0.6001.18000
Signer: microsoft windows

In Fedora, when I set acpi=off, there are no restarts but no wifi too! My system is updated with the latest kernel.

Please help and update us how did you fix yours. Thanks.

---

