---
title: "PCI WIFI card not working?"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Org1 on 2011-12-08
I'm a noob when it comes to Ubuntu.

I installed a RaLink RT2561 PCI wifi card from what I've read it should of worked right out of the box: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

I created a new wireless profile (named it wifi) its is set to 2.4ghz (channel 1 2.412ghz) but I can't find it with my phone (or Nintendo wii) the light on the back of the wifi card is not blinking.

I use Ubunut 11.10 it is updated.

Do I need to install a driver? if so how I don't know how to do things like that on Ubuntu.

---

### Post by Org1 on 2011-12-09
I downloaded the driver and firmware.

**[Firmware RT2501(RT2561/RT2661)]("http://www.ralinktech.com/en/04_support/license.php?sn=5027")** [B][RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)]("http://www.ralinktech.com/en/04_support/license.php?sn=5024")


but I don't know what to do next.
[]("http://www.ralinktech.com/en/04_support/license.php?sn=5024")[/B]

---

### Post by gandaran on 2011-12-09
before you install anything check if any ralink driver is loaded
```
lsmod
```
shows drivers/modules loaded and post here the output 
also post the output of
```
lspci
```
sometimes ubuntu loads the wrong ralink driver for the device, usually it's easy to fix by just blacklisting the driver so the right driver can load.

---

### Post by Org1 on 2011-12-09
> adam@adam-desktop:~$ lsmod
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
nf_nat                 24958  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat
nf_conntrack           70103  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21975  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
nvidia              10390874  30 
binfmt_misc            17292  1 
arc4                   12473  2 
rt61pci                27493  0 
rt2x00pci              14202  1 rt61pci
rt2x00lib              48114  2 rt61pci,rt2x00pci
mac80211              393459  2 rt2x00pci,rt2x00lib
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
snd_emu10k1           133258  5 snd_emu10k1_synth
snd_ac97_codec        106082  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  3 snd_emu10k1,snd_ac97_codec
snd_page_alloc         14115  2 snd_emu10k1,snd_pcm
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13276  2 snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
snd_rawmidi            25241  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
dcdbas                 14098  0 
snd_seq                51567  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  2 rt2x00lib,mac80211
emu10k1_gp             12570  0 
gameport               15060  2 emu10k1_gp
eeprom_93cx6           12653  1 rt61pci
soundcore              12600  1 snd
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
ahci                   21634  0 
libahci                25727  1 ahci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  2 rt61pci,firewire_core
tg3                   132972  0 


The rt61pci's is that it being loaded?

> 
adam@adam-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82955X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82955X PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
05:03.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
05:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
adam@adam-desktop:~$ 
.

---

### Post by gandaran on 2011-12-09
> rt61pci 27493 0 
rt2x00pci 14202 1 rt61pci
rt2x00lib 48114 2 rt61pci,rt2x00pci
> 05:03.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
the right driver for the device is loaded, should be working fine
> I created a new wireless profile (named it wifi) its is set to 2.4ghz but I can't find it with my phone (or Nintendo wii) the light on the back of the wifi card is not blinking.
can you explain what exactly you trying to do, setup a wireless access point to share wired internet?

---

### Post by Org1 on 2011-12-09
> **gandaran said:**
> the right driver for the device is loaded, should be working fine

can you explain what exactly you trying to do, setup a wireless access point to share wired internet?


Ya, The main goal is it connect the Wii too the internet via the wifi connection but no access point is found and the light on the wifi card isn't blinking.

It's with in rage (about 14 foot away).

---

### Post by Org1 on 2011-12-09
Could I have a defective card?

---

### Post by wildmanne39 on 2011-12-10
Hi, please post the results of this command it will tell us all the information needed to find out which of the drivers loaded is correct if some of them need blacklisted or have parameters that can be set to help you connect.
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by UltimateCat on 2011-12-10
> **Org1 said:**
> I'm a noob when it comes to Ubuntu.

I installed a RaLink RT2561 PCI wifi card from what I've read it should of worked right out of the box: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

I created a new wireless profile (named it wifi) its is set to 2.4ghz (channel 1 2.412ghz) but I can't find it with my phone (or Nintendo wii) the light on the back of the wifi card is not blinking.

I use Ubunut 11.10 it is updated.

Do I need to install a driver? if so how I don't know how to do things like that on Ubuntu.
:)   After you download the driver you can install it using Synaptic Package Manager.
It might be a little different from the Ubuntu10.04 that I have but I also have Ultimate Ed 2.7...Also the book " " Beginning Ubuntu Linux" has been helpful to me and the " Ubuntu Linux Bible" as well perhaps you could consider these aids.....
Good Luck to you

---

### Post by Org1 on 2011-12-10
[IMG]http://img26.imageshack.us/img26/120/screenshotat20111210021.png[/IMG]

Had to do screen shot couldn't get it all highlighted,

---

### Post by idoitprone on 2011-12-10
I cant find anything about it in linuxwireless site


[http://linuxwireless.org/en/users/Drivers/rt61pci?highlight=%28rt2561%29]("http://linuxwireless.org/en/users/Drivers/rt61pci?highlight=%28rt2561%29")

Here a link to opensuse post that has an answer, but the post is a little old and might not work. Are you sure your wireless does not work?

[http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/332352-ralink-rt2561-rt61-native-linux-drivers.html](http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/332352-ralink-rt2561-rt61-native-linux-drivers.html)

---

### Post by Org1 on 2011-12-10
Pretty sure its not working.  My phone/WII is not detecting anything at the very lest the light on the back of the card should of blinked atlest once if it was working.

---

### Post by wildmanne39 on 2011-12-10
Hi, the driver and all that it depends on are installed, so lets see if we can get it to connect to the internet.

Please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep rt6
```
```
dmesg | egrep 'rtl|firm|wpa|etowrk|wlan0'
```
Thank you

---

### Post by gandaran on 2011-12-10
> **Org1 said:**
> Pretty sure its not working.  My phone/WII is not detecting anything at the very lest the light on the back of the card should of blinked atlest once if it was working.
look try connecting to some wireless network first just check if the card is working then only when you are sure wireless work try the wifi sharing setup for the phone and wii

---

### Post by Org1 on 2011-12-10
Screenshots: 
[http://img857.imageshack.us/img857/3432/66387974.png](http://img857.imageshack.us/img857/3432/66387974.png)
[http://img268.imageshack.us/img268/4744/20795123.png](http://img268.imageshack.us/img268/4744/20795123.png)


Don't have any other wifi connection around here nearest one is at-lest 400 foot away.

---

### Post by wildmanne39 on 2011-12-10
Hi, do you have your computer plugged into your modem with a hardwire? I am going to give you a link to refer too.
[http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/](http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/)
I can only help getting the card working which needs to be done first before trying to set it up as an access point because that is the easiest way, having said that it looks like your card should work it is just a matter of setting it as an access point.

I did some research and I found one link that said the driver that you have to use does not support master mode and if that is the case it will never work as an access point, it will be able to connect to a wireless network though, but you have to change ad-hoc mode to infrastructure.
Thank you

---

### Post by Org1 on 2011-12-10
Ya, the computers plunged in with a hardwired from a linksys router. Darn needed it for the AP guess buying the cheapest card was a bad idea  ](*,).

Thank you for the help (everyone).

---

### Post by wildmanne39 on 2011-12-10
Hi, your welcome! maybe someone else will have a suggestion.

---

