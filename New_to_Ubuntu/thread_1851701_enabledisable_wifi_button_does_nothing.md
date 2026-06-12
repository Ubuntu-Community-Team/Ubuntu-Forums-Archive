---
title: "enable/disable wifi button does nothing"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by Vanity on 2011-09-28
Hello,

I am absolutely new to Ubuntu and well all linux for that matter. I am having issues getting my wireless to work on my laptop. I have an older Gateway M675 laptop. the enable/disable wifi button does absolutely nothing. is there a way to enable my wireless network adapter without the switch? I typed the command sudo lshw -C network and it tells me I have a broadcom network adapter. 

can anyone help me out?

---

### Post by wildmanne39 on 2011-09-28
Hi, welcome to the forum! Please open a terminal by hitting ctrl+alt+t then copy and paste these commands into it then paste the results here:
```
cat /etc/lsb-release; uname -a
``` 
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Vanity on 2011-09-28
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux kenneth-Gateway-M675 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

 lspci -nnk grep -iA2 net
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of A2
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

 rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kenneth@kenneth-Gateway-M675:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  0 
isofs                  39571  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
b43legacy             127415  0 
mac80211              257001  1 b43legacy
snd_seq_midi           13132  0 
joydev                 17322  0 
binfmt_misc            13213  1 
pcmcia                 39671  0 
ppdev                  12849  0 
snd_rawmidi            25269  1 snd_seq_midi
yenta_socket           27230  0 
radeon                900494  3 
cfg80211              156212  2 b43legacy,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia_rsrc            18292  1 yenta_socket
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
ttm                    65184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 radeon
drm                   180037  5 radeon,ttm,drm_kms_helper
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
parport_pc             32111  1 
i2c_algo_bit           13184  1 radeon
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
ssb                    45942  1 b43legacy
e1000                 101089  0 
crc_itu_t              12627  1 firewire_core
floppy                 60032  0

---

### Post by Vanity on 2011-09-28
I hope thats right

---

### Post by wildmanne39 on 2011-09-28
Hi, all of them were good but this one and I really need to see the results of it so I can see if the right driver is installed.

Please just copy and paste the command, the results should show both of your networking cards.
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by Vanity on 2011-09-28
lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019]
    Subsystem: Gateway 2000 Device [107b:0601]
    Kernel driver in use: e1000
--
03:02.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)
    Subsystem: Broadcom Corporation Device [14e4:0421]
    Kernel driver in use: b43-pci-bridge

---

### Post by wildmanne39 on 2011-09-28
Hi, the driver is the wrong one just by a little.

Open synaptic package manager type bcm into the search window in synaptic and it will show you what is installed for your broadcom card.

Then uninstall the ones that have a green square by them, it should only be between 2 and 4 that are green there if there are more then you are probably in the wrong place so do not uninstall them.

Restart your computer then run this command please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
let it finish installing then disconnect your wired connection and restart your computer.
Thank you

---

### Post by Vanity on 2011-09-28
only one box is green it is the libklibc package installed version for ubuntu 1.5.20-1ubuntu6 description is minimal libc subset for use with initramfs.

Is this one of the ones I need to uninstall?

Thank you for your help sir

---

### Post by wildmanne39 on 2011-09-29
Hi, just any of the ones that I have showing in this screenshot and nothing else.

You may have activated the driver in additional drivers if so deactivate it then restart your computer then look in synaptic and make sure none of those in the screenshot are installed then run follow the directions on running the command in my previous post.
Thank you

---

### Post by Vanity on 2011-09-29
Jus the ones with the green box in the screen shot righ?

---

### Post by wildmanne39 on 2011-09-29
Hi, no any of those eight, I was afraid that might confuse you but the  green ones are the ones installed on my computer and I did not want to uninstall them to post the screenshot then have to reinstall them.

So any of the 8 that are in the screenshot.
Thank you

---

### Post by Vanity on 2011-09-29
ok I ran the command as you instructed and let it finish installing and unplugged my wired networking and reboot but am still unable to enable my wireless network card when I click on the network icon the wireless connections link is greyed out. I went back to synaptics package manager and noticed that there are two new packages with green squares next to them. 

Not sure where to go from here.

---

### Post by wildmanne39 on 2011-09-29
Hi, there should be 2 and only 2.

Please post the results of these commands:
```
sudo lshw -C network
``` 
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
ndiswrapper -l
```
```
lsmod | grep b43
```
```
dmesg | egrep 'b43|firm|wlan0'
```
Thank you

---

### Post by Vanity on 2011-09-29
sudo lshw -C network
[sudo] password for kenneth: 
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:5c:ac:9d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.1.5 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:18 memory:e0200000-e021ffff ioport:4000(size=32)
  *-network
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:19 memory:e0304000-e0305fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:1c:91:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

 *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:5c:ac:9d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.1.5 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:18 memory:e0200000-e021ffff ioport:4000(size=32)
  *-network
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:19 memory:e0304000-e0305fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:1c:91:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
kenneth@kenneth-Gateway-M675:~$ clear

kenneth@kenneth-Gateway-M675:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connected
  Default:           yes
  HW Address:        00:E0:B8:5C:AC:9D

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43legacy
  State:             unavailable
  Default:           no
  HW Address:        00:90:4B:1C:91:01

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

lsmod | grep b43
b43legacy             127415  0 
mac80211              257001  1 b43legacy
cfg80211              156212  2 b43legacy,mac80211
ssb                    45942  1 b43legacy


dmesg | egrep 'b43|firm|wlan0'
[    1.703870] b43-pci-bridge 0000:03:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   21.108649] b43legacy-phy0: Broadcom 4306 WLAN found
[   21.132139] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   21.132163] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   21.156082] b43legacy-phy0 debug: Radio initialized
[   21.247587] b43legacy-phy0 debug: Ignoring unconnected 802.11 core
[   22.351397] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   22.351410] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).

---

### Post by Vanity on 2011-09-29
so I went back through the list before you had me input all these commands to show you the outcome and I re rean the command for the drivers or firmware or whatever and I now have only two green boxes in synaptics. 

Then I ran all these commands you asked and these are the findings 

I really appreciate all of your help

---

### Post by wildmanne39 on 2011-09-29
Hi, the firmware is refusing to install, so go back into synaptic and remove the 2 that are there with green squares then restart your computer.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, then disconnect your wired connection. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Run the commands one at a time, and it should work.

If the first command tells you the directory already exists just continue with the next command.
Thank you

---

### Post by Vanity on 2011-09-29
sudo rmmod -f ssb
ERROR: Removing 'ssb': Resource temporarily unavailable


all worked fine until I got to this one is it still going to work?

---

### Post by wildmanne39 on 2011-09-29
Hi, not sure did you run the last command? I have been on here for 14 hours I am going to have to sleep before I continue, that should not have given an error.
Thank you

---

### Post by Vanity on 2011-09-29
yes I ran the last command and it accepted it fine no errors but when I unplugged my wired connection I still had no wifi connection. I understand thank you very much for your help maybe another day we can figure this out. I really do appreciate your help though. 

I will continue researching on it though. 

Thanks again

---

### Post by Vanity on 2011-09-29
I tried running the same commands again this morning and the 2nd to last one gives me the same error ERROR: Removing 'ssb': Resource temporarily unavailable

no clue where to go from here.

---

### Post by wildmanne39 on 2011-09-29
Hi, I do not know why it is being so hard to get the firmware installed.

Open synaptic and show me all the things that are installed for your wireless card, you can take a screenshot by hitting alt+prnt/screen key then post it here by clicking on the paper clip in the window where you type your reply.
Thank you

---

### Post by wildmanne39 on 2011-09-29
Hi, I found an updated driver and firmware that may work better. Use synaptic and uninstall everything there in green again then restart you computer.
[http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
Click on this link it will download your firmware and driver 
then after you downloaded it move it to your home folder then click on your home folder, then you user folder not your download. Now you want to create a folder called wireless then put the download in the folder. After that go back to your terminal and type in:
```
sudo cp -r ~/wireless/* /lib/firmware/
cd /lib/firmware
sudo -s
tar -xzf b43-all-fw.tar_.gz
exit
sudo reboot
```
Run the commands one at a time.
Thank you

---

### Post by waterleat on 2011-09-29
To [wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

I have been following this thread hoping that you will be able to show the bit that I am missing. I too, like <Vanity>, am new to Linux. My laptop is an ACER Travelmate 292LCi. 
From your first reply here is the output from post #2

d@d-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux d-laptop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux


d@d-laptop:~$ lspci -nnk | grep -iA2 net
01:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
01:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200


d@d-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


d@d-laptop:~$ rfkill list all                             [COLOR=Blue]Note here that no output is shown even though command entered[/COLOR]
d@d-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 36110  0 
hid                    67288  1 usbhid
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
pcmcia                 30784  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8740  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20408  1 
ipw2200               135216  0 
rsrc_nonstatic         10015  1 yenta_socket
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
libipw                 39896  1 ipw2200
i915                  288611  3 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
lib80211                5046  2 ipw2200,libipw
drm_kms_helper         29329  1 i915
ppdev                   5259  0 
soundcore               6620  1 snd
intel_agp              24375  2 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
led_class               2864  0 
psmouse                63677  0 
serio_raw               3978  0 
parport_pc             25962  1 
shpchp                 28835  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
ieee1394               81181  1 ohci1394
d@d-laptop:~$ 

I hope that you can point me in right direction

---

### Post by wildmanne39 on 2011-09-29
Hi waterleat, your driver is installed so it will take some more troubleshooting to find the problem, since this is a completely different kind of wireless card please start your own thread then post the information you gave here in the new thread and post a link here to it so I can find it.
Thank you

---

### Post by Vanity on 2011-09-29
here is what drivers are there. none right that one is not a driver for my BCM wireless card. Right? I did as you instructed by putting the saved file into a new wireless folder under my user account. but when running the command I got an error. 

 sudo cp -r ~/wireless/* /lib/firmware/
cp: cannot stat `/home/kenneth/wireless/*': No such file or directory


where did I mess this up?

Thanks

---

### Post by waterleat on 2011-09-29
Thank you for your quick reply 
Setup new thread in Laptop section with my printout info
[http://ubuntuforums.org/showthread.php?t=1852150](http://ubuntuforums.org/showthread.php?t=1852150)
thank you

---

### Post by wildmanne39 on 2011-09-29
Hi, it took me awhile to figure out what happened, I believe you extracted the driver and this one you do not extract like the other one we do it in the terminal, so you need to download it again and move it to your wireless folder in your home folder, then run the commands.

In your screenshot it looks like you are in the wrong place in synaptic, you type bcm into its search window at the top of the window in synaptic please refer to by screenshot in previous post.

We have to make sure there is not anything for your card installed there before we can run those commands.

Have you updated your computer since you installed ubuntu?

If nothing shows in synaptic as being able to be installed or removed for your card, then check and make sure you have backports in synaptic checked, by going into settings,repositories. 
Thank you

---

### Post by Vanity on 2011-09-29
not sure how I am in the wrong place in synaptics. I go to my applications and open synaptoc package manager in the upper right hand corner the search buttin pops up a new dialogue box I type BCM and these are the results I get

---

### Post by Vanity on 2011-09-29
I went into synaptics and went under settings... repositories and saw nothing regarding backports. I have not updated this laptop since the install of ubuntu.

---

### Post by wildmanne39 on 2011-09-29
Hi, that looks better in the last screenshot all I saw packages that said nothing about broadcom.
Did you ever have just these two installed?
> b43-fwcutter,firmware-b43legacy-installer 
if not try to install them from synaptic then disconnect wired connection and restart.
Thank you

---

### Post by wildmanne39 on 2011-09-29
Hi, that maybe why the firmware install failed.

Here is a screenshot of backports.
Thank you

---

### Post by Vanity on 2011-09-29
Ok so I updated them through synaptics package manager and one of them successfully updated but I got an error (first screen shot) for the second one. But when I went into synaptics after they were installed both of them show installed (second screen shot) I unplugged my wired connection and rebooted and still nothing with the wifi nor the wifi button

---

### Post by Vanity on 2011-09-29
okay backports was not checked so I checked it and it had a window of something being downloaded. should I unplug restart and check for wifi now?

---

### Post by wildmanne39 on 2011-09-29
Hi, no that is okay, I did not think that the firmware was going to install correctly it is an issue with 11.04 and this wireless card.

So uninstall both of them then restart your computer and do the follow the directions below please.

I believe you extracted the driver and this one you do not extract like the other one we do it in the terminal, so you need to download it again and move it to your wireless folder in your home folder, then run the commands.
Thank you

---

### Post by Vanity on 2011-09-30
so it still didnt work. I redownloaded the zip file you instructed and ran all commands i think they were all successfully installed. the first screen shot is synaptics after running the commands and reboots.the second is what I got when I entered the commands in terminal.

obviously the BCM drivers didnt install as the synap shows. Did I miss something?

Thanks

---

### Post by wildmanne39 on 2011-09-30
Hi, yes I believe you missed a step or added a step, I installed it on my system last night, and I did manage to come up with that error by extracting it, then putting the extracted file in the wireless folder I created instead of putting just the downloaded file in the wireless folder.

Either you extracted it and then put it in the folder or you did not put the file in the wireless folder you created, or you did not put your wireless folder in your home folder.
Thank you

---

### Post by Vanity on 2011-10-01
So I think I m having an issue with the filing system for ubuntu. I made a folder in my home folder named wireless and I am putting the downloaded folder all.tar in the wireless folder runnign the commands and I am still getting the same are. 

Am I doing it right?

here is a screen shot of where the wireless folder is

I apologize but I am still familiarizing myself with the filing system for linux. Like I said I am a newbie thanks alot for your patience and help.

---

### Post by wildmanne39 on 2011-10-01
Hi, that looks correct, I do not know why you are getting that error.

I will research it and see if I can figure it out.
Thank you

---

### Post by Vanity on 2011-10-03
any luck finding anything about that error message?

---

### Post by wildmanne39 on 2011-10-03
Hi, no I do not know why it failed, but let's try this please:
```
sudo apt-get --purge remove /lib/firmware/b43*
```
Download the b43zip and drag it to your desktop, then unplug your wired connection.

Then try this again:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run these commands one line at a time.
Thank you

---

### Post by Vanity on 2011-10-04
so I downloaded the zip put it to my desktop and ran the commands as instructed. 

I still got the ssb error when it came to that command 

what do you think? could this be a hardware issue?

---

### Post by wildmanne39 on 2011-10-04
Hi, I do not know, I had one other person had that same error a few days ago and I had him complete the rest of the commands and when he restarted it worked.

This is only the second time I have seen this error.
Thank you

---

### Post by Vanity on 2011-10-04
Iran the commands again last night and I got the sbb error again would this maybe have anything to do with the one driver installed for bcm that is there for ubuntu?

---

### Post by wildmanne39 on 2011-10-04
Hi, no I do not think so, that driver is needed for the other driver to work all we are trying to do is unload it then, with the last command it will be reloaded with the b43.

Please make sure there are no green squares in th section of synaptic at bcm.

Then
```
sudo apt-get --purge remove /lib/firmware/b43*
```
Then restart your computer and update your system then:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Then disconnect your wired connection and restart,if you have errors with any of the commands please post them here.
Thank you

---

### Post by Vanity on 2011-10-05
So i uninstalled that driver and it rebooted on its own when it began booting it got hung up for about 30 min so I did a hard reboot and now it is running memory tests over and over again I can upload a pic if you need me to. I am at a complete loss here is it possible I will have to do a complete reload?

---

### Post by wildmanne39 on 2011-10-05
Hi, it hard to say, the commands I gave you should have caused no damage as long as you copied and pasted the complete command.

It is most likely an update that did not agree with the computer like a video card driver.

A hard reboot very often causes file corruption and disk errors.
Thank you

---

### Post by Vanity on 2011-10-05
no I never got to run the commands I simply went into synaptics and removed the only green square I had in there as you tad me and I was rebooting so that I could then go back and run the commands you last gave me.

---

### Post by Vanity on 2011-10-05
this is a picture i took of what the laptop is doing now. it does this process non stop repeatedly. have no clue whats going on.

---

### Post by wildmanne39 on 2011-10-05
Do you remember what it was you removed? since it was under bcm I do not see anything there that would break the system.

It should have been one of these 8 as mentioned in a previous post, I am trying to figure out where to start.
Thank you

---

### Post by wildmanne39 on 2011-10-05
Here is the screenshot.

---

### Post by Vanity on 2011-10-05
yes the one I removed is in the screen shot of post #25 

the green box next to the driver in that screen shot is the one I removed and this started after that.


[http://ubuntuforums.org/attachment.php?attachmentid=203161&d=1317328687](http://ubuntuforums.org/attachment.php?attachmentid=203161&d=1317328687)

---

### Post by wildmanne39 on 2011-10-05
Hi, it is running a memory test, when you get to the grub menu see if you can high light the first kernel then hit enter.

Did it say when you rebooted that it detected faulty memory?

It takes about 16 hours or longer to run a memory test, then it will make another pass if you do not stop it.
Thank you

---

### Post by westie457 on 2011-10-05
@ wildmann39 I think this is the thread you were referring to. If not my mistake. [http://ubuntuforums.org/showthread.php?t=1854033&page=2](http://ubuntuforums.org/showthread.php?t=1854033&page=2) You and anewguy combined to work the magic on a Broadcom 4309 chip.


> go to synaptic package manager and look for and install the STA driver and remove the firmware cutter (essentially we want to reverse everything you have done so far so we are starting at a clean slate again).
by anewguy in this post
[http://ubuntuforums.org/showpost.php?p=11308724&postcount=15@](http://ubuntuforums.org/showpost.php?p=11308724&postcount=15@)
 I think the OP had gotten round to installing the STA driver and you came along and spotted that ndiswrapper was installed.

The above is a brief synopsis of the thread. Would you agree that we both have been trying to install the wrong driver and Vanity -the OP you are now helping should try the STA driver as well.

As for the reason Memory Test is running I have no idea to help.

---

### Post by Vanity on 2011-10-05
is there no way around this memory test?

---

### Post by wildmanne39 on 2011-10-05
Hi westie457, yes that is a good link and you did a great job on that thread too, if my memory serves me.

Right not he can not boot his computer, I believe it is because he removed a package that I did not mean for him to remove.
Thank you

---

### Post by wildmanne39 on 2011-10-05
Hi, you can cancel it, then reboot at the grub menu choose recovery, then root recover with network, then choose to fix broken packages, I may have the directions how it is worded wrong a little, I have not booted into recovery in a long time.

If that does not work drop to the command prompt and try this.
```
sudo apt-get install libklibc
```
Thank you

---

### Post by Vanity on 2011-10-05
I assume when you say "grub menu" you mean where I can enter the bios setup utility? 

anyhow when I enter <esc> to reboot or cancel I have only the options to enter f2 for settings and f10 for bios setup there is no option to choose recovery.

---

### Post by wildmanne39 on 2011-10-05
Hi, no that is not what I mean.

If you have only one operating system, reboot then start hitting the shift key and then you should see the menu, it is still worth a try to see if you can high light the kernel in the first position in the grub menu then hit enter.
Thank you

---

### Post by Vanity on 2011-10-05
no I don't believe I can when I get to the menu I have the option to continue f1 or f2 to enter setup. the menu displays system information and that the RAM passed the cache passed and system BIOS and video BIOS are shadowed then it says event log messages, enter setup to view ERROR followed by 0210 stuck key. if I enter f1 to continue it simply takes me to run the memory test then f2 takes me to Pheonix Bios setup utility

---

### Post by wildmanne39 on 2011-10-05
Hi, you have to be able to get to the boot menu for grub by hitting the shift key as soon as you reboot, otherwise there is nothing we can try except reinstall ubuntu.
Thank you

---

### Post by Vanity on 2011-10-05
okay so i am reinstalling ubuntu this is no problem because I had no data stored to this notebook it is simply a learning tool for me now. I will get back to you once I have completed the install and am ready to begin the troubleshooting once more for the network card. again I want to thank you for all of your help thus far and for your patience as I am a newbie to this OS. 

I have learned quite a bit from you already thank you 

I will get back to you soon 

V

---

### Post by wildmanne39 on 2011-10-05
Hi, your welcome please do not install any wireless drivers until you post here, and go ahead and run all the updates and restart your computer after.
Thank you

---

### Post by Vanity on 2011-10-05
Hi, I will have to run updates because the ubuntu disc I am booting from is a very old version of ubuntu but in the updates will it automatically try to install and update for the wireless?

---

### Post by wildmanne39 on 2011-10-05
Hi, it will not install any drivers for your card, so what version of ubuntu are you starting with? it is best to do a clean install to make sure no configuration files get messed up.
Thank you

---

### Post by Vanity on 2011-10-05
it is version 6.06 it was the only disk I already have.

---

### Post by wildmanne39 on 2011-10-05
Hi, that is a lot of upgrades and you run a much greater risk of something not working right.

Can you not go to the ubuntu download page and download and burn the iso image to disc?
Thank you

---

### Post by Vanity on 2011-10-06
Hi, 
Latest Ubuntu is loaded and updates are almost complete.

---

### Post by wildmanne39 on 2011-10-06
Hi, I am on my way to bed, so if it is all right with you I would rather do it tomorrow while I am more rested so I do not make any mistakes.
Thank you

---

### Post by Vanity on 2011-10-06
Hi,

Whenever you are ready sir, I am.

---

### Post by wildmanne39 on 2011-10-06
Hi, now that you have ubuntu installed run updates and if there are any install them then restart your computer, and I want to review your information so we get this right the first time.
Thank you

---

### Post by Vanity on 2011-10-06
all updates are installed and the machine has been rebooted.

---

### Post by wildmanne39 on 2011-10-06
Hi, this is what we are going to do, this should work if the install does not fail,watch for errors and post them here.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
then unplug your wired connection and restart.

I am afraid you will get errors because it is a known bug with this older card, the same thing happened to me.

I have to be out for a few minutes.
Thank you

---

### Post by Vanity on 2011-10-06
you were right there were errors here is a screen shot of terminal and all the errors

---

### Post by wildmanne39 on 2011-10-06
Hi, none of those errors said anything about your broadcom driver, it appears that many updates are broke and you will not be able to try to install the b43 firmware until you have fixed them.

Please run this command and if there are errors post all of them here:
```
sudo apt-get update && sudo apt-get upgrade
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Vanity on 2011-10-06
here are all the errors and there are quite a bit

---

### Post by wildmanne39 on 2011-10-06
Hi, that is a little above my pay grade, I was hoping there was more on why the errors occurred, I have a feeling it is because you upgraded instead of doing a clean install, which means to many files are messed up, but I hope I am wrong. 

I think you need to start a new thread on update manager not working and see if someone can help fix it, sometimes I can but I am over my head on this one.
Thank you

---

### Post by Vanity on 2011-10-06
okay will do, however I did not do an upgrade. after you told me a clean install would be best I downloaded the iso off of the website burned it and performed a clean install last night then ran all the updates. 

I will begin a new thread though thank you.

---

### Post by wildmanne39 on 2011-10-06
Hi, okay after you get your update manager issue fixed, come back and we will see if we can get the wireless card working.
Thank you

---

### Post by westie457 on 2011-10-06
Hi Vanity and wildmanne39, have seen the difficulties both of you are having to sort what for you wildmanne39 is normally a relatively easy procedure and have it turn into something above the pay-grade. Anyway have just spent about an hour searching [www.googlubuntu.com](www.googlubuntu.com) finally getting the right question. This thread [here]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/114401") has what may be a solution even though the specific problem was different. The solution to fix update-manager starts in post #3.

Hope this helps the pair of you and good luck.

---

### Post by Vanity on 2011-10-06
Hello westie457

I read though the link you posted and I will input all of those command this evening when I can I am in class right now and will be stuck here for about four more hours. I appreciate The support and research you did and I hope to be able to provide this kind of help to others down the road. Well I'll get those results posted when I can thanks again.

V

---

### Post by wildmanne39 on 2011-10-06
Hi westie457, thank you for that link, this card is hard enough because there is a bug in 11.04 that makes it hard to install the firmware for that card, I suspect even when this problem is fixed we will have an issue, but I want to try to do it with apt-get before going to the zip file I have because we had trouble with it last time.

This is the only time that the zip file I use has failed, I have even had this card work with the zip file that was identical to this card.
Thank you again.

---

### Post by Vanity on 2011-10-07
Westie457 

here are the results of running the commands from the source you provided no luck they gave me the same errors as the previous update manager. No idea where to go from here. there are two more screen shots that I couldnt upload let me know and I will get them to you 

V

---

### Post by westie457 on 2011-10-07
@ Vanity sorry to hear you are still having problems. As this is a clean install you have that has gone wrong after updating it probably will be quicker and easier to start again.

Boot your cd and go to install, at the where would you like to install screen select 'use the whole drive' if you get that option.
If not select 'something else' and in here select your current / root partition to use as EXT4 and mark the small box below to 'format'. Do the same for Home if you have a separate Home.
Carry on installing and finally reboot into your new system.

Additional Drivers should let you know there is a driver needed that is not installed, IGNORE IT. Because that driver will not work. By this time Update Manager should have started to let you know there are updates available. If it has not then start Update Manager but before checking for updates go to the 'Settings' - bottom left. In the 'Ubuntu Software' tab check mark the top four boxes and in the 'Other Software' tab just the top two boxes should be marked. Click 'Close' then 'Okay' to update the sources. DO NOT install the updates.

Instead open a terminal, type in and run ```
sudo apt-get install b43-fwcutter
``` followed by ```
sudo apt-get install firmware-b43-installer
``` the ones suggested by wildmanne39.
If there is any errors in the terminal instead of taking screen shots (limited to 5 per post) highlight and copy the output and paste between ```
 
``` tags by clicking the # at the top of the message window. This is so much easier to read as my eyes are struggling to focus on the text of the screen shots.
Remove the cable and restart your computer. Wireless should now be working. 

I am going on the theory of get it working first then updates might not break it.
If the wireless works go ahead and update. If not come back here and we will try some of the other drivers before allowing any updates to be installed.

@ wildmanne39 hope you do not mind me sticking my nose in. Definitely not trying to claim 'kudos' for your hard work.

---

### Post by wildmanne39 on 2011-10-07
Hi westie457, I like working with people,  you are welcome and appreciated anytime.
Thank you

---

### Post by westie457 on 2011-10-07
@ wildmanne39 always trying to help even when I get things wrong though not harming someone's pc deliberately to teach a lesson. Not in my nature. Anyway CONGRATS on your Membership, could not post on the application thread as it has been closed.

Hopefully we will cross paths again and have some good-natured banter.

@ Vanity The suggestion to format and clean install is just in case there was any cruft hanging on from all the upgrades you did that were affecting the configuration of ubuntuone.

---

### Post by wildmanne39 on 2011-10-07
Hi westie457, me too , there is so much to know that we can not possibly know it all and just when we think we have a device like this card figured out a new release of ubuntu comes out and we have to start all over again.

Thank you I appreciate the congratulations.

@Vanity post all the errors when you are try to update in the new thread you opened in code boxes so we can take the errors and copy them and paste so we can do a search and try to find the problem.

Please post a link to the thread here.

westie457 gave good advice if you would rather do it that way, some of these problems are hard to fix while others or easy.
Thank you

---

### Post by Vanity on 2011-10-08
okay so first thing I noticed is that in the other software tab under setting for update manager the pre-released box, and the unsupported box were check not the top two. I now have it like the screen shot shows.
```

vanity@Vanity:~$ sudo apt-get install b43-fwcutter
[sudo] password for vanity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 222 not upgraded.
Need to get 14.6 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ natty/main b43-fwcutter i386 1:013-3 [14.6 kB]
Fetched 14.6 kB in 0s (19.5 kB/s)       
Selecting previously deselected package b43-fwcutter.
(Reading database ... 130073 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...

```

```

vanity@Vanity:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 0 to remove and 222 not upgraded.
Need to get 3,632 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ natty/multiverse firmware-b43-installer all 4.150.10.5-5 [3,632 B]
Fetched 3,632 B in 0s (8,362 B/s)           
Selecting previously deselected package firmware-b43-installer.
(Reading database ... 130080 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
--2011-10-07 23:18:29--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Resolving mirror2.openwrt.org... 46.4.11.11
Connecting to mirror2.openwrt.org|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-bzip2]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2'

100%[======================================>] 3,888,794   1.04M/s   in 4.7s    

2011-10-07 23:18:35 (807 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw

```

---

### Post by Vanity on 2011-10-08
I unplugged and rebooted as you instructed when i was booted up wireless was still not working.

---

### Post by westie457 on 2011-10-08
Hi Vanity the output shows the installation of the bcmwl driver as well as the b43 drivers. Unfortunately they will not work together.

There is now two ways to go about this.

Option 1 is to remove bcmwl driver and reboot or 

Option 2 remove the two b43 files and reboot.

If the bcmwl driver was installed from the zip file wildmanne39 gave you, you might have move it from where it is to somewhere else so it does not run.


-------------------------------------------------------------------------
EDIT

If you go with option 2 you might as well install the bcmwl-modaliases package too. It might just work and will do no harm.

Option 3 will be to remove everything suggested so far and install the two Broadcom packages.
There is a screen shot attached to show you all of the correct bcm packages.

After trying all of the above and rebooting at the end of each option it should be working.

Keeping fingers crossed.

---

### Post by Vanity on 2011-10-08
Hi Westie457,

I am running the updates right now and will reboot when they are done in hopes that these updates after we have finally gotten the B43 drivers installed will work. This is something that wildmanne39 tried but never got them to actually install. 

as for the options, I have included a screenshot of what stybaptics packet manager shows installed for the BCM. it doesnt show anything for the bcmwl or (option 3) bcmwl-modaliases.

---

### Post by westie457 on 2011-10-08
When you set your sources list earlier did you put a check mark in the top four boxes in the 'UBUNTU SOFTWARE'tab, check please. Also as an extra idea in the 'UPDATES' tab put a mark against the Natty backports box.

Another thing is you are using the full search function, that is why you have a very long list to look through, try using the 'QUICK SEARCH' box. This will list no more than 12 items, a lot easier to look through. Another little tip here is to click on the left hand column of the package lists. It has a 'S' in it, clicking this brings all of the matching installed packages to the top of the list.

As you said hopefully the updates install without any major errors.

---

### Post by wildmanne39 on 2011-10-08
Hi, we never got the firmware to install so it will probably be a matter of blacklisting the other driver to get it to work.

Please post the results of:
```
lsmod
```
```
dmesg | egrep 'b43|firm|bcmwl|wlan0'
```
The zip file I gave him just contained the b43 firmware.
Thank you

---

### Post by Vanity on 2011-10-08
```

vanity@Vanity:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
arc4                   12473  2 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
b43legacy             127415  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
radeon                900494  3 
mac80211              257001  1 b43legacy
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 radeon
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 b43legacy,mac80211
drm_kms_helper         40745  1 radeon
joydev                 17322  0 
soundcore              12600  1 snd
drm                   184164  5 radeon,ttm,drm_kms_helper
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
pcmcia                 39671  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
i2c_algo_bit           13184  1 radeon
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
video                  18951  0 
serio_raw              12990  0 
ppdev                  12849  0 
shpchp                 32345  0 
parport_pc             32111  1 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
ssb                    45942  1 b43legacy
e1000                 101089  0 
floppy                 60032  0 
crc_itu_t              12627  1 firewire_core

[CODE]
vanity@Vanity:~$ dmesg | egrep 'b43|firm|bcmwl|wlan0'
[    1.357353] b43-pci-bridge 0000:03:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.347870] b43legacy-phy0: Broadcom 4306 WLAN found
[   16.368056] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   16.368078] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   16.392034] b43legacy-phy0 debug: Radio initialized
[   17.176478] b43legacy-phy0 debug: Ignoring unconnected 802.11 core
[   22.319184] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   22.319196] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[   70.794712] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   70.794722] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).


```
[/CODE]

the updates did not get the wireless to work however there is some good news the update manager was successful in installing all updates.

---

### Post by wildmanne39 on 2011-10-08
Hi, please let us see the results of:
```
ls /lib/firmware | grep b43
```
```
ls -al /lib/firmware/b43
```
```
dmesg | grep firmware | tail -n20
```
Thank you

---

### Post by Vanity on 2011-10-08
```

vanity@Vanity:~$ ls /lib/firmware | grep b43
b43

```

```

vanity@Vanity:~$ ls -al /lib/firmware/b43
ls: cannot open directory /lib/firmware/b43: Permission denied

```

```

vanity@Vanity:~$ dmesg | grep firmware | tail -n20
[   22.319196] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[   70.794722] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  911.029634] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).

```

---

### Post by wildmanne39 on 2011-10-08
Hi, open synaptic and remove firmware-b43-installer then restart your computer and install:
```
firmware-b43legacy-installer
```
Then unplug wired connection and restart.
Thank you

---

### Post by Vanity on 2011-10-09
i unistalled the b43 installer as you said and restarted then went to install the b43 legacy installer and terminal kicked out command not found

---

### Post by wildmanne39 on 2011-10-09
Hi, I thought you would install it in synaptic that is why I only gave the package name and not the install command, but no problem.
```
sudo apt-get install firmware-b43legacy-installer
```
Thank you

---

### Post by Vanity on 2011-10-09
vanity@Vanity:~$ sudo apt-get install firmware-b43legacy-installer
[sudo] password for vanity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  firmware-b43legacy-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,478 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty/multiverse firmware-b43legacy-installer all 4.178.10.4-5 [3,478 B]
Fetched 3,478 B in 0s (8,917 B/s)                       
Selecting previously deselected package firmware-b43legacy-installer.
(Reading database ... 157730 files and directories currently installed.)
Unpacking firmware-b43legacy-installer (from .../firmware-b43legacy-installer_4.178.10.4-5_all.deb) ...
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:4324)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)


this was the output from command followed by a window stating that the b43 installer failed with an error it asked me to report the problem and I did 

V

---

### Post by wildmanne39 on 2011-10-09
Hi, I just wanted to confirm the information, that is what I thought would happen.

Give me a few minutes to do some more research.
Thank you

---

### Post by wildmanne39 on 2011-10-09
Hi, we are still having trouble with the firmware, we are going to try what we tried last time but I think there is better directions at this link.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

First open synaptic and remove b43cutter and firmware installer then restart your computer.

Then go to the link and go to the section where is says installing with no internet connection that will have the driver and install directions, you do not have to worry about using a flash drive or cd since you have an internet connection.

Download the firmware and follow the directions and it should work.
Thank you

---

### Post by Vanity on 2011-10-12
Hello,

so it took me a few days to be able to sit down and follow these steps (work) but I finally got to it and it seems that we already did these steps. Anyways I did them following the instructions exactly. and I got the same results when I input
```

tar -xzf b43-all-fw.tar_.gz

```this was my output from terminal. 

vanity@Vanity:~$ tar -xzf b43-all-fw.tar_.gz
tar (child): b43-all-fw.tar_.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now


attached is a screenshot of what synaptic shows, it appears that the drivers were in fact installed but I still have no wireless.

---

### Post by westie457 on 2011-10-12
Hi somewhere between wildmanne39's instructions and mine we have worked out that the b43 drivers are not working for you. the only ones left are the STA drivers.

Open synaptic and remove only the firmware-b43-installer - leaving fwcutter in will not hurt anything. Install the two Broadcom-STA packages. 

Unplug the cable and reboot. Keeping everything crossed your wireless should now find some networks to connect to.

This had better work as I am rapidly running out if options for you to try.

---

### Post by wildmanne39 on 2011-10-12
Hi, the problem it looks like according to the dmesg is that it wants a different firmware but everything we try to do to install it fails.

I was also thinking about trying the sta driver it can not hurt.

Have a look at this link westie457.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by westie457 on 2011-10-12
Hi have accidentally found by pure chance another thread concerning another Broadcom chip -b4311- with a different solution to the one used in my laptop.
The thread is this one, [http://ubuntuforums.org/showthread.php?p=11334219#post11334219](http://ubuntuforums.org/showthread.php?p=11334219#post11334219)
and possibly the solution was posted by josephmills.

```
sudo apt-get --purge remove bcmwl-kernel-source && sudo apt-get remove broadcom-sta-source  && sudo apt-get remove broadcom-sta-common && sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer && sudo apt-get install bcmwl-kernel-source && sleep 15 && sudo reboot
```
I realise we are dealing with a b4309 chip and treating it as a b4306 however it is refusing to work. It will not hurt to try this and if it works HURRAH.

---

### Post by Vanity on 2011-10-12
so which should I attempt first?

should I try the code last suggested by Westie457 treating it as a B4306?

---

### Post by wildmanne39 on 2011-10-12
Hi, I am sorry for the late reply I have been at the doctor most of the day and having lab work done.

I am going to ask a friend to take a look that is much more experienced then I am.
Thank you

---

### Post by praseodym on 2011-10-12
Hi friends,

take this firmware package attached and extract the 2 folders directly into /lib/firmware. The firmware for b43legacy is inside, too. You may want to uninstall the other packages first:

```
sudo apt-get remove --purge b43-fwcutter firmware-b43*
```
Save the firmware-tarball in /home and unpack it via terminal:

```
sudo tar xvf ~/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot and check:

```
iwconfig
dmesg | grep b43
rfkill list
sudo iwlist scan
lsmod
```

---

### Post by wildmanne39 on 2011-10-12
Hi praseodym, is that firmware different from the 2 other versions we have tried?

That is why I asked you to help you always have the coolest packages to install, and the 2 I have tried have failed badly.

This is the only time the b43zip has not worked for me.
Thank you for coming to help us my friend it is greatly appreciated.

---

### Post by Vanity on 2011-10-13
okay so please remember I am a complete newbie to ubunu and its filing system how do I get into lib/firmware more less how can I get the two abstracted files there?

Thank you guys for all your help and you patience as this is all a learning experience for me 

V-

---

### Post by praseodym on 2011-10-13
Hi, I just wanted to start "from the beginning". The device BCM430[COLOR="Red"]9[/COLOR] with the ID 14e4:4324 is not listed [here]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices") (or [here]("http://wiki.ubuntuusers.de/wlan/karten/Broadcom")), and i have never seen it before. The device ID needs the b43legacy incl. the firmware.

---

### Post by praseodym on 2011-10-13
> how do I get into lib/firmware more less how can I get the two abstracted files there?

See the explanation above. The "sudo tar"-command line extracts the tarball file.

---

### Post by Vanity on 2011-10-13
this is after i uninstall the b43 legacy installer correct?

---

### Post by Vanity on 2011-10-13
after uninstalling the b43 legacy installer I downloaded the zip file you told me to and ran the commands you gave me this was my output.

```

vanity@Vanity:~$ sudo apt-get remove --purge b43-fwcutter firmware-b43*
[sudo] password for vanity: 
[B]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]
vanity@Vanity:~$ sudo apt-get remove --purge b43-fwcutter firmware-b43*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'firmware-b43-installer' for regex 'firmware-b43*'
Note, selecting 'firmware-b43-lpphy-installer' for regex 'firmware-b43*'
Note, selecting 'firmware-b43legacy-installer' for regex 'firmware-b43*'
Package firmware-b43-lpphy-installer is not installed, so not removed
Package firmware-b43legacy-installer is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  b43-fwcutter* firmware-b43-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 81.9 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157729 files and directories currently installed.)
Removing b43-fwcutter ...
Removing firmware-b43-installer ...
Purging configuration files for firmware-b43-installer ...
Processing triggers for man-db ...
vanity@Vanity:~$ sudo tar xvf ~/Broadcom_Firmware.tar.gz -C /lib/firmware/
tar: /home/vanity/Broadcom_Firmware.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
vanity@Vanity:~$ sudo tar xvf ~/Broadcom_Firmware.tar.gz -C /lib/firmware/
tar: /home/vanity/Broadcom_Firmware.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


```

the error at the top was because I forgot to close synaptic"

---

### Post by praseodym on 2011-10-13
Did you save the attached file in /home?

---

### Post by Vanity on 2011-10-13
okay so after I made sure to save that folder in my home folder and I ran the commands I unplugged and reboot and wireless was not working at first so I clicked on the network connections icon and selected create a new wireless connection and so I just put in my information to my current wireless network and all of a sudden all of the LAN's showed up and it is allowing me to be wireless. I then selected my network and input my password and here I am but I want to run those commands that you said to double check. 

```

vanity@Vanity:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"VANITY"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: E0:46:9A:40:E7:B3   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:24   Missed beacon:0

```

```

 dmesg | grep b43
[    1.523810] b43-pci-bridge 0000:03:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   20.058654] b43legacy-phy0: Broadcom 4306 WLAN found
[   20.090407] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   20.090437] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   20.116892] b43legacy-phy0 debug: Radio initialized
[   20.187755] b43legacy-phy0 debug: Ignoring unconnected 802.11 core
[   20.976115] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   21.040656] b43legacy-phy0 debug: Chip initialized
[   21.040897] b43legacy-phy0 debug: 30-bit DMA initialized
[   21.041169] Registered led device: b43legacy-phy0::tx
[   21.041229] Registered led device: b43legacy-phy0::rx
[   21.041284] Registered led device: b43legacy-phy0::radio
[   21.041334] b43legacy-phy0 debug: Wireless interface started
[   21.041353] b43legacy-phy0 debug: Adding Interface type 2
[   21.049946] b43legacy-phy0: Radio hardware status changed to DISABLED
[   21.049956] b43legacy-phy0 debug: Radio initialized
[   21.088061] b43legacy-phy0 debug: Removing Interface type 2
[   21.096312] b43legacy-phy0 debug: Wireless interface stopped
[   21.096799] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   21.096860] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   21.097027] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   21.104059] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   21.112089] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   21.120040] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   21.128036] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   21.136035] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   21.144039] b43legacy-phy0 debug: Radio initialized
[   21.144053] b43legacy-phy0 debug: Radio initialized
[   60.832051] b43legacy-phy0: Radio hardware status changed to ENABLED
[   61.232041] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   61.264546] b43legacy-phy0 debug: Chip initialized
[   61.264780] b43legacy-phy0 debug: 30-bit DMA initialized
[   61.265047] Registered led device: b43legacy-phy0::tx
[   61.265100] Registered led device: b43legacy-phy0::rx
[   61.265173] Registered led device: b43legacy-phy0::radio
[   61.265226] b43legacy-phy0 debug: Wireless interface started
[   61.272331] b43legacy-phy0 debug: Adding Interface type 2
[   61.300107] b43legacy-phy0 debug: Removing Interface type 2
[   61.300149] b43legacy-phy0 debug: Wireless interface stopped
[   61.300440] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   61.300517] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   61.300593] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   61.308071] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   61.316063] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   61.324047] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   61.332046] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   61.340047] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   61.348047] b43legacy-phy0 debug: Radio initialized
[   61.348060] b43legacy-phy0 debug: Radio initialized
[   61.712031] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   61.776549] b43legacy-phy0 debug: Chip initialized
[   61.776783] b43legacy-phy0 debug: 30-bit DMA initialized
[   61.777046] Registered led device: b43legacy-phy0::tx
[   61.777102] Registered led device: b43legacy-phy0::rx
[   61.777166] Registered led device: b43legacy-phy0::radio
[   61.777214] b43legacy-phy0 debug: Wireless interface started
[   61.784327] b43legacy-phy0 debug: Adding Interface type 2
[   63.428067] b43legacy-phy0 ERROR: MAC suspend failed
[  100.316051] b43legacy-phy0 debug: Removing Interface type 2
[  100.324027] b43legacy-phy0 debug: Wireless interface stopped
[  100.324325] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[  100.324394] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[  100.324477] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  100.332044] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  100.340089] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  100.348077] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  100.356083] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 4/128
[  100.364086] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  100.372076] b43legacy-phy0 debug: Radio initialized
[  100.372093] b43legacy-phy0 debug: Radio initialized
[  100.748055] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  100.812611] b43legacy-phy0 debug: Chip initialized
[  100.812843] b43legacy-phy0 debug: 30-bit DMA initialized
[  100.813110] Registered led device: b43legacy-phy0::tx
[  100.813173] Registered led device: b43legacy-phy0::rx
[  100.813248] Registered led device: b43legacy-phy0::radio
[  100.813306] b43legacy-phy0 debug: Wireless interface started
[  100.813318] b43legacy-phy0 debug: Adding Interface type 1
[  108.164016] b43legacy-phy0 ERROR: MAC suspend failed
[  108.164027] b43legacy-phy0 debug: Set beacon interval to 100
[  171.439045] b43legacy-phy0 debug: Removing Interface type 1
[  171.448160] b43legacy-phy0 debug: Wireless interface stopped
[  171.448457] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[  171.448528] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 2/64
[  171.448611] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  171.456062] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  171.464152] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  171.472178] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  171.483568] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 4/128
[  171.488070] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  171.496049] b43legacy-phy0 debug: Radio initialized
[  171.496062] b43legacy-phy0 debug: Radio initialized
[  171.868032] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  171.932576] b43legacy-phy0 debug: Chip initialized
[  171.932809] b43legacy-phy0 debug: 30-bit DMA initialized
[  171.933068] Registered led device: b43legacy-phy0::tx
[  171.933129] Registered led device: b43legacy-phy0::rx
[  171.933200] Registered led device: b43legacy-phy0::radio
[  171.933253] b43legacy-phy0 debug: Wireless interface started
[  171.933266] b43legacy-phy0 debug: Adding Interface type 2
[  172.252044] b43legacy-phy0 ERROR: MAC suspend failed
[  172.600029] b43legacy-phy0 ERROR: MAC suspend failed
[  172.956015] b43legacy-phy0 ERROR: MAC suspend failed
[  332.745988] b43legacy-phy0 ERROR: PHY transmission error
[  332.746013] b43legacy-phy0 ERROR: PHY transmission error
[  336.499125] b43legacy-phy0 ERROR: PHY transmission error
[  517.539786] b43legacy-phy0 ERROR: PHY transmission error
[  576.741386] b43legacy-phy0 ERROR: PHY transmission error
[  577.104838] b43legacy-phy0 ERROR: PHY transmission error

```

```

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

sudo iwlist scan
[sudo] password for vanity: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E0:46:9A:40:E7:B3
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"VANITY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000029e9abf02d
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000656414E495459
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD820050F204104A0001101044000102103B0001031047001000000000000010000000E0469A40E7B31021000D4E6574676561722C20496E632E10230007574E44524D41431024000456314831104200046E6F6E651054000800060050F204000110110014574E44524D414328576972656C65737320415029100800020086103C000103
          Cell 02 - Address: 00:1C:DF:72:C1:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Bridge_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b2e530e183
                    Extra: Last beacon: 952ms ago
                    IE: Unknown: 000E4272696467655F4E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD001CDF72C17C1021000642656C6B696E1023000F463544373233312D342D763330303010240007575053303030311042000E32303734393732333131313231391054000800060050F204000110110020463544373233312D340000000000000000000000000000000000000000000000100800020084
                    IE: Unknown: DD09001018020013000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

```

 lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52200  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13562  1 nf_nat_pptp
nf_conntrack_proto_gre    13353  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16922  0 
nf_conntrack_sip       24652  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_conntrack_ftp       13106  1 nf_nat_ftp
iptable_nat            12977  0 
nf_nat                 24827  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18125  2 iptable_filter,iptable_nat
x_tables               21907  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
radeon                900494  3 
snd_seq_midi           13132  0 
arc4                   12473  2 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
b43legacy             127415  0 
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  1 b43legacy
ppdev                  12849  0 
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 b43legacy,mac80211
yenta_socket           27230  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 radeon
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
shpchp                 32345  0 
video                  18951  0 
parport_pc             32111  1 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
ssb                    45942  1 b43legacy
e1000                 101089  0 
floppy                 60032  0 
crc_itu_t              12627  1 firewire_core

```

PROBLEM SOLVED EH.... I have been wireless this entire time. I want to thank you guys all for the help I truly learned alot by having to work this issue out. Ubuntu has a great community. Thank you all again. 

VANITY

---

### Post by praseodym on 2011-10-13
You are welcome.

Those disconnects in dmesg can be originated from the ip-tables (firewall) used. Did you configure one? Do you need one?

If not:

Read them out with:

```
sudo iptables -t filter -n -L -v
```

If you dont want to use it, remove:

```
sudo iptables -F
sudo iptables -X
```
In Ubuntu all ports are closed by default (in complete opposite to Windows), so only ports _you_ are opening (SSH, whatever) are open.

---

### Post by westie457 on 2011-10-13
@ praseodym thank you for helping. One question though. What was the thing that wildmanne39 and myself missed? just in case this '4309' chip ever shows itself again.

---

### Post by praseodym on 2011-10-13
> **westie457 said:**
> @ praseodym thank you for helping. One question though. What was the thing that wildmanne39 and myself missed? just in case this '4309' chip ever shows itself again.

It was the missing firmware for b43legacy (not b43)

---

### Post by sadaruwan12 on 2011-10-13
OK sorry to jump in but now this is done and solved can the owner please mark this as solved

:-)

---

### Post by wildmanne39 on 2011-10-13
Hi, I tried both firmwares and they would not install originally.

So I gave him the b43zip file and it has the legacy and the b43 but it would not install kept getting errors, then the tar file I gave him kept getting errors trying to install. 

I think you gave him a different tar file then the one I had I think mine was older.

Thank you praseodym I am glad I asked for your help you are the networking warrior.

Vanity what do you mean by
> I have been wireless this entire time.

It was good working with you westie457.
Thank you

---

### Post by Vanity on 2011-10-13
my apologies for not being clear. I was pretty stoked this morning when we had finally gotten it working I meant I have been wireless this entire time as I in since I started writing that perticular response. 

I could imagine the frustrations you might have felt but by no means did I intend for you to think that. My wireless is working now and only now it was never working before. again it was awesome working with you guys and I truly learned alot thank you so much again. 

V-

---

### Post by wildmanne39 on 2011-10-13
Hi, your welcome! and enjoy.

---

