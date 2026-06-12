---
title: "wireless driver issue on packard bell easy note"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by alexreyland on 2012-03-16
Im trying to brake into the big bad world of Linux and the biggest thing thats putting me off is not being able to get the wireless working on this old Packard bell easynote r1935 laptop

after installing latest ubuntu a message comes up that a propitiatory driver for the wireless needs to be activated, so i did and still no sign of wireless working. i know you need more info but i dont know what so just ask with specific instructions keeping in mind in a noob

thanks for your time

oh, and i like your socks, they say a lot about you:-s

---

### Post by Daveth on 2012-03-16
Hallo. Welcome to the Ubuntu Forum.
Does this post match your machine?

[http://steveyoung.wordpress.com/2011/08/11/no-wireless-networks-with-easynote-laptop-and-ubuntu-11-04/](http://steveyoung.wordpress.com/2011/08/11/no-wireless-networks-with-easynote-laptop-and-ubuntu-11-04/)

---

### Post by alexreyland on 2012-03-16
yes!! and thats helped a bit. at east now it says it can enable wireless but now it says its not ready, any ideas.

 thanks for quick response

---

### Post by wildmanne39 on 2012-03-16
Hi, please post the output of:
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

### Post by alexreyland on 2012-03-17
here it is


cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmodalex@alex-Packard-Bell-EasyNote:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux alex-Packard-Bell-EasyNote 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux
alex@alex-Packard-Bell-EasyNote:~$ lspci -nnk | grep -iA2 net
00:06.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: Ralink corp. EW-7108PCg [1814:2561]
	Kernel driver in use: rt61pci
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
	Subsystem: Packard Bell B.V. Device [1631:c015]
	Kernel driver in use: via-rhine
alex@alex-Packard-Bell-EasyNote:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
alex@alex-Packard-Bell-EasyNote:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


so what is the prognosis?

---

### Post by alexreyland on 2012-03-17
what's with the smilies?

---

### Post by alexreyland on 2012-03-17
sorry only rust read the last bit of your message
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmodalex@alex-Packard-Bell-EasyNote:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux alex-Packard-Bell-EasyNote 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux
alex@alex-Packard-Bell-EasyNote:~$ lspci -nnk | grep -iA2 net
00:06.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
Subsystem: Ralink corp. EW-7108PCg [1814:2561]
Kernel driver in use: rt61pci
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
Subsystem: Packard Bell B.V. Device [1631:c015]
Kernel driver in use: via-rhine
alex@alex-Packard-Bell-EasyNote:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bg ESSIDff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

alex@alex-Packard-Bell-EasyNote:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
```

---

### Post by wildmanne39 on 2012-03-19
Hi, please try this and just copy and paste for accuracy:
```
sudo ifconfig wlan0 down
sudo rmmod -f rt61pci
sudo modprobe rt61pci nohwcrypt=1
sudo ifconfig wlan0 up

```
This is good for one boot so do not reboot, if it works we need to make it permanent.
Thanks

---

### Post by alexreyland on 2012-03-19
i did and it replyed```
SIOCSIFFLAGS: Device or resource busy

```so what's next experts?

---

### Post by wildmanne39 on 2012-03-19
Hi reboot your computer then try the commands again and run them one line at a time.
Thanks

---

### Post by alexreyland on 2012-03-19
I'm afraid it is still the same output after turning off and on (cant restart as it hangs) did all individually ```
alex@alex-Packard-Bell-EasyNote:~$ sudo ifconfig wlan0 down
alex@alex-Packard-Bell-EasyNote:~$ sudo rmmod -f rt61pci
alex@alex-Packard-Bell-EasyNote:~$ sudo modprobe rt61pci nohwcrypt=1
alex@alex-Packard-Bell-EasyNote:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Device or resource busy

```

---

### Post by wildmanne39 on 2012-03-20
Hi, I suggest you unplug your usb adapter then run those commands then plug it into a new usb port.

I believe there is a problem with the adapter using that port.
Thanks

---

### Post by alexreyland on 2012-03-20
This is an inbuilt adapter in my pakard bell easynote r1935

---

### Post by wildmanne39 on 2012-03-20
Hi, sorry I knew that, I confused yours with another persons.

It is still the same answer basically I believe there is a problem with the slot it is in from what you say it can not be moved to another slot is that correct?
Thanks

---

### Post by alexreyland on 2012-03-20
Nope only one slot for wireless card in this laptop. I had similar trouble getting wireless to work on xp when I reinstalled but found a random driver that did the trick. If I dig out what the driver was for you think its possible to find a linux equivilent? Otherwise are there any USB adaptors you would suggest that are well supported in linux as I also need one for my raspberry pi when it arrives, maybe this deserves a new thread.

---

### Post by wildmanne39 on 2012-03-20
Hi, please show me the output of:
```
lsmod
```
so I can see if there is more then one driver loading for your device.

As for usb adapters there are so many variables that I do not give advice on them what works with one kernel will not work easily with another.
Thanks

---

### Post by alexreyland on 2012-03-21
here it is, hope you can make sense of it```
alex@alex-Packard-Bell-EasyNote:~$ lsmod
Module                  Size  Used by
via                    45249  2 
drm                   192194  3 via
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
rfcomm                 38408  0 
joydev                 17393  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_via82xx            24720  2 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
arc4                   12473  2 
rt61pci                27493  0 
crc_itu_t              12627  1 rt61pci
snd_seq_midi           13132  0 
rt2x00pci              14202  1 rt61pci
rt2x00lib              48146  2 rt61pci,rt2x00pci
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi
mac80211              393421  2 rt2x00pci,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
i2c_viapro             12969  0 
snd                    55902  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via_ircc               26781  0 
irda                  185428  1 via_ircc
cfg80211              172427  2 rt2x00lib,mac80211
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              12600  1 snd
crc_ccitt              12595  1 irda
shpchp                 32356  0 
eeprom_93cx6           12653  1 rt61pci
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
via_rhine              27413  0 
hid                    77367  1 usbhid
pata_via               13398  2
```

---

### Post by wildmanne39 on 2012-03-21
Hi, the driver is loaded so lets dig deeper, please post the output of:
```
nm-tool
sudo iwlist scan
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
dmesg | egrep 'rt6|firm|radio|switch|wlan|etwork'
```
Thanks

---

### Post by alexreyland on 2012-03-21
i dont know if im being stupid or there is something wrong but it wont accept my password```
alex@alex-Packard-Bell-EasyNote:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:40:D0:95:7B:14

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             unavailable
  Default:           no
  HW Address:        00:10:60:67:7D:88

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


alex@alex-Packard-Bell-EasyNote:~$ sudo iwlist scan
[sudo] password for alex: 

```

---

### Post by wildmanne39 on 2012-03-21
Hi, if you look at post 18 you will see on the right side of the box that has the commands in it there is a scroll bar, scroll down and post the output from the other 3 commands please.
thanks

---

### Post by alexreyland on 2012-03-21
```
alex@alex-Packard-Bell-EasyNote:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
alex@alex-Packard-Bell-EasyNote:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
alex@alex-Packard-Bell-EasyNote:~$ dmesg | egrep 'rt6|firm|radio|switch|wlan|etwork'^C
alex@alex-Packard-Bell-EasyNote:~$ 

```
the terminal password is the same as my login password isnt it?

---

### Post by HiImTye on 2012-03-21
..ignore this

---

### Post by wildmanne39 on 2012-03-21
Hi, will you try this command again and just copy and paste I hope it shows output because it should.
```
dmesg | egrep 'rt6|firm|radio|switch|wlan|etwork'
```
Thanks

---

### Post by alexreyland on 2012-03-21
```
alex@alex-Packard-Bell-EasyNote:~$ dmesg | egrep 'rt6|firm|radio|switch|wlan|etwork'
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.012686] SMP alternatives: switching to UP code
[   11.709635] type=1400 audit(1332351910.013:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=475 comm="apparmor_parser"
[   12.515005] type=1400 audit(1332351910.817:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=621 comm="apparmor_parser"
[   12.747165] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   12.747182] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   12.747199] rt61pci 0000:00:06.0: setting latency timer to 64
[   12.848938] Registered led device: rt61pci-phy0::radio
[   12.849032] Registered led device: rt61pci-phy0::assoc
[   14.435309] Console: switching to colour frame buffer device 80x30
alex@alex-Packard-Bell-EasyNote:~$ 

```

---

### Post by wildmanne39 on 2012-03-21
Hi, this is your problem > can't find IRQ for PCI INT A
lets try changing this ```
GRUB_CMDLINE_LINUX=""
```
To
```
GRUB_CMDLINE_LINUX="pci=biosirq"
```
Then run ```
sudo update-grub
```
and reboot.

Also if you can update your bios that may fix the problem but it is always risky to do so.
Thanks

---

### Post by alexreyland on 2012-03-21
tried that but no change. ill look into updating the bios. 
thanks for all the help, i think my first mission in linux is to try and get a grasp of bash and understand all the commands you fired at me.

and thanks again!

---

### Post by wildmanne39 on 2012-03-21
Hi, it takes time to learn commands, I learned then from the forum.

Please run this command again and we can see if it helped and there is also another issue now that did not show up until the first problem was solved.
```
dmesg | egrep 'rt6|firm|radio|switch|wlan|etwork'
```
Thanks

---

### Post by alexreyland on 2012-03-22
```
dmesg | egrep 'rt6|firm|radio|switch|wlan|etwork'alex@alex-Packard-Bell-EasyNoteork'dmesg | egrep 'rt6|firm|radio|switch|wlan|etw 
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.008668] SMP alternatives: switching to UP code
[   11.597263] type=1400 audit(1332442406.907:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[   12.562639] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   12.562656] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   12.562673] rt61pci 0000:00:06.0: setting latency timer to 64
[   12.756576] Registered led device: rt61pci-phy0::radio
[   12.756657] Registered led device: rt61pci-phy0::assoc
[   13.886561] type=1400 audit(1332442409.195:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=735 comm="apparmor_parser"
[   14.543570] Console: switching to colour frame buffer device 80x30
alex@alex-Packard-Bell-EasyNote:~$ 

```

---

### Post by wildmanne39 on 2012-03-22
Hi, you have the same problem so if you can update your bios it may fix your problem if that does not help there are other grub parameters we can try.
Thanks

---

