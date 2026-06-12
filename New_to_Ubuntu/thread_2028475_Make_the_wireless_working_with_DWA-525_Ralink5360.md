---
title: "Make the wireless working with DWA-525 Ralink5360"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by row225 on 2012-07-18
Hi
 
I'am using ubuntu12.04 LTS on an Acer-Veriton desktop and i have been struggling the whole week digging and trying to find a way to make my wireless card (D-link DWA-525) work, but unsuccessfully :-( i've been through quiete a lot of post on how to install it on previous version of Ubuntu and some method of make it work but i cant still get it work.
 
if any new solution different from those on google please let me know. 
 
Thanks

---

### Post by mebomechanicno1 on 2012-07-18
I regret I have never ever managed to get a wireless adaptor card to work, but people say it is possible, and I suggest you start by reading this article
 
[http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/)

---

### Post by kurt18947 on 2012-07-18
Here's a link to a pretty good site to wireless driver information.  This ain't gonna be simple.  Note this is for rev_A2.

[http://www.wikidevi.com/wiki/D-Link_DWA-525_rev_A2](http://www.wikidevi.com/wiki/D-Link_DWA-525_rev_A2)

If you want to develop knowledge,  you can work to get your internal card working.   If you just want your wireless to work, you might consider a nano USB adapter that is known to work.  I'm using one of these on a Thinkpad with a built-in G speed Wifi:

[http://www.amazon.com/gp/product/B005CLMJLU/ref=s9_simh_gw_p147_d1_g147_i5?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=0HGN6VKX5W7KPD6NTPG5&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846](http://www.amazon.com/gp/product/B005CLMJLU/ref=s9_simh_gw_p147_d1_g147_i5?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=0HGN6VKX5W7KPD6NTPG5&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846)

with the realtek driver.  The driver that comes integral with Ubuntu recognizes the adapter but will not connect.  The driver from Realtek includes an install script that seems quite reliable, you just have to know how to run a bash script.

Upon further research, you might have another alternative.  I looked at Dlink's drivers.  There are Windows drivers that include .cat .inf & .sys files in the drivers folder.  You could download these and try using NDISwrapper.  The software center should have it and the GUI front-end.  If you're using 32 bit Ubuntu you'd need 32 bit WindowsXP/2K drivers,  Ubuntu64 needs 64 bit  WinXP drivers.  Win Vista/Win7 drivers generally don't work.  You're fortunate that Dlink uses this driver style; many vendors just give an .exe file which will not work with NDIS wrapper.  I'm not a fan of NDISwapper;  if it doesn't work I've had it mess up an install big-time but at least Dlink has the correct Windows driver format to be able to use it.

---

### Post by row225 on 2012-07-20
> **mebomechanicno1 said:**
> I regret I have never ever managed to get a wireless adaptor card to work, but people say it is possible, and I suggest you start by reading this article
 
[http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/)

yeah ,i did read this article and tried unsuccessfully. thanks

---

### Post by row225 on 2012-07-20
> **kurt18947 said:**
> Here's a link to a pretty good site to wireless driver information.  This ain't gonna be simple.  Note this is for rev_A2.

[http://www.wikidevi.com/wiki/D-Link_DWA-525_rev_A2](http://www.wikidevi.com/wiki/D-Link_DWA-525_rev_A2)

If you want to develop knowledge,  you can work to get your internal card working.   If you just want your wireless to work, you might consider a nano USB adapter that is known to work.  I'm using one of these on a Thinkpad with a built-in G speed Wifi:

[http://www.amazon.com/gp/product/B005CLMJLU/ref=s9_simh_gw_p147_d1_g147_i5?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=0HGN6VKX5W7KPD6NTPG5&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846](http://www.amazon.com/gp/product/B005CLMJLU/ref=s9_simh_gw_p147_d1_g147_i5?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=0HGN6VKX5W7KPD6NTPG5&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846)

with the realtek driver.  The driver that comes integral with Ubuntu recognizes the adapter but will not connect.  The driver from Realtek includes an install script that seems quite reliable, you just have to know how to run a bash script.

Upon further research, you might have another alternative.  I looked at Dlink's drivers.  There are Windows drivers that include .cat .inf & .sys files in the drivers folder.  You could download these and try using NDISwrapper.  The software center should have it and the GUI front-end.  If you're using 32 bit Ubuntu you'd need 32 bit WindowsXP/2K drivers,  Ubuntu64 needs 64 bit  WinXP drivers.  Win Vista/Win7 drivers generally don't work.  You're fortunate that Dlink uses this driver style; many vendors just give an .exe file which will not work with NDIS wrapper.  I'm not a fan of NDISwapper;  if it doesn't work I've had it mess up an install big-time but at least Dlink has the correct Windows driver format to be able to use it.

indeed, it is the A2 version that's why its bothering so much, i will try the cross-install with the windows drivers and see if its work, the thing is ,the Desktop am using is for the department and they are all using this wi-fi adapter on win 7, i installed Linux because i need it to make NS2 work properly and do some simulations (am doing some research on WSN)
thanks i will let you know how it goes.

---

### Post by jdldeauna on 2012-07-23
Hi row225 any luck installing the wireless adapter? I'm going through similar difficulties. Thanks.

---

### Post by row225 on 2012-07-23
> **jdldeauna said:**
> Hi row225 any luck installing the wireless adapter? I'm going through similar difficulties. Thanks.


Unfortunately ,i've tried the ndiswrapper command to install the driver from the inf file for windows. but that was unsuccessful. 
the driver has been installed correctly but when you list to see if its working , an error message tells you that its not the correct driver! when i just copied the files from the Driver-Disk.
guess i have to find a usb modem stick to use until i find a solution :(

---

### Post by kurt18947 on 2012-07-24
> **row225 said:**
> Unfortunately ,i've tried the ndiswrapper command to install the driver from the inf file for windows. but that was unsuccessful. 
the driver has been installed correctly but when you list to see if its working , an error message tells you that its not the correct driver! when i just copied the files from the Driver-Disk.
guess i have to find a usb modem stick to use until i find a solution :(

That is in part why I'm not much of a fan of NDISwrapper.  Do you know if the drivers on the CD are 32 bit or 64 bit?  As far as I know, if you have 64 bit Linux you must use 64 bit Windows drivers with NDISwapper.  I wonder if the drivers on the CD were 32 bit and you have 64 bit?  Other than that, I'm pretty hopeless with NDISwrapper.

---

### Post by wildmanne39 on 2012-07-24
Hi, please post the output of:
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

### Post by Bufeu on 2012-07-24
Also, the output of *ifconfig* and *route -n* should be helpful.

---

### Post by row225 on 2012-07-27
> **wildmanne39 said:**
> Hi, please post the output of:
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

here is the output,sorry i could not make it earlier
```
williams@williams-Veriton-M680G:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux williams-Veriton-M680G 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
williams@williams-Veriton-M680G:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82578DM Gigabit Network Connection [8086:10ef] (rev 06)
	Subsystem: Acer Incorporated [ALI] Device [1025:8000]
	Kernel driver in use: e1000e
--
01:01.0 Network controller [0280]: Ralink corp. Device [1814:5360]
	Subsystem: D-Link System Inc Device [1186:3c05]
williams@williams-Veriton-M680G:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 04ca:002f Lite-On Technology Corp.
Bus 002 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 004: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800 (HSPA modem)
williams@williams-Veriton-M680G:~$ rfkill list all
williams@williams-Veriton-M680G:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1
isofs                  39553  1
nls_iso8859_1          12617  1
nls_cp437              12751  1
vfat                   17308  1
fat                    55605  1 vfat
uas                    17699  0
usb_storage            39646  1
bnep                   17830  2
rfcomm                 38139  0
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_hdmi     31775  1
snd_hda_codec_realtek   174055  1
snd_hda_intel          32765  3
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414603  3
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  0
mei                    36570  0
tpm_tis                18308  0
ppdev                  12849  0
parport_pc             32114  1
psmouse                72846  0
mac_hid                13077  0
serio_raw              13027  0
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0
hid                    77367  1 usbhid
e1000e                140005  0

```

---

### Post by row225 on 2012-07-27
williams@williams-Veriton-M680G:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:87:fc:68:ac:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fbec0000-fbee0000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:55536 (55.5 KB)  TX bytes:55536 (55.5 KB)

williams@williams-Veriton-M680G:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by wildmanne39 on 2012-07-27
Hi, the driver you need is in ubuntu but the device needs to be added, but I do not know if this well work but we can try.

Please do:
```
echo "1814 5360" > /sys/bus/pci/drivers/rt2800pci/new_id
```
Then:
```
modinfo rt2800pci
```
see if 1814 5360 is listed now in the output.
If so do:
```
sudo modprobe rt2800pci
```
does it come on?
Thanks

---

### Post by row225 on 2012-07-30
i posted the output some days ago but apparently it did not show on the forum i dont know how, but anyway am posting the output again for any help thanks. 
```

[FONT=Batang][SIZE=3]williams@williams-Veriton-M680G:~$ cat /etc/lsb-release; uname -a[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_ID=Ubuntu[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_RELEASE=12.04[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_CODENAME=precise[/SIZE][/FONT]
[FONT=Batang][SIZE=3]DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Linux williams-Veriton-M680G 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux[/SIZE][/FONT]
[FONT=Batang][SIZE=3]williams@williams-Veriton-M680G:~$ lspci -nnk | grep -iA2 net[/SIZE][/FONT]
[FONT=Batang][SIZE=3]00:19.0 Ethernet controller [0200]: Intel Corporation 82578DM Gigabit Network Connection [8086:10ef] (rev 06)[/SIZE][/FONT]
[SIZE=3][FONT=Batang]           Subsystem: Acer Incorporated [ALI] Device [1025:8000][/FONT][/SIZE]
[SIZE=3][FONT=Batang]           Kernel driver in use: e1000e[/FONT][/SIZE]
[FONT=Batang][SIZE=3]--[/SIZE][/FONT]
[FONT=Batang][SIZE=3]01:01.0 Network controller [0280]: Ralink corp. Device [1814:5360][/SIZE][/FONT]
[SIZE=3][FONT=Batang]           Subsystem: D-Link System Inc Device [1186:3c05][/FONT][/SIZE]
[FONT=Batang][SIZE=3]williams@williams-Veriton-M680G:~$ lsusb[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Bus 002 Device 003: ID 04ca:002f Lite-On Technology Corp.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Bus 002 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Bus 001 Device 004: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800 (HSPA modem)[/SIZE][/FONT]
[FONT=Batang][SIZE=3]williams@williams-Veriton-M680G:~$ rfkill list all[/SIZE][/FONT]
[FONT=Batang][SIZE=3]williams@williams-Veriton-M680G:~$ lsmod[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Module                  Size  Used by[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nls_utf8               12493  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]isofs                  39553  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nls_iso8859_1          12617  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nls_cp437              12751  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]vfat                   17308  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]fat                    55605  1 vfat[/SIZE][/FONT]
[FONT=Batang][SIZE=3]uas                    17699  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]usb_storage            39646  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]bnep                   17830  2[/SIZE][/FONT]
[FONT=Batang][SIZE=3]rfcomm                 38139  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]bluetooth             158438  10 bnep,rfcomm[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_hda_codec_hdmi     31775  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_hda_codec_realtek   174055  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_hda_intel          32765  3[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_hwdep              13276  1 snd_hda_codec[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_midi           13132  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_rawmidi            25424  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_midi_event     14475  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_timer              28931  2 snd_pcm,snd_seq[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
[FONT=Batang][SIZE=3]i915                  414603  3[/SIZE][/FONT]
[FONT=Batang][SIZE=3]drm_kms_helper         45466  1 i915[/SIZE][/FONT]
[FONT=Batang][SIZE=3]drm                   197692  4 i915,drm_kms_helper[/SIZE][/FONT]
[FONT=Batang][SIZE=3]i2c_algo_bit           13199  1 i915[/SIZE][/FONT]
[FONT=Batang][SIZE=3]video                  19068  1 i915[/SIZE][/FONT]
[FONT=Batang][SIZE=3]soundcore              14635  1 snd[/SIZE][/FONT]
[FONT=Batang][SIZE=3]snd_page_alloc         14108  2 snd_hda_intel,snd_pcm[/SIZE][/FONT]
[FONT=Batang][SIZE=3]wmi                    18744  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]mei                    36570  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]tpm_tis                18308  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]ppdev                  12849  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]parport_pc             32114  1[/SIZE][/FONT]
[FONT=Batang][SIZE=3]psmouse                72846  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]mac_hid                13077  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]serio_raw              13027  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]lp                     17455  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]parport                40930  3 ppdev,parport_pc,lp[/SIZE][/FONT]
[FONT=Batang][SIZE=3]usbhid                 41906  0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]hid                    77367  1 usbhid[/SIZE][/FONT]
[FONT=Batang][SIZE=3]e1000e                140005  0[/SIZE][/FONT]

```
 
oh my bad i was looking for any reply and i cldnt see it under my thread thats make me post it twice.

---

### Post by row225 on 2012-07-30
morning and thanks for your help
here is the output
```

[FONT=Batang][SIZE=3]williams@williams-Veriton-M680G:~$ echo "1814 5360" > /sys/bus/pci/drivers/rt2800pci/new_id[/SIZE][/FONT]
[FONT=Batang][SIZE=3]bash: /sys/bus/pci/drivers/rt2800pci/new_id: No such file or directory[/SIZE][/FONT]

```
 
an then for the list
```

[FONT=Batang][SIZE=3]filename:       /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko[/SIZE][/FONT]
[FONT=Batang][SIZE=3]license:        GPL[/SIZE][/FONT]
[FONT=Batang][SIZE=3]firmware:       rt2860.bin[/SIZE][/FONT]
[FONT=Batang][SIZE=3]description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]version:        2.3.0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]author:         http://rt2x00.serialmonkey.com[/SIZE][/FONT]
[FONT=Batang][SIZE=3]srcversion:     88E705B35667EF897566E11[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00005390sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003593sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003592sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003562sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003062sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003060sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007722sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007711sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003390sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007768sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007758sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007748sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007738sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007728sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007727sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001432d00007708sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003092sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003091sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00003090sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00000781sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00000701sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00000681sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]alias:          pci:v00001814d00000601sv*sd*bc*sc*i*[/SIZE][/FONT]
[FONT=Batang][SIZE=3]depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6[/SIZE][/FONT]
[FONT=Batang][SIZE=3]intree:         Y[/SIZE][/FONT]
[FONT=Batang][SIZE=3]vermagic:       3.2.0-23-generic-pae SMP mod_unload modversions 686[/SIZE][/FONT]
[FONT=Liberation Serif]parm:           nohwcrypt:Disable hardware encryption. (bool)[/FONT]
```
 
think its not listed:mad:.

---

### Post by row225 on 2012-07-30
> **wildmanne39 said:**
> Hi, the driver you need is in ubuntu but the device needs to be added, but I do not know if this well work but we can try.
 
Please do:
```
echo "1814 5360" > /sys/bus/pci/drivers/rt2800pci/new_id
```
Then:
```
modinfo rt2800pci
```
see if 1814 5360 is listed now in the output.
If so do:
```
sudo modprobe rt2800pci
```
does it come on?
Thanks
 
its not working this adapter seems to be a  problematic version pffffff

---

### Post by wildmanne39 on 2012-07-30
Hi, no it did not work, you could try ndiswrapper but I am not sure it will work, but you can post in this thread.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

---

### Post by row225 on 2012-08-09
> **wildmanne39 said:**
> Hi, no it did not work, you could try ndiswrapper but I am not sure it will work, but you can post in this thread.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

could anybody explain to me how i can use this patch for the ralink 5360
[http://www.spinics.net/lists/linux-wireless/msg90498.html](http://www.spinics.net/lists/linux-wireless/msg90498.html)
thanks in advance

---

### Post by wildmanne39 on 2012-08-09
Hi, my good friend chili555 and I worked on this all afternoon to get it to work, this should compile fine, it did on two machines.

Please be sure you have a wired connection and do:
```
sudo apt-get install linux-headers-generic build-essential
```

Now go here and download compat-wireless-2.6.tar.bz2 to your desktop. [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

When you have the file on your desktop, right-click it and select Extract Here. Open the folder it extracts and go down to drivers/net/wireless/rt2x00/rt2800. 

In the file /drivers/net/wireless/rt2x00/rt2800.h around line 54 add the line as I have highlighted:
> * RF3053 2.4G/5G 3T3R(RT3883/RT3563/RT3573/RT3593/RT3662)
[COLOR="Red"]* RF5360 2.4G 1T1R[/COLOR]
* RF5370 2.4G 1T1R
* RF5390 2.4G 1T1R
around line 71 add the highlighted line:
> #define RF3320 0x000b
#define RF3322 0x000c
#define RF3053 0x000d
[COLOR="Red"]#define RF5360 0x5360[/COLOR]
#define RF5370 0x5370
#define RF5372 0x5372
#define RF5390 0x5390
In the file /drivers/net/wireless/rt2x00/rt2800lib.c around line 2063 add the highlighted text.
> case RF3052:
rt2800_config_channel_rf3052(rt2x00dev, conf, rf, info);
break;
[COLOR="Red"]case RF5360:[/COLOR]
case RF5370:
case RF5372:
case RF5390:

Also change highlighted text around line 2553:
Quote:
> rt2800_rfcsr_write(rt2x00dev, 7, rfcsr);
break;
[COLOR="Red"]case RF5360:[/COLOR]
case RF5370:
case RF5372:
case RF5390:

add highlighted text around line 4268.
> case RF3022:
case RF3052:
case RF3320:
[COLOR="Red"]case RF5360:[/COLOR]
case RF5370:
case RF5372:
case RF5390:

add highlighted text around line 4583.
> (rt2x00_rf(rt2x00dev, RF3020) ||
rt2x00_rf(rt2x00dev, RF2020) ||
rt2x00_rf(rt2x00dev, RF3021) ||
rt2x00_rf(rt2x00dev, RF3022) ||
rt2x00_rf(rt2x00dev, RF3320) ||
[COLOR="Red"]rt2x00_rf(rt2x00dev, RF5360) ||[/COLOR]
rt2x00_rf(rt2x00dev, RF5370) ||
rt2x00_rf(rt2x00dev, RF5372) ||
rt2x00_rf(rt2x00dev, RF5390))

add highlighted text around line 4668.
> case RF3320:
case RF3052:
[COLOR="Red"]case RF5360:[/COLOR]
case RF5370:
case RF5372:
case RF5390: 

In the file /drivers/net/wireless/rt2x00/rt2800pci.c around line 1191 add the highlighted text.
> #ifdef CONFIG_RT2800PCI_RT53XX
[COLOR="Red"]        { PCI_DEVICE(0x1814, 0x5360) },[/COLOR]
	{ PCI_DEVICE(0x1814, 0x5362) },
	{ PCI_DEVICE(0x1814, 0x5390) },
	{ PCI_DEVICE(0x1814, 0x5392) },
	{ PCI_DEVICE(0x1814, 0x539a) },
	{ PCI_DEVICE(0x1814, 0x539f) },
#endif

In a terminal:


```
cd Desktop/compat-wireless-2012-05-10 [COLOR="Red"]<--or whatever version was extracted, if not 2012-05-10[/COLOR]
sudo su
./scripts/driver-select rt2x00
make
make install
exit
```
When there is an upgrade to the kernel you will need to recompile this driver:
```
cd Desktop/compat-wireless-2012-05-10
sudo su
./scripts/driver-select restore
./scripts/driver-select rt2x00
make clean
make
make install
exit
```
Thanks

---

### Post by row225 on 2012-09-19
Hi all
Sorry for the long silence, i have been away for long, now am back and just tried the link
you sent me, only to find that things have changed in the website ( of course lol)
but i did find a file already compiled as you told and it working 100 percent now....:popcorn:
Thank you so much it saves me to use data bundles!!! thanks a lot to you and your friend for your assistance, i mark it as solved!
:KS=D>
here is the link : [http://www.orbit-lab.org/kernel/compat-wireless/](http://www.orbit-lab.org/kernel/compat-wireless/)
the version i used is : compat-wireless-2012-07-03

---

### Post by quello on 2012-09-25
Hi,
 
I've been battling to also get the DWA-525 Ralink5360 working on 12.04 Server.
 
In Row225's last post, he mentioned that he found a an already compiled driver and that it worked 100%.
 
I am very new to Linux and compiling, etc. Would you therefore kindly let me know of the exact steps to take to download and install the driver?
 
In the site refered to by Row225, namely, [http://www.orbit-lab.org/kernel/compat-wireless/2012/07/](http://www.orbit-lab.org/kernel/compat-wireless/2012/07/), I find 3 driver versions namely, [compat-wireless-2012-07-03.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless/2012/07/compat-wireless-2012-07-03.tar.bz2"), [compat-wireless-2012-07-03-pc.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless/2012/07/compat-wireless-2012-07-03-pc.tar.bz2") and [compat-wireless-2012-07-03-p.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless/2012/07/compat-wireless-2012-07-03-p.tar.bz2"). Which of these would be the correct, compiled driver?
 
What steps do I take to install the compiled driver?
 
Thank you so much for any assistance.

---

### Post by kaartz on 2012-11-07
I'm also looking for a solution to make the wireless card working with Ubuntu 12.10. Please let me know how to use the pre-compiled compat-wireless package.

---

### Post by kaartz on 2012-11-07
> **quello said:**
> Hi,
 
I've been battling to also get the DWA-525 Ralink5360 working on 12.04 Server.
 
In Row225's last post, he mentioned that he found a an already compiled driver and that it worked 100%.
 
I am very new to Linux and compiling, etc. Would you therefore kindly let me know of the exact steps to take to download and install the driver?
 
In the site refered to by Row225, namely, [http://www.orbit-lab.org/kernel/compat-wireless/2012/07/](http://www.orbit-lab.org/kernel/compat-wireless/2012/07/), I find 3 driver versions namely, [compat-wireless-2012-07-03.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless/2012/07/compat-wireless-2012-07-03.tar.bz2"), [compat-wireless-2012-07-03-pc.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless/2012/07/compat-wireless-2012-07-03-pc.tar.bz2") and [compat-wireless-2012-07-03-p.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless/2012/07/compat-wireless-2012-07-03-p.tar.bz2"). Which of these would be the correct, compiled driver?
 
What steps do I take to install the compiled driver?
 
Thank you so much for any assistance.

Hi,

It's very simple!

You have to just download the source from here: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1.tar.bz2)

Step1: unpack the tar ball
```

cd <where you downloaded and unpacked>/compat-wireless-2012-11-06/

```

Step2: 
```

sudo su

```

Step3:
```

./scripts/driver-select rt2x00

```

Step4:
```

modprobe rt2800pci

```

The WiFi card will detect wireless networks!

---

### Post by chili555 on 2012-11-08
> **kaartz said:**
> Hi,

It's very simple!

You have to just download the source from here: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1.tar.bz2)

Step1: unpack the tar ball
```

cd <where you downloaded and unpacked>/compat-wireless-2012-11-06/

```

Step2: 
```

sudo su

```

Step3:
```

./scripts/driver-select rt2x00

```

Step4:
```

modprobe rt2800pci

```

The WiFi card will detect wireless networks!You may wish to add how to unpack the tarball; make and make install to your HOWTO. Also, please note that build-essential and linux-headers-generic are required.

---

### Post by CGeek on 2013-01-07
Ok, so I have a DWA-525 Ralink5360 wireless NIC and I've been searching and trying methods all through the ubuntuforums and otherwise, namely:

[http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/)
[http://ubuntuforums.org/showthread.php?t=1559576](http://ubuntuforums.org/showthread.php?t=1559576)
[http://ubuntuforums.org/showpost.php?p=10055176&postcount=4](http://ubuntuforums.org/showpost.php?p=10055176&postcount=4)
etc...

The final thing I tried was this: [http://ubuntuforums.org/showpost.php?p=12343622](http://ubuntuforums.org/showpost.php?p=12343622)
There was even a post telling to edit some lines to include rt5360 and I checked the latest versions and they were already there...

The final result is that ubuntu 12.04 is not even displaying the wireless card be it in the notification area nor through the iwconfig
lshw -C network: 
*-network UNCLAIMED
           description: Network controller
           product: Ralink corp.
           vendor: Ralink corp.
           physical id: 3
           bus info: pci@0000:05:03.0
           version: 00
           width: 32 bits
           clock: 33MHz
           capabiities: cap_list
           configuration: latency=32 maxlatency=4 mingnt=2
           resources: memory:e3000000-e300ffff

I also noticed some error messages during booting and when I modprobe rt2x00pci in dmesg: 
[   26.588543] rt2800pci 0000:05:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.598629] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.608682] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.618762] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.620009] psmouse serio1: Failed to enable mouse on isa0060/serio1
[   26.628805] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.638862] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.648917] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.658960] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.669015] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.679060] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.689154] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.699194] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.709300] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.719389] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.729439] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.739614] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.749664] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.759910] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   26.759949] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0xffff detected.
[   26.759977] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   26.760043] rt2800pci 0000:05:03.0: PCI INT A disabled

That seems to me like some sort of error in the driver itself...do I use one of the older ones in [http://www.orbit-lab.org/kernel/compat-wireless/](http://www.orbit-lab.org/kernel/compat-wireless/) ?

Please advise.

---

### Post by chili555 on 2013-01-08
> [ 26.759949] phy0 -> rt2800_init_eeprom: Error - [COLOR="Red"]Invalid RF chipset 0xffff detected.[/COLOR]
[ 26.759977] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 26.760043] rt2800pci 0000:05:03.0: PCI INT A disabled
It seems that the driver doesn't like the chipset! Let's do a full diagnostic workup and see if we can fix it. Please post:```
lspci -nn | grep 0280
lsb_release -d
modinfo rt2800pci | head -n3
```Thanks.

---

### Post by CGeek on 2013-01-08
lsb_release -d
Description:    Ubuntu 12.04.1 LTS

lspci -nn | grep 0280
05:03.0 Network controller [0280]: Ralink corp. Device [1814:5360]

modinfo rt2800pci | head -n3
filename:       /lib/modules/3.2.0-35-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin

---

### Post by chili555 on 2013-01-09
> /lib/modules/3.2.0-35-generic/*updates*/drivers/net/wireless/rt2x00/rt2800pci.koThe *updates* in the file location indicates it's a newer version than the in-kernel driver; probably one you compiled. I wonder if the process of adding device IDs to the code went wrong. Let's try a different approach:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```Reboot and let us have your report.

---

### Post by CGeek on 2013-01-10
Heh, this requires an internet connection from the problematic desktop

I downloaded the package from my laptop and tried installing it using gdebi but I'm guessing a backport's use is through internet updates...

I can try to get hold of a usb modem but if there is another way, please advise.

P.S. Thank you very much for your help

---

### Post by chili555 on 2013-01-10
You can install it from a download transferred on a USB key easily. You need both the -generic as well as the package matching your running kernel; i.e. 3.2.0-35-generic. Therefor, you'd need the packages linux-backports-modules-cw-3.6-precise-generic and linux-backports-modules-cw-3.6-3.2.0-35-generic. You should then be able to install both with gdebi or, if you are old-skool, from a terminal. Assuming you drag-n-dropped them to your desktop:```
cd Desktop
sudo dpkg -i linux-backports*.deb
```There may be some missing dependencies. If so, you will get the notification; something like 'linux-backports depends on some_package, but some_package is not installed so leaving unconfigured.' If so, go get the missing dependency and install it and try backports again. It is eminently do-able.

Be sure you get and install the packages appropriate to your architecture; either 32- or 64-bit. Find out with:```
arch
```If 'arch' returns i686, then you need 32-bit packages, shown in the attached as i[COLOR="Red"]3[/COLOR]86 (I know, it's a puzzle.)

Post back if you get stuck.

---

### Post by CGeek on 2013-01-10
I just sudo apt-get download the packages and yes, I am aware of the intel architectures, thank you for making sure of it.

After installing, I rebooted and it still gives the same error (also I'm noticing a bluetooth-related error too, which is funny because I have no bluetooth devices connected)

I hope this doesn't mean we've reached the end of the line and I apologize for any inconveniences.

---

### Post by chili555 on 2013-01-10
The same error being invalid chipset? Does the system try to load rt2800pci, error out and give up? What is the bluetooth error. I hope it offers a clue!

I struggle and often don't quite succeed trying to explain quite thoroughly to new users and yet briefly to experienced users. I sometimes mis-judge who is which and hope I was not offensive. I know when I started in Linux 212 years ago, I was baffled at times and hardly anyone explained anything. I vowed to not ever be those guys and I hope I've not swung too far on the pendulum.

---

### Post by CGeek on 2013-01-10
I apologize for giving you the impression that I was offended, I just wanted you to know that I am a bit experienced with linux and that you needn't go over everything in details :)

Here are the interesting dmesg portions

```
[   27.486572] Compat-drivers backport release: compat-drivers-2012-12-14-3
[   27.486575] Backport based on linux-next.git next-20121218
[   27.486576] compat.git: linux-next.git
[   27.593024] cfg80211: Calling CRDA to update world regulatory domain
[   27.654520] rt2800pci 0000:05:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.664579] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.674633] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.684695] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.694746] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.694795] psmouse serio1: Failed to enable mouse on isa0060/serio1
[   27.704873] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.714924] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.724984] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.735035] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.745115] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.755183] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.765260] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.775326] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.785403] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.795470] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.805547] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.815619] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.825697] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00000580, value=0xffffffff
[   27.825765] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0xffff detected.
[   27.825821] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   27.825901] rt2800pci 0000:05:03.0: PCI INT A disabled


repeats the following 2 lines 6 times
[   30.835792] bluetooth: disagrees about version of symbol __pskb_copy
[   30.835797] bluetooth: Unknown symbol __pskb_copy (err -22)

[   30.904124] init: bluetooth main process (917) terminated with status 1
[   30.904148] init: bluetooth main process ended, respawning
[   30.939800] vboxdrv: Found 2 processor cores.
[   30.940692] vboxdrv: fAsync=0 offMin=0x1cc offMax=0xbe0
[   30.940745] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   30.940747] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   30.953684] vboxpci: IOMMU not found (not registered)
[   30.996176] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X

repeats them 7 times

[   31.052088] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   31.052295] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.052555] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.092193] init: bluetooth main process (1184) terminated with status 1
[   31.092215] init: bluetooth main process ended, respawning

repeats them 2 times

[   31.117197] Bridge firewalling registered

repeats them 5 times

[   31.191956] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.216212] init: bluetooth main process (1277) terminated with status 1
[   31.216235] init: bluetooth main process ended, respawning

repeats them 3 times

[   31.247839] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)

repeats them 4 times

[   31.288195] ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   31.336121] init: bluetooth main process (1379) terminated with status 1
[   31.336144] init: bluetooth main process ended, respawning

repeats them 7 times

[   31.564104] init: bluetooth main process (1508) terminated with status 1
[   31.564129] init: bluetooth main process ended, respawning

repeats them 7 times

[   31.752127] init: bluetooth main process (1556) terminated with status 1
[   31.752150] init: bluetooth main process ended, respawning

repeats them 7 times

[   31.956132] init: bluetooth main process (1597) terminated with status 1
[   31.956157] init: bluetooth main process ended, respawning
[   31.967547] bluetooth: disagrees about version of symbol __pskb_copy
[   31.967550] bluetooth: Unknown symbol __pskb_copy (err -22)
[   32.087664] Ebtables v2.0 registered
[   32.099746] ip6_tables: (C) 2000-2006 Netfilter Core Team

repeats them 6 times

[   32.760095] init: bluetooth main process (1634) terminated with status 1
[   32.760119] init: bluetooth main process ended, respawning

repeats them 7 times

[   32.852138] init: bluetooth main process (1693) terminated with status 1
[   32.852163] init: bluetooth main process ended, respawning
[   32.856716] init: plymouth-upstart-bridge main process (913) killed by TERM signal

repeats them 7 times

[   33.004141] init: bluetooth main process (1720) terminated with status 1
[   33.004164] init: bluetooth main process ended, respawning

repeats them 7 times

[   33.088157] init: bluetooth main process (1835) terminated with status 1
[   33.088184] init: bluetooth respawning too fast, stopped
[   33.105550] bluetooth: disagrees about version of symbol __pskb_copy
[   33.105554] bluetooth: Unknown symbol __pskb_copy (err -22)
```

---

### Post by chili555 on 2013-01-11
Yikes. You have one unhappy driver there. I am a bit unsure how to proceed. I suspect the addition of the pci.id 1814:5360 is a bit faulty in backports. I participated here: [http://ubuntuforums.org/showthread.php?p=12161447](http://ubuntuforums.org/showthread.php?p=12161447) See post #19. However, in post #20, the OP says the later compat-wireless package has the device added and it's working 100%.

The backports package is supposed to be an Ubuntu-ized version of compat-wireless, so I don't understand why backports doesn't work and the OP says the compat package compiled from source is:> it working 100 percent now....Does the card work seamlessly with other operating systems? With another Linux distro? Can we rule out a hardware issue?

---

### Post by CGeek on 2013-02-01
I made a fresh install (the first since a few years now) but I still  needed an internet connection to be able to update it properly and  install the required packages

I connected it to my other box using a USB Hub-to-Hub connection, made all the upgrades and ran these two lines

sudo apt-get install linux-backports-modules-cw-3.6-precise-generic-pae linux-backports-modules-net-3.6-precise-generic-pae

rebooted and that did the trick

Thank you very much

---

### Post by vezolmi on 2013-04-11
In Lubuntu 12.04 I have solved the issue as stated in [http://ubuntuforums.org/showthread.php?t=2008849&p=12302336#post12302336](http://ubuntuforums.org/showthread.php?t=2008849&p=12302336#post12302336)

---

### Post by Muzafsh on 2013-05-27
> **Wild Man said:**
> Hi, please post the output of:
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


1:~$ cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux ALHAMDULILLAH11 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 17:35:01 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



```


1:~$ lspci -nnk | grep -iA2 net
```
0a:0b.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet [14e4:1654] (rev 03)
    Subsystem: IBM Device [1014:02f8]
    Kernel driver in use: tg3
--
0a:0c.0 Network controller [0280]: Ralink corp. Device [1814:5360]
    Subsystem: D-Link System Inc Device [1186:3c05]



```


lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04ca:0061 Lite-On Technology Corp. 

```
:~$ iwconfig
```
lo        no wireless extensions.


eth0      no wireless extensions.

```



:~$ rfkill list all
```
- No output -

```


:~$ lsmod
```
Module                  Size  Used by
snd_intel8x0           38570  2 
snd_ac97_codec        134869  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97275  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
ppdev                  17113  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32866  1 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_intel8x0,snd_pcm
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14620  1 rt2800pci
rt2x00lib              55326  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
i915                  478189  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mac_hid                13253  0 
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
floppy                 70207  0 
tg3                   152085  0 



```

**@Wildman** ... Help most appreciated !!!

thanks,

---

