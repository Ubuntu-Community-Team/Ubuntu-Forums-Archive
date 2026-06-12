---
title: "Wifi problems with Atheros AR5B93"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by Music Guy123 on 2012-06-02
Hi there,

I have just installed Ubuntu with Gnome 3 and I must say I really do like it, especially compared to windows, already after a day of using it and coming back to windows for 5 minutes I am disliking windows! Anyway, I still have one major problem that I just can't get fixed, and if I can't fix it, I am afraid that'll be the end of Ubuntu for me! Basically, I have spent the last two days at school setting up my Ubuntu, I have overcome all sorts of teething problems like multi screens, mounting two hard drives automatically on boot and sorted out my video card driver to a degree, I think it could be better though but it isn't a priority. I am still a complete newbie to Ubuntu, I am good with computers and I am learning fast but I know for a fact, I would never been able to install linux without the help of my friend who really is a complete guru. Anyway, that is the background, now for the problem.

It is wifi. It works absolutely fine at my school, probably due to superior routers and an insanely fast connection (over 100mbps). However, as soon as  I come home to a not great router, browsing stops, google takes about 20s to load. I know my home router is dodgy and does have a lot of problems with windows as well but I can't change it for various reasons. So Ubuntu will connect (just) but it will hardly open pages. I am unable to google anything. On windows, it does work, I can google stuff fine but downloads are slow. Hardware wise, according to windows device manager, my wifi card is an Atheros AR5B93. It could be a simple driver update required but I don't know where to get a driver from and how to install it in linux (my noobishness I know!). I have tried disabling ipv6 and similar to no avail. I know similar things get posted the whole time but I really don't know what to try! I am happy to explain anything else that may be required, I am sorry this is such a bloated post. I hope you can help, it would be very much appreciated.

Music Guy

---

### Post by Music Guy123 on 2012-06-02
After a little tampering seems to be working now :)

I am afraid I am not really sure what I did though!

---

### Post by Music Guy123 on 2012-06-03
No, not working anymore! It hardly brings up google and definately doesn't do search. I am wondering if it is a driver problem but I don't know how I would go about updating it. This is really annoying because it means I can't use Ubuntu. I have turned off ipv6, I have disabled power management, I tried putting the ipv4 as Automatic (addresses only) and the DNS server as my ip address. All to no improvement. I would really appreciate some help on this.

Music Guy

---

### Post by chamber on 2012-06-03
I'm not sure that it would be a driver issue as you will be using the same drivers in your home as you would be in your school.  

Take a look at the latency on your connection at home and if possible try a third location to connect to in order to ensure that the issue is in fact your home router.

---

### Post by wildmanne39 on 2012-06-03
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Music Guy123 on 2012-06-04
Firstly, thank you both very much for replying, it is very much appreciated. As for my router, I haven't checked the latency yet but do I need to? My wifi works in windows. It doesn't work flawlessly, my router I admit is rubbish but it does work. As for the code, I ran it whilst being connected to the router but I still couldn't bring up a webpage. Anyway, here is what I got: 

```
henry@henry-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux henry-laptop 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 athlon i386 GNU/Linux
henry@henry-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6632]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:020f]
	Kernel driver in use: tg3
henry@henry-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
henry@henry-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"XXX-Xxxxwifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:5D:4E:7C:7F:D1   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0

eth0      no wireless extensions.

henry@henry-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
henry@henry-laptop:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
rfcomm                 38139  0 
snd_hda_codec_hdmi     31775  1 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
binfmt_misc            17292  1 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
acer_wmi               23612  0 
snd_seq_midi           13132  0 
sparse_keymap          13658  1 acer_wmi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
uvcvideo               67203  0 
snd_timer              28931  2 snd_pcm,snd_seq
radeon                733693  4 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 117326  0 
videodev               86588  1 uvcvideo
mac80211              436455  1 ath9k
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  6 radeon,ttm,drm_kms_helper
snd                    62064  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
psmouse                72919  0 
serio_raw              13027  0 
k10temp                12990  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
wmi                    18744  1 acer_wmi
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
shpchp                 32325  0 
soundcore              14635  1 snd
cfg80211              178679  3 ath9k,mac80211,ath
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
video                  19068  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141369  0

```

P.S. I didn't understand your thing about the '#' key but I think I got the code in alright.

Thank you very much again and I hope you are able to continue to help me.

Music Guy

---

### Post by wildmanne39 on 2012-06-04
Hi, try this:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

```
do not reboot or the settings will be lost, if this helps we can make it permanent by:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

### Post by Music Guy123 on 2012-06-04
Thank you! seems to work but I am not certain. Before I make it permanent, can I please just check that if I find it doesn't work, I can make it 'un permanent' again. I can do that right?

---

### Post by wildmanne39 on 2012-06-04
Hi, yes we can change it even after you make it permanent but give it a few more minutes.
Thanks

---

### Post by Music Guy123 on 2012-06-04
Thank you very much, your help is much appreciated. It seems to be working now, I'll see how it goes and report back here if I have any problems!

---

### Post by wildmanne39 on 2012-06-04
Hi, after you have tried it for a little while and are satisfied that it is working good please use thread tools at the top of the page to mark the thread solved.
Thanks

---

