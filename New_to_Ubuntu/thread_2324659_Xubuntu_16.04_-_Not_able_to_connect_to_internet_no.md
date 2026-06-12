---
title: "Xubuntu 16.04 - Not able to connect to internet not even in live cd mode"
date: 2016-05-15
forum: New to Ubuntu
---

### Post by konsolelover on 2016-05-15
Hello All,

I have installed Xubuntu 16.04 on my new HP AC026TX Laptop alongside Windows 8.1 but I am not able to connect to internet. Even in "try Xubuntu" mode it didn't work. I can create a DSL connection but it fails to connect to internet. I also tried Ubuntu 16.04 in live cd mode but it gave me the same result. Same DSL connection is working fine in Windows 8.1 . Please not that this DSL connection does not require any router or modem.

Here is output of some commands, 

```
lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80c2]
    Kernel driver in use: r8169
    Kernel modules: r8169
--
13:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Kernel driver in use: bcma-pci-bridge



```

```
lsmod
Module                  Size  Used by
rfcomm                 69632  12
pppoe                  20480  0
pppox                  16384  1 pppoe
bnep                   20480  2
uvcvideo               90112  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  37 bnep,btbcm,btrtl,btusb,rfcomm,btintel
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
intel_rapl             20480  0
videobuf2_v4l2         28672  1 uvcvideo
x86_pkg_temp_thermal    16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
intel_powerclamp       16384  0
coretemp               16384  0
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
snd_hda_codec_hdmi     53248  1
kvm                   536576  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  0
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_ssm4567        16384  0
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_hda_codec_realtek    81920  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
bcma                   53248  0
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
joydev                 20480  0
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
input_leds             16384  0
snd_hwdep              16384  1 snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
serio_raw              16384  0
intel_pch_thermal      16384  0
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
mei_me                 36864  0
mei                    98304  1 mei_me
int3403_thermal        16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
snd_soc_sst_acpi       16384  0
hp_wireless            16384  0
soundcore              16384  1 snd
shpchp                 36864  0
spi_pxa2xx_platform    24576  0
i2c_designware_platform    16384  0
8250_dw                16384  0
i2c_designware_core    20480  1 i2c_designware_platform
int3402_thermal        16384  0
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
acpi_pad               20480  0
processor_thermal_device    16384  0
int340x_thermal_zone    16384  3 int3402_thermal,processor_thermal_device,int3403_thermal
lpc_ich                24576  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd
radeon               1511424  1
i915                 1208320  4
ttm                    98304  1 radeon
i2c_algo_bit           16384  2 i915,radeon
drm_kms_helper        139264  2 i915,radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
psmouse               126976  0
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
drm                   360448  8 ttm,i915,drm_kms_helper,radeon
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    20480  1 hp_wmi
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
sdhci_acpi             16384  0
video                  40960  1 i915
sdhci                  45056  1 sdhci_acpi
fjes                   28672  0



```

If some other details are required please let me know.

Thanks & Regards,

---

### Post by Ercan_Gul on 2016-05-15
Hi,
I'm new to this this community as well as ubuntu & linux enironment. I'm a real newbie. But I had the same problem alongside others that I still have trying to figure out.
 What I did after a long google search was to get into BIOS settings and disable secure boot or sth like that in the settings. I don't know if this is your problem but I think secure boot prevented my hardware in my laptop which connects to internet ( is it called modem? ) and I changed the proprietary driver in the settings now it is fine. 
Remind you I'm not at a place to give suggestions about anything and do not know if disabling secure boot is sth dangerous.

---

### Post by konsolelover on 2016-05-18
Thanks Ercan_Gul for your reply,  I forgot to mention that secure boot is already disabled. I bought this laptop with pre installed FreeDOS then I installed Windows 8.1 in it so I think it is not running in UEFI mode. By the way I tried my internet connection with Linux Mint 17.3 and it worked like a charm. Maybe it is time to give Mint a try.

---

### Post by KenUBF on 2016-05-23
Hi konsolelover,I had a similar issue a few months back. I'm still not sure what caused the issue but it seems to have resolved itself. I'm guessing some update broke something and a few months later another update fixed it. A friend gave me a USB Ethernet adapter since Ubuntu didn't recognize my own built in adapter. This solution worked for me so I still had internet access until the update (or whatever it was) rolled out. It's worked fine ever since. I hope that might work for you. If not, Linux Mint is a nice system. I'm trying to get my father to switch over from Windows 10 *shutter*

---

