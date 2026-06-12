---
title: "Difficulty with Wireless PCI Adapter"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by Rickx84 on 2012-03-29
Hello Ubuntu community ):P.

I'm relatively new to Ubuntu and have just got a problem that I can't solve myself. I think my biggest problem is I am not fluent in gobbledegook :lolflag:.

I recently bought a wireless PCI adapter (Tenda W322P V2.0) that I can't get to work. I think all the information anyone needs to be able to help me is below:

```
rick@rick-N61PB-M2S:~$ 
rick@rick-N61PB-M2S:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux rick-N61PB-M2S 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:35:26 UTC 2012 i686 GNU/Linux
rick@rick-N61PB-M2S:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:2505]
	Kernel driver in use: forcedeth
--
01:06.0 Network controller [0280]: RaLink Device [1814:3062]
	Subsystem: RaLink Device [1814:3062]
	Kernel driver in use: rt2800pci
rick@rick-N61PB-M2S:~$ lsusb
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rick@rick-N61PB-M2S:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
rick@rick-N61PB-M2S:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
rick@rick-N61PB-M2S:~$ lsmod
Module                  Size  Used by
rfcomm                 33843  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37040  16 rfcomm,bnep
snd_hda_codec_realtek   218460  1 
nvidia               9329739  38 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
arc4                    1165  2 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci               8852  0 
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  1 rt2800pci
rt2x00lib              27307  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231959  3 rt2x00usb,rt2x00pci,rt2x00lib
btusb                  11065  2 
ppdev                   5556  0 
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058  1 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
agpgart                32011  1 nvidia
cfg80211              144758  2 rt2x00lib,mac80211
psmouse                59027  0 
soundcore                880  1 snd
eeprom_93cx6            1345  1 rt2800pci
k10temp                 2607  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
i2c_nforce2             5179  0 
parport                31492  3 ppdev,parport_pc,lp
floppy                 54311  0 
forcedeth              49433  0 
pata_amd                8746  2 
sata_nv                19420  0 
rick@rick-N61PB-M2S:~$
```

I don't know if I'm just being thick, but any attempts I have had to get it working tell me that Autorun cannot be found.

Any help will be greatly appreciated.

Thanks.

Rick

---

### Post by Gleichsnerd on 2012-03-29
Welcome to the Ubuntu Forums, Rick!

Can you quickly plug this into your terminal and post your output?

```
lshw -C network
```

Cheers!

---

### Post by wildmanne39 on 2012-03-29
Hi, I left a response in the other thread you posted in.
Thanks

---

### Post by Rickx84 on 2012-03-29
```
rick@rick-N61PB-M2S:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wlan0
       version: 00
       serial: c8:3a:35:ca:e3:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-32-generic firmware=N/A latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:fdff0000-fdffffff
rick@rick-N61PB-M2S:~$ 

```

---

### Post by Bucky Ball on 2012-03-29
Right click on network icon, go to the 'Wireless' tab and input the correct details for the router/access point manually: ESSID (AP name) and security key (with the correct security type). Click on 'Connect Automatically' and 'Available to all users' if they are not already clicked. 

Have you gotten online with a cable (with the wireless dongle plugged in) and gotten updates?

---

### Post by SeijiSensei on 2012-03-29
I gave up trying to get my rt2500usb based device (a Linksys) to work reliably with Ubuntu.  I sprung for $20 or so and bought [this Atheros-based device]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045").  So far it's been rock-solid.

---

### Post by Rickx84 on 2012-03-29
I've tried all that with no success. All the info has been checked over and over. Wireless Networks is not available in the Network Manager even though Enable Wireless is ticked . I do get online with a cable, with or without the adapter.

---

### Post by Bucky Ball on 2012-03-29
So you have plugged in the adapter, plugged in a cable, gotten online and done an update?

After this, check 'Additional Drivers' and see if there is anything disabled for the wireless.

---

### Post by Rickx84 on 2012-03-29
> **wildmanne39 said:**
> Hi, I left a response in the other thread you posted in.
Thanks
Hi Wildmanne,

I checked your reply in the other thread:
Hi, please do:
Code:
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
Then unplug your wired connection and reboot does it work?
Thanks

and would prefer to answer here (can never find the other one, lol). I've tried that. . . that doesn't work either :(.

---

### Post by Rickx84 on 2012-03-29
> **Bucky Ball said:**
> So you have plugged in the adapter, plugged in a cable, gotten online and done an update?

After this, check 'Additional Drivers' and see if there is anything disabled for the wireless.
Hi Bucky,

No success with those, either.
(I have done an update and checked for drivers)

---

### Post by wildmanne39 on 2012-03-29
Hi, let's troubleshoot further please post the output of the following commands by copying and pasting for accuracy:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
nm-tool
sudo iwlist scan
ndiswrapper -l
lsmod | grep rt2
```
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.

I know some of this is in the other thread but it will be much easier for me to keep track of all in one thread.
Thank you

---

### Post by Rickx84 on 2012-04-14
I have now "upgraded?" to Ubuntu 11.10 (and seriously unhappy with it) and having the same problems with wireless.

I've done as requested with the codes (I don't know if the upgrade will make any difference).

```
rick@rick-N61PB-M2S:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux rick-N61PB-M2S 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux
rick@rick-N61PB-M2S:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:2505]
	Kernel driver in use: forcedeth
--
01:08.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Ralink corp. Device [1814:3062]
	Kernel driver in use: rt2800pci
rick@rick-N61PB-M2S:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
rick@rick-N61PB-M2S:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
rick@rick-N61PB-M2S:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
rick@rick-N61PB-M2S:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        C8:3A:35:CA:E3:BE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:30:67:60:AA:51

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


rick@rick-N61PB-M2S:~$ sudo iwlist scan
[sudo] password for rick: 
Sorry, try again.
[sudo] password for rick: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

rick@rick-N61PB-M2S:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
rick@rick-N61PB-M2S:~$ lsmod | grep rt2
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172427  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
rick@rick-N61PB-M2S:~$ sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n55
Apr 14 01:40:53 rick-N61PB-M2S NetworkManager[845]: <info> kernel firmware directory '/lib/firmware' changed
Apr 14 01:49:11 rick-N61PB-M2S NetworkManager[845]: <info> kernel firmware directory '/lib/firmware' changed
Apr 14 02:17:31 rick-N61PB-M2S NetworkManager[913]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 14 02:43:59 rick-N61PB-M2S NetworkManager[905]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 14 10:34:03 rick-N61PB-M2S NetworkManager[879]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 14 17:11:26 rick-N61PB-M2S kernel: [   17.471190] rt2800pci 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Apr 14 17:11:26 rick-N61PB-M2S kernel: [   17.471198] rt2800pci 0000:01:08.0: setting latency timer to 64
Apr 14 17:11:26 rick-N61PB-M2S kernel: [   17.694667] Registered led device: rt2800pci-phy0::radio
Apr 14 17:11:26 rick-N61PB-M2S kernel: [   17.694682] Registered led device: rt2800pci-phy0::assoc
Apr 14 17:11:26 rick-N61PB-M2S kernel: [   17.694697] Registered led device: rt2800pci-phy0::quality
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/wlan0, iface: wlan0)
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): now managed
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 14 17:11:26 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): bringing up device.
Apr 14 17:11:27 rick-N61PB-M2S kernel: [   18.356154] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
Apr 14 17:11:27 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): preparing device.
Apr 14 17:11:27 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 14 17:11:27 rick-N61PB-M2S dbus[921]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Apr 14 17:11:27 rick-N61PB-M2S kernel: [   18.380375] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 14 17:11:27 rick-N61PB-M2S dbus[921]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Apr 14 17:11:28 rick-N61PB-M2S NetworkManager[939]: <info> wpa_supplicant started
Apr 14 17:11:28 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 14 17:11:28 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 14 17:11:28 rick-N61PB-M2S NetworkManager[939]: <info> (wlan0): supplicant interface state: ready -> inactive
rick@rick-N61PB-M2S:~$ 
```

Reading through some of the problems everyone is having with Ubuntu, it makes me wonder, is it really worth keeping?

---

### Post by anewguy on 2012-04-14
First, my sympathies.  Sometimes wireless or video can be a little tricky to get working.  One thing to remember - of all the posts on the forum which make you think ubuntu is full of problems, I can guarantee you there are hundreds of thousands if not millions of us that normally don't have problems - you just don't see us posting to say "everything works great".

I need to do more research, but so far it looks to me like you need a 3062 driver - that's the model that's actually coming back for that PCI id.  Since it is showing the rt2800pci driver, my first suspicion is that that will need to be blacklisted and another driver used.  I just need to find that driver.

Also, wildmanne39 who has been trying to help you is very good at wireless support - if he posts things for you, I suggest doing them.  Remember he is normally trying to walk you through a step at a time, so don't expect the first thing to make it work.  Identifying the problem usually takes a little time.

In the mean time, I'll keep looking.  There are some posts on the net itself for ubuntu 11.10 and the 3062, I just need some time to read through them.

Dave ;)

---

### Post by kurt18947 on 2012-04-14
> **SeijiSensei said:**
> I gave up trying to get my rt2500usb based device (a Linksys) to work reliably with Ubuntu.  I sprung for $20 or so and bought [this Atheros-based device]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045").  So far it's been rock-solid.

That is certainly the simplest and least time consuming solution.  I've learned to do a little home work when shopping for hardware on Linux machines.  Some hardware is plug -n- play, others makes me want to emulate that fella on Youtube with the .45 and the daughter's laptop.

---

### Post by wildmanne39 on 2012-04-15
Hi, please do:
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```

Add a single line:

```
options rt2800pci nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by Rickx84 on 2012-04-16
Hello again Wildmanne.

Apologies for absence, but had real life problems that needed sorting first.
Your help is very much appreciated. . . even though I still have no wireless, it is all helping me to understand a bit more about Ubuntu.

I've tried everything in this thread since I changed over to 11.10, including your last post, all with no success. I'm not sure what I was supposed to be proof reading in Gedit, but everything looked in order to me (but that's no guarantee of anything, lol). I think my frustration has showed in some of the things I have said, but I try to be patient. Nothing's broken yet though, lol.

---

### Post by wildmanne39 on 2012-04-16
Hi, this is a problem. > rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
have you installed all updates since you installed 11.10? 

Did you install the wireless driver yourself and how did you do it?

Did you do a fresh install of ubuntu or did you upgrade?

Please post the contents of:
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by Rickx84 on 2012-04-24
I've had enough!

I've decided to give up on Ubuntu.

Apart from the wireless problems and other things I can't get to work on it, I really do not like 11.10 at all. I've had a look at 12.04 as an alternative, but it looks pretty much the same to me. As I am the user on this PC, I can honestly say that Ubuntu is no longer user friendly. It doesn't like me and I don't like it.
I liked 10.10, but too many changes have been made.

I'll make do with a wired connection until I find a suitable alternative. . . but I definitely think I would prefer to go back to Windows (apologies for the bad language) than carry on with this.

---

### Post by wildmanne39 on 2012-04-24
Hi, I am sorry to hear that if you decide to come back at a later time I am sure people will be here to help if needed.

---

### Post by Bucky Ball on 2012-04-25
Why not try Xubuntu? The desktop environment will be much more familiar. Or Gnome fallback (Gnome Classic) in 12.04? Either way, good luck with your computing ...

---

