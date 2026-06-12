---
title: "After upgrade to latest kernel, error in wifi hotspot"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by eshant_engineer on 2012-08-11
Hi,

Today I upgraded my kernel to the latest release. After reboot when I tried to connect to my hotspot connection. It started giving error

Linux version:
```
Linux ebuntu-Inspiron-N5110 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Syslog:
```
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0) starting connection 'Hotspot'
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0/wireless): connection 'Hotspot' requires no security.  No secrets needed.
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Config: added 'ssid' value 'ebuntu-Inspiron-N5110'
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Config: added 'mode' value '1'
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Config: added 'frequency' value '2412'
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Config: added 'key_mgmt' value 'NONE'
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 12 01:33:42 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Config: set interface ap_scan to 2
Aug 12 01:33:42 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Trying to associate with SSID 'ebuntu-Inspiron-N5110'
Aug 12 01:33:43 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Could not set interface wlan0 flags: Device or resource busy
Aug 12 01:33:43 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: nl80211: Failed to set interface into IBSS mode
Aug 12 01:33:43 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Association request to the driver failed
Aug 12 01:33:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> (wlan0): supplicant interface state: inactive -> associating
Aug 12 01:33:52 ebuntu-Inspiron-N5110 kernel: [ 1084.035448] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=79.32.68.249 DST=117.254.19.27 LEN=131 TOS=0x00 PREC=0x20 TTL=109 ID=2170 PROTO=UDP SPT=16293 DPT=57655 LEN=111 
Aug 12 01:33:53 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Authentication with 00:00:00:00:00:00 timed out.
Aug 12 01:33:53 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Trying to associate with SSID 'ebuntu-Inspiron-N5110'
Aug 12 01:33:53 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Association request to the driver failed
Aug 12 01:34:03 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Authentication with 00:00:00:00:00:00 timed out.
Aug 12 01:34:03 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Trying to associate with SSID 'ebuntu-Inspiron-N5110'
Aug 12 01:34:03 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Association request to the driver failed
Aug 12 01:34:09 ebuntu-Inspiron-N5110 kernel: [ 1100.685554] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=178.216.44.24 DST=117.254.19.27 LEN=131 TOS=0x1C PREC=0x20 TTL=112 ID=27205 PROTO=UDP SPT=11338 DPT=57655 LEN=111 
Aug 12 01:34:13 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Authentication with 00:00:00:00:00:00 timed out.
Aug 12 01:34:13 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Trying to associate with SSID 'ebuntu-Inspiron-N5110'
Aug 12 01:34:13 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Association request to the driver failed
Aug 12 01:34:23 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Authentication with 00:00:00:00:00:00 timed out.
Aug 12 01:34:23 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Trying to associate with SSID 'ebuntu-Inspiron-N5110'
Aug 12 01:34:23 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Association request to the driver failed
Aug 12 01:34:28 ebuntu-Inspiron-N5110 kernel: [ 1120.228413] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=178.116.37.243 DST=117.254.19.27 LEN=95 TOS=0x00 PREC=0x20 TTL=47 ID=40582 PROTO=UDP SPT=26085 DPT=57655 LEN=75 
Aug 12 01:34:33 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Authentication with 00:00:00:00:00:00 timed out.
Aug 12 01:34:33 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Trying to associate with SSID 'ebuntu-Inspiron-N5110'
Aug 12 01:34:33 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Association request to the driver failed
Aug 12 01:34:43 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Authentication with 00:00:00:00:00:00 timed out.
Aug 12 01:34:43 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Trying to associate with SSID 'ebuntu-Inspiron-N5110'
Aug 12 01:34:43 ebuntu-Inspiron-N5110 wpa_supplicant[1435]: Association request to the driver failed
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <warn> Activation (wlan0/wireless): Ad-Hoc network creation took too long, failing activation.
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <warn> Activation (wlan0) failed for access point (ebuntu-Inspiron-N5110)
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> Marking connection 'Hotspot' invalid.
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <warn> Activation (wlan0) failed.
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <info> (wlan0): supplicant interface state: associating -> disconnected
Aug 12 01:34:43 ebuntu-Inspiron-N5110 NetworkManager[1367]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
```


Thanks for analyzing...

---

