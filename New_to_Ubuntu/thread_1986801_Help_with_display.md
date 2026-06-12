---
title: "Help with display"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by lord flasheart on 2012-05-25
I'm currently running 11.10, after upgrading from 10.10 through the update manager I'm having a prob with the refresh rate: 0hz...'detect monitors' does nothing.

I have both gnome and xfce4 .

I'm outputting to a home cinema projector through hdmi, this is the only screen I have connected.

[HTML]lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
04:00.0 Multimedia controller: Broadcom Corporation BCM70015 Video Decoder [Crystal HD]
[/HTML]Any help would be much appreciated, thanks in advance.

---

### Post by lord flasheart on 2012-05-27
Any ideas, anyone? I've looked at solutions other people have posted for similar problems but with different hardware.
It's obviously not a system breaking problem but it's annoying as hell when the cursor keeps disappearing.

---

### Post by jtarin on 2012-05-27
[Try this fix.]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

---

