---
title: "Lenovo T510 taking forever to boot"
date: 2017-04-16
forum: New to Ubuntu
---

### Post by alouvatar on 2017-04-16
Hello all! I  &#42892;ve just installed Ubuntu Gnome on my lenovo t510 as a second OS. I ve recently installed an ssd on this laptop too so i would expect the system to boot fast but it's taking more than 90s. I used ```
dmesg
``` to produce a log and the problematic part seems to be here
```

[    5.682189] input: HDA Intel MID HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    5.782308] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   50.080429] random: crng init done
[   95.277708] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   95.277710] Bluetooth: BNEP filters: protocol multicast


```
Any advice would be really helpful! Thanks in advance!

---

### Post by DuckHook on 2017-04-17
Welcome to the forums, alouvatar.

Please post results of:```
systemd-analyze blame
``````
sudo lspci -vk | grep -iA13 net
``````
uname -a
``````
lsb_release -a
```
Did it boot quickly before you switched to the SSD?

---

### Post by alouvatar on 2017-04-17
Hello and thanks for your reply. I never tried Ubuntu before switching  to an SSD but other distros i used  didnt take too long to boot  (15-30s?) and so did windows 10. 
By the way i m not sure if it's  related but randomly ubuntu freezes and needs to be reset. Below i m  posting the results of the commands you asked.
```
Systemd-analyze blame
```
```
 3.809s plymouth-quit-wait.service
          1.667s fwupd.service
           832ms dev-sda4.device
           364ms systemd-resolved.service
           350ms networking.service
           196ms apparmor.service
           158ms keyboard-setup.service
           137ms ModemManager.service
           130ms accounts-daemon.service
           121ms speech-dispatcher.service
           111ms apport.service
           111ms grub-common.service
           108ms systemd-timesyncd.service
           100ms NetworkManager.service
           100ms systemd-udev-trigger.service
            99ms systemd-logind.service
            89ms systemd-tmpfiles-setup-dev.service
            88ms irqbalance.service
            76ms systemd-rfkill.service
            72ms thermald.service
            69ms gpu-manager.service
            66ms pppd-dns.service
            65ms switcheroo-control.service
            63ms packagekit.service
            62ms upower.service
            62ms rsyslog.service
            60ms alsa-restore.service
            55ms systemd-journald.service
            43ms udisks2.service
            41ms user@1000.service
            41ms snapd.autoimport.service
            37ms systemd-tmpfiles-setup.service
            35ms polkit.service
            34ms systemd-modules-load.service
            33ms avahi-daemon.service
            32ms systemd-sysctl.service
            29ms colord.service
            28ms sys-kernel-debug.mount


```

```
sudo lspci -vk | grep -iA13 net
[sudo] password for jasmin: 
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
    Subsystem: Lenovo 82577LM Gigabit Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at f2600000 (32-bit, non-prefetchable) [size=128K]
    Memory at f2625000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1820 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Lenovo 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
--
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f2400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 18-3d-a2-ff-ff-1a-76-28
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

0d:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
    Subsystem: Lenovo MMC/SD Host Controller


```

```
uname -a
Linux jasmin-ThinkPad-T510 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty


```
Thanks in Advance!!

---

### Post by DuckHook on 2017-04-18
systemd-analyze shows that your system should be loading very quickly. However, dmesg does not. I don't know what to make of this.

Have you tried a LiveUSB of an LTS version like 16.04?

---

