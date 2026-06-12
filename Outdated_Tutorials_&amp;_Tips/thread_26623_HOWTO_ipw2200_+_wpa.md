---
title: "HOWTO: ipw2200 + wpa"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by luca_linux on 2005-04-13
**[SIZE="5"]PLEASE, PAY ATTENTION: This HowTo was intended for Hoary. If you are running a higher version of Ubuntu, please take a look here: [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)[/SIZE]**



Hi!
I've seen there are many requests about how to get ipw2200 and wpa to work. So, as I've managed to get them to work, I've decided to write a howto. It's also good if you just want to get ipw2200 without wpa; just follow the first part in this case.

We have to compile and install the latest ipw2200 1.0.6 driver from [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net) and we also have to install the firmware, as the ipw2200 0.19 included in the standard installation of Hoary doesn't support wpa.

Since ipw2200 1.0.5, ipw2200 project does not include ieee80211 subsystem anymore, so we also have to compile and install them from [http://ieee80211.sourceforge.net](http://ieee80211.sourceforge.net).

_Since we have to compile the driver from sources, we need the packages: build-essential, gcc, linux-headers-myOwnKernelVersion._
So:
```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install gcc
sudo apt-get install linux-headers-$(uname -r)

```

Note: if you have the kernel sources installed, you won't need the linux-headers. And if you're running a custom kernel compiled by you, you won't need to install the packages mentioned above.

First of all, follow [these instructions](http://www.ubuntuguide.org/#extrarepositories) to add extra repositories, which are always handy to have.

Here are the steps (for newbies: the following commands are supposed to be typed in the same console session):

First of all, download the firmware from [here](http://ipw2200.sourceforge.net/firmware.php?fid=5).
Then install it:
```

sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/

```
Now download the latest ieee80211 subsystem from [here](http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.0.3.tgz?download).
Then untar it and change your current directory into the driver's one:
```

sudo tar xvzf ieee80211-1.0.3.tgz
cd ieee80211-1.0.3

```
Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted:
```
sudo sh remove-old
```
Now download the latest ipw22000 driver from [here](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.6.tgz?download).
Then untar it and change your current directory into the driver's one:
```

cd ..
sudo tar xvzf ipw2200-1.0.6.tgz
cd ipw2200-1.0.6

```
Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted:
```
sudo sh remove-old
```
Now your system is clean and it's time to make and install ieee80211, so:
```

cd ..
cd ieee80211-1.0.3
make
sudo make install

```
Then make and install ipw2200 as well:
```

cd ..
cd ipw2200-1.0.6
make
sudo make install

```
Note: it seems there's currently a bug of remove-old script on some systems; if you get errors when compiling ieee80211 about the presence of old modules, you'll have to delete them manually, after having unloded all ieee80211* modules through "modprobe -r module_name" (type "lsmod" to see the current loaded modules).


Now we have to download and install the wpa_supplicant package:
```

sudo apt-get install wpasupplicant

```
Then you have to create a wpa_supplicant.conf in /etc, so:
```

sudo gedit /etc/wpa_supplicant.conf

```
And paste the following lines in the text editor:
```

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Anyway there are further configuration examples in /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz.

Then reboot to make sure that the new modules are loaded successfully and type:
```
dmesg | grep ipw
``` 
to see if there are errors.
Then type the following command to configurate wpa_supplicant:
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
```
Note: "eth1" is your wireless device.
If you get troubles establishing the connection with the AP, try to take the "-w" flag out.

Some systems may have problems in finding the AP; so, if you get troubles finding your AP, add the "ap_scan=2" option to let wpa_supplicant performing the scan instead of the wireless card driver. So your /etc/wpa_supplicant.conf will look like the following:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Some systems may have problems in connecting to the AP; if you get this issue, try to add the directive "pairwise=TKIP" in the relative network section of /etc/wpa_supplicant.conf, so that it looks like this:
```

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="your_secret_key"
}

```
Of course, if you have problems both findind the AP and connecting to it, you have to add both "ap_scan=2" and "pairwise=TKIP", like the following:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="your_secret_key"
}

```

Now we have to create a small script (first provided by fulco and edited by me) in order to get wpa starting automatically at boot:
```

sudo gedit /etc/init.d/wifi_wpa.sh

```
Here's the script:
```

#! /bin/sh
# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w
fi

exit 0

```
Change the script's permissions to allow it to be executed:
```

sudo chmod +x /etc/init.d/wifi_wpa.sh

```
And create a symlink to define the relative service:
```

sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/S40netwifiwpa

```

Ok, that's all!
I hope this howto will be helpful.

---

### Post by mirtux on 2005-04-13
Thanks for this!

Regards,
MC

---

### Post by justinflavin on 2005-04-14
i dont have wpa on my home network - will Hoary work out of the box so with the ipw2200 card in my Compaq Nx9030 laptop?

---

### Post by luca_linux on 2005-04-14
If you don't need wpa support, you won't need to install wpa_supplicant.
Anyway you had better install the latest driver and firmware from ipw2200.sourceforge.net...so just follow the howto without the latest part concerning wpa_supplicant.

---

### Post by justinflavin on 2005-04-14
i'm not sure if one should do that , unless you really know what you are doing, as that makes your system slightly non-Ubuntu (you've gone out of the apt-get/synaptic way of doing things), and will make your system slightly non-standard (unless you really really need wpa support).

so , the ipw2200 works without wpa , if you just install/upgrade to Hoary?

---

### Post by hamustar on 2005-04-14
hi i have gotten ipw2200 to work without installing any other packages. This was successful in the Beta Array 4 install CD , and now the live Ubuntu 5.04 version.

I have a Compaq Presario 2200 series with 2200BG centrino wlan.
this is what u do, in sudo / root mode,

Step 1
# iwconfig
--  u should see that u have IEEE802.11(B/G) under eth1 (or some other)

Step 2
# iwlist eth1 scan
-- this will scan for all available networks.
-- if there is something picked up, it means ubuntu is able to detect a network.
-- if nothing is detected, pls check your router.

Step 2a: if your wlan network is protected
# iwconfig eth1 essid YOURSSID
-- to define your SSID (access point name)
# iwconfig eth1 key xxxxxxxxxx
-- to define your WEP key, if any.

Step 3
# dhclient eth1
-- this will request a IP from your router, if successfull u will see some messages ending with " bound to 192.168.x.x..." 
-- u are connected to the internet !

hope this helps some of the newbies.

---

### Post by luca_linux on 2005-04-14
Yes, you are right, but the point is that Ubuntu has an old version of the driver (0.19), far from the latest one, that is 1.0.3.
There have been a lot of fixes and new features have been added.
So without installing anything else ipw2200 should basically work, but if you want ehanced features as wpa, you need to follow my howto.

---

### Post by dejitarob on 2005-04-14
Danke, works great!

---

### Post by jerome bettis on 2005-04-14
also if you compile your own kernels and you want this to be built into the source tree instead of having to do it afterward everytime, the following commands work.

cd
wget [http://voxel.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.0.1.tgz](http://voxel.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.0.1.tgz)
cd /usr/src/linux/drivers/net/wireless
tar -xzf ~/ipw2200-1*tgz
mv ipw2200* ipw2200
cd /usr/src/linux
patch -p1 < drivers/net/wireless/ipw2200/patches/ipw2200-*-patch

the latest version does not include the patch file, so you'll need to use the older version, which the first command downloads.  i'm assuming you have the symlink to the kernel source tree in /usr/src/linux.

you'll also need to get the firmware image in place, just like in the first post.  and do not try to build this driver into the kernel, it won't work.  build it as a module.  i just find this way useful because i went through a phase of constantly tweaking the kernel, and it became a real pain to have to manually install the driver everytime.

---

### Post by luca_linux on 2005-04-15
Yes, I knew this solution, but since that driver version doesn't include wpa support, I didn't considered it.

---

### Post by meesmany on 2005-04-15
Hello everybody.
Please forgive my poor Englich.
So i have a Thinkpad T40 with Ubuntu Hoary. It's wonderful.
Ubuntu is for me one of the best distribution and i want to keep it installed.
I had the problem that my wlan only without encryption work "even without wep"
I've tryed this how-to. and i become this.

###########################
jhioui@Thinkpad:~$ sudo dmesg | grep ipw
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.0
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
jhioui@Thinkpad:~$ sudo wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=12):
     53 6f 75 66 69 61 6e 65 57 4c 61 6e               meinssid
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=13): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='meinssid'
Daemonize..
########################

but i still have no connection to my router. or i become no ip from my dhcp.
I dont know what to do. What did i wrong??
Please help me solve this. I don't want to use my wlan without encryption.
Thank you All!!

---

### Post by luca_linux on 2005-04-15
Are you using the latest ipw2100 driver from [http://ipw2100.sourceforge.net?](http://ipw2100.sourceforge.net?)
If not, try to install it.
You also have to download and install the latest firmware.
You can follow my howto. It should be the same, even if you have ipw2100 and not ipw2200.

---

### Post by meesmany on 2005-04-16
Hello,
I have the Latest IPW2100 driver and the latest firmware but it still not work. hier is my output:
##############################################
###########################
jhioui@Thinkpad:~$ sudo dmesg | grep ipw
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.0
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
jhioui@Thinkpad:~$ sudo wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=12):
53 6f 75 66 69 61 6e 65 57 4c 61 6e meinssid
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=13): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
id=0 ssid='meinssid'
Daemonize..
########################
I do deactivate my Cable Network and try wpa_suppliccant but nothing happens????? ](*,)

---

### Post by luca_linux on 2005-04-16
There's no error from your log.
Are you sure you've set the right key or you're allowed to connect to the access point?

---

### Post by meesmany on 2005-04-17
Hello,
I'm really sure I've write allthings right. but it still not works my eth0 become no IP from DHCP.???
But a lot of Thanks for your Help.

---

### Post by domo on 2005-04-17
Hi all,

I followed the howto (thank to you Luca).
After a little fight with the old version of the driver, I finally get this after a reboot:
```
[domo@Xmas:~ $ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

``` 

But, when I launched the wpa_supplicant, I get this loop

```
domo@Xmas:~ $ sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     72 61 62 61 6c 69 6e                              rabalin
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='rabalin'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
Own MAC address: 00:0e:35:26:aa:bb
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     72 61 62 61 6c 69 6e                              rabalin
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
.....

``` 

the strange think is that I set the mode as ad-hoc, and after running wpa_supplicant the mode is unset

```
domo@Xmas:~ $ sudo iwconfig eth1
eth1      unassociated  ESSID:"rabalin"  Nickname:"domo_node"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` 

Did wpa_supplicant don't support the ad-hoc mode ? or did I miss something ?

(forgive my poor english as well :) )

---

### Post by Darrena on 2005-04-17
[QUOTE=domo]Hi all,

I followed the howto (thank to you Luca).
After a little fight with the old version of the driver, I finally get this after a reboot:
```
[domo@Xmas:~ $ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

``` 

But, when I launched the wpa_supplicant, I get this loop

```
domo@Xmas:~ $ sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     72 61 62 61 6c 69 6e                              rabalin
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='rabalin'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
Own MAC address: 00:0e:35:26:aa:bb
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     72 61 62 61 6c 69 6e                              rabalin
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
.....

``` 

the strange think is that I set the mode as ad-hoc, and after running wpa_supplicant the mode is unset

```
domo@Xmas:~ $ sudo iwconfig eth1
eth1      unassociated  ESSID:"rabalin"  Nickname:"domo_node"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` 

Did wpa_supplicant don't support the ad-hoc mode ? or did I miss something ?

(forgive my poor english as well :) )[/QUOTE]
 Domo, How did you remove the old driver?  when I install 1.0.3 I get the following:
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt


I have verified that I updated the firmware..

---

### Post by domo on 2005-04-17
> **Darrena]Domo, How did you remove the old driver?  when I install 1.0.3 I get the following:
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt


I have verified that I updated the firmware..[/QUOTE]
Darrena, as the INSTALL file say:

> Whenever you upgrade your driver, you need to make sure that your system
no longer has older versions of the modules in various locations that
could be found by modprobe instead of the new version.  If you see
problems about unresolved symbols, chances are good you have an old
module someplace.  You can typically find the offending modules via:

        % for i in ieee80211 ipw2200 said:**
> 

So basically, this command display all the file link with your old installation, you have to delete them all.
I don't blame you, I passed more than 1 hours, try to find the info on google instead of reading the INSTALL file :)

I don't understant what mean the second part of the Upgrading section of the INSTALL file:
[QUOTE]You should also check your kernel's configuration for any old
declarations from old installs:

        % for i in IEEE80211 IPW; do \
                grep CONFIG_${i} \
                /lib/modules/`uname -r`/build/include/linux/autoconf.h; done


I don't understand what they means by "check your kernel's configuration". And what else ?
this is what I receive when I enter this command:
[QUOTE]domo@Xmas:~/data/setup/ipw2200/ipw2200-1.0.3 $ for i in IEEE80211 IPW; do \
>                 grep CONFIG_${i} \
>                 /lib/modules/`uname -r`/build/include/linux/autoconf.h; done
#define CONFIG_IEEE80211_MODULE 1
#undef CONFIG_IEEE80211_DEBUG
#define CONFIG_IEEE80211_CRYPT_MODULE 1
#define CONFIG_IEEE80211_WPA_MODULE 1
#define CONFIG_IEEE80211_CRYPT_CCMP_MODULE 1
#define CONFIG_IEEE80211_CRYPT_TKIP_MODULE 1
#define CONFIG_IPW2100_MODULE 1
#undef CONFIG_IPW2100_DEBUG
#define CONFIG_IPW2100_PROMISC 1
#undef CONFIG_IPW2100_LEGACY_FW_LOAD
#define CONFIG_IPW2100_FS_AMILO_M7400_MODULE 1
#define CONFIG_IPW2200_MODULE 1
#undef CONFIG_IPW2200_DEBUG


But I have know clue about what to do  with this, so I let it like it was.

---

### Post by hyapadi on 2005-04-18
This WPA tutorial works like magic for me. Perhaps someone can put it at ubuntulinux.org`s wiki. It will help many people. Thank you very much.

---

### Post by luca_linux on 2005-04-18
[QUOTE=domo]Hi all,

I followed the howto (thank to you Luca).
After a little fight with the old version of the driver, I finally get this after a reboot:
```
[domo@Xmas:~ $ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

``` 

But, when I launched the wpa_supplicant, I get this loop

```
domo@Xmas:~ $ sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     72 61 62 61 6c 69 6e                              rabalin
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='rabalin'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
Own MAC address: 00:0e:35:26:aa:bb
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     72 61 62 61 6c 69 6e                              rabalin
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
.....

``` 

the strange think is that I set the mode as ad-hoc, and after running wpa_supplicant the mode is unset

```
domo@Xmas:~ $ sudo iwconfig eth1
eth1      unassociated  ESSID:"rabalin"  Nickname:"domo_node"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` 

Did wpa_supplicant don't support the ad-hoc mode ? or did I miss something ?

(forgive my poor english as well :) )[/QUOTE]

wpa_supplicant isn't currently able to support ad-hoc mode.

---

### Post by luca_linux on 2005-04-18
[QUOTE=Darrena]Domo, How did you remove the old driver?  when I install 1.0.3 I get the following:
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt


I have verified that I updated the firmware..[/QUOTE]
Are you sure you've replaced all the old modules as I specified in my howto?
Anyway you can follow the domo's post.
The way he suggested is good.

---

### Post by luca_linux on 2005-04-18
[QUOTE=hyapadi]This WPA tutorial works like magic for me. Perhaps someone can put it at ubuntulinux.org`s wiki. It will help many people. Thank you very much.[/QUOTE]
Thanks so much! That's very kind of you.
I'll put it in Ubuntu's official wiki soon.

---

### Post by domo on 2005-04-18
Thank for the answer.

I'm sad to heard that, but at least I know what to do:
Back to WEP and iptables

---

### Post by luca_linux on 2005-04-18
Yes, but don't be sad: I think ad-hoc support will be added in the next release of wpa_supplicant.

---

### Post by hyapadi on 2005-04-19
* Updated *

I have follow this tutorial. Everythings connected. But the problem is, everytime I have to run the wpa_supplicant bla2.. comand, then reactivated the ath0 from networking GUI. Can this process automated?

Any Ideas?

THanks

---

### Post by tomasvilda on 2005-04-19
Here you can find tutorial on [IPW2200 + WPA + connect on startup script](http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_en)

---

### Post by luca_linux on 2005-04-19
I made an edit to my howto: in fact I had written "ipw2000.ko" instead of "ipw2200.ko".

---

### Post by juicewvu on 2005-04-20
when trying to follow this tutorial i recieve the following error(s) when trying to compile the ipw2200 driver:

```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I tried making the /lib/modules/2.6.10-5-386/build directory as it infact does not exist, after which I recieve the following error(s):
```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

```
I'm kind of stuck here, do i need to copy the source files to the /lib/modules/2.6.10-5-386/build directory before trying to compile?


-Juice

---

### Post by luca_linux on 2005-04-20
You have to install the kernel source package and make a symlink.

---

### Post by juicewvu on 2005-04-20
i have the kernel source package installed, and I have made a simlink from the build directory to the directory in where the source files are saved, now attempting to compile gets most of the way through before the scren fills with error 2 errors.

Further investigation reveals that before the error 2's scroll past the screen, the following errors are displayed:
```

make[1748]: execvp: /bin/sh: Argument List too long
make[1748]: Entering directory `\home\jcsmith\ipw2200-1.0.3'
make[1748]: execvp: make: Argument list too long
make[1748: *** [module] Error 127

```

---

### Post by Darrena on 2005-04-20
Ok finally figured it out, I had to remove all the old modules BEFORE I installed the new drivers!  Doh!

---

### Post by wlx on 2005-04-22
hi, I just do as you said.
but when I run dmesg | grep ipw:
> 
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
ipw2200: failed to send POWER_MODE command
 
the last line told me the wireless card is poweroff,but how can I make it power on?

---

### Post by Darrena on 2005-04-22
[QUOTE=wlx]hi, I just do as you said.
but when I run dmesg | grep ipw:
 
the last line told me the wireless card is poweroff,but how can I make it power on?[/QUOTE]


Make sure that your wireless card isn't controlled by an external button, some laptops have a button to do this.

---

### Post by hyapadi on 2005-04-23
[QUOTE=tomasvilda]Here you can find tutorial on [IPW2200 + WPA + connect on startup script](http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_en)[/QUOTE]
It just too much.
All I want is to run "sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd " before the wireless interface up. Is there anyway to do it?

Thx

---

### Post by luca_linux on 2005-04-23
Just create a script with that line and put it under /etc/init.d

---

### Post by hyapadi on 2005-04-23
[QUOTE=luca_linux]Hi!
I've seen there are many requests about how to get ipw2200 and wpa working. So, as I've managed to get them to work, I've decided to write a howto.

We have to compile and install the latest ipw2200 1.0.3 driver from ipw2200.sourceforge.net and we also have to install the firmware, as the ipw2200 0.19 included in the standard installation of hoarty doesn't support wpa.
Here are the steps:
First of all, download the firmware from [here]("http://ipw2200.sourceforge.net/firmware.php?fid=4").
Then install it:
```

sudo tar xvzf ipw2200-fw-2.2.tgz
sudo cp ipw-2.2-*.fw /usr/lib/hotplug/firmware/

```
Now download the latest driver from [here]("http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.3.tgz?download").
Then install it:
```

sudo tar xvzf ipw2200-1.0.3.tgz
cd ipw2200-1.0.3
make
sudo make install

```
Then you have to copy all the modules it installs from /lib/modules/$(KVER)/drivers/net/wireless/ to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ and /lib/modules/$(KVER)/drivers/net/wireless/ipw2200.ko to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ipw2200/, since there's currently a bug in their location: in fact ipw2200 installs its modules in the first directory, while Ubuntu loads them from the second directory.

Now we have to download and install the wpa_supplicant package:
```

sudo apt-get install wpasupplicant

```
Then you have to create a wpa_supplicant.conf in /etc, so:
```

sudo gedit /etc/wpa_supplicant.conf

```
And paste the following lines in the text editor:
```

network={
       ssid="your_network_name"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Anyway there are further configuration examples in /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz.

Then reboot to make sure that the new modules are loaded successfully and type:
```
dmesg | grep ipw
``` 
to see if there are errors.
Then type the following command to configurate wpa_supplicant:
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
```
Note: "eth1" is your wireless device.

Ok, that's all!
I hope this howto will be helpful.[/QUOTE]

* additional settings*
edit /etc/default/wpasupplicant to activate the wpasupplicant during boot.

Here I attatched my configuration file :
> # /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless Driver
#  -i <ifname>		Interface (required, unless specified in config)
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

OPTIONS="-w -D madwifi -i ath0 -c /etc/wpa_supplicant.conf -dd" 

Although the wpasupllicant can be run automatically during boot, I still have to reactivate the wireless card in the network configuration. Can anyone help?

Thanks

---

### Post by tomasvilda on 2005-04-26
Please look few posts higher there is links to other Tutorial IPW2200 + WPA with startup script.

---

### Post by firas on 2005-04-29
Thanks for the HOWTO luca_linux. However I'm having the same problem as meesmany. I have an IBM ThinkPad T41 with an ipw2100. I downloaded the latest firmware and source for ipw2100. Copied the firmware to the right folder, compiled the drivers and copied them to the right folder. Installed and configured wpasupplicant.conf just like you mentioned with my own essid and psk ofcourse but I can't get my card to associate with my LinkSys WAG54G ap. Here is the output from some commands:

```

firas@ibm-t41:~$ dmesg | grep ipw2100
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.0
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

firas@ibm-t41:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=11):
     61 6c 72 61 67 6f 6d 2d 6e 65 74                  my-essid
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='my-essid'
Daemonize..

firas@ibm-t41:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I even tried setting my essid manually using iwconfig eth1 essid my-essid to no avail. I disabled WPA on my AP and was able to connect just fine using iwconfig. 

Can anyone shed any light on this problem ? I'm really getting desperate here, I've spent days on this with no luck.

And a little off topic here. How can I disable IPv6 on my laptop (the sit0 interface) permanently ?

---

### Post by DLM on 2005-05-02
[QUOTE=luca_linux]You have to install the kernel source package and make a symlink.[/QUOTE]

Forgive me, but how would one go about doing this?

*EDIT* nevermind, I figured it out.  but now, when I dmesg | grep ipw, I get ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Radio Frequency Kill Switch is On:
ipw2200: Already sending a command
ipw2200: failed to send SCAN_REQUEST_EXT command
  as output.

TO be honest, I have no real clue as to what I'm doing (this is day one of me using linux).  How do I activate my wireless after a set it up?

---

### Post by kiranos on 2005-05-03
What do I type in my interfaces file in /etc/network/ for the wireless card?

As default it got eth0 when I installed but I chose eth1 LAN card to install on. So no entry was given in interfaces for eth0 so my wireless card aint conifgured. What do you guys have in it? also It got eth0 not wlan0 or what I have seen before.

---

### Post by luca_linux on 2005-05-03
[QUOTE=DLM]Forgive me, but how would one go about doing this?

*EDIT* nevermind, I figured it out.  but now, when I dmesg | grep ipw, I get ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Radio Frequency Kill Switch is On:
ipw2200: Already sending a command
ipw2200: failed to send SCAN_REQUEST_EXT command
  as output.

TO be honest, I have no real clue as to what I'm doing (this is day one of me using linux).  How do I activate my wireless after a set it up?[/QUOTE]
 You should install the latest ipw2200 driver rather than using the old one included in Ubuntu (0.19).

---

### Post by luca_linux on 2005-05-03
[QUOTE=kiranos]What do I type in my interfaces file in /etc/network/ for the wireless card?

As default it got eth0 when I installed but I chose eth1 LAN card to install on. So no entry was given in interfaces for eth0 so my wireless card aint conifgured. What do you guys have in it? also It got eth0 not wlan0 or what I have seen before.[/QUOTE]
 I've got a gigabit ethernet card as eth0 and the wireless one as eth1 automatically since the installation.
Anyway, you should be able to change the interfaces from System-->Administration-->Network.

---

### Post by kiranos on 2005-05-03
I now get:

ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt

when I type "dmesg | grep ipw" I have rebooted but it's still the same :(

In  /lib/moduels/kernelversion/kernel/drivers/net/wireless/ I have 4 iee80211_crypt*.ko files and ieee80211.ko and in wireless/ipw2200 I have the ipw2200.ko file but it doesnt work. Anyone know what it might be?

---

### Post by luca_linux on 2005-05-03
As already said, it's due to the presence of old modules...you should remove all the modules ipw2200.ko and ieee80211*.ko and then install the latest driver again and copy them as said in the howto.

---

### Post by kiranos on 2005-05-03
ok thanks will try. I have them compiled in another directory so it will be easy. Again to the interfaces file. What do you have in yours there for your wireless nick? I'm going to run with WPA and if I use wpa_supplicant I put my wpa_psk in another file than interfaces so I dont know what to have in my interfaces file. is it just ip, gateway, subnet or is what goes there?

EDIT: found the problem, the modules should go in wireless/ieee81102/ and not straight into wireless as I did :) glad I found it, still dont know what to do about the interfaces file though.

---

### Post by luca_linux on 2005-05-03
Here's my interfaces file (/etc/network/interfaces):
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x

iface eth1 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
wireless-essid MyEssid

auto eth1

---

### Post by kiranos on 2005-05-03
[QUOTE=luca_linux]Here's my interfaces file (/etc/network/interfaces):
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x

iface eth1 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
wireless-essid MyEssid

auto eth1[/QUOTE]
 ah thanks will try it.

---

### Post by luca_linux on 2005-05-03
Note that I don't use DHCP but static IP addresses.

---

### Post by kiranos on 2005-05-03
I do aswell I'm using NAT. I got it to work. Think of that :) I have to topy in "sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd" everytime I reboot though. Now it's just time to make some personal notes so I dont have to get all these prolems next time thanks for all your help.

---

### Post by DLM on 2005-05-03
so, now I need to install my old driver that came with ubuntu.
	% for i in ieee80211 ipw2200; do \
		find /lib/modules/`uname -r` -iname ${i}*; done

is what I'm told to do.  But what exactly does this mean?
It's not a command, except for the 'find'.  what exactly do the above ines mean?

(once again, sorry, excuse my lack of any real knowledge :-\)
And thanks for being patient with m.

---

### Post by luca_linux on 2005-05-03
Just make a search for ipw2200.ko and ieee80211*.ko modules and delete them; then install the latest driver.

---

### Post by DLM on 2005-05-03
when I do locate ipw2200.ko, I only get one location, /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200/ipw2200.ko, which is where I just installed it.  same with iee80211

---

### Post by luca_linux on 2005-05-04
Are you sure they are the right new modules and not the old ones? Look at the date of the files and check...

---

### Post by DLM on 2005-05-04
ok, so, when I dmesg | grep ipw now, I get
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

which, I assume, is what I want to get.  so, I've set up my /etc/wpa_supplicant.conf file.  But, I cant get on with my wireless network still, even after I sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
.  

(WHich I get 

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=4):
     64 61 76 65                                       dave
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='dave'
Daemonize..
from)

WHat else is thre that could be wrong?

---

### Post by radhaz on 2005-05-04
I'm feeling pretty stupid at the moment.  When I attempt from a root terminal 
```

sudo tar xvzf ipw2200-1.0.3.tgz
cd ipw2200-1.0.3
make
sudo make install 
```

I get an error to the effect of ```
 
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/ipw2200-1.0.3 modules
make *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I foolishly attempted to make the directory (this is my 2nd distro and 4th day of trying to get wireless working :( so this was out of sheer desperation lol) and the error I got was ```

make[1] Entering directory '/lib/modules/2.6.10-5-386/build'
make[1] *** No rule to make target 'modules'. Stop.
make[1] Leaving directory '/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

```

I feel like the village idiot at the moment, I appreciate any help that anyone care's to offer.

Respectfully,
RadHaz

Edit:  I couldn't run the command string found in the install file, ubuntu didn't like the "do" argument?  I did manually remove the instances of ipw and ieee80211 though.  I rebooted and did the modprobe and dmesg and came up with 0 instances of either module.

---

### Post by luca_linux on 2005-05-05
[QUOTE=DLM]ok, so, when I dmesg | grep ipw now, I get
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

which, I assume, is what I want to get.  so, I've set up my /etc/wpa_supplicant.conf file.  But, I cant get on with my wireless network still, even after I sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
.  

(WHich I get 

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=4):
     64 61 76 65                                       dave
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='dave'
Daemonize..
from)

WHat else is thre that could be wrong?[/QUOTE]
 It looks like ok.
Are you sure you don't have any other protection on your router such as MAC Address filtering?
If you disable WPA, are you able to connect?

---

### Post by luca_linux on 2005-05-05
[QUOTE=radhaz]I'm feeling pretty stupid at the moment.  When I attempt from a root terminal 
```

sudo tar xvzf ipw2200-1.0.3.tgz
cd ipw2200-1.0.3
make
sudo make install 
```

I get an error to the effect of ```
 
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/ipw2200-1.0.3 modules
make *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I foolishly attempted to make the directory (this is my 2nd distro and 4th day of trying to get wireless working :( so this was out of sheer desperation lol) and the error I got was ```

make[1] Entering directory '/lib/modules/2.6.10-5-386/build'
make[1] *** No rule to make target 'modules'. Stop.
make[1] Leaving directory '/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

```

I feel like the village idiot at the moment, I appreciate any help that anyone care's to offer.

Respectfully,
RadHaz

Edit:  I couldn't run the command string found in the install file, ubuntu didn't like the "do" argument?  I did manually remove the instances of ipw and ieee80211 though.  I rebooted and did the modprobe and dmesg and came up with 0 instances of either module.[/QUOTE]
 As said in some previous posts, you have to install the packages: build essentials, kernel hearders.

---

### Post by The Warlock on 2005-05-05
[QUOTE=luca_linux]As said in some previous posts, you have to install the packages: build essentials, kernel hearders.[/QUOTE]
[post edited]

I was having the same problem as RazHat here, except I'm using the AMD64 version.
Okay, so I installed build essentials and kernel headers and linux source and whatnot, and I set up my symbolic links and everything, and now instead of the one error message, I get about FIFTY GRILLION compiler errors if I use make. 

And my card isn't working with the built-in .19 driver at all! It's not even showing up as eth1.

What do I do?

---

### Post by luca_linux on 2005-05-05
Are the packages you've installed for AMD64? Especially the kernel headers...

---

### Post by The Warlock on 2005-05-05
[QUOTE=luca_linux]Are the packages you've installed for AMD64? Especially the kernel headers...[/QUOTE]

Why, of course not! :D 

Okay, so I got the CORRECT packages and it compiled and installed and modprobed without a problem. It even shows up in that Network Settings thing now. The only problem is that it doesn't actually work, and in the Network Settings thingy it shows it as grayed out with the message "The interface eth1 is not configured". When I [FONT=Courier New]dmesg | grep ipw[/FONT] I don't get any error messages, either.

Did I miss something? (It's not the firmware, I installed that).

Edit: NEvermind, I fixed it. I had to configure it. This should have been obvious to me earlier, but it's been a LONG day. Sorry.

---

### Post by fulco on 2005-05-05
I am a linux newbie and I had problems to get my Intel PRO/Wireless 2200 card working. My problems were:

[list]
[*]Getting WPA to work
[*]Recovering from the inevitable disconnects without rebooting
[/list]  

Using the information in this great thread (thank you, luca_linux!), a nice disconnect solution by [snop](http://www.ubuntuforums.org/showthread.php?t=21056&page=2&pp=10&highlight=mywirelessdevice) and some info I found in other places on the web I managed to get things working.

I will put my story here, hoping it will be helpful to some, especially newbies like me :-).
**Beware: since I am a total newbie I probably have made some rather silly mistakes.**
Hopefully there will some Ubuntu / Linux wizards there to correct me!

Ok enough talk. Let's get on with it.

First things first: make sure you meet the following requirements below before proceeding!
[i]
1. You have an Intel PRO/Wireless 2200 card (obviously)
2. It doesn't work 'out of the box' with Ubuntu (probably why you read this)
3. Not a requirement but a tip: start with a fresh Ubuntu installation! If you have been messing with your system trying to get Wifi working -like i did the first time- my instructions might not work.
4. Make sure your system is connected to the internet by using the wired ethernet connection (wireless isn't working, obviously!). This comes in handy for downloadable packages and help.
5. Make sure you have the Universe repositories enabled so you can download the 
packages needed. What's that? Go to System, Administration, Synaptic Package Manager, Settings, Repositories, Settings, Show disabled software sources, and select the binary software sources marked "Community maintained (Universe)". Do a "reload" in Synaptic Package Manager to make sure all packages show up.
6. Make sure you perform all commandline actions as "root" (Applications, System Tools, Root Terminal. Just be careful with what you do in there!).
7. Make sure that the package build-essential is marked installed under "Development" in the Synaptic package manager (it must be checked, unchecked means not installed). If not check it and apply, or do a "apt-get install build-essential" in the Root Terminal.
[/i]

Now that is out of the way, let's start with Luca's HowTo:

**Step 1: Install firmware (optional)**
If you need this depends. With my fresh Ubuntu install, the same firmware files were already in: /lib/hotplug/firmware (just with a slightly different filename, ending with the kernel version), so I did not install it in /usr/lib/hotplug/firmware/ like Luca did.

```

sudo tar xvzf ipw2200-fw-2.2.tgz
sudo cp ipw-2.2-*.fw /usr/lib/hotplug/firmware/

```

**Step 2: Install driver**
I did as Luca suggested, but I made sure I did a make uninstall first just to be sure. (You might first want to stop any present ipw2200 driver here by a "modprobe -r ipw2200").

```

sudo tar xvzf ipw2200-1.0.3.tgz
cd ipw2200-1.0.3
make
make uninstall
make
make install

```

If there are no errors you are still in business. I had problems doing this with my first, messed-up Ubuntu installation. When I did a fresh install things were fine.

**Step 3: Copy the modules to another location (optional)**
Luca suggests you copy the modules you just made

from /lib/modules/$(KVER)/drivers/net/wireless/
to    /lib/modules/$(KVER)/kernel/drivers/net/wireless/

I did not do this and had no problems with it.

**Step 4: Check if the driver works**
The best thing to do first is make sure you have an open network at this time (no WPA, no WEP, no MAC security). Also it might be a good idea to use a static IP. Configure your Wireless connection in the network settings according to your network IP range. Now let's enable the driver.

```

modprobe ipw2200
dmesg | grep ipw

```

If it works you will see something like this:

```

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

```

**Step 5: Install wpasupplicant (only if you need WPA)**
No surprises here, just do as Luca suggests: install it and edit the .conf file.

```

sudo apt-get install wpasupplicant
sudo gedit /etc/wpa_supplicant.conf

```

Insert these lines of code in the wpa_supplicant.conf file, and make sure you get your ssid and psk right:

```

network={
       ssid="your_network_name"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```

Now restart the ipw2200 driver and run wpa_supplicant. Make sure that you use the right interface. On my notebook, eth0 is the wireless interface. Luca uses eth1. You can check yours in System, Administration, Networking.

```

modprobe -r ipw2200
modprobe ipw2200
wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D ipw -w -dd

```

**Step 6: Check if WPA is working**
Just remember to restart your accespoint in WPA mode with the right key! If it works: jump, run circles around your Ubuntu CD, get a beer, enjoy! If not, see if you (or I) missed something in the steps above.


**Step 7: Make wpa_supplicant start at boottime**
...and even better: make sure that if the connection goes down, it will go up again automatically!

*a. Make a python script that does the reconnect thing*
I just made a file with the silly name rewifi.py as shown below and make it executable. This script scans for a disconnected Wifi device and reconnects if needed. Make sure you put the right interface at MYWIRELESSDEVICE.

```

gedit /usr/local/bin/rewifi.py

```

```

#!/usr/bin/env python

from time import sleep
from os import system

#Check for your wireless device typing iwconfig in a terminal and assign
#your device here (it can be eth0, eth1, etc...)
MYWIRELESSDEVICE = 'eth0'

while (1):
	#Wait for 15s
	sleep(15)
	
	#Reload the module when the connections drops	
	if system('iwconfig ' + MYWIRELESSDEVICE + ' | grep 00:00:00:00:00:00 > /dev/null') == 0:
		#Wait for 5 seconds more, just in case our connection comes back (we may be just 
		#moving our laptop from one place to another)
		sleep(5)
		if system('iwconfig ' + MYWIRELESSDEVICE + ' | grep 00:00:00:00:00:00 > /dev/null') == 0:
                        system('killall wpa_supplicant')
			system('/sbin/rmmod ipw2200')
			system('/sbin/modprobe ipw2200')
			system('/etc/init.d/networking restart')
                        system('/usr/sbin/wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D ipw -w')

```

```

chmod +x /usr/local/bin/rewifi.py

```

*b. Make a script in /etc/init.d to start rewifi.py on boot*
This goes much the same way as step a.

```

gedit /etc/init.d/rewifi.sh

```

```

#! /bin/sh
# wifi re-init on disconnect + wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D ipw -w
fi

if ! [ -x /usr/local/bin/rewifi.py ]; then
    exit 0
fi

echo " * [Wifi]: Enabling script for automatic Wifi re-initialization on disconnect..."
/usr/local/bin/rewifi.py &

exit 0

```

```

chmod +x /etc/init.d/rewifi.sh

```

*c. Make sure your script is started*
This is done by putting a symlink "S40netwifi" in /etc/rcS.d. Like this it starts just before S40networking. If you want to start it after you can use " S41netwifi" or an even higher number.

```

ln -s /etc/init.d/rewifi.sh /etc/rcS.d/S40netwifi

```

*d. Lazy me* 
If you are lazy, you can just put these scripts in one place, edit them there and then reinstall them. For example:

```

#! /bin/sh
# this script installs auto Wifi re-init on disconnect + WPA support with wpa_supplicant
cp rewifi.py /usr/local/bin/
cp rewifi.sh /etc/init.d/
ln -f -s /etc/init.d/rewifi.sh /etc/rcS.d/S40netwifi

```

Well that's about it. It took me some time but seems to work fine for me. Hopefully this will help someone.

---

### Post by DLM on 2005-05-05
question:the wireless network I am connecting to has a hidden ssid.  would that make a difference?

---

### Post by radhaz on 2005-05-05
[QUOTE=luca_linux]As said in some previous posts, you have to install the packages: build essentials, kernel hearders.[/QUOTE]

Thanks for the straightforward advice.  I fired up synaptic and snagged the build essentials and the kernel headers and the drivers installed without a hitch!

Now its just a matter of finding a way to get the wpasupplicant to my laptop (which doesnt have a net connection until I get the wifi working).  Is there a way to download packages manually and xfer them to CD?

Thanks for the help.

---

### Post by DLM on 2005-05-05
also, we do have mac address filtering on the router, but I can still get on with windows, so I know mine is on there,

---

### Post by Psquared on 2005-05-05
Interesting discussion. I suppose I will have to compile and install the IPW2200 because my wifi gets dropped about every other time I start Linux.

My output is as follows:

dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright (c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x0000010, Config: 00000142
ipw2200: Start IPW Event Log Dump:

Funny thing is my wireless is working as I write this. Also, on bootup, when network services are starting, I see errors sometimes (not always), but the wireless works.

I know I need the new version of the driver, but I'm a little gunshy right now. I wonder when Ubuntu will upgrade this via apt-get?

---

### Post by radhaz on 2005-05-05
Final Follow-up of the battle for n00bs with inspiron 9300's like me who dont have internet capable systems (yet)

1. Copied wpa_supplicant from the repository found [here](http://packages.ubuntu.com/hoary/net/wpasupplicant) (Note the newer debian version wasn't compatible with ubuntu, but I had to try)
2. Burned it to CD
3. Copied it from CD to the HD of the laptop
4. From the directory I unpacked (if that's what its called) the file using "dpkg -i [package name]"
5. Continued on with the wpa_supplicant instructions as found in the original tutorial.

Thanks to everyone who contributed to this post!

---

### Post by luca_linux on 2005-05-06
[QUOTE=DLM]question:the wireless network I am connecting to has a hidden ssid.  would that make a difference?[/QUOTE]
 Don't worry about: in wpa_supplicant we set "scan_ssid=1" that's just used to connect to a hidden ssid.

---

### Post by luca_linux on 2005-05-06
[QUOTE=Psquared]Interesting discussion. I suppose I will have to compile and install the IPW2200 because my wifi gets dropped about every other time I start Linux.

My output is as follows:

dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright (c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x0000010, Config: 00000142
ipw2200: Start IPW Event Log Dump:

Funny thing is my wireless is working as I write this. Also, on bootup, when network services are starting, I see errors sometimes (not always), but the wireless works.

I know I need the new version of the driver, but I'm a little gunshy right now. I wonder when Ubuntu will upgrade this via apt-get?[/QUOTE]
 Yes, your problem depends on the old driver.
I don't know if there will be an updated version soon available in the repositories, but you really should update it manually.

---

### Post by luca_linux on 2005-05-06
@ fulco: the python script is useless since the disconnecting issue has been fixed in 1.0.3 driver version.
The sh script for booting is really useful, instead. Thanks!

---

### Post by luca_linux on 2005-05-06
I've edited my howto in order to get wpa starting automatically at boot (I edited the sh script provided by fulco).

---

### Post by fulco on 2005-05-06
[QUOTE=luca_linux]@ fulco: the python script is useless since the disconnecting issue has been fixed in 1.0.3 driver version.
The sh script for booting is really useful, instead. Thanks![/QUOTE]
@luca: for me it is useful, because my Wifi regularly disconnects in the house. This is not a driver issue (I use 1.0.3) but an issue with my reception quality due to walls, distance, electronic equipment. The problem was that, once it was disconnected, it would not reconnect automatically. Disabling/enabling the network interface would not reconnect me either. So only unloading and reloading de driver with a modprobe works for me (or rebooting, obviously). I have seen more people with this problem on this forum.

Another thing (which might actually make my bootscript useless for you if you dont use the python script): I now added these lines to my **/etc/network/interfaces** to (re)init wpa_supplicant (found it in the WPA WiKi):

```

up   /usr/sbin/wpa_supplicant -B -w -D ipw -i eth0 -c/etc/wpa_supplicant.conf -qq
down killall wpa_supplicant


```

This works great too. I now just use the bootscript for starting the python script that just bothers with modprobing the driver in case of connectionloss, and leave bringing up wpa_supplicant to /etc/network/interfaces.

---

### Post by ChamPro on 2005-05-10
Okay... I have the kernel headers (linux-headers-686) and the build essential meta packages installed. Do I still need the kernel source too? (linux-source-2.6.10)

I have no idea where I'm supposed to create a kernel symlink. I looked all over the forums, but couldn't find the directory I'm supposed to point to.

[QUOTE=radhaz]Thanks for the straightforward advice.  I fired up synaptic and snagged the build essentials and the kernel headers and the drivers installed without a hitch![/QUOTE]

---

### Post by radhaz on 2005-05-12
[QUOTE=ChamPro]Okay... I have the kernel headers (linux-headers-686) and the build essential meta packages installed. Do I still need the kernel source too? (linux-source-2.6.10)

I have no idea where I'm supposed to create a kernel symlink. I looked all over the forums, but couldn't find the directory I'm supposed to point to.[/QUOTE]

I didn't need to install the kernel source to get it up and running  :?

---

### Post by ChamPro on 2005-05-12
I'm still getting this error when I try to make.
```
make[1] Entering directory '/lib/modules/2.6.10-5-386/build'
make[1] *** No rule to make target 'modules'. Stop.
make[1] Leaving directory '/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2
```[QUOTE=radhaz]I didn't need to install the kernel source to get it up and running  :?[/QUOTE]

---

### Post by luca_linux on 2005-05-12
Install the package linux-tree-2.6.10 too and type at console the following commands:
```

ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-5-386/build

```
It should work now.

---

### Post by ChamPro on 2005-05-12
Thanks for being explicit for a newbie, however (always a but isn't there). I unpacked the source into that directory and used those two links (the second one I modified to 686). I then tried the make command and I have a crazy amount of warnings and errors. I really don't know what's up condering this install of Ubuntu is only a week or two old.

My errors end with this for make install. Thanks for your help.
```
/home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200.c:7730: error: storage size of `ipw_wx_handler_def' isn't known
/home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200.c:8097: error: storage size of `ipw_ethtool_ops' isn't known
{standard input}:6009: Error: symbol `channel' is already defined
{standard input}:7534: Error: symbol `mode' is already defined
make[2]: *** [/home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200.o] Error 1
make[1]: *** [_module_/home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
make: *** [modules] Error 2
```
[QUOTE=luca_linux]Install the package linux-tree-2.6.10 too and type at console the following commands:
```

ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-5-386/build

```
It should work now.[/QUOTE]

---

### Post by luca_linux on 2005-05-12
Try to manually copy the modules (made in the ipw2200-1.0.3 dir) into the right directories specified in the howto.

---

### Post by ChamPro on 2005-05-13
Wow... I really don't know what the #*&$ is going on. I haven't had this much trouble with Ubuntu ever.

Here's the beginning of the list of warnings I get when executing make. I tried changing the permissions of a lot of directories to no avail. The make and make install creates no kernel modules whatsoever.
```
zoph@nebosuke:~/Desktop/Downloads/ipw2200/ipw2200-1.0.3$ make
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/home/zoph/Desktop/Downloads/ipw 2200/ipw2200-1.0.3 MODVERDIR=/home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.10'
Makefile:484: .config: No such file or directory
  CC [M]  /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200.o
In file included from include/linux/module.h:9,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/sched.h:4:37: asm/param.h: No such file or directory
In file included from include/linux/types.h:13,
                 from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/posix_types.h:47:29: asm/posix_types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/types.h:14:23: asm/types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/types.h:18: error: syntax error before "__kernel_dev_t"
include/linux/types.h:18: warning: type defaults to `int' in declaration of `__k ernel_dev_t'
include/linux/types.h:18: warning: data definition has no type or storage class
include/linux/types.h:21: error: syntax error before "dev_t"
include/linux/types.h:21: warning: type defaults to `int' in declaration of `dev _t'
```
Maybe I'm heading for a another format. Lovely.

[QUOTE=luca_linux]Try to manually copy the modules (made in the ipw2200-1.0.3 dir) into the right directories specified in the howto.[/QUOTE]

---

### Post by MonkeyWrench32 on 2005-05-13
ChamPro, I'm getting the same errors and I have no clue what do to either.  :(

---

### Post by gondoi on 2005-05-14
Man I don't know what's going on here... Everyone seems to be able to get wpasupplicant in a snap.  Maybe it's because i'm new to Ubuntu and i'm missing a repository, but I keep getting this when i try to apt-get the wpasupplicant:

```
~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wpasupplicant
```

---

### Post by MonkeyWrench32 on 2005-05-14
I was able to fix this error:

Makefile:484: .config: No such file or directory

From this reference:  [http://www.linuxquestions.org/questions/showthread.php?threadid=311810](http://www.linuxquestions.org/questions/showthread.php?threadid=311810)

No clue on the rest, though.

---

### Post by luca_linux on 2005-05-14
[QUOTE=gondoi]Man I don't know what's going on here... Everyone seems to be able to get wpasupplicant in a snap.  Maybe it's because i'm new to Ubuntu and i'm missing a repository, but I keep getting this when i try to apt-get the wpasupplicant:

```
~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wpasupplicant
```[/QUOTE]
 Yes, you're missing a repository: you have to enable te universe one: look here for how to do: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by MonkeyWrench32 on 2005-05-15
I downloaded and installed the latest .deb package from here:  [http://linux.org.by/debian/pool/contrib/i/ipw2200/](http://linux.org.by/debian/pool/contrib/i/ipw2200/)

But when I did a modprobe and a dmesg, it still says that the 0.19 is loaded.   :?

---

### Post by MonkeyWrench32 on 2005-05-15
I did a little checking and I had to run module-assistant to install that package.  I did all of that and copied the files like it says in the first post, but I've got a situation here:

```
jon@UbuntuMonkey:~$ dmesg | grep ipw
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
```

Please help!

---

### Post by MonkeyWrench32 on 2005-05-15
Well, I uninstalled all of that package crap and actually got make to work!  Apparently I didn't have the linux headers installed after all.  :)

Now to work on the WPA...

---

### Post by MonkeyWrench32 on 2005-05-15
GOT IT!  :D

Thank you so much, Luca!

---

### Post by MechR on 2005-05-17
Hmm, I tried the instructions, but now Ubuntu can't seem to detect eth0 (my built-in wireless Intel hardware) at all* :(  Notably, the "dmesg | grep ipw" step didn't return any output.

*: Before, eth0 would show up in the list in Network Settings (System -> Administration -> Networking), but now it is missing.  Manually typing eth0 in Connection Properties (the window that pops up when you click the system tray icon) shows an error.  Also, the Device Manager used to have a longer list of info on the wireless hardware (PRO/Wireless 2200BG) in the Advanced tab.  And doing "sudo ifup eth0" spits out a number of errors, with several mentions of "no such device."

---

### Post by MechR on 2005-05-18
[QUOTE=luca_linux]Then you have to copy all the modules (ieee80211*.ko) it installs from /lib/modules/$(KVER)/drivers/net/wireless/ to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ and /lib/modules/$(KVER)/drivers/net/wireless/ipw2200.ko to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ipw2200/, since there's currently a bug in their location: in fact ipw2200 installs its modules in the first directory, while Ubuntu loads them from the second directory.[/QUOTE][quote=kiranos]EDIT: found the problem, the modules should go in wireless/ieee81102/ and not straight into wireless as I did[/quote]Ahh, that fixes my problem :)

Kiranos has it right; the ieee80211*.ko files should go in /lib/modules/$(KVER)/kernel/drivers/net/wireless/ieee80211/

Luca, could you edit your post to read:

"Then you have to copy all the modules (ieee80211*.ko) it installs from /lib/modules/$(KVER)/drivers/net/wireless/ to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ieee80211"

for people who come after me?  Thanks bunches, in any case :)

---

### Post by luca_linux on 2005-05-18
Yes, you're right...I meant that directory...I didn't pay attention to it.

HowTo edited.

---

### Post by Emerick on 2005-05-18
Hi everybody,

After some painful hours  on this install, i finally found why I had these messages:

```
$ dmesg | grep ipw
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
```

It was very easy, i just  needed to reboot the computer  ](*,)  :grin: 

So now, 'cause i'm a lazy boy, i decided to automate the install, so i made a script.
I give it for everyone who is interessed in.
You need to be root to execute this script, and remember that you have to edit some vars in the script in order to match your network config.

You can install the latest version of the driver , all you need is to change to variables in the script and put these names of files *ipw2200-1.0.4* and *ipw2200-fw-2.3* instead of *ipw2200-1.0.3* and *ipw2200-fw-2.2*.

Hope it will help :)

---

### Post by Technoviking on 2005-05-18
With ipw2200 1.0.4 you will get error while compiling unless you run the *remove_old* script from the ipw2200 1.0.4 sources. Also I'm getting a ton of firmware errors, so you may want towait till 1.0.5.

Mike

---

### Post by Emerick on 2005-05-18
[QUOTE=Mike Basinger]With ipw2200 1.0.4 you will get error while compiling unless you run the *remove_old* script from the ipw2200 1.0.4 sources. Also I'm getting a ton of firmware errors, so you may want towait till 1.0.5.

Mike[/QUOTE]
 Strange, i've got some warnings during compilation, but no error.
I'm sending you this message with these drivers.
Did you take the sources from cvs or as me from the website ?

---

### Post by luca_linux on 2005-05-19
I'm giving 1.0.4 driver version a try this afternoon...then I'll let you all know.

---

### Post by luca_linux on 2005-05-19
Ok, just updated the driver to 1.0.4 without any problem. Just following my howto.
Anyway there've been some fixes, especially about the power management stuff.
I suggest this update.

---

### Post by luca_linux on 2005-05-19
Ok, HowTo updated to 1.0.4: now every link refers to the new driver version.

---

### Post by dejitarob on 2005-05-19
Yup works great. Thanks again for your excellent how-to. Also, the "remove-old" sh script included with the new drivers is an easy way to ensure the upgrade goes smoothly without any symbolic errors from leftovers of the old driver. You may want to mention that in your how-to for future easy reference.

---

### Post by Emerick on 2005-05-19
[QUOTE=dejitarob]Yup works great. Thanks again for your excellent how-to. Also, the "remove-old" sh script included with the new drivers is an easy way to ensure the upgrade goes smoothly without any symbolic errors from leftovers of the old driver. You may want to mention that in your how-to for future easy reference.[/QUOTE]
 I didn't see this script. How silly i am :)
In fact, it's logical, because i used my script to install this driver :D

---

### Post by hshen on 2005-05-19
Hi Fulco,

very informative list.

I have a question about your step 4 "Check if the driver works". After you install the ipw2200, ieee80211 and firmwire, and run modprobe, does dmesg show only those 3 lines related to ipw2200? How do you know your ipw2200 driver works properly? 

In addition to these 3 lines, I also got something like
```

    ipw2200: failed to send TX_POWER command

```
I believe that the driver does not work properly, even though I installed ipw2200 1.0.3. I disabled hotplug as Ubuntu hung during the boot when loading hotplug. I am not sure if this the root cause of ipw2200 driver failure.

Thansk!
hshen

> 
**Step 4: Check if the driver works**
The best thing to do first is make sure you have an open network at this time (no WPA, no WEP, no MAC security). Also it might be a good idea to use a static IP. Configure your Wireless connection in the network settings according to your network IP range. Now let's enable the driver.

```

modprobe ipw2200
dmesg | grep ipw

```

If it works you will see something like this:

```

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

```


---

### Post by luca_linux on 2005-05-20
[QUOTE=hshen]
I have a question about your step 4 "Check if the driver works". After you install the ipw2200, ieee80211 and firmwire, and run modprobe, does dmesg show only those 3 lines related to ipw2200? How do you know your ipw2200 driver works properly? 

In addition to these 3 lines, I also got something like
```

    ipw2200: failed to send TX_POWER command

```
I believe that the driver does not work properly, even though I installed ipw2200 1.0.3. I disabled hotplug as Ubuntu hung during the boot when loading hotplug. I am not sure if this the root cause of ipw2200 driver failure.
[/QUOTE]
Yes, just those 3 lines have to be shown.
The latest driver version 1.0.4 has fixed many bugs especially about the power management stuff: so, you'd better give it a try.
You need hotplug and in particular the kernel option "Device Drivers -> Generic Driver Options -> Hotplug firmware loading support", that's enabled by default.

---

### Post by luca_linux on 2005-05-20
[QUOTE=dejitarob]Yup works great. Thanks again for your excellent how-to. Also, the "remove-old" sh script included with the new drivers is an easy way to ensure the upgrade goes smoothly without any symbolic errors from leftovers of the old driver. You may want to mention that in your how-to for future easy reference.[/QUOTE]
Done!

---

### Post by MechR on 2005-05-20
1.0.4 Upgrade successful :)  I have a couple questions, though...

1. Is it necessary to remove the old 2.2 firmware files?  They don't get overwritten by the 2.3 files because of their different names.  I removed them myself just to be sure.

2. Both times I've tried this, after the reboot I'd find that wireless isn't working, and that "dmesg | grep ipw" would give no output.  Trying "modprobe ipw2200" would show that Linux is looking in the wrong places for the files (i.e., the places that the driver "make install" installs to, as opposed to the places I moved them to afterward).  Running "sudo depmod" seems to straighten things out.

(Note, I'm not really knowledgeable about Linux :---) I just figured #2 out from bits of prior info and trial-and-error by man-page reading.  Still happy with getting everything working, though \\:D/ )

---

### Post by dejitarob on 2005-05-20
[QUOTE=Emerick]I didn't see this script. How silly i am :)
In fact, it's logical, because i used my script to install this driver :D[/QUOTE]
Yea I wanted to try your script but I kept getting connection refused. Try attaching it to your post.

---

### Post by Emerick on 2005-05-20
[QUOTE=dejitarob]Yea I wanted to try your script but I kept getting connection refused. Try attaching it to your post.[/QUOTE]

Very strange.
I put the file on this message, and i edit the other post.

You need to edit some vars on the file, and need to be root.

---

### Post by hshen on 2005-05-20
[QUOTE=luca_linux]Yes, just those 3 lines have to be shown.
The latest driver version 1.0.4 has fixed many bugs especially about the power management stuff: so, you'd better give it a try.
You need hotplug and in particular the kernel option "Device Drivers -> Generic Driver Options -> Hotplug firmware loading support", that's enabled by default.[/QUOTE]
 I don't think that driver version is a problem. I guess that the hotplug support is an issue as I have to disable the hotplug to make Ubuntu boot. I am new to Linux and never build the Linux kernel before. What does this kernel option mean?

Thanks!
hshen

---

### Post by luca_linux on 2005-05-21
[QUOTE=hshen]I don't think that driver version is a problem. I guess that the hotplug support is an issue as I have to disable the hotplug to make Ubuntu boot. I am new to Linux and never build the Linux kernel before. What does this kernel option mean?

Thanks!
hshen[/QUOTE]
If you've never recompiled the kernel before, yours has already included that option by default, so don't worry about. Anyway, try to update the driver.

---

### Post by luca_linux on 2005-05-21
[QUOTE=MechR]1.0.4 Upgrade successful :)  I have a couple questions, though...

1. Is it necessary to remove the old 2.2 firmware files?  They don't get overwritten by the 2.3 files because of their different names.  I removed them myself just to be sure.

2. Both times I've tried this, after the reboot I'd find that wireless isn't working, and that "dmesg | grep ipw" would give no output.  Trying "modprobe ipw2200" would show that Linux is looking in the wrong places for the files (i.e., the places that the driver "make install" installs to, as opposed to the places I moved them to afterward).  Running "sudo depmod" seems to straighten things out.

(Note, I'm not really knowledgeable about Linux :---) I just figured #2 out from bits of prior info and trial-and-error by man-page reading.  Still happy with getting everything working, though \\:D/ )[/QUOTE]
Yeah, it's better to remove the old firmware files.
About the second point, you're right, in fact, as said in the howto, you need to copy the files to one directory to another...

---

### Post by MechR on 2005-05-21
[QUOTE=luca_linux]About the second point, you're right, in fact, as said in the howto, you need to copy the files to one directory to another...[/QUOTE]Sorry, I was unclear  :-#  I meant that even though I had moved the files as instructed, Linux kept looking in the wrong places until I ran depmod.

---

### Post by MonkeyWrench32 on 2005-05-21
I completely removed the old drivers and firmware and installed all of the new stuff.  Here's the errors that I'm getting:

> jon@UbuntuMonkey:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: failed to send ASSOCIATE command
ipw2200: failed to send SSID command
ipw2200: failed to send SYSTEM_CONFIG command
ipw2200: ipw_send_system_config failed
ipw2200: failed to send SSID command
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command
ipw2200: No space for Tx
ipw2200: failed to send SSID command

Please help me!  :)

---

### Post by goudiemark on 2005-05-21
[QUOTE=juicewvu]when trying to follow this tutorial i recieve the following error(s) when trying to compile the ipw2200 driver:

```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I tried making the /lib/modules/2.6.10-5-386/build directory as it infact does not exist, after which I recieve the following error(s):
```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

```
I'm kind of stuck here, do i need to copy the source files to the /lib/modules/2.6.10-5-386/build directory before trying to compile?


-Juice[/QUOTE]


Ok i crawled through the post and i have no clue how to make the systemlink correctly I think i have the kernel headers updated i ran this command
```
$ sudo apt-get install linux-headers-2.6.10-5-386
``` 

btw im a complete newb when it comes to linux and drivers

---

### Post by ChamPro on 2005-05-23
Somehow the new firmware (2.3) and the new drivers (1.0.6) make all the difference. I had no trouble compiling them using the same settings I've been using.

However, an old problem is popping back up. I can't connect to a WiFi router that is using DHCP and WEP. It just times out. Any suggestions?

*EDIT* I got it working. Forgot about changing the router to Open System for WEP Authentication Type. Oops.

[QUOTE=ChamPro]Wow... I really don't know what the #*&$ is going on. I haven't had this much trouble with Ubuntu ever.

Here's the beginning of the list of warnings I get when executing make. I tried changing the permissions of a lot of directories to no avail. The make and make install creates no kernel modules whatsoever.
```
zoph@nebosuke:~/Desktop/Downloads/ipw2200/ipw2200-1.0.3$ make
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/home/zoph/Desktop/Downloads/ipw 2200/ipw2200-1.0.3 MODVERDIR=/home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.10'
Makefile:484: .config: No such file or directory
  CC [M]  /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200.o
In file included from include/linux/module.h:9,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/sched.h:4:37: asm/param.h: No such file or directory
In file included from include/linux/types.h:13,
                 from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/posix_types.h:47:29: asm/posix_types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/types.h:14:23: asm/types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/types.h:18: error: syntax error before "__kernel_dev_t"
include/linux/types.h:18: warning: type defaults to `int' in declaration of `__k ernel_dev_t'
include/linux/types.h:18: warning: data definition has no type or storage class
include/linux/types.h:21: error: syntax error before "dev_t"
include/linux/types.h:21: warning: type defaults to `int' in declaration of `dev _t'
```
Maybe I'm heading for a another format. Lovely.[/QUOTE]

---

### Post by MonkeyWrench32 on 2005-05-23
I rolled back to 1.0.3 and everything almost works.  I am able to connect and what not, but I don't get a response when doing a ping.  It does the DNS resolution, but that's all.  Any suggestions?

---

### Post by fulco on 2005-05-24
[QUOTE=MonkeyWrench32]I completely removed the old drivers and firmware and installed all of the new stuff.  Here's the errors that I'm getting:
[/QUOTE]

Hi MokeyWrench,

I have the exact same errors when using the 2.3 fw/ 1.04 driver combination when setting the Wireless network device to static IP (which I prefer because I use my laptop at home only and it's faster at boottime since there is no waiting for an answer from the DHCP server involved). 

Switching to DHCP leaves me with a dead connection after boot (Wifi card not assoiciated with AP). Only after I disable and enable the driver with a modprobe -r and a subsequent modprobe I manage to get a connection, but only for a very short time. After that de connection is dead again.

I went back to driver 1.03 which does not give me these problems. Maybe I will give 1.04 another try tomorrow. I might also try to use the 2.3 fw with the 1.03 driver if possible to see what that gives (I already verified the fw 2.2 / driver 1.04 combination does not work).

Anyway, I really would like to have static IP functioning again since it's fast an reliable.

---

### Post by radhaz on 2005-05-24
When I power down the system I get a statement that states something to the effect of:

```

wpasupplicant: Disabled see /etc/default/
```

Is this normal?  I am also getting a lot of packet loss / network drops that sometime necessitate either deactivating & reactivating the eth1 connection or even rebooting the laptop.

If anyone has any advice or can point me towards a thread for ways to troubleshoot wireless networking ie commands and such I would be greatly appreciate.

Also something you might want to note for people doing fresh installs is they have to install gcc & headers from the cd (can be done via synaptic for n00bs like myself) otherwise the install won't work.

Very Respectfully
RadHaz

---

### Post by Technoviking on 2005-05-24
I had to do two things to make the ipw2200 driver happy with my computer.

1. Remove old driver:
```
remove-old
``` 
Run this from the ipw2200-1.0.4 directory, it cleans up your modules directory, and resets compile options.

2. Disable hardware crypto: 
```
echo "options ipw2200 hwcrypto=0" > /etc/modprobe.d/ipw2200
``` 
This solved firmware errors I was having.

Mike

---

### Post by radhaz on 2005-05-24
[QUOTE=Mike Basinger]...

2. Disable hardware crypto: 
```
echo "options ipw2200 hwcrypto=0" > /etc/modprobe.d/ipw2200
``` 
This solved firmware errors I was having....[/QUOTE]

What error's were you having?

---

### Post by Technoviking on 2005-05-24
[QUOTE=radhaz]What error's were you having?[/QUOTE]
I kept getting "ipw2200: Firmware error detected. Restarting".

Mike

---

### Post by dejitarob on 2005-05-24
I used the 1.03 drivers+firmware for a few months with no issues. I upgraded to 1.04 the other day fine. A few days later I suddenly was unable to get an IP or even see any APs. "dmesg | grep ipw" showed the firmware error restarting. Removing and reinstalling the firmware fixed this and its been working great since.

---

### Post by MikePB on 2005-05-25
Hey. I'm a big 'ol noob and I did all of what I was supposed to do, and now my wireless card seems to have disappeared  :confused: 

I can get on fine over ethernet (hence the post :P ), but my wireless interface eth1 is no more!

Please help a confused and frustrated noob!

---

### Post by fulco on 2005-05-25
Ok, I reinstalled driver 1.04 and firmware 2.3, making sure no old drivers of firmware are present.

The firmware loads normally when booting into Ubuntu, but... there is no connection. Checking the network connection told me DHCP had not been succesfull since there was no IP address. I set the interface to Static IP to force IP address and re-initialized the network with the commands:
```

sudo /sbin/modprobe -r ipw2200
sudo /sbin/modprobe ipw2200
sudo /etc/init.d/networking restart
sudo killall wpa_supplicant
sudo /usr/sbin/wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D ipw

```
Now, my network connection kept going up and down every few seconds: it does connect to my accesspoint, but not for long.

The messagelog shows:
```
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:01:07.0[A] -> GSI 5 (level, low) -> IRQ 5
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ieee80211: eth0: Unknown management packet: 0
ieee80211: eth0: Unknown management packet: 0
ieee80211: eth0: Unknown management packet: 0
```
Everytime the interface goes trough a disconnect/connect cycle, this last message is repeated.

Sometimes, between all the "Unknown management packet 0:"  messages, a firmware error or some other network related message shows up too. This happened too with driver 1.03 but did not cause any problems with my connection. Just for reference:
```
ieee80211: eth0: Unknown management packet: 0
ieee80211: eth0: Unknown management packet: 0
TKIP: replay detected: STA=00:13:01:10:06:16 previous TSC 000000000000 received TSC 000000000000
TKIP: replay detected: STA=00:13:01:10:06:16 previous TSC 000000000000 received TSC 000000000000
ieee80211: eth0: Unknown management packet: 0
ieee80211: eth0: Unknown management packet: 0
ieee80211: eth0: Unknown management packet: 0
ieee80211: eth0: Unknown management packet: 0
ipw2200: Firmware error detected.  Restarting.
ieee80211: eth0: Unknown management packet: 0
ieee80211: eth0: Unknown management packet: 0
```
Does anybody have a clue what is going on here?

**Edit**: I had a look in the ipw2200 code:

```
+void ieee80211_rx_mgt(struct ieee80211_device *ieee,
+		      struct ieee80211_hdr *header,
+		      struct ieee80211_rx_stats *stats)
+{
+	switch (WLAN_FC_GET_STYPE(header->frame_ctl)) {
+	case IEEE80211_STYPE_ASSOC_RESP:
+		IEEE80211_DEBUG_MGMT("received ASSOCIATION RESPONSE (%d)\n",
+				     WLAN_FC_GET_STYPE(header->frame_ctl));
+		break;
+
+	case IEEE80211_STYPE_REASSOC_RESP:
+		IEEE80211_DEBUG_MGMT("received REASSOCIATION RESPONSE (%d)\n",
+				     WLAN_FC_GET_STYPE(header->frame_ctl));
+		break;
+
``````

+	case IEEE80211_STYPE_PROBE_RESP:
+		IEEE80211_DEBUG_MGMT("received PROBE RESPONSE (%d)\n",
+				     WLAN_FC_GET_STYPE(header->frame_ctl));
+		IEEE80211_DEBUG_SCAN("Probe response\n");
+		ieee80211_process_probe_response(
+			ieee, (struct ieee80211_probe_response *)header, stats);
+		break;
+
+	case IEEE80211_STYPE_BEACON:
+		IEEE80211_DEBUG_MGMT("received BEACON (%d)\n",
+				     WLAN_FC_GET_STYPE(header->frame_ctl));
+		IEEE80211_DEBUG_SCAN("Beacon\n");
+		ieee80211_process_probe_response(
+			ieee, (struct ieee80211_probe_response *)header, stats);
+		break;
+
+	default:
+		IEEE80211_DEBUG_MGMT("received UNKNOWN (%d)\n",
+				     WLAN_FC_GET_STYPE(header->frame_ctl));
+		IEEE80211_WARNING("%s: Unknown management packet: %d\n",
+				  ieee->dev->name,
+				  WLAN_FC_GET_STYPE(header->frame_ctl));
+		break;
+	}
```Apparently the driver cannot make up the signal type and defaults to "unknown".  I have no idea what is causing this, I have not changed the setup of my accesspoint and/or WPA supplicant  since upgrading from ipw version 1.03 to 1.04.

Anyway, it seems I am not alone:

[http://article.gmane.org/gmane.linux.drivers.ipw2100.devel/5325](http://article.gmane.org/gmane.linux.drivers.ipw2100.devel/5325)

**Edit 2**: if I disable my WPA and set my accesspoint to "open" mode, the 1.04 driver works. I will try to reinstall WPA to see if that solves anything!

---

### Post by fulco on 2005-05-25
[QUOTE=MikePB]Hey. I'm a big 'ol noob and I did all of what I was supposed to do, and now my wireless card seems to have disappeared  :confused: 

I can get on fine over ethernet (hence the post :P ), but my wireless interface eth1 is no more!

Please help a confused and frustrated noob![/QUOTE]Check your /etc/network/interfaces file. Open a terminal window and paste the following command into it:```
sudo gedit /etc/network/interfaces
```It should contain lines like this:```
mapping hotplug
    script grep
    map eth1

iface eth1 inet dhcp

```If not, I suggest you add these lines.

Also, check if the driver reports a firmare error or other error:
```
sudo dmesg | grep ipw
sudo dmesg | grep iee
```If everything is OK then it only shows a few lines containing the Intel Pro Wireless networkdriver version - in this case 1.04 - and a message it has detected a Intel Pro Wireless network connection.

Just put the errors the messagelog gives you in this thread and I am sure someone will be able to help.

---

### Post by MikePB on 2005-05-25
Thanks Fulco!

my /etc/network/interfaces contained the lines already, besides what you said it should have it had auto eth1 at the end

and doing sudo dmesg | grep iee returned info about my firewire :)

but sudo dmesg | grep ipw returned nothing....

---

### Post by fulco on 2005-05-25
The eth1 auto is normal, I think it means the network interface should autoconfigure itself with DHCP (assign IP address etc).

If you don't have any "ipw" reference in your messagelog this means the driver is not initialized so you probably missed something when following Luca's how-to.

Follow the procedure again and watch the output carefully when you do the "make" and "make install". You might have had error messages there that you missed when installing the first time.

Check if you have ipw2200.ko and five ieee80211*.ko files in 

/lib/modules/$(KVER)/kernel/drivers/net/wireless/

The howto mentions they should be in 

/lib/modules/$(KVER)/kernel/drivers/net/wireless/ipw2200     and
/lib/modules/$(KVER)/kernel/drivers/net/wireless/ieee80211

but I noticed the installer in 1.04 defaults to the wireless directory and not the specific ipw2200 and ieee80211 directories (by the way, I replaced the KMISC := line in the Makefile with KMISC := /lib/modules/$(KVER)/kernel/drivers/net/wireless/, as the how-to suggests. Although the how-to explains this after the "make" and "make install" instructions, ofcourse you have to do this replacement **before** the make).

Check if the files are where I expect them to be using Nautilus or by doing a

```
ls /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ipw2200*.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211*.ko

ieee80211_crypt_ccmp.ko  ieee80211_crypt_tkip.ko  ieee80211.ko
ieee80211_crypt.ko       ieee80211_crypt_wep.ko   ipw2200.ko
```

If the files are not there but are in the ipw2200 and ieee80211 directories, try copying them to the wireless directory and see if that helps: When I had the files in the subdirectories my driver did not load either.

You might also try a "sudo depmod" and see if that makes Ubuntu find your driver files at boottime.

---

### Post by dejitarob on 2005-05-25
I had to reinstall the driver since there was a kernel update from the ubuntu repositories. I noticed the how-to currently says: > Then install it:
```
sudo tar xvzf ipw2200-1.0.4.tgz cd ipw2200-1.0.4 make sudo make install
```Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted. It should be the other way around, that is remove the old driver then install :]. Most people should catch it but someone new or reading through it quickly probably won't follow the correct order.

---

### Post by radhaz on 2005-05-25
Could someone break the results of this for me?  I'm trying to work all the kinks out of my install.  

```
dmesg | grep ieee8
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: eth1: Unknown management packet: 0
ieee80211_crypt: registered algorithm 'TKIP'

```

Im wondering if it has something to do with my earlier [posted problem](http://www.ubuntuforums.org/showthread.php?p=185078#post185078) 

Thanks in advance for your time.

---

### Post by MikePB on 2005-05-25
Still no luck. I redid the installation, and even hand copied them over. It looks to me like NOTHING is being installed. 


Strange though, I plug in a PCMCIA card and it detects it just fine. (the card itself was bad, but still :))

Now, I AM running the 686 kernel, but I still have the 386 installed as a fallback. Does that matter at all?

---

### Post by Emerick on 2005-05-26
I use a 2.6.10.5-686 kernel and no problem for me.
Did you tried my install script ? (seek 1-2 previous pages)
It work great for me.

---

### Post by Silwenae on 2005-05-26
I wasn't having any luck last night until I changed from 2.6.10.5-386 to 686.  (Make wouldn't run).  Once I installed 686, everything worked perfectly.  I uninstalled the 386 kernel, ymmv.

Thanks for the how-to.

---

### Post by luca_linux on 2005-05-26
[QUOTE=dejitarob]I had to reinstall the driver since there was a kernel update from the ubuntu repositories. I noticed the how-to currently says:  It should be the other way around, that is remove the old driver then install :]. Most people should catch it but someone new or reading through it quickly probably won't follow the correct order.[/QUOTE]
Thanks.
HowTo edited.

---

### Post by MikePB on 2005-05-26
okay..... still not working. I tried with the newly modified how-to and nadda.

Emerick, I dl'd your script and it won't run for me. don't know why.


Here's what's happening now:

if I type in dmesg | grep ipw I get no output, BUT if I do sudo modprobe ipw2200 THEN do a dmesg I get this:

```
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
``` 


Ideas?

thanks in advance

---

### Post by zith on 2005-05-26
Hello! I'm getting an error when trying to compile the driver.

> 
zith@lapbock:/usr/src/ipw2200-1.0.4$ make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/usr/src/ipw2200-1.0.4 MODVERDIR=/usr/src/ipw2200-1.0.4 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
 

Does anyone know why I get this?

---

### Post by radhaz on 2005-05-26
[QUOTE=zith]Hello! I'm getting an error when trying to compile the driver.

 

Does anyone know why I get this?[/QUOTE]

I had that exact problem and posted it in this very thread [here](http://www.ubuntuforums.org/showthread.php?p=158980#post158980) 

The answer I was given 2 posts below was 

[QUOTE=luca_linux]As said in some previous posts, you have to install the packages: build essentials, kernel hearders.[/QUOTE]

Best of luck.

---

### Post by zith on 2005-05-26
Thank you!

Sorry for not searching in the forums enough

---

### Post by goudiemark on 2005-05-26
Im still getting the make error 

admin@tantalus:~/ipw2200-1.0.4$ make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/admin/ipw2200-1.0.4 MODVERDIR=/home/admin/ipw2200-1.0.4 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2


I have installed the kernel headers and the build-essentials via apt-get.  I dont know what to do.

Thanks for any help in advance

---

### Post by zith on 2005-05-27
I installed the following packages:
build-essential
linux-headers-386

and then it worked fine

---

### Post by goudiemark on 2005-05-27
Sorry to be such a bother but i figured out i was missing the headers I thought i had installed them but i didnt.

Now when i do make i get this error

admin@tantalus:~/ipw2200-1.0.4$ make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/admin/ipw2200-1.0.4 MODVERDIR=/home/admin/ipw2200-1.0.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/admin/ipw2200-1.0.4/ipw2200.o
/home/admin/ipw2200-1.0.4/ipw2200.c: In function `ipw_request_scan':
/home/admin/ipw2200-1.0.4/ipw2200.c:5588: warning: unused variable `channel'
/home/admin/ipw2200-1.0.4/ipw2200.c: In function `ipw_set_channel':
/home/admin/ipw2200-1.0.4/ipw2200.c:7443: warning: unused variable `i'
objdump: /home/admin/ipw2200-1.0.4/.tmp_ipw2200.o: File format not recognized
  CC [M]  /home/admin/ipw2200-1.0.4/ieee80211_module.o
objdump: /home/admin/ipw2200-1.0.4/.tmp_ieee80211_module.o: File format not recognized
  CC [M]  /home/admin/ipw2200-1.0.4/ieee80211_tx.o
objdump: /home/admin/ipw2200-1.0.4/.tmp_ieee80211_tx.o: File format not recognized
  CC [M]  /home/admin/ipw2200-1.0.4/ieee80211_rx.o
objdump: /home/admin/ipw2200-1.0.4/.tmp_ieee80211_rx.o: File format not recognized
  CC [M]  /home/admin/ipw2200-1.0.4/ieee80211_wx.o
objdump: /home/admin/ipw2200-1.0.4/.tmp_ieee80211_wx.o: File format not recognized
  CC [M]  /home/admin/ipw2200-1.0.4/ieee80211_geo.o
objdump: /home/admin/ipw2200-1.0.4/.tmp_ieee80211_geo.o: File format not recognized
  LD [M]  /home/admin/ipw2200-1.0.4/ieee80211.o
/home/admin/ipw2200-1.0.4/ieee80211_module.o: file not recognized: File format not recognized
make[2]: *** [/home/admin/ipw2200-1.0.4/ieee80211.o] Error 1
make[1]: *** [_module_/home/admin/ipw2200-1.0.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [modules] Error 2

---

### Post by gumby on 2005-05-30
Hi,
I followed your excellent how-to.  I got my driver successfully loaded and think I am close to getting WPA support working.
I then run the following:
1.   wpa_supplicant -B -i eth1 -c /etc/wpa_suppicant.conf -D ipw -w -dd 

2.   iwconfig
      I get "Access Point: 00:00:00:00:00"... I'm not connecting to my AP!

3.   dmesg | grep 80211 returns
      [snip]
            ieee80211_crypt: registered algorithm 'NULL'
            ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
            ieee80211_crypt: registered algorithm 'NULL'
      [/snip]

Any ideas?

Thanks!
Gumby

---

### Post by MikePB on 2005-05-31
UPDATE!::

Yeah, when you decide to upgade hardware drivers and firmware, make sure you know what device you have.

THAT was my problem. I have an ipw2100.... so no wonder it didn't work..... :?:

---

### Post by Emerick on 2005-05-31
[QUOTE=MikePB]UPDATE!::

Yeah, when you decide to upgade hardware drivers and firmware, make sure you know what device you have.

THAT was my problem. I have an ipw2100.... so no wonder it didn't work..... :?:[/QUOTE]
 ipw2200 doesn't work with ipw2100 hardware.
Please go to [http://ipw2100.sf.net](http://ipw2100.sf.net) for drivers.

---

### Post by luca_linux on 2005-05-31
[QUOTE=gumby]Hi,
I followed your excellent how-to.  I got my driver successfully loaded and think I am close to getting WPA support working.
I then run the following:
1.   wpa_supplicant -B -i eth1 -c /etc/wpa_suppicant.conf -D ipw -w -dd 

2.   iwconfig
      I get "Access Point: 00:00:00:00:00"... I'm not connecting to my AP!

3.   dmesg | grep 80211 returns
      [snip]
            ieee80211_crypt: registered algorithm 'NULL'
            ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
            ieee80211_crypt: registered algorithm 'NULL'
      [/snip]

Any ideas?

Thanks!
Gumby[/QUOTE]
 Does it work without wpa?
Are you sure you've removed all the old modules before installing the driver?
What firmware are you using?
Do you have an ipw2200 or an ipw2100?

---

### Post by scottylans on 2005-06-01
I'm getting this error

root@laptop:/home/user/ipw2200-1.0.4 # make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/user/ipw2200-1.0.4 MODVERDIR=/home/user/ipw2200-1.0.4 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2
root@laptop:/home/user/ipw2200-1.0.4 #



I have Hoary 5.04 installed from an iso I downloaded 48 hours ago.
I have "build essentials" installed in Synaptic. (that wasn't included in the initial tutorial :( ....? )

Any idea's?

---

### Post by goudiemark on 2005-06-01
You also need kernel headers, search through sanaptic for that, im not in ubunutu right now, but when i log back in ill put the exact package name i used.  Also you have to get the right kernel headers for the install you using.

---

### Post by dejitarob on 2005-06-01
there is linux-kernel-headers, linux-headers-2.6.10-5 and linux-headers-2.6.10.5-686 (or 386, k7, etc depending on what kernel you are using)

---

### Post by nxv_ on 2005-06-04
[QUOTE=firas]Thanks for the HOWTO luca_linux. However I'm having the same problem as meesmany. I have an IBM ThinkPad T41 with an ipw2100. I downloaded the latest firmware and source for ipw2100. Copied the firmware to the right folder, compiled the drivers and copied them to the right folder. Installed and configured wpasupplicant.conf just like you mentioned with my own essid and psk ofcourse but I can't get my card to associate with my LinkSys WAG54G ap. Here is the output from some commands:

```

firas@ibm-t41:~$ dmesg | grep ipw2100
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.0
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

firas@ibm-t41:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=11):
     61 6c 72 61 67 6f 6d 2d 6e 65 74                  my-essid
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='my-essid'
Daemonize..

firas@ibm-t41:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I even tried setting my essid manually using iwconfig eth1 essid my-essid to no avail. I disabled WPA on my AP and was able to connect just fine using iwconfig. 

Can anyone shed any light on this problem ? I'm really getting desperate here, I've spent days on this with no luck.

And a little off topic here. How can I disable IPv6 on my laptop (the sit0 interface) permanently ?[/QUOTE]

I have the same problem as firas, don't get any error message but wpa doesn't wan't to work. Without encryption i get a connectin to my router.

I updated to the latest driver and firmware. No improvement.

What looks strange to me is that sudo wpa_cli status returns the following

```


Selected interface 'eth1'
bssid=00:00:00:00:00:00
pairwise_cipher=UNKNOWN
group_cipher=UNKNOWN
key_mgmt=UNKNOWN
wpa_state=SCANNING
Supplicant PAE state=DISCONNECTED

suppPortStatus=Unauthorized
EAP state=DISABLED


```

Why does it complain key_mgmt=UNKNOWN. It is set to key_mgmt=WPA-PSK in /etc/wpa_supplicant.conf and manually starting wpa returns: key_mgmt: 0x2 analog to firas post.

I am now trying to build a vanilla kernel from kernel.org and install ipw2100 again. At the moment i am getting mad. I checked every config i know several times. No errors in the log and i know the wpz_supplicant.conf hast to work, as it did in gentoo, before i switched to ubuntu. My stomache realy hurts cause of waisting time with this @#%^&*( network encryption.

I additionaly found this Bugreport, but without a solution:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=9970](https://bugzilla.ubuntu.com/show_bug.cgi?id=9970)


Hope firas or anyoneelse solved the problem with 2100 and can give me a hint.

---

### Post by motion_blur on 2005-06-08
Ok, i followed the HowTo
all seens to work:
```
stan@ubuntu:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
stan@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=6):
     XX XX XX XX XX XX                                 XWLAN
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='XWLAN'
Daemonize..
stan@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"XWLAN"
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:XX:XX:XX:XX:XX
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:173   Missed beacon:0

sit0      no wireless extensions.
```

but i cannot connect to the internet (timeout) with firefox or ping for example...
PLEASE, need help  :sad:

edit: it seems, that the WLAN DOES something, i can see the MAC-address in the AP-menu, but no IP!
how i can configure my eth1 for DHCP??
sould i do something with /etc/network/interfaces?

before last apt-get update i had no problems with this configuration  :mad:

---

### Post by dejitarob on 2005-06-08
sudo ifdown eth1 then sudo ifup eth1 will get a new ip address. Look at the latter part of the guide for info on how to start wpa_supplicant on bootup. If you do this the network daemon should automatically get a new IP on bootup.

---

### Post by motion_blur on 2005-06-08
no, does not work,
now the driver is broken or something...
at startup i get errors like this:
```
ipw2200: failed to send ASSOCIATE command
ipw2200: failed to send SSID command
ipw2200: ipw_send_system_config failed
ipw2200: failed to send SSID command
ipw2200: failed to send SSID command
ipw2200: no space for Tx
ipw2200: failed to send SSID command
```

---

### Post by MrSandman on 2005-06-09
if there a definative tutorial on how to do this? i have tried and tried and i keep getting the make error, so do i need the header package also?

i am pretty much a newbie.

---

### Post by dejitarob on 2005-06-09
[QUOTE=MrSandman]if there a definative tutorial on how to do this? i have tried and tried and i keep getting the make error, so do i need the header package also?

i am pretty much a newbie.[/QUOTE]This is a pretty much definative but it does assume you have a bit of experience with compiling which is easy once you do it and learn to interpret the error messages. So what is the error message you are getting? Where are you getting stuck at? If you are more specific, we can help.

[QUOTE=motion_blur]no, does not work,
now the driver is broken or something...
at startup i get errors like this:
```
ipw2200: failed to send ASSOCIATE command
ipw2200: failed to send SSID command
ipw2200: ipw_send_system_config failed
ipw2200: failed to send SSID command
ipw2200: failed to send SSID command
ipw2200: no space for Tx
ipw2200: failed to send SSID command
```[/QUOTE]Make sure you are disabling your wireless card in the BIOS or through a button the keyboard. If not, try reinstalling being sure to remove the old drivers.

---

### Post by luca_linux on 2005-06-09
[QUOTE=MrSandman]if there a definative tutorial on how to do this? i have tried and tried and i keep getting the make error, so do i need the header package also?

i am pretty much a newbie.[/QUOTE]
 Yes, you need the kernel headers or the kernel source.

---

### Post by sinaen on 2005-06-09
Hi ive done everything in your howto, but when i start up my computer, i get this message from dmesg, with the command dmesg | grep ipw..

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Radio Frequency Kill Switch is On:
ipw2200: failed to send SYSTEM_CONFIG command
ipw2200: ipw_send_system_config failed

i dunno what this means, but it seems that i cannot get the wireless interface to function properly, im sending screens of iwconfig eth1 and /etc/network/interfaces too

sudo iwconfig eth1

eth1      radio off  ESSID:"YoshisIsland"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo ifconfig eth1

eth1      Link encap:Ethernet  HWaddr 00:0E:35:60:69:2D
          inet6 addr: fe80::20e:35ff:fe60:692d/64 Scope:Link
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:d0202000-d0202fff



iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid YoshisIsland
wireless-channel 6

the only thing i get when i do try to take the interface up is that it dhcp.. request and different intervals, you know ;)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.


my router stands on this settings

SSID 
	YoshisIsland 
Channel
	6 
Encryption 
	AES_CCMP 
its a D-link di-624

hope this information is enough ;)

thanks for the howto, with this i at least got a MAC-address ;D

---

### Post by pdk001 on 2005-06-09
thanks for the tip

---

### Post by sinaen on 2005-06-10
I forgot to write what computer im sitting on, its a  Fujitsu siemens p7010...

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Radio Frequency Kill Switch is On:
ipw2200: failed to send SYSTEM_CONFIG command
ipw2200: ipw_send_system_config failed

iwconfig eth1
eth1      radio off  

Does some of this means that the network card is not powerd on?...
how do i do to get it to power on?

---

### Post by sbukka on 2005-06-11
I am using DELL INSPIRON 600 M , CENTRINO . with 2200BG Intel/Pro wireless
I saw some commands some body told before here.
I tried thsoe on my mewly installed UBUNTU.

first i run the command iwconfig 
i got the o/p like below,

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"APT 212"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

sit0      no wireless extensions.

I didn't find any "IEEE" thing here.

Next i run the second command .It dispalyed all wireless networks around my place.  
this is my wireless connection.


Cell 03 - Address: 00:90:4C:7E:00:64
                    ESSID:"APT 212"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Extra: RSSI: -37  dBm
                    Extra: Last beacon: 37ms ago

Her I can see that "IEE" thing .

i also run the third one u said  iwconfig eth1 essid "APT 212".

it went good until now. 

But for the next command  iwconfig eth1 key XXXXXXXX
i gave my password here. Actually its in WPA i think so.
The commands u send works for both WPA and WPE or only for WPE?

i also run that last command    " dhclient eth1"
I got the following messages.
I didn't see any IP here but saying that "unknown hardware address".

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:74:fa:ad
Sending on   LPF/eth1/00:0e:35:74:fa:ad
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20

I don't what is the problem...
  If u can please help me in this.....

---

### Post by Lycron on 2005-06-11
[QUOTE=luca_linux]Hi!
I've seen there are many requests about how to get ipw2200 and wpa working. So, as I've managed to get them to work, I've decided to write a howto.

We have to compile and install the latest ipw2200 1.0.4 driver from [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net) and we also have to install the firmware, as the ipw2200 0.19 included in the standard installation of Hoary doesn't support wpa.
Here are the steps:
First of all, download the firmware from [here]("http://ipw2200.sourceforge.net/firmware.php?fid=5").
Then install it:
```

sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/

```
Now download the latest driver from [here]("http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.4.tgz?download").
Then untar it and change your current directory into the driver's one:
```

sudo tar xvzf ipw2200-1.0.4.tgz
cd ipw2200-1.0.4

```
Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted:
```
sudo sh remove-old
```

Since there's currently a bug in their location (in fact ipw2200 installs its modules in the first directory, while Ubuntu loads them from the second directory), you have two way to get around it:
1) Edit this line of the Makefile,
from ```
 KMISC := /lib/modules/$(KVER)/drivers/net/wireless/ 
``` to ```
 KMISC := /lib/modules/$(KVER)/kernel/drivers/net/wireless/ 
```
Then install it:
```

make
sudo make install

```
2) Or just copy all the modules (ieee80211*.ko) it _installs_ from /lib/modules/$(KVER)/drivers/net/wireless/ to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ieee80211 and /lib/modules/$(KVER)/drivers/net/wireless/ipw2200.ko to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ipw2200/.

Now we have to download and install the wpa_supplicant package:
```

sudo apt-get install wpasupplicant

```
Then you have to create a wpa_supplicant.conf in /etc, so:
```

sudo gedit /etc/wpa_supplicant.conf

```
And paste the following lines in the text editor:
```

network={
       ssid="your_network_name"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Anyway there are further configuration examples in /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz.

Then reboot to make sure that the new modules are loaded successfully and type:
```
dmesg | grep ipw
``` 
to see if there are errors.
Then type the following command to configurate wpa_supplicant:
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
```
Note: "eth1" is your wireless device.

Now we have to create a small script (first provided by fulco and edited by me) in order to get wpa starting automatically at boot:
```

sudo gedit /etc/init.d/wifi_wpa.sh

```
Here's the script:
```

#! /bin/sh
# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w
fi

exit 0

```
Change the script's permissions to allow it to be executed:
```

sudo chmod +x /etc/init.d/wifi_wpa.sh

```
And create a symlink to define the relative service:
```

sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/S40netwifiwpa

```

Ok, that's all!
I hope this howto will be helpful.[/QUOTE]
 I need some help if i try to get running wpa i become sutch errors....what can i do ??


domdom@domlap:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

domdom@domlap:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:30:F1:D3:B1:66
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=98/100  Signal level=-26 dBm
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    Extra: Last beacon: 10ms ago

domdom@domlap:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Password:
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     44 6f 6d 48 6f 6d 65                              DomHome
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=14): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='DomHome'
Daemonize..
domdom@domlap:~$ sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=7):
     44 6f 6d 48 6f 6d 65                              DomHome
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=14): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='DomHome'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
Own MAC address: 00:0e:35:4d:6c:a9
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     44 6f 6d 48 6f 6d 65                              DomHome
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 278 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:30:f1:d3:b1:66 ssid='<hidden>' wpa_ie_len=26 rsn_ie_len=0
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 278 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:30:f1:d3:b1:66 ssid='<hidden>' wpa_ie_len=26 rsn_ie_len=0
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     44 6f 6d 48 6f 6d 65                              DomHome
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 278 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:30:f1:d3:b1:66 ssid='<hidden>' wpa_ie_len=26 rsn_ie_len=0
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Starting AP scan (broadcast SSID)
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 278 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:30:f1:d3:b1:66 ssid='<hidden>' wpa_ie_len=26 rsn_ie_len=0
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     44 6f 6d 48 6f 6d 65                              DomHome
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 278 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:30:f1:d3:b1:66 ssid='<hidden>' wpa_ie_len=26 rsn_ie_len=0
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Signal 2 received - terminating
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=0
wpa_driver_ipw_set_countermeasures: enabled=0
--------------------------------------------------------------------------------
i followed the howto....but it doesn't work...

i got a toshiba Satelite M30x-102 with bg2200(ipw2200)... i downloaded the latest drivers and firmware .... and also the latest linux kernel headers....

i don't know what else to do?

could some one help me ?

thanks a lot...
Lyc

---

### Post by hshen on 2005-06-12
[QUOTE=luca_linux]If you've never recompiled the kernel before, yours has already included that option by default, so don't worry about. Anyway, try to update the driver.[/QUOTE]

I believe that I finally got somewhere. The real problem is that some PCI devices in my machine do not work properly. As I totally disabled "hotplug" script under init.d, all the .rc scripts under /etc/hotplug are not executed in the boot time.  This somehow makes the wireless controller unhappy. Now, I just disabled the pci.rc. Even though the the wireless controller is one of the PCI device, iwconfig shows that the wireless controller is ready to work. 

Lesson: if you want to use Linux, never buy a computer with the latest hardware.

---

### Post by luca_linux on 2005-06-15
[QUOTE=hshen]I believe that I finally got somewhere. The real problem is that some PCI devices in my machine do not work properly. As I totally disabled "hotplug" script under init.d, all the .rc scripts under /etc/hotplug are not executed in the boot time.  This somehow makes the wireless controller unhappy. Now, I just disabled the pci.rc. Even though the the wireless controller is one of the PCI device, iwconfig shows that the wireless controller is ready to work. 

Lesson: if you want to use Linux, never buy a computer with the latest hardware.[/QUOTE]
 Why disabling hotplug? It's so useful...

---

### Post by jhuff on 2005-06-16
I need a lot of help!

I don't know a lot about Linux, I have completely destroyed my Dell Inspiron 9300 wireless drivers.

I get the following error when getting to the point of typing "make"

/bin/sh: cc: command not found
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jah/ipw2200-1.0.4 MODVERDIR=/home/jah/ipw2200-1.0.4 modules
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-5-386/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/jah/ipw2200-1.0.4/ipw2200.o
/bin/sh: gcc: command not found
make[2]: *** [/home/jah/ipw2200-1.0.4/ipw2200.o] Error 127
make[1]: *** [_module_/home/jah/ipw2200-1.0.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [modules] Error 2

Can anyone help me out?

---

### Post by jhuff on 2005-06-16
I got it to WORK!!!!

I must have missed the post that mentioned installing "build-essential"  Once I installed that everything worked great.  

Can anyone explain why "build-essential" is needed?

---

### Post by luca_linux on 2005-06-17
Because you have to compile the driver from sources.

---

### Post by jhuff on 2005-06-17
Updating the driver did work.  I know little about Linux so it was a painful process.  I lost wireless capability for two days while I tried to figure out what went wrong with installing ipw2200 1.0.4 as described in [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

I finally got it working after I did the following:
1.Followed the instruction from  [http://nickselby.com/articles/technology/?a=1807](http://nickselby.com/articles/technology/?a=1807)  for adding kernel headers
2.Manually deleted the directories that were not deleted by the remove-old script.
3.Installed "build-essential"

---

### Post by motion_blur on 2005-06-17
Now it works, it took a long, long time, but now i have go it!
maybe you should add this to the HOWTO
my wireless connetion was working perfect all the time!
but i could not connect to the internet, my wlan got a dynimic IP, but my eth0 a static IP.
your /etc/network/interfaces should look like this:
```
...
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth0 inet static
address 192.168.0.13
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

# laptop built in mini-pci wireless interface:

iface eth1 inet dhcp
wireless-essid MySSID

auto eth1
``` 
there was a problem with the gateway over eth1, the solution:
```
sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo route add default gw 192.168.0.1

``` you have to turn off eth0, eth1 is on, of course.
then have to set a default gateway, this sould be the IP of your AP!!

---

### Post by luca_linux on 2005-06-18
[QUOTE=motion_blur]Now it works, it took a long, long time, but now i have go it!
maybe you should add this to the HOWTO
my wireless connetion was working perfect all the time!
but i could not connect to the internet, my wlan got a dynimic IP, but my eth0 a static IP.
your /etc/network/interfaces should look like this:
```
...
# The primary network interface
iface eth0 inet static
address 192.168.0.13
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

# laptop built in mini-pci wireless interface:

iface eth1 inet dhcp
wireless-essid MySSID

auto eth1
``` 
there was a problem with the gateway over eth1, the solution:
```
sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo route add default gw 192.168.0.1

``` you have to turn off eth0, eth1 is on, of course.
then have to set a default gateway, this sould be the IP of your AP!![/QUOTE]
 My howto supposes you to have already experienced some network configuration...
Anyway, I'll see to add some advices...

---

### Post by IchBin on 2005-06-23
I cannot thank you enough for this tutorial. I told myself that if I were to ever move to linux as my "main" OS that I would **have** to make my Dell Laptop with Centrino work with Linux completely. I couldn't have finished the move without your tutorial, which worked perfectly I must say. Thanks to you, I am now officially in my heart a Linux user. THANK YOU!!!

---

### Post by stamy on 2005-06-26
only for a few seconds, then i have this error message (i start wpa_supplicant without the -B option):

wireless event: cmd=0x8b15 len=20
wireless event: new AP:00:00:00:00:00:00
Added BSSID 00:13:10:0b:18:47 into blacklist (it is the MAC from my wifi router) !!! ???

Why ????
What is this event ? (i dont find anything about it on the web)

Can someone help ?

I have a nx6110 HP notebook with a Intel 2200BG mini-pci card on it.

---

### Post by IchBin on 2005-06-29
Does anyone have a problem with apt-get using this setup? I cannot use apt-get with my wireless card. I get timed out when  I'm on my wireless. As soon as I plug in my wired eth0 I can apt-get just fine. Anyone have any ideas?

---

### Post by mh10190 on 2005-06-30
Hi all,
Im new to ubuntu and linux
And i just installed Horay on my laptop
Everything is wonderful Except the wireless
I flipped thru the forum
And to tell u the truth im a little overwhlmed
Im crossing over from windows
And the terminal intimidates me
im haing a hard time
my situtation is that i use a lynsis wireless router
my laptop has my ipw2200 as the wireless card
im not sure if i have dchp or stati ip
i tried to configure both
as well as the DNS
im quiete confused y its not working either way ](*,) 
im trying to use the terminal 
but im going no where
i really need to be babyed thru this situation
keep in mind i dont even knoe how to install programs at all
Im extremly new
and any help to make it easier on me would br greatly appreciated
thanks

---

### Post by IchBin on 2005-06-30
I just read the sticky that says we're not supposed to ask questions in the How-to forum .... :o I'd suggest you post your question in the appropriate forum m8.

---

### Post by jc3835 on 2005-07-01
[QUOTE=hamustar]hi i have gotten ipw2200 to work without installing any other packages. This was successful in the Beta Array 4 install CD , and now the live Ubuntu 5.04 version.

I have a Compaq Presario 2200 series with 2200BG centrino wlan.
this is what u do, in sudo / root mode,

Step 1
# iwconfig
--  u should see that u have IEEE802.11(B/G) under eth1 (or some other)

Step 2
# iwlist eth1 scan
-- this will scan for all available networks.
-- if there is something picked up, it means ubuntu is able to detect a network.
-- if nothing is detected, pls check your router.

Step 2a: if your wlan network is protected
# iwconfig eth1 essid YOURSSID
-- to define your SSID (access point name)
# iwconfig eth1 key xxxxxxxxxx
-- to define your WEP key, if any.

Step 3
# dhclient eth1
-- this will request a IP from your router, if successfull u will see some messages ending with " bound to 192.168.x.x..." 
-- u are connected to the internet !

hope this helps some of the newbies.[/QUOTE]

I tried doing this, and everything is fine up to the "dhclient eth1" portion...
I've tried everything from default setup, to ndiswrapper, to latest ipw2200 drivers... all to no avail!!  ](*,) 
Currently I'm running 1.0.0 of ipw2200 (latest stable version)... I've got all of my router security disabled and everything is at default (wardrivers are parking outside my house!)
Does ANYONE have any more ideas... I'm all out.  :-#

---

### Post by magalas_79 on 2005-07-02
[QUOTE=ChamPro]Wow... I really don't know what the #*&$ is going on. I haven't had this much trouble with Ubuntu ever.

Here's the beginning of the list of warnings I get when executing make. I tried changing the permissions of a lot of directories to no avail. The make and make install creates no kernel modules whatsoever.
```
zoph@nebosuke:~/Desktop/Downloads/ipw2200/ipw2200-1.0.3$ make
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/home/zoph/Desktop/Downloads/ipw 2200/ipw2200-1.0.3 MODVERDIR=/home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.10'
Makefile:484: .config: No such file or directory
  CC [M]  /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200.o
In file included from include/linux/module.h:9,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/sched.h:4:37: asm/param.h: No such file or directory
In file included from include/linux/types.h:13,
                 from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/posix_types.h:47:29: asm/posix_types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/types.h:14:23: asm/types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .h:32,
                 from /home/zoph/Desktop/Downloads/ipw2200/ipw2200-1.0.3/ipw2200 .c:33:
include/linux/types.h:18: error: syntax error before "__kernel_dev_t"
include/linux/types.h:18: warning: type defaults to `int' in declaration of `__k ernel_dev_t'
include/linux/types.h:18: warning: data definition has no type or storage class
include/linux/types.h:21: error: syntax error before "dev_t"
include/linux/types.h:21: warning: type defaults to `int' in declaration of `dev _t'
```
Maybe I'm heading for a another format. Lovely.[/QUOTE]

Hi all.

I've got a similar problem during ipw2200 compilation. I installed all additional package : kernel source (tree), kernel headers, and gcc, created link to kernel source, but when i launch make I receive a lot of errors. I checked the type of error and it is similiar to ChamPro]Wow's errors, the difference is that i don't get error on .config but only on .h files. Someone can help me?

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/pasquinelli/download/ipw2200-1.0.4 MODVERDIR=/home/pasquinelli/download/ipw2200-1.0.4 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.10'
  CC [M]  /home/pasquinelli/download/ipw2200-1.0.4/ipw2200.o
In file included from include/linux/module.h:10,
                 from /home/pasquinelli/download/ipw2200-1.0.4/ipw2200.h:32,
                 from /home/pasquinelli/download/ipw2200-1.0.4/ipw2200.c:33:
include/linux/sched.h:4:37: asm/param.h: No such file or directory
In file included from include/linux/types.h:13,
                 from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/pasquinelli/download/ipw2200-1.0.4/ipw2200.h:32,
                 from /home/pasquinelli/download/ipw2200-1.0.4/ipw2200.c:33:
include/linux/posix_types.h:47:29: asm/posix_types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/pasquinelli/download/ipw2200-1.0.4/ipw2200.h:32,
                 from /home/pasquinelli/download/ipw2200-1.0.4/ipw2200.c:33:
include/linux/types.h:14:23: asm/types.h: No such file or directory
In file included from include/linux/capability.h:16,
                 from include/linux/sched.h:7,


TNX!

I resolved this problem. There is and error in remove script of ipw2200, read this article : [http://nickselby.com/articles/technology/?a=1807](http://nickselby.com/articles/technology/?a=1807)

---

### Post by luca_linux on 2005-07-02
[QUOTE=jc3835]I tried doing this, and everything is fine up to the "dhclient eth1" portion...
I've tried everything from default setup, to ndiswrapper, to latest ipw2200 drivers... all to no avail!!  ](*,) 
Currently I'm running 1.0.0 of ipw2200 (latest stable version)... I've got all of my router security disabled and everything is at default (wardrivers are parking outside my house!)
Does ANYONE have any more ideas... I'm all out.  :-#[/QUOTE]
 You have to upgrade to ipw2200 1.0.4 in order to have WPA support.

---

### Post by matthew on 2005-07-07
Luca, you are my hero. Thanks! This Howto worked beautifully.

---

### Post by orgyn on 2005-07-09
I'm new in linux, i'm using Mandrake 10.1, so be patient :D.
how do i install packages: build essentials, kernel hearders? 'cause i havent been able to compile the ipw2200 drivers  :?  :-|

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=orgyn]I'm new in linux, i'm using Mandrake 10.1, so be patient :D.
how do i install packages: build essentials, kernel hearders? 'cause i havent been able to compile the ipw2200 drivers  :?  :-|[/QUOTE]

Search for both terms in synaptic. "system" "administration" "synaptic package manager"

---

### Post by miiky on 2005-07-09
Hi.
I noticed that some of you have had the same problems as I. Error messages looks like this on "dmesg |grep ipw":

```
ipw2200: failed to send ASSOCIATE command
ipw2200: failed to send SSID command
ipw2200: ipw_send_system_config failed
ipw2200: failed to send SSID command
ipw2200: failed to send SSID command
ipw2200: no space for Tx
ipw2200: failed to send SSID command
``` 

I got this after upgrading to latest drivers and fw. To fix it, create a file, "/etc/modprobe.d/ipw2200", and insert

```
options ipw2200 hwcrypto=0
```

Also, I had to do "modprobe -r ipw2200", before I could write to the file. 

This was mentioned already back in post [#113](http://ubuntuforums.org/showpost.php?p=185095&postcount=113) by Mike Basinger. However, it seems like no-one has mentioned that it also fixes this problem. (well, I assume it will work for others than me also...)

Anyway, thanks to luca for a great howto, this thread has been most helpful.

my first post on this forum btw  :)

---

### Post by orgyn on 2005-07-09
[QUOTE=poofyhairguy]Search for both terms in synaptic. "system" "administration" "synaptic package manager"[/QUOTE]

as i said i'm a total noob in linux.... still cant make it work, any step by step tutorial?... please.

---

### Post by lmp3 on 2005-07-14
i have tried to follow your HOWTO to the letter (up to an excluding the WPA part,
in which i am not presently interested but cannot get my ipw2200 wireless card to work; 

when i do a "dmesg | grep ipw'  i get the message 

     ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
     ipw2200: Copyright (c) 2003-2004 Intel Corporation

however there seems to be no eth1 device around... for instance when i try iwconfig it only
sees eth0 (my ethernet card).... am i supposed to be doing something else?  :confused:

p.s. in case it's not obvious enough, i am a relative newbie to ubuntu and linux in general...
thanks in advance for your help...

---

### Post by UnNamed on 2005-07-14
Sorry for my poor english.

This is my problem:

If I put in wpa_supplicant.conf a wrong password in psk, reboot the system and type 
"dmesg | grep ipw" ,  i get the message 

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright (c) 2003-2004 Intel Corporation
ipw2200: Detected Intel Pro/Wireless 2200BG Network Connection

..and stop.The connection go up and then down but it seems to work.

If I put in wpa_supplicant.conf the **right** password, the message is:


ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright (c) 2003-2004 Intel Corporation
ipw2200: Detected Intel Pro/Wireless 2200BG Network Connection
ipw2200: failed to send ASSOCIATE command
ipw2200: failed to send SCAN_REQUEST_EXT command
ipw2200: ip_send_system_config failed
ipw2200: failed to send SCAN_REQUEST_EXT command
ipw2200: failed to send SCAN_REQUEST_EXT command
ipw2200: No space for Tx
ipw2200: failed to send SCAN_REQUEST_EXT command
ipw2200: No space for Tx

and so on.

Why? The message looks like the Milky'one but it is a little bit  different.

---

### Post by UnNamed on 2005-07-14
I only had to disable hardware crypto.

Now the connection work!!

---

### Post by Off_Kilter on 2005-07-14
I'm having the same problem, everything looks good, but no ip is coming, and I can't find an error indicating why.

How did you disable the hardware crypto?  I'm willing to try anything to avoid having to boot into windows in the office :)

---

### Post by UnNamed on 2005-07-15
[QUOTE=Off_Kilter]

How did you disable the hardware crypto?  [/QUOTE]

```


echo "options ipw2200 hwcrypto=0" > /etc/modprobe.d/ipw2200


```

---

### Post by matthew on 2005-07-15
I started another thread [here](http://ubuntuforums.org/showthread.php?p=256556#post256556) and was wondering if anyone knew how to upgrade to the new driver from 1.0.4.

---

### Post by luca_linux on 2005-07-18
Ok, I'm back. I've been busy in these days. I'll update my HowTo soon, probably by tomorrow.
Thanks for being patient.

---

### Post by matthew on 2005-07-18
Luca, you're a good man. No stress about taking a little time--it's not like you are being paid to do this. When you get time to do it that will be fine. Just know that we appreciate it!

---

### Post by luca_linux on 2005-07-18
Ok, I've just updated the HowTo.
I've removed the part concerning the modules moving, because it was not needed on my box.
But I'm running a customized 2.6.12 kernel, so I don't know if it woks for Ubuntu default kernel too. Please, let me know if you get troubles.

---

### Post by matthew on 2005-07-18
[QUOTE=luca_linux]Ok, I've just updated the HowTo.
I've removed the part concerning the modules moving, because it was not needed on my box.
But I'm running a customized 2.6.12 kernel, so I don't know if it woks for Ubuntu default kernel too. Please, let me know if you get troubles.[/QUOTE]

It worked beautifully. The only catch was when I ran the remove-old script during the driver installation it also removed the new iee80211 subsystem. I just reinstalled the subsystem and didn't run the remove-old script again and all was well with the world.

Also, since I was just upgrading from 1.0.4 I already had wpa_supplicant installed and configured so I was done once the new driver was installed and I rebooted.

Thanks, again, Luca!!

---

### Post by luca_linux on 2005-07-18
[QUOTE=matthew]It worked beautifully. The only catch was when I ran the remove-old script during the driver installation it also removed the new iee80211 subsystem. I just reinstalled the subsystem and didn't run the remove-old script again and all was well with the world.

Also, since I was just upgrading from 1.0.4 I already had wpa_supplicant installed and configured so I was done once the new driver was installed and I rebooted.

Thanks, again, Luca!![/QUOTE]
 HowTo fixed.
Thanks for the feedback.

---

### Post by kemi on 2005-07-19
For those newbies having trouble compiling the sources.
I'm a newbie also and was having all the same error messages. 
I spent hours on it.
Then I re-booted and went through all the steps again (except for downloading), cutting and pasting each command to make sure I got it right,and... it works!
Don't ask me why, I was very very careful the first time, but now I'm sending this message over my WPA encrypted wireless connection!
Thanks a bunch for your help Luca!
-Mike

---

### Post by zackman2002 on 2005-07-19
I currently dual boot Kubuntu with Windows XP.  I was wondering if upgrading the firmware for the wireless card while running Kubuntu would have any affect on Windows XP.  I was afraid to upgrade the firmware thinking that WPA would stop functioning or the wireless card in general would no longer work in Windows.  Is it safe to upgrade firmware and still use wpa in windows xp?

---

### Post by matthew on 2005-07-20
[QUOTE=zackman2002]I currently dual boot Kubuntu with Windows XP.  I was wondering if upgrading the firmware for the wireless card while running Kubuntu would have any affect on Windows XP.  I was afraid to upgrade the firmware thinking that WPA would stop functioning or the wireless card in general would no longer work in Windows.  Is it safe to upgrade firmware and still use wpa in windows xp?[/QUOTE]

Not to worry. I dual boot with windows (95% Ubuntu, 5% Windows) and have upgraded the firmware while using Ubuntu and it had absolutely no effect on my ability to use wpa with windows.

---

### Post by luca_linux on 2005-07-21
No, this firmware has nothing to do with the one in the chip, the card won't be modified in any way. It's just a *software* layer that handles some control functions to the ipw2200 driver and that is loaded every time and only when you boot in Linux. Other operating systems won't be influenced in any way, because the card is not modified.
So, don't worry!

---

### Post by microsome on 2005-07-21
I tried to install the wpa supplicant. This is the results:
> yyyy@xxx:~/software/ipw2200-1.0.6$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package wpasupplicant
markus@mpk:~/software/ipw2200-1.0.6$ sudo apt-get install wpasupplicant
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any suggestions?

---

### Post by luca_linux on 2005-07-22
Try "sudo apt-get update" before installing the package.

---

### Post by mpdemian on 2005-07-22
hi there,

ok so after going through 19 pages of this thread, I am still in trouble...
I set things up the way Luca suggested (thanks!), and there are no signs of anything out of place, except that with WPA enabled (or WEP with the previous version of the driver, for that matter) the card just won't get the AP's attention.
 If I disable WPA or WEP (and only leave MAC address filtering), I get a clean connection to DHCP and an address.

Someone has a clue? many thanks!

Here are the details:


testing the modules and drivers:

# dmesg| grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

I have the following ieee80211.ko:
# cd /lib/modules
# find -iname ieee80211.ko
./2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211.ko

I then start the wpa:

# wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=11):
     44 45 4d 49 41 4e 5f 48 4f 4d 45                  DEMIAN_HOME
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='DEMIAN_HOME'
Daemonize..

so far so good?
I can even control the card power using the HW Switch From Hell on my laptop:
initially:
---------
eth1      radio off  ESSID:"DEMIAN-home"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

<hw switch on>
eth1      unassociated  ESSID:"DEMIAN-home"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
however, this is where the good news stop. no signal.

what is strange is if I remove and reload ipw2200, I get the same identical status report, but *sometimes* the gnome network monitor shows all sorts of packet traffic over eth1.
Also, if I scan for APs I get:

 # iwlist eth1 scanning
eth1      Scan completed :
Cell 01 - Address: 00:0F:B5:1B:2B:30
                    ESSID:"DEMIAN-home"
Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=72/100  Signal level=-56 dBm
                     Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra: Last beacon: 97ms ago

but I can get no further...

thanks!

ciao --

---

### Post by luca_linux on 2005-07-22
1) Try to use a static IP address just for testing if it's DHCP related.
2) Try to remove "-w" flag when loading wpa_supplicant.
Then let me know.

---

### Post by Stealth on 2005-07-22
LUCA YOU DA MAN!  :) 

I just reinstalled Kubuntu after trying to see what other distros worked with my Inspiron 9300. Nothing came close to Kubuntu's awesome detection and hardware support, all missing was connecting to my WPA network. I've followed this before, and tried it again with no avail, but I was following an older howto, because I see you updated to the 1.0.6 which is what I was trying, having the problems of that ieee80211 thing. Thanks a bunch dude!  \\:D/  :grin:

---

### Post by mpdemian on 2005-07-24
well many thanks for your tips, I have tried several combinations, it looks like if I disable WPA on the AP, I can get an address from DHCP just fine,
but as soon as I start the wpa_supplicant daemon, I get kicked out.
  If I enable WPA on the AP, I no longer get an address without wap_supplicant, which is ok, but I don't get one either when I start it.

(and yes I have checked that the passwords match :-))

So I would conclude that for some reason this doesn't work for me.

The only oddity is that for some reason I end up with two drivers in the kernel, ipw and ipw2200:

 # lsmod | grep ipw
ipw                     8452  0
usbserial              28136  1 ipw
ipw2200                89608  0
firmware_class          9728  1 ipw2200
ieee80211              28900  1 ipw2200
ieee80211_crypt         6472  2 ipw2200,ieee80211
usbcore               107384  6 ipw,usbserial,usbhid,ehci_hcd,uhci_hcd

is this a clue?

if I remove ipw2200, eth1 disappears altogether, while nothing seems to happen if I remove ipw.

but I need it (?) because this is the driver that wpa_supplicant expects to find:

 # wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd


thanks again...

---

### Post by luca_linux on 2005-07-24
Uhm...there's something strange...the only modules you should have are ipw2200 and ieee80211* ones.
Try to reinstall all, after remove the old modules COMPLETELY.

---

### Post by mpdemian on 2005-07-26
uhm... no luck.
I reinstalled everything and zapped the ipw whatever it was, now I have what I consider a clean config but I get the same exact behaviour:

 # lsmod | grep ipw
ipw2200               162568  0
firmware_class          9728  1 ipw2200
ieee80211              44548  1 ipw2200
ieee80211_crypt         6472  2 ipw2200,ieee80211

I am tempted to blame the router/AP but I have no way to test the card and driver using a different router.
 Giving up on this for the time being...

thx anyway, cheers

---

### Post by luca_linux on 2005-07-26
Try updating wpa_supplicant to the latest version. The one from the Ubuntu Repositories is old. You can download the source from here: [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

---

### Post by MadJeff on 2005-07-26
Guys, I'm crying Uncle! I need help with this one.

New IBM ThinkPad X40, new Ubuntu install. I've followed the instructions to the letter and keep hitting an error when I go to run Make on the ieee802.11 components. Here's the error:

> Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

/lib/modules/2.6.10-5-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1 

I've ran the sudo make check_old command and get the same error. It thinks there are still old modules floating around. Just to be sure, I reinstalled from scratch last night and did the procedure on a clean default install, with the same results.

This is my last piece of the Ubuntu puzzle, getting WPA working here at home. If I can beat this, I have decided I'll be standardizing all my linux installs here at home and work, as I've had nothing but good luck with it so far. It rocks!

Any ideas? :-?

---

### Post by 67fbd400_Linux on 2005-07-27
I Just loaded up my Latitude c600 with ubuntu. This forum rocks. I noticed many people having the same problem of connecting with WPA + DHCP. I believe I have found the answer. 

You need to edit your /etc/wpa_supplicant.conf and add ap_scan=2 this allow you to search for hidden ap's. Before I made this change I was not able to locate my ap.                                                                                                                                                               

ap_scan=2
network={
        ssid="APNAME"
        proto=WPA
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="Secret Key"
        group=TKIP
        pairwise=TKIP
}

I also had to change the networking start script to S41networking.

sudo rm /etc/rcS.d/S40networking

sudo ln -s /etc/init.d/networking /etc/rcS.d/S41networking

I added wpasupplicant to the /etc/rcS.d/ directory to start at S40wpa_supplicant.

sudo ln -s /etc/init.d/wpasupplicant /etc/rcS.d/S40wpa_supplicant

The start script order change was because I noticed wpasupplicant was sTarting after networking.

I am also using the default start script for wpasupplicant.

I hope this helps some people get connect thise who can't get IP's this will help.

Luca great job on the how to you might want to add some of this to it.

---

### Post by luca_linux on 2005-07-27
[QUOTE=MadJeff]Guys, I'm crying Uncle! I need help with this one.

New IBM ThinkPad X40, new Ubuntu install. I've followed the instructions to the letter and keep hitting an error when I go to run Make on the ieee802.11 components. Here's the error:

 

I've ran the sudo make check_old command and get the same error. It thinks there are still old modules floating around. Just to be sure, I reinstalled from scratch last night and did the procedure on a clean default install, with the same results.

This is my last piece of the Ubuntu puzzle, getting WPA working here at home. If I can beat this, I have decided I'll be standardizing all my linux installs here at home and work, as I've had nothing but good luck with it so far. It rocks!

Any ideas? :-?[/QUOTE]
 Have you run the command "sudo sh remove-old" in ieee80211-1.0.3 directory?

---

### Post by luca_linux on 2005-07-27
[QUOTE=67fbd400_Linux]I Just loaded up my Latitude c600 with ubuntu. This forum rocks. I noticed many people having the same problem of connecting with WPA + DHCP. I believe I have found the answer. 

You need to edit your /etc/wpa_supplicant.conf and add ap_scan=2 this allow you to search for hidden ap's. Before I made this change I was not able to locate my ap.                                                                                                                                                               

ap_scan=2
network={
        ssid="APNAME"
        proto=WPA
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="Secret Key"
        group=TKIP
        pairwise=TKIP
}

I also had to change the networking start script to S41networking.

sudo rm /etc/rcS.d/S40networking

sudo ln -s /etc/init.d/networking /etc/rcS.d/S41networking

I added wpasupplicant to the /etc/rcS.d/ directory to start at S40wpa_supplicant.

sudo ln -s /etc/init.d/wpasupplicant /etc/rcS.d/S40wpa_supplicant

The start script order change was because I noticed wpasupplicant was sTarting after networking.

I am also using the default start script for wpasupplicant.

I hope this helps some people get connect thise who can't get IP's this will help.

Luca great job on the how to you might want to add some of this to it.[/QUOTE]
 Thanks for the suggesting, I'll add it to my HowTo.
Anyway, as said in the wpa_supplicant documentation, "scan_ssid=1" allows the scanning with SSID-specific Probe Request frames (this can be used to find APs that do not accept broadcast SSID or use multiple SSIDs; this will add latency to scanning, so enable this only when needed).
While "ap_scan=2" let wpa_supplicant performing the scan instead of the driver.
So, I think there may be a bug in ipw2200 on some system configurations and only add the "ap_scan=2" option if you get troubles finding your AP.

---

### Post by mr_crimp on 2005-07-27
First of all, thanks Luca for this excellent HowTo it is very nice for a Newbee like me to have a detailed step by step HowTo like this.

I have the exact same problem as MadJeff (post #198 ) and I am sure that I have run the "sudo sh remove-old" command in the ieee80211-1.0.3 directory.

I have an IBM T42 if that is for any help. 

Thanks

---

### Post by luca_linux on 2005-07-27
What's the output of "sudo sh remove-old" command?

---

### Post by mr_crimp on 2005-07-27
This is the output from the "sudo sh remove-old" command:

```
Checking in /lib/modules/2.6.10-5-686/ for ieee80211 components...

/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211

Above files found.  Remove? [y],n y
``` 

But then when I run the "make" command I get this:

```
Checking in /lib/modules/2.6.10-5-686/build/ for ieee80211 components...

/lib/modules/2.6.10-5-686/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Fejl 1

``` 

Then when I run the "sudo make check_old" command I get the same error as above.

---

### Post by luca_linux on 2005-07-27
Have you press the "y" key and then Enter after "sudo sh remove-old", haven't you?

---

### Post by mr_crimp on 2005-07-27
Yes.

But I've forgot that the first time I ran the command I got this error, but I took a screenshot. Sorry if I should have brought this up before. Here it is:

[IMG]http://users.cybercity.dk/~dsl195400/screen_error.png[/IMG] 

The text at the end of the two last lines says: No such file or directory.

But I don't know if that have something to do with the problem.

---

### Post by luca_linux on 2005-07-27
Have installed the kernel headers?

---

### Post by mr_crimp on 2005-07-27
Yes, linux-headers-2.6.10-5-686.

---

### Post by MadJeff on 2005-07-27
[QUOTE=luca_linux]What's the output of "sudo sh remove-old" command?[/QUOTE]

Here's a complete run of the procedure up to the point where it fails:

> jbolden@snoopy50:~$ sudo tar xvzf ipw2200-fw-2.3.tgz
Password:
LICENSE
ipw-2.3-boot.fw
ipw-2.3-bss.fw
ipw-2.3-bss_ucode.fw
ipw-2.3-ibss.fw
ipw-2.3-ibss_ucode.fw
ipw-2.3-sniffer.fw
ipw-2.3-sniffer_ucode.fw
jbolden@snoopy50:~$ sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/
jbolden@snoopy50:~$ sudo tar xvzf ieee80211-1.0.3.tgz
ieee80211-1.0.3/
ieee80211-1.0.3/net/
ieee80211-1.0.3/net/ieee80211.h.orig
ieee80211-1.0.3/net/ieee80211_crypt.h
ieee80211-1.0.3/net/ieee80211.h
ieee80211-1.0.3/Makefile
ieee80211-1.0.3/LICENSE
ieee80211-1.0.3/remove-old
ieee80211-1.0.3/ieee80211_module.c
ieee80211-1.0.3/ieee80211_crypt_ccmp.c
ieee80211-1.0.3/ieee80211_geo.c
ieee80211-1.0.3/idvals
ieee80211-1.0.3/GIT_SHA1
ieee80211-1.0.3/ieee80211_crypt_tkip.c
ieee80211-1.0.3/ieee80211_rx.c
ieee80211-1.0.3/ieee80211_tx.c
ieee80211-1.0.3/ieee80211_wx.c
ieee80211-1.0.3/INSTALL
ieee80211-1.0.3/CHANGES
ieee80211-1.0.3/ieee80211_crypt.c
ieee80211-1.0.3/ieee80211_crypt_wep.c
jbolden@snoopy50:~$ cd ieee80211-1.0.3
jbolden@snoopy50:~/ieee80211-1.0.3$ sudo sh remove-old
Checking in /lib/modules/2.6.10-5-686/ for ieee80211 components...

/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211
/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211/ieee80211.ko
/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_wep.ko

Above files found.  Remove? [y],n y
jbolden@snoopy50:~/ieee80211-1.0.3$ sudo sh remove-old
Checking in /lib/modules/2.6.10-5-686/ for ieee80211 components...

/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211

Above files found.  Remove? [y],n y
jbolden@snoopy50:~/ieee80211-1.0.3$ cd ..
jbolden@snoopy50:~$ sudo tar xvzf ipw2200-1.0.6.tgz
ipw2200-1.0.6/
ipw2200-1.0.6/pci
ipw2200-1.0.6/load
ipw2200-1.0.6/Makefile
ipw2200-1.0.6/ISSUES
ipw2200-1.0.6/FILES
ipw2200-1.0.6/restart
ipw2200-1.0.6/LICENSE
ipw2200-1.0.6/dvals
ipw2200-1.0.6/remove-old
ipw2200-1.0.6/config
ipw2200-1.0.6/idvals
ipw2200-1.0.6/GIT_SHA1
ipw2200-1.0.6/status
ipw2200-1.0.6/unload
ipw2200-1.0.6/INSTALL
ipw2200-1.0.6/CHANGES
ipw2200-1.0.6/ipw2200.c
ipw2200-1.0.6/ipw2200.h
ipw2200-1.0.6/README.ipw2200
jbolden@snoopy50:~$ cd ipw2200-1.0.6
jbolden@snoopy50:~/ipw2200-1.0.6$ sudo sh remove-old
/lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ieee80211 /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ipw2100 /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ipw2100/ipw2100.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ipw2200 /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko
No modules unloaded.
Above files found.  Remove? [y],n y
CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT=m
CONFIG_IEEE80211_WPA=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IPW2100=m
CONFIG_IPW2100_PROMISC=y
CONFIG_IPW2100_FS_AMILO_M7400=m
CONFIG_IPW2200=m
Above definitions found.  Comment out? [y], n y
jbolden@snoopy50:~/ipw2200-1.0.6$ cd ..
jbolden@snoopy50:~$ cd ieee80211-1.0.3
jbolden@snoopy50:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-686/build/ for ieee80211 components...

/lib/modules/2.6.10-5-686/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
jbolden@snoopy50:~/ieee80211-1.0.3$ sudo make check_old
Checking in /lib/modules/2.6.10-5-686/build/ for ieee80211 components...

/lib/modules/2.6.10-5-686/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
jbolden@snoopy50:~/ieee80211-1.0.3$ 

As I stated before, I wiped and reinstalled just in case I had some extra bits floating around, so this is on a clean install, but I'm still getting the same issue.

---

### Post by 67fbd400_Linux on 2005-07-27
[QUOTE=luca_linux]Thanks for the suggesting, I'll add it to my HowTo.
Anyway, as said in the wpa_supplicant documentation, "scan_ssid=1" allows the scanning with SSID-specific Probe Request frames (this can be used to find APs that do not accept broadcast SSID or use multiple SSIDs; this will add latency to scanning, so enable this only when needed).
While "ap_scan=2" let wpa_suppliant performing the scaninstead of the driver.
So, I think there may be a bug in ipw2200 on some system configurations and only add the "ap_scan=2" option if you get troubles finding your AP.[/QUOTE]


Luca you are correct about a bug in ipw2200. I tried it again without ap_scan=2 and could not find my ap. scan-ssid=1 does not correctly configure somthing. So I just commented it out and using the ap_scan. Working great I appreciate you not flaming me. It says I am a newbie but I have played with alot of distro's and I am a Linux SA for Sprint.

---

### Post by luca_linux on 2005-07-28
@MadJeff: try to unload all ipw2200 and ieee80211* modules and then follow the HowTo again. Then let me know if that worked.

---

### Post by luca_linux on 2005-07-28
[QUOTE=67fbd400_Linux]Luca you are correct about a bug in ipw2200. I tried it again without ap_scan=2 and could not find my ap. scan-ssid=1 does not correctly configure somthing. So I just commented it out and using the ap_scan. Working great I appreciate you not flaming me. It says I am a newbie but I have played with alot of distro's and I am a Linux SA for Sprint.[/QUOTE]
No problem. I don't see why I would have flamed you. Your suggesting has been useful.

---

### Post by majie on 2005-07-28
after this, I lost my wireless connection. How can I look back it?

---

### Post by luca_linux on 2005-07-28
[QUOTE=majie]after this, I lost my wireless connection. How can I look back it?[/QUOTE]
 What do you mean exactly? After adding "ap_scan=2"?

---

### Post by majie on 2005-07-28
[QUOTE=luca_linux]What do you mean exactly? After adding "ap_scan=2"?[/QUOTE]

I checked the post, I have a problem
> You have to install the kernel source package and make a symlink. 

is the kernel-source-2.4.27 package.

and how to make a symlink?

---

### Post by luca_linux on 2005-07-28
Have a look at here: [http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)

---

### Post by _whynot on 2005-07-28
[QUOTE=luca_linux]@MadJeff: try to unload all ipw2200 and ieee80211* modules and then follow the HowTo again. Then let me know if that worked.[/QUOTE]
Thank you so much for your help, luca! I too am finding that the remove-old scripts are not working. When you say to unload all ipw2200 and ieee80211* modules, are you talking about using rmmod or some other method?

Sorry about the newbie question. Your help is greatly appreciated!

---

### Post by luca_linux on 2005-07-28
[QUOTE=_whynot]Thank you so much for your help, luca! I too am finding that the remove-old scripts are not working. When you say to unload all ipw2200 and ieee80211* modules, are you talking about using rmmod or some other method?

Sorry about the newbie question. Your help is greatly appreciated![/QUOTE]
 rmmod is deprecated. Use "modprobe -r" instead.

---

### Post by majie on 2005-07-28
> jie@ubuntu:~/ipw2200-1.0.6$ make

 ERROR: ieee80211.h not found in '/lib/modules/2.6.10-5-386/include'.

 You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
 and point this build to the location where you installed those sources, eg.:

 % make IEEE80211_INC=/usr/src/ieee80211/

 will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1 

> jie@ubuntu:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

grep: /lib/modules/2.6.10-5-386/build//.config: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.10-5-386/build M=/home/jie/ieee80211-1.0.3 MODVERDIR=/home/jie/ieee80211-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2 


what's matter?

---

### Post by _whynot on 2005-07-28
[QUOTE=luca_linux]rmmod is deprecated. Use "modprobe -r" instead.[/QUOTE]
 Ah... didn't know that. Thanks!

I ran the command:
```
sudo modprobe -r ieee80211
```
which gave no feedback, just a new prompt. Then I ran:
```
sudo sh remove-old
```
again just to see if it would take care of the old module. However, I am still getting the errors about references to the old module when I run the make command (see below). Any ideas here?
```
_whynot@mobiletalon:~/Downloads/ieee80211-1.0.3$ sudo make check_old
Checking in /lib/modules/2.6.10-5-686/build/ for ieee80211 components...

/lib/modules/2.6.10-5-686/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
_whynot@mobiletalon:~/Downloads/ieee80211-1.0.3$
```

---

### Post by _whynot on 2005-07-28
[QUOTE=majie]what's matter?[/QUOTE]
Just like the output says, "You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)" before you run the make command.

---

### Post by luca_linux on 2005-07-28
[QUOTE=majie]what's matter?[/QUOTE]
 The first error is related to the second one: in fact ieee80211 was not properly installed because of the second one and the first one just says that you need ieee80211 to be installed before installing ipw2200.
Are you sure you have installed the headers?

---

### Post by luca_linux on 2005-07-28
[QUOTE=_whynot]Ah... didn't know that. Thanks!

I ran the command:
```
sudo modprobe -r ieee80211
```
which gave no feedback, just a new prompt. Then I ran:
```
sudo sh remove-old
```
again just to see if it would take care of the old module. However, I am still getting the errors about references to the old module when I run the make command (see below). Any ideas here?
```
_whynot@mobiletalon:~/Downloads/ieee80211-1.0.3$ sudo make check_old
Checking in /lib/modules/2.6.10-5-686/build/ for ieee80211 components...

/lib/modules/2.6.10-5-686/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
_whynot@mobiletalon:~/Downloads/ieee80211-1.0.3$
```[/QUOTE]
 If you run "lsmod | grep ieee80211", you'll see there are several modules: you have to unload them all, not only the main ieee80211 one.

---

### Post by cs378 on 2005-07-28
First of, i am a big newbie, first time using linux

ok i am in ieee folder

after i type in make i get this kind of error

```
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

find: /lib/modules/2.6.10-5-386/build/: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//.config: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.10-5-386/build M=/home/cs378/ieee80211-1.0.3/ieee80211-1.0.3 MODVERDIR=/home/cs378/ieee80211-1.0.3/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
``` 

i installed apt-get install essential package


thx

---

### Post by luca_linux on 2005-07-28
Have you installed linux-headers and build-essential?

---

### Post by _whynot on 2005-07-28
[QUOTE=luca_linux]If you run "lsmod | grep ieee80211", you'll see there are several modules: you have to unload them all, not only the main ieee80211 one.[/QUOTE]
 When I run:
```
lsmod | grep ieee80211
```
I get nothing. I'm pretty sure I've unloaded everything. And I do have build-essential and linux-headers installed. Weird, eh?

---

### Post by luca_linux on 2005-07-28
Try to seach for ieee80211* files in /lib/modules/ and then delete them.

---

### Post by cs378 on 2005-07-28
[QUOTE=luca_linux]Try to seach for ieee80211* files in /lib/modules/ and then delete them.[/QUOTE]


i have the same problem, you mean delete the ieee80211 folder in /lib/modules/2.6.10-5-386/build/include/config/ieee80211/ ?

thx

---

### Post by MadJeff on 2005-07-28
[QUOTE=luca_linux]Try to seach for ieee80211* files in /lib/modules/ and then delete them.[/QUOTE]

I ended up doing that last night, just went in and renamed the ieee80211 directory and got everything installed. I'm now farther along, but it's still not working ;) I'll work on it some more tonight. 

Thanks for the suggestions!

---

### Post by luca_linux on 2005-07-28
[QUOTE=cs378]i have the same problem, you mean delete the ieee80211 folder in /lib/modules/2.6.10-5-386/build/include/config/ieee80211/ ?

thx[/QUOTE]
 Yes.

---

### Post by luca_linux on 2005-07-28
[QUOTE=MadJeff]I ended up doing that last night, just went in and renamed the ieee80211 directory and got everything installed. I'm now farther along, but it's still not working ;) I'll work on it some more tonight. 

Thanks for the suggestions![/QUOTE]
 But you have to rename it to something not containing "ieee80211". Or just delete it.

---

### Post by cs378 on 2005-07-28
[QUOTE=luca_linux]But you have to rename it to something not containing "ieee80211". Or just delete it.[/QUOTE]

yes i delete it, but still given me problems

```
 
root@ubuntu:/home/cs378/ieee80211-1.0.3/ieee80211-1.0.3 # make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT=m
CONFIG_IEEE80211_WPA=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
Above definitions found.  Comment out? [y], n y

sed: can't read /lib/modules/2.6.10-5-386/build//build/.config: No such file or
directory

make -C /lib/modules/2.6.10-5-386/build M=/home/cs378/ieee80211-1.0.3/ieee80211-
1.0.3 MODVERDIR=/home/cs378/ieee80211-1.0.3/ieee80211-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_module.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_tx.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_rx.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_wx.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_geo.o
  LD [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_wep.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_ccmp.o
  CC [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_tkip.o
  Building modules, stage 2.
  MODPOST
  CC      /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211.mod.o
  LD [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211.ko
  CC      /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt.mod.o
  LD [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt.ko
  CC      /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_ccmp.ko
  CC      /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_tkip.ko
  CC      /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_wep.mod.o
  LD [M]  /home/cs378/ieee80211-1.0.3/ieee80211-1.0.3/ieee80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'

``` 

as you can see im getting the 
```
sed: can't read /lib/modules/2.6.10-5-386/build//build/.config: No such file or
``` 

thx

---

### Post by _whynot on 2005-07-28
Mine is working now... thank you so much luca! You have been a big help.

cs378: I believe I got the same message but I don't think it's a critical error. It looks like it's completing the build. Did you try running:
```
sudo make install
``` after to see if it installs ok?

---

### Post by luca_linux on 2005-07-28
Yes, _whynot is right. This time ieee80211 modules have been made. Now, just "sudo make install".

Enjoy.

---

### Post by majie on 2005-07-28
[QUOTE=luca_linux]The first error is related to the second one: in fact ieee80211 was not properly installed because of the second one and the first one just says that you need ieee80211 to be installed before installing ipw2200.
Are you sure you have installed the headers?[/QUOTE]


I installed linux-headers-2.6.10-5-386

sudo apt-get install linux-headers-2.6.10-5-386

is it right?

It still have same error

> jie@ubuntu:~$ cd ieee80211-1.0.3
jie@ubuntu:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

find: /lib/modules/2.6.10-5-386/build/: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//.config: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.10-5-386/build M=/home/jie/ieee80211-1.0.3 MODVERDIR=/home/jie/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

---

### Post by Magneto on 2005-07-29
do you guys find the wireless adapter going out and having to be reinitialized like a few minutes after being initialized? I get this without fail, after being initialized again aka removing and reinserting the module , it stays up fine.

I had the same problem in windows until updating to the latest driver from intel's site

---

### Post by matthew on 2005-07-29
[QUOTE=Magneto]do you guys find the wireless adapter going out and having to be reinitialized like a few minutes after being initialized? I get this without fail, after being initialized again aka removing and reinserting the module , it stays up fine.

I had the same problem in windows until updating to the latest driver from intel's site[/QUOTE]

I did when I was using the 0.19 driver. Since I upgraded to the 1.0.2 and more recently the 1.0.6 driver I haven't had any problems like that.  What driver version do you have installed?

---

### Post by cs378 on 2005-07-29
[QUOTE=luca_linux]Yes, _whynot is right. This time ieee80211 modules have been made. Now, just "sudo make install".

Enjoy.[/QUOTE]


yes everything is fine hehe thx

---

### Post by Magneto on 2005-07-29
[QUOTE=matthew]I did when I was using the 0.19 driver. Since I upgraded to the 1.0.2 and more recently the 1.0.6 driver I haven't had any problems like that.  What driver version do you have installed?[/QUOTE]
 I have 0.19 - installing  1.0.6 now 
thanks for that

---

### Post by scottylans on 2005-07-31
luca:

again I've tried to run your how to on my install and it just plain didn't work :(
I really think you need to expand on it for complete newbies (since every other part of ubuntu is nice and simple - a lot of REALLY dumb linux people try it - only to get stumped on your tutorial)


I ran the dmesg part of your tutorial and got this.
root@laptop:/home/user # dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
root@laptop:/home/user #


but no ip address



eth1      Link encap:Ethernet  HWaddr 00:12:F0:80:A0:87
          inet6 addr: fe80::212:f0ff:fe80:a087/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:791 (791.0 b)  TX bytes:264 (264.0 b)
          Interrupt:7 Base address:0xa000 Memory:faffc000-faffcfff



i've tried the 

sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
and
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd


and I've tried the 

ap_scan=2
and without the ap_scan=2


:(



EDIT: UPDATE>

I just re-read the past 5 pages, I'm having exactly the same problem as madjeff.

I re-installed from scratch and I tried manually deleting the ieeee directory /files which the remove script didnt do properly - it did seem to build and install ok - but then the same problems as above)

pretty sure madjeff and i are stuck at the same point.
/

---

### Post by scottylans on 2005-08-01
I have managed to get kismet working so I know the 1.06 driver / ieee and firmware seem ok - I just can't get an ip address from my access point, I don't get it :(

Anyone?

---

### Post by luca_linux on 2005-08-01
Are you using DHCP?

---

### Post by srijith on 2005-08-01
Finally I compiled and installed the 1.0.3 ieee80211 subsystem and ipw2200 1.0.6. A small problem I faced was maybe because of my Ubuntu iso. I am using the HP Ubuntu for ncx laptops.

On this installation to compile ieee80211subsystem I had to perform the following symbolic linking
```

ln -s /usr/src/linux-headers-2.6.10-5-386 /lib/modules/2.6.10-5-386/build

```
Note that link to "linux-source-2.6.10" will not work as some include files wants 386 specific file structures. Everything else was a breeze.

Now my nc6120 can connect to WEP, WPA (using wpa_supplicant) and TTLS-PAP (using xsupplicant) wireless networks.

---

### Post by scottylans on 2005-08-01
[QUOTE=luca_linux]Are you using DHCP?[/QUOTE]

To be honest, I don't know - I just followed your tutorial.
I can tell you under Windows I'm using DHCP - and the router is set to give an ip to the card (which works under windows)

Also DHCP works fine on the LAN / ethernet port on the laptop - but not the 2200.

---

### Post by scottylans on 2005-08-01
[QUOTE=luca_linux] 
Try to seach for ieee80211* files in /lib/modules/ and then delete them.[/QUOTE]



[QUOTE=MadJeff]I ended up doing that last night, just went in and renamed the ieee80211 directory and got everything installed. I'm now farther along, but it's still not working ;) I'll work on it some more tonight. 

Thanks for the suggestions![/QUOTE]




Luca:
This is MadJeff's last post - I had the same problem - ieee had to be manually deleted.
My problem is why? - I followed the tutorial /how-to by the book, why is this happening? any idea's?

---

### Post by srijith on 2005-08-01
[QUOTE=scottylans]Luca:
This is MadJeff's last post - I had the same problem - ieee had to be manually deleted.
My problem is why? - I followed the tutorial /how-to by the book, why is this happening? any idea's?[/QUOTE]
I too had to manually delete the ieee80211 directory. Since the remove-old uses regular expressions, simply renaming it to ieee80211-bak or something will not work. Either you have to rename it to something different like "whatanameforadir" or just delete it. 

Not sure why though   :???:

---

### Post by Magneto on 2005-08-02
[QUOTE=srijith]I too had to manually delete the ieee80211 directory. Since the remove-old uses regular expressions, simply renaming it to ieee80211-bak or something will not work. Either you have to rename it to something different like "whatanameforadir" or just delete it. 

Not sure why though   :???:[/QUOTE]
 same here with the ieee80211 directory - the script included to delete the old files failed every time
not a big deal  rm -rf worked fine

---

### Post by luca_linux on 2005-08-02
[QUOTE=scottylans]To be honest, I don't know - I just followed your tutorial.
I can tell you under Windows I'm using DHCP - and the router is set to give an ip to the card (which works under windows)

Also DHCP works fine on the LAN / ethernet port on the laptop - but not the 2200.[/QUOTE]
 My HowTo is not about network configuration, but about getting ipw2200+wpa to work.
You have to configure the gateway, IP addresses, DNS, etc. Just set them up through the Network panel.

---

### Post by luca_linux on 2005-08-02
[QUOTE=Magneto]same here with the ieee80211 directory - the script included to delete the old files failed every time
not a big deal  rm -rf worked fine[/QUOTE]
 Yeah, that's true.

---

### Post by scottylans on 2005-08-02
[QUOTE=srijith]I too had to manually delete the ieee80211 directory. Since the remove-old uses regular expressions, simply renaming it to ieee80211-bak or something will not work. Either you have to rename it to something different like "whatanameforadir" or just delete it. 

Not sure why though   :???:[/QUOTE]


I'm not sure either! :(

I wish Luca would put this stuff in the howto.
I REALLY DO appreciate it - don't get me wrong, but this is the second time I've had to mention things that we're simply not included in the how-to.

For example - the bit about installing gcc, linux-headers - that wasn't in the original FAQ - it was assumed :(

It's GREAT of him to do this for us - it is but when someone points out a flaw with the documentation it should be updated.

I want you (all) to know, not only am I a linux newbie but I'm following the how-to word for word on a FRESH installed copy of ubuntu from the 5.04 CD
every time something goes wrong, I re-start from a fresh re-install.

Therefore I see every problem with the how-to - because I follow it word for word :(

I think there should be at least these 2 changes.


1, information on how to add the repositories in synaptic so the users know EXACTLY (and I quote)  what this means 
"[U]
Since we have to compile the driver from sources, we need the packages: build-essential, gcc, linux-headers-myOwnKernelVersion.[/U]"

and how to actually do it.


2, information on the ieee "bug" thing - so the users know that the remove-old script does NOT work and needs to be manually fixed.

:(

(thanks again luca - but plz update how-to very comprehensively - it will stop a lot of idiot posters (like me!) who ask questions)

---

### Post by scottylans on 2005-08-02
[QUOTE=luca_linux]My HowTo is not about network configuration, but about getting ipw2200+wpa to work.
You have to configure the gateway, IP addresses, DNS, etc. Just set them up through the Network panel.[/QUOTE]


Thanks for the response.
The network panel is greyed out after following your instructions?
Is there any reason why?
The LAN / ethernet section I can change but the wifi = no?
Does the network panel actually recognise the wpa package and the newer drivers for the 2200?

---

### Post by luca_linux on 2005-08-02
Are you sure?
In a previous post you said that the eth1 interface was activated but doesn't get any IP address. So, if eth1 is shown by ifconfig, it'll be shown by the network panel too, which is just a GUI of ifconfig.

---

### Post by luca_linux on 2005-08-02
[QUOTE=scottylans]I'm not sure either! :(

I wish Luca would put this stuff in the howto.
I REALLY DO appreciate it - don't get me wrong, but this is the second time I've had to mention things that we're simply not included in the how-to.

For example - the bit about installing gcc, linux-headers - that wasn't in the original FAQ - it was assumed :(

It's GREAT of him to do this for us - it is but when someone points out a flaw with the documentation it should be updated.

I want you (all) to know, not only am I a linux newbie but I'm following the how-to word for word on a FRESH installed copy of ubuntu from the 5.04 CD
every time something goes wrong, I re-start from a fresh re-install.

Therefore I see every problem with the how-to - because I follow it word for word :(

I think there should be at least these 2 changes.


1, information on how to add the repositories in synaptic so the users know EXACTLY (and I quote)  what this means 
"[U]
Since we have to compile the driver from sources, we need the packages: build-essential, gcc, linux-headers-myOwnKernelVersion.[/U]"

and how to actually do it.


2, information on the ieee "bug" thing - so the users know that the remove-old script does NOT work and needs to be manually fixed.

:(

(thanks again luca - but plz update how-to very comprehensively - it will stop a lot of idiot posters (like me!) who ask questions)[/QUOTE]
 HowTo edited.

---

### Post by scottylans on 2005-08-02
[QUOTE=luca_linux]Are you sure?
In a previous post you said that the eth1 interface was activated but doesn't get any IP address. So, if eth1 is shown by ifconfig, it'll be shown by the network panel too, which is just a GUI of ifconfig.[/QUOTE]



Well it's greyed out - when I go into it, it asks for a SSID and a WEP key??
Surely this means the network control panel isn't fully compatible with the WPA supplicant?


Anyhow!

Here's the results of ifconfig



eth1      Link encap:Ethernet  HWaddr 00:12:F0:80:A0:87
          inet6 addr: fe80::212:f0ff:fe80:a087/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1275 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 Base address:0xa000 Memory:faffc000-faffcfff



but here's something interesting from dmesg

"IPv6 over IPv4 tunneling driver"
"eth1: no IPv6 routers present"

Maybe eth1 is set to only be running on ipv6?

BTW as I mentioned in my other post.

I've tried 
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw  -dd
(no w)

doesn't make a difference.
I think I am very close now :(
Once we work it out - I'll help update the how-to so it's flawless - from  a fresh 5.04 cd to working.

---

### Post by scottylans on 2005-08-02
[QUOTE=luca_linux]Are you sure?
In a previous post you said that the eth1 interface was activated but doesn't get any IP address. So, if eth1 is shown by ifconfig, it'll be shown by the network panel too, which is just a GUI of ifconfig.[/QUOTE]


damnit! I think I am close!!!!!!
I have disabled ALL encryption on my router.
My drivers (ipw) are installed good enough to work fine without encryption! - the problem is definately with the WPA supp!

Also when I logged off my machine it said "wpa disabled, please see /etc/default/wpasupplicant"

So I've checked it out, it says this./



> 
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=0

# Useful flags:
#  -D <driver>		Wireless Driver
#  -i <ifname>		Interface (required, unless specified in config)
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

OPTIONS="-w" 




Does this mean I've done something wrong during the howto?

---

### Post by luca_linux on 2005-08-02
Are you sure you have /etc/wpa_supplican.conf file?
Anyway, try to change "ENABLE=0" to "ENABLE=1" in /etc/default/wpasupplicant.
If it doesn't work, change it back to "0".

Then, also try to remove and reinstall wpasupplicant.

---

### Post by Magneto on 2005-08-02
[QUOTE=luca_linux]Are you sure you have /etc/wpa_supplican.conf file?
Anyway, try to change "ENABLE=0" to "ENABLE=1" in /etc/default/wpasupplicant.
If it doesn't work, change it back to "0".

Then, also try to remove and reinstall wpasupplicant.[/QUOTE]
 just wanted to say thanks for this howto -i setup my intel card faster in linux than in windows
I haven't tried wpa yet but I will soon enough

---

### Post by scottylans on 2005-08-02
[QUOTE=luca_linux]Are you sure you have /etc/wpa_supplican.conf file?
Anyway, try to change "ENABLE=0" to "ENABLE=1" in /etc/default/wpasupplicant.
If it doesn't work, change it back to "0".

Then, also try to remove and reinstall wpasupplicant.[/QUOTE]


I'm going to try this tonight (enable 1 / 0) thing.
I thought maybe that this enabled it anyhow so it didn't matter
"sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd"  ????

How do I remove wpa supplicant?    (thanks)

---

### Post by Gobelet on 2005-08-03
Hello,

I've translated the "Ubuntu + ipw2200 + WPA + Startup Script" wiki entry ([here](http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_en)) into French ([there](http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_fr)).

Hope you'll like it ;)

---

### Post by luca_linux on 2005-08-03
Just remove it through Synaptic or dpkg.

---

### Post by luca_linux on 2005-08-03
[QUOTE=Gobelet]Hello,

I've translated the "Ubuntu + ipw2200 + WPA + Startup Script" wiki entry ([here](http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_en)) into French ([there](http://tvilda.tigbis.lt/dokuwiki/doku.php?id=ubuntu__intel_pro_wireless_2200bg__wpa_mini-howto_fr)).

Hope you'll like it ;)[/QUOTE]
Good work.

---

### Post by scottylans on 2005-08-03
[QUOTE=luca_linux]Just remove it through Synaptic or dpkg.[/QUOTE]


luca:

Tonight I un-installed and re-installed wpa supplicant from synaptic.
The version in synaptic says it's only 0.3.8-1

The version you recommended I download and install at the rest of the tutorial is 0.3.9  

Either way they both don't work.
I also added the   "enabled = 1" in /etc/default/wpasupplicant :(
I have tried setting my WPA pass in the WEP section (pass) in the network control panel.
I've tried not having the network card enabled (de-activate) and then manually starting it (as per the how-to) 
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd


Umm I've with the -w and without

any other idea's at this point? :(

- Scott

---

### Post by luca_linux on 2005-08-03
Try to compile and install the latest development version of wpa_supplicant (0.4.3) from [here](http://hostap.epitest.fi/wpa_supplicant/).
Obviously you first have to remove wpa_supplicant currently installed.

---

### Post by scottylans on 2005-08-03
[QUOTE=luca_linux]Try to compile and install the latest development version of wpa_supplicant (0.4.3) from [here](http://hostap.epitest.fi/wpa_supplicant/).
Obviously you first have to remove wpa_supplicant currently installed.[/QUOTE]

Thanks luca

Also, last night - when I used synaptic to un-install WPA, I then popped open a console session and typed "locate wpa" and all the files could still be found? :( :(

Any idea's why, synaptic should've removed them right?


I re-installed 0.3.8-1 using synaptic anyhow.
Maybe synaptic refused to remove wpa supplicant because it was a manually installed version of 0.3.9?

Can you give me manual instructions on how to remove 0.3.9 plz?

---

### Post by scottylans on 2005-08-03
Hey Luca,

This might help with the FAQ / howto - steal some of the commands the rt2500 howto uses - looks handy.

sudo apt-get install build-essential linux-headers-$(uname -r)

---

### Post by scottylans on 2005-08-04
[QUOTE=luca_linux]Try to compile and install the latest development version of wpa_supplicant (0.4.3) from [here](http://hostap.epitest.fi/wpa_supplicant/).
Obviously you first have to remove wpa_supplicant currently installed.[/QUOTE]


When attempting to compile the new wpa (0.4.3) I get this error.
md5.h:20:25: warning: openssl/md5.h: No such file or directory (amongst others)


UPDATE:

Ok using synaptic, I managed to install the SSL stuff it needed.
Then it compiled ok - but "sudo make install" seemed awfully quick.
it did not make a /etc/default/wpasupplicant.  file either.

when I popped in the sommand to actually START the supplicant (the one with -w in it) it just said unsupported driver "ipw" :(

I don't know why I need a new version of wpa supplicant if others can get on with the old one - there's something missing here.

---

### Post by luca_linux on 2005-08-04
[QUOTE=scottylans]Hey Luca,

This might help with the FAQ / howto - steal some of the commands the rt2500 howto uses - looks handy.

sudo apt-get install build-essential linux-headers-$(uname -r)[/QUOTE]
 HowTo edited.

---

### Post by luca_linux on 2005-08-04
[QUOTE=scottylans]When attempting to compile the new wpa (0.4.3) I get this error.
md5.h:20:25: warning: openssl/md5.h: No such file or directory (amongst others)


UPDATE:

Ok using synaptic, I managed to install the SSL stuff it needed.
Then it compiled ok - but "sudo make install" seemed awfully quick.
it did not make a /etc/default/wpasupplicant.  file either.

when I popped in the sommand to actually START the supplicant (the one with -w in it) it just said unsupported driver "ipw" :(

I don't know why I need a new version of wpa supplicant if others can get on with the old one - there's something missing here.[/QUOTE]
 It's a development version with great improvements, but it's still under heavy development. They also added a GUI. Anyway, I'll look at wpa_supplicant mailing list to see if there's something in particular about ipw.

---

### Post by scottylans on 2005-08-04
[QUOTE=luca_linux]It's a development version with great improvements, but it's still under heavy development. They also added a GUI. Anyway, I'll look at wpa_supplicant mailing list to see if there's something in particular about ipw.[/QUOTE]

Thank you heaps for the help so far - it's been great.

I am confused why this is happening I must admit - there's got to be something we're over-looking - because I've followed the how-to precisely.
Maybe my version of WPA on my AP is not 100% WPA compliant?

Anyhow to re-iterate where I am at.

I can use kismet - using 1.06 drivers so the card works fine.
I can connect to the AP with encryption disabled, works fine.

The wpasupplicant file had "enabled = 0" and "enabled =1" in it - both ways didn't work.

The network control box only mentions WEP not WAP - but I still set my WAP password in there, incase.

---

### Post by luca_linux on 2005-08-04
After searching a bit, I've found that "enabled" should be set on 0.
Anyway, you shouldn't set any encryption option in the network panel, otherwise it won't work at all.
Actually, the GNOME network panel only supports WEP. So delete any password you set there.
What AP have you got?

---

### Post by gerbman on 2005-08-05
I followed your howto carefully, with no success.  When I rebooted, my eth1 (wireless) interface was no longer listed under network config, and I can't get it back.  After taking out the "-w" flag, I got the following output:

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=7):
     47 65 72 62 6d 61 6e                              Gerbman
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Gerbman'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth1' UP
ioctl[SIOCGIFINDEX]: No such device
wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: No such device
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: No such device
wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: No such device
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: No such device
ioctl[SIOCGIFFLAGS]: No such device
rmdir[ctrl_interface]: No such file or directory

Any thoughts?

---

### Post by zencoder on 2005-08-05
[QUOTE=luca_linux]You have to install the kernel source package and make a symlink.[/QUOTE]

Can you tell us exactly what to make a symlink to?

- I've added Universe repository for Hoary and for Security Updates (BIN and SRC)
- I've retrieved the kernel headers AND the kernel source via apt-get
- I've followed your HOWTO to the *letter* up to where we build the ieee80211-1.0.3 package

I am now stuck in exactly the same place that ***juicewvu*** was [here](http://www.ubuntuforums.org/showpost.php?p=140699&postcount=28), except I don't know precisely what to symlink for **/lib/modules/2.6.10-5-386/build**.

Help please!  Thanks for the great work and support for us Centrino users!

---

### Post by luca_linux on 2005-08-05
Could you post your "dmesg | grep ipw"?
The device is not present, so the driver has not been loaded successfully.

---

### Post by gerbman on 2005-08-05
Thanks for the quick reply.  'dmesg | grep ipw' lists nothing.

Here's a little more background information.  When I ran

cd ..
cd ieee80211-1.0.3
make
sudo make install

it errored off with a message about old modules still existing, even though I had already run the 'remove-old' script and said 'y' to deleting old files (you mention this as a bug in your how-to).  The only file/folder that 'make' listed as an old module was 'ieee80211' (can't remember the exact location), so I simply moved this to another location, assuming the compile process would create the necessary folders.  This was probably a bad idea, as I later saw you posted different directions for manually removing old modules.  In a super-noobish move, I didn't write down where I moved the 'ieee80211' directory from, and so can't test whether or not returning the directory to is original location fixes anything. 

Is there a way to restore the original config?

Thanks again, these forums are great,

G

---

### Post by luca_linux on 2005-08-05
If "dmesg | grep ipw" shows nothing, so the driver is not set up correctly.
Anyway, just search for all ieee80211* files and delete them, then also make sure that any ieee80211* module is currently loaded (type "lsmod" to have a list of the currently loaded modules). If there's some, just type "modprobe -r module_name" to unload it.
Then remake the driver.

---

### Post by ape on 2005-08-05
luca_linux,

  Something I discovered today that might be of use in the HOWTO:

  I'd been trying all day to get wpa_supplicant to connect up to my DLink DWL-2100AP all afternoon only to have it attach then disconnect over and over again.  I was using your sample wpa_supplicant.conf file and was trying to connect in using CCMP.  Once I forced this to TKIP using the pairwise directive, I was finally able to connect.

  The DLink AP can use AES, TKIP or both, but for whatever reason, my laptop wouldn't authenticate until I forced TKIP.  (On the other hand, my wife's new iMac G5 connected in just fine using either method.<G>)

Ape

---

### Post by luca_linux on 2005-08-06
Thanks for your feedback.
HowTo edited.

---

### Post by mr_crimp on 2005-08-07
Hi, I have finally got my wireless network working, thanks to your very nice Howto.
I only have one problem left and that is when I boot up my laptop(IBM T42) then it is hanging for about 1min and 20 sec. at the “Configuring network interfaces” part. I have followed the howto step by step. I am pretty new in Linux so I have no idea what causes the long hang time. 

Thanks for the help.

---

### Post by luca_linux on 2005-08-07
Did you also have this problem before installing ipw2200 driver?

---

### Post by mr_crimp on 2005-08-07
No, it first appear after I followed your howto.

---

### Post by luca_linux on 2005-08-07
Is there any error in your dmesg?

---

### Post by scottylans on 2005-08-07
Luca! - I don't know what I did but I re-installed ubuntu from scratch and got it working, finally full WPA and DHCP etc on my 2200....  


I wrote down a couple of things which stumped me and didn't work properly :( - so i'll let you know so you can update the howto.

Now my kismet is broke though - whoops :(

---

### Post by pm4000 on 2005-08-08
Hello !

I'm new to ubuntu , and I try hopelessly to get my wlan connexion work.

My laptop has an Intel 2200BG card. My AP is set up to use WPA2 (PSK/AES) with SSID broadcast disabled (no dhcp).

First, I would like to thank the author for his work on this how-to. It was so easy for a newbie like me to compile and install the drivers and the firmware with such explanations!

With WindowsXP SP2, I had no problem to get a connexion between the intel card and the AP using WPA2.

With ubuntu, when wpa_supplicant is running if I ping my AP (IP 192.168.1.1) I get:
```
root@ubuntu:/home/pm4000 # ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable
From 192.168.1.3 icmp_seq=4 Destination Host Unreachable
...
```

Here is my /etc/wpa_supplicant.conf
```
root@ubuntu:/home/pm4000 # more /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant

# mandatory when ssid broadcast is disabled
ap_scan=2

network={
       ssid="my_ssid"
       mode=0
       proto=WPA2
       key_mgmt=WPA-PSK
       #auth_alg=OPEN
       #pairwise=CCMP
       #group=CCMP
       psk=my_key
}
```

Here is the output of wpa_supplicant with debug (MAC and ssid hidden)
```
root@ubuntu:/home/pm4000 # wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dipw -d
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Priority group 0
   id=0 ssid='my_ssid'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
Own MAC address: eth1_MAC_ADRESS
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Trying to associate with SSID 'my_ssid'
Cancelling scan request
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Own WPA IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=24
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: AP_MAC_ADDRESS
Association event - clear replay counter
Associated to a new BSS: BSSID=AP_MAC_ADDRESS
No keys have been configured - skip key clearing
Network configuration found for the current AP
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Own WPA IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Associated with AP_MAC_ADDRESS
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from AP_MAC_ADDRESS
Setting authentication timeout: 10 sec 0 usec
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=2 type=3 length=117
  EAPOL-Key type=2
WPA: RX message 1 of 4-Way Handshake from AP_MAC_ADDRESS (ver=2)
RSN: msg 1/4 key data - hexdump(len=22): dd 14 00 0f ac 04 fc e8 bb c2 5c e2 c4 69 70 29 fd a3 49 f5 b9 75
RSN: PMKID from Authenticator - hexdump(len=16): fc e8 bb c2 5c e2 c4 69 70 29 fd a3 49 f5 b9 75
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Renewed SNonce - hexdump(len=32): cc 18 a5 97 94 c2 c0 4b a7 9e 24 e8 c6 4f 7a 94 7e e2 bf 22 6e 88 e7 e2 8c 46 e9 e3 3f 9e ae 37
RSN: no matching PMKID found
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: EAPOL-Key MIC - hexdump(len=16): 1a 48 34 b4 e6 6a f9 a0 58 13 2a 7b c0 87 3a 11
WPA: Sending EAPOL-Key 2/4
RX EAPOL from AP_MAC_ADDRESS
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=2 type=3 length=151
  EAPOL-Key type=2
RSN: encrypted key data - hexdump(len=56): 9f c6 39 bf e5 b0 73 05 59 9f 15 fb bc b1 ab 3a f3 cc 1a a2 1a 15 44 2b 5c 09 d9 5e 84 43 d5 8a 80 57 5f 83 c7 29 68 c6 85 fc 1f e3 62 36 10 a7 49 89 c9 6a af e1 29 73
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
WPA: RX message 3 of 4-Way Handshake from AP_MAC_ADDRESS (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 45 ec d7 c4 b8 41
b5 ae b6 f4 eb c9 90 0b c8 78 dd 00
WPA: No WPA/RSN IE for this AP known. Trying to get from scan results
Received 542 bytes of scan results (2 BSSes)
Scan results: 2
WPA: Found the current AP from updated scan results
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_ipw_set_key: alg=CCMP key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 17 01 00 00 00 00
wpa_driver_ipw_set_key: alg=CCMP key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with AP_MAC_ADDRESS [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
***************** HERE I SENT ^C *******************
Signal 2 received - terminating
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=0
wpa_driver_ipw_set_countermeasures: enabled=0
```

And the output of iwconfig before I sent ^C:
```
root@ubuntu:/home/pm4000 # iwconfig eth1
eth1      IEEE 802.11g  ESSID:"my_ssid"
          Mode:Managed  Frequency:2.462 GHz  Access Point: AP_MAC_ADDRESS
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:my_key   Security mode:open
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:27   Missed beacon:0
```

It seems that the AP and eth1 are associated (not sure). eth1 has a static ip:
```
root@neptune:/home/thomas # ifconfig eth1
eth1      Link encap:Ethernet  HWaddr MAC_ADDRESS
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: IPV6_ADDRESS/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:50550 errors:0 dropped:27 overruns:0 frame:0
          TX packets:17937 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:55604 (54.3 KiB)  TX bytes:33700 (32.9 KiB)
          Interrupt:5 Base address:0xc000 Memory:90000000-90000fff
```

So what's wrong ? Any ideas ?

Thanks in advance, and sorry for my poor english!

---

### Post by luca_linux on 2005-08-08
Try the following /etc/wpa_supplicant.conf:
```

ctrl_interface=/var/run/wpa_supplicant

# mandatory when ssid broadcast is disabled
ap_scan=2

network={
       ssid="my_ssid"
       mode=0
       #proto=WPA2
       key_mgmt=WPA-PSK
       #auth_alg=OPEN
       pairwise=CCMP
       group=CCMP
       psk=my_key
}

```
Anyway remember that if you type the key as a string, you'll have to put it between quotes (psk="my_key").

---

### Post by pm4000 on 2005-08-09
[QUOTE=luca_linux]Try the following /etc/wpa_supplicant.conf:
```

ctrl_interface=/var/run/wpa_supplicant

# mandatory when ssid broadcast is disabled
ap_scan=2

network={
       ssid="my_ssid"
       mode=0
       #proto=WPA2
       key_mgmt=WPA-PSK
       #auth_alg=OPEN
       pairwise=CCMP
       group=CCMP
       psk=my_key
}

```
Anyway remember that if you type the key as a string, you'll have to put it between quotes (psk="my_key").[/QUOTE]

Hello and thank you for trying to help me!
This config file doesn't change anything. I get exactly the same outputs from wpa_supplicant, iwconfig and ping.
For the key it's ok, it's hexadecimal so I did not put quotes. If you take a look at the output of wpa_supplicant, it seems to me that the association works  :?
```
[...]
Associated with AP_MAC_ADDRESS
[...]
WPA: Key negotiation completed with AP_MAC_ADDRESS [PTK=CCMP GTK=CCMP]
[...]
```
So I don't understand where is the problem  ](*,) 
Thank you for your attention ;)

---

### Post by luca_linux on 2005-08-09
What happens if you take "ap_scan=2" out?

---

### Post by pm4000 on 2005-08-09
[QUOTE=luca_linux]What happens if you take "ap_scan=2" out?[/QUOTE]

Hello :)

Always the same without "ap_scan=2". Here is the end of output of wpa_supplicant.
```
WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
WPA: RX message 3 of 4-Way Handshake from xx:xx:xx:xx:xx:xx (ver=2)
WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 01 00 45 ec d7 c4 b8 41 b5 ae b6 f4 eb c9 90 0b c8 78 dd 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_ipw_set_key: alg=CCMP key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 88 01 00 00 00 00
wpa_driver_ipw_set_key: alg=CCMP key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE

```

All that is strange :(

---

### Post by luca_linux on 2005-08-09
Have you set gateway and DNS up in the networking panel?

Anyway, let's make a test: try to use WPA instead WPA2 and so TKIP instead of CCMP.
Let's see if that works, to figure out if it's a general problem or just WPA2 related.

---

### Post by pm4000 on 2005-08-09
[QUOTE=luca_linux]Have you set gateway and DNS up in the networking panel?
[/QUOTE]

DNS was set because I can post from this laptop without problem with eth0 (wired) enabled.
Gateway doesn't seems to be useful because I only tried to ping AP's IP (192.168.1.1). I also tested with "route add default gw 192.168.1.1" before pinging but I got nothing new.

[QUOTE=luca_linux]Anyway, let's make a test: try to use WPA instead WPA2 and so TKIP instead of CCMP.
Let's see is that works, to figure out if it's a general problem or just WPA2 related.[/QUOTE]

Ok, I'll try and keep you informed.
Thank you once again :)

---

### Post by pm4000 on 2005-08-09
Ok. I first enabled ssid broadcast without effect.

So I changed the settings to WPA/PSK/TKIP and tested again.
And it works! I'm sending this reply over wifi. Thank you again ;)

But I would prefer to use WPA2 (more secured).
I'll do several other tests (AES intead of TKIP, etc.) and try to discover where the problem (WPA2 or AES ?) comes from.

Bye.

---

### Post by luca_linux on 2005-08-09
Ok. So it's just a config problem.

Set WPA2 on your AP again and try:
```

ctrl_interface=/var/run/wpa_supplicant

proactive_key_caching=1

network={
       ssid="my_ssid"
       scan_ssid=1
       mode=0
       proto=RSN
       key_mgmt=WPA-PSK
       #auth_alg=OPEN
       pairwise=CCMP
       group=CCMP
       psk=my_key
}

```
And if it doesn't work, try:
```

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="my_ssid"
       scan_ssid=1
       mode=0
       proto=RSN
       key_mgmt=WPA-PSK
       #auth_alg=OPEN
       pairwise=CCMP
       group=CCMP
       psk=my_key
}

```

You could also try to update to the latest version of wpa_supplicant (0.4.3), while Ubuntu uses 0.3.8. Quite old.
Look at here: [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

P.S.: Disable ssid broadcast. That's really important hiding it.

---

### Post by pm4000 on 2005-08-09
[QUOTE=luca_linux]```

ctrl_interface=/var/run/wpa_supplicant

proactive_key_caching=1

network={
       ssid="my_ssid"
       scan_ssid=1
       mode=0
       proto=RSN
       key_mgmt=WPA-PSK
       #auth_alg=OPEN
       pairwise=CCMP
       group=CCMP
       psk=my_key
}

```
And if it doesn't work, try:
```

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="my_ssid"
       scan_ssid=1
       mode=0
       proto=RSN
       key_mgmt=WPA-PSK
       #auth_alg=OPEN
       pairwise=CCMP
       group=CCMP
       psk=my_key
}

```
[/QUOTE]

Both config files don't work. For the first one I get the error below:
```
Line 4: Invalid configuration line 'proactive_key_caching=1'.
```
I think this keyword isn't recognized by my version of wpa_supplicant (0.3.8 ).
For the second one it is always the same problem (association and key negociation ok, but can't ping my AP).

Also I tried tu use WPA2/PSK+TKIP instead of CCMP (AES) and it works well. 
In my config file I only changed pairwise and group from CCMP to TKIP (and set my AP consequently)...
I wonder if AES is correctly supported by my kernel (from default installation of Hoary 5.04). How can I check this ?

[QUOTE=luca_linux]
You could also try to update to the latest version of wpa_supplicant (0.4.3), while Ubuntu uses 0.3.8. Quite old.
Look at here: [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

P.S.: Disable ssid broadcast. That's really important hiding it.[/QUOTE]

Ok, I'll now try to update it (I'm new to linux so it will take some time :) ). 
And ssid broadcast is disabled, I just enabled it for testing ;)

---

### Post by luca_linux on 2005-08-09
Using TKIP instead of CCMP (AES) means using WPA. WPA2 only uses CCMP (AES).
Check among the crypto modules (.ko) in /lib/modules/your_kernel_version/....and so on.

---

### Post by mr_crimp on 2005-08-09
[QUOTE=luca_linux]Is there any error in your dmesg?[/QUOTE]

I don't think so. But here is the output from "dmesg" and "dmesg | grep ipw".

dmesg:
```
) @ 0x3ff5a9b4
ACPI: ECDT (v001 IBM    TP-1R    0x00003130 IBM  0x00000001) @ 0x3ff66ebc
ACPI: TCPA (v001 IBM    TP-1R    0x00003130 PTL  0x00000001) @ 0x3ff66f0e
ACPI: BOOT (v001 IBM    TP-1R    0x00003130  LTP 0x00000001) @ 0x3ff66fd8
ACPI: DSDT (v001 IBM    TP-1R    0x00003130 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
Built 1 zonelists
Kernel command line: root=/dev/hda3 ro pci=noacpi acpi_sleep=s3_bios resume=/dev/hda4 vga=0x318 quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (0180a000)
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 65536 bytes)
Detected 598.194 MHz processor.
Using pmtmr for high-res timesource
Console: colour dummy device 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 1030888k/1047872k available (1587k kernel code, 16308k reserved, 714k data, 164k init, 130368k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1183.74 BogoMIPS (lpj=591872)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0a00 (from 0800)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4524k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Found ECDT
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: Embedded Controller [EC] (gpe 28)
ACPI: Power Resource [PUBS] (on)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 14 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
PCI: Discovered primary peer bus 09 [IRQ]
PCI: Using IRQ router PIIX/ICH [8086/24cc] at 0000:00:1f.0
PCI: IRQ 0 for device 0000:00:1f.1 doesn't match PIRQ mask - try pci=usepirqmaskPCI: Found IRQ 11 for device 0000:00:1f.1
PCI: Sharing IRQ 11 with 0000:00:1d.2
PCI: Sharing IRQ 11 with 0000:02:02.0
Simple Boot Flag at 0x35 set to 0x1
audit: initializing netlink socket (disabled)
audit(1123504161.270:0): initialized
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
PCI: Found IRQ 11 for device 0000:00:1f.6
PCI: Sharing IRQ 11 with 0000:00:1f.3
PCI: Sharing IRQ 11 with 0000:00:1f.5
PCI: Sharing IRQ 11 with 0000:02:00.1
pnp: Device 00:09 activated.
ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
 LID SLPB PCI0 UART PCI1 USB0 USB1 AC9M
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4524KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
vesafb: framebuffer at 0xe0000000, mapped to 0xf8880000, using 4608k, total 32704k
vesafb: mode is 1024x768x24, linelength=3072, pages=13
vesafb: protected mode interface info at c000:5710
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
fb0: VESA VGA frame buffer device
Console: switching to colour frame buffer device 128x48
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
ACPI: Processor [CPU] (supports 8 throttling states)
ACPI: Thermal Zone [THM0] (44 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
PCI: Found IRQ 11 for device 0000:00:1f.1
PCI: Sharing IRQ 11 with 0000:00:1d.2
PCI: Sharing IRQ 11 with 0000:02:02.0
ICH4: chipset revision 1
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: HTS548080M9AT00, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 156301488 sectors (80026 MB) w/7877KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
Probing IDE interface ide1...
hdc: UJDA755yDVD/CDRW, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (464 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1943856k swap on /dev/hda4.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
Non-volatile memory driver v1.2
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
input: PC Speaker
Real Time Clock Driver v1.12
inserting floppy driver for 2.6.10-5-686
Floppy drive(s): fd0 is 1.44M
FDC 0 is a National Semiconductor PC87306
irda_init()
NET: Registered protocol family 23
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855PM Chipset.
agpgart: Maximum main memory to use for agp memory: 941M
agpgart: AGP aperture is 256M @ 0xd0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
shpchp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
shpchp: acpi_shpchprm:   Slot sun(1) at s:b:d:f=0x00:02:00:00
shpchp: acpi_shpchprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
shpchp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
shpchp: acpi_shpchprm:   Slot sun(2) at s:b:d:f=0x00:02:00:01
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(1) at s:b:d:f=0x00:02:00:00
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(2) at s:b:d:f=0x00:02:00:01
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
PCI: Found IRQ 11 for device 0000:00:1d.0
PCI: Sharing IRQ 11 with 0000:01:00.0
PCI: Sharing IRQ 11 with 0000:02:00.0
PCI: Sharing IRQ 11 with 0000:02:01.0
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 11, io base 0x1800
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
PCI: Found IRQ 11 for device 0000:00:1d.1
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 11, io base 0x1820
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
PCI: Found IRQ 11 for device 0000:00:1d.2
PCI: Sharing IRQ 11 with 0000:00:1f.1
PCI: Sharing IRQ 11 with 0000:02:02.0
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 11, io base 0x1840
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 3-2: new full speed USB device using uhci_hcd and address 2
PCI: Found IRQ 11 for device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xc0000000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
usb 3-2: USB disconnect, address 2
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(1) at s:b:d:f=0x00:02:00:00
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(2) at s:b:d:f=0x00:02:00:01
pciehp: Fails to gain control of native hot-plug
usb 3-2: new full speed USB device using uhci_hcd and address 3
hw_random hardware driver 1.0.0 loaded
PCI: Found IRQ 11 for device 0000:00:1f.5
PCI: Sharing IRQ 11 with 0000:00:1f.3
PCI: Sharing IRQ 11 with 0000:00:1f.6
PCI: Sharing IRQ 11 with 0000:02:00.1
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49343 usecs
intel8x0: clocking to 48000
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Found IRQ 11 for device 0000:02:00.0
PCI: Sharing IRQ 11 with 0000:00:1d.0
PCI: Sharing IRQ 11 with 0000:01:00.0
PCI: Sharing IRQ 11 with 0000:02:01.0
Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
Yenta: Using INTVAL to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
Yenta: ISA IRQ mask 0x0438, PCI irq 11
Socket status: 30000086
PCI: Found IRQ 11 for device 0000:02:00.1
PCI: Sharing IRQ 11 with 0000:00:1f.3
PCI: Sharing IRQ 11 with 0000:00:1f.5
PCI: Sharing IRQ 11 with 0000:00:1f.6
Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
Yenta: Using INTVAL to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
Yenta: ISA IRQ mask 0x0438, PCI irq 11
Socket status: 30000086
Intel(R) PRO/1000 Network Driver - version 5.5.4-k2
Copyright (c) 1999-2004 Intel Corporation.
PCI: Found IRQ 11 for device 0000:02:01.0
PCI: Sharing IRQ 11 with 0000:00:1d.0
PCI: Sharing IRQ 11 with 0000:01:00.0
PCI: Sharing IRQ 11 with 0000:02:00.0
e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, 1.0.3
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
PCI: Found IRQ 11 for device 0000:02:02.0
PCI: Sharing IRQ 11 with 0000:00:1d.2
PCI: Sharing IRQ 11 with 0000:00:1f.1
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
NET: Registered protocol family 17
ieee80211_crypt: registered algorithm 'TKIP'
ACPI: AC Adapter [AC] (off-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: IBM ThinkPad ACPI Extras v0.8
ibm_acpi: http://ibm-acpi.sf.net/
ibm_acpi: dock device not present
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
mtrr: 0xe0000000,0x2000000 overlaps existing 0xe0000000,0x1000000
IBM machine detected. Enabling interrupts during APM calls.
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
[drm] Initialized drm 1.0.0 20040925
PCI: Found IRQ 11 for device 0000:01:00.0
PCI: Sharing IRQ 11 with 0000:00:1d.0
PCI: Sharing IRQ 11 with 0000:02:00.0
PCI: Sharing IRQ 11 with 0000:02:01.0
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
mtrr: 0xe0000000,0x2000000 overlaps existing 0xe0000000,0x1000000
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (8186 buckets, 65488 max) - 336 bytes per conntrack
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
eth1: no IPv6 routers present
eth0: no IPv6 routers present
``` 

dmesg | grep ipw:
```
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
``` 

I hope this can help.

Thanks

---

### Post by gerbman on 2005-08-10
Got my wireless working (thanks), but now I have no sound.  Updating the wireless driver is the only modification I have made since my sound was working, and yes the volume is turned up  ;-)  Any thoughts?

---

### Post by gerbman on 2005-08-10
[QUOTE=gerbman]Got my wireless working (thanks), but now I have no sound.  Updating the wireless driver is the only modification I have made since my sound was working, and yes the volume is turned up  ;-)  Any thoughts?[/QUOTE]

I stand corrected.  Although the desktop volume control was unmuted, the PCM audio channel in alsamixer somehow got muted.  Doh.

---

### Post by ub13 on 2005-08-10
I am using a derived howto for my ipw2100:
[http://www.ubuntu-de.org/wiki/netzwerk:wlan_wpa_ipw2100](http://www.ubuntu-de.org/wiki/netzwerk:wlan_wpa_ipw2100)
Thanx anyway...

The steps are following the same procedure.
The only difference are the software packages for the 2100.
ipw2100-1.1.2
ieee80211-1.0.3
ipw2100-fw-1.3
ipw2100-1.1.2-ieee80211-1.0.3.patch

I have put the question to different forums, but did not get any answer or clue so far - so I will try it here also...
Everything seems to work fine: dmesg, wpa_cli status, etc. So I can see the AP, but I can't ping it?! Starting with parallel installed WEP is fine.

So, if there are ideas, please don't hold back... ;)

---

### Post by luca_linux on 2005-08-10
I guess you're not getting any IP address, aren't you?
Try to use static IP address instead of DHCP.
Anyway, have you set gateway and DNS up?

---

### Post by pm4000 on 2005-08-11
[QUOTE=luca_linux]Using TKIP instead of CCMP (AES) means using WPA. WPA2 only uses CCMP (AES).
Check among the crypto modules (.ko) in /lib/modules/your_kernel_version/....and so on.[/QUOTE]

Ok. AES module is loaded.
I compiled and installed wpa_supplicant 0.4.3 but it is always the same.
With TKIP only, association works and I can ping my AP, but with CCMP association works too but I can't ping it.
It is very strange, because in both cases the output of wpa_supplicant is ok.

With TKIP:
```
WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (auth)
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
```

With CCMP:
```
WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (auth)
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
```

---

### Post by luca_linux on 2005-08-12
Have you tried WPA2 on another operating system? It could just be that the wireless card doesn't support WPA2. It may also be a problem of ipw2200.

Anyway, don't worry. WPA is secure enough. It takes too long time to be cracked and hours, even days. of packets sniffing.

---

### Post by pm4000 on 2005-08-12
[QUOTE=luca_linux]Have you tried WPA2 on another operating system? It could just be that the wireless card doesn't support WPA2. It may also be a problem of ipw2200.[/QUOTE]

Yes, I tried, and WPA2 works perfectly with WinXP SP2 (I have a dual boot Win/Ubuntu).

[QUOTE=luca_linux]Anyway, don't worry. WPA is secure enough. It takes too long time to be cracked and hours, even days. of packets sniffing.[/QUOTE]
Ok.

I finally set finally my AP to accept both AES and TKIP, so I will now be able to use AES from Win and TKIP from Linux.

Anyway, thank you for your precious help and for this how-to  ;)

---

### Post by luca_linux on 2005-08-12
Then it's the ipw2200 driver that doesn't currently support the WPA2.

Anyway stay tuned! There will probably be news in the future about WPA2.

---

### Post by chruesu on 2005-08-14
THANKS LUCA! 

I really appreciate your work on all those HowTo's!
Thanks to you I already managed to get the new drivers installed.
However, unfortunately I had to re-install my OS and the 2ond time its not working anymore and I have absolutely no idea what to do now

:~$ dmesg |grep ipw
```
ipw2200: failed to send CARD_DISABLE command
```

:~$ iwpriv eth1
```
eth1      Available private ioctl :
          set_power        (8BE0) : set   1 int   & get   0
          get_power        (8BE1) : set   0       & get  80 char
          set_mode         (8BE2) : set   1 int   & get   0
          get_mode         (8BE3) : set   0       & get  80 char
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get  16 char
          reset            (8BE6) : set   0 int   & get   0
          sw_reset         (8BE7) : set   0 int   & get   0
```

:~$ iwconfig eth1
```
eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: FF:00:FF:00:FF:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by luca_linux on 2005-08-14
What laptop have you got?
Anyway, try to reinstall the driver and the latest firmware.

---

### Post by ndub on 2005-08-14
Thank you so much luca, you helpful howto allowed me to make it work almost out of the box.   \\:D/ 
It's been working fine so far (no ssid, channel 11, infrastructure), however I have a minor concern (please forgive me if this  it's already been posted in this long thread):
My HP dv4000 laptop doesn't light up the little WiFi led located under the screen as it does under M$. 
Any clue? I guess this must be hardware related somehow? Anyway it ain't such a big deal, that led's never been working under Linux...
Thank you again,

ndub

---

### Post by luca_linux on 2005-08-15
No problem, there are several ways to do this. Try the following:
```

sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1

```
If it works, you'll probably want to save the passed parameter, so that it automatically turns the led on on boot, so:
create the file /etc/modprobe.d/ipw2200. Then type:
```
sudo echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200
```
If this doesn't work, just let me know and I'll suggest you the other ways.

---

### Post by chruesu on 2005-08-15
Thanks for your fast reply!

[QUOTE=luca_linux]try to reinstall the driver and the latest firmware.[/QUOTE]
Hmm, that's exaclty what I did for about 100 times now...  :-(

Any other suggestions?

---

### Post by bleers on 2005-08-15
great howto.. great people!
I followed each step of the Howto today.
Unfortunately some errors appear. Please could u help me..?
I configured my router for use with static IP and a WPA key..
Also with MAC-access..
I'm a newbie to Ubuntu (Linux) and wlan.
Do u need more info? Thanks in advance...

notebook: IBM Thinkpad R52
router: Netgear WGT624 (latest firmware v3)
OS: Kubunu 5.04 (kernel 2.6.10-5-386)

bleers@bleers:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

bleers@bleers:/etc/network$ sudo tail interfaces
# The primary network interface
iface eth0 inet dhcp
        hostname CP517078-A

iface eth1 inet static
wireless-essid dinky2001
address 192.168.0.3
netmask 255.255.255.0


WPA_SUPPLICANT.CONF :

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid=dinky2001
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
#       pairwise=TKIP
       psk=test1234
}

STANDARD : 

bleers@bleers:/etc$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
Line 5: failed to parse ssid 'dinky2001'.
Line 5: failed to parse ssid 'dinky2001'.
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
Line 10: Invalid PSK 'test1234'.
Line 10: failed to parse psk 'test1234'.
Line 11: WPA-PSK accepted for key management, but no PSK configured.
Line 11: failed to parse network block.
Failed to read configuration file '/etc/wpa_supplicant.conf'.
bleers@bleers:/etc$                               


WITH ap_scan=2 :

bleers@bleers:/etc$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
Line 5: failed to parse ssid 'dinky2001'.
Line 5: failed to parse ssid 'dinky2001'.
proto: 0x1
key_mgmt: 0x2
Line 10: Invalid PSK 'test1234'.
Line 10: failed to parse psk 'test1234'.
Line 11: WPA-PSK accepted for key management, but no PSK configured.
Line 11: failed to parse network block.
Failed to read configuration file '/etc/wpa_supplicant.conf'.
bleers@bleers:/etc$

Log: WEIRD ERROR wih REMOVE OLD, during Howto INSTALL :

bleers@bleers:~/ieee80211-1.0.3$ sudo sh remove-old
Checking in /lib/modules/2.6.10-5-386/ for ieee80211 components...

/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211_crypt_wep.ko

Above files found.  Remove? [y],n y
grep: /lib/modules/2.6.10-5-386//.config: No such file or directory
grep: /lib/modules/2.6.10-5-386//include/linux/autoconf.h: No such file or directory
bleers@bleers:~/ieee80211-1.0.3$          


bleers@bleers:~/ipw2200-1.0.6$ sudo sh remove-old
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211 /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2100 /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2100/ipw2100.ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200 /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200/ipw2200.ko
Unloaded: ipw2200 ieee80211 ieee80211_crypt
Above files found.  Remove? [y],n y
CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT=m
CONFIG_IEEE80211_WPA=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IPW2100=m
CONFIG_IPW2100_PROMISC=y
CONFIG_IPW2100_FS_AMILO_M7400=m
CONFIG_IPW2200=m
Above definitions found.  Comment out? [y], n y
bleers@bleers:~/ipw2200-1.0.6$                     

bleers@bleers:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

/lib/modules/2.6.10-5-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
bleers@bleers:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

/lib/modules/2.6.10-5-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y
Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
bleers@bleers:~/ieee80211-1.0.3$ sudo make install
make -C /lib/modules/2.6.10-5-386/build M=/home/bleers/ieee80211-1.0.3 MODVERDIR=/home/bleers/ieee80211-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_module.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_tx.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_rx.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_wx.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_geo.o
  LD [M]  /home/bleers/ieee80211-1.0.3/ieee80211.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt_wep.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt_ccmp.o
  CC [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt_tkip.o
  Building modules, stage 2.
  MODPOST
  CC      /home/bleers/ieee80211-1.0.3/ieee80211.mod.o
  LD [M]  /home/bleers/ieee80211-1.0.3/ieee80211.ko
  CC      /home/bleers/ieee80211-1.0.3/ieee80211_crypt.mod.o
  LD [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt.ko
  CC      /home/bleers/ieee80211-1.0.3/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt_ccmp.ko
  CC      /home/bleers/ieee80211-1.0.3/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt_tkip.ko
  CC      /home/bleers/ieee80211-1.0.3/ieee80211_crypt_wep.mod.o
  LD [M]  /home/bleers/ieee80211-1.0.3/ieee80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
install -d /lib/modules/2.6.10-5-386/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.10-5-386/net/ieee80211/
install -d `echo /lib/modules/2.6.10-5-386/include | grep "/net\$" || echo /lib/modules/2.6.10-5-386/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h `echo /lib/modules/2.6.10-5-386/include | grep "/net\$" || echo /lib/modules/2.6.10-5-386/include/net`
mkdir -p /lib/modules/2.6.10-5-386/net/ieee80211//.tmp_versions
install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.10-5-386/net/ieee80211//.tmp_versions
/sbin/depmod -a
bleers@bleers:~/ieee80211-1.0.3$   


bleers@bleers:~/ipw2200-1.0.6$ make
mkdir -p /home/bleers/ipw2200-1.0.6/tmp/.tmp_versions
cp /lib/modules/2.6.10-5-386/net/ieee80211/.tmp_versions/*.mod /home/bleers/ipw2200-1.0.6/tmp/.tmp_versions
make -C /lib/modules/2.6.10-5-386/build M=/home/bleers/ipw2200-1.0.6 MODVERDIR=/home/bleers/ipw2200-1.0.6/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/bleers/ipw2200-1.0.6/ipw2200.o
  Building modules, stage 2.
  MODPOST
  CC      /home/bleers/ipw2200-1.0.6/ipw2200.mod.o
  LD [M]  /home/bleers/ipw2200-1.0.6/ipw2200.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
bleers@bleers:~/ipw2200-1.0.6$ sudo make install
mkdir -p /home/bleers/ipw2200-1.0.6/tmp/.tmp_versions
cp /lib/modules/2.6.10-5-386/net/ieee80211/.tmp_versions/*.mod /home/bleers/ipw2200-1.0.6/tmp/.tmp_versions
make -C /lib/modules/2.6.10-5-386/build M=/home/bleers/ipw2200-1.0.6 MODVERDIR=/home/bleers/ipw2200-1.0.6/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
install -d /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/
install -m 644 -c ipw2200.ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/
/sbin/depmod -a
Don't forget to copy firmware to your hotplug's firmware directory and have the
hotplug tools in place.
See INSTALL for more information.
bleers@bleers:~/ipw2200-1.0.6$

---

### Post by ndub on 2005-08-15
Thanks for the quick reply.
Your trick worked. This is great! I now have a fully working system :D 
Just for the record, what were(are) the other solutions?

Thank you again,

ndub

EDIT: the led was up... until I had to reboot. At boot I get messages stating this:

WARNING: /etc/modprobe.d/ipw2200 line 1: ignoring bad line starting with 'echo'

and of course I have to run 
sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1
to make it work again. Maybe some syntax problem?

Hoping a suggestion will come...

ndub

---

### Post by IronKnuckles on 2005-08-15
When I try to run "make" on the ieee80211 driver I get an error about ieee80211 still being in my system. I saw your 'note' about this, but how do I fix it? I don't see the ieee80211 listed when I do lsmod. When I run make, I get an error message telling me to run 'sudo make check_old' instead to remove the old version. This does not work, however, and gives me the same error message. I don't know what I did wrong... Help please?

---

### Post by gerbman on 2005-08-15
[QUOTE=IronKnuckles]When I try to run "make" on the ieee80211 driver I get an error about ieee80211 still being in my system. I saw your 'note' about this, but how do I fix it? I don't see the ieee80211 listed when I do lsmod. When I run make, I get an error message telling me to run 'sudo make check_old' instead to remove the old version. This does not work, however, and gives me the same error message. I don't know what I did wrong... Help please?[/QUOTE]

I had the same problem, and eventually tried [this](http://www.nickselby.com/articles/technology/?a=1807) how-to.  It's very simliar, with a possible difference being the remove-old script used.  Things worked fine for me after doing this.

---

### Post by IronKnuckles on 2005-08-15
[QUOTE=gerbman]I had the same problem, and eventually tried [this](http://www.nickselby.com/articles/technology/?a=1807) how-to.  It's very simliar, with a possible difference being the remove-old script used.  Things worked fine for me after doing this.[/QUOTE]

I got it to install fine now. However, it was rather pointless for me as the only reason I was trying to install the newer driver was in hopes that an issue I had with the slowness of bringing up eth1 (the ipw2200) would be solved. It wasnt.  ](*,) 
But it works. So whatever.

---

### Post by gerbman on 2005-08-15
[QUOTE=IronKnuckles]I got it to install fine now. However, it was rather pointless for me as the only reason I was trying to install the newer driver was in hopes that an issue I had with the slowness of bringing up eth1 (the ipw2200) would be solved. It wasnt.  ](*,) 
But it works. So whatever.[/QUOTE]

I have the same problem when Ubuntu boots.  It hangs for a few minutes when "Configuring network interfaces".  It eventually moves on, and the wireless connection is up and running when the desktop is displayed.  Any thoughts, luca_linux?

---

### Post by luca_linux on 2005-08-15
[QUOTE=chruesu]Thanks for your fast reply!


Hmm, that's exaclty what I did for about 100 times now...  :-(

Any other suggestions?[/QUOTE]
 What laptop have you got?

---

### Post by luca_linux on 2005-08-15
[QUOTE=bleers]great howto.. great people!
I followed each step of the Howto today.
Unfortunately some errors appear. Please could u help me..?
I configured my router for use with static IP and a WPA key..
Also with MAC-access..
I'm a newbie to Ubuntu (Linux) and wlan.
Do u need more info? Thanks in advance...

notebook: IBM Thinkpad R52
router: Netgear WGT624 (latest firmware v3)
OS: Kubunu 5.04 (kernel 2.6.10-5-386)

bleers@bleers:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

bleers@bleers:/etc/network$ sudo tail interfaces
# The primary network interface
iface eth0 inet dhcp
        hostname CP517078-A

iface eth1 inet static
wireless-essid dinky2001
address 192.168.0.3
netmask 255.255.255.0


WPA_SUPPLICANT.CONF :

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid=dinky2001
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
#       pairwise=TKIP
       psk=test1234
}
[/QUOTE]
You have to put the strings into quotes (""), so:
```

WPA_SUPPLICANT.CONF :

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="dinky2001"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
#       pairwise=TKIP
       psk="test1234"
}

```

---

### Post by luca_linux on 2005-08-15
[QUOTE=ndub]Thanks for the quick reply.
Your trick worked. This is great! I now have a fully working system :D 
Just for the record, what were(are) the other solutions?

Thank you again,

ndub

EDIT: the led was up... until I had to reboot. At boot I get messages stating this:

WARNING: /etc/modprobe.d/ipw2200 line 1: ignoring bad line starting with 'echo'

and of course I have to run 
sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1
to make it work again. Maybe some syntax problem?

Hoping a suggestion will come...

ndub[/QUOTE]
 Could you post the content of /etc/modprobe.d/ipw2200? Are you sure you typed the echo command rightly?

The other ways are:
1) Turn the led on through the ACPI interface;
2) Enable the relative button on your laptop if there's one.

---

### Post by luca_linux on 2005-08-15
[QUOTE=gerbman]I have the same problem when Ubuntu boots.  It hangs for a few minutes when "Configuring network interfaces".  It eventually moves on, and the wireless connection is up and running when the desktop is displayed.  Any thoughts, luca_linux?[/QUOTE]
 What AP have you got?
Anyway is there any error or warning message in your dmesg?

---

### Post by ndub on 2005-08-15
luca, this is it:

zulu:~$ ls -la /etc/modprobe.d/ | grep ipw2200
-rw-r--r--    1 root root    55 2005-08-15 16:15 ipw2200
zulu:~$ cat /etc/modprobe.d/ipw2200
echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200

I joined the ls command so you can see permissions are ok. I am not very good at writing scripts and did not try to modify the file.
Thanks for any suggestion!  :roll: 

ndub

---

### Post by bleers on 2005-08-15
Hi luca and others.
I modified wpa_supplicant.conf with luca's remarks.. see below.
But no connection or result...see below. Don't know what to do next...

Wihin my KWiFiManger the eth1 is running/up.
My iwconfig shows at the AP MAC: 00:00:00:00:00:00
please help me.

bleers@bleers:/etc$ tail wpa_supplicant.conf
#ap_scan=2

network={
       ssid="dinky2001"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
#       pairwise=TKIP
       psk="test1234"
}
bleers@bleers:/etc$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=9):
     64 69 6e 6b 79 32 30 30 31                        dinky2001
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='dinky2001'
Daemonize..
bleers@bleers:/etc$

---

### Post by luca_linux on 2005-08-15
[QUOTE=ndub]luca, this is it:

zulu:~$ ls -la /etc/modprobe.d/ | grep ipw2200
-rw-r--r--    1 root root    55 2005-08-15 16:15 ipw2200
zulu:~$ cat /etc/modprobe.d/ipw2200
echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200

I joined the ls command so you can see permissions are ok. I am not very good at writing scripts and did not try to modify the file.
Thanks for any suggestion!  :roll: 

ndub[/QUOTE]
 Ok. I figured it out: open the file /etc/modprobe.d/ipw2200, delete all the content and then put "options ipw2200 led=1" without the quotes ("").
It should work now.
Let me know.

---

### Post by luca_linux on 2005-08-15
[QUOTE=bleers]Hi luca and others.
I modified wpa_supplicant.conf with luca's remarks.. see below.
But no connection or result...see below. Don't know what to do next...

Wihin my KWiFiManger the eth1 is running/up.
My iwconfig shows at the AP MAC: 00:00:00:00:00:00
please help me.

bleers@bleers:/etc$ tail wpa_supplicant.conf
#ap_scan=2

network={
       ssid="dinky2001"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
#       pairwise=TKIP
       psk="test1234"
}
bleers@bleers:/etc$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=9):
     64 69 6e 6b 79 32 30 30 31                        dinky2001
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='dinky2001'
Daemonize..
bleers@bleers:/etc$[/QUOTE]
 There're no errors anymore. Good. Now try to take the "-w" flag out in the wpa_supplicant command you type.

---

### Post by ndub on 2005-08-15
Thank you luca, now it works per-fect-ly!!!

 \\:D/  \\:D/  \\:D/ 

ndub

---

### Post by bleers on 2005-08-15
Luca, I did as you said.. See below a log ..
I see I got the MAC of the router within iwconfig..
And the MAC of my laptop in wpa_supplicant command..
My channel set on the router is 13, but I see below a mentioned channel 0.. 
is that right?
What's next?

I'm spending some hours with reading threads on this topic and other sources... but it's too tricky for me as a newbie.

bleers@bleers:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=9):
     64 69 6e 6b 79 32 30 30 31                        dinky2001
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='dinky2001'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
Own MAC address: 00:12:f0:b2:2e:a8
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Daemonize..

bleers@bleers:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"dinky2001"
          Mode:Managed  Channel=0  Access Point: 00:0F:B5:E1:C2:A8
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
bleers@bleers:~$

---

### Post by gerbman on 2005-08-15
[QUOTE=gerbman]I have the same problem when Ubuntu boots. It hangs for a few minutes when "Configuring network interfaces". It eventually moves on, and the wireless connection is up and running when the desktop is displayed. Any thoughts, luca_linux?
[QUOTE=luca_linux]What AP have you got?
Anyway is there any error or warning message in your dmesg?[/QUOTE][/QUOTE]

I'm connecting to a D-Link DI-524 router.  I'm using DHCP and encryption is disabled, but I am running a MAC address filter.  Here's a segment of my dmesg.  Notice the last line (eth1 is my wireless card).  

```
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.0
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 17
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
eth1: duplicate address detected!
```

Thanks!

---

### Post by luca_linux on 2005-08-16
[QUOTE=bleers]Luca, I did as you said.. See below a log ..
I see I got the MAC of the router within iwconfig..
And the MAC of my laptop in wpa_supplicant command..
My channel set on the router is 13, but I see below a mentioned channel 0.. 
is that right?
What's next?

I'm spending some hours with reading threads on this topic and other sources... but it's too tricky for me as a newbie.
[/QUOTE]
Try to change the channel to something from 1 to 11.
Then let me know.

---

### Post by luca_linux on 2005-08-16
[QUOTE=gerbman]I'm connecting to a D-Link DI-524 router.  I'm using DHCP and encryption is disabled, but I am running a MAC address filter.  Here's a segment of my dmesg.  Notice the last line (eth1 is my wireless card).  

```
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.0
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 17
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
eth1: duplicate address detected!
```

Thanks![/QUOTE]
 It seems like there's another device with the same IP either on your computer or on your network. Check it out and then let me know.

---

### Post by gerbman on 2005-08-16
> I'm connecting to a D-Link DI-524 router. I'm using DHCP and encryption is disabled, but I am running a MAC address filter. Here's a segment of my dmesg. Notice the last line (eth1 is my wireless card).

```
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.0
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 17
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
eth1: duplicate address detected!
```

Thanks!
[QUOTE=luca_linux]It seems like there's another device with the same IP either on your computer or on your network. Check it out and then let me know.[/QUOTE]

The web interface to my router shows the router's address, my PC, and my laptop (I'm using the wireless with my laptop) as being distinct.  I don't have wireless on my PC or the cabled connection on my laptop connected, so I'm confused as to where the duplicate address message is coming from.

---

### Post by 89c51 on 2005-08-16
hello 
i 'm having problems setting up wireless on my vaio s4hp laptop
i followed lucas how to whithout the wpasupplcant (i ll try this later) and the installation whent fine

iwconfig gives me the following

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"mininet"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

when i give 

dmesg | grep ipw

i get

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

the iwlist eth1 scan command gives me

eth1      Scan completed :
          Cell 01 - Address: 00:C0:49:5D:90:4A
                    ESSID:"mininet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=99/100  Signal level=-21 dBm
                    Extra: Last beacon: 180ms ago

when activate the wireless (and deactivate eth0) through Administration>Networing and set the connection to eth1 it cant connect to the router (us robotics 9160) in order to be able to connect to the internet

i configure the connection (eth1) with a static IP

can somebody help

i tried modprobe ipw2200 led=1 but it didnt work
also the rf_kil is 0

---

### Post by chruesu on 2005-08-16
[QUOTE=luca_linux]What laptop have you got?[/QUOTE]

Please forgive that I was annoying you so many times!
Everything is again working flawlessly

The sh remove_old was not working properly but I only had to delete two, three files manually, then again re-install as Luca told me to do.

I'm quite stupdi, however happy now

---

### Post by luca_linux on 2005-08-17
[QUOTE=gerbman]The web interface to my router shows the router's address, my PC, and my laptop (I'm using the wireless with my laptop) as being distinct.  I don't have wireless on my PC or the cabled connection on my laptop connected, so I'm confused as to where the duplicate address message is coming from.[/QUOTE]
You said you've been using DHCP on your AP. Are you sure there's any IP set on Linux for eth1?

---

### Post by luca_linux on 2005-08-17
[QUOTE=89c51]hello 
i 'm having problems setting up wireless on my vaio s4hp laptop
i followed lucas how to whithout the wpasupplcant (i ll try this later) and the installation whent fine

iwconfig gives me the following

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"mininet"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

when i give 

dmesg | grep ipw

i get

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

the iwlist eth1 scan command gives me

eth1      Scan completed :
          Cell 01 - Address: 00:C0:49:5D:90:4A
                    ESSID:"mininet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=99/100  Signal level=-21 dBm
                    Extra: Last beacon: 180ms ago

when activate the wireless (and deactivate eth0) through Administration>Networing and set the connection to eth1 it cant connect to the router (us robotics 9160) in order to be able to connect to the internet

i configure the connection (eth1) with a static IP

can somebody help

i tried modprobe ipw2200 led=1 but it didnt work
also the rf_kil is 0[/QUOTE]
 Have you set the right gateway and DNS addresses up?
As for the led, your Sony should be like my Asus: the led=1 flag doesn't work, because the led turning on/off is handled by ACPI. So look at /proc/acpi/, there should be a folder called "sony" (or something like that) and search for a file called "wlan" or "wled" or something like that. Then type at the console:
```
sudo echo "1" /proc/acpi/sony_folder/led_file
```
where "sony_folder" and "led_file" are respective the folder and the file you've found.
Let me know it that works.

---

### Post by luca_linux on 2005-08-17
[QUOTE=chruesu]Please forgive that I was annoying you so many times!
Everything is again working flawlessly

The sh remove_old was not working properly but I only had to delete two, three files manually, then again re-install as Luca told me to do.

I'm quite stupdi, however happy now[/QUOTE]
Ok. I'm happy for you.

---

### Post by 89c51 on 2005-08-17
the dns and gateaway are the same i use for my wired connection (which works fine)

in the proc/acpi/sony there is nothing like a wlan or similar file there is only a file caled brt (which i believe it has nothing to do with wireless)

---

### Post by Xyresic on 2005-08-17
Hello. I'm pretty new to Linux, so please forgive any silly questions, but I have two problems.

The first is that ipw2200, ieee80211, and ieee80211_crypt don't load up automatically anymore. The little icon in the corner whines about something, then disappears after I modprobe the modules. How can I make them load on startup?

The second:

This is my $dmesg | grep ipw

```
josh@Ozzy:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

```

Is there something that I missed? Removal of some files or editing of something? I don't know how to start going about fixing this.

And I don't know if this is a factor to anything, but lspci gives me

```
0000:03:02.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)
```

So Ubuntu doesn't actually recognize the card? =/

Thanks.

---

### Post by luca_linux on 2005-08-18
[QUOTE=89c51]the dns and gateaway are the same i use for my wired connection (which works fine)

in the proc/acpi/sony there is nothing like a wlan or similar file there is only a file caled brt (which i believe it has nothing to do with wireless)[/QUOTE]
 Type "lsmod" (without the quotes): is there any module name something like "sony"?

Are you sure you don't have any sort of MAC Address Filter on your AP?

---

### Post by luca_linux on 2005-08-18
[QUOTE=Xyresic]Hello. I'm pretty new to Linux, so please forgive any silly questions, but I have two problems.

The first is that ipw2200, ieee80211, and ieee80211_crypt don't load up automatically anymore. The little icon in the corner whines about something, then disappears after I modprobe the modules. How can I make them load on startup?

The second:

This is my $dmesg | grep ipw

```
josh@Ozzy:~$ dmesg | grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

```

Is there something that I missed? Removal of some files or editing of something? I don't know how to start going about fixing this.

And I don't know if this is a factor to anything, but lspci gives me

```
0000:03:02.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)
```

So Ubuntu doesn't actually recognize the card? =/

Thanks.[/QUOTE]
 I think the first problem is related to the second: the old files have not been removed and there's a conflict between the various driver versions.
So, you have to delete all the modules in /lib/modules/your_kernel_version/ named ipw2200.ko and ieee80211*.ko. Then follow the HowTo again.
If you'd rather use the GUI instead of the console to find and remove the files, just type "sudo nautilus --browser" (without the quotes).

---

### Post by 89c51 on 2005-08-18
luca 

first off all thanks for the interest

there is a sony_acpi module but its Used by 0

as for mac filters there arent any configured on the modem/router

its weird because the laptop can see the router but it cant sent data

---

### Post by luca_linux on 2005-08-18
[QUOTE=89c51]luca 

first off all thanks for the interest

there is a sony_acpi module but its Used by 0

as for mac filters there arent any configured on the modem/router

its weird because the laptop can see the router but it cant sent data[/QUOTE]
 What happens if you ping the router?

---

### Post by 89c51 on 2005-08-18
[QUOTE=luca_linux]What happens if you ping the router?[/QUOTE]

tried it and got

unable to reach host (i tried it both in gnome and command line)

---

### Post by luca_linux on 2005-08-18
[QUOTE=89c51]tried it and got

unable to reach host (i tried it both in gnome and command line)[/QUOTE]
 What do your interfaces, resolv.conf files look like?

---

### Post by srijith on 2005-08-19
I am working with the latest ipw2200 drivers and firmwares, latest wpa_supplicant and latest xsupplicant on a TTLS-EAP network. The auth works great and so does the dhcp. However every once in a while (not too frequently, but frequent enough to drive me crazy), ipw2200 firmware complains:

> 
ipw2200: Firmware error detected.  Restarting.

I need to run iwconfig, xsupplicant and dhclient after this to get the connectivity up again.

I have disabled hwcrypto, so it can't be that. Any one has similar problems? The firmware works like a charm in a WPA-PSK setup without the errors.

---

### Post by luca_linux on 2005-08-19
I think it's a problem without solution at the moment because it seems that the firmware doesn't manage to handle the card in some situations.
Anyway, I'll search a bit for your problem and then I'll let you know.

---

### Post by 89c51 on 2005-08-19
[QUOTE=luca_linux]What do your interfaces, resolv.conf files look like?[/QUOTE]

my resolv.conf is

search "name of my isp"
nameserver 192.168.x.x (my dns)

---

### Post by bleers on 2005-08-19
Hi Luca,
I'm still dealing with my setup problem with my wlan.
You posted some advice at 16th August.. unfortunateley it didn't resolve the problem.

Is it necesarry to reboot everytime the configuration (cable modem, router and latop) after adjusting some settings on laptop (wpa_supplicant.conf) and router?

KWifiManager says:
AP: UNKOWN
Signal strength: 0 (out of range)
Searching for network: dinky2001
AP: <the right MAC address>
Local IP: <IP address pointed to my laptop>
Frequency (channel): ? [0]

Please could you give me your email-address? 
Then am I allowed to send you some screenshots of my KwifiManager, router- and Linux- config files?

Thank you.

---

### Post by luca_linux on 2005-08-19
[QUOTE=89c51]my resolv.conf is

search "name of my isp"
nameserver 192.168.x.x (my dns)[/QUOTE]
 And what about your /etc/network/interfaces?

---

### Post by luca_linux on 2005-08-19
[QUOTE=bleers]Hi Luca,
I'm still dealing with my setup problem with my wlan.
You posted some advice at 16th August.. unfortunateley it didn't resolve the problem.

Is it necesarry to reboot everytime the configuration (cable modem, router and latop) after adjusting some settings on laptop (wpa_supplicant.conf) and router?

KWifiManager says:
AP: UNKOWN
Signal strength: 0 (out of range)
Searching for network: dinky2001
AP: <the right MAC address>
Local IP: <IP address pointed to my laptop>
Frequency (channel): ? [0]

Please could you give me your email-address? 
Then am I allowed to send you some screenshots of my KwifiManager, router- and Linux- config files?

Thank you.[/QUOTE]
 My email is available in my profile. Look at [here](http://www.ubuntuforums.org/member.php?userid=14369).
Of course you can contact me whenever you like.

---

### Post by 89c51 on 2005-08-20
[QUOTE=luca_linux]And what about your /etc/network/interfaces?[/QUOTE]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	address 192.168.x.x
	netmask 255.255.255.0
	network 192.168.x.x
	broadcast 192.168.x.x
	gateway 192.168.x.x
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.x.x
	dns-search otenet.gr

iface eth1 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.x.x
wireless-essid mininet
wireless-key 666666



auto eth0

i use different addresses and the same gateaway

---

### Post by luca_linux on 2005-08-20
Try to take the "wireless-key" field out.
Then let me know.

---

### Post by 89c51 on 2005-08-21
[QUOTE=luca_linux]Try to take the "wireless-key" field out.
Then let me know.[/QUOTE]

ok i removed the wep and it worked (for one time)

i tried with a wep and it cant sent data correctly or data are lost (the signal power is 100% and seems ike it can enstablish a connection)

i then again removed the wep and got back to zero ](*,)  ](*,) (it doesnt work again :-x  :-x  :-x  :-x  :-x  :-x )

---

### Post by bleers on 2005-08-21
Luca for me you're a guru!
Thanks to your great support and indepth-sigth I get it working.
My ISP uses DHCP.. this is arranged router-side.. and on my router I setup static IP-addresses for my PC's, with WPA and access-control via MAC...
Little adjustments in some files:
- interfaces: include --> address, netmask, gateway (router address, this I'd forgotten), wireless-essid, wireless-key.
- wpa_supplicant.conf --> "no" ap_scan=2, for so far....

---

### Post by luca_linux on 2005-08-21
[QUOTE=89c51]ok i removed the wep and it worked (for one time)

i tried with a wep and it cant sent data correctly or data are lost (the signal power is 100% and seems ike it can enstablish a connection)

i then again removed the wep and got back to zero ](*,)  ](*,) (it doesnt work again :-x  :-x  :-x  :-x  :-x  :-x )[/QUOTE]
 Try to remake the steps you followed and see if it works. Check out the interfaces file.

---

### Post by luca_linux on 2005-08-21
[QUOTE=bleers]Luca for me you're a guru!
Thanks to your great support and indepth-sigth I get it working.
My ISP uses DHCP.. this is arranged router-side.. and on my router I setup static IP-addresses for my PC's, with WPA and access-control via MAC...
Little adjustments in some files:
- interfaces: include --> address, netmask, gateway (router address, this I'd forgotten), wireless-essid, wireless-key.
- wpa_supplicant.conf --> "no" ap_scan=2, for so far....[/QUOTE]
 Glad to have helped you out.

---

### Post by OKK77 on 2005-08-23
I've been trying and trying but this just don't seem to work.  Gosh.

When I try the **sudo wpa_supplicant -B -i eth1 -D ipw -c /etc/wpa_supplicant.conf -w -dd** command, it gives me this output, and no working connection.

```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=12):
     57 4c 41 4e 2d 53 74 75 64 65 6e 74               WLAN-Student
scan_ssid=1 (0x1)
key_mgmt: 0x8
eap methods - hexdump(len=4): 19 15 0d 00
identity - hexdump_ascii(len=22):
     6b 79 61 77 2e 6f 6b 6b 61 72 2e 32 30 30 35 40   user.name@
     53 4d 55 53 54 55                                 DOMAIN
password - hexdump_ascii(len=8): [REMOVED]
Line: 22 - start of a new network block
ssid - hexdump_ascii(len=4):
     57 4c 41 4e                                       WLAN
scan_ssid=1 (0x1)
PSK (ASCII passphrase) - hexdump_ascii(len=30): [REMOVED]
priority=2 (0x2)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 2
   id=1 ssid='WLAN'
Priority group 0
   id=0 ssid='WLAN-Student'
Daemonize..
```

The wireless connection works fine without WPA.

**/etc/wpa_supplicant.conf**
```
ctrl_interface=/var/run/wpa_supplicant

# SMU WLAN-Student configuration
network={
	ssid="WLAN-Student"
	scan_ssid=1
	key_mgmt=IEEE8021X
	eap=PEAP
	identity="user.name@DOMAIN"
	password="secretuserpassword"
}

# WLAN (WRT54GS @ home) configuration
network={
	ssid="WLAN"
	scan_ssid=1
	psk="blahblahblah@blahblahblah"
	priority=2
}
```

**/etc/default/wpasupplicant**
```
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless Driver
#  -i <ifname>		Interface (required, unless specified in config)
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

OPTIONS="-B -D ipw -i eth1 -c /etc/wpa_supplicant.conf -dd -w"

```

**/etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

# Intel PRO/Wirelss 2200BG
iface eth1 inet dhcp
```

---

### Post by luca_linux on 2005-08-24
Try to take the "-w" flag out.

---

### Post by OKK77 on 2005-08-24
Done that also.  Tried everything I have seen.

---

### Post by 89c51 on 2005-08-24
[QUOTE=luca_linux]Try to remake the steps you followed and see if it works. Check out the interfaces file.[/QUOTE]
OK

this is the first wireless post

it worked now

ill try with wep at the begining and then with wpa and see what i can manage

---

### Post by Psquared on 2005-08-24
Hey luca, I've got an issue with ipw2200 that you may or may not know anything about.  installed Rox-Desktop using 0install. I got it up and running fine and wifi was fine. I let my battery run down accidentally but when I plugged it back in and charged the battery I could not connect.

I am in Windows right now and wifi works, so I can't post the error messages. I ran dmseg, lspci and iwconfig and its clear something is not loading. Would the simplest thing to do be just to reinstall the firmware and ipw2200 1.06?

Thanks.

---

### Post by luca_linux on 2005-08-25
[QUOTE=OKK77]Done that also.  Tried everything I have seen.[/QUOTE]
 Try to set up just one network in your /etc/wpa_supplicant.conf and see if it works. If so, then add the other one, setting the right priority.

---

### Post by luca_linux on 2005-08-25
[QUOTE=89c51]OK

this is the first wireless post

it worked now

ill try with wep at the begining and then with wpa and see what i can manage[/QUOTE]
 Ok. I'm glad to have helped you out.

---

### Post by luca_linux on 2005-08-25
[QUOTE=Psquared]Hey luca, I've got an issue with ipw2200 that you may or may not know anything about.  installed Rox-Desktop using 0install. I got it up and running fine and wifi was fine. I let my battery run down accidentally but when I plugged it back in and charged the battery I could not connect.

I am in Windows right now and wifi works, so I can't post the error messages. I ran dmseg, lspci and iwconfig and its clear something is not loading. Would the simplest thing to do be just to reinstall the firmware and ipw2200 1.06?

Thanks.[/QUOTE]
 Uhm...that's really strange. Before reinstalling, it'd be interesting if you could post the errors.
Try:
```
dmesg > mydmesg.txt
```
And then copy this file on an USB key, a floppy, a cd, or whatever you want.
Then read it on Windows and post the errors.
Thanks for the feedback.

---

### Post by 89c51 on 2005-08-25
[QUOTE=luca_linux]Ok. I'm glad to have helped you out.[/QUOTE]

and i ll just say THANKS A LOT :)  :)  :)

---

### Post by OKK77 on 2005-08-26
Whee, the PEAP authentication works in school now!  The only problem is the DHCP request part.  I wonder why it can't work.  I still can't get WPA-PSK to work at home though.

---

### Post by OKK77 on 2005-08-28
```
eth1      IEEE 802.11g  ESSID:"SSID1"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:1B:02:92
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx   Security mode:open
          Power Management:off
          Link Quality=72/100  Signal level=-50 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5
```

This is the iwconfig output.  Sometimes, it seems associated sometimes it is not.  dhclient requests won't get any response.

---

### Post by luca_linux on 2005-08-29
Have you tried a static IP instead of DHCP?
Anyway, what AP do you connect to?
Can you try to connect to some other AP for testing any compatibility issue?

---

### Post by dixonstalbert on 2005-09-04
hello

I have been trying to get the ipw2200 drivers to install and keep getting stopped because of old ieee80211 modules loaded.

I typed lsmod to see what modules were loaded but i cannot find any listed.

I do not know what to delete manually.

can you help? thank you


here is my terminal log:
root@default:/home/dixon/My Downloads/ieee80211-1.0.3 # make
Checking in /lib/modules/2.6.10-5-686/build/ for ieee80211 components...

/lib/modules/2.6.10-5-686/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
root@default:/home/dixon/My Downloads/ieee80211-1.0.3 #** lsmod**
Module                  Size  Used by
ipv6                  257760  6
speedstep_centrino      7892  1
proc_intf               3908  0
freq_table              4004  1 speedstep_centrino
cpufreq_userspace       4348  1
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
pcmcia                 22244  2
i915                   19552  1
drm                    65172  2 i915
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
af_packet              21992  2
ohci1394               34596  0
yenta_socket           21344  0
pcmcia_core            57984  2 pcmcia,yenta_socket
b44                    21988  0
mii                     4896  1 b44
i2c_i801                8364  0
i2c_core               22320  1 i2c_i801
snd_intel8x0           32352  2
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  1
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore              10016  3 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
usbhid                 31936  0
ehci_hcd               32708  0
uhci_hcd               32816  0
usbcore               119000  4 usbhid,ehci_hcd,uhci_hcd
intel_agp              22140  1
agpgart                33608  3 drm,intel_agp
pcspkr                  3496  0
rtc                    12472  0
md                     47440  0
dm_mod                 59420  1
capability              4648  0
evdev                   9344  0
commoncap               7712  1 capability
tsdev                   7520  0
sbp2                   23816  0
ieee1394              108312  2 ohci1394,sbp2
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  0
lp                     11144  0
parport                36744  2 parport_pc,lp
ext3                  137256  1
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ahci                   10724  0
sr_mod                 17188  0
cdrom                  40220  1 sr_mod
sd_mod                 17776  3
sg                     38400  0
ata_piix                9124  7
libata                 49316  2 ahci,ata_piix
scsi_mod              127552  6 sbp2,ahci,sr_mod,sd_mod,sg,libata
unix                   28276  846
thermal                13320  0
processor              22452  2 speedstep_centrino,thermal
fan                     4388  0
fbcon                  37504  0
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  0
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb
root@default:/home/dixon/My Downloads/ieee80211-1.0.3 #

---

### Post by luca_linux on 2005-09-04
Search for ieee802*.ko files in /lib/modules/your_kernel_version and for ipw2200.ko in the same directory. Delete these files manually.

---

### Post by dixonstalbert on 2005-09-04
ipw2200 finally installed and working!!!!!

thank you for replying

I searched from the root directory and could not find any instances of ieee80211* and lsmod did not show any ieee80211 modules loaded- but I kept getting the same error message about modules loaded...

I reformatted the partition and reinstalled ubuntu 5.04 from the DVD image I downloaded.

I got an error message when i tried to install linux-headers and again I got the same error message regarding ieee80211 modules even though I again could not find them
them in /lib/modules/2.6.10-5-686 subdirectorys

I reformatted again and this time installed from downloaded CD image.

I noticed this time uname = 2.6.10-5-**386** .

I did not get any errors with linux headers and the remove-old worked first time!


dmesg | grep ipw reports new driver loaded and i have been on the internet for one hour without a disconnect (only lasted a few minutes before)

Beware the DVD version of Ubuntu and the 2.6.10-5-686 !!!!

---

### Post by OKK77 on 2005-09-05
[QUOTE=luca_linux]Have you tried a static IP instead of DHCP?
Anyway, what AP do you connect to?
Can you try to connect to some other AP for testing any compatibility issue?[/QUOTE]
 Hi luca,  I've noticed that the connection association with my AP is very intermittent.  I monitored it through my AP's WLAN status page and sometimes, the card is there and sometimes, it just disappears.  So, I guess it is more of a connection problem still.  The same problem in my school too.  Maybe I'll try doing everything from scratch again.  Is there any other known situation like mine?

---

### Post by shizow on 2005-09-07
i followed the how-to but without the wpa stuff

i can connect  to every network, when i know the ssid

but when i do iwlist eth1 scan, i always get "no scan results"
when i  am connected i get the result of the net i am connected but nothing more

---

### Post by luca_linux on 2005-09-07
[QUOTE=dixonstalbert]ipw2200 finally installed and working!!!!!

thank you for replying

I searched from the root directory and could not find any instances of ieee80211* and lsmod did not show any ieee80211 modules loaded- but I kept getting the same error message about modules loaded...

I reformatted the partition and reinstalled ubuntu 5.04 from the DVD image I downloaded.

I got an error message when i tried to install linux-headers and again I got the same error message regarding ieee80211 modules even though I again could not find them
them in /lib/modules/2.6.10-5-686 subdirectorys

I reformatted again and this time installed from downloaded CD image.

I noticed this time uname = 2.6.10-5-**386** .

I did not get any errors with linux headers and the remove-old worked first time!


dmesg | grep ipw reports new driver loaded and i have been on the internet for one hour without a disconnect (only lasted a few minutes before)

Beware the DVD version of Ubuntu and the 2.6.10-5-686 !!!![/QUOTE]
 Are you sure you were installing the right kernel-headers package?

---

### Post by luca_linux on 2005-09-07
[QUOTE=OKK77]Hi luca,  I've noticed that the connection association with my AP is very intermittent.  I monitored it through my AP's WLAN status page and sometimes, the card is there and sometimes, it just disappears.  So, I guess it is more of a connection problem still.  The same problem in my school too.  Maybe I'll try doing everything from scratch again.  Is there any other known situation like mine?[/QUOTE]
 Can you try to disable WPA (both on your AP and on your box) and just connect with ipw2200 (and wep at most)?

---

### Post by luca_linux on 2005-09-07
[QUOTE=shizow]i followed the how-to but without the wpa stuff

i can connect  to every network, when i know the ssid

but when i do iwlist eth1 scan, i always get "no scan results"
when i  am connected i get the result of the net i am connected but nothing more[/QUOTE]
 Have you tried the various options (scan_ssid=1, ap_scan=2) mentioned in the HowTo?

---

### Post by jackjeraco on 2005-09-07
when i get to the step:
[I]
Now your system is clean and it's time to make and install ieee80211, so:
Code:

cd .. 
cd ieee80211-1.0.3
make
sudo make install
[/I]

I get this:
[I]Checking in /lib/modules/2.6.10-5-686/build/ for ieee80211 components...

find: /lib/modules/2.6.10-5-686/build/: No such file or directory
grep: /lib/modules/2.6.10-5-686/build//.config: No such file or directory
grep: /lib/modules/2.6.10-5-686/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.10-5-686/build M=/home/jr/Downloads/ieee80211-1.0.3 MODVERDIR=/home/jr/Downloads/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.10-5-686/build: No such file or directory.  Stop.
make: *** [modules] Error 2[/I]

I realize this is saying there is no /build directory...WHY?  I followed step by step and am completely stumped.  Thanks in advance with a quickness! ](*,)

---

### Post by jackjeraco on 2005-09-07
NEVERMIND...man I am an ID10TS!!!!!!!!!!   ](*,)

---

### Post by Magneto on 2005-09-08
okay here is my setup

dell latitude c640 to which i added a mini-pci bg2200 for around 20 bucks new on ebay :)

i have a docking station too so when in docked mode I need to rearrange my ethernet port numbering etc



So i have  two files in /etc/network/interface  - if.2 and if.3


[Color=Blue]if.2  - this file gets copied to /etc/networks/interfaces when I startup into runlevel 2 which I don't have to call with grub since it  is the default runlevel and by default I am docked- I call an item I labeled "Ubuntu Docked" from my bootloader menu
[/color]

```
#Modified for runlevel script support
#Docking Station Profile
#
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth2


# The primary network interface
#iface eth0 inet static
#address 192.168.0.17
#netmask 255.255.255.0
#gateway 192.168.0.1


#Docking Station interface
iface eth1 inet static
address 192.168.0.17
netmask 255.255.255.0
#gateway 192.168.0.1



iface eth2 inet static
address 192.168.5.17
netmask 255.255.255.0
gateway 192.168.5.73
wireless-essid somecrap

auto eth1

auto eth2


```


[Color=Blue]if.3  - this file gets copied to /etc/networks/interfaces when I startup into runlevel 3 which I call with the number 3 in my grub boot commands under the menu item I call "Ubuntu Docked"
[/color]
```
#Modified for runlevel script support
#Mobile Profile
#
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth0 inet static
address 192.168.0.17
netmask 255.255.255.0
#gateway 192.168.0.1



iface eth1 inet static
address 192.168.5.17
netmask 255.255.255.0
gateway 192.168.5.73
wireless-essid somecrap

auto eth0

auto eth1


```


[Color=Blue]Next I created two wifi_wpa scripts to be copied to wifi_wpa.sh for initialization of the supplicant on the right interface. They are again named by runlevel.[/color]


/etc/init.d/wifi_wpa2

```
 

#! /bin/sh
# wifi: wpa_supplicant init
#Docked version
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth2 -c /etc/wpa_supplicant.conf -D ipw -w -dd
fi

exit 0

```





/etc/init.d/wifi_wpa3

```
 

#! /bin/sh
# wifi: wpa_supplicant init
#Mobile version
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
fi

exit 0

```







Now some good stuff. In order to get the system to start up everything real nice I have a script called "netprofile" which is located in /etc/init.d and is linked in /etc/rc2.d/S08netprofile and /etc/rc3.d/S08netprofile.  rc3.d is the folder that contains all the runlevel scripts for runlevel 3 which if you recall is my "mobile" runlevel.
I also put a link to this script in /usr/bin so that I can use it easy anytime I need to.





```
#!/bin/sh
RUNLEVEL=`runlevel| awk '{ print $2 }'`

case "$1" in
    start|force-reload)
	echo -n "Configuring Networking: "
	echo cp /etc/network/if.$RUNLEVEL /etc/network/interfaces
	cp /etc/network/if.$RUNLEVEL /etc/network/interfaces
	cp /etc/init.d/wifi_wpa$RUNLEVEL /etc/init.d/wifi_wpa.sh 
	rmmod 3c59x; rmmod ipw2200; rmmod ieee80211; rmmod ieee80211_crypt_tkip; rmmod ieee80211_crypt
	modprobe 3c59x; /etc/init.d/wifi_wpa.sh; modprobe ipw2200; ifup -a
	echo "Done"
	;;
    mobile)
	echo -n "Configuring Mobile Networking "
	cp /etc/network/if.3 /etc/network/interfaces 
	cp /etc/init.d/wifi_wpa3 /etc/init.d/wifi_wpa.sh
	rmmod 3c59x; rmmod ipw2200; rmmod ieee80211; rmmod ieee80211_crypt_tkip; rmmod ieee80211_crypt
	modprobe 3c59x; /etc/init.d/wifi_wpa.sh; modprobe ipw2200; ifup -a
	echo "Done"
	;;
    docked)
	echo -n "Configuring Docked Networking "
	cp /etc/network/if.2 /etc/network/interfaces
	cp /etc/init.d/wifi_wpa2 /etc/init.d/wifi_wpa.sh
	rmmod 3c59x; rmmod ipw2200; rmmod ieee80211; rmmod ieee80211_crypt_tkip; rmmod ieee80211_crypt
	modprobe 3c59x; /etc/init.d/wifi_wpa.sh; modprobe ipw2200; ifup -a
	echo "Done"
	;;
    restart)
	echo -n "Restarting Wireless and Onboard Ethernet: "
	rmmod 3c59x; rmmod ipw2200; rmmod ieee80211; rmmod ieee80211_crypt_tkip; rmmod ieee80211_crypt
	modprobe 3c59x; modprobe ipw2200; ifup -a
	echo "Done"
	;;
    stop)
	echo -n "Stopping Wireless and Onboard Ethernet: "
	rmmod 3c59x; rmmod ipw2200; rmmod ieee80211; rmmod ieee80211_crypt_tkip; rmmod ieee80211_crypt
	echo "Done"
	;;
    *)
	echo "Usage: /etc/init.d/netprofile {start|mobile|docked|restart|stop|force-reload}"
	exit 1
	;;
esac

exit 0


```






I do something similar for X to differentiate between my laptop screen and monitor.


Good howto - I wish my atheros wireless pci cards worked as well as my intel.

---

### Post by alvonsius on 2005-09-08
[QUOTE=luca_linux]Have you tried a static IP instead of DHCP?
Anyway, what AP do you connect to?
Can you try to connect to some other AP for testing any compatibility issue?[/QUOTE]

I currently having similar problems here, I cannot connect to AP with DHCP. But when I use a static IP (on my office) I connected perfectly, and when I connect to my university DHCP (3 different AP, two different building, 3 different floor), I only get a request message (querying 4 ... 13 ... blah blah ... sleep ...). Is this maybe a vendor specific? I'm using Compaq M2232AP, I already installed the new driver, I uninstalled wpa_supplicant (coz I never use it, and my network dont implement WPA) ... everything .. but why with this DHCP ...  ](*,) 

PS; is there any negative effect if I using ndiswrapper? I wanna try it, but affraid if there is any effect ... and afraid if I cannot uninstall it  ](*,)

---

### Post by OKK77 on 2005-09-08
[QUOTE=luca_linux]Can you try to disable WPA (both on your AP and on your box) and just connect with ipw2200 (and wep at most)?[/QUOTE]

It works fine without WPA.

This is the iwconfig eth1 output.

```
eth1      IEEE 802.11g  ESSID:"WLAN"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:1B:02:92
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=78/100  Signal level=-51 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3
```

ifconfig eth1
```
eth1      Link encap:Ethernet  HWaddr 00:12:F0:35:C4:B5
          inet addr:10.0.0.110  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe35:c4b5/64 Scope:Link
          UP BROADCAST RUNNING ALLMULTI MULTICAST  MTU:1500  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:98665 (96.3 KiB)  TX bytes:23842 (23.2 KiB)
          Interrupt:21 Base address:0x6000 Memory:a0202000-a0202fff
```

So I guess everything is fine and dandy like this.

---

### Post by OKK77 on 2005-09-08
I'm having the same problem on another notebook now.  *sigh*

```
root@localhost:/home/okkar # iwconfig eth1
eth1      IEEE 802.11g  ESSID:"WLAN"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:1B:02:92
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:B520-7BE5-C410-2A26-47C7-EE9C-E656-42E3   Security mode:open
          Power Management:off
          Link Quality=79/100  Signal level=-49 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

root@localhost:/home/okkar # iwconfig eth1
eth1      unassociated  ESSID:"WLAN"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by dixonstalbert on 2005-09-09
[QUOTE=luca_linux]Are you sure you were installing the right kernel-headers package?[/QUOTE]

 Hi luca

I used:

sudo apt-get install linux-headers-$(uname -r) 

from your HOWTO.

Does soemthing else have to be changed for a different kernel header?



BTW: I did not understand forum guidelines. Am I posting my questions in the right forum? Or should I not post questions to a HOWTO thread?

---

### Post by luca_linux on 2005-09-12
@ people getting issues with DHCP:

I guess it's WPA related, so maybe you can try to install (compiling from sources) the latest development version of wpa_supplicant (that is 0.4.4), that is stable enough (so don't worry for this) and has the latest features and patches.
Here it is: [http://hostap.epitest.fi/releases/wpa_supplicant-0.4.4.tar.gz](http://hostap.epitest.fi/releases/wpa_supplicant-0.4.4.tar.gz)

I don't know if this will help, but maybe it's worth trying.

Remember to unistall the wpa_supplicant currently installed.

Then let me know and post your experience.

---

### Post by luca_linux on 2005-09-13
@ people getting issues with DHCP:

Try this patch against ipw2200 1.0.6: [http://people.redhat.com/pjones/ipw2200/broadcast.patch](http://people.redhat.com/pjones/ipw2200/broadcast.patch)

---

### Post by OKK77 on 2005-09-14
How do I assign static IP?

---

### Post by alvonsius on 2005-09-14
[QUOTE=luca_linux]@ people getting issues with DHCP:

Try this patch against ipw2200 1.0.6: [http://people.redhat.com/pjones/ipw2200/broadcast.patch](http://people.redhat.com/pjones/ipw2200/broadcast.patch)[/QUOTE]


Uhm ... Luca, could you show me how to do the patch? Thanks ...

---

### Post by luca_linux on 2005-09-15
[QUOTE=alvonsius]Uhm ... Luca, could you show me how to do the patch? Thanks ...[/QUOTE]
 Of course! Just type:
```

cd ipw2200-1.0.6
patch -p1 < /dir_where_the_patch_is/broadcast.patch

```

Then just follow the HowTo.

---

### Post by OKK77 on 2005-09-16
[QUOTE=luca_linux]@ people getting issues with DHCP:

I guess it's WPA related, so maybe you can try to install (compiling from sources) the latest development version of wpa_supplicant (that is 0.4.4), that is stable enough (so don't worry for this) and has the latest features and patches.
Here it is: [http://hostap.epitest.fi/releases/wpa_supplicant-0.4.4.tar.gz](http://hostap.epitest.fi/releases/wpa_supplicant-0.4.4.tar.gz)

I don't know if this will help, but maybe it's worth trying.

Remember to unistall the wpa_supplicant currently installed.

Then let me know and post your experience.[/QUOTE]

Is anyone having problem compiling this?  I'm having errors with md5.c file.

---

### Post by net_benjo on 2005-09-17
Hello,

I've followed this HOWTO and I think I did everything correctly.  I had to manualy remove old ieee80211 module. 

Now when I turn on my computer I was expecingt to be connected to my wireless automatically.  But my wireless does not work.  this is what I get when I type iwconfig:
lo        no wireless extensions.

eth0      unassociated  ESSID:"bosna"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

Can anybody help give me a hint as to what I need to do for wireless to work?  

thanks

---

### Post by luca_linux on 2005-09-17
Are you using WPA?

---

### Post by FishFoot on 2005-09-17
Hey all,

Luca, thanks for the great guide.  I'm having some trouble though.  I've been through this (and a couple of other) guides and I've not had much success.  I'm sure it was working at one point but it isn't now, and I can't get WEP or WPA to work.  

What I'd like to do is clear out anything that I may have screwed up and start from scratch.  Trouble is I don't know which config files and programs should be cleared out and I'm not quite sure how to clear them once I've figured out what they are.

I know I've played with wpasupplicant, modprobe, and I've followed the above guide twice to no avail.  I tried another guide that suggested using ndiswrapper and the win drivers.  I think I've removed everything from all this but I'm not sure.

On a related note, what are the implications of using the ubuntu networking config GUI tool.  How well does it play with the other network tools and scripts like ifconfig, iwconfig and ifup/ifdown?

I hope somebody can help
FishFoot.

---

### Post by net_benjo on 2005-09-17
[QUOTE=luca_linux]Are you using WPA?[/QUOTE]

Yes luca_linux, I am using WPA-PSK. I know becase that is how my windows connects to my wireless...

Ben

---

### Post by luca_linux on 2005-09-18
[QUOTE=net_benjo]Yes luca_linux, I am using WPA-PSK. I know becase that is how my windows connects to my wireless...

Ben[/QUOTE]
 Type:
```
dmesg | grep ipw
```
and post the result.

---

### Post by luca_linux on 2005-09-18
[QUOTE=FishFoot]Hey all,

Luca, thanks for the great guide.  I'm having some trouble though.  I've been through this (and a couple of other) guides and I've not had much success.  I'm sure it was working at one point but it isn't now, and I can't get WEP or WPA to work.  

What I'd like to do is clear out anything that I may have screwed up and start from scratch.  Trouble is I don't know which config files and programs should be cleared out and I'm not quite sure how to clear them once I've figured out what they are.

I know I've played with wpasupplicant, modprobe, and I've followed the above guide twice to no avail.  I tried another guide that suggested using ndiswrapper and the win drivers.  I think I've removed everything from all this but I'm not sure.

On a related note, what are the implications of using the ubuntu networking config GUI tool.  How well does it play with the other network tools and scripts like ifconfig, iwconfig and ifup/ifdown?

I hope somebody can help
FishFoot.[/QUOTE]
 Yeah, except for the WPA you can use the GUI tool.
Does you wireless connection work without WEP/WPA?

---

### Post by FishFoot on 2005-09-18
[QUOTE=luca_linux]Yeah, except for the WPA you can use the GUI tool.
Does you wireless connection work without WEP/WPA?[/QUOTE]

Not at the moment, it did at some point.  That's why I want to clear everything out.  I'm sure I just got things a little mixed up and if I can get back to ground zero and then start again it will work... I hope.

Thanks for the reply
FishFoot

---

### Post by net_benjo on 2005-09-18
[QUOTE=luca_linux]Type:
```
dmesg | grep ipw
```
and post the result.[/QUOTE]
 this is the output for dmesg | grep ipw:

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

---

### Post by luca_linux on 2005-09-18
[QUOTE=net_benjo]this is the output for dmesg | grep ipw:

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[/QUOTE]
 Everything seems fine, so the problem isn't there.
Does it connect without WEP/WPA?

---

### Post by net_benjo on 2005-09-18
[QUOTE=luca_linux]Everything seems fine, so the problem isn't there.
Does it connect without WEP/WPA?[/QUOTE]
 I'm not sure I understood your question, but I'll try answering anyways.  I can use wired conneciton no problem. But I have problem with wireless internet.  My router is set to use WPA and I cannot connect to it.  But even if I set my router to use WEP, i still cannot connect to it.

I could connect to WEP enabled wireless BEFORE I followed this HOWTO.  Now neither WPA nor WEP works...Let me post the output of iwconfig to see if that tells you anything more.

lo        no wireless extensions.

eth0      unassociated  ESSID:"bosna"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

thanks again.

---

### Post by luca_linux on 2005-09-18
I just wanted to know if it connects when you disable wpa on the router.
Anyway, are you using DHCP or static IP?
If you're using the DHCP, try to use static IP and let me know.

---

### Post by davinci123 on 2005-09-18
Hello, I am a total n00b to Linux and Ubuntu so please in advance excuse my ignorance! I have been trying to install my ipw2200 on a Thinkpad R50e on and on for a couple of weeks ago. When I run make on the ieee80211-1.0.3 directory, I receive this:
> 
sed: can't read /lib/modules/2.6.12-8-686/build//build/.config: No such file or directory
make -C /lib/modules/2.6.12-8-686/build M=/home/aarona/Desktop/ieee80211-1.0.3 MODVERDIR=/home/aarona/Desktop/ieee80211-1.0.3 modules
/usr/src/linux-headers-2.6.12-8-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-8-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found[PHP]
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-8-686'
CC [M]  /home/aarona/Desktop/ieee80211-1.0.3/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/aarona/Desktop/ieee80211-1.0.3/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/aarona/Desktop/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-8-686'
make: *** [modules] Error 2

Can someone please help me? It seems as though the first line: "/lib/modules/2.6.12-8-686/build//build/.config" is an invalid path because of the double slashes. I followed the directions verbatium until this point

Thanks in Advance,
Aaron

---

### Post by luca_linux on 2005-09-19
GCC is not installed on your system: just install it from Synaptics or apt.

---

### Post by davinci123 on 2005-09-19
Thank you luca! What a silly oversight on my part. I haven't tested WPA yet, but non-secured wireless is working great!

Take care,
Aaron

---

### Post by jhuff on 2005-09-19
Is there anyway to upgrade the linux headers without having to reinstall ipw2200?  

I have a lot of updates waiting to be downloaded and installed, its just a pain to lose my wireless connection and having to go the the entire installation process all over again to get the wireless card working.

---

### Post by luca_linux on 2005-09-20
If you run another kernel, you'll have to recompile ipw2200.
If you just upgrade the linux headers (and I don't see the need without running a new kernel), then you won't probably have to recompile it.

---

### Post by yopnono on 2005-09-20
Have tried this to install the drives for my 2200 card. And all I get is make : command not found??? is not make inc in the built 5.10?

---

### Post by luca_linux on 2005-09-20
You have to install the package build_essential as specified in the HowTo.

---

### Post by yopnono on 2005-09-20
[QUOTE=luca_linux]You have to install the package build_essential as specified in the HowTo.[/QUOTE]
Is that not kind of stupid, that it's not inc by default?
Anyhow thanks

Are you talking about the [http://www.ubuntu.com/support/documentation/](http://www.ubuntu.com/support/documentation/)
How to section?
That have no info on anything.

Argh have not time for this I'm back to windows. I will have a go on this som other time. Or I try another dist of linux.

---

### Post by luca_linux on 2005-09-20
No, it's not included since this is basically a desktop-oriented distro.
Anyway, I was referring to MY HowTo, the HowTo of this thread.
At the top, in the first part of it, it's explained that you need some packages, such as build-essential, gcc, linux-headers, etc.

---

### Post by yopnono on 2005-09-20
[QUOTE=luca_linux]No, it's not included since this is basically a desktop-oriented distro.
Anyway, I was referring to MY HowTo, the HowTo of this thread.
At the top, in the first part of it, it's explained that you need some packages, such as build-essential, gcc, linux-headers, etc.[/QUOTE]
 Well on a desktop you some times need to install drivers, so make is needed.

I will ha a look in you howto

---

### Post by shizow on 2005-09-20
[QUOTE=luca_linux]Have you tried the various options (scan_ssid=1, ap_scan=2) mentioned in the HowTo?[/QUOTE]

no, because i do not need wpa, just wep

i reinstalled the driver again, but i have the same problem
i cannot scan, but when i know the essid and password i can connect withput any problems

any help

---

### Post by bryan986 on 2005-09-22
After you start wpa_supplicant

You can enter the wpa command line interface as such:
```

sudo wpa_cli

```

In that mode you can see the status of the wpa connection as it tries to authenticate with the AP

From there you can enter commands such as
```

status

```
To see information about the connection

or

```

help

```
to get a list of other information

It was a really helpful too when getting my connection to work

---

### Post by megan at terrormachine on 2005-09-27
I apologize if this was covered in other posts. On WPA networks that do not broadcast an SSID is it possible to still use the method explained in this howto? My wpa_cli status says:

bssid=00:00:00:00:00:00
pairwise_cipher=UNKNOWN
group_cipher=UNKNOWN
key_mgmnt=UNKNOWN
wpa_state=SCANNING
Supplicant PAE state=DISCONNECTED
suppPortStatus=Unauthorized
EAP state=DISABLED

I installed Ubuntu today as someone dropped a boxful of disks off at my workplace. Previously I was using ndiswrapper. this is a little different.

---

### Post by netox on 2005-09-28
Wow. Thanks so much for this.  Ever since I installed Hoary I was getting a Fatal Error message, and then I upgraded to the latest ipw drivers with another tutorial and it didn't solve the problem.  I followed your tutorial and I didn't get one single error message, so, once again, thanks a lot.

---

### Post by bryan986 on 2005-09-28
[QUOTE=megan at terrormachine]I apologize if this was covered in other posts. On WPA networks that do not broadcast an SSID is it possible to still use the method explained in this howto? My wpa_cli status says:

bssid=00:00:00:00:00:00
pairwise_cipher=UNKNOWN
group_cipher=UNKNOWN
key_mgmnt=UNKNOWN
wpa_state=SCANNING
Supplicant PAE state=DISCONNECTED
suppPortStatus=Unauthorized
EAP state=DISABLED

I installed Ubuntu today as someone dropped a boxful of disks off at my workplace. Previously I was using ndiswrapper. this is a little different.[/QUOTE]

in your wpa_supplicant.conf
make sure you have your ssid set

```

network={
        ...other stuff...
        ssid="MYSSID"    # Change to your ssid
	...other stuff...
}

```

if that does not work you can try

```

sudo iwconfig eth1 essid myssid

```

to set your ssid

where eth1 is your wireless device
and where myssid is your ssid

---

### Post by luca_linux on 2005-09-29
[QUOTE=megan at terrormachine]I apologize if this was covered in other posts. On WPA networks that do not broadcast an SSID is it possible to still use the method explained in this howto? My wpa_cli status says:

bssid=00:00:00:00:00:00
pairwise_cipher=UNKNOWN
group_cipher=UNKNOWN
key_mgmnt=UNKNOWN
wpa_state=SCANNING
Supplicant PAE state=DISCONNECTED
suppPortStatus=Unauthorized
EAP state=DISABLED

I installed Ubuntu today as someone dropped a boxful of disks off at my workplace. Previously I was using ndiswrapper. this is a little different.[/QUOTE]
Yeah, just add to /etc/wpa_supplicant.conf:
```
scan_ssid=1
```
As already suggested in the HowTo.
That does the trick.

---

### Post by luca_linux on 2005-09-29
[QUOTE=netox]Wow. Thanks so much for this.  Ever since I installed Hoary I was getting a Fatal Error message, and then I upgraded to the latest ipw drivers with another tutorial and it didn't solve the problem.  I followed your tutorial and I didn't get one single error message, so, once again, thanks a lot.[/QUOTE]
Glad to have helped you out.

---

### Post by megan at terrormachine on 2005-09-29
Thanks for the suggestions Bryan and Luca but still no joy. This is what my iwconfig looks like
```

eth1      IEEE 802.11-DS  ESSID:"Transmatofluffer 5000"  Nickname:"HERMES I"
Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00 
Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
Retry limit:4   RTS thr:off   Fragment thr:off
Encryption key:off
Power Management:off

```
and here is my wpa_supplicant.conf
```

root@terrormachine:~# more /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
network={
ssid="Transmatofluffer 5000"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
psk="supursekrutpassword"
}

```
I've tried with and without both ap_scan and pairwise options.
If anyone can point out what I'm doing wrong lemme know! Thanks!

---

### Post by luca_linux on 2005-09-30
Try to first take "ap_scan" out, then "pairwise" and then both of them.

---

### Post by billeman on 2005-10-01
Im getting an error because i cant delete one of the files:

troels@troels:~/download/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

/lib/modules/2.6.10-5-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Fejl 1

all the prior steps have worked without errors..

What is wrong??

Billeman

---

### Post by megan at terrormachine on 2005-10-02
[QUOTE=billeman]Im getting an error because i cant delete one of the files:
troels@troels:~/download/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...
/lib/modules/2.6.10-5-386/build/include/config/ieee80211
Above files found.  Remove? [y],n y
Old ieee80211 references found.  In order to build the ieee80211
subsystem, prior versions must first be removed.  You can perform
this task by running this makefile as root via:
% sudo make check_old
and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Fejl 1
all the prior steps have worked without errors..
What is wrong??
Billeman[/QUOTE]
You'll need to remove that dir manually, as there is a bug with the script that causes it to not be removed (I can only guess it's because Ubuntu uses sudo to issue all root permissioned commands)
Try:
```

sudo rm -rf /lib/modules/2.6.10-5-386/build/include/config/ieee80211

```
If you don't feel comfortable deleting it you can move it out of the /lib/modules/2.6.10-5-386/build path.


As for my own problems, I have tried the config file all 3 ways and could not get this to work. Since in iwconfig it states my AP mac is 00:00:00:00:00:00 I was assuming it wasn't seeing my AP, possibly because I have my WPA config on the router to not broadcast my SSID. Anyhow, I've given up hope. I will just wait until the powers that be decide to listen to the suggestions and make WPA standard in future releases. Thanks for all input though! :D

---

### Post by marstell on 2005-10-04
Hi.
I have a Fedora Core 4. A few days ago I followed the instructions in the Luca_Linux's how-to and all was Ok. I installed ieee80211, ipw2200, wpa_supplicant (I use WPA) and I was able to connect regularly.

A few days later I had to reinstall the system, since I wasn't able to boot anymore.
I updated the kernel from 2.6.11-1.1369_FC4 to 2.6.13-1.1526_FC4 (in the previous installation I didn't do that... so I installed the wireless card with the old kernel).

Well, I tried to follow the instructions in the how-to another time, but now, at the end of installation, after typing 

# wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd    

nothing happens
if i type [FONT="Fixedsys"]iwconfig[/FONT] i receive "Encryption key:off" when in the previous installation i could see the exadecimal format of my key and after typing 

ifconfig eth1 up
dhclient eth1

i can't receive an ip address from DHCP....

I tried to follow the instructions reported [here]("http://http://www.ces.clemson.edu/linux/fc2-ipw2200.shtml")
which should be just for my kernel, but nothing...... I cant't connect anyway.....

I can't understand where I'm wrong! I'm sure to do the same things I did the previous time.... 

This is my /etc/wpa_supplicant.conf file:

[FONT="Fixedsys"]ctrl_interface=/var/run/wpa_supplicant
network={
ssid="3Com"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
psk="<my password>"
}[/FONT]

(the same information I wrote the previous time)

Here is what  I get when I type

[FONT="Fixedsys"][root@localhost ~]# wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=4):
     33 43 6f 6d                                       3Com
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=31): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='3Com'
Daemonize..
[root@localhost ~]#  [/FONT]


And here is the output of iwconfig after typing the instruction above:

[FONT="Fixedsys"][root@localhost ~]# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR="Red"]Warning: Driver for device eth1 has been compiled with version 18
of Wireless Extension, while this program supports up to version 17.
Some things may be broken...[/COLOR]

eth1      [COLOR="Red"]unassociated[/COLOR]  ESSID:"3Com"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:CB:A9:DB:B6
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Encryption key:off[/COLOR]
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
[/FONT]

Are there any other information I have to post?
Have you got any idea?
Thank you

---

### Post by marstell on 2005-10-05
Hi. My problem must be about WPA.
In fact today I tried to disable security mode in my access point and then I was able to reach the network and connect to the Internet via Wireless.

Then I retried to set WPA-PSK in the wireless configuration, I retried to type

ifconfig eth1 up
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd 
dhclient eth1 

but nothing. I can't reach the network.

I controlled in autoconf.h and i have:
CONFIG_CRYPTO
CONFIG_CRYPTO_ARC4
CONFIG_CRC32
CONFIG_CRYPTO_MICHAEL_MIC
CONFIG_CRYPTO_AES_586
regularly set to  1

Any idea? What can I control or do to be able to use WPA-PSK??
(I remember you that in the previous installation all was OK....)

Thanks in advance

P.S. Today I have updated wireless-tools to version 28 from 27, and  wpa_supplicant to 0.4.5 from 0.3.9

---

### Post by strawman on 2005-10-06
I just want to thank you for this howto.  I updated to "breezy badger" and it comes with the latest driver/firmware (ipw2100 for me), so i was able to install wpa_supplicant, follow the rest of the howto and now i'm using wpa in ubuntu on my hp nc8000 laptop.  Thanks again!

---

### Post by luca_linux on 2005-10-07
@ Marstell: Does it work if you use static IP instead of DHCP?

---

### Post by marstell on 2005-10-07
Hi Luca_linux and thanks for you reply.

No. I tried typing 
ifconfig eth1 192.168.1.8 
but i can't reach the network .

But today I discovered a "nice" thing..
if I type
wpa_supplicant  -c /etc/wpa_supplicant.conf -i eth1 -D ipw -w -dd
instead of
wpa_supplicant -B -c /etc/wpa_supplicant.conf -i eth1 -D ipw -w -dd

i get more information. This is the output:

[FONT="Courier New"]Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=4):
     33 43 6f 6d                                       3Com
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=31): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='3Com'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
[COLOR="Red"]wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported[/COLOR]
SIOCGIWRANGE: WE(compiled)=18 WE(source)=16 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
Own MAC address: 00:0e:35:67:88:81
[COLOR="Red"]wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
**Failed to set encryption.**
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
**Failed to set encryption.**
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
**Failed to set encryption.**
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
**Failed to set encryption.**
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported[/COLOR]
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=4):
     33 43 6f 6d                                       3Com
Scan timeout - try to get results
Received 271 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:0f:cb:a9:db:b6 ssid='3Com' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected
Trying to associate with 00:0f:cb:a9:db:b6 (SSID='3Com' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
State: SCANNING -> ASSOCIATING
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=17
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
[/FONT]


It seems that the problem is in wpa_supplicant, or in the driver which is not enabled to wpa, or what other....
In fact the driver works well without wpa or wep encryption...

Where is the matter?

I've tried with wpa_supplicant 0.39 and 0.45
ipw2200 v. 1.0.6 and 1.0.7 (firmware 2.3 and 2.4)
ieee80211 1.0.3 and 1.1.4

I really don't know what to think...

Thanks
Marco

---

### Post by luca_linux on 2005-10-08
Annoying issue...
That happened to me a couple of times. I solved it reinstalling the ipw2200 driver. Make sure you delete all previous modules. You could also try to disable hwcrypto.
At most you can try to install ipw2200 1.0.4.

---

### Post by asterix404 on 2005-10-09
okay so I know this thread is heuge but no one has had my problem yet soo here goes. I folowed your instructions step by tiny step and got to the make bit of the ieee80211-1.0.3 and I get the error

"no rule for target 'modules'" stop

which I thought was kidna wierd so I poked around and sure enough there was a make modules: however inside of it it called itself and didn't do much. I don't know what these modules however are supose to mean, can someone help me? Thanks ~BEn

---

### Post by luca_linux on 2005-10-09
Have you installed kernel-headers?

---

### Post by Psquared on 2005-10-09
Is is the consensus that ipw2200 ver 1.0.4 is the most stable? The most recent release is now 1.0.8 and I've tried up to 1.0.6 and still find it to be flaky with my Toshiba laptop's built-in Intel Pro Wireless adapter.

I'm happy to go back to to 1.0.4 if its the most stable.

---

### Post by luca_linux on 2005-10-09
1.0.4 is the last version which includes the ieee80211 subsystem too and so there could be fewer issues.

---

### Post by asterix404 on 2005-10-09
Okay, this is the wierdest thing, it worked after I rebooted my comp. I had everything that I did before and didn't change a thing and now I restarted and bam...

I noticed though that you have your ssid and I am a total nube when it comes to anything wireless since I prefer wired. I have my laptop at school and really don't know what my ssid name is. There are also multiple access points that I can be useing esp if I move around. Could you tell me how to set somthing like that up? It would really help me a lot, Thanks ~Ben

---

### Post by luca_linux on 2005-10-09
It depends on how the net is set up. Anyway, if the ssid is broadcast, you can try to scan the area and see the ssid found. Otherwise, if the ssid is not broadcast, you have to ask you school for it.
As far as the multiple access points, you could set up several network profiles with different gateway IPs.

---

### Post by bryan986 on 2005-10-11
Likely if there are multiple access points at your school, they will all have the same SSID, just use "iwlist eth1 scan" (where eth1 is your wireless device) to get a list of access points

---

### Post by Chris Braendle on 2005-10-11
:p :p  Thank you very much - it works!

---

### Post by marstell on 2005-10-12
Hi..

I have just come back to kernel 2.6.11-1.1369_FC4 and now wpa works ok...
Probably there is a problem with kernel 2.6.13.* or the new versions of the ipw drivers...

With kernel 2.6.11-1.1369_FC4 I have followed the luca_linux's how-to instructions and all works well.

Thanks luca_linus for the how-to!

---

### Post by jwolf on 2005-10-14
I am having a little trouble with the configuration side of this. 
The contents of /etc/wpa_supplicant.conf:
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="alchemy"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk="sekretpassword"
}

```
The ouput from running:
jwolf@hydrogen:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd
```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=7):
     61 6c 63 68 65 6d 79                              alchemy
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=28): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='alchemy'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:0e:35:27:78:28
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Daemonize..

```

---

### Post by frobroj on 2005-10-15
OK I am a TOTAL NEWB!!! And of course I come begging for help. I have a Sabio Digital Whitebook with Breezy installed. First thing I have started working on is the wireless. It has the adaper and Identifies it correctly as a Intel Pro Wireless 2200B/G. I can set the SSID and the Wep Key but it doesnt pull dhcp and it doesnt seem to activate. When activating it takes a while and then says active. 
Does anyone have any tips for testing general connectivity? I have tried hard setting it and still cant ping the gateway. Just wondering what I might be looking for in the config and on the machine that might indicate the adapter is functioning. Note Its only worked with with Linspire which I am assuming uses NDIS Wrappers. 
Note on my previous install I tried the above upgrades and when it came to the make it failed on me. So any tips or trick to test the device would be greatly appreciated.

Thanks All!
Fro

---

### Post by Sianis on 2005-10-15
[QUOTE=luca_linux]Hi!
I've seen there are many requests about how to get ipw2200 and wpa to work. So, as I've managed to get them to work, I've decided to write a howto. It's also good if you just want to get ipw2200 without wpa; just follow the first part in this case.[/QUOTE]

I followed your instruction, but not works for me! :( 


Here is My MS XP setup and my Router setup:

[MS Wireless]("http://kepfeltoltes.hu/051015/ms_wpa.JPG")
[Router]("http://kepfeltoltes.hu/051015/router_wireless.JPG")

What's wrong or not wrote down in the #1? 

What do I have to change in the /etc/wpa_supplicant.conf, or in the Networks settings, or upload pictures from this setups?

I'm not newbie, but i cannot setup this now...

Thanks....Sianis

---

### Post by Sianis on 2005-10-15
Hi!

I read some manual, and it's workink now!

Here is my /etc/wpa_supplicant.conf file:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="Router"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        psk="secure key"
}

```

And for the fast boot I commented the eth0 in the /etc/network/interfaces...:

```


iface eth0 inet dhcp

#auto eth0

iface eth1 inet dhcp

auto eth1

```

And 1 thing also! The System -> Administration -> Network; I setting eth1 DHCP and activated...this feature give IP address from router every boot.

That's all! Thanks the first post, it' helping me finaly.

---

### Post by Psquared on 2005-10-16
I'm having problems with ipw2200 as well. For awhile it would not detect the firmware so it didn't see my Intel Pro Wireless adapter at all. I reinstalled ipw2200, firmware and ieee80211 and now it barfs on the "make" command. I followed the steps by coping the firmware first and then trying to compile ieee80211 .... here is the output I get.

>  peyre@PTL-Mobile:~/Desktop/Downloads/ieee80211-1.0.3 $ make
Checking in /lib/modules/2.6.12-9-686/build/ for ieee80211 components...

CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT=m
CONFIG_IEEE80211_WPA=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
Above definitions found. Comment out? [y], n y
sed: can't read /lib/modules/2.6.12-9-686/build//build/.config: No such file or directory
make -C /lib/modules/2.6.12-9-686/build M=/home/peyre/Desktop/Downloads/ieee80211-1.0.3 MODVERDIR=/home/peyre/Desktop/Downloads/ieee80211-1.0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
Building modules, stage 2.
MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
peyre@PTL-Mobile:~/Desktop/Downloads/ieee80211-1.0.3 $

Anybody got any ideas. I tried uninstalling build-essential and then reinstalling it but that didn't work. I have the kernel-headers installed so I can't figure out why it won't compile.

Maybe I should compile from source??

Anyone care to walk me through that? ;)

---

### Post by rgould on 2005-10-17
My issue with my network is that it takes approximately five minutes to restart networking (this includes while booting!).

More specifically, issuing the following command takes a ridiculously long time:
```
sudo rmmod ipw2200; sudo modprobe ipw2200; sudo /etc/init.d/networking restart
```

Once a wireless connection has been established, everything is okay and it is stable. If I boot up the machine with the exterior wireless switch off, I have to restart networking before it will activate. 

How can I tell what is causing networking to take so long to restart?

Note: I am not using WPA.

Thanks

---

### Post by ZaphodX on 2005-10-17
I have spent a lot of time to get WPA working on Breezy. Since I brew my own Kernel 2.6.13.2, I was not able to use WPA at first.

The ipw2200-1.0.6 does not support wpa_supplicant with Wireless-Extensions version > 17 anymore, instead it has built in support for new and different function calls. Older kernels with Wireless-Extensions < V18 should work as expected.
Kernel 2.6.13.* uses Version 18, so trying to use wpa_supplicant, it will e.g. complain that it cannot perfom IPW_IOCTL_WPA_SUPPLICANT.

I think that this will be solved in the future, when newer versions of the wireless-tools support the new wireless extensions' WPA function calls. Wpa-supplicant will be obselete then.

Because I did not want to wait until the new wireless-tools are available, but also did not want to step back to older kernels, I patched the IPW200-1.0.6 sources to support wpa_supplicant with all version of the Wireless-Extensions.

If you also ran into the troubles, I ran into, feel free to use [this patch]("http://www.schnackelchen.de/ipw2200.patch").
Beware: This is extremely experimental. It works for me and I have only tested it with kernel 2.6.13.2. I expect it to work with all 2.6.13.* kernels, but do not guarantee anything, since I consider this a really dirty hack :)

The patch also contains the changes needed to allow the ipw2200 to do dhcp.

To apply the patch, just copy it into the directory, where your ipw2000-1.0.6 sources reside and do a "patch < ipw2200.path", do a "make" and "make install" and follow the excellent howto at the beginning of this thread.

Have fun :)

Carsten

---

### Post by ZaphodX on 2005-10-17
> **rgould]My issue with my network is that it takes approximately five minutes to restart networking (this includes while booting!).

More specifically, issuing the following command takes a ridiculously long time:
```
sudo rmmod ipw2200 said:**
> 

Since you wrote, that you do not use WPA, your question is not related to the thread's topic, but I will try to help you anyway :)

First of all, do you only use the wireless interface? How does your */etc/network/interfaces* look like?

I assume, you're using DHCP and your wireless interface is eth1. So these two lines should be in you *interfaces*:
[I]auto eth1
iface eth1 inet dhcp
[/I]
Right?

Now, I suspect that it is not the *rmmod ipw2200 && modprobe ipw2200* part that's causing your troubles, ok?

To see what happens, when your interfaces come up, simply type
*sudo ifdown -a* following
*sudo ifup -a*

You will get a more verbose output of what is going on. With this output it may be possible to see at which step the delay is occuring.

*----
Carsten


[QUOTE=rgould]
Once a wireless connection has been established, everything is okay and it is stable. If I boot up the machine with the exterior wireless switch off, I have to restart networking before it will activate. 

How can I tell what is causing networking to take so long to restart?

Note: I am not using WPA.

Thanks

---

### Post by rgould on 2005-10-17
[QUOTE=ZaphodX]Since you wrote, that you do not use WPA, your question is not related to the thread's topic, but I will try to help you anyway :)[/QUOTE]
Oops! Perhaps there should be a separate HOWTO for non-wpa ipw2200 usage?

> First of all, do you only use the wireless interface? How does your */etc/network/interfaces* look like?
This looks alright - those lines are present (Except wireless is eth0). 

> Now, I suspect that it is not the *rmmod ipw2200 && modprobe ipw2200* part that's causing your troubles, ok?
It wasn't at first. Let me explain:
Started up system, eth1 (LAN) not plugged in, eth0 (wireless) external switch on. Network started up okay, but slow as usual. Performed ifdown -a and then ifup -a. Noted that the delay is spent while eth1 was doing DHCPDISCOVERY. Eth0's attempts were speedy.
Plugged in eth1 and tried to do rmmod ipw2200 and everything locked up. Couldn't kill the process and the console was receiving a message along the lines of "unregister_netdevice: waiting for eth0 to be come free. Usage count = 1". Had to do a soft reboot. (I typed this all up and couldn't save it.. oops)

I also tried doing ifdown/ifup with wireless switched off, and it took twice as long (while eth0 performed DHCPDISCOVERY).

So I guess I have two questions:
How do I speed up DHCPDISCOVERY (or reduce the timeout)?

How do I free eth0 while doing rmmod ipw2200 so my system doesn't freeze? 

Vielen Dank,

Richard

---

### Post by bryan986 on 2005-10-18
I would like to note that in 5.10 Breezy, all I had to do was install wpasupplicant and configure wpa_supplicant conf, nothing else...it just worked

---

### Post by Cyril on 2005-10-18
I don't know if somewhere in these 44 pages someone already mentioned this but, if you are going to follow the instructions at the start of this thread, you want to make sure you have gcc3.4 installed.  Otherwise you won't be able to run make successfully and will be stuck without an internet connection.

---

### Post by mr_crimp on 2005-10-23
I've just installed Breezy and followed this very nice guide from the wpa supplicant part and to the end. After completing the guide I've rebooted my laptop. It went very smooth and fast. The "wireless radio" light got turned on under the booting. But I couldn't get any connection to the Internet even that the "wireless radio" light still was turned on. I clicked the little “Network Connection” icon at the top panel and chose Configuring. My wireless card was not activated so I clicked "Activate" and only filled out the  SSID field, not the password field because it only works for WEP. Afterwards I clicked “OK”. It took about 3 min. to activate the card and then I rebooted my laptop again. This time it got stock at the "Configuring Network Interfaces" part for about 2 - 3 min. and then it went on. Now wpa works but it is very frustrating that it takes over 3 min. to boot my laptop every time. 

My Hardware:
IBM T42, Intel PRO2200 B/G

I hope someone can help me with this mysterious problem.

---

### Post by mr_crimp on 2005-10-24
I have now made a clean reinstall of Breezy because my problem was very frustrating. I havn't installed wpa supplicant jet. But when I choose "Network Tools" (Applications -> System Tools -> Network Tools) I can't find my wireless network card (eth1) under Devices -> Network devices. There is only my Ethernet Card(eth0) and a "Loopback Interface(lo)".

Can this have something to do with my problem? And why is my wireless network card not there?

---

### Post by javaguru on 2005-10-25
Nice .. this worked for a while .. now i'm running kernel 2.6.13 and ipw2200 1.0.7 (debian unstable package) and i'm trying to get it to work with WPA2 and TKIP/AES. 
I already checked out the tutorial with the wpa_helper package, it doesn't work. The module loads, i can scan the AP, but i can't connect. I saw that someone used "proto=RSN" in wpa_supplicant.conf but it doesn't work either. 
any suggestions ?

---

### Post by ZaphodX on 2005-10-27
[QUOTE=javaguru] .. now i'm running kernel 2.6.13 and ipw2200 1.0.7 (debian unstable package) and i'm trying to get it to work with WPA2 and TKIP/AES. 
[/QUOTE]

As I wrote before in this thread, the IPW2200 driver > 1.0.4 does not work together with the recent wpa_supplicant implementation AND kernel 2.6.13.*. Either you use this [patch]("http://www.schnackelchen.de/ipw2200.patch") together with the ipw2200 driver v 1.0.6 or you wait until the new wireless tools support the new driver semantics.
Or you have to live with the kernel that comes along with the Breezy installation.

Carsten

---

### Post by ZaphodX on 2005-10-27
[QUOTE=rgould]
I also tried doing ifdown/ifup with wireless switched off, and it took twice as long (while eth0 performed DHCPDISCOVERY).

So I guess I have two questions:
How do I speed up DHCPDISCOVERY (or reduce the timeout)?

How do I free eth0 while doing rmmod ipw2200 so my system doesn't freeze? [/QUOTE]

I'm afraid, I can't help you with the freezitng of your machine while trying to remove the ipw2200 module. Have a look into /var/log/kern.log, perhaps there's something that might help identifying your problem. Did you do a "ifdown -a" or a "ifdown eth0" before you tried to remove the module?

For the DHCPDISCOVERY timeout I have two suggestions:
1. Turn off dhcp for eth0/eth1 during bootup (remove the line "auto ethx" from /etc/network/interfaces), depending on which interface you use preferably.
2. Change your dhcp configuration. I'm using the package dhcp3-client. In /etc/dhcp3/dhclient.conf there's a line "#timeout 60". 
I changed it to "timeout 10" (remove the '#'!) and apparently the DHCP requests time out much faster on my machine.

Have fun
Carsten

---

### Post by mcleanr on 2005-10-28
Guys, I am a total newb at linux so please bare with me on this.  I'm hoping the answer might be simple to someone, as I am having trouble at the point in the instruction where I install the ieee80211 subsystem.  This is what I get from the console.

root@ubuntu:~/Desktop/subsystem/ieee80211-1.0.3# make
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

/lib/modules/2.6.12-9-386/build/include/config/ieee80211

Above files found.  Remove? [y],n  y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1



It doesn't matter if I say y or n it still errors out.  Then I try Make Install and this is what I get.

  root@ubuntu:~/Desktop/subsystem/ieee80211-1.0.3# make install
make -C /lib/modules/2.6.12-9-386/build M=/root/Desktop/subsystem/ieee80211-1.0.3 MODVERDIR=/root/Desktop/subsystem/ieee80211-1.0.3 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /root/Desktop/subsystem/ieee80211-1.0.3/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/root/Desktop/subsystem/ieee80211-1.0.3/ieee80211_module.o] Error 127
make[1]: *** [_module_/root/Desktop/subsystem/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2



Any help would be GREATLY appreciated!

Thanks,
Ryan

---

### Post by mcleanr on 2005-10-28
Just an update, however not much progress. 

I finally deleted the directory references it was finding, manually.  Using rm -r

Then I ran Make again and I get this.

root@ubuntu:~/Desktop/subsystem/ieee80211-1.0.3# make
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-9-386/build M=/root/Desktop/subsystem/ieee80211-1.0.3 MODVERDIR=/root/Desktop/subsystem/ieee80211-1.0.3 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /root/Desktop/subsystem/ieee80211-1.0.3/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/root/Desktop/subsystem/ieee80211-1.0.3/ieee80211_module.o] Error 127
make[1]: *** [_module_/root/Desktop/subsystem/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2


I'm seeing alot of reference to "gcc-3.4: Command not found", is there a problem with my GCC compiler perhaps?  I did what luca_linux said in the beginning in terms of "sudo apt-get install gcc".  

This is what I get when I execute that line, indicating that everything supposedly seems okay and that I have it.

root@ubuntu:~/Desktop/subsystem/ieee80211-1.0.3# sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I would really appreciate any help I can get.  Thanks so much.

Ryan

---

### Post by ZaphodX on 2005-10-28
Just a shot into the sky:

try: apt-get install gcc-3.4
Try to 'make' again and post your error messages.

Currently I do not have the ieee80211 sources on my machine, so I cannot dig deeper into your problem.

Carsten

---

### Post by mcleanr on 2005-10-28
Perfect, that helped out emensly.  I am much further.  Now what I have run into in following the instruction is the wpasupplicant part, i get the following:

root@ubuntu:~/Desktop/driver/ipw2200-1.0.6# sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wpasupplicant


Any ideas?  As well, do I even need WPA if I'm only using WEP?

---

### Post by zdavidlnx on 2005-10-28
[QUOTE=mcleanr]Perfect, that helped out emensly.  I am much further.  Now what I have run into in following the instruction is the wpasupplicant part, i get the following:

root@ubuntu:~/Desktop/driver/ipw2200-1.0.6# sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wpasupplicant


Any ideas?  As well, do I even need WPA if I'm only using WEP?[/QUOTE]

If you only use WEP you don't need wpa_supplicant, you just need to configure your network connection(wifi one) with your WEP password. No need for wpa_supplicant in your case.

---

### Post by mcleanr on 2005-10-28
Thank you.

However I updated with the repositories and was able to install wpasupplicant.  After reading through I realized the same thing as you indicated that I wouldn't require it.  Does it matter that I installed it?  If so how do I go about removing it.

So everything is apparently loaded, the driver, firmware and ieee80211 subsystem.  I still can't get online wirelessly.  When I execute 

dmesg | grep ipw

I get the following.
root@ubuntu:/usr/lib/hotplug/firmware# dmesg | grep ipw
[4294699.812000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294699.812000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294699.816000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[4294700.370000] ipw2200: Radio Frequency Kill Switch is On:
[4294703.553000] ipw2200: failed to send WEP_KEY command

Also - when in network settings from System settings, my wifi card shows up as eth1.  I can't get it to enable.  I click enable and it attempts and immediately goes back to disabled.  I have tried disabling my eth0 and rebooting, but still the same problem.  Is there some conf file or something I need to edit to get this working and initialized?  

Thanks again for everyones help.

---

### Post by mcleanr on 2005-10-28
Just some more information in case it helps, this is what I get from iwconfig

eth1      radio off  ESSID:"Rynet"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:2A2A-2A2A-2A2A-2A2A-2A2A-0000-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by mcleanr on 2005-10-29
Okay, got my radio on I had to do an Fn F2 on the keyboard.  So everything appears good, I am able to scan networks and it appears to be functioning, however I am unable to use the internet.

---

### Post by mcleanr on 2005-10-29
I FINALLY FIGURED IT OUT BOYS!!!  WOO HOO LOL

That was a serious mission!

In the end after turning on my wireless radios, all I needed to do was add my WEP key explicitly in  /etc/network/interfaces

iface eth1 inet dhcp 
 wireless-essid MYSSID 
 wireless-key MYWEPKEY

Thanks to everyone who tried to help out with this issue!  And thanks to the writer of the original post with a great explanation on the installation process.

---

### Post by ZaphodX on 2005-10-29
So, now that you found out how to enable your wlan interface and to use it with WEP encryption you should try to go one step further and enable WPA encryption, since it is much more secure.

Good luck :)

---

### Post by smd on 2005-11-01
Thanks Luca Linux............:)

as I am new to linux, I tried Ubuntu 5.10 on IBM R52 Laptop
I was facing same problem but this tutorial solved my problem :)

But I have facing new problem now...:(
Previously on OLD driver I was getting 2-4mBps speed for data trasfer 
but now I am getting 0.5 to 1 mBps with this new driver ...

DO i need to do any additional settings or I missed any setting ?

Thanks

---

### Post by elfandereth on 2005-11-01
Hi. I have just installed ubunto 5.10, and i'm newbie in linux.

For two days i have been fighting against my laptop (fujitsu-siemens amiilo 1425) following the how to. All is fine until I have to execute *make* in the ieee80211-1.1.6 directory.

I have the following messages:

[I]Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-9-386/build M=/home/jandrey/ieee80211-1.1.6 MODVERDIR=/home/jandrey/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: No se encontr&#243; el programa
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/jandrey/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/jandrey/ieee80211-1.1.6/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/jandrey/ieee80211-1.1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2
[/I]

I have read twice the whole thread and i couldn't find any problem like mine. I have download delates version of ipw driver 1.0.8 and 802.11 subsystem 1.1.6

thanks for helping me

---

### Post by ZaphodX on 2005-11-01
A few messages below I posted this answer:

[QUOTE=ZaphodX]Just a shot into the sky:

try: apt-get install gcc-3.4
Try to 'make' again and post your error messages.
[/QUOTE]

Good luck!
Carsten

---

### Post by Magneto on 2005-11-01
im using breezy and previously was fine with wpa working great in hoary but now   everytime I attempt to send data like request a webpage or access a mounted network drive etc the wireless connection is lost then reconnects
anyone else see this?

I found it mentioned by some other people as an ipw2200  firmware bug

---

### Post by Magneto on 2005-11-01
[QUOTE=Magneto]im using breezy and previously was fine with wpa working great in hoary but now   everytime I attempt to send data like request a webpage or access a mounted network drive etc the wireless connection is lost then reconnects
anyone else see this?

I found it mentioned by some other people as an ipw2200  firmware bug[/QUOTE]

found the answer

the crypto support in the driver causes this disconnect on transmit and disconnects every so often - to disable the hardware crypto
create a file in /etc/modprobe.d/   I made one called ipw2200 and add this line to it

options ipw2200 hwcrypto=0



sorry if this is a repost

---

### Post by ZaphodX on 2005-11-01
[QUOTE=Magneto]found the answer

the crypto support in the driver causes this disconnect on transmit and disconnects every so often - to disable the hardware crypto
create a file in /etc/modprobe.d/   I made one called ipw2200 and add this line to it

options ipw2200 hwcrypto=0
[/QUOTE]

Hi!

Just get this straight:

Which version of the ipw2200 driver do you use?

I switched to ipw2200-1.0.8 and removed the line mentioned above from /etc/modprobe.d/ipw2200.
I did not experience any problems so far (using WPA, did not test with WEP). So I think that this issue is closed in the current driver.

Cheers
Carsten

---

### Post by OKK77 on 2005-11-01
[[IMG]http://img120.imageshack.us/img120/3442/wirelessconnection2mg.th.png[/IMG]](http://img120.imageshack.us/my.php?image=wirelessconnection2mg.png)

This is what I've managed to do so far after the upgrade to Breezy.  It seems like, I gotta wait. |=

---

### Post by Magneto on 2005-11-02
[QUOTE=ZaphodX]Hi!

Just get this straight:

Which version of the ipw2200 driver do you use?

I switched to ipw2200-1.0.8 and removed the line mentioned above from /etc/modprobe.d/ipw2200.
I did not experience any problems so far (using WPA, did not test with WEP). So I think that this issue is closed in the current driver.

Cheers
Carsten[/QUOTE]

although i added gcc-3.4 trying to build 1.0.8 keeps shooting me errors so that is not gonna be an option for me now

---

### Post by alexdfe on 2005-11-02
hi luca_linux, i used your fine script and it works great with my wpa network at home. but now when i am at the university we have an open access point wlan. problem: i have to disable wpa_supplicant config file to use the wireless network there. is there an easier way to use all types of networks (wep, open, wpa) at the same time?
greetz
alex

---

### Post by sporto on 2005-11-05
Hi,

thanks for the guide.

i am trying with ieee80211-1.1.6 , ipw2200-1.0.8, and ipw2200-fw-2.4.

I successfully get this with dmesg:
[4296316.590000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.8
[4296316.590000] ipw2200: Copyright(c) 2003-2005 Intel Corporation

when I run sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd

i get:

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=14):
     62 69 6c 6c 79 20 61 6e 64 20 62 65 61 72         billy and bear
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='billy and bear'
Daemonize..


and dmesg shows:

[4296316.590000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.8
[4296316.590000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4296316.594000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection[4296316.930000] ipw2200: Can't set TKIP countermeasures: crypt not set!
[4296324.669000] ipw2200: Can't set TKIP countermeasures: crypt not set!
[4296324.670000] ipw2200: Can't set TKIP countermeasures: crypt not set!


can someone help me with the problem?

many thanks.

---

### Post by digumo on 2005-11-06
After fighting with my Breezy install for the past few hours I found an issue that might be something someone else is having. I am working with the following updates

ieee80211-1.1.6
ipw2200-1.0.8
ipw2200-fw-2.4.tgz

All of the latest packages as of this posting.

In my situtation, after having just updated from 5.04 (Hoary Hedgehog) it looks like there were some changes to some of the file locations. I had unloaded ipw and it's associated dependancies on ieee80211 using the unload script in the ipw directory.

```
sh unload
```
When you're in the ipw2200-1.x.x directory

You can check that neither ipw or ieee80211 is running by using

```
lsmod | grep ipw
```

You can then run your "make; make install" per the instructions on the first page. Compiling ieee80211 first is best.

When running modprobe ieee80211 you might get success like I did. The problem is you may be loading an older driver. Untill I did a date check, it looks like the  make install puts the ieee80211 files into /lib/modules/2.6.12-9-386/net/ieee80211 and does not overwrite the files in /lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ieee80211/ which is where they are loaded from.

Notice the dates on the files...

**NEWER FILES WERE ADDED HERE**

```
# ls /lib/modules/2.6.12-9-386/net/ieee80211
total 968K
drwxr-xr-x  3 root root 4.0K Nov  5 21:42 .
drwxr-xr-x  3 root root 4.0K Nov  5 17:05 ..
drwxr-xr-x  2 root root 4.0K Nov  5 21:42 .tmp_versions
-rw-r--r--  1 root root 575K Nov  5 21:42 ieee80211.ko
-rw-r--r--  1 root root  91K Nov  5 21:42 ieee80211_crypt.ko
-rw-r--r--  1 root root  87K Nov  5 21:42 ieee80211_crypt_ccmp.ko
-rw-r--r--  1 root root  95K Nov  5 21:42 ieee80211_crypt_tkip.ko
-rw-r--r--  1 root root  82K Nov  5 21:42 ieee80211_crypt_wep.ko
```

**THEY SHOULD HAVE BEEN HERE**

```
# ls /lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ieee80211/
total 80K
drwxr-xr-x   2 root root 4.0K Nov  5 15:25 .
drwxr-xr-x  13 root root 4.0K Nov  5 21:51 ..
-rw-r--r--   1 root root  31K Oct 10 06:16 ieee80211.ko
-rw-r--r--   1 root root 7.8K Oct 10 06:16 ieee80211_crypt.ko
-rw-r--r--   1 root root 8.3K Oct 10 06:16 ieee80211_crypt_ccmp.ko
-rw-r--r--   1 root root  12K Oct 10 06:16 ieee80211_crypt_tkip.ko
-rw-r--r--   1 root root 6.4K Oct 10 06:16 ieee80211_crypt_wep.ko
```

If your dmesg output shows you anything like like this.

```
ipw2200: disagrees about version of symbol ieee80211*....
```

Then it means your ipw2200 is newer and does not like your ieee80211 - probably because it's older and doesn't include the newer stuff required. Which was my case. As soon as I did a

```
cp /lib/modules/2.6.12-9-386/net/ieee80211/ieee80211* /lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ieee80211/
```

I got a successful load of both ieee80211 and ipw2200 with modprobe and therefore no more problems.



Oh, and if your connection keeps dropping after all this work make sure and run the following

```
ps aux | grep wpa
```

And make sure you don't have two wpa_supplicant processes running. I had rebooted and forgot to kill my startup of wpa_supplicant, so my further testing of running a second one caused the connection to associate then disconnect every few seconds.

I hope this helps someone else out. It took me more than a few hours to get this one solved. Thanks go out to everyone who posted help on this topic. This was my lesson on how modules are loaded in linux. Prior to this I never knew. ;)

---

### Post by digumo on 2005-11-06
Well, it looks like I might have spoken too soon. My interface is connecting to the wireless network but I'm not able to get the DNS working. After unplugging my wired connection and trying the wireless, it connects to the AP but I loose any DNS services.

I tried editing resolv.conf with some fixed IP's but that is getting reset - by dhclient?

Anyone know how to troubleshoot dns issues with wpa_supplicant? Here is my iwconfig output it it helps.

```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"home"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:1234-69D5-5432-7654-EBA3-SDFE-1235-XCFR-8634-BD56-9864-9DCC-GHTY-2C4C-8DBF-4018   Security mode:open
          Power Management:off
          Link Quality=89/100  Signal level=-41 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by ErikTheRed on 2005-11-06
Can I use this guide for Ubuntu 5.10? I'd like to get WPA working, and just wondered if this guide would work okay if I was going to use 5.10 along with the latest ipw2200 drives & firmware.

---

### Post by Sebby on 2005-11-11
Can anyone help? I'm fairly new to Linux, and I'm having some problems. I have followed everything in this guide, but when I try to make in the ieee80211-1.1.6 directory, I get:

```
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-9-386/build M=/home/sebby/ieee80211-1.1.6 MODVERDIR=/home/sebby/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/sebby/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/sebby/ieee80211-1.1.6/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/sebby/ieee80211-1.1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2

```

When I make install:

```
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-9-386/build M=/home/sebby/ieee80211-1.1.6 MODVERDIR=/home/sebby/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/sebby/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/sebby/ieee80211-1.1.6/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/sebby/ieee80211-1.1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2
sebby@ubuntu:~/ieee80211-1.1.6$ make install
make -C /lib/modules/2.6.12-9-386/build M=/home/sebby/ieee80211-1.1.6 MODVERDIR=/home/sebby/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/sebby/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/sebby/ieee80211-1.1.6/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/sebby/ieee80211-1.1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2

```

As I say, I've followed everything, including install gcc, etc.

Any help would be grately appreciated.

---

### Post by sporto on 2005-11-11
try this :)

sudo apt-get install gcc-3.4


this will fix your problem

---

### Post by Sebby on 2005-11-11
[QUOTE=sporto]sudo apt-get install gcc-3.4[/QUOTE]
Thanks, that sorted that problem. :)

After hours of messing around, I've finally got my IPW2200 working with WPA.

When I dmesg | grep ipw2200, I get:

```
[4294706.617000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.8
[4294706.617000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294706.621000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294710.521000] ipw2200: Can't set TKIP countermeasures: crypt not set!

```

As I say, it's all working, but what does "Can't set TKIP countermeasures: crypt not set!" mean?

---

### Post by ilbozo on 2005-11-13
when i try to "make" the downloaded iee80211-1.0.3 gives me some error... What does it mean?

Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

find: /lib/modules/2.6.12-9-386/build/: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//include/linux/autoconf.h: No such file or  directory
make -C /lib/modules/2.6.12-9-386/build M=/home/bozo/Desktop/ieee80211-1.0.3 MOD VERDIR=/home/bozo/Desktop/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
bozo@bozonb:~/Desktop/ieee80211-1.0.3$ sudo make
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

find: /lib/modules/2.6.12-9-386/build/: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//include/linux/autoconf.h: No such file or  directory
make -C /lib/modules/2.6.12-9-386/build M=/home/bozo/Desktop/ieee80211-1.0.3 MOD VERDIR=/home/bozo/Desktop/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

---

### Post by linux_newbie on 2005-11-19
Could you tell me how do I install the kernel source package . I am very new to linux. I am trying to use wpa for my wireless and followed the how to on
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

and this is what I get when I run make for installing the ieee80211 components

Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

find: /lib/modules/2.6.10-5-386/build/: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//.config: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.10-5-386/build M=/home/<myname>/tmp/ieee/ieee80211-1.0.3 MODVERDIR=/home/<myname>/tmp/ieee/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

---

### Post by linux_newbie on 2005-11-19
I am following the steps exactly as given in this howto and this is what I get when I run remove-old scripts

find: /lib/modules/2.6.10-5-386/build: No such file or directory
grep: /lib/modules/2.6.10-5-386/build/.config: No such file or directory
grep: /lib/modules/2.6.10-5-386/build/include/linux/autoconf.h: No such file or directory

Also when I do a make when installed ieee80211 I get 

Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

find: /lib/modules/2.6.10-5-386/build/: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//.config: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.10-5-386/build M=/home/<myname>/tmp/ieee/ieee80211-1.0.3 MODVERDIR=/home/<myname>/tmp/ieee/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory. Stop.
make: *** [modules] Error 2


Could anyone tell me what am I doing wrong or is there something that I am missing. I am pretty new to linux

Thanks

---

### Post by ruffneck on 2005-11-20
I'm not sure if this has been mentioned in the thread before. If it was I apologize and will delete my post if so.

There is a nifty program called "Wifi-radar" that I use to configure ipw2200+wpa and create profiles (ie. home, work etc.)

You can find it in the breezy repos or [http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/)

---

### Post by joters on 2005-11-21
[QUOTE=luca_linux]Hi!
I've seen there are many requests about how to get ipw2200 and wpa to work. So, as I've managed to get them to work, I've decided to write a howto. It's also good if you just want to get ipw2200 without wpa; just follow the first part in this case.

We have to compile and install the latest ipw2200 1.0.6 driver from [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net) and we also have to install the firmware, as the ipw2200 0.19 included in the standard installation of Hoary doesn't support wpa.

Since ipw2200 1.0.5, ipw2200 project does not include ieee80211 subsystem anymore, so we also have to compile and install them from [http://ieee80211.sourceforge.net](http://ieee80211.sourceforge.net).

_Since we have to compile the driver from sources, we need the packages: build-essential, gcc, linux-headers-myOwnKernelVersion._
So:
```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install gcc
sudo apt-get install linux-headers-$(uname -r)

```

Note: if you have the kernel sources installed, you won't need the linux-headers. And if you're running a custom kernel compiled by you, you won't need to install the packages mentioned above.

First of all, follow [these instructions](http://www.ubuntuguide.org/#extrarepositories) to add extra repositories, which are always handy to have.

Here are the steps (for newbies: the following commands are supposed to be typed in the same console session):

First of all, download the firmware from [here](http://ipw2200.sourceforge.net/firmware.php?fid=5).
Then install it:
```

sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/

```
Now download the latest ieee80211 subsystem from [here](http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.0.3.tgz?download).
Then untar it and change your current directory into the driver's one:
```

sudo tar xvzf ieee80211-1.0.3.tgz
cd ieee80211-1.0.3

```
Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted:
```
sudo sh remove-old
```
Now download the latest ipw22000 driver from [here](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.6.tgz?download).
Then untar it and change your current directory into the driver's one:
```

cd ..
sudo tar xvzf ipw2200-1.0.6.tgz
cd ipw2200-1.0.6

```
Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted:
```
sudo sh remove-old
```
Now your system is clean and it's time to make and install ieee80211, so:
```

cd ..
cd ieee80211-1.0.3
make
sudo make install

```
Then make and install ipw2200 as well:
```

cd ..
cd ipw2200-1.0.6
make
sudo make install

```
Note: it seems there's currently a bug of remove-old script on some systems; if you get errors when compiling ieee80211 about the presence of old modules, you'll have to delete them manually, after having unloded all ieee80211* modules through "modprobe -r module_name" (type "lsmod" to see the current loaded modules).


Now we have to download and install the wpa_supplicant package:
```

sudo apt-get install wpasupplicant

```
Then you have to create a wpa_supplicant.conf in /etc, so:
```

sudo gedit /etc/wpa_supplicant.conf

```
And paste the following lines in the text editor:
```

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Anyway there are further configuration examples in /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz.

Then reboot to make sure that the new modules are loaded successfully and type:
```
dmesg | grep ipw
``` 


[COLOR="Red"]
Hi,

at Reboot ...dmesg :

```


root@joters-notebook:~# dmesg | grep ipw
[4294700.462000] ipw2200: disagrees about version of symbol ieee80211_get_crypto _ops
[4294700.462000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4294700.462000] ipw2200: disagrees about version of symbol ieee80211_wx_set_enc ode
[4294700.462000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4294700.462000] ipw2200: disagrees about version of symbol ieee80211_wx_get_enc ode
[4294700.462000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4294700.462000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4294700.462000] ipw2200: Unknown symbol ieee80211_txb_free
[4294700.462000] ipw2200: disagrees about version of symbol ieee80211_crypt_dela yed_deinit
[4294700.462000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4294700.462000] ipw2200: disagrees about version of symbol ieee80211_wx_get_sca n
[4294700.462000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4294700.462000] ipw2200: Unknown symbol escape_essid
[4294700.463000] ipw2200: disagrees about version of symbol ieee80211_rx
[4294700.463000] ipw2200: Unknown symbol ieee80211_rx
[4294700.463000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4294700.463000] ipw2200: Unknown symbol ieee80211_rx_mgt


```

??

Why? sorry my short dialog, i speak spanish :confused: 


[/COLOR]

---

### Post by mathew.chacko on 2005-11-25
I too get the samilar listing, using **dmesg** command. On Ubuntu 5.10 and after installing new drivers/modules ieee80211-1.1.6, ipw2200-1.0.8, and ipw2200-fw-2.4

Thanks in advance.

---

### Post by baix on 2005-11-25
I also get this error messages in dmesg after installing ieee80211-1.1.6 and ipw2200-1.0.8 like it's described in the howto. I hope anyone of the linux gurus here has a suggestion to resolve this problem.

thx

My output is:
[4294686.952000] ieee1394: Initialized config rom entry `ip1394'
[4294705.639000] ieee80211_crypt: registered algorithm 'NULL'
[4294705.868000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4294705.868000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4294705.868000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4294705.868000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4294705.868000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4294705.868000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4294705.868000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4294705.868000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4294705.870000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294705.870000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4294705.968000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4294705.968000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4294705.968000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4294705.968000] ipw2200: Unknown symbol ieee80211_txb_free
[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4294705.968000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4294705.968000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_rx
[4294705.968000] ipw2200: Unknown symbol ieee80211_rx
[4294705.968000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4294705.968000] ipw2200: Unknown symbol ieee80211_rx_mgt

---

### Post by amilist on 2005-11-27
I had some errors like this too:

[4294705.639000] ieee80211_crypt: registered algorithm 'NULL'
[4294705.868000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4294705.868000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4294705.868000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
....

after looking for my kernel-version, I recognized that there was a kernel-update last week (2.6.12.9 to 2.6.12.10).

This update installed a new kernel-image but not the right sources and headers.... and the compiling procedure (make, make install) compiled with the kernel 2.6.12.9-sources which still were installed. Also the "remove-old"-script referred to the old drivers of 2.6.12.9. The result was an updated ipw-driver for 2.6.12.9 but he used the old driver in 2.12.10. 

So I uninstalled everything with 2.6.12.9 and installed sources and headers for 2.6.12.10. After this, i deleted all the obsolete folders in /lib/modules and compiled the driver again. This worked so far and the current driver is loaded :-)


But now  i got the  "Can't set TKIP countermeasures: crypt not set!"-error. Any hints????

Cheers

---

### Post by master$hake on 2005-12-01
Works great on my Dell 6000 can now connect to my schools network with a little variation of this.  Instead of making all these scripts to start wpa I downloaded network selector panel applet so I can choose which network I want to connect to since they all use the same credentials.
Great Job man

---

### Post by newblacknoise on 2005-12-04
hi, i'd just like to say that after much hair-tearing and frustration, i used your HOWTO to get my wireless network up and running, so thank you very much.

extra credit points for making it nice and simple for people like myself (happy linux/ubuntu user for 4 days and counting...)

---

### Post by spier on 2005-12-05
Just tryed this excellent HowTo with the up to date files:

Ubuntu 5.10
ieee80211-1.1.6
ipw2200-1.0.8
ipw2200-fw-2.4

and everything works perfectly after following these advises, addressed in this thread:

[QUOTE=sporto]
sudo apt-get install gcc-3.4

[/QUOTE]

[QUOTE=digumo]
...
When running modprobe ieee80211 you might get success like I did. The problem is you may be loading an older driver. Untill I did a date check, it looks like the  make install puts the ieee80211 files into /lib/modules/2.6.12-9-386/net/ieee80211 and does not overwrite the files in /lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ieee80211/ which is where they are loaded from.
...
Then it means your ipw2200 is newer and does not like your ieee80211 - probably because it's older and doesn't include the newer stuff required. Which was my case. As soon as I did a

```
cp /lib/modules/2.6.12-9-386/net/ieee80211/ieee80211* /lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ieee80211/
```

I got a successful load of both ieee80211 and ipw2200 with modprobe and therefore no more problems.
...
[/QUOTE]

Thank you guys

---

### Post by Darksun on 2005-12-05
This may sound ignorant, but... What do I put in /etc/network/interfaces ?

I've done all of the above, and tried to connect via System->Administraton->Networking

I select the SSID and leave the security part blank, or should I put my WPA key in for the WEP key?

Thanks!:confused:

---

### Post by coderasm on 2005-12-06
Thankyou very much for this how-to Luca, and everyone else who has made other contributions.  Even though Ubuntu is probably the best linux distro out right now,  the wealth of knowledge spread by its users on this forum, makes it all that much better to use.:razz:

---

### Post by coderasm on 2005-12-07
Hello all.  Thanks to Luca and others in this forum I'm now able to connect to ap's with wap protection.  However, I'm no longer able to connect unencrypted ap's.  I'm running a gateway MX3560 laptop, with ubuntu Breazy 5.10 and ipw2200 driver 1.0.6.  I have wpasupplicant set to load when I boot, so my laptop is automatically configured for wpa.  When I tried using the built-in network configuring tool in Ubuntu, I could see the listing of all the potentially connectable ap's.  I chose one which I knew to not be encryted, but the eth1 wireless interface would not configure.  It is as though the wpasupplicant is completely controlling my interface.  Is there a somewhat easy way of switching between wpa and no encryption during the same booted session? Thanks for any help.

---

### Post by n!x on 2005-12-09
I'm getting an error when trying to make the "ieee80211-1.0.3"

The error is:
```
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

/lib/modules/2.6.12-10-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1

```

I have tried to "sudo make check_old" - but still get the same error...

I have followed this guide, but get's the error all the time. Anyone having a suggestion what to do? I have a IBM T43 2668-74G.

---

### Post by royg1234 on 2005-12-10
[QUOTE=n!x]I'm getting an error when trying to make the "ieee80211-1.0.3"

The error is:
```
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

/lib/modules/2.6.12-10-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1

```

I have tried to "sudo make check_old" - but still get the same error...

I have followed this guide, but get's the error all the time. Anyone having a suggestion what to do? I have a IBM T43 2668-74G.[/QUOTE]

You need to open up the root file browser (see [www.ubuntuguide.org)](www.ubuntuguide.org)), and then  go into the directory **/lib/modules/2.6.12-10-386/build/include/config/** and manually delete **ieee80211** and **ipw2200**

---

### Post by royg1234 on 2005-12-10
question:

in /etc/wpa_supplicant.conf, the part that says psk="something", is that something supposed to be the password you set on your router, or some wierd long string that that password represents?

---

### Post by rasmusbp on 2005-12-11
Thanks for all this information. 

I'm a complete newbie here, trying to make the wireless internet working on Ubuntu 5.10 (i've downloaded the ipw2200-1.0.8 drivers). Using this howto, I run into problems already when trying to compile the ieee80211-1.1.6 package

This is what I get from the root-terminal:

> root@ubuntu:/home/rasmus/ieee80211-1.1.6# make
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-10-386/build M=/home/rasmus/ieee80211-1.1.6 MODVERDI R=/home/rasmus/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: c ommand not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: c ommand not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/rasmus/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/rasmus/ieee80211-1.1.6/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/rasmus/ieee80211-1.1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
root@ubuntu:/home/rasmus/ieee80211-1.1.6# sudo make install
make -C /lib/modules/2.6.12-10-386/build M=/home/rasmus/ieee80211-1.1.6 MODVERDI R=/home/rasmus/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: c ommand not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: c ommand not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/rasmus/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/rasmus/ieee80211-1.1.6/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/rasmus/ieee80211-1.1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
 

Aargh, what's going on? From then on, nothing seemed to work. Eventually, when trying to install the ipw2200 drivers, I got the message:
> 
root@ubuntu:/home/rasmus/ipw2200-1.0.8# make

 ERROR: ieee80211.h not found in '/lib/modules/2.6.12-10-386/include'.

 You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
 and point this build to the location where you installed those sources, eg.:

 % make IEEE80211_INC=/usr/src/ieee80211/

 will look for ieee80211.h in /usr/src/ieee80211/net/

I hope someone can help. Cheers!

Rasmus
Copenhagen, Denmark

---

### Post by routerstu on 2005-12-11
i reinstalled breezy and followed the directions here  along with Spier's directions in this post and it does work.  I am using wpa2 currently.  i do have an issue yet though.  when it boots up i dont get an ip, i enter wpa_cli and enter "status" to see i am associated and all looks well.  i then run dhclient but it times out.  i then reenter wpa_cli and disconnect, then reassociate, then run dhclient again and i DO get an ip.   this does work but it obviously not automatic.  thanks to everyone for posting their results.

---

### Post by royg1234 on 2005-12-11
> I'm a complete newbie here, trying to make the wireless internet working on Ubuntu 5.10 (i've downloaded the ipw2200-1.0.8 drivers). Using this howto, I run into problems already when trying to compile the ieee80211-1.1.6 package

you need to make sure you install all the headers and development packages.  go into synaptic and search for "linux 686", or "linux 386" or whatever your cpu is.  and all the gcc stuff too.  I'm not sure exactly what.  I just installed everything that the search found.

---

### Post by rasmusbp on 2005-12-12
thanks  royg. i installed the gcc package, all the headers and 386 development packages i could find (centrino is 386, right?) and then I managed to go through the howto's steps apparantly without problems. 

but but....that's was too easy....after I rebooted the system, my wireless interface has disappeared completely from the network settings menu. i only have the LAN ethernet card and modem left there. i pricked around in different administration programmes, and it seems the card is still "visible" in e.g. system information/device manager. but not working. 

what might have happened?

thanks,

all the best,
rasmus

---

### Post by royg1234 on 2005-12-14
[QUOTE=rasmusbp]thanks  royg. i installed the gcc package, all the headers and 386 development packages i could find (centrino is 386, right?) and then I managed to go through the howto's steps apparantly without problems. 

but but....that's was too easy....after I rebooted the system, my wireless interface has disappeared completely from the network settings menu. i only have the LAN ethernet card and modem left there. i pricked around in different administration programmes, and it seems the card is still "visible" in e.g. system information/device manager. but not working. 

what might have happened?

thanks,

all the best,
rasmus[/QUOTE]

Full disclosure: I'm not very good at this stuff.

The only thing I can think of is to check your cards' names (eth0, eth1, etc.) against the files the howto told you to make.  I know in mine I had to find and replace the ethx to make sure that it matched my wireless cards.  But that's just a guess.

---

### Post by rasmusbp on 2005-12-14
thanks again.

in the end, though, i managed to solve the problem by reinstalling ubuntu (sic) and then - very strictly and in the right sequence - following the steps in this howto, paying special attention to always downloading the newest drivers. 

cheers,
rasmus

---

### Post by njm on 2005-12-21
[QUOTE=Sebby]
```
[4294710.521000] ipw2200: Can't set TKIP countermeasures: crypt not set!

```

As I say, it's all working, but what does "Can't set TKIP countermeasures: crypt not set!" mean?[/QUOTE]

I have the same error & the same question ;) 
At home (WPA-PSK) it works fine. But at university, they use PEAP : success to authenticate with wpa_supplicant but after no response from dhcp server. Does it error can be the source of the problem ?

---

### Post by niggli on 2005-12-25
Thanks for the how-to. I've compiled everything but the wpa-thing. However, now my ipw2200 does not work anymore:

```
falknis ipw2200-1.0.6 $ modprobe ipw2200
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.12-10-386/net/ieee80211/ieee80211_crypt.ko): Invalid module format
WARNING: Error inserting ieee80211 (/lib/modules/2.6.12-10-386/net/ieee80211/ieee80211.ko): Invalid module format
FATAL: Error inserting ipw2200 (/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ipw2200.ko): Invalid module format
```

Does anybody know what the problem could be? I'm using kernel 2.6.12-10, ipw2200-1.0.6 and ieee80211-1.0.3

---

### Post by albertux on 2006-01-01
I have one problem :( 
```

root@h4xb0x:/home/evil/wifi/ieee80211-1.1.6# make
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

make -C /lib/modules/2.6.12-10-386/build M=/home/evil/wifi/ieee80211-1.1.6 MODVERDIR=/home/evil/wifi/ieee80211-1.1.6 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386:/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/evil/wifi/ieee80211-1.1.6/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/evil/wifi/ieee80211-1.1.6/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/evil/wifi/ieee80211-1.1.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
root@h4xb0x:/home/evil/wifi/ieee80211-1.1.6#
```

---

### Post by Maggot on 2006-01-01
[QUOTE=Magneto]found the answer

the crypto support in the driver causes this disconnect on transmit and disconnects every so often - to disable the hardware crypto
create a file in /etc/modprobe.d/   I made one called ipw2200 and add this line to it

options ipw2200 hwcrypto=0
sorry if this is a repost[/QUOTE]
This made mine work after having trouble. Aside from that I followed the guide.

---

### Post by zasf on 2006-01-09
Hi, my wireless card has been working since breezy install with no hassle for me.

I first of all would like to know wich version of ipw2200 i have installed, how can i know it? "lsmod | grep ipw2200" tells me that the module is loaded but which version?

Second, i'm compiling my own kernel, they say i have to uninstall the current version of ipw2200 before installing a new one, does it also apply if you compile a different kernel? Aren't modules kernel dependents??

Thank you all

---

### Post by bennettg on 2006-01-09
> **luca_linux]Hi!
I've seen there are many requests about how to get ipw2200 and wpa to work. So, as I've managed to get them to work, I've decided to write a howto. It's also good if you just want to get ipw2200 without wpa said:**
> http://ipw2200.sourceforge.net[/url] and we also have to install the firmware, as the ipw2200 0.19 included in the standard installation of Hoary doesn't support wpa.

Since ipw2200 1.0.5, ipw2200 project does not include ieee80211 subsystem anymore, so we also have to compile and install them from [http://ieee80211.sourceforge.net](http://ieee80211.sourceforge.net).

_Since we have to compile the driver from sources, we need the packages: build-essential, gcc, linux-headers-myOwnKernelVersion._
So:
```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install gcc
sudo apt-get install linux-headers-$(uname -r)

```

Note: if you have the kernel sources installed, you won't need the linux-headers. And if you're running a custom kernel compiled by you, you won't need to install the packages mentioned above.

First of all, follow [these instructions](http://www.ubuntuguide.org/#extrarepositories) to add extra repositories, which are always handy to have.

Here are the steps (for newbies: the following commands are supposed to be typed in the same console session):

First of all, download the firmware from [here](http://ipw2200.sourceforge.net/firmware.php?fid=5).
Then install it:
```

sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/

```
Now download the latest ieee80211 subsystem from [here](http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.0.3.tgz?download).
Then untar it and change your current directory into the driver's one:
```

sudo tar xvzf ieee80211-1.0.3.tgz
cd ieee80211-1.0.3

```
Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted:
```
sudo sh remove-old
```
Now download the latest ipw22000 driver from [here](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.6.tgz?download).
Then untar it and change your current directory into the driver's one:
```

cd ..
sudo tar xvzf ipw2200-1.0.6.tgz
cd ipw2200-1.0.6

```
Now run the remove-old.sh script that comes with the driver package in order to make sure that any old module is deleted:
```
sudo sh remove-old
```
Now your system is clean and it's time to make and install ieee80211, so:
```

cd ..
cd ieee80211-1.0.3
make
sudo make install

```
Then make and install ipw2200 as well:
```

cd ..
cd ipw2200-1.0.6
make
sudo make install

```
Note: it seems there's currently a bug of remove-old script on some systems; if you get errors when compiling ieee80211 about the presence of old modules, you'll have to delete them manually, after having unloded all ieee80211* modules through "modprobe -r module_name" (type "lsmod" to see the current loaded modules).


Now we have to download and install the wpa_supplicant package:
```

sudo apt-get install wpasupplicant

```
Then you have to create a wpa_supplicant.conf in /etc, so:
```

sudo gedit /etc/wpa_supplicant.conf

```
And paste the following lines in the text editor:
```

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Anyway there are further configuration examples in /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz.

Then reboot to make sure that the new modules are loaded successfully and type:
```
dmesg | grep ipw
``` 
to see if there are errors.
Then type the following command to configurate wpa_supplicant:
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
```
Note: "eth1" is your wireless device.
If you get troubles establishing the connection with the AP, try to take the "-w" flag out.

Some systems may have problems in finding the AP; so, if you get troubles finding your AP, add the "ap_scan=2" option to let wpa_supplicant performing the scan instead of the wireless card driver. So your /etc/wpa_supplicant.conf will look like the following:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Some systems may have problems in connecting to the AP; if you get this issue, try to add the directive "pairwise=TKIP" in the relative network section of /etc/wpa_supplicant.conf, so that it looks like this:
```

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="your_secret_key"
}

```
Of course, if you have problems both findind the AP and connecting to it, you have to add both "ap_scan=2" and "pairwise=TKIP", like the following:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="your_secret_key"
}

```

Now we have to create a small script (first provided by fulco and edited by me) in order to get wpa starting automatically at boot:
```

sudo gedit /etc/init.d/wifi_wpa.sh

```
Here's the script:
```

#! /bin/sh
# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/sbin/wpa_supplicant ]; then
    /usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w
fi

exit 0

```
Change the script's permissions to allow it to be executed:
```

sudo chmod +x /etc/init.d/wifi_wpa.sh

```
And create a symlink to define the relative service:
```

sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/S40netwifiwpa

```

Ok, that's all!
I hope this howto will be helpful.


thanks for this.   can it be added to the wiki

---

### Post by Stramash on 2006-01-12
Excellent HowTo, TY luca_linux :) GJ!

WPA great running on my Toshiba Qosmio F20.

---

### Post by RickKnight on 2006-01-12
Luca_linux's excelent HOW-TO worked great for me, until I upgraded to Kubuntu-5.10 that is. Wireless broke when I upgraded, and I've spent days trying to get it back. I've finally succeeded. I have wifi working with WPA-TKIP security and a dhcp assigned IP address on Kubuntu-5.10. Here's what to do...

Get the latest ipw2200, firmaware and ieee80211 packages and put them in a new folder. I used /home/share/ipw2200. We'll call this the "base directory"...

[http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.10.tgz?download](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.10.tgz?download)
[http://ipw2200.sourceforge.net/firmware.php?fid=6](http://ipw2200.sourceforge.net/firmware.php?fid=6)
[http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.1.8.tgz?download](http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.1.8.tgz?download)

While you're at it, grab this "no cast" patch
[http://ieee80211.sourceforge.net/patches/ieee80211-1.1.8-nocast.patch](http://ieee80211.sourceforge.net/patches/ieee80211-1.1.8-nocast.patch)

Also get wpa_supplicant source
[http://hostap.epitest.fi/releases/wpa_supplicant-0.4.7.tar.gz](http://hostap.epitest.fi/releases/wpa_supplicant-0.4.7.tar.gz)

OK. extract all of the packages...
```
cd /home/share/ipw2200
tar zxpvf ieee80211-1.1.8.tgz
tar zxpvf ipw2200-1.0.10.tgz
tar zxpvf ipw2200-fw-2.4.tgz

``` Copy the firmware to the porper directory...
```
sudo cp ipw-2.4-fw* /usr/lib/hotplug/firmware
```
Install the ieee80211 modules
```
cd ieee80211-1.1.8
sudo sh remove-old
sudo make install
```
Move on to the ipw2200 module
```
cd ../ipw2200-1.0.10
sudo sh remove-old
sudo make install
```
If you have trouble with 'make' on the ipw2200 module, then you will probably need to apply the "no cast" patch. to do this, cd to the "base directory" and apply the patch...
```
cd /home/share/ipw2200
patch -p0 < ieee80211-1.1.8-nocast.patch
```
If the patch completes successfully, continue with the ipw2200 module install.

After you have successfully installed ieee80211-1.1.8 and ipw2200-1.0.10, move on to install the wpa_supplicant. The first step here is to use Kynaptic to remove the Kubuntu/Debian wpasupplicant.

Go to K Menu ->System ->(Package Manager) Kynaptic.
Enter the password for sudo.
Select Edit ->Find (or Ctrl-F) and search for wpasupplicant.
Right click anywhere on wpasupplicant and check Remove. While you're in Kynaptic ->Find, search for ipw2200 and ieee80211 and check Remove for both of them. CLose the Find dialog and commit the changes, by clicking on the "Commit Changes to the System" icon.

Now, build wpa_supplicant.
```
cd /home/share/ipw2200
tar zxpvf wpa_supplicant-0.4.7.tar.gz
cd wpa_supplicant-0.4.7

```
```

```Copy this code to .config in /home/share/ipw2200/wpa_supplicant-0.4.7/
```
CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_MD5=y
CONFIG_EAP_MSCHAPV2=y
CONFIG_EAP_TLS=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TTLS=y
#CONFIG_EAP_GTC=y
#CONFIG_EAP_OTP=y
#CONFIG_EAP_SIM=y
#CONFIG_EAP_AKA=y
CONFIG_EAP_PSK=y
#CONFIG_EAP_PAX=y
CONFIG_EAP_LEAP=y
CONFIG_WIRELESS_EXTENSION=y
#CONFIG_DRIVER_HOSTAP=y
#CONFIG_DRIVER_HERMES=y
#CONFIG_DRIVER_MADWIFI=y
#CFLAGS += -I../madwifi
#CONFIG_DRIVER_ATMEL=y
CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_NDISWRAPPER=y
#CONFIG_DRIVER_BROADCOM=y
CONFIG_DRIVER_IPW=y
CONFIG_CTRL_IFACE=y

```Enable additional drivers you may need, madwifi for example, by removing the # from the front of that particular line.
```
sudo make
sudo make wpa_gui
sudo cp wpa_supplicant /usr/local/bin
sudo cp wpa_cli /usr/local/bin
sudo cp wpa_gui/wpa_gui /usr/local/bin
```
Set your interface to "Managed Mode"
```
sudo iwconfig eth0 mode managed
```

Now reload the ieee80211 and ipw2200 modules
```
sudo modprobe -r ipw2200
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt

sudo modprobe ipw2200
```
Make certain there are no remnants of the Kubuntu/Debian wpa_supplicant
```
which wpa_supplicant
```The only one you should have is /usr/local/bin/wpa_supplicant. If something els shows up, delete it. 
Now test wpa_supplicant.
```
sudo wpa_supplicant -ieth0 -c/etc/wpa-supplicant.conf -Dipw -w
```You should see something like the following
```
Trying to associate with 00:ff:00:1e:a7:7d (SSID='NetworkEssid' freq=0 MHz)
Associated with 00:ff:00:1e:a7:7d
WPA: Key negotiation completed with 00:ff:00:1e:a7:7d [PTK=TKIP GTK=TKIP]

```
That's it. Just put the "wpa_supplicant" command in a startup script with dhcp ```
#! /bin/sh
# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/local/bin/wpa_supplicant ]; then
 /usr/local/bin/wpa_supplicant -ieth0 -c/etc/wpa_supplicant.conf -Dipw -w &
fi

sleep 2

#use dhcp to request a network address
dhclient eth0

exit 0

```and you're done. 

NOTE. This addition to the excelent HOWTO by Luca_Linux assumes you have been working with ipw2200 and have a wpa_supplicant.conf file in your /etc directory.

If you need further help, post here and I will try to respond. I also have been known to frequent irc channels #ubuntu, #kubuntu and #ipw2100.

Hope this helps someone,

Rick Knight

---

### Post by bennettg on 2006-01-14
Please help this nOOb!!!  (Part 1 of 2)

I followed the How to instructions, substituting the newer versions of drivers and firmware.  I got to the point where it asked me to reboot and then got the following after doing the HOWTO commands:

bennettg@ubuntu:~$ dmesg | grep ipw
[4294701.737000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.2
[4294701.737000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[4294701.742000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
bennettg@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Password:
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
opensc_engine_path='/usr/lib/opensc/engine_opensc.so'
pkcs11_engine_path='/usr/lib/opensc/engine_pkcs11.so'
pkcs11_module_path='/usr/lib/pkcs11/opensc-pkcs11.so'
Line: 327 - start of a new network block
ssid - hexdump_ascii(len=6):
     73 69 6d 70 6c 65                                 simple
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
priority=5 (0x5)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 335 - start of a new network block
ssid - hexdump_ascii(len=11):
     73 65 63 6f 6e 64 20 73 73 69 64                  second ssid
scan_ssid=1 (0x1)
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
priority=2 (0x2)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 343 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
proto: 0x1
key_mgmt: 0x2
pairwise: 0x18
group: 0x1e
PSK - hexdump(len=32): [REMOVED]
priority=2 (0x2)
Line: 355 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
proto: 0x2
key_mgmt: 0x1
pairwise: 0x18
group: 0x18
eap methods - hexdump(len=2): 0d 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
private_key - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     72 76                                             rv
private_key_passwd - hexdump_ascii(len=8): [REMOVED]
priority=1 (0x1)
Line: 372 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 19 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
phase1 - hexdump_ascii(len=11):
     70 65 61 70 6c 61 62 65 6c 3d 31                  peaplabel=1
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2
priority=10 (0xa)
Line: 386 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 15 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
anonymous_identity - hexdump_ascii(len=21):
     61 6e 6f 6e 79 6d 6f 75 73 40 65 78 61 6d 70 6c   anonymous@exampl
     65 2e 63 6f 6d                                    e.com
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
priority=2 (0x2)
Line: 399 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 15 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
anonymous_identity - hexdump_ascii(len=21):
     61 6e 6f 6e 79 6d 6f 75 73 40 65 78 61 6d 70 6c   anonymous@exampl
     65 2e 63 6f 6d                                    e.com
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2
Line: 412 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 15 00
anonymous_identity - hexdump_ascii(len=21):
     61 6e 6f 6e 79 6d 6f 75 73 40 65 78 61 6d 70 6c   anonymous@exampl
     65 2e 63 6f 6d                                    e.com
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
phase2 - hexdump_ascii(len=11):
     61 75 74 68 65 61 70 3d 54 4c 53                  autheap=TLS
ca_cert2 - hexdump_ascii(len=17):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 32 2e 70 65   /etc/cert/ca2.pe
     6d                                                m
client_cert2 - hexdump_ascii(len=17):
     2f 65 74 63 2f 63 65 72 2f 75 73 65 72 2e 70 65   /etc/cer/user.pe
     6d                                                m
private_key2 - hexdump_ascii(len=17):
     2f 65 74 63 2f 63 65 72 2f 75 73 65 72 2e 70 72   /etc/cer/user.pr
     76                                                v
private_key2_passwd - hexdump_ascii(len=8): [REMOVED]
priority=2 (0x2)
Line: 430 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
BSSID - hexdump(len=6): 00 11 22 33 44 55
proto: 0x3
key_mgmt: 0x3
pairwise: 0x10
group: 0x10
PSK - hexdump(len=32): [REMOVED]
Line: 442 - start of a new network block
ssid - hexdump_ascii(len=4):
     00 01 02 03                                       ____
PSK - hexdump(len=32): [REMOVED]
Line: 449 - start of a new network block
ssid - hexdump_ascii(len=12):
     65 61 70 2d 73 69 6d 2d 74 65 73 74               eap-sim-test
key_mgmt: 0x1
Line 452: unknown EAP method 'SIM'
You may need to add support for this EAP method during wpa_supplicant
build time configuration.
See README for more information.
eap methods - hexdump(len=2): 00 00
Line 452: failed to parse eap 'SIM'.
pin - hexdump_ascii(len=4): [REMOVED]
pcsc - hexdump_ascii(len=0):
Line 455: failed to parse network block.
Line: 459 - start of a new network block
ssid - hexdump_ascii(len=12):
     65 61 70 2d 70 73 6b 2d 74 65 73 74               eap-psk-test
key_mgmt: 0x1
eap methods - hexdump(len=2): ff 00
identity - hexdump_ascii(len=12):
     65 61 70 5f 70 73 6b 5f 75 73 65 72               eap_psk_user
eappsk - hexdump_ascii(len=16): [REMOVED]
nai - hexdump_ascii(len=24):
     65 61 70 5f 70 73 6b 5f 75 73 65 72 40 65 78 61   eap_psk_user@exa
     6d 70 6c 65 2e 63 6f 6d                           mple.com
Line: 472 - start of a new network block
ssid - hexdump_ascii(len=7):
     31 78 2d 74 65 73 74                              1x-test
key_mgmt: 0x8
eap methods - hexdump(len=2): 0d 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
private_key - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     72 76                                             rv
private_key_passwd - hexdump_ascii(len=8): [REMOVED]
eapol_flags=3 (0x3)
Line: 486 - start of a new network block
ssid - hexdump_ascii(len=12):
     6c 65 61 70 2d 65 78 61 6d 70 6c 65               leap-example
key_mgmt: 0x8
eap methods - hexdump(len=2): 11 00
identity - hexdump_ascii(len=4):
     75 73 65 72                                       user
password - hexdump_ascii(len=6): [REMOVED]
Line: 495 - start of a new network block
ssid - hexdump_ascii(len=13):
     65 61 70 2d 66 61 73 74 2d 74 65 73 74            eap-fast-test
key_mgmt: 0x1
Line 498: unknown EAP method 'FAST'
You may need to add support for this EAP method during wpa_supplicant
build time configuration.
See README for more information.
eap methods - hexdump(len=2): 00 00
Line 498: failed to parse eap 'FAST'.
anonymous_identity - hexdump_ascii(len=17):
     46 41 53 54 2d 30 30 30 31 30 32 30 33 30 34 30   FAST-00010203040
     35                                                5
identity - hexdump_ascii(len=8):
     75 73 65 72 6e 61 6d 65                           username
password - hexdump_ascii(len=8): [REMOVED]
phase1 - hexdump_ascii(len=19):
     66 61 73 74 5f 70 72 6f 76 69 73 69 6f 6e 69 6e   fast_provisionin
     67 3d 31                                          g=1
pac_file - hexdump_ascii(len=32):
     2f 65 74 63 2f 77 70 61 5f 73 75 70 70 6c 69 63   /etc/wpa_supplic
     61 6e 74 2e 65 61 70 2d 66 61 73 74 2d 70 61 63   ant.eap-fast-pac
Line 504: failed to parse network block.
Line: 507 - start of a new network block
ssid - hexdump_ascii(len=14):
     70 6c 61 69 6e 74 65 78 74 2d 74 65 73 74         plaintext-test
key_mgmt: 0x4
Line: 514 - start of a new network block
ssid - hexdump_ascii(len=15):
     73 74 61 74 69 63 2d 77 65 70 2d 74 65 73 74      static-wep-test
key_mgmt: 0x4
wep_key0 - hexdump(len=5): [REMOVED]
wep_key1 - hexdump(len=5): [REMOVED]
wep_key2 - hexdump(len=13): [REMOVED]
wep_tx_keyidx=0 (0x0)
priority=5 (0x5)
Line: 527 - start of a new network block
ssid - hexdump_ascii(len=16):
     73 74 61 74 69 63 2d 77 65 70 2d 74 65 73 74 32   static-wep-test2
key_mgmt: 0x4
wep_key0 - hexdump(len=5): [REMOVED]
wep_key1 - hexdump(len=5): [REMOVED]
wep_key2 - hexdump(len=13): [REMOVED]
wep_tx_keyidx=0 (0x0)
priority=5 (0x5)
auth_alg: 0x2
Line: 540 - start of a new network block
ssid - hexdump_ascii(len=10):
     74 65 73 74 20 61 64 68 6f 63                     test adhoc
mode=1 (0x1)
proto: 0x1
key_mgmt: 0x10
pairwise: 0x1
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=17): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 552 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
scan_ssid=1 (0x1)
key_mgmt: 0xf
pairwise: 0x18
group: 0x1e
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
eap methods - hexdump(len=4): 15 19 0d 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
private_key - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     72 76                                             rv
private_key_passwd - hexdump_ascii(len=8): [REMOVED]
phase1 - hexdump_ascii(len=11):
     70 65 61 70 6c 61 62 65 6c 3d 30                  peaplabel=0
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 570 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 0d 00
proto: 0x2
pairwise: 0x18
group: 0x18
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
engine=1 (0x1)
engine_id - hexdump_ascii(len=6):
     70 6b 63 73 31 31                                 pkcs11
key_id - hexdump_ascii(len=5):
     69 64 5f 34 35                                    id_45
pin - hexdump_ascii(len=4): [REMOVED]
Line: 600 - start of a new network block
ssid - hexdump_ascii(len=7):
     4e 65 74 77 6f 72 6b                              Network
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
ctrl_interface='/var/run/wpa_supplicant'
Line: 610 - start of a new network block
ssid - hexdump_ascii(len=5):
     61 63 6f 72 6e                                    acorn
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 617: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 10
   id=4 ssid='example'
Priority group 5
   id=0 ssid='simple'
   id=16 ssid='static-wep-test'
   id=17 ssid='static-wep-test2'
Priority group 2
   id=1 ssid='second ssid'
   id=2 ssid='example'
   id=5 ssid='example'
   id=7 ssid='example'
Priority group 1
   id=3 ssid='example'
Priority group 0
   id=6 ssid='example'
   id=8 ssid='example'
   id=9 ssid=''
   id=11 ssid='eap-psk-test'
   id=12 ssid='1x-test'
   id=13 ssid='leap-example'
   id=15 ssid='plaintext-test'
   id=18 ssid='test adhoc'
   id=19 ssid='example'
   id=20 ssid='example'
   id=21 ssid='Network'
   id=22 ssid='acorn'
Failed to read configuration file '/etc/wpa_supplicant.conf'.
bennettg@ubuntu:~

In the post below, I will put the /etc/wpa_supplicant.conf file (the board says it is too long if i put it here)

---

### Post by bennettg on 2006-01-14
Part 2 of 2 (see above post.  had to split becuase of size limitations)

Here is my file /etc/wpa_supplicant.conf:

##### Example wpa_supplicant configuration file ###############################
# Empty lines and lines starting with # are ignored

# NOTE! This file may contain password information and should probably be made
# readable only by root user on multiuser systems.

# Whether to allow wpa_supplicant to update (overwrite) configuration
#
# This option can be used to allow wpa_supplicant to overwrite configuration
# file whenever configuration is changed (e.g., new network block is added with
# wpa_cli or wpa_gui, or a password is changed). This is required for
# wpa_cli/wpa_gui to be able to store the configuration changes permanently.
# Please note that overwriting configuration file will remove the comments from
# it.
#update_config=1

# global configuration (shared by all network blocks)
#
# Interface for separate control program. If this is specified, wpa_supplicant
# will create this directory and a UNIX domain socket for listening to requests
# from external programs (CLI/GUI, etc.) for status information and
# configuration. The socket file will be named based on the interface name, so
# multiple wpa_supplicant processes can be run at the same time if more than
# one interface is used.
# /var/run/wpa_supplicant is the recommended directory for sockets and by
# default, wpa_cli will use it when trying to connect with wpa_supplicant.
ctrl_interface=/var/run/wpa_supplicant

# Access control for the control interface can be configured by setting the
# directory to allow only members of a group to use sockets. This way, it is
# possible to run wpa_supplicant as root (since it needs to change network
# configuration and open raw sockets) and still allow GUI/CLI components to be
# run as non-root users. However, since the control interface can be used to
# change the network configuration, this access needs to be protected in many
# cases. By default, wpa_supplicant is configured to use gid 0 (root). If you
# want to allow non-root users to use the control interface, add a new group
# and change this value to match with that group. Add users that should have
# control interface access to this group. If this variable is commented out or
# not included in the configuration file, group will not be changed from the
# value it got by default when the directory or socket was created.
#
# This variable can be a group name or gid.
#ctrl_interface_group=wheel
ctrl_interface_group=0

# IEEE 802.1X/EAPOL version
# wpa_supplicant was implemented based on IEEE 802-1X-REV-d8 which defines
# EAPOL version 2. However, there are many APs that do not handle the new
# version number correctly (they seem to drop the frames completely). In order
# to make wpa_supplicant interoperate with these APs, the version number is set
# to 1 by default. This configuration value can be used to set it to the new
# version (2).
eapol_version=1

# AP scanning/selection
# By default, wpa_supplicant requests driver to perform AP scanning and then
# uses the scan results to select a suitable AP. Another alternative is to
# allow the driver to take care of AP scanning and selection and use
# wpa_supplicant just to process EAPOL frames based on IEEE 802.11 association
# information from the driver.
# 1: wpa_supplicant initiates scanning and AP selection
# 0: driver takes care of scanning, AP selection, and IEEE 802.11 association
#    parameters (e.g., WPA IE generation); this mode can also be used with
#    non-WPA drivers when using IEEE 802.1X mode; do not try to associate with
#    APs (i.e., external program needs to control association). This mode must
#    also be used when using wired Ethernet drivers.
# 2: like 0, but associate with APs using security policy and SSID (but not
#    BSSID); this can be used, e.g., with ndiswrapper and NDIS drivers to
#    enable operation with hidden SSIDs and optimized roaming; in this mode,
#    the network blocks in the configuration file are tried one by one until
#    the driver reports successful association; each network block should have
#    explicit security policy (i.e., only one option in the lists) for
#    key_mgmt, pairwise, group, proto variables
ap_scan=1

# EAP fast re-authentication
# By default, fast re-authentication is enabled for all EAP methods that
# support it. This variable can be used to disable fast re-authentication.
# Normally, there is no need to disable this.
fast_reauth=1

# OpenSSL Engine support
# These options can be used to load OpenSSL engines.
# The two engines that are supported currently are shown below:
# They are both from the opensc project ([http://www.opensc.org/](http://www.opensc.org/))
# By default no engines are loaded.
# make the opensc engine available
opensc_engine_path=/usr/lib/opensc/engine_opensc.so
# make the pkcs11 engine available
pkcs11_engine_path=/usr/lib/opensc/engine_pkcs11.so
# configure the path to the pkcs11 module required by the pkcs11 engine
pkcs11_module_path=/usr/lib/pkcs11/opensc-pkcs11.so

# Driver interface parameters
# This field can be used to configure arbitrary driver interace parameters. The
# format is specific to the selected driver interface. This field is not used
# in most cases.
#driver_param="field=value"

# Maximum lifetime for PMKSA in seconds; default 43200
#dot11RSNAConfigPMKLifetime=43200
# Threshold for reauthentication (percentage of PMK lifetime); default 70
#dot11RSNAConfigPMKReauthThreshold=70
# Timeout for security association negotiation in seconds; default 60
#dot11RSNAConfigSATimeout=60

# network block
#
# Each network (usually AP's sharing the same SSID) is configured as a separate
# block in this configuration file. The network blocks are in preference order
# (the first match is used).
#
# network block fields:
#
# disabled:
#	0 = this network can be used (default)
#	1 = this network block is disabled (can be enabled through ctrl_iface,
#	    e.g., with wpa_cli or wpa_gui)
#
# ssid: SSID (mandatory); either as an ASCII string with double quotation or
#	as hex string; network name
#
# scan_ssid:
#	0 = do not scan this SSID with specific Probe Request frames (default)
#	1 = scan with SSID-specific Probe Request frames (this can be used to
#	    find APs that do not accept broadcast SSID or use multiple SSIDs;
#	    this will add latency to scanning, so enable this only when needed)
#
# bssid: BSSID (optional); if set, this network block is used only when
#	associating with the AP using the configured BSSID
#
# priority: priority group (integer)
# By default, all networks will get same priority group (0). If some of the
# networks are more desirable, this field can be used to change the order in
# which wpa_supplicant goes through the networks when selecting a BSS. The
# priority groups will be iterated in decreasing priority (i.e., the larger the
# priority value, the sooner the network is matched against the scan results).
# Within each priority group, networks will be selected based on security
# policy, signal strength, etc.
# Please note that AP scanning with scan_ssid=1 and ap_scan=2 mode are not
# using this priority to select the order for scanning. Instead, they try the
# networks in the order that used in the configuration file.
#
# mode: IEEE 802.11 operation mode
# 0 = infrastructure (Managed) mode, i.e., associate with an AP (default)
# 1 = IBSS (ad-hoc, peer-to-peer)
# Note: IBSS can only be used with key_mgmt NONE (plaintext and static WEP)
# and key_mgmt=WPA-NONE (fixed group key TKIP/CCMP). In addition, ap_scan has
# to be set to 2 for IBSS. WPA-None requires following network block options:
# proto=WPA, key_mgmt=WPA-NONE, pairwise=NONE, group=TKIP (or CCMP, but not
# both), and psk must also be set.
#
# proto: list of accepted protocols
# WPA = WPA/IEEE 802.11i/D3.0
# RSN = WPA2/IEEE 802.11i (also WPA2 can be used as an alias for RSN)
# If not set, this defaults to: WPA RSN
#
# key_mgmt: list of accepted authenticated key management protocols
# WPA-PSK = WPA pre-shared key (this requires 'psk' field)
# WPA-EAP = WPA using EAP authentication (this can use an external
#	program, e.g., Xsupplicant, for IEEE 802.1X EAP Authentication
# IEEE8021X = IEEE 802.1X using EAP authentication and (optionally) dynamically
#	generated WEP keys
# NONE = WPA is not used; plaintext or static WEP could be used
# If not set, this defaults to: WPA-PSK WPA-EAP
#
# auth_alg: list of allowed IEEE 802.11 authentication algorithms
# OPEN = Open System authentication (required for WPA/WPA2)
# SHARED = Shared Key authentication (requires static WEP keys)
# LEAP = LEAP/Network EAP (only used with LEAP)
# If not set, automatic selection is used (Open System with LEAP enabled if
# LEAP is allowed as one of the EAP methods).
#
# pairwise: list of accepted pairwise (unicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# NONE = Use only Group Keys (deprecated, should not be included if APs support
#	pairwise keys)
# If not set, this defaults to: CCMP TKIP
#
# group: list of accepted group (broadcast/multicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# WEP104 = WEP (Wired Equivalent Privacy) with 104-bit key
# WEP40 = WEP (Wired Equivalent Privacy) with 40-bit key [IEEE 802.11]
# If not set, this defaults to: CCMP TKIP WEP104 WEP40
#
# psk: WPA preshared key; 256-bit pre-shared key
# The key used in WPA-PSK mode can be entered either as 64 hex-digits, i.e.,
# 32 bytes or as an ASCII passphrase (in which case, the real PSK will be
# generated using the passphrase and SSID). ASCII passphrase must be between
# 8 and 63 characters (inclusive).
# This field is not needed, if WPA-EAP is used.
# Note: Separate tool, wpa_passphrase, can be used to generate 256-bit keys
# from ASCII passphrase. This process uses lot of CPU and wpa_supplicant
# startup and reconfiguration time can be optimized by generating the PSK only
# only when the passphrase or SSID has actually changed.
#
# eapol_flags: IEEE 802.1X/EAPOL options (bit field)
# Dynamic WEP key required for non-WPA mode
# bit0 (1): require dynamically generated unicast WEP key
# bit1 (2): require dynamically generated broadcast WEP key
# 	(3 = require both keys; default)
# Note: When using wired authentication, eapol_flags must be set to 0 for the
# authentication to be completed successfully.
#
# proactive_key_caching:
# Enable/disable opportunistic PMKSA caching for WPA2.
# 0 = disabled (default)
# 1 = enabled
#
# Following fields are only used with internal EAP implementation.
# eap: space-separated list of accepted EAP methods
#	MD5 = EAP-MD5 (unsecure and does not generate keying material ->
#			cannot be used with WPA; to be used as a Phase 2 method
#			with EAP-PEAP or EAP-TTLS)
#       MSCHAPV2 = EAP-MSCHAPv2 (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       OTP = EAP-OTP (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       GTC = EAP-GTC (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#	TLS = EAP-TLS (client and server certificate)
#	PEAP = EAP-PEAP (with tunnelled EAP authentication)
#	TTLS = EAP-TTLS (with tunnelled EAP or PAP/CHAP/MSCHAP/MSCHAPV2
#			 authentication)
#	If not set, all compiled in methods are allowed.
#
# identity: Identity string for EAP
# anonymous_identity: Anonymous identity string for EAP (to be used as the
#	unencrypted identity with EAP types that support different tunnelled
#	identity, e.g., EAP-TTLS)
# password: Password string for EAP
# ca_cert: File path to CA certificate file (PEM/DER). This file can have one
#	or more trusted CA certificates. If ca_cert is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured when using EAP-TLS/TTLS/PEAP.
# client_cert: File path to client certificate file (PEM/DER)
# private_key: File path to client private key file (PEM/DER/PFX)
#	When PKCS#12/PFX file (.p12/.pfx) is used, client_cert should be
#	commented out. Both the private key and certificate will be read from
#	the PKCS#12 file in this case.
#	Windows certificate store can be used by leaving client_cert out and
#	configuring private_key in one of the following formats:
#	cert://substring_to_match
#	hash://certificate_thumbprint_in_hex
#	for example: private_key="hash://63093aa9c47f56ae88334c7b65a4"
# private_key_passwd: Password for private key file (if left out, this will be
#	asked through control interface)
# dh_file: File path to DH/DSA parameters file (in PEM format)
#	This is an optional configuration file for setting parameters for an
#	ephemeral DH key exchange. In most cases, the default RSA
#	authentication does not use this configuration. However, it is possible
#	setup RSA to use ephemeral DH key exchange. In addition, ciphers with
#	DSA keys always use ephemeral DH keys. This can be used to achieve
#	forward secrecy. If the file is in DSA parameters format, it will be
#	automatically converted into DH params.
# subject_match: Substring to be matched against the subject of the
#	authentication server certificate. If this string is set, the server
#	sertificate is only accepted if it contains this string in the subject.
#	The subject string is in following format:
#	/C=US/ST=CA/L=San Francisco/CN=Test AS/emailAddress=as@example.com
# altsubject_match: Substring to be matched against the alternative subject
#	name of the authentication server certificate. If this string is set,
#	the server sertificate is only accepted if it contains this string in
#	an alternative subject name extension.
#	altSubjectName string is in following format: TYPE:VALUE
#	Example: DNS:server.example.com
#	Following types are supported: EMAIL, DNS, URI
# phase1: Phase1 (outer authentication, i.e., TLS tunnel) parameters
#	(string with field-value pairs, e.g., "peapver=0" or
#	"peapver=1 peaplabel=1")
#	'peapver' can be used to force which PEAP version (0 or 1) is used.
#	'peaplabel=1' can be used to force new label, "client PEAP encryption",
#	to be used during key derivation when PEAPv1 or newer. Most existing
#	PEAPv1 implementation seem to be using the old label, "client EAP
#	encryption", and wpa_supplicant is now using that as the default value.
#	Some servers, e.g., Radiator, may require peaplabel=1 configuration to
#	interoperate with PEAPv1; see eap_testing.txt for more details.
#	'peap_outer_success=0' can be used to terminate PEAP authentication on
#	tunneled EAP-Success. This is required with some RADIUS servers that
#	implement draft-josefsson-pppext-eap-tls-eap-05.txt (e.g.,
#	Lucent NavisRadius v4.4.0 with PEAP in "IETF Draft 5" mode)
#	include_tls_length=1 can be used to force wpa_supplicant to include
#	TLS Message Length field in all TLS messages even if they are not
#	fragmented.
#	sim_min_num_chal=3 can be used to configure EAP-SIM to require three
#	challenges (by default, it accepts 2 or 3)
# phase2: Phase2 (inner authentication with TLS tunnel) parameters
#	(string with field-value pairs, e.g., "auth=MSCHAPV2" for EAP-PEAP or
#	"autheap=MSCHAPV2 autheap=MD5" for EAP-TTLS)
# Following certificate/private key fields are used in inner Phase2
# authentication when using EAP-TTLS or EAP-PEAP.
# ca_cert2: File path to CA certificate file. This file can have one or more
#	trusted CA certificates. If ca_cert2 is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured.
# client_cert2: File path to client certificate file
# private_key2: File path to client private key file
# private_key2_passwd: Password for private key file
# dh_file2: File path to DH/DSA parameters file (in PEM format)
# subject_match2: Substring to be matched against the subject of the
#	authentication server certificate.
# altsubject_match2: Substring to be matched against the alternative subject
#	name of the authentication server certificate.
#
# EAP-PSK variables:
# eappsk: 16-byte (128-bit, 32 hex digits) pre-shared key in hex format
# nai: user NAI
#
# EAP-FAST variables:
# pac_file: File path for the PAC entries. wpa_supplicant will need to be able
#	to create this file and write updates to it when PAC is being
#	provisioned or refreshed.
# phase1: fast_provisioning=1 option enables in-line provisioning of EAP-FAST
#	credentials (PAC)
#
# wpa_supplicant supports number of "EAP workarounds" to work around
# interoperability issues with incorrectly behaving authentication servers.
# These are enabled by default because some of the issues are present in large
# number of authentication servers. Strict EAP conformance mode can be
# configured by disabling workarounds with eap_workaround=0.

# Example blocks:

# Simple case: WPA-PSK, PSK as an ASCII passphrase, allow all valid ciphers
network={
	ssid="simple"
	psk="very secret passphrase"
	priority=5
}

# Same as previous, but request SSID-specific scanning (for APs that reject
# broadcast SSID)
network={
	ssid="second ssid"
	scan_ssid=1
	psk="very secret passphrase"
	priority=2
}

# Only WPA-PSK is used. Any valid cipher combination is accepted.
network={
	ssid="example"
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP WEP104 WEP40
	psk=06b4be19da289f475aa46a33cb793029d4ab3db7a23ee92382eb0106c72ac7bb
	priority=2
}

# Only WPA-EAP is used. Both CCMP and TKIP is accepted. An AP that used WEP104
# or WEP40 as the group cipher will not be accepted.
network={
	ssid="example"
	proto=RSN
	key_mgmt=WPA-EAP
	pairwise=CCMP TKIP
	group=CCMP TKIP
	eap=TLS
	identity="user@example.com"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"
	private_key="/etc/cert/user.prv"
	private_key_passwd="password"
	priority=1
}

# EAP-PEAP/MSCHAPv2 configuration for RADIUS servers that use the new peaplabel
# (e.g., Radiator)
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=PEAP
	identity="user@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	phase1="peaplabel=1"
	phase2="auth=MSCHAPV2"
	priority=10
}

# EAP-TTLS/EAP-MD5-Challenge configuration with anonymous identity for the
# unencrypted use. Real identity is sent only within an encrypted TLS tunnel.
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TTLS
	identity="user@example.com"
	anonymous_identity="anonymous@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	priority=2
}

# EAP-TTLS/MSCHAPv2 configuration with anonymous identity for the unencrypted
# use. Real identity is sent only within an encrypted TLS tunnel.
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TTLS
	identity="user@example.com"
	anonymous_identity="anonymous@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	phase2="auth=MSCHAPV2"
}

# WPA-EAP, EAP-TTLS with different CA certificate used for outer and inner
# authentication.
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TTLS
	# Phase1 / outer authentication
	anonymous_identity="anonymous@example.com"
	ca_cert="/etc/cert/ca.pem"
	# Phase 2 / inner authentication
	phase2="autheap=TLS"
	ca_cert2="/etc/cert/ca2.pem"
	client_cert2="/etc/cer/user.pem"
	private_key2="/etc/cer/user.prv"
	private_key2_passwd="password"
	priority=2
}

# Both WPA-PSK and WPA-EAP is accepted. Only CCMP is accepted as pairwise and
# group cipher.
network={
	ssid="example"
	bssid=00:11:22:33:44:55
	proto=WPA RSN
	key_mgmt=WPA-PSK WPA-EAP
	pairwise=CCMP
	group=CCMP
	psk=06b4be19da289f475aa46a33cb793029d4ab3db7a23ee92382eb0106c72ac7bb
}

# Special characters in SSID, so use hex string. Default to WPA-PSK, WPA-EAP
# and all valid ciphers.
network={
	ssid=00010203
	psk=000102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f
}


# EAP-SIM with a GSM SIM or USIM
network={
	ssid="eap-sim-test"
	key_mgmt=WPA-EAP
	eap=SIM
	pin="1234"
	pcsc=""
}


# EAP-PSK
network={
	ssid="eap-psk-test"
	key_mgmt=WPA-EAP
	eap=PSK
	identity="eap_psk_user"
	eappsk=06b4be19da289f475aa46a33cb793029
	nai="eap_psk_user@example.com"
}


# IEEE 802.1X/EAPOL with dynamically generated WEP keys (i.e., no WPA) using
# EAP-TLS for authentication and key generation; require both unicast and
# broadcast WEP keys.
network={
	ssid="1x-test"
	key_mgmt=IEEE8021X
	eap=TLS
	identity="user@example.com"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"
	private_key="/etc/cert/user.prv"
	private_key_passwd="password"
	eapol_flags=3
}


# LEAP with dynamic WEP keys
network={
	ssid="leap-example"
	key_mgmt=IEEE8021X
	eap=LEAP
	identity="user"
	password="foobar"
}

# EAP-FAST with WPA (WPA or WPA2)
network={
	ssid="eap-fast-test"
	key_mgmt=WPA-EAP
	eap=FAST
	anonymous_identity="FAST-000102030405"
	identity="username"
	password="password"
	phase1="fast_provisioning=1"
	pac_file="/etc/wpa_supplicant.eap-fast-pac"
}

# Plaintext connection (no WPA, no IEEE 802.1X)
network={
	ssid="plaintext-test"
	key_mgmt=NONE
}


# Shared WEP key connection (no WPA, no IEEE 802.1X)
network={
	ssid="static-wep-test"
	key_mgmt=NONE
	wep_key0="abcde"
	wep_key1=0102030405
	wep_key2="1234567890123"
	wep_tx_keyidx=0
	priority=5
}


# Shared WEP key connection (no WPA, no IEEE 802.1X) using Shared Key
# IEEE 802.11 authentication
network={
	ssid="static-wep-test2"
	key_mgmt=NONE
	wep_key0="abcde"
	wep_key1=0102030405
	wep_key2="1234567890123"
	wep_tx_keyidx=0
	priority=5
	auth_alg=SHARED
}


# IBSS/ad-hoc network with WPA-None/TKIP.
network={
	ssid="test adhoc"
	mode=1
	proto=WPA
	key_mgmt=WPA-NONE
	pairwise=NONE
	group=TKIP
	psk="secret passphrase"
}


# Catch all example that allows more or less all configuration modes
network={
	ssid="example"
	scan_ssid=1
	key_mgmt=WPA-EAP WPA-PSK IEEE8021X NONE
	pairwise=CCMP TKIP
	group=CCMP TKIP WEP104 WEP40
	psk="very secret passphrase"
	eap=TTLS PEAP TLS
	identity="user@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"
	private_key="/etc/cert/user.prv"
	private_key_passwd="password"
	phase1="peaplabel=0"
}

# Example of EAP-TLS with smartcard (openssl engine)
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TLS
	proto=RSN
	pairwise=CCMP TKIP
	group=CCMP TKIP
	identity="user@example.com"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"

	engine=1

	# The engine configured here must be available. Look at
	# OpenSSL engine support in the global section.
	# The key available through the engine must be the private key
	# matching the client certificate configured above.

	# use the opensc engine
	#engine_id="opensc"
	#key_id="45"

	# use the pkcs11 engine
	engine_id="pkcs11"
	key_id="id_45"

	# Optional PIN configuration; this can be left out and PIN will be
	# asked through the control interface
	pin="1234"
}
network={
        ssid="Network"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=0dc7ca9fe55776e6bda6b655c9ae04c3e3dba0718f08e3a9c2d2f6d53c252830
}

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="acorn"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="24334B4A44412423486A736B61"
}

I also tried without the "pairwise=TKIP" without success.

Can someone help me what am I doing worng.

Thanks in advance.

---

### Post by RickKnight on 2006-01-14
Bennettg,

One more thing I had to do, but forgot to mention in my addition to the HOW-TO, was to edit the wpa_supplicant.conf and comment out the "ctrl_interface" and ctrl_interface_group" entries. 

```
#ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=sudo

eapol_version=1
ap_scan=1
fast_reauth=1

network={
 ssid="mynetworkname"
 scan_ssid=1
 proto=WPA
 key_mgmt=WPA-PSK
 psk="my26charpassphrase"
}

network={
 ssid="mynetworkname"
 scan_ssid=1
 proto=WPA
 key_mgmt=WPA-PSK
 psk="my26charpassphrase"
}

```
This is my wpa_supplicant.conf. Notice the 2 top lines are remarked out. I had to do this in order for wpa_supplicant to read the file. I was getting the same error you're seeing and this solved that problem.

Hope this helps,
Rick Knight

---

### Post by bennettg on 2006-01-14
Part 1 of 2 for the post:

Rich,

Thanks.  I commented out what lines I thought you were referring to, but my file didnt look exactley like yours.  Did you post the entrire wpa_supplicant.conf or just a portion of it?  Here is mine now after commenting the 3 lines:

##### Example wpa_supplicant configuration file ###############################
# Empty lines and lines starting with # are ignored

# NOTE! This file may contain password information and should probably be made
# readable only by root user on multiuser systems.

# Whether to allow wpa_supplicant to update (overwrite) configuration
#
# This option can be used to allow wpa_supplicant to overwrite configuration
# file whenever configuration is changed (e.g., new network block is added with
# wpa_cli or wpa_gui, or a password is changed). This is required for
# wpa_cli/wpa_gui to be able to store the configuration changes permanently.
# Please note that overwriting configuration file will remove the comments from
# it.
#update_config=1

# global configuration (shared by all network blocks)
#
# Interface for separate control program. If this is specified, wpa_supplicant
# will create this directory and a UNIX domain socket for listening to requests
# from external programs (CLI/GUI, etc.) for status information and
# configuration. The socket file will be named based on the interface name, so
# multiple wpa_supplicant processes can be run at the same time if more than
# one interface is used.
# /var/run/wpa_supplicant is the recommended directory for sockets and by
# default, wpa_cli will use it when trying to connect with wpa_supplicant.
[SIZE="4"]_# ctrl_interface=/var/run/wpa_supplicant_[/SIZE]

# Access control for the control interface can be configured by setting the
# directory to allow only members of a group to use sockets. This way, it is
# possible to run wpa_supplicant as root (since it needs to change network
# configuration and open raw sockets) and still allow GUI/CLI components to be
# run as non-root users. However, since the control interface can be used to
# change the network configuration, this access needs to be protected in many
# cases. By default, wpa_supplicant is configured to use gid 0 (root). If you
# want to allow non-root users to use the control interface, add a new group
# and change this value to match with that group. Add users that should have
# control interface access to this group. If this variable is commented out or
# not included in the configuration file, group will not be changed from the
# value it got by default when the directory or socket was created.
#
# This variable can be a group name or gid.
[U][SIZE="4"]#ctrl_interface_group=wheel
#ctrl_interface_group=0[/SIZE][/U]

# IEEE 802.1X/EAPOL version
# wpa_supplicant was implemented based on IEEE 802-1X-REV-d8 which defines
# EAPOL version 2. However, there are many APs that do not handle the new
# version number correctly (they seem to drop the frames completely). In order
# to make wpa_supplicant interoperate with these APs, the version number is set
# to 1 by default. This configuration value can be used to set it to the new
# version (2).
eapol_version=1

# AP scanning/selection
# By default, wpa_supplicant requests driver to perform AP scanning and then
# uses the scan results to select a suitable AP. Another alternative is to
# allow the driver to take care of AP scanning and selection and use
# wpa_supplicant just to process EAPOL frames based on IEEE 802.11 association
# information from the driver.
# 1: wpa_supplicant initiates scanning and AP selection
# 0: driver takes care of scanning, AP selection, and IEEE 802.11 association
#    parameters (e.g., WPA IE generation); this mode can also be used with
#    non-WPA drivers when using IEEE 802.1X mode; do not try to associate with
#    APs (i.e., external program needs to control association). This mode must
#    also be used when using wired Ethernet drivers.
# 2: like 0, but associate with APs using security policy and SSID (but not
#    BSSID); this can be used, e.g., with ndiswrapper and NDIS drivers to
#    enable operation with hidden SSIDs and optimized roaming; in this mode,
#    the network blocks in the configuration file are tried one by one until
#    the driver reports successful association; each network block should have
#    explicit security policy (i.e., only one option in the lists) for
#    key_mgmt, pairwise, group, proto variables
ap_scan=1

# EAP fast re-authentication
# By default, fast re-authentication is enabled for all EAP methods that
# support it. This variable can be used to disable fast re-authentication.
# Normally, there is no need to disable this.
fast_reauth=1

# OpenSSL Engine support
# These options can be used to load OpenSSL engines.
# The two engines that are supported currently are shown below:
# They are both from the opensc project ([http://www.opensc.org/](http://www.opensc.org/))
# By default no engines are loaded.
# make the opensc engine available
opensc_engine_path=/usr/lib/opensc/engine_opensc.so
# make the pkcs11 engine available
pkcs11_engine_path=/usr/lib/opensc/engine_pkcs11.so
# configure the path to the pkcs11 module required by the pkcs11 engine
pkcs11_module_path=/usr/lib/pkcs11/opensc-pkcs11.so

# Driver interface parameters
# This field can be used to configure arbitrary driver interace parameters. The
# format is specific to the selected driver interface. This field is not used
# in most cases.
#driver_param="field=value"

# Maximum lifetime for PMKSA in seconds; default 43200
#dot11RSNAConfigPMKLifetime=43200
# Threshold for reauthentication (percentage of PMK lifetime); default 70
#dot11RSNAConfigPMKReauthThreshold=70
# Timeout for security association negotiation in seconds; default 60
#dot11RSNAConfigSATimeout=60

# network block
#
# Each network (usually AP's sharing the same SSID) is configured as a separate
# block in this configuration file. The network blocks are in preference order
# (the first match is used).
#
# network block fields:
#
# disabled:
#	0 = this network can be used (default)
#	1 = this network block is disabled (can be enabled through ctrl_iface,
#	    e.g., with wpa_cli or wpa_gui)
#
# ssid: SSID (mandatory); either as an ASCII string with double quotation or
#	as hex string; network name
#
# scan_ssid:
#	0 = do not scan this SSID with specific Probe Request frames (default)
#	1 = scan with SSID-specific Probe Request frames (this can be used to
#	    find APs that do not accept broadcast SSID or use multiple SSIDs;
#	    this will add latency to scanning, so enable this only when needed)
#
# bssid: BSSID (optional); if set, this network block is used only when
#	associating with the AP using the configured BSSID
#
# priority: priority group (integer)
# By default, all networks will get same priority group (0). If some of the
# networks are more desirable, this field can be used to change the order in
# which wpa_supplicant goes through the networks when selecting a BSS. The
# priority groups will be iterated in decreasing priority (i.e., the larger the
# priority value, the sooner the network is matched against the scan results).
# Within each priority group, networks will be selected based on security
# policy, signal strength, etc.
# Please note that AP scanning with scan_ssid=1 and ap_scan=2 mode are not
# using this priority to select the order for scanning. Instead, they try the
# networks in the order that used in the configuration file.
#
# mode: IEEE 802.11 operation mode
# 0 = infrastructure (Managed) mode, i.e., associate with an AP (default)
# 1 = IBSS (ad-hoc, peer-to-peer)
# Note: IBSS can only be used with key_mgmt NONE (plaintext and static WEP)
# and key_mgmt=WPA-NONE (fixed group key TKIP/CCMP). In addition, ap_scan has
# to be set to 2 for IBSS. WPA-None requires following network block options:
# proto=WPA, key_mgmt=WPA-NONE, pairwise=NONE, group=TKIP (or CCMP, but not
# both), and psk must also be set.
#
# proto: list of accepted protocols
# WPA = WPA/IEEE 802.11i/D3.0
# RSN = WPA2/IEEE 802.11i (also WPA2 can be used as an alias for RSN)
# If not set, this defaults to: WPA RSN
#
# key_mgmt: list of accepted authenticated key management protocols
# WPA-PSK = WPA pre-shared key (this requires 'psk' field)
# WPA-EAP = WPA using EAP authentication (this can use an external
#	program, e.g., Xsupplicant, for IEEE 802.1X EAP Authentication
# IEEE8021X = IEEE 802.1X using EAP authentication and (optionally) dynamically
#	generated WEP keys
# NONE = WPA is not used; plaintext or static WEP could be used
# If not set, this defaults to: WPA-PSK WPA-EAP
#
# auth_alg: list of allowed IEEE 802.11 authentication algorithms
# OPEN = Open System authentication (required for WPA/WPA2)
# SHARED = Shared Key authentication (requires static WEP keys)
# LEAP = LEAP/Network EAP (only used with LEAP)
# If not set, automatic selection is used (Open System with LEAP enabled if
# LEAP is allowed as one of the EAP methods).
#
# pairwise: list of accepted pairwise (unicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# NONE = Use only Group Keys (deprecated, should not be included if APs support
#	pairwise keys)
# If not set, this defaults to: CCMP TKIP
#
# group: list of accepted group (broadcast/multicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# WEP104 = WEP (Wired Equivalent Privacy) with 104-bit key
# WEP40 = WEP (Wired Equivalent Privacy) with 40-bit key [IEEE 802.11]
# If not set, this defaults to: CCMP TKIP WEP104 WEP40
#
# psk: WPA preshared key; 256-bit pre-shared key
# The key used in WPA-PSK mode can be entered either as 64 hex-digits, i.e.,
# 32 bytes or as an ASCII passphrase (in which case, the real PSK will be
# generated using the passphrase and SSID). ASCII passphrase must be between
# 8 and 63 characters (inclusive).
# This field is not needed, if WPA-EAP is used.
# Note: Separate tool, wpa_passphrase, can be used to generate 256-bit keys
# from ASCII passphrase. This process uses lot of CPU and wpa_supplicant
# startup and reconfiguration time can be optimized by generating the PSK only
# only when the passphrase or SSID has actually changed.
#
# eapol_flags: IEEE 802.1X/EAPOL options (bit field)
# Dynamic WEP key required for non-WPA mode
# bit0 (1): require dynamically generated unicast WEP key
# bit1 (2): require dynamically generated broadcast WEP key
# 	(3 = require both keys; default)
# Note: When using wired authentication, eapol_flags must be set to 0 for the
# authentication to be completed successfully.
#
# proactive_key_caching:
# Enable/disable opportunistic PMKSA caching for WPA2.
# 0 = disabled (default)
# 1 = enabled
#
# Following fields are only used with internal EAP implementation.
# eap: space-separated list of accepted EAP methods
#	MD5 = EAP-MD5 (unsecure and does not generate keying material ->
#			cannot be used with WPA; to be used as a Phase 2 method
#			with EAP-PEAP or EAP-TTLS)
#       MSCHAPV2 = EAP-MSCHAPv2 (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       OTP = EAP-OTP (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       GTC = EAP-GTC (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#	TLS = EAP-TLS (client and server certificate)
#	PEAP = EAP-PEAP (with tunnelled EAP authentication)
#	TTLS = EAP-TTLS (with tunnelled EAP or PAP/CHAP/MSCHAP/MSCHAPV2
#			 authentication)
#	If not set, all compiled in methods are allowed.
#
# identity: Identity string for EAP
# anonymous_identity: Anonymous identity string for EAP (to be used as the
#	unencrypted identity with EAP types that support different tunnelled
#	identity, e.g., EAP-TTLS)
# password: Password string for EAP
# ca_cert: File path to CA certificate file (PEM/DER). This file can have one
#	or more trusted CA certificates. If ca_cert is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured when using EAP-TLS/TTLS/PEAP.
# client_cert: File path to client certificate file (PEM/DER)
# private_key: File path to client private key file (PEM/DER/PFX)
#	When PKCS#12/PFX file (.p12/.pfx) is used, client_cert should be
#	commented out. Both the private key and certificate will be read from
#	the PKCS#12 file in this case.
#	Windows certificate store can be used by leaving client_cert out and
#	configuring private_key in one of the following formats:
#	cert://substring_to_match
#	hash://certificate_thumbprint_in_hex
#	for example: private_key="hash://63093aa9c47f56ae88334c7b65a4"
# private_key_passwd: Password for private key file (if left out, this will be
#	asked through control interface)
# dh_file: File path to DH/DSA parameters file (in PEM format)
#	This is an optional configuration file for setting parameters for an
#	ephemeral DH key exchange. In most cases, the default RSA
#	authentication does not use this configuration. However, it is possible
#	setup RSA to use ephemeral DH key exchange. In addition, ciphers with
#	DSA keys always use ephemeral DH keys. This can be used to achieve
#	forward secrecy. If the file is in DSA parameters format, it will be
#	automatically converted into DH params.
# subject_match: Substring to be matched against the subject of the
#	authentication server certificate. If this string is set, the server
#	sertificate is only accepted if it contains this string in the subject.
#	The subject string is in following format:
#	/C=US/ST=CA/L=San Francisco/CN=Test AS/emailAddress=as@example.com
# altsubject_match: Substring to be matched against the alternative subject
#	name of the authentication server certificate. If this string is set,
#	the server sertificate is only accepted if it contains this string in
#	an alternative subject name extension.
#	altSubjectName string is in following format: TYPE:VALUE
#	Example: DNS:server.example.com
#	Following types are supported: EMAIL, DNS, URI
# phase1: Phase1 (outer authentication, i.e., TLS tunnel) parameters
#	(string with field-value pairs, e.g., "peapver=0" or
#	"peapver=1 peaplabel=1")
#	'peapver' can be used to force which PEAP version (0 or 1) is used.
#	'peaplabel=1' can be used to force new label, "client PEAP encryption",
#	to be used during key derivation when PEAPv1 or newer. Most existing
#	PEAPv1 implementation seem to be using the old label, "client EAP
#	encryption", and wpa_supplicant is now using that as the default value.
#	Some servers, e.g., Radiator, may require peaplabel=1 configuration to
#	interoperate with PEAPv1; see eap_testing.txt for more details.
#	'peap_outer_success=0' can be used to terminate PEAP authentication on
#	tunneled EAP-Success. This is required with some RADIUS servers that
#	implement draft-josefsson-pppext-eap-tls-eap-05.txt (e.g.,
#	Lucent NavisRadius v4.4.0 with PEAP in "IETF Draft 5" mode)
#	include_tls_length=1 can be used to force wpa_supplicant to include
#	TLS Message Length field in all TLS messages even if they are not
#	fragmented.
#	sim_min_num_chal=3 can be used to configure EAP-SIM to require three
#	challenges (by default, it accepts 2 or 3)
# phase2: Phase2 (inner authentication with TLS tunnel) parameters
#	(string with field-value pairs, e.g., "auth=MSCHAPV2" for EAP-PEAP or
#	"autheap=MSCHAPV2 autheap=MD5" for EAP-TTLS)
# Following certificate/private key fields are used in inner Phase2
# authentication when using EAP-TTLS or EAP-PEAP.
# ca_cert2: File path to CA certificate file. This file can have one or more
#	trusted CA certificates. If ca_cert2 is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured.
# client_cert2: File path to client certificate file
# private_key2: File path to client private key file
# private_key2_passwd: Password for private key file
# dh_file2: File path to DH/DSA parameters file (in PEM format)
# subject_match2: Substring to be matched against the subject of the
#	authentication server certificate.
# altsubject_match2: Substring to be matched against the alternative subject
#	name of the authentication server certificate.
#
# EAP-PSK variables:
# eappsk: 16-byte (128-bit, 32 hex digits) pre-shared key in hex format
# nai: user NAI
#
# EAP-FAST variables:
# pac_file: File path for the PAC entries. wpa_supplicant will need to be able
#	to create this file and write updates to it when PAC is being
#	provisioned or refreshed.
# phase1: fast_provisioning=1 option enables in-line provisioning of EAP-FAST
#	credentials (PAC)
#
# wpa_supplicant supports number of "EAP workarounds" to work around
# interoperability issues with incorrectly behaving authentication servers.
# These are enabled by default because some of the issues are present in large
# number of authentication servers. Strict EAP conformance mode can be
# configured by disabling workarounds with eap_workaround=0.

# Example blocks:

# Simple case: WPA-PSK, PSK as an ASCII passphrase, allow all valid ciphers
network={
	ssid="simple"
	psk="very secret passphrase"
	priority=5
}

# Same as previous, but request SSID-specific scanning (for APs that reject
# broadcast SSID)
network={
	ssid="second ssid"
	scan_ssid=1
	psk="very secret passphrase"
	priority=2
}

# Only WPA-PSK is used. Any valid cipher combination is accepted.
network={
	ssid="example"
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP WEP104 WEP40
	psk=06b4be19da289f475aa46a33cb793029d4ab3db7a23ee92382eb0106c72ac7bb
	priority=2
}

# Only WPA-EAP is used. Both CCMP and TKIP is accepted. An AP that used WEP104
# or WEP40 as the group cipher will not be accepted.
network={
	ssid="example"
	proto=RSN
	key_mgmt=WPA-EAP
	pairwise=CCMP TKIP
	group=CCMP TKIP
	eap=TLS
	identity="user@example.com"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"
	private_key="/etc/cert/user.prv"
	private_key_passwd="password"
	priority=1
}

# EAP-PEAP/MSCHAPv2 configuration for RADIUS servers that use the new peaplabel
# (e.g., Radiator)
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=PEAP
	identity="user@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	phase1="peaplabel=1"
	phase2="auth=MSCHAPV2"
	priority=10
}

# EAP-TTLS/EAP-MD5-Challenge configuration with anonymous identity for the
# unencrypted use. Real identity is sent only within an encrypted TLS tunnel.
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TTLS
	identity="user@example.com"
	anonymous_identity="anonymous@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	priority=2
}

# EAP-TTLS/MSCHAPv2 configuration with anonymous identity for the unencrypted
# use. Real identity is sent only within an encrypted TLS tunnel.
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TTLS
	identity="user@example.com"
	anonymous_identity="anonymous@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	phase2="auth=MSCHAPV2"
}

# WPA-EAP, EAP-TTLS with different CA certificate used for outer and inner
# authentication.
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TTLS
	# Phase1 / outer authentication
	anonymous_identity="anonymous@example.com"
	ca_cert="/etc/cert/ca.pem"
	# Phase 2 / inner authentication
	phase2="autheap=TLS"
	ca_cert2="/etc/cert/ca2.pem"
	client_cert2="/etc/cer/user.pem"
	private_key2="/etc/cer/user.prv"
	private_key2_passwd="password"
	priority=2
}

# Both WPA-PSK and WPA-EAP is accepted. Only CCMP is accepted as pairwise and
# group cipher.
network={
	ssid="example"
	bssid=00:11:22:33:44:55
	proto=WPA RSN
	key_mgmt=WPA-PSK WPA-EAP
	pairwise=CCMP
	group=CCMP
	psk=06b4be19da289f475aa46a33cb793029d4ab3db7a23ee92382eb0106c72ac7bb
}

# Special characters in SSID, so use hex string. Default to WPA-PSK, WPA-EAP
# and all valid ciphers.
network={
	ssid=00010203
	psk=000102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f
}


# EAP-SIM with a GSM SIM or USIM
network={
	ssid="eap-sim-test"
	key_mgmt=WPA-EAP
	eap=SIM
	pin="1234"
	pcsc=""
}


# EAP-PSK
network={
	ssid="eap-psk-test"
	key_mgmt=WPA-EAP
	eap=PSK
	identity="eap_psk_user"
	eappsk=06b4be19da289f475aa46a33cb793029
	nai="eap_psk_user@example.com"
}


# IEEE 802.1X/EAPOL with dynamically generated WEP keys (i.e., no WPA) using
# EAP-TLS for authentication and key generation; require both unicast and
# broadcast WEP keys.
network={
	ssid="1x-test"
	key_mgmt=IEEE8021X
	eap=TLS
	identity="user@example.com"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"
	private_key="/etc/cert/user.prv"
	private_key_passwd="password"
	eapol_flags=3
}


# LEAP with dynamic WEP keys
network={
	ssid="leap-example"
	key_mgmt=IEEE8021X
	eap=LEAP
	identity="user"
	password="foobar"
}

# EAP-FAST with WPA (WPA or WPA2)
network={
	ssid="eap-fast-test"
	key_mgmt=WPA-EAP
	eap=FAST
	anonymous_identity="FAST-000102030405"
	identity="username"
	password="password"
	phase1="fast_provisioning=1"
	pac_file="/etc/wpa_supplicant.eap-fast-pac"
}

# Plaintext connection (no WPA, no IEEE 802.1X)
network={
	ssid="plaintext-test"
	key_mgmt=NONE
}


# Shared WEP key connection (no WPA, no IEEE 802.1X)
network={
	ssid="static-wep-test"
	key_mgmt=NONE
	wep_key0="abcde"
	wep_key1=0102030405
	wep_key2="1234567890123"
	wep_tx_keyidx=0
	priority=5
}


# Shared WEP key connection (no WPA, no IEEE 802.1X) using Shared Key
# IEEE 802.11 authentication
network={
	ssid="static-wep-test2"
	key_mgmt=NONE
	wep_key0="abcde"
	wep_key1=0102030405
	wep_key2="1234567890123"
	wep_tx_keyidx=0
	priority=5
	auth_alg=SHARED
}


# IBSS/ad-hoc network with WPA-None/TKIP.
network={
	ssid="test adhoc"
	mode=1
	proto=WPA
	key_mgmt=WPA-NONE
	pairwise=NONE
	group=TKIP
	psk="secret passphrase"
}


# Catch all example that allows more or less all configuration modes
network={
	ssid="example"
	scan_ssid=1
	key_mgmt=WPA-EAP WPA-PSK IEEE8021X NONE
	pairwise=CCMP TKIP
	group=CCMP TKIP WEP104 WEP40
	psk="very secret passphrase"
	eap=TTLS PEAP TLS
	identity="user@example.com"
	password="foobar"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"
	private_key="/etc/cert/user.prv"
	private_key_passwd="password"
	phase1="peaplabel=0"
}

# Example of EAP-TLS with smartcard (openssl engine)
network={
	ssid="example"
	key_mgmt=WPA-EAP
	eap=TLS
	proto=RSN
	pairwise=CCMP TKIP
	group=CCMP TKIP
	identity="user@example.com"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"

	engine=1

	# The engine configured here must be available. Look at
	# OpenSSL engine support in the global section.
	# The key available through the engine must be the private key
	# matching the client certificate configured above.

	# use the opensc engine
	#engine_id="opensc"
	#key_id="45"

	# use the pkcs11 engine
	engine_id="pkcs11"
	key_id="id_45"

	# Optional PIN configuration; this can be left out and PIN will be
	# asked through the control interface
	pin="1234"
}
network={
        ssid="Network"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=0dc7ca9fe55776e6bda6b655c9ae04c3e3dba0718f08e3a9c2d2f6d53c252830
}
[SIZE="4"][U]
#ctrl_interface=/var/run/wpa_supplicant[/U][/SIZE]

network={
       ssid="acorn"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="24334B4A44412423486A736B61"
}

In the file above, I underlined and increased the font size to show you were I made the changes you suggested.

After changing the /etc/wpa.supplicant.conf file, here is the outpur I got from the terminal:

See post 2 of 2 below

---

### Post by bennettg on 2006-01-14
post 2 of 2 from above:



[4294702.071000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.2
[4294702.071000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[4294702.075000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
bennettg@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
eapol_version=1
ap_scan=1
fast_reauth=1
opensc_engine_path='/usr/lib/opensc/engine_opensc.so'
pkcs11_engine_path='/usr/lib/opensc/engine_pkcs11.so'
pkcs11_module_path='/usr/lib/pkcs11/opensc-pkcs11.so'
Line: 327 - start of a new network block
ssid - hexdump_ascii(len=6):
     73 69 6d 70 6c 65                                 simple
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
priority=5 (0x5)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 335 - start of a new network block
ssid - hexdump_ascii(len=11):
     73 65 63 6f 6e 64 20 73 73 69 64                  second ssid
scan_ssid=1 (0x1)
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
priority=2 (0x2)
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 343 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
proto: 0x1
key_mgmt: 0x2
pairwise: 0x18
group: 0x1e
PSK - hexdump(len=32): [REMOVED]
priority=2 (0x2)
Line: 355 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
proto: 0x2
key_mgmt: 0x1
pairwise: 0x18
group: 0x18
eap methods - hexdump(len=2): 0d 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
private_key - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     72 76                                             rv
private_key_passwd - hexdump_ascii(len=8): [REMOVED]
priority=1 (0x1)
Line: 372 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 19 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
phase1 - hexdump_ascii(len=11):
     70 65 61 70 6c 61 62 65 6c 3d 31                  peaplabel=1
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2
priority=10 (0xa)
Line: 386 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 15 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
anonymous_identity - hexdump_ascii(len=21):
     61 6e 6f 6e 79 6d 6f 75 73 40 65 78 61 6d 70 6c   anonymous@exampl
     65 2e 63 6f 6d                                    e.com
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
priority=2 (0x2)
Line: 399 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 15 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
anonymous_identity - hexdump_ascii(len=21):
     61 6e 6f 6e 79 6d 6f 75 73 40 65 78 61 6d 70 6c   anonymous@exampl
     65 2e 63 6f 6d                                    e.com
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2
Line: 412 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 15 00
anonymous_identity - hexdump_ascii(len=21):
     61 6e 6f 6e 79 6d 6f 75 73 40 65 78 61 6d 70 6c   anonymous@exampl
     65 2e 63 6f 6d                                    e.com
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
phase2 - hexdump_ascii(len=11):
     61 75 74 68 65 61 70 3d 54 4c 53                  autheap=TLS
ca_cert2 - hexdump_ascii(len=17):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 32 2e 70 65   /etc/cert/ca2.pe
     6d                                                m
client_cert2 - hexdump_ascii(len=17):
     2f 65 74 63 2f 63 65 72 2f 75 73 65 72 2e 70 65   /etc/cer/user.pe
     6d                                                m
private_key2 - hexdump_ascii(len=17):
     2f 65 74 63 2f 63 65 72 2f 75 73 65 72 2e 70 72   /etc/cer/user.pr
     76                                                v
private_key2_passwd - hexdump_ascii(len=8): [REMOVED]
priority=2 (0x2)
Line: 430 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
BSSID - hexdump(len=6): 00 11 22 33 44 55
proto: 0x3
key_mgmt: 0x3
pairwise: 0x10
group: 0x10
PSK - hexdump(len=32): [REMOVED]
Line: 442 - start of a new network block
ssid - hexdump_ascii(len=4):
     00 01 02 03                                       ____
PSK - hexdump(len=32): [REMOVED]
Line: 449 - start of a new network block
ssid - hexdump_ascii(len=12):
     65 61 70 2d 73 69 6d 2d 74 65 73 74               eap-sim-test
key_mgmt: 0x1
Line 452: unknown EAP method 'SIM'
You may need to add support for this EAP method during wpa_supplicant
build time configuration.
See README for more information.
eap methods - hexdump(len=2): 00 00
Line 452: failed to parse eap 'SIM'.
pin - hexdump_ascii(len=4): [REMOVED]
pcsc - hexdump_ascii(len=0):
Line 455: failed to parse network block.
Line: 459 - start of a new network block
ssid - hexdump_ascii(len=12):
     65 61 70 2d 70 73 6b 2d 74 65 73 74               eap-psk-test
key_mgmt: 0x1
eap methods - hexdump(len=2): ff 00
identity - hexdump_ascii(len=12):
     65 61 70 5f 70 73 6b 5f 75 73 65 72               eap_psk_user
eappsk - hexdump_ascii(len=16): [REMOVED]
nai - hexdump_ascii(len=24):
     65 61 70 5f 70 73 6b 5f 75 73 65 72 40 65 78 61   eap_psk_user@exa
     6d 70 6c 65 2e 63 6f 6d                           mple.com
Line: 472 - start of a new network block
ssid - hexdump_ascii(len=7):
     31 78 2d 74 65 73 74                              1x-test
key_mgmt: 0x8
eap methods - hexdump(len=2): 0d 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
private_key - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     72 76                                             rv
private_key_passwd - hexdump_ascii(len=8): [REMOVED]
eapol_flags=3 (0x3)
Line: 486 - start of a new network block
ssid - hexdump_ascii(len=12):
     6c 65 61 70 2d 65 78 61 6d 70 6c 65               leap-example
key_mgmt: 0x8
eap methods - hexdump(len=2): 11 00
identity - hexdump_ascii(len=4):
     75 73 65 72                                       user
password - hexdump_ascii(len=6): [REMOVED]
Line: 495 - start of a new network block
ssid - hexdump_ascii(len=13):
     65 61 70 2d 66 61 73 74 2d 74 65 73 74            eap-fast-test
key_mgmt: 0x1
Line 498: unknown EAP method 'FAST'
You may need to add support for this EAP method during wpa_supplicant
build time configuration.
See README for more information.
eap methods - hexdump(len=2): 00 00
Line 498: failed to parse eap 'FAST'.
anonymous_identity - hexdump_ascii(len=17):
     46 41 53 54 2d 30 30 30 31 30 32 30 33 30 34 30   FAST-00010203040
     35                                                5
identity - hexdump_ascii(len=8):
     75 73 65 72 6e 61 6d 65                           username
password - hexdump_ascii(len=8): [REMOVED]
phase1 - hexdump_ascii(len=19):
     66 61 73 74 5f 70 72 6f 76 69 73 69 6f 6e 69 6e   fast_provisionin
     67 3d 31                                          g=1
pac_file - hexdump_ascii(len=32):
     2f 65 74 63 2f 77 70 61 5f 73 75 70 70 6c 69 63   /etc/wpa_supplic
     61 6e 74 2e 65 61 70 2d 66 61 73 74 2d 70 61 63   ant.eap-fast-pac
Line 504: failed to parse network block.
Line: 507 - start of a new network block
ssid - hexdump_ascii(len=14):
     70 6c 61 69 6e 74 65 78 74 2d 74 65 73 74         plaintext-test
key_mgmt: 0x4
Line: 514 - start of a new network block
ssid - hexdump_ascii(len=15):
     73 74 61 74 69 63 2d 77 65 70 2d 74 65 73 74      static-wep-test
key_mgmt: 0x4
wep_key0 - hexdump(len=5): [REMOVED]
wep_key1 - hexdump(len=5): [REMOVED]
wep_key2 - hexdump(len=13): [REMOVED]
wep_tx_keyidx=0 (0x0)
priority=5 (0x5)
Line: 527 - start of a new network block
ssid - hexdump_ascii(len=16):
     73 74 61 74 69 63 2d 77 65 70 2d 74 65 73 74 32   static-wep-test2
key_mgmt: 0x4
wep_key0 - hexdump(len=5): [REMOVED]
wep_key1 - hexdump(len=5): [REMOVED]
wep_key2 - hexdump(len=13): [REMOVED]
wep_tx_keyidx=0 (0x0)
priority=5 (0x5)
auth_alg: 0x2
Line: 540 - start of a new network block
ssid - hexdump_ascii(len=10):
     74 65 73 74 20 61 64 68 6f 63                     test adhoc
mode=1 (0x1)
proto: 0x1
key_mgmt: 0x10
pairwise: 0x1
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=17): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 552 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
scan_ssid=1 (0x1)
key_mgmt: 0xf
pairwise: 0x18
group: 0x1e
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
eap methods - hexdump(len=4): 15 19 0d 00
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
password - hexdump_ascii(len=6): [REMOVED]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
private_key - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     72 76                                             rv
private_key_passwd - hexdump_ascii(len=8): [REMOVED]
phase1 - hexdump_ascii(len=11):
     70 65 61 70 6c 61 62 65 6c 3d 30                  peaplabel=0
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line: 570 - start of a new network block
ssid - hexdump_ascii(len=7):
     65 78 61 6d 70 6c 65                              example
key_mgmt: 0x1
eap methods - hexdump(len=2): 0d 00
proto: 0x2
pairwise: 0x18
group: 0x18
identity - hexdump_ascii(len=16):
     75 73 65 72 40 65 78 61 6d 70 6c 65 2e 63 6f 6d   [email]user@example.com[/email]
ca_cert - hexdump_ascii(len=16):
     2f 65 74 63 2f 63 65 72 74 2f 63 61 2e 70 65 6d   /etc/cert/ca.pem
client_cert - hexdump_ascii(len=18):
     2f 65 74 63 2f 63 65 72 74 2f 75 73 65 72 2e 70   /etc/cert/user.p
     65 6d                                             em
engine=1 (0x1)
engine_id - hexdump_ascii(len=6):
     70 6b 63 73 31 31                                 pkcs11
key_id - hexdump_ascii(len=5):
     69 64 5f 34 35                                    id_45
pin - hexdump_ascii(len=4): [REMOVED]
Line: 600 - start of a new network block
ssid - hexdump_ascii(len=7):
     4e 65 74 77 6f 72 6b                              Network
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Line: 610 - start of a new network block
ssid - hexdump_ascii(len=5):
     61 63 6f 72 6e                                    acorn
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 617: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 10
   id=4 ssid='example'
Priority group 5
   id=0 ssid='simple'
   id=16 ssid='static-wep-test'
   id=17 ssid='static-wep-test2'
Priority group 2
   id=1 ssid='second ssid'
   id=2 ssid='example'
   id=5 ssid='example'
   id=7 ssid='example'
Priority group 1
   id=3 ssid='example'
Priority group 0
   id=6 ssid='example'
   id=8 ssid='example'
   id=9 ssid=''
   id=11 ssid='eap-psk-test'
   id=12 ssid='1x-test'
   id=13 ssid='leap-example'
   id=15 ssid='plaintext-test'
   id=18 ssid='test adhoc'
   id=19 ssid='example'
   id=20 ssid='example'
   id=21 ssid='Network'
   id=22 ssid='acorn'
Failed to read configuration file '/etc/wpa_supplicant.conf'.
bennettg@ubuntu:~$ 

Any ideas as to what I am still doing wrong?  thanks

---

### Post by RickKnight on 2006-01-14
Bennettg,

You are using sudo to start wpa_supplicant?

Try this. Move your .conf file out of the way and create a new, empty .conf file using your favorite text editor (I usually use kate)
```
cd /etc
sudo mv wpa_supplicant.conf wpa_supplicant.conf.bak
sduo touch wpa_supplicant.conf
```
Now copy/paste the is code into your empty .conf file```

eapol_version=1
ap_scan=1
fast_reauth=1

network={
 ssid="acorn"
 scan_ssid=1
 proto=WPA
 key_mgmt=WPA-PSK
 psk="24334B4A44412423486A736B61"
}

```Adjust the .conf for your network but don't add anything.
Try the wpa_supplicant test.
```
sudo wpa_supplicant -ietho -c/etc/wpa_supplicnt.conf -Dipw -w
```
If this still doesn't work, post just the output of the command. To capture it in a log file, try this```
sudo wpa_supplicant -ietho -c/etc/wpa_supplicnt.conf -Dipw -w >& ~/wpa.log
```Then post the wpa.log in your home directory.

Good Luck,
Rick Knight

---

### Post by bennettg on 2006-01-14
Still no luck.  here is the output from the terminal command:sudo wpa_supplicant -ietho -c/etc/wpa_supplicnt.conf -Dipw -w


w
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'etho' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..



here is the log you asked me to post from the terminal command sudo wpa_supplicant -ietho -c/etc/wpa_supplicnt.conf -Dipw -w >& ~/wpa.log               

ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
ioctl[SIOCGIFFLAGS]: No such device
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCGIFINDEX]: No such device

---

### Post by bennettg on 2006-01-14
had to edit 

[QUOTE=bennettg]Still no luck.  here is the output from the terminal command:sudo wpa_supplicant -ietho -c/etc/wpa_supplicnt.conf -Dipw -w


w
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'etho' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..



here is the log you asked me to post from the terminal command sudo wpa_supplicant -ietho -c/etc/wpa_supplicnt.conf -Dipw -w >& ~/wpa.log               

ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
ioctl[SIOCGIFFLAGS]: No such device
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCGIFINDEX]: No such device[/QUOTE]

---

### Post by RickKnight on 2006-01-14
Bennettg,

Ihope you didn't repeat my typo on your command line. wpa_supplicnt.conf should be wpa_supplicant.conf.

Sorry 'bout that
Rick Knight

---

### Post by RickKnight on 2006-01-14
Are you sure you have the ipw2200 module loaded?

Do sudo modinfo ipw2200.

Rick Knight

---

### Post by RickKnight on 2006-01-14
Bennettg,

Also do ifconfig.

I'm assuming you have an ethernet card as well as the wireless? You may als want to take a look at /etc/network/interfaces. Post thst here if you can.

Rick Knight

---

### Post by bennettg on 2006-01-14
bennettg@ubuntu:~$ sudo modinfo ipw2200 
Password:
filename:       /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200.ko
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
version:        1.0.10
author:         Copyright(c) 2003-2005 Intel Corporation
license:        GPL
vermagic:       2.6.12-10-686 686 gcc-3.4
depends:        ieee80211,ieee80211_crypt,ieee80211,firmware_class
alias:          pci:v00008086d00001043sv00008086sd00002701bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002702bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002711bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002712bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002721bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002722bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002731bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002732bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv0000103Csd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002742bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002751bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002752bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002753bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002754bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002761bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002762bc*sc*i*
alias:          pci:v00008086d0000104Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00004220sv*sd*bc*sc*i*
alias:          pci:v00008086d00004221sv*sd*bc*sc*i*
alias:          pci:v00008086d00004223sv*sd*bc*sc*i*
alias:          pci:v00008086d00004224sv*sd*bc*sc*i*
srcversion:     887496B10C4BB70516D2F71
parm:           roaming:enable roaming support (default on) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           hwcrypto:enable hardware crypto (default on) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           debug:debug output mask (int)
parm:           led:enable led control on some systems (default 0 off)
 (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           associate:auto associate when scanning (default on) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
bennettg@ubuntu:~$   

Here is my /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid acorn
	wireless-key1 24334B4A44412423486A736B61

iface eth0 inet dhcp

auto eth0

---

### Post by RickKnight on 2006-01-14
Bennettg,

Is your wireless interface eth0 or eth1? If eth1, then you need to run wpa_supplicant like this ```
sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dipw -w
```
Also, post the output of 'ifconfig'.

Rick Knight

---

### Post by bennettg on 2006-01-14
here is the output:

bennettg@ubuntu:~$ ifconfig   
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:26:F8:FD
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe26:f8fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:799220 (780.4 KiB)  TX bytes:201929 (197.1 KiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:2A:F3:C8
          inet6 addr: fe80::20c:f1ff:fe2a:f3c8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 Base address:0xc000 Memory:faffc000-faffcfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)




the wireless is eth1.  so i did this in the terminal
bennettg@ubuntu:~$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dipw -w 
bennettg@ubuntu:~$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dipw -w
Password:
ioctl[SIOCSIWPMKSA]: Operation not supported


I tried this last command earlier and was getting output that said it was associated, with outher things.  then the computer froze.  when i did it again after restarting, all i got was the above

---

### Post by RickKnight on 2006-01-14
bennettg,

Did you apply a fix that called for creating```
/etc/modprobe.d/ipw2200
```And adding the single line```
options ipw2200 hwcrypt=0
```?
If you did, then undo it by putting a # at the beginning of the line. You can also use this file to turn on control of the wireless LED```
options ipw2200 led=1
```

---

### Post by RickKnight on 2006-01-14
Bennettg,

I think you're allmost there. If you can run the wpa_supplicant command and get a good 'associate' without locking up, try to enable dhcp on the interface```
sudo dhclient eth1
```And see if it gets you an IP address.

Rick Knight

---

### Post by bennettg on 2006-01-14
thanks for helping.  i hope i'm almost there.

i dont know about any fix.  i followed the steps in the ifrst post of this thread, but used the newest drivers.  I dont' have a file /etc/modprobe.d/ipw2200

here is the output.  Do I have an IP?

bennettg@ubuntu:~$ sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0c:f1:2a:f3:c8
Sending on   LPF/eth1/00:0c:f1:2a:f3:c8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19


Also, most of the time when booting, I seem to get the following error:

modprobe: FATAL: Error inserting ieee80211_crypt_wep (/lib/modules/2.6.12-10-686/net/ieee80211/ieee80211_crypt_wep.ko): unknown symbol in module or unknown parameter (see dmesg)

---

### Post by bennettg on 2006-01-14
RickKnight,

I am so frustrated that I decied to start from the beginning with your HowTo.  I do not know how to erase anything we were working on.  Earlier, I was using the howto posted in the first post on this thread.

I wasnot able to create a folder called /home/share/ipw2200 so I created one called /home/bennettg/share/ipw2200.

I then downloaded the following packages into that directory:
ipw2200, firmaware, ieee80211, nocast patch, and wpa_supplicant source from the links on your post #503 on this thread.  As per your Howto, I did the following at the terminal and got the error in the last line

bennettg@ubuntu:~/Share/ipw2200$ tar zxpvf ieee80211-1.1.8.tgz
ieee80211-1.1.8/
ieee80211-1.1.8/GIT_SHA1
ieee80211-1.1.8/in-tree/
ieee80211-1.1.8/in-tree/Makefile
ieee80211-1.1.8/in-tree/Kconfig
ieee80211-1.1.8/ieee80211_crypt.c
ieee80211-1.1.8/ieee80211_crypt_ccmp.c
ieee80211-1.1.8/ieee80211_crypt_tkip.c
ieee80211-1.1.8/ieee80211_crypt_wep.c
ieee80211-1.1.8/ieee80211_geo.c
ieee80211-1.1.8/ieee80211_module.c
ieee80211-1.1.8/ieee80211_rx.c
ieee80211-1.1.8/ieee80211_tx.c
ieee80211-1.1.8/ieee80211_wx.c
ieee80211-1.1.8/net/
ieee80211-1.1.8/net/ieee80211.h
ieee80211-1.1.8/net/ieee80211_crypt.h
ieee80211-1.1.8/net/ieee80211_radiotap.h
ieee80211-1.1.8/LICENSE
ieee80211-1.1.8/CHANGES
ieee80211-1.1.8/INSTALL
ieee80211-1.1.8/Makefile
ieee80211-1.1.8/idvals
ieee80211-1.1.8/remove-old
bennettg@ubuntu:~/Share/ipw2200$ tar zxpvf ipw2200-1.0.10.tgz
ipw2200-1.0.10/
ipw2200-1.0.10/GIT_SHA1
ipw2200-1.0.10/ipw2200.c
ipw2200-1.0.10/ipw2200.h
ipw2200-1.0.10/LICENSE
ipw2200-1.0.10/CHANGES
ipw2200-1.0.10/FILES
ipw2200-1.0.10/ISSUES
ipw2200-1.0.10/Makefile
ipw2200-1.0.10/dvals
ipw2200-1.0.10/idvals
ipw2200-1.0.10/load
ipw2200-1.0.10/unload
ipw2200-1.0.10/status
ipw2200-1.0.10/config
ipw2200-1.0.10/restart
ipw2200-1.0.10/verify_wifi_hw
ipw2200-1.0.10/remove-old
ipw2200-1.0.10/README.ipw2200
ipw2200-1.0.10/INSTALL
bennettg@ubuntu:~/Share/ipw2200$ tar ipw2200-fw-2.4.tgz
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
bennettg@ubuntu:~/Share/ipw2200$  

Maybe starting from here will help.  Is there supposed to be a tar zxpvf before the ipw2200-fw-2.4.tgz in the last command above (the one which cased the error)??

---

### Post by RickKnight on 2006-01-14
[QUOTE=bennettg]
modprobe: FATAL: Error inserting ieee80211_crypt_wep (/lib/modules/2.6.12-10-686/net/ieee80211/ieee80211_crypt_wep.ko): unknown symbol in module or unknown parameter (see dmesg)[/QUOTE]
This may well be part of the problem. If ieee80211 isn't loading properly, WPA and WEP won't work. What ieee80211 modules do you have loaded?```
sudo lsmod | grep ieee802
```
Rick Knight

---

### Post by RickKnight on 2006-01-14
[QUOTE=bennettg]
bennettg@ubuntu:~/Share/ipw2200$ tar ipw2200-fw-2.4.tgz
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
[/QUOTE]
The command should be ```
tar zxpvf ipw2200-fw-2.4.tgz
```
Also, in```
Now, build wpa_supplicant.
Code:

cd /home/share/ipw2200 tar zxpvfwpa_supplicant-0.4.7.tar.gz cd wpa_supplicant-0.4.7

Copy this code to .config in /home/share/ipw2200/wpa_supplicant-0.4.7/
Code:

CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_MD5=y
CONFIG_EAP_MSCHAPV2=y
CONFIG_EAP_TLS=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TTLS=y
#CONFIG_EAP_GTC=y
#CONFIG_EAP_OTP=y
#CONFIG_EAP_SIM=y
#CONFIG_EAP_AKA=y
CONFIG_EAP_PSK=y
#CONFIG_EAP_PAX=y
CONFIG_EAP_LEAP=y
CONFIG_WIRELESS_EXTENSION=y
#CONFIG_DRIVER_HOSTAP=y
#CONFIG_DRIVER_HERMES=y
#CONFIG_DRIVER_MADWIFI=y
#CFLAGS += -I../madwifi
#CONFIG_DRIVER_ATMEL=y
CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_NDISWRAPPER=y
#CONFIG_DRIVER_BROADCOM=y
CONFIG_DRIVER_IPW=y

Enable additional drivers you may need, madwifi for example, by removing the # from the front of that particular line.
Code:

sudo make sudo cp wpa_supplicant /usr/local/bin cp wpa_cli /usr/local/bin

```right after "CONFIG_DRIVER_IPW=y" add ```
CONFIG_CTRL_IFACE=y
```Before you build wpa_supplicant.

Rick Knight

---

### Post by RickKnight on 2006-01-14
Bennettg,

Adding ```
CONFIG_CTRL_IFACE=y
```
will allow you to use ```
control_interface=/var/run/wpa_supplicant
control_interface_group=sudo
```in your /etc/wpa_supplicant.conf file. That, in turn will allow you to run wpa_cli and wpa_gui.

Rick Knight

---

### Post by bennettg on 2006-01-14
[QUOTE=RickKnight]This may well be part of the problem. If ieee80211 isn't loading properly, WPA and WEP won't work. What ieee80211 modules do you have loaded?```
sudo lsmod | grep ieee802
```
Rick Knight[/QUOTE]

bennettg@ubuntu:/$ sudo lsmod | grep ieee802
Password:
ieee80211              29380  1 ipw2100
ieee80211_crypt         5604  2 ipw2100,ieee80211
bennettg@ubuntu:/$

---

### Post by bennettg on 2006-01-14
[QUOTE=RickKnight]The command should be ```
tar zxpvf ipw2200-fw-2.4.tgz
```
Also, in```
Now, build wpa_supplicant.
Code:

cd /home/share/ipw2200 tar zxpvfwpa_supplicant-0.4.7.tar.gz cd wpa_supplicant-0.4.7

Copy this code to .config in /home/share/ipw2200/wpa_supplicant-0.4.7/
Code:

CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_MD5=y
CONFIG_EAP_MSCHAPV2=y
CONFIG_EAP_TLS=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TTLS=y
#CONFIG_EAP_GTC=y
#CONFIG_EAP_OTP=y
#CONFIG_EAP_SIM=y
#CONFIG_EAP_AKA=y
CONFIG_EAP_PSK=y
#CONFIG_EAP_PAX=y
CONFIG_EAP_LEAP=y
CONFIG_WIRELESS_EXTENSION=y
#CONFIG_DRIVER_HOSTAP=y
#CONFIG_DRIVER_HERMES=y
#CONFIG_DRIVER_MADWIFI=y
#CFLAGS += -I../madwifi
#CONFIG_DRIVER_ATMEL=y
CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_NDISWRAPPER=y
#CONFIG_DRIVER_BROADCOM=y
CONFIG_DRIVER_IPW=y

Enable additional drivers you may need, madwifi for example, by removing the # from the front of that particular line.
Code:

sudo make sudo cp wpa_supplicant /usr/local/bin cp wpa_cli /usr/local/bin

```right after "CONFIG_DRIVER_IPW=y" add ```
CONFIG_CTRL_IFACE=y
```Before you build wpa_supplicant.

Rick Knight[/QUOTE]

Still an error:

bennettg@ubuntu:~/Share/ipw2200$ tar zxpvf ipw2200-fw-2.4.tgz
LICENSE
ipw-2.4-boot.fw
ipw-2.4-bss.fw
ipw-2.4-bss_ucode.fw
ipw-2.4-ibss.fw
ipw-2.4-ibss_ucode.fw
ipw-2.4-sniffer.fw
ipw-2.4-sniffer_ucode.fw
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-fw* /usr/lib/hotplug//firmware
cp: cannot stat `ipw-fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-fw* /usr/lib/hotplug/firmware
cp: cannot stat `ipw-fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$ 

I am sorry this is not working and truly appreciate your help.

---

### Post by RickKnight on 2006-01-14
Bennettg,

```
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-fw* /usr/lib/hotplug//firmware
cp: cannot stat `ipw-fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-fw* /usr/lib/hotplug/firmware
cp: cannot stat `ipw-fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$

```

Try ```
sudo cp ipw-2.4.fw*
```This may have been a typo in my instructions. I'll check and correct.

Rick Knight

---

### Post by bennettg on 2006-01-14
[QUOTE=RickKnight]Bennettg,

```
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-fw* /usr/lib/hotplug//firmware
cp: cannot stat `ipw-fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-fw* /usr/lib/hotplug/firmware
cp: cannot stat `ipw-fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$

```

Try ```
sudo cp ipw-2.4.fw*
```This may have been a typo in my instructions. I'll check and correct.

Rick Knight[/QUOTE]


Rick,

No luck.

bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-2.4.fw* /usr/lib/hotplug//firmware
Password:
cp: cannot stat `ipw-2.4.fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-2.4.fw* /usr/lib/hotplug/firmware
cp: cannot stat `ipw-2.4.fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$ 

Again, I am very grateful for your help.

---

### Post by RickKnight on 2006-01-14
Bennettg,

Verify that the files exist and you're in the right directory.
```
pwd
lsipw-2.4-fw*
```

---

### Post by RickKnight on 2006-01-14
Oops, Make that```
pwd
ls ipw-2.4-fw*
```

---

### Post by RickKnight on 2006-01-14
I just looked back at my original posting and I see more than a few typos. I'll try to correct those off-line and then repost.

Rick Knight

---

### Post by RickKnight on 2006-01-14
Bennettg,

I've just made some corrections and a couple of additions to my HOWTO post. Your cut and pastes should work now.

Rick Knight

---

### Post by bennettg on 2006-01-15
The line in your post that should copy the firmware to the porper directory...

bennettg@ubuntu:~$ cd /home/bennettg/Share/ipw2200
bennettg@ubuntu:~/Share/ipw2200$ sudo cp ipw-2.4-fw* /usr/lib/hotplug/firmware
Password:
cp: cannot stat `ipw-2.4-fw*': No such file or directory
bennettg@ubuntu:~/Share/ipw2200$

Still is not working.

Is there anything this nOOb can do to help?  Do you have a project that I can donate to?  Thank you for your continued patience and support

---

### Post by bennettg on 2006-01-15
Also, there is not a file called .config in /home/share/ipw2200/wpa_supplicant-0.4.7   (I even looked for hidden files)

In you HowTO where you call for:

Copy this code to .config in /home/share/ipw2200/wpa_supplicant-0.4.7/
Code:

CONFIG_IEEE8021X_EAPOL=y CONFIG_EAP_MD5=y CONFIG_EAP_MSCHAPV2=y CONFIG_EAP_TLS=y CONFIG_EAP_PEAP=y CONFIG_EAP_TTLS=y #CONFIG_EAP_GTC=y #CONFIG_EAP_OTP=y #CONFIG_EAP_SIM=y #CONFIG_EAP_AKA=y CONFIG_EAP_PSK=y #CONFIG_EAP_PAX=y CONFIG_EAP_LEAP=y CONFIG_WIRELESS_EXTENSION=y #CONFIG_DRIVER_HOSTAP=y #CONFIG_DRIVER_HERMES=y #CONFIG_DRIVER_MADWIFI=y #CFLAGS += -I../madwifi #CONFIG_DRIVER_ATMEL=y CONFIG_DRIVER_WEXT=y CONFIG_DRIVER_NDISWRAPPER=y #CONFIG_DRIVER_BROADCOM=y CONFIG_DRIVER_IPW=y CONFIG_CTRL_IFACE=y

---

### Post by bennettg on 2006-01-15
Rick,

I may be closer.  Since last night, I stopped everything, deleted all files ipw2200.ko and ieee80211*.ko and started from scratch with luca_linux's how to in post 1 of this thread.

I followed his instructions step by step (only substitutiing newer versions of drivers and firmware).  I did not encounter any errors when installing.

However, the wireless is nto working.  when booting it hangs with networking.  

prior to using wpa, i had configured wep through the kde gui system settings.  those setting are still there and I cannot remove them.  Is there a conflict here?

I also took luca_linux's advice and modified my /etc/wpa_supplicant.conf file as follows (this is it's current state):

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="acorn"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="24334B4A44412423486A736B61"
}


The following terminal outputs are form commands that luca_linux says to do.  I dont understand what it means, but maybe you or someone else can help.  this is the last thing I need to configure and then I am deleting Windows from my partition.  Bye Bye M$!


bennettg@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     61 63 6f 72 6e                                    acorn
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='acorn'
Daemonize..
bennettg@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     61 63 6f 72 6e                                    acorn
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='acorn'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:0c:f1:2a:f3:c8
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
wpa_driver_ipw_set_wpa: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=0
wpa_driver_ipw_set_countermeasures: enabled=0
No keys have been configured - skip key clearing

---

### Post by RickKnight on 2006-01-15
Bennettg,

```
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

```I found this near the end of your last message. To do what it suggests,```
sudo rm -f /var/run/wpa_supplicant/eth1
```And try to start wpa_supplicant again and see what happens.

Rick Knight

---

### Post by Fragma on 2006-01-15
Hey everyone, I seriously need some help here.

I went through the entire guide with the help of all these replies. However, after installing the ipw2200 driver, my card still isn't detected. I tried the lsmod command but nothing comes up. The wifi light is not on either, I'm pretty sure I installed everything correctly. Does anything need to be enabled in order for this to work? :confused: 

My ethernet works fine but my wireless is still down. 


Please help! 

Thanks

---

### Post by bennettg on 2006-01-16
Rick (or anyone kinf enough to help),


I am soooo close.  I wiped my hard drive and did a fresh install of kubuntu/ubuntu.  I followed luca_linux's instructions in post 1 of this thread.  Upon rebooting, I was connected!!!!  The speed was much slower than in windows with wpa or in kubuntu with wep, but I was pleased.  

However, since that time, I have only been able to connect wirelessly 1 out of 7 times.  I wonder if it is something in my /etc/wpa_supplicant.conf file.

To help solve this probelm, I will post a picture of the wireless security settings from my router, and my /etc/wpa_supplicant.conf file.  Does it have anything to do with TPIK?  My WPA passphrase in ascii and i do not broadcast my ssid.

[IMG]/home/bennettg/Desktop/snapshot1.png[/IMG]

see attached snapshot		
				




Here is my etc/wpa_supplicant.conf:


# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid=""
        key_mgmt=NONE
}

ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="acorn"
       scan_ssid=1
       psk="24334B4A44412423486A736B61"
       priority=2
}


Thank you so very much for your assistance.  If I can just get this to connect reliabily, I will delete windoze from my partitions.  Bye Bye M$ and Bill Gates

---

### Post by RickKnight on 2006-01-16
Bennettg,

I notice you didn't pot key management and proto in your wpa_supplicant.conf. You might try adding them.
```
proto = WPA
key_mgmt = WPA-PSK
```They go in the 'network' stanza.

Good luck,
Rick Knight

---

### Post by bennettg on 2006-01-16
[QUOTE=RickKnight]Bennettg,

I notice you didn't pot key management and proto in your wpa_supplicant.conf. You might try adding them.
```
proto = WPA
key_mgmt = WPA-PSK
```They go in the 'network' stanza.

Good luck,
Rick Knight[/QUOTE]

Does it matter if I am using a ascii passphrase (i.e. 8-63 characters) as opposed to a hexadecimal (64 characters)?  I tried to use the examples in the /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz file.

Why would I have been able to connect sporadically with the current /etc/wpa_supplicant.conf?

---

### Post by linux_newbie on 2006-01-16
Hi, 

I am not so expert in using linux. I am currently using Kubuntu Breezy. I followed all the steps in the How-To and got the wireless interface up and running and I could see my access point but the problem is that I am not getting an ip address and hence i am not able to connect.

Has anyone seen this problem before. I would be very grateful if somebody tells me what did I do wrong and what I need to do.

Thanks,

---

### Post by bennettg on 2006-01-17
[QUOTE=bennettg]Does it matter if I am using a ascii passphrase (i.e. 8-63 characters) as opposed to a hexadecimal (64 characters)?  I tried to use the examples in the /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz file.

Why would I have been able to connect sporadically with the current /etc/wpa_supplicant.conf?[/QUOTE]


PLEASE HELP ME

---

### Post by RickKnight on 2006-01-18
Bennettg,

I don't know why your getting the sporadic connection, but I don't think the ascii passphrase is the culprit, allthough you'll want to change the passphrase to something more secure when you get things working.

Luca_linux' HOWTO worked great for me with Hoary (Kubuntu-5.04) but not with  Breezy, so when I did finally get my wireless working with Breezy I posted the steps here. Go back through Luca_linux' howto and look at what I've added or changed . If you have a problem with any one step, post back here and I'll try to help. Also, you can find a lot of help, including an occaisional developer on irc channels #ipw2100 and #ipw2200 at freenode.net.

Good Luck
Rick Knight

---

### Post by srijith on 2006-01-19
I recently tried to compile the drivers for the 2.6.10-6 kernel and found that using the 2.4 firmware hangs the bootup at the hotplug level. Using 2.3 firmware got the whole thing to work fine.

HP nc6120, Ubuntu Hoary.

---

### Post by mxr on 2006-01-20
probably this has been posted before but the thread is just too big to go through. and when i searched for dns related issues no one was addressed (at least not the identical ones that i have).

i know this is a howto about gettin ipw2200 to work with wpa but there are some issues... at work i have wpa personal and following configuration:

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
        ssid="Work Network"
        key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="workkey"
}

it works! at home i have wpa2 personal. guess what - same config works - i can connect to AP and get an IP and the DNS servers in my /etc/resolv.conf

now - here is the trick! at home, DNS resolution does not work - i can access stuff only via IPs.

noticed a difference - at home (WPA2), my resolv.conf has 3 outside DNS servers (that I can ping by both IP and hostname). but at work my resolv.conf has search workdomain.com and a local (192.168.x.x) DNS server.

first i was thinking that this is WPA and WPA2 issue. changed at home to WPA. still no luck. but now i am thinking that there is something with those DNS servers and it does matter if its a 192.168.x.x or an outside one. btw i have a Linksys wrt54gs v4 at home (where i have the DNS issues).

---

### Post by iansyngin on 2006-01-20
Has anyone seen the following.
I'm following the guide for installing wifi drivers: ipw2200 and ieee
when i run the command

sudo make 

i recieve the following error:

/tmp/wifi/ieee80211-1.1.9$ sudo make
Password:
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...
make -C /lib/modules/2.6.12-10-386/build M=/tmp/wifi/ieee80211-1.1.9 MODVERDIR=/tmp/wifi/ieee80211-1.1.9 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /tmp/wifi/ieee80211-1.1.9/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/tmp/wifi/ieee80211-1.1.9/ieee80211_module.o] Error 127
make[1]: *** [_module_/tmp/wifi/ieee80211-1.1.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2


has anyone any ideas?

---

### Post by iansyngin on 2006-01-20
found answer to this:
i needed to install gcc 3.4 and removed other version. worked fine after that.
the latest version of gcc incompatible with the document

---

### Post by mxr on 2006-01-21
Problem solved. The issue was, well I would not say in the router but partially. The thing is that in my Linksys you can set under DHCP server DNS addresses and you can leave 0.0.0.0. In both cases they get into /etc/resolv.conf but with defined IPs it did not work for me. So I replaced them with 0.0.0.0 and now it rocks!

[QUOTE=mxr]probably this has been posted before but the thread is just too big to go through. and when i searched for dns related issues no one was addressed (at least not the identical ones that i have).

i know this is a howto about gettin ipw2200 to work with wpa but there are some issues... at work i have wpa personal and following configuration:

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
        ssid="Work Network"
        key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="workkey"
}

it works! at home i have wpa2 personal. guess what - same config works - i can connect to AP and get an IP and the DNS servers in my /etc/resolv.conf

now - here is the trick! at home, DNS resolution does not work - i can access stuff only via IPs.

noticed a difference - at home (WPA2), my resolv.conf has 3 outside DNS servers (that I can ping by both IP and hostname). but at work my resolv.conf has search workdomain.com and a local (192.168.x.x) DNS server.

first i was thinking that this is WPA and WPA2 issue. changed at home to WPA. still no luck. but now i am thinking that there is something with those DNS servers and it does matter if its a 192.168.x.x or an outside one. btw i have a Linksys wrt54gs v4 at home (where i have the DNS issues).[/QUOTE]

---

### Post by bennettg on 2006-01-23
[QUOTE=RickKnight]Bennettg,

I don't know why your getting the sporadic connection, but I don't think the ascii passphrase is the culprit, allthough you'll want to change the passphrase to something more secure when you get things working.

Luca_linux' HOWTO worked great for me with Hoary (Kubuntu-5.04) but not with  Breezy, so when I did finally get my wireless working with Breezy I posted the steps here. Go back through Luca_linux' howto and look at what I've added or changed . If you have a problem with any one step, post back here and I'll try to help. Also, you can find a lot of help, including an occaisional developer on irc channels #ipw2100 and #ipw2200 at freenode.net.

Good Luck
Rick Knight[/QUOTE]


Rick,

I've got it working well, though I don't know exactly how.  It still drops occasionally, so I wonder if that is a signal issue or somehting on my laptop.

I followed luca_linux's how to and it didnt work.  I then changed what luca_linux had for his script and replaced it with yours.  It still didn;t work, until I changed the loading to S43 from S40.

relevant files are attached.  I have chenged the security settings from what you see here (and what was posted earlier) for security.

/etc/rcS.d:
bennettg@ubuntu:~$ sudo kate /etc/init.d/wifi_wpa.sh

#! /bin/sh
# wifi: wpa_supplicant init
echo " * [Wifi]: Enabling WPA supplicant..."
if [ -x /usr/local/bin/wpa_supplicant ]; then
 /usr/local/bin/wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dipw -w &
fi

sleep 2

#use dhcp to request a network address
dhclient eth1

exit 0

bennettg@ubuntu:~$ sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/S43netwifiwpa




/etc/wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="acorn"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP
    psk="24334B4A44412423486A736B61"
}


I don't know why, but it works and I'm not touching it.  So in summary I followed luca_linux's how to word for word throughout, failed to get it started and then used the portions of your howto above (the start-up script) and changed its symlink to s43.

does this make sense to you?  I am writing the details here in case someone else has this problem or in case i do in the future.  maybe you understand what happened more than me and can add the caveats to your howto!

thanks for all your help.  let me know if you have an open source project i can donate to

---

### Post by Robor on 2006-01-23
I wasn't trying to enable WPA but I had an occasional loss of wireless connectivity and I was getting an error in my logs about firmware.  A Google search hit this thread.  

I figured, I don't want WPA but it looks like I can upgrade my firmware and ieee80211 subsystem and hope that fixes my problems.   Well, I went through the process and it broke my wireless.  On reboot my wireless (Eth1) doesn't show up and if I double click my 'Network Connection' icon I get a "No such device" error.  I repeated the process to no avail.

---

### Post by Robor on 2006-01-23
[QUOTE=Robor]I wasn't trying to enable WPA but I had an occasional loss of wireless connectivity and I was getting an error in my logs about firmware.  A Google search hit this thread.  

I figured, I don't want WPA but it looks like I can upgrade my firmware and ieee80211 subsystem and hope that fixes my problems.   Well, I went through the process and it broke my wireless.  On reboot my wireless (Eth1) doesn't show up and if I double click my 'Network Connection' icon I get a "No such device" error.  I repeated the process to no avail.[/QUOTE]

Well, after some hair pulling and trial and troubleshooting I managed to get it working.  A 'dmesg' had a spew of errors for iee80211 so I repeated the process using ieee80211-1.1.8 instead of ieee80211-1.1.9.  I used the process here...  

[http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)

It appears to be very similar to the initial post so it probably was just using the 1.1.8 instead of 1.1.9.  Just thought I'd mention it.

---

### Post by RickKnight on 2006-01-23
Bennettg,

Glad you've got it working.

Luca_linux's howto is a good, accurate howto, the problems with wifi on breezy seem to be due to cjanges the debian folks made to things like wpasupplicant. In my howto, I try to address those changes. Also, startup order can be critical. SOme things just need to be loaded before others. The main thing is, you got it working! If the occaisional drops become a problem, take a look at the ipw2200 developers forum. It seems to be a pretty common proble.

Rick Knight

---

### Post by gidkill on 2006-01-25
Does installing the firmware actually update anything on the hardware itself, such as a flash ROM? And if so, is the firmware compat with Windows?

Just curious. Perhaps I'm missing something obvious here.

---

### Post by gidkill on 2006-01-25
Apparently I'm struggling with something more fundamental. I can't get past this:

root@lucky:/var/tmp/ipw2200/ieee80211-1.1.8# make install
make -C /lib/modules/2.6.12-10-386/build M=/var/tmp/ipw2200/ieee80211-1.1.8 MODVERDIR=/var/tmp/ipw2200/ieee80211-1.1.8 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2


Help?

Thanks,

Gidkill

---

### Post by e-blade on 2006-01-27
i've seen a lot ppl asking the same question but noone seems to give the answer. After having followed the guide and trying to make the ieee80211 file i get the:

Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

find: /lib/modules/2.6.12-10-386/build/: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.12-10-386/build M=/home/<myname>/tmp/ieee/ieee80211-1.0.3 MODVERDIR=/home/<myname>/tmp/ieee/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory. Stop.
make: *** [modules] Error 2

I do confess to being a ubuntu/linux noob but i am hoping someone can hekp me get rid of the problem.

Thanks for all the help upfront.

---

### Post by e-blade on 2006-01-28
I solved the "problem". More a lack of brain activity. The reason why ppl get the 'make' error following this guide is because the linus-header files doesnt match your kernel version. In my case i searched repositories/google and found the linux-headers-2.6.12-10_2.6.12-10.26_i386.deb and linux-headers-2.6.12-10-386_2.6.12-10.26_i386. 

It will solve your problem as long as your headers match the kernel version. Also note that the first file i listed above has to be installed first.
In case you dont know how to install debian files, open your terminal window and type:

sudo dpkg -i package_file.deb

---

### Post by azuro on 2006-01-30
[QUOTE=juicewvu]when trying to follow this tutorial i recieve the following error(s) when trying to compile the ipw2200 driver:

```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I tried making the /lib/modules/2.6.10-5-386/build directory as it infact does not exist, after which I recieve the following error(s):
```

make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2

```
I'm kind of stuck here, do i need to copy the source files to the /lib/modules/2.6.10-5-386/build directory before trying to compile?


-Juice[/QUOTE]


I got the same problem here.  I've installed the linux-header.  Now, how do I make the symlink??  Thanks

---

### Post by luca_linux on 2006-02-01
Hi guys.
Sorry, I haven't been on the forum for awhile, a long while. :P
Now I am.
I think I'll update my HowTo within the next 2 days.
Anyway, here's a tip: if you want to get ipw2200 and WPA to work on a system running kernel >= 2.6.13, you'll need to change the driver interface in wpa_supplicant from "ipw" to "wext".

---

### Post by keldrum on 2006-02-01
Hi All,

I'm stepping through Luca's how to but I'm having trouble when it comes to the ieee80211-1.0.3 make process & it exits with error2 (see below). It seems that it may be related to the make command getting an incorrect gcc number. 

I'm running:
Ubuntu Breezy 5.10 - 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 GNU/Linux

Here is the error I'm receiving during the "make":
```
keldrum@k9:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...
make -C /lib/modules/2.6.12-10-386/build M=/home/keldrum/ieee80211-1.0.3 MODVERDIR=/home/keldrum/ieee80211-1.0.3 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/keldrum/ieee80211-1.0.3/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/keldrum/ieee80211-1.0.3/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/keldrum/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
```

It looks to me (in my very limited knowledge) like it's giving the wrong gcc version number during this section:

```
/usr/src/linux-headers-2.6.12-1-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
```

I tried running that script individually and it reports an error on exit:
```
keldrum@k9:/usr/src/linux-headers-2.6.12-10-386/scripts$ sh gcc-version.sh
gcc-version.sh: line 11: -E: command not found
gcc-version.sh: line 12: -E: command not found
0000
```

I checked in synaptic and it reports gcc as version# 4:4.0.1-3 (breezy). Should I try the newest versions of the ieee80211 subsystem and ipw2200 driver? I though that sticking to the versions numbers listed in the how to may avoid some potential problems.

I would appreciate any ideas.

Thanks!

---

### Post by drpolish on 2006-02-04
i can't 'make' ieee80211. im on my desktop/ieee80211/ and cant use 'make'
my error report is:
```
Checking in /lib/modules/2.6.12-10-686/build/ for ieee80211 components...

CONFIG_IEEE80211=m
CONFIG_IEEE80211_CRYPT=m
CONFIG_IEEE80211_WPA=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
Above definitions found.  Comment out? [y], n n
make -C /lib/modules/2.6.12-10-686/build M=/home/thomas/Desktop/ieee80211-1.0.3 MODVERDIR=/home/thomas/Desktop/ieee80211-1.0.3 modules
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/thomas/Desktop/ieee80211-1.0.3/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/thomas/Desktop/ieee80211-1.0.3/ieee80211_module.o] Error 127make[1]: *** [_module_/home/thomas/Desktop/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [modules] Error 2

```

---

### Post by willin on 2006-02-04
[QUOTE=keldrum]Hi All,

I'm stepping through Luca's how to but I'm having trouble when it comes to the ieee80211-1.0.3 make process & it exits with error2 (see below). It seems that it may be related to the make command getting an incorrect gcc number. 

I'm running:
Ubuntu Breezy 5.10 - 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 GNU/Linux

Here is the error I'm receiving during the "make":
```
keldrum@k9:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...
make -C /lib/modules/2.6.12-10-386/build M=/home/keldrum/ieee80211-1.0.3 MODVERDIR=/home/keldrum/ieee80211-1.0.3 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/keldrum/ieee80211-1.0.3/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/keldrum/ieee80211-1.0.3/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/keldrum/ieee80211-1.0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
```

It looks to me (in my very limited knowledge) like it's giving the wrong gcc version number during this section:

```
/usr/src/linux-headers-2.6.12-1-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
```

I tried running that script individually and it reports an error on exit:
```
keldrum@k9:/usr/src/linux-headers-2.6.12-10-386/scripts$ sh gcc-version.sh
gcc-version.sh: line 11: -E: command not found
gcc-version.sh: line 12: -E: command not found
0000
```

I checked in synaptic and it reports gcc as version# 4:4.0.1-3 (breezy). Should I try the newest versions of the ieee80211 subsystem and ipw2200 driver? I though that sticking to the versions numbers listed in the how to may avoid some potential problems.

I would appreciate any ideas.

Thanks![/QUOTE]

I had this same problem.  I just installed the version of gcc it used and it seemed to fix the problem:

```

sudo apt-get install gcc-3.4

```

Hope it helps.

---

### Post by gidkill on 2006-02-05
This is so frustrating. So, I have Breezy. I have all the prerequisites that have been mentioned so far, and a number that have not: build-essentials, the headers, gcc 3.4, open ssl. I am following Rick Knight's instructions. I get no errors when I run make install, but when I try to load the new modules, I get:

root@lucky:/staging/ipw2200-1.0.10# modprobe ieee80211
FATAL: Error inserting ieee80211 (/lib/modules/2.6.12-10-386/net/ieee80211/ieee80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@lucky:/staging/ipw2200-1.0.10# dmesg |grep ieee80211
[4294704.614000] ieee80211_crypt: registered algorithm 'NULL'
[4294704.617000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294704.617000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4296372.769000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[4296678.340000] ieee80211_crypt: registered algorithm 'NULL'
[4296678.357000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4296678.357000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4296678.357000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4296678.357000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4296678.357000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296678.357000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4296678.358000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4296678.358000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4296752.080000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[4296820.365000] ieee80211_crypt: registered algorithm 'NULL'
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4296820.368000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4296820.368000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296820.368000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4296820.368000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4296833.710000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4296833.710000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4296833.710000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4296833.710000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4296833.710000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296833.710000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4296833.711000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4296833.711000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
root@lucky:/staging/ipw2200-1.0.10#

---

### Post by jezjones on 2006-02-06
- > justinflavin, 

not sure if one should go outside of the ubuntu way in order to secure a wifi network???? are you mad?

Unfortunately the thing with linux distros is that they can never be up to date, they are always trying to catch up with the latest drivers and features as they are trying to please the greatest range of hardware.

For an individual who has only one set of hardware to look after, this kind of stepping outside of the distro package system is necessary.

Being able to download and compile your own programs is what linux is about.

---

### Post by pacele on 2006-02-09
[QUOTE=gidkill]This is so frustrating. So, I have Breezy. I have all the prerequisites that have been mentioned so far, and a number that have not: build-essentials, the headers, gcc 3.4, open ssl. I am following Rick Knight's instructions. I get no errors when I run make install, but when I try to load the new modules, I get:

root@lucky:/staging/ipw2200-1.0.10# modprobe ieee80211
FATAL: Error inserting ieee80211 (/lib/modules/2.6.12-10-386/net/ieee80211/ieee80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@lucky:/staging/ipw2200-1.0.10# dmesg |grep ieee80211
[4294704.614000] ieee80211_crypt: registered algorithm 'NULL'
[4294704.617000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294704.617000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4296372.769000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[4296678.340000] ieee80211_crypt: registered algorithm 'NULL'
[4296678.357000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4296678.357000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4296678.357000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4296678.357000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4296678.357000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296678.357000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4296678.358000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4296678.358000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4296752.080000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[4296820.365000] ieee80211_crypt: registered algorithm 'NULL'
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4296820.368000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4296820.368000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296820.368000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4296820.368000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4296820.368000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4296833.710000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4296833.710000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4296833.710000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4296833.710000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4296833.710000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296833.710000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4296833.711000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4296833.711000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
root@lucky:/staging/ipw2200-1.0.10#[/QUOTE]

... got the same problem :-/

---

### Post by JazzSax on 2006-02-09
Hello,
 First time post...long time voyeur. Anywho, I followed luca's howto and now eth1 is nowhere to be found, either with iwconfig or Network Manager.  I started the howto in attempt to configure my Dell Inspiron 9300 with Intel 2915 abg to work on my WPA2 Personal home network. Being a noob, I am not sure on the next plan of attack. How could I undo what was done with the howto. Also where would I go from here to get it configured? 

Thanks

E

---

### Post by psihog on 2006-02-09
Does this work for 5.10? I did a fresh 5.10 install with the server option. I managed to make and install the IEEE80211 by addng gcc-3.4 and manually removing an existing IEEE80211 folder with "sudo rm -ir /lib/modules/2.6.12-9-386/build/include/IEEE80211"

So I went on to make install ipw2200 driver and received the following errors. 

```

......
.........
/home/sho/ipw2200-1.0.7/ipw2200.c: In function `ipw_up':
/home/sho/ipw2200-1.0.7/ipw2200.c:11298: error: structure has no member named `geo'
/home/sho/ipw2200-1.0.7/ipw2200.c: In function `ipw_pci_probe':
/home/sho/ipw2200-1.0.7/ipw2200.c:11600: error: structure has no member named `is_queue_full'
/home/sho/ipw2200-1.0.7/ipw2200.c:11603: error: structure has no member named `handle_probe_response'
/home/sho/ipw2200-1.0.7/ipw2200.c:11604: error: structure has no member named `handle_beacon'
/home/sho/ipw2200-1.0.7/ipw2200.c:11605: error: structure has no member named `handle_assoc_response'
make[2]: *** [/home/sho/ipw2200-1.0.7/ipw2200.o] Error 1
make[1]: *** [_module_/home/sho/ipw2200-1.0.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2

```

My two week linux experience tells me that linux is actually pretty straight forward, but this whole compile driver/kernel from source thing could drive a linux noob insane... I'll wait for your updated howto if you still plan on making it. Thanks

---

### Post by smd on 2006-02-10
> sudhir@sudlap:~/wifi/ieee80211-1.1.11$ sudo make
Checking in /lib/modules/2.6.12-10-386 for ieee80211 components...
make -C /lib/modules/2.6.12-10-386/build M=/home/sudhir/wifi/ieee80211-1.1.11 MODVERDIR=/home/sudhir/wifi/ieee80211-1.1.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/home/sudhir/wifi/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/home/sudhir/wifi/ieee80211-1.1.11/ieee80211.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
sudhir@sudlap:~/wifi/ieee80211-1.1.11$ sudo make install
make -C /lib/modules/2.6.12-10-386/build M=/home/sudhir/wifi/ieee80211-1.1.11 MODVERDIR=/home/sudhir/wifi/ieee80211-1.1.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/home/sudhir/wifi/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/home/sudhir/wifi/ieee80211-1.1.11/ieee80211.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
install -d /lib/modules/2.6.12-10-386/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.12-10-386/net/ieee80211/
install -d `echo /lib/modules/2.6.12-10-386/include | grep "/net\$" || echo /lib/modules/2.6.12-10-386/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.12-10-386/include | grep "/net\$" || echo /lib/modules/2.6.12-10-386/include/net`
mkdir -p /lib/modules/2.6.12-10-386/net/ieee80211//.tmp_versions
install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.12-10-386/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.12-10-386
WARNING: Loop detected: /lib/modules/2.6.12-10-386/net/ieee80211/ieee80211.ko which needs ieee80211.ko again!
WARNING: Module /lib/modules/2.6.12-10-386/net/ieee80211/ieee80211.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ipw2200.ko ignored, due to loop
sudhir@sudlap:~/wifi/ieee80211-1.1.11$


this is error I got while making it :(

---

### Post by aktizol on 2006-02-12
[COLOR="DarkRed"]Firstly I had this error:[/COLOR]

> aktizol@ubuntu:~/ieee80211-1.1.11$ make
Checking in /lib/modules/2.6.12-10-686 for ieee80211 components...
make -C /lib/modules/2.6.12-10-686/build M=/home/aktizol/ieee80211-1.1.11 MODVERDIR=/home/aktizol/ieee80211-1.1.11 modules
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/aktizol/ieee80211-1.1.11/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/aktizol/ieee80211-1.1.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [modules] Error 2
aktizol@ubuntu:~/ieee80211-1.1.11$ sudo make install
make -C /lib/modules/2.6.12-10-686/build M=/home/aktizol/ieee80211-1.1.11 MODVERDIR=/home/aktizol/ieee80211-1.1.11 modules
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/aktizol/ieee80211-1.1.11/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/aktizol/ieee80211-1.1.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [modules] Error 2
aktizol@ubuntu:~/ieee80211-1.1.11$ make
Checking in /lib/modules/2.6.12-10-686 for ieee80211 components...
make -C /lib/modules/2.6.12-10-686/build M=/home/aktizol/ieee80211-1.1.11 MODVERDIR=/home/aktizol/ieee80211-1.1.11 modules
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/aktizol/ieee80211-1.1.11/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/aktizol/ieee80211-1.1.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [modules] Error 2

[COLOR="DarkRed"]
then i installed the gcc-3.4:[/COLOR]

> aktizol@ubuntu:~$ sudo apt-get install gcc-3.4
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4 gcc-3.4-base
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2355kB of archives.
After unpacking 8720kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main gcc-3.4-base 3.4.4-6ubuntu8 [163kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main cpp-3.4 3.4.4-6ubuntu8 [1707kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main gcc-3.4 3.4.4-6ubuntu8 [484kB]
Fetched 2355kB in 13s (179kB/s)

Preconfiguring packages ...
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 77777 files and directories currently installed.)
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package cpp-3.4.
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.4-6ubuntu8_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.4-6ubuntu8_i386.deb) ...
Setting up gcc-3.4-base (3.4.4-6ubuntu8) ...
Setting up cpp-3.4 (3.4.4-6ubuntu8) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8) ...


[COLOR="DarkRed"]and now i receive the following error:[/COLOR]

> aktizol@ubuntu:~/ieee80211-1.1.11$ make
Checking in /lib/modules/2.6.12-10-686 for ieee80211 components...
make -C /lib/modules/2.6.12-10-686/build M=/home/aktizol/ieee80211-1.1.11 MODVERDIR=/home/aktizol/ieee80211-1.1.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_module.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_tx.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_rx.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_wx.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_geo.o
  LD [M]  /home/aktizol/ieee80211-1.1.11/ieee80211.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_wep.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_ccmp.o
  CC [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_tkip.o
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
  CC      /home/aktizol/ieee80211-1.1.11/ieee80211.mod.o
  LD [M]  /home/aktizol/ieee80211-1.1.11/ieee80211.ko
  CC      /home/aktizol/ieee80211-1.1.11/ieee80211_crypt.mod.o
  LD [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt.ko
  CC      /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_ccmp.ko
  CC      /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_tkip.ko
  CC      /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_wep.mod.o
  LD [M]  /home/aktizol/ieee80211-1.1.11/ieee80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
aktizol@ubuntu:~/ieee80211-1.1.11$ sudo make install
make -C /lib/modules/2.6.12-10-686/build M=/home/aktizol/ieee80211-1.1.11 MODVERDIR=/home/aktizol/ieee80211-1.1.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
install -d /lib/modules/2.6.12-10-686/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.12-10-686/net/ieee80211/
install -d `echo /lib/modules/2.6.12-10-686/include | grep "/net\$" || echo /lib/modules/2.6.12-10-686/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.12-10-686/include | grep "/net\$" || echo /lib/modules/2.6.12-10-686/include/net`
mkdir -p /lib/modules/2.6.12-10-686/net/ieee80211//.tmp_versions
install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.12-10-686/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.12-10-686
WARNING: Loop detected: /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko which needs ieee80211.ko again!
WARNING: Module /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2100/ipw2100.ko ignored, due to loop

[COLOR="DarkRed"]is there any solution?

thanx, in advance.[/COLOR]

---

### Post by aktizol on 2006-02-12
[COLOR="DarkRed"]and i also get this error for the drivers:[/COLOR]

> aktizol@ubuntu:~/ipw2200-1.0.10$ make
mkdir -p /home/aktizol/ipw2200-1.0.10/tmp/.tmp_versions
cp /lib/modules/2.6.12-10-686/net/ieee80211/.tmp_versions/*.mod /home/aktizol/ipw2200-1.0.10/tmp/.tmp_versions
make -C /lib/modules/2.6.12-10-686/build M=/home/aktizol/ipw2200-1.0.10 MODVERDIR=/home/aktizol/ipw2200-1.0.10/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/aktizol/ipw2200-1.0.10/ipw2200.o
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
  CC      /home/aktizol/ipw2200-1.0.10/ipw2200.mod.o
  LD [M]  /home/aktizol/ipw2200-1.0.10/ipw2200.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
aktizol@ubuntu:~/ipw2200-1.0.10$ sudo make install
mkdir -p /home/aktizol/ipw2200-1.0.10/tmp/.tmp_versions
cp /lib/modules/2.6.12-10-686/net/ieee80211/.tmp_versions/*.mod /home/aktizol/ipw2200-1.0.10/tmp/.tmp_versions
make -C /lib/modules/2.6.12-10-686/build M=/home/aktizol/ipw2200-1.0.10 MODVERDIR=/home/aktizol/ipw2200-1.0.10/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/home/aktizol/ieee80211-1.1.11/ieee80211.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
install -d /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/
install -m 644 -c ipw2200.ko /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.12-10-686
WARNING: Loop detected: /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko which needs ieee80211.ko again!
WARNING: Module /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2100/ipw2100.ko ignored, due to loop
Don't forget to copy firmware to your hotplug's firmware directory and have the
hotplug tools in place.
See INSTALL for more information.


[COLOR="DarkRed"]actually it's a warning so i don't really know if it matters or not..[/COLOR]

---

### Post by wbastien on 2006-02-12
ok I must have screwed something up because now when i type iwlist scan, it doesnt recognize anything, it says it doesnt support scanning. how do i remove everything that  i've done and start over.

---

### Post by aktizol on 2006-02-13
I have read a lot of tutorials (including this one) on how to install DRIVER/FIRMWARE/IEEE80211 for an Intel Pro/Wireless 2200BG card.

I'm using Linux for 2 days now -- so you can consider me as a newbie.

I copied all the parts of the process (that worked for me) from the tuts i have read, and i'm providing it below.

Download: (ipw2200-1.0.10.tgz)(ipw2200-fw-2.4.tgz)(ieee80211-1.1.9.tgz)

> ##### RUN THE SCRIPT IN A SHELL ######

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install gcc-3.4
sudo apt-get install linux-headers-2.6.12-10-686
sudo apt-get install linux-headers-`uname -r`
cd /tmp
mkdir wifi
cd wifi
cp ~/ipw2200-1.0.10.tgz ~/ipw2200-fw-2.4.tgz ~/ieee80211-1.1.9.tgz .
mkdir fw
tar xzvf ipw2200-1.0.10.tgz
tar xzvf ieee80211-1.1.9.tgz
tar xzvf ipw2200-fw-2.4.tgz -C fw/
wget [http://wael.nasreddine.com/files/ubuntu/remove-old](http://wael.nasreddine.com/files/ubuntu/remove-old)
sudo rmmod ipw2200
sudo rmmod ieee80211
sudo rmmod ieee80211_crypt
chmod a+x remove-old
sudo ./remove-old
cd ipw2200-1.0.10
chmod a+x remove-old
sudo ./remove-old
cd ..
cd ieee80211-1.1.9
chmod a+x remove-old
sudo ./remove-old
cd ..
cd ieee80211-1.1.9
make && sudo make install
cd ..
cd ipw2200-1.0.10
make && sudo make install
cd ..
cd fw
sudo cp * /usr/lib/hotplug/firmware
sudo modprobe ipw2200
dmesg | grep ipw

##### RESTART YOUR PC ######

Even though the drivers work fine with me:

[PHP]aktizol@ubuntu:~$ dmesg | grep ipw
[4294704.192000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.10
[4294704.192000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294704.196000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[/PHP]

My eth1 still denied to change to MONITOR MODE!

And this is the error i received :

[PHP]aktizol@ubuntu:~$ iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
SET failed on device eth1 ; Operation not permitted.[/PHP]

Do you have a solution for this?

---

### Post by nikdc5 on 2006-02-13
Hi, when I keep getting this error, and I have no idea how to get round it.

```
nik@niklaptop:~/Desktop/wireless/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

/lib/modules/2.6.12-10-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1
nik@niklaptop:~/Desktop/wireless/ieee80211-1.0.3$ sudo make check_old
Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...

/lib/modules/2.6.12-10-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1

```

I am pretty new to this linux game by the way, and am terribly sorry if this has been brought up already in this thread, there are a lot of pages to look through, and most of what is said is over my head...

---

### Post by aktizol on 2006-02-13
check the script i have above - it will work for you.

it worked for me at least.

---

### Post by woifi on 2006-02-13
hi!

i followed the instructions in the german ubuntu wiki ([http://wiki.ubuntuusers.de/Strom_sparen](http://wiki.ubuntuusers.de/Strom_sparen)) to save power on my laptop. i works great though i have to install new ipw2200 drivers because they don't work any more (i followed the link in the bottom of the wiki page).

well, i downloaded the two ipw and the ieee files and installed them as described. it compiled *without failure messages*.

unfortunately i am not able to load the ipw2200 module:```
 woifi@mojo:/usr/src/linux/net$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg:```
[4298410.573000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4298410.574000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4298410.574000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4298410.574000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4298410.574000] ipw2200: Unknown symbol ieee80211_txb_free
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4298410.574000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4298410.574000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4298410.574000] ipw2200: Unknown symbol escape_essid
[4298410.575000] ipw2200: disagrees about version of symbol ieee80211_rx
[4298410.575000] ipw2200: Unknown symbol ieee80211_rx
[4298410.575000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4298410.575000] ipw2200: Unknown symbol ieee80211_rx_mgt

```

i would really appreciate it it anyone could give me an hint!

bye

woifi

edit:

lsmod says, ieee80211 modules are loaded:
```
ieee80211              27012  0
ieee80211_crypt         5636  1 ieee80211
```

---

### Post by aktizol on 2006-02-13
[QUOTE=woifi]
dmesg:```
[4298410.573000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4298410.574000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4298410.574000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4298410.574000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4298410.574000] ipw2200: Unknown symbol ieee80211_txb_free
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4298410.574000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4298410.574000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4298410.574000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4298410.574000] ipw2200: Unknown symbol escape_essid
[4298410.575000] ipw2200: disagrees about version of symbol ieee80211_rx
[4298410.575000] ipw2200: Unknown symbol ieee80211_rx
[4298410.575000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4298410.575000] ipw2200: Unknown symbol ieee80211_rx_mgt

```

i would really appreciate it it anyone could give me an hint![/QUOTE]
the hint is that you have to read what it says in the INSTALL file!

you will find the solution for the "Unknown symbol"

---

### Post by woifi on 2006-02-14
hi!

i followed the instrucions in the INSTALL file, here is my output:
```
root@mojo:/lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless # for i in ieee80211 ipw2200; do find /lib/modules/`uname -r` -iname ${i}*; done

root@mojo:/lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless # for i in IEEE80211 IPW; do grep CONFIG_${i} /lib/modules/`uname -r`/build/include/linux/autoconf.h; done
/*#define CONFIG_IEEE80211_MODULE 1*/
/*#undef CONFIG_IEEE80211_DEBUG*/
/*#define CONFIG_IEEE80211_CRYPT_MODULE 1*/
/*#define CONFIG_IEEE80211_WPA_MODULE 1*/
/*#define CONFIG_IEEE80211_CRYPT_CCMP_MODULE 1*/
/*#define CONFIG_IEEE80211_CRYPT_TKIP_MODULE 1*/
/*#define CONFIG_IPW2100_MODULE 1*/
/*#undef CONFIG_IPW2100_DEBUG*/
/*#define CONFIG_IPW2100_MONITOR 1*/
/*#define CONFIG_IPW2100_FS_AMILO_M7400_MODULE 1*/
/*#define CONFIG_IPW2200_MODULE 1*/
/*#define CONFIG_IPW2200_MONITOR 1*/
/*#define CONFIG_IPW2200_QOS 1*/
/*#undef CONFIG_IPW2200_DEBUG*/

root@mojo:/lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless # for i in IEEE80211 IPW; do grep CONFIG_${i} /lib/modules/`uname -r`/build/.config; done #CONFIG_IEEE80211=m
# CONFIG_IEEE80211_DEBUG is not set
#CONFIG_IEEE80211_CRYPT=m
#CONFIG_IEEE80211_WPA=m
#CONFIG_IEEE80211_CRYPT_CCMP=m
#CONFIG_IEEE80211_CRYPT_TKIP=m
#CONFIG_IPW2100=m
# CONFIG_IPW2100_DEBUG is not set
#CONFIG_IPW2100_MONITOR=y
#CONFIG_IPW2100_FS_AMILO_M7400=m
#CONFIG_IPW2200=m
#CONFIG_IPW2200_MONITOR=y
#CONFIG_IPW2200_QOS=y
# CONFIG_IPW2200_DEBUG is not set
root@mojo:/lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless #
```

so, everythings seems to be ok - but i still get the failures:
```
root@mojo:/lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless # cd /home/woifi/programs/ieee80211-1.1.9
root@mojo:/home/woifi/programs/ieee80211-1.1.9 # make install
make -C /lib/modules/2.6.12-uservcore/build M=/home/woifi/programs/ieee80211-1.1.9 MODVERDIR=/home/woifi/programs/ieee80211-1.1.9 modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-source-2.6.12«
  Building modules, stage 2.
  MODPOST
make[1]: Verlasse Verzeichnis »/usr/src/linux-source-2.6.12«
install -d /lib/modules/2.6.12-uservcore/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.12-uservcore/net/ieee80211/
install -d `echo /lib/modules/2.6.12-uservcore/include | grep "/net\$" || echo /lib/modules/2.6.12-uservcore/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.12-uservcore/include | grep "/net\$" || echo /lib/modules/2.6.12-uservcore/include/net`
mkdir -p /lib/modules/2.6.12-uservcore/net/ieee80211//.tmp_versions
install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.12-uservcore/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.12-uservcore
root@mojo:/home/woifi/programs/ieee80211-1.1.9 # cd ../ipw/driver/ipw2200-1.0.10
ipw2200-1.0.10/     ipw2200-1.0.10.tgz
root@mojo:/home/woifi/programs/ieee80211-1.1.9 # cd ../ipw/driver/ipw2200-1.0.10

root@mojo:/home/woifi/programs/ipw/driver/ipw2200-1.0.10 # make
mkdir -p /home/woifi/programs/ipw/driver/ipw2200-1.0.10/tmp/.tmp_versions
cp /lib/modules/2.6.12-uservcore/net/ieee80211/.tmp_versions/*.mod /home/woifi/programs/ipw/driver/ipw2200-1.0.10/tmp/.tmp_versions
make -C /lib/modules/2.6.12-uservcore/build M=/home/woifi/programs/ipw/driver/ipw2200-1.0.10 MODVERDIR=/home/woifi/programs/ipw/driver/ipw2200-1.0.10/tmp/.tmp_versions modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-source-2.6.12«
  CC [M]  /home/woifi/programs/ipw/driver/ipw2200-1.0.10/ipw2200.o
  Building modules, stage 2.
  MODPOST
  LD [M]  /home/woifi/programs/ipw/driver/ipw2200-1.0.10/ipw2200.ko
make[1]: Verlasse Verzeichnis »/usr/src/linux-source-2.6.12«

root@mojo:/home/woifi/programs/ipw/driver/ipw2200-1.0.10 # make install
mkdir -p /home/woifi/programs/ipw/driver/ipw2200-1.0.10/tmp/.tmp_versions
cp /lib/modules/2.6.12-uservcore/net/ieee80211/.tmp_versions/*.mod /home/woifi/programs/ipw/driver/ipw2200-1.0.10/tmp/.tmp_versions
make -C /lib/modules/2.6.12-uservcore/build M=/home/woifi/programs/ipw/driver/ipw2200-1.0.10 MODVERDIR=/home/woifi/programs/ipw/driver/ipw2200-1.0.10/tmp/.tmp_versions modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-source-2.6.12«
  Building modules, stage 2.
  MODPOST
make[1]: Verlasse Verzeichnis »/usr/src/linux-source-2.6.12«
install -d /lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless/
install -m 644 -c ipw2200.ko /lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.12-uservcore
Don't forget to copy firmware to your hotplug's firmware directory and have the
hotplug tools in place.
See INSTALL for more information.
root@mojo:/home/woifi/programs/ipw/driver/ipw2200-1.0.10 # ls /usr/lib
lib/   lib64/
root@mojo:/home/woifi/programs/ipw/driver/ipw2200-1.0.10 # ls /usr/lib/hotplug/firmware/
ipw-2.4-boot.fw  ipw-2.4-bss.fw  ipw-2.4-bss_ucode.fw  ipw-2.4-ibss.fw  ipw-2.4-ibss_ucode.fw  ipw-2.4-sniffer.fw  ipw-2.4-sniffer_ucode.fw

[B]root@mojo:/home/woifi/programs/ipw/driver/ipw2200-1.0.10 # modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.12-uservcore/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/B]
```

any more hints? ;)

bye

woifi

---

### Post by aktizol on 2006-02-14
can you please try the commands i have post in this reply: [http://ubuntuforums.org/showpost.php?p=728478&postcount=571](http://ubuntuforums.org/showpost.php?p=728478&postcount=571)

it's a mixture of many tutorials i read - and it works fine for an ipw2220 with kernel 2.6.12

give the commands one by one - so not to miss something.

use the versions i mention in this post.

e.g. i haven't manage to compile the ieee80211-1.1.11.tgz (which is the latest, cause it gives me errors)

but with the ieee80211-1.1.9.tgz it works perfect!

so don't try different versions.

---

### Post by greatbeyond on 2006-02-15
Hey,
1.1.11 compiled for me on Breezy 2.6.12-10 after i applied this patch:

[http://www.bughost.org/bugzilla/show_bug.cgi?id=907](http://www.bughost.org/bugzilla/show_bug.cgi?id=907)

Apparently, it has been merged into the package now, so try downloading again.

Otherwise, i stuck to your script, worked in the end. Thank you.

Cheers
Matthias

---

### Post by aktizol on 2006-02-15
New **ipw2200** & **ieee80211** drivers released to day:

> 2006-Feb-15   	 ipw2200-1.0.11.tgz  	 6b64247500a61313e5a40d82a09a48c4 distros/ipw2200-1.0.11.tgz
2006-Feb-15   	 ieee80211-1.1.12.tgz  	 20da3f23dad2356da8f14d8b3d88d58e distros/ieee80211-1.1.12.tgz

I will give them a try later on.

---

### Post by greatbeyond on 2006-02-15
Hey,
ieee80211-1.1.12 compiles nicely, as expected.

ipw2200-1.0.11 doesn't compile and gives this error:

[PHP]/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c: In function `ipw_wpa_supplicant':
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:6769: Fehler: structure hat kein Element namens »sem«
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:6796: Fehler: structure hat kein Element namens »sem«
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c: In function `ipw_wx_get_range':
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:8991: Fehler: structure hat kein Element namens »enc_capa«
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:8991: Fehler: »IW_ENC_CAPA_WPA« nicht deklariert (erste Benutzung in dieser Funktion)
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:8991: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgeführt
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:8991: Fehler: für jede Funktion in der er auftritt.)
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:8991: Fehler: »IW_ENC_CAPA_WPA2« nicht deklariert (erste Benutzung in dieser Funktion)
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:8992: Fehler: »IW_ENC_CAPA_CIPHER_TKIP« nicht deklariert (erste Benutzung in dieser Funktion)
/home/trac/Desktop/ipw2200-1.0.11/ipw2200.c:8992: Fehler: »IW_ENC_CAPA_CIPHER_CCMP« nicht deklariert (erste Benutzung in dieser Funktion)
make[2]: *** [/home/trac/Desktop/ipw2200-1.0.11/ipw2200.o] Fehler 1
make[1]: *** [_module_/home/trac/Desktop/ipw2200-1.0.11] Fehler 2
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.12-10-386«
make: *** [modules] Fehler 2
root@mobilfaber:/home/trac/Desktop/ipw2200-1.0.11#
[/PHP]

I wanted to install 1.0.11 because it promises to have fixed a WEP authentification bug w/ shared key mode, which i seem to be experiencing (associates a couple of times, then just quits -- iwevent "new access point xx:yy:zz:.." is immediately followed by "new access point 00:00:00:.."), won't re-associate before i set the router to open network and back to WEP -- resetting the router doesn't work. (POS Telekom 1054DSL)

Looking around for a patch or an answer why 1.0.11 won't install..

Greetings
Matthias

---

### Post by aktizol on 2006-02-15
greatbeyond: some compilation error for me also with the drivers 1.0.11

so the latest combination it works is:

(**ipw2200-1.0.10.tgz**)(**ipw2200-fw-2.4.tgz**)(**ieee80211-1.1.12.tgz**)


if anybody found any fix/workaround plz post.

---

### Post by woifi on 2006-02-15
hi!

the drivers work for me fine now (ieee1.1.9 & ipw2200-1.0.10)!
funnily enough i didn't change anything! i was 2 days not at home, started my notebook half an hour ago an look - the module is loaded :D

thx for your help,

bye

woifi

---

### Post by greatbeyond on 2006-02-15
Aktizol:

After what i've figured out the .11 driver expects Wireless Extensions Version >=18, the 2.6.12 kernel in standard Breezy has v17. There are lines in ipw2200.c commented out for pre-18 WExt, but taking them back in produces more errors, apparently a problem of matching wpa_supplicant/driver_ipw.c
I'm far from knowing my way round Linux/C, so it'll have to be left to others to figure out..if you want to see what i'm talking about in ipw2200.c, search for "supplicant" in it.

Greetings
Matthias

---

### Post by cvmostert on 2006-02-17
[QUOTE=meesmany]Hello everybody.
Please forgive my poor Englich.
So i have a Thinkpad T40 with Ubuntu Hoary. It's wonderful.
Ubuntu is for me one of the best distribution and i want to keep it installed.
I had the problem that my wlan only without encryption work "even without wep"
I've tryed this how-to. and i become this.

###########################
jhioui@Thinkpad:~$ sudo dmesg | grep ipw
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.0
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
jhioui@Thinkpad:~$ sudo wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D ipw -w -dd
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=12):
     53 6f 75 66 69 61 6e 65 57 4c 61 6e               meinssid
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=13): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='meinssid'
Daemonize..
########################

but i still have no connection to my router. or i become no ip from my dhcp.
I dont know what to do. What did i wrong??
Please help me solve this. I don't want to use my wlan without encryption.
Thank you All!![/QUOTE]


I have the same wlan card and the breezy live cd works on my machine, so you should be able to get it working.  I also use encryption.... works like a charm... i only have to go to the network settings and activate the card, choose my network and provide the password.

try the live cd, if it works... you should be able to get it working otherwise...
cheers

---

### Post by greatbeyond on 2006-02-17
Hey,
1.0.11 compiled for me as followed:

- Install Kernel Sources 2.6.12
- go to /usr/src/linux-source-2.6.12/include/linux and apply this [patch](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/iw_we18-5.diff) to install Wireless Extensions v18 with the command "patch -p3 wireless.h /whereever/you/put/iw_18-5.diff", you will be asked for the location of of "wireless.c", enter "/usr/src/linux-source-2.6.12/net/core/wireless.c"
- compile, install and boot Kernel (good howto in German here: [click](http://wiki.ubuntuusers.de/Kernel), maybe somebody could link a good english tutorial?)
- install ieee80211-1.1.12 and ipw2200-1.0.11 (compiles nicely now you have Wireless Extensions 18 ;))
- tada :)

Got rid of my problem (mentioned above) nicely. So if your WEP connection works once and never again, try this.

@meesmany:

Are you trying to connect to a WEP network or a WPA network?



Greetings to you all
Matthias

---

### Post by greatbeyond on 2006-02-17
*gnarf*

the ipw2200 project just released 1.0.12 which fixes the "doesn't compile on Kernels with Wireless Extension <18" problem.

Matthias

---

### Post by eedge on 2006-02-20
I have a IntelPro 2100 3b minipci card in my laptop, and my network is completely open.

With the default drivers installed (ipw2100) I can scan and see my OPEN network, but I cannot connect to it as I cannot change to the correct channel - no matter what it gives me the same error (something todo with wrong privilages - yes, I am doing it as root - and something basically saying it is unable to change the frequency: Will post error later when on laptop. Tried the ipw2200 drivers but do not work with card at all.

edit: error on sudo iwconfig set channel 1 is

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device set ; No such device.

but as I said, can scan fine. 



Tried dhclient eth1 (the wlan adapter) with both drivers, as well as configuring manually.

dhclient eth1 returns:
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:04:23:7e:a7:73
Sending on   LPF/eth1/00:04:23:7e:a7:73
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I believe this is probably as I can't set the frequency though.
Intrested to try LATEST ipw2100 driver, but as am a newbie to linux completely unsure how to install it; looking for a guide to do so.

---

### Post by greatbeyond on 2006-02-21
Hey,
"iwconfig set channel 1" gives an error because you didn't specify the interface -- "iwconfig eth1 set channel 1" would be correct. However, there is no need to choose the channel, the driver does that. Just tell the adapter which network to connect to, 

[php]iwconfig eth1 essid "MyNetwork"[/php]

that should already be it. do "iwconfig eth1" to check if you are associated to the network, it should say ESSID="MyNetwork" and "Access Point" should be an address different from 00:00:00:...

If that has worked, you can run dhclient eth1 to obtain an IP and route.

And if that works, i recommend you get GNOME NetworkManager to do all that stuff for you ;)

Hope i could help. If not, ask.

Greetings
Matthias

**Edit:** If this doesn't work, it would be useful if you let "iwevent" run in another terminal while you did this, and post the log here. Also, post the printout of "iwconfig eth1" and "iwlist scan", please.

---

### Post by hibatsu on 2006-02-23
I tried to remove the old ipw2100 and ieee80211, that worked. But when wanting to install the new ieee80211 it failed:

```

root@solanki:/home/hibatsu/ieee80211-1.1.12# make
Checking in /lib/modules/2.6.15-15-386 for ieee80211 components...
make -C /lib/modules/2.6.15-15-386/build M=/home/hibatsu/ieee80211-1.1.12 MODVERDIR=/home/hibatsu/ieee80211-1.1.12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-15-386'
  CC [M]  /home/hibatsu/ieee80211-1.1.12/ieee80211_module.o
/home/hibatsu/ieee80211-1.1.12/ieee80211_module.c: In Funktion »ieee80211_network_reset«:
/home/hibatsu/ieee80211-1.1.12/ieee80211_module.c:90: Fehler: »struct ieee80211_network« hat kein Element namens »ibss_dfs«
/home/hibatsu/ieee80211-1.1.12/ieee80211_module.c:91: Fehler: »struct ieee80211_network« hat kein Element namens »ibss_dfs«
/home/hibatsu/ieee80211-1.1.12/ieee80211_module.c:92: Fehler: »struct ieee80211_network« hat kein Element namens »ibss_dfs«
/home/hibatsu/ieee80211-1.1.12/ieee80211_module.c: In Funktion »ieee80211_networks_free«:
/home/hibatsu/ieee80211-1.1.12/ieee80211_module.c:104: Fehler: »struct ieee80211_network« hat kein Element namens »ibss_dfs«
/home/hibatsu/ieee80211-1.1.12/ieee80211_module.c:105: Fehler: »struct ieee80211_network« hat kein Element namens »ibss_dfs«
make[2]: *** [/home/hibatsu/ieee80211-1.1.12/ieee80211_module.o] Fehler 1
make[1]: *** [_module_/home/hibatsu/ieee80211-1.1.12] Fehler 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-15-386'
make: *** [modules] Fehler 2

```

---

### Post by eedge on 2006-02-23
Sorry, I meant sudo iwconfig eth1 set channel 1...

The correct essid is allready in, I'm starting to think that the card my actually be broken as I can't get the connection to work in xp sp2 with the correct drivers - allthough, once again I can scan for networks :(

---

### Post by Olleo on 2006-02-24
[QUOTE=luca_linux]Hi!
I've seen there are many requests about how to get ipw2200 and wpa to work. So, as I've managed to get them to work, I've decided to write a howto. It's also good if you just want to get ipw2200 without wpa; just follow the first part in this case.[/QUOTE]

Hello,

I've installed the ubuntu hoary hedgehoge version, then upgraded the distribution to breezy. Later on I have followed your instructions.
But I stucked in the beginning: after I have removed the old modules (2x sudo sh remove-old) it occured that:

'Old ieee80211 references found. In order to build the ieee80211 subsystem, prior versions must first be removed. You can perform this task by running this makefile as root via:

% sudo make check_old

and answering Y to remove the file references.

Aborting make .

make: *** [check_old] Error 1"

After I try this sudo make check_old the same message appeares. I saw that you mentioned, that on some systems there are some problems like this and you advice to unload the modules with modprob -r but using 'lsmod' I cannot see any ieee80211* modules. When I try to follow with the installation with 'sudo make install' I get the errors:
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 1: gcc-3.4: command not found'
and a lot of more errors because of that. When I try to execute manually 'gcc-3.4' I also get the command not found, but gcc-4.0 works.

Main problem is that I am green with linux, not mentioning debian so now I'm in big troubles - I have uninstalled the ipw2200 (which worked fine, but without WPA) and now it doesn't work at all. I don't know how to proceed or go back.

Could you please help me in that matter? Thanks in advance.

---

### Post by Olleo on 2006-02-24
Ok nvm. I've managed to get help from my colleague. Now I'm at point of wpa_supplicant... If I have some troubles I will for sure get back to you =)

---

### Post by Olleo on 2006-02-24
[QUOTE=Olleo]Ok nvm. I've managed to get help from my colleague. Now I'm at point of wpa_supplicant... If I have some troubles I will for sure get back to you =)[/QUOTE]
Actually... I have compiled the ipw and ieee with gcc-4.0 =( Now I know it was wrong. But I don't have net access from the ubuntu machine to apt-get the gcc-3.4, so I cannot proceed.

I will try to get connected with eth0 at home, but tell me - how to undo what I have done incorrectly?

---

### Post by Olleo on 2006-02-24
Had some problems with gcc-3.4 but I made it. Now it works. Anyway I got additional question - is there a possibility to have a possibility to choose the wireless network from two (like 1st with wpa-psk and the 2nd completely open) without configuring it manually everytime?

---

### Post by CarbineReloaded on 2006-02-25
I'm having the same problem Olleo had... same exact error msg


I'll freely admit I'm green to linux.... this is my first day running Ubuntu.... I ran FC4 for abot 6 months before I got my new laptop (2200 chipset).

Edit: I currently have NO networking support now on Ubuntu..... tried a hardwire through my router and have zilch...... not feeling too warm and fuzzy right now about this.

---

### Post by CarbineReloaded on 2006-02-25
Alright got past the msg saying that it wasn't an empt directory -- that was fun.....


However any suggestions on how to get Gcc-3.4 onto a laptop that has no internet connection?  I do have a usb jump drive... buti'm at a loss now.

---

### Post by brucetan on 2006-03-03
hi luca_linux or anyone who is familiar with this howto guide, can this guide be used for ubuntu breezy 5.10?  

I just tried to follow it and failed at the "make" & "sudo make install" cmds for both ieee and ipw2200 steps.  

Can someone help me? 

I'm using a Dell Inspiron 6000 with IntelProset 2200BG wireless and I need WPA to interface with a Wifi router.

---

### Post by daynah on 2006-03-03
I'm also with Brucetan and Olleo, can this be used with Breezy? It failed, like Brucetan, at the first "make", saying that there were things that still needed to be deleted, which you had menchioned. I think we're all getting the same error message

I picked ubuntu 'cause it was easy and "breezy badger" sounded friendly. ;) So I'm not particularly the smartest person to pick to figure out how to delete this on my own. Also, will it be okay for me to close this Terminal session and restart it later when I figure out how to fix this?

My wireless not only plain out doesn't work on WPA, but it only works some of the time with WEP (it works at school, but not at home, at school there's no key, so I think that may be the difference). So I'm really hoping this will finally be the thing that fixes it. The first time I tried wpa_supplicant, didn't do a thing.

Thanks! :)

---

### Post by brucetan on 2006-03-04
Hello Matthias and Aktizol, 
I went back to read your posting.  I have a few questions hope you can help to enlighten us.

(1) Are you using ubuntu Breezy 5.10 with this ipw2200BG?
(2) if yes, were you using luca_linux's guide successfully in getting ipw2200+WPA work?
(3) If Aktizol's install script different from luca_linux?
(4) If yes, which one should I use Aktizol or luca_linux's?  for my ubuntu breezy.
(5) Is Aktizol's install scripts using the latest drivers as what Matthias highlighted?

I'm sorry to ask so many questions.  As there are so many people on this thread and had different ways to get it installed and working. I am just new and confused.

Hope both of you be kind enough share with us on the above.

Best regards,

Bruce

---

### Post by brucetan on 2006-03-04
Hi Emerik, 

From your post: [http://www.ubuntuforums.org/showpost.php?p=177833&postcount=89]("http://www.ubuntuforums.org/showpost.php?p=177833&postcount=89")
> So now, 'cause i'm a lazy boy, i decided to automate the install, so i made a script.
I give it for everyone who is interessed in.
You need to be root to execute this script, and remember that you have to edit some vars in the script in order to match your network config.

You can install the latest version of the driver , all you need is to change to variables in the script and put these names of files ipw2200-1.0.4 and ipw2200-fw-2.3 instead of ipw2200-1.0.3 and ipw2200-fw-2.2.

Hope it will help
Attached Files
File Type: gz 	ipw2200_install.sh.gz (1.4 KB, 99 views)

I notice your script is for ubuntu Hoary 5.04.  I am using ubuntu Breezy 5.10.  Do you think you have a equivalent install script for Breezy 5.10?

By the way, I also notice your is different from Luca's.  Can you tell us are they essential achieve the same functions? or the differences?

Many thanks in advance.

---

### Post by brucetan on 2006-03-04
Hello Master$hake,

In your last post : [http://www.ubuntuforums.org/showpost.php?p=536941&postcount=481]("http://www.ubuntuforums.org/showpost.php?p=536941&postcount=481")

> Works great on my Dell 6000 can now connect to my schools network with a little variation of this. Instead of making all these scripts to start wpa I downloaded network selector panel applet so I can choose which network I want to connect to since they all use the same credentials.
Great Job man

Where I can obtain a copy of yr mentioned network selector panel applet?

---

### Post by brucetan on 2006-03-04
Hello e-blade,

In post #556 [http://www.ubuntuforums.org/showpost.php?p=687386&postcount=556]("http://www.ubuntuforums.org/showpost.php?p=687386&postcount=556")
> I solved the "problem". More a lack of brain activity. The reason why ppl get the 'make' error following this guide is because the linus-header files doesnt match your kernel version. In my case i searched repositories/google and found the linux-headers-2.6.12-10_2.6.12-10.26_i386.deb and linux-headers-2.6.12-10-386_2.6.12-10.26_i386.

It will solve your problem as long as your headers match the kernel version. Also note that the first file i listed above has to be installed first.
In case you dont know how to install debian files, open your terminal window and type:

sudo dpkg -i package_file.deb

(1) How can I tell which kernel version I have on my ubuntu breezy 5.10?
(2) Can you provide the url for downloading the headers?

Many thanks.

---

### Post by brucetan on 2006-03-04
> 
From post #558:
Hi guys.
Sorry, I haven't been on the forum for awhile, a long while. :P
Now I am.
I think I'll update my HowTo within the next 2 days.
Anyway, here's a tip: if you want to get ipw2200 and WPA to work on a system running kernel >= 2.6.13, you'll need to change the driver interface in wpa_supplicant from "ipw" to "wext".
__________________
[http://www.openlaptops.org](http://www.openlaptops.org) 

Where have you been chief!  we are using yr howto guide but hitting some problems with ubuntu breezy 5.10!  Hope you can provdie a version of it for breezy 5.10 users.

---

### Post by brucetan on 2006-03-04
Hello Aktizol,

With your post #568 & #569, would you still advice others to try the install script described in your previous thread: [http://ubuntuforums.org/showpost.php?p=728478&postcount=1]("http://ubuntuforums.org/showpost.php?p=728478&postcount=1")

Are these 2 are different problems?

Appreciate your clarification.

I am using ubuntu breezy 5.10 and trying to follow luca's how-to but hitting problems at the moment.  I am going this huge thread (pagesss) to find a solution to my problem.

---

### Post by brucetan on 2006-03-04
Hello,

I read thru the whole 60pages. I decided to use the latest:
ieee80211-1.1.12
ipw2200-1.1.0
ipw2200-fw-2.4
Kernel version = 2.6.12-10-386
gcc 3.4
on Dell Inspiron 6000 with InterProset 2200BG

I then followed Luca_linux's Howto exactly.

Also, after make & install ieee80211-1.1.12, I did the copy to wireless sub-dir
> cp /lib/modules/2.6.12-10-386/net/ieee80211/ieee80211* /lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ieee80211/ 

Then I continue to make & install the rest.

I edited /etc/wpa_supplicant.conf to contain below before I reboot the notebook.

> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid=""
        key_mgmt=NONE
}

network={
       ssid="WoodlandsSGHome"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="D5D6B899E6766C3B36B46A1223"
}


After reboot, I checked the network adpaters status thru the [Administrator]->[Networks], and found the wireless was not activated.  I then activated manual through the network screen.

I then did the command as per Luca's dmesg and it showed below status and seemed ok to me.
> boon@ubuntu:~$ dmesg | grep ipw
[4294702.726000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.0
[4294702.726000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294702.729000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294703.390000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11 a channels)


Then, I executed the wpa_supplicant command as per Luca's:
> boon@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd


The command results are:
> Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=0):
key_mgmt: 0x4
Line: 20 - start of a new network block
ssid - hexdump_ascii(len=15):
     57 6f 6f 64 6c 61 6e 64 73 53 47 48 6f 6d 65      WoodlandsSGHome
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid=''
   id=1 ssid='WoodlandsSGHome'
Daemonize..


I then checked the eth1.  Sadly the status showed disconnected.[-( 

Then, I followed Luca's suggestion to take out the "-w" flag in the wpa_supplicant command and reran it.

> boon@ubuntu:~$ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd


The results:
> Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=0):
key_mgmt: 0x4
Line: 20 - start of a new network block
ssid - hexdump_ascii(len=15):
     57 6f 6f 64 6c 61 6e 64 73 53 47 48 6f 6d 65      WoodlandsSGHome
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=26): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid=''
   id=1 ssid='WoodlandsSGHome'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:13:ce:54:c7:a5
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
wpa_driver_ipw_set_wpa: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=0
wpa_driver_ipw_set_countermeasures: enabled=0
No keys have been configured - skip key clearing


From the look at it, not very good.  I then checked the network adapter status.  It is still disconnected.[-( 

Can anyone see where is the problem? Appreciate very much.

---

### Post by gumbald on 2006-03-04
I'm going insane trying to get my wireless to work. I'm using a Fujitsu Siemens Amilo V2000, been through every point in here, and it won't even pick up a wireless network?! Should this happen even with the basic Ubuntu driver?

Jamie

---

### Post by daynah on 2006-03-04
I don't understand how to get past the "make" issue. I'm not sure what e-blade meant that searching through my repositories is going to solve my problem. I feel like I'm missing about 8 steps.

---

### Post by brucetan on 2006-03-05
Hello Woifi,

Replying yr post #576 [http://www.ubuntuforums.org/showpost.php?p=731451&postcount=576]("http://www.ubuntuforums.org/showpost.php?p=731451&postcount=576")

Which is you gcc version?  I was reading the earlier thread that only gcc 3.4 would be able to have the compatible symbol table for ipw2200 compilation.  

If you are not sure, I suggest you to try menu [System]->[Administrator]->[Synaptic Package Manager] and search for "gcc" to see which gcc version you have.  If gcc 3.4 & gcc 3.4(base) are not installed, then I suggest you try install them & restart the installation procedure as luca's.

Good luck

---

### Post by xrado on 2006-03-05
i have problems compiling ieee80211
this is what i get:
```

xrado@ubuntu:~/Desktop/ieee80211-1.1.11$ make
Checking in /lib/modules/2.6.15-17-386 for ieee80211 components...
make -C /lib/modules/2.6.15-17-386/build M=/home/xrado/Desktop/ieee80211-1.1.11 MODVERDIR=/home/xrado/Desktop/ieee80211-1.1.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-17-386'
  CC [M]  /home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.o
/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.c: In function ‘ieee80211_network_reset’:
/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.c:90: error: ‘struct ieee80211_network’ has no member named ‘ibss_dfs’
/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.c:91: error: ‘struct ieee80211_network’ has no member named ‘ibss_dfs’
/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.c:92: error: ‘struct ieee80211_network’ has no member named ‘ibss_dfs’
/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.c: In function ‘ieee80211_networks_free’:
/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.c:104: error: ‘struct ieee80211_network’ has no member named ‘ibss_dfs’
/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.c:105: error: ‘struct ieee80211_network’ has no member named ‘ibss_dfs’
make[2]: *** [/home/xrado/Desktop/ieee80211-1.1.11/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/xrado/Desktop/ieee80211-1.1.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-17-386'
make: *** [modules] Error 2


```

???

---

### Post by xrado on 2006-03-05
ok i solve it by:

sudo sh remove-old
sudo rm -rf /lib/modules/$(uname -r)/kernel/net/ieee80211
sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/net/ieee80211*
sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/config/ieee80211*

---

### Post by gumbald on 2006-03-05
After multiple attempts using different combinations of drivers and firmware, I keep getting the same output:

```
jammy@solomon:~$ dmesg | grep ipw
[4294699.455000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.10[4294699.455000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[4294699.462000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294699.805000] ipw2200: Radio Frequency Kill Switch is On:
[4294703.250000] ipw2200: Failed to send WEP_KEY: Command timed out.
```

Any ideas? I have never picked up a wireless network in Ubuntu still, even though I get excellent signal in Windows...

---

### Post by brucetan on 2006-03-05
Hi all,

If you are running ubuntu breezy 5.10 and is having problem to get WPA-PSK working like me, you may like also to look the post: [Howto: WPA in Ubuntu 5.10 (Breezy)]("http://www.ubuntuforums.org/showthread.php?t=90450").

Hope it helps!

---

### Post by dbunder on 2006-03-13
NOTE: Scan to the bottom.  I got it working.  Just not in the way I'd like it to work.  There are questions at the bottom of this post in my edits that could use some answering.  The config info and whatnot contained in this post for WPA2/TKIP+AES are still accurate.

Great tutorial!  Exactly what I was looking for.  Unfortunately, I am having issues and cannot connect wirelessly with my Dell Inspiron 8600 w/ Intel Broadcom 2200 adapter.  I followed your tutorial step-by-step, but no dice.  I'm typing this on a wired connection now. :( It's accepting the DHCP-assigned DNS servers and ip and all that happy stuff.  Everything it's supposed to do.  Here's all my relevant information, excluding startup scripts and whatnot:

Router/network setup:
-Linksys WRT54G (rev 1.0 newest firmware)
-Set to hand out ips/DNS over DHCP
-WPA2 Personal security using TKIP+AES algorithms
-No MAC address filtering or anything like that, so I'm not being locked out

My wpa_supplicant.conf file in full:
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="my_ssid"
        scan_ssid=1
        proto=WPA2
        key_mgmt=WPA-PSK
        pairwise=TKIP CCMP
        group=TKIP CCMP
        psk="my_key"
}

```

Command line in my startup script:
```

/usr/sbin/wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w

```

iwconfig output:
```

eth1      IEEE 802.11g  ESSID:"my ssid"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:C5:89:27
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=85/100  Signal level=-45 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:1

```

The above, of course,  meaning it's connected to my router and is getting a signal.

ifconfig eth1 output:
```

eth1      Link encap:Ethernet  HWaddr 00:0E:35:B2:74:60
          inet6 addr: fe80::20e:35ff:feb2:7460/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:975 errors:0 dropped:19 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:132777 (129.6 KiB)  TX bytes:647 (647.0 b)
          Interrupt:7 Base address:0x4000 Memory:faffc000-faffcfff

```

Unsure why it's not getting an IPv4 address...

Output of wpa_supplicant if I run it on the command line:
```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=10):
     64 65 61 64 20 64 69 73 63 6f                     my ssid
scan_ssid=1 (0x1)
proto: 0x2
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='my ssid'
Daemonize..

```

dmesg | grep ipw
```

[4294706.101000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294706.101000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294706.104000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

```

So everything SEEMS to be in order, except that weirdo IPv6 net address.  I am using all the latest ipw and ieee drivers and the latest firmware.

When unwired, I reboot and resolv.conf is not filled in with nameservers, so obviously if I try to ping a site, nothing happens.  If i try to ping a site using that site's ip address, I get "Destination host unreachable" instead of the ping milliseconds.

Sooo... I'm getting a signal from my router, it's a strong one, the drivers are just fine, and everything else seems kosher.  But I'm not getting an ip (or at least I don't think I am... my wired connection on ifconfig receives a standard xxx.xxx.xxx.xxx IPv4 address) or nameservers from my router.

I'm thinking it has something to do with the group and pairwise lines in my configuration file or kernel config (I am using the Ubuntu default kernel, and did the clean scripts in the original tutorial).  Also, I haven't touched /etc/default/wpasupplicant.  Could it be something in there?

Or it could possibly be what I receive when I type "dmesg | grep eth1" - "eth1: no IPv6 routers present"... that seems a bit fishy to me.

I'm sorry if this has been answered, but this thread is huuuuge and I don't have time to go through all of it to seek an answer to my question.

Thanks to anyone who can help or give suggestions.  This is driving me up the wall... my config seems flawless, but it's clearly not, and I don't know what I'm missing.

edit: for good measure, I've tried setting my router and my conf file to WPA (not WPA2) and have tried both TKIP and AES (CCMP) in WPA.  same results.

another edit aka (WOOHOO!): I got it working, but only with WPA and TKIP.  I removed the scan line from my .conf file, added mode=0, changed proto to WPA, and changed related fields to TKIP.  Has anyone been able to get a config working with WPA2 though?  It's much preferred.  Also, what does mode=0 do?  Went through the manpage but didn't catch it.  Could have just been scanning too fast.  I tried the WPA2 AES+TKIP with mode=0 and the scan disabled, but it's still a no go.  Who cares though?  it works!  Just not optimally.  

And yes, I did try WPA2 TKIP+AES in a Windows Vista beta on this same computer and the card supports it.  Assuming it's just a silly driver issue.

Thanks to anyone who shoots me some help on my updated questions in my edit. ;)

---

### Post by spier on 2006-03-13
[QUOTE=dbunder]
...
another edit aka (WOOHOO!): I got it working, but only with WPA and TKIP.  I removed the scan line from my .conf file, added mode=0, changed proto to WPA, and changed related fields to TKIP.  Has anyone been able to get a config working with WPA2 though?  It's much preferred.  Also, what does mode=0 do?  Went through the manpage but didn't catch it.  Could have just been scanning too fast.  I tried the WPA2 AES+TKIP with mode=0 and the scan disabled, but it's still a no go.  Who cares though?  it works!  Just not optimally.  

And yes, I did try WPA2 TKIP+AES in a Windows Vista beta on this same computer and the card supports it.  Assuming it's just a silly driver issue.

Thanks to anyone who shoots me some help on my updated questions in my edit. ;)[/QUOTE]

Well, following this howto and trying hard (as a newbie!),  I got wpa2 working like a charm. Not shure if it is of any help, but here is my wpasuplicant.conf, that differs sligthly from yours: 

```
network={
        ssid="my ssid"
        scan_ssid=1
 	proto=RSN
	pairwise=CCMP
	group=CCMP
	key_mgmt=WPA-PSK
        psk=aaa...fff
}


```

---

### Post by dbunder on 2006-03-13
spier, worked like a charm.  i didn't notice that in the example config file RSN=WPA2.  slight contradiction in the config file tho - it says WPA2 can be used as an alias for RSN, which it obviously can't, at least according to the config I have.  but replacing WPA2 with RSN fixed it right up. :)

thanks so much!  i feel a tiny bit more secure now. :D

only difference in our configs is i have:
pairwise=CCMP TKIP
group=CCMP TKIP

since it matches with my router setup.

---

### Post by dbunder on 2006-03-13
erf.  scratch that.

i just did today's updates, which included a new kernel image and a couple other things, now wpa2 won't work at all.  at boot i get "invalid firmware" errors when it's going through the 2200 firmware stuff.

WPA1 still works though, so i just switched it back.

i should just bite the bullet, download the most recent kernel sources, and build my own, compact kernel and not let Ubuntu update my kernel images.  ever.  *control freak*

so, if you have WPA2/RSN working, don't get the new kernel images and whatnot unless you feel like figuring out what's wrong after the update or don't mind going back to WPA1.

---

### Post by Commuto on 2006-03-13
Don't want to interfere and drag the story to my own issue, but I did not find  the courage to go through the whole thread for an unpredictable answer. Tried the search function, though :o.
I'm currently struggling to get an ipw2200 to work under Ubuntu 5.10. The card runs fine on the same laptop under Windows.
Basically the issue is that the firmware won't be loaded. dmesg gives:
```
me@Host:/var/log$ dmesg | grep ipw2200
[4297637.249000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4297637.250000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4297637.253000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[b][4297637.488000] ipw2200: Unable to load ucode
[4297637.488000] ipw2200: Unable to load firmware: 0xFFFFFFEA[/b]
[4297637.488000] ipw2200: failed to register network device
[4297637.493000] ipw2200: probe of 0000:02:0a.0 failed with error -5
me@Host:/var/log$

```
I created a dedicated thread [here](http://www.ubuntuforums.org/showthread.php?t=141493)... sorry but I though this one could also eventually lead to dismantling the issue.
Thanks :D

---

### Post by dbunder on 2006-03-14
another reboot (battery ran out, oops), no config changes, and wireless is once again not working.  this is WAY too on and off for me.

this time iwconfig isn't even seeing my router, and dhclient eth1 just sends it into a loop that eventually ends with no result.

ugly, ugly, ugly.

---

### Post by aramourne on 2006-03-14
[QUOTE=dbunder]another reboot (battery ran out, oops), no config changes, and wireless is once again not working.  this is WAY too on and off for me.

this time iwconfig isn't even seeing my router, and dhclient eth1 just sends it into a loop that eventually ends with no result.

ugly, ugly, ugly.[/QUOTE]

This is exactly where I am too.. except it never worked in the first place.. it looks like the driver is working though and it works as soon as i turn off WPA in the router. (I also have an ipw2200 and wrt54g)

If you figure something out please post it.. I feel like I've tried every combination of settings that I can..

---

### Post by scottylans on 2006-03-24
**I would like to officially request a complete re-write of this HOW-TO**


Luca has done a great job with it and if I recall took some of my advice back in the early pages to make it really easy for basic users.


Unfortunately he didn't take all my advice and while he's helpful with replies, the HOW-TO needs an update for the ipw2200 under 5.10!
It needs to be simple, concise and from A->B
It's likely only a thorough re-edit of the current one, but having to trawl through 60 pages of help is ridiculous!

_Do NOT _take this as me not appreciating the help but more me trying to _save my time AND YOURS_ by having a new 5.10 guide.

I want to use ipw2200, kismet on 5.10 working fine without problems - this guide used to do that for 5.04 but the recent changes to Ubuntu have "broken it"

Anyone else agree?

(please?)

- Scott


P.S / EDIT


What I specifically would like to acheive with a new HOWTO is,..

User downloads 5.10 CD of Ubuntu
User installs 5.10 Ubuntu on to machine, with ethernet cable hooked up.
User uses the auto update / patches to bring machine up to date.
User follows 15 / 20 / 30 (?) step guide to getting wireless / wpa working.

I know this sounds like I'm being a pushy bastard! :) I'm not! - Luca's old guide used to do this, till they changed Ubuntu :( - I don't know enough to know the terminology but hotplug system was changed I THINK (so a friend tells me?) - and the HOW-TO is now not detailed enough from A to B :(

Thanks again for reading and help.

---

### Post by dbunder on 2006-03-24
it worked more than fine for me.  i'm using breezy, and it was a snap, save for my aforementioned dell wireless toggle button woes (which were in turn related with my wpa+tkip auth woes).  what's wrong with it?  it still applies, unless dapper changed something drastically.

edit: oh, hotplugging does not work for me, but i'm sure that could be easily fixed with a few changes (cut-n-paste style) in /etc/networking/interfaces.  just copy what eth0 does.

---

### Post by scottylans on 2006-03-24
[QUOTE=dbunder]it worked more than fine for me.  i'm using breezy, and it was a snap, save for my aforementioned dell wireless toggle button woes (which were in turn related with my wpa+tkip auth woes).  what's wrong with it?  it still applies, unless dapper changed something drastically.

edit: oh, hotplugging does not work for me, but i'm sure that could be easily fixed with a few changes (cut-n-paste style) in /etc/networking/interfaces.  just copy what eth0 does.[/QUOTE]


The guide simply does not work from a fresh CD install, start to finish.
Some backend application was changed and a heap of fiddling now has to be done.

ALSO I heard intel removed monitor mode from ipw2200 too, is that true?

---

### Post by scottylans on 2006-03-31
[QUOTE=scottylans]**I would like to officially request a complete re-write of this HOW-TO**


Luca has done a great job with it and if I recall took some of my advice back in the early pages to make it really easy for basic users.


Unfortunately he didn't take all my advice and while he's helpful with replies, the HOW-TO needs an update for the ipw2200 under 5.10!
It needs to be simple, concise and from A->B
It's likely only a thorough re-edit of the current one, but having to trawl through 60 pages of help is ridiculous!

_Do NOT _take this as me not appreciating the help but more me trying to _save my time AND YOURS_ by having a new 5.10 guide.

I want to use ipw2200, kismet on 5.10 working fine without problems - this guide used to do that for 5.04 but the recent changes to Ubuntu have "broken it"

Anyone else agree?

(please?)

- Scott


P.S / EDIT


What I specifically would like to acheive with a new HOWTO is,..

User downloads 5.10 CD of Ubuntu
User installs 5.10 Ubuntu on to machine, with ethernet cable hooked up.
User uses the auto update / patches to bring machine up to date.
User follows 15 / 20 / 30 (?) step guide to getting wireless / wpa working.

I know this sounds like I'm being a pushy bastard! :) I'm not! - Luca's old guide used to do this, till they changed Ubuntu :( - I don't know enough to know the terminology but hotplug system was changed I THINK (so a friend tells me?) - and the HOW-TO is now not detailed enough from A to B :(

Thanks again for reading and help.[/QUOTE]


As I said in the 5.10 thread. ([http://www.ubuntuforums.org/showthread.php?p=878819#post878819](http://www.ubuntuforums.org/showthread.php?p=878819#post878819)) 

Curious on any comments, please? -sorry to hassle but I really do find the how-to's un-necessarily complex since they made that udev thingo change to ubuntu :(

---

### Post by nemik on 2006-04-04
following this guide a while ago got everything working perfectly. but last night the update manager upgraded my linux-headers and linux-image. suddenly, i have no more eth0. my wifi is simply not detected.

dmesg gives something about IEEE errors. but it still works with the 2.16-9 kernel, just not the newest 2.16-10 which did work before.

does anyone else have this problem? how did you get around it?

---

### Post by scottylans on 2006-04-07
[QUOTE=nemik]following this guide a while ago got everything working perfectly. but last night the update manager upgraded my linux-headers and linux-image. suddenly, i have no more eth0. my wifi is simply not detected.

dmesg gives something about IEEE errors. but it still works with the 2.16-9 kernel, just not the newest 2.16-10 which did work before.

does anyone else have this problem? how did you get around it?[/QUOTE]


Posts like these are why I'd like a fully updated howto :(

---

### Post by RoyCowboy on 2006-04-14
Hi everyone.

I've read through all 63 pages and tried every litt tip I could find but still my wireless network is not working properly.
I am currently using Drapper drak flight 6 with:
- ieee80211-1.1.13
- ipw2200-1.1.2
- ipw2200-fw-3.0

First of all it did not work "out-of-the-box" so I tried to compile everything like descibed in this thread. After a couple of tries I finally successed the compilation with no errors.
The thing is, I can only connect to unsecured network. If I try to connect to a network secured with wep/wpa my network-montitor-applet suddenly shows eth1 as disconnected.

Is there a common solution to this problem? I mean, if I can connect to an unsecured network, I dont see why I cant connect to a secured one..?

Thanks in advance! :D

---

### Post by blubb on 2006-04-16
Well, I haven't read everything, but it didn't work for me to.
I found the solution there: [http://lists.shmoo.com/pipermail/hostap/2005-November/011787.html]("http://lists.shmoo.com/pipermail/hostap/2005-November/011787.html")
it was simply to use -Dwext rather using -Dipw in the "wpa_supplicant bla" command line
Ive compiled the thing three times (including kernel) ] (*,) 

hth

---

### Post by vladimir-dk on 2006-04-20
I have read all 63 posts and now i just about to crash my keyboard.
The sh script wont delete these drivers automatically.
I cant get rid of the "old" drivers. I get this error message:

---------------------------------------------------------------------------------
Old ieee80211 references found.  In order to build the ieee80211
subsystem, prior versions must first be removed.  You can perform
this task by running this makefile as root via:

    % sudo make check_old

and answering Y to remove the file references.
Aborting make.
make: *** [check_old] Error 1[/CODE]
---------------------------------------------------------------------------------

I have deleted the folders (ieee22810 and ipw2200) in:
/lib/modules/2.6.12-10-386/build/include/config/

How can i locate these missing files ? Any help would be appriciated...

---

### Post by x5452 on 2006-04-20
Hello all, im new on ubuntu Breezy, this guide i found says for Hoary, is it the same for breezy?  I have dell 700m with Intel PRO/Wireless 2200BG integrated, is that what ipw2200 stand for?  I am about to buy a new router and want to enable security, so I want to make sure I can get it to work before I go spend money on a 54g router, (still have stupid 'b' router, sloooow) 
I would appreciate very much your advice, thank you!:mrgreen:

---

### Post by vladimir-dk on 2006-04-22
Can anyone help me with the question above... 
Thank in advance...:-k

---

### Post by greeners on 2006-04-24
This was a very helpful thread.  Thank you so much.  I have my WPA-PSK working in under an hour.

One thing that may be helpful for others.  If you are not using the ipw2200 network driver then you need to change the wpa_supplicant -D parameter.

In my case I had to change it to the following for my atheros chipset wifi card:

sudo /usr/sbin/wpa_supplicant -B -dd -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w

Note that the /etc/init.d/wifi_wpa.sh script also needs changing.  If you're not sure what the parameter should be then the following is what my version of wpa_supplicant will accept:

---

### Post by greeners on 2006-04-24
Curses.  I posted the previous message before I added the drivers list.  So here it is:

drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  prism54 = Prism54.org driver (Intersil Prism GT/Duette/Indigo)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver

---

### Post by Mars Thrax on 2006-05-16
I'm new to Ubuntu (and linux in general), and am still having trouple getting my wireless card to work.

I followed the original instructions word for word (including installing the new headers and build essentials, as well as following the instructions for adding repositories). My problem is that, when I try to run make in the ieee80211-1.0.3 folder, I get the following output:

> 
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

find: /lib/modules/2.6.12-9-386/build/: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.12-9-386/build M=/home/ubuntu/Desktop/ieee80211-1.0.3 MODVERDIR=/home/ubuntu/Desktop/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
ubuntu@ubuntu:~/Desktop/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

find: /lib/modules/2.6.12-9-386/build/: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-9-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.12-9-386/build M=/home/ubuntu/Desktop/ieee80211-1.0.3 MODVERDIR=/home/ubuntu/Desktop/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2


So, I know I'm missing the stuff that is supposed to be in /lib/modules/2.6.12-9-386/build/
What I don't understand is where I went wrong. I would assume that those things should have been added when I installed the headers and build-essentials.

Any help would be greatly appreciated.

Oh, it may be worth noting that I am doing this from the livedisk. I wanted to make sure I could do the configuration things before I commited myself to Ubuntu.

---

### Post by mnd- on 2006-05-17
Sorry if this has been answered somewhere in this thread, but it's getting quite big so I couldn't read it through :)

I got wpasupplicant working with this howto but now my problem is that my wlan connection reconnects about every 10 sec. This makes it practically unbearable to use SSH for example. In the wlan AP log I can see lines "wl0: 11g: associated user......" & "wl0: 11g: deassociated user..." every 10 seconds. It takes about three seconds for the wlan connection to come up again as it disconnects and this is very annoying. This is my wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="XXXX"
        scan_ssid=1
        proto=WPA
        group=TKIP
        key_mgmt=WPA-PSK
        psk="XXXX"
}
```
Anybody have any ideas why this happens ?

---

### Post by snakeyes37 on 2006-06-11
I keep getting this error when trying to follow this guide in my terminal window,


```

root@AUDIE:/home/nicholas/Desktop/ieee80211-1.0.3# make
Checking in /lib/modules/2.6.15-23-386/build/ for ieee80211 components...

find: /lib/modules/2.6.15-23-386/build/: No such file or directory
grep: /lib/modules/2.6.15-23-386/build//.config: No such file or directory
grep: /lib/modules/2.6.15-23-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.15-23-386/build M=/home/nicholas/Desktop/ieee80211-1.0.3 MODVERDIR=/home/nicholas/Desktop/ieee80211-1.0.3 modules
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
root@AUDIE:/home/nicholas/Desktop/ieee80211-1.0.3#

```


Any ideas?


Thanks.

---

### Post by mech7 on 2006-07-09
mm it still does not work with me either :(

Also it says..

Warning PCI Driver IPW2200 has a struct device driver shutdown method please update

:(

---

### Post by mech7 on 2006-07-09
mmm it is weird i dont even have this directory:

```
sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/
```

There is no hotplug and firmware :confused:

---

### Post by Zeratul7 on 2006-07-20
> **mech7 said:**
> mmm it is weird i dont even have this directory:

```
sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/
```

There is no hotplug and firmware :confused:

Same problem here...

---

### Post by Jochus on 2006-08-05
Okay, I've done something really stupid I think :-(

I followed this tutorial, but it doesn't worked it all. So after a while, I rebooted to Windows, but now my WLAN isn't working any longer in Windows as well :-(

Windows finds my network, but can't connect ... Does this mean I ****** up my wireless card? Is there a possibility to fix it?

---

### Post by wieman01 on 2006-08-06
Same here for some reason. So I stopped using Windows after all. :-( Which is not a big deal for me, however, I am surprised such a thing could happen at all.

---

### Post by Jochus on 2006-08-06
Problem solved in Windows by disabling/enabling MAC filter on the router
( don't even ask how that comes! :p )

Now, in Kubuntu, it still doesn't work :-(

The card gets recognized, but

```
jochus@bacardi:~$ dmesg | grep -i intel
[4294667.296000] ACPI: FADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @
0x3fee9e88
[4294667.296000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @                                                                                                    0x3fee9efc
[4294667.296000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @                                                                                                    0x3fee9f9c
[4294667.296000] ACPI: DSDT (v001 INTEL  ALVISO   0x06040000 MSFT 0x0100000e) @                                                                                                    0x00000000
[4294671.448000] CPU: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[4294686.686000] agpgart: Detected an Intel 915GM Chipset.
[4294688.469000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@                                                                                                   linux.intel.com>
[4294688.966000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.0
[4294688.966000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294688.966000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

```

... now, there's something wrong with my eth1

```

jochus@bacardi:~$ dmesg | grep eth1
[4294693.947000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

What could be the problem?

---

### Post by woifi on 2006-08-07
> **mech7 said:**
> mmm it is weird i dont even have this directory:

```
sudo tar xvzf ipw2200-fw-2.3.tgz
sudo cp ipw-2.3-*.fw /usr/lib/hotplug/firmware/
```

There is no hotplug and firmware :confused:

try /lib/firmware/ on dapper

---

### Post by bjacquet on 2006-08-11
Hello,

When going through the make of ipw2200:
```
cd ipw2200-1.0.6
make
```
The following output is given:
```
mkdir -p /home/bruno/wireless/ipw2200-1.0.6/tmp/.tmp_versions
cp /lib/modules/2.6.15-26-386/net/ieee80211/.tmp_versions/*.mod /home/bruno/wireless/ipw2200-1.0.6/tmp/.tmp_versions
make -C /lib/modules/2.6.15-26-386/build M=/home/bruno/wireless/ipw2200-1.0.6 MODVERDIR=/home/bruno/wireless/ipw2200-1.0.6/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /home/bruno/wireless/ipw2200-1.0.6/ipw2200.o
/home/bruno/wireless/ipw2200-1.0.6/ipw2200.c: In function 'ipw_pci_probe':
/home/bruno/wireless/ipw2200-1.0.6/ipw2200.c:10748: error: 'struct iw_handler_def' has no member named 'spy_offset'
make[2]: *** [/home/bruno/wireless/ipw2200-1.0.6/ipw2200.o] Error 1
make[1]: *** [_module_/home/bruno/wireless/ipw2200-1.0.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [modules] Error 2

```
Notice the message: **ipw2200.c:10748: error: 'struct iw_handler_def' has no member named 'spy_offset'**.

This is obviously an error in the script, right?

Bruno.

---

### Post by ZaphodX on 2006-08-11
Hello Bruno,

this is **not** an error in the source code of the driver.

As you are trying to compile the driver with kernel version 2.6.15,  you should use a more recent version of the IPW source code. ipw2200-1.0.6 is a little outdated.

Please use
[http://ipw2200.sourceforge.net/#downloads](http://ipw2200.sourceforge.net/#downloads)
to download the newest driver and
[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
in order to download the according firmware.

Or... upgrade your Ubuntu installation to Dapper Drake ;)

Good Luck
Carsten

---

### Post by Styles on 2006-10-25
Funny I'm getting the same error about eth1 link not ready. This is a brand new install of edgy, I riped out the org ipw2200 ieee and ipw2200 firmware, download new drivers off SF and installed them.

this was in my dmesg using the original drivers

> Oct 25 08:41:58 laptop kernel: [17179586.312000] Driver 'ipw2200' needs updating - please use bus_type methods

after updating to the latest and greatest that msg is gone

> Oct 25 10:47:29 laptop kernel: [17179586.840000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0dmq
Oct 25 10:47:29 laptop kernel: [17179586.840000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Oct 25 10:47:29 laptop kernel: [17179587.088000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Oct 25 10:47:29 laptop kernel: [17179587.356000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

 sudo lshw -C network even shows eth1 info and wifi-radar even picks up other networks..

> 

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth0
       version: 11
       serial: 00:14:c2:da:b5:6b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5751m-v3.29a ip=10.0.100.121 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:c8000000-c800ffff irq:169
  *-usb
       description: Bluetooth wireless interface
       product: HP integrated Bluetooth module
       vendor: Broadcom
       physical id: 2
       bus info: usb@2:2
       version: 0.17
       capabilities: bluetooth usb-1.10
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 05
       serial: 00:15:00:1f:9f:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0dmq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:c8400000-c8400fff irq:50

output of ifconfig notice the missing ip?

> 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:C2:DA:B5:6B  
          inet addr:10.0.100.121  Bcast:10.0.100.255  Mask:255.255.255.0
          inet6 addr: fe80::214:c2ff:feda:b56b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1049811 (1.0 MiB)  TX bytes:262819 (256.6 KiB)
          Interrupt:169 

eth1      Link encap:Ethernet  HWaddr 00:15:00:1F:9F:DD  
          inet6 addr: fe80::215:ff:fe1f:9fdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2578 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0xe000 Memory:c8400000-c8400fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

and when I try and start the wifi eth1 link via NetworkMangler err NetworkManager in Gnome I see this in messages.

> 
 kernel: [17182505.884000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Any ideas anybody? I'm fresh out

---

### Post by Styles on 2006-10-25
forgot to add my /etc/network/interfaces and iwconfig output

 cat /etc/network/interfaces
> 
auto lo
iface lo inet loopback
#auto eth0
#iface eth0 inet dhcp
#iface eth2 inet dhcp
#wireless-essid goaway
#wireless-key s:secretkey
#auto eth2
#iface eth1 inet dhcp
#wireless-essid QcS1-M4B-01s
#wireless-key s:secretkey

I commented out all except lo and rebooted 

get this in dmesg |grep eth1

> [17179590.768000] eth1: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:14:c2:da:b5:6b
[17179590.768000] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17179590.768000] eth1: dma_rwctrl[76180000] dma_mask[64-bit]
[17179606.484000] ADDRCONF(NETDEV_UP): eth1: link is not ready

dmesg |grep ipw2200
> 
[17179590.528000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0dmq
[17179590.528000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179590.528000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179590.736000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

---

### Post by Psquared on 2006-10-25
Hmmmm..... lots of questions and not many answers. Luca has moved on to his own website with its own forum. I think it might be time to move this thread over there. I can't get wireless to work either BTW; but I am using Elive so its an entirely different set of problems.

---

### Post by kroschel on 2006-12-20
hi...
i got this error message:
[4294698.284000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.4dmq
[4294698.284000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294698.289000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294698.377000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[4294698.377000] ipw2200: Unable to load firmware: -2
[4294698.377000] ipw2200: failed to register network device
[4294698.381000] ipw2200: probe of 0000:06:07.0 failed with error -5

i copy the firmware to /usr/lib/hotplug/firmware
this is not the error.

---

### Post by kroschel on 2006-12-20
ok, my mistake ;) ... wrong driver.
sorry ;)

---

### Post by amitbiswas on 2007-01-28
hi there, I have installed ubuntu edgy on my laptop and facing problem with activating the wireless. Here is some info regarding wireless hardware and software
# uname -r
2.6.17-10-generic
# dmesg | grep 2200
[17179572.800000]   MEM window: 22000000-23ffffff
[17179573.220000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179573.220000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179573.220000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179573.220000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179573.220000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179573.220000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.220000] EISA: Probing bus 0 at eisa.0
[17179573.220000] EISA: Detected 0 cards.
[17179602.052000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1dmq
[17179602.052000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179608.472000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179608.700000] ipw2200: [COLOR="Navy"]Radio Frequency Kill Switch is On:[/COLOR]
[17179608.700000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

I have tried every solution what I can find through google; but unfortunately still not working. and as instructed on ubuntu forum regarding copy the firmware into /usr/lib/hotplug/firmware but in my system there is no folder called /usr/lib/hotplug.... 

If any one have a idea to fix this problem would be great.

---

### Post by jerich007 on 2007-02-14
Hi -

Got this finally to work on Edgy on my T43.  I followed the steps as directed here, but there was a key step missing from the steps here that didn't allow me to load the new driver.  I had to unload the modules for ieee80211 and ieee80211_crypt to get the new ipw2200 to load.  This was the cause of all my 'unknown symbol' errors.  You can unload the modules via this:

rmmod ieee80211
rmmod ieee80211_crypt

When I run 'modprobe ipw2200' I don't get errors and it loads fine.  Also, there is no /usr/lib/hotplug/firmware directory in Edgy.  Just copy the files to /lib/firmware instead.

Hope this helps,
Jericho

---

### Post by Linda on 2007-07-06
I've tried several times to install firmware. The first time I got the first line in and hit enter and it asked for a password.  Every attempt after that it tells me "error" it cannot open the directory.
In need of help.

Linda

---

### Post by HarM_triade on 2008-04-15
Very nice HOWTO.
No frills, simple and just works on my fujitsu T3010d ..... thanks!:popcorn:

---

### Post by moransa on 2011-04-20
I guess this is what I get for trying to help someone.  

I'm trying to install the stupid wireless card on this stupid laptop for my friend who is going out of town for business.  

I've read about 50 pages of instructions from you people, none of them were completely helpful, it just jumps to another page where I start over with a bunch more useless commands.  I am seriously considering taking my shotgun to stupid thing and telling my friend the dog ate it.  

I have the drivers.  How do I install them????  Can anyone answer this, or you just skip that part to **** people off?  The drivers are in my download folder.  Terminal apparently does not know where the hell that is, so how do I tell it to look there?  

Please don't guess, I only have a few more attempts before I completely lose my temper.

---

