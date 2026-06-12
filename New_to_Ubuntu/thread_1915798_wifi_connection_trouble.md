---
title: "wifi connection trouble"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by JEV23 on 2012-01-26
Don't know if anyone can help, but i am having trouble with my wifi. It works fine on Windows 7 but when I try Oneric Ocelot I have trouble getting on. I am dual booting on a Toshiba Satellite C655D-S5200 so I don't understand why it works on one but not the other. Stranger still I can get on Ocelot if I boot up Windows, connect the Wifi then turn off Windows and boot up Ocelot. Its only when I boot up Ocelot first or when I suspend Ocelot and come back that the trouble begins. Any ideas? I've tried uploading a new driver and same problem.

---

### Post by carl4926 on 2012-01-26
What windows does is of little consequence...

What we need to know is, what wireless device..
Open a terminal and post for us the result of

```
lspci -nnk
```

---

### Post by JEV23 on 2012-01-26
Hate to sound stupid but how do show what I got on the terminal?

---

### Post by carl4926 on 2012-01-26
Use your mouse to select > right click > copy

then paste here in code tags

---

### Post by JEV23 on 2012-01-27
es [AMD] Family 14h Processor Root Complex [1022:1510]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9804]
    Subsystem: Toshiba America Info Systems Device [1179:fde8]
    Kernel driver in use: radeon
    Kernel modules: radeon
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
    Kernel modules: shpchp
00:15.0 PCI bridge [0604]: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.1 PCI bridge [0604]: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c
    Kernel modules: atl1c
james@ubuntu:~$ 


Here you go. Hope it 's all there.

---

### Post by omghahalol on 2012-01-27
Can you run "uname -srvi" in terminal and show the output here?

---

### Post by carl4926 on 2012-01-27
This is your wireless device

```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce
```

You might benefit from the Compat wireless
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

But I'm not sure how you go about that

---

### Post by JEV23 on 2012-01-27
Linux 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64

---

### Post by Chilkat on 2012-02-05
Debian 6.0 Squeeze fixed my Toshiba C655D-S5200. 

What I did, was install Debian 6.0 Squeeze with kernel 2.6.32-5 as it supports the RTL-8188 network card driver. I'd bet a newer kernel will work as well, but 2.6.32 was an alternate kernel on my install CD. I used Debian Non-Free firmware, the RTL8192U WLAN Driver, and the latest AMD Catalyst Video driver package with admin software. It took a bit of tweaking but my Toshiba C655D-S5200 (wallyworld special) has been running Linux exclusively since September. The rtl-8188 wireless network card has run flawlessly to date, no apparent, loss of connectivity or slow connections. 

Before settling on Debian, I tried some other releases, Mint 11, Open Suse 11.4, Fedora 15, Xbuntu & Ubuntu 11.10, PCLinux OS 2011.6, and Cent OS 5.4. They would all hang on install, or install then fail to boot with a power off reset required. The only catch so far is that one Debian patch a couple months ago axed my vid drivers, but nothing hard to re-install. Debian Squeeze is cool and will do till the freezing error with Ubuntu is sorted out.


note: I used the Raphael Hertzog single disk AMD-64 DVD as it comes with the non-free firmware and the 2.6.32-5 kernel as well. You could DL your own drivers and spin your own DVD.

---

