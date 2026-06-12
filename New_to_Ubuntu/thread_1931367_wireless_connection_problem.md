---
title: "wireless connection problem"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by sundit1 on 2012-02-25
v 11.10 installed via Wubi.
Using Orange's BrightBox router which has connected immediately on entering password to my Windows PC, MacBook laptop and son's Playstation.

Ubuntu recognizes the BrightBox and asks for password. Tries continually to connect but fails. Is there a simple answer?

I have gone through various sudo commands as per Help and took screenshots, intending to post them here but they do not transfer successfully to my Windows folders.

---

### Post by androssofer on 2012-02-25
> **sundit1 said:**
> v 11.10 installed via Wubi.
Using Orange's BrightBox router which has connected immediately on entering password to my Windows PC, MacBook laptop and son's Playstation.

Ubuntu recognizes the BrightBox and asks for password. Tries continually to connect but fails. Is there a simple answer?

I have gone through various sudo commands as per Help and took screenshots, intending to post them here but they do not transfer successfully to my Windows folders.

humm... have you tried it when running the live cd? sometimes wubi is a bit funny...

i'm assuming the encryption type of the network matches the 1 in the drop down above where it asks for the password? 

other suggestions would be to check the wireless type, ubuntu doesnt work the best with wireless N... try a g/n mix perhaps?

funny, in my house its the windows machines that dont like my router...

---

### Post by sundit1 on 2012-02-25
Everything matches as far as I can see.
I have got a full list of Terminal outputs, I wonder if anyone can see from this what the problem is? It appears ok to me until the last item:

b@ubuntu:~$ nm-tool
NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        00:26:18:D4:91:A4

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [BrightBox-6m679n] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connecting (configuring)
  Default:           no
  HW Address:        80:1F:02:1C:E7:3E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BrightBox-6m679n:Infra, 00:00:00:00:00:00, Freq 0 MHz, Rate 0 Mb/s, Strength 0 WPA WPA2


b@ubuntu:~$ ^C
b@ubuntu:~$ 
----------------------------------------------------------------------
------------------------------------------------------------------------
b@ubuntu:~$ sudo lshw -C network
[sudo] password for b: 
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: 00:26:18:d4:91:a4
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:feac0000-feafffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 80:1f:02:1c:e7:3e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-12-generic firmware=0.34 latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:febf0000-febfffff
b@ubuntu:~$ 

----------------------------------------------------------------------
------------------------------------------------------------------------

Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
lp                     17799  0 
binfmt_misc            17540  1 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  566711  4 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36962  1 
parport                46562  3 lp,ppdev,parport_pc
drm_kms_helper         42558  1 i915
drm                   236330  5 i915,drm_kms_helper
asus_atk0110           18078  0 
snd                    68266  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1e                  42080  0 
b@ubuntu:~$ ^C
------------------------------------------------------------------------------
--------------------------------------------------------------------------
b@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
b@ubuntu:~$ 
-----------------------------------------------------------------------------
---------------------------------------------------------------------------
b@ubuntu:~$ sudo iwlist scan
[sudo] password for b: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

b@ubuntu:~$

---

### Post by HeroOfCanton on 2012-02-25
Please use the code tag (pound sign in editor) when posting terminal results. It's easier to read, allows scrolling, and escapes the smilies to we don't have to interpret what the actual output was.

Thanks.

I tried for two years to get my wireless working on my laptop. Even got so far as linux reporting connected, but still no luck. I finally decided my time was worth too much and bought a compatible card from [www.thinkpenguin.com](www.thinkpenguin.com).

Just something to consider.

---

### Post by sundit1 on 2012-02-26
> **HeroOfCanton said:**
> Please use the code tag (pound sign in editor) when posting terminal results. 

I tried for two years to get my wireless working on my laptop. Even got so far as linux reporting connected, but still no luck. I finally decided my time was worth too much and bought a compatible card from [www.thinkpenguin.com]("http://www.thinkpenguin.com").

Just something to consider.
No point if I am not getting a result.
I think I will consider forgetting about Linux.

---

