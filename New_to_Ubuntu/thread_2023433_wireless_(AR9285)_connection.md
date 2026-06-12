---
title: "wireless (AR9285) connection"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by bekirs on 2012-07-12
Hi,

I'm an absolute beginner and have Xubuntu 12.04 installed on my HP 635 Laptop.
My wireless network adapter is AR9285. 
I couldn't connect to wireless internet and it is even not possible to put a tick in "Enable wireless" although it seems active.

Thanks in advance for your help

---

### Post by spcwingo on 2012-07-12
First, connect via ethernet, then Press ALT+F2.  When the run prompt comes up enter

```
jockey-gtk
```

and press enter.

It sounds like you don't have the necessary firmware installed.

Just for good measure post the output of the following commands:

```
lspci
```

```
lsusb
```

```
ifconfig
```

---

### Post by bekirs on 2012-07-12
_**lspci:**_

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

**_ lsusb_**

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 004 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth


_** ifconfig:**_

eth0      Link encap:Ethernet  HWaddr e4:11:5b:ef:13:fd  
          inet addr:10.107.4.12  Bcast:10.107.4.255  Mask:255.255.255.0
          inet6 addr: fe80::e611:5bff:feef:13fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:380964 (380.9 KB)  TX bytes:64358 (64.3 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4788 (4.7 KB)  TX bytes:4788 (4.7 KB)

pan1      Link encap:Ethernet  HWaddr 2e:c9:e3:93:63:a3  
          inet addr:10.161.204.1  Bcast:10.161.204.255  Mask:255.255.255.0
          inet6 addr: fe80::2cc9:e3ff:fe93:63a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8677 (8.6 KB)

---

### Post by spcwingo on 2012-07-12
Did you try the suggestion from the first part of my post?

---

### Post by bekirs on 2012-07-12
yes, I did.
It listed me two things:

1- ATI/AMD proprietary FGLRX graphics driver (post-release updates)
2- ATI/AMD proprietary FGLRX graphics driver

I was able to activate the 2nd one, but it did not work for the 1st.

---

### Post by spcwingo on 2012-07-12
Those are only for the graphics, not the wireless card.  Could you please post the output of these commands:

```
iwconfig
```

```
rfkill list all
```

---

### Post by bekirs on 2012-07-12
here it is

```
iwconfig
pan1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


```
```
rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by spcwingo on 2012-07-12
Try:

```
sudo rfkill unblock all
```

Then reboot.  If that doesn't work I think something else that I have up my sleeve just might.  :)

---

### Post by bekirs on 2012-07-12
it still doesn't work... "Enable Wireless" seems active but does not to put the "check" sign after clicking.

---

### Post by spcwingo on 2012-07-12
Okay, try this:

Press ALT+F2 and enter:

```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

In that editor copy/paste this:

```
options ath9k nohwcrypt=1
```

save and reboot.

If that doesn't work I do a little more digging and see what I come up with.

---

### Post by bekirs on 2012-07-12
After I type the first command in "Run Program...", it asks me a password. Then, after I type the password correctly, nothing appears...?

---

### Post by spcwingo on 2012-07-12
My fault, you're using XFCE...gedit is not installed by default.  Just replace:

```
gedit
```

with

```
mousepad
```

in that command.

---

### Post by bekirs on 2012-07-12
After ALT+F2,I typed:

gksudo mousepad /etc/modprobe.d/ath9k.conf
it asked me the password and nothing happened after I've typed it correctly.

---

### Post by spcwingo on 2012-07-12
Okay let's try it this way.  From a terminal enter:

```
sudo nano /etc/modprobe.d/ath9k.conf
```

then enter the:

```
options ath9k nohwcrypt=1
```

Then CTRL+O (upper case o) to save then CTRL+X to exit.  Then reboot.

---

### Post by bekirs on 2012-07-12
I've done it but still I couldn't actviate the wireless.

---

### Post by spcwingo on 2012-07-12
Post the output of this command:

```
ifconfig && iwconfig && rfkill list all
```

These are the same commands as earlier, I just want to see if everything is being recognized now and that there is no more blocked hardware.

---

### Post by bekirs on 2012-07-12
eth0      Link encap:Ethernet  HWaddr e4:11:5b:ef:13:fd  
          inet addr:10.107.4.12  Bcast:10.107.4.255  Mask:255.255.255.0
          inet6 addr: fe80::e611:5bff:feef:13fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2752497 (2.7 MB)  TX bytes:503096 (503.0 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23181 (23.1 KB)  TX bytes:23181 (23.1 KB)

pan1      Link encap:Ethernet  HWaddr 62:34:87:53:a9:8b  
          inet addr:10.161.204.1  Bcast:10.161.204.255  Mask:255.255.255.0
          inet6 addr: fe80::6034:87ff:fe53:a98b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8993 (8.9 KB)

pan1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by spcwingo on 2012-07-12
> **bekirs said:**
> 1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

This is the part that's causing the problems.  As far as the hard block, you might want to poke around the bios settings to see if it's been disabled or check the switch to make sure that it hasn't been accidentally switched off.  There might also be a keyboard shortcut to enable/disable wireless.  Try that too.  As far as the soft block, it should have been taken care of by the:

```
sudo rfkill unblock all
```

command.

I just checked around a little more and what some people are saying worked for them is changing the boot order in the bios to have network booting first.  It wouldn't hurt to give that a whirl also.  I'll do some more digging tomorrow when I get off of work and see if there is anything else to try.  With this forum, someone else will probably stop by before then and get you rolling.

---

### Post by bekirs on 2012-07-13
In BIOS, in the following path

**InsydeH20 SetupUtility\System Configuration\Boot Options**

I have changed the status of "_Internal Network Adapter Boot_" from "_Disabled_" to "_Enabled_"

then, in the following path 

**InsydeH20 SetupUtility\System Configuration\Boot Options\Boot Order**
I put the "_Network Adapter_" to the first rank and "_Notebook Hard Drive_" to the second.

Still it does not put a check beside even if I select active "_Enable Wireless_" choice.

I get the following after I type "_rfkill list all_"

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


I'm able to switch "Hard blocked" status from "yes" to "no" simply by pressing to the wireless  key. However "Soft blocked" (for "hp-wifi") is always "no"  even if I type "sudo rfkill unblock all".

By the way, when the computer boots the "_Network Adapter_" first, the following is written after waiting around ten seconds:

"_PXE-E53: No boot filename received_"

---

### Post by spcwingo on 2012-07-16
I'm sorry it has taken me so long to reply.  Does anything change if you run this command:

```
sudo rfkill unblock all
```

(the soft blocked listing of hp-wifi from yes to no)

---

### Post by NikTh on 2012-07-16
Hi , 
i think it will be helpful if provided the modules are loaded. 
Open a terminal and ```
lsmod
```**Put the results here inside [CODE] tags , by highlighting the text and click at[SIZE=3] #[/SIZE] symbol on top of message pane.**
Thanks

---

### Post by wildmanne39 on 2012-07-16
Hi, please try:
```
sudo modprobe -r hp-wmi
```
see if it removes the softblock with:
```
rfkill list all
```
if so does it connect? if it does you will need to black list hp-wmi with:
```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
Thanks

---

### Post by NikTh on 2012-07-17
> **wildmanne39 said:**
> 
```
sudo su
echo hp-wmi >> /etc/modprobe.d/blacklist.conf
```

Hi , 
i thought that correct command was 
```
echo '**blacklist** hp-wmi' >> /etc/modprobe.d/blacklist.conf

```It is the same ? 
Thanks

---

### Post by wildmanne39 on 2012-07-17
Hi NikTh, I did make a mistake because I am on a computer without my files so I typed it instead of coping and pasting but I fixed it and it can be ran either way.
Thanks for bringing it to my attention.

---

### Post by NikTh on 2012-07-17
> **wildmanne39 said:**
> Hi NikTh, I did make a mistake because I am on a computer without my files so I typed it instead of coping and pasting but I fixed it and it can be ran either way.
Thanks for bringing it to my attention.

Its ok , i just thought, maybe 2 commands had the same effect. 
Thanks for clarification.

---

### Post by bekirs on 2012-07-17
answer to spcwingo (message #20)

before I type ```
sudo rfkill unblock all
``` I had 
```
 0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no 
```after I type ```
sudo rfkill unblock all
``` I got
```
 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```So, there's no change in the _soft-blocked_ status of _hp-wifi_ but the one for the _phy0_ is switched to _no_
Conclusion: no check mark appears after I select _Enable Wireless_

---

### Post by bekirs on 2012-07-17
here is the result for the message #21 of NikTh > **NikTh said:**
> Hi , 
i think it will be helpful if provided the modules are loaded. 
Open a terminal and ```
lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  1 
iptable_filter         12810  1 
iptable_nat            13229  1 
nf_nat                 25891  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           81926  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  4 ipt_MASQUERADE,iptable_filter,iptable_nat,ip_tables
bridge                 90989  0 
stp                    12931  1 bridge
vesafb                 13844  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
arc4                   12529  2 
uvcvideo               72627  0 
psmouse                87692  0 
ath9k                 132390  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
mac80211              506816  1 ath9k
serio_raw              13211  0 
parport_pc             32866  0 
ath3k                  12961  0 
btusb                  18288  1 
ppdev                  17113  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
sp5100_tco             13791  0 
bnep                   18281  2 
rfcomm                 47604  4 
k10temp                13166  0 
bluetooth             180104  14 ath3k,btusb,bnep,rfcomm
snd_hda_codec_realtek   223867  1 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
rts_pstor             445196  0 
snd_hda_codec_hdmi     32474  1 
i2c_piix4              13301  0 
snd_hda_intel          33773  8 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
fglrx                3263886  84 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
video                  19596  0 
wmi                    19256  1 hp_wmi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
snd                    78855  25 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
usbhid                 47199  0 
hid                    99559  1 usbhid

```

---

### Post by bekirs on 2012-07-17
> **wildmanne39 said:**
> Hi, please try:
```
sudo modprobe -r hp-wmi
```see if it removes the softblock with:
```
rfkill list all
```if so does it connect? if it does you will need to black list hp-wmi with:
```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Thanks

I tried ```
sudo modprobe -r hp-wmi
``` and then ```
rfkill list all
``` gave me the following:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```It seems that _1: hp-wifi_ _2:hp-bluetooth_ disappeared. The _Enable Wireless_ choice is not active anymore.

---

### Post by sujitrjadhav on 2012-07-17
I too face same problem on my dell mini. If I turn wireless off in network manager in gnome shell I can not turn it on again. It goes in airplane mode that can not be reversed. 

I have tried it using many other linux distros. But I have found a work around. I know this is not a solution but this is what I do.  I use live usb with backtrack installed on it. when I run wicd in backtrack it is unblocked.  If I try to remove hard or soft block using wicd on any else distro it dose not work.

---

### Post by NikTh on 2012-07-17
> **bekirs said:**
> I tried ```
sudo modprobe -r hp-wmi
``` and then ```
rfkill list all
``` gave me the following:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```It seems that _1: hp-wifi_ _2:hp-bluetooth_ disappeared. The _Enable Wireless_ choice is not active anymore.
Hi,
Try to see if some keys compilation will unblock the wireless. e.g Fn+F3 . Its seems that your WiFi is disabled.
And now that you blacklisted hp-wmi , give the results of ```
lsmod
``` again. 
Thanks

---

### Post by bekirs on 2012-07-17
> **NikTh said:**
> Hi,
Try to see if some keys compilation will unblock the wireless. e.g Fn+F3 . Its seems that your WiFi is disabled.
And now that you blacklisted hp-wmi , give the results of ```
lsmod
``` again. 
Thanks

here is the result of ```
lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  1 
iptable_filter         12810  1 
iptable_nat            13229  1 
nf_nat                 25891  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           81926  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  4 ipt_MASQUERADE,iptable_filter,iptable_nat,ip_tables
bridge                 90989  0 
stp                    12931  1 bridge
rfcomm                 47604  4 
bnep                   18281  2 
parport_pc             32866  0 
vesafb                 13844  1 
ppdev                  17113  0 
snd_hda_codec_realtek   223867  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath3k                  12961  0 
fglrx                3263886  100 
joydev                 17693  0 
snd                    78855  22 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18288  1 
ath_pci               202589  0 
bluetooth             180104  14 rfcomm,bnep,ath3k,btusb
uvcvideo               72627  0 
hp_wmi                 18092  0 
videodev               98259  1 uvcvideo
soundcore              15091  1 snd
v4l2_compat_ioctl32    17128  1 videodev
sp5100_tco             13791  0 
rts_pstor             445196  0 
k10temp                13166  0 
i2c_piix4              13301  0 
wlan                  252939  1 ath_pci
video                  19596  0 
sparse_keymap          13890  1 hp_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 hp_wmi
psmouse                87692  0 
ath_hal               430739  1 ath_pci
serio_raw              13211  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 

```

---

### Post by NikTh on 2012-07-18
Hi ,
i see that 
**hp_wmi **module its still there. 
Did you make the blacklist permanent ? 
Please give the results of 
```
cat /etc/modprobe.d/blacklist.conf
```I also see this module 
**iptable_filter ,** i don't know much about iptables , but maybe had something to do with your wireless connection ? (not sure)
Thanks

---

### Post by bekirs on 2012-07-18
> **NikTh said:**
> Hi ,
i see that 
**hp_wmi **module its still there. 
Did you make the blacklist permanent ? 
Please give the results of 
```
cat /etc/modprobe.d/blacklist.conf
```I also see this module 
**iptable_filter ,** i don't know much about iptables , but maybe had something to do with your wireless connection ? (not sure)
Thanks

I have unfortunately not so many ideas about what I am doing, therefore I can't answer whether I made it permanently blacklist or not; but here is the output of what you've asked
```
cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

thanks...

---

### Post by NikTh on 2012-07-18
Ok ,
lets try again what @wildmanne39 told you to do. 
Open a terminal and copy-paste from here to your terminal (for more accuracy) 
```
echo 'blacklist hp_wmi' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
After this command reboot your system and open a terminal again .. 
give this command 
```
sudo rfkill unblock all
```
wait for few seconds and see if wireless work..
if not ..
give the results of these commands 
```
rfkill list all 
lsmod | grep hp
```
Thanks

---

### Post by bekirs on 2012-07-18
> **NikTh said:**
> Ok ,
lets try again what @wildmanne39 told you to do. 
Open a terminal and copy-paste from here to your terminal (for more accuracy) 
```
echo 'blacklist hp_wmi' | sudo tee -a /etc/modprobe.d/blacklist.conf
```After this command reboot your system and open a terminal again .. 
give this command 
```
sudo rfkill unblock all
```wait for few seconds and see if wireless work..
if not ..
give the results of these commands 
```
rfkill list all 
lsmod | grep hp
```Thanks
it didn't work, here are the outputs... 
```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
```
lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  1 
iptable_filter         12810  1 
iptable_nat            13229  1 
nf_nat                 25891  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           81926  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  4 ipt_MASQUERADE,iptable_filter,iptable_nat,ip_tables
bridge                 90989  0 
stp                    12931  1 bridge
vesafb                 13844  1 
joydev                 17693  0 
snd_hda_codec_realtek   223867  1 
snd_hda_codec_hdmi     32474  1 
psmouse                87692  0 
serio_raw              13211  0 
uvcvideo               72627  0 
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
videodev               98259  1 uvcvideo
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17128  1 videodev
k10temp                13166  0 
sp5100_tco             13791  0 
ath3k                  12961  0 
rts_pstor             445196  0 
i2c_piix4              13301  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rfcomm                 47604  16 
parport_pc             32866  0 
fglrx                3263886  78 
snd_rawmidi            30748  1 snd_seq_midi
btusb                  18288  2 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180104  24 ath3k,rfcomm,btusb,bnep
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  22 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19596  0 
wmi                    19256  0 
mac_hid                13253  0 
ath_pci               202589  0 
wlan                  252939  1 ath_pci
ath_hal               430739  1 ath_pci
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 

```

---

### Post by NikTh on 2012-07-18
Ok , 
lets see what dmesg says 
```
dmesg | grep -e wl -e net -e work
``` 
Try also this 
```
sudo modprobe ath9k
``` 
wait few seconds and see if WiFi enabled. 
Thanks

---

### Post by bekirs on 2012-07-18
> **NikTh said:**
> Ok , 
lets see what dmesg says 
```
dmesg | grep -e wl -e net -e work
```Try also this 
```
sudo modprobe ath9k
```wait few seconds and see if WiFi enabled. 
Thanks

After I typed both commands, I saw a "check mark" in "Enable Wireless". However, it wasn't able to connect or even find the wireless connection which is available for another computer in the room. I restarted the system and "Enable Wireless" has disappeared. I retyped the commands you told and "Enable Wireless" returned with the "check mark". And now I give you the final outputs:  
```

dmesg | grep -e wl -e net -e work
[    0.000000] DMI: Hewlett-Packard HP 635 Notebook PC              /3577, BIOS F.35 10/26/2011
[    0.004064] Security Framework initialized
[    1.177774] audit: initializing netlink socket (disabled)
[    1.386057] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.397506] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.203784] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   16.352386] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.578469] type=1400 audit(1342635823.432:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   17.211918] type=1400 audit(1342635824.064:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=851 comm="apparmor_parser"
[  125.908600] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.912606] ADDRCONF(NETDEV_UP): wlan0: link is not ready

``````
sudo modprobe ath9k
 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```

---

### Post by NikTh on 2012-07-18
Ok . 
Lets try something else. 
open a terminal and copy-paste this
```
echo 'ath9k' | sudo tee -a /etc/modules
```
reboot without an ethernet cable and see if WiFi enabled. 

Give the results of these commands 
```
rfkill list all 
lsmod 
```
Thanks

---

### Post by bekirs on 2012-07-18
I just noticed that wireless connection is fine after I typed the commands
dmesg | grep -e wl -e net -e workand
sudo modprobe ath9kI'm writing and sending this message without wired connection... It's already great, thank you very much... Now, the only problem is to repeat this configuration after rebooting. Do you have a solution for that?

---

### Post by NikTh on 2012-07-18
> **bekirs said:**
> .. Now, the only problem is to repeat this configuration after rebooting. Do you have a solution for that?

Yes , the solution (probably) its on above post #38. Try it and i wait you to  post back the results.

This command 
```
dmesg | grep -e wl -e net -e work
```its not a workaround . Its just info .. 

Thanks

---

### Post by bekirs on 2012-07-18
> **NikTh said:**
> Yes , the solution (probably) its on above post #38. Try it and i wait you to  post back the results.

This command 
```
dmesg | grep -e wl -e net -e work
```its not a workaround . Its just info .. 

Thanks
here is the result:

```
dmesg | grep -e wl -e net -e work
[    0.000000] DMI: Hewlett-Packard HP 635 Notebook PC              /3577, BIOS F.35 10/26/2011
[    0.004064] Security Framework initialized
[    1.169842] audit: initializing netlink socket (disabled)
[    1.381847] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.393471] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.229818] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   16.134438] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.256739] type=1400 audit(1342637459.117:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
[   16.920782] type=1400 audit(1342637459.781:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=845 comm="apparmor_parser"
[   65.546447] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.547356] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   68.505584] wlan0: authenticate with 00:13:49:d4:3a:e6 (try 1)
[   68.507660] wlan0: authenticated
[   68.526442] wlan0: associate with 00:13:49:d4:3a:e6 (try 1)
[   68.529205] wlan0: RX AssocResp from 00:13:49:d4:3a:e6 (capab=0x431 status=0 aid=3)
[   68.529213] wlan0: associated
[   68.530247] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   78.952037] wlan0: no IPv6 routers present

```

---

### Post by NikTh on 2012-07-18
Just to be sure , give the results of these commands 
```
cat /etc/modprobe.d/blacklist.conf 
cat /etc/modules
```

---

### Post by bekirs on 2012-07-18
> **NikTh said:**
> Just to be sure , give the results of these commands 
```
cat /etc/modprobe.d/blacklist.conf 
cat /etc/modules
```

here it is:
```
cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist hp_wmi

``````
cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
ath_pci
ath_pci

```

---

### Post by NikTh on 2012-07-18
Ok , open a terminal and copy-paste this command from here to your terminal..
```
echo 'ath9k' | sudo tee -a /etc/modules
```

Reboot your system and report back if WiFi enabled and working as you expected. 
Thanks

---

### Post by bekirs on 2012-07-18
> **NikTh said:**
> Ok , open a terminal and copy-paste this command from here to your terminal..
```
echo 'ath9k' | sudo tee -a /etc/modules
```Reboot your system and report back if WiFi enabled and working as you expected. 
Thanks

it's OK now, thank you very much... In conclusion, the solution is at message #37. The secondary problem, namely repeating the commands after every reboot, has been solved at message #44.

Thank you and all others who spent their time to help...

---

### Post by NikTh on 2012-07-18
Ok , 
Glad that worked for you . 
Now you can mark this **thread as solved** , from **thread tools**.
Thanks

---

### Post by wildmanne39 on 2012-07-18
Hi, I am glad to see you have it sorted, sorry I was not available more I just finally got home to my computer where I can get on more.

Blacklisting hp_wmi got rid of the block and 
```
echo 'ath9k' | sudo tee -a /etc/modules
```
made it load the driver at boot.

NikTh you did a great job.

---

### Post by NikTh on 2012-07-19
> **wildmanne39 said:**
> 

NikTh you did a great job.

Thank you teacher . :)

---

