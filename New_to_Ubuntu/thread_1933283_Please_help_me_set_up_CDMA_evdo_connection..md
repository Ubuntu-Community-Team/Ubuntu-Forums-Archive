---
title: "Please help me set up CDMA evdo connection."
date: 2012-02-29
forum: New to Ubuntu
---

### Post by DisappearingOak on 2012-02-29
Hi, I've always wanted to run Ubuntu but it refused to run on my intel 845 system; so now that I've finally built a new system, I'm excited about using the OS. I installed Ubuntu 11.10, and love the new gui, especially the dash; it's great.

But I'm having trouble setting up my internet connection with a CDMA evdo modem. My modem is detected as a 'cdc modem', and after setting up the user name and password, it doesn't connect but I get Modem disconnected - You are now offline message. I tried running Sakis3g, a script I found on the internet, but it gives the error 'Modem responded "Error" while checking for pin'. This modem and connection works fine on Windows 7. Please help me.

Also, I want to enable Bluetooth, and when I plug in my Bluetooth dongle, I get the Bluetooth icon in the taskbar, and it shows that it is enabled but the menu doesn't have any options to pair devices. When I click on Preferences the dialog says Bluetooth is disabled! When I click the On button, nothing happens, and the dialog still shows disabled! How do I get it to run. Please help a newbie, thanks.

System specs are - Gigabyte 880gm-d2h, AMD PhenomII 965be, 4gb ram, if it matters.

---

### Post by Lisiano on 2012-02-29
I don't know how to solve this but please provide some info for people that can, specifically, open a terminal (Ctrl+Alt+T) then type these after a little while when both devices were connected.
```
lsusb
```
```
rfkill list
```
```
dmesg | tail -n 100
```
Please use the code tags (# button) for the output you get.

---

### Post by DisappearingOak on 2012-02-29
after plugging in evdo modem:
```

oak@Oak:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04ca:0022 Lite-On Technology Corp. 
Bus 003 Device 003: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 005 Device 004: ID 15eb:1231  
oak@Oak:~$ rfkill list
oak@Oak:~$ dmesg | tail -n 100
[   15.430679] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.430680] [drm] Driver supports precise vblank timestamp query.
[   15.430694] [drm] radeon: irq initialized.
[   15.430698] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.431414] [drm] Loading RS780 Microcode
[   15.501755] radeon 0000:01:05.0: WB enabled
[   15.509877] Adding 4550652k swap on /dev/sda3.  Priority:-1 extents:1 across:4550652k 
[   15.532725] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.532781] [drm] ring test succeeded in 1 usecs
[   15.532854] [drm] radeon: ib pool ready.
[   15.532906] [drm] ib test succeeded in 0 usecs
[   15.532916] failed to evaluate ATIF got AE_BAD_PARAMETER
[   15.533079] [drm] Radeon Display Connectors
[   15.533080] [drm] Connector 0:
[   15.533081] [drm]   VGA
[   15.533082] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.533084] [drm]   Encoders:
[   15.533085] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.533086] [drm] Connector 1:
[   15.533086] [drm]   DVI-D
[   15.533087] [drm]   HPD1
[   15.533089] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   15.533090] [drm]   Encoders:
[   15.533091] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[   15.588383] [drm] Radeon display connector VGA-1: Found valid EDID
[   15.609617] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
[   15.609642] [drm] radeon: power management initialized
[   15.677513] [drm] fb mappable at 0xD0141000
[   15.677514] [drm] vram apper at 0xD0000000
[   15.677515] [drm] size 5324800
[   15.677516] [drm] fb depth is 24
[   15.677517] [drm]    pitch is 5888
[   15.677558] fbcon: radeondrmfb (fb0) is primary device
[   15.677645] Console: switching to colour frame buffer device 180x56
[   15.677663] fb0: radeondrmfb frame buffer device
[   15.677664] drm: registered panic notifier
[   15.677670] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[   15.677978] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.678007] HDA Intel 0000:01:05.1: setting latency timer to 64
[   16.003312] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.544619] ppdev: user-space parallel port driver
[   16.549908] type=1400 audit(1330519821.537:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=895 comm="apparmor_parser"
[   16.550260] type=1400 audit(1330519821.537:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=895 comm="apparmor_parser"
[   16.735229] type=1400 audit(1330519821.721:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=915 comm="apparmor_parser"
[   16.735465] type=1400 audit(1330519821.721:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=916 comm="apparmor_parser"
[   16.735804] type=1400 audit(1330519821.721:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=916 comm="apparmor_parser"
[   16.736014] type=1400 audit(1330519821.725:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=916 comm="apparmor_parser"
[   16.736281] type=1400 audit(1330519821.725:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=919 comm="apparmor_parser"
[   16.856877] r8169 0000:02:00.0: eth0: link down
[   16.857240] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.869497] init: failsafe main process (838) killed by TERM signal
[   16.869735] init: apport pre-start process (953) terminated with status 1
[   16.875589] init: apport post-stop process (978) terminated with status 1
[   17.077642] Bluetooth: Core ver 2.16
[   17.077662] NET: Registered protocol family 31
[   17.077663] Bluetooth: HCI device and connection manager initialized
[   17.077664] Bluetooth: HCI socket layer initialized
[   17.077665] Bluetooth: L2CAP socket layer initialized
[   17.077699] Bluetooth: SCO socket layer initialized
[   17.078906] Bluetooth: RFCOMM TTY layer initialized
[   17.078909] Bluetooth: RFCOMM socket layer initialized
[   17.078910] Bluetooth: RFCOMM ver 1.11
[   17.097225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.097227] Bluetooth: BNEP filters: protocol multicast
[   17.170621] radeon 0000:01:05.0: texture bo too small (1440 900 26 0 -> 5322752 have 5300224)
[   17.170625] radeon 0000:01:05.0: alignments 1472 64 8 256
[   17.170627] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[   21.848577] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   22.189413] init: plymouth-stop pre-start process (1405) terminated with status 1
[   58.832059] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   58.832063] ata4.00: failed command: SMART
[   58.832066] ata4.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
[   58.832067]          res 40/00:00:00:00:00/00:01:00:00:00/00 Emask 0x4 (timeout)
[   58.832069] ata4.00: status: { DRDY }
[   58.832072] ata4: hard resetting link
[   59.324063] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   59.328096] ata4.00: configured for UDMA/100
[   59.344064] ata4: EH complete
[  130.440106] usb 5-3: new full speed USB device number 2 using ohci_hcd
[  130.964086] usbcore: registered new interface driver uas
[  130.974659] Initializing USB Mass Storage driver...
[  130.974952] scsi6 : usb-storage 5-3:1.0
[  130.975181] usbcore: registered new interface driver usb-storage
[  130.975187] USB Mass Storage support registered.
[  131.975561] usb 5-3: USB disconnect, device number 2
[  132.724084] usb 5-3: new full speed USB device number 3 using ohci_hcd
[  136.412422] usb 5-3: USB disconnect, device number 3
[  138.444105] usb 5-3: new full speed USB device number 4 using ohci_hcd
[  138.623429] scsi7 : usb-storage 5-3:1.2
[  138.935994] cdc_acm 5-3:1.0: This device cannot do calls on its own. It is not a modem.
[  138.936112] cdc_acm 5-3:1.0: ttyACM0: USB ACM device
[  138.939371] usbcore: registered new interface driver cdc_acm
[  138.939377] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[  139.625232] scsi 7:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
[  139.629226] scsi 7:0:0:1: Direct-Access     BSNL     Mass Storage SD  7.00 PQ: 0 ANSI: 0 CCS
[  139.826218] sr1: scsi-1 drive
[  139.826492] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  139.826739] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  139.827208] sd 7:0:0:1: Attached scsi generic sg3 type 0
[  139.906225] sd 7:0:0:1: [sdb] Attached SCSI removable disk

```
after plugging in bluetooth dongle:
```

oak@Oak:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04ca:0022 Lite-On Technology Corp. 
Bus 003 Device 003: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 005 Device 004: ID 15eb:1231  
Bus 006 Device 002: ID 0c10:0000  
oak@Oak:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
oak@Oak:~$ dmesg | tail -n 100
[   15.430698] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.431414] [drm] Loading RS780 Microcode
[   15.501755] radeon 0000:01:05.0: WB enabled
[   15.509877] Adding 4550652k swap on /dev/sda3.  Priority:-1 extents:1 across:4550652k 
[   15.532725] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.532781] [drm] ring test succeeded in 1 usecs
[   15.532854] [drm] radeon: ib pool ready.
[   15.532906] [drm] ib test succeeded in 0 usecs
[   15.532916] failed to evaluate ATIF got AE_BAD_PARAMETER
[   15.533079] [drm] Radeon Display Connectors
[   15.533080] [drm] Connector 0:
[   15.533081] [drm]   VGA
[   15.533082] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.533084] [drm]   Encoders:
[   15.533085] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.533086] [drm] Connector 1:
[   15.533086] [drm]   DVI-D
[   15.533087] [drm]   HPD1
[   15.533089] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   15.533090] [drm]   Encoders:
[   15.533091] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[   15.588383] [drm] Radeon display connector VGA-1: Found valid EDID
[   15.609617] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
[   15.609642] [drm] radeon: power management initialized
[   15.677513] [drm] fb mappable at 0xD0141000
[   15.677514] [drm] vram apper at 0xD0000000
[   15.677515] [drm] size 5324800
[   15.677516] [drm] fb depth is 24
[   15.677517] [drm]    pitch is 5888
[   15.677558] fbcon: radeondrmfb (fb0) is primary device
[   15.677645] Console: switching to colour frame buffer device 180x56
[   15.677663] fb0: radeondrmfb frame buffer device
[   15.677664] drm: registered panic notifier
[   15.677670] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[   15.677978] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.678007] HDA Intel 0000:01:05.1: setting latency timer to 64
[   16.003312] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.544619] ppdev: user-space parallel port driver
[   16.549908] type=1400 audit(1330519821.537:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=895 comm="apparmor_parser"
[   16.550260] type=1400 audit(1330519821.537:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=895 comm="apparmor_parser"
[   16.735229] type=1400 audit(1330519821.721:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=915 comm="apparmor_parser"
[   16.735465] type=1400 audit(1330519821.721:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=916 comm="apparmor_parser"
[   16.735804] type=1400 audit(1330519821.721:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=916 comm="apparmor_parser"
[   16.736014] type=1400 audit(1330519821.725:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=916 comm="apparmor_parser"
[   16.736281] type=1400 audit(1330519821.725:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=919 comm="apparmor_parser"
[   16.856877] r8169 0000:02:00.0: eth0: link down
[   16.857240] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.869497] init: failsafe main process (838) killed by TERM signal
[   16.869735] init: apport pre-start process (953) terminated with status 1
[   16.875589] init: apport post-stop process (978) terminated with status 1
[   17.077642] Bluetooth: Core ver 2.16
[   17.077662] NET: Registered protocol family 31
[   17.077663] Bluetooth: HCI device and connection manager initialized
[   17.077664] Bluetooth: HCI socket layer initialized
[   17.077665] Bluetooth: L2CAP socket layer initialized
[   17.077699] Bluetooth: SCO socket layer initialized
[   17.078906] Bluetooth: RFCOMM TTY layer initialized
[   17.078909] Bluetooth: RFCOMM socket layer initialized
[   17.078910] Bluetooth: RFCOMM ver 1.11
[   17.097225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.097227] Bluetooth: BNEP filters: protocol multicast
[   17.170621] radeon 0000:01:05.0: texture bo too small (1440 900 26 0 -> 5322752 have 5300224)
[   17.170625] radeon 0000:01:05.0: alignments 1472 64 8 256
[   17.170627] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[   21.848577] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   22.189413] init: plymouth-stop pre-start process (1405) terminated with status 1
[   58.832059] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   58.832063] ata4.00: failed command: SMART
[   58.832066] ata4.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
[   58.832067]          res 40/00:00:00:00:00/00:01:00:00:00/00 Emask 0x4 (timeout)
[   58.832069] ata4.00: status: { DRDY }
[   58.832072] ata4: hard resetting link
[   59.324063] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   59.328096] ata4.00: configured for UDMA/100
[   59.344064] ata4: EH complete
[  130.440106] usb 5-3: new full speed USB device number 2 using ohci_hcd
[  130.964086] usbcore: registered new interface driver uas
[  130.974659] Initializing USB Mass Storage driver...
[  130.974952] scsi6 : usb-storage 5-3:1.0
[  130.975181] usbcore: registered new interface driver usb-storage
[  130.975187] USB Mass Storage support registered.
[  131.975561] usb 5-3: USB disconnect, device number 2
[  132.724084] usb 5-3: new full speed USB device number 3 using ohci_hcd
[  136.412422] usb 5-3: USB disconnect, device number 3
[  138.444105] usb 5-3: new full speed USB device number 4 using ohci_hcd
[  138.623429] scsi7 : usb-storage 5-3:1.2
[  138.935994] cdc_acm 5-3:1.0: This device cannot do calls on its own. It is not a modem.
[  138.936112] cdc_acm 5-3:1.0: ttyACM0: USB ACM device
[  138.939371] usbcore: registered new interface driver cdc_acm
[  138.939377] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[  139.625232] scsi 7:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
[  139.629226] scsi 7:0:0:1: Direct-Access     BSNL     Mass Storage SD  7.00 PQ: 0 ANSI: 0 CCS
[  139.826218] sr1: scsi-1 drive
[  139.826492] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  139.826739] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  139.827208] sd 7:0:0:1: Attached scsi generic sg3 type 0
[  139.906225] sd 7:0:0:1: [sdb] Attached SCSI removable disk
[  312.388103] usb 6-2: new full speed USB device number 2 using ohci_hcd
[  312.618880] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  312.619275] usbcore: registered new interface driver btusb
oak@Oak:~$ 

```

---

### Post by DisappearingOak on 2012-03-01
Does anyone know how to fix this? Because EVDO is the only broadband connection I have. :(

---

### Post by Lisiano on 2012-03-01
While it seems both devices get connected to your PC, I don't like the fact they don't identify themselves with some sort of name```
Bus 005 Device 004: ID 15eb:1231  
Bus 006 Device 002: ID 0c10:0000  
```

Anyway, I looked around for your modem and it seems that using something called "wvdial" will help.
Here is a link on how to set it up
[http://www.binbert.com/blog/2011/07/configure-a-gprs-dialer-in-linux-using-wvdial-gnome-ppp/](http://www.binbert.com/blog/2011/07/configure-a-gprs-dialer-in-linux-using-wvdial-gnome-ppp/)

As for the Bluetooth part, to me it seems fine, though honestly I never dealt with Bluetooth in Linux, only a single time in OS X to transfer a file and Windows XP to play music on my Nokia 5300. Though it says that neither hardware (A button/switch) nor software (Enable/Disable in a menu) is blocking Bluetooth.

Googling for the device resulted that restarting the Bluetooth service on the PC might help, to do that, first plug in the dongle then open a terminal and type the following
```
sudo service bluetooth restart
```
It will ask you for your password, type it, note that it won't display any kind of visual feedback, even dots or asterisks, when you finish typing, just hit enter.
You should get this if the restart goes okay
```
oak@0ak:~$ sudo service bluetooth restart
[sudo] password for oak: 
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
oak@0ak:~$ 
```

---

### Post by DisappearingOak on 2012-03-02
Okay, I installed wvdial along with it's dependencies manually through the terminal. Then, I ran wvdial but it spewed out a lot of garbage saying 'carrier detected -- signal lost' and hundreds of symbols. But after editing wvdial.conf to exactly this, I got it running: 
```


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
Modem = /dev/ttyACM0
ISDN = 0
Phone = #777
Password = 91xxxxxxxx
Username = 91xxxxxxxx
Stupid Mode = 1

```

and now I can use the internet. Now I need to know how do I create an icon on my desktop which will run the 'sudo wvdial' command when I want to connect and how to get the terminal window to not show up.

---

### Post by Lisiano on 2012-03-02
Open a terminial once again and create a file with any name, ending in .desktop, for example: wvdial.desktop
```
gedit ~/Desktop/wvdial.desktop
```
Now paste the following into it
```
[Desktop Entry]
Name=wvdial
Exec='gksudo wvdial'
Type=Application
StartupNotify=false
Icon=package_network
```
Now just save it and a icon with a globe should appear on your desktop, double clicking it will open a password prompt, after you hit enter, the prompt will dissapear and wvdial will start in the background.

---

