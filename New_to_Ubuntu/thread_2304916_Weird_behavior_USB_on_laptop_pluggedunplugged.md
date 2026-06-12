---
title: "Weird behavior USB on laptop plugged/unplugged"
date: 2015-12-01
forum: New to Ubuntu
---

### Post by flo16 on 2015-12-01
Hi, 
I'm very new on Linux and I face  avery strange problem : I have a USB camera plugged to my laptop to record experiments. The images are read with the software uEyeDemo. When the laptop is on battery {unplugged), everything goes smoothly and the software displays the images recorded by the camera. However, as soon as I plug the laptop to power, all frames start to drop. Any idea hoz I could correct this ?
Thanks

---

### Post by tgalati4 on 2015-12-01
Welcome to the forums.  Laptops have different modes when on AC power and on Battery.  So perhaps turn off all power-saving modes.

After dropping some frames, open a terminal:

```
dmesg | tail -40
```

Post any errors.

What version of Ubuntu?

---

### Post by flo16 on 2015-12-02
Hi, 
My version of Ubuntu is 14.04LTS

Below is a copy paste of the output of the command : 

[ 5342.358774] dell_wmi: Unknown WMI event type 0x11: 0xffd0
[ 5342.410699] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 5342.525968] ata1.00: ACPI cmd ef/5a:00:00:00:00:a0 (SET FEATURES) succeeded
[ 5342.554743] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[ 5342.555007] ata1.00: configured for UDMA/133
[ 5343.010556] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5343.084860] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 5343.084881] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[ 5343.085073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5343.821988] dell_wmi: Unknown WMI event type 0x11: 0xffd1
[ 5343.929158] wlan0: authenticate with c4:14:3c:fa:7e:d2
[ 5343.931072] wlan0: direct probe to c4:14:3c:fa:7e:d2 (try 1/3)
[ 5344.133688] wlan0: direct probe to c4:14:3c:fa:7e:d2 (try 2/3)
[ 5344.337597] wlan0: send auth to c4:14:3c:fa:7e:d2 (try 3/3)
[ 5344.339143] wlan0: authenticated
[ 5344.341595] wlan0: associate with c4:14:3c:fa:7e:d2 (try 1/3)
[ 5344.347532] wlan0: RX AssocResp from c4:14:3c:fa:7e:d2 (capab=0x421 status=0 aid=2)
[ 5344.348122] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 5344.348129] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 5344.348143] wlan0: associated
[ 5344.348187] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5344.348332] cfg80211: Calling CRDA for country: PL
[ 5344.352738] cfg80211: Regulatory domain changed to country: PL
[ 5344.352745] cfg80211:  DFS Master region: unset
[ 5344.352747] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 5344.352752] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 5344.352756] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 5344.352759] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[ 5344.352762] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
[ 5344.352766] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[ 5344.397733] wlan0: Limiting TX power to 16 dBm as advertised by c4:14:3c:fa:7e:d2
[ 5345.462029] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 5484.159400] usb 2-1.3: new high-speed USB device number 11 using ehci-pci
[ 5484.251853] usb 2-1.3: New USB device found, idVendor=1409, idProduct=1000
[ 5484.251859] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 5486.774323] usb 2-1.3: USB disconnect, device number 11
[ 5488.508962] usb 2-1.3: new high-speed USB device number 12 using ehci-pci
[ 5488.601665] usb 2-1.3: New USB device found, idVendor=1409, idProduct=1555
[ 5488.601669] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 5498.502072] init: anacron main process (18013) killed by TERM signal

---

### Post by tgalati4 on 2015-12-02
Nothing helpful there.  These [cameras]("http://http://www.visiononline.org/vision-resources-details.cfm/vision-resources/uEye-Demo-Camera-Viewer-v3-80/content_id/2496") are embedded devices, not your typical USB webcam.

Put your laptop power supply on an oscilloscope.  It's possible that you have a leaky power supply that is putting out AC noise, which is interfering with the camera's operation.  Try a new, or different power supply.

Try using a desktop computer to set up your recording station.

---

