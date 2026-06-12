---
title: "wpa supplicant Hidden SSID"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by uchihaitachi on 2008-10-13
Hi all, I'm trying to connect to my school's hidden network NUS.

My conf file is as follows and the error that I receive upon running the file. Apparently it doesn't connect to the hidden SSID. Any ideas?

ctrl_interface=/var/run/wpa_supplicant

network={
ssid="NUS"
scan_ssid=1
key_mgmt=IEEE8021X
eap=PEAP
phase2="auth=MSCHAPV2"
identity="osdhsdf"
password="sadfjsdf"
ca_cert="/etc/ssl/cert/Thawte_Premium_Server_CA.pem"
phase2="auth=MSCHAPV2"
} 

sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -d

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='NUS'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1d:e0:34:b4:6d
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=3):
     4e 55 53                                          NUS             
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 4093 bytes of scan results (22 BSSes)
Scan results: 22
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:4a:32:36:a0 ssid='' wpa_ie_len=30 rsn_ie_len=28 caps=0x11
   skip - SSID mismatch
1: 00:17:3f:ba:bb:12 ssid='belkin54g' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:34:a3:da:50 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:0f:24:fd:5f:d0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
4: 00:0f:34:96:0c:10 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
5: 00:0f:34:a0:63:40 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
6: 00:0f:34:96:0b:00 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
7: 00:12:43:15:14:00 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
8: 00:0e:38:c7:63:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
9: 00:1e:13:6e:08:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
10: 00:0f:34:a0:66:10 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
11: 00:0d:ed:2e:db:dc ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
12: 00:0f:34:a0:5c:d0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
13: 00:0e:83:12:aa:50 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
14: 00:0e:83:12:ac:10 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
15: 00:0e:83:11:69:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
16: 00:1e:4a:32:36:a3 ssid='WebTest' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
17: 00:1e:4a:32:36:a2 ssid='bmsiwlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
18: 00:1e:13:1c:20:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
19: 00:0f:24:fd:59:b0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
20: 00:0c:ce:2a:e4:42 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
21: 00:0e:38:c8:e0:d0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x0
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:4a:32:36:a0 ssid='' wpa_ie_len=30 rsn_ie_len=28 caps=0x11
   skip - SSID mismatch
1: 00:17:3f:ba:bb:12 ssid='belkin54g' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:0f:34:a3:da:50 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:0f:24:fd:5f:d0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
4: 00:0f:34:96:0c:10 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
5: 00:0f:34:a0:63:40 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
6: 00:0f:34:96:0b:00 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
7: 00:12:43:15:14:00 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
8: 00:0e:38:c7:63:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
9: 00:1e:13:6e:08:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
10: 00:0f:34:a0:66:10 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
11: 00:0d:ed:2e:db:dc ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
12: 00:0f:34:a0:5c:d0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
13: 00:0e:83:12:aa:50 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
14: 00:0e:83:12:ac:10 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
15: 00:0e:83:11:69:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
16: 00:1e:4a:32:36:a3 ssid='WebTest' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
17: 00:1e:4a:32:36:a2 ssid='bmsiwlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
18: 00:1e:13:1c:20:70 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
19: 00:0f:24:fd:59:b0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
20: 00:0c:ce:2a:e4:42 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
21: 00:0e:38:c8:e0:d0 ssid='NUSOPEN' wpa_ie_len=0 rsn_ie_len=0 caps=0x0
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 4093 bytes of scan results (22 BSSes)
Scan results: 22
Selecting BSS from priority group 0
Try to find WPA-enabled AP

No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

---

