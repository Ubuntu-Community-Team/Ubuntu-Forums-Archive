---
title: "Erratic but consistent freezing (14.04)"
date: 2015-09-07
forum: New to Ubuntu
---

### Post by amloren1 on 2015-09-07
I have been using linux for awhile now and recently decided to go with Ubuntu 14.04 for my pc. Seems to work well enough until it freezes. ctrl-alt-f1 takes me nowhere and alt-sysrq REISUB doesn't work either. This leaves me to do a hard boot 

System specs:

-BIOSTAR Hi-Fi A70U3P FM2+ MOBO
-AMD 7870K APU
-stock cooler
-Hyper-x Savage RAM DDR3 running @ 2133 
-SSD: boot, /
-HDD: swap, /var, /home

Attempts to find a solution:
-memtest came out with no errors

I thought at first that my problem could be related to the graphics drivers. However, videos work fine. No choppiness. Just random freezing. This is a new install of 14.04. Any help is appreciated


edit: 
-The same issue is occurring with Ubuntu 15.04
-motherboard resets the clock when set to the correct time

---

### Post by coldraven on 2015-09-08
You could start by doing a memory check. There might be a utility in the BIOS to do it. Another method is to press shift on boot and get to the grub screen, there is a memcheck option there. If you do a full check it will take a long time so maybe do it overnight.

---

### Post by amloren1 on 2015-09-08
Thanlks. I don't think it's a memory issue though. Everything is brand new. But if there aren't any other suggestions, Ill go ahead and do it tonight anyhow.

---

### Post by ian-weisser on 2015-09-08
> **amloren1 said:**
> alt-sysrq REISUB doesn't work
That means it's either a kernel crash or a hardware fault. Coldraven's advice to rule out memory, one of the most common hardware faults, is appropriate.
Can you recreate the crash at will?
Or will the crash eventually happen regardless of what you are doing on the system?
If you boot the system but leave it idle (don't login), will it eventually crash?
If you boot from a LiveUSB, will it crash?

---

### Post by amloren1 on 2015-09-08
The crash seems imminent. After doing some work for about an hour with no crash, I left and came back 2 hours later and it had crashed on idle. I've played around on the live usb without a crash. Maybe I can leave it on idle for awhile on the live usb to see if this occurs again. 

Forgot to mention, I am using a stock cooler since the one I bought didnt fit the case. Temperatures don't seem to get very high though and I have only done some light coding while having a few chrome tabs open so far. Though I have not been able to check the temperatures since my goto terminal program, sensors, for some reason does not have access to the temperature data from the components. That's a separate issue I suppose.

---

### Post by andrei21 on 2015-09-08
I have the same issue bro..

---

### Post by amloren1 on 2015-09-08
> **andrei21 said:**
> I have the same issue bro..


Same or similar hardware?

---

### Post by andrei21 on 2015-09-08
I have an Nvidia GPU

---

### Post by amloren1 on 2015-09-09
Bump

---

### Post by ian-weisser on 2015-09-09
Any useful error messages around crash time in /var/log/syslog ?
Any useful error messages around crash time in /var/log/dmesg ?
Any relevant .crash files generated in /var/crash?

Those are all text files, you can look them over in any text editor, or using the 'more' or 'less' shell commands.

---

### Post by amloren1 on 2015-09-10
memtest came out fine. I will wait for the next crash to take a look at the logs.

---

### Post by amloren1 on 2015-09-10
in syslog the first failure before the time I think a crash occurred was: 

Sep 10 05:41:15 TheShip kernel: [    0.268109] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM

A similar failure is noted in dmsg:

[    0.268109] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM

Not sure what ACPI is but it has several occurrences of failure as well

Nothing in the crash directory

---

### Post by amloren1 on 2015-09-11
Good chunk of syslog after a crash 



```
Sep 10 22:41:31 TheMothership kernel: [    3.046008] input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input12
Sep 10 22:41:31 TheMothership kernel: [    3.046667] input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input13
Sep 10 22:41:31 TheMothership kernel: [    3.046821] input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input14
Sep 10 22:41:31 TheMothership kernel: [    3.046918] input: HD-Audio Generic Line Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input15
Sep 10 22:41:31 TheMothership kernel: [    3.046992] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
Sep 10 22:41:31 TheMothership kernel: [    3.047601] [drm] Internal thermal controller without fan control
Sep 10 22:41:31 TheMothership kernel: [    3.048742] [drm] radeon: dpm initialized
Sep 10 22:41:31 TheMothership kernel: [    3.052705] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
Sep 10 22:41:31 TheMothership kernel: [    3.052734] [drm] GART: num cpu pages 262144, num gpu pages 262144
Sep 10 22:41:31 TheMothership kernel: [    3.094632] [drm] PCIE GART of 1024M enabled (table at 0x000000000078C000).
Sep 10 22:41:31 TheMothership kernel: [    3.094770] radeon 0000:00:01.0: WB enabled
Sep 10 22:41:31 TheMothership kernel: [    3.094783] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff8800c783bc00
Sep 10 22:41:31 TheMothership kernel: [    3.094785] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff8800c783bc04
Sep 10 22:41:31 TheMothership kernel: [    3.094788] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff8800c783bc08
Sep 10 22:41:31 TheMothership kernel: [    3.094791] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff8800c783bc0c
Sep 10 22:41:31 TheMothership kernel: [    3.094793] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff8800c783bc10
Sep 10 22:41:31 TheMothership kernel: [    3.095205] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90005d36c98
Sep 10 22:41:31 TheMothership kernel: [    3.097579] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000040000c18 and cpu addr 0xffff8800c783bc18
Sep 10 22:41:31 TheMothership kernel: [    3.097583] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000040000c1c and cpu addr 0xffff8800c783bc1c
Sep 10 22:41:31 TheMothership kernel: [    3.097585] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Sep 10 22:41:31 TheMothership kernel: [    3.097586] [drm] Driver supports precise vblank timestamp query.
Sep 10 22:41:31 TheMothership kernel: [    3.097612] radeon 0000:00:01.0: radeon: using MSI.
Sep 10 22:41:31 TheMothership kernel: [    3.097635] [drm] radeon: irq initialized.
Sep 10 22:41:31 TheMothership kernel: [    3.100423] kvm: Nested Virtualization enabled
Sep 10 22:41:31 TheMothership kernel: [    3.100428] kvm: Nested Paging enabled
Sep 10 22:41:31 TheMothership kernel: [    3.100937] [drm] ring test on 0 succeeded in 2 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.101076] [drm] ring test on 1 succeeded in 2 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.101090] [drm] ring test on 2 succeeded in 2 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.109092] [drm] ring test on 3 succeeded in 3 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.109101] [drm] ring test on 4 succeeded in 3 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.156023] Switched to clocksource tsc
Sep 10 22:41:31 TheMothership kernel: [    3.156393] [drm] ring test on 5 succeeded in 1 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.176763] [drm] UVD initialized successfully.
Sep 10 22:41:31 TheMothership kernel: [    3.286087] [drm] ring test on 6 succeeded in 16 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.286098] [drm] ring test on 7 succeeded in 3 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.286099] [drm] VCE initialized successfully.
Sep 10 22:41:31 TheMothership kernel: [    3.288115] [drm] ib test on ring 0 succeeded in 0 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.784417] [drm] ib test on ring 1 succeeded in 0 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.784469] [drm] ib test on ring 2 succeeded in 0 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.784529] [drm] ib test on ring 3 succeeded in 0 usecs
Sep 10 22:41:31 TheMothership kernel: [    3.784576] [drm] ib test on ring 4 succeeded in 0 usecs
Sep 10 22:41:31 TheMothership kernel: [    4.304365] [drm] ib test on ring 5 succeeded
Sep 10 22:41:31 TheMothership kernel: [    4.324829] [drm] ib test on ring 6 succeeded
Sep 10 22:41:31 TheMothership kernel: [    4.325333] [drm] ib test on ring 7 succeeded
Sep 10 22:41:31 TheMothership kernel: [    4.326407] [drm] Radeon Display Connectors
Sep 10 22:41:31 TheMothership kernel: [    4.326409] [drm] Connector 0:
Sep 10 22:41:31 TheMothership kernel: [    4.326411] [drm]   HDMI-A-1
Sep 10 22:41:31 TheMothership kernel: [    4.326412] [drm]   HPD3
Sep 10 22:41:31 TheMothership kernel: [    4.326414] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
Sep 10 22:41:31 TheMothership kernel: [    4.326415] [drm]   Encoders:
Sep 10 22:41:31 TheMothership kernel: [    4.326416] [drm]     DFP2: INTERNAL_UNIPHY2
Sep 10 22:41:31 TheMothership kernel: [    4.326417] [drm] Connector 1:
Sep 10 22:41:31 TheMothership kernel: [    4.326418] [drm]   VGA-1
Sep 10 22:41:31 TheMothership kernel: [    4.326419] [drm]   HPD1
Sep 10 22:41:31 TheMothership kernel: [    4.326420] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
Sep 10 22:41:31 TheMothership kernel: [    4.326421] [drm]   Encoders:
Sep 10 22:41:31 TheMothership kernel: [    4.326422] [drm]     CRT1: INTERNAL_UNIPHY
Sep 10 22:41:31 TheMothership kernel: [    4.326423] [drm]     CRT1: NUTMEG
Sep 10 22:41:31 TheMothership kernel: [    4.326424] [drm] Connector 2:
Sep 10 22:41:31 TheMothership kernel: [    4.326425] [drm]   HDMI-A-2
Sep 10 22:41:31 TheMothership kernel: [    4.326426] [drm]   HPD2
Sep 10 22:41:31 TheMothership kernel: [    4.326427] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
Sep 10 22:41:31 TheMothership kernel: [    4.326428] [drm]   Encoders:
Sep 10 22:41:31 TheMothership kernel: [    4.326429] [drm]     DFP1: INTERNAL_UNIPHY3
Sep 10 22:41:31 TheMothership kernel: [    4.570385] [drm] fb mappable at 0xD0990000
Sep 10 22:41:31 TheMothership kernel: [    4.570389] [drm] vram apper at 0xD0000000
Sep 10 22:41:31 TheMothership kernel: [    4.570390] [drm] size 8294400
Sep 10 22:41:31 TheMothership kernel: [    4.570391] [drm] fb depth is 24
Sep 10 22:41:31 TheMothership kernel: [    4.570392] [drm]    pitch is 7680
Sep 10 22:41:31 TheMothership kernel: [    4.570671] fbcon: radeondrmfb (fb0) is primary device
Sep 10 22:41:31 TheMothership kernel: [    4.570771] Console: switching to colour frame buffer device 240x67
Sep 10 22:41:31 TheMothership kernel: [    4.570807] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
Sep 10 22:41:31 TheMothership kernel: [    4.570809] radeon 0000:00:01.0: registered panic notifier
Sep 10 22:41:31 TheMothership kernel: [    4.587644] kfd kfd: error getting iommu info. is the iommu enabled?
Sep 10 22:41:31 TheMothership kernel: [    4.587649] kfd kfd: Error initializing iommuv2 for device (1002:130f)
Sep 10 22:41:31 TheMothership kernel: [    4.587671] Creating topology SYSFS entries
Sep 10 22:41:31 TheMothership kernel: [    4.588221] kfd kfd: device (1002:130f) NOT added due to errors
Sep 10 22:41:31 TheMothership kernel: [    4.588226] [drm] Initialized radeon 2.40.0 20080528 for 0000:00:01.0 on minor 0
Sep 10 22:41:31 TheMothership kernel: [    5.525677] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Sep 10 22:41:31 TheMothership kernel: [   12.946757] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
Sep 10 22:41:31 TheMothership kernel: [   13.027187] init: failsafe main process (665) killed by TERM signal
Sep 10 22:41:31 TheMothership kernel: [   13.109537] Bluetooth: Core ver 2.20
Sep 10 22:41:31 TheMothership kernel: [   13.109561] NET: Registered protocol family 31
Sep 10 22:41:31 TheMothership kernel: [   13.109563] Bluetooth: HCI device and connection manager initialized
Sep 10 22:41:31 TheMothership kernel: [   13.109879] Bluetooth: HCI socket layer initialized
Sep 10 22:41:31 TheMothership kernel: [   13.109885] Bluetooth: L2CAP socket layer initialized
Sep 10 22:41:31 TheMothership kernel: [   13.109894] Bluetooth: SCO socket layer initialized
Sep 10 22:41:31 TheMothership kernel: [   13.117912] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 10 22:41:31 TheMothership kernel: [   13.117916] Bluetooth: BNEP filters: protocol multicast
Sep 10 22:41:31 TheMothership kernel: [   13.117922] Bluetooth: BNEP socket layer initialized
Sep 10 22:41:31 TheMothership kernel: [   13.123635] Bluetooth: RFCOMM TTY layer initialized
Sep 10 22:41:31 TheMothership kernel: [   13.123643] Bluetooth: RFCOMM socket layer initialized
Sep 10 22:41:31 TheMothership kernel: [   13.123651] Bluetooth: RFCOMM ver 1.11
Sep 10 22:41:31 TheMothership rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Sep 10 22:41:31 TheMothership avahi-daemon[815]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Sep 10 22:41:31 TheMothership avahi-daemon[815]: Successfully dropped root privileges.
Sep 10 22:41:31 TheMothership avahi-daemon[815]: avahi-daemon 0.6.31 starting up.
Sep 10 22:41:31 TheMothership avahi-daemon[815]: Successfully called chroot().
Sep 10 22:41:31 TheMothership avahi-daemon[815]: Successfully dropped remaining capabilities.
Sep 10 22:41:31 TheMothership kernel: [   13.157047] audit: type=1400 audit(1441950091.262:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=803 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.157057] audit: type=1400 audit(1441950091.262:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=803 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.157430] audit: type=1400 audit(1441950091.262:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=803 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership avahi-daemon[815]: No service file found in /etc/avahi/services.
Sep 10 22:41:31 TheMothership avahi-daemon[815]: Network interface enumeration completed.
Sep 10 22:41:31 TheMothership avahi-daemon[815]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep 10 22:41:31 TheMothership avahi-daemon[815]: Server startup complete. Host name is TheMothership.local. Local service cookie is 2421763489.
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> NetworkManager (version 0.9.8.8) is starting...
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> WEXT support is enabled
Sep 10 22:41:31 TheMothership kernel: [   13.180320] init: cups main process (832) killed by HUP signal
Sep 10 22:41:31 TheMothership kernel: [   13.180333] init: cups main process ended, respawning
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> DNS: loaded plugin dnsmasq
Sep 10 22:41:31 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Sep 10 22:41:31 TheMothership kernel: [   13.191624] audit: type=1400 audit(1441950091.298:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=858 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.191635] audit: type=1400 audit(1441950091.298:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=858 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.191641] audit: type=1400 audit(1441950091.298:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.192066] audit: type=1400 audit(1441950091.298:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=858 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.192071] audit: type=1400 audit(1441950091.298:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.192283] audit: type=1400 audit(1441950091.298:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership kernel: [   13.195416] audit: type=1400 audit(1441950091.302:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=857 comm="apparmor_parser"
Sep 10 22:41:31 TheMothership polkitd[856]: started daemon version 0.105 using authority implementation `local' version `0.105'
Sep 10 22:41:31 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: init!
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: update_system_hostname
Sep 10 22:41:31 TheMothership NetworkManager[836]:       interface-parser: parsing file /etc/network/interfaces
Sep 10 22:41:31 TheMothership NetworkManager[836]:       interface-parser: finished parsing file /etc/network/interfaces
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPluginIfupdown: management mode: unmanaged
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0/net/eth0, iface: eth0)
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: end _init.
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ofono: init!
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ofono: end _init.
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> Loaded plugin (null): (null)
Sep 10 22:41:31 TheMothership NetworkManager[836]:    Ifupdown: get unmanaged devices count: 0
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: (10547952) ... get_connections.
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ifupdown: (10547952) ... get_connections (managed=false): return empty list.
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ofono: (-536854160) ... get_connections.
Sep 10 22:41:31 TheMothership NetworkManager[836]:    SCPlugin-Ofono: (-536854160) connections count: 0
Sep 10 22:41:31 TheMothership NetworkManager[836]:    Ifupdown: get unmanaged devices count: 0
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> Networking is enabled by state file
Sep 10 22:41:31 TheMothership NetworkManager[836]: <warn> failed to allocate link cache: (-12) Object not found
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> (eth0): carrier is OFF
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> (eth0): bringing up device.
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> (eth0): preparing device.
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> (eth0): deactivating device (reason 'managed') [2]
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0/net/eth0
Sep 10 22:41:31 TheMothership kernel: [   13.272876] r8169 0000:03:00.0 eth0: link down
Sep 10 22:41:31 TheMothership kernel: [   13.272929] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 10 22:41:31 TheMothership kernel: [   13.272941] r8169 0000:03:00.0 eth0: link down
Sep 10 22:41:31 TheMothership NetworkManager[836]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 10 22:41:31 TheMothership NetworkManager[836]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> urfkill disappeared from the bus
Sep 10 22:41:31 TheMothership NetworkManager[836]: <info> ModemManager available in the bus
Sep 10 22:41:31 TheMothership cron[945]: (CRON) INFO (pidfile fd = 3)
Sep 10 22:41:31 TheMothership cron[1001]: (CRON) STARTUP (fork ok)
Sep 10 22:41:31 TheMothership anacron[993]: Anacron 2.3 started on 2015-09-10
Sep 10 22:41:31 TheMothership cron[1001]: (CRON) INFO (Running @reboot jobs)
Sep 10 22:41:31 TheMothership anacron[993]: Normal exit (0 jobs run)
Sep 10 22:41:31 TheMothership whoopsie[999]: whoopsie 0.2.24.6 starting up.
Sep 10 22:41:31 TheMothership whoopsie[999]: Using lock path: /var/lock/whoopsie/lock
Sep 10 22:41:31 TheMothership whoopsie[1036]: offline
Sep 10 22:41:31 TheMothership acpid: starting up with netlink and the input layer
Sep 10 22:41:31 TheMothership acpid: 9 rules loaded
Sep 10 22:41:31 TheMothership acpid: waiting for events: event logging is off
Sep 10 22:41:32 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Sep 10 22:41:32 TheMothership accounts-daemon[1132]: started daemon version 0.6.35
Sep 10 22:41:32 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.Accounts'
Sep 10 22:41:33 TheMothership ModemManager[750]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0': not supported by any plugin
Sep 10 22:41:33 TheMothership kernel: [   15.327966] init: plymouth-upstart-bridge main process ended, respawning
Sep 10 22:41:33 TheMothership kernel: [   15.333879] init: plymouth-upstart-bridge main process (1150) terminated with status 1
Sep 10 22:41:33 TheMothership kernel: [   15.333892] init: plymouth-upstart-bridge main process ended, respawning
Sep 10 22:41:34 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Sep 10 22:41:34 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.UPower'
Sep 10 22:41:34 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Sep 10 22:41:34 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully called chroot.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully dropped privileges.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully limited resources.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Running.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Watchdog thread running.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Canary thread running.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully made thread 1310 of process 1310 (n/a) owned by '112' high priority at nice level -11.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Supervising 1 threads of 1 processes of 1 users.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully made thread 1322 of process 1310 (n/a) owned by '112' RT at priority 5.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Supervising 2 threads of 1 processes of 1 users.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully made thread 1340 of process 1310 (n/a) owned by '112' RT at priority 5.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Supervising 3 threads of 1 processes of 1 users.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully made thread 1344 of process 1310 (n/a) owned by '112' RT at priority 5.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Supervising 4 threads of 1 processes of 1 users.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Successfully made thread 1363 of process 1363 (n/a) owned by '112' high priority at nice level -11.
Sep 10 22:41:34 TheMothership rtkit-daemon[1313]: Supervising 5 threads of 2 processes of 1 users.
Sep 10 22:41:34 TheMothership pulseaudio[1363]: [pulseaudio] pid.c: Daemon already running.
Sep 10 22:41:34 TheMothership anacron[1372]: Anacron 2.3 started on 2015-09-10
Sep 10 22:41:34 TheMothership anacron[1372]: Normal exit (0 jobs run)
Sep 10 22:41:34 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Sep 10 22:41:34 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.systemd1'
Sep 10 22:41:34 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Sep 10 22:41:34 TheMothership colord: Using config file /etc/colord.conf
Sep 10 22:41:34 TheMothership colord: Using mapping database file /var/lib/colord/mapping.db
Sep 10 22:41:34 TheMothership colord: Using device database file /var/lib/colord/storage.db
Sep 10 22:41:34 TheMothership colord: loaded plugin libcd_plugin_scanner.so
Sep 10 22:41:34 TheMothership colord: loaded plugin libcd_plugin_camera.so
Sep 10 22:41:34 TheMothership colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Sep 10 22:41:34 TheMothership colord: Daemon ready for requests
Sep 10 22:41:34 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Sep 10 22:41:34 TheMothership colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Sep 10 22:41:34 TheMothership colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Sep 10 22:41:34 TheMothership colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Sep 10 22:41:34 TheMothership colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Sep 10 22:41:34 TheMothership colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Sep 10 22:41:34 TheMothership colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Sep 10 22:41:34 TheMothership colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Sep 10 22:41:34 TheMothership colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Sep 10 22:41:34 TheMothership colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Sep 10 22:41:34 TheMothership colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Sep 10 22:41:34 TheMothership colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Sep 10 22:41:34 TheMothership colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> (eth0): carrier now ON (device state 20)
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Auto-activating connection 'Wired connection 1'.
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) starting connection 'Wired connection 1'
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> NetworkManager state is now CONNECTING
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 10 22:41:34 TheMothership kernel: [   16.833752] r8169 0000:03:00.0 eth0: link up
Sep 10 22:41:34 TheMothership kernel: [   16.833766] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 10 22:41:34 TheMothership colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Sep 10 22:41:34 TheMothership colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 10 22:41:34 TheMothership colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Sep 10 22:41:34 TheMothership colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Sep 10 22:41:34 TheMothership colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Sep 10 22:41:34 TheMothership colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Sep 10 22:41:34 TheMothership colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Sep 10 22:41:34 TheMothership colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Sep 10 22:41:34 TheMothership colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Sep 10 22:41:34 TheMothership colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Sep 10 22:41:34 TheMothership colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Sep 10 22:41:34 TheMothership colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> dhclient started with pid 1494
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Beginning IP6 addrconf.
Sep 10 22:41:34 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 10 22:41:34 TheMothership dhclient: Internet Systems Consortium DHCP Client 4.2.4
Sep 10 22:41:34 TheMothership dhclient: Copyright 2004-2012 Internet Systems Consortium.
Sep 10 22:41:34 TheMothership dhclient: All rights reserved.
Sep 10 22:41:34 TheMothership dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep 10 22:41:34 TheMothership dhclient: 
Sep 10 22:41:35 TheMothership NetworkManager[836]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 10 22:41:35 TheMothership dhclient: Listening on LPF/eth0/b8:97:5a:ae:70:b4
Sep 10 22:41:35 TheMothership dhclient: Sending on   LPF/eth0/b8:97:5a:ae:70:b4
Sep 10 22:41:35 TheMothership dhclient: Sending on   Socket/fallback
Sep 10 22:41:35 TheMothership dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xe897996d)
Sep 10 22:41:35 TheMothership dhclient: DHCPREQUEST of 192.168.0.19 on eth0 to 255.255.255.255 port 67 (xid=0x6d9997e8)
Sep 10 22:41:35 TheMothership dhclient: DHCPOFFER of 192.168.0.19 from 192.168.0.1
Sep 10 22:41:35 TheMothership colord: Device added: xrandr-Acer Technologies-G226HQL-LYLAA0018500
Sep 10 22:41:35 TheMothership colord: Automatic metadata add icc-94aa530e03404e3131d72e6bb9341aa0 to xrandr-Acer Technologies-G226HQL-LYLAA0018500
Sep 10 22:41:35 TheMothership colord: Profile added: icc-94aa530e03404e3131d72e6bb9341aa0
Sep 10 22:41:36 TheMothership avahi-daemon[815]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::ba97:5aff:feae:70b4.
Sep 10 22:41:36 TheMothership avahi-daemon[815]: New relevant interface eth0.IPv6 for mDNS.
Sep 10 22:41:36 TheMothership avahi-daemon[815]: Registering new address record for fe80::ba97:5aff:feae:70b4 on eth0.*.
Sep 10 22:41:36 TheMothership dhclient: DHCPACK of 192.168.0.19 from 192.168.0.1
Sep 10 22:41:36 TheMothership dhclient: bound to 192.168.0.19 -- renewal in 32595 seconds.
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info>   address 192.168.0.19
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info>   prefix 24 (255.255.255.0)
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info>   gateway 192.168.0.1
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info>   nameserver '68.105.28.11'
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info>   nameserver '68.105.29.11'
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info>   nameserver '68.105.28.12'
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 10 22:41:36 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep 10 22:41:36 TheMothership avahi-daemon[815]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.19.
Sep 10 22:41:36 TheMothership avahi-daemon[815]: New relevant interface eth0.IPv4 for mDNS.
Sep 10 22:41:36 TheMothership avahi-daemon[815]: Registering new address record for 192.168.0.19 on eth0.IPv4.
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> DNS: starting dnsmasq...
Sep 10 22:41:37 TheMothership NetworkManager[836]: <warn> dnsmasq not available on the bus, can't update servers.
Sep 10 22:41:37 TheMothership NetworkManager[836]: <error> [1441950097.213991] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Sep 10 22:41:37 TheMothership NetworkManager[836]: <warn> DNS: plugin dnsmasq update failed
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> Writing DNS information to /sbin/resolvconf
Sep 10 22:41:37 TheMothership dnsmasq[1505]: started, version 2.68 cache disabled
Sep 10 22:41:37 TheMothership dnsmasq[1505]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Sep 10 22:41:37 TheMothership dnsmasq[1505]: DBus support enabled: connected to system bus
Sep 10 22:41:37 TheMothership dnsmasq[1505]: warning: no upstream servers configured
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> Activation (eth0) successful, device activated.
Sep 10 22:41:37 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 10 22:41:37 TheMothership NetworkManager[836]: <warn> dnsmasq appeared on DBus: :1.43
Sep 10 22:41:37 TheMothership NetworkManager[836]: <info> Writing DNS information to /sbin/resolvconf
Sep 10 22:41:37 TheMothership dnsmasq[1505]: setting upstream servers from DBus
Sep 10 22:41:37 TheMothership dnsmasq[1505]: using nameserver 68.105.28.12#53
Sep 10 22:41:37 TheMothership dnsmasq[1505]: using nameserver 68.105.29.11#53
Sep 10 22:41:37 TheMothership dnsmasq[1505]: using nameserver 68.105.28.11#53
Sep 10 22:41:37 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 10 22:41:37 TheMothership whoopsie[1036]: message repeated 3 times: [ offline]
Sep 10 22:41:38 TheMothership whoopsie[1036]: online
Sep 10 22:41:41 TheMothership NetworkManager[836]: <info> WiFi hardware radio set enabled
Sep 10 22:41:40 TheMothership ntpdate[1603]: step time server 91.189.94.4 offset -3.416622 sec
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership colord: device removed: xrandr-Acer Technologies-G226HQL-LYLAA0018500
Sep 10 22:41:45 TheMothership colord: Profile removed: icc-94aa530e03404e3131d72e6bb9341aa0
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:45 TheMothership NetworkManager[836]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.22': no such name
Sep 10 22:41:46 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Sep 10 22:41:46 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.systemd1'
Sep 10 22:41:46 TheMothership rtkit-daemon[1313]: Successfully made thread 1956 of process 1956 (n/a) owned by '1000' high priority at nice level -11.
Sep 10 22:41:46 TheMothership rtkit-daemon[1313]: Supervising 5 threads of 2 processes of 2 users.
Sep 10 22:41:47 TheMothership rtkit-daemon[1313]: Successfully made thread 1984 of process 1956 (n/a) owned by '1000' RT at priority 5.
Sep 10 22:41:47 TheMothership rtkit-daemon[1313]: Supervising 6 threads of 2 processes of 2 users.
Sep 10 22:41:47 TheMothership rtkit-daemon[1313]: Successfully made thread 1985 of process 1956 (n/a) owned by '1000' RT at priority 5.
Sep 10 22:41:47 TheMothership rtkit-daemon[1313]: Supervising 7 threads of 2 processes of 2 users.
Sep 10 22:41:47 TheMothership rtkit-daemon[1313]: Successfully made thread 1986 of process 1956 (n/a) owned by '1000' RT at priority 5.
Sep 10 22:41:47 TheMothership rtkit-daemon[1313]: Supervising 8 threads of 2 processes of 2 users.
Sep 10 22:41:47 TheMothership colord: Device added: xrandr-Acer Technologies-G226HQL-LYLAA0018500
Sep 10 22:41:47 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Sep 10 22:41:47 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.locale1'
Sep 10 22:41:47 TheMothership colord: Automatic metadata add icc-bb0db35c4a43b2ee829f4a8dcd489666 to xrandr-Acer Technologies-G226HQL-LYLAA0018500
Sep 10 22:41:47 TheMothership colord: Profile added: icc-bb0db35c4a43b2ee829f4a8dcd489666
Sep 10 22:41:48 TheMothership dbus[719]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Sep 10 22:41:48 TheMothership udisksd[2064]: udisks daemon version 2.1.3 starting
Sep 10 22:41:48 TheMothership dbus[719]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Sep 10 22:41:48 TheMothership udisksd[2064]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Sep 10 22:41:51 TheMothership NetworkManager[836]: <info> (eth0): IP6 addrconf timed out or failed.
Sep 10 22:41:51 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 10 22:41:51 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 10 22:41:51 TheMothership NetworkManager[836]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 10 22:41:57 TheMothership kernel: [   43.255803] audit_printk_skb: 132 callbacks suppressed
Sep 10 22:41:57 TheMothership kernel: [   43.255807] audit: type=1400 audit(1441950117.949:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2180 comm="apparmor_parser"
Sep 10 22:41:57 TheMothership kernel: [   43.255817] audit: type=1400 audit(1441950117.949:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2180 comm="apparmor_parser"
Sep 10 22:41:57 TheMothership kernel: [   43.256269] audit: type=1400 audit(1441950117.953:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2180 comm="apparmor_parser"[CODE]
```
[/CODE]

---

### Post by ian-weisser on 2015-09-11
> **amloren1 said:**
> [    0.268109] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM

Well, the kernel log timestamp [0.268109] indicates the message was generated .268 seconds after poweron, so it's probably not a pre-crash item. It seems part of the post-crash reboot.
[This AskUbuntu question]("http://askubuntu.com/questions/86499/error-about-acpi-osc-request-failed-ae-not-found") seems to indicate it's the kernel probing for a power-saving mode on your hardware, and not finding it. This seems unsurprising - the kernel probes for lots of hardware and features during boot.

> **amloren1 said:**
> ]Sep 10 22:41:31 TheMothership kernel: [    3.046008] input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input12
...
Sep 10 22:41:57 TheMothership kernel: [   43.256269] audit: type=1400 audit(1441950117.953:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2180 comm="apparmor_parser"

This sequence looks like a fairly typical reboot to me, the log covering from 3.04600 seconds to 43.256269 seconds after poweron. Unfortunately, after a poweroff or reboot, the system retains no memory of why it crashed. That's why it keeps logs.

It seems looks like your crashes are not being logged.
That suggests that something really low-level is crashing: A hardware failure or kernel crash, not the fault of the OS nor any application nor any feature). Either the crash is so sudden that a log cannot be generated, or it's so unexpected that developers never thought to create an error message for it. The latter is moderately rare, developers put in a *ton* of error messages.

Without useful log clues, troubleshooting becomes a bit more hit or miss. Here's what I would try next:
1) Rule out the kernel - see if you can get the crash to recur using the 15.04 kernel. Boot from a 15.04 LiveUSB for a few days.
2) Rule out thermal - I know you have a great cooler, but[ install a temp monitor]("http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature") and look for spikes around crash times.

---

### Post by amloren1 on 2015-09-11
more of the syslog after a recent crash, sorry if this is repeated. Having trouble posting this



```


Sep 10 23:17:01 TheMothership CRON[2986]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 00:17:01 TheMothership CRON[3015]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 01:17:01 TheMothership CRON[3038]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 02:17:01 TheMothership CRON[3051]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 03:17:01 TheMothership CRON[3087]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 04:17:01 TheMothership CRON[3103]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 05:17:01 TheMothership CRON[3129]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 06:17:01 TheMothership CRON[3145]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 06:25:01 TheMothership CRON[3153]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Sep 11 06:54:12 TheMothership kernel: [29571.941673] it87: Found IT8772E chip at 0xa30, revision 1
Sep 11 06:54:12 TheMothership kernel: [29571.941689] it87: Beeping is supported
Sep 11 06:54:12 TheMothership kernel: [29571.941729] ACPI Warning: SystemIO range 0x0000000000000a35-0x0000000000000a36 conflicts with OpRegion 0x0000000000000a35-0x0000000000000a36 (\SENP) (20141107/utaddress-258)
Sep 11 06:54:12 TheMothership kernel: [29571.941736] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 11 07:17:01 TheMothership CRON[4041]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 07:20:30 TheMothership rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="839" x-info="http://www.rsyslog.com"] start
Sep 11 07:20:30 TheMothership rsyslogd: rsyslogd's groupid changed to 104
Sep 11 07:20:30 TheMothership rsyslogd: rsyslogd's userid changed to 101
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Initializing cgroup subsys cpuacct
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Linux version 3.19.0-28-generic (buildd@lgw01-21) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 (Ubuntu 3.19.0-28.30~14.04.1-generic 3.19.8-ckt5)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-28-generic root=UUID=b4e01cbd-282d-4e55-a39f-4383dc417a47 ro quiet splash vt.handoff=7
Sep 11 07:20:30 TheMothership kernel: [    0.000000] KERNEL supported cpus:
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   Intel GenuineIntel
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   AMD AuthenticAMD
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   Centaur CentaurHauls
Sep 11 07:20:30 TheMothership kernel: [    0.000000] tseg: 00cf000000
Sep 11 07:20:30 TheMothership kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cbc29fff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000cbc2a000-0x00000000cc648fff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000cc649000-0x00000000cc919fff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000cc91a000-0x00000000cc9d2fff] ACPI NVS
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000cc9d3000-0x00000000cdec0fff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000cdec1000-0x00000000cdec1fff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000cdec2000-0x00000000ce0c7fff] ACPI NVS
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce0c8000-0x00000000ce21efff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce21f000-0x00000000ce83bfff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce83c000-0x00000000ce86ffff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce870000-0x00000000ceff0fff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000ceff1000-0x00000000ceffffff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec01fff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000003eeffffff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] NX (Execute Disable) protection: active
Sep 11 07:20:30 TheMothership kernel: [    0.000000] SMBIOS 2.8 present.
Sep 11 07:20:30 TheMothership kernel: [    0.000000] DMI: BIOSTAR Group Hi-Fi A70U3P/Hi-Fi A70U3P, BIOS 4.6.5 10/29/2014
Sep 11 07:20:30 TheMothership kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] AGP: No AGP bridge found
Sep 11 07:20:30 TheMothership kernel: [    0.000000] e820: last_pfn = 0x3ef000 max_arch_pfn = 0x400000000
Sep 11 07:20:30 TheMothership kernel: [    0.000000] MTRR default type: uncachable
Sep 11 07:20:30 TheMothership kernel: [    0.000000] MTRR fixed ranges enabled:
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   00000-9FFFF write-back
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   A0000-BFFFF write-through
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   C0000-CFFFF write-protect
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   D0000-E7FFF uncachable
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   E8000-FFFFF write-protect
Sep 11 07:20:30 TheMothership kernel: [    0.000000] MTRR variable ranges enabled:
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   3 disabled
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   4 disabled
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   5 disabled
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   6 disabled
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   7 disabled
Sep 11 07:20:30 TheMothership kernel: [    0.000000] TOM2: 000000042f000000 aka 17136M
Sep 11 07:20:30 TheMothership kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
Sep 11 07:20:30 TheMothership kernel: [    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000] e820: last_pfn = 0xcf000 max_arch_pfn = 0x400000000
Sep 11 07:20:30 TheMothership kernel: [    0.000000] found SMP MP-table at [mem 0x000fd7c0-0x000fd7cf] mapped at [ffff8800000fd7c0]
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Scanning 1 areas for low memory corruption
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Using GB pages for direct mapping
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0x3eee00000-0x3eeffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x3eee00000-0x3eeffffff] page 2M
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0x3e0000000-0x3eedfffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x3e0000000-0x3eedfffff] page 2M
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0x3c0000000-0x3dfffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x3c0000000-0x3dfffffff] page 2M
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xcbc29fff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0xc0000000-0xcbbfffff] page 2M
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0xcbc00000-0xcbc29fff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0xcc649000-0xcc919fff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0xcc649000-0xcc919fff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
Sep 11 07:20:30 TheMothership kernel: [    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0xcdec1000-0xcdec1fff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0xcdec1000-0xcdec1fff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0xce0c8000-0xce21efff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0xce0c8000-0xce21efff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0xce83c000-0xce86ffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0xce83c000-0xce86ffff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0xceff1000-0xceffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0xceff1000-0xceffffff] page 4k
Sep 11 07:20:30 TheMothership kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x3bfffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [mem 0x100000000-0x3bfffffff] page 1G
Sep 11 07:20:30 TheMothership kernel: [    0.000000] RAMDISK: [mem 0x35a2a000-0x36d0cfff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: Early table checksum verification disabled
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: RSDP 0x00000000000F04A0 000024 (v02 ALASKA)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: XSDT 0x00000000CC99E080 00007C (v01 ALASKA A M I    01072009 AMI  00010013)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: FACP 0x00000000CC9A3060 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20141107/tbfadt-654)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: DSDT 0x00000000CC99E190 004ECC (v02 ALASKA A M I    00000000 INTL 20051117)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: FACS 0x00000000CC9C9D80 000040
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: APIC 0x00000000CC9A3170 00007E (v03 ALASKA A M I    01072009 AMI  00010013)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: FPDT 0x00000000CC9A31F0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: FIDT 0x00000000CC9A3238 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: MCFG 0x00000000CC9A32D8 00003C (v01 ALASKA A M I    01072009 MSFT 00010013)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: HPET 0x00000000CC9A3318 000038 (v01 ALASKA A M I    01072009 AMI  00000005)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: UEFI 0x00000000CC9A3350 000042 (v01 ALASKA A M I    01072009      00000000)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: SSDT 0x00000000CC9A3398 000EE4 (v01 AMD    BANTRY   00000001 AMD  00000001)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: SSDT 0x00000000CC9A4280 00033B (v02 AMD    BANTRY   00000002 MSFT 04000000)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: CRAT 0x00000000CC9A45C0 0005A0 (v01 AMD    BANTRY   00000001 AMD  00000001)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: SSDT 0x00000000CC9A4B60 00122C (v01 AMD    CPMCMN   00000001 INTL 20051117)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 11 07:20:30 TheMothership kernel: [    0.000000] No NUMA configuration found
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x00000003eeffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x3eeff4000-0x3eeff8fff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]  [ffffea0000000000-ffffea000fbfffff] PMD -> [ffff8803df600000-ffff8803ee5fffff] on node 0
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Zone ranges:
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   Normal   [mem 0x100000000-0x3eeffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Movable zone start for each node
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Early memory node ranges
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0x00100000-0xcbc29fff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0xcc649000-0xcc919fff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0xcdec1000-0xcdec1fff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0xce0c8000-0xce21efff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0xce83c000-0xce86ffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0xceff1000-0xceffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   node   0: [mem 0x100000000-0x3eeffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Initmem setup node 0 [mem 0x00001000-0x3eeffffff]
Sep 11 07:20:30 TheMothership kernel: [    0.000000] On node 0 totalpages: 3911732
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   DMA zone: 21 pages reserved
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   DMA32 zone: 12995 pages used for memmap
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   DMA32 zone: 831638 pages, LIFO batch:31
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   Normal zone: 48064 pages used for memmap
Sep 11 07:20:30 TheMothership kernel: [    0.000000]   Normal zone: 3076096 pages, LIFO batch:31
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Sep 11 07:20:30 TheMothership kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec01000] gsi_base[24])
Sep 11 07:20:30 TheMothership kernel: [    0.000000] IOAPIC[1]: apic_id 1, version 33, address 0xfec01000, GSI 24-55
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep 11 07:20:30 TheMothership kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 11 07:20:30 TheMothership kernel: [    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
Sep 11 07:20:30 TheMothership kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Sep 11 07:20:30 TheMothership kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff

```

---

### Post by amloren1 on 2015-09-11
The last crash did allow me to use REISEB. 

Also I am having trouble with sensors. Seems it doesn't have access to the thermal readings. Right now it says all temps are near freezing. Still tinkering with this though

---

### Post by amloren1 on 2015-09-12
bump

---

### Post by ian-weisser on 2015-09-12
Awaiting your result from trying a different kernel.

---

### Post by amloren1 on 2015-09-14
Thanks for waiting I've tested it with 2 other variants. Xubuntu 14.04 (I know its the same as Ub 14.04) and Ubuntu 15. Both having the same issues. I will post another log report when it crashes again. 

 The time on the UEFI BIOS resets itself every time I change it. Maybe there's a related issue there. I also tried a update. Every time I tried to update the BIOS I got a CMOS fail. So I understand this could be a CMOS battery issue or something else is wonky with the mobo.

---

### Post by amloren1 on 2015-09-14
Most recent syslog after a crash



```


Sep 13 21:06:03 NewOne anacron[648]: Job `cron.daily' terminated
Sep 13 21:06:03 NewOne anacron[648]: Normal exit (1 job run)
Sep 13 21:07:11 NewOne com.ubuntu.OneConf[914]: WARNING:oneconf.hosts:Error in loading other_hosts file: [Errno 2] No such file or directory: '/home/alejandro/.cache/oneconf/f3edf1003ebe4d0f947b1c8ae11ce9ac/other_hosts'
Sep 13 21:12:00 NewOne systemd[1]: Starting Cleanup of Temporary Directories...
Sep 13 21:12:00 NewOne systemd-tmpfiles[2930]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Sep 13 21:12:00 NewOne systemd[1]: Started Cleanup of Temporary Directories.
Sep 13 21:12:47 NewOne kernel: [  947.215851] show_signal_msg: 39 callbacks suppressed
Sep 13 21:12:47 NewOne kernel: [  947.215860] Compositor[2263]: segfault at fffff4cd334eabeb ip 00007ff014ee5119 sp 00007ff00239daa0 error 5 in chrome[7ff013f90000+576c000]
Sep 13 21:17:01 NewOne CRON[2988]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 13 22:17:01 NewOne CRON[3150]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 13 22:25:23 NewOne kernel: [ 5302.707650] Compositor[2943]: segfault at fffff4cd32a42c8b ip 00007ff014ee5119 sp 00007ff00239daa0 error 5 in chrome[7ff013f90000+576c000]
Sep 13 23:12:15 NewOne rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="691" x-info="http://www.rsyslog.com"] start
Sep 13 23:12:15 NewOne rsyslogd: rsyslogd's groupid changed to 110
Sep 13 23:12:15 NewOne rsyslogd: rsyslogd's userid changed to 104
Sep 13 23:12:15 NewOne systemd-modules-load[224]: Inserted module 'lp'
Sep 13 23:12:15 NewOne systemd-modules-load[224]: Inserted module 'ppdev'
Sep 13 23:12:15 NewOne systemd-modules-load[224]: Inserted module 'parport_pc'
Sep 13 23:12:15 NewOne systemd-modules-load[224]: Module 'fuse' is builtin
Sep 13 23:12:15 NewOne systemd-udevd[263]: starting version 219
Sep 13 23:12:15 NewOne systemd[1]: Started udev Kernel Device Manager.
Sep 13 23:12:15 NewOne systemd[1]: Starting Show Plymouth Boot Screen...
Sep 13 23:12:15 NewOne mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:10.0/usb1/1-1"
Sep 13 23:12:15 NewOne mtp-probe: bus: 1, device: 2 was not an MTP device
Sep 13 23:12:15 NewOne mtp-probe: checking bus 8, device 2: "/sys/devices/pci0000:00/0000:00:13.0/usb8/8-1"
Sep 13 23:12:15 NewOne mtp-probe: bus: 8, device: 2 was not an MTP device
Sep 13 23:12:15 NewOne systemd[1]: Created slice system-ifup.slice.
Sep 13 23:12:15 NewOne systemd[1]: Starting system-ifup.slice.
Sep 13 23:12:15 NewOne systemd[1]: Found device WDC_WD10EZEX-60M2NA0 2.
Sep 13 23:12:15 NewOne systemd[1]: Activating swap /dev/disk/by-uuid/6bad8b54-27d9-46fe-af88-737aa5489a48...
Sep 13 23:12:15 NewOne systemd[1]: Found device WDC_WD10EZEX-60M2NA0 1.
Sep 13 23:12:15 NewOne systemd[1]: Found device SanDisk_SDSSDHII120G 1.
Sep 13 23:12:15 NewOne systemd[1]: Activated swap /dev/disk/by-uuid/6bad8b54-27d9-46fe-af88-737aa5489a48.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Swap.
Sep 13 23:12:15 NewOne systemd[1]: Starting Swap.
Sep 13 23:12:15 NewOne systemd[1]: Found device WDC_WD10EZEX-60M2NA0 3.
Sep 13 23:12:15 NewOne systemd[1]: Received SIGRTMIN+20 from PID 271 (plymouthd).
Sep 13 23:12:15 NewOne systemd[1]: Started Show Plymouth Boot Screen.
Sep 13 23:12:15 NewOne systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Sep 13 23:12:15 NewOne systemd[1]: Starting Forward Password Requests to Plymouth Directory Watch.
Sep 13 23:12:15 NewOne systemd[1]: Started Dispatch Password Requests to Console Directory Watch.
Sep 13 23:12:15 NewOne systemd[1]: plymouth-start.service: main process exited, code=killed, status=11/SEGV
Sep 13 23:12:15 NewOne systemd[1]: Unit plymouth-start.service entered failed state.
Sep 13 23:12:15 NewOne systemd[1]: plymouth-start.service failed.
Sep 13 23:12:15 NewOne systemd[1]: Started udev Wait for Complete Device Initialization.
Sep 13 23:12:15 NewOne systemd[1]: Starting Copy rules generated while the root was ro...
Sep 13 23:12:15 NewOne systemd[1]: Started Recovery mode menu.
Sep 13 23:12:15 NewOne systemd[1]: Starting File System Check on Root Device...
Sep 13 23:12:15 NewOne systemd[1]: Started Copy rules generated while the root was ro.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Sound Card.
Sep 13 23:12:15 NewOne systemd[1]: Starting Sound Card.
Sep 13 23:12:15 NewOne systemd[1]: Started File System Check Daemon to report status.
Sep 13 23:12:15 NewOne systemd[1]: Starting File System Check Daemon to report status...
Sep 13 23:12:15 NewOne systemd-fsck[414]: /dev/sda2: clean, 208768/7315456 files, 1446188/29256192 blocks
Sep 13 23:12:15 NewOne systemd[1]: Started File System Check on Root Device.
Sep 13 23:12:15 NewOne systemd[1]: Starting Remount Root and Kernel File Systems...
Sep 13 23:12:15 NewOne systemd[1]: Started Remount Root and Kernel File Systems.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Local File Systems (Pre).
Sep 13 23:12:15 NewOne systemd[1]: Starting Local File Systems (Pre).
Sep 13 23:12:15 NewOne systemd[1]: Starting File System Check on /dev/disk/by-uuid/5eef3b19-74e5-4bc9-9685-a511f79bc61f...
Sep 13 23:12:15 NewOne systemd[1]: Starting File System Check on /dev/disk/by-uuid/8440fcbe-d04e-404b-855c-995ee695a598...
Sep 13 23:12:15 NewOne systemd[1]: Starting File System Check on /dev/disk/by-uuid/0e4295d6-79bc-41a6-9062-d7110345f60e...
Sep 13 23:12:15 NewOne systemd[1]: Started Rebuild Hardware Database.
Sep 13 23:12:15 NewOne systemd-fsck[428]: /dev/sda1: recovering journal
Sep 13 23:12:15 NewOne systemd-fsck[428]: /dev/sda1: clean, 308/48768 files, 99334/194560 blocks
Sep 13 23:12:15 NewOne systemd[1]: Started File System Check on /dev/disk/by-uuid/0e4295d6-79bc-41a6-9062-d7110345f60e.
Sep 13 23:12:15 NewOne systemd[1]: Mounting /boot...
Sep 13 23:12:15 NewOne systemd[1]: Mounted /boot.
Sep 13 23:12:15 NewOne systemd-fsck[426]: /dev/sdb1: recovering journal
Sep 13 23:12:15 NewOne systemd-fsck[426]: /dev/sdb1: Clearing orphaned inode 260846 (uid=1000, gid=1000, mode=0100600, size=4104)
Sep 13 23:12:15 NewOne systemd-fsck[426]: /dev/sdb1: Clearing orphaned inode 261000 (uid=1000, gid=1000, mode=0100600, size=2052)
Sep 13 23:12:15 NewOne systemd-fsck[426]: /dev/sdb1: Clearing orphaned inode 260997 (uid=1000, gid=1000, mode=0100600, size=16400)
Sep 13 23:12:15 NewOne systemd-fsck[426]: /dev/sdb1: Clearing orphaned inode 260906 (uid=1000, gid=1000, mode=0100600, size=4104)
Sep 13 23:12:15 NewOne systemd-fsck[426]: /dev/sdb1: clean, 10033/610800 files, 289673/2441216 blocks
Sep 13 23:12:15 NewOne systemd[1]: Started File System Check on /dev/disk/by-uuid/5eef3b19-74e5-4bc9-9685-a511f79bc61f.
Sep 13 23:12:15 NewOne systemd[1]: var.mount: Directory /var to mount over is not empty, mounting anyway.
Sep 13 23:12:15 NewOne systemd[1]: Mounting /var...
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: recovering journal
Sep 13 23:12:15 NewOne systemd[1]: Mounted /var.
Sep 13 23:12:15 NewOne systemd[1]: Started Various fixups to make systemd work better on Debian.
Sep 13 23:12:15 NewOne systemd[1]: Starting Load/Save Random Seed...
Sep 13 23:12:15 NewOne systemd[1]: Started Read required files in advance.
Sep 13 23:12:15 NewOne systemd[1]: Starting Read required files in advance...
Sep 13 23:12:15 NewOne systemd[1]: Starting Flush Journal to Persistent Storage...
Sep 13 23:12:15 NewOne systemd[1]: Started Flush Journal to Persistent Storage.
Sep 13 23:12:15 NewOne systemd[1]: Started Load/Save Random Seed.
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27267836 (uid=1000, gid=1000, mode=0100600, size=19873792)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27008276 (uid=1000, gid=1000, mode=0100664, size=10788)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27007394 (uid=1000, gid=1000, mode=0100664, size=32768)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27002091 (uid=1000, gid=1000, mode=0100600, size=544)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27002088 (uid=1000, gid=1000, mode=0100640, size=85)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27001065 (uid=1000, gid=1000, mode=0100640, size=1544)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27002097 (uid=1000, gid=1000, mode=0100640, size=230)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27006458 (uid=1000, gid=1000, mode=0100640, size=164)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27007498 (uid=1000, gid=1000, mode=0100664, size=10788)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27002096 (uid=1000, gid=1000, mode=0100664, size=10788)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: Clearing orphaned inode 27006467 (uid=1000, gid=1000, mode=0100664, size=10788)
Sep 13 23:12:15 NewOne systemd-fsck[427]: /dev/sdb3: clean, 36977/58490880 files, 6382870/233936384 blocks
Sep 13 23:12:15 NewOne systemd[1]: Started File System Check on /dev/disk/by-uuid/8440fcbe-d04e-404b-855c-995ee695a598.
Sep 13 23:12:15 NewOne systemd[1]: Mounting /home...
Sep 13 23:12:15 NewOne systemd[1]: Mounted /home.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Local File Systems.
Sep 13 23:12:15 NewOne systemd[1]: Starting Local File Systems.
Sep 13 23:12:15 NewOne systemd[1]: Starting Create Volatile Files and Directories...
Sep 13 23:12:15 NewOne systemd[1]: Starting Set console keymap...
Sep 13 23:12:15 NewOne systemd[1]: Started Commit a transient machine-id on disk.
Sep 13 23:12:15 NewOne systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
Sep 13 23:12:15 NewOne systemd[1]: Starting LSB: AppArmor initialization...
Sep 13 23:12:15 NewOne systemd[1]: Starting Wait for all "auto" /etc/network/interfaces to be up for network-online.target...
Sep 13 23:12:15 NewOne systemd-tmpfiles[461]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Remote File Systems.
Sep 13 23:12:15 NewOne systemd[1]: Starting Remote File Systems.
Sep 13 23:12:15 NewOne systemd[1]: Started Wait for all "auto" /etc/network/interfaces to be up for network-online.target.
Sep 13 23:12:15 NewOne apparmor[464]: * Starting AppArmor profiles
Sep 13 23:12:15 NewOne systemd[1]: Started Tell Plymouth To Write Out Runtime Data.
Sep 13 23:12:15 NewOne apparmor[464]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Sep 13 23:12:15 NewOne loadkeys[462]: Loading /etc/console-setup/cached.kmap.gz
Sep 13 23:12:15 NewOne systemd[1]: Started Set console keymap.
Sep 13 23:12:15 NewOne systemd[1]: Started Create Volatile Files and Directories.
Sep 13 23:12:15 NewOne apparmor[464]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Sep 13 23:12:15 NewOne systemd[1]: Starting Network Time Synchronization...
Sep 13 23:12:15 NewOne systemd[1]: Starting Update UTMP about System Boot/Shutdown...
Sep 13 23:12:15 NewOne systemd[1]: Started Network Time Synchronization.
Sep 13 23:12:15 NewOne systemd[1]: Reached target System Time Synchronized.
Sep 13 23:12:15 NewOne systemd[1]: Starting System Time Synchronized.
Sep 13 23:12:15 NewOne systemd[1]: Started Update UTMP about System Boot/Shutdown.
Sep 13 23:12:15 NewOne apparmor[464]: ...done.
Sep 13 23:12:15 NewOne systemd[1]: Started LSB: AppArmor initialization.
Sep 13 23:12:15 NewOne systemd[1]: Started ifup for eth0.
Sep 13 23:12:15 NewOne systemd[1]: Starting ifup for eth0...
Sep 13 23:12:15 NewOne systemd[1]: Starting LSB: Raise network interfaces....
Sep 13 23:12:15 NewOne sh[528]: Unknown interface eth0
Sep 13 23:12:15 NewOne networking[529]: * Configuring network interfaces...
Sep 13 23:12:15 NewOne networking[529]: ...done.
Sep 13 23:12:15 NewOne systemd[1]: Started LSB: Raise network interfaces..
Sep 13 23:12:15 NewOne systemd[1]: Reached target System Initialization.
Sep 13 23:12:15 NewOne systemd[1]: Starting System Initialization.
Sep 13 23:12:15 NewOne systemd[1]: Listening on ACPID Listen Socket.
Sep 13 23:12:15 NewOne systemd[1]: Starting ACPID Listen Socket.
Sep 13 23:12:15 NewOne systemd[1]: Listening on UUID daemon activation socket.
Sep 13 23:12:15 NewOne systemd[1]: Starting UUID daemon activation socket.
Sep 13 23:12:15 NewOne systemd[1]: Listening on D-Bus System Message Bus Socket.
Sep 13 23:12:15 NewOne systemd[1]: Starting D-Bus System Message Bus Socket.
Sep 13 23:12:15 NewOne systemd[1]: Started Daily Cleanup of Temporary Directories.
Sep 13 23:12:15 NewOne systemd[1]: Starting Daily Cleanup of Temporary Directories.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Timers.
Sep 13 23:12:15 NewOne systemd[1]: Starting Timers.
Sep 13 23:12:15 NewOne systemd[1]: Started Manage Sound Card State (restore and store).
Sep 13 23:12:15 NewOne systemd[1]: Starting Restore Sound Card State...
Sep 13 23:12:15 NewOne systemd[1]: Started CUPS Scheduler.
Sep 13 23:12:15 NewOne systemd[1]: Starting CUPS Scheduler.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Paths.
Sep 13 23:12:15 NewOne systemd[1]: Starting Paths.
Sep 13 23:12:15 NewOne systemd[1]: Started Manage Sound Card State (restore and store).
Sep 13 23:12:15 NewOne systemd[1]: Listening on CUPS Scheduler.
Sep 13 23:12:15 NewOne systemd[1]: Starting CUPS Scheduler.
Sep 13 23:12:15 NewOne systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Sep 13 23:12:15 NewOne systemd[1]: Starting Avahi mDNS/DNS-SD Stack Activation Socket.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Sockets.
Sep 13 23:12:15 NewOne systemd[1]: Starting Sockets.
Sep 13 23:12:15 NewOne systemd[1]: Reached target Basic System.
Sep 13 23:12:15 NewOne systemd[1]: Starting Basic System.
Sep 13 23:12:15 NewOne systemd[1]: Starting LSB: Set the CPU Frequency Scaling governor to "ondemand"...
Sep 13 23:12:15 NewOne systemd[1]: Started crash report submission daemon.
Sep 13 23:12:15 NewOne systemd[1]: Starting crash report submission daemon...
Sep 13 23:12:15 NewOne systemd[1]: Starting LSB: Speech Dispatcher...
Sep 13 23:12:15 NewOne systemd[1]: Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down....
Sep 13 23:12:15 NewOne systemd[1]: Starting Permit User Sessions...
Sep 13 23:12:15 NewOne systemd[1]: Starting Thermal Daemon Service...
Sep 13 23:12:15 NewOne systemd[1]: Started CUPS Scheduler.
Sep 13 23:12:15 NewOne systemd[1]: Starting CUPS Scheduler...
Sep 13 23:12:15 NewOne speech-dispatcher[653]: * speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Sep 13 23:12:15 NewOne systemd[1]: Starting Login Service...
Sep 13 23:12:15 NewOne systemd[1]: Starting Network Manager...
Sep 13 23:12:15 NewOne systemd[1]: Started Cgroup management daemon.
Sep 13 23:12:15 NewOne systemd[1]: Starting Cgroup management daemon...
Sep 13 23:12:15 NewOne systemd[1]: Started Cgroup management proxy.
Sep 13 23:12:15 NewOne systemd[1]: Starting LSB: daemon to balance interrupts for SMP systems...
Sep 13 23:12:15 NewOne systemd[1]: Starting Modem Manager...
Sep 13 23:12:15 NewOne systemd[1]: Started Run anacron jobs.
Sep 13 23:12:15 NewOne systemd[1]: Starting Run anacron jobs...
Sep 13 23:12:15 NewOne systemd[1]: Starting D-Bus System Message Bus...
Sep 13 23:12:15 NewOne systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Sep 13 23:12:15 NewOne systemd[1]: Started getty on tty2-tty6 if dbus and logind are not available.
Sep 13 23:12:15 NewOne systemd[1]: Starting LSB: Record successful boot for GRUB...
Sep 13 23:12:15 NewOne anacron[675]: Anacron 2.3 started on 2015-09-13
Sep 13 23:12:15 NewOne systemd[1]: Started Regular background program processing daemon.
Sep 13 23:12:15 NewOne systemd[1]: Starting Regular background program processing daemon...
Sep 13 23:12:15 NewOne irqbalance[672]: * Starting SMP IRQ Balancer: irqbalance
Sep 13 23:12:15 NewOne systemd[1]: Starting Detect the available GPUs and deal with any system changes...
Sep 13 23:12:15 NewOne cron[684]: (CRON) INFO (pidfile fd = 3)
Sep 13 23:12:15 NewOne avahi-daemon[679]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Sep 13 23:12:15 NewOne avahi-daemon[679]: Successfully dropped root privileges.
Sep 13 23:12:15 NewOne avahi-daemon[679]: avahi-daemon 0.6.31 starting up.
Sep 13 23:12:15 NewOne systemd[1]: Starting System Logging Service...
Sep 13 23:12:15 NewOne systemd[1]: Starting LSB: automatic crash report generation...
Sep 13 23:12:15 NewOne systemd[1]: Starting Accounts Service...
Sep 13 23:12:15 NewOne kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 13 23:12:15 NewOne kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 13 23:12:15 NewOne kernel: [    0.000000] Initializing cgroup subsys cpuacct
Sep 13 23:12:15 NewOne kernel: [    0.000000] Linux version 3.19.0-28-generic (buildd@lgw01-03) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #30-Ubuntu SMP Mon Aug 31 15:52:51 UTC 2015 (Ubuntu 3.19.0-28.30-generic 3.19.8-ckt5)
Sep 13 23:12:15 NewOne kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-28-generic root=UUID=4c6b959e-d3ef-449b-8f28-4f96c761d9fc ro quiet splash vt.handoff=7
Sep 13 23:12:15 NewOne kernel: [    0.000000] KERNEL supported cpus:
Sep 13 23:12:15 NewOne kernel: [    0.000000]   Intel GenuineIntel
Sep 13 23:12:15 NewOne kernel: [    0.000000]   AMD AuthenticAMD
Sep 13 23:12:15 NewOne kernel: [    0.000000]   Centaur CentaurHauls
Sep 13 23:12:15 NewOne kernel: [    0.000000] tseg: 00cf000000
Sep 13 23:12:15 NewOne kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cbc29fff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000cbc2a000-0x00000000cc648fff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000cc649000-0x00000000cc919fff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000cc91a000-0x00000000cc9d2fff] ACPI NVS
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000cc9d3000-0x00000000cdec0fff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000cdec1000-0x00000000cdec1fff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000cdec2000-0x00000000ce0c7fff] ACPI NVS
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce0c8000-0x00000000ce21efff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce21f000-0x00000000ce83bfff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce83c000-0x00000000ce86ffff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000ce870000-0x00000000ceff0fff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000ceff1000-0x00000000ceffffff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec01fff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000003eeffffff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] NX (Execute Disable) protection: active
Sep 13 23:12:15 NewOne kernel: [    0.000000] SMBIOS 2.8 present.
Sep 13 23:12:15 NewOne kernel: [    0.000000] DMI: BIOSTAR Group Hi-Fi A70U3P/Hi-Fi A70U3P, BIOS 4.6.5 10/29/2014
Sep 13 23:12:15 NewOne kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: No AGP bridge found
Sep 13 23:12:15 NewOne kernel: [    0.000000] e820: last_pfn = 0x3ef000 max_arch_pfn = 0x400000000
Sep 13 23:12:15 NewOne kernel: [    0.000000] MTRR default type: uncachable
Sep 13 23:12:15 NewOne kernel: [    0.000000] MTRR fixed ranges enabled:
Sep 13 23:12:15 NewOne kernel: [    0.000000]   00000-9FFFF write-back
Sep 13 23:12:15 NewOne kernel: [    0.000000]   A0000-BFFFF write-through
Sep 13 23:12:15 NewOne kernel: [    0.000000]   C0000-CFFFF write-protect
Sep 13 23:12:15 NewOne kernel: [    0.000000]   D0000-E7FFF uncachable
Sep 13 23:12:15 NewOne kernel: [    0.000000]   E8000-FFFFF write-protect
Sep 13 23:12:15 NewOne kernel: [    0.000000] MTRR variable ranges enabled:
Sep 13 23:12:15 NewOne kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Sep 13 23:12:15 NewOne kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Sep 13 23:12:15 NewOne kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Sep 13 23:12:15 NewOne kernel: [    0.000000]   3 disabled
Sep 13 23:12:15 NewOne kernel: [    0.000000]   4 disabled
Sep 13 23:12:15 NewOne kernel: [    0.000000]   5 disabled
Sep 13 23:12:15 NewOne kernel: [    0.000000]   6 disabled
Sep 13 23:12:15 NewOne kernel: [    0.000000]   7 disabled
Sep 13 23:12:15 NewOne kernel: [    0.000000] TOM2: 000000042f000000 aka 17136M
Sep 13 23:12:15 NewOne kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
Sep 13 23:12:15 NewOne kernel: [    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000] e820: last_pfn = 0xcf000 max_arch_pfn = 0x400000000
Sep 13 23:12:15 NewOne kernel: [    0.000000] found SMP MP-table at [mem 0x000fd7c0-0x000fd7cf] mapped at [ffff8800000fd7c0]
Sep 13 23:12:15 NewOne kernel: [    0.000000] Scanning 1 areas for low memory corruption
Sep 13 23:12:15 NewOne kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Sep 13 23:12:15 NewOne kernel: [    0.000000] Using GB pages for direct mapping
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
Sep 13 23:12:15 NewOne kernel: [    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
Sep 13 23:12:15 NewOne kernel: [    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0x3eee00000-0x3eeffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x3eee00000-0x3eeffffff] page 2M
Sep 13 23:12:15 NewOne kernel: [    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0x3e0000000-0x3eedfffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x3e0000000-0x3eedfffff] page 2M
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0x3c0000000-0x3dfffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x3c0000000-0x3dfffffff] page 2M
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xcbc29fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0xc0000000-0xcbbfffff] page 2M
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0xcbc00000-0xcbc29fff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0xcc649000-0xcc919fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0xcc649000-0xcc919fff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE
Sep 13 23:12:15 NewOne kernel: [    0.000000] BRK [0x01fea000, 0x01feafff] PGTABLE
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0xcdec1000-0xcdec1fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0xcdec1000-0xcdec1fff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0xce0c8000-0xce21efff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0xce0c8000-0xce21efff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0xce83c000-0xce86ffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0xce83c000-0xce86ffff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0xceff1000-0xceffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0xceff1000-0xceffffff] page 4k
Sep 13 23:12:15 NewOne kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x3bfffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [mem 0x100000000-0x3bfffffff] page 1G
Sep 13 23:12:15 NewOne kernel: [    0.000000] RAMDISK: [mem 0x3583c000-0x36c15fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: Early table checksum verification disabled
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: RSDP 0x00000000000F04A0 000024 (v02 ALASKA)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: XSDT 0x00000000CC99E080 00007C (v01 ALASKA A M I    01072009 AMI  00010013)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: FACP 0x00000000CC9A3060 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20141107/tbfadt-654)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: DSDT 0x00000000CC99E190 004ECC (v02 ALASKA A M I    00000000 INTL 20051117)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: FACS 0x00000000CC9C9D80 000040
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: APIC 0x00000000CC9A3170 00007E (v03 ALASKA A M I    01072009 AMI  00010013)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: FPDT 0x00000000CC9A31F0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: FIDT 0x00000000CC9A3238 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: MCFG 0x00000000CC9A32D8 00003C (v01 ALASKA A M I    01072009 MSFT 00010013)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: HPET 0x00000000CC9A3318 000038 (v01 ALASKA A M I    01072009 AMI  00000005)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: UEFI 0x00000000CC9A3350 000042 (v01 ALASKA A M I    01072009      00000000)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: SSDT 0x00000000CC9A3398 000EE4 (v01 AMD    BANTRY   00000001 AMD  00000001)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: SSDT 0x00000000CC9A4280 00033B (v02 AMD    BANTRY   00000002 MSFT 04000000)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: CRAT 0x00000000CC9A45C0 0005A0 (v01 AMD    BANTRY   00000001 AMD  00000001)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: SSDT 0x00000000CC9A4B60 00122C (v01 AMD    CPMCMN   00000001 INTL 20051117)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 13 23:12:15 NewOne kernel: [    0.000000] No NUMA configuration found
Sep 13 23:12:15 NewOne kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x00000003eeffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x3eeff4000-0x3eeff8fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]  [ffffea0000000000-ffffea000fbfffff] PMD -> [ffff8803df600000-ffff8803ee5fffff] on node 0
Sep 13 23:12:15 NewOne kernel: [    0.000000] Zone ranges:
Sep 13 23:12:15 NewOne kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   Normal   [mem 0x100000000-0x3eeffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] Movable zone start for each node
Sep 13 23:12:15 NewOne kernel: [    0.000000] Early memory node ranges
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0x00100000-0xcbc29fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0xcc649000-0xcc919fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0xcdec1000-0xcdec1fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0xce0c8000-0xce21efff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0xce83c000-0xce86ffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0xceff1000-0xceffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000]   node   0: [mem 0x100000000-0x3eeffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] Initmem setup node 0 [mem 0x00001000-0x3eeffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] On node 0 totalpages: 3911732
Sep 13 23:12:15 NewOne kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Sep 13 23:12:15 NewOne kernel: [    0.000000]   DMA zone: 21 pages reserved
Sep 13 23:12:15 NewOne kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Sep 13 23:12:15 NewOne kernel: [    0.000000]   DMA32 zone: 12995 pages used for memmap
Sep 13 23:12:15 NewOne kernel: [    0.000000]   DMA32 zone: 831638 pages, LIFO batch:31
Sep 13 23:12:15 NewOne kernel: [    0.000000]   Normal zone: 48064 pages used for memmap
Sep 13 23:12:15 NewOne kernel: [    0.000000]   Normal zone: 3076096 pages, LIFO batch:31
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Sep 13 23:12:15 NewOne kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec01000] gsi_base[24])
Sep 13 23:12:15 NewOne kernel: [    0.000000] IOAPIC[1]: apic_id 1, version 33, address 0xfec01000, GSI 24-55
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep 13 23:12:15 NewOne kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 13 23:12:15 NewOne kernel: [    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
Sep 13 23:12:15 NewOne kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcbc2a000-0xcc648fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcc91a000-0xcc9d2fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcc9d3000-0xcdec0fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcdec2000-0xce0c7fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xce21f000-0xce83bfff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xce870000-0xceff0fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcf000000-0xfebfffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec01fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec02000-0xfec0ffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfecfffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed7ffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] e820: [mem 0xcf000000-0xfebfffff] available for PCI devices
Sep 13 23:12:15 NewOne kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep 13 23:12:15 NewOne kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Sep 13 23:12:15 NewOne kernel: [    0.000000] PERCPU: Embedded 31 pages/cpu @ffff8803eec00000 s87104 r8192 d31680 u524288
Sep 13 23:12:15 NewOne kernel: [    0.000000] pcpu-alloc: s87104 r8192 d31680 u524288 alloc=1*2097152
Sep 13 23:12:15 NewOne kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Sep 13 23:12:15 NewOne kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 3850588
Sep 13 23:12:15 NewOne kernel: [    0.000000] Policy zone: Normal
Sep 13 23:12:15 NewOne kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-28-generic root=UUID=4c6b959e-d3ef-449b-8f28-4f96c761d9fc ro quiet splash vt.handoff=7
Sep 13 23:12:15 NewOne kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: Checking aperture...
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: No AGP bridge found
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: Node 0: aperture [bus addr 0x00000000-0x01ffffff] (32MB)
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: Your BIOS doesn't leave a aperture memory hole
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: This costs you 64MB of RAM
Sep 13 23:12:15 NewOne kernel: [    0.000000] AGP: Mapping aperture over RAM [mem 0xc0000000-0xc3ffffff] (65536KB)
Sep 13 23:12:15 NewOne kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xc3ffffff]
Sep 13 23:12:15 NewOne kernel: [    0.000000] Memory: 15232072K/15646928K available (8002K kernel code, 1234K rwdata, 3764K rodata, 1408K init, 1300K bss, 414856K reserved, 0K cma-reserved)
Sep 13 23:12:15 NewOne kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Sep 13 23:12:15 NewOne kernel: [    0.000000] Hierarchical RCU implementation.
Sep 13 23:12:15 NewOne kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Sep 13 23:12:15 NewOne kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Sep 13 23:12:15 NewOne kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Sep 13 23:12:15 NewOne kernel: [    0.000000] NR_IRQS:16640 nr_irqs:1000 16
Sep 13 23:12:15 NewOne kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
Sep 13 23:12:15 NewOne kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
Sep 13 23:12:15 NewOne kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Sep 13 23:12:15 NewOne kernel: [    0.000000] vt handoff: transparent VT on vt#7
Sep 13 23:12:15 NewOne kernel: [    0.000000] Console: colour dummy device 80x25
Sep 13 23:12:15 NewOne kernel: [    0.000000] console [tty0] enabled
Sep 13 23:12:15 NewOne kernel: [    0.000000] hpet clockevent registered
Sep 13 23:12:15 NewOne kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Sep 13 23:12:15 NewOne kernel: [    0.000000] tsc: Detected 3892.418 MHz processor
Sep 13 23:12:15 NewOne kernel: [    0.000044] Calibrating delay loop (skipped), value calculated using timer frequency.. 7784.83 BogoMIPS (lpj=15569672)
Sep 13 23:12:15 NewOne kernel: [    0.000049] pid_max: default: 32768 minimum: 301
Sep 13 23:12:15 NewOne kernel: [    0.000059] ACPI: Core revision 20141107
Sep 13 23:12:15 NewOne kernel: [    0.008095] ACPI: All ACPI Tables successfully acquired
Sep 13 23:12:15 NewOne kernel: [    0.008132] Security Framework initialized
Sep 13 23:12:15 NewOne kernel: [    0.008157] AppArmor: AppArmor initialized
Sep 13 23:12:15 NewOne kernel: [    0.008160] Yama: becoming mindful.
Sep 13 23:12:15 NewOne kernel: [    0.010208] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.015920] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.018349] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.018386] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.018819] Initializing cgroup subsys memory
Sep 13 23:12:15 NewOne kernel: [    0.018829] Initializing cgroup subsys devices
Sep 13 23:12:15 NewOne kernel: [    0.018833] Initializing cgroup subsys freezer
Sep 13 23:12:15 NewOne kernel: [    0.018838] Initializing cgroup subsys net_cls
Sep 13 23:12:15 NewOne kernel: [    0.018842] Initializing cgroup subsys blkio
Sep 13 23:12:15 NewOne kernel: [    0.018845] Initializing cgroup subsys perf_event
Sep 13 23:12:15 NewOne kernel: [    0.018848] Initializing cgroup subsys net_prio
Sep 13 23:12:15 NewOne kernel: [    0.018852] Initializing cgroup subsys hugetlb
Sep 13 23:12:15 NewOne kernel: [    0.018884] CPU: Physical Processor ID: 0
Sep 13 23:12:15 NewOne kernel: [    0.018886] CPU: Processor Core ID: 0
Sep 13 23:12:15 NewOne kernel: [    0.018889] mce: CPU supports 7 MCE banks
Sep 13 23:12:15 NewOne kernel: [    0.018899] LVT offset 1 assigned for vector 0xf9
Sep 13 23:12:15 NewOne kernel: [    0.018909] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
Sep 13 23:12:15 NewOne kernel: [    0.018909] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512, 1GB 0
Sep 13 23:12:15 NewOne kernel: [    0.019048] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
Sep 13 23:12:15 NewOne kernel: [    0.042511] ftrace: allocating 30112 entries in 118 pages
Sep 13 23:12:15 NewOne kernel: [    0.052512] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 13 23:12:15 NewOne kernel: [    0.092188] smpboot: CPU0: AMD A10-7870K Radeon R7, 12 Compute Cores 4C+8G (fam: 15, model: 38, stepping: 01)
Sep 13 23:12:15 NewOne kernel: [    0.197949] Performance Events: Fam15h core perfctr, AMD PMU driver.
Sep 13 23:12:15 NewOne kernel: [    0.197958] ... version:                0
Sep 13 23:12:15 NewOne kernel: [    0.197961] ... bit width:              48
Sep 13 23:12:15 NewOne kernel: [    0.197963] ... generic registers:      6
Sep 13 23:12:15 NewOne kernel: [    0.197965] ... value mask:             0000ffffffffffff
Sep 13 23:12:15 NewOne kernel: [    0.197967] ... max period:             00007fffffffffff
Sep 13 23:12:15 NewOne kernel: [    0.197969] ... fixed-purpose events:   0
Sep 13 23:12:15 NewOne kernel: [    0.197971] ... event mask:             000000000000003f
Sep 13 23:12:15 NewOne kernel: [    0.199360] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Sep 13 23:12:15 NewOne kernel: [    0.199541] x86: Booting SMP configuration:
Sep 13 23:12:15 NewOne kernel: [    0.199544] .... node  #0, CPUs:      #1 #2 #3
Sep 13 23:12:15 NewOne kernel: [    0.238985] x86: Booted up 1 node, 4 CPUs
Sep 13 23:12:15 NewOne kernel: [    0.238988] smpboot: Total of 4 processors activated (31139.34 BogoMIPS)
Sep 13 23:12:15 NewOne kernel: [    0.239750] devtmpfs: initialized
Sep 13 23:12:15 NewOne kernel: [    0.243475] evm: security.selinux
Sep 13 23:12:15 NewOne kernel: [    0.243476] evm: security.SMACK64
Sep 13 23:12:15 NewOne kernel: [    0.243478] evm: security.SMACK64EXEC
Sep 13 23:12:15 NewOne kernel: [    0.243479] evm: security.SMACK64TRANSMUTE
Sep 13 23:12:15 NewOne kernel: [    0.243480] evm: security.SMACK64MMAP
Sep 13 23:12:15 NewOne kernel: [    0.243481] evm: security.ima
Sep 13 23:12:15 NewOne kernel: [    0.243482] evm: security.capability
Sep 13 23:12:15 NewOne kernel: [    0.243552] PM: Registering ACPI NVS region [mem 0xcc91a000-0xcc9d2fff] (757760 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.243568] PM: Registering ACPI NVS region [mem 0xcdec2000-0xce0c7fff] (2121728 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.243778] pinctrl core: initialized pinctrl subsystem
Sep 13 23:12:15 NewOne kernel: [    0.243899] RTC time:  6:12:02, date: 09/14/15
Sep 13 23:12:15 NewOne kernel: [    0.244013] NET: Registered protocol family 16
Sep 13 23:12:15 NewOne kernel: [    0.246020] cpuidle: using governor ladder
Sep 13 23:12:15 NewOne kernel: [    0.250021] cpuidle: using governor menu
Sep 13 23:12:15 NewOne kernel: [    0.250145] ACPI: bus type PCI registered
Sep 13 23:12:15 NewOne kernel: [    0.250148] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Sep 13 23:12:15 NewOne kernel: [    0.250249] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Sep 13 23:12:15 NewOne kernel: [    0.250252] PCI: not using MMCONFIG
Sep 13 23:12:15 NewOne kernel: [    0.250253] PCI: Using configuration type 1 for base access
Sep 13 23:12:15 NewOne kernel: [    0.250254] PCI: Using configuration type 1 for extended access
Sep 13 23:12:15 NewOne kernel: [    0.250675] mtrr: your CPUs had inconsistent variable MTRR settings
Sep 13 23:12:15 NewOne kernel: [    0.250676] mtrr: probably your BIOS does not setup all CPUs.
Sep 13 23:12:15 NewOne kernel: [    0.250677] mtrr: corrected configuration.
Sep 13 23:12:15 NewOne kernel: [    0.254597] ACPI: Added _OSI(Module Device)
Sep 13 23:12:15 NewOne kernel: [    0.254600] ACPI: Added _OSI(Processor Device)
Sep 13 23:12:15 NewOne kernel: [    0.254602] ACPI: Added _OSI(3.0 _SCP Extensions)
Sep 13 23:12:15 NewOne kernel: [    0.254603] ACPI: Added _OSI(Processor Aggregator Device)
Sep 13 23:12:15 NewOne kernel: [    0.256963] ACPI: Executed 1 blocks of module-level executable AML code
Sep 13 23:12:15 NewOne kernel: [    0.261355] ACPI: Interpreter enabled
Sep 13 23:12:15 NewOne kernel: [    0.261362] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
Sep 13 23:12:15 NewOne kernel: [    0.261368] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
Sep 13 23:12:15 NewOne kernel: [    0.261390] ACPI: (supports S0 S3 S4 S5)
Sep 13 23:12:15 NewOne kernel: [    0.261392] ACPI: Using IOAPIC for interrupt routing
Sep 13 23:12:15 NewOne kernel: [    0.261416] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Sep 13 23:12:15 NewOne kernel: [    0.261464] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in ACPI motherboard resources
Sep 13 23:12:15 NewOne kernel: [    0.261586] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Sep 13 23:12:15 NewOne kernel: [    0.262257] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Sep 13 23:12:15 NewOne kernel: [    0.266109] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Sep 13 23:12:15 NewOne kernel: [    0.268298] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Sep 13 23:12:15 NewOne kernel: [    0.268306] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Sep 13 23:12:15 NewOne kernel: [    0.268313] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
Sep 13 23:12:15 NewOne kernel: [    0.268698] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
Sep 13 23:12:15 NewOne kernel: [    0.268972] PCI host bridge to bus 0000:00
Sep 13 23:12:15 NewOne kernel: [    0.268976] pci_bus 0000:00: root bus resource [bus 00-ff]
Sep 13 23:12:15 NewOne kernel: [    0.268979] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
Sep 13 23:12:15 NewOne kernel: [    0.268981] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
Sep 13 23:12:15 NewOne kernel: [    0.268984] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
Sep 13 23:12:15 NewOne kernel: [    0.268986] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Sep 13 23:12:15 NewOne kernel: [    0.268988] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Sep 13 23:12:15 NewOne kernel: [    0.268990] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
Sep 13 23:12:15 NewOne kernel: [    0.268993] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xffffffff]
Sep 13 23:12:15 NewOne kernel: [    0.269001] pci 0000:00:00.0: [1022:1422] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.269143] pci 0000:00:01.0: [1002:130f] type 00 class 0x030000
Sep 13 23:12:15 NewOne kernel: [    0.269155] pci 0000:00:01.0: reg 0x10: [mem 0xd0000000-0xdfffffff 64bit pref]
Sep 13 23:12:15 NewOne kernel: [    0.269164] pci 0000:00:01.0: reg 0x18: [mem 0xe0000000-0xe07fffff 64bit pref]
Sep 13 23:12:15 NewOne kernel: [    0.269170] pci 0000:00:01.0: reg 0x20: [io  0xf000-0xf0ff]
Sep 13 23:12:15 NewOne kernel: [    0.269176] pci 0000:00:01.0: reg 0x24: [mem 0xfeb00000-0xfeb3ffff]
Sep 13 23:12:15 NewOne kernel: [    0.269182] pci 0000:00:01.0: reg 0x30: [mem 0xfeb40000-0xfeb5ffff pref]
Sep 13 23:12:15 NewOne kernel: [    0.269218] pci 0000:00:01.0: supports D1 D2
Sep 13 23:12:15 NewOne kernel: [    0.269220] pci 0000:00:01.0: PME# supported from D1 D2 D3hot
Sep 13 23:12:15 NewOne kernel: [    0.269341] pci 0000:00:01.1: [1002:1308] type 00 class 0x040300
Sep 13 23:12:15 NewOne kernel: [    0.269352] pci 0000:00:01.1: reg 0x10: [mem 0xfeb64000-0xfeb67fff 64bit]
Sep 13 23:12:15 NewOne kernel: [    0.269400] pci 0000:00:01.1: supports D1 D2
Sep 13 23:12:15 NewOne kernel: [    0.269503] pci 0000:00:02.0: [1022:1424] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.269628] pci 0000:00:03.0: [1022:1424] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.269752] pci 0000:00:04.0: [1022:1424] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.269912] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
Sep 13 23:12:15 NewOne kernel: [    0.269935] pci 0000:00:10.0: reg 0x10: [mem 0xfeb6a000-0xfeb6bfff 64bit]
Sep 13 23:12:15 NewOne kernel: [    0.270038] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
Sep 13 23:12:15 NewOne kernel: [    0.270114] pci 0000:00:10.0: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.270183] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
Sep 13 23:12:15 NewOne kernel: [    0.270205] pci 0000:00:10.1: reg 0x10: [mem 0xfeb68000-0xfeb69fff 64bit]
Sep 13 23:12:15 NewOne kernel: [    0.270307] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
Sep 13 23:12:15 NewOne kernel: [    0.270383] pci 0000:00:10.1: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.270446] pci 0000:00:11.0: [1022:7800] type 00 class 0x01018f
Sep 13 23:12:15 NewOne kernel: [    0.270462] pci 0000:00:11.0: reg 0x10: [io  0xf140-0xf147]
Sep 13 23:12:15 NewOne kernel: [    0.270471] pci 0000:00:11.0: reg 0x14: [io  0xf130-0xf133]
Sep 13 23:12:15 NewOne kernel: [    0.270480] pci 0000:00:11.0: reg 0x18: [io  0xf120-0xf127]
Sep 13 23:12:15 NewOne kernel: [    0.270489] pci 0000:00:11.0: reg 0x1c: [io  0xf110-0xf113]
Sep 13 23:12:15 NewOne kernel: [    0.270498] pci 0000:00:11.0: reg 0x20: [io  0xf100-0xf10f]
Sep 13 23:12:15 NewOne kernel: [    0.270507] pci 0000:00:11.0: reg 0x24: [mem 0xfeb71000-0xfeb717ff]
Sep 13 23:12:15 NewOne kernel: [    0.270528] pci 0000:00:11.0: set SATA to AHCI mode
Sep 13 23:12:15 NewOne kernel: [    0.270652] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
Sep 13 23:12:15 NewOne kernel: [    0.270665] pci 0000:00:12.0: reg 0x10: [mem 0xfeb70000-0xfeb70fff]
Sep 13 23:12:15 NewOne kernel: [    0.270777] pci 0000:00:12.0: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.270837] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
Sep 13 23:12:15 NewOne kernel: [    0.270855] pci 0000:00:12.2: reg 0x10: [mem 0xfeb6f000-0xfeb6f0ff]
Sep 13 23:12:15 NewOne kernel: [    0.270931] pci 0000:00:12.2: supports D1 D2
Sep 13 23:12:15 NewOne kernel: [    0.270933] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Sep 13 23:12:15 NewOne kernel: [    0.271003] pci 0000:00:12.2: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.271069] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
Sep 13 23:12:15 NewOne kernel: [    0.271082] pci 0000:00:13.0: reg 0x10: [mem 0xfeb6e000-0xfeb6efff]
Sep 13 23:12:15 NewOne kernel: [    0.271195] pci 0000:00:13.0: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.271255] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
Sep 13 23:12:15 NewOne kernel: [    0.271273] pci 0000:00:13.2: reg 0x10: [mem 0xfeb6d000-0xfeb6d0ff]
Sep 13 23:12:15 NewOne kernel: [    0.271348] pci 0000:00:13.2: supports D1 D2
Sep 13 23:12:15 NewOne kernel: [    0.271351] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Sep 13 23:12:15 NewOne kernel: [    0.271417] pci 0000:00:13.2: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.271478] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
Sep 13 23:12:15 NewOne kernel: [    0.271635] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
Sep 13 23:12:15 NewOne kernel: [    0.271655] pci 0000:00:14.2: reg 0x10: [mem 0xfeb60000-0xfeb63fff 64bit]
Sep 13 23:12:15 NewOne kernel: [    0.271717] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Sep 13 23:12:15 NewOne kernel: [    0.271782] pci 0000:00:14.2: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.271836] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
Sep 13 23:12:15 NewOne kernel: [    0.271997] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
Sep 13 23:12:15 NewOne kernel: [    0.272089] pci 0000:00:14.4: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.272142] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
Sep 13 23:12:15 NewOne kernel: [    0.272155] pci 0000:00:14.5: reg 0x10: [mem 0xfeb6c000-0xfeb6cfff]
Sep 13 23:12:15 NewOne kernel: [    0.272265] pci 0000:00:14.5: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.272327] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
Sep 13 23:12:15 NewOne kernel: [    0.272400] pci 0000:00:15.0: supports D1 D2
Sep 13 23:12:15 NewOne kernel: [    0.272402] pci 0000:00:15.0: PME# supported from D0 D3hot D3cold
Sep 13 23:12:15 NewOne kernel: [    0.272474] pci 0000:00:15.0: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.272531] pci 0000:00:15.1: [1022:43a1] type 01 class 0x060400
Sep 13 23:12:15 NewOne kernel: [    0.272604] pci 0000:00:15.1: supports D1 D2
Sep 13 23:12:15 NewOne kernel: [    0.272607] pci 0000:00:15.1: PME# supported from D0 D3hot D3cold
Sep 13 23:12:15 NewOne kernel: [    0.272678] pci 0000:00:15.1: System wakeup disabled by ACPI
Sep 13 23:12:15 NewOne kernel: [    0.272740] pci 0000:00:18.0: [1022:141a] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.272853] pci 0000:00:18.1: [1022:141b] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.272962] pci 0000:00:18.2: [1022:141c] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.273075] pci 0000:00:18.3: [1022:141d] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.273190] pci 0000:00:18.4: [1022:141e] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.273299] pci 0000:00:18.5: [1022:141f] type 00 class 0x060000
Sep 13 23:12:15 NewOne kernel: [    0.273494] pci 0000:00:14.4: PCI bridge to [bus 01] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273503] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273506] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273508] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273510] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273513] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273515] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273518] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xffffffff] (subtractive decode)
Sep 13 23:12:15 NewOne kernel: [    0.273587] pci 0000:00:15.0: PCI bridge to [bus 02]
Sep 13 23:12:15 NewOne kernel: [    0.273681] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Sep 13 23:12:15 NewOne kernel: [    0.273701] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
Sep 13 23:12:15 NewOne kernel: [    0.273731] pci 0000:03:00.0: reg 0x18: [mem 0xfea00000-0xfea00fff 64bit]
Sep 13 23:12:15 NewOne kernel: [    0.273750] pci 0000:03:00.0: reg 0x20: [mem 0xe0800000-0xe0803fff 64bit pref]
Sep 13 23:12:15 NewOne kernel: [    0.273852] pci 0000:03:00.0: supports D1 D2
Sep 13 23:12:15 NewOne kernel: [    0.273854] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 13 23:12:15 NewOne kernel: [    0.282017] pci 0000:00:15.1: PCI bridge to [bus 03]
Sep 13 23:12:15 NewOne kernel: [    0.282031] pci 0000:00:15.1:   bridge window [io  0xe000-0xefff]
Sep 13 23:12:15 NewOne kernel: [    0.282037] pci 0000:00:15.1:   bridge window [mem 0xfea00000-0xfeafffff]
Sep 13 23:12:15 NewOne kernel: [    0.282045] pci 0000:00:15.1:   bridge window [mem 0xe0800000-0xe08fffff 64bit pref]
Sep 13 23:12:15 NewOne kernel: [    0.282620] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *5 7 10 11 14 15)
Sep 13 23:12:15 NewOne kernel: [    0.282702] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 *10 11 14 15)
Sep 13 23:12:15 NewOne kernel: [    0.282783] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 *11 14 15)
Sep 13 23:12:15 NewOne kernel: [    0.282863] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 7 9 11 12 14 15)
Sep 13 23:12:15 NewOne kernel: [    0.282929] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
Sep 13 23:12:15 NewOne kernel: [    0.282982] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
Sep 13 23:12:15 NewOne kernel: [    0.283034] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
Sep 13 23:12:15 NewOne kernel: [    0.283092] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
Sep 13 23:12:15 NewOne kernel: [    0.283278] ACPI: Enabled 1 GPEs in block 00 to 1F
Sep 13 23:12:15 NewOne kernel: [    0.283484] vgaarb: setting as boot device: PCI:0000:00:01.0
Sep 13 23:12:15 NewOne kernel: [    0.283487] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
Sep 13 23:12:15 NewOne kernel: [    0.283495] vgaarb: loaded
Sep 13 23:12:15 NewOne kernel: [    0.283497] vgaarb: bridge control possible 0000:00:01.0
Sep 13 23:12:15 NewOne kernel: [    0.283781] SCSI subsystem initialized
Sep 13 23:12:15 NewOne kernel: [    0.283858] libata version 3.00 loaded.
Sep 13 23:12:15 NewOne kernel: [    0.283892] ACPI: bus type USB registered
Sep 13 23:12:15 NewOne kernel: [    0.283917] usbcore: registered new interface driver usbfs
Sep 13 23:12:15 NewOne kernel: [    0.283929] usbcore: registered new interface driver hub
Sep 13 23:12:15 NewOne kernel: [    0.283952] usbcore: registered new device driver usb
Sep 13 23:12:15 NewOne kernel: [    0.284125] PCI: Using ACPI for IRQ routing
Sep 13 23:12:15 NewOne kernel: [    0.285822] PCI: pci_cache_line_size set to 64 bytes
Sep 13 23:12:15 NewOne kernel: [    0.285899] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Sep 13 23:12:15 NewOne kernel: [    0.285902] e820: reserve RAM buffer [mem 0xcbc2a000-0xcbffffff]
Sep 13 23:12:15 NewOne kernel: [    0.285904] e820: reserve RAM buffer [mem 0xcc91a000-0xcfffffff]
Sep 13 23:12:15 NewOne kernel: [    0.285906] e820: reserve RAM buffer [mem 0xcdec2000-0xcfffffff]
Sep 13 23:12:15 NewOne kernel: [    0.285908] e820: reserve RAM buffer [mem 0xce21f000-0xcfffffff]
Sep 13 23:12:15 NewOne kernel: [    0.285910] e820: reserve RAM buffer [mem 0xce870000-0xcfffffff]
Sep 13 23:12:15 NewOne kernel: [    0.285912] e820: reserve RAM buffer [mem 0xcf000000-0xcfffffff]
Sep 13 23:12:15 NewOne kernel: [    0.285914] e820: reserve RAM buffer [mem 0x3ef000000-0x3efffffff]
Sep 13 23:12:15 NewOne kernel: [    0.286082] NetLabel: Initializing
Sep 13 23:12:15 NewOne kernel: [    0.286084] NetLabel:  domain hash size = 128
Sep 13 23:12:15 NewOne kernel: [    0.286086] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 13 23:12:15 NewOne kernel: [    0.286106] NetLabel:  unlabeled traffic allowed by default
Sep 13 23:12:15 NewOne kernel: [    0.286237] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 13 23:12:15 NewOne kernel: [    0.286242] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Sep 13 23:12:15 NewOne kernel: [    0.288358] Switched to clocksource hpet
Sep 13 23:12:15 NewOne kernel: [    0.298872] AppArmor: AppArmor Filesystem Enabled
Sep 13 23:12:15 NewOne kernel: [    0.298965] pnp: PnP ACPI init
Sep 13 23:12:15 NewOne kernel: [    0.299136] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.299141] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Sep 13 23:12:15 NewOne kernel: [    0.299265] system 00:01: [mem 0x90000000-0xcfffffff] could not be reserved
Sep 13 23:12:15 NewOne kernel: [    0.299268] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 13 23:12:15 NewOne kernel: [    0.299377] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 13 23:12:15 NewOne kernel: [    0.299637] system 00:03: [io  0x0a00-0x0a1f] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.299640] system 00:03: [io  0x0a20-0x0a2f] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.299643] system 00:03: [io  0x0a30-0x0a3f] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.299646] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 13 23:12:15 NewOne kernel: [    0.299722] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Sep 13 23:12:15 NewOne kernel: [    0.299897] system 00:05: [io  0x04d0-0x04d1] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.299901] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 13 23:12:15 NewOne kernel: [    0.299962] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 13 23:12:15 NewOne kernel: [    0.300180] pnp 00:07: [dma 0 disabled]
Sep 13 23:12:15 NewOne kernel: [    0.300239] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
Sep 13 23:12:15 NewOne kernel: [    0.300686] system 00:08: [io  0x04d0-0x04d1] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300689] system 00:08: [io  0x040b] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300692] system 00:08: [io  0x04d6] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300695] system 00:08: [io  0x0c00-0x0c01] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300698] system 00:08: [io  0x0c14] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300700] system 00:08: [io  0x0c50-0x0c51] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300703] system 00:08: [io  0x0c52] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300705] system 00:08: [io  0x0c6c] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300707] system 00:08: [io  0x0c6f] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300710] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300712] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300715] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300717] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300720] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300722] system 00:08: [io  0x0800-0x089f] could not be reserved
Sep 13 23:12:15 NewOne kernel: [    0.300725] system 00:08: [io  0x0b20-0x0b3f] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300727] system 00:08: [io  0x0900-0x090f] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300730] system 00:08: [io  0x0910-0x091f] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300733] system 00:08: [io  0xfe00-0xfefe] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300736] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
Sep 13 23:12:15 NewOne kernel: [    0.300739] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300743] system 00:08: [mem 0xfed80000-0xfed8ffff] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300745] system 00:08: [mem 0xfed61000-0xfed70fff] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300748] system 00:08: [mem 0xfec10000-0xfec10fff] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300751] system 00:08: [mem 0xff000000-0xffffffff] has been reserved
Sep 13 23:12:15 NewOne kernel: [    0.300754] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep 13 23:12:15 NewOne kernel: [    0.301023] pnp: PnP ACPI: found 9 devices
Sep 13 23:12:15 NewOne kernel: [    0.309518] pci 0000:00:14.4: PCI bridge to [bus 01]
Sep 13 23:12:15 NewOne kernel: [    0.309531] pci 0000:00:15.0: PCI bridge to [bus 02]
Sep 13 23:12:15 NewOne kernel: [    0.309541] pci 0000:00:15.1: PCI bridge to [bus 03]
Sep 13 23:12:15 NewOne kernel: [    0.309545] pci 0000:00:15.1:   bridge window [io  0xe000-0xefff]
Sep 13 23:12:15 NewOne kernel: [    0.309550] pci 0000:00:15.1:   bridge window [mem 0xfea00000-0xfeafffff]
Sep 13 23:12:15 NewOne kernel: [    0.309554] pci 0000:00:15.1:   bridge window [mem 0xe0800000-0xe08fffff 64bit pref]
Sep 13 23:12:15 NewOne kernel: [    0.309560] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
Sep 13 23:12:15 NewOne kernel: [    0.309563] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
Sep 13 23:12:15 NewOne kernel: [    0.309565] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
Sep 13 23:12:15 NewOne kernel: [    0.309568] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
Sep 13 23:12:15 NewOne kernel: [    0.309570] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
Sep 13 23:12:15 NewOne kernel: [    0.309572] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
Sep 13 23:12:15 NewOne kernel: [    0.309575] pci_bus 0000:00: resource 10 [mem 0xd0000000-0xffffffff]
Sep 13 23:12:15 NewOne kernel: [    0.309578] pci_bus 0000:01: resource 4 [io  0x0000-0x03af]
Sep 13 23:12:15 NewOne kernel: [    0.309580] pci_bus 0000:01: resource 5 [io  0x03e0-0x0cf7]
Sep 13 23:12:15 NewOne kernel: [    0.309582] pci_bus 0000:01: resource 6 [io  0x03b0-0x03df]
Sep 13 23:12:15 NewOne kernel: [    0.309584] pci_bus 0000:01: resource 7 [io  0x0d00-0xffff]
Sep 13 23:12:15 NewOne kernel: [    0.309587] pci_bus 0000:01: resource 8 [mem 0x000a0000-0x000bffff]
Sep 13 23:12:15 NewOne kernel: [    0.309589] pci_bus 0000:01: resource 9 [mem 0x000c0000-0x000dffff]
Sep 13 23:12:15 NewOne kernel: [    0.309591] pci_bus 0000:01: resource 10 [mem 0xd0000000-0xffffffff]
Sep 13 23:12:15 NewOne kernel: [    0.309594] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Sep 13 23:12:15 NewOne kernel: [    0.309596] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
Sep 13 23:12:15 NewOne kernel: [    0.309599] pci_bus 0000:03: resource 2 [mem 0xe0800000-0xe08fffff 64bit pref]
Sep 13 23:12:15 NewOne kernel: [    0.309633] NET: Registered protocol family 2
Sep 13 23:12:15 NewOne kernel: [    0.309959] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.310375] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.310661] TCP: Hash tables configured (established 131072 bind 65536)
Sep 13 23:12:15 NewOne kernel: [    0.310701] TCP: reno registered
Sep 13 23:12:15 NewOne kernel: [    0.310742] UDP hash table entries: 8192 (order: 6, 262144 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.310852] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
Sep 13 23:12:15 NewOne kernel: [    0.311006] NET: Registered protocol family 1
Sep 13 23:12:15 NewOne kernel: [    0.311037] pci 0000:00:01.0: Video device with shadowed ROM
Sep 13 23:12:15 NewOne kernel: [    0.640583] PCI: CLS 64 bytes, default 64
Sep 13 23:12:15 NewOne kernel: [    0.640665] Trying to unpack rootfs image as initramfs...
Sep 13 23:12:15 NewOne kernel: [    1.160790] Freeing initrd memory: 20328K (ffff88003583c000 - ffff880036c16000)
Sep 13 23:12:15 NewOne kernel: [    1.160827] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Sep 13 23:12:15 NewOne kernel: [    1.160832] software IO TLB [mem 0xc7c2a000-0xcbc2a000] (64MB) mapped at [ffff8800c7c2a000-ffff8800cbc29fff]
Sep 13 23:12:15 NewOne kernel: [    1.161210] perf: AMD NB counters detected
Sep 13 23:12:15 NewOne kernel: [    1.161320] microcode: CPU0: patch_level=0x00000000
Sep 13 23:12:15 NewOne kernel: [    1.161334] microcode: CPU1: patch_level=0x00000000
Sep 13 23:12:15 NewOne kernel: [    1.161347] microcode: CPU2: patch_level=0x00000000
Sep 13 23:12:15 NewOne kernel: [    1.161355] microcode: CPU3: patch_level=0x00000000
Sep 13 23:12:15 NewOne kernel: [    1.161448] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Sep 13 23:12:15 NewOne kernel: [    1.161455] LVT offset 0 assigned for vector 0x400
Sep 13 23:12:15 NewOne kernel: [    1.161474] perf: AMD IBS detected (0x000001ff)
Sep 13 23:12:15 NewOne kernel: [    1.161524] Scanning for low memory corruption every 60 seconds
Sep 13 23:12:15 NewOne kernel: [    1.162212] futex hash table entries: 1024 (order: 4, 65536 bytes)
Sep 13 23:12:15 NewOne kernel: [    1.162237] Initialise system trusted keyring
Sep 13 23:12:15 NewOne kernel: [    1.162268] audit: initializing netlink subsys (disabled)
Sep 13 23:12:15 NewOne kernel: [    1.162299] audit: type=2000 audit(1442211123.036:1): initialized
Sep 13 23:12:15 NewOne kernel: [    1.162993] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Sep 13 23:12:15 NewOne kernel: [    1.166465] zpool: loaded
Sep 13 23:12:15 NewOne kernel: [    1.166470] zbud: loaded
Sep 13 23:12:15 NewOne kernel: [    1.166813] VFS: Disk quotas dquot_6.5.2
Sep 13 23:12:15 NewOne kernel: [    1.166885] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep 13 23:12:15 NewOne kernel: [    1.167930] fuse init (API version 7.23)
Sep 13 23:12:15 NewOne kernel: [    1.168210] Key type big_key registered
Sep 13 23:12:15 NewOne kernel: [    1.168876] Key type asymmetric registered
Sep 13 23:12:15 NewOne kernel: [    1.168882] Asymmetric key parser 'x509' registered
Sep 13 23:12:15 NewOne kernel: [    1.168954] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Sep 13 23:12:15 NewOne kernel: [    1.169017] io scheduler noop registered
Sep 13 23:12:15 NewOne kernel: [    1.169023] io scheduler deadline registered (default)
Sep 13 23:12:15 NewOne kernel: [    1.169088] io scheduler cfq registered
Sep 13 23:12:15 NewOne kernel: [    1.169669] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 13 23:12:15 NewOne kernel: [    1.169702] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 13 23:12:15 NewOne kernel: [    1.169768] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
Sep 13 23:12:15 NewOne kernel: [    1.169770] vesafb: scrolling: redraw
Sep 13 23:12:15 NewOne kernel: [    1.169773] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Sep 13 23:12:15 NewOne kernel: [    1.170247] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90005b80000, using 8128k, total 8128k
Sep 13 23:12:15 NewOne kernel: [    1.170463] Console: switching to colour frame buffer device 240x67
Sep 13 23:12:15 NewOne kernel: [    1.170518] fb0: VESA VGA frame buffer device
Sep 13 23:12:15 NewOne kernel: [    1.170692] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Sep 13 23:12:15 NewOne kernel: [    1.170698] ACPI: Power Button [PWRB]
Sep 13 23:12:15 NewOne kernel: [    1.170782] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Sep 13 23:12:15 NewOne kernel: [    1.170785] ACPI: Power Button [PWRF]
Sep 13 23:12:15 NewOne kernel: [    1.170934] ACPI: acpi_idle registered with cpuidle
Sep 13 23:12:15 NewOne kernel: [    1.174028] thermal LNXTHERM:00: registered as thermal_zone0
Sep 13 23:12:15 NewOne kernel: [    1.174032] ACPI: Thermal Zone [THRM] (32 C)
Sep 13 23:12:15 NewOne kernel: [    1.174095] GHES: HEST is not enabled!
Sep 13 23:12:15 NewOne kernel: [    1.174284] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Sep 13 23:12:15 NewOne kernel: [    1.194733] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Sep 13 23:12:15 NewOne kernel: [    1.197896] Linux agpgart interface v0.103
Sep 13 23:12:15 NewOne kernel: [    1.200576] brd: module loaded
Sep 13 23:12:15 NewOne kernel: [    1.201935] loop: module loaded
Sep 13 23:12:15 NewOne kernel: [    1.202336] libphy: Fixed MDIO Bus: probed
Sep 13 23:12:15 NewOne kernel: [    1.202342] tun: Universal TUN/TAP device driver, 1.6
Sep 13 23:12:15 NewOne kernel: [    1.202345] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 13 23:12:15 NewOne kernel: [    1.202437] PPP generic driver version 2.4.2
Sep 13 23:12:15 NewOne kernel: [    1.202731] QUIRK: Enable AMD PLL fix
Sep 13 23:12:15 NewOne kernel: [    1.202750] xhci_hcd 0000:00:10.0: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.202761] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Sep 13 23:12:15 NewOne kernel: [    1.203164] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Sep 13 23:12:15 NewOne kernel: [    1.203169] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.203173] usb usb1: Product: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.203176] usb usb1: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
Sep 13 23:12:15 NewOne kernel: [    1.203179] usb usb1: SerialNumber: 0000:00:10.0
Sep 13 23:12:15 NewOne kernel: [    1.203389] hub 1-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.203404] hub 1-0:1.0: 2 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.203576] xhci_hcd 0000:00:10.0: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.203584] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Sep 13 23:12:15 NewOne kernel: [    1.206416] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Sep 13 23:12:15 NewOne kernel: [    1.206420] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.206423] usb usb2: Product: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.206426] usb usb2: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
Sep 13 23:12:15 NewOne kernel: [    1.206429] usb usb2: SerialNumber: 0000:00:10.0
Sep 13 23:12:15 NewOne kernel: [    1.206624] hub 2-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.206637] hub 2-0:1.0: 2 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.206956] xhci_hcd 0000:00:10.1: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.206965] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Sep 13 23:12:15 NewOne kernel: [    1.207332] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Sep 13 23:12:15 NewOne kernel: [    1.207336] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.207339] usb usb3: Product: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.207342] usb usb3: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
Sep 13 23:12:15 NewOne kernel: [    1.207345] usb usb3: SerialNumber: 0000:00:10.1
Sep 13 23:12:15 NewOne kernel: [    1.207536] hub 3-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.207551] hub 3-0:1.0: 2 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.207709] xhci_hcd 0000:00:10.1: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.207717] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 4
Sep 13 23:12:15 NewOne kernel: [    1.210616] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
Sep 13 23:12:15 NewOne kernel: [    1.210619] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.210622] usb usb4: Product: xHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.210625] usb usb4: Manufacturer: Linux 3.19.0-28-generic xhci-hcd
Sep 13 23:12:15 NewOne kernel: [    1.210627] usb usb4: SerialNumber: 0000:00:10.1
Sep 13 23:12:15 NewOne kernel: [    1.210816] hub 4-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.210829] hub 4-0:1.0: 2 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.211007] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 13 23:12:15 NewOne kernel: [    1.211015] ehci-pci: EHCI PCI platform driver
Sep 13 23:12:15 NewOne kernel: [    1.211190] ehci-pci 0000:00:12.2: EHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.211198] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 5
Sep 13 23:12:15 NewOne kernel: [    1.211204] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Sep 13 23:12:15 NewOne kernel: [    1.211216] ehci-pci 0000:00:12.2: debug port 1
Sep 13 23:12:15 NewOne kernel: [    1.211264] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb6f000
Sep 13 23:12:15 NewOne kernel: [    1.220326] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Sep 13 23:12:15 NewOne kernel: [    1.220416] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
Sep 13 23:12:15 NewOne kernel: [    1.220420] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.220423] usb usb5: Product: EHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.220425] usb usb5: Manufacturer: Linux 3.19.0-28-generic ehci_hcd
Sep 13 23:12:15 NewOne kernel: [    1.220427] usb usb5: SerialNumber: 0000:00:12.2
Sep 13 23:12:15 NewOne kernel: [    1.220651] hub 5-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.220662] hub 5-0:1.0: 5 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.221015] ehci-pci 0000:00:13.2: EHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.221024] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 6
Sep 13 23:12:15 NewOne kernel: [    1.221029] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Sep 13 23:12:15 NewOne kernel: [    1.221040] ehci-pci 0000:00:13.2: debug port 1
Sep 13 23:12:15 NewOne kernel: [    1.221074] ehci-pci 0000:00:13.2: irq 17, io mem 0xfeb6d000
Sep 13 23:12:15 NewOne kernel: [    1.232320] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Sep 13 23:12:15 NewOne kernel: [    1.232406] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
Sep 13 23:12:15 NewOne kernel: [    1.232408] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.232411] usb usb6: Product: EHCI Host Controller
Sep 13 23:12:15 NewOne kernel: [    1.232413] usb usb6: Manufacturer: Linux 3.19.0-28-generic ehci_hcd
Sep 13 23:12:15 NewOne kernel: [    1.232414] usb usb6: SerialNumber: 0000:00:13.2
Sep 13 23:12:15 NewOne kernel: [    1.232609] hub 6-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.232619] hub 6-0:1.0: 5 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.232804] ehci-platform: EHCI generic platform driver
Sep 13 23:12:15 NewOne kernel: [    1.232822] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 13 23:12:15 NewOne kernel: [    1.232829] ohci-pci: OHCI PCI platform driver
Sep 13 23:12:15 NewOne kernel: [    1.232966] ohci-pci 0000:00:12.0: OHCI PCI host controller
Sep 13 23:12:15 NewOne kernel: [    1.232974] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 7
Sep 13 23:12:15 NewOne kernel: [    1.233007] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb70000
Sep 13 23:12:15 NewOne kernel: [    1.292348] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Sep 13 23:12:15 NewOne kernel: [    1.292352] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.292354] usb usb7: Product: OHCI PCI host controller
Sep 13 23:12:15 NewOne kernel: [    1.292355] usb usb7: Manufacturer: Linux 3.19.0-28-generic ohci_hcd
Sep 13 23:12:15 NewOne kernel: [    1.292356] usb usb7: SerialNumber: 0000:00:12.0
Sep 13 23:12:15 NewOne kernel: [    1.292533] hub 7-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.292543] hub 7-0:1.0: 5 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.292795] ohci-pci 0000:00:13.0: OHCI PCI host controller
Sep 13 23:12:15 NewOne kernel: [    1.292801] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 8
Sep 13 23:12:15 NewOne kernel: [    1.292832] ohci-pci 0000:00:13.0: irq 18, io mem 0xfeb6e000
Sep 13 23:12:15 NewOne kernel: [    1.352334] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
Sep 13 23:12:15 NewOne kernel: [    1.352338] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.352340] usb usb8: Product: OHCI PCI host controller
Sep 13 23:12:15 NewOne kernel: [    1.352342] usb usb8: Manufacturer: Linux 3.19.0-28-generic ohci_hcd
Sep 13 23:12:15 NewOne kernel: [    1.352343] usb usb8: SerialNumber: 0000:00:13.0
Sep 13 23:12:15 NewOne kernel: [    1.352523] hub 8-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.352532] hub 8-0:1.0: 5 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.352782] ohci-pci 0000:00:14.5: OHCI PCI host controller
Sep 13 23:12:15 NewOne kernel: [    1.352791] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 9
Sep 13 23:12:15 NewOne kernel: [    1.352817] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb6c000
Sep 13 23:12:15 NewOne kernel: [    1.412313] usb usb9: New USB device found, idVendor=1d6b, idProduct=0001
Sep 13 23:12:15 NewOne kernel: [    1.412317] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep 13 23:12:15 NewOne kernel: [    1.412319] usb usb9: Product: OHCI PCI host controller
Sep 13 23:12:15 NewOne kernel: [    1.412320] usb usb9: Manufacturer: Linux 3.19.0-28-generic ohci_hcd
Sep 13 23:12:15 NewOne kernel: [    1.412322] usb usb9: SerialNumber: 0000:00:14.5
Sep 13 23:12:15 NewOne kernel: [    1.412509] hub 9-0:1.0: USB hub found
Sep 13 23:12:15 NewOne kernel: [    1.412522] hub 9-0:1.0: 2 ports detected
Sep 13 23:12:15 NewOne kernel: [    1.412641] ohci-platform: OHCI generic platform driver
Sep 13 23:12:15 NewOne kernel: [    1.412657] uhci_hcd: USB Universal Host Controller Interface driver
Sep 13 23:12:15 NewOne kernel: [    1.412720] i8042: PNP: No PS/2 controller found. Probing ports directly.
Sep 13 23:12:15 NewOne kernel: [    1.413080] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 13 23:12:15 NewOne kernel: [    1.413085] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 13 23:12:15 NewOne kernel: [    1.413362] mousedev: PS/2 mouse device common for all mice
Sep 13 23:12:15 NewOne kernel: [    1.413521] rtc_cmos 00:04: RTC can wake from S4
Sep 13 23:12:15 NewOne kernel: [    1.413634] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Sep 13 23:12:15 NewOne kernel: [    1.413655] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Sep 13 23:12:15 NewOne kernel: [    1.413675] i2c /dev entries driver
Sep 13 23:12:15 NewOne kernel: [    1.413748] device-mapper: uevent: version 1.0.3
Sep 13 23:12:15 NewOne kernel: [    1.413824] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
Sep 13 23:12:15 NewOne kernel: [    1.413845] ledtrig-cpu: registered to indicate activity on CPUs
Sep 13 23:12:15 NewOne kernel: [    1.414039] PCCT header not found.
Sep 13 23:12:15 NewOne kernel: [    1.414042] ACPI PCC probe failed.
Sep 13 23:12:15 NewOne kernel: [    1.414132] TCP: cubic registered
Sep 13 23:12:15 NewOne kernel: [    1.414247] NET: Registered protocol family 10
Sep 13 23:12:15 NewOne kernel: [    1.414531] NET: Registered protocol family 17
Sep 13 23:12:15 NewOne kernel: [    1.414546] Key type dns_resolver registered
Sep 13 23:12:15 NewOne kernel: [    1.415029] Loading compiled-in X.509 certificates
Sep 13 23:12:15 NewOne kernel: [    1.415770] Loaded X.509 cert 'Magrathea: Glacier signing key: 99112ef1a6ba85be992582e9fef3a23f1a888175'
Sep 13 23:12:15 NewOne kernel: [    1.415785] registered taskstats version 1
Sep 13 23:12:15 NewOne kernel: [    1.417877] Key type trusted registered
Sep 13 23:12:15 NewOne kernel: [    1.421134] Key type encrypted registered
Sep 13 23:12:15 NewOne kernel: [    1.421147] AppArmor: AppArmor sha1 policy hashing enabled
Sep 13 23:12:15 NewOne kernel: [    1.421151] ima: No TPM chip found, activating TPM-bypass!
Sep 13 23:12:15 NewOne kernel: [    1.421179] evm: HMAC attrs: 0x1
Sep 13 23:12:15 NewOne kernel: [    1.421501]   Magic number: 15:870:215
Sep 13 23:12:15 NewOne kernel: [    1.421521] event_source software: hash matches
Sep 13 23:12:15 NewOne kernel: [    1.421593] rtc_cmos 00:04: setting system clock to 2015-09-14 06:12:03 UTC (1442211123)
Sep 13 23:12:15 NewOne kernel: [    1.421756] acpi-cpufreq: overriding BIOS provided _PSD data
Sep 13 23:12:15 NewOne kernel: [    1.421936] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 13 23:12:15 NewOne kernel: [    1.421937] EDD information not available.
Sep 13 23:12:15 NewOne kernel: [    1.422026] PM: Hibernation image not present or could not be loaded.
Sep 13 23:12:15 NewOne kernel: [    1.422439] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
Sep 13 23:12:15 NewOne kernel: [    1.422441] Write protecting the kernel read-only data: 12288k
Sep 13 23:12:15 NewOne kernel: [    1.422659] Freeing unused kernel memory: 176K (ffff8800017d4000 - ffff880001800000)
Sep 13 23:12:15 NewOne kernel: [    1.422782] Freeing unused kernel memory: 332K (ffff880001bad000 - ffff880001c00000)
Sep 13 23:12:15 NewOne kernel: [    1.432941] random: systemd-udevd urandom read with 4 bits of entropy available
Sep 13 23:12:15 NewOne kernel: [    1.452237] ahci 0000:00:11.0: version 3.0
Sep 13 23:12:15 NewOne kernel: [    1.452424] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Sep 13 23:12:15 NewOne kernel: [    1.452428] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Sep 13 23:12:15 NewOne kernel: [    1.454228] scsi host0: ahci
Sep 13 23:12:15 NewOne kernel: [    1.456182] scsi host1: ahci
Sep 13 23:12:15 NewOne kernel: [    1.456284] scsi host2: ahci
Sep 13 23:12:15 NewOne kernel: [    1.456378] scsi host3: ahci
Sep 13 23:12:15 NewOne kernel: [    1.456428] ata1: SATA max UDMA/133 abar m2048@0xfeb71000 port 0xfeb71100 irq 19
Sep 13 23:12:15 NewOne kernel: [    1.456431] ata2: SATA max UDMA/133 abar m2048@0xfeb71000 port 0xfeb71180 irq 19
Sep 13 23:12:15 NewOne kernel: [    1.456433] ata3: SATA max UDMA/133 abar m2048@0xfeb71000 port 0xfeb71200 irq 19
Sep 13 23:12:15 NewOne kernel: [    1.456435] ata4: SATA max UDMA/133 abar m2048@0xfeb71000 port 0xfeb71280 irq 19
Sep 13 23:12:15 NewOne kernel: [    1.457550] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep 13 23:12:15 NewOne kernel: [    1.457560] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
Sep 13 23:12:15 NewOne kernel: [    1.465142] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90005b70000, b8:97:5a:ae:70:b4, XID 0c000800 IRQ 34
Sep 13 23:12:15 NewOne kernel: [    1.465145] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Sep 13 23:12:15 NewOne kernel: [    1.512261] usb 1-1: new low-speed USB device number 2 using xhci_hcd
Sep 13 23:12:15 NewOne kernel: [    1.674587] usb 1-1: New USB device found, idVendor=046d, idProduct=c069
Sep 13 23:12:15 NewOne kernel: [    1.674591] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 13 23:12:15 NewOne kernel: [    1.674593] usb 1-1: Product: USB Laser Mouse
Sep 13 23:12:15 NewOne kernel: [    1.674594] usb 1-1: Manufacturer: Logitech
Sep 13 23:12:15 NewOne kernel: [    1.674931] usb 1-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Sep 13 23:12:15 NewOne kernel: [    1.689353] hidraw: raw HID events driver (C) Jiri Kosina
Sep 13 23:12:15 NewOne kernel: [    1.703700] usbcore: registered new interface driver usbhid
Sep 13 23:12:15 NewOne kernel: [    1.703703] usbhid: USB HID core driver
Sep 13 23:12:15 NewOne kernel: [    1.705399] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/0003:046D:C069.0001/input/input5
Sep 13 23:12:15 NewOne kernel: [    1.705538] hid-generic 0003:046D:C069.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:10.0-1/input0
Sep 13 23:12:15 NewOne kernel: [    1.776227] ata4: SATA link down (SStatus 0 SControl 300)
Sep 13 23:12:15 NewOne kernel: [    1.780233] ata3: SATA link down (SStatus 0 SControl 300)
Sep 13 23:12:15 NewOne kernel: [    1.804210] usb 8-1: new full-speed USB device number 2 using ohci-pci
Sep 13 23:12:15 NewOne kernel: [    1.948184] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 13 23:12:15 NewOne kernel: [    1.948218] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 13 23:12:15 NewOne kernel: [    1.948774] ata2.00: ATA-9: WDC WD10EZEX-60M2NA0, 03.01A03, max UDMA/100
Sep 13 23:12:15 NewOne kernel: [    1.948778] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Sep 13 23:12:15 NewOne kernel: [    1.949122] ata1.00: ATA-9: SanDisk SDSSDHII120G, X31200RL, max UDMA/133
Sep 13 23:12:15 NewOne kernel: [    1.949123] ata1.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Sep 13 23:12:15 NewOne kernel: [    1.949312] ata2.00: configured for UDMA/100
Sep 13 23:12:15 NewOne kernel: [    1.950644] ata1.00: configured for UDMA/133
Sep 13 23:12:15 NewOne kernel: [    1.950909] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SDSSDHII 00RL PQ: 0 ANSI: 5
Sep 13 23:12:15 NewOne kernel: [    1.951207] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 13 23:12:15 NewOne kernel: [    1.951211] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 13 23:12:15 NewOne kernel: [    1.951277] sd 0:0:0:0: [sda] Write Protect is off
Sep 13 23:12:15 NewOne kernel: [    1.951280] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 13 23:12:15 NewOne kernel: [    1.951319] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 13 23:12:15 NewOne kernel: [    1.951355] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EZEX-60M 1A03 PQ: 0 ANSI: 5
Sep 13 23:12:15 NewOne kernel: [    1.951590] sd 1:0:0:0: Attached scsi generic sg1 type 0
Sep 13 23:12:15 NewOne kernel: [    1.951619] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Sep 13 23:12:15 NewOne kernel: [    1.951622] sd 1:0:0:0: [sdb] 4096-byte physical blocks
Sep 13 23:12:15 NewOne kernel: [    1.951646] sd 1:0:0:0: [sdb] Write Protect is off
Sep 13 23:12:15 NewOne kernel: [    1.951648] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep 13 23:12:15 NewOne kernel: [    1.951659] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 13 23:12:15 NewOne kernel: [    1.952841]  sda: sda1 sda2
Sep 13 23:12:15 NewOne kernel: [    1.953209] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 13 23:12:15 NewOne kernel: [    1.977353] usb 8-1: New USB device found, idVendor=1532, idProduct=011b
Sep 13 23:12:15 NewOne kernel: [    1.977360] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 13 23:12:15 NewOne kernel: [    1.977364] usb 8-1: Product: Razer BlackWidow
Sep 13 23:12:15 NewOne kernel: [    1.977368] usb 8-1: Manufacturer: Razer
Sep 13 23:12:15 NewOne kernel: [    1.983666] input: Razer Razer BlackWidow as /devices/pci0000:00/0000:00:13.0/usb8/8-1/8-1:1.0/0003:1532:011B.0002/input/input6
Sep 13 23:12:15 NewOne kernel: [    2.026099]  sdb: sdb1 sdb2 sdb3
Sep 13 23:12:15 NewOne kernel: [    2.026449] sd 1:0:0:0: [sdb] Attached SCSI disk
Sep 13 23:12:15 NewOne kernel: [    2.036188] hid-generic 0003:1532:011B.0002: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer BlackWidow] on usb-0000:00:13.0-1/input0
Sep 13 23:12:15 NewOne kernel: [    2.045534] input: Razer Razer BlackWidow as /devices/pci0000:00/0000:00:13.0/usb8/8-1/8-1:1.1/0003:1532:011B.0003/input/input7
Sep 13 23:12:15 NewOne kernel: [    2.100511] hid-generic 0003:1532:011B.0003: input,hidraw2: USB HID v1.11 Keyboard [Razer Razer BlackWidow] on usb-0000:00:13.0-1/input1
Sep 13 23:12:15 NewOne kernel: [    2.106426] input: Razer Razer BlackWidow as /devices/pci0000:00/0000:00:13.0/usb8/8-1/8-1:1.2/0003:1532:011B.0004/input/input8
Sep 13 23:12:15 NewOne kernel: [    2.106617] hid-generic 0003:1532:011B.0004: input,hidraw3: USB HID v1.11 Mouse [Razer Razer BlackWidow] on usb-0000:00:13.0-1/input2
Sep 13 23:12:15 NewOne kernel: [    2.160132] tsc: Refined TSC clocksource calibration: 3892.724 MHz
Sep 13 23:12:15 NewOne kernel: [    2.376292] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
Sep 13 23:12:15 NewOne kernel: [    2.376296] EXT4-fs (sda2): write access will be enabled during recovery
Sep 13 23:12:15 NewOne kernel: [    2.474777] EXT4-fs (sda2): orphan cleanup on readonly fs
Sep 13 23:12:15 NewOne kernel: [    2.474909] EXT4-fs (sda2): 7 orphan inodes deleted
Sep 13 23:12:15 NewOne kernel: [    2.474910] EXT4-fs (sda2): recovery complete
Sep 13 23:12:15 NewOne kernel: [    2.477980] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Sep 13 23:12:15 NewOne kernel: [    2.586699] systemd[1]: Inserted module 'autofs4'
Sep 13 23:12:15 NewOne kernel: [    2.591174] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
Sep 13 23:12:15 NewOne kernel: [    2.591310] systemd[1]: Detected architecture x86-64.
Sep 13 23:12:15 NewOne kernel: [    2.591515] systemd[1]: Set hostname to <NewOne>.
Sep 13 23:12:15 NewOne kernel: [    2.667187] systemd[1]: Reached target Remote File Systems (Pre).
Sep 13 23:12:15 NewOne kernel: [    2.667209] systemd[1]: Starting Remote File Systems (Pre).
Sep 13 23:12:15 NewOne kernel: [    2.667295] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
Sep 13 23:12:15 NewOne kernel: [    2.667309] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
Sep 13 23:12:15 NewOne kernel: [    2.667380] systemd[1]: Created slice Root Slice.
Sep 13 23:12:15 NewOne kernel: [    2.667394] systemd[1]: Starting Root Slice.
Sep 13 23:12:15 NewOne kernel: [    2.667455] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
Sep 13 23:12:15 NewOne kernel: [    2.667469] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
Sep 13 23:12:15 NewOne kernel: [    2.667625] systemd[1]: Created slice User and Session Slice.
Sep 13 23:12:15 NewOne kernel: [    2.667638] systemd[1]: Starting User and Session Slice.
Sep 13 23:12:15 NewOne kernel: [    2.667724] systemd[1]: Listening on Journal Socket.
Sep 13 23:12:15 NewOne kernel: [    2.667746] systemd[1]: Starting Journal Socket.
Sep 13 23:12:15 NewOne kernel: [    2.667800] systemd[1]: Listening on udev Kernel Socket.
Sep 13 23:12:15 NewOne kernel: [    2.667815] systemd[1]: Starting udev Kernel Socket.
Sep 13 23:12:15 NewOne kernel: [    2.667970] systemd[1]: Created slice System Slice.
Sep 13 23:12:15 NewOne kernel: [    2.667993] systemd[1]: Starting System Slice.
Sep 13 23:12:15 NewOne kernel: [    2.668966] systemd[1]: Starting Increase datagram queue length...
Sep 13 23:12:15 NewOne kernel: [    2.670053] systemd[1]: Starting Create list of required static device nodes for the current kernel...
Sep 13 23:12:15 NewOne kernel: [    2.671233] systemd[1]: Started Braille Device Support.
Sep 13 23:12:15 NewOne kernel: [    2.671488] systemd[1]: Starting Braille Device Support...
Sep 13 23:12:15 NewOne kernel: [    2.672639] systemd[1]: Mounting Huge Pages File System...
Sep 13 23:12:15 NewOne kernel: [    2.672819] systemd[1]: Created slice system-systemd\x2dfsck.slice.
Sep 13 23:12:15 NewOne kernel: [    2.672839] systemd[1]: Starting system-systemd\x2dfsck.slice.
Sep 13 23:12:15 NewOne kernel: [    2.673662] systemd[1]: Starting Uncomplicated firewall...
Sep 13 23:12:15 NewOne kernel: [    2.674500] systemd[1]: Starting Nameserver information manager...
Sep 13 23:12:15 NewOne kernel: [    2.674596] systemd[1]: Reached target Slices.
Sep 13 23:12:15 NewOne kernel: [    2.674623] systemd[1]: Starting Slices.
Sep 13 23:12:15 NewOne kernel: [    2.675626] systemd[1]: Mounting Debug File System...
Sep 13 23:12:15 NewOne kernel: [    2.675731] systemd[1]: Listening on Delayed Shutdown Socket.
Sep 13 23:12:15 NewOne kernel: [    2.675755] systemd[1]: Starting Delayed Shutdown Socket.
Sep 13 23:12:15 NewOne kernel: [    2.675797] systemd[1]: Listening on fsck to fsckd communication Socket.
Sep 13 23:12:15 NewOne kernel: [    2.675808] systemd[1]: Starting fsck to fsckd communication Socket.
Sep 13 23:12:15 NewOne kernel: [    2.675887] systemd[1]: Listening on udev Control Socket.
Sep 13 23:12:15 NewOne kernel: [    2.675898] systemd[1]: Starting udev Control Socket.
Sep 13 23:12:15 NewOne kernel: [    2.677842] systemd[1]: Starting udev Coldplug all Devices...
Sep 13 23:12:15 NewOne kernel: [    2.680766] systemd[1]: Starting Load Kernel Modules...
Sep 13 23:12:15 NewOne kernel: [    2.681084] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
Sep 13 23:12:15 NewOne kernel: [    2.681109] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
Sep 13 23:12:15 NewOne kernel: [    2.681891] systemd[1]: Started Set Up Additional Binary Formats.
Sep 13 23:12:15 NewOne kernel: [    2.682765] systemd[1]: Starting Setup Virtual Console...
Sep 13 23:12:15 NewOne kernel: [    2.682863] systemd[1]: Listening on Journal Socket (/dev/log).
Sep 13 23:12:15 NewOne kernel: [    2.682923] systemd[1]: Starting Journal Socket (/dev/log).
Sep 13 23:12:15 NewOne kernel: [    2.683025] systemd[1]: Listening on Journal Audit Socket.
Sep 13 23:12:15 NewOne kernel: [    2.683037] systemd[1]: Starting Journal Audit Socket.
Sep 13 23:12:15 NewOne kernel: [    2.683068] systemd[1]: Reached target Encrypted Volumes.
Sep 13 23:12:15 NewOne kernel: [    2.683078] systemd[1]: Starting Encrypted Volumes.
Sep 13 23:12:15 NewOne kernel: [    2.684074] systemd[1]: Mounting POSIX Message Queue File System...
Sep 13 23:12:15 NewOne kernel: [    2.684244] systemd[1]: Created slice system-getty.slice.
Sep 13 23:12:15 NewOne kernel: [    2.684263] systemd[1]: Starting system-getty.slice.
Sep 13 23:12:15 NewOne kernel: [    2.685364] systemd[1]: Mounted Huge Pages File System.
Sep 13 23:12:15 NewOne kernel: [    2.685404] systemd[1]: Mounted Debug File System.
Sep 13 23:12:15 NewOne kernel: [    2.685683] systemd[1]: Started Increase datagram queue length.
Sep 13 23:12:15 NewOne kernel: [    2.685966] systemd[1]: Started Create list of required static device nodes for the current kernel.
Sep 13 23:12:15 NewOne kernel: [    2.686841] systemd[1]: Started Uncomplicated firewall.
Sep 13 23:12:15 NewOne kernel: [    2.687963] systemd[1]: Started Setup Virtual Console.
Sep 13 23:12:15 NewOne kernel: [    2.691342] systemd[1]: Started Nameserver information manager.
Sep 13 23:12:15 NewOne kernel: [    2.691629] systemd[1]: Mounted POSIX Message Queue File System.
Sep 13 23:12:15 NewOne kernel: [    2.693745] lp: driver loaded but no devices found
Sep 13 23:12:15 NewOne kernel: [    2.696951] ppdev: user-space parallel port driver
Sep 13 23:12:15 NewOne kernel: [    2.701379] systemd[1]: Started Load Kernel Modules.
Sep 13 23:12:15 NewOne kernel: [    2.710433] systemd[1]: Started udev Coldplug all Devices.
Sep 13 23:12:15 NewOne kernel: [    2.712192] systemd[1]: Starting udev Wait for Complete Device Initialization...
Sep 13 23:12:15 NewOne kernel: [    2.712756] systemd[1]: Starting Apply Kernel Variables...
Sep 13 23:12:15 NewOne kernel: [    2.712827] systemd[1]: Mounted Configuration File System.
Sep 13 23:12:15 NewOne kernel: [    2.713497] systemd[1]: Mounting FUSE Control File System...
Sep 13 23:12:15 NewOne kernel: [    2.714126] systemd[1]: Starting Create Static Device Nodes in /dev...
Sep 13 23:12:15 NewOne kernel: [    2.714192] systemd[1]: Listening on Syslog Socket.
Sep 13 23:12:15 NewOne kernel: [    2.714224] systemd[1]: Starting Syslog Socket.
Sep 13 23:12:15 NewOne kernel: [    2.714790] systemd[1]: Starting Journal Service...
Sep 13 23:12:15 NewOne kernel: [    2.717314] systemd[1]: Mounted FUSE Control File System.
Sep 13 23:12:15 NewOne kernel: [    2.720199] systemd[1]: Started Apply Kernel Variables.
Sep 13 23:12:15 NewOne kernel: [    2.723604] systemd[1]: Started Create Static Device Nodes in /dev.
Sep 13 23:12:15 NewOne kernel: [    2.724378] systemd[1]: Starting udev Kernel Device Manager...
Sep 13 23:12:15 NewOne kernel: [    2.749359] systemd[1]: Started Journal Service.
Sep 13 23:12:15 NewOne kernel: [    2.944792] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Sep 13 23:12:15 NewOne kernel: [    2.944831] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Sep 13 23:12:15 NewOne kernel: [    2.944925] ACPI Error: [AFN7] Namespace lookup failure, AE_NOT_FOUND (20141107/psargs-359)
Sep 13 23:12:15 NewOne kernel: [    2.944930] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.LCD_._BCM] (Node ffff8803df0a3ca8), AE_NOT_FOUND (20141107/psparse-536)
Sep 13 23:12:15 NewOne kernel: [    2.944937] ACPI Error: Evaluating _BCM failed (20141107/video-387)
Sep 13 23:12:15 NewOne kernel: [    2.945043] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input9
Sep 13 23:12:15 NewOne kernel: [    2.954066] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Sep 13 23:12:15 NewOne kernel: [    2.954469] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
Sep 13 23:12:15 NewOne kernel: [    2.966284] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 13 23:12:15 NewOne kernel: [    2.966440] MCE: In-kernel MCE decoding enabled.
Sep 13 23:12:15 NewOne kernel: [    2.968762] EDAC MC: Ver: 3.0.0
Sep 13 23:12:15 NewOne kernel: [    2.984359] AMD64 EDAC driver v3.4.0
Sep 13 23:12:15 NewOne kernel: [    2.984398] EDAC amd64: DRAM ECC disabled.
Sep 13 23:12:15 NewOne kernel: [    2.984404] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Sep 13 23:12:15 NewOne kernel: [    2.984404]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Sep 13 23:12:15 NewOne kernel: [    2.984404]  (Note that use of the override may cause unknown side effects.)
Sep 13 23:12:15 NewOne kernel: [    2.984981] [drm] Initialized drm 1.1.0 20060810
Sep 13 23:12:15 NewOne kernel: [    3.024943] [drm] radeon kernel modesetting enabled.
Sep 13 23:12:15 NewOne kernel: [    3.026282] AVX version of gcm_enc/dec engaged.
Sep 13 23:12:15 NewOne kernel: [    3.026286] AES CTR mode by8 optimization enabled
Sep 13 23:12:15 NewOne kernel: [    3.028205] Adding 31250428k swap on /dev/sdb2.  Priority:-1 extents:1 across:31250428k FS
Sep 13 23:12:15 NewOne kernel: [    3.060288] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
Sep 13 23:12:15 NewOne kernel: [    3.060291] AMD IOMMUv2 functionality not available on this system
Sep 13 23:12:15 NewOne kernel: [    3.063392] Found CRAT image with size=1440
Sep 13 23:12:15 NewOne kernel: [    3.063398] Parsing CRAT table with 1 nodes
Sep 13 23:12:15 NewOne kernel: [    3.063400] Found CU entry in CRAT table with proximity_domain=0 caps=0
Sep 13 23:12:15 NewOne kernel: [    3.063401] CU CPU: cores=4 id_base=16
Sep 13 23:12:15 NewOne kernel: [    3.063402] Found CU entry in CRAT table with proximity_domain=0 caps=0
Sep 13 23:12:15 NewOne kernel: [    3.063403] CU GPU: simds=32 id_base=-2147483648
Sep 13 23:12:15 NewOne kernel: [    3.063404] Found memory entry in CRAT table with proximity_domain=0
Sep 13 23:12:15 NewOne kernel: [    3.063405] Found memory entry in CRAT table with proximity_domain=0
Sep 13 23:12:15 NewOne kernel: [    3.063406] Found memory entry in CRAT table with proximity_domain=0
Sep 13 23:12:15 NewOne kernel: [    3.063407] Found memory entry in CRAT table with proximity_domain=0
Sep 13 23:12:15 NewOne kernel: [    3.063408] Found cache entry in CRAT table with processor_id=16
Sep 13 23:12:15 NewOne kernel: [    3.063409] Found cache entry in CRAT table with processor_id=16
Sep 13 23:12:15 NewOne kernel: [    3.063411] Found cache entry in CRAT table with processor_id=16
Sep 13 23:12:15 NewOne kernel: [    3.063412] Found cache entry in CRAT table with processor_id=17
Sep 13 23:12:15 NewOne kernel: [    3.063412] Found cache entry in CRAT table with processor_id=18
Sep 13 23:12:15 NewOne kernel: [    3.063413] Found cache entry in CRAT table with processor_id=18
Sep 13 23:12:15 NewOne kernel: [    3.063414] Found cache entry in CRAT table with processor_id=18
Sep 13 23:12:15 NewOne kernel: [    3.063415] Found cache entry in CRAT table with processor_id=19
Sep 13 23:12:15 NewOne kernel: [    3.063416] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063416] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063417] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063418] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063418] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063419] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063420] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063421] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063421] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063422] Found TLB entry in CRAT table (not processing)
Sep 13 23:12:15 NewOne kernel: [    3.063423] Creating topology SYSFS entries
Sep 13 23:12:15 NewOne kernel: [    3.063444] Finished initializing topology ret=0
Sep 13 23:12:15 NewOne kernel: [    3.067810] kfd kfd: Initialized module
Sep 13 23:12:15 NewOne kernel: [    3.069051] checking generic (d0000000 7f0000) vs hw (d0000000 10000000)
Sep 13 23:12:15 NewOne kernel: [    3.069054] fb: switching to radeondrmfb from VESA VGA
Sep 13 23:12:15 NewOne kernel: [    3.069083] Console: switching to colour dummy device 80x25
Sep 13 23:12:15 NewOne kernel: [    3.069376] [drm] initializing kernel modesetting (KAVERI 0x1002:0x130F 0x1565:0x1708).
Sep 13 23:12:15 NewOne kernel: [    3.069391] [drm] register mmio base: 0xFEB00000
Sep 13 23:12:15 NewOne kernel: [    3.069393] [drm] register mmio size: 262144
Sep 13 23:12:15 NewOne kernel: [    3.069397] [drm] doorbell mmio base: 0xE0000000
Sep 13 23:12:15 NewOne kernel: [    3.069398] [drm] doorbell mmio size: 8388608
Sep 13 23:12:15 NewOne kernel: [    3.069450] ATOM BIOS: 113
Sep 13 23:12:15 NewOne kernel: [    3.069502] radeon 0000:00:01.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
Sep 13 23:12:15 NewOne kernel: [    3.069504] radeon 0000:00:01.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
Sep 13 23:12:15 NewOne kernel: [    3.069506] [drm] Detected VRAM RAM=1024M, BAR=256M
Sep 13 23:12:15 NewOne kernel: [    3.069507] [drm] RAM width 128bits DDR
Sep 13 23:12:15 NewOne kernel: [    3.069963] [TTM] Zone  kernel: Available graphics memory: 7627174 kiB
Sep 13 23:12:15 NewOne kernel: [    3.069964] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
Sep 13 23:12:15 NewOne kernel: [    3.069966] [TTM] Initializing pool allocator
Sep 13 23:12:15 NewOne kernel: [    3.069971] [TTM] Initializing DMA pool allocator
Sep 13 23:12:15 NewOne kernel: [    3.069989] [drm] radeon: 1024M of VRAM memory ready
Sep 13 23:12:15 NewOne kernel: [    3.069991] [drm] radeon: 1024M of GTT memory ready.
Sep 13 23:12:15 NewOne kernel: [    3.070003] [drm] Loading kaveri Microcode
Sep 13 23:12:15 NewOne kernel: [    3.093228] [drm] Internal thermal controller without fan control
Sep 13 23:12:15 NewOne kernel: [    3.094720] [drm] radeon: dpm initialized
Sep 13 23:12:15 NewOne kernel: [    3.098121] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
Sep 13 23:12:15 NewOne kernel: [    3.098220] [drm] GART: num cpu pages 262144, num gpu pages 262144
Sep 13 23:12:15 NewOne kernel: [    3.100472] kvm: Nested Virtualization enabled
Sep 13 23:12:15 NewOne kernel: [    3.100475] kvm: Nested Paging enabled
Sep 13 23:12:15 NewOne kernel: [    3.115813] [drm] PCIE GART of 1024M enabled (table at 0x000000000078C000).
Sep 13 23:12:15 NewOne kernel: [    3.115961] radeon 0000:00:01.0: WB enabled
Sep 13 23:12:15 NewOne kernel: [    3.115974] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff8803da97cc00
Sep 13 23:12:15 NewOne kernel: [    3.115977] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff8803da97cc04
Sep 13 23:12:15 NewOne kernel: [    3.115980] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff8803da97cc08
Sep 13 23:12:15 NewOne kernel: [    3.115983] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff8803da97cc0c
Sep 13 23:12:15 NewOne kernel: [    3.115985] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff8803da97cc10
Sep 13 23:12:15 NewOne kernel: [    3.116400] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90007136c98
Sep 13 23:12:15 NewOne kernel: [    3.116472] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000040000c18 and cpu addr 0xffff8803da97cc18
Sep 13 23:12:15 NewOne kernel: [    3.116474] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000040000c1c and cpu addr 0xffff8803da97cc1c
Sep 13 23:12:15 NewOne kernel: [    3.116477] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Sep 13 23:12:15 NewOne kernel: [    3.116478] [drm] Driver supports precise vblank timestamp query.
Sep 13 23:12:15 NewOne kernel: [    3.116510] radeon 0000:00:01.0: radeon: using MSI.
Sep 13 23:12:15 NewOne kernel: [    3.116533] [drm] radeon: irq initialized.
Sep 13 23:12:15 NewOne kernel: [    3.119797] [drm] ring test on 0 succeeded in 3 usecs
Sep 13 23:12:15 NewOne kernel: [    3.119889] [drm] ring test on 1 succeeded in 2 usecs
Sep 13 23:12:15 NewOne kernel: [    3.119902] [drm] ring test on 2 succeeded in 2 usecs
Sep 13 23:12:15 NewOne kernel: [    3.120035] [drm] ring test on 3 succeeded in 3 usecs
Sep 13 23:12:15 NewOne kernel: [    3.120041] [drm] ring test on 4 succeeded in 3 usecs
Sep 13 23:12:15 NewOne kernel: [    3.165711] Switched to clocksource tsc
Sep 13 23:12:15 NewOne kernel: [    3.165714] [drm] ring test on 5 succeeded in 1 usecs
Sep 13 23:12:15 NewOne kernel: [    3.185569] [drm] UVD initialized successfully.
Sep 13 23:12:15 NewOne kernel: [    3.294752] [drm] ring test on 6 succeeded in 15 usecs
Sep 13 23:12:15 NewOne kernel: [    3.294764] [drm] ring test on 7 succeeded in 3 usecs
Sep 13 23:12:15 NewOne kernel: [    3.294765] [drm] VCE initialized successfully.
Sep 13 23:12:15 NewOne kernel: [    3.296839] [drm] ib test on ring 0 succeeded in 0 usecs
Sep 13 23:12:15 NewOne kernel: [    3.795726] [drm] ib test on ring 1 succeeded in 0 usecs
Sep 13 23:12:15 NewOne kernel: [    3.844153] random: nonblocking pool is initialized
Sep 13 23:12:15 NewOne kernel: [    4.295621] [drm] ib test on ring 2 succeeded in 0 usecs
Sep 13 23:12:15 NewOne kernel: [    4.295690] [drm] ib test on ring 3 succeeded in 0 usecs
Sep 13 23:12:15 NewOne kernel: [    4.295735] [drm] ib test on ring 4 succeeded in 0 usecs
Sep 13 23:12:15 NewOne kernel: [    4.815509] [drm] ib test on ring 5 succeeded
Sep 13 23:12:15 NewOne kernel: [    4.835977] [drm] ib test on ring 6 succeeded
Sep 13 23:12:15 NewOne kernel: [    4.836485] [drm] ib test on ring 7 succeeded
Sep 13 23:12:15 NewOne kernel: [    4.837313] [drm] Radeon Display Connectors
Sep 13 23:12:15 NewOne kernel: [    4.837315] [drm] Connector 0:
Sep 13 23:12:15 NewOne kernel: [    4.837316] [drm]   HDMI-A-1
Sep 13 23:12:15 NewOne kernel: [    4.837317] [drm]   HPD3
Sep 13 23:12:15 NewOne kernel: [    4.837319] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
Sep 13 23:12:15 NewOne kernel: [    4.837320] [drm]   Encoders:
Sep 13 23:12:15 NewOne kernel: [    4.837321] [drm]     DFP2: INTERNAL_UNIPHY2
Sep 13 23:12:15 NewOne kernel: [    4.837322] [drm] Connector 1:
Sep 13 23:12:15 NewOne kernel: [    4.837323] [drm]   VGA-1
Sep 13 23:12:15 NewOne kernel: [    4.837323] [drm]   HPD1
Sep 13 23:12:15 NewOne kernel: [    4.837325] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
Sep 13 23:12:15 NewOne kernel: [    4.837326] [drm]   Encoders:
Sep 13 23:12:15 NewOne kernel: [    4.837326] [drm]     CRT1: INTERNAL_UNIPHY
Sep 13 23:12:15 NewOne kernel: [    4.837327] [drm]     CRT1: NUTMEG
Sep 13 23:12:15 NewOne kernel: [    4.837328] [drm] Connector 2:
Sep 13 23:12:15 NewOne kernel: [    4.837329] [drm]   HDMI-A-2
Sep 13 23:12:15 NewOne kernel: [    4.837330] [drm]   HPD2
Sep 13 23:12:15 NewOne kernel: [    4.837331] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
Sep 13 23:12:15 NewOne kernel: [    4.837332] [drm]   Encoders:
Sep 13 23:12:15 NewOne kernel: [    4.837332] [drm]     DFP1: INTERNAL_UNIPHY3
Sep 13 23:12:15 NewOne kernel: [    5.081440] [drm] fb mappable at 0xD0990000
Sep 13 23:12:15 NewOne kernel: [    5.081442] [drm] vram apper at 0xD0000000
Sep 13 23:12:15 NewOne kernel: [    5.081444] [drm] size 8294400
Sep 13 23:12:15 NewOne kernel: [    5.081445] [drm] fb depth is 24
Sep 13 23:12:15 NewOne kernel: [    5.081446] [drm]    pitch is 7680
Sep 13 23:12:15 NewOne kernel: [    5.081635] fbcon: radeondrmfb (fb0) is primary device
Sep 13 23:12:15 NewOne kernel: [    5.081720] Console: switching to colour frame buffer device 240x67
Sep 13 23:12:15 NewOne kernel: [    5.081747] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
Sep 13 23:12:15 NewOne kernel: [    5.081748] radeon 0000:00:01.0: registered panic notifier
Sep 13 23:12:15 NewOne kernel: [    5.105441] kfd kfd: error getting iommu info. is the iommu enabled?
Sep 13 23:12:15 NewOne kernel: [    5.105446] kfd kfd: Error initializing iommuv2 for device (1002:130f)
Sep 13 23:12:15 NewOne kernel: [    5.105464] Creating topology SYSFS entries
Sep 13 23:12:15 NewOne kernel: [    5.105961] kfd kfd: device (1002:130f) NOT added due to errors
Sep 13 23:12:15 NewOne kernel: [    5.105967] [drm] Initialized radeon 2.40.0 20080528 for 0000:00:01.0 on minor 0
Sep 13 23:12:15 NewOne kernel: [    5.106135] snd_hda_intel 0000:00:01.1: Force to non-snoop mode
Sep 13 23:12:15 NewOne kernel: [    5.115848] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input10
Sep 13 23:12:15 NewOne kernel: [    5.116119] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.1/sound/card0/input11
Sep 13 23:12:15 NewOne kernel: [    5.121552] sound hdaudioC1D2: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Sep 13 23:12:15 NewOne kernel: [    5.121555] sound hdaudioC1D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Sep 13 23:12:15 NewOne kernel: [    5.121557] sound hdaudioC1D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Sep 13 23:12:15 NewOne kernel: [    5.121559] sound hdaudioC1D2:    mono: mono_out=0x0
Sep 13 23:12:15 NewOne kernel: [    5.121560] sound hdaudioC1D2:    inputs:
Sep 13 23:12:15 NewOne kernel: [    5.121562] sound hdaudioC1D2:      Front Mic=0x19
Sep 13 23:12:15 NewOne kernel: [    5.121564] sound hdaudioC1D2:      Rear Mic=0x18
Sep 13 23:12:15 NewOne kernel: [    5.121565] sound hdaudioC1D2:      Line=0x1a
Sep 13 23:12:15 NewOne kernel: [    5.130846] input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input12
Sep 13 23:12:15 NewOne kernel: [    5.130930] input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input13
Sep 13 23:12:15 NewOne kernel: [    5.131009] input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input14
Sep 13 23:12:15 NewOne kernel: [    5.131119] input: HD-Audio Generic Line Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input15
Sep 13 23:12:15 NewOne kernel: [    5.131214] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
Sep 13 23:12:15 NewOne kernel: [    5.151662] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Sep 13 23:12:15 NewOne kernel: [    5.176081] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Sep 13 23:12:15 NewOne kernel: [    5.739384] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Sep 13 23:12:15 NewOne kernel: [    5.769766] systemd-journald[253]: Received request to flush runtime journal from PID 1
Sep 13 23:12:15 NewOne kernel: [   12.804239] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
Sep 13 23:12:15 NewOne kernel: [   12.850285] audit: type=1400 audit(1442211134.928:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.850296] audit: type=1400 audit(1442211134.928:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.852276] audit: type=1400 audit(1442211134.928:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.852283] audit: type=1400 audit(1442211134.928:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.852289] audit: type=1400 audit(1442211134.928:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.852295] audit: type=1400 audit(1442211134.928:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.861845] audit: type=1400 audit(1442211134.940:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.861856] audit: type=1400 audit(1442211134.940:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.861862] audit: type=1400 audit(1442211134.940:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   12.861869] audit: type=1400 audit(1442211134.940:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=516 comm="apparmor_parser"
Sep 13 23:12:15 NewOne kernel: [   13.012410] cgroup: new mount options do not match the existing superblock, will be ignored
Sep 13 23:12:15 NewOne ModemManager[674]: <info>  ModemManager (version 1.4.0) starting in system bus...
Sep 13 23:12:15 NewOne systemd[1]: Started System Logging Service.
Sep 13 23:12:15 NewOne systemd[1]: Started Restore Sound Card State.
Sep 13 23:12:15 NewOne systemd[1]: Started LSB: Set the CPU Frequency Scaling governor to "ondemand".
Sep 13 23:12:15 NewOne cron[684]: (CRON) INFO (Running @reboot jobs)
Sep 13 23:12:15 NewOne systemd[1]: Started LSB: Speech Dispatcher.
Sep 13 23:12:15 NewOne systemd[1]: Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down..
Sep 13 23:12:15 NewOne gpu-manager[688]: /etc/modprobe.d is not a file
Sep 13 23:12:15 NewOne systemd[1]: Started Permit User Sessions.
Sep 13 23:12:15 NewOne irqbalance[672]: ...done.
Sep 13 23:12:15 NewOne anacron[675]: Normal exit (0 jobs run)
Sep 13 23:12:15 NewOne systemd[1]: Started D-Bus System Message Bus.
Sep 13 23:12:15 NewOne rsyslogd-2039: Could no open output pipe '/dev/xconsole': Permission denied [try http://www.rsyslog.com/e/2039 ]
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> NetworkManager (version 0.9.10.0) is starting...
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Read config: /etc/NetworkManager/NetworkManager.conf
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> WEXT support is enabled
Sep 13 23:12:15 NewOne dbus[715]: [system] AppArmor D-Bus mediation is enabled
Sep 13 23:12:15 NewOne apport[693]: * Starting automatic crash report generation: apport
Sep 13 23:12:15 NewOne thermald[657]: NO RAPL sysfs present
Sep 13 23:12:15 NewOne thermald[657]: Running on a vanilla kernel
Sep 13 23:12:15 NewOne thermald[657]: Polling mode is enabled: 4
Sep 13 23:12:15 NewOne thermald[657]: sensor_update: type acpitz
Sep 13 23:12:15 NewOne thermald[657]: thd_read_default_thermal_sensors loaded 1 sensors
Sep 13 23:12:15 NewOne avahi-daemon[679]: Successfully called chroot().
Sep 13 23:12:15 NewOne avahi-daemon[679]: Successfully dropped remaining capabilities.
Sep 13 23:12:15 NewOne thermald[657]: Thermal DTS: No coretemp sysfs found!!
Sep 13 23:12:15 NewOne thermald[657]: failed to open /dev/acpi_thermal_rel
Sep 13 23:12:15 NewOne thermald[657]: failed to open /dev/acpi_thermal_rel
Sep 13 23:12:15 NewOne thermald[657]: TRT/ART read failed
Sep 13 23:12:15 NewOne avahi-daemon[679]: No service file found in /etc/avahi/services.
Sep 13 23:12:15 NewOne dbus[715]: [system] Activating systemd to hand-off: service name='org.freedesktop.PolicyKit1' unit='polkitd.service'
Sep 13 23:12:15 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.systemd1'
Sep 13 23:12:15 NewOne systemd[1]: Started Thermal Daemon Service.
Sep 13 23:12:15 NewOne systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Sep 13 23:12:15 NewOne systemd[1]: Started LSB: daemon to balance interrupts for SMP systems.
Sep 13 23:12:15 NewOne systemd[1]: Started LSB: Record successful boot for GRUB.
Sep 13 23:12:15 NewOne apport[693]: ...done.
Sep 13 23:12:15 NewOne thermald[657]: Dumping parsed XML Data
Sep 13 23:12:15 NewOne thermald[657]: *** Index 0 ***
Sep 13 23:12:15 NewOne thermald[657]: Name: GenericX86LaptopDevice
Sep 13 23:12:15 NewOne systemd[1]: Started LSB: automatic crash report generation.
Sep 13 23:12:15 NewOne thermald[657]: UUID:
Sep 13 23:12:15 NewOne thermald[657]: type: 0
Sep 13 23:12:15 NewOne thermald[657]: Sensor 0
Sep 13 23:12:15 NewOne thermald[657]: Name: TSKN
Sep 13 23:12:15 NewOne thermald[657]: Path:
Sep 13 23:12:15 NewOne thermald[657]: Async Capable: 1
Sep 13 23:12:15 NewOne thermald[657]: Virtual: 0
Sep 13 23:12:15 NewOne thermald[657]: Zone 0
Sep 13 23:12:15 NewOne thermald[657]: Name: SKIN
Sep 13 23:12:15 NewOne thermald[657]: Trip Point 0
Sep 13 23:12:15 NewOne thermald[657]: temp 55000
Sep 13 23:12:15 NewOne thermald[657]: trip type 2
Sep 13 23:12:15 NewOne thermald[657]: hyst id 0
Sep 13 23:12:15 NewOne thermald[657]: sensor type TSKN
Sep 13 23:12:15 NewOne thermald[657]: cdev index 0
Sep 13 23:12:15 NewOne thermald[657]: type rapl_controller
Sep 13 23:12:15 NewOne thermald[657]: influence 100
Sep 13 23:12:15 NewOne thermald[657]: SamplingPeriod 16
Sep 13 23:12:15 NewOne thermald[657]: cdev index 1
Sep 13 23:12:15 NewOne thermald[657]: type intel_powerclamp
Sep 13 23:12:15 NewOne thermald[657]: influence 100
Sep 13 23:12:15 NewOne thermald[657]: SamplingPeriod 12
Sep 13 23:12:15 NewOne thermald[657]: *** Index 1 ***
Sep 13 23:12:15 NewOne thermald[657]: Name: ExamplePlatformName
Sep 13 23:12:15 NewOne thermald[657]: UUID: ExampleUUID
Sep 13 23:12:15 NewOne thermald[657]: type: 0
Sep 13 23:12:15 NewOne thermald[657]: Sensor 0
Sep 13 23:12:15 NewOne thermald[657]: Name: TSKN
Sep 13 23:12:15 NewOne thermald[657]: Path:
Sep 13 23:12:15 NewOne thermald[657]: Async Capable: 1
Sep 13 23:12:15 NewOne thermald[657]: Virtual: 0
Sep 13 23:12:15 NewOne thermald[657]: Sensor 1
Sep 13 23:12:15 NewOne thermald[657]: Name: example_sensor_1
Sep 13 23:12:15 NewOne thermald[657]: Path: /some_path
Sep 13 23:12:15 NewOne thermald[657]: Async Capable: 0
Sep 13 23:12:15 NewOne thermald[657]: Virtual: 0
Sep 13 23:12:15 NewOne thermald[657]: Sensor 2
Sep 13 23:12:15 NewOne thermald[657]: Name: example_thermal_sysfs_sensor
Sep 13 23:12:15 NewOne thermald[657]: Path:
Sep 13 23:12:15 NewOne thermald[657]: Async Capable: 1
Sep 13 23:12:15 NewOne thermald[657]: Virtual: 0
Sep 13 23:12:15 NewOne thermald[657]: Sensor 3
Sep 13 23:12:15 NewOne thermald[657]: Name: example_virtual_sensor
Sep 13 23:12:15 NewOne thermald[657]: Path:
Sep 13 23:12:15 NewOne thermald[657]: Async Capable: 0
Sep 13 23:12:15 NewOne thermald[657]: Virtual: 1
Sep 13 23:12:15 NewOne thermald[657]: Link type: example_sensor_1
Sep 13 23:12:15 NewOne thermald[657]: Link mult: 0.500000
Sep 13 23:12:15 NewOne thermald[657]: Link offset: 10.000000
Sep 13 23:12:15 NewOne thermald[657]: Zone 0
Sep 13 23:12:15 NewOne thermald[657]: Name: ExampleZonetype
Sep 13 23:12:15 NewOne thermald[657]: Trip Point 0
Sep 13 23:12:15 NewOne thermald[657]: temp 75000
Sep 13 23:12:15 NewOne thermald[657]: trip type 1
Sep 13 23:12:15 NewOne thermald[657]: hyst id 0
Sep 13 23:12:15 NewOne thermald[657]: sensor type example_sensor_1
Sep 13 23:12:15 NewOne thermald[657]: cdev index 0
Sep 13 23:12:15 NewOne thermald[657]: type example_cooling_device
Sep 13 23:12:15 NewOne thermald[657]: influence 100
Sep 13 23:12:15 NewOne thermald[657]: SamplingPeriod 12
Sep 13 23:12:15 NewOne thermald[657]: Cooling Dev 0
Sep 13 23:12:15 NewOne thermald[657]: Type: example_cooling_device
Sep 13 23:12:15 NewOne thermald[657]: Path:
Sep 13 23:12:15 NewOne thermald[657]: Min: 0
Sep 13 23:12:15 NewOne thermald[657]: Max: 50
Sep 13 23:12:15 NewOne thermald[657]: Step: 10
Sep 13 23:12:15 NewOne thermald[657]: AutoDownControl: 0
Sep 13 23:12:15 NewOne thermald[657]: PID: Kp 0.001000
Sep 13 23:12:15 NewOne thermald[657]: PID: Ki 0.000100
Sep 13 23:12:15 NewOne thermald[657]: PID: Kd 0.000100
Sep 13 23:12:15 NewOne thermald[657]: Product Name matched [wildcard]
Sep 13 23:12:15 NewOne thermald[657]: sensor id 1: No temp sysfs for reading raw temp
Sep 13 23:12:15 NewOne thermald[657]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Sep 13 23:12:15 NewOne thermald[657]: thd_read_default_cooling devices loaded 4 cdevs
Sep 13 23:12:15 NewOne thermald[657]: powercap RAPL no long term time window
Sep 13 23:12:15 NewOne thermald[657]: Product Name matched [wildcard]
Sep 13 23:12:15 NewOne thermald[657]: 0: Processor, C:0 MN: 0 MX:10 ST:1 pt:/sys/class/thermal/ rd_bk 0
Sep 13 23:12:15 NewOne thermald[657]: 1: Processor, C:0 MN: 0 MX:10 ST:1 pt:/sys/class/thermal/ rd_bk 0
Sep 13 23:12:15 NewOne thermald[657]: 2: Processor, C:0 MN: 0 MX:10 ST:1 pt:/sys/class/thermal/ rd_bk 0
Sep 13 23:12:15 NewOne thermald[657]: 3: Processor, C:0 MN: 0 MX:10 ST:1 pt:/sys/class/thermal/ rd_bk 0
Sep 13 23:12:15 NewOne thermald[657]: 4: cpufreq, C:0 MN: 0 MX:0 ST:1 pt:/sys/devices/system/cpu/ rd_bk 1
Sep 13 23:12:15 NewOne thermald[657]: Sorted trip dump :
Sep 13 23:12:15 NewOne thermald[657]: index 0: type:critical temp:127000 hyst:1 zone id:0 sensor id:0 cdev size:0
Sep 13 23:12:15 NewOne thermald[657]: trip type: 0 temp: 127000
Sep 13 23:12:15 NewOne thermald[657]: sysfs write failed trip_point_0_temp
Sep 13 23:12:15 NewOne thermald[657]: thd_read_default_thermal_zones loaded 1 zones
Sep 13 23:12:15 NewOne thermald[657]: zone cpu will be created
Sep 13 23:12:15 NewOne thermald[657]: /sys/class/hwmon/hwmon0/name->acpitz
Sep 13 23:12:15 NewOne thermald[657]: /sys/class/hwmon/hwmon1/name->k10temp
Sep 13 23:12:15 NewOne thermald[657]: /sys/class/hwmon/hwmon2/name->fam15h_power
Sep 13 23:12:15 NewOne thermald[657]: /sys/class/hwmon/hwmon3/name->radeon
Sep 13 23:12:15 NewOne thermald[657]: Thermal DTS or hwmon: No Zones present Need to configure manually
Sep 13 23:12:15 NewOne thermald[657]: Product Name matched [wildcard]
Sep 13 23:12:15 NewOne thermald[657]: XML zone: invalid sensor type TSKN
Sep 13 23:12:15 NewOne thermald[657]: Zone update failed: unable to bind
Sep 13 23:12:15 NewOne thermald[657]: cthd_cpu_default_binding::do_default_binding: No relavent cpu cdevs
Sep 13 23:12:15 NewOne thermald[657]: Zone 0: acpitz, Active:0 Bind:0 Sensor_cnt:1
Sep 13 23:12:15 NewOne thermald[657]: ..sensors..
Sep 13 23:12:15 NewOne thermald[657]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Sep 13 23:12:15 NewOne thermald[657]: ..trips..
Sep 13 23:12:15 NewOne thermald[657]: index 0: type:critical temp:127000 hyst:1 zone id:0 sensor id:0 cdev size:0
Sep 13 23:12:15 NewOne thermald[657]: index 1: type:polling temp:122000 hyst:0 zone id:0 sensor id:0 cdev size:0
Sep 13 23:12:15 NewOne systemd[1]: Started Login Service.
Sep 13 23:12:15 NewOne systemd[1]: Starting Authenticate and Authorize Users to Run Privileged Tasks...
Sep 13 23:12:15 NewOne systemd[1]: Started Make remote CUPS printers available locally.
Sep 13 23:12:15 NewOne systemd[1]: Starting Make remote CUPS printers available locally...
Sep 13 23:12:15 NewOne ntpdate[744]: name server cannot be used: Temporary failure in name resolution (-3)
Sep 13 23:12:15 NewOne avahi-daemon[679]: Network interface enumeration completed.
Sep 13 23:12:15 NewOne avahi-daemon[679]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep 13 23:12:15 NewOne avahi-daemon[679]: Server startup complete. Host name is NewOne.local. Local service cookie is 533882672.
Sep 13 23:12:15 NewOne thermald[657]: FD = 8
Sep 13 23:12:15 NewOne thermald[657]: Current user preference is 0
Sep 13 23:12:15 NewOne thermald[657]: thd_engine_thread begin
Sep 13 23:12:15 NewOne polkitd[745]: started daemon version 0.105 using authority implementation `local' version `0.105'
Sep 13 23:12:15 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Sep 13 23:12:15 NewOne whoopsie[652]: [23:12:15] Using lock path: /var/lock/whoopsie/lock
Sep 13 23:12:15 NewOne cups-browsed[746]: (process:746): GLib-CRITICAL **: Source ID 4294967295 was not found when attempting to remove it
Sep 13 23:12:15 NewOne systemd[1]: Started Authenticate and Authorize Users to Run Privileged Tasks.
Sep 13 23:12:15 NewOne kernel: [   13.110027] cfg80211: Calling CRDA to update world regulatory domain
Sep 13 23:12:15 NewOne accounts-daemon[694]: started daemon version 0.6.37
Sep 13 23:12:15 NewOne systemd[1]: Started Accounts Service.
Sep 13 23:12:15 NewOne systemd[1]: Started Modem Manager.
Sep 13 23:12:15 NewOne kernel: [   13.112980] cfg80211: World regulatory domain updated:
Sep 13 23:12:15 NewOne kernel: [   13.112984] cfg80211:  DFS Master region: unset
Sep 13 23:12:15 NewOne kernel: [   13.112986] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Sep 13 23:12:15 NewOne kernel: [   13.112988] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Sep 13 23:12:15 NewOne kernel: [   13.112991] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Sep 13 23:12:15 NewOne kernel: [   13.112993] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Sep 13 23:12:15 NewOne kernel: [   13.112995] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Sep 13 23:12:15 NewOne kernel: [   13.112997] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Sep 13 23:12:15 NewOne kernel: [   13.112999] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Sep 13 23:12:15 NewOne kernel: [   13.113001] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Sep 13 23:12:15 NewOne kernel: [   13.113003] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Sep 13 23:12:15 NewOne whoopsie[652]: [23:12:15] Could not get the Network Manager state:
Sep 13 23:12:15 NewOne whoopsie[652]: [23:12:15] GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> DNS: loaded plugin dnsmasq
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> init!
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> update_system_hostname
Sep 13 23:12:15 NewOne NetworkManager[667]: <info>       interface-parser: parsing file /etc/network/interfaces
Sep 13 23:12:15 NewOne NetworkManager[667]: <info>       interface-parser: finished parsing file /etc/network/interfaces
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> management mode: unmanaged
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0/net/eth0, iface: eth0)
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> device added (path: /sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> end _init.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Loaded plugin keyfile: (c) 2007 - 2013 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> SCPlugin-Ofono: init!
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> SCPlugin-Ofono: end _init.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Loaded plugin ofono: (C) 2013 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (11305120) ... get_connections.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (11305120) ... get_connections (managed=false): return empty list.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> SCPlugin-Ofono: (11122192) ... get_connections.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> SCPlugin-Ofono: (11122192) connections count: 0
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> get unmanaged devices count: 0
Sep 13 23:12:15 NewOne NetworkManager[667]: (NetworkManager:667): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> monitoring ifupdown state file '/run/network/ifstate'.
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> Networking is enabled by state file
Sep 13 23:12:15 NewOne systemd[1]: Started Network Manager.
Sep 13 23:12:15 NewOne systemd[1]: Starting Network Manager Wait Online...
Sep 13 23:12:15 NewOne systemd[1]: Reached target Network.
Sep 13 23:12:15 NewOne systemd[1]: Starting Network.
Sep 13 23:12:15 NewOne systemd[1]: Starting /etc/rc.local Compatibility...
Sep 13 23:12:15 NewOne systemd[1]: Started /etc/rc.local Compatibility.
Sep 13 23:12:15 NewOne systemd[1]: Starting Wait for Plymouth Boot Screen to Quit...
Sep 13 23:12:15 NewOne systemd[1]: Started Wait for Plymouth Boot Screen to Quit.
Sep 13 23:12:15 NewOne systemd[1]: Started Getty on tty1.
Sep 13 23:12:15 NewOne systemd[1]: Starting Getty on tty1...
Sep 13 23:12:15 NewOne systemd[1]: Reached target Login Prompts.
Sep 13 23:12:15 NewOne systemd[1]: Starting Login Prompts.
Sep 13 23:12:15 NewOne NetworkManager[667]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (lo): link connected
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (lo): carrier is ON
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (lo): new Generic device (driver: 'unknown' ifindex: 1)
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (lo): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 13 23:12:15 NewOne NetworkManager[667]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (eth0): carrier is OFF
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (eth0): preparing device
Sep 13 23:12:15 NewOne kernel: [   13.380294] r8169 0000:03:00.0 eth0: link down
Sep 13 23:12:15 NewOne kernel: [   13.380314] r8169 0000:03:00.0 eth0: link down
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> (eth0): created default wired connection 'Wired connection 1'
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> urfkill disappeared from the bus
Sep 13 23:12:15 NewOne NetworkManager[667]: <info> ModemManager available in the bus
Sep 13 23:12:15 NewOne gpu-manager[688]: message repeated 3 times: [ /etc/modprobe.d is not a file]
Sep 13 23:12:15 NewOne gpu-manager[688]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Sep 13 23:12:15 NewOne systemd[1]: Started Detect the available GPUs and deal with any system changes.
Sep 13 23:12:15 NewOne systemd[1]: Starting Light Display Manager...
Sep 13 23:12:15 NewOne systemd[1]: Started Light Display Manager.
Sep 13 23:12:16 NewOne systemd[1]: Created slice user-1000.slice.
Sep 13 23:12:16 NewOne systemd[1]: Starting user-1000.slice.
Sep 13 23:12:16 NewOne systemd[1]: Starting User Manager for UID 1000...
Sep 13 23:12:16 NewOne systemd[1]: Started Session c1 of user alejandro.
Sep 13 23:12:16 NewOne systemd[1]: Starting Session c1 of user alejandro.
Sep 13 23:12:16 NewOne systemd[827]: Reached target Timers.
Sep 13 23:12:16 NewOne systemd[827]: Starting Timers.
Sep 13 23:12:16 NewOne systemd[827]: Reached target Sockets.
Sep 13 23:12:16 NewOne systemd[827]: Starting Sockets.
Sep 13 23:12:16 NewOne systemd[827]: Reached target Paths.
Sep 13 23:12:16 NewOne systemd[827]: Starting Paths.
Sep 13 23:12:16 NewOne systemd[827]: Reached target Basic System.
Sep 13 23:12:16 NewOne systemd[827]: Starting Basic System.
Sep 13 23:12:16 NewOne systemd[827]: Reached target Default.
Sep 13 23:12:16 NewOne systemd[827]: Startup finished in 43ms.
Sep 13 23:12:16 NewOne systemd[827]: Starting Default.
Sep 13 23:12:16 NewOne systemd[1]: Started User Manager for UID 1000.
Sep 13 23:12:17 NewOne ModemManager[674]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:15.1/0000:03:00.0': not supported by any plugin
Sep 13 23:12:17 NewOne org.a11y.Bus[914]: Activating service name='org.a11y.atspi.Registry'
Sep 13 23:12:17 NewOne org.a11y.Bus[914]: Successfully activated service 'org.a11y.atspi.Registry'
Sep 13 23:12:17 NewOne org.a11y.atspi.Registry[989]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Sep 13 23:12:18 NewOne dbus[715]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service'
Sep 13 23:12:18 NewOne systemd[1]: Starting Daemon for power management...
Sep 13 23:12:18 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.UPower'
Sep 13 23:12:18 NewOne systemd[1]: Started Daemon for power management.
Sep 13 23:12:18 NewOne gnome-session[1016]: GPG_AGENT_INFO=/run/user/1000/keyring/gpg:0:1
Sep 13 23:12:18 NewOne gnome-session[1016]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Sep 13 23:12:18 NewOne gnome-session[1016]: GPG_AGENT_INFO=/run/user/1000/keyring/gpg:0:1
Sep 13 23:12:18 NewOne gnome-session[1016]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Sep 13 23:12:18 NewOne gnome-session[1016]: GPG_AGENT_INFO=/run/user/1000/keyring/gpg:0:1
Sep 13 23:12:18 NewOne gnome-session[1016]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Sep 13 23:12:18 NewOne gnome-session[1016]: GPG_AGENT_INFO=/run/user/1000/keyring/gpg:0:1
Sep 13 23:12:18 NewOne gnome-session[1016]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Sep 13 23:12:18 NewOne dbus[715]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service'
Sep 13 23:12:18 NewOne systemd[1]: Starting RealtimeKit Scheduling Policy Service...
Sep 13 23:12:18 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Sep 13 23:12:18 NewOne systemd[1]: Started RealtimeKit Scheduling Policy Service.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully called chroot.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully dropped privileges.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully limited resources.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Running.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Watchdog thread running.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Canary thread running.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully made thread 1194 of process 1194 (n/a) owned by '1000' high priority at nice level -11.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 1 threads of 1 processes of 1 users.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 1 threads of 1 processes of 1 users.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully made thread 1215 of process 1194 (n/a) owned by '1000' RT at priority 5.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 2 threads of 1 processes of 1 users.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 2 threads of 1 processes of 1 users.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully made thread 1225 of process 1194 (n/a) owned by '1000' RT at priority 5.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 3 threads of 1 processes of 1 users.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 3 threads of 1 processes of 1 users.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully made thread 1226 of process 1194 (n/a) owned by '1000' RT at priority 5.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 4 threads of 1 processes of 1 users.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Successfully made thread 1228 of process 1228 (n/a) owned by '1000' high priority at nice level -11.
Sep 13 23:12:18 NewOne rtkit-daemon[1195]: Supervising 5 threads of 2 processes of 1 users.
Sep 13 23:12:18 NewOne pulseaudio[1228]: [pulseaudio] pid.c: Daemon already running.
Sep 13 23:12:18 NewOne dbus[715]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service'
Sep 13 23:12:18 NewOne systemd[1]: Starting Manage, Install and Generate Color Profiles...
Sep 13 23:12:18 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Sep 13 23:12:18 NewOne systemd[1]: Started Manage, Install and Generate Color Profiles.
Sep 13 23:12:18 NewOne dbus[715]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Sep 13 23:12:18 NewOne systemd[1]: Starting Locale Service...
Sep 13 23:12:18 NewOne gnome-session[1016]: (process:1252): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Sep 13 23:12:18 NewOne gnome-session[1016]: (process:1252): indicator-application-service-WARNING **: Name Lost
Sep 13 23:12:18 NewOne gnome-session[1016]: Entering running state
Sep 13 23:12:18 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.locale1'
Sep 13 23:12:18 NewOne systemd[1]: Started Locale Service.
Sep 13 23:12:19 NewOne kernel: [   16.993177] r8169 0000:03:00.0 eth0: link up
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> (eth0): link connected
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Auto-activating connection 'Wired connection 1'.
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) starting connection 'Wired connection 1'
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> NetworkManager state is now CONNECTING
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 13 23:12:19 NewOne whoopsie[652]: [23:12:19] offline
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> dhclient started with pid 1269
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 13 23:12:19 NewOne NetworkManager[667]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep 13 23:12:19 NewOne dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x34221f4b)
Sep 13 23:12:19 NewOne dbus[715]: [system] Activating via systemd: service name='org.freedesktop.UDisks2' unit='udisks2.service'
Sep 13 23:12:19 NewOne systemd[1]: Starting Disk Manager...
Sep 13 23:12:19 NewOne udisksd[1280]: udisks daemon version 2.1.5 starting
Sep 13 23:12:19 NewOne dhclient: DHCPREQUEST of 192.168.0.19 on eth0 to 255.255.255.255 port 67 (xid=0x4b1f2234)
Sep 13 23:12:19 NewOne dhclient: DHCPOFFER of 192.168.0.19 from 192.168.0.1
Sep 13 23:12:19 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Sep 13 23:12:19 NewOne udisksd[1280]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Sep 13 23:12:19 NewOne systemd[1]: Started Disk Manager.
Sep 13 23:12:19 NewOne org.gtk.Private.AfcVolumeMonitor[914]: Volume monitor alive
Sep 13 23:12:20 NewOne org.gnome.ScreenSaver[914]: ** Message: Lost the name, shutting down.
Sep 13 23:12:20 NewOne dhclient: DHCPACK of 192.168.0.19 from 192.168.0.1
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   address 192.168.0.19
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   plen 24 (255.255.255.0)
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   gateway 192.168.0.1
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   server identifier 192.168.0.1
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   lease time 86400
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   nameserver '68.105.28.11'
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   nameserver '68.105.29.11'
Sep 13 23:12:20 NewOne NetworkManager[667]: <info>   nameserver '68.105.28.12'
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep 13 23:12:20 NewOne avahi-daemon[679]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.19.
Sep 13 23:12:20 NewOne avahi-daemon[679]: New relevant interface eth0.IPv4 for mDNS.
Sep 13 23:12:20 NewOne avahi-daemon[679]: Registering new address record for 192.168.0.19 on eth0.IPv4.
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> (eth0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> (eth0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> NetworkManager state is now CONNECTED_LOCAL
Sep 13 23:12:20 NewOne dhclient: bound to 192.168.0.19 -- renewal in 39686 seconds.
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> DNS: starting dnsmasq...
Sep 13 23:12:20 NewOne NetworkManager[667]: <warn> dnsmasq not available on the bus, can't update servers.
Sep 13 23:12:20 NewOne NetworkManager[667]: <error> [1442211140.338037] [dns-manager/nm-dns-dnsmasq.c:398] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Sep 13 23:12:20 NewOne NetworkManager[667]: <warn> DNS: plugin dnsmasq update failed
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> Writing DNS information to /sbin/resolvconf
Sep 13 23:12:20 NewOne whoopsie[652]: [23:12:20] Cannot reach: https://daisy.ubuntu.com
Sep 13 23:12:20 NewOne dnsmasq[1335]: started, version 2.72 cache disabled
Sep 13 23:12:20 NewOne dnsmasq[1335]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect
Sep 13 23:12:20 NewOne dnsmasq[1335]: DBus support enabled: connected to system bus
Sep 13 23:12:20 NewOne dnsmasq[1335]: warning: no upstream servers configured
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> Activation (eth0) successful, device activated.
Sep 13 23:12:20 NewOne dbus[715]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Sep 13 23:12:20 NewOne NetworkManager[667]: <warn> dnsmasq appeared on DBus: :1.54
Sep 13 23:12:20 NewOne systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep 13 23:12:20 NewOne NetworkManager[667]: <info> Writing DNS information to /sbin/resolvconf
Sep 13 23:12:20 NewOne dnsmasq[1335]: setting upstream servers from DBus
Sep 13 23:12:20 NewOne dnsmasq[1335]: using nameserver 68.105.28.11#53
Sep 13 23:12:20 NewOne dnsmasq[1335]: using nameserver 68.105.29.11#53
Sep 13 23:12:20 NewOne dnsmasq[1335]: using nameserver 68.105.28.12#53
Sep 13 23:12:20 NewOne dbus[715]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 13 23:12:20 NewOne systemd[1]: Started Network Manager Script Dispatcher Service.
Sep 13 23:12:20 NewOne nm-dispatcher: Dispatching action 'up' for eth0
Sep 13 23:12:20 NewOne whoopsie[652]: [23:12:20] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Sep 13 23:12:20 NewOne whoopsie[652]: [23:12:20] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Sep 13 23:12:20 NewOne whoopsie[652]: [23:12:20] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Sep 13 23:12:20 NewOne whoopsie[652]: [23:12:20] online
Sep 13 23:12:20 NewOne avahi-daemon[679]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::ba97:5aff:feae:70b4.
Sep 13 23:12:20 NewOne avahi-daemon[679]: New relevant interface eth0.IPv6 for mDNS.
Sep 13 23:12:20 NewOne avahi-daemon[679]: Registering new address record for fe80::ba97:5aff:feae:70b4 on eth0.*.
Sep 13 23:12:24 NewOne NetworkManager[667]: <info> startup complete
Sep 13 23:12:24 NewOne systemd[1]: Started Network Manager Wait Online.
Sep 13 23:12:24 NewOne systemd[1]: Reached target Network is Online.
Sep 13 23:12:24 NewOne systemd[1]: Starting Network is Online.
Sep 13 23:12:24 NewOne systemd[1]: Starting LSB: Cleans up any mess left by 0dns-up...
Sep 13 23:12:24 NewOne systemd[1]: Starting LSB: Tool to automatically collect and submit kernel crash signatures...
Sep 13 23:12:24 NewOne dns-clean[1531]: * Restoring resolver state...
Sep 13 23:12:24 NewOne dns-clean[1531]: ...done.
Sep 13 23:12:24 NewOne systemd[1]: Started LSB: Cleans up any mess left by 0dns-up.
Sep 13 23:12:24 NewOne systemd[1]: Started LSB: Tool to automatically collect and submit kernel crash signatures.
Sep 13 23:12:24 NewOne systemd[1]: Reached target Multi-User System.
Sep 13 23:12:24 NewOne systemd[1]: Starting Multi-User System.
Sep 13 23:12:24 NewOne systemd[1]: Reached target Graphical Interface.
Sep 13 23:12:24 NewOne systemd[1]: Starting Graphical Interface.
Sep 13 23:12:24 NewOne systemd[1]: Starting Update UTMP about System Runlevel Changes...
Sep 13 23:12:24 NewOne systemd[1]: Started Stop ureadahead data collection 45s after completed startup.
Sep 13 23:12:24 NewOne systemd[1]: Starting Stop ureadahead data collection 45s after completed startup.
Sep 13 23:12:24 NewOne systemd[1]: Started Update UTMP about System Runlevel Changes.
Sep 13 23:12:24 NewOne systemd[1]: Startup finished in 2.447s (kernel) + 19.584s (userspace) = 22.031s.
Sep 13 23:12:25 NewOne NetworkManager[667]: <info> WiFi hardware radio set enabled
Sep 13 23:12:25 NewOne NetworkManager[667]: <info> WWAN hardware radio set enabled
Sep 13 23:12:26 NewOne ntpdate[1509]: adjust time server 91.189.94.4 offset 0.246605 sec
Sep 13 23:12:29 NewOne gnome-session[1016]: (nm-applet:1248): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
Sep 13 23:12:39 NewOne org.gnome.zeitgeist.Engine[914]: ** (zeitgeist-datahub:1632): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Sep 13 23:13:09 NewOne systemd[1]: Starting Stop ureadahead data collection...
Sep 13 23:13:09 NewOne systemd[1]: Stopped Read required files in advance.
Sep 13 23:13:09 NewOne systemd[1]: Started Stop ureadahead data collection.

```

---

### Post by ian-weisser on 2015-09-14
Not seeing any useful log entries.
Chrome seems to crash rather often, but you knew that already.

---

### Post by bobnn on 2015-09-14
Have you tired SSH'ing into the system from another machine?

My system started doing this, if I SSH in and reset the USB ports, it starts working again from the mouse and keyboard.

Resetting the USB ports is accomplished on my 14.04 system using this script, which I got from the Intarwebz somewhere:

```
#!/bin/sh

SYSXHCI=/sys/bus/pci/drivers/ehci-pci

if [ "$(id -u)" != 0 ] ; then
 echo This must be run as root!
 exit 1
fi

if ! cd $SYSXHCI ; then
 echo Weird error. Failed to change directory to $SYSXHCI
 exit 1
fi

for dev_id in ????:??:??.? ; do
 echo "\$dev_id = $dev_id"
 printf "${dev_id}" > unbind
 printf "${dev_id}" > bind
done

```

I'm thinking I need a new mouse, or keyboard, or new USB ports.

---

### Post by amloren1 on 2015-09-14
I'm not familiar with SSH right now. However, the keyboard does seem to sometimes work on crash. I think this is an issue not explicitly related to the usb ports though. 

Yes, chrome produced a crash report on just one of the crashes so far. I think I just happen to usually be in chrome upon failure. So I used firefox instead and the crashes were just as well.

---

### Post by bobnn on 2015-09-15
yeah if the keyboard still works, that's different from what I'm seeing.

---

### Post by amloren1 on 2015-09-17
bump

---

### Post by Geoffrey_Arndt on 2015-09-17
Perhaps a vanilla install on the SSD is worth a shot (can always setup data drive on hdd).  Two partitions (swap and all-else) to keep everything simple.    I would suggest either 15.04 or 15.10 (leaning toward the latter).   Then, do the usual tweaks and updates especially nividia driver install.    Using this basic setup may make it easier to ID other issues.

---

### Post by amloren1 on 2015-09-17
Yeah I was thinking this. Though I've been so frustrated that I was leaning towards a new mobo. But Ill go ahead and follow through your suggestion. Might be a couple days til I get back. Will be out of town. Thanks

---

### Post by amloren1 on 2015-09-22
Well I've had it running on 15.04 for a few days now without any freezing issues. It's a bit gritty though. Maybe because I havent yet setup the proprietary amd drivers.

---

### Post by amloren1 on 2015-09-27
The freezing continues. Tried an install of 14.04 on just the SSD, then just the HDD. No luck. Freezing all around.

---

### Post by amloren1 on 2015-09-27
bump

---

### Post by ian-weisser on 2015-09-27
Awaiting your complete results from Post #14. "Here's what I would try next...."

---

