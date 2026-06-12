---
title: "intel wifi 5100 disconnects a lot"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by eriadorian on 2012-06-22
Hi folks!
 I just installed ubuntu yesterday. Never used it before.    

I tried a wireless connection and it seemed like it was going to work, entered  my network security code and it was accepted.    Every few seconds I get the popup message "wireless network disconnected."    The wired connections works find.    I've tried troubleshooting and run into a confusing deadend.  Towards the end  (see below) 

 Thanks!    

Best wishes,    Bill        

Here is my info:    
Dell Latitude E6400  w/ an intel wifi link 5100    

ubuntu 12.04 LTS   
dual boot with windows xp (wireless works in xp)

 wireless router - linksys wrt54g    

modem - rca dcm425    

and the diagnostics I've run

 ====================    

@ubuntu:~$ nm-tool    NetworkManager Tool    State: connected (global)    - Device: wlan0 ----------------------------------------------------------------    Type:              802.11 WiFi    Driver:            iwlwifi    State:             disconnected    Default:           no    HW Address:        00:24:D6:1E:9C:5A      Capabilities:      Wireless Properties      WEP Encryption:  yes      WPA Encryption:  yes      WPA2 Encryption: yes      Wireless Access Points      Entourage:       Infra, 00:24:B2:C0:A1:5E, Freq 2412 MHz, Rate 54 Mb/s,  Strength 35 WPA      boag:            Infra, 00:18:39:61:1D:2E, Freq 2457 MHz, Rate 54 Mb/s,  Strength 34 WPA2      carlucci:        Infra, 68:7F:74:19:73:AF, Freq 2462 MHz, Rate 54 Mb/s,  Strength 30 WPA      Chome:           Infra, 90:E6:BA:91:23:AA, Freq 2462 MHz, Rate 54 Mb/s,  Strength 29 WPA WPA2      Ace1:            Infra, 00:22:3F:A6:C9:3F, Freq 2462 MHz, Rate 54 Mb/s,  Strength 27 WPA      Arturo's Guest Network: Infra, 72:73:CB:B9:92:80, Freq 2412 MHz, Rate 54  Mb/s, Strength 32 WPA2      Arturo's Network:Infra, 70:73:CB:B9:92:89, Freq 2412 MHz, Rate 54 Mb/s,  Strength 34 WPA2      jenners:         Infra, 00:1E:E5:53:D7:28, Freq 2437 MHz, Rate 54 Mb/s,  Strength 29 WPA WPA2      belkin.cac:      Infra, 08:86:3B:5D:4C:AC, Freq 2412 MHz, Rate 54 Mb/s,  Strength 25 WPA WPA2      Tsaba:           Infra, 58:6D:8F:F6:7D:14, Freq 2412 MHz, Rate 54 Mb/s,  Strength 25 WPA2      Commish:         Infra, A0:21:B7:5F:D6:3D, Freq 2462 MHz, Rate 54 Mb/s,  Strength 25 WPA2      Lindsay Lohan Robbed Me: Infra, 5C:D9:98:5F:5F:4C, Freq 2417 MHz, Rate 54  Mb/s, Strength 34 WEP      07B402753291:    Infra, 00:12:0E:5C:A5:A1, Freq 2437 MHz, Rate 54 Mb/s,  Strength 29 WEP      08FX09042847:    Infra, 00:18:3A:D2:03:3A, Freq 2437 MHz, Rate 54 Mb/s,  Strength 35 WEP      linksys:         Infra, 00:23:69:4E:26:33, Freq 2437 MHz, Rate 54 Mb/s,  Strength 55      NETGEAR:         Infra, 2C:B0:5D:45:CC:2C, Freq 2437 MHz, Rate 54 Mb/s,  Strength 29      Bunnybot:        Infra, 00:21:29:9E:5C:89, Freq 2437 MHz, Rate 54 Mb/s,  Strength 37 WPA WPA2      BeigeLion:       Infra, 20:AA:4B:23:25:00, Freq 2462 MHz, Rate 54 Mb/s,  Strength 25 WPA WPA2      BEMR6:           Infra, 00:18:01:AD:70:26, Freq 2452 MHz, Rate 54 Mb/s,  Strength 27 WEP      TRONGS:          Infra, 30:46:9A:9F:FF:02, Freq 2452 MHz, Rate 54 Mb/s,  Strength 35 WPA WPA2      GRJVH:           Infra, 00:7F:28:95:6B:81, Freq 2437 MHz, Rate 54 Mb/s,  Strength 24 WPA2      FlossNet:        Infra, 00:16:B6:23:BE:F6, Freq 2462 MHz, Rate 54 Mb/s,  Strength 100 WEP      kpo:             Infra, 00:23:6C:BF:73:18, Freq 2462 MHz, Rate 54 Mb/s,  Strength 25 WPA WPA2      Shahadat:        Infra, 00:24:B2:13:79:26, Freq 2437 MHz, Rate 54 Mb/s,  Strength 27 WEP      SBG6580B9:       Infra, 00:26:82:6A:C1:54, Freq 2412 MHz, Rate 54 Mb/s,  Strength 20 WPA WPA2      JENN:            Infra, 00:24:B2:C1:31:52, Freq 2412 MHz, Rate 54 Mb/s,  Strength 20 WPA WPA2      Going Postal:    Infra, 00:1B:2F:69:E7:5E, Freq 2462 MHz, Rate 54 Mb/s,  Strength 20 WPA      Logitech:        Infra, C8:3A:35:12:8A:D0, Freq 2452 MHz, Rate 11 Mb/s,  Strength 22 WEP      - Device: eth0  [Wired connection 1] -------------------------------------------    

Type:              Wired    Driver:            e1000e    State:             connected    Default:           yes    HW Address:        00:24:E8:DA:CF:AF      Capabilities:      Carrier Detect:  yes      Speed:           100 Mb/s      Wired Properties      Carrier:         on      IPv4 Settings:      Address:         192.168.1.100      Prefix:          24 (255.255.255.0)      Gateway:         192.168.1.1        DNS:             209.18.47.61      DNS:             209.18.47.62      =============================================================


 @ubuntu:~$ lshw -c network  WARNING: you should run this program as super-user.    *-network                       description: Ethernet interface         product: 82567LM Gigabit Network Connection         vendor: Intel Corporation         physical id: 19         bus info: pci@0000:00:19.0         logical name: eth0         version: 03         serial: 00:24:e8:da:cf:af         size: 100Mbit/s         capacity: 1Gbit/s         width: 32 bits         clock: 33MHz         capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt  100bt-fd 1000bt-fd autonegotiation         configuration: autonegotiation=on broadcast=yes driver=e1000e  driverversion=1.5.1-k duplex=full firmware=1.7-7 ip=192.168.1.100 latency=0  multicast=yes port=twisted pair speed=100Mbit/s         resources: irq:45 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff  ioport:efe0(size=32)    *-network         description: Wireless interface         product: WiFi Link 5100         vendor: Intel Corporation         physical id: 0         bus info: pci@0000:0c:00.0         logical name: wlan0         version: 00         serial: 00:24:d6:1e:9c:5a         width: 64 bits         clock: 33MHz         capabilities: bus_master cap_list ethernet physical wireless         configuration: broadcast=yes driver=iwlwifi  driverversion=3.2.0-25-generic firmware=8.83.5.1 build 33692 latency=0  multicast=yes wireless=IEEE 802.11abgn         resources: irq:47 memory:f69fe000-f69fffff  WARNING: output may be incomplete or inaccurate, you should run this program as  super-user.    ============================================================



 @ubuntu:~$ lspci -v  00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller  Hub (rev 07)      Subsystem: Dell Device 0233      Flags: bus master, fast devsel, latency 0      Capabilities: <access denied>      Kernel driver in use: agpgart-intel    00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset  Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])      Subsystem: Dell Device 0233      Flags: bus master, fast devsel, latency 0, IRQ 46      Memory at f6c00000 (64-bit, non-prefetchable) [size=4M]      Memory at e0000000 (64-bit, prefetchable) [size=256M]      I/O ports at ef98 [size=8]      Expansion ROM at <unassigned> [disabled]      Capabilities: <access denied>      Kernel driver in use: i915      Kernel modules: i915    00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated  Graphics Controller (rev 07)      Subsystem: Dell Device 0233      Flags: bus master, fast devsel, latency 0      Memory at f6b00000 (64-bit, non-prefetchable) [size=1M]      Capabilities: <access denied>    00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network  Connection (rev 03)      Subsystem: Dell Device 0233      Flags: bus master, fast devsel, latency 0, IRQ 45      Memory at f6ae0000 (32-bit, non-prefetchable) [size=128K]      Memory at f6adb000 (32-bit, non-prefetchable) [size=4K]      I/O ports at efe0 [size=32]      Capabilities: <access denied>      Kernel driver in use: e1000e      Kernel modules: e1000e    00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI  Controller #4 (rev 03) (prog-if 00 [UHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 20      I/O ports at 6f60 [size=32]      Capabilities: <access denied>      Kernel driver in use: uhci_hcd    00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI  Controller #5 (rev 03) (prog-if 00 [UHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 21      I/O ports at 6f80 [size=32]      Capabilities: <access denied>      Kernel driver in use: uhci_hcd    00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI  Controller #6 (rev 03) (prog-if 00 [UHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 22      I/O ports at 6fa0 [size=32]      Capabilities: <access denied>      Kernel driver in use: uhci_hcd    00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI  Controller #2 (rev 03) (prog-if 20 [EHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 22      Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]      Capabilities: <access denied>      Kernel driver in use: ehci_hcd    00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller  (rev 03)      Subsystem: Dell Device 0233      Flags: bus master, fast devsel, latency 0, IRQ 48      Memory at f6adc000 (64-bit, non-prefetchable) [size=16K]      Capabilities: <access denied>      Kernel driver in use: snd_hda_intel      Kernel modules: snd-hda-intel    00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1  (rev 03) (prog-if 00 [Normal decode])      Flags: bus master, fast devsel, latency 0      Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0      I/O behind bridge: 00004000-00004fff      Memory behind bridge: 80600000-807fffff      Prefetchable memory behind bridge: 0000000080800000-00000000809fffff      Capabilities: <access denied>      Kernel driver in use: pcieport      Kernel modules: shpchp    00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2  (rev 03) (prog-if 00 [Normal decode])      Flags: bus master, fast devsel, latency 0      Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0      I/O behind bridge: 00003000-00003fff      Memory behind bridge: f6900000-f69fffff      Prefetchable memory behind bridge: 0000000080400000-00000000805fffff      Capabilities: <access denied>      Kernel driver in use: pcieport      Kernel modules: shpchp    00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3  (rev 03) (prog-if 00 [Normal decode])      Flags: bus master, fast devsel, latency 0      Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0      I/O behind bridge: 00002000-00002fff      Memory behind bridge: 80000000-801fffff      Prefetchable memory behind bridge: 0000000080200000-00000000803fffff      Capabilities: <access denied>      Kernel driver in use: pcieport      Kernel modules: shpchp    00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4  (rev 03) (prog-if 00 [Normal decode])      Flags: bus master, fast devsel, latency 0      Bus: primary=00, secondary=0e, subordinate=0f, sec-latency=0      I/O behind bridge: 0000d000-0000dfff      Memory behind bridge: f6600000-f68fffff      Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff      Capabilities: <access denied>      Kernel driver in use: pcieport      Kernel modules: shpchp    00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI  Controller #1 (rev 03) (prog-if 00 [UHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 20      I/O ports at 6f00 [size=32]      Capabilities: <access denied>      Kernel driver in use: uhci_hcd    00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI  Controller #2 (rev 03) (prog-if 00 [UHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 21      I/O ports at 6f20 [size=32]      Capabilities: <access denied>      Kernel driver in use: uhci_hcd    00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI  Controller #3 (rev 03) (prog-if 00 [UHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 22      I/O ports at 6f40 [size=32]      Capabilities: <access denied>      Kernel driver in use: uhci_hcd    00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI  Controller #1 (rev 03) (prog-if 20 [EHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0, IRQ 20      Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]      Capabilities: <access denied>      Kernel driver in use: ehci_hcd    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if  01 [Subtractive decode])      Flags: bus master, fast devsel, latency 0      Bus: primary=00, secondary=03, subordinate=03, sec-latency=32      Memory behind bridge: f6500000-f65fffff      Capabilities: <access denied>    00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 0      Capabilities: <access denied>      Kernel modules: iTCO_wdt    00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller  [RAID mode] (rev 03)      Subsystem: Dell Device 0233      Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44      I/O ports at 6e70 [size=8]      I/O ports at 6e78 [size=4]      I/O ports at 6e80 [size=8]      I/O ports at 6e88 [size=4]      I/O ports at 6ea0 [size=32]      Memory at fed1c800 (32-bit, non-prefetchable) [size=2K]      Capabilities: <access denied>      Kernel driver in use: ahci    00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)      Subsystem: Dell Device 0233      Flags: medium devsel, IRQ 3      Memory at f6adaf00 (64-bit, non-prefetchable) [size=256]      I/O ports at 1100 [size=32]      Kernel modules: i2c-i801    03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)  (prog-if 10 [OHCI])      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 64, IRQ 17      Memory at f65ff800 (32-bit, non-prefetchable) [size=2K]      Capabilities: <access denied>      Kernel driver in use: firewire_ohci      Kernel modules: firewire-ohci    03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host  Adapter (rev 21) (prog-if 01)      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 64, IRQ 18      Memory at f65ff600 (32-bit, non-prefetchable) [size=256]      Capabilities: <access denied>      Kernel driver in use: sdhci-pci      Kernel modules: sdhci-pci    03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)      Subsystem: Dell Device 0233      Flags: bus master, medium devsel, latency 64, IRQ 18      Memory at f65ff700 (32-bit, non-prefetchable) [size=256]      Capabilities: <access denied>      Kernel driver in use: sdhci-pci      Kernel modules: sdhci-pci    0c:00.0 Network controller: Intel Corporation WiFi Link 5100      Subsystem: Intel Corporation WiFi Link 5100 AGN      Flags: bus master, fast devsel, latency 0, IRQ 47      Memory at f69fe000 (64-bit, non-prefetchable) [size=8K]      Capabilities: <access denied>      Kernel driver in use: iwlwifi      Kernel modules: iwlwifi    ==================================================    

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsI ntel]("http://webmail.nyc.rr.com/do/redirect?url=https%253A%252F%252Fhelp.ubuntu.com%252Fcommunity%252FHardwareSupportComponentsWirelessNetworkCardsIntel")    

Intel PRO/Wireless 5100 AGN [Shiloh]          Intel 5100          iwlagn          Untested          Yes          Yes          This driver worked out of the box on a default (desktop) install of Ubuntu 10.04  and 10.10 using WPA and WEP and open networks.          2010-02-18

 ==========================================================    

@ubuntu:~$ sudo lspci -nm  [sudo] password for :  00:00.0 "0600" "8086" "2a40" -r07 "1028" "0233"  00:02.0 "0300" "8086" "2a42" -r07 "1028" "0233"  00:02.1 "0380" "8086" "2a43" -r07 "1028" "0233"  00:19.0 "0200" "8086" "10f5" -r03 "1028" "0233"  00:1a.0 "0c03" "8086" "2937" -r03 "1028" "0233"  00:1a.1 "0c03" "8086" "2938" -r03 "1028" "0233"  00:1a.2 "0c03" "8086" "2939" -r03 "1028" "0233"  00:1a.7 "0c03" "8086" "293c" -r03 -p20 "1028" "0233"  00:1b.0 "0403" "8086" "293e" -r03 "1028" "0233"  00:1c.0 "0604" "8086" "2940" -r03 "" ""  00:1c.1 "0604" "8086" "2942" -r03 "" ""  00:1c.2 "0604" "8086" "2944" -r03 "" ""  00:1c.3 "0604" "8086" "2946" -r03 "" ""  00:1d.0 "0c03" "8086" "2934" -r03 "1028" "0233"  00:1d.1 "0c03" "8086" "2935" -r03 "1028" "0233"  00:1d.2 "0c03" "8086" "2936" -r03 "1028" "0233"  00:1d.7 "0c03" "8086" "293a" -r03 -p20 "1028" "0233"  00:1e.0 "0604" "8086" "2448" -r93 -p01 "" ""  00:1f.0 "0601" "8086" "2917" -r03 "1028" "0233"  00:1f.2 "0104" "8086" "282a" -r03 "1028" "0233"  00:1f.3 "0c05" "8086" "2930" -r03 "1028" "0233"  03:01.0 "0c00" "1180" "0832" -r04 -p10 "1028" "0233"  03:01.1 "0805" "1180" "0822" -r21 -p01 "1028" "0233"  03:01.2 "0880" "1180" "0843" -r11 "1028" "0233"  0c:00.0 "0280" "8086" "4232" "8086" "1321"      =====================================================    

@ubuntu:~$ lspci -nm | grep 0280  0c:00.0 "0280" "8086" "4232" "8086" "1321"      ========================================================    

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel%20WiFi%20Link%205100]("http://webmail.nyc.rr.com/do/redirect?url=https%253A%252F%252Fhelp.ubuntu.com%252Fcommunity%252FWifiDocs%252FDriver%252FIntel%252520WiFi%252520Link%2525205100")    

Intel WiFi Link 5100 is compatible with Ubuntu 9.04+ 32-bit and 64-bit.    


=========================================================      

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/174965]("http://webmail.nyc.rr.com/do/redirect?url=https%253A%252F%252Fanswers.launchpad.net%252Fubuntu%252F%252Bsource%252Fgnome-nettool%252F%252Bquestion%252F174965")    rebooting the router with the wired link and ubuntu on solved the problem.    but this person had no wired or wireless connections.

---

### Post by wildmanne39 on 2012-06-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by anewguy on 2012-06-22
[This]("wireless-on-an-acer-aspire-1810t-with-an-intel-5100agn-works-for-less-than-a-day") thread - showing that bug reports should be initiated - shows your problem but on a different PC -> SAME wireless device though.

---

### Post by Prometheus418 on 2012-06-22
Hello-

First, let me apologize for both not knowing any of the standards relating to posting linux information (I see some of you have some very detailed text dumps on these posts, and I don't have anything like that.)  All that stuff might mean something to me someday, but I've only had Ubuntu for a couple of weeks.

I'm going to include an intro here, so feel free to skip the next paragraph or two if you just don't care.  I'm an aerospace engineer that does a respectable amount of IT support work on our internal (windows) systems.  I am switching to Linux as much as I can because of the gradual tightening of the WWW and the PC world- naughty men like me need room to wiggle about.  I guess I'd call myself a Windows hacker, having memorized the registry and being able to do more or less anything I want with the systems, no matter what Microsoft has to say about it.  But now I'm tired of it, and the Unix community had evolved enough since my last attempt (Redhat in 2000) to make Ubuntu the sole OS of my laptop computer.

So, I'm not a computer n00b- just new to Linux.  I mention it so that you do not disregard the post because of a translation error.  Also, I am watching "Abraham Lincoln Vs Zombies" while typing this, so you know the information must be good.

My primary PC is an i7 cad system with 16gb Ram and (not enough) SSDs.  I recently bought a Dell Latitude d630 second-hand because, well, it was cheap.  It has been upgraded to 8gb Ram and a 256gb SSD, mainly just because I could.  My primary intended use for the machine was as a remote terminal to access my personal CAD system for work, where I have a matching machine.  (I do manage to max my systems out a few times a week, so having a standby to compare models is helpful.)

I put Ubuntu 12.04 on the Dell laptop because I needed support for a Zen Touch mp3 player, and was pleasantly surprised at the evolution of Linux since I had last used it.  The only downfall was the very issue that started this thread- it kept dropping the wifi connection at home, but was pretty stable at work.

So, I did a little digging- it seems like many people have this problem, but there are not a lot of answers.  What worked for me was a hybrid solution that incorporated the changes suggested by several different posts here and elsewhere.  I did not take notes, but I can relay the thought process that solved the issue.

First, I have a TRENDnet TEW-673GRU gigabit router with dual 2.4ghz/5.0ghz bands.  The documentation with this device was less than awesome, so it has been an adventure since day one- even before adding Linux to the mix.

Windows 7 systems, both 32 and 64-bit connect to my network with no issues.  There are no dropped connections or apparent signal weakness, so I know that the faulty hardware was not the issue.  After goofing around with the Ubuntu laptop for a while with only dead-reckoning as a guide, I finally decided to check the router settings.

The first issue was that the band on the laptop did not match the band on the router. I adjusted the settings on the laptop and entered the MAC address for the router.

The second issue was apparently one of power management.  I turned off power management to the WAN, and rebooted.  There is an article somewhere that describes this process in detail, but I managed to somehow flush it out of my history, so I guess Google is your friend here.

The third move was to adjust the MTU value to 1500, based on yet another recommendation I did not save the link to.

The last one is simple derp-ishness, and I think it might be the thing that a lot of people may be missing.  Prior to installing Ubuntu on this machine, I had Win7 64-bit on it.  Compared to Ubuntu, Win7 is horribly bloated, and takes a comparably long time to reload.  I was impressed by Ubuntu's reboot speeds, and forgot patience entirely.  

What I found was that after making any wireless change, a dialog box would pop up indicating that there were wireless connections available.  I kept jumping the gun, and starting up my connection from the list.  A minute or two later, it would lose the connection.

I noticed something, though- there were two similar connections listed, one that was as expected, and one that had a "1" appended to the name.  Evidently, I was over-eager and beat the automatic function to the punch- and that second connection was interfering with the one I made manually,

The fix was to delete the properly named connection, and rename the one with the number to the original SSID.  After a reboot and a moment of patience to allow the auto connect to do it's thing, the wireless connection has stabilized and improved. 

Like I said, it's dumb.  But it worked, and that is what counts, right?  Windows has a virtually instant connect, so I forgot to wait.

Anyhow, for what that's worth.  Hope it helps someone!  I'm very impressed with the Ubuntu release, and will do my best to support it going forward.

---

### Post by anewguy on 2012-06-22
That's good information, but perhaps next time you could post it in it's own thread?

---

### Post by eriadorian on 2012-06-23
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```by clicking on new reply and click # then paste the information between the brackets.
Thank you


Thanks, WM!

Here is the output:

washton@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


washton@ubuntu:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Dell Device [1028:0233]
    Kernel driver in use: e1000e
--
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi
washton@ubuntu:~$ 


washton@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"FlossNet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:23:BE:F6   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


washton@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
washton@ubuntu:~$ 


washton@ubuntu:~$ lsmod
Module                  Size  Used by
joydev                 17693  0 
bnep                   18281  2 
rfcomm                 47604  12 
btusb                  18288  3 
bluetooth             180104  25 bnep,rfcomm,btusb
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
dell_laptop            18119  0 
snd_seq_midi_event     14899  1 snd_seq_midi
dcdbas                 14490  1 dell_laptop
psmouse                87692  0 
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               332672  0 
snd_timer              29990  2 snd_pcm,snd_seq
mac80211              506816  1 iwlwifi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
wmi                    19256  1 dell_wmi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  468745  3 
cfg80211              205544  2 iwlwifi,mac80211
drm_kms_helper         46978  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 
usbhid                 47199  0 
hid                    99559  1 usbhid

-- Bill

---

### Post by wildmanne39 on 2012-06-23
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```
Does that help if not please post the output of:
```
nm-tool
```
by placing the output between the code tags by hitting the # sign above the window you type in.
Thanks

---

### Post by eriadorian on 2012-06-23
> **wildmanne39 said:**
> Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```Does that help if not please post the output of:
```
nm-tool
```by placing the output between the code tags by hitting the # sign above the window you type in.
Thanks


I tried it and it didn't work ... here is the output 

washton@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [FlossNet] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:24:D6:1E:9C:5A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    boag:            Infra, 00:18:39:61:1D:2E, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA2
    Chome:           Infra, 90:E6:BA:91:23:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    carlucci:        Infra, 68:7F:74:19:73:AF, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    U10C0228C:       Infra, 18:F4:6A:59:F5:1C, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    jenners:         Infra, 00:1E:E5:53:D7:28, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    NETGEAR23:       Infra, 4C:60:DE:39:52:0A, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Ace1:            Infra, 00:22:3F:A6:C9:3F, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    belkin.cac:      Infra, 08:86:3B:5D:4C:AC, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Arturo's Guest Network: Infra, 72:73:CB:B9:92:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Arturo's Network:Infra, 70:73:CB:B9:92:89, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    08FX09042847:    Infra, 00:18:3A:D2:03:3A, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    Lindsay Lohan Robbed Me: Infra, 5C:D9:98:5F:5F:4C, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WEP
    07B402753291:    Infra, 00:12:0E:5C:A5:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP
    Shahadat:        Infra, 00:24:B2:13:79:26, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WEP
    BEMR6:           Infra, 00:18:01:AD:70:26, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WEP
    linksys:         Infra, 00:23:69:4E:26:33, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    NETGEAR:         Infra, 2C:B0:5D:45:CC:2C, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    Entourage:       Infra, 00:24:B2:C0:A1:5E, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA
    FlossNet:        Infra, 00:16:B6:23:BE:F6, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WEP
    Commish:         Infra, A0:21:B7:5F:D6:3D, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Bunnybot:        Infra, 00:21:29:9E:5C:89, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SBG6580B9:       Infra, 00:26:82:6A:C1:54, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:DA:CF:AF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62

---

### Post by wildmanne39 on 2012-06-23
Hi, go into your router settings through your web browser and change your encryption to just wpa2 if you have that option and not wep, or wpa/wpa2 and it will work better that way.

Also you will need to change it in network settings to wpa/wpa2, then reboot.

Then if it will not connect post the output of:
```
nm-tool
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by eriadorian on 2012-06-23
I found a solution on another forum:

Please connect the network adapter to your wireless router using a LAN cable.

Please log into the router and

* enable SSID broadcasting on the router
* temporarily disable encryption on the router (for troubleshooting purposes)
* force the router to use Wireless-G (54 Mbps) speeds
* change the wireless transmission channel to channel 4 on the router, to AVOID wireless interference from the other wireless access points.

Then install wicd as a replacement for NetworkManager using the following command:

sudo apt-get update && sudo apt-get install wicd

Then REBOOT your PC and retest wireless.

Hope it helps.

---

### Post by wildmanne39 on 2012-06-23
Hi, I am glad you got it working but that is where we were heading with the commands I was giving you, > * force the router to use Wireless-G (54 Mbps) speedswe done this with the driver parameter with this command ```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
it is just another way of doing the same thing.
Enjoy

---

