---
title: "Unstable wireless with Netgear WNA1000M USB"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by matbluvenger on 2012-02-16
Tried to get responses to this in a thread marked "solved"... didn't realize solved threads won't show up in the new posts section.... still new.

Before I continue I should mention I'm running 11.10 Ocelot. So I have the Netgear WNA1000M usb wireless network adapter and it runs really fast.... sometimes. Other times I get almost zero connection but when it pops back up I get normal download/upload/ping from speedtests.

I've tried chili's solution from [http://ubuntuforums.org/showthread.php?t=1806839](http://ubuntuforums.org/showthread.php?t=1806839) and it straight up dropped my adapter like it wasn't there. So now I'm doing a clean re-install and have a couple questions:

1) I noticed the advice given on the linked thread was for 11.04... is there anything I should be doing differently for 11.10?

2) Will this fix work if I installed 11.04 instead?

3) Is there a PCI or USB wireless network adapter that anybody knows for *sure* is compatible right out of the box with either 11.04 or (preferably) 11.10?


Thanks in advance for any help!

---

### Post by josephmills on 2012-02-16
> **matbluvenger said:**
> Tried to get responses to this in a thread marked "solved"... didn't realize solved threads won't show up in the new posts section.... still new.

Before I continue I should mention I'm running 11.10 Ocelot. So I have the Netgear WNA1000M usb wireless network adapter and it runs really fast.... sometimes. Other times I get almost zero connection but when it pops back up I get normal download/upload/ping from speedtests.

I've tried chili's solution from [http://ubuntuforums.org/showthread.php?t=1806839](http://ubuntuforums.org/showthread.php?t=1806839) and it straight up dropped my adapter like it wasn't there. So now I'm doing a clean re-install and have a couple questions:

1) I noticed the advice given on the linked thread was for 11.04... is there anything I should be doing differently for 11.10?

2) Will this fix work if I installed 11.04 instead?

3) Is there a PCI or USB wireless network adapter that anybody knows for *sure* is compatible right out of the box with either 11.04 or (preferably) 11.10?


Thanks in advance for any help!

Hello there I was wondering if we could get some more information about you wireless card please could you please open your terminal and enter ```
lspci -nn && lsmod && lsusb && rfkill list all
```

then paste that here thanks

---

### Post by matbluvenger on 2012-02-16
Thanks for the quick response! So it's finally installed, here's what I get when I enter that code:


00:00.0 Host bridge [0600]: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge [1106:0308]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:1308]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:2308]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. PT890 Host Bridge [1106:3208]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:4308]
00:00.5 PIC [0800]: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller [1106:5308]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:7308]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller [1106:a208]
00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VT8237A SATA 2-Port Controller [1106:0591] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237A PCI to ISA Bridge [1106:3337]
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller [1106:287e]
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
00:13.0 Host bridge [0600]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
02:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 8400 GS] [10de:10c3] (rev a2)
02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
80:01.0 Audio device [0403]: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)
Module                  Size  Used by
vesafb                 13489  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  8 rfcomm,bnep
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
nvidia              10390874  40 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95614  1 rtl8192cu
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              172392  2 rtlwifi,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
ppdev                  12849  0 
i2c_viapro             12969  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32356  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
via_rhine              27413  0 
pata_via               13359  2 
sata_via               13534  0 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Hope that helps.

---

### Post by josephmills on 2012-02-16
ahh compat wireless time could I see a ```
uname -a 
```
thanks

---

### Post by matbluvenger on 2012-02-16
Sorry for the delay. Here ya go

Linux rafferty-desktop 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by josephmills on 2012-02-16
cool lets try this 
Download this 
[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.0/compat-wireless-3.0.9-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.0/compat-wireless-3.0.9-1.tar.bz2)

then open terminal 
```
cd ~/Downloads 
```
then 
```
tar -xvf compat-wireless-3.0.9-1.tar.bz2
```
then 
```
cd compat-wireless-3.0.9-1/

```
then 
```
make 
```
then 
```
sudo make install 
```
after done 
```
sudo reboot 
```

do you have wireless ? if not please post any error that you may have gotten 
thanks

---

### Post by matbluvenger on 2012-02-16
Seems good so far. If it's not a problem, I think I may wait just a little bit until I mark this as solved. The previous "fixes" stopped working after a couple hours so I want to give this guy a chance. THANK YOU SO MUCH!


But maybe it's just the content I'm going to. It seems like I can go to most pages really fast. But it's not crazy about certain flash streaming video players (i.e. what putlocker, gorillavid, etc,. use.) Is it just that Ubuntu isn't a fan of those kinds of video players?

---

### Post by matbluvenger on 2012-02-16
It seems to be stable still. This is around the time other fixes would take a crap.

I just have one last question: when there is a major update (kernel, etc.) do I have to redo this or is it permanent?

Thank you so much josephmills!

---

### Post by Scott Baker on 2012-02-16
You should have mentioned the issue, as it pertains to what you're trying to view online. Your net may be working just fine, it's the content that could be causing hiccups. I recently upgraded to 11.10 on all of my machines. Since the upgrade, I found that with regards to being online, that sometimes I would either be kicked offline, or worse, I would have my machine reboot. I've seen this happen with my laptops (wireless) and my desktop (DSL). I've kept track of what was being done when this happened, and it ALWAYS happens when viewing various videos online, no other times. I've already submitted a bug report on this, because I've not had this problem in previous versions of Ubuntu or Edubuntu. Start tracking when this is happening, and see if you may be running into the same problem. Let know what your findings are please.  :-k

---

### Post by matbluvenger on 2012-02-16
Gotcha, thanks for the advice.

Previous to this fix that actually worked, all websites would be crazy slow to load or not load at all but I would still have full bars on the taskbar icon. But now it's just certain video players... all websites so far have been blazing fast (with the exceptions of those that I know to be on slow or sketchy servers.) I will definitely keep a log of which video players will and will not work and post it on here after I have enough findings.

---

### Post by josephmills on 2012-02-17
> **matbluvenger said:**
> Gotcha, thanks for the advice.

Previous to this fix that actually worked, all websites would be crazy slow to load or not load at all but I would still have full bars on the taskbar icon. But now it's just certain video players... all websites so far have been blazing fast (with the exceptions of those that I know to be on slow or sketchy servers.) I will definitely keep a log of which video players will and will not work and post it on here after I have enough findings.

have you tried a different weplayer ? say something like [ Mega video Player Plus ](https://chrome.google.com/webstore/detail/efpoolkicbnlkaibhppihnfehghajfeg)  give it a shot. then test next to other browsers that do not have it installed. as far as 
> It seems to be stable still. This is around the time other fixes would take a crap.

I just have one last question: when there is a major update (kernel, etc.) do I have to redo this or is it permanent?



Yes if you upgrade you kernel it is best to upgrade compat to do this just do a ```
uname -a
``` so you know what kernel it is then go to this page [http://linuxwireless.org/en/users/Download/stable](http://linuxwireless.org/en/users/Download/stable)
and look for the one that you need. 
then uninstall the old one ```
cd ~/Downloads/compat-wireless-3.0.9-1/ && sudo make uninstall 
``` then install the new one. Hope that this helps. there is also a README page in that Directory that you could read to learn more about compat wireless. 
Once again glad too see that things worked out. Have a good one 
Joseph

---

### Post by matbluvenger on 2012-02-17
> **josephmills said:**
> have you tried a different weplayer ? say something like [ Mega video Player Plus ](https://chrome.google.com/webstore/detail/efpoolkicbnlkaibhppihnfehghajfeg)  give it a shot. then test next to other browsers that do not have it installed.
Cool, I'll give it a shot. This works for a slew of streaming sites, not just MegaVideo? 


> **josephmills said:**
> Yes if you upgrade you kernel it is best to upgrade compat to do this just do a ```
uname -a
``` so you know what kernel it is then go to this page [http://linuxwireless.org/en/users/Download/stable](http://linuxwireless.org/en/users/Download/stable)
and look for the one that you need. 
then uninstall the old one ```
cd ~/Downloads/compat-wireless-3.0.9-1/ && sudo make uninstall 
``` then install the new one. Hope that this helps.

Immense amounts of help! But I'm still quite new and have a (probably) silly question: if uname -a gives me

Linux rafferty-desktop 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

that means my kernel is 3.0.0-16-generic and I should download the compat-wireless-3.0.9-1.tar.bz2 version, and alternately the very first download on the linuxwireless page (compat-wireless-3.3-rc1-2.tar.bz2) would be what I would want if I upgraded to kernel 3.3... am I making the correct assumptions here?

---

### Post by matbluvenger on 2012-02-25
Meh decided to not use that one anymore. My roommate bought a couple of Rosewill RNX-n180UBE wireless usb adapters and it works soooo much better.

I'm not sure if it's a driver thing, a hardware thing, or just the fact that the Rosewill has a USB extension cable so I can keep it in optimal position.

---

### Post by CableCat on 2012-02-28
Mini USB wifi adaptor that work in Ubuntu:
* Buffalo AirStation N-Technology 150Mbps USB 2.0 Client [WLI-UC-GNM-EU]

Mini USB wifi adaptors that do not work in Ubuntu:
* NETGEAR G54/N150 Wireless USB Micro Adapter WNA1000M [WNA1000M-100PES]
* TRENDnet TEW 648UBM [TEW-648UBM]
* D-Link Wireless N 150 Micro USB Adapter DWA-121 [DWA-121]
* Belkin N150 Micro Wireless USB Adapter [F7D1102AZ]

Tested at 2012-02-28 in Ubuntu 11.10 and Daily Live.
Connecting to WPA2 enterprise network fails most times.

[IMG]http://kom.aau.dk/~pmr/www/mini_USB_WIFI/Mini_USB_WIFI_in_Ubuntu_550px.png[/IMG]

---

### Post by matbluvenger on 2012-02-28
Fun! And incredibly recent, wow....

Good thing I'm not using the Netgear anymore :D

---

