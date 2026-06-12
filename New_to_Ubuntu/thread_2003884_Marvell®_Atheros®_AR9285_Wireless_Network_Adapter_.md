---
title: "Marvell® Atheros® AR9285 Wireless Network Adapter NOT TURNING ON!!!"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by meathdeath on 2012-06-14
hello ubuntuforum users,
this is my very first post so sorry if im a little off my rocker in the way that i post but i am wondering if you can help me with my problem. when i flip the wifi switch on my sony  VPCEB32FM laptop the light does not come on and ubuntu has no "enable wireless" option on the internet icon at the top right side of the panel. i was wondering if anybody has had the same or similar issue and how you fixed it:) thank you for replying..
meathdeath

---

### Post by afixane on 2012-06-15
1. Search for a wired network
2. Open "Additional Driver" from unity, or "jockey-gtk" from terminal
3. Click Install blablabla

---

### Post by meathdeath on 2012-06-15
> **afixane said:**
> 1. Search for a wired network
2. Open "Additional Driver" from unity, or "jockey-gtk" from terminal
3. Click Install blablabla

thank you for the quick reply...
i tried that... no proprietry driver are in use on my system.. the thing all of the sudden wont turn on even thought it was working for the past couple weeks without a problem. i tried to run a live cd of ubuntu 12.04 (same distro im on) and the wireless worked. i dont know what this means but im thinking il have to reinstall ubuntu and i dont like that. is there a work around? im on a laptop and so its a pain in the ***.

---

### Post by Mark Phelps on 2012-06-15
Unfortunately, laptop hardware uses specialized drivers for which, all too often, there is no Linux equivalent.  The wireless "buttons" tend to fall into this category.

So, if you get wireless working once you reinstall, you may have no way to disable the wireless from Ubuntu.  That's one of the major downsides of Linux distros -- lack of specialized drivers.

---

### Post by meathdeath on 2012-06-15
thank you for your reply Marc Phelps..
i still think i will continue to use my ethernet cable until someone comes along with a really brilliant idea that none of us have come up with yet. i just wish i could reinstall Ubuntu without losing my stuff i have saved on my hard drive. i have several Gb on my laptop and it would be a pain to go and redownload/setup all of the stuff i have done on my distro so far.

---

### Post by meathdeath on 2012-06-15
***EDIT
The wireless switch was functional until recently so im afraid your theory is incorrect.

---

### Post by wildmanne39 on 2012-06-15
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Mark Phelps on 2012-06-15
> **meathdeath said:**
> ***EDIT
The wireless switch was functional until recently so im afraid your theory is incorrect.

Not necessarily ...

I had a Tablet PC with specialized hardware "buttons" -- which also worked, until there was a kernel upgrade.  After that, they never worked again.  And, I tried different Ubuntu versions for several years before giving up.

So, just like you, I had hardware buttons that worked, for a while, and then, stopped working.

---

### Post by meathdeath on 2012-06-15
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```by clicking on new reply and click # and paste the information between the brackets.
Thank you

tyler@Delorian:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Delorian 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
tyler@Delorian:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
    Subsystem: Sony Corporation Device [104d:9071]
    Kernel driver in use: sky2
tyler@Delorian:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:6409 Microdia Webcam
Bus 002 Device 003: ID 1d38:08aa  
tyler@Delorian:~$ iwconfig
Command 'iwconfig' is available in '/sbin/iwconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
iwconfig: command not found
tyler@Delorian:~$ rfkill list all
Command 'rfkill' is available in '/usr/sbin/rfkill'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
rfkill: command not found
tyler@Delorian:~$ lsmod

this is the results of the code you told me to enter... what does it mean? im an absolute noob... and thank you for your time mr. Phelps but im fairly sure youre not understanding exactly what im saying. thanks for the replies guys:D

---

### Post by wildmanne39 on 2012-06-15
Hi, well most of those commands did not work and that does not make since.

Please try this and see if your wireless comes on make sure the button to the wireless card is on before you paste the command into the terminal.
```
sudo rmmod -f sony-laptop
```
 do not reboot.
Thanks

---

### Post by meathdeath on 2012-06-15
Thank you Wild Manne for replying once again...
the code you gave me was a dead end at least from my observation (even has an ubuntu noob) sorry if i jack it up when i post the code but here is what i got

#[sudo rmmod -f sony-laptoptyler@Delorian:~$ sudo rmmod -f sony-laptop
[sudo] password for tyler: 
tyler@Delorian:~$ sudo rmmod -f sony-laptop
ERROR: Removing 'sony_laptop': No such file or directory
tyler@Delorian:~$ sudo rmmod -f sony-laptop
ERROR: Removing 'sony_laptop': No such file or directory
tyler@Delorian:~$]

---

### Post by meathdeath on 2012-06-15
Wild Manne,
I do not know why or how it worked but i turned off my computer turned on the wifi switch and prayed as it booted up and it worked. i cant explain this but im starting to believe that it was the praying that helped as i had tried this before and it didnt work. Issue solved then?

---

### Post by wildmanne39 on 2012-06-15
Hi, please install wireless-tools and rfkill using software center then post output of:
```
lsmod
/sbin/iwconfig
/usr/sbin/rfkill list
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by wildmanne39 on 2012-06-15
Hi, please post the information and lets see what is going on.
Thanks

---

### Post by meathdeath on 2012-06-15
> **wildmanne39 said:**
> Hi, please install wireless-tools and rfkill using software center then post output of:
```
lmsod
/sbin/iwconfig
/usr/sbin/rfkill list
nm-tool
sudo iwlist scan
``````
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```Thanks

tyler@Delorian:~$ lmsod
No command 'lmsod' found, did you mean:
 Command 'lsmod' from package 'module-init-tools' (main)
lmsod: command not found
tyler@Delorian:~$ /sbin/iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Virus"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:30:A9:5B   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:203   Missed beacon:0

eth0      no wireless extensions.

tyler@Delorian:~$ /usr/sbin/rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
tyler@Delorian:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        54:42:49:EA:70:75

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Virus] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        78:DD:08:C0:1D:3E

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Virus:          Infra, 00:12:17:30:A9:5B, Freq 2437 MHz, Rate 54 Mb/s, Strength 86 WPA
    NETGEAR:         Infra, 00:26:F2:18:BD:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA
    2WIRE869:        Infra, B0:E7:54:EE:80:00, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Maehler:         Infra, 00:22:3F:7C:AF:58, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.100
    DNS:             75.75.75.75
    DNS:             75.75.76.76


tyler@Delorian:~$ sudo iwlist scansudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
[sudo] password for tyler: 
iwlist: unknown command `cat' (check 'iwlist --help').
tyler@Delorian:~$ 

is that what you were looking for?

---

### Post by wildmanne39 on 2012-06-15
Hi, please try the commands again and just copy and paste one line at a time then hit enter and paste the information here then repeat the process for the next command.
Thanks

---

### Post by dodo3773 on 2012-06-15
> 
wlan0 IEEE 802.11bgn ESSID:"Virus" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:12:17:30:A9:5B 

> 
IPv4 Settings:
Address: 192.168.1.105
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1


Looks like it's working to me.

---

### Post by meathdeath on 2012-06-15
> **dodo3773 said:**
> Looks like it's working to me.

yes it is:) i dont know what else he is looking for?

---

### Post by wildmanne39 on 2012-06-15
Hi, I am still looking because the problem may come back and some of the information is not correct because of typo's and I do not want the issue to pop back up because I did not follow through, but if you are happy then so am I.
Enjoy

---

