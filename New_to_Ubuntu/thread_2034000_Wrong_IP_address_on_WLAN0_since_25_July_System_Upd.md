---
title: "Wrong IP address on WLAN0 since 25 July System Update"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by peterh84 on 2012-07-27
Since running System Update  on Wednesday 25 July, in which a new Linux kernel level and other updates were downloaded, my wireless connection doesn't work, in the following way.  I connect to the same network name as before, though most recently I have to delete it and reinput its name to force the connection.  I don't see a list of available networks.  I then get a connection, but the IP address that I get is 10.x.x.x.  That connection, or pseudo-connection, is unusable.  I just get error messages from my browser, e-mail, etc.  I tried from both the Xfce session that I normally use and standard Ubuntu.  (I think the networking is the same in either case.)  But when I connect from the same laptop to the same network from either Windows 7 or my Ubuntu 12.04 installation USB stick, everything works fine, I see available networks, I pick my normal one,  and I get an IP address from the real network, 172.x.x.x.  

Any ideas on what I can do other than reinstalling?

---

### Post by levlaz on 2012-08-01
In the edit connections window check the ipv4 settings, is it set to DHCP (automatic)?

---

### Post by anewguy on 2012-08-02
Also, when you edit connections, try deleting the old connection definition.  Sometimes you need to do that and then when you try to connect it will ask for you network key again and redefine the connection.

Also - are you sure 10.x.x.x is not valid?  If you have a cable or dsl modem with ethernet ports, and then connect your router to one of those ethernet ports, usually your router will be different from the "standard" 192.168.x.x octets.  For example, on my old Netgear router it used to always be in the 10.x.x.x range.

---

### Post by wildmanne39 on 2012-08-02
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by peterh84 on 2012-08-03
Thanks, all, for your suggestions.  It happened again: I installed Ubuntu again on a different partition, was able to get a network connection and used it for all kinds of tasks, then did an update today of everything that is currently out of date on the Ubuntu 12.04 system that I had installed from USB, rebooted, and...dead in the water.  

Answers in order:
1) Yes, DHCP is enabled in network connections IP v4.
2) The valid IP address, which I got prior to updating, or get from Windows or from a pre-updated Ubuntu 12.04 on USB, is 172.x.x.x, not 192.x.x.x.  It's the ISP's IP address, not a router's.  10.x.x.x is invalid because it doesn't work.  I get it only when I boot from an Ubuntu system that has been updated since last week. 
3) When I first rebooted, I don't recall whether there were no network connections at all listed in the top menu bar drop-down, or just the one for the library where I get internet access.  In any case, I didn't get a connection at all.  No IP address for WLAN0.  (I did get the connection and valid IP address immediately with the non-updated Ubuntu system.)  After checking DHCP, I deleted the network name for wireless, then defined a new connection with the same name.  It appeared to connect (the name showed and the "Disconnect" option showed).  The IP address was again 10.x.x.x.
4) Here is the command output requested.

```
peterhu@peterhu-ThinkPad-T420:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux peterhu-ThinkPad-T420 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
peterhu@peterhu-ThinkPad-T420:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce
peterhu@peterhu-ThinkPad-T420:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
```
```

peterhu@peterhu-ThinkPad-T420:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```
```

peterhu@peterhu-ThinkPad-T420:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
peterhu@peterhu-ThinkPad-T420:~$ lsmod
Module                  Size  Used by
joydev                 17693  0 
dm_crypt               23125  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62311  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
arc4                   12529  2 
ppdev                  17113  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                87692  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
serio_raw              13211  0 
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
thinkpad_acpi          81819  0 
tpm_tis                18804  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nvram                  14413  1 thinkpad_acpi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  2 rtlwifi,mac80211
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
i915                  472897  3 
wmi                    19256  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
peterhu@peterhu-ThinkPad-T420:~$ 

```

Also, after deleting and redefining the connection, using the standard name (a public library's connection), it seems to work in that Ubuntu tells me I have a connection, but it's a dud.  ifconfig gives me this.
```
wlan0     Link encap:Ethernet  HWaddr 74:de:2b:e7:ed:df  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:fee7:eddf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:14608 (14.6 KB)
```
The 10.x.x.x address must be some kind of default.  Searching on the internet (from Windows) I see that 10.0.0.1 is a default gateway address used some routers including Cisco.

Thanks very much for your help!

---

### Post by peterh84 on 2012-08-03
I see some of the command output was garbled by the forum software's translation to emoticons.   Let's try that again:

```
peterhu@peterhu-ThinkPad-T420:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

---

### Post by coffeecat on 2012-08-03
> **peterh84 said:**
> I see some of the command output was garbled by the forum software's translation to emoticons.

If you use BBCode [noparse]```

```[/noparse] tags - see the link in my sig - for terminal output, you won't see that problem. They will also preserve formatting which you lose by posting as open text. I've added code tags where appropriate in both your posts. The simplest way of adding code tags is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by wildmanne39 on 2012-08-03
Hi, this driver has been causing issues but they can usually be fixed.

Go into your router and change 802.11bgn to just 802.11bg.

Then do:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```

A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```

Proofread, save and close gedit, then reboot.
Thanks

---

### Post by peterh84 on 2012-08-04
Hi Coffeecat, I noticed the option to disable the translation to emoticons when I was doing the first post, but forgot to check it.  As soon as I saw all the smiley faces, I remembered and used that for my next update.  Thanks!

Hi Wildmanne39, I can't change the router settings because it's the library's router, not mine.  But I created the file as you specified, and I can access the network from my updated Linux system now.  Thanks!  

Now that I have that, I updated the system to include Xubuntu and my other personally selected packages, and I get a failure message when I try to start an Xubuntu session, but I'll worry about that later and still declare victory for the day.

---

### Post by wildmanne39 on 2012-08-04
Hi, please go to the top of the page and use thread tools and mark this thread solved, then start a new thread on the new issue with a descriptive title.
Thanks

---

