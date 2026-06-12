---
title: "Draytek Vigor 560 - not supported?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by kentcb on 2008-05-12
Hi all,

I'm a linux newbie and am having trouble getting my wireless access to work. Ethernet is fine (posting this via my ubuntu machine).

I have a Draytek Vigor 560 wireless card. I've installed ndiswrapper and the driver for the card. However, it still doesn't work. If I choose 'Edit wireless networks' I get nothing listed.

If I look in the system log I see this:

May 12 20:32:02 Leo NetworkManager: <info>  Recreating the device list. 
May 12 20:32:02 Leo kernel: [ 1606.050238] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 12 20:32:02 Leo NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
May 12 20:32:02 Leo NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
May 12 20:32:02 Leo NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 12 20:32:02 Leo NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 12 20:32:02 Leo NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May 12 20:32:02 Leo NetworkManager: <info>  Deactivating device wlan0. 
May 12 20:32:02 Leo NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
May 12 20:32:02 Leo NetworkManager: <info>  Device list recreated successfully. 

So it looks like the device doesn't support SSID scans, even though it did under Windoze. Can anyone explain / help?

Thanks,
Kent

---

### Post by kentcb on 2008-05-13
*bump* Anybody?

---

