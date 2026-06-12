---
title: "wireless connection from ubuntu"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by GarethA on 2012-11-04
Hi - am having wireless connection probs.
Have the trawled this site and others for help but can't figure it out.
Probably doing something stupid...

I have a wireless router running wpa2 which is being used fine by a variety of devices.
I have tried 2 machines now running ubuntu 12 (and tried another simmilar distro) and I can't connect.
Wired connection is fine.

It detects the wireless network but wont establish a connection.

I've tried disabling security, picking different wireless frequencies.

any help gratefully received.

here's the syslog with networkmanager messages:
```

Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Activation (wlan0/wireless): connection 'linux-special' has security, and secrets exist.  No new secrets needed.
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Config: added 'ssid' value 'linux-special'
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Config: added 'scan_ssid' value '1'
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Config: added 'auth_alg' value 'OPEN'
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Config: added 'psk' value '<omitted>'
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> Config: set interface ap_scan to 1
Nov  4 10:36:33 peter-linux NetworkManager[691]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  4 10:37:33 peter-linux NetworkManager[691]: <warn> Activation (wlan0/wireless): association took too long.
Nov  4 10:37:33 peter-linux NetworkManager[691]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov  4 10:37:33 peter-linux NetworkManager[691]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov  4 10:37:33 peter-linux NetworkManager[691]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov  4 10:37:33 peter-linux NetworkManager[691]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```

---

### Post by GarethA on 2012-11-04
Tried WICD ... same

booted the same box to XP and it connects 
:confused:

---

