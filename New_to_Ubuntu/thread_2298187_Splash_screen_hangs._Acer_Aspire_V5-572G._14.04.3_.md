---
title: "Splash screen hangs. Acer Aspire V5-572G. 14.04.3 LTS"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by Jon_Taylor on 2015-10-09
Hi,

I am new to Ubuntu!

I have a variety of problems that have appeared recently. All of these used to work. I'll post them in separate threads in case they're separate problems, but I suppose they may well be linked.

So first up, my splash screen hangs. The little loading circle goes round a couple of times and then stops, never to go again. It used to work fine, then it worked intermittently, now it never works. It used to be that one boot would hang, then I would force reboot, and that would work. When I did this, it seemed that my custom desktop background was always reverted to default. Now, forcing a reboot doesn't help. What does work without fail is booting into safe mode, and then immediately resuming normal boot.

If it helps with diagnosis I also have problems with backlight hotkeys not working when they used to, being unable to set a preferred web browser when I used to have one, unreliably detecting connection of a TV via HDMI when this used to work fine, and a Sonos controller install using wine/playonlinux which has never worked. I'll put these in separate threads.

Here are the results of lspci (more because it sounds clever than because I know it will be useful):

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev ff)
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 14)
```

---

