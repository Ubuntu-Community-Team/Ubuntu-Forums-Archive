---
title: "Asus 1015 pem with BCM4313 not connecting to wifi"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by junapo on 2012-04-30
Hi everyone!
I have an Asus 1015 pem notebook running ubuntu 12.04 after replacing windows 7 starter.
everything works fine except wireless...
It can detect all wireless networks around but is not able to connect to any.
I tried linuxmint12 too,but had the same problem.
My WiFi card is **Broadcom BCM4313** and i found many posts suggesting some different ways of solving this issue, but being new to the Linux world, i'm not sure which way i should go!

Please help me with a solution or redirect me to the right thread if the solution has been given.
Please be detailed if you ask me for more info cause.. you know.. newbie!!

Many thanks!

---

### Post by daslinkard on 2012-04-30
The following commands (one at a time should take care of you)

 	Code:
 	sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf 
The first makes sure that the sta driver is in place, the second  and third blacklist the two drivers brcmsmac and bcma which clash with  the correct sta driver. Copy/paste or make sure your typing is correct!

You may have to reboot the machine for the changes to take effect.

---

### Post by junapo on 2012-04-30
daslinkard, thanks for the quick reply!

After executing the first command:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package echo
E: Unable to locate package blacklist brcmsmac

tried the second, but nothing happened...

any ideas?

---

### Post by daslinkard on 2012-04-30
I'm trying to see what I can come up for you....I found this link [here]("http://ubuntuforums.org/showthread.php?t=1889170")....the only bad thing is that I'm still at work right now....hopefully either you and me, or someone else can get this up and running for you.

---

### Post by junapo on 2012-04-30
ok I'll try this one tomorrow, had a quick look and i think i can manage!
if i get stuck or get it done, i'll get back here!
good chance for me to practice, worst case i reinstall a fresh copy of ubuntu and start over!!

thanks again!

---

### Post by ts3 on 2012-04-30
> **junapo said:**
> After executing the first command:
tried the second, but nothing happened...

any ideas?

There should be a line break before each "echo" command: each of the lines starting with echo should be entered as a separate command whereas it looks like you entered everything on one line and the installer tried to install a package called "echo" and another called "blacklist brcmsmac" and errored out.  The first line, sudo apt-get etc., installs the driver you need for BCM4313, which is called wl (that's WL).  I am not sure but you might need to run it again because it is not clear if the driver installed or not.

The two "echo" commands add the lines 

```
blacklist bcma
blacklist brcmsmac
```

to your /etc/modprobe.d/blacklist.conf file.

You can do this this way, with echo (again, start on new lines for each instance of echo).  Other ways to do the same thing would be to open the etc/modprobe.d/blacklist.conf file with 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

This will open the text editor with root privileges so you'll be able to add the two lines (blacklist bcma and blacklist brcmsmac on two lines as shown above) and save the changes.  You can also use a command-line editor such as nano (very user-friendly) to do the same thing.

At the end of the day for the wireless to work you need to have an installed and loaded wl driver and blacklisted bcma and brcmsmac drivers.  The latter two conflict with wl.  

To check which drivers are loaded and in use run 

```
lspci -k
```

If after blacklisting bcma and brcmsmac (and re-booting) your wireless is not working try

```
sudo rmmod wl
sudo modprobe wl
```

These remove and re-load the wl driver.  

The STA driver option in system settings -> additional drivers should do the same thing, i.e. load the wl driver (at least it did when I installed the 12.04 beta version) but I understand there might be some sort of problem right now so I'd avoid that route & install/uninstall the wl driver either through the command line using apt-get or through the software centre.

---

### Post by junapo on 2012-05-01
Hi there ts3, here is what i did:

1)run
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

2)run
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and entered 
```
#Fix for BCM4313
blacklist bcma
blacklist brcmsmac
```
to the blacklist.conf

3)rebooted

4)run
```
lspci -k
```
with this result
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: AzureWave Device 2047
	Kernel driver in use: wl
	Kernel modules: wl, bcma, brcmsmac

```

5)run
```
sudo rmmod wl
sudo modprobe wl
```
and steps 3,4 with same result

I tried the wifi before step 4 and after 5 and still no joy
Does same thing, just keeps asking for authentication.

I noticed that in the blacklist.conf there was this line
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source echo "blacklist brcmsmac"
```
Looks out of place...

---

### Post by ts3 on 2012-05-02
> **junapo said:**
> 
I noticed that in the blacklist.conf there was this line
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source echo "blacklist brcmsmac"
```
Looks out of place...

Right, it does, the install line got added to your blacklist.conf file.  I think you can safely delete it :) but it might be a good idea to backup blacklist.conf before you start deleting (just open the file and copy/paste into a new document).

As to the wireless it looks like you have the right driver loaded; at this point my wireless just connects but your set-up is probably different.  

I am out of ideas (my knowledge extends as far as getting the wl driver loaded) but you can try the wireless troubleshooting guide here [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) which walks one through the steps of troubleshooting and setting up a connection.    

Also, someone more knowledgeable might step in :)

---

### Post by junapo on 2012-05-03
Thank you for your time ts3
I went through the guide you linked but more or less you 've given me the same info already!

The thing is that the actual problem is not connecting but _authenticating the encryption key_.
Searching around the web i found many references of linux users having trouble with authentication but i can't say if the problem is located to the drivers of the wireless card or something else.

With linuxmint12 had the same problem although some times it connected for some minutes with low speed...

I even used wicd network manager and in both distros i had the same fail message: **BAD PASSWORD**



If someone comes up with a solution i will be grateful!

---

### Post by ts3 on 2012-05-03
> **junapo said:**
> If someone comes up with a solution i will be grateful!

Sorry I can't help more.  For what it's worth, on the wireless & networking subforum there are quite a few posts about broadcom cards dropping the connection or repeatedly asking for passwords.  It might be worth checking them out for ideas.  Cheers.

---

### Post by wildmanne39 on 2012-05-04
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
dmesg | grep wl
lsmod | grep wl
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by junapo on 2012-05-08
Thanks wildmanne39 for the reply and sorry for the delay.
```
napoleon@napoleon-1015PEM:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux napoleon-1015PEM 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux
napoleon@napoleon-1015PEM:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: AzureWave Device [1a3b:2047]
	Kernel driver in use: wl
napoleon@napoleon-1015PEM:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 002 Device 002: ID 056e:0057 Elecom Co., Ltd 
napoleon@napoleon-1015PEM:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:196  Noise level:166
          Rx invalid nwid:0  invalid crypt:22  invalid misc:0

eth0      no wireless extensions.

napoleon@napoleon-1015PEM:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
napoleon@napoleon-1015PEM:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
snd_hda_codec_realtek   174055  1 
ppdev                  12849  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
binfmt_misc            17292  1 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                72919  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
lib80211_crypt_tkip    17275  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wl                   2646601  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414603  3 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14040  2 lib80211_crypt_tkip,wl
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mac_hid                13077  0 
wmi                    18744  1 asus_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
atl1c                  36718  0 
napoleon@napoleon-1015PEM:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        BC:AE:C5:1B:3D:62

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.97
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.254

    DNS:             194.219.227.2


- Device: eth1  [@avoid@] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (configuring)
  Default:           no
  HW Address:        48:5D:60:6D:DC:32

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    @avoid@:         Infra, 00:1D:7E:AE:74:10, Freq 2462 MHz, Rate 0 Mb/s, Strength 67 WPA WPA2


napoleon@napoleon-1015PEM:~$ sudo iwlist scan
[sudo] password for napoleon: 
Sorry, try again.
[sudo] password for napoleon: 
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1D:7E:AE:74:10
                    ESSID:"@avoid@"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-60 dBm  Noise level:-89 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.

```

---

### Post by junapo on 2012-05-15
Help please?

---

### Post by Hadaka on 2012-05-15
from a wired internet connection enter

```

```sudo apt-get install b43-fwcutter firmware-b43-installer

---

### Post by junapo on 2012-05-15
Hadaka this is the result:

```
napoleon@napoleon-1015PEM:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
[sudo] password for napoleon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

that was already done in the previous steps i think..
thanks for the help anyway!

---

### Post by wildmanne39 on 2012-05-16
Hi, I am sorry it has taken me so long to reply I have been ot of town and I did not have access to a computer.

Please post the output of:
```
dmesg | grep wl
lsmod | grep wl
```
Thanks

---

### Post by junapo on 2012-05-16
here it is

```
napoleon@napoleon-1015PEM:~$ dmesg | grep wl
[   17.546069] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.622225] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.622245] wl 0000:02:00.0: setting latency timer to 64
napoleon@napoleon-1015PEM:~$ lsmod | grep wl
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl

```

---

### Post by wildmanne39 on 2012-05-16
Hi, change your network name by taking out the special characters and see if you can connect then if not change your encryption in your router to just wpa2 if possible and change the speed to b/g and take out the n.
Thanks

---

### Post by Chaz46 on 2012-05-16
Hi there, I have the same netbook and when I upgraded to 12.04 I had a really similar problem. This may sound a bit daft but I solved it by disabling the Broadcom drivers all together. Give it a try and let me know how you get on!

---

### Post by junapo on 2012-05-17
Ok, i managed to connect to a "Linksys wireless-G ADSL Home Gateway" router so far before #18 but i still have the encryption problem with a "[SIZE=1]TP-Link Wireless ADSL Modem/Router N150 Annex A TD-W8951N"
[SIZE=2]
I will post #12 again trying to connect to tp-link in 5 hours when I'll be home wildmanne 39, so you see whats wrong there!

Chaz46 i will try your way as a last solution because wildmanne 39 seems to have something going right!;)

Thanks again for your time guys!
[/SIZE] [/SIZE]

---

### Post by junapo on 2012-05-18
ok trying to connect to tp-link
#12 

```
napoleon@napoleon-1015PEM:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux napoleon-1015PEM 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux
napoleon@napoleon-1015PEM:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: AzureWave Device [1a3b:2047]
	Kernel driver in use: wl
napoleon@napoleon-1015PEM:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 002 Device 002: ID 056e:0057 Elecom Co., Ltd 
napoleon@napoleon-1015PEM:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:234  Noise level:164
          Rx invalid nwid:0  invalid crypt:98  invalid misc:0

eth0      no wireless extensions.

napoleon@napoleon-1015PEM:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
napoleon@napoleon-1015PEM:~$ lsmod
Module                  Size  Used by
uas                    17699  0 
usb_storage            39646  0 
joydev                 17393  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
binfmt_misc            17292  1 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67203  0 
psmouse                72919  0 
serio_raw              13027  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
lib80211_crypt_tkip    17275  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
snd_rawmidi            25424  1 snd_seq_midi
wl                   2646601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414603  3 
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
wmi                    18744  1 asus_wmi
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0 
napoleon@napoleon-1015PEM:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        BC:AE:C5:1B:3D:62

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1  [Napoleon] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (configuring)
  Default:           no
  HW Address:        B0:48:7A:E6:A2:64

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SitzinAthen:     Infra, 00:13:33:A1:65:A8, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    phedz:           Infra, 00:1C:A8:83:D0:87, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Papi:            Infra, 00:1C:A2:B5:8E:D1, Freq 2452 MHz, Rate 0 Mb/s, Strength 68 WEP
    ETAD WIFI:       Infra, F8:D1:11:88:15:26, Freq 2452 MHz, Rate 0 Mb/s, Strength 27 WPA WPA2
    Tony:            Infra, A6:3E:61:81:96:A3, Freq 2432 MHz, Rate 0 Mb/s, Strength 14 WPA
    ETAD WIFI 1:     Infra, F8:D1:11:88:23:1A, Freq 2447 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    OTE6479B0:       Infra, BC:76:70:64:79:B8, Freq 2452 MHz, Rate 0 Mb/s, Strength 14 WPA
    Napoleon:        Infra, B0:48:7A:E6:A2:64, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA2


napoleon@napoleon-1015PEM:~$ sudo iwlist scan
[sudo] password for napoleon: 
Sorry, try again.
[sudo] password for napoleon: 
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: B0:48:7A:E6:A2:64
                    ESSID:"Napoleon"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-34 dBm  Noise level:-89 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9F0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601B0487AE6A2641021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000B5472656E64436869704150100800020084103C000100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:13:33:A1:65:A8
                    ESSID:"SitzinAthen"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-89 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1C:A8:83:D0:87
                    ESSID:"phedz"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-98 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 00:1C:A2:B5:8E:D1
                    ESSID:"Papi"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-98 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 05 - Address: BC:76:70:64:79:B8
                    ESSID:"OTE6479B0"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/5  Signal level:-93 dBm  Noise level:-93 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

eth0      Interface doesn't support scanning.

```

---

### Post by wildmanne39 on 2012-05-18
Hi, is Napoleon the network you are trying to connect too?

Did you make all the changes from my last post including setting wireless speed to just b/g?
Thanks

---

### Post by junapo on 2012-05-19
Yes, the network name is Napoleon
changed speed to b/g
but encryption is wpa2-psk there is no wpa2 only selection.
still no joy::-(

---

### Post by wildmanne39 on 2012-05-19
Hi, can you set your encryption to wpa2/AES? if not disable encryption for a few minutes and see if you can connect, also change your channel and see if that helps.
Thanks

---

### Post by junapo on 2012-05-21
tried wpa2 TKIP/AES , wpa2 AES , 3 different channels,
when i removed the encryption, couldn't detect the wifi, found it as hidden.
no connection established, no way!
Just to be clear, I can connect from win7 laptop, android phone and iphone 3 with no problem.

wilmanne 39 if there isn't anything else i can do, there are only 2 steps remaining, just to be sure.
1 do what Chaz46 proposed and if it doesn't work
2 reinstall ubuntu in case something went wrong.

What do you think?

---

### Post by wildmanne39 on 2012-05-21
Hi, if you disable the broadcom all together as sugessted bu chaz46 then will not be able to even detect networks.

Is your network hidden because when you turned of encryption your computer should not have seen it as hidden.

You can also install wicd then uninstall network manager in that order because wicd handles encrption better then network manager.

Please post the output from:
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e etork | tail -n55
```
Thanks

---

### Post by junapo on 2012-05-21
```
napoleon@napoleon-1015PEM:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e etork | tail -n55
[sudo] password for napoleon: 
May 21 19:07:37 napoleon-1015PEM kernel: [   16.254670] wl: module license 'MIXED/Proprietary' taints kernel.
May 21 19:07:37 napoleon-1015PEM kernel: [   16.328660] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 21 19:07:37 napoleon-1015PEM kernel: [   16.328678] wl 0000:02:00.0: setting latency timer to 64
May 21 19:07:37 napoleon-1015PEM kernel: [   16.927976] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140100)
May 21 19:07:37 napoleon-1015PEM NetworkManager[723]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 21 19:07:37 napoleon-1015PEM NetworkManager[723]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
May 21 19:07:37 napoleon-1015PEM dbus[687]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
May 21 19:07:38 napoleon-1015PEM dbus[687]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
May 21 19:07:38 napoleon-1015PEM wpa_supplicant[853]: nl80211: 'nl80211' generic netlink not found
May 21 19:07:38 napoleon-1015PEM kernel: [   18.121299] ACPI Error: [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dswload2-316)
May 21 19:07:39 napoleon-1015PEM NetworkManager[723]: <info> wpa_supplicant started
May 21 21:10:52 napoleon-1015PEM wpa_supplicant[853]: nl80211: 'nl80211' generic netlink not found
napoleon@napoleon-1015PEM:~$ 

```

---

### Post by wildmanne39 on 2012-05-21
Hi, I recommend trying wicd and it will not put an icon in the top panel so you will have to go into apllications and click on it to set it up.
Thanks

---

### Post by junapo on 2012-05-23
Wildmanne 39, solution found!!!

When i turned to wicd i uninstalled network manager but still i had the bad password problem:(
searching the web i found a tip that solved the problem
I just had to fully uninstall nm using these 2:

1)```
sudo apt-get remove --yes network-manager
```

2)```
sudo dpkg --purge network-manager-pptp-gnome network-manager-pptp network-manager
```

rebooted and BOOM i connected with wicd in 4 seconds!!!:guitar:

So finaly 2 steps after ubuntu instalation:
use wl drivers and turn to wicd completely uninstalling nm!

---

### Post by wildmanne39 on 2012-05-23
Hi, I am glad that worked, next time I will make sure to include the command to purge network manager, I use synaptic and I forget not everyone does becasue the configuration files can be purged from there by choosing to remove completely.
Thanks

---

### Post by junapo on 2012-05-23
Thank you for your time and help!

Now i can enjoy one of the best netbooks with THE BEST OS!

---

### Post by junapo on 2012-05-23
OK problem again...
very slow speed and sometimes i get the bad password again
any ideas?
here is the speedtest results
ping:42ms
dl speed:0.61Mbps
ul speed:0.35Mbps
dl is around 8Mbps on wired connection.

---

### Post by wildmanne39 on 2012-05-23
Hi, set your wireless settings to match the screenshots, it will look a litte different since you are using wicd.

I am not sure why you get the bad password sometimes.
Thanks

---

### Post by junapo on 2012-05-25
hi, wicd has no ipv6 settings but with the dns setting its already much better!
Thanks again.

---

### Post by wildmanne39 on 2012-05-25
Hi, that is great, you can use this command to turn off IPV6 also:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Thanks

---

