---
title: "Want to use NetworkManager, but keeps disconnecting"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by UnknownFearNG on 2012-03-19
I want to use the default way of connecting to the Internet via NetworkManager, however, when I connect to it, it keeps disconnecting me from my connection. I have to use Wicd, which is fine, everything works great, but I kind of wanted that "out of the box" feel, if anyone knows what I mean. The connection I have here seems to be really low, 45-50% at best, and it seems that, when I use NetworkManager, it kicks me off due to the connecting dropping below a certain connection level, but it loads pages just fine using Wicd.

---

### Post by Ms. Daisy on 2012-03-22
I take it this is a wireless connection?  Can you boost the signal from the router, perhaps move the router so your signal is higher?

---

### Post by wildmanne39 on 2012-03-22
Hi, there are some people that have trouble using network manager I usually help then switch to wicd so if it is working for you then you may not have much of a choice for now, you could install network manager then remove wicd and we will try to troubleshoot the problem but you will still probably end up using wicd anyway.

You can see if there is an update to network manager that you can install that might fix the problem.
Thanks

---

### Post by UnknownFearNG on 2012-04-05
I found the problem to be the signal strength. The router is down stairs whereas I am in my room on the second floor. You wouldn't think it would change so drastically, but I have a range anywhere between 40% to 55% so it's not too bad, however, on Windows, I was getting near perfect signal. Very weird.

---

### Post by wildmanne39 on 2012-04-05
Hi, if you will post the output from the following commands we may be able to increase your signal:
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

### Post by UnknownFearNG on 2012-04-05
I actually got my signal strength much higher then it was, and it's a lot more stable. I had to turn off power management for my network. Here is the output of the commands:

```

djmillier@Darkan:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Darkan 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux

djmillier@Darkan:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0602]
	Kernel driver in use: atl1c
--
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6631]
	Kernel driver in use: ath9k

djmillier@Darkan:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04e8:6860 Samsung Electronics Co., Ltd 
Bus 002 Device 002: ID 064e:d214 Suyin Corp. 
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth

djmillier@Darkan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"link_xbox"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:D1:C8:25:50   
          Bit Rate=81 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:56  Invalid misc:889   Missed beacon:0

djmillier@Darkan:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

djmillier@Darkan:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_conexant    52460  1 
arc4                   12473  2 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k                 112711  0 
joydev                 17393  0 
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              393421  1 ath9k
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                929507  3 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
cfg80211              172427  3 ath9k,mac80211,ath
k10temp                12990  0 
binfmt_misc            17292  1 
ttm                    65224  1 radeon
sp5100_tco             13495  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
sparse_keymap          13658  0 
wmi                    18744  0 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
atl1c                  36638  0 
ahci                   21634  2 
libahci                25727  1 ahci

```

---

### Post by wildmanne39 on 2012-04-06
Hi, yes power management can cause issues.

Let's make this one other change it may make your signal a little stronger if not it at least makes your connection more stable.
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by UnknownFearNG on 2012-04-06
> **wildmanne39 said:**
> Hi, yes power management can cause issues.

Let's make this one other change it may make your signal a little stronger if not it at least makes your connection more stable


Already have that option listed :)

---

### Post by UnknownFearNG on 2012-04-06
Just got thinking. Since my signal strength is fixed, I might try and install NetworkManager and see if it works. If not, least I know it works perfectly on Wicd.

---

### Post by wildmanne39 on 2012-04-06
Hi, then you have done all that I know to improve signal.

---

### Post by wildmanne39 on 2012-04-06
Hi, that is up to you if you like wicd since it works I would just keep using it if it was me.
Thanks

---

### Post by UnknownFearNG on 2012-04-06
> **wildmanne39 said:**
> Hi, that is up to you if you like wicd since it works I would just keep using it if it was me.
Thanks

I tried it, no dice. Kept disconnecting after a period of time. wicd is the way to go for me I guess :)

---

### Post by wildmanne39 on 2012-04-06
Hi, some people have trouble with network manager and wicd handles encryption better that is why it works for you and network manager does not.
Thanks

---

### Post by UnknownFearNG on 2012-04-06
Good to know. I'll definitely be installing wicd and removing network manager when I install new releases of Ubuntu from now on :)

---

### Post by UnknownFearNG on 2012-04-07
And back with a different problem. I thought I would never see it happen again, but my network every so often will disconnect. It happened all the time when I used Network Manager and I thought the problem would be fixed after I installed wicd, but low and behold, it disconnects every so often. This is just frustrating me to no end!! Anyone have any idea why it does this? I tried installing a backport for it, but no dice.

Worst case, and this is the DEFINITE worst case scenario. When I had Windows 7 running, the wireless was perfect. Can't believe I'm saying this, but worst case, I can install Windose and put Ubuntu over it so I'm using the WiFi connection from Windose. But I DO NOT want to do this if I can help it!!!

---

### Post by wildmanne39 on 2012-04-07
Hi when you installed network manager how did you remove it? you may have left configuration files behind.

I would run this command:
```
sudo apt-get purge network-manager network-manager-gnome
```
Then reboot.

Also have you had any upgrades? what is your encryption set on in the router.

If the above command does not fix it I will see if I can help tomorrow.
Thanks

---

### Post by UnknownFearNG on 2012-04-07
I don't have any of those packages installed. The network encryption is WPA2 and I have no upgrades.

So far, it actually hasn't disconnected so far. But I'll keep you posted.

---

### Post by Ms. Daisy on 2012-04-07
If you don't get any other suggestions, you may look at your sys log. I'm assuming you've got WPA set up?  My logs show that WPA is rekeying every 10 minutes.  Do your logs show success each time?  I'm just spit-balling, but I suppose your rekeying could be hanging up or failing, causing the disconnection.

---

### Post by wildmanne39 on 2012-04-07
Hi, when you have trouble staying connected post the output of:
```
nm-tool
sudo iwlist scan

```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by Ms. Daisy on 2012-04-07
I was just coming back to say you should look at the logs when you get kicked off the network to see what's getting recorded more generally, but wildmanne39 beat me to it.  

BTW, what does etork do? And where did you come up with that string of commands? Don't think I could have patched that together in a million years on my own.  I'm forced to look at the logs in the GUI log file viewer. :oops:

---

### Post by UnknownFearNG on 2012-04-07
> **Ms. Daisy said:**
>   
BTW, what does etork do? And where did you come up with that string of commands? 

Tell me about it lol. I tried doing the command and it didn't do anything. I checked syslog, but it doesn't have anything yet. I'll post back in this thread if it gets hairy. Actually, I'll attempt a restart and see if it happens.

---

### Post by UnknownFearNG on 2012-04-07
GOT IT!!! I have captured the output when it connects and disconnects. You can even see Skype getting disconnected as well. Here is the output:

```

Apr  7 09:44:33 Darkan dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr  7 09:44:33 Darkan dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr  7 09:44:33 Darkan dhclient: All rights reserved.
Apr  7 09:44:33 Darkan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  7 09:44:33 Darkan dhclient: 
Apr  7 09:44:33 Darkan kernel: [  688.482619] type=1400 audit(1333806273.861:23): apparmor="DENIED" operation="open" parent=3859 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=3892 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Apr  7 09:44:33 Darkan dhclient: Listening on LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 09:44:33 Darkan dhclient: Sending on   LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 09:44:33 Darkan dhclient: Sending on   Socket/fallback
Apr  7 09:44:33 Darkan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr  7 09:44:34 Darkan avahi-daemon[608]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::6aa3:c4ff:fee5:408.
Apr  7 09:44:34 Darkan avahi-daemon[608]: New relevant interface wlan0.IPv6 for mDNS.
Apr  7 09:44:34 Darkan avahi-daemon[608]: Registering new address record for fe80::6aa3:c4ff:fee5:408 on wlan0.*.
Apr  7 09:44:36 Darkan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr  7 09:44:36 Darkan dhclient: DHCPOFFER of 192.168.1.115 from 192.168.1.1
Apr  7 09:44:36 Darkan dhclient: DHCPREQUEST of 192.168.1.115 on wlan0 to 255.255.255.255 port 67
Apr  7 09:44:36 Darkan dhclient: DHCPACK of 192.168.1.115 from 192.168.1.1
Apr  7 09:44:36 Darkan avahi-daemon[608]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.115.
Apr  7 09:44:36 Darkan avahi-daemon[608]: New relevant interface wlan0.IPv4 for mDNS.
Apr  7 09:44:36 Darkan avahi-daemon[608]: Registering new address record for 192.168.1.115 on wlan0.IPv4.
Apr  7 09:44:36 Darkan dhclient: bound to 192.168.1.115 -- renewal in 32765 seconds.
Apr  7 09:44:43 Darkan kernel: [  698.064207] wlan0: no IPv6 routers present
Apr  7 09:44:45 Darkan ntpdate[3943]: step time server 91.189.94.4 offset 0.592832 sec
Apr  7 09:53:04 Darkan kernel: [ 1198.417796] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Apr  7 10:00:42 Darkan kernel: [ 1656.063689] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr  7 10:00:42 Darkan kernel: [ 1656.063708] cfg80211: Restoring regulatory settings
Apr  7 10:00:42 Darkan kernel: [ 1656.063723] cfg80211: Calling CRDA to update world regulatory domain
Apr  7 10:00:42 Darkan kernel: [ 1656.074908] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Apr  7 10:00:42 Darkan kernel: [ 1656.074922] cfg80211: World regulatory domain updated:
Apr  7 10:00:42 Darkan kernel: [ 1656.074929] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  7 10:00:42 Darkan kernel: [ 1656.074941] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:00:42 Darkan kernel: [ 1656.074951] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:00:42 Darkan kernel: [ 1656.074961] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:00:42 Darkan kernel: [ 1656.074971] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:00:42 Darkan kernel: [ 1656.074980] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:00:46 Darkan dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr  7 10:00:46 Darkan dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr  7 10:00:46 Darkan dhclient: All rights reserved.
Apr  7 10:00:46 Darkan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  7 10:00:46 Darkan dhclient: 
Apr  7 10:00:46 Darkan dhclient: Listening on LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:00:46 Darkan dhclient: Sending on   LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:00:46 Darkan dhclient: Sending on   Socket/fallback
Apr  7 10:00:46 Darkan dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Apr  7 10:00:46 Darkan avahi-daemon[608]: Withdrawing address record for 192.168.1.115 on wlan0.
Apr  7 10:00:46 Darkan avahi-daemon[608]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.115.
Apr  7 10:00:46 Darkan avahi-daemon[608]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  7 10:00:46 Darkan avahi-daemon[608]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr  7 10:00:46 Darkan avahi-daemon[608]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::6aa3:c4ff:fee5:408.
Apr  7 10:00:46 Darkan avahi-daemon[608]: Withdrawing address record for fe80::6aa3:c4ff:fee5:408 on wlan0.
Apr  7 10:00:46 Darkan kernel: [ 1660.465561] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 10:00:46 Darkan dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr  7 10:00:46 Darkan dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr  7 10:00:46 Darkan dhclient: All rights reserved.
Apr  7 10:00:46 Darkan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  7 10:00:46 Darkan dhclient: 
Apr  7 10:00:46 Darkan dhclient: Listening on LPF/eth0/b8:70:f4:92:5c:5d
Apr  7 10:00:46 Darkan dhclient: Sending on   LPF/eth0/b8:70:f4:92:5c:5d
Apr  7 10:00:46 Darkan dhclient: Sending on   Socket/fallback
Apr  7 10:00:46 Darkan kernel: [ 1660.698567] atl1c 0000:06:00.0: irq 41 for MSI/MSI-X
Apr  7 10:00:46 Darkan kernel: [ 1660.782288] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  7 10:00:51 Darkan kernel: [ 1665.122782] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 10:01:02 Darkan dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr  7 10:01:02 Darkan dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr  7 10:01:02 Darkan dhclient: All rights reserved.
Apr  7 10:01:02 Darkan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  7 10:01:02 Darkan dhclient: 
Apr  7 10:01:02 Darkan dhclient: Listening on LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:01:02 Darkan dhclient: Sending on   LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:01:02 Darkan dhclient: Sending on   Socket/fallback
Apr  7 10:01:02 Darkan dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Apr  7 10:01:02 Darkan dhclient: send_packet: Network is unreachable
Apr  7 10:01:02 Darkan dhclient: send_packet: please consult README file regarding broadcast address.
Apr  7 10:01:02 Darkan kernel: [ 1676.628947] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 10:01:02 Darkan dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr  7 10:01:02 Darkan dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr  7 10:01:02 Darkan dhclient: All rights reserved.
Apr  7 10:01:02 Darkan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  7 10:01:02 Darkan dhclient: 
Apr  7 10:01:02 Darkan dhclient: Listening on LPF/eth0/b8:70:f4:92:5c:5d
Apr  7 10:01:02 Darkan dhclient: Sending on   LPF/eth0/b8:70:f4:92:5c:5d
Apr  7 10:01:02 Darkan dhclient: Sending on   Socket/fallback
Apr  7 10:01:02 Darkan kernel: [ 1676.868107] atl1c 0000:06:00.0: irq 41 for MSI/MSI-X
Apr  7 10:01:02 Darkan kernel: [ 1676.954315] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  7 10:01:03 Darkan dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr  7 10:01:03 Darkan dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr  7 10:01:03 Darkan dhclient: All rights reserved.
Apr  7 10:01:03 Darkan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  7 10:01:03 Darkan dhclient: 
Apr  7 10:01:03 Darkan dhclient: Listening on LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:01:03 Darkan dhclient: Sending on   LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:01:03 Darkan dhclient: Sending on   Socket/fallback
Apr  7 10:01:03 Darkan dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Apr  7 10:01:03 Darkan dhclient: send_packet: Network is unreachable
Apr  7 10:01:03 Darkan dhclient: send_packet: please consult README file regarding broadcast address.
Apr  7 10:01:03 Darkan kernel: [ 1677.286902] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 10:01:05 Darkan kernel: [ 1679.680282] wlan0: authenticate with 00:14:d1:c8:25:50 (try 1)
Apr  7 10:01:05 Darkan kernel: [ 1679.683206] wlan0: authenticated
Apr  7 10:01:05 Darkan kernel: [ 1679.683290] wlan0: associate with 00:14:d1:c8:25:50 (try 1)
Apr  7 10:01:05 Darkan kernel: [ 1679.698725] wlan0: RX AssocResp from 00:14:d1:c8:25:50 (capab=0x411 status=0 aid=1)
Apr  7 10:01:05 Darkan kernel: [ 1679.698741] wlan0: associated
Apr  7 10:01:05 Darkan kernel: [ 1679.706042] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  7 10:01:06 Darkan dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Apr  7 10:01:06 Darkan dhclient: Copyright 2004-2010 Internet Systems Consortium.
Apr  7 10:01:06 Darkan dhclient: All rights reserved.
Apr  7 10:01:06 Darkan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  7 10:01:06 Darkan dhclient: 
Apr  7 10:01:06 Darkan kernel: [ 1680.522723] type=1400 audit(1333807266.491:24): apparmor="DENIED" operation="open" parent=5192 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=5227 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Apr  7 10:01:06 Darkan dhclient: Listening on LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:01:06 Darkan dhclient: Sending on   LPF/wlan0/68:a3:c4:e5:04:08
Apr  7 10:01:06 Darkan dhclient: Sending on   Socket/fallback
Apr  7 10:01:06 Darkan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr  7 10:01:07 Darkan avahi-daemon[608]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::6aa3:c4ff:fee5:408.
Apr  7 10:01:07 Darkan avahi-daemon[608]: New relevant interface wlan0.IPv6 for mDNS.
Apr  7 10:01:07 Darkan avahi-daemon[608]: Registering new address record for fe80::6aa3:c4ff:fee5:408 on wlan0.*.
Apr  7 10:01:08 Darkan kernel: [ 1682.063411] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr  7 10:01:08 Darkan kernel: [ 1682.063431] cfg80211: Restoring regulatory settings
Apr  7 10:01:08 Darkan kernel: [ 1682.063445] cfg80211: Calling CRDA to update world regulatory domain
Apr  7 10:01:08 Darkan kernel: [ 1682.074780] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Apr  7 10:01:08 Darkan kernel: [ 1682.074795] cfg80211: World regulatory domain updated:
Apr  7 10:01:08 Darkan kernel: [ 1682.074802] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  7 10:01:08 Darkan kernel: [ 1682.074814] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:01:08 Darkan kernel: [ 1682.074824] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:01:08 Darkan kernel: [ 1682.074834] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:01:08 Darkan kernel: [ 1682.074843] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:01:08 Darkan kernel: [ 1682.074853] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  7 10:01:08 Darkan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr  7 10:01:09 Darkan kernel: [ 1683.127278] wlan0: authenticate with 00:14:d1:c8:25:50 (try 1)
Apr  7 10:01:09 Darkan kernel: [ 1683.324143] wlan0: authenticate with 00:14:d1:c8:25:50 (try 2)
Apr  7 10:01:09 Darkan kernel: [ 1683.524130] wlan0: authenticate with 00:14:d1:c8:25:50 (try 3)
Apr  7 10:01:09 Darkan kernel: [ 1683.724075] wlan0: authentication with 00:14:d1:c8:25:50 timed out
Apr  7 10:01:11 Darkan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr  7 10:01:16 Darkan kernel: [ 1690.560045] wlan0: no IPv6 routers present
Apr  7 10:01:18 Darkan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr  7 10:01:20 Darkan kernel: [ 1694.054826] wlan0: authenticate with 00:14:d1:c8:25:50 (try 1)
Apr  7 10:01:20 Darkan kernel: [ 1694.058475] wlan0: authenticated
Apr  7 10:01:20 Darkan kernel: [ 1694.058555] wlan0: associate with 00:14:d1:c8:25:50 (try 1)
Apr  7 10:01:20 Darkan kernel: [ 1694.063949] wlan0: RX AssocResp from 00:14:d1:c8:25:50 (capab=0x411 status=0 aid=1)
Apr  7 10:01:20 Darkan kernel: [ 1694.063964] wlan0: associated
Apr  7 10:01:27 Darkan dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Apr  7 10:01:27 Darkan dhclient: DHCPOFFER of 192.168.1.115 from 192.168.1.1
Apr  7 10:01:27 Darkan dhclient: DHCPREQUEST of 192.168.1.115 on wlan0 to 255.255.255.255 port 67
Apr  7 10:01:27 Darkan dhclient: DHCPACK of 192.168.1.115 from 192.168.1.1
Apr  7 10:01:27 Darkan avahi-daemon[608]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.115.
Apr  7 10:01:27 Darkan avahi-daemon[608]: New relevant interface wlan0.IPv4 for mDNS.
Apr  7 10:01:27 Darkan avahi-daemon[608]: Registering new address record for 192.168.1.115 on wlan0.IPv4.
Apr  7 10:01:27 Darkan dhclient: bound to 192.168.1.115 -- renewal in 42437 seconds.
Apr  7 10:01:50 Darkan ntpdate[5287]: adjust time server 91.189.94.4 offset 0.029930 sec

```

---

### Post by Ms. Daisy on 2012-04-07
It looks like Ubuntu is talking to the router with IPv6, but there's a line in there indicating that the router isn't IPv6 capable:
```
Apr  7 09:44:43 Darkan kernel: [  698.064207] wlan0: no IPv6 routers present
```

My two thoughts are that perhaps the wireless driver isn't quite right or you need to disable IPv6.  But I would really prefer that someone more knowledgeable chime in before I lead you down an experimental path.

---

### Post by UnknownFearNG on 2012-04-07
I'm sure it's just a warning message. I can turn it off, but would it actually benefit me?

---

### Post by Ms. Daisy on 2012-04-07
Yes, it's a warning message. But my point is that Ubuntu & your router aren't communicating properly.  It seems like a DHCP failure, and that could be caused by a bad wireless driver.  I wonder what would happen if you assigned a static IP to your computer- that would be more of a workaround than a fix.

You can check route- what's the output of
```
route
```

---

### Post by UnknownFearNG on 2012-04-07
Here is the output.

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         TEW-639GR       0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0

```

---

### Post by wildmanne39 on 2012-04-07
Hi, I did not see the output from the other 2 commands I asked you to run in my last post.

It is best to disable IPV6.

It says could not connect because of hidden network do you have yours hidden? if so I would change it to broadcast, because it is not safer with it hidden that is a myth, a hacker can get passed the hidden feature in a few seconds.

Do you have dhcp set as dhclient? I believe that is what is ususally required with wicd.

Set your settings to match the settings in the screenshot.
Thanks

---

### Post by Ms. Daisy on 2012-04-07
> **UnknownFearNG said:**
> I'm sure it's just a warning message. I can turn it off, but would it actually benefit me?
Oh, I misread this the first time. I thought you were talking about turning off the warning message. If you turn off IPv6, then it would force Ubuntu to use IPv4 to talk to the router, and that would ensure that the router understands Ubuntu. As it stands now, it looks to me like the router is just ignoring Ubuntu's IPv6 messages causing time-outs.

I'll look forward to hear if it's resolved when you use Wildemanne39's advice.

---

### Post by UnknownFearNG on 2012-04-07
I can't use Wildemannes39's advice as I use Wicd, not the gnome-networkmanager.

---

### Post by wildmanne39 on 2012-04-07
Hi, you should be able to change your dns server to the one I have in the screenshot and if there is not a place you can disable IPV6 in wicd then you can use this command:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Something must have changed or a configuration file left behind when you installed and uninstalled network manager and reinstalled wicd.

Did you have an upgrade that could have caused this?
Thanks

---

### Post by UnknownFearNG on 2012-04-07
Actually, the above command didn't help at all. I rebooted and it couldn't connect to the router. I commented it out, rebooted, and I was able to connect.

---

