---
title: "fwcutter, WPA and other headache sources"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by maurolust on 2008-05-01
I have tried about every forum entry I could find, and I'm still not able to use my BCM4306 wireless card, nor connect to a wpa protected network. I'm using **xubunTOS** Feisty.

First approach: [http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html](http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html)
This was the default solution for everyone with the same problem as me, but aptget downloads files from *boredklinks* which doesn't exist anymore. David prompts to complete the instalation manually, and that's what I did (but I don't know how to check if the installation was in fact successful).

Now, I'll just post a few outputs from my terminal to show how my system is right now.

 sudo cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 139.82.74.100
netmask 255.255.255.0
gateway 139.82.74.3


iface eth1 inet dhcp
wireless-essid reisnet
wireless-key s:...

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
So I figure my wireless card is eth1.

 iwconfig eth1
```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I had also realized earlier that my netconf utility didn't allow me to use wpa, so I figured it would be useful to enable wpa as well. And there I go again
sudo apt-get install wpasupplicant
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
--10:07:28--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 209.85.141.118
Connecting to boredklink.googlepages.com|209.85.141.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:07:28 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```:mad:
Which reminds me of what happened when downloading fwcutter, but I don't know how to go around it this time.

So, is there any way I can solve this?  What should I do first, install wpasupplicant or is there still some driver incompatibiliby issue? 
Will the repositories ever face the fact that boredklinks is gone?

---

### Post by maurolust on 2008-05-02
Oh, Signal and Noise readings from iwconfig suggest that the wireless card isn't active, is this right? I was standing right next to the Wireless router when I did this, so it should have detected something (either signal or noise).

---

### Post by Sam Lars on 2008-05-31
I've got a bcm4306 also (rev 03), and I have had no luck on WPA.

---

