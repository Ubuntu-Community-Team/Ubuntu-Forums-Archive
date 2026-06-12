---
title: "Wireless Network not seen"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-10-15
Hello;

Looks like the Atheros proprietary driver is installed and Ubuntu should be picking my wireless network. However it does NOT. Any ideas as how to trouble shoot this. My other XP laptop works great with wireless, so I know it is not a router issue. The only way Ubuntu now works is by ethernet cable.


HELP


loyaleagle@loyaleagle-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
[COLOR="Red"]**17:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**[/COLOR]
1d:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1d:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1d:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1d:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by trikster_x on 2008-10-16
Check your router settings and make sure that it is set to broadcast your ssid.

---

### Post by pak33m on 2008-10-16
loyaleagle,

Where are you not seeing the wireless connection: Network Manager or network-admin?

Are you trying to use Network Manager with a wireless configuration in network-admin?

You can check this by going to System -> Administration -> Network.  You will have to enter your password.  Once network-admin has come up you should see straight away if a wireless connection has been configured, as a wireless connection will be enabled.  If it is you should check to see if all of the correct wireless info is entered correctly.  

If you're going to use network-admi for your wireless configguration you should disable Network Manager from System -> Preferences - Sessions so that there is no conflict between programs.

If you plan to just use Network Manager you should remove the wireless configuration from network-admin.  You can do this either through the same location I mentioned above or by removing all of the interfaces except for **lo** listed in the /etc/network/interfaces file in the terminal:

```
sudo vim /etc/network/interfaces
```

Use the **dd** command on all lines to delete again except for the **lo** interface.

That's just my two cents from a whole lot of tinkering with wireless myself.

---

