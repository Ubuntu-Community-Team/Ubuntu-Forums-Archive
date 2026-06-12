---
title: "Problems with my Wlan card."
date: 2012-05-15
forum: New to Ubuntu
---

### Post by royhenriksen on 2012-05-15
hello,

I am completely new to linux and have just installed the latest version of Ubuntu on a Dell Latitude D531 with a Dell Wireless 1500 (802.11draft-n/a/g) WLAN minicard.
Since ubuntu didnt detect my wlan card, i downloaded the driver from this page:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Wireless_1500](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Wireless_1500)

and ndisgtk. It works perfectly to install the driver and my wlan card works, but everytime i reboot the computer, ubuntu doesnt detect the wlan card and i have to do the installation process all over again even windows wireless driver detects that the hardware is present. 

I have search all over the internet without finding a solution and would appreciate any help i can get from this forum in solving my problem.

---

### Post by Lisiano on 2012-05-15
A quick Google showed me it's a BCM94321MC (BCM4321), can you please open a terminal (Ctrl+Alt+T) and issue this command?```
lspci
```If you find this line there
```
Broadcom Corporation BCM4321 802.11a/b/g/n
```
Then all you need to do is to run this command 
```
sudo apt-get install firmware-b43-installer
```
And either reboot or run these 2 commands
```
sudo modprobe -r -f b43
sudo modprobe b43
```

And remember, The Internet is a _VERY_ big place.

---

### Post by royhenriksen on 2012-05-15
Hey, thanks for answering.
I did as you said and found the same wlan card. I typed in the command and it installed perfectely. still i have the same problem at reboot :(

---

### Post by Lisiano on 2012-05-15
Interesting, try the last 2 commands again. If they work, then you will have to fix whatever you did to get ndiswrapper to work.

---

### Post by royhenriksen on 2012-05-15
I wrote the two lines and when i tried to install the driver with ndiswrapper, the computer froze or turned black with a lot codes scrolling down

---

### Post by Lisiano on 2012-05-15
Nonononononono(Repeat 42 times) and no. When we give commands, we tell you how to use them and when, I didn't say to use ndiswrapper. Just run the 2 commands without ndiswrapper and tell me if starts. Also please point to the tutorial you used to install ndiswrapper and the drivers.

---

### Post by royhenriksen on 2012-05-15
When i typed the first line, it asked for my password where i typed it in and nothing happend. When i typed in the second line, nothing happend either. I downloaded an graphical interface of ndiswrapper from ubuntu software center and the driver from the link above in the first post.

---

### Post by Lisiano on 2012-05-15
Did you perform anything else when you used ndiswrapper? Like blacklisting drivers. The BCM4321 natively works on Ubuntu, it only requires the firmware to be installed.

Just incase ndisgtk actually does blacklisting itself, please show me the output of this command
```
cat /etc/modprobe.d/blacklist
```
And this command ```
lsmod
```

---

### Post by westie457 on 2012-05-15
Hi, I am with Lisiano with the nos.

Try things in this order -

Connect a cable, it is needed and run these commands ```
sudo apt-get install b43-fwcutter

sudo apt-get install --reinstall firmware-b43-installer

sudo apt-get remove ndiswrapper
```

Unplug the cable and reboot.

Your wireless should come to life. Post back here with the news.

---

### Post by westie457 on 2012-05-15
> **Bigpat said:**
> I have not used Ubuntu since 2009. I just did a fresh install of Ubuntu 12.04 and everything seems fine however here s what bugs me. I can connect to my WiFi in my home but no other WiFi out side of my home. I install ubuntu 12 on a samsung NC10 which is a mini. Please don't laught because I chose this over an Ipad. I really love Linux and I feel I need to get back into it again can you please help me with this. Here is what I'm working with.

00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 5150
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

I can connect to my wire network at home but not anywhere else out side of my home like for example my job. Please help me with this issue

Please do not take this the wrong way. You should start a new thread for your issue.

You have different hardware to what the OP is using and to help you in this thread would cause a lot of confusion. Once you have your new thread you can post a link to it here so we can find it.

Thank you

---

### Post by royhenriksen on 2012-05-15
from the first line:
roy@roy-Latitude-D531:~$ cat /etc/modprobe.d/blacklist
cat: /etc/modprobe.d/blacklist: No such file or directory
roy@roy-Latitude-D531:~$ 

Second:
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148869  10 rfcomm,bnep
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60049  1 
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
pcmcia                 39822  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73673  0 
soundcore              12600  1 snd
serio_raw              12990  0 
k8temp                 12905  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
radeon                933705  3 
video                  19069  0 
ttm                    65224  1 radeon
wmi                    18744  1 dell_wmi
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
sp5100_tco             13495  0 
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
wl                   2646601  0 
shpchp                 32356  0 
ati_agp                13242  0 
lib80211               14570  1 wl
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12967  0 
tg3                   132972  0 
ahci                   21634  2 
libahci                25727  1 ahci

---

### Post by Lisiano on 2012-05-15
Please run this command (Forgot that lsmod isn't sorted)
```
lsmod | sort
```And please use code tags (The hash (#) button) so it is easier to read and so the forum doesn't cut it off.

Also please post the output of these commands as well
```
sudo modprobe -r -f b43
sudo modprobe -f b43
sleep 5s
dmesg | tail -50
```

---

### Post by royhenriksen on 2012-05-15
hey, i ran the following setup and still at reboot nothing happend. However at the third line there where some error about that the following directory didnt exist.

---

### Post by royhenriksen on 2012-05-15
```

roy@roy-Latitude-D531:~$ lsmod | sort
ahci                   21634  2 
ati_agp                13242  0 
binfmt_misc            17292  1 
bluetooth             148869  10 rfcomm,bnep
bnep                   17923  2 
crc_itu_t              12627  1 firewire_core
dcdbas                 14098  1 dell_laptop
dell_laptop            13519  0 
dell_wmi               12601  0 
drm                   192194  5 radeon,ttm,drm_kms_helper
drm_kms_helper         32889  1 radeon
firewire_core          56937  1 firewire_ohci
firewire_ohci          35854  0 
i2c_algo_bit           13199  1 radeon
i2c_piix4              13093  0 
joydev                 17393  0 
k8temp                 12905  0 
lib80211               14570  1 wl
libahci                25727  1 ahci
lp                     17455  0 
Module                  Size  Used by
parport                40930  3 parport_pc,ppdev,lp
parport_pc             32114  0 
pata_atiixp            12967  0 
pcmcia                 39822  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
pcmcia_rsrc            18367  1 yenta_socket
ppdev                  12849  0 
psmouse                73673  0 
radeon                933705  3 
rfcomm                 38408  0 
serio_raw              12990  0 
shpchp                 32356  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hwdep              13276  1 snd_hda_codec
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28932  2 snd_pcm,snd_seq
soundcore              12600  1 snd
sp5100_tco             13495  0 
sparse_keymap          13658  1 dell_wmi
tg3                   132972  0 
ttm                    65224  1 radeon
video                  19069  0 
wl                   2646601  0 
wmi                    18744  1 dell_wmi
yenta_socket           27428  0 

```

---

### Post by Lisiano on 2012-05-15
Looks like b43 (The BCM4321 driver) is not loaded, run the 4 commands from my post edit above

---

### Post by royhenriksen on 2012-05-15
```

roy@roy-Latitude-D531:~$ sudo modprobe -r -f b43
[sudo] password for roy: 
roy@roy-Latitude-D531:~$ sudo modprobe -f b43
WARNING: Error inserting mac80211 (/lib/modules/3.0.0-19-generic/kernel/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting ssb (/lib/modules/3.0.0-19-generic/kernel/drivers/ssb/ssb.ko): Invalid module format
FATAL: Error inserting b43 (/lib/modules/3.0.0-19-generic/kernel/drivers/net/wireless/b43/b43.ko): Invalid module format
roy@roy-Latitude-D531:~$ sleep 5s
roy@roy-Latitude-D531:~$ dmesg | tail -50
[   20.202128] [drm] radeon: power management initialized
[   20.290304] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   20.292351] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x408-0x40f 0x4d0-0x4d7
[   20.293173] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   20.293872] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xc80-0xcbf 0xcd0-0xcdf
[   20.294344] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xf0000-0xfffff
[   20.294411] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   20.294476] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   20.294547] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: excluding nothing: probe failed.
[   20.607193] Bluetooth: Core ver 2.16
[   20.607329] NET: Registered protocol family 31
[   20.607332] Bluetooth: HCI device and connection manager initialized
[   20.607337] Bluetooth: HCI socket layer initialized
[   20.607340] Bluetooth: L2CAP socket layer initialized
[   20.608588] Bluetooth: SCO socket layer initialized
[   20.615075] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.615082] Bluetooth: BNEP filters: protocol multicast
[   20.621257] Bluetooth: RFCOMM TTY layer initialized
[   20.621268] Bluetooth: RFCOMM socket layer initialized
[   20.621272] Bluetooth: RFCOMM ver 1.11
[   20.794025] composite sync not supported
[   20.891456] [drm] fb mappable at 0xE0040000
[   20.891461] [drm] vram apper at 0xE0000000
[   20.891463] [drm] size 4096000
[   20.891466] [drm] fb depth is 24
[   20.891468] [drm]    pitch is 5120
[   20.891626] fbcon: radeondrmfb (fb0) is primary device
[   20.891825] Console: switching to colour frame buffer device 160x50
[   20.891872] fb0: radeondrmfb frame buffer device
[   20.891874] drm: registered panic notifier
[   20.891887] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[   21.092061] composite sync not supported
[   21.146418] ppdev: user-space parallel port driver
[   21.935940] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   22.158091] composite sync not supported
[   22.512098] composite sync not supported
[   24.040159] composite sync not supported
[   24.548131] composite sync not supported
[   25.183113] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   28.508080] composite sync not supported
[   29.264087] composite sync not supported
[   29.672117] composite sync not supported
[   30.424084] composite sync not supported
[   60.776400] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   60.776407] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   60.776665] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   61.000082] dell_wmi: Unknown key e043 pressed
[   71.504029] eth0: no IPv6 routers present
[  290.253203] CE: hpet increased min_delta_ns to 20113 nsec
[  662.952546] CE: hpet increased min_delta_ns to 30169 nsec


```

---

### Post by Lisiano on 2012-05-15
This is strange. Another driver called mac80211 and ssb are failing to be installed. Could you run this again to make sure b43 installed correctly?
```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
```
Post the output of the 2nd command.

---

### Post by royhenriksen on 2012-05-15
```

roy@roy-Latitude-D531:~$ sudo apt-get purge firmware-b43-installer
[sudo] password for roy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Følgende pakker vil bli FJERNET:
  firmware-b43-installer*
0 oppgraderte, 0 nylig installerte, 1 å fjerne og 0 ikke oppgradert.
Etter denne operasjonen vil 53,2 kB diskplass bli ledig.
Vil du fortsette [Y/n]? Y
(Leser database ... 163219 filer og kataloger er for øyeblikket installerte.)
Fjerner firmware-b43-installer ...
Deleting old extracted firmware...
Renser ut oppsettsfiler for firmware-b43-installer ...
roy@roy-Latitude-D531:~$ sudo apt-get install firmware-b34-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b34-installer
roy@roy-Latitude-D531:~$ 






```

---

### Post by Lisiano on 2012-05-15
You mistyped the 2nd command (Typed b34 instead of b43), to avoid such issues, just copy paste it right to the terminal, or even drag-and-drop(tm) it there.

---

### Post by royhenriksen on 2012-05-15
```

roy@roy-Latitude-D531:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Følgende NYE pakker vil bli installert:
  firmware-b43-installer
0 oppgraderte, 1 nylig installerte, 0 å fjerne og 0 ikke oppgradert.
Må hente 0 B/3 272 B med arkiver.
Etter denne operasjonen vil 53,2 kB ekstra diskplass bli brukt.
Velger den tidligere fravalgte pakken firmware-b43-installer.
(Leser database ... 163216 filer og kataloger er for øyeblikket installerte.)
Pakker ut firmware-b43-installer (fra .../firmware-b43-installer_1%3a014-9_all.deb) ...
Setter opp firmware-b43-installer (1:014-9) ...
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2012-05-16 01:54:06--  http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
Resolving mirror2.openwrt.org... 46.4.11.11
Connecting to mirror2.openwrt.org|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596823 (1,5M) [application/x-bzip2]
Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'

100%[======================================>] 1 596 823    252K/s   in 6,2s    

2012-05-16 01:54:12 (251 KB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]

broadcom-wl-5.10.56.27.3/driver/
broadcom-wl-5.10.56.27.3/driver/Makefile
broadcom-wl-5.10.56.27.3/driver/aiutils.c
broadcom-wl-5.10.56.27.3/driver/bcmsrom.c
broadcom-wl-5.10.56.27.3/driver/bcmutils.c
broadcom-wl-5.10.56.27.3/driver/hnddma.c
broadcom-wl-5.10.56.27.3/driver/hndpmu.c
broadcom-wl-5.10.56.27.3/driver/include/
broadcom-wl-5.10.56.27.3/driver/include/UdpLib.h
broadcom-wl-5.10.56.27.3/driver/include/aidmp.h
broadcom-wl-5.10.56.27.3/driver/include/arminc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcdc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aes.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aeskeywrap.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bcmccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bn.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/des.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/dh.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/hmac_sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md5.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/passhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/prf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rc4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rijndael-alg-fst.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha1.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/tkhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdefs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdevs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmendian.h
broadcom-wl-5.10.56.27.3/driver/include/bcmnvram.h
broadcom-wl-5.10.56.27.3/driver/include/bcmotp.h
broadcom-wl-5.10.56.27.3/driver/include/bcmparams.h
broadcom-wl-5.10.56.27.3/driver/include/bcmperf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmrobo.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_fmt.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_tbl.h
broadcom-wl-5.10.56.27.3/driver/include/bcmstdlib.h
broadcom-wl-5.10.56.27.3/driver/include/bcmutils.h
broadcom-wl-5.10.56.27.3/driver/include/bcmwifi.h
broadcom-wl-5.10.56.27.3/driver/include/bitfuncs.h
broadcom-wl-5.10.56.27.3/driver/include/dmemc_core.h
broadcom-wl-5.10.56.27.3/driver/include/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/igs/
broadcom-wl-5.10.56.27.3/driver/include/epivers.h
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.in
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.prev
broadcom-wl-5.10.56.27.3/driver/include/etioctl.h
broadcom-wl-5.10.56.27.3/driver/include/flash.h
broadcom-wl-5.10.56.27.3/driver/include/flashutl.h
broadcom-wl-5.10.56.27.3/driver/include/hndarm.h
broadcom-wl-5.10.56.27.3/driver/include/hndchipc.h
broadcom-wl-5.10.56.27.3/driver/include/hndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/hnddma.h
broadcom-wl-5.10.56.27.3/driver/include/hndgige.h
broadcom-wl-5.10.56.27.3/driver/include/hndjtagdefs.h
broadcom-wl-5.10.56.27.3/driver/include/hndmips.h
broadcom-wl-5.10.56.27.3/driver/include/hndpci.h
broadcom-wl-5.10.56.27.3/driver/include/hndpmu.h
broadcom-wl-5.10.56.27.3/driver/include/hndsoc.h
broadcom-wl-5.10.56.27.3/driver/include/linux_gpio.h
broadcom-wl-5.10.56.27.3/driver/include/linux_osl.h
broadcom-wl-5.10.56.27.3/driver/include/linuxver.h
broadcom-wl-5.10.56.27.3/driver/include/min_osl.h
broadcom-wl-5.10.56.27.3/driver/include/mips33_core.h
broadcom-wl-5.10.56.27.3/driver/include/mips74k_core.h
broadcom-wl-5.10.56.27.3/driver/include/mipsinc.h
broadcom-wl-5.10.56.27.3/driver/include/ndiserrmap.h
broadcom-wl-5.10.56.27.3/driver/include/nicpci.h
broadcom-wl-5.10.56.27.3/driver/include/osl.h
broadcom-wl-5.10.56.27.3/driver/include/pci_core.h
broadcom-wl-5.10.56.27.3/driver/include/pcicfg.h
broadcom-wl-5.10.56.27.3/driver/include/pcie_core.h
broadcom-wl-5.10.56.27.3/driver/include/proto/
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11e.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.1d.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmeth.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmevent.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmip.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmtcp.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eap.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eapol.h
broadcom-wl-5.10.56.27.3/driver/include/proto/ethernet.h
broadcom-wl-5.10.56.27.3/driver/include/proto/vlan.h
broadcom-wl-5.10.56.27.3/driver/include/proto/wpa.h
broadcom-wl-5.10.56.27.3/driver/include/rts/
broadcom-wl-5.10.56.27.3/driver/include/rts/crc.h
broadcom-wl-5.10.56.27.3/driver/include/sbchipc.h
broadcom-wl-5.10.56.27.3/driver/include/sbconfig.h
broadcom-wl-5.10.56.27.3/driver/include/sbgige.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndarm.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/sbhnddma.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndpio.h
broadcom-wl-5.10.56.27.3/driver/include/sbmemc.h
broadcom-wl-5.10.56.27.3/driver/include/sbpcmcia.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdio.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdpcmdev.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsocram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsprom.h
broadcom-wl-5.10.56.27.3/driver/include/sflash.h
broadcom-wl-5.10.56.27.3/driver/include/siutils.h
broadcom-wl-5.10.56.27.3/driver/include/trxhdr.h
broadcom-wl-5.10.56.27.3/driver/include/typedefs.h
broadcom-wl-5.10.56.27.3/driver/include/wlc_ethereal.h
broadcom-wl-5.10.56.27.3/driver/include/wlioctl.h
broadcom-wl-5.10.56.27.3/driver/include/wllmacctl.h
broadcom-wl-5.10.56.27.3/driver/linux_osl.c
broadcom-wl-5.10.56.27.3/driver/nicpci.c
broadcom-wl-5.10.56.27.3/driver/nvram_stub.c
broadcom-wl-5.10.56.27.3/driver/sbutils.c
broadcom-wl-5.10.56.27.3/driver/siutils.c
broadcom-wl-5.10.56.27.3/driver/siutils_priv.h
broadcom-wl-5.10.56.27.3/driver/wl_apsta/
broadcom-wl-5.10.56.27.3/driver/wl_apsta/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_dbg.h
broadcom-wl-5.10.56.27.3/driver/wl_export.h
broadcom-wl-5.10.56.27.3/driver/wl_iw.c
broadcom-wl-5.10.56.27.3/driver/wl_iw.h
broadcom-wl-5.10.56.27.3/driver/wl_linux.c
broadcom-wl-5.10.56.27.3/driver/wl_linux.h
broadcom-wl-5.10.56.27.3/driver/wlc_key.h
broadcom-wl-5.10.56.27.3/driver/wlc_pub.h
broadcom-wl-5.10.56.27.3/nas_exe.o
broadcom-wl-5.10.56.27.3/shared/
broadcom-wl-5.10.56.27.3/shared/Makefile
broadcom-wl-5.10.56.27.3/shared/UdpLib.c
broadcom-wl-5.10.56.27.3/shared/bcmcvar.h
broadcom-wl-5.10.56.27.3/shared/bcmtimer.h
broadcom-wl-5.10.56.27.3/shared/ctype.c
broadcom-wl-5.10.56.27.3/shared/linux_timer.c
broadcom-wl-5.10.56.27.3/shared/netconf.h
broadcom-wl-5.10.56.27.3/shared/opencrypto.h
broadcom-wl-5.10.56.27.3/shared/rte_timers.c
broadcom-wl-5.10.56.27.3/shared/shutils.c
broadcom-wl-5.10.56.27.3/shared/shutils.h
broadcom-wl-5.10.56.27.3/shared/wl.c
broadcom-wl-5.10.56.27.3/shared/wl_linux.c
broadcom-wl-5.10.56.27.3/shared/wlutils.h
broadcom-wl-5.10.56.27.3/wl_exe.o
This file is recognised as:
  ID         :  FW15
  filename   :  wl_prebuilt.o
  version    :  508.1084
  MD5        :  490d4e149ecc45eb1a91f06aa75be071
Extracting b43/ucode19.fw
Extracting b43/lp0initvals14.fw
Extracting b43/ucode16_lp.fw
Extracting b43/ucode16_sslpn.fw
  ucode revision: 1084
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/sslpn2bsinitvals17.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/ucode16_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/sslpn2initvals17.fw
Extracting b43/ucode4.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ucode17.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/pcm4.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/pcm5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/ucode20.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw

```

---

### Post by Bigpat on 2012-05-15
> **westie457 said:**
> Please do not take this the wrong way. You should start a new thread for your issue.

You have different hardware to what the OP is using and to help you in this thread would cause a lot of confusion. Once you have your new thread you can post a link to it here so we can find it.

Thank you
Sorry about that not used to the using forums

---

### Post by Lisiano on 2012-05-15
Darn character limit! Anyway, looks like it's installed (Mostly), so let's try loading it one more time.
```
sudo modprobe -r b43
sudo modprobe b43
sleep 5s
lsmod | sort
dmesg | tail -n 20
```

---

### Post by Bigpat on 2012-05-15
> **westie457 said:**
> Please do not take this the wrong way. You should start a new thread for your issue.

You have different hardware to what the OP is using and to help you in this thread would cause a lot of confusion. Once you have your new thread you can post a link to it here so we can find it.

Thank you
Here is the link to my new thread and once again sorry for the confusion.

[http://ubuntuforums.org/showthread.php?p=11939493#post11939493](http://ubuntuforums.org/showthread.php?p=11939493#post11939493)

---

### Post by royhenriksen on 2012-05-15
```

roy@roy-Latitude-D531:~$ sudo modprobe -r b43
[sudo] password for roy: 
roy@roy-Latitude-D531:~$ sudo modprobe b43
roy@roy-Latitude-D531:~$ sleep 5s
roy@roy-Latitude-D531:~$ lsmod | sort
ahci                   21634  2 
ati_agp                13242  0 
b43                   318816  0 
binfmt_misc            17292  1 
bluetooth             148869  10 rfcomm,bnep
bnep                   17923  2 
cfg80211              172427  2 b43,mac80211
crc_itu_t              12627  1 firewire_core
dcdbas                 14098  1 dell_laptop
dell_laptop            13519  0 
dell_wmi               12601  0 
drm                   192194  5 radeon,ttm,drm_kms_helper
drm_kms_helper         32889  1 radeon
firewire_core          56937  1 firewire_ohci
firewire_ohci          35854  0 
i2c_algo_bit           13199  1 radeon
i2c_piix4              13093  0 
joydev                 17393  0 
k8temp                 12905  0 
lib80211               14570  1 wl
libahci                25727  1 ahci
lp                     17455  0 
mac80211              393421  1 b43
Module                  Size  Used by
ndiswrapper           193669  0 
parport                40930  3 parport_pc,ppdev,lp
parport_pc             32114  0 
pata_atiixp            12967  0 
pcmcia                 39822  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
pcmcia_rsrc            18367  1 yenta_socket
ppdev                  12849  0 
psmouse                73673  0 
radeon                933705  3 
rfcomm                 38408  0 
serio_raw              12990  0 
shpchp                 32356  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hwdep              13276  1 snd_hda_codec
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28932  2 snd_pcm,snd_seq
soundcore              12600  1 snd
sp5100_tco             13495  0 
sparse_keymap          13658  1 dell_wmi
ssb                    50682  1 b43
tg3                   132972  0 
ttm                    65224  1 radeon
video                  19069  0 
wl                   2646601  0 
wmi                    18744  1 dell_wmi
yenta_socket           27428  0 
roy@roy-Latitude-D531:~$ dmesg | tail -n 20
[ 1055.270310] ndiswrapper 0000:0b:00.0: setting latency timer to 64
[ 1055.278495] ndiswrapper: using IRQ 17
[ 1055.697807] wlan0: ethernet device 00:1c:26:04:fa:ee using NDIS driver: bcmwl5, version: 0x4501c05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4312.5.conf
[ 1055.697948] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1055.698130] usbcore: registered new interface driver ndiswrapper
[ 1055.779940] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1066.427638] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1066.924890] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1077.408046] wlan0: no IPv6 routers present
[ 1095.160357] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1109.208051] wlan0: no IPv6 routers present
[ 2244.978980] cfg80211: Calling CRDA to update world regulatory domain
[ 2245.647027] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[ 2245.712781] cfg80211: World regulatory domain updated:
[ 2245.712804] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2245.712816] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2245.712826] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2245.712834] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2245.712842] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2245.712850] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
roy@roy-Latitude-D531:~$ 

```

---

### Post by Lisiano on 2012-05-15
Okay. It's loaded properly now and scanning. Does it find your WiFi spot on your end now?

If it does, all we need to do is get rid of ndiswrapper
```
sudo apt-get purge ndisgtk ndiswrapper-*
```

---

### Post by royhenriksen on 2012-05-15
it didnt show up on reboot.

---

### Post by Lisiano on 2012-05-15
The hell?
```
lsmod | sort
dmesg | tail -n 20
sudo modprobe -r b43
sudo modprobe b43
sleep 10s
lsmod | sort
dmesg | tail -n 20
```

---

### Post by royhenriksen on 2012-05-15
```

roy@roy-Latitude-D531:~$ lsmod | sort
ahci                   21634  2 
ati_agp                13242  0 
binfmt_misc            17292  1 
bluetooth             148869  10 bnep,rfcomm
bnep                   17923  2 
crc_itu_t              12627  1 firewire_core
dcdbas                 14098  1 dell_laptop
dell_laptop            13519  0 
dell_wmi               12601  0 
drm                   192194  5 radeon,ttm,drm_kms_helper
drm_kms_helper         32889  1 radeon
firewire_core          56937  1 firewire_ohci
firewire_ohci          35854  0 
i2c_algo_bit           13199  1 radeon
i2c_piix4              13093  0 
joydev                 17393  0 
k8temp                 12905  0 
lib80211               14570  1 wl
libahci                25727  1 ahci
lp                     17455  0 
Module                  Size  Used by
ndiswrapper           193669  0 
parport                40930  3 parport_pc,ppdev,lp
parport_pc             32114  0 
pata_atiixp            12967  0 
pcmcia                 39822  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
pcmcia_rsrc            18367  1 yenta_socket
ppdev                  12849  0 
psmouse                73673  0 
radeon                933705  3 
rfcomm                 38408  0 
serio_raw              12990  0 
shpchp                 32356  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hwdep              13276  1 snd_hda_codec
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28932  2 snd_pcm,snd_seq
soundcore              12600  1 snd
sp5100_tco             13495  0 
sparse_keymap          13658  1 dell_wmi
tg3                   132972  0 
ttm                    65224  1 radeon
video                  19069  0 
wl                   2646601  0 
wmi                    18744  1 dell_wmi
yenta_socket           27428  0 
roy@roy-Latitude-D531:~$ dmesg | tail -n 20
[   52.656525] keyboard: can't emulate rawmode for keycode 240
[   65.325807] dell_wmi: Unknown key e043 pressed
[   65.326042] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   65.326049] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   65.326302] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   75.376033] eth0: no IPv6 routers present
[  144.784520] CE: hpet increased min_delta_ns to 20113 nsec
[  144.785022] CE: hpet increased min_delta_ns to 30169 nsec
[  144.785455] CE: hpet increased min_delta_ns to 45253 nsec
[  212.488761] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  212.538554] ndiswrapper: driver bcmwl5 (Broadcom,06/21/2006, 4.80.28.5) loaded
[  212.539022] ndiswrapper 0000:0b:00.0: setting latency timer to 64
[  212.545644] ndiswrapper: using IRQ 17
[  212.958681] wlan0: ethernet device 00:1c:26:04:fa:ee using NDIS driver: bcmwl5, version: 0x4501c05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4312.5.conf
[  212.958827] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  212.959278] usbcore: registered new interface driver ndiswrapper
[  212.995068] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  223.407546] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  223.904694] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  237.664049] wlan0: no IPv6 routers present
roy@roy-Latitude-D531:~$ sudo modprobe -r b43
[sudo] password for roy: 
roy@roy-Latitude-D531:~$ sudo modprobe b43
roy@roy-Latitude-D531:~$ sleep 10s
roy@roy-Latitude-D531:~$ lsmod | sort
ahci                   21634  2 
ati_agp                13242  0 
b43                   318816  0 
binfmt_misc            17292  1 
bluetooth             148869  10 bnep,rfcomm
bnep                   17923  2 
cfg80211              172427  2 b43,mac80211
crc_itu_t              12627  1 firewire_core
dcdbas                 14098  1 dell_laptop
dell_laptop            13519  0 
dell_wmi               12601  0 
drm                   192194  5 radeon,ttm,drm_kms_helper
drm_kms_helper         32889  1 radeon
firewire_core          56937  1 firewire_ohci
firewire_ohci          35854  0 
i2c_algo_bit           13199  1 radeon
i2c_piix4              13093  0 
joydev                 17393  0 
k8temp                 12905  0 
lib80211               14570  1 wl
libahci                25727  1 ahci
lp                     17455  0 
mac80211              393421  1 b43
Module                  Size  Used by
ndiswrapper           193669  0 
parport                40930  3 parport_pc,ppdev,lp
parport_pc             32114  0 
pata_atiixp            12967  0 
pcmcia                 39822  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
pcmcia_rsrc            18367  1 yenta_socket
ppdev                  12849  0 
psmouse                73673  0 
radeon                933705  3 
rfcomm                 38408  0 
serio_raw              12990  0 
shpchp                 32356  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hwdep              13276  1 snd_hda_codec
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28932  2 snd_pcm,snd_seq
soundcore              12600  1 snd
sp5100_tco             13495  0 
sparse_keymap          13658  1 dell_wmi
ssb                    50682  1 b43
tg3                   132972  0 
ttm                    65224  1 radeon
video                  19069  0 
wl                   2646601  0 
wmi                    18744  1 dell_wmi
yenta_socket           27428  0 
roy@roy-Latitude-D531:~$ dmesg | tail -n 20
[  212.488761] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  212.538554] ndiswrapper: driver bcmwl5 (Broadcom,06/21/2006, 4.80.28.5) loaded
[  212.539022] ndiswrapper 0000:0b:00.0: setting latency timer to 64
[  212.545644] ndiswrapper: using IRQ 17
[  212.958681] wlan0: ethernet device 00:1c:26:04:fa:ee using NDIS driver: bcmwl5, version: 0x4501c05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4312.5.conf
[  212.958827] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  212.959278] usbcore: registered new interface driver ndiswrapper
[  212.995068] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  223.407546] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  223.904694] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  237.664049] wlan0: no IPv6 routers present
[  564.251362] cfg80211: Calling CRDA to update world regulatory domain
[  564.626513] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[  564.646118] cfg80211: World regulatory domain updated:
[  564.646133] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  564.646143] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  564.646152] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  564.646160] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  564.646168] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  564.646176] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
roy@roy-Latitude-D531:~$ 


```

---

### Post by Lisiano on 2012-05-15
I blame ndiswrapper. It's catching the card and puts it's driver onto it. Kill it with fire!
```
sudo apt-get purge ndisgtk ndiswrapper-*
```Now after a reboot it should finally stick.

---

### Post by royhenriksen on 2012-05-15
I am sorry to tell you, but it didnt work. i purged ndiswrapper, but no wifi at startup.

Earlier i did something in: gksudo gedit  /etc/modules 
and added wl to the end of the file. Could this be a cause to a problem?

---

### Post by Lisiano on 2012-05-15
Yes, please remove it. We don't need statically loaded modules as most of the time our systems handle it really well.

---

### Post by royhenriksen on 2012-05-15
i have still no luck with my wifi.

---

### Post by Lisiano on 2012-05-15
Ugggghhh... Weird system. I have a nagging suspicion it's something you changed somewhere. For now, just use ```
sudo modprobe b43
``` to turn it on. I'll think of possible causes tommorow as it's almost 4am here. You continue thinking what you changed while trying to get WiFi working with ndiswrapper. Maybe someone else will notice something I missed while I'm asleep.

---

### Post by Lisiano on 2012-05-16
I really wasn't thinking straight huh...
To add persistence to the driver (Hell knows why it doesn't stick) is to run this command.
```
echo "b43" | sudo tee -a /etc/modules
```
Basically we put b43 into modules, except without the need to open up Gedit.

Oh and can you issue this
```
for i in *; do echo; echo ----------; echo $i; echo ----------; echo; cat $i; done > ~/modprobe.ls.result.txt
```
Then paste the content of a file named modprobe.ls.result.txt in your home directory using [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by royhenriksen on 2012-05-16
Hey, sorry i havent answered, been gone for some hours now. I just startet my computer and god news, everything works fine now. What you did seem to have worked (thank you so much):)

---

### Post by Lisiano on 2012-05-17
Well, as long as it works. Please mark the thread as solved if you have no questions.

---

