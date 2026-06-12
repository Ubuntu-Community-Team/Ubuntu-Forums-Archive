---
title: "Problems connecting to WPA home network on Natty"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by as4556 on 2012-01-31
Hi Everyone:

I recently changed my isp and with my new router have set the network security to WPA-PSK. It works fine in Windows 7 but I can't get Natty to connect. It recognises the network as WPA and prompts for my password but the wireless symbol shows just the "establishing connection" forever until the prompt for my password shows up again. Now before I had WEP with a 2wire built-in router and that worked fine. Here are some of the things I did:

1. Installed wpasupplicant and wpagui

2. went to the /etc/wpa_supplicant.conf and added this by first using the wpa_passphrase command:

network={
    ssid="ZyXEL"
    #psk="blahblah" (not actual one)
    psk=2ce679c9a60cab77d76fd7512723b1d52a79cbf7e1bf7250f569253d8a849fe4
}

3. Tried this first:

network={
        ssid="ZyXEL"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="blahblah"
}                      

Neither worked!!!

4. whenever I do iwlist scan wlan0, a lot of times i get either "no scan results" or 
wlan0     Failed to read scan data : Network is down

Why does this happen? The command should work every single time not intermittently.... I don't know if it is a problem with having the Ethernet connected when I run the command but I doubt it...

5. The times I do get it I see it I see the SSID 

6. I ran this after adding the wpa conf file: sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext

Some outputs I find strange:

**1st run of command**

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='ZyXEL'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: 00:26:82:9e:5a:54
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 66 4d 39 46 62 b3 58 27 ad 5b 30 56 2f 40 4d a9
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
State: DISCONNECTED -> SCANNING
Starting AP scan for wildcard SSID
ioctl[SIOCSIWSCAN]: Device or resource busy
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
Setting scan request: 1 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 1
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found

**2nd run of command:**

Wireless event: cmd=0x8b19 len=8
Scan results did not fit - trying larger buffer (8192 bytes)
Scan results did not fit - trying larger buffer (16384 bytes)
Received 10288 bytes of scan results (23 BSSes)
BSS: Start scan result update 1
BSS: Add new id 0 BSSID 7c:4f:b5:9b:5e:58 SSID 'BabyBear'
BSS: Add new id 1 BSSID 98:fc:11:5b:92:1e SSID ''
**BSS: Add new id 2 BSSID cc:5d:4e:44:ba:45 SSID 'ZyXEL'**
BSS: Add new id 3 BSSID a0:21:b7:99:2c:64 SSID 'KissMyBass'
BSS: Add new id 4 BSSID 00:26:f2:a2:42:66 SSID 'frogpond'
BSS: Add new id 5 BSSID 14:d6:4d:2f:ca:9e SSID 'FBI Van #2'
BSS: Add new id 6 BSSID 20:4e:7f:6b:93:13 SSID 'ATT4752'
BSS: Add new id 7 BSSID 00:14:51:77:28:8f SSID 'Airport Express Network'
BSS: Add new id 8 BSSID 78:cd:8e:3d:ae:0b SSID ''
BSS: Add new id 9 BSSID 00:25:9c:16:84:1f SSID 'uprising foundation'
BSS: Add new id 10 BSSID 78:cd:8e:3d:ae:0a SSID ''
BSS: Add new id 11 BSSID 78:cd:8e:3d:ae:09 SSID ''
BSS: Add new id 12 BSSID 94:44:52:74:91:94 SSID 'Belkin.3194'
BSS: Add new id 13 BSSID 00:22:3f:80:18:44 SSID 'JAWN'
BSS: Add new id 14 BSSID 78:cd:8e:3d:ae:08 SSID 'HOME-AE08'
BSS: Add new id 15 BSSID e0:91:f5:0e:a6:7a SSID 'xxxbadkitty'
BSS: Add new id 16 BSSID 00:26:f2:96:a0:35 SSID 'apt2009'
BSS: Add new id 17 BSSID 28:16:2e:66:e2:59 SSID 'BahamaMamaPapa'
BSS: Add new id 18 BSSID 20:4e:7f:67:85:0f SSID 'ATT6808'
BSS: Add new id 19 BSSID 00:14:bf:9c:01:1a SSID 'GuessThePassword'
BSS: Add new id 20 BSSID 00:1c:df:bc:2d:e9 SSID 'Belkin_G_Wireless_BC2DE9'
BSS: Add new id 21 BSSID 00:23:51:61:80:b9 SSID 'ashapea'
BSS: Add new id 22 BSSID 00:15:e9:19:cf:ee SSID 'Arlington Blvd'
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 7c:4f:b5:9b:5e:58 ssid='BabyBear' wpa_ie_len=0 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
1: 98:fc:11:5b:92:1e ssid='' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   skip - SSID mismatch
[B]2: cc:5d:4e:44:ba:45 ssid='ZyXEL' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP cc:5d:4e:44:ba:45 ssid='ZyXEL'
Trying to associate with cc:5d:4e:44:ba:45 (SSID='ZyXEL' freq=2412 MHz)[/B]
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP fail=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portControl=Auto
EAPOL: Supplicant port status: Unauthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=13
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=13
Authentication with cc:5d:4e:44:ba:45 timed out.
Added BSSID cc:5d:4e:44:ba:45 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan for wildcard SSID
Scan requested (ret=0) - scan timeout 30 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 2
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No APs found - clear blacklist and try again
Removed BSSID cc:5d:4e:44:ba:45 from blacklist (clear)
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable network found
Setting scan request: 5 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 0 bytes of scan results (0 BSSes)
BSS: Start scan result update 3
BSS: Expire BSS 0 due to no match in scan
BSS: Remove id 0 BSSID 7c:4f:b5:9b:5e:58 SSID 'BabyBear'
BSS: Expire BSS 1 due to no match in scan
BSS: Remove id 1 BSSID 98:fc:11:5b:92:1e SSID ''
[B]BSS: Expire BSS 2 due to no match in scan
BSS: Remove id 2 BSSID cc:5d:4e:44:ba:45 SSID 'ZyXEL'[/B]

[B]Interesting first it found ZyXEL and then complains it can't find it!

[/B]Well I am completely stumped.... Any help is greatly appreciated. Sorry for the long post but I spent quite a while on this I don't know what else to do...

Thanks in advance.

---

### Post by anewguy on 2012-02-01
Right now I don't have a clue, so we'll start with something very basic:

I haven't needed to install wpasupplicant in several releases - it was there and running.  I think this was due to it becoming the predominant encryption.  With that in mind, what release of Ubuntu are you running?

Did you try to connect using WPA without first installing the WPA supplicant package?


Dave ;)

---

### Post by as4556 on 2012-02-01
Hi Dave:

I am running Ubuntu 11.04 (Natty) with 2.6.38-11 generic pae kernel. The first thing I did was just to try connecting it without the wpa supplicant because I didn't even know I needed one, but that didn't work.
This problem is not only restricted to my home wifi. My school has a WPA network as well and I can't connect to it either only their WEP.

- Adith

---

