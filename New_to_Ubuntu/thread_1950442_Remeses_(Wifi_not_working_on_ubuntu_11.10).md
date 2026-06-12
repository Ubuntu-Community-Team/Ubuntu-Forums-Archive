---
title: "Remeses (Wifi not working on ubuntu 11.10)"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by remeses on 2012-03-31
So I've a dell inspiron N-series laptop.. The wireless internet was working fine, but something happened and it is not working now!

I've tried the following commands.. but it is not showing the wireless networks now.. before it did!

     Code:
     sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source 
     Code:
     echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf 
     Code:
     sudo rmmod -f brcmsmac 
     Code:
     sudo modprobe wl

---

### Post by wildmanne39 on 2012-03-31
Hi, ok I gave you a link that had the wrong driver to blacklist, easily fixable, I am sorry my mistake.

Please run:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
remove [COLOR="Red"]blacklist brcmsmac[/COLOR] then save and close gedit, then reboot.
Thanks

---

### Post by remeses on 2012-03-31
Okay, now I can see the connections but I'm having the same problem  again.. can't download anything from software center or terminal.. some  webpages are opening but majority of them aren't.

---

### Post by wildmanne39 on 2012-03-31
Hi, my understanding you could not connect at all before, please post the output of:
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e brc -e firmware -e eth1 -e wpa -e etork | tail -n55
```
```
dmesg | egrep 'brc|firm|radio|switch|eth1'
```
I have to go eat supper.
Thanks

---

### Post by remeses on 2012-03-31
**output for 1st code:**



mutahir@mutahir:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [DesI MundeY] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        1C:65:9D:D9:91:12

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    knet_pppoe_md:   Infra, 02:0C:42:18:AA:E9, Freq 2437 MHz, Rate 0 Mb/s, Strength 20
    KibrisNet_WiFi_2288585: Infra, 00:0C:42:18:AA:E8, Freq 2437 MHz, Rate 0 Mb/s, Strength 24
    *DesI MundeY:    Infra, 54:E6:FC:DC:1E:22, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Cagnet_Wireless_Tel:2237138: Infra, 74:EA:3A:E7:3D:00, Freq 2427 MHz, Rate 54 Mb/s, Strength 14 WPA2
    KibrisNet_DERVIS:Infra, F8:D1:11:35:92:E9, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WPA

  IPv4 Settings:
    Address:         192.168.1.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:4D:A2:C4:77:1E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.5.250
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.5.1

    DNS:             31.209.96.10
    DNS:             31.209.96.11


mutahir@mutahir:~$ sudo iwlist scan
[sudo] password for mutahir: 
Sorry, try again.
[sudo] password for mutahir: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 54:E6:FC:DC:1E:22
                    ESSID:"DesI MundeY"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-12 dBm  Noise level:-96 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700100000000000001000000054E6FCDC1E221021000754502D4C494E4B10230009544C2D57523934314E10240003322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523934314E100800020086103C000101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: F8:D1:11:35:92:E9
                    ESSID:"KibrisNet_DERVIS"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-98 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 03 - Address: 74:EA:3A:E7:3D:00
                    ESSID:"Cagnet_Wireless_Tel:2237138"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:0/5  Signal level:-91 dBm  Noise level:-95 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD850050F204104A0001101044000102103B000103104700100000000000001000000074EA3AE73D001021000754502D4C494E4B10230009544C2D57523734314E10240007312E302F322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734314E100800020086103C000101
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by remeses on 2012-03-31
**output of 2nd code:**



mutahir@mutahir:~$ sudo cat /var/log/syslog | grep -e brc -e firmware -e eth1 -e wpa -e etork | tail -n55
[sudo] password for mutahir: 
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1/wireless): access point 'DesI MundeY' has security, but secrets are required.
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1/wireless): connection 'DesI MundeY' has security, and secrets exist.  No new secrets needed.
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> (eth1): supplicant interface state: completed -> disconnected
Apr  1 06:18:35 mutahir NetworkManager[971]: <info> (eth1): supplicant interface state: disconnected -> scanning
Apr  1 06:19:07 mutahir wpa_supplicant[1076]: Trying to associate with 54:e6:fc:dc:1e:22 (SSID='DesI MundeY' freq=2442 MHz)
Apr  1 06:19:07 mutahir wpa_supplicant[1076]: Association request to the driver failed
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  1 06:19:07 mutahir wpa_supplicant[1076]: Associated with 54:e6:fc:dc:1e:22
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Apr  1 06:19:07 mutahir wpa_supplicant[1076]: WPA: Key negotiation completed with 54:e6:fc:dc:1e:22 [PTK=CCMP GTK=CCMP]
Apr  1 06:19:07 mutahir wpa_supplicant[1076]: CTRL-EVENT-CONNECTED - Connection to 54:e6:fc:dc:1e:22 completed (reauth) [id=0 id_str=]
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> (eth1): supplicant interface state: 4-way handshake -> completed
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'DesI MundeY'.
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Beginning IP6 addrconf.
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Apr  1 06:19:07 mutahir dhclient: Listening on LPF/eth1/1c:65:9d:d9:91:12
Apr  1 06:19:07 mutahir dhclient: Sending on   LPF/eth1/1c:65:9d:d9:91:12
Apr  1 06:19:07 mutahir dhclient: DHCPREQUEST of 192.168.1.108 on eth1 to 255.255.255.255 port 67
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Apr  1 06:19:07 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Apr  1 06:19:08 mutahir NetworkManager[971]: <info> (eth1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  1 06:19:09 mutahir NetworkManager[971]: <info> Policy set 'DesI MundeY' (eth1) as default for IPv4 routing and DNS.
Apr  1 06:19:09 mutahir NetworkManager[971]: <info> Activation (eth1) successful, device activated.
Apr  1 06:19:09 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Apr  1 06:19:09 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  1 06:19:18 mutahir kernel: [  118.467105] eth1: no IPv6 routers present
Apr  1 06:19:28 mutahir NetworkManager[971]: <info> (eth1): IP6 addrconf timed out or failed.
Apr  1 06:19:28 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr  1 06:19:28 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr  1 06:19:28 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Apr  1 06:19:28 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Apr  1 06:19:28 mutahir NetworkManager[971]: <info> Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr  1 06:25:15 mutahir NetworkManager[971]: <info> Policy set 'DesI MundeY' (eth1) as default for IPv4 routing and DNS.

---

### Post by remeses on 2012-03-31
**output for 3rd code:**


mutahir@mutahir:~$ dmesg | egrep 'brc|firm|radio|switch|eth1'
[   22.786818] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
[   24.474133] Console: switching to colour frame buffer device 170x48
[   36.245785] eth1: no IPv6 routers present
[  118.467105] eth1: no IPv6 routers present
mutahir@mutahir:~$

---

### Post by wildmanne39 on 2012-03-31
Hi, first when you use your wireless if you do not disconnect your wired it is overridden by it.

In your router change your encryption to just wpa2 if you have that option instead of wpa/wpa2.

It would be best not to have spaces in your network name.

Set your wireless setting in network manager to look like the screenshots.

The installing software issue may be a completely different issue and it usually is.
Thanks

---

### Post by remeses on 2012-04-02
> **wildmanne39 said:**
> Hi, first when you use your wireless if you do not disconnect your wired it is overridden by it.

In your router change your encryption to just wpa2 if you have that option instead of wpa/wpa2.

It would be best not to have spaces in your network name.

Set your wireless setting in network manager to look like the screenshots.

The installing software issue may be a completely different issue and it usually is.
Thanks
thanks man you are a genius this worked perfectly

---

### Post by remeses on 2012-04-02
i tried the settings you gave me in the pictures and it worked all fine 
can you briefly explain what was causing the problem?
:)

---

### Post by wildmanne39 on 2012-04-02
Hi, the first issue was that you had 2 drivers installed and they were conflicting with each other.

The settings in the screenshot improves speed on most systems by turning off IPV6 and by setting your dns server to google.
Enjoy

---

