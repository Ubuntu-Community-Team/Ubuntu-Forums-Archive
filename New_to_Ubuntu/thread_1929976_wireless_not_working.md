---
title: "wireless not working"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by i8ajar on 2012-02-22
I just installed 10.04 and when I connect to internet so that I can get the driver (through system administration) to make my wireless work it says that there are no drivers for the hardware that I have.  I could use some help.

---

### Post by wildmanne39 on 2012-02-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by i8ajar on 2012-02-23
```
jared@jared-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux jared-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
jared@jared-laptop:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Kernel driver in use: r8169
	Kernel modules: r8169
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
jared@jared-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jared@jared-laptop:~$ rfkill list all
jared@jared-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
i2c_piix4               8335  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vga16fb                11385  1 
vgastate                8961  1 vga16fb
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169



```

---

### Post by wildmanne39 on 2012-02-23
Hi, please do:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
watch for errors, unplug wired connection and reboot.
Thanks

---

### Post by i8ajar on 2012-02-23
First off thanks for helping me.

second I still have no wireless.  The button on the keyboard will not turn on.

---

### Post by wildmanne39 on 2012-02-23
Hi, were you connected to the internet when you ran the commands? did you have errors while the commands ran?

Did you reboot after they were done?

Please post the output of:
```
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
```
Thanks

---

### Post by i8ajar on 2012-02-23
I was connected to the internet, (I'm not now on that computer).  There were no errors. and here is the output of the last command
```
[   11.050165] Console: switching to colour frame buffer device 80x30
```

---

### Post by i8ajar on 2012-02-23
Yes I did reboot.

---

### Post by wildmanne39 on 2012-02-23
Hi, the output should have looked something like this:
```
[   14.848509] Console: switching to colour frame buffer device 80x30
[   15.177242] Registered led device: b43-phy0::radio
[   15.290062] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   15.351149] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   15.355034] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   15.361677] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   15.500047] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   15.703553] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.232702] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[   44.232909] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[   44.236822] wlan0: direct probe responded
[   44.236829] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[   44.238370] wlan0: authenticated
[   44.238406] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[   44.241404] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=3)
[   44.241408] wlan0: associated
[   44.242769] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   55.230028] wlan0: no IPv6 routers present
[ 1874.600181] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[ 1881.344797] SMP alternatives: switching to UP code
[ 1881.351664] SMP alternatives: switching to SMP code
[ 1886.948693] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1887.221000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1893.850261] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[ 1894.060167] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[ 1894.063368] wlan0: direct probe responded
[ 1894.063381] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[ 1894.065629] wlan0: authenticated
[ 1894.065702] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[ 1894.068730] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=3)
[ 1894.068737] wlan0: associated
[ 1894.071225] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1904.550047] wlan0: no IPv6 routers present
[ 4240.933322] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[ 4242.520384] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[ 4242.523644] wlan0: direct probe responded
[ 4242.523659] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[ 4242.525217] wlan0: authenticated
[ 4242.525281] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[ 4242.528346] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[ 4242.528356] wlan0: associated
[ 7954.620170] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[ 7960.700029] SMP alternatives: switching to UP code
[ 7960.710185] SMP alternatives: switching to SMP code
[ 7965.930073] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7966.141805] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7972.850251] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[ 7973.040172] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[ 7973.043383] wlan0: direct probe responded
[ 7973.043397] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[ 7973.044877] wlan0: authenticated
[ 7973.044949] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[ 7973.047992] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[ 7973.047999] wlan0: associated
[ 7973.050540] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7983.780044] wlan0: no IPv6 routers present
[ 8031.730196] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[ 8032.235109] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[ 8032.420201] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[ 8032.423428] wlan0: direct probe responded
[ 8032.423442] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[ 8032.425616] wlan0: authenticated
[ 8032.425690] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[ 8032.428662] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[ 8032.428669] wlan0: associated
[22895.349156] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[22896.993036] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[22896.996275] wlan0: direct probe responded
[22896.996289] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[22896.997783] wlan0: authenticated
[22896.997838] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[22897.002262] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[22897.002272] wlan0: associated
[28624.750381] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[28626.402887] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[28626.600163] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 2)
[28626.603376] wlan0: direct probe responded
[28626.603387] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[28626.604892] wlan0: authenticated
[28626.604966] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[28626.608079] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[28626.608090] wlan0: associated
[38070.645072] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[38072.310385] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[38072.313627] wlan0: direct probe responded
[38072.313641] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[38072.315210] wlan0: authenticated
[38072.315283] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[38072.318315] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[38072.318325] wlan0: associated
[41774.213325] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[41775.860382] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[41775.864205] wlan0: direct probe responded
[41775.864219] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[41775.865711] wlan0: authenticated
[41775.865769] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[41775.869962] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[41775.869972] wlan0: associated
[42477.872695] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[42484.250052] SMP alternatives: switching to UP code
[42484.260234] SMP alternatives: switching to SMP code
[42489.550060] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[42489.751792] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[42496.420264] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[42496.612656] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[42496.615870] wlan0: direct probe responded
[42496.615884] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[42496.617371] wlan0: authenticated
[42496.617428] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[42496.620473] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=4)
[42496.620480] wlan0: associated
[42496.623075] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[42507.158033] wlan0: no IPv6 routers present
[42825.122683] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[42831.370056] SMP alternatives: switching to UP code
[42831.380217] SMP alternatives: switching to SMP code
[42836.812604] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[42837.026244] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[42843.692804] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[42843.881730] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[42843.884985] wlan0: direct probe responded
[42843.884999] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[42843.886949] wlan0: authenticated
[42843.887024] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[42843.890004] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=3)
[42843.890062] wlan0: associated
[42843.892539] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[42854.090053] wlan0: no IPv6 routers present
[46733.668069] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[46735.370320] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[46735.373561] wlan0: direct probe responded
[46735.373575] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[46735.375065] wlan0: authenticated
[46735.375141] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[46735.379057] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[46735.379067] wlan0: associated
[47960.842687] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[47967.160053] SMP alternatives: switching to UP code
[47967.170247] SMP alternatives: switching to SMP code
[47972.242567] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[47972.453338] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[47979.130282] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[47979.322303] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[47979.325692] wlan0: direct probe responded
[47979.325706] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[47979.327893] wlan0: authenticated
[47979.327969] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[47979.330990] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=3)
[47979.330996] wlan0: associated
[47979.333458] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[47989.520036] wlan0: no IPv6 routers present
[48804.466499] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[48806.110447] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[48806.113959] wlan0: direct probe responded
[48806.113972] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[48806.116421] wlan0: authenticated
[48806.116485] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[48806.123985] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[48806.123996] wlan0: associated
[52566.573834] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[52568.220536] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[52568.223776] wlan0: direct probe responded
[52568.223790] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[52568.225354] wlan0: authenticated
[52568.225426] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[52568.228449] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[52568.228460] wlan0: associated
[56362.438513] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[56364.100362] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[56364.103612] wlan0: direct probe responded
[56364.103626] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[56364.105132] wlan0: authenticated
[56364.105191] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[56364.108215] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[56364.108226] wlan0: associated
[58093.474631] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[58095.200394] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[58095.204080] wlan0: direct probe responded
[58095.204094] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[58095.205545] wlan0: authenticated
[58095.205612] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[58095.208738] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[58095.208749] wlan0: associated
[59705.200512] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[59705.202752] wlan0: direct probe responded
[59705.202766] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[59705.204254] wlan0: authenticated
[59705.204309] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[59705.209281] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=2)
[59705.209292] wlan0: associated
[61281.924000] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[61283.530418] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[61283.533408] wlan0: direct probe responded
[61283.533422] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[61283.534919] wlan0: authenticated
[61283.535007] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[61283.538027] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[61283.538038] wlan0: associated
[65264.950186] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[65271.154802] SMP alternatives: switching to UP code
[65271.161707] SMP alternatives: switching to SMP code
[65276.002561] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[65276.217846] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[65282.892749] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[65283.080187] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[65283.082410] wlan0: direct probe responded
[65283.082425] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[65283.084007] wlan0: authenticated
[65283.084076] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[65283.140816] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=3)
[65283.140825] wlan0: associated
[65283.143309] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[65293.740055] wlan0: no IPv6 routers present
[66579.643404] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[66581.290321] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[66581.293354] wlan0: direct probe responded
[66581.293368] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[66581.294853] wlan0: authenticated
[66581.294903] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[66581.297950] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[66581.297960] wlan0: associated
[67639.252691] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[67645.314787] SMP alternatives: switching to UP code
[67645.321772] SMP alternatives: switching to SMP code
[67650.210079] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[67650.451699] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[67657.092796] wlan0: deauthenticating from 00:24:7b:28:b0:3a by local choice (reason=3)
[67657.282651] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[67657.284828] wlan0: direct probe responded
[67657.284841] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[67657.286358] wlan0: authenticated
[67657.286432] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[67657.289393] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=3)
[67657.289399] wlan0: associated
[67657.291930] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[67667.570041] wlan0: no IPv6 routers present
[70859.703070] wlan0: deauthenticated from 00:24:7b:28:b0:3a (Reason: 1)
[70861.352583] wlan0: direct probe to AP 00:24:7b:28:b0:3a (try 1)
[70861.354838] wlan0: direct probe responded
[70861.354853] wlan0: authenticate with AP 00:24:7b:28:b0:3a (try 1)
[70861.356362] wlan0: authenticated
[70861.356431] wlan0: associate with AP 00:24:7b:28:b0:3a (try 1)
[70861.359462] wlan0: RX AssocResp from 00:24:7b:28:b0:3a (capab=0x411 status=0 aid=1)
[70861.359473] wlan0: associated
larry@ubuntu:~$ 

```
please reboot and if the wireless does not come on run:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
again then disconnect wire connection and reboot because something did not go right.
Thanks

---

### Post by i8ajar on 2012-02-24
I did the last commands that you suggested and it now works.  It did do some different thing this time than last time, but this is posted via wireless.  

Thank you for your help.

---

### Post by wildmanne39 on 2012-02-25
Hi, your welcome! Glad I could help.
Enjoy

---

