---
title: "Broadcom driver not loading"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by Inisfad on 2012-02-25
Anyway feel like taking on this beaten up issue again? My friend's  computer is running Lucid, and he is trying to activate broadband.   Regrettably the card is Broadcom.  I had a similar issue with my  computer, it took me days to get it running, and frankly, I don't  remember what I did, installed, uninstalled, reinstalled, etc. to get  this working.  I hope that I can get some help here.  Newbie, as you  will soon notice.

lspci:
#
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
#
lsmod:
#
Module                  Size  Used by
b44                    25574  0 
ssb                    38934  1 b44
mii                     4381  1 b44
wl                   1959598  0 
lib80211                5046  1 wl
ppp_deflate             3682  0 
zlib_deflate           19568  1 ppp_deflate
bsd_comp                4811  0 
ppp_async               6734  1 
crc_ccitt               1339  1 ppp_async
isofs                  29250  1 
option                 20198  1 
usbserial              33694  4 option
usb_storage            39905  1 
binfmt_misc             6587  1 
ipt_REJECT              1928  1 
ipt_LOG                 4542  4 
xt_multiport            2378  1 
xt_limit                1382  6 
xt_tcpudp               2011  9 
ipt_addrtype            1599  4 
xt_state                1098  9 
dm_crypt               11331  0 
snd_hda_codec_analog    58598  1 
ip6table_filter         1248  1 
snd_hda_intel          22069  2 
ip6_tables             11102  1 ip6table_filter
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
nf_nat_irc              1124  0 
snd_hwdep               5412  1 snd_hda_codec
nf_conntrack_irc        3332  1 nf_nat_irc
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
nf_nat_ftp              1836  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            26722  0 
nf_conntrack_ipv4      10346  11 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi            4557  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_rawmidi            19056  1 snd_seq_midi
nf_conntrack           60975  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ndiswrapper           184677  0 
ip_tables               9899  1 iptable_filter
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               5470  0 
x_tables               14175  9 ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
pcmcia                 30784  0 
sdhci                  15494  1 sdhci_pci
tifm_7xx1               3690  0 
joydev                  8740  0 
tifm_core               6045  1 tifm_7xx1
tpm_infineon            7745  0 
snd                    54244  17  snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                 7488  0 
yenta_socket           20408  1 
ppdev                   5259  0 
soundcore               6620  1 snd
rsrc_nonstatic         10015  1 yenta_socket
parport_pc             25962  1 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               2864  1 sdhci
lp                      7028  0 
psmouse                63677  0 
tpm                    13936  2 tpm_infineon,tpm_tis
tpm_bios                5266  1 tpm
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
shpchp                 28835  0 
serio_raw               3978  0 
k8temp                  3152  0 
i2c_piix4               8335  0 
parport                32635  3 ppdev,parport_pc,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
radeon                678735  3 
ttm                    49847  1 radeon
drm_kms_helper         29329  1 radeon
ohci1394               26950  0 
drm                   163651  5 radeon,ttm,drm_kms_helper
ati_agp                 5094  0 
ieee1394               81181  1 ohci1394
tg3                   109324  0 
sata_sil                6959  2 
pata_atiixp             3148  0 
i2c_algo_bit            5028  1 radeon
video                  17375  0 
agpgart                31724  3 ttm,drm,ati_agp
output                  1871  1 video
ramzswap                6362  1 
xvmalloc                4074  1 ramzswap
lzo_decompress          2189  1 ramzswap
lzo_compress            1853  1 ramzswap
#
rfkill list all does nothing but bring me back to prompt

modprobe wl:
#WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
#

bcm-kernel-source, broadcom-sta-common, broadcom-sta-source,  b43-fwcutter and bcmwl-modialiases are installed in synaptic.  I do not  have the b43 installer that I have read about.
Hardware driver finds only finds the Broadcom STA driver but will not activate it.


I would appreciate any help anyone can give me here.  My head is pounding.  Thanks!

---

### Post by Inisfad on 2012-02-25
A bit more info:

Also iwconfig:
#
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.
#

I cannot get the wifi light to go on, on the computer (HP compaq nx6325).  Last night, doing some (forgotten) command, I was able to get the light to blink for a second.

---

### Post by Inisfad on 2012-02-25
I also wouldn't mind if someone explained to me how to get my pasted information into the gray boxes that I see on the forum.  Thanks.

output for cat /etc/modprobe.d/blacklist.conf
#
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
#

---

### Post by Inisfad on 2012-02-25
I keep going on to other blogs about this, and getting more info.  Hopefully some of this is helpful:

ls /etc/modprobe.d:
#
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
blacklist               blacklist-framebuffer.conf  broadcom-sta-common.conf
blacklist-ath_pci.conf  blacklist-modem.conf        libpisock9.conf
blacklist-bcm43.conf    blacklist-oss.conf          ndiswrapper
blacklist.conf          blacklist-vmc.conf
#

cat /etc/modules:
#
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
ndiswrapper
lp
lp
#

---

### Post by Megaptera on 2012-02-25
What's the make & model of your friend's machine? My Dell laptop has Broadcom and it's just a simple 'install driver' from option given next to wireless icon, re-boot and sorted.

Just wondered ...

---

### Post by Inisfad on 2012-02-25
Its a HP compaq nx6325.  I have a Dell, and it took me about 3 weeks of installing, uninstalling to get my Broadcom card to work.  You were really lucky - there are 1,000's of pages (and 1,000's of alternative instructions, codes, etc.) on the internet trying to get the Broadcom to work.

---

### Post by Inisfad on 2012-02-25
Output for lspci -vnn
#30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 1361
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c4000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ndiswrapper
    Kernel modules: ssb
#

I give up......ndiswrapper is not installed.

---

### Post by gordintoronto on 2012-02-25
> **Inisfad said:**
> Anyway feel like taking on this beaten up issue again? My friend's  computer is running Lucid...

lspci:
#
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)


Why Lucid? I think the BCM4312 will work out-of-the-box with the latest Ubuntu. If you are prejudiced against that, try Kubuntu or Mint.

---

### Post by 3rdalbum on 2012-02-25
> **gordintoronto said:**
> Why Lucid? I think the BCM4312 will work out-of-the-box with the latest Ubuntu. If you are prejudiced against that, try Kubuntu or Mint.

I agree. Using such an old version is simply an invitation to tolerate MORE pain.

Broadcom devices should be as simple as:

1. Get an internet connection (through mobile broadband, Ethernet cable to your router, phone tethering etc)

2. Refresh your package list (sudo apt-get update, or press Check in Update Manager)

3. Open the Additional Drivers program and click Activate.

4. Reboot and you should be able to get wireless.

However, if Ubuntu 10.04 predates the wireless card, that won't work.

In short, try Ubuntu 11.10, and if the wireless doesn't work out-of-the-box then try Additional Drivers.

---

### Post by Inisfad on 2012-02-26
My adventure is over, but not without some pretty ugly complications.  I upgraded to 11.10.  Wifi work out of the box? No.  Modem work out of the box? Not that, either.  My USB dongle worked with the Live CD, worked at my first boot on to the installed version.  I then enabled the wireless driver for the Broadcom 4312 card, that was 'out of the box'.  Result?  My USB dongle disappeared from network manager, and did not come back at reboot, or re-installation.  Back on to the internet to go through the myriad of posts to find the problem.  Finally found instructions for a code:
suco nmcli nm wwan on
which I ran, rebooted and my dongle was back.  I then removed the Broadcom STA driver (which is the 'out of the box version', and installed  b43-fwcutter and firmware-b43-installer (a result of 2 days previous 'study').  Even though most sites advise that as of 11.04 it is the Broadcom STA driver that should be used, apparently it isn't.  After the installation of the above two files, my physical wifi button worked, and I now have the option of either wifi or the dongle.  End of adventure!!

---

### Post by Inisfad on 2012-02-26
Now I just have to learn how to mark this post as solved......

---

### Post by BlinkinCat on 2012-02-26
> **Inisfad said:**
> Now I just have to learn how to mark this post as solved......

Hi,

In the thread tools box at top of page you can mark as "solved" - :)

---

### Post by Megaptera on 2012-02-27
Glad to read that you solved it & thanks for posting the solution, that will no doubt help others.

---

