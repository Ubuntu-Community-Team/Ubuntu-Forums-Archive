---
title: "Wireless Card problem"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Guibibi on 2012-01-25
Hello guys,i have an WMP11_V27,and when i try to connect to the network,it says to enter the WEP key,but my network is under protection of WPA.Every time that i try to edit the network setup in my linux,when i try to join the network,it create a new one and ask me for a WEP key.I tried to install the drivers with ndiswrapper,i could connect to the network perfectly fine,but when i rebooted my computer,i dind't want to work anymore.

Hope you could help me :)

---

### Post by anewguy on 2012-01-26
I'm not familiar with your adapter, but I've seen this problem with drivers and/or adapters that actually don't support wpa.

Post back the output of:

lspci

- and -

lsmod


That way we should be able to determine the chipset being used and if a module (driver) is loaded.  It will also allows us to research whether the driver or hardware supports WPA.

Dave ;)

---

### Post by Guibibi on 2012-01-26
Hello,thank you for the fast response,here is the result of lspci:

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0b.0 Network controller: Broadcom Corporation BCM4301 802.11b Wireless LAN Controller (rev 02)
00:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0d.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)


And lsmod

> Module                  Size  Used by
snd_hrtimer            12648  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
ppdev                  12849  0 
snd_emu10k1           133258  3 snd_emu10k1_synth
snd_usb_audio         100930  2 
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_via82xx            24720  2 
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  3 snd_emu10k1,snd_via82xx,snd_via82xx_modem
psmouse                73673  0 
ac97_bus               12642  1 snd_ac97_codec
serio_raw              12990  0 
snd_pcm                80435  5 snd_usb_audio,snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_mpu401_uart        13865  1 snd_via82xx
i2c_viapro             12969  0 
snd_hwdep              13276  3 snd_emux_synth,snd_usb_audio,snd_emu10k1
radeon                925178  3 
snd_page_alloc         14115  4 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_pcm
snd_seq_midi           13132  0 
snd_rawmidi            25241  5 snd_seq_virmidi,snd_emu10k1,snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
ns558                  12654  0 
parport_pc             32114  1 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
ttm                    65224  1 radeon
snd_seq                51567  6 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
binfmt_misc            17292  1 
snd_timer              28932  4 snd_hrtimer,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 radeon
snd                    55902  28 snd_emux_synth,snd_seq_virmidi,snd_usb_audio,snd_emu10k1,snd_via82xx,snd_usbmidi_lib,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lm63                   13998  0 
it87                   29199  0 
emu10k1_gp             12570  0 
hwmon_vid              12658  1 it87
soundcore              12600  1 snd
gameport               15060  5 snd_via82xx,ns558,emu10k1_gp
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
via_rhine              27413  0 
pata_via               13398  2 
sata_via               13534  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60310  0 


---

### Post by anewguy on 2012-01-26
I'm in a rush here as I am trying to head out.  Based on the PM's you sent me, 2 things seem to come to mind:

- if you have to reload the driver on each boot we need to know what you mean:

if you mean you have to modprobe:

edit the etc/modules file and add a line containing the module name


if you mean you use ndiswrapper/ndisgtk (Windows drivers), then add a line to the bottom of the /etc/modules file that simply says

ndiswrapper


If you mean something else, please explain.

I would also try hard-wiring the computer to the router and doing the following:

sudo apt-get update

sudo apt-get upgrade

Then look for Additional Drivers in your menus and click it.  It will take a little while to search for a compatible driver.  If it finds one and shows it, be sure it is marked as "enabled".

Disconnect the hard wire connection.

reboot.

I'm going to be gone for a few hours.

---

### Post by Guibibi on 2012-01-26
Hello,thank your  for replying.

What i meant for the reloading driver was modprobe,so i will try adding the line.

I did the commands in the terminal and used Additionals driver,but i did not find drivers.I was connected to the internet by a wire when doing this.

---

### Post by anewguy on 2012-01-28
BCM4301 - try following this link:

[http://linuxforums.org.uk/index.php?topic=5842.0]("http://linuxforums.org.uk/index.php?topic=5842.0")


Dave ;)

---

### Post by anewguy on 2012-01-28
Also note:  from what I've seen on the net, you can't connect to a WPA network with this adapter -> only open or WEP.  It's also only a "B" adapter, not a B/G or B/G/N.

So, you won't be able to connect to your WPA network.  And while you may be tempted, DON'T go backwards to a WEP network - can be hacked in to easily in just a few seconds.  Stay at WPA or WPA2, check on another adapter if need be and if funds allow (you can usually pick one up fairly cheap if you're patient and just keep watching Ebay).

Dave ;)

---

### Post by sandyd on 2012-01-28
> **anewguy said:**
> Also note:  from what I've seen on the net, you can't connect to a WPA network with this adapter -> only open or WEP.  It's also only a "B" adapter, not a B/G or B/G/N.

So, you won't be able to connect to your WPA network.  And while you may be tempted, DON'T go backwards to a WEP network - can be hacked in to easily in just a few seconds.  Stay at WPA or WPA2, check on another adapter if need be and if funds allow (you can usually pick one up fairly cheap if you're patient and just keep watching Ebay).

Dave ;)
+1.
Check [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) for supported adaptors

P.S. There have actually been some instances where some routers (***cough*** Cisco Wireless-N VPN Firewall ***cough***), have this weird thing where the wireless network displays on the computer - even though the network card supports only b, and the router is broadcasting in g/n. Deathly confusing, and it doesn't work anyways. Took me an hour to figure out that the card didn't even support b....

Check what your router is broadcasting in.

---

