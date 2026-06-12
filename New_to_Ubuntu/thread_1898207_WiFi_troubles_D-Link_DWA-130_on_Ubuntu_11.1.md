---
title: "WiFi troubles: D-Link DWA-130 on Ubuntu 11.1"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by SpiritBear on 2011-12-20
Hello,
I have a D-Link DWA-130 (rev C1) USB Wireless Adapter, and I'm trying to work with Ubuntu 11.1 on a AMD quad-core desktop.
Here is my lsusb for more adapter info:
```

tyler@Tyler:/$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 2001:3301 D-Link Corp. DWA-130 802.11n Wireless N Adapter(rev.C1) [Realtek RTL8192U]
Bus 004 Device 002: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 005 Device 002: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse

```
I have downloaded (ethernet works fine) and installed Ndiswapper and my device's driver from the D-Link webpage.  I am using the dnet130c1.inf file in the WINXPx64 folder that D-Link provided as my driver. Ndiswapper says "dnet130c1 Hardware present: Yes", so I went to "Configure Network" and under Wireless I add a profile for my SSID and WPA passphrase.  Reboot.  Adapter is not lighting up and Wi-Fi is greyed out on the systray saying "Wireless Network wireless is disabled".  I did iwconfig and ifconfig:
```

tyler@Tyler:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tyler@Tyler:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:94:f5:45  
          inet addr:66.177.134.86  Bcast:66.177.135.255  Mask:255.255.254.0
          inet6 addr: fe80::6ef0:49ff:fe94:f545/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9595059 (9.5 MB)  TX bytes:1164146 (1.1 MB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60680 (60.6 KB)  TX bytes:60680 (60.6 KB)


```
I noticed on iwconfig it says Access Point: not associated.  So I'm thinking that the driver is fine but somehow the adapter isn't "turned on", aka not looking for network for some reason.  This is the same whether or not I unplug the ethernet and I don't have a radio tower key on my keyboard. What is my next step here?  I'm stuck :confused:

---

### Post by wildmanne39 on 2011-12-20
Hi, welcome to the forum! You should not need ndiswrapper because ubuntu comes with the driver you need.

Copy and paste all commands for accuracy.

Please run these commands one at a time:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Then unplug your wired connection and run:
```
sudo modprobe r8192u_usb
```
Thanks

---

### Post by SpiritBear on 2011-12-20
Hey wildmanne,
Thanks for your help.  I did exactly what you posted to do. Ndiswrapper was successfully removed, but I have not gotten any further with the problem.  Systray still says "Wireless Networks: device not ready" and the light is off on the adapter.  I tried rebooting and unplugging/plugging the adapter.  No change. :(

---

### Post by wildmanne39 on 2011-12-20
Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by QIII on 2011-12-20
Doesn't the DWA-130 use the ar9170 chipset, necessitating the use of the (comes with the 2.6 kernel and beyond) carl9170 driver with carl9170-1.fw?  Or does the C1 version use another chipset?
I was just working through this on someone else's machine.  May not have been the same revision.

Please ignore a forgetful old man...

---

### Post by SpiritBear on 2011-12-20
```
tyler@Tyler:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Tyler 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux
tyler@Tyler:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tyler@Tyler:~$ rfkill list all
tyler@Tyler:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
r8192u_usb            248351  0 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2595537  116 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
k10temp                12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i2c_piix4              13093  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
floppy                 60310  0 
pata_atiixp            12967  0 
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci

```

> **wildmanne39 said:**
> Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by QIII on 2011-12-20
Dang!  OK.  Forget the old man.  It was in his original post.

I'll go drool somewhere in my boxers and black socks with garters.

Carry on!

---

### Post by wildmanne39 on 2011-12-20
Hi QIII
Chocolate-Covered Ubuntu, there are probably some that do but each wireless card comes with many chips and that is what you have to go by that is why I ask him to run commands and post information because of so many different chips even in the same card, I will show you how to tell which chip later if you would like.

SpiritBear I have to get off for tonight, I will start on this tomorrow we have made progress you are using the right driver now that is a big start.
Thanks

---

### Post by QIII on 2011-12-20
No thanks.  I saw the chipset when I bothered to tip my bifocals and look back at his original post.

I've been doing this computer gig since the days of punch cards and acoustic couplers.  Just the eyes going bad.

---

### Post by SpiritBear on 2011-12-20
> **wildmanne39 said:**
> Hi QIII
SpiritBear I have to get off for tonight, I will start on this tomorrow we have made progress you are using the right driver now that is a big start.
Thanks

:popcorn: thanks for your help so far :D

---

### Post by SpiritBear on 2011-12-21
> **wildmanne39 said:**
> I will start on this tomorrow we have made progress you are using the right driver now that is a big start.
Ok, so I have the right driver now you say. I am still having all the same symptoms... Wireless is unavailable/device not ready. Feeling stuck. ](*,) What is the next step?

---

### Post by wildmanne39 on 2011-12-21
Hi, please unplug your wired connection and run the following commands and post the results here:
```
sudo cat /var/log/syslog | grep -e 819 -e firmware -e wpa -e etork -e wlan | tail -n55
```
```
nm-tool
```
```
sudo iwlist scan
```
Thanks

---

### Post by SpiritBear on 2011-12-21
```


tyler@Tyler:~$ sudo cat /var/log/syslog | grep -e 819 -e firmware -e wpa -e etork -e wlan | tail -n55
Dec 21 09:37:15 Tyler kernel: [    0.523819] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec 21 09:37:15 Tyler kernel: [    0.845819] io scheduler cfq registered (default)
Dec 21 09:37:15 Tyler kernel: [   16.320486] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
Dec 21 09:37:15 Tyler kernel: [   16.322460] Linux kernel driver for RTL8192 based WLAN cards
Dec 21 09:37:15 Tyler kernel: [   16.539883] type=1400 audit(1324478235.967:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=819 comm="apparmor_parser"
Dec 21 09:37:16 Tyler kernel: [   16.737409] usbcore: registered new interface driver rtl819xU
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 21 09:37:16 Tyler NetworkManager[847]: <error> [1324478236.286056] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl819xU' ifindex: 3)
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): now managed
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): bringing up device.
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 21 09:37:16 Tyler dbus[826]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 21 09:37:16 Tyler kernel: [   17.082592] rtl819xU:request firmware fail!
Dec 21 09:37:16 Tyler kernel: [   17.082596] rtl819xU:ERR in init_firmware()
Dec 21 09:37:16 Tyler kernel: [   17.082599] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
Dec 21 09:37:16 Tyler kernel: [   17.082602] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
Dec 21 09:37:16 Tyler NetworkManager[847]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6:1.0/net/wlan0, iface: wlan0)
Dec 21 09:37:16 Tyler NetworkManager[847]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 21 09:37:16 Tyler dbus[826]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> wpa_supplicant started
Dec 21 09:37:16 Tyler wpa_supplicant[1062]: nl80211: 'nl80211' generic netlink not found
Dec 21 09:37:16 Tyler wpa_supplicant[1062]: Could not set interface wlan0 flags: Resource temporarily unavailable
Dec 21 09:37:16 Tyler wpa_supplicant[1062]: Failed to initialize driver interface
Dec 21 09:37:16 Tyler NetworkManager[847]: <error> [1324478236.745334] [nm-supplicant-interface.c:570] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Dec 21 09:37:16 Tyler NetworkManager[847]: <info> (wlan0): supplicant interface state: starting -> down
Dec 21 09:37:16 Tyler kernel: [   17.312292] rtl819xU:request firmware fail!
Dec 21 09:37:16 Tyler kernel: [   17.312296] rtl819xU:ERR in init_firmware()
Dec 21 09:37:16 Tyler kernel: [   17.312299] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
Dec 21 09:37:16 Tyler kernel: [   17.312302] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
tyler@Tyler:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        6C:F0:49:94:F5:45

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xU
  State:             unavailable
  Default:           no
  HW Address:        00:22:B0:ED:21:3A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


tyler@Tyler:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```
Thanks

---

### Post by wildmanne39 on 2011-12-21
Hi, give me a few minutes to research the problem, the firmware is not loading correctly.
Thanks

---

### Post by wildmanne39 on 2011-12-21
Hi, download the file that's attached. I assume it's going to Downloads.
Run the commands one at a time.
```
sudo mkdir /lib/firmware/RTL8192U
cd Downloads
unzip RTL8192U.zip
cd RTL8192U
sudo cp * /lib/firmware/RTL8192U/
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
```
Did that work, if not repost:
```
sudo cat /var/log/syslog | grep -e 819 -e firmware -e wpa -e etork -e wlan | tail -n55
``` command
Thanks

---

### Post by SpiritBear on 2011-12-21
```

    	 	 	 	 	 	   Dec 21 12:50:39 Tyler NetworkManager[802]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6:1.0/net/wlan0, iface: wlan0)  
 Dec 21 12:50:39 Tyler NetworkManager[802]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <error> [1324489839.715310] [nm-device-wifi.c:3081] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl819xU' ifindex: 4)  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <info> (wlan0): now managed  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <info> (wlan0): bringing up device.  
 Dec 21 12:50:39 Tyler NetworkManager[802]: <info> (wlan0): deactivating device (reason 'managed') [2]  
 Dec 21 12:50:39 Tyler wpa_supplicant[1024]: nl80211: 'nl80211' generic netlink not found  
 Dec 21 12:50:39 Tyler kernel: [  586.488417] rtl819xU:request firmware fail!  
 Dec 21 12:50:39 Tyler kernel: [  586.488421] rtl819xU:ERR in init_firmware()  
 Dec 21 12:50:39 Tyler kernel: [  586.488423] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed  
 Dec 21 12:50:39 Tyler kernel: [  586.488426] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!  
 Dec 21 12:50:40 Tyler wpa_supplicant[1024]: Could not set interface wlan0 flags: Resource temporarily unavailable  
 Dec 21 12:50:40 Tyler wpa_supplicant[1024]: Failed to initialize driver interface  
 Dec 21 12:50:40 Tyler NetworkManager[802]: <error> [1324489840.166429] [nm-supplicant-interface.c:570] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.  
 Dec 21 12:50:40 Tyler NetworkManager[802]: <info> (wlan0): supplicant interface state: starting -> down  
 Dec 21 12:50:40 Tyler kernel: [  586.713070] rtl819xU:request firmware fail!  
 Dec 21 12:50:40 Tyler kernel: [  586.713081] rtl819xU:ERR in init_firmware()  
 Dec 21 12:50:40 Tyler kernel: [  586.713088] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed  
 Dec 21 12:50:40 Tyler kernel: [  586.713096] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!  
 Dec 21 12:53:09 Tyler kernel: [  735.681960] sd 6:0:0:0: [sdb] No Caching mode page present  
 Dec 21 12:53:09 Tyler kernel: [  735.681971] sd 6:0:0:0: [sdb] Assuming drive cache: write through  
  

```

---

### Post by wildmanne39 on 2011-12-21
Hi, did you have any errors when you ran those commands?
thanks

---

### Post by SpiritBear on 2011-12-21
Yes but the errors were from you putting the wrong filename in the code. RTL8192U.zip does not exist so I just downloaded your attachment and created a RTL8192U folder in Downloads and extracted it there and ran the rest of the code.  No other errors.

I forgot to mention: this system is dual-boot with Windows 7 and the adapter works fine in that environment.
Also, When I unplug the adapter an Ubuntu prompt says "Network Disconnected", so it knows it's plugged in.  Seems like it's still a firmware issue....

---

### Post by wildmanne39 on 2011-12-21
Hi, please post output of:
```
ls -al /lib/firmware/RTL8192SU/
```
Thanks

---

### Post by SpiritBear on 2011-12-21
```

tyler@Tyler:~$ ls -al /lib/firmware/RTL8192SU/ 
ls: cannot access /lib/firmware/RTL8192SU/: No such file or directory 
tyler@Tyler:~$ ls -al /lib/firmware/RTL8192U 
total 76 
drwxr-xr-x  2 root root  4096 2011-12-21 12:38 . 
drwxr-xr-x 63 root root  4096 2011-12-21 12:34 .. 
-rw-r--r--  1 root root 68368 2011-12-21 12:38 rtl8192sfw.bin 
tyler@Tyler:~$ 

```

---

### Post by wildmanne39 on 2011-12-21
Hi, alright let's try it this way delete the firmware folder and let's start over.

All commands run one line at a time.

Open a terminal and do:
```
sudo mkdir /lib/firmware/RTL8192U
```
Download the attached file to your desktop. Right-click it and select 'Extract Here.' Back to the terminal and do:
```
cd Desktop/RTL8192U
sudo cp * /lib/firmware/RTL8192U/
```

Now, let's unload and reload the driver:
```
sudo rmmod -f r8192u_usb
sudo modprobe r8192u_usb
```
Did that help?

---

### Post by SpiritBear on 2011-12-21
wildmanne you rock! :guitar:


the wirless turned on immeditately after that last uninstall/reinstall.

kudos!  :KS:KS:KS:KS:KS

---

### Post by wildmanne39 on 2011-12-21
Hi, that is great!!! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by WickedLittleThing on 2012-01-02
@ wildmanne39, You are amazing! thank you. i followed your steps and sure enough i had the same problem with my d-link dwa 130.

---

### Post by wildmanne39 on 2012-01-02
Hi WickedLittleThing, your welcome I am glad to help.
Enjoy

---

### Post by mbarela on 2012-05-10
When I tried sudo rmmod -f r8192u_usb, I got an error message, no such file or directory.

---

