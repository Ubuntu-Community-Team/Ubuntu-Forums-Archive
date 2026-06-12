---
title: "Trouble installing wireless driver RTL8191SU"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by damain on 2011-11-07
Hello,  
Maybe is was the fact that I have been configuring this my computer all day but I am having a problem installing the driver for the RTL8191SU driver. every time I use the make command the output is this
  make 
ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.39.4/build M=/home/user/rtl/driver/rtl8
  modules make[1]: Entering directory `/usr/src/linux-source-2.6.39.4'
    WARNING: Symbol version dump /usr/src/linux-source-2.6.39.4/Module.symvers
            is missing; modules will have no dependencies and modversions.
    CC [M]  /home/user/rtl/driver/rtl8/cmd/rtl871x_cmd.o In file included from /home/user/rtl/driver/rtl8/include/drv_types.h:77,
                  from /home/user/rtl/driver/rtl8/cmd/rtl871x_cmd.c:24: /home/user/rtl/driver/rtl8/include/rtl871x_io.h:35:28: error: linux/smp_lock.h: No such file or directory make[2]: *** [/home/user/rtl/driver/rtl8/cmd/rtl871x_cmd.o] Error 1 make[1]: *** [_module_/home/user/rtl/driver/rtl8] Error 2 make[1]: Leaving directory `/usr/src/linux-source-2.6.39.4' make: *** [modules] Error 2      I have spent sometime working on this and I have been using 2 pages mainly as reference [http://andi.opensuse-id.org/2010/05/27/how-to-install-rtl8191seva-wlan-device-driver-on-opensuse/](http://andi.opensuse-id.org/2010/05/27/how-to-install-rtl8191seva-wlan-device-driver-on-opensuse/)  and [http://ubuntuforums.org/showthread.php?t=1834478](http://ubuntuforums.org/showthread.php?t=1834478)  

here is what I am working with right now:  
-------------------------------------------------------------  
root@bt:/home/user/rtl/driver# sudo lshw -c network
   *-network UNCLAIMED
             description: Network controller
        product: RTL8191SEvA Wireless LAN Controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        version: 10
        width: 32 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list        configuration: latency=0
        resources: ioport:3000(size=256) memory:d3500000-d3503fff
   *-network
        description: Ethernet interface
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:03:00.0
        logical name: eth0
        version: 02
        serial: c8:0a:a9:c5:a4:0d
        size: 100MB/s
        capacity: 100MB/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
        resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
  -----------------------------------------------------------------
  root@bt:/home/user/rtl/driver# lspci -nn | grep
 0280 02:00.0 
Network controller [0280]: Realtek Semiconductor Co., Ltd.
 RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
  -------------------------------------------------------------
  root@bt:/home/user/rtl/driver# iwconfig lo
        no wireless extensions.
  eth0
      no wireless extensions.
  -------------------------------------------------------------------
  root@bt:/home/user/rtl/driver# rfkill list all 0: hp-wifi: Wireless LAN
         Soft blocked: no
         Hard blocked: yes
  -----------------------------------------------------------------
  root@bt:/home/user/rtl/driver# lsmod Module
                  Size  Used by dm_crypt
               14720  0  snd_hda_codec_hdmi     21630  1  joydev
                  8649  0  snd_hda_codec_realtek   248710  1  snd_hda_intel
          21661  2  snd_hda_codec
          80498  3
 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel snd_hwdep
               5424  1 snd_hda_codec snd_pcm_oss
            36427  0  snd_mixer_oss
          13581  1 snd_pcm_oss snd_pcm
                68662  4
 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
 snd_seq_dummy
           1358  0  snd_seq_oss
            26216  0  snd_seq_midi
            4460  0  snd_rawmidi
            18745  1 snd_seq_midi snd_seq_midi_event
      5720  2 snd_seq_oss,snd_seq_midi snd_seq
                45875  6
 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event snd_timer
              17803  2 snd_pcm,snd_seq snd_seq_device
          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq lp
                      7373  0  parport
                29468  1 lp snd
                    50697  17
 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device uvcvideo
               60284  0
  hp_wmi
                  7748  0  soundcore
               6048  1 snd sparse_keymap
           3194  1 hp_wmi rfkill
                 14987  1 hp_wmi snd_page_alloc
          6801  2 snd_hda_intel,snd_pcm videodev
               75797  1 uvcvideo psmouse                52655  0  wmi
                     8772  1 hp_wmi serio_raw
               3744  0  mac_hid
                 3029  0  i915
                  476096  3  drm_kms_helper
         31085  1 i915 drm
                   178158  4 i915,drm_kms_helper ahci
                   18634  2  intel_agp
               9614  1 i915 i2c_algo_bit
            4916  1 i915 intel_gtt
              13296  3 i915,intel_agp libahci
                19920  1 ahci r8169
                  36663  0  video
                  10930  1 i915
 mii
                     4091  1 r8169 agpgart
                27414  3 drm,intel_agp,intel_gtt
    
I am installing this new driver since my wifi is no longer working. It was working fine from the live CD but now it is no longer working once I installed onto my harddrive Thank you so much for you help

---

### Post by bkratz on 2011-11-07
Here is a really good thread about that device.  [http://ubuntuforums.org/showthread.php?t=1674994](http://ubuntuforums.org/showthread.php?t=1674994)

See post two especially.

---

### Post by gandaran on 2011-11-07
> description: Network controller
product: RTL8191SEvA Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
you are installing the wrong driver, you need SEva not SU driver
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
the RTL8191SU chipset works 'out of the box' on ubuntu 11.10 and 11.04, for 10.10 it just need a minor firmware fix and for 10.04 needs the full driver install.

---

### Post by damain on 2011-11-07
Thanks [gandaran]("http://ubuntuforums.org/member.php?u=417273") I knew it was something simple, a little bit of sleep goes a long way I guess. I am not quite out of the water yet though. my computer is recognizing my wireless now, it's showing a blue light. But the Wicd network manager is still not picking up any wireless signals. I've read the other topics. I've check out the other threads on this. It doesn't seem like people have problems once the driver is recognized, I am using wext. *edit*Ha ha, I got it sorry I just needed to add wlan0 to my wireless interface in wicd

---

