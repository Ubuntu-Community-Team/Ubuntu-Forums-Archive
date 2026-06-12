---
title: "Setting wireless connection in desktop"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by user_linux on 2012-01-01
Hi,
I am trying to setup wireless connection on my desktop. It was prevously connected via an ethernet cable but now I have moved the desktop so I want it wireless. I don't see the enable wireless option in the network manager icon. I even tried to set up the same settings as my laptop which is connected wirlessly. Here is what I tried to make it look similar:
I went to Network connections>wireless tab>clicked add on the right, then I inputted the SSID, made sure the wirelss security is similar to the laptop and have even named the connection starting with auto.
Please help!

---

### Post by TeoBigusGeekus on 2012-01-01
Can you post the output of
```
ifconfig
```
and
```
iwconfig
```
?

---

### Post by user_linux on 2012-01-01
p { margin-bottom: 0.08in; }  :~$ **ifconfig  **
 eth0      Link encap:Ethernet  HWaddr 00:13:20:72:0a:1b   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)  
 

 :~$ **iwconfig**  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 


> **TeoBigusGeekus said:**
> Can you post the output of
```
ifconfig
```and
```
iwconfig
```?

---

### Post by TeoBigusGeekus on 2012-01-01
Your wireless card is not recognised by ubuntu.
Move your pc to a place where you can get a wired connection and go to "Additional Drivers" to see if there's a proprietary driver for your wireless card.
If there is, install it and try again.

---

### Post by wildmanne39 on 2012-01-01
Hi, if there are no drivers in additional drivers for your wireless card please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by zachapre on 2012-01-01
I just installed ubuntu 11.10 64 bit on my desktop. I have a wireless PCI card in my desktop and i have a driver installation disk. when i insert the installation disk and open it and click autorun.exe nothing happens. this is a linux compatible device but i am clueless about ubuntu and installing drivers in general. please be very descriptive in your answers and dumb it down for me lol.
thanks, preston.

---

### Post by wildmanne39 on 2012-01-01
Hi zachapre, you pm me, I am about to leave for a little while but I see that you started your own thread and you have a person in there trying to help you so work in that thread.

It is not a good idea to jump into some one else's thread unless you know you have the same wireless card and the exact same problem .
Thanks

---

### Post by user_linux on 2012-01-02
> **wildmanne39 said:**
> Hi, if there are no drivers in additional drivers for your wireless card please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you
```
:~$ cat /etc/lsb-release; uname -a   DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=10.04  
 DISTRIB_CODENAME=lucid  
 DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"  
 Linux my-desktop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux  
 :~$ lspci -nnk | grep -iA2 net  
 01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)  
 	Kernel driver in use: e100  
 	Kernel modules: e100  
 :~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 :~$ rfkill list all  
 :~$ lsmod 
```   	 	 	 	
 
This is what I have. Please tell me the name of any additional drivers to be installed. I can save them and try to install it on my desktop. I tried to directly connect my computer wired but it doesnt connect. I think it might be due to the fact that I don't have the connection enabled through the cable outlet.

Thx!

---

### Post by wildmanne39 on 2012-01-02
Hi, I see that for some reason a lot of the information I asked for shows no results.

Also I do not see a wireless card, please run these commands and post the output here.
```
lspci -nn
```
```
lsusb
```
```
sudo pccardctl ident
```
hopefully one of those commands will show a wireless card, just so you know it is going to be a lot harder to get a wireless connection going without any connection to the internet.
Thanks

---

### Post by user_linux on 2012-01-03
```
 
lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02) 
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02) 
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) 
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02) 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02) 
01:01.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20] 
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
 
lusb:
 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 004: ID 13fe:3600 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 


 
sudo pccardctl ident: No result shown

```
What to do next?

---

### Post by wildmanne39 on 2012-01-03
Hi, I still do not see a wireless device.

Most desktops do not come with one did you install one or buy an usb adapter? If it is usb unplug it and replug it and run the:
```
lsusb
```
command again.

If internal you need to make sure wireless lan is set to on in your bios, also you can open your computer and reset the device.
Thanks

---

### Post by user_linux on 2012-01-04
Ok, I figured out I don't have an inbuilt wireless adapter. But, I have a wireless dongle. I plugged in the dongle. I saw my home connection, but I am still unable to connect to internet. My page keeps loading. How can I resolve this issue?
thx!

> **wildmanne39 said:**
> Hi, I still do not see a wireless device.

Most desktops do not come with one did you install one or buy an usb adapter? If it is usb unplug it and replug it and run the:
```
lsusb
```command again.

If internal you need to make sure wireless lan is set to on in your bios, also you can open your computer and reset the device.
Thanks

---

### Post by wildmanne39 on 2012-01-04
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here with the usb adapter plugged in:
```

lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by user_linux on 2012-01-05
Here are the results:
```
   	 	 	 	   	 	 	 	p { margin-bottom: 0.08in; }  :~$ lsusb  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 005: ID 13fe:3600 Kingston Technology Company Inc.  
 Bus 001 Device 002: ID 04e8:2018 Samsung Electronics Co., Ltd  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11abgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=10 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
            
 

:~$ rfkill list all  
 0: phy0: Wireless LAN  
 	Soft blocked: no  
 	Hard blocked: no  
 

:~$ lsmod  
 Module                  Size  Used by  
 nls_utf8                1069  1  
 nls_iso8859_1           3249  1  
 nls_cp437               4919  1  
 vfat                    8933  1  
 fat                    47767  1 vfat  
 isofs                  29250  1  
 usb_storage            39969  1  
 binfmt_misc             6587  1  
 snd_intel8x0           25652  2  
 snd_ac97_codec        100646  1 snd_intel8x0  
 ac97_bus                1002  1 snd_ac97_codec  
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss  
 snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss  
 snd_seq_dummy           1338  0  
 fbcon                  35102  71  
 tileblit                1999  1 fbcon  
 font                    7557  1 fbcon  
 snd_seq_oss            26722  0  
 bitblit                 4707  1 fbcon  
 softcursor              1189  1 bitblit 
 snd_seq_midi            4557  0  
 vga16fb                11385  0  
 vgastate                8961  1 vga16fb 
 snd_rawmidi            19056  1 snd_seq_midi  
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi  
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 rt2870sta             461811  0  
 arc4                    1153  2  
 snd_timer              19130  2 snd_pcm,snd_seq  
 i915                  289715  3  
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 rt2800usb              31531  0  
 drm_kms_helper         29329  1 i915  
 rt2x00usb               9639  1 rt2800usb  
 snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 ppdev                   5259  0  
 rt2x00lib              27573  2 rt2800usb,rt2x00usb  
 led_class               2864  1 rt2x00lib  
 mac80211              205402  2 rt2x00usb,rt2x00lib  
 parport_pc             25962  1  
 soundcore               6620  1 snd  
 drm                   163747  4 i915,drm_kms_helper  
 snd_page_alloc          7076  2 snd_intel8x0,snd_pcm  
 shpchp                 28835  0  
 dell_wmi                1793  0  
 dcdbas                  5422  0  
 cfg80211              126144  2 rt2x00lib,mac80211  
 intel_agp              24375  2 i915  
 i2c_algo_bit            5028  1 i915  
 agpgart                31724  2 drm,intel_agp  
 crc_ccitt               1339  1 rt2800usb  
 video                  17375  1 i915  
 output                  1871  1 video  
 lp                      7028  0  
 parport                32635  3 ppdev,parport_pc,lp  
 usbhid                 36110  0  
 hid                    67288  1 usbhid  
 e100                   28211  0  
 mii                     4381  1 e100  
 floppy                 53016  0
 
```
What next?

---

### Post by wildmanne39 on 2012-01-05
Hi, run this command please:
```
echo "blacklist rt2x00usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
unplug your wired connection and reboot.
Thanks

---

### Post by user_linux on 2012-01-06
> **wildmanne39 said:**
> Hi, run this command please:
```
echo "blacklist rt2x00usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
unplug your wired connection and reboot.
Thanks
Sorry it doesn't work. I typed in the code, rebooted, and then plugged in my wireless USB adapter. I still see my wireless manager icon attmepting to connect.

---

### Post by wildmanne39 on 2012-01-06
Hi, please copy and past all commands for accuracy.

Show:
```
lsmod | grep rt2
```
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by user_linux on 2012-01-06
Here is what I got with the wireless adapter USB plugged in:
```
**:~$ lsmod | grep rt2  **
 rt2870sta             461811  0  
 rt2800usb              31531  0  
 rt2x00usb               9639  1 rt2800usb  
 rt2x00lib              27573  2 rt2800usb,rt2x00usb  
 led_class               2864  1 rt2x00lib  
 mac80211              205402  2 rt2x00usb,rt2x00lib  
 cfg80211              126144  2 rt2x00lib,mac80211  
 crc_ccitt               1339  1 rt2800usb  
 

**:~$ cat /etc/modprobe.d/blacklist.conf  **
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
 blacklist rt2x00usb  
 blacklist rt2x00usb  

```
How can I make the internet up and running?

---

### Post by wildmanne39 on 2012-01-06
Hi, run this command also so we can blacklist this drive too:
```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Unplug wirted connection and reboot.
Thanks

---

### Post by user_linux on 2012-01-07
It works, thx a lot, I really appreciate your help and guidance throughout the whole process. Although I don't understand why that last drive was creating a problem, can you explain why?

> **wildmanne39 said:**
> Hi, run this command also so we can blacklist this drive too:
```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```Unplug wirted connection and reboot.
Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, in the version of ubuntu you are using this driver works better rt2870sta but the other one is loaded also and it conflicts so it needs blacklisted, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

