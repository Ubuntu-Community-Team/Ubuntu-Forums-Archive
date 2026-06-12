---
title: "VAIO VGN wired and wireless not working"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by LinuxNiuB on 2012-06-01
I am new to Linux and have installed Ubuntu 12.04, then Mint 12, to check if the wired and wireless connections could work.  In this process I have been learning how to use Linux.  I will mention the Wireless issue only for now.  I have tried a few things and I think I have discovered that:


[LIST=1]
[*]iwlagn has the wrong driver for my wireless card:
[/LIST]
```
lspci -nn
```
 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03) 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) 00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02) 00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) 00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) 00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) 00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02) 00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) 00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) 00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) 00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) 00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02) 00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) 00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) 00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02) 02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 16) 06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [**8086:4222**] (rev 02) 0a:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039] 0a:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a] 0a:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

```
modinfo iwlagn
```
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko license:        GPL author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com> version:        in-tree: description:    Intel(R) Wireless WiFi Link AGN driver for Linux firmware:       iwlwifi-5150-2.ucode firmware:       iwlwifi-5000-5.ucode firmware:       iwlwifi-6000g2b-5.ucode firmware:       iwlwifi-6000g2a-5.ucode firmware:       iwlwifi-6050-5.ucode firmware:       iwlwifi-6000-4.ucode firmware:       iwlwifi-100-5.ucode firmware:       iwlwifi-1000-5.ucode firmware:       iwlwifi-105-5.ucode firmware:       iwlwifi-2030-5.ucode firmware:       iwlwifi-2000-5.ucode srcversion:     F1AF2D897D96C14B77FE0BA alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i* alias:          pci:v00008086d00000893sv*sd00000266bc*sc*i* alias:          pci:v00008086d00000892sv*sd00000066bc*sc*i* alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i* alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i* alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i* alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i* alias:          pci:v00008086d00000895sv*sd00000226bc*sc*i* alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i* alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i* alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i* alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004466bc*sc*i* alias:          pci:v00008086d0000088Fsv*sd00004266bc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004066bc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004464bc*sc*i* alias:          pci:v00008086d0000088Fsv*sd00004264bc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004064bc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i* alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i* alias:          pci:v00008086d00000887sv*sd00004466bc*sc*i* alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i* alias:          pci:v00008086d00000887sv*sd00004066bc*sc*i* alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i* alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i* alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i* alias:          pci:v00008086d00000890sv*sd00004426bc*sc*i* alias:          pci:v00008086d00000891sv*sd00004226bc*sc*i* alias:          pci:v00008086d00000890sv*sd00004026bc*sc*i* alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i* alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i* alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i* alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i* alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i* alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i* alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i* alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i* alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i* alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i* alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i* alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i* alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i* alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i* alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i* alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i* alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i* alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i* alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i* alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i* alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i* alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i* alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i* alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i* alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i* alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i* depends:        mac80211,cfg80211 vermagic:       3.0.0-12-generic SMP mod_unload modversions 686  parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int) parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (bool) parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool) parm:           swcrypto:using crypto in software (default 0 [hardware]) (int) parm:           queues_num:number of hw queues. (int) parm:           11n_disable:disable 11n functionality (int) parm:           amsdu_size_8K:enable 8K amsdu size (int) parm:           fw_restart:restart firmware in case of error (int) parm:           ucode_alternative:specify ucode alternative to use from ucode file (int) parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int) parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool) parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool) parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)

Thank you in advance for any help provided.

---

### Post by linuxman94 on 2012-06-01
Can you please surround the output in code tags (# sign in the full editor)? It makes it much easier to read.  

Also, please paste the output of these commands.

```
iwconfig
lsmod
uname -a

```

---

### Post by LinuxNiuB on 2012-06-01
iwconfig
```
lo        no wireless extensions.  eth0      no wireless extensions.  wlan0     IEEE 802.11abg  ESSID:off/any             Mode:Managed  Access Point: Not-Associated   Tx-Power=12 dBm              Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:off
```

lsmod
```
Module                  Size  Used by snd_atiixp_modem       18604  0  snd_via82xx_modem      18377  0  snd_intel8x0m          18498  0  snd_ac97_codec        106082  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m ac97_bus               12642  1 snd_ac97_codec nls_iso8859_1          12617  0  nls_cp437              12751  0  vfat                   17308  0  fat                    55577  1 vfat iwlagn                273944  0  bnep                   17923  2  rfcomm                 38408  12  parport_pc             32114  0  ppdev                  12849  0  dm_crypt               22565  0  joydev                 17393  0  pcmcia                 39822  0  arc4                   12473  2  iwl3945                73329  0  iwl_legacy             71499  1 iwl3945 snd_hda_codec_realtek   254125  1  tifm_7xx1              12937  0  btusb                  18160  2  tifm_core              15040  1 tifm_7xx1 psmouse                73673  0  mac80211              272785  3 iwlagn,iwl3945,iwl_legacy bluetooth             148839  23 bnep,rfcomm,btusb serio_raw              12990  0  yenta_socket           27428  0  pcmcia_rsrc            18367  1 yenta_socket pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc cfg80211              172392  4 iwlagn,iwl3945,iwl_legacy,mac80211 snd_hda_intel          24262  2  snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel snd_hwdep              13276  1 snd_hda_codec snd_pcm                80468  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec sony_laptop            39681  0  snd_seq_midi           13132  0  snd_rawmidi            25241  1 snd_seq_midi snd_seq_midi_event     14475  1 snd_seq_midi snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event snd_timer              28932  2 snd_pcm,snd_seq snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq snd                    55902  17 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device soundcore              12600  1 snd snd_page_alloc         14115  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm lp                     17455  0  parport                40930  3 parport_pc,ppdev,lp i915                  505108  3  firewire_ohci          35854  0  firewire_core          56937  1 firewire_ohci usb_storage            44173  0  uas                    17699  0  crc_itu_t              12627  1 firewire_core drm_kms_helper         32889  1 i915 drm                   192226  4 i915,drm_kms_helper sky2                   49317  0  i2c_algo_bit           13199  1 i915 video                  18908  1 i915
```

uname -a
```
Linux phi-VGN-C21CH-L 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by coffeecat on 2012-06-02
@LinuxNiuB, all the line breaks have disappeared from your terminal output and even with code tags it is completely unreadable. Are you using a Windows-based text editor in order to post the outputs? Windows and Linux text editors manage new lines differently and Notepad will do this to text files saved in Ubuntu.

If a Windows text editor is the problem, try this with linuxman94's commands:

```
iwconfig > Desktop/iwconfig.txt
lsmod > Desktop/lsmod.txt
uname -a > Desktop/uname.txt
```

Three *txt files will appear on your desktop. Transfer them to your Windows system if you are using Windows to post and then add them as attachments to your next post with the "Manage Attachments" button you will find under the message field.

Alternatively, if you are using Windows to post your outputs, try Wordpad instead of Notepad. Check to see that your text files still appear with line breaks. I'm not 100% sure but I seem to remember that it doesn't garble text files produced in Ubuntu the way Notepad does.

---

### Post by LinuxNiuB on 2012-06-02
Really sorry about this, thank you for the patience.

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```[FONT=monospace]

[/FONT]lsmod
```
Module                  Size  Used by
snd_atiixp_modem       18604  0 
snd_via82xx_modem      18377  0 
snd_intel8x0m          18498  0 
snd_ac97_codec        106082  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
iwlagn                273944  0 
bnep                   17923  2 
rfcomm                 38408  12 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
joydev                 17393  0 
pcmcia                 39822  0 
arc4                   12473  2 
iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
snd_hda_codec_realtek   254125  1 
tifm_7xx1              12937  0 
btusb                  18160  2 
tifm_core              15040  1 tifm_7xx1
psmouse                73673  0 
mac80211              272785  3 iwlagn,iwl3945,iwl_legacy
bluetooth             148839  23 bnep,rfcomm,btusb
serio_raw              12990  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
cfg80211              172392  4 iwlagn,iwl3945,iwl_legacy,mac80211
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec
sony_laptop            39681  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  505108  3 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
usb_storage            44173  0 
uas                    17699  0 
crc_itu_t              12627  1 firewire_core
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
sky2                   49317  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

```
uname -a
```
Linux phi-VGN-C21CH-L 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by linuxman94 on 2012-06-02
From the output, the module is loaded and the card appears to be functioning. 
What specific of problem are you having with the network?

---

### Post by LinuxNiuB on 2012-06-02
(Both) Wireless (and Wired) network(s) does not connect.  It is able to scan for connections but it is not able to connect.  This Vaio VGN-C21CH has a switch that is on but the WLAN logo does not lit only the Bluetooth symbol lights up.  I booted the Live-CD on another computer, a Dell, and it worked right away.  Thank you for your help and patience, once again.

---

### Post by linuxman94 on 2012-06-04
Ok, can you post what this command gives?

```
rfkill list all
```

---

### Post by LinuxNiuB on 2012-06-04
```
$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
9: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by LinuxNiuB on 2012-06-07
:confused: Any other possibilities?

---

### Post by wildmanne39 on 2012-06-10
Hi, sorry it has taken me so long to reply but I am out of town and only have internet access today.

Please copy and past all commands for accuracy:
```
echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Then:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```

Add one line:

```
options iwl3945 11n_disable=1
```

Proofread carefully, save and close gedit. Reboot.

---

### Post by LinuxNiuB on 2012-06-11
```
$ echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password: 
blacklist iwlagn
``````
$ gksudo gedit /etc/modprobe.d/iwl3945.conf
``````
$ options iwl3945 11n_disable=1
options: command not found
```Really appreciate the help since it is a big step in moving to Linux.

---

### Post by wildmanne39 on 2012-06-11
Hi, after you enter this:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
type your password in the small window that opens, then another window should open and paste this into it:
```
options iwl3945 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot.

---

### Post by LinuxNiuB on 2012-06-11
Sorry, nothing opened and upon reboot it is prompting me for a username and password which I type mine and tries to load what were maybe my settings then goes back to asking username and password again. I hope this does not take me from my route.

Maybe it was this code that I typed:

```
sudo apt-get remove --purge ndis*
```from this post:

[http://ubuntuforums.org/showthread.php?t=1806410&page=3](http://ubuntuforums.org/showthread.php?t=1806410&page=3)

---

### Post by wildmanne39 on 2012-06-11
Hi, this $ is not part of the command, did you have it in front of the command as it shows in your post? 

I believe that is the problem with the window not opening but it should not have effected the username and password.

Just copy and paste the commands for accuracy as I suggested in post 11.

Also  when you blacklisted the driver in post 11 make sure that sign was not in front of the command please.
Thanks

---

### Post by LinuxNiuB on 2012-06-11
The $ was from the Terminal, I did not include it and it was followed exactly as prescribed.

---

### Post by LinuxNiuB on 2012-06-13
I am able to login again.  I typed this

```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```and it tries to load something but it doesn't appear.

---

### Post by wildmanne39 on 2012-06-13
Hi, are you running ubuntu or maybe lubuntu or something different?

If gedit is not installed try this:
```
sudo apt-get install gedit
```
Thanks

---

### Post by LinuxNiuB on 2012-06-13
I have Linux Mint 12 (lisa).  (I don't have Wired internet either but I have learned to get files through USB.)

I installed gedit and followed your instructions:

[LIST]
[*]In the internet connections the Wireless connections don't come up like they use to.
[*]The Wireless option is not present.
[/LIST]
Thanks again for your help.

---

### Post by wildmanne39 on 2012-06-13
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
Thanks

---

### Post by LinuxNiuB on 2012-06-13
```
alpha@alpha-VGN-C21CH-L ~ $ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:13:A9:A6:75:03

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


alpha@alpha-VGN-C21CH-L ~ $ sudo iwlist scan
[sudo] password for alpha: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

alpha@alpha-VGN-C21CH-L ~ $ cat /etc/resolv.conf
# Generated by NetworkManager
alpha@alpha-VGN-C21CH-L ~ $ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
alpha@alpha-VGN-C21CH-L ~ $ lsmod | grep iwl
iwl_legacy             71499  0 
mac80211              272785  1 iwl_legacy
cfg80211              172392  2 iwl_legacy,mac80211
``````
alpha@alpha-VGN-C21CH-L ~ $ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
[sudo] password for alpha: 
Jun 13 09:21:38 alpha-VGN-C21CH-L kernel: [   29.085398] iwl3945: Unknown parameter `11n_disable'
Jun 13 09:21:39 alpha-VGN-C21CH-L NetworkManager[685]: <info> monitoring kernel firmware directory '/lib/firmware'.
``````
gksudo gedit /etc/modprobe.d/iwl3945.conf
```This last one opened gedit

---

### Post by wildmanne39 on 2012-06-13
Hi, I need to know what is in this file, it looks incorrect:
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
is it:
```
options iwl3945 11n_disable=1
```
if not paste it in there and remove what is there then save and close gedit.

I also am wondering if you are missing other applications and dependencies since you used the purge ndis command from the other thread, I know in ubuntu it removes the ubuntu desktop and it has to be reinstalled.
Thanks

---

### Post by LinuxNiuB on 2012-06-13
:idea: I am continuing to read on this matter, ultimately to learn more about Linux.  I found some information from about two years ago that mentioned the using > wicd instead of the > network manager.  Though not sure how relevant it would be.

[http://ihaveapc.com/2010/07/how-to-fix-wi-fi-reconnection-problem-in-linux-mint/](http://ihaveapc.com/2010/07/how-to-fix-wi-fi-reconnection-problem-in-linux-mint/)

---

### Post by wildmanne39 on 2012-06-13
Hi, it may be something we need to do later but for now that is not the issue, please post the contents of that file from my previous post in gedit.

Is this > Jun 13 09:21:38 alpha-VGN-C21CH-L kernel: [   29.085398] iwl3945: Unknown parameter `11n_disable'
Jun 13 09:21:39 alpha-VGN-C21CH-L NetworkManager[685]: <info> monitoring kernel firmware directory '/lib/firmware'.
all the output from:
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```

---

### Post by LinuxNiuB on 2012-06-13
Concerning the purging, I reinstalled Linux which is back to exactly how we started out in the beginning.

```
alpha@alpha-VGN-C21CH-L ~ $ gksudo gedit /etc/modprobe.d/iwl3945.conf

(gedit:2713): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HH73FW': No such file or directory

(gedit:2713): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2713): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.1V4ZFW': No such file or directory

(gedit:2713): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2713): Gtk-WARNING **: Unable to retrieve the file info for `file:///home/alpha/Desktop/iwl3945.conf': Error stating file '/home/alpha/Desktop/iwl3945.conf': No such file or directory

(gedit:2713): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.4BROFW': No such file or directory

(gedit:2713): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2713): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.P9OYFW': No such file or directory

(gedit:2713): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
alpha@alpha-VGN-C21CH-L ~ $
```The attachment will show you what loads up with```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```and what follows is when I close gedit.  Please note that there's a iwl3945.conf tab in gedit and a blank one that loads up also.

---

### Post by LinuxNiuB on 2012-06-13
Yes, this is all from ```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```

---

### Post by wildmanne39 on 2012-06-13
Hi, whenever you do something please let me know because it puts us back to square one.

Remove:
```
options iwl3945 11n_disable=1
```
make sure to save it then reboot and post the output from the commands in post 20.
Thanks

---

### Post by LinuxNiuB on 2012-06-13
Removed and rebooted.```
alpha@alpha-VGN-C21CH-L ~ $ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:13:A9:A6:75:03

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:18:DE:DA:8D:A1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    calvarin-guest:  Infra, 58:6D:8F:4D:D3:FF, Freq 2412 MHz, Rate 54 Mb/s, Strength 17
    2WIRE517:        Infra, 3C:EA:4F:3C:1B:51, Freq 2447 MHz, Rate 54 Mb/s, Strength 17 WEP
    2WIRE969:        Infra, 00:1D:5A:66:0E:29, Freq 2427 MHz, Rate 54 Mb/s, Strength 19 WEP
    CottonBalls:     Infra, 74:44:01:71:09:0E, Freq 2417 MHz, Rate 54 Mb/s, Strength 15 WPA2
    Wireless_N:      Infra, C8:3A:35:44:60:B0, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    NETGEAR:         Infra, E0:46:9A:42:EE:3D, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WEP                         
    Connectify-me:   Ad-Hoc, 22:06:F8:82:44:55, Freq 2462 MHz, Rate 11 Mb/s, Strength 100 WEP                       
    calvarin:        Infra, 58:6D:8F:4D:D3:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2                    
    dlink3258:       Infra, 00:26:5A:FB:AB:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA                         
    monkeyTorture:   Infra, 00:1A:70:DD:2D:28, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2                        
    Sparky:          Infra, 00:0D:93:EC:DA:E4, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ATT592:          Infra, 1C:14:48:10:A7:40, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2


alpha@alpha-VGN-C21CH-L ~ $ sudo iwlist scan
[sudo] password for alpha: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

alpha@alpha-VGN-C21CH-L ~ $ cat /etc/resolv.conf
# Generated by NetworkManager
alpha@alpha-VGN-C21CH-L ~ $ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
alpha@alpha-VGN-C21CH-L ~ $ lsmod | grep iwl
iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
``````
alpha@alpha-VGN-C21CH-L ~ $ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
[sudo] password for alpha: 
Jun 13 09:21:38 alpha-VGN-C21CH-L kernel: [   29.085398] iwl3945: Unknown parameter `11n_disable'
Jun 13 09:21:39 alpha-VGN-C21CH-L NetworkManager[685]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.471203] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.471207] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.471291] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.471307] iwl3945 0000:06:00.0: setting latency timer to 64
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.532612] iwl3945 0000:06:00.0: Tunable channels: 13 802.11bg, 4 802.11a channels
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.532618] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.532778] iwl3945 0000:06:00.0: irq 45 for MSI/MSI-X
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   29.571377] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlan0, iface: wlan0)
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): now managed
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): bringing up device.
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   30.416384] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): preparing device.
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 13 11:21:50 alpha-VGN-C21CH-L kernel: [   30.486381] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 13 11:21:50 alpha-VGN-C21CH-L dbus[645]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jun 13 11:21:50 alpha-VGN-C21CH-L dbus[645]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> wpa_supplicant started
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]                                                                      
Jun 13 11:21:50 alpha-VGN-C21CH-L NetworkManager[713]: <info> (wlan0): supplicant interface state: ready -> inactive

``````
alpha@alpha-VGN-C21CH-L ~ $ gksudo gedit /etc/modprobe.d/iwl3945.conf                                               
                                                                                                                    
(gedit:2248): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BEOWFW': No such file or directory

(gedit:2248): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```For the last code, gedit was blank.  Thanks!

---

### Post by wildmanne39 on 2012-06-13
Hi, the device is detecting networks now.

Is this Connectify-me the network you are trying to connect too? if so please remove the dash and change ad-hoc to infrastructure in network settings in network manager.

Also you should try just wpa2 for encryption in your router it works better for linux, router can usually be accessed by entering 192.168.0.1 into your web browser while connected to it by a wire.
Thanks

---

### Post by LinuxNiuB on 2012-06-13
I have a Windows 7 computer connected to the non-wireless modem which gives wireless internet through an ad-hoc set-up to an iPod (was not able to get wpa2 to work) and Linux computer.

Connectify-me is the network I am trying to connect.  It's a program I installed and it won't let me delete the dash. Can Linux still recognize it with the dash?

---

### Post by wildmanne39 on 2012-06-13
Hi, okay but did you change ad-hoc to infrastructure in ubuntu? if you want it to connect wirelessly you will need too.

Ad-hoc can be use with different software if you want to use the laptop as an access point but you need to get wireless working first, and then I can give you a link for that but I have no experience in that area.
Thanks

---

### Post by LinuxNiuB on 2012-06-13
Wireless works now!! and also the wired! How did you do it? I am not sure what you did? Did you black list something? Also, can I put it is solved or is there something else I should look into?  Thank you so much!!:KS

---

### Post by wildmanne39 on 2012-06-13
Hi, it was several things.

First you had two drivers so we got rid of one.

Second I hope you changed ad-hoc to infratructure.

Third took the dash out of your network name.

Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

