---
title: "Help! After update only text based login"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by Gart3nzw3rg on 2012-05-26
Hey everyone! 

I have a thinkpad X121e and I recently installed Ubuntu 12.04 on it. It worked fine for about two weeks but after installing updates and rebooting, I was greeted with a text based login screen.
I tried to get the graphical environment back by typing in "startx" but the screen turned black and it froze (in the upper left corner there is a dash).

Is there any way to find out what the problem is? Like an error log that I can take a look at?

Any help is much appreciated!

Gart3nzw3rg

---

### Post by josephmills on 2012-05-26
sure boot the computer and sign in (ctrl+alt+f1)

then add this program 
```
sudo apt-get install pastebinit 
```
after that is installed run 
```
lspci -nn | pastebinit 
```
you will get a link (if you are connected to the internet) save it and so that you can post it here 

then run 
```
lsmod | pastebinit 
```
grab the link and paste the two links here thanks.

---

### Post by mapes12 on 2012-05-26
May be worth a try:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Gart3nzw3rg on 2012-05-26
@josephmills: here are the two links:

[http://paste.ubuntu.com/1008074/](http://paste.ubuntu.com/1008074/)
[http://paste.ubuntu.com/1008076/](http://paste.ubuntu.com/1008076/)

@mapes12: the boot-loader works fine. I only get the text based login after I already booted. 

Oh and when I press strg+alt+f7 there is the following text:

"** (plymouthd:234): WARNING **: Command line 'dbus-launch --autolaunch=da8a13cd8251c09752a59f4000000008 --binary-syntax --close-stderr' exited witn non-zero exit status 1: Autolaunch error: X11 initialization failed.\n"

I dont know if that helps.

---

### Post by josephmills on 2012-05-26
From your pastes 
```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320] [1002:9806]
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1513]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1514]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1515]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
```


00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320] [COLOR="Red"][1002:9806][/COLOR]


look at post 2 here 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/945663](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/945663)
which also points to
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/921384](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/921384)

From you 2nd paste 
 
```
Module                  Size  Used by
vesafb                 13844  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_conexant    62128  1 
snd_seq_midi           13324  0 
snd_hda_codec_hdmi     32474  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_hda_intel          33773  0 
snd_hda_codec         127706  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_rawmidi            30748  1 snd_seq_midi
snd_hwdep              13668  1 snd_hda_codec
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
serio_raw              13211  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
sp5100_tco             13791  0 
k10temp                13166  0 
i2c_piix4              13301  0 
rtl8192ce              84826  0 
thinkpad_acpi          81819  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
rts_pstor             445196  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nvram                  14413  1 thinkpad_acpi
btusb                  18288  2 
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
rfcomm                 47604  12 
bnep                   18281  2 
bluetooth             180104  23 btusb,rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
snd_timer              29990  2 snd_pcm,snd_seq
cfg80211              205544  2 rtlwifi,mac80211
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17540  1 
fglrx                3263966  0 
snd                    78855  11 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
video                  19596  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41717  0 
```



[COLOR="Red"]fglrx                3263966  0 
[/COLOR]

depends of fglrx 
```
Replaces: fglrx-amdcccle, fglrx-driver, fglrx-kernel-source, fglrx-modaliases, fglrx-updates, libamdxvba1, xfree86-driver-fglrx, xorg-driver-fglrx
Provides: fglrx-driver
Depends: libc6 (>= 2.3.3), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libice6 (>= 1:1.0.0), libqtcore4 (>= 4:4.5.3), libqtgui4 (>= 4:4.5.3), libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxinerama1, libxrandr2, libxrender1, libxxf86vm1, xserver-xorg-core, lib32gcc1, libc6-i386, dkms, make, linux-libc-dev, linux-headers-generic | linux-headers
Recommends: fglrx-amdcccle
Conflicts: fglrx-driver, fglrx-kernel-source, fglrx-modaliases, libamdxvba1, xfree86-driver-fglrx, xorg-driver-fglrx

```

Notice Replaces:  I am sure that is where things when bad on the upgrade.(I am guessing)

try 

```
sudo apt-get install fglrx-amdcccle 
```

then reboot 

come back here let us know. If nothing worked out use pastebinit again to get us this info 

this code will make a file called testaroo under you home folder you may delete later 
1)
```
touch ~/testaroo && uname -a >~/testaroo && dpkg-query -l >>~/testaroo
```
2)
```
cat~/testaroo | pastebinit 
```

---

### Post by Gart3nzw3rg on 2012-05-26
I tried the command you gave me and it works fine now.

I just would also like to understand what the problem was. Did I understood it correctly that the ATI-drivers have a problem with 12.04 and with the command you gave me I re-installed(?) the drivers.

thanks a lot!

---

### Post by josephmills on 2012-05-27
> **Gart3nzw3rg said:**
> I tried the command you gave me and it works fine now.

I just would also like to understand what the problem was. Did I understood it correctly that the ATI-drivers have a problem with 12.04 and with the command you gave me I re-installed(?) the drivers.

thanks a lot!

Kinda there is a bug fglrx we just added what the package suggests . 

could you file a bug ? 

open terminal 
```
ubuntubug fglrx
```



it will gather all your info and send you to launchpad 

in the summary bar put 

"fglrx needed fglrx-amdcccle in order for xorg to work "

search to see if there is a active bug already If not file one and point the link to this page.

---

### Post by Gart3nzw3rg on 2012-05-27
I reported the bug.

Thanks again for the quick help!

---

