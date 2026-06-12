---
title: "Wireless: Slightly Moody Boot Up Connection"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by Andavane on 2011-10-07
My Set-up:
Lenovo Thinkpad X201i
Dual Boot &#299; Windows 7 Pro &
Ubuntu 11.04 Natty

All working fine and when I boot up the wireless _always_ connects if I'm going into Windows (which isn't very often) and 
nearly always when I boot into Ubuntu. But not always.
Sometimes it just doesn't connect.
When it did that I would reboot and invariably (but not always) wireless would connect on 2nd boot.
What I do now Is click on the wireless icon in the topbar and disconnect the router, leave it a few seconds, then connect again and the wireless hooks on. Alternatively I click on the icon and take the tick out of "enable wireless" and then the tick back and that nearly always works.

The thing is, I wish I knew what sometimes stops it from hooking on.

Router is:
Billion BiPAC 7300N Wireless N Firewall ADSL2+ Broadband Router.

---

### Post by grahammechanical on 2011-10-07
If you open a terminal and run these two commands you will get information that will help find out if there is interference affecting your connection.

```
nm-tool
```

That will give you a list of all wireless access points in range. Compare the frequency and signal strength of your wireless access point with some others. If they are on the same frequency and the same strength it could make it difficult for network manager to get a strong lock on your signal.

```
sudo iwconfig
```

This will give you the link quality and signal strength of your connection. If there is interference it will also report that.

regards.

---

### Post by Andavane on 2011-10-08
Graham, I replied in a post listing my results but it wouldn't post.
I got:
> You have included 16 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

which suggest to me that it was reading part of the results as smileys. So I will make more replies, splitting them up.
Annoying! I'm not immediately sure how to rectify this.

Anyway here goes with the first half of the response:

Hi Graham,
Many thanks for this. I waited for the problem to re-occur and solved it by removing and reinserting the tick. Here are the results for working and non-working and I'd like to know what your diagnosis is.

1) nm-tool (wireless not working)
2) nm-tool (wireless working)
3) sudo iwconfig (wireless not working)
4) sudo iwconfig (wireless working)

_Results:_

**1)** nm-tool (wireless not working)

> andavane@andavane-think:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:43:DF:F6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto wlan-ap] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        18:3D:A2:22:89:1C

  Capabilities:
    Speed:           121 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *wlan-ap:        Infra, 00:04:ED:D4:30:F4, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    ThomsonD90FFA:   Infra, 00:1F:9F:87:01:35, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    BTOpenzone:      Infra, 02:FE:F4:0E:8A:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 41
    BTFON:           Infra, 12:FE:F4:0E:8A:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 41
    IMTL:            Infra, 00:22:3F:4C:3F:42, Freq 2417 MHz, Rate 54 Mb/s, Strength 31 WEP
    NETGEAR:         Infra, 00:18:4D:FF:BE:58, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    BTHub3-9FTP:     Infra, 00:FE:F4:0E:8A:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    NETGEAR:         Infra, 00:18:4D:3B:E4:CC, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


andavane@andavane-think:~$ 


**2)** nm-tool (wireless working)

> andavane@andavane-think:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:43:DF:F6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto wlan-ap] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        18:3D:A2:22:89:1C

  Capabilities:
    Speed:           162 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NETGEAR:         Infra, 00:18:4D:FF:BE:58, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA
    *wlan-ap:        Infra, 00:04:ED:D4:30:F4, Freq 2412 MHz, Rate 54 Mb/s, Strength 82
    BTHomeHub-D48B:  Infra, 00:1D:68:04:CE:73, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WEP
    ThomsonD90FFA:   Infra, 00:1F:9F:87:01:35, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NETGEAR:         Infra, 00:18:4D:3B:E4:CC, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    BTFON:           Infra, 12:FE:F4:0E:8A:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 51
    BTOpenzone:      Infra, 02:FE:F4:0E:8A:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    IMTL:            Infra, 00:22:3F:4C:3F:42, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WEP
    EdgeWireless:    Infra, 22:CB:4E:30:6B:6E, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA
    BTHub3-9FTP:     Infra, 00:FE:F4:0E:8A:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


andavane@andavane-think:~$


---

### Post by Andavane on 2011-10-08
Now here's the remainder Graham, with the annoying smileys!


**3)** sudo iwconfig (wireless not working)

> andavane@andavane-think:~$ sudo iwconfig
[sudo] password for andavane: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"wlan-ap"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:D4:30:F4   
          Bit Rate=108 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andavane@andavane-think:~$ 


---

### Post by Andavane on 2011-10-08
And finally:

**4)** sudo iwconfig (wireless working)

> andavane@andavane-think:~$ sudo iwconfig
[sudo] password for andavane: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"wlan-ap"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:D4:30:F4   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:29  Invalid misc:0   Missed beacon:0

andavane@andavane-think:~$ 


Kind regards, john

NB: In future will "Disable Smileys in Text" when replying !!

---

