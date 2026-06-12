---
title: "Hostapd to connect laptop to Android"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by kmegamind on 2012-09-27
i am trying to set up my laptop as an access point for my Android to use WiFi, so i knew that ubuntu sets the network as Ad-Hoc which is not discoverable by android, So i tried the method explained [here]("http://asd-justthat.blogspot.com/2012/04/create-wifi-wireless-hotspot-in-ubuntu.html") -which i found on many other websites- but when i run hostapd.conf this error appears :

   
```
nl80211: Failed to set interface wlan0 into AP mode
nl80211 driver initialization failed.
ELOOP: remaining socket: sock=4 eloop_data=0x8e488f8 user_data=0x8e48ea0 handler=0x807c5e0
ELOOP: remaining socket: sock=6 eloop_data=0x8e4aca8 user_data=(nil) handler=0x8086770
```


this is how my hostapd.cof looks like :

```
interface=wlan0
driver=nl80211
ssid=Any_SSID_name 
hw_mode=g
channel=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2 
wpa_passphrase=Any_password
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```


and this is my wireless card info 

```

 description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:73:51:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-31-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0300000-f0303fff
```

What should I do to get my WiFi network running ?

---

### Post by Epodx64 on 2012-09-27
not really sure if this will help but maybe try changing the driver to
driver=brcmsmac

---

### Post by kmegamind on 2012-09-28
> **Epodx64 said:**
> not really sure if this will help but maybe try changing the driver to
driver=brcmsmac

Now it says : 
```
 invalid/unknown driver 'brcmsmac'

```

---

