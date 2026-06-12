---
title: "Wireless found but not connecting."
date: 2011-10-06
forum: New to Ubuntu
---

### Post by amaro_ on 2011-10-06
Hello all, i would not say i am new to ubuntu but this is the first time i am having issues that i could not find an answer through google.

My laptop (hp pavillion tx1000) running 10.04 discovers wireless networks but will not connect to any (locked unlocked wep/wap doesn't matter), the ethernet port will also not connect. My theory is that the card is shot as it is the same in windows. Is there any last attempts i can make before giving up? i have also purchased a little dongle (linksys n nano), which is not being recognised by the computer at all. How can i run ndis wrapper without an internet connection? any help what so ever is greatly appreciated.

---

### Post by qkall on 2011-10-06
> **amaro_ said:**
> Hello all, i would not say i am new to ubuntu but this is the first time i am having issues that i could not find an answer through google.

My laptop (hp pavillion tx1000) running 10.04 discovers wireless networks but will not connect to any (locked unlocked wep/wap doesn't matter), the ethernet port will also not connect. My theory is that the card is shot as it is the same in windows. Is there any last attempts i can make before giving up? i have also purchased a little dongle (linksys n nano), which is not being recognised by the computer at all. How can i run ndis wrapper without an internet connection? any help what so ever is greatly appreciated.


well i'm not sure about the rest... but if you have a tethering plan or someone with a rooted/jailbroken phone (i use android so can't really speak for ios) you should be able to connect via usb with the phone.  then you can figure the rest out... above my know how but peep the IRC's (the local ones are generally less crowded and easier to get help)

---

### Post by grahammechanical on 2011-10-06
If the network adapter/card, as you say, discovers networks, then the adapter is working. May I suggest that while trying to fix one problem you may have caused other problems. When under stress we get mixed up.

Try again from the beginning and write down the error messages. They will useful for diagnostics.

Edit Connections and remove all connections. Reboot and try again and use Network manager to make the connection.

Open a terminal and type

```
cat /etc/network/interfaces
```

The interfaces file (when using network manager) should read

> auto lo
> iface lo inet loopback

and not anything else. If something else is there then edit it out with

```
sudo gedit /etc/network/interfaces
```

That will open the interfaces file in Gedit with administrator privileges which will let you edit and save the file. Then reboot.

This solved it for me on one occasion. In the past the interfaces file was used to set up connections. So some advise putting this or that in the file. But It conflicts with what Network manager is trying to do.

Regards.

---

### Post by amaro_ on 2011-10-12
Thank you both for your replies I shall respond to both of you in one message and i apologize for the tardiness of my reply (i was unaware i would not receive a notification upon reply to my thread)

qkall can you elaborate on local? do you mean like my irl area, or as in this communities local channel. But i had not thought of connecting my nexus thanks for the tip.



grahammechanical, As far as my attempts to repair it all i haqve done thus far really is install ubuntu. Its an older laptop so i had a theory that perhaps the reason it was not connecting to wireless and not recognizing ethernet in windows was OS degradation. But alas after installing ubuntu it remains the same. 


a little more info:

>lshw -C network 
 *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:a7:26:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:c8000000-c8003fff

> iw config

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


So is this card really a lost cause or not?

---

### Post by josephmills on 2011-10-12
> **amaro_ said:**
> Thank you both for your replies I shall respond to both of you in one message and i apologize for the tardiness of my reply (i was unaware i would not receive a notification upon reply to my thread)

qkall can you elaborate on local? do you mean like my irl area, or as in this communities local channel. But i had not thought of connecting my nexus thanks for the tip.



grahammechanical, As far as my attempts to repair it all i haqve done thus far really is install ubuntu. Its an older laptop so i had a theory that perhaps the reason it was not connecting to wireless and not recognizing ethernet in windows was OS degradation. But alas after installing ubuntu it remains the same. 


a little more info:

>lshw -C network 
 *-network               
       description: Wireless interface
       product: [COLOR="Red"]BCM4311 802.11b/g WLAN[/COLOR]
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:a7:26:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=wl0 [/COLOR]driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:c8000000-c8003fff

> iw config

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


So is this card really a lost cause or not?


No it is not a lost cause could we please see a ```
lspci -nn | grep 14e4
``` and a ```
lsmod
``` and a ```
rfkill list all 
```

---

### Post by computerguts on 2011-10-12
I am sure you have probably already tried this, but it might be a problem with your router. Try turning off you router for ten seconds, then turn it back on and wait for all the lights on your router to turn green. 

Hope this helps

---

### Post by amaro_ on 2011-10-12
> lspci -nn | grep 14e4

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

> lsmod

Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8901  0 
fat                    47767  1 vfat
usb_storage            39425  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203168  1 
joydev                  8708  0 
snd_hda_intel          21877  5 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
uvcvideo               56990  0 
lib80211_crypt_tkip     7596  0 
psmouse                63245  0 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
videodev               34361  1 uvcvideo
softcursor              1189  1 bitblit
v4l1_compat            13251  2 uvcvideo,videodev
nvidia               9961216  45 
snd                    54148  21 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3978  0 
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
i2c_nforce2             5199  0 
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
pata_amd                8766  0 
forcedeth              49556  0 
sata_nv                19440  2
 
>rfkill list

outputs nothing 





And thank you computerguts but yes i have tried that and have also tried different routers and types of connections (linksys/smc and wep/wap respectively)

---

### Post by josephmills on 2011-10-12
> **amaro_ said:**
> > lspci -nn | grep 14e4

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [COLOR="Red"][14e4:4311][/COLOR] (rev 02)

> lsmod

Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8901  0 
fat                    47767  1 vfat
usb_storage            39425  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203168  1 
joydev                  8708  0 
snd_hda_intel          21877  5 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
uvcvideo               56990  0 
lib80211_crypt_tkip     7596  0 
psmouse                63245  0 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
videodev               34361  1 uvcvideo
softcursor              1189  1 bitblit
v4l1_compat            13251  2 uvcvideo,videodev
nvidia               9961216  45 
snd                    54148  21 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3978  0 
[COLOR="red"]wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl [/COLOR]
i2c_nforce2             5199  0 
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
pata_amd                8766  0 
forcedeth              49556  0 
sata_nv                19440  2
 
>rfkill list

outputs nothing 





And thank you computerguts but yes i have tried that and have also tried different routers and types of connections (linksys/smc and wep/wap respectively)

Ok I see the trouble dang propitiatory software this is what you need to do 

first is to get rid of the wl mod to do this open terminal and copy and paste  in ```
 sudo apt-get --purge remove bcmwl-kernel-source && sudo apt-get remove broadcom-sta-source  && sudo apt-get remove broadcom-sta-common && sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer && sudo apt-get install bcmwl-kernel-source && sleep 15 && sudo reboot 
```  after reboot please use this code 
```
sudo su 
```
then 
```
echo wl >> /etc/modprobe.d/blacklist.conf ; modprobe b43 ; echo b43 >> /etc/modules; exit
```


then reboot agian do you have wireless ?

---

### Post by amaro_ on 2011-10-12
Dammit i have had a similar problem with another laptop years back (ended up just using it wired when not in windows). Trying this out now i get a "couldn't find package firmware-b43-installer" .

I saw it was "apt-get install" so i tried tethering my phone to see if it was the lack of internet access. While the web browser now works "apt-get install firmware-b43-installer" outputs the same. However some quick googling results in "apt-get install b43-fwcutter firmware-b43-installer" (on this page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)) but it references natty (i am still on 10.04) do i in fact require this?



EDIT:

ignored that portion and it all worked thank you all very much, looks like i owe some random strangers a few favors. Pay it forward and what not.

---

