---
title: "Can't Install wireless driver"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by SupermanNC21 on 2012-08-15
Hello i'm new to Ubuntu i'm kinda ok with computer but i can't for the life of me figure out how to install Ndiswrapper or Sypantic i have the .deb file for both an the tar.gz file for Ndiswrapper but Ubuntu only wants to break them down like a zip file then it brings up the text or it wants to open with Software center an it wanted let me install it there. I did want the install file said my Kenrel atlest has inclued and I CANT use internet my Wireless card is out an my Internet port want connect for some reason my router is flashed with DD-wrt i dont think that would affect the ethernet an my wifi card won't turn on at all i have the window 7 .sys driver for my wifi card an the .inf driver for my ethernet I don't have Ubuntu CD i download Windows install for it from main page I have Ubuntu 12.04 LTS please help i been trying to figure this out for weeks now an im about to give up.

---

### Post by nothingspecial on 2012-08-15
Prefix changed from lubuntu to ubuntu.

---

### Post by SupermanNC21 on 2012-08-15
Also I have a Gateway M675PRR with windows 7 Ulitmate 32-bit duel booded with Ubuntu 2GB ram it has build in wifi card the wifi won't turn on pressed button 100 times lol ethernet lights up but doesn't connect Video card and usb driver out but i can worry about that later after i fix my internet issue all other driver seem to work mouse an keyboard and scoll tap an cd driver are ok

---

### Post by SupermanNC21 on 2012-08-16
Ok so i been playing around with it more trying to figure out how it install this Ndiswrapper program but still no success made some lead way with it when i tried 
"Sudo dpkg -i" 
but when i tried to finish it said "process to man.deb" an then it stop there.
tried same scipt with synapic but i had some dependency issues.
Also when my ubuntu starts up right before it boots it says "Prefix is not set" seacrh around about that i did "chkdsk" and ran "advance system care" over it but it didnt fix anything well anywho hope u guys can help me with these problem i'm go try an do some more researching.
 
also it does bring up my ubuntu even with it saying prefix is not set
 
 
 
 
Eventually I will have Ubuntu Online.......

---

### Post by wildmanne39 on 2012-08-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by SupermanNC21 on 2012-08-16
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-08-16 20:06:53-- [_[COLOR=#0000ff]http://dl.dropbox.com/u/57264241/wireless_script_[/COLOR]]("http://dl.dropbox.com/u/57264241/wireless_script")
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Name or service not known.
wget: unable to resolve host address `dl.dropbox.com'

---

### Post by SupermanNC21 on 2012-08-16
also info about Wifi and ethernet cards
 
```
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: agpgart-intel 
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P AGP Bridge [8086:2571] (rev 02) 
Kernel modules: shpchp 
00:03.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to CSA Bridge [8086:2573] (rev 02) 
Kernel modules: shpchp 
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02) 
00:1d.0 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.1 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.2 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.3 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.7 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: ehci_hcd 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) 
Kernel modules: shpchp 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02) 
Kernel modules: iTCO_wdt, intel-rng 
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: ata_piix 
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel modules: i2c-i801 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: snd_intel8x0 
Kernel modules: snd-intel8x0 
00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller [8086:24d6] (rev 02) 
Subsystem: AMBIT Microsystem Corp. Device [1468:0601] 
Kernel modules: snd-intel8x0m 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV350 [Mobility Radeon 9600 M10] [1002:4e50] 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: radeon 
Kernel modules: radeon, radeonfb 
02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019] 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: e1000 
Kernel modules: e1000 
03:01.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: yenta_cardbus 
Kernel modules: yenta_socket 
03:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029] 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: firewire_ohci 
Kernel modules: firewire-ohci 
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) 
Subsystem: Broadcom Corporation Device [14e4:0418] 
Kernel driver in use: b43-pci-bridge 
Kernel modules: ssb 
superman@ubuntu:~$ 
superman@ubuntu:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
superman@ubuntu:~$ 
superman@ubuntu:~$ iwconfig 
lo no wireless extensions. 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]wlan0 IEEE 802.11bg ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off 
Power Management:on 

eth0 no wireless extensions. 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ 
superman@ubuntu:~$ lsmod 
Module Size Used by 
nls_utf8 12493 1 
isofs 39553 1 
rfcomm 38139 0 
parport_pc 32114 1 
ppdev 12849 0 
bnep 17830 2 
bluetooth 158438 10 rfcomm,bnep 
lp 17455 0 
parport 40930 3 parport_pc,ppdev,lp 
joydev 17393 0 
arc4 12473 2 
b43 342643 0 
mac80211 436455 1 b43 
snd_intel8x0 33455 2 
snd_ac97_codec 106082 1 snd_intel8x0 
ac97_bus 12642 1 snd_ac97_codec 
snd_pcm 80845 2 snd_intel8x0,snd_ac97_codec 
snd_seq_midi 13132 0 
snd_rawmidi 25424 1 snd_seq_midi 
cfg80211 178679 2 b43,mac80211 
snd_seq_midi_event 14475 1 snd_seq_midi 
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event 
mac_hid 13077 0 
bcma 25651 1 b43 
pcmcia 39791 0 
snd_timer 28931 2 snd_pcm,snd_seq 
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq 
yenta_socket 27465 0 
pcmcia_rsrc 18367 1 yenta_socket 
psmouse 72846 0 
snd 62064 11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
serio_raw 13027 0 
pcmcia_core 21511 3 pcmcia,yenta_socket,pcmcia_rsrc 
soundcore 14635 1 snd 
snd_page_alloc 14108 2 snd_intel8x0,snd_pcm 
shpchp 32325 0 
radeon 733693 2 
firewire_ohci 40172 0 
firewire_core 56906 1 firewire_ohci 
crc_itu_t 12627 1 firewire_core 
ssb 50691 1 b43 
ttm 65344 1 radeon 
drm_kms_helper 45466 1 radeon 
drm 197692 4 radeon,ttm,drm_kms_helper 
e1000 101693 0 
i2c_algo_bit 13199 1 radeon 
superman@ubuntu:~$ 
superman@ubuntu:~$ rfkill list 
0: phy0: Wireless LAN 
Soft blocked: no 
Hard blocked: no
```

---

### Post by wildmanne39 on 2012-08-16
Hi, I just copied and pasted that command in my terminal and it worked perfect, please try again, you do need an internet connection of course.

Did you paste the command into the terminal?
Thanks

---

### Post by anewguy on 2012-08-16
It's the Broadcom 4306.  What I would try while waiting for wildmanne39 to get back to you:

- connect your PC to the router via hard-wire, if possible

- go to "additional drivers" and see if it finds a driver for you and/or has one but you need to enable it

- I wouldn't mess with ndiswrapper at this point.  I used to recommend it, and had written a couple of how-to's for it, but with the changes in the last few releases of Ubuntu, you really shouldn't need it. 

Normally now the driver can be found via additional drivers, or by loading in a couple of packages or blacklisting a module and loading a different one.

Wildmanne39 is an expert at this, so I'd wait for him to get back to you.

OOOPPPPSS -  you're back before I got my post in!  Sorry!  Dave ;)

---

### Post by SupermanNC21 on 2012-08-16
yes i copied an pasted it an thats what i put out

---

### Post by wildmanne39 on 2012-08-16
Hi,
 Download the zipped wireless script file then:
 Open a terminal using ctrl+alt+t then copy and paste each command online at a time.
```
cd ~/Downloads
chmod +x wireless_script
./wireless_script
```
then reply back,  and attach the netinfo.txt file it will be located in your downloads file.

The script removes the MAC Address, WPA and WEP key for security.
Thanks

---

### Post by wildmanne39 on 2012-08-16
Hi, the script would not attach until I changed the name of the file.

So please run it like this.

Download the zipped wireless script file then:
 Open a terminal using ctrl+alt+t then copy and paste each command online at a time.
```
cd ~/Downloads
chmod +x netscript.sh
./netscript.sh
```
 then reply back,  and attach the netinfo.txt file it will be located in your downloads folder.
The script removes the MAC Address, WPA and WEP key for security.
Thanks

---

### Post by SupermanNC21 on 2012-08-16
Ok the cd script didn't work again but i copy and pasted the .sh file script an here's it finding>>
superman@ubuntu:~$ echo -e "\n\n**** uname -a ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** uname -a ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]```
superman@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
superman@ubuntu:~$ echo -e "\n\n**** lsb-release ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** lsb-release ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
superman@ubuntu:~$ echo -e "\n\n**** lspci ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** lspci ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019]
Subsystem: Gateway 2000 Device [107b:0603]
Kernel driver in use: e1000
--
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
Subsystem: Broadcom Corporation Device [14e4:0418]
Kernel driver in use: b43-pci-bridge
superman@ubuntu:~$ echo -e "\n\n**** lsusb ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** lsusb ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
superman@ubuntu:~$ echo -e "\n\n**** iwconfig ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** iwconfig ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ iwconfig
lo no wireless extensions.
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]wlan0 IEEE 802.11bg ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on

eth0 no wireless extensions.
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ echo -e "\n\n**** rfkill ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** rfkill ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
superman@ubuntu:~$ echo -e "\n\n**** lsmod ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** lsmod ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ lsmod
Module Size Used by
nls_utf8 12493 1 
isofs 39553 1 
rfcomm 38139 0 
bnep 17830 2 
bluetooth 158438 10 rfcomm,bnep
parport_pc 32114 1 
ppdev 12849 0 
lp 17455 0 
parport 40930 3 parport_pc,ppdev,lp
joydev 17393 0 
snd_intel8x0 33455 2 
snd_ac97_codec 106082 1 snd_intel8x0
ac97_bus 12642 1 snd_ac97_codec
snd_pcm 80845 2 snd_intel8x0,snd_ac97_codec
snd_seq_midi 13132 0 
snd_rawmidi 25424 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
arc4 12473 2 
snd_timer 28931 2 snd_pcm,snd_seq
b43 342643 0 
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211 436455 1 b43
radeon 733693 2 
pcmcia 39791 0 
snd 62064 11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm 65344 1 radeon
mac_hid 13077 0 
psmouse 72846 0 
cfg80211 178679 2 b43,mac80211
serio_raw 13027 0 
drm_kms_helper 45466 1 radeon
yenta_socket 27465 0 
pcmcia_rsrc 18367 1 yenta_socket
drm 197692 4 radeon,ttm,drm_kms_helper
soundcore 14635 1 snd
pcmcia_core 21511 3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc 14108 2 snd_intel8x0,snd_pcm
bcma 25651 1 b43
i2c_algo_bit 13199 1 radeon
shpchp 32325 0 
ssb 50691 1 b43
firewire_ohci 40172 0 
firewire_core 56906 1 firewire_ohci
crc_itu_t 12627 1 firewire_core
e1000 101693 0 
superman@ubuntu:~$ echo -e "\n\n**** nm-tool ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** nm-tool ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ nm-tool
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]NetworkManager Tool
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]State: disconnected
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: b43
State: unavailable
Default: no
HW Address: 00:**:**:**:**:**
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Capabilities:
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Wireless Access Points 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: e1000
State: unavailable
Default: no
HW Address: 00:**:**:**:**:**
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Capabilities:
Carrier Detect: yes
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Wired Properties
Carrier: off
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ echo -e "\n\n**** NetworkManager.state ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** NetworkManager.state ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ cat /var/lib/NetworkManager/NetworkManager.state
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT][main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
superman@ubuntu:~$ echo -e "\n\n**** NetworkManager.conf ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** NetworkManager.conf ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ cat /etc/NetworkManager/NetworkManager.conf
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT][main]
plugins=ifupdown,keyfile
dns=dnsmasq
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]no-auto-default=00:**:**:**:**:**,
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT][ifupdown]
managed=false
superman@ubuntu:~$ echo -e "\n\n**** interfaces ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** interfaces ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
superman@ubuntu:~$ echo -e "\n\n**** iwlist ****\n\n"
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]**** iwlist ****
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]superman@ubuntu:~$ [ -t 0 ] && sudo iwlist scan
[sudo] password for superman: 
Sorry, try again.
[sudo] password for superman: 
lo Interface doesn't support scanning.
```
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]wlan0 Interface doesn't support scanning : Network is down
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]eth0 Interface doesn't support scanning.

---

### Post by wildmanne39 on 2012-08-16
Hi, please do:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot

You must not have been in the same directory as the script.
Thanks

---

### Post by SupermanNC21 on 2012-08-16
Bad News
 
superman@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for superman: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
ndisgtk : Depends: python-glade2 but it is not going to be installed
synaptic : Depends: libapt-inst-libc6.7-6-1.1 but it is not installable
Depends: libapt-pkg-libc6.7-6-4.6 but it is not installable
Depends: libglade2-0 (>= 1:2.6.1) but it is not going to be installed
Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not going to be installed
Depends: libvte9 (>= 1:0.16.9) but it is not going to be installed
Depends: scrollkeeper
Recommends: deborphan but it is not going to be installed
Recommends: libgnome2-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by wildmanne39 on 2012-08-16
Hi, that is a separate issue so let's try to get around it, then you can start a new thread for it.

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do: 
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by SupermanNC21 on 2012-08-16
Ok I so tried the B43 files i add it to desktop then I went into terminal but when I used 
"sudo mv b43/* /lib/firmware" 
it said mv couldnt find b43 then i tried to give it the exact location an it still could not find it. i put in
 "sudo rmmod -f b43"   "sudo rmmod -f ssb"  "sudo modprobe b43"
they worked my connection icon came up but said disconnected i tired pushing wifi button but it didnt light up or do anything.
 
 
 
 
 
 
Eventually i will have Internet on Ubuntu.....

---

### Post by SupermanNC21 on 2012-08-16
Here's all of my hardware info 
 
```
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: agpgart-intel 
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P AGP Bridge [8086:2571] (rev 02) 
Kernel modules: shpchp 
00:03.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to CSA Bridge [8086:2573] (rev 02) 
Kernel modules: shpchp 
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02) 
00:1d.0 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.1 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.2 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.3 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: uhci_hcd 
00:1d.7 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: ehci_hcd 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) 
Kernel modules: shpchp 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02) 
Kernel modules: iTCO_wdt, intel-rng 
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: ata_piix 
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel modules: i2c-i801 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: snd_intel8x0 
Kernel modules: snd-intel8x0 
00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller [8086:24d6] (rev 02) 
Subsystem: AMBIT Microsystem Corp. Device [1468:0601] 
Kernel modules: snd-intel8x0m 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV350 [Mobility Radeon 9600 M10] [1002:4e50] 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: radeon 
Kernel modules: radeon, radeonfb 
02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019] 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: e1000 
Kernel modules: e1000 
03:01.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02) 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: yenta_cardbus 
Kernel modules: yenta_socket 
03:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029] 
Subsystem: Gateway 2000 Device [107b:0603] 
Kernel driver in use: firewire_ohci 
Kernel modules: firewire-ohci 
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) 
Subsystem: Broadcom Corporation Device [14e4:0418] 
Kernel driver in use: b43-pci-bridge 
Kernel modules: ssb 
superman@ubuntu:~$ 
superman@ubuntu:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
superman@ubuntu:~$ 
superman@ubuntu:~$ iwconfig 
lo no wireless extensions. 
wlan0 IEEE 802.11bg ESSID:eek:ff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thr:eek:ff Fragment thr:eek:ff 
Power Management:eek:n 

eth0 no wireless extensions. 
superman@ubuntu:~$ 
superman@ubuntu:~$ lsmod 
Module Size Used by 
nls_utf8 12493 1 
isofs 39553 1 
rfcomm 38139 0 
parport_pc 32114 1 
ppdev 12849 0 
bnep 17830 2 
bluetooth 158438 10 rfcomm,bnep 
lp 17455 0 
parport 40930 3 parport_pc,ppdev,lp 
joydev 17393 0 
arc4 12473 2 
b43 342643 0 
mac80211 436455 1 b43 
snd_intel8x0 33455 2 
snd_ac97_codec 106082 1 snd_intel8x0 
ac97_bus 12642 1 snd_ac97_codec 
snd_pcm 80845 2 snd_intel8x0,snd_ac97_codec 
snd_seq_midi 13132 0 
snd_rawmidi 25424 1 snd_seq_midi 
cfg80211 178679 2 b43,mac80211 
snd_seq_midi_event 14475 1 snd_seq_midi 
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event 
mac_hid 13077 0 
bcma 25651 1 b43 
pcmcia 39791 0 
snd_timer 28931 2 snd_pcm,snd_seq 
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq 
yenta_socket 27465 0 
pcmcia_rsrc 18367 1 yenta_socket 
psmouse 72846 0 
snd 62064 11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,sn d_seq,snd_timer,snd_seq_device 
serio_raw 13027 0 
pcmcia_core 21511 3 pcmcia,yenta_socket,pcmcia_rsrc 
soundcore 14635 1 snd 
snd_page_alloc 14108 2 snd_intel8x0,snd_pcm 
shpchp 32325 0 
radeon 733693 2 
firewire_ohci 40172 0 
firewire_core 56906 1 firewire_ohci 
crc_itu_t 12627 1 firewire_core 
ssb 50691 1 b43 
ttm 65344 1 radeon 
drm_kms_helper 45466 1 radeon 
drm 197692 4 radeon,ttm,drm_kms_helper 
e1000 101693 0 
i2c_algo_bit 13199 1 radeon 
superman@ubuntu:~$ 
superman@ubuntu:~$ rfkill list 
0: phy0: Wireless LAN 
Soft blocked: no 
Hard blocked: no
```

---

### Post by unevenflow on 2012-08-16
Hey,
you shouldn't have changed thread because nobody can folloe your progress and help you but its ok i found you
right click the b43.zip file and choose move to home  extract it then again in terminal
> sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43 
as Wild Man suggested

---

### Post by wildmanne39 on 2012-08-16
Threads merged. Please do not post duplicates, it dilutes community effort.

---

### Post by SupermanNC21 on 2012-08-17
Sorry thought i was suppose to make new thread from that one post u add but anywho i did what you said extracted the zip file to desktop and ran scipts in therminal then the icon for wireless came up(the one with the bars to show signal strenght) then it said disconnected i open the extracted file an there was nothing in there so i deleted it and did process again an same thing happen all files where gone but the wireless wasnt working i tried reboot to see if that would help it turn on an it didn't.

---

### Post by wildmanne39 on 2012-08-17
Hi, I thought you probably miss understood what I had said so no problem.

Once the light comes on do not do anything to make it go out, the light has to be on before we can go any further.

I added a little more instructions.

Download the zipped wireless script file to your download folder then: Open a terminal using ctrl+alt+t then copy and paste each command online at a time.
```
cd ~/Downloads
chmod +x netscript.sh
./netscript.sh
```
then reply back, and attach the netinfo.txt file by clicking on the paper clip in the reply window, the netinfo.txt file will be located in your downloads folder.

The script removes the MAC Address, WPA and WEP key for security.
Thanks

---

### Post by SupermanNC21 on 2012-08-17
i tired that script nothing happen at first it couldn't find file then i showed it the right way there then i asked for pass enter pass then it stop after that it didn't do anything else, idk maybe i should just delete Ubuntu and start all over again from scratch. cause this wireless is maken me mad an doesnt help when ethernet port doesn't either.

---

### Post by wildmanne39 on 2012-08-17
Hi, look in your download folder for netinfo.txt file and attach it if it is there.
Thanks

---

### Post by SupermanNC21 on 2012-08-17
WOOT ubuntu still has hope for me yet ok i got it right i add the file u want onto my desktop but here's what it pop out.
 

```
*************** info trace ****************
 
**** uname -a ****

Linux ubuntu 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

**** lsb-release ****

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

**** lspci ****

02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019]
 Subsystem: Gateway 2000 Device [107b:0603]
 Kernel driver in use: e1000
--
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
 Subsystem: Broadcom Corporation Device [14e4:0418]
 Kernel driver in use: b43-pci-bridge

**** lsusb ****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**** iwconfig ****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

**** rfkill ****

0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no

**** lsmod ****

Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
rfcomm                 38139  0 
parport_pc             32114  1 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
radeon                733693  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39791  0 
ttm                    65344  1 radeon
b43                   342643  0 
mac80211              436455  1 b43
drm_kms_helper         45466  1 radeon
psmouse                72846  0 
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
mac_hid                13077  0 
drm                   197692  4 radeon,ttm,drm_kms_helper
cfg80211              178679  2 b43,mac80211
soundcore              14635  1 snd
bcma                   25651  1 b43
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 radeon
shpchp                 32325  0 
firewire_ohci          40172  0 
ssb                    50691  1 b43
firewire_core          56906  1 firewire_ohci
e1000                 101693  0 
crc_itu_t              12627  1 firewire_core

**** nm-tool ****
 
NetworkManager Tool
State: disconnected
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off
 

**** NetworkManager.state ****
 
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

**** NetworkManager.conf ****
 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq
no-auto-default=<MAC address removed>,
[ifupdown]
managed=false

**** interfaces ****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

**** iwlist ****
 

**** resolv ****

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

**** blacklist.conf ****

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

**** dmesg ****

[    1.560834] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.560842] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.560930] e1000 0000:02:01.0: can't find IRQ for PCI INT B; probably buggy MP table
[    1.560953] e1000 0000:02:01.0: setting latency timer to 64
[    1.575177] b43-pci-bridge 0000:03:02.0: can't find IRQ for PCI INT C; probably buggy MP table
[    1.575244] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.575255] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.575266] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.575275] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.575284] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.581850] ssb: Sonics Silicon Backplane found on PCI device 0000:03:02.0
[    2.202752] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) <MAC address removed>
[    2.202766] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
[   31.630467] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   31.746339] Registered led device: b43-phy0::tx
[   31.746487] Registered led device: b43-phy0::rx
[   31.746613] Registered led device: b43-phy0::radio
[   35.816219] type=1400 audit(1345256267.113:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=719 comm="apparmor_parser"
[   36.071013] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   36.071025] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   36.071032] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   36.080526] ADDRCONF(NETDEV_UP): wlan0: link is not
```

---

### Post by wildmanne39 on 2012-08-17
Hi, it is a firmware issue still go back to post 16 and do what it says very carefully, copy and paste for accuracy and watch the terminal for errors.
Thanks

---

### Post by SupermanNC21 on 2012-08-17
windows cut this part off 
 
ready
[   78.293442] type=1400 audit(1345256309.589:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1581 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

**************** done ********************

---

### Post by SupermanNC21 on 2012-08-17
k i did post #16 again the firmware one it went in ok but didnt do anything it just pop up the wireless icon and said Disconnected-you are not connected now i reboot still noting did it over again same wireless icon tried turn wifi on didnt turn on. i didnt get any error in the therminal and it took the files out of the b43 exracted folder.

---

### Post by wildmanne39 on 2012-08-17
So is your light on, if so run and post the script again so we can see what is going on now and it will have a number in the file name like 1 or 2 for however many times you have run it.
Thanks

---

### Post by SupermanNC21 on 2012-08-17
nope lights off

---

### Post by wildmanne39 on 2012-08-17
Hi, please post the results of:
```
ls /lib/firmware/
```
here by clicking on new reply and click # then paste the information between the brackets.
Thanks

---

### Post by SupermanNC21 on 2012-08-18
```
3.2.0-23-generic-pae lp0bsinitvals13.fw 
3com lp0bsinitvals14.fw 
a0g0bsinitvals5.fw lp0bsinitvals15.fw 
a0g0bsinitvals9.fw lp0initvals13.fw 
a0g0initvals5.fw lp0initvals14.fw 
a0g0initvals9.fw lp0initvals15.fw 
a0g1bsinitvals13.fw matrox 
a0g1bsinitvals5.fw mrvl 
a0g1bsinitvals9.fw mts_cdma.fw 
a0g1initvals13.fw mts_edge.fw 
a0g1initvals5.fw mts_gsm.fw 
a0g1initvals9.fw mts_mt9234mu.fw 
acenic mts_mt9234zba.fw 
adaptec mwl8335_duplex.fw 
advansys mwl8k 
agere_ap_fw.bin myri10ge_ethp_z8e.dat 
agere_sta_fw.bin myri10ge_eth_z8e.dat 
aic94xx-seq.fw myri10ge_rss_ethp_z8e.dat 
ar3k myri10ge_rss_eth_z8e.dat 
ar7010_1_1.fw myricom 
ar7010.fw n0absinitvals11.fw 
ar9170-1.fw n0bsinitvals11.fw 
ar9170-2.fw n0initvals11.fw 
ar9170.fw NPE-B 
ar9271.fw NPE-C 
asihpi ositech 
ath3k-1.fw pcm5.fw 
ath6k phanfw.bin 
atmel_at76c502_3com.bin ql2100_fw.bin 
atmel_at76c502.bin ql2200_fw.bin 
atmel_at76c502d.bin ql2300_fw.bin 
atmel_at76c502e.bin ql2322_fw.bin 
atmel_at76c504_2958.bin ql2400_fw.bin 
atmel_at76c504a_2958.bin ql2500_fw.bin 
atmel_at76c504.bin qlogic 
atmel_at76c506.bin r128 
atmsar11.fw radeon 
av7110 rt2561.bin 
b0g0bsinitvals13.fw rt2561s.bin 
b0g0bsinitvals5.fw rt2661.bin 
b0g0bsinitvals9.fw rt2860.bin 
b0g0initvals13.fw rt2870.bin 
b0g0initvals5.fw rt3070.bin 
b0g0initvals9.fw rt3071.bin 
b43 rt3090.bin 
bnx2 rt73.bin 
bnx2x RTL8192E 
brcm RTL8192SE 
carl9170-1.fw rtl_nic 
cis rtlwifi 
cpia2 s2250.fw 
cxgb3 s2250_loader.fw 
cxgb4 sb16 
dabusb scripts 
dsp56k slicoss 
dvb-fe-xc5000-1.6.114.fw sun 
dvb-usb-dib0700-1.20.fw sxg 
dvb-usb-terratec-h5-drxk.fw TDA7706_OM_v2.5.1_boot.txt 
e100 TDA7706_OM_v3.0.2_boot.txt 
ea tehuti 
edgeport ti_3410.fw 
emi26 ti_5052.fw 
emi62 ti-connectivity 
ene-ub6250 tigon 
ess tlg2300_firmware.bin 
f2255usb.bin tr_smctr.bin 
GPL-3 ttusb-budget 
hp ucode11.fw 
htc_7010.fw ucode13.fw 
htc_9271.fw ucode14.fw 
i2400m-fw-usb-1.4.sbcf ucode15.fw 
i2400m-fw-usb-1.5.sbcf ucode5.fw 
i6050-fw-usb-1.5.sbcf ucode9.fw 
intelliport2.bin ueagle-atm 
ipw2100-1.3.fw usbdux 
ipw2100-1.3-i.fw usbduxfast_firmware.bin 
ipw2100-1.3-p.fw usbdux_firmware.bin 
ipw2200-bss.fw usbduxsigma_firmware.bin 
ipw2200-ibss.fw v4l-cx231xx-avcore-01.fw 
ipw2200-sniffer.fw v4l-cx23418-apu.fw 
isci v4l-cx23418-cpu.fw 
iwlwifi-1000-5.ucode v4l-cx23418-dig.fw 
iwlwifi-100-5.ucode v4l-cx2341x-dec.fw 
iwlwifi-105-6.ucode v4l-cx2341x-enc.fw 
iwlwifi-135-6.ucode v4l-cx2341x-init.mpg 
iwlwifi-2000-6.ucode v4l-cx23885-avcore-01.fw 
iwlwifi-2030-6.ucode v4l-cx23885-enc.fw 
iwlwifi-3945-2.ucode v4l-cx25840.fw 
iwlwifi-4965-2.ucode v4l-pvrusb2-24xxx-01.fw 
iwlwifi-5000-5.ucode v4l-pvrusb2-29xxx-01.fw 
iwlwifi-5150-2.ucode vicam 
iwlwifi-6000-4.ucode vntwusb.fw 
iwlwifi-6000g2a-5.ucode vxge 
iwlwifi-6000g2b-6.ucode WHENCE.ubuntu 
iwlwifi-6050-5.ucode whiteheat.fw 
kaweth whiteheat_loader.fw 
keyspan yam 
keyspan_pda yamaha 
korg zd1201-ap.fw 
lbtf_usb.bin zd1201.fw 
lgs8g75.fw zd1211 
libertas
```

---

### Post by wildmanne39 on 2012-08-18
Hi, I just installed the firmware on my system and it worked just like it should, please post the output of:
```
ls -al /lib/firmware/b43
```
Thanks

---

### Post by SupermanNC21 on 2012-08-18
total 8
drwxr-x--- 2 superman superman ****** Aug 16 22:23 .
drwxr-xr-x 63 root root 7168 Aug 18 00:06 ..

---

### Post by wildmanne39 on 2012-08-18
Hi try it this way please:

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
watch for error but complete the process even if you have an error.
Thanks

---

### Post by SupermanNC21 on 2012-08-18
ok it worked wifi turn on BUT when i connected it wasnt getting right ip address so wasn't able to connect to internet then i restarted an it wouldn't connet to router wep key wouldn't go in i checked it on windows to make sure i was using right key but im try and make another key to see if it will work but the one time it did connect with right key it wasn't get right ip address it wasn't like it ip address u would get for a invaild key.

---

### Post by wildmanne39 on 2012-08-18
Hi, we are getting closer now that it turns on post the information from the script again from post 12 since you already have one saved the next one well save with the number 1 in it and so on, it should give us the information we need to get it to work.
Thanks

---

### Post by SupermanNC21 on 2012-08-19
Ok i see what the problem is it only wants to connect to my router as an ad-hoc rather than an infrastructure an when i change to it wep key fails. here the info u needed.
 

```
*************** info trace ****************
 
**** uname -a ****

Linux ubuntu 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

**** lsb-release ****

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

**** lspci ****

02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019]
 Subsystem: Gateway 2000 Device [107b:0603]
 Kernel driver in use: e1000
--
03:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
 Subsystem: Broadcom Corporation Device [14e4:0418]
 Kernel driver in use: b43-pci-bridge

**** lsusb ****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**** iwconfig ****

wlan0     IEEE 802.11bg  ESSID:"superman2"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: <MAC address removed>   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

**** rfkill ****

0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no

**** lsmod ****

Module                  Size  Used by
ipt_MASQUERADE         12663  1 
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_tcpudp              12531  4 
iptable_filter         12706  1 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  1 
nf_nat                 24959  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat
nf_conntrack           73847  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21974  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
nls_utf8               12493  1 
isofs                  39553  1 
bnep                   17830  2 
parport_pc             32114  1 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
radeon                733693  2 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65344  1 radeon
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
b43                   342643  0 
drm_kms_helper         45466  1 radeon
pcmcia                 39791  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              436455  1 b43
drm                   197692  4 radeon,ttm,drm_kms_helper
cfg80211              178679  2 b43,mac80211
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27465  0 
bcma                   25651  1 b43
pcmcia_rsrc            18367  1 yenta_socket
i2c_algo_bit           13199  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                72846  0 
mac_hid                13077  0 
soundcore              14635  1 snd
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
shpchp                 32325  0 
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50691  1 b43
e1000                 101693  0 

**** nm-tool ****
 
NetworkManager Tool
State: connected (global)
- Device: wlan0  [superman2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points (* = current AP)
    *superman2:      Ad-Hoc, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
  IPv4 Settings:
    Address:         00.00.0.00
    Prefix:          24 (000.000.000.000)
    Gateway:         0.0.0.0
 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off
 

**** NetworkManager.state ****
 
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

**** NetworkManager.conf ****
 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq
no-auto-default=<MAC address removed>,
[ifupdown]
managed=false

**** interfaces ****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

**** iwlist ****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"superman2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 278712ms ago
                    IE: Unknown: 000973757065726D616E32
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD070050F202000100
 
**** resolv ****

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

**** blacklist.conf ****

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

**** dmesg ****

[    1.540096] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.540104] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.540182] e1000 0000:02:01.0: can't find IRQ for PCI INT B; probably buggy MP table
[    1.540199] e1000 0000:02:01.0: setting latency timer to 64
[    1.582724] b43-pci-bridge 0000:03:02.0: can't find IRQ for PCI INT C; probably buggy MP table
[    1.582790] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.582801] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.582810] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.582820] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.582829] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.590725] ssb: Sonics Silicon Backplane found on PCI device 0000:03:02.0
[    2.178761] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) <MAC address removed>
[    2.178775] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
[   31.879815] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   31.975249] Registered led device: b43-phy0::tx
[   31.975312] Registered led device: b43-phy0::rx
[   31.975371] Registered led device: b43-phy0::radio
[   35.810518] type=1400 audit(1345349069.102:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=689 comm="apparmor_parser"
[   35.811519] type=1400 audit(1345349069.102:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=689 comm="apparmor_parser"
[   36.476135] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   36.552661] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.553402] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.011668] type=1400 audit(1345349112.302:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1591 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  123.252133] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  131.820056] wlan0: Creating new IBSS network, BSSID <MAC address removed>
[  142.464023] wlan0: no IPv6 routers present
[  283.872068] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  315.232033] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  347.104053] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  379.104125] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)

**************** done ********************
```

---

### Post by wildmanne39 on 2012-08-19
Hi, it can not connect as ad-hoc, it has to be infrastructure.

Please do:
```
sudo iwconfig wlan0 mode managed
```
Then in network manager settings in the top right corner of the screen change your wireless settings to match the screenshoots, while in wireless settings change encryption to wpa/wpa2.

Go into your router settings and set your encryption so just wpa2 if you have that option if not the wpa2/wpa.

Make sure your wired connection is unplugged and you may need to remove iptables that you have set up it looks like it is blocking the connection.

If it does not connect after the changes please attach the info script again using the paper clip in the reply window so we can see if the changes took and what effect they had.
Reboot
Thanks

---

### Post by SupermanNC21 on 2012-08-19
i put the script in but it didnt bring up the application in your screen shot do you still want me to run that last script again it accept the command no error

---

### Post by wildmanne39 on 2012-08-19
Hi, the code I gave you will not bring up a window it will do something else that you will not see. 

Now that you have done that read the rest of my directions carefully to get to the part that has the screenshots, then also change your router settings as stated, then if it does not work attach a new information text file.
Thanks

---

### Post by SupermanNC21 on 2012-08-19
ok so i change the ipv4 add the DNS in ignored ipv6 change to infrastructure and wep key failed i put correct one in and ecrypection set to 128. ran that netinfo again an here results

---

### Post by wildmanne39 on 2012-08-19
Hi, in your router have you checked to make sure that wireless is turned on?

In network manager top right corner of the screen make sure enable wireless is checked.

I asked you to change your encryption in network manager to wpa/wpa2 and in the router to just wpa2 if it has that option but it is still on wep which does not work that well with linux.
Thanks

---

### Post by SupermanNC21 on 2012-08-19
ok so i change my connection to a wpa2 personal mixed with TKIP+AES but that didn't wrok pass keep failing changed it to a wpa personal with TKIP+AES and that didn't work pass keep failing. i tried putting in full ipv4 setting manual but still pass keeps failing. EPIC FAIL all that work an passwork failing i may just have to try it with no pass

---

### Post by wildmanne39 on 2012-08-19
Hi, did you do the first two things in my last post and what was the result?

Please see screenshot is wireless enabled?

Also attach screenshots of your wireless settings like the ones I attached for you a few posts back.
Thanks

---

### Post by SupermanNC21 on 2012-08-19
srry fell asleep but i was looking around earlyer an i stumped onto this im not sure what if its the problem im having but me an this guy have same router flashed with dd-wrt but i have mega frimware instead of generic heres the ubuntu link [http://ubuntuforums.org/showthread.php?t=989615](http://ubuntuforums.org/showthread.php?t=989615)
 but i think they worte the script for ehternet i think thats what "lan" means ok im try what you sujected now.

---

### Post by SupermanNC21 on 2012-08-20
yes i did 1st two umm i don't know how to do a screenshot

---

### Post by wildmanne39 on 2012-08-20
Hi, you can do a screenshot by ctrl+alt+printscreen or open the application screenshot then browse and find the screenshot and upload it as an attachment.
Thanks

---

### Post by SupermanNC21 on 2012-08-21
K here's the screenshot of me trying to connect to my router an but the pass fails

---

### Post by wildmanne39 on 2012-08-21
Hi, the screenshot should match the screenshots in post 39.

The screenshots did not attach.
Thanks

---

### Post by SupermanNC21 on 2012-08-22
sorry had to find a file to open it with.

---

### Post by SupermanNC21 on 2012-08-22
ok i just tried to scan to see if i couldn't find my network with.
"sudo iwlist wlan0 scan"
and it didn't find any an there a 3 around me not incluing mine but it didn't find any networks at all.

---

### Post by wildmanne39 on 2012-08-22
Hi, the screenshots I want you to post look exactly like the one's in post 39, the setting's are in network manger, click on edit connections.

Please do:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.
Thanks

---

### Post by SupermanNC21 on 2012-08-22
k i put that in and saved it an rebooted and "iwconfig" says power managment off but it still didn't help can't connect to router an i've dropped my pass until i can connect.

---

### Post by SupermanNC21 on 2012-08-23
k here those other screen shots

---

### Post by SupermanNC21 on 2012-08-28
Ok so i'm still lost my wireless driver works now but it can't connect to my router as an infrastructure it will connect as and ad-hoc but i don't have and ad-hoc everytime i change it to infrastructure the wpa key fails i also tried taking pass off and manual adding ip address,subnet,gateway,and dns in but that doesn't work so im lost now i don't know what else to do i've been looking around and i cant really find anything to fix this problem i have a broadcom 4306 wifi card working and a Linksys WRT54GS flashed with DD-WRT v24-sp2 Mega with WPA personal Tkip+Aes. 
I hope u all can help with this issue.

---

### Post by wildmanne39 on 2012-09-01
Hi, I noticed that your dns server does not match the screenshots in post 39.
Thanks

---

### Post by SupermanNC21 on 2012-09-05
Ok so i changed ipv4 to auto dhcp address only and ipv6 ignore but that didnt work wpa password failed turned pass off on router an it just wouldn't connect i'm lost i can't scan to find my network and i can't manual put my network in either its looking like Ubuntu will never let me connect

---

### Post by SupermanNC21 on 2012-09-18
ok so i've tried everything to connect to my connection but it seems as if my wifi card just can't see any networks i've tried connecting to my network went to starbucks and tried there my wifi card will turn on an off but that its i reinstalled b43 but that didn't help i tried manual ip i turn pass off i switch from wep to wpa2 personal i tried ipv6 ignore an link-to-link that my windows uses. it only seems to want to connect as an ah-hoc but i don't have another laptop to connect to when i try infrastructure thats when i get all my problems.

---

### Post by SupermanNC21 on 2012-09-19
ok so im giving up on installing my wifi card it looks as if that will never happen so im try and get my ethernet to work but it looks like i may have sum depends problems which could be effecting my BCM43x also.
Ubuntu wants to update but i can't connect to the internet.
Is there anyway that i can download the most latest updates for ubuntu 12.04LTS throught winodws 7 and install them on ubuntu.

---

### Post by SupermanNC21 on 2012-09-21
Ok so i'm more lost than i was before i still can't connect to the internet on ubuntu i tried using ndiswrapper again but that dont work i cant figure out how to install the deb file i download the Ubuntu cd and i doesn't want to work i tried figuring out how to get my ethernet to work i got a e100 file and that doesn't worth either it's been a month or more now and i'm still not online it starting to feel like ubuntu's not worth all the trouble i'm having but i would really like to try it out.

---

### Post by kurt18947 on 2012-09-22
Have you considered another wifi adapter?  There are several that are plug 'n' play no NDISwrapper or other workaround required.  And they're not budget busters -- $15 or less usually.

---

### Post by SupermanNC21 on 2012-09-22
ok so i just uninstalled and reinstalled ubuntu i think i got ndiswrapper in this time i used Sudo dpkg -i ndiswrapper-common-*.deb and untils they load up right from the terminal but when i run                       "sudo modprobe ndiswrapper" i get **FATAL**: module ndiswrapper cant find.

---

### Post by SupermanNC21 on 2012-09-22
Ok so here what i think my problem is i did ndiswrapper -l and i get Bcmwl5 installed then it says device {14E4:4320} alternate device ssb. does anyone know how i delete ssb or blacklist it.

---

### Post by SupermanNC21 on 2012-09-24
nah can't use another wifi card unless i take the main one out of my laptop all my usb drivers are out to only cd-rom and basic stuff like laptop mouse and keyboard works and graphic card works but it doesn't have updated driver it won't work in 3D only 2D.

---

### Post by SupermanNC21 on 2012-09-24
**SOLVED: **Ok so i'm the dumbest perosn ever. I finally got my wifi and ethernet and usb working in about 5sec and it took me a month to figure this out the 1st time i installed Ubuntu WUI i did it via wifi in windows 7 second time i did, the same way then i download cd and got smart an plugged my ethernet in while it download an low and behold my ethernet worked and while it was installing it install my usb drivers plugged trutle beach in a bam they got power. Wifi still didn't work but i open terminal typed in
sudo apt-get install linux-firmware-nonfreesudo apt-get install linux-firmware-nonfreebam it turn on did Ubuntu updates restarted and wifi is good to go thank you Wild Man for all you help bro.

---

