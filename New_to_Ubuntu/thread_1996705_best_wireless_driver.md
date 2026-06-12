---
title: "best wireless driver?"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by mlplatt on 2012-06-04
Because my wireless connection was borderline on Windows Vista and frequently went down I replaced the original 'G' wireless adapter with a TP-LNK N PCI Adapter TL-WN951N.

This has transformed my Windows connection and it is now both stable and much faster. 

With my Ubuntu connection the gain has been much less obvious. Previously the Ubuntu connection was far better than the Windows one but with the new adapter it is worse. The Windows is stable at 130 Mb/s whereas the Ubuntu one is unstable at anything  up to a maximum of 78 Mb/s

The Ubuntu connection was made automatically and I now seem to have a ath9k driver instead of the previous b43. 

I have tried to understand the various articles on this subject but am at a loss to know what to do . With my level of terminal ignorance /incompetence I feel I risk losing all internet connection if I meddle. 

Is there any simple way I can improve the connection? Would a return to the b43 driver help and if so how can it be achieved?

Any advice will be most gratefully received.

Malcolm Platt

---

### Post by wildmanne39 on 2012-06-04
Hi, please open a terminal ctrl+alt+t copy and do:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

```
do not reboot if it helps we need to make it permanent by:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

```
Thanks

---

### Post by mlplatt on 2012-06-05
Hi wildmanne,

Thanks for your response.

After I type the first line i.e   [I]sudo ifconfig wlan0 down

[/I]I get the immediate response    	 	 	 	 	 	    *Wlan0: ERROR while getting interface flags: no such device*


Incidentally I did not mention in my first post that the adapter does come with its own CD driver but presumably that doesn't work with Ubuntu .


Regards,


Malcolm

---

### Post by wildmanne39 on 2012-06-05
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

### Post by mlplatt on 2012-06-05
Hi,

Since the last post outlining the reaction I got to typing in the terminal the Wireless connection in Ubuntu has disappeared completely.

This post is through a  Windows connection.   

I will go back and try the new terminal entry in Ubuntu but it will take a little time so bear with me. 

Regards Malcolm

---

### Post by mlplatt on 2012-06-05
When I returned to Ubuntu the wireless option was re-established but it keeps disconnecting.

```
  mlplatt@mlplatt-Inspiron-530s:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux mlplatt-Inspiron-530s 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:51:22 UTC 2012 i686 i686 i386 GNU/Linux
mlplatt@mlplatt-Inspiron-530s:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
	Subsystem: Dell Inspiron 530 [1028:020d]
	Kernel driver in use: e1000e
--
02:01.0 Network controller [0280]: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] [168c:0023] (rev 01)
	Subsystem: Atheros Communications Inc. Device [168c:3071]
	Kernel driver in use: ath9k
mlplatt@mlplatt-Inspiron-530s:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 002 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 002: ID 04d2:0305 Altec Lansing Technologies Non-Compliant Audio Device
mlplatt@mlplatt-Inspiron-530s:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"PlusnetWireless5E8161"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 58:98:35:5E:81:61   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

eth0      no wireless extensions.

mlplatt@mlplatt-Inspiron-530s:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mlplatt@mlplatt-Inspiron-530s:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55605  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
binfmt_misc            17292  1 
arc4                   12473  2 
dcdbas                 14098  0 
snd_hda_codec_realtek   174055  1 
ath9k                 117425  0 
mac80211              436455  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                87213  0 
serio_raw              13027  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
cfg80211              178679  3 ath9k,mac80211,ath
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
i915                  414637  3 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_logitech           22024  0 
ff_memless             12945  1 hid_logitech
usbhid                 41906  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
floppy                 60310  0 
e1000e                140005  0 
usb_storage            39646  2 


```

Regards,

Malcolm

---

### Post by wildmanne39 on 2012-06-05
Hi, run the commands in my first post and change [COLOR="Red"]wlan0 to wlan1[/COLOR] before running the commands.

Your link quality is to low to connect, how far are you from the router? 

The commands I gave you will most likely improve that as well.
Thanks

---

### Post by mlplatt on 2012-06-05
Hi wildmanne,

No more time now ... will try again tomorrow.

I am about 15 -20 ft away from the router but with a 2' thick stone wall between us. This is why I have updated the wireless adapter because I kept losing the connection on Windows and was only getting up to 24 Mb/s at best .... Oddly enough I was getting 36 Mb/s on Ubuntu which was also far more stable. 

I changed to a high gain antenna and upgraded the Wireless adapter to 'N' (previously 'G') to match the wireless/router. This was an immediate success with Windows which now shows 'V. Good' signal strength with an unvarying 130 Mb/s which I think is the max I can expect from the set up. 

Initially Ubuntu did pick it up but only on an unstable 74 Mb/s. Now it seems to have abandoned the attempt.

Regards,

Malcolm

---

### Post by mlplatt on 2012-06-06
Hi wildmanne,

I have now followed the instructions you gave in your first post changing wlan0 to wlan1 throughout. 

The connection is made but the speed varies wildly moving 78Mb/s to an heartening 104Mb/s then to a 1 Mb/s and then to an unknown when it disconnects ...then back to a 78  ... then 104 ... then 1. This is after and during a ten minute spell.

This is after the first part ... I have not rebooted nor confirmed as in the second part awaiting your advice.  

Thanks,

Malcolm

---

### Post by wildmanne39 on 2012-06-06
Hi, I would make those commands permanent.

Then set your wireless settings in network manager to match the screenshots.

This speed is arbitrary it changes with signal strength, the real way to tell is how fast it loads web pages and downloads from several different sites.

Make sure in your router that encryption is set to just wpa2 if it has that option it usually works best in ubuntu.
Thanks

---

### Post by mlplatt on 2012-06-07
Hi,

I have followed your instructions and confirm that my router encryption is set to WPA-personal.

I take your point about the speed being arbitrary but what is happening now is that I continually lose the connection altogether so that the link is effectively unusable. 

I am back on Windows Vista now which is currently stable and fast. Quite the reverse from the situation before I upgraded the Wireless Adapter! 

Thanks for all your help but but I fear I am fated to be stuck with Vista at least for access to the Internet. 

Regards,

Malcolm

---

### Post by wildmanne39 on 2012-06-10
Hi, the exact settings I asked you to see if you can use is wpa2 only not wpa or wpa2 or mixed.

Please post the contents of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
I am out of town and only have internet access today so I will be slow at responding.
Thanks

---

### Post by mlplatt on 2012-06-10
Hi again.

Sorry. I did indeed set it to WPA-personal on the Security installation on the adapter in Windows but in Ubuntu that option does not exist, only WPA and WPA2 - personal.  

 The result of the posting is, in a new window -

```
options ath9k nohwcrypt=1
```I myself shan't be here again today it now being 6.45 p.m. my (UK) time so no hurry.

Incidentally earlier today the connection was constantly down and unusable but on returning to Ubuntu to do this it has been stable for the last twenty minutes

Thanks

---

### Post by wildmanne39 on 2012-06-13
Hi, try changing the the channel in the router to 1 or 11.
Thanks

---

### Post by mlplatt on 2012-06-13
Hi,

I did try all the channels when my problems first started. I am currently on 9 but in fact there seems little difference as I live in a very rural area and there is little in the way of interference from other users. As I recall 11 was the poorest for both Windows and Ubuntu. 

My service providers recommended that I download the inSiDDer programme but frankly I do not understand the information that it gives me.  

Do you know it?

Regards,

Malcolm

---

### Post by chili555 on 2012-06-13
I'm helping out wildmanne39; he's away for a bit. Can you please change the router to B and G only; no N and see if there is any improvement?```
iwconfig
```Thanks.

PS to wildmanne39: I think the driver is correct.

---

### Post by mlplatt on 2012-06-13
Hi chili555,

I am not sure how I can change the router itself and would indeed be a bit reluctant to do so as it has been provided precisely because the previous router  and the previous adapter were providing insufficient signal strength for my Windows Vista connection to function with any degree of stability. 

The signal strength now is far better as far as I can gather on both Vista and Ubuntu as is the stability of Vista. Ubuntu however fluctuates wildly and disconnects frequently so that in effect it is unusable. 

It is true that Ubuntu seemed to work better with the old adapter for the few days it was running with it but as at that time I couldn't get Vista to work I don't want to revert to that situation.

Regards,

Malcolm.

---

### Post by chili555 on 2012-06-13
> I am not sure how I can change the router itself and would indeed be a bit reluctant to do so All you do is log on to the administration pages of the router and look in wireless settings. Look for a setting for B & G, G only, B, G & N, etc. and change it to B & G only, save and close. It's a one minute fix. Try it and if it doesn't help, it's a one minute un-fix. I'd give it an hour or so.> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:13:10:62:8D:xx   
          [COLOR="Red"]Bit Rate=54 Mb/s[/COLOR]   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  [COLOR="Blue"]Signal level=-41 dBm[/COLOR]  
[COLOR="Blue"]Signal strength[/COLOR] and [COLOR="Red"]bit rate[/COLOR] are two very different things.

---

### Post by wildmanne39 on 2012-06-13
Hi, according to your last post you have not changed any settings in the router as I had previously asked about like the wpa2 only setting or the channel setting they are both in the router so it makes it hard to help you.

The linux drivers are different from the windows drivers so we have to make some adjustments, but I have never seen the adjustment in the router settings effect windows ability to connect so you should not have to worry about that.

You can change the settings in your router most likely by typing 192.168.0.1 into your browser while you are wired to the router if you choose to if not I am afraid that is all I can help you with.
Thanks

PS chili555 thanks a lot for the help.

---

### Post by mlplatt on 2012-06-13
Thanks. I am off to bed now .. it is 11.30 here so will try tomorrow. I am judging the signal strength on somne little bars that appear in Vista which come with a range of signal strengths Poor, Fair, Good, Very Good, and Excellent.

Before I was on Poor/Fair. Now it shows Very Good occasionally dropping to Good. 

I have only got Excellent when connected by Ethernet.

Regards

---

### Post by mlplatt on 2012-06-14
Apologies wildmanne my last post was in response to that of chili555. Your post must have just beaten mine . Apologies too if I have given the impression that I have disregarded your advice. I was only trying to explain what I had done previously but I obviously expressed it badly.

I did in fact change the channel to 1 and it is running on that now. I also then changed the router setting to WPA2-Personal by going to 192.168.1.254 . but I cannot change it in Ubuntu as the option does not exist. In wireless security found by going through the Ubuntu settings the option is only 'WPA and WPA2."

Again the reason I said I didn't know how to change the router settings to 'B' and 'G'  was simply that on my router settings accessed through 192.168.1.254 I can find no option to do so. There it merely states "Interface type 802.11b/g/n" and I cannot find any facility to change this overall setting. 

I am sorry if I have explained this badly but assure you my intent was not to ignore your instructions. I am very grateful for your help and advice.

When I logged on today the Ubuntu connection was unstable and kept disconnecting. This was with the settings outlined above. It occurred to me that when I had originally configured the router and adapter I had done so through Windows so I reconfigured through Ubuntu using the same settings.  So far the connection has not been lost but I am at a loss to know if this could make any difference. It must surely be coincidence and I have not yet  spent any time on the net so don't know if will last..  

Regards,

Malcolm

---

### Post by wildmanne39 on 2012-06-14
Hi, to change the speed setting it should be under wireless tab in the router settings here is a screenshot of what mine looks like, beside the speed it has a drop down menu.
Thanks

---

### Post by mlplatt on 2012-06-15
Hi,

I am afraid that my router settings bear little or no resemblance to yours which seem far more comprehensive. In the *overview* the wireless setting is just a given and when I go to *configure* it isn't mentioned. I have had another check this morning but there seems to be no option allowing me to do this. 

I don't know how to get a thumbnail. I can just download the page if it helps. 

Regards

---

### Post by chili555 on 2012-06-15
Wild Man and his faithful assistant chili555 wonder what brand and model router it is so we may review the manual on line.

---

### Post by mlplatt on 2012-06-15
Hi , 

The router is the one supplied by my server PlusNet. It is a Technicolor Gateway TG582n. The wireless adaopter is a TP-Link TL-WN951N.

Incidentally so far today all is well. In half an hours' use I haven't dropped the connection once whereas previously it was every couple of minutes. Long may it last!

Regards

Malcolm

---

### Post by wildmanne39 on 2012-06-15
Hi, I did not find any information on setting the speed of the router but I did find this.

PS Chili this is interesting.
[http://wiki.aa.org.uk/index.php/Linux](http://wiki.aa.org.uk/index.php/Linux)
Thanks

---

### Post by mlplatt on 2012-06-16
Hi,

I am afraid this is all rather over my head. Is it possible that I have this bug? I do update from time to time. 

In fact the connection is behaving itself at the moment. I have not lost it once recently although I have not used it a great deal either. But before it was going down continuously every couple of minutes or so. 

 Maybe the system has settled down after the modifications made? There are only two other things that I have done recently apart from updating Ubuntu. The first is that I added two more high gain antennae to the wireless adapter - it comes equipped with 3 fittings - and previously I have only one of them high gain. This seems to have had no effect whatsoever in Windows. 

The other thing is that when I reconfigured the system on Ubuntu I changed under IPV4 settings the method from 'Automatic (DHCP) addressees only' to ''Automatic (DHCP)' for no good reason other then there didn't seem any point in it as there were no addressees that I could see. I am sure this will make you both shrink in horror at such a mindless cavalier action but I reasoned that it looked tidier and I could always change it back if necessary.  

Regards,

Malcolm

---

### Post by wildmanne39 on 2012-06-16
Hi, I am not sure about the bug either hopefully chili will understand it more but I part of it at least I believe is to do with a wired connection, as far as your issue I know nothing else to try.

---

### Post by chili555 on 2012-06-16
> The other thing is that when I reconfigured the system on Ubuntu I changed under IPV4 settings the method from 'Automatic (DHCP) addressees only' to ''Automatic (DHCP)' for no good reason other then there didn't seem any point in it as there were no addressees that I could see. I am sure this will make you both shrink in horror at such a mindless cavalier action but I reasoned that it looked tidier and I could always change it back if necessary. It does, sort of.

I thought in post #10, wildmanne39 suggested settings for 'Automatic (DHCP) addressees only.' Did you not have those numbers in there? Did they not work for you? Better? Worse? 

It's your system and you can do whatever you want with it, but when you ask for help and get the two best guys in the forum, why change something "for no good reason?" Change it because it doesn't work as well or at all.> PS Chili this is interesting.
[http://wiki.aa.org.uk/index.php/Linux](http://wiki.aa.org.uk/index.php/Linux)
ThanksI don't believe it applies here.

---

### Post by mlplatt on 2012-06-17
You are quite right Chili and I apologise yet again. I am afraid it is just another example of my general incompetence. 

I did indeed change the settings in accordance with the thumbnails provided by Wildmanne. Unfortunately I just followed the instructions without understanding their significance and without mentally registering what I was doing.  When I did reconfigure they must have been changed back and I hadn't noticed. All I saw was an apparent inconsistency. I have now of course changed them back

I deeply regret giving you cause to think you have wasted your time. 

I think the truth is that I am not really up to trying to understand and follow instructions. Perhaps Ubuntu is a step too far for me.  

You haven't of course wasted your time because the connection does now seem to be working which must be due to something you did in spite of my innate ability to **** things up. 

For which my heartfelt thanks. 

Regards,

Malcolm

---

### Post by wildmanne39 on 2012-06-17
Hi, please do not feel bad in any way it is hard to grasp this new system in the beginning there is a lot to know, and I am always glad to try, if it is much better please use thread tools at the top of the page to mark the thread solved.
Thanks

---

