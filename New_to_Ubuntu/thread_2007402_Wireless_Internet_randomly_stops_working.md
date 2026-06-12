---
title: "Wireless Internet randomly stops working"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by ebodnaruk on 2012-06-20
Hi I've been running Ubuntu for a few years now, and in the past year or two something strange has been happening.  I'll be able to access the internet just fine on Ubuntu, then it will stop one day.  Anywhere from a few weeks to a few months later it will just start working.  Then it will last again for a few months.  I have no idea why!  

I read one post which said to change the following file:  /etc/NetworkManager/nm-system-settings.conf  I changed 'managed = false' to 'managed = true' after the [ifupdown] part.  

Here's some info:

ethan@eefieb:~$ cat /etc/lsb-release; uname -a 
	DISTRIB_ID=Ubuntu 
	DISTRIB_RELEASE=10.04 
	DISTRIB_CODENAME=lucid 
	DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS" 
	Linux eefieb 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 	GNU/Linux 

lspci -nnk | grep -iA2 net 
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13) 
	Kernel driver in use: sky2 
	Kernel modules: sky2 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01) 
	Kernel driver in use: wl 
	Kernel modules: wl, ssb 

lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 1058:071a Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 

rfkill list all 
0: dell-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 

lsmod 
Module                  Size  Used by 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               5412  1 snd_hda_codec 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1338  0 
dell_wmi                1793  0 
snd_seq_oss            26722  0 
i915                  289715  3 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
lib80211_crypt_tkip     7596  0 
snd_timer              19130  2 snd_pcm,snd_seq 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
drm_kms_helper         29329  1 i915 
ses                     5907  0 
dell_laptop             6888  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
dcdbas                  5422  1 dell_laptop 
psmouse                63677  0 
serio_raw               3978  0 
enclosure               6624  1 ses 
drm                   163747  4 i915,drm_kms_helper 
soundcore               6620  1 snd 
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl 
intel_agp              24375  2 i915 
agpgart                31724  2 drm,intel_agp 
i2c_algo_bit            5028  1 i915 
video                  17375  1 i915 
output                  1871  1 video 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
lp                      7028  0 
parport                32635  2 ppdev,lp 
usb_storage            40033  1 
sky2                   40807  0 
ahci                   32680  2 


Thanks so much for your help!  I hate being so clueless on this stuff!

Best,
Ethan

---

### Post by chili555 on 2012-06-21
Please open a terminal and try this:```
sudo su
modprobe wl
echo wl >> /etc/modules
exit
```Does it work now? Please post back if it still doesn't perform as expected.> I hate being so clueless on this stuff!
No worries. All of us, even Dr. Chili and even Linus Torvalds didn't know very much about all this once upon a time.

---

### Post by ebodnaruk on 2012-06-21
Hi Chili555,

Thanks so much for your time in trying to help me!

I tried what you wrote, but it didn't work.  I also tried changing the [ifupdown] thing back to false, that I mentioned in my original post.  No clue what I'm doing!

I'd appreciate any other ideas you'd have!

Best,
Ethan

---

### Post by chili555 on 2012-06-21
Let's do some diagnostics. Please run and post:```
dmesg | grep -e wlan -e wl
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by ebodnaruk on 2012-06-21
Hi Doc,

A diagnosis sounds like a good idea.  I hope it's not terminal!  ;-)

Here's the output: (nice and short)

ethan@eefieb:~$ dmesg | grep -e wlan -e wl 
[   25.238151] wl: module license 'MIXED/Proprietary' taints kernel. 
[   25.334189] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   25.334203] wl 0000:0c:00.0: setting latency timer to 64

---

### Post by chili555 on 2012-06-22
I made a mistake and I'm sorry about that:> [COLOR="Red"]eth1[/COLOR] IEEE 802.11 Access Point: Not-Associated
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0I really should have asked for:```
dmesg | grep eth1
```So far, your readings look pretty solid!

---

### Post by ebodnaruk on 2012-06-22
No problem!  Here's the info:

 dmesg | grep eth1 
[25.373687] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 


Thanks so much for your continued help!!

Best,
Ethan

---

### Post by chili555 on 2012-06-22
I see nothing whatever that is wrong or even slightly suspicious. I assume it's because it's working fine today. Is that correct? I am interested in this comment:> I tried what you wrote, but it didn't work. What exactly didn't work? Did your wireless stop working suddenly or what?

---

### Post by NikTh on 2012-06-22
> **ebodnaruk said:**
> 
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 
Hi,
This is a very bad link quality at my opinion. Of course **chili555** is one of the "masters" of wireless in here and sorry for interrupt , but try an easy thing:

Go to your router's configuration page and try to change channel or connection protocol (b,g,n) and see if something change. You will see multiple numbers for channel there , try 2 or 3 randomly . Sometimes maybe channel be responsible for such behavior . 
Thanks

---

### Post by ebodnaruk on 2012-06-22
Hey there!

I can't access the internet using Ubuntu.  It's so weird!  I have an Ubuntu/Windows dual boot setup, so I post to this forum using Windows and I go back into Ubuntu to run the code you post, save it on a flash drive, then boot back into Windows to report.

Earlier when I wrote "I tried what you said but it didn't work"  I meant that I typed what you said (the block starting with sudo su and ending with exit) and it didn't work in restoring the internet.  

This mysterious problem has happened a few times in the past, and I've always adjusted by just using windows instead of Ubuntu.  However, I have some work that's easier to do in a Linux environment so I'm trying harder this time to figure out why I can't access the internet!  

Thanks so much!
Ethan

---

### Post by ebodnaruk on 2012-06-22
I also can't access the internet when I plug my computer directly into the Fios router with an ethernet cable.  

I tried connecting on a different network other than my home network as well, and it works with Windows but again not with Ubuntu.  I'm so stumped!


For the other user who had a suggestion:
   I checked the channel value as you said, and found that it was set to "Automatic".  I didn't want to mess with it in case that makes it worse.  But if the Doctor doesn't have any more ideas I can certainly give it a shot!  I was only able to access the router page in Windows, not Ubuntu.  

Thanks for your help!!!
Ethan

---

### Post by chili555 on 2012-06-22
> [QUOTE]Originally Posted by ebodnaruk 
eth1 IEEE 802.11 Access Point: [COLOR="Red"]Not-Associated[/COLOR]
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0
Hi,
This is a very bad link quality at my opinion.[/QUOTE]I don't think the signal quality is at all meaningful if you are not connected.> I also can't access the internet when I plug my computer directly into the Fios router with an ethernet cable. Ah, haaa! I wonder if you don't have a configuration problem and not a driver problem. In Windows, with an ethernet connection, do you need to give any details? A user name and password? Are you given and need to use a static IP address? Tell us more.

---

### Post by ebodnaruk on 2012-06-22
> **chili555 said:**
> Ah, haaa! I wonder if you don't have a configuration problem and not a driver problem. In Windows, with an ethernet connection, do you need to give any details? A user name and password? Are you given and need to use a static IP address? Tell us more.


For both systems (Ubuntu and Windows) I had to provide all the usual info:  Network Name, SSID, WEP password.  I never change these.  Literally, I could access the internet in Ubuntu for months, and a few days ago it just stopped.  I couldn't think of ANYTHING I'd done differently.  And it's happened like that before, then seemingly magically after some period of time of weeks to months I'll boot up Linux and it'll work again. (But not on previous attempts).  

So I've included some screenshots of the wireless setup.  I also have a little weather program installed that will give me the current temperature on the toolbar on the top right part of my screen next to the "power down" button.  This gives me the first visual hint of whether or not my Ubuntu system is connecting to the internet.  If it updates with a reasonable temperature value, I know it's connected.  If it stays a -- or says 0 deg F I know it's not connected.  I've also attached a screenshot of that menu bar. (The -- to the left of the red power button is what I'm talking about)

I would also be inclined to think it's some sort of configuration issue rather than a driver issue because I can't imagine the driver having problems on and off over a period of years.  But I also wouldn't think the configuration would magically change over time!  Who knows.  

Thanks so much for your help!
Ethan

---

### Post by chili555 on 2012-06-22
Your settings look entirely normal. I wonder what Network Manager is doing all this time:```
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```

What do the wired ethernet settings look like? Have you tried a power reset of the router? Unplug it, count to eleven and plug it back in. Does anything change?

---

### Post by ebodnaruk on 2012-06-22
Here's the output:

ethan@eefieb:~$ sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20 
Jun 22 12:28:56 eefieb NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. 
Jun 22 12:28:56 eefieb NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list. 
Jun 22 12:28:56 eefieb NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>) 
Jun 22 12:28:56 eefieb kernel: [   26.592906] type=1505 audit(1340382536.545:7):  operation="profile_replace" pid=869 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
Jun 22 12:28:56 eefieb NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file 
Jun 22 12:28:56 eefieb NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file 
Jun 22 12:28:56 eefieb NetworkManager:    SCPlugin-Ifupdown: (150628080) ... get_connections. 
Jun 22 12:28:56 eefieb NetworkManager:    SCPlugin-Ifupdown: (150628080) ... get_connections (managed=false): return empty list. 
Jun 22 12:28:56 eefieb NetworkManager:    Ifupdown: get unmanaged devices count: 0 
Jun 22 12:28:56 eefieb NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01). 
Jun 22 12:28:56 eefieb NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl') 
Jun 22 12:28:56 eefieb NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0 
Jun 22 12:28:56 eefieb NetworkManager: <info>  (eth0): carrier is OFF 
Jun 22 12:28:56 eefieb NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2') 
Jun 22 12:28:56 eefieb NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1 
Jun 22 12:28:56 eefieb NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files 
Jun 22 12:28:56 eefieb NetworkManager: <info>  modem-manager is now available 
Jun 22 12:28:56 eefieb NetworkManager: <info>  Trying to start the supplicant... 
Jun 22 12:28:56 eefieb NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle 
Jun 22 12:28:56 eefieb avahi-daemon[865]: Network interface enumeration completed. 

I'll try the router power on/off after I hear back from you on the above stuff.  It's silly but I'm afraid to possibly mess things up more by messing with the router.  But I'll do it!  

Thanks so much!
Ethan

---

### Post by ebodnaruk on 2012-06-22
I also tried unplugging the router and restarting it.  Still have no problems with Windows, but no internet with Ubuntu!

---

### Post by anewguy on 2012-06-23
I noticed you seem to be running 10.04.  Do you remember if Ubuntu had updates go through prior to this starting?  It's quite possible that some module, heck maybe even a kernel update, could have corrupted this.


With 10.04, it seems some people also installed the b43-firmware-cutter first THEN installed and used the B43 driver and blacklisted WL.  I don't know the state of 10.04 now, so I don't know if any of these things still apply.  Chili555 really is the expert in this area - I just thought I'd throw these outdated, but possibly still valid since you run 10.40, ideas out there.

---

### Post by chili555 on 2012-06-23
I am very concerned that two interfaces, wired and wireless, both with working and usually reliable drivers, don't connect. If you don't mind, for now, I'd like to concentrate on wired. Please flip the wireless switch off and hook up a known good ethernet cable. Let Network Manager try to connect. Then run and post:```
nm-tool
sudo cat /var/log/syslog | grep -e etwork -e sky
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/NetworkManager/nm-system-settings.conf
```One of the latter two will be 'file not found.' Simply post the one you do have.

---

### Post by ebodnaruk on 2012-06-23
> **anewguy said:**
> I noticed you seem to be running 10.04.  Do you remember if Ubuntu had updates go through prior to this starting?  It's quite possible that some module, heck maybe even a kernel update, could have corrupted this.


With 10.04, it seems some people also installed the b43-firmware-cutter first THEN installed and used the B43 driver and blacklisted WL.  I don't know the state of 10.04 now, so I don't know if any of these things still apply.  Chili555 really is the expert in this area - I just thought I'd throw these outdated, but possibly still valid since you run 10.40, ideas out there.

I've wondered this myself.  When my system boots up I can choose earlier kernels.  I've tried a few of them to see if I can connect with them, but I haven't tried them all methodically.  

I'll try this since it's fast, and concentrate on Dr. Chili's advice below as well!  Thanks for your input!

---

### Post by anewguy on 2012-06-23
DEFINITELY do everything chili555 wants you to!  I didn't mean to butt in here, so I'm going to fade away and let chili555 handle it with you.  He is very much the expert!

---

### Post by chili555 on 2012-06-23
Thanks for your confidence, guys! If you have the firmware, you can easily try b43/ssb instead of wl. It costs only a few moments to test and is easily reversible. Verify you have the needed firmware:```
ls /lib/firmware/b43
```Is there a whole list of firmware files there? If so, let's try:```
sudo modprobe -r wl
sudo modprobe b43
```Does it work as expected? If so, we'll change a file or two and make it persistent and then fall off our chairs in shock. Get the paddles ready.

If not, reverse it:```
sudo modprobe -r b43
sudo modprobe wl
```

---

### Post by oldrocker99 on 2012-06-23
Chili, I've been having the same sort of problems with my Acer Aspire 5516 with a Broadcom BCM4312. I read what you said above and installed the b43 firmware and modprobe -r wl, then modprobe b43. No success, either. My results have been similar to those already listed.

This IS frustrating; I eagerly await some more wisdom.

Xubuntu 12.04 64 bit, 3.75 GB RAM.

---

### Post by chili555 on 2012-06-23
> **oldrocker99 said:**
> Chili, I've been having the same sort of problems with my Acer Aspire 5516 with a Broadcom BCM4312. I read what you said above and installed the b43 firmware and modprobe -r wl, then modprobe b43. No success, either. My results have been similar to those already listed.

This IS frustrating; I eagerly await some more wisdom.

Xubuntu 12.04 64 bit, 3.75 GB RAM.Is your pci.id the same? 14e4:4315? Did you try the fix in post #2?

---

### Post by oldrocker99 on 2012-06-24
I tried the fix in post #2 first thing when I found this thread. No success. My wired Ethernet has sometimes been spotty (which could be the cable). When I log in, I get a wireless connection enabled notification. As soon as I try to use it, it drops, asking repeatedly for the WPA2 Personal password (which is already entered in the request). 

Feh.

---

### Post by chili555 on 2012-06-25
Please post:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl -e ndis
iwconfig
```Thanks.

---

### Post by ebodnaruk on 2012-06-25
> **chili555 said:**
> Thanks for your confidence, guys! If you have the firmware, you can easily try b43/ssb instead of wl. It costs only a few moments to test and is easily reversible. Verify you have the needed firmware:```
ls /lib/firmware/b43
```Is there a whole list of firmware files there? If so, let's try:```
sudo modprobe -r wl
sudo modprobe b43
```Does it work as expected? If so, we'll change a file or two and make it persistent and then fall off our chairs in shock. Get the paddles ready.

If not, reverse it:```
sudo modprobe -r b43
sudo modprobe wl
```

Hey Chili,

Sorry I've been out of touch - was away for the weekend.

I don't have the b43 firmware so wasn't able to try that.  

I also don't have an ethernet cable (!)  but will be at the office tomorrow and will try it out there. 

Thanks so much!
Ethan

---

### Post by ebodnaruk on 2012-06-25
> **chili555 said:**
> Please post:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl -e ndis
iwconfig
```Thanks.

Did you want me to post this too, or just Oldrocker?

---

### Post by chili555 on 2012-06-25
> **ebodnaruk said:**
> Did you want me to post this too, or just Oldrocker?Just oldrocker99, please.

---

### Post by oldrocker99 on 2012-06-25
Here it is:

>lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

>lsmod | grep -e b43 -e wl -e ndis
wl                   2568210  0 
lib80211               14381  2 lib80211_crypt_tkip,wl

>iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:194  Noise level:199
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

eth0      no wireless extensions.


I **SO** appreciate your assistance, Chili; the best reason to use Linux is the Ubuntu forums. No kidding.

---

### Post by chili555 on 2012-06-25
The only driver that's loaded is the correct driver wl, also known as the Broadcom STA driver. As you have already shown, b43 and its firmware don't work. I am a bit puzzled by this:> eth1 IEEE 802.11 Access Point: Not-Associated
[COLOR="Red"]Link Quality:4[/COLOR] Signal level:194 Noise level:199
Rx invalid nwid:0 invalid crypt:1 invalid misc:0Yikes! I'm not sure the link quality means much when you are not connected. It might help to see the numbers when you have a connection. I'd also like to see scan results:```
sudo iwlist eth1 scan
```Thanks.

Here, for comparison, is the link quality on my machine:> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:13:10:62:8D:xx   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=[COLOR="Red"]40[/COLOR]/70  Signal level=-70 dBm  
40/70 is not a great number, but I stay connected.

---

### Post by oldrocker99 on 2012-06-25
Here you go:

sudo iwlist eth1 scan
[sudo] password for oldrocker99: 
eth1      Scan completed :
          Cell 01 - Address: 00:1E:E5:FD:8A:37
                    ESSID:"oldrocker99"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-71 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

This is from upstairs in my house (the router is downstairs), where I also have my desktop, which uses a Linksys AE1000 USB receiver, which works great. I may just use it for this little kinda crappy lappy, but let's keep trying!

---

### Post by chili555 on 2012-06-25
> sudo iwlist eth1 scan
[sudo] password for oldrocker99:
eth1 Scan completed :
Cell 01 - Address: 00:1E:E5:FD:8A:37
ESSID:"oldrocker99"
Mode:Managed
Frequency=2.412 GHz (Channel 1)
[COLOR="Red"]Quality:2/5[/COLOR] Signal level:-71 dBm Noise level:-92 dBm
[COLOR="Red"]IE: IEEE 802.11i/WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
[COLOR="Red"]IE: WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Encryption key: onThe signal level is pretty low. You might experiment with different channels to see if that helps. You might have better luck with WPA2 only and not WPA and WPA2 mixed mode. Finally, some routers have variable power settings. I suggest you look and see if your connectivity can be improved by carefully inching the setting up. Be cautious as increased transmit power equals heat which often equals reduced lifespan. Please see attached.

---

### Post by ravikanth1988 on 2012-06-25
Hey Chilli,
I tried some of the commands which you suggested in thread for the sake of diagnostics. Can you please look into it?(last post)

[http://ubuntuforums.org/showthread.php?t=2010190](http://ubuntuforums.org/showthread.php?t=2010190)

---

### Post by ebodnaruk on 2012-06-26
> **chili555 said:**
> I am very concerned that two interfaces, wired and wireless, both with working and usually reliable drivers, don't connect. If you don't mind, for now, I'd like to concentrate on wired. Please flip the wireless switch off and hook up a known good ethernet cable. Let Network Manager try to connect. Then run and post:```
nm-tool
sudo cat /var/log/syslog | grep -e etwork -e sky
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/NetworkManager/nm-system-settings.conf
```One of the latter two will be 'file not found.' Simply post the one you do have.

Chili,

I'm running into all sorts of problems now.  Yesterday I installed a bunch of programs on Ubuntu (downloading from Windows dual boot and transferring over via external HD) for dealing with NetCDF, a scientific data format and language.  

I started to work on the wired internet analysis you requested, and now Ubuntu doesn't even load!  It quickly flashes some I/O error stuff, then loads the Ubuntu screen, makes the little drum noise, but the password menu doesn't appear and the desktop icons don't load.  

Do you think I should just do a fresh installation of 12.04 LTS or something? 


Then on the topic of wired internet:  My Windows dual boot can connect to the wireless internet.  I turn off the wireless and plug in the ethernet cable known to work on a desktop (I switch back and forth) and my computer doesn't even recognize the LAN!  Ugh.  This is not good.

Sorry this is so complicated.  

Thanks again for your help!
Ethan

---

### Post by Ashtonford on 2012-06-26
> **ebodnaruk said:**
> Hi I've been running Ubuntu for a few years now, and in the past year or two something strange has been happening.  I'll be able to access the internet just fine on Ubuntu, then it will stop one day.  Anywhere from a few weeks to a few months later it will just start working.  Then it will last again for a few months.  I have no idea why!  

I read one post which said to change the following file:  /etc/NetworkManager/nm-system-settings.conf  I changed 'managed = false' to 'managed = true' after the [ifupdown] part.  

Here's some info:

ethan@eefieb:~$ cat /etc/lsb-release; uname -a 
	DISTRIB_ID=Ubuntu 
	DISTRIB_RELEASE=10.04 
	DISTRIB_CODENAME=lucid 
	DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS" 
	Linux eefieb 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 	GNU/Linux 

lspci -nnk | grep -iA2 net 
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13) 
	Kernel driver in use: sky2 
	Kernel modules: sky2 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01) 
	Kernel driver in use: wl 
	Kernel modules: wl, ssb 

lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 1058:071a Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 

rfkill list all 
0: dell-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 

lsmod 
Module                  Size  Used by 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               5412  1 snd_hda_codec 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1338  0 
dell_wmi                1793  0 
snd_seq_oss            26722  0 
i915                  289715  3 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
lib80211_crypt_tkip     7596  0 
snd_timer              19130  2 snd_pcm,snd_seq 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
drm_kms_helper         29329  1 i915 
ses                     5907  0 
dell_laptop             6888  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
dcdbas                  5422  1 dell_laptop 
psmouse                63677  0 
serio_raw               3978  0 
enclosure               6624  1 ses 
drm                   163747  4 i915,drm_kms_helper 
soundcore               6620  1 snd 
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl 
intel_agp              24375  2 i915 
agpgart                31724  2 drm,intel_agp 
i2c_algo_bit            5028  1 i915 
video                  17375  1 i915 
output                  1871  1 video 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
lp                      7028  0 
parport                32635  2 ppdev,lp 
usb_storage            40033  1 
sky2                   40807  0 
ahci                   32680  2 


Thanks so much for your help!  I hate being so clueless on this stuff!

Best,
Ethan





was having the same thing happening but this fixed it for me
after spending some time trying to fix the problem with my b43 card (Broadcom Corporation BCM4312 802.11b/g (rev 01) on HP ProBook 5310m) I found the solution and now the card is working pretty stable.
The problem was that each time 6 seconds after each AP association  the connection was dropped with this error in the dmesg:
No probe response from AP xxxxxxxxxxxxx after 500ms, disconnecting
The fix is to disable the QOS of the driver.
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf

---

### Post by chili555 on 2012-06-26
I'd boot into recovery mode at the GRUB menu and see what messages are scrolling by as it's not loading a desktop. You might check:```
dmesg | less
```The *less* will allow you to scroll back and forth with the arrow keys; get out of *less* with q. You might also look at:```
sudo cat /var/log/syslog | tail -n25
```*tail* will let you see the last 25 lines posted during boot; hopefully containing the glitch.

I suspect it may be a graphics problem so you might also check:```
sudo cat /var/log/Xorg.0.log | grep -e EE -e WW
```As you may guess EE are errors and WW are warnings.

We are quickly surpassing my limited scope of knowledge.

---

### Post by chili555 on 2012-06-26
> **Ashtonford said:**
> was having the same thing happening but this fixed it for me
after spending some time trying to fix the problem with my b43 card (Broadcom Corporation BCM4312 802.11b/g (rev 01) on HP ProBook 5310m) I found the solution and now the card is working pretty stable.
The problem was that each time 6 seconds after each AP association  the connection was dropped with this error in the dmesg:
No probe response from AP xxxxxxxxxxxxx after 500ms, disconnecting
The fix is to disable the QOS of the driver.
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf@ebodnaruk--

You are not using b43, so this won't help you but will probably help those that do. Thanks, Ashtonford.

---

### Post by ebodnaruk on 2012-06-26
> **chili555 said:**
> I'd boot into recovery mode at the GRUB menu and see what messages are scrolling by as it's not loading a desktop. You might check:```
dmesg | less
```The *less* will allow you to scroll back and forth with the arrow keys; get out of *less* with q. You might also look at:```
sudo cat /var/log/syslog | tail -n25
```*tail* will let you see the last 25 lines posted during boot; hopefully containing the glitch.

I suspect it may be a graphics problem so you might also check:```
sudo cat /var/log/Xorg.0.log | grep -e EE -e WW
```As you may guess EE are errors and WW are warnings.

We are quickly surpassing my limited scope of knowledge.

Chili,

So I booted in recovery mode and was presented with a list of options.  I first booted in low graphic failsafeX mode, but it didn't load the desktop.  Next time I booted in root (figured that would give me the command line)

I typed dmesg | less and got a TON of output.  The significant-looking stuff I type below:

dcdbas dcdbas: Dell Systems Management Base Driver (verson 5.6.0-3.2)
[drm] INitialize drm 1.1.0 20060810
[25.786574] Buffer I/O error on device sr0, logical block 0.
    sr 2:0:0:0  [sr0] Result: hostbyte = DID_OK driverbyte = DRIVER_SENSE
    sr 2:0:0:0   Sense key: Illegal Request [current]
                 Add Sense:  Illegal mode for this track
                 CDB: Read(10): 28 00 00 00 00 00 00 00 02 00.


This block was basically repeated again (starting at Buffer I/O Error)

Then another Buffer I/O error with a different second line:

agpart-intel 0000:00:00:0 AGP aperture is 256M @ 0xe0000000
then all the same stuff with the 2:0:0:0 illegal request illegal mode junk.  

Repeated 6 times

Skip down a bunch...

eth1: Broadcom BCM 4315 802.11 Hyrbrid Wireless 

   then more of the error stuff same as above.

end_request I/O error, dev sr0, sector 0. 
With all the sr 2:0:0:0 junk, 
Repeat 15 times.

I start to notice that the sector number is different sometimes:  0, 8, 24, 56, 120, 16.

Then at the very bottom:

[27.267962] registered panic notifier
vga16fb: initializing 
vga16fb: mapped to 00xc00a0000
vga16fb: not registering due to another framebuffer present

[27.512188] sky2 eth0: enabling interface
       ADDRCONF (NETDEV_UP): eth0: link is not ready
[37.664041] eth1: no IPv6 router present.


Most of the lines had [27.something] and this last one had  [37.664041].  Maybe it got thru a lot of error-free stuff until there?  


SECOND SET OF CODE YOU RECOMMENDED:  (-n25)

avahi_daemon  Registered new additional record for fe80:blah:blah:blah on eth1.*.

Then there were a bunch of these lines:

wpa_supplicant [898: WPS_AP_AVAILABLE


THIRD SET OF CODE  (with the EE's and WW's):

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist
(II) Loading extension MIT_SCREEN_SAVER
(WW) Falling back to old probe method for vcsa
(WW) Falling back to old probe method for fbdev

HOpe this makes some sense to you!

Thanks again for all your help!
Ethan

---

### Post by chili555 on 2012-06-26
> [25.786574] Buffer I/O error on device sr0, logical block 0.
sr 2:0:0:0 [sr0] Result: hostbyte = DID_OK driverbyte = DRIVER_SENSE
sr 2:0:0:0 Sense key: Illegal Request [current]
Add Sense: Illegal mode for this trackThis is simply your CD drive having difficulty. Is there a CD in there? I'd try to remove it and try again.

As I said, we are quickly surpassing my limited scope of knowledge. I suggest you look for errors after you remove the CD and post here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Of course, a reinstall is a 20 minute process, so I'm always a bit reluctant to spend 3 hours solving a 20 minute problem, aside, of course, from general curiousity.

---

### Post by ebodnaruk on 2012-06-26
I ran the -n25 part again and got a somewhat different output, some of which seems related to networking issues:

NetworkManager brings up device eth0, prepares it, deactivates it (reason 2).  Added default wired connection 'Auto eth0' for sys/devices/pc blah blah

NetworkManager: <WARN> default_adapter_eb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
<info> modem-manager is now available
<info> Trying to start the supplicant...
kernel:  [   27.blah] sky2 eth0: enabled

NetworkManager: <info> (eth1): supplicant manager state:  down -> idle
                 <info> (eth1): device state change: 2 -> 3 (reason 0)
                  <info> (eth1): supplicant interface state:  starting -> ready
      
Also says eth1: no Ipv6 router present
Then it gives 7 wpa_supplicant[898] WPS-AP_AVAILABLE

---

### Post by ebodnaruk on 2012-06-26
> **chili555 said:**
> This is simply your CD drive having difficulty. Is there a CD in there? I'd try to remove it and try again.

As I said, we are quickly surpassing my limited scope of knowledge. I suggest you look for errors after you remove the CD and post here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Of course, a reinstall is a 20 minute process, so I'm always a bit reluctant to spend 3 hours solving a 20 minute problem, aside, of course, from general curiousity.

Wow, I feel silly that some of this was just due to a CD!  

Well I tried it all again and I got all of the same stuff except the error you pointed out as being due to the CD.  

When I boot up, now it lets me see and move the mouse pointer but the password screen and desktop don't load.  

I think at this point I'd just like to re-install Ubuntu, with 12.04 maybe.  Would it be best to just download and make a CD and install it through Windows?  (I want to keep a dual boot)

Thanks so much!
Ethan

---

### Post by chili555 on 2012-06-26
> Would it be best to just download and make a CD and install it through Windows? (I want to keep a dual boot)That's what I recommend.

---

### Post by ebodnaruk on 2012-06-26
> **chili555 said:**
> That's what I recommend.

Alright, thanks so much for your help.  I feel like I should have just reinstalled from the get-go since I knew I was out of date with 10.04!  

Oh well, hopefully the new installation will make everything work smoothly!  

I'll be sure to post my problems if any come up!

Thanks,
Ethan

---

### Post by ebodnaruk on 2012-06-27
I installed 12.04 LTS and everything works wonderfully!

Thanks for your help!!!
Ethan

---

### Post by oldrocker99 on 2012-06-27
> **chili555 said:**
> The signal level is pretty low. You might experiment with different channels to see if that helps. You might have better luck with WPA2 only and not WPA and WPA2 mixed mode. Finally, some routers have variable power settings. I suggest you look and see if your connectivity can be improved by carefully inching the setting up. Be cautious as increased transmit power equals heat which often equals reduced lifespan. Please see attached.

When I have the laptop within 6" of the router, the same thing happens; it connects at first, then can't reconnect at all, keeps asking for the WPA2 password, etc. Grrr.

---

### Post by chili555 on 2012-06-27
> **oldrocker99 said:**
> When I have the laptop within 6" of the router, the same thing happens; it connects at first, then can't reconnect at all, keeps asking for the WPA2 password, etc. Grrr.Let's see what the wireless driver is doing...```
dmesg | grep wl
```...and Network Manager:```
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```

---

### Post by oldrocker99 on 2012-07-12
Sorry; I've been hospitalized and am all better now!


dmesg | grep wl
[   15.669715] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.686711] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.686720] wl 0000:02:00.0: setting latency timer to 64


sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
 

No response.


Hmmm.


Removed everything after the '|':


sudo cat /var/log/syslog 
[sudo] password for oldrocker99: 
Jul 12 07:53:43 oldrocker99-Aspire-5516 anacron[25496]: Job `cron.daily' terminated (mailing output)
Jul 12 07:53:43 oldrocker99-Aspire-5516 anacron[25496]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jul 12 07:53:43 oldrocker99-Aspire-5516 anacron[25496]: Normal exit (1 job run)
Jul 12 08:09:01 oldrocker99-Aspire-5516 CRON[26138]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jul 12 08:17:01 oldrocker99-Aspire-5516 CRON[26173]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): disconnecting for new activation request.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: activated -> disconnected (reason 'none') [100 30 0]
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): deactivating device (reason 'none') [0]
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): canceled DHCP transaction, DHCP client pid 1310
Jul 12 08:18:54 oldrocker99-Aspire-5516 wpa_supplicant[898]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jul 12 08:18:54 oldrocker99-Aspire-5516 dnsmasq[1530]: exiting on receipt of SIGTERM
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> DNS: starting dnsmasq...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): writing resolv.conf to /sbin/resolvconf
Jul 12 08:18:54 oldrocker99-Aspire-5516 dnsmasq[26177]: started, version 2.59 cache disabled
Jul 12 08:18:54 oldrocker99-Aspire-5516 dnsmasq[26177]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul 12 08:18:54 oldrocker99-Aspire-5516 dnsmasq[26177]: using nameserver 192.168.1.1#53
Jul 12 08:18:54 oldrocker99-Aspire-5516 dnsmasq[26177]: using nameserver 75.75.76.76#53
Jul 12 08:18:54 oldrocker99-Aspire-5516 dnsmasq[26177]: using nameserver 75.75.75.75#53
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul 12 08:18:54 oldrocker99-Aspire-5516 dbus[611]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) starting connection 'oldrocker99'
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): supplicant interface state: completed -> disconnected
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2/wireless): access point 'oldrocker99' has security, but secrets are required.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) started...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) scheduled...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2/wireless): connection 'oldrocker99' has security, and secrets exist.  No new secrets needed.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Config: added 'ssid' value 'oldrocker99'
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Config: added 'scan_ssid' value '1'
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Config: added 'psk' value '<omitted>'
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Config: set interface ap_scan to 1
Jul 12 08:18:54 oldrocker99-Aspire-5516 dbus[611]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 12 08:18:54 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): supplicant interface state: disconnected -> scanning
Jul 12 08:18:57 oldrocker99-Aspire-5516 ntpd[2162]: Deleting interface #4 eth2, 192.168.1.106#123, interface stats: received=0, sent=0, dropped=0, active_time=32377 secs
Jul 12 08:18:57 oldrocker99-Aspire-5516 ntpd[2162]: peers refreshed
Jul 12 08:19:25 oldrocker99-Aspire-5516 wpa_supplicant[898]: Trying to associate with 00:1e:e5:fd:8a:37 (SSID='oldrocker99' freq=2437 MHz)
Jul 12 08:19:25 oldrocker99-Aspire-5516 wpa_supplicant[898]: Association request to the driver failed
Jul 12 08:19:25 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): supplicant interface state: scanning -> associating
Jul 12 08:19:26 oldrocker99-Aspire-5516 wpa_supplicant[898]: Associated with 00:1e:e5:fd:8a:37
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): supplicant interface state: associating -> associated
Jul 12 08:19:26 oldrocker99-Aspire-5516 wpa_supplicant[898]: WPA: Key negotiation completed with 00:1e:e5:fd:8a:37 [PTK=CCMP GTK=CCMP]
Jul 12 08:19:26 oldrocker99-Aspire-5516 wpa_supplicant[898]: CTRL-EVENT-CONNECTED - Connection to 00:1e:e5:fd:8a:37 completed (reauth) [id=0 id_str=]
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): supplicant interface state: associated -> completed
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'oldrocker99'.
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 3 of 5 (IP Configure Start) started...
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> dhclient started with pid 26204
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Beginning IP6 addrconf.
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: All rights reserved.
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: 
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: Listening on LPF/eth2/00:25:56:88:af:cd
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): DHCPv4 state changed nbi -> preinit
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: Sending on   LPF/eth2/00:25:56:88:af:cd
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: Sending on   Socket/fallback
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: DHCPREQUEST of 192.168.1.106 on eth2 to 255.255.255.255 port 67
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: DHCPACK of 192.168.1.106 from 192.168.1.1
Jul 12 08:19:26 oldrocker99-Aspire-5516 dhclient: bound to 192.168.1.106 -- renewal in 38039 seconds.
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): DHCPv4 state changed preinit -> reboot
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   address 192.168.1.106
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   prefix 24 (255.255.255.0)
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   gateway 192.168.1.1
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   nameserver '75.75.75.75'
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   nameserver '75.75.76.76'
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   nameserver '192.168.1.1'
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   domain name 'hsd1.ct.comcast.net.'
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 12 08:19:26 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) started...
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26177]: exiting on receipt of SIGTERM
Jul 12 08:19:27 oldrocker99-Aspire-5516 NetworkManager[839]: <info> DNS: starting dnsmasq...
Jul 12 08:19:27 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): writing resolv.conf to /sbin/resolvconf
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: started, version 2.59 cache disabled
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: using nameserver 192.168.1.1#53
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: using nameserver 75.75.76.76#53
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: using nameserver 75.75.75.75#53
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: using nameserver 192.168.1.1#53
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: using nameserver 75.75.76.76#53
Jul 12 08:19:27 oldrocker99-Aspire-5516 dnsmasq[26207]: using nameserver 75.75.75.75#53
Jul 12 08:19:27 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul 12 08:19:27 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 12 08:19:27 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) successful, device activated.
Jul 12 08:19:27 oldrocker99-Aspire-5516 dbus[611]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 12 08:19:27 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) complete.
Jul 12 08:19:27 oldrocker99-Aspire-5516 dbus[611]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 12 08:19:28 oldrocker99-Aspire-5516 ntpd[2162]: ntpd exiting on signal 15
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): disconnecting for new activation request.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): device state change: activated -> disconnected (reason 'none') [100 30 0]
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): deactivating device (reason 'none') [0]
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): canceled DHCP transaction, DHCP client pid 904
Jul 12 08:19:29 oldrocker99-Aspire-5516 dnsmasq[26207]: exiting on receipt of SIGTERM
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> DNS: starting dnsmasq...
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jul 12 08:19:29 oldrocker99-Aspire-5516 dnsmasq[26276]: started, version 2.59 cache disabled
Jul 12 08:19:29 oldrocker99-Aspire-5516 dnsmasq[26276]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul 12 08:19:29 oldrocker99-Aspire-5516 dnsmasq[26276]: using nameserver 192.168.1.1#53
Jul 12 08:19:29 oldrocker99-Aspire-5516 dnsmasq[26276]: using nameserver 75.75.76.76#53
Jul 12 08:19:29 oldrocker99-Aspire-5516 dnsmasq[26276]: using nameserver 75.75.75.75#53
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Policy set 'oldrocker99' (eth2) as default for IPv4 routing and DNS.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Policy set 'oldrocker99' (eth2) as default for IPv4 routing and DNS.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> dhclient started with pid 26286
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Beginning IP6 addrconf.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: All rights reserved.
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: 
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: Listening on LPF/eth0/00:23:5a:e8:64:cc
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: Sending on   LPF/eth0/00:23:5a:e8:64:cc
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: Sending on   Socket/fallback
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 12 08:19:29 oldrocker99-Aspire-5516 dhclient: bound to 192.168.1.103 -- renewal in 32980 seconds.
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   address 192.168.1.103
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   prefix 24 (255.255.255.0)
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   gateway 192.168.1.1
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   nameserver '75.75.75.75'
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   nameserver '75.75.76.76'
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   nameserver '192.168.1.1'
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info>   domain name 'hsd1.ct.comcast.net.'
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 12 08:19:29 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26276]: exiting on receipt of SIGTERM
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> DNS: starting dnsmasq...
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: started, version 2.59 cache disabled
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: using nameserver 192.168.1.1#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: using nameserver 75.75.76.76#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: using nameserver 75.75.75.75#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: using nameserver 192.168.1.1#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: using nameserver 75.75.76.76#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: using nameserver 75.75.75.75#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Policy set 'oldrocker99' (eth2) as default for IPv4 routing and DNS.
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> DNS: starting dnsmasq...
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26301]: exiting on receipt of SIGTERM
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: started, version 2.59 cache disabled
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: using nameserver 192.168.1.1#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: using nameserver 75.75.76.76#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: using nameserver 75.75.75.75#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: using nameserver 192.168.1.1#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: using nameserver 75.75.76.76#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 dnsmasq[26308]: using nameserver 75.75.75.75#53
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) successful, device activated.
Jul 12 08:19:30 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 12 08:19:32 oldrocker99-Aspire-5516 NetworkManager[839]: <warn> error monitoring device for netlink events: error processing netlink message: Object busy
Jul 12 08:19:34 oldrocker99-Aspire-5516 ntpdate[26272]: sendto(ntp1.Housing.Berkeley.EDU): Network is unreachable
Jul 12 08:19:36 oldrocker99-Aspire-5516 kernel: [32466.536039] eth2: no IPv6 routers present
Jul 12 08:19:40 oldrocker99-Aspire-5516 kernel: [32470.304053] eth0: no IPv6 routers present
Jul 12 08:19:43 oldrocker99-Aspire-5516 NetworkManager[839]: <warn> error monitoring device for netlink events: error processing netlink message: Object busy
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpdate[26272]: adjust time server 72.26.198.233 offset -0.001205 sec
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26372]: ntpd 4.2.6p3@1.2290-o Tue Jun  5 20:12:08 UTC 2012 (1)
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: proto: precision = 0.977 usec
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen and drop on 1 v6wildcard :: UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen normally on 2 lo 127.0.0.1 UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen normally on 3 eth0 192.168.1.103 UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen normally on 4 eth2 192.168.1.106 UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen normally on 5 eth2 fe80::225:56ff:fe88:afcd UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen normally on 6 eth0 fe80::223:5aff:fee8:64cc UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listen normally on 7 lo ::1 UDP 123
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: peers refreshed
Jul 12 08:19:44 oldrocker99-Aspire-5516 ntpd[26373]: Listening on routing socket on fd #24 for interface updates
Jul 12 08:19:45 oldrocker99-Aspire-5516 ntpd[26373]: ntpd exiting on signal 15
Jul 12 08:19:47 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth2): IP6 addrconf timed out or failed.
Jul 12 08:19:47 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 12 08:19:47 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 12 08:19:47 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 12 08:19:50 oldrocker99-Aspire-5516 NetworkManager[839]: <info> (eth0): IP6 addrconf timed out or failed.
Jul 12 08:19:50 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 12 08:19:50 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 12 08:19:50 oldrocker99-Aspire-5516 NetworkManager[839]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 12 08:19:56 oldrocker99-Aspire-5516 ntpdate[26399]: adjust time server 207.150.168.70 offset -0.007468 sec
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26427]: ntpd 4.2.6p3@1.2290-o Tue Jun  5 20:12:08 UTC 2012 (1)
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: proto: precision = 0.977 usec
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen and drop on 1 v6wildcard :: UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 2 lo 127.0.0.1 UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 3 eth0 192.168.1.103 UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 4 eth2 192.168.1.106 UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 5 eth2 fe80::225:56ff:fe88:afcd UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 6 eth0 fe80::223:5aff:fee8:64cc UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 7 lo ::1 UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: peers refreshed
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listening on routing socket on fd #24 for interface updates
Jul 12 08:39:01 oldrocker99-Aspire-5516 CRON[26529]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jul 12 09:09:01 oldrocker99-Aspire-5516 CRON[26572]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jul 12 09:17:01 oldrocker99-Aspire-5516 CRON[26588]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 12 09:39:01 oldrocker99-Aspire-5516 CRON[26649]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)

---

### Post by chili555 on 2012-07-12
Oh, no! I hope you are doing fine now.> dmesg | grep wl
[ 15.669715] wl: module license 'MIXED/Proprietary' taints kernel.
[ 15.686711] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 15.686720] wl 0000:02:00.0: setting latency timer to 64
Looks perfectly normal.> sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20The syslog gets archived and restarted when it gets full. You might try to connect with wireless again so we have current activity and try again:```
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```You can look at the archived file:```
sudo cat /var/log/syslog[COLOR="Red"].1[/COLOR] | grep -e wlan -e etwork | tail -n20
```Glad to have you back!

---

### Post by chili555 on 2012-07-12
> Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 3 [COLOR="Red"]eth0 192.168.1.103[/COLOR] UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 4 [COLOR="Red"]eth2 192.168.1.106[/COLOR] UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 5 eth2 fe80::225:56ff:fe88:afcd UDP 123
Jul 12 08:19:57 oldrocker99-Aspire-5516 ntpd[26428]: Listen normally on 6 eth0 fe80::223:5aff:fee8:64cc UDP 123We see that you have both the wired ethernet and wireless competing. Network Manager is designed to disallow wireless if wired is available. Please detach the ethernet and try again:```
sudo cat /var/log/syslog | grep -e eth2 -e etwork | tail -n20
```

---

### Post by oldrocker99 on 2012-07-17
OK, got this the first time, when the wireless was working:


sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
[sudo] password for oldrocker99: 
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info>   gateway 192.168.1.1
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info>   nameserver '75.75.75.75'
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info>   nameserver '75.75.76.76'
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info>   nameserver '192.168.1.1'
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info>   domain name 'hsd1.ct.comcast.net.'
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Scheduling stage 5
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Done scheduling stage 5
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 17 08:21:32 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jul 17 08:21:33 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jul 17 08:21:33 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Jul 17 08:21:33 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) successful, device activated.
Jul 17 08:21:33 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jul 17 08:34:51 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 17 08:34:55 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Jul 17 08:34:55 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth0): deactivating device (reason: 40).
Jul 17 08:34:55 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2173
Jul 17 08:34:55 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Policy set 'Auto oldrocker99' (eth1) as default for IPv4 routing and DNS.
Jul 17 08:34:55 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Policy set 'Auto oldrocker99' (eth1) as default for IPv4 routing and DNS.


Then, when the wireless shut off (yet again) and kept trying and trying and trying to connect, asked for the WPA2 password yet again, etc, etc:


sudo cat /var/log/syslog | grep -e eth2 -e etwork | tail -n20
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1/wireless): access point 'Auto oldrocker99' has security, but secrets are required.
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth1): device state change: 5 -> 6 (reason 0)
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth1): device state change: 6 -> 4 (reason 0)
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1/wireless): connection 'Auto oldrocker99' has security, and secrets exist.  No new secrets needed.
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Config: added 'ssid' value 'oldrocker99'
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Config: added 'scan_ssid' value '1'
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Config: added 'psk' value '<omitted>'
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 17 08:35:58 oldrocker99-Aspire-5516 NetworkManager[547]: <info> Config: set interface ap_scan to 1
Jul 17 08:35:59 oldrocker99-Aspire-5516 NetworkManager[547]: <info> (eth1): supplicant connection state:  disconnected -> scanning


:confused: and about to say fugit...

---

