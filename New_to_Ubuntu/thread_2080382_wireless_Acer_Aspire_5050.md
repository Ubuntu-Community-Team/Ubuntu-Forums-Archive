---
title: "wireless Acer Aspire 5050"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by Ggubunted on 2012-11-03
Hi!

My use linux operating systems is fairly recent but for now, I'm quite happy. For this reason, I need help trying to resolve this situation: First I installed Mint Xfce 13 but did not start (someone can tell me why. I made several boot changes and nothing. Anyway...). After I installed Lubuntu 12.04 LXDE on a laptop Acer Aspire 5050 (or 5051awxmi, I could never understand exactly what would be) and seems to work very well. However, the hardware of wireless (Broadcom b4318 or RealTek RTL-8139C + series 10/100 PCI Ethernet driver, do not know which is. But too i do not know confirm which is.) Does not work. I've tried to do some things that I found on the internet but nothing gives. Can you help me? Explain to me step by step on the console, please, because I'm very new at this... It is urgent...

Hug

---

### Post by overdrank on 2012-11-03
Hi and welcome. Moved and bumped to Absolute Beginners Section

---

### Post by Paari on 2012-11-04
hi... try the code below. It should install the corresponding broadcom driver...
```

sudo apt-get install firmware-b43-installer 

```

---

### Post by Ggubunted on 2012-11-04
Thank you.

I had already done that but it did not work.

---

### Post by Ggubunted on 2012-11-04
Help!!!

I'm desperate with this error...

---

### Post by NikTh on 2012-11-04
Hi and Welcome. 

Please post the results of bellow commands 

```
lsb_release -rcd ; uname -r 
lspci -nnk | grep -iA2 net 
dmesg | grep -ie net -ie wlan -ie firm
nmcli nm status 
lsmod
rfkill list all
```

You can copy-paste above commands one at time in your terminal and vise versa (for the results) here to forum. 

Please put the results between these brackets [noparse]```
the results here
```[/noparse] to be easier to read. 

Thanks

---

### Post by Ggubunted on 2012-11-04
Between [...] it is the command that you suggested and after this the result of that command.

[lsb_release -rcd ; uname -r] 
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
3.5.0-17-generic

[lspci -nnk | grep -iA2 net]
08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:010f]
	Kernel driver in use: 8139too
--
08:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
	Kernel modules: ssb

[dmesg | grep -ie net -ie wlan -ie firm]
[    0.084004] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.084004] NET: Registered protocol family 16
[    0.123263] NetLabel: Initializing
[    0.123266] NetLabel:  domain hash size = 128
[    0.123267] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.123280] NetLabel:  unlabeled traffic allowed by default
[    0.140956] NET: Registered protocol family 2
[    0.143216] NET: Registered protocol family 1
[    0.252916] audit: initializing netlink socket (disabled)
[    0.493356] NET: Registered protocol family 10
[    0.493598] NET: Registered protocol family 17
[    0.907878] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.533010] 8139too: 8139too Fast Ethernet driver 0.9.28
[   12.248107] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.194373] type=1400 audit(1352038302.016:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=553 comm="apparmor_parser"
[   13.412173] NET: Registered protocol family 31
[   13.424971] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.113987] type=1400 audit(1352038302.936:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=795 comm="apparmor_parser"
[   14.284334] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.284671] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.870468] [Firmware Bug]: battery: (dis)charge rate invalid.
[   79.369862] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2169.868220] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2173.815454] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

[nmcli nm status]
EXECUÇÃO        ESTADO          DISPOSITIVO-WIFI WIFI       DISPOSITIVO-WWAN WWAN      
em execução     ligado          activo          activo     activo          desactivado

[lsmod]
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39842  1 
joydev                 17457  0 
acer_wmi               32453  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_codec_realtek    77876  1 
video                  19335  1 acer_wmi
snd_hda_intel          33491  1 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
parport_pc             32688  0 
snd_seq_midi           13324  0 
ppdev                  17073  0 
rfcomm                 46619  0 
snd_rawmidi            30512  1 snd_seq_midi
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
snd_seq_midi_event     14899  1 snd_seq_midi
kvm_amd                55604  0 
pcmcia                 48964  0 
kvm                   414070  1 kvm_amd
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17500  1 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           31817  0 
pcmcia_rsrc            18288  1 yenta_socket
snd                    78734  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                95552  0 
soundcore              15047  1 snd
edac_core              52451  0 
k8temp                 12978  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
radeon                895653  2 
serio_raw              13215  0 
edac_mce_amd           23303  0 
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13413  1 radeon
wmi                    19070  1 acer_wmi
mac_hid                13205  0 
i2c_piix4              13167  0 
shpchp                 37108  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
8139too                31917  0 
8139cp                 27234  0 
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
pata_atiixp            13204  3 
sata_sil               13501  0 

[rfkill list all]
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


Thank you...

---

### Post by NikTh on 2012-11-04
Hi , 

try this from terminal (execute bellow commands with order) (Active Internet connection required)

```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
echo 'b43' | sudo tee -a /etc/modules
```Reboot your PC and remove the Ethernet Cable. See if wireless works. 

Or else give the results of below commands 

```
lsmod
ifconfig 
iwlist scanning 
dmesg | grep -ie b43 -ie firm -ie net
```When I said "Put the results between the brackets" 
I mean to put the results between these brackets ==> [noparse]```
the results here
```[/noparse] <=== so the results displayed ```
Here
```
OR
you can click the "New Reply" and highlight the results and click this symbol **#** at the message toolbar. 

Thanks

---

### Post by Ggubunted on 2012-11-04
I apologize. I did not realize it was a tool in the new message.
My English is poor. Sorry...

Finally, it works.

Thank you for the precious help.

Big hug

---

