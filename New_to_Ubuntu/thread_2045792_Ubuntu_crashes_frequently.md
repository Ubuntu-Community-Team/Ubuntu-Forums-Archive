---
title: "Ubuntu crashes frequently"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by gcy56 on 2012-08-21
I am new to Ubuntu 12.04. I started using it after my computer motherboard had a problem. I am running it off external usb drive.
Worked great for 2 months. I thought I am going to move over permanently to linux from windows.
For the last week- nothing but problems.
The computer keeps freezing up- lot of times after the computergoes to sleep. It is also happening a lot with random computer usage.

I am not sure how to trouble shoot . I have no linux background but can certainly find my way around Ubuntu

Please help. I am this close to buying a win 7 machine

---

### Post by Bucky Ball on 2012-08-21
> **gcy56 said:**
>  I am this close to buying a win 7 machine

Hard to buy a machine that's not 'Win' something unless you build it yourself or buy a Mac (which can also be 'win' or 'linux'). A 'machine' per se, is not actually the operating system, of course. A 'Win' machine is really a PC and can just as easily become a 'Linux' machine, but not a Mac machine and ... I dribble.

Are you sure using the dongle has not killed it? The cheaper, nastier and older they are the more likely they are to fail after fewer read/writes. They do have a limited life and you should expect crash-age, especially if being used a lot. If the dongle has been in the family for decades this is even more likely the cause.

Does it work on other machines? Try that or maybe grab another dongle, if you can, dump Ubuntu on that and see if that works. That will rule out the dongle in any case. ;)

PS: Unless you did a dodgy update or can put your finger on something you've done to cause this, it is very unlikely software. Would be unusual for Linux to randomly self combust.

---

### Post by jualin on 2012-08-21
Hi gcy56,
A good way to start is to look at the kernel log to see what actually happened when your computer crashed. 
Next time that it crashes, restart and check the kern.log inside /var/log/
You can do it using the command line with ```
cat /var/log/kern.log
```
You can also access it graphically using the ["Log File Viewer"]("http://askubuntu.com/questions/15647/where-can-i-find-the-kernel-logs").
You can then post the log here.
Hope this helps!

---

### Post by gcy56 on 2012-08-22
Kernel Log- Not sure this is what you were looking for
```

Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389390] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389392] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389393] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389395] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389397] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389399] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389401] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389403] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389405] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389407] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389408] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389410] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389412] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389414] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389416] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389418] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389419] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389421] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389423] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389425] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389427] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389429] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389431] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389432] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389434] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389436] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389438] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389440] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389442] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389443] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389445] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389447] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389449] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389451] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389453] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389455] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389457] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389458] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389460] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389462] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389464] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389466] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389468] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389469] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389471] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389473] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389475] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389477] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389479] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389481] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389483] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389484] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389486] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389488] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389490] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389492] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389494] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389495] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389497] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389499] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389501] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389503] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389505] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389506] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389508] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.395747] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.399905] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.401149] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.401740] Registered led device: ath9k-phy0
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.401744] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xf9e20000, irq=17
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.433410] init: failsafe main process (1016) killed by TERM signal
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481772] Bluetooth: Core ver 2.16
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481794] NET: Registered protocol family 31
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481796] Bluetooth: HCI device and connection manager initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481798] Bluetooth: HCI socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481800] Bluetooth: L2CAP socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481804] Bluetooth: SCO socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.485592] Bluetooth: RFCOMM TTY layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.485600] Bluetooth: RFCOMM socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.485602] Bluetooth: RFCOMM ver 1.11
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.497555] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.497558] Bluetooth: BNEP filters: protocol multicast
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518083] type=1400 audit(1345599692.480:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1106 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518501] type=1400 audit(1345599692.480:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1106 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518717] type=1400 audit(1345599692.480:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1106 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518974] type=1400 audit(1345599692.480:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1109 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.519002] type=1400 audit(1345599692.480:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1105 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.520960] type=1400 audit(1345599692.484:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1112 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.521194] type=1400 audit(1345599692.484:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=1112 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.547007] ppdev: user-space parallel port driver
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.588013] hda_codec: ALC888: BIOS auto-probing.
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.588017] hda_codec: ALC888: SKU not ready 0x411111f0
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.589369] forcedeth 0000:00:0a.0: irq 40 for MSI/MSI-X
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.589560] forcedeth 0000:00:0a.0: eth0: no link during initialization
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.590133] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.590470] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.631991] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.635032] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.714887] init: alsa-restore main process (1186) terminated with status 19
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.890090] usbcore: registered new interface driver usblp
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974099] vboxdrv: Found 4 processor cores.
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974268] vboxdrv: fAsync=0 offMin=0x498 offMax=0x139a
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974514] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974516] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.981501] vboxpci: IOMMU not found (not registered)
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828096] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input7
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828214] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input8
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828301] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828359] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input10
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828416] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input11
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828473] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input12
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828530] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828591] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input14
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.339762] vesafb: mode is 1024x768x32, linelength=4096, pages=0
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.339765] vesafb: scrolling: redraw
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.339767] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.343294] vesafb: framebuffer at 0xe7000000, mapped to 0xf8c00000, using 3072k, total 3072k
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.343535] Console: switching to colour frame buffer device 128x48
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.343557] fb0: VESA VGA frame buffer device
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.356188] init: plymouth-splash main process (1601) terminated with status 1
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.669081] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.465905] wlan0: authenticate with e8:40:f2:2a:0f:04 (try 1)
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.468047] wlan0: authenticated
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.487094] wlan0: associate with e8:40:f2:2a:0f:04 (try 1)
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.490446] wlan0: RX AssocResp from e8:40:f2:2a:0f:04 (capab=0x431 status=0 aid=5)
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.490449] wlan0: associated
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.497489] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 21 20:41:45 arun40-AY020AA-ABA-p6320f kernel: [   43.747414] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41402 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:41:51 arun40-AY020AA-ABA-p6320f kernel: [   49.508128] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41403 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:41:51 arun40-AY020AA-ABA-p6320f kernel: [   49.776016] wlan0: no IPv6 routers present
Aug 21 20:42:02 arun40-AY020AA-ABA-p6320f kernel: [   61.028496] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41404 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:42:26 arun40-AY020AA-ABA-p6320f kernel: [   84.068603] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41405 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:43:12 arun40-AY020AA-ABA-p6320f kernel: [  130.147590] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41406 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:43:39 arun40-AY020AA-ABA-p6320f kernel: [  157.129892] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:45:45 arun40-AY020AA-ABA-p6320f kernel: [  283.082835] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:47:51 arun40-AY020AA-ABA-p6320f kernel: [  409.146709] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:49:57 arun40-AY020AA-ABA-p6320f kernel: [  535.096219] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:52:03 arun40-AY020AA-ABA-p6320f kernel: [  661.146536] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:54:09 arun40-AY020AA-ABA-p6320f kernel: [  787.098970] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:56:15 arun40-AY020AA-ABA-p6320f kernel: [  913.154152] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:58:21 arun40-AY020AA-ABA-p6320f kernel: [ 1039.108865] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:00:27 arun40-AY020AA-ABA-p6320f kernel: [ 1165.167075] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:04:39 arun40-AY020AA-ABA-p6320f kernel: [ 1417.170381] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:06:45 arun40-AY020AA-ABA-p6320f kernel: [ 1543.124300] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:08:51 arun40-AY020AA-ABA-p6320f kernel: [ 1669.180040] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:10:57 arun40-AY020AA-ABA-p6320f kernel: [ 1795.131442] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:13:03 arun40-AY020AA-ABA-p6320f kernel: [ 1921.186733] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:15:09 arun40-AY020AA-ABA-p6320f kernel: [ 2047.139572] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:17:15 arun40-AY020AA-ABA-p6320f kernel: [ 2173.194832] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:19:21 arun40-AY020AA-ABA-p6320f kernel: [ 2299.147791] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:21:27 arun40-AY020AA-ABA-p6320f kernel: [ 2425.204132] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:23:33 arun40-AY020AA-ABA-p6320f kernel: [ 2551.156615] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:25:39 arun40-AY020AA-ABA-p6320f kernel: [ 2677.218808] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:27:45 arun40-AY020AA-ABA-p6320f kernel: [ 2803.164301] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:29:51 arun40-AY020AA-ABA-p6320f kernel: [ 2929.219432] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:31:57 arun40-AY020AA-ABA-p6320f kernel: [ 3055.172309] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:34:03 arun40-AY020AA-ABA-p6320f kernel: [ 3181.227640] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:38:15 arun40-AY020AA-ABA-p6320f kernel: [ 3433.236823] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:46:39 arun40-AY020AA-ABA-p6320f kernel: [ 3937.257056] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:52:57 arun40-AY020AA-ABA-p6320f kernel: [ 4315.213859] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:55:03 arun40-AY020AA-ABA-p6320f kernel: [ 4441.269308] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:01:21 arun40-AY020AA-ABA-p6320f kernel: [ 4819.230661] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:03:27 arun40-AY020AA-ABA-p6320f kernel: [ 4945.286123] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:05:33 arun40-AY020AA-ABA-p6320f kernel: [ 5071.239220] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:07:39 arun40-AY020AA-ABA-p6320f kernel: [ 5197.294582] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:09:45 arun40-AY020AA-ABA-p6320f kernel: [ 5323.247637] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:11:51 arun40-AY020AA-ABA-p6320f kernel: [ 5449.303091] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:13:57 arun40-AY020AA-ABA-p6320f kernel: [ 5575.256086] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:16:03 arun40-AY020AA-ABA-p6320f kernel: [ 5701.311588] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:18:09 arun40-AY020AA-ABA-p6320f kernel: [ 5827.264625] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:20:15 arun40-AY020AA-ABA-p6320f kernel: [ 5953.320013] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:22:21 arun40-AY020AA-ABA-p6320f kernel: [ 6079.273360] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:24:27 arun40-AY020AA-ABA-p6320f kernel: [ 6205.328571] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:28:39 arun40-AY020AA-ABA-p6320f kernel: [ 6457.338656] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:30:45 arun40-AY020AA-ABA-p6320f kernel: [ 6583.290154] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:32:51 arun40-AY020AA-ABA-p6320f kernel: [ 6709.345625] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:34:57 arun40-AY020AA-ABA-p6320f kernel: [ 6835.298702] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:37:03 arun40-AY020AA-ABA-p6320f kernel: [ 6961.354143] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:39:09 arun40-AY020AA-ABA-p6320f kernel: [ 7087.310646] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:41:15 arun40-AY020AA-ABA-p6320f kernel: [ 7213.362701] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:43:21 arun40-AY020AA-ABA-p6320f kernel: [ 7339.323355] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:45:27 arun40-AY020AA-ABA-p6320f kernel: [ 7465.372757] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:47:33 arun40-AY020AA-ABA-p6320f kernel: [ 7591.324350] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:49:39 arun40-AY020AA-ABA-p6320f kernel: [ 7717.379846] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:51:45 arun40-AY020AA-ABA-p6320f kernel: [ 7843.333219] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:53:51 arun40-AY020AA-ABA-p6320f kernel: [ 7969.388381] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:55:57 arun40-AY020AA-ABA-p6320f kernel: [ 8095.443967] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:58:03 arun40-AY020AA-ABA-p6320f kernel: [ 8221.403828] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:00:09 arun40-AY020AA-ABA-p6320f kernel: [ 8347.461076] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:02:15 arun40-AY020AA-ABA-p6320f kernel: [ 8473.406454] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:04:21 arun40-AY020AA-ABA-p6320f kernel: [ 8599.461015] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:06:27 arun40-AY020AA-ABA-p6320f kernel: [ 8725.414137] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:10:39 arun40-AY020AA-ABA-p6320f kernel: [ 8977.422696] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:12:45 arun40-AY020AA-ABA-p6320f kernel: [ 9103.482022] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:14:51 arun40-AY020AA-ABA-p6320f kernel: [ 9229.431340] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:16:57 arun40-AY020AA-ABA-p6320f kernel: [ 9355.486800] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:19:03 arun40-AY020AA-ABA-p6320f kernel: [ 9481.439897] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:21:09 arun40-AY020AA-ABA-p6320f kernel: [ 9607.495449] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
arun40@arun40-AY020AA-ABA-p6320f:~$

```

---

### Post by mastablasta on 2012-08-22
> **gcy56 said:**
> I started using it after my computer **motherboard had a problem**. 
 
 
are you sure there is no hardware error on the maschine?
 
> **Bucky Ball said:**
> Hard to buy a machine that's not 'Win' something unless ....
 
Here they sell plenty maschines with no OS installed (or rather they have FreeDOS on them). It has somethign to do with the anti monopoly laws.

---

### Post by Bucky Ball on 2012-08-22
> **mastablasta said:**
> Here they sell plenty maschines with no OS installed (or rather they have FreeDOS on them). It has somethign to do with the anti monopoly laws.

Great. Not too thick on the ground in Australia. ;(

---

### Post by jualin on 2012-08-22
> **gcy56 said:**
> Kernel Log- Not sure this is what you were looking for
```

Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389390] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389392] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389393] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389395] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389397] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389399] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389401] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389403] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389405] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389407] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389408] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389410] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389412] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389414] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389416] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389418] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389419] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389421] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389423] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389425] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389427] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389429] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389431] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389432] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389434] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389436] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389438] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389440] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389442] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389443] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389445] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389447] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389449] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389451] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389453] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389455] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389457] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389458] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389460] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389462] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389464] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389466] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389468] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389469] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389471] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389473] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389475] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389477] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389479] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389481] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389483] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389484] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389486] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389488] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389490] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389492] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389494] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389495] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389497] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389499] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389501] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389503] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389505] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389506] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.389508] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.395747] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.399905] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.401149] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.401740] Registered led device: ath9k-phy0
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.401744] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xf9e20000, irq=17
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.433410] init: failsafe main process (1016) killed by TERM signal
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481772] Bluetooth: Core ver 2.16
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481794] NET: Registered protocol family 31
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481796] Bluetooth: HCI device and connection manager initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481798] Bluetooth: HCI socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481800] Bluetooth: L2CAP socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.481804] Bluetooth: SCO socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.485592] Bluetooth: RFCOMM TTY layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.485600] Bluetooth: RFCOMM socket layer initialized
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.485602] Bluetooth: RFCOMM ver 1.11
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.497555] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.497558] Bluetooth: BNEP filters: protocol multicast
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518083] type=1400 audit(1345599692.480:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1106 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518501] type=1400 audit(1345599692.480:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1106 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518717] type=1400 audit(1345599692.480:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1106 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.518974] type=1400 audit(1345599692.480:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1109 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.519002] type=1400 audit(1345599692.480:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1105 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.520960] type=1400 audit(1345599692.484:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1112 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.521194] type=1400 audit(1345599692.484:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=1112 comm="apparmor_parser"
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.547007] ppdev: user-space parallel port driver
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.588013] hda_codec: ALC888: BIOS auto-probing.
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.588017] hda_codec: ALC888: SKU not ready 0x411111f0
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.589369] forcedeth 0000:00:0a.0: irq 40 for MSI/MSI-X
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.589560] forcedeth 0000:00:0a.0: eth0: no link during initialization
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.590133] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.590470] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.631991] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.635032] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.714887] init: alsa-restore main process (1186) terminated with status 19
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.890090] usbcore: registered new interface driver usblp
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974099] vboxdrv: Found 4 processor cores.
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974268] vboxdrv: fAsync=0 offMin=0x498 offMax=0x139a
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974514] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.974516] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Aug 21 20:41:32 arun40-AY020AA-ABA-p6320f kernel: [   30.981501] vboxpci: IOMMU not found (not registered)
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828096] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input7
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828214] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input8
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828301] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828359] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input10
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828416] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input11
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828473] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input12
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828530] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
Aug 21 20:41:33 arun40-AY020AA-ABA-p6320f kernel: [   31.828591] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input14
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.339762] vesafb: mode is 1024x768x32, linelength=4096, pages=0
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.339765] vesafb: scrolling: redraw
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.339767] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.343294] vesafb: framebuffer at 0xe7000000, mapped to 0xf8c00000, using 3072k, total 3072k
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.343535] Console: switching to colour frame buffer device 128x48
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.343557] fb0: VESA VGA frame buffer device
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.356188] init: plymouth-splash main process (1601) terminated with status 1
Aug 21 20:41:34 arun40-AY020AA-ABA-p6320f kernel: [   32.669081] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.465905] wlan0: authenticate with e8:40:f2:2a:0f:04 (try 1)
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.468047] wlan0: authenticated
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.487094] wlan0: associate with e8:40:f2:2a:0f:04 (try 1)
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.490446] wlan0: RX AssocResp from e8:40:f2:2a:0f:04 (capab=0x431 status=0 aid=5)
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.490449] wlan0: associated
Aug 21 20:41:41 arun40-AY020AA-ABA-p6320f kernel: [   39.497489] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 21 20:41:45 arun40-AY020AA-ABA-p6320f kernel: [   43.747414] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41402 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:41:51 arun40-AY020AA-ABA-p6320f kernel: [   49.508128] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41403 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:41:51 arun40-AY020AA-ABA-p6320f kernel: [   49.776016] wlan0: no IPv6 routers present
Aug 21 20:42:02 arun40-AY020AA-ABA-p6320f kernel: [   61.028496] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41404 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:42:26 arun40-AY020AA-ABA-p6320f kernel: [   84.068603] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41405 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:43:12 arun40-AY020AA-ABA-p6320f kernel: [  130.147590] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:82:47:88:b9:18:59:33:43:7e:e1:08:00 SRC=91.189.89.114 DST=192.168.0.14 LEN=126 TOS=0x00 PREC=0x00 TTL=51 ID=41406 DF PROTO=TCP SPT=443 DPT=54164 WINDOW=121 RES=0x00 ACK PSH URGP=0 
Aug 21 20:43:39 arun40-AY020AA-ABA-p6320f kernel: [  157.129892] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:45:45 arun40-AY020AA-ABA-p6320f kernel: [  283.082835] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:47:51 arun40-AY020AA-ABA-p6320f kernel: [  409.146709] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:49:57 arun40-AY020AA-ABA-p6320f kernel: [  535.096219] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:52:03 arun40-AY020AA-ABA-p6320f kernel: [  661.146536] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:54:09 arun40-AY020AA-ABA-p6320f kernel: [  787.098970] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:56:15 arun40-AY020AA-ABA-p6320f kernel: [  913.154152] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 20:58:21 arun40-AY020AA-ABA-p6320f kernel: [ 1039.108865] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:00:27 arun40-AY020AA-ABA-p6320f kernel: [ 1165.167075] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:04:39 arun40-AY020AA-ABA-p6320f kernel: [ 1417.170381] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:06:45 arun40-AY020AA-ABA-p6320f kernel: [ 1543.124300] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:08:51 arun40-AY020AA-ABA-p6320f kernel: [ 1669.180040] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:10:57 arun40-AY020AA-ABA-p6320f kernel: [ 1795.131442] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:13:03 arun40-AY020AA-ABA-p6320f kernel: [ 1921.186733] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:15:09 arun40-AY020AA-ABA-p6320f kernel: [ 2047.139572] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:17:15 arun40-AY020AA-ABA-p6320f kernel: [ 2173.194832] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:19:21 arun40-AY020AA-ABA-p6320f kernel: [ 2299.147791] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:21:27 arun40-AY020AA-ABA-p6320f kernel: [ 2425.204132] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:23:33 arun40-AY020AA-ABA-p6320f kernel: [ 2551.156615] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:25:39 arun40-AY020AA-ABA-p6320f kernel: [ 2677.218808] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:27:45 arun40-AY020AA-ABA-p6320f kernel: [ 2803.164301] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:29:51 arun40-AY020AA-ABA-p6320f kernel: [ 2929.219432] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:31:57 arun40-AY020AA-ABA-p6320f kernel: [ 3055.172309] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:34:03 arun40-AY020AA-ABA-p6320f kernel: [ 3181.227640] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:38:15 arun40-AY020AA-ABA-p6320f kernel: [ 3433.236823] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:46:39 arun40-AY020AA-ABA-p6320f kernel: [ 3937.257056] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:52:57 arun40-AY020AA-ABA-p6320f kernel: [ 4315.213859] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 21:55:03 arun40-AY020AA-ABA-p6320f kernel: [ 4441.269308] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:01:21 arun40-AY020AA-ABA-p6320f kernel: [ 4819.230661] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:03:27 arun40-AY020AA-ABA-p6320f kernel: [ 4945.286123] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:05:33 arun40-AY020AA-ABA-p6320f kernel: [ 5071.239220] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:07:39 arun40-AY020AA-ABA-p6320f kernel: [ 5197.294582] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:09:45 arun40-AY020AA-ABA-p6320f kernel: [ 5323.247637] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:11:51 arun40-AY020AA-ABA-p6320f kernel: [ 5449.303091] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:13:57 arun40-AY020AA-ABA-p6320f kernel: [ 5575.256086] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:16:03 arun40-AY020AA-ABA-p6320f kernel: [ 5701.311588] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:18:09 arun40-AY020AA-ABA-p6320f kernel: [ 5827.264625] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:20:15 arun40-AY020AA-ABA-p6320f kernel: [ 5953.320013] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:22:21 arun40-AY020AA-ABA-p6320f kernel: [ 6079.273360] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:24:27 arun40-AY020AA-ABA-p6320f kernel: [ 6205.328571] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:28:39 arun40-AY020AA-ABA-p6320f kernel: [ 6457.338656] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:30:45 arun40-AY020AA-ABA-p6320f kernel: [ 6583.290154] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:32:51 arun40-AY020AA-ABA-p6320f kernel: [ 6709.345625] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:34:57 arun40-AY020AA-ABA-p6320f kernel: [ 6835.298702] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:37:03 arun40-AY020AA-ABA-p6320f kernel: [ 6961.354143] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:39:09 arun40-AY020AA-ABA-p6320f kernel: [ 7087.310646] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:41:15 arun40-AY020AA-ABA-p6320f kernel: [ 7213.362701] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:43:21 arun40-AY020AA-ABA-p6320f kernel: [ 7339.323355] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:45:27 arun40-AY020AA-ABA-p6320f kernel: [ 7465.372757] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:47:33 arun40-AY020AA-ABA-p6320f kernel: [ 7591.324350] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:49:39 arun40-AY020AA-ABA-p6320f kernel: [ 7717.379846] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:51:45 arun40-AY020AA-ABA-p6320f kernel: [ 7843.333219] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:53:51 arun40-AY020AA-ABA-p6320f kernel: [ 7969.388381] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:55:57 arun40-AY020AA-ABA-p6320f kernel: [ 8095.443967] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 22:58:03 arun40-AY020AA-ABA-p6320f kernel: [ 8221.403828] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:00:09 arun40-AY020AA-ABA-p6320f kernel: [ 8347.461076] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:02:15 arun40-AY020AA-ABA-p6320f kernel: [ 8473.406454] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:04:21 arun40-AY020AA-ABA-p6320f kernel: [ 8599.461015] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:06:27 arun40-AY020AA-ABA-p6320f kernel: [ 8725.414137] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:10:39 arun40-AY020AA-ABA-p6320f kernel: [ 8977.422696] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:12:45 arun40-AY020AA-ABA-p6320f kernel: [ 9103.482022] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:14:51 arun40-AY020AA-ABA-p6320f kernel: [ 9229.431340] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:16:57 arun40-AY020AA-ABA-p6320f kernel: [ 9355.486800] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:19:03 arun40-AY020AA-ABA-p6320f kernel: [ 9481.439897] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Aug 21 23:21:09 arun40-AY020AA-ABA-p6320f kernel: [ 9607.495449] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:18:59:33:43:7e:e1:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
arun40@arun40-AY020AA-ABA-p6320f:~$

```

I don't see anything weird with the kernel logs. I am not sure if anyone else wants to double check. What were you exactly doing when the crash happened? And also, does you machine work on Windows?
I ask because it may be a hardware issue like others have suggested.

---

### Post by Ymurti on 2012-08-23
> **jualin said:**
> Hi gcy56,
A good way to start is to look at the kernel log to see what actually happened when your computer crashed. 
Next time that it crashes, restart and check the kern.log inside /var/log/
You can do it using the command line with ```
cat /var/log/kern.log
```You can also access it graphically using the ["Log File Viewer"]("http://askubuntu.com/questions/15647/where-can-i-find-the-kernel-logs").
You can then post the log here.
Hope this helps!


Dear Jualin, I am having the same problem and here it is my kernel.log:

```
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.232731] EDD information not available.
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.457650] Refined TSC clocksource calibration: 2393.996 MHz.
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.457657] Switching to clocksource tsc
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.481561] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.482042] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.493528] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.531091] ata1.00: ATA-8: TOSHIBA MK3265GSX, GJ002H, max UDMA/100
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.531097] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.531936] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.532260] ata1.00: configured for UDMA/100
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.532597] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3265GS GJ00 PQ: 0 ANSI: 5
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.532823] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.532860] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.533074] sd 0:0:0:0: [sda] Write Protect is off
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.533080] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.533216] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.616798]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.618518] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.626483] hub 1-1:1.0: USB hub found
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.626671] hub 1-1:1.0: 6 ports detected
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.737161] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.848935] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.850770] ata2.00: ATAPI: Optiarc DVD RW AD-7710H, 1.V0, max UDMA/100
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.852969] ata2.00: configured for UDMA/100
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.855130] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7710H  1.V0 PQ: 0 ANSI: 5
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.857779] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.857784] cdrom: Uniform CD-ROM driver Revision: 3.20
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.857986] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.858089] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.869767] hub 2-1:1.0: USB hub found
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.869965] hub 2-1:1.0: 8 ports detected
Aug 24 06:37:44 yajnamurti-laptop kernel: [    5.940969] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.140629] usb 2-1.2: new low-speed USB device number 3 using ehci_hcd
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.176342] ata6: SATA link down (SStatus 0 SControl 300)
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.176613] Freeing unused kernel memory: 712k freed
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.176855] Write protecting the kernel text: 5616k
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.176938] Write protecting the kernel read-only data: 2324k
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.230343] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.251710] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input3
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.251881] generic-usb 0003:0A81:0101.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:1d.0-1.2/input0
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.262068] acpi device:4b: registered as cooling_device4
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.262203] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:4a/LNXVIDEO:01/input/input4
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.262255] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.262549] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input5
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.262934] generic-usb 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:1d.0-1.2/input1
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.262955] usbcore: registered new interface driver usbhid
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.262957] usbhid: USB HID core driver
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.274679] sdhci: Secure Digital Host Controller Interface driver
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.274682] sdhci: Copyright(c) Pierre Ossman
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.275014] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 0)
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.275069] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.275133] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.275143] sdhci-pci 0000:03:00.0: setting latency timer to 64
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.275171] mmc0: no vmmc regulator found
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.275248] Registered led device: mmc0::
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.275973] sky2: driver version 1.30
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.276116] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.276189] sky2 0000:04:00.0: setting latency timer to 64
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.276312] sky2 0000:04:00.0: Yukon-2 Optima chip revision 1
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.277074] sky2 0000:04:00.0: irq 42 for MSI/MSI-X
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279000] sky2 0000:04:00.0: eth0: addr 54:42:49:e6:3d:20
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279458] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279508] sdhci-pci 0000:03:00.4: SDHCI controller found [1180:e822] (rev 0)
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279560] sdhci-pci 0000:03:00.4: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279620] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279629] sdhci-pci 0000:03:00.4: setting latency timer to 64
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279656] mmc1: no vmmc regulator found
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.279726] Registered led device: mmc1::
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.280798] mmc1: SDHCI controller on PCI [0000:03:00.4] using DMA
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.448111] hub 2-1:1.0: over-current condition on port 5
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.519989] usb 2-1.6: new high-speed USB device number 4 using ehci_hcd
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.613949] hub 2-1.6:1.0: USB hub found
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.614269] hub 2-1.6:1.0: 4 ports detected
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.891467] usb 2-1.6.3: new low-speed USB device number 5 using ehci_hcd
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.993950] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.3/2-1.6.3:1.0/input/input6
Aug 24 06:37:44 yajnamurti-laptop kernel: [    6.994161] generic-usb 0003:1BCF:0005.0003: input,hidraw2: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.6.3/input0
Aug 24 06:37:44 yajnamurti-laptop kernel: [    7.999907] vesafb: mode is 1366x768x32, linelength=5504, pages=0
Aug 24 06:37:44 yajnamurti-laptop kernel: [    7.999910] vesafb: scrolling: redraw
Aug 24 06:37:44 yajnamurti-laptop kernel: [    7.999913] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Aug 24 06:37:44 yajnamurti-laptop kernel: [    8.001789] vesafb: framebuffer at 0xe0000000, mapped to 0xf8100000, using 4160k, total 4160k
Aug 24 06:37:44 yajnamurti-laptop kernel: [    8.001903] fbcon: VESA VGA (fb0) is primary device
Aug 24 06:37:44 yajnamurti-laptop kernel: [    8.001995] Console: switching to colour frame buffer device 170x48
Aug 24 06:37:44 yajnamurti-laptop kernel: [    8.002025] fb0: VESA VGA frame buffer device
Aug 24 06:37:44 yajnamurti-laptop kernel: [    8.321072] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Aug 24 06:37:44 yajnamurti-laptop kernel: [    8.321076] EXT4-fs (sda5): write access will be enabled during recovery
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.186811] EXT4-fs (sda5): orphan cleanup on readonly fs
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.186820] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 786499
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.186869] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1835830
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.186926] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1835505
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.186961] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6030024
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.186975] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1320197
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.187009] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1311986
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.187036] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 786459
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.187056] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6030021
Aug 24 06:37:44 yajnamurti-laptop kernel: [   12.187065] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6030020
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187075] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029997
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187085] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029982
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187095] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029537
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187106] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1445308
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187116] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1445302
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187126] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1445235
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187136] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1445230
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187146] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029909
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187156] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029747
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187166] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029746
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187176] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029745
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187185] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029743
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187195] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029742
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187204] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029740
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187215] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1454625
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187225] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1454742
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187244] EXT4-fs (sda5): 25 orphan inodes deleted
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.187246] EXT4-fs (sda5): recovery complete
Aug 24 06:37:45 yajnamurti-laptop kernel: [   12.543867] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   49.769681] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 24 06:37:45 yajnamurti-laptop kernel: [   49.999799] type=1400 audit(1345770462.340:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=417 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.000440] type=1400 audit(1345770462.340:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=417 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.000812] type=1400 audit(1345770462.344:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=417 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.002604] Adding 6350844k swap on /dev/sda6.  Priority:-1 extents:1 across:6350844k 
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.331534] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.657923] mei: module is from the staging directory, the quality is unknown, you have been warned.
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.658287] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.658293] mei 0000:00:16.0: setting latency timer to 64
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.658357] mei 0000:00:16.0: irq 43 for MSI/MSI-X
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.683815] cfg80211: Calling CRDA to update world regulatory domain
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.689158] cfg80211: World regulatory domain updated:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.689160] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.689163] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.689165] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.689167] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.689169] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.689171] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   50.823608] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.040100] sony_laptop: Sony Notebook Control Driver v0.6
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.051437] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/SNY5001:00/input/input7
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.051571] input: Sony Vaio Jogdial as /devices/virtual/input/input8
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.052176] sony_laptop: brightness ignored, must be controlled by ACPI video driver
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.115696] Linux video capture interface: v2.00
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.169640] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6464)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.177106] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input9
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.177289] usbcore: registered new interface driver uvcvideo
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.177295] USB Video Class driver (1.1.1)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.303260] lp: driver loaded but no devices found
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.537123] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.691427] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.691441] ath9k 0000:02:00.0: setting latency timer to 64
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742664] ath: EEPROM regdomain: 0x65
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742666] ath: EEPROM indicates we should expect a direct regpair map
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742669] ath: Country alpha2 being used: 00
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742670] ath: Regpair used: 0x65
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742673] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742676] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742678] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742680] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742682] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742684] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742686] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742688] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742690] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742692] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742693] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742696] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742697] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742699] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742701] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742703] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742705] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742707] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742709] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742711] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742713] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742715] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742717] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742719] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742721] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742723] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.742724] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.744272] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.955215] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.956063] Registered led device: ath9k-phy0
Aug 24 06:37:45 yajnamurti-laptop kernel: [   51.956073] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8720000, irq=16
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.275740] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.275811] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.275861] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.435860] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.435977] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.436253] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.436324] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.436350] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.468600] init: failsafe main process (897) killed by TERM signal
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.487819] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.487922] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.503998] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input13
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.521476] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input14
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.522513] ppdev: user-space parallel port driver
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.600376] type=1400 audit(1345770464.948:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1011 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.600833] type=1400 audit(1345770464.948:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1011 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.601153] type=1400 audit(1345770464.948:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1011 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.707441] Bluetooth: Core ver 2.16
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.707466] NET: Registered protocol family 31
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.707469] Bluetooth: HCI device and connection manager initialized
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.707472] Bluetooth: HCI socket layer initialized
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.707474] Bluetooth: L2CAP socket layer initialized
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.707481] Bluetooth: SCO socket layer initialized
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.720834] type=1400 audit(1345770465.068:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1010 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.737175] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.748849] sky2 0000:04:00.0: eth0: enabling interface
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.749567] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.752266] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.804691] type=1400 audit(1345770465.152:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1014 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.805183] type=1400 audit(1345770465.152:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1014 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   52.830894] type=1400 audit(1345770465.176:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1028 comm="apparmor_parser"
Aug 24 06:37:45 yajnamurti-laptop kernel: [   53.040809] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 24 06:37:45 yajnamurti-laptop kernel: [   53.040812] Bluetooth: BNEP filters: protocol multicast
Aug 24 06:37:45 yajnamurti-laptop kernel: [   53.040984] Bluetooth: RFCOMM TTY layer initialized
Aug 24 06:37:45 yajnamurti-laptop kernel: [   53.040989] Bluetooth: RFCOMM socket layer initialized
Aug 24 06:37:45 yajnamurti-laptop kernel: [   53.040992] Bluetooth: RFCOMM ver 1.11
Aug 24 06:37:45 yajnamurti-laptop kernel: [   53.231580] init: gdm main process (1192) killed by TERM signal
Aug 24 06:37:46 yajnamurti-laptop kernel: [   54.073848] postgres (1229): /proc/1229/oom_adj is deprecated, please use /proc/1229/oom_score_adj instead.
Aug 24 06:37:46 yajnamurti-laptop kernel: [   54.429211] sky2 0000:04:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control rx
Aug 24 06:37:46 yajnamurti-laptop kernel: [   54.429458] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug 24 06:37:50 yajnamurti-laptop kernel: [   57.763398] vboxdrv: Found 4 processor cores.
Aug 24 06:37:50 yajnamurti-laptop kernel: [   57.763892] vboxdrv: fAsync=0 offMin=0x2ce offMax=0x1f3e
Aug 24 06:37:50 yajnamurti-laptop kernel: [   57.764031] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug 24 06:37:50 yajnamurti-laptop kernel: [   57.764034] vboxdrv: Successfully loaded version 4.1.18 (interface 0x00190000).
Aug 24 06:37:50 yajnamurti-laptop kernel: [   58.035066] vboxpci: IOMMU not found (not registered)
Aug 24 06:37:50 yajnamurti-laptop kernel: [   58.344721] init: plymouth-stop pre-start process (1854) terminated with status 1
Aug 24 06:37:57 yajnamurti-laptop kernel: [   65.098655] eth0: no IPv6 routers present
Aug 24 06:38:28 yajnamurti-laptop kernel: [   96.203148] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=40048 PROTO=TCP SPT=993 DPT=41381 WINDOW=16080 RES=0x00 ACK PSH URGP=0 
Aug 24 06:38:28 yajnamurti-laptop kernel: [   96.209248] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=43757 PROTO=TCP SPT=993 DPT=41382 WINDOW=15008 RES=0x00 ACK PSH URGP=0 
Aug 24 06:38:36 yajnamurti-laptop kernel: [  103.676467] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=40049 PROTO=TCP SPT=993 DPT=41381 WINDOW=16080 RES=0x00 ACK PSH URGP=0 
Aug 24 06:38:36 yajnamurti-laptop kernel: [  103.701245] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=43758 PROTO=TCP SPT=993 DPT=41382 WINDOW=15008 RES=0x00 ACK PSH URGP=0 
Aug 24 06:38:46 yajnamurti-laptop kernel: [  113.659286] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=40050 PROTO=TCP SPT=993 DPT=41381 WINDOW=16080 RES=0x00 ACK PSH URGP=0 
Aug 24 06:38:46 yajnamurti-laptop kernel: [  113.682990] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=43759 PROTO=TCP SPT=993 DPT=41382 WINDOW=15008 RES=0x00 ACK PSH URGP=0 
Aug 24 06:38:56 yajnamurti-laptop kernel: [  123.642033] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=40051 PROTO=TCP SPT=993 DPT=41381 WINDOW=16080 RES=0x00 ACK PSH URGP=0 
Aug 24 06:38:56 yajnamurti-laptop kernel: [  123.666817] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=43760 PROTO=TCP SPT=993 DPT=41382 WINDOW=15008 RES=0x00 ACK PSH URGP=0 
Aug 24 06:39:06 yajnamurti-laptop kernel: [  133.624945] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=40052 PROTO=TCP SPT=993 DPT=41381 WINDOW=16080 RES=0x00 ACK PSH URGP=0 
Aug 24 06:39:06 yajnamurti-laptop kernel: [  133.649701] Inbound IN=eth0 OUT= MAC=54:42:49:e6:3d:20:00:16:76:4b:2a:c7:08:00 SRC=74.125.127.16 DST=172.130.121.53 LEN=73 TOS=0x00 PREC=0x00 TTL=40 ID=43761 PROTO=TCP SPT=993 DPT=41382 WINDOW=15008 RES=0x00 ACK PSH URGP=0 
yajnamurti@yajnamurti-laptop:~$
```

---

### Post by Bucky Ball on 2012-08-23
@ Ymurti: Please use code tags. They make things easier to read. They can be found by clicking 'Go Advanced', highlight the code then click the hash icon (#). I have edited your post for easier reading. Thanks. ;)

BB

---

### Post by Ymurti on 2012-08-23
> **Bucky Ball said:**
> @ Ymurti: Please use code tags. They make things easier to read. They can be found by clicking 'Go Advanced', highlight the code then click the hash icon (#). I have edited your post for easier reading. Thanks. ;)

BB

```
Dear Bucky, Thank You for the instruction. :)
```

---

### Post by Ymurti on 2012-08-23
```
yajnamurti@yajnamurti-laptop:~$ lspci -v | grep -iA12 vga
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0020000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at d000 [size=256]
	Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 45
yajnamurti@yajnamurti-laptop:~$
```

---

### Post by Bucky Ball on 2012-08-24
> **Ymurti said:**
> ```
Dear Bucky, Thank You for the instruction. :)
```

LOL. My pleasure. You can also type them manually with [code] and another one on the other end with a '[/' before 'code]' (can't demonstrate or it puts the text in code tags, naturally). 

Copy how the auto-formatting does it is what I mean. ;)

---

