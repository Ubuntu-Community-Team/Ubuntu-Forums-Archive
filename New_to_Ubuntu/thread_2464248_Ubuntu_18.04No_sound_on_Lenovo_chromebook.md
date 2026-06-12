---
title: "Ubuntu 18.04/No sound on Lenovo chromebook"
date: 2021-06-27
forum: New to Ubuntu
---

### Post by edis8co on 2021-06-27
Hey guys.! I got an Lenovo Chromebook s345 and want to install Linux/Ubuntu on it. The problem is no matter which OS i install i cant get the sound / speakers to work and i've tried every tipp/solution i could find on the internet (except black magic..thats a last resort :D ) So i'm currently trying on Ubuntu 18.04 and the last thing i did is a fresh install and installed some packages like inxi and git. I'm a novice to Linux so every idea is welcome ! Here are some outputs:

inxi -Fzx:

System:    Host: liara-Liara Kernel: 5.4.0-77-generic x86_64
           bits: 64 gcc: 7.5.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.3 LTS
Machine:   Device: laptop System: Google product: Liara v: rev6 serial: N/A
           Mobo: Google model: Liara v: rev6 serial: N/A
           UEFI: coreboot v: MrChromebox-4.13 date: 04/26/2021
Battery    BAT0: charge: 21.7 Wh 37.3% condition: 58.2/56.9 Wh (102%)
           model: Sunwoda L18D3PG status: Discharging
           CROS_USBPD_CHARGER0: charge: N/A condition: NA/NA Wh
           model: 0 0 status: Not charging
           CROS_USBPD_CHARGER1: charge: N/A condition: NA/NA Wh
           model: 0 0 status: Not charging
CPU:       Dual core AMD A6-9220C RADEON R5 5 COMPUTE CORES 2C+3G (-MCP-) 
           arch: Excavator rev.0 cache: 2048 KB
           
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 7186
           clock speeds: max: 1800 MHz 1: 1286 MHz 2: 1267 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Stoney [Radeon R2/R3/R4/R5 Graphics]
           bus-ID: 00:01.0
           Display Server: x11 (X.Org 1.20.4 )
           drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)
           Resolution: 1920x1080@0.00hz
           OpenGL: renderer: llvmpipe (LLVM 8.0, 128 bits)
           version: 3.3 Mesa 19.0.2 Direct Render: Yes
Audio:     Card Advanced Micro Devices [AMD/ATI] Device 15b3
           driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture v: k5.4.0-77-generic
Network:   Card-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter
           driver: ath10k_pci bus-ID: 01:00.0
           IF: wlp1s0 state: up mac: d8:f3:bc:cc:95:5f
           Card-2: Atheros usb-ID: 001-004
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: NA (-)
           ID-1: /dev/mmcblk1 model: N/A size: 62.5GB
Partition: ID-1: / size: 57G used: 7.2G (14%) fs: ext4 dev: /dev/mmcblk1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 51.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 189 Uptime: 12 min Memory: 1138.2/3885.6MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.201) inxi: 2.3.56 
lshw:

liara@liara-Liara:~$ lshw
WARNING: you should run this program as super-user.
liara-liara                 
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3885MiB
     *-cpu
          product: AMD A6-9220C RADEON R5, 5 COMPUTE CORES 2C+3G
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2469MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate ssbd vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov cpufreq
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 60h-6fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Stoney [Radeon R2/R3/R4/R5 Graphics]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: ca
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller cap_list
             configuration: latency=0
             resources: memory:d0000000-d3ffffff memory:d4000000-d47fffff ioport:1000(size=256) memory:d4d00000-d4d3ffff memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:36 memory:d4d80000-d4d83fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 60h-6fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:d4800000-d49fffff
           *-network
                description: Wireless interface
                product: QCA6174 802.11ac Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 32
                serial: d8:f3:bc:cc:95:5f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=5.4.0-77-generic firmware=WLAN.RM.4.4.1-00079-QCARMSWPZ-1 ip=192.168.0.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:38 memory:d4800000-d49fffff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 60h-6fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:d4a00000-d4afffff
           *-generic
                description: SD Host controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:33 memory:d4a00000-d4a00fff memory:d4a01000-d4a017ff
        *-generic:0 UNCLAIMED
             description: Encryption controller
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d4d60000-d4d7ffff memory:d4b00000-d4bfffff memory:d4d88000-d4d88fff memory:d4c00000-d4cfffff memory:d4d84000-d4d85fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:d4d86000-d4d87fff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:18 memory:d4d89000-d4d890ff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 4b
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-generic:1
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 01
             width: 64 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=sdhci-pci latency=71
             resources: irq:16 memory:d4d8a000-d4d8a0ff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 60h-6fh) Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 60h-6fh) Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:09.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
WARNING: output may be incomplete or inaccurate, you should run this program as super-user
lsmod:

liara@liara-Liara:~$ lsmod
Module                  Size  Used by
rfcomm                 81920  4
cmac                   16384  1
bnep                   24576  2
nls_iso8859_1          16384  1
designware_i2s         24576  0
cros_usbpd_logger      20480  0
cros_ec_lightbar       16384  0
cros_ec_sysfs          16384  0
cros_usbpd_charger     20480  0
cros_ec_chardev        16384  0
cros_ec_debugfs        16384  0
joydev                 28672  0
edac_mce_amd           32768  0
kvm_amd                98304  0
ccp                    86016  1 kvm_amd
kvm                   659456  1 kvm_amd
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           372736  1
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
amdgpu               4530176  0
glue_helper            16384  1 aesni_intel
ath10k_pci             49152  0
input_leds             16384  0
amd_iommu_v2           20480  1 amdgpu
serio_raw              20480  0
gpu_sched              32768  1 amdgpu
ath10k_core           466944  1 ath10k_pci
ttm                   102400  1 amdgpu
uvcvideo               94208  0
ath                    36864  1 ath10k_core
drm_kms_helper        188416  1 amdgpu
videobuf2_vmalloc      20480  1 uvcvideo
btusb                  57344  0
videobuf2_memops       20480  1 videobuf2_vmalloc
btrtl                  24576  1 btusb
mac80211              856064  1 ath10k_core
videobuf2_v4l2         24576  1 uvcvideo
drm                   491520  4 gpu_sched,drm_kms_helper,amdgpu,ttm
btbcm                  16384  1 btusb
fam15h_power           16384  0
k10temp                16384  0
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
btintel                24576  1 btusb
videodev              221184  3 videobuf2_v4l2,uvcvideo,videobuf2_common
bluetooth             544768  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
i2c_algo_bit           16384  1 amdgpu
snd_soc_acp_da7219mx98357_mach    16384  0
snd_hda_codec_hdmi     61440  1
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
fb_sys_fops            16384  1 drm_kms_helper
cros_ec_dev            20480  0
snd_soc_max98357a      20480  0
acp_audio_dma          20480  1 snd_soc_acp_da7219mx98357_mach
snd_soc_adau7002       16384  0
syscopyarea            16384  1 drm_kms_helper
snd_soc_da7219         77824  1 snd_soc_acp_da7219mx98357_mach
snd_hda_intel          49152  1
cfg80211              712704  3 ath,mac80211,ath10k_core
snd_intel_dspcfg       28672  1 snd_hda_intel
sysfillrect            16384  1 drm_kms_helper
snd_soc_core          245760  6 snd_soc_da7219,snd_soc_adau7002,designware_i2s,acp_audio_dma,snd_soc_max98357a,snd_soc_acp_da7219mx98357_mach
ecdh_generic           16384  2 bluetooth
snd_hda_codec         135168  2 snd_hda_codec_hdmi,snd_hda_intel
sysimgblt              16384  1 drm_kms_helper
ecc                    32768  1 ecdh_generic
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_hda_core           90112  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hwdep              20480  1 snd_hda_codec
libarc4                16384  1 mac80211
snd_pcm               102400  10 snd_hda_codec_hdmi,snd_hda_intel,snd_soc_da7219,snd_hda_codec,designware_i2s,acp_audio_dma,snd_soc_core,snd_soc_acp_da7219mx98357_mach,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           20480  0
acpi_als               20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
kfifo_buf              16384  1 acpi_als
industrialio           73728  2 acpi_als,kfifo_buf
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    86016  14 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_soc_acp_da7219mx98357_mach,snd_rawmidi
cros_kbd_led_backlight    16384  0
8250_dw                16384  0
soundcore              16384  1 snd
raydium_i2c_ts         24576  0
mac_hid                16384  0
elan_i2c               40960  0
sch_fq_codel           20480  1
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               45056  1 ip_tables
autofs4                45056  2
mmc_block              49152  3
sdhci_pci              53248  0
i2c_piix4              28672  0
cqhci                  28672  1 sdhci_pci
sdhci                  65536  1 sdhci_pci
cros_ec_lpcs           16384  0
cros_ec                20480  1 cros_ec_lpcs
i2c_hid                32768  0
hid                   126976  1 i2c_hid
video                  49152  0
.

aplay -l:

liara@liara-Liara:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Hope someone is out there who can help me solve this. Thankss !

---

### Post by edis8co on 2021-06-27
Forgot to mention, neither the speakers, nor headphones are working. Tested on firefox, downloaded mp3, vlac..nothing. The speakers were working on chromeOS. Also tried with repository drivers and this one too : devicehunt.com/view/type/pci/vendor/1002/device/98E4 ..and nothing..

---

### Post by tea for one on 2021-06-27
> **edis8co said:**
> Hey guys.! I got an Lenovo Chromebook s345 and want to install Linux/Ubuntu on it. The problem is no matter which OS i install i cant get the sound / speakers to work and i've tried every tipp/solution i could find on the internet (except black magic..thats a last resort :D ) So i'm currently trying on Ubuntu 18.04 and the last thing i did is a fresh install and installed some packages like inxi and git. I'm a novice to Linux so every idea is welcome ! 

From the comments I've seen in Ubuntu forums and other sites, Linux and Chromebooks are sometimes incompatible, especially sound.

Is this info any use [https://galliumos.org/](https://galliumos.org/)

There is a list of hardware and comments within that site.

I'm not a Chromebook user, just supplying a bit of information.

---

### Post by bobunderwood99 on 2021-07-05
Exactly how are you installing Ubuntu on your Chromebook? With Crostini or cras or Crouton or ?

---

### Post by ActionParsnip on 2021-07-06
Please follow this
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Give the URL created by the script in step 3

---

