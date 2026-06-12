---
title: "My wireless is not working"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by peterg943 on 2012-11-26
I am new to the forum and new to Ubuntu. I am a total novice and need help getting my old compaq nx6110 to work wireless. Love what I see so far but would like to use my laptop everywhere. Can someone tell me how to fix this is layman terms?

---

### Post by DuckHook on 2012-11-26
Welcome to the forums and to Ubuntu!

You've come to the right place for help. Here is what we will attempt to do:

I've looked up your model of laptop. The link is here:

[http://h18000.www1.hp.com/products/quickspecs/12135_na/12135_na.HTML](http://h18000.www1.hp.com/products/quickspecs/12135_na/12135_na.HTML)

Apparently, your laptop comes with a number of possible internal wireless cards, and no model numbers are given in any case. So, in order to determine what chipset yours is, open a terminal window and type in:

```
lspci -vvnn | less
```

This will generate a large list of the PCI devices on your laptop. We are looking for the details of your wireless chipset under the paragraph dealing with "network controller" or "network adapter". This is not to be confused with "Ethernet controller/adapter" which is your wired interface.

Please copy and post the results of that paragraph back here using the "code" marks (# marks at top of the page) for easy readability.

It may be easier to redirect the output of the above command and self generate a file for easy posting:

```
lspci -vvnn > ~/Desktop/lspci_output
```

Once we know which chipset you use, we will attempt to locate the proper modules for it.

As preparatory work, do you still have the Windows OEM driver disks for this laptop? As a last resort, we may have to shoehorn in a Windows driver for our wireless card, but usually this is neither desirable nor necessary. However, nice to know if we have that fallback.

---

### Post by wildmanne39 on 2012-11-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by DuckHook on 2012-11-26
Follow Wild Man's instructions instead of mine. If he is looking after your case, you are in good hands.

---

### Post by peterg943 on 2012-11-27
Hi Wild Man,
is this what we need?

pete@pete-HP-Compaq-nx6110-PZ866UA-ABA:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-11-27 18:47:18--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 174.129.218.194, 23.23.141.117, 107.20.132.43, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|174.129.218.194|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2012-11-27 18:47:19 (54.4 MB/s) - `wireless_script' saved [1555/1555]

[sudo] password for pete: 
[sudo] password for pete: 
pete@pete-HP-Compaq-nx6110-PZ866UA-ABA:~$ 


man, is this what we need?

pete@pete-HP-Compaq-nx6110-PZ866UA-ABA:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-11-27 18:47:18--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 174.129.218.194, 23.23.141.117, 107.20.132.43, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|174.129.218.194|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 1,555       --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2012-11-27 18:47:19 (54.4 MB/s) - `wireless_script' saved [1555/1555]

[sudo] password for pete: 
[sudo] password for pete: 
pete@pete-HP-Compaq-nx6110-PZ866UA-ABA:~$

---

### Post by wildmanne39 on 2012-11-27
Hi, this is the file you need to post.
netinfo.txt 

The directions in post 3 tells you where it is.
Thanks

---

### Post by peterg943 on 2012-11-27
I see the file in my home folder but when I copy and paste I only get what's below. Am I doing something wrong?

/home/pete/netinfo.txt

---

### Post by peterg943 on 2012-11-27
how about this?

**** uname -a ****


Linux pete-HP-Compaq-nx6110-PZ866UA-ABA 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****

---

### Post by wildmanne39 on 2012-11-27
Hi, did you open the file? then copy it and paste here.
Thanks

---

### Post by wildmanne39 on 2012-11-27
The file should look like this.

Please use the paper clip in the reply window to attach the file.
Thanks

---

### Post by peterg943 on 2012-11-27
i think so, is it #8

---

### Post by wildmanne39 on 2012-11-27
That is the file but it is only a small part of it, I need to see it all.
Thanks

---

### Post by peterg943 on 2012-11-27
Sorry but I dont know what you mean, guess im over my head!!

---

### Post by wildmanne39 on 2012-11-27
Was there more information in the file that you posted in post 8? 
Did you look at the file I attached?
Thanks

---

### Post by peterg943 on 2012-11-27
**** uname -a ****


Linux pete-HP-Compaq-nx6110-PZ866UA-ABA 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****
*************** info trace ****************



**** uname -a ****


Linux pete-HP-Compaq-nx6110-PZ866UA-ABA 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


02:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f8]
    Kernel driver in use: b43-pci-bridge
--
02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Hewlett-Packard Company NX6110/NC6120 [103c:099c]
    Kernel driver in use: b44


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
arc4                   12473  2 
b43                   342643  0 
mac80211              436455  1 b43
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                86486  0 
i915                  419110  3 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 b43,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158438  8 bnep,rfcomm
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
bcma                   25651  1 b43
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
drm_kms_helper         45466  1 i915
soundcore              14635  1 snd
drm                   197599  4 i915,drm_kms_helper
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b44                    31364  0 
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50691  2 b43,b44


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:14:A5:21:25:FC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:14:38:1F:A2:96

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.32
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1




**** NetworkManager.state ****

Any better?

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****

---

### Post by wildmanne39 on 2012-11-27
Hi, please do exactly what it says to do in this link, post 13.
[http://ubuntuforums.org/showthread.php?p=12375983#post12375983](http://ubuntuforums.org/showthread.php?p=12375983#post12375983)
Thanks

---

### Post by wildmanne39 on 2012-11-27
Also please do: copy and paste for accuracy.
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by peterg943 on 2012-11-27
OK I have the file on the desktop. I did the extract here and opened a terminal. Its asking for a password yet will not let me type it in

---

### Post by wildmanne39 on 2012-11-27
Hi, the password does not show up in the terminal just type it and hit enter, and it is the password you setup when you installed ubuntu.
Thanks

---

### Post by peterg943 on 2012-11-27
I am now talking to you wirelessly!!! I can't believe it but we did it. I can't thank you enough! Wild Man is the MAN.

Thanks,
Pete

---

### Post by wildmanne39 on 2012-11-27
Your welcome! Glad to help, please use thread tools at the top of the page to mark the thread solved.
Enjoy

---

