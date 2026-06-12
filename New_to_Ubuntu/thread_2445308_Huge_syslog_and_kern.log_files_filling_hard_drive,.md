---
title: "Huge syslog and kern.log files filling hard drive, possibly on account of wifi?"
date: 2020-06-11
forum: New to Ubuntu
---

### Post by siragan on 2020-06-11
I am running Ubuntu 20.04 Focal Fossa on the following hardware.

Motherboard: Gigabyte X570 Aorus Elite Wifi rev. 1.0 BIOS version f12e
CPU: AMD Ryzen 9 3900X
Memory: Corsair Vengeance RGB Pro 3600MHz (actual speed 3200MHz)
GPU: AMD Radeon RX5700XT
PSU: Seasonic 760W

From time to time the syslog and kern.log files will start filling up until there is very little remaining space on the hard drive. The files quickly grow to many tens of gigabytes in size. Often I do a hard reboot and sometimes boot from a USB stick. Then I run commands like

```
sudo su
> syslog
> kern.log

```
from the /var/log directory in order to clear these files, and sometimes also other syslog and kern.log files.

I see in particular repeating messages like the ones posted below. Is this indeed something to do with wifi drivers, and is there a recommended way to attempt to fix it? Unfortunately, the motherboard maufacturer does not support Linux, at least not with this board. Thank you in advance for your assistance!

```
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672559] ------------[ cut here ]------------
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672562] wlp3s0:  Failed check-sdata-in-driver check, flags: 0x0
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672579] WARNING: CPU: 5 PID: 19481 at net/mac80211/driver-ops.h:17 drv_sta_state+0x254/0x3f0 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672581] Modules linked in: ses enclosure scsi_transport_sas uas usb_storage rfcomm ccm cmac algif_hash algif_skcipher af_alg bnep edac_mce_amd nls_iso8859_1 kvm snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep snd_pcm crct10dif_pclmul btusb btrtl ghash_clmulni_intel amdgpu btbcm snd_seq_midi btintel snd_seq_midi_event iwlmvm bluetooth snd_rawmidi mac80211 joydev input_leds amd_iommu_v2 snd_seq libarc4 gpu_sched aesni_intel snd_seq_device snd_timer ttm iwlwifi ecdh_generic ecc crypto_simd drm_kms_helper cryptd glue_helper snd fb_sys_fops syscopyarea sysfillrect wmi_bmof sysimgblt cfg80211 k10temp soundcore ccp mac_hid sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_generic usbhid hid crc32_pclmul i2c_piix4 igb ahci libahci i2c_algo_bit dca wmi
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672638] CPU: 5 PID: 19481 Comm: kworker/u64:4 Tainted: G        W         5.4.0-37-generic #41-Ubuntu
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672638] Hardware name: Gigabyte Technology Co., Ltd. X570 AORUS ELITE WIFI/X570 AORUS ELITE WIFI, BIOS F12e 03/06/2020
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672646] Workqueue: phy0 ieee80211_csa_connection_drop_work [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672653] RIP: 0010:drv_sta_state+0x254/0x3f0 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672654] Code: 00 45 31 ed e9 66 fe ff ff 48 8b 83 78 04 00 00 48 8d b3 98 04 00 00 48 c7 c7 c8 88 2e c1 48 85 c0 48 0f 45 f0 e8 47 a1 e3 f1 <0f> 0b 41 bd fb ff ff ff e9 3d fe ff ff 65 8b 05 e8 8c da 3e 89 c0
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672654] RSP: 0018:ffffb7914874fc98 EFLAGS: 00010282
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672656] RAX: 0000000000000000 RBX: ffff8c0f97f988c0 RCX: 0000000000000006
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672656] RDX: 0000000000000007 RSI: ffff8c0f9ea2ba00 RDI: ffff8c0f9e9578c0
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672656] RBP: ffffb7914874fcd0 R08: 0000000000240000 R09: 0000000000000004
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672657] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8c0f86a587a0
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672657] R13: ffff8c0f86a587a0 R14: 0000000000000004 R15: ffff8c0f86a58d68
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672658] FS:  0000000000000000(0000) GS:ffff8c0f9e940000(0000) knlGS:0000000000000000
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672659] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672660] CR2: 00007f6a5119c000 CR3: 0000001e95edc000 CR4: 0000000000340ee0
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672660] Call Trace:
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672667]  sta_info_move_state+0x276/0x370 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672674]  __sta_info_destroy_part2+0x2f/0x180 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672681]  __sta_info_flush+0x128/0x180 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672689]  ieee80211_set_disassoc+0xc0/0x5f0 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672690]  ? _raw_spin_unlock_bh+0x1e/0x20
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672698]  __ieee80211_disconnect+0x86/0x120 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672705]  ieee80211_csa_connection_drop_work+0x15/0x20 [mac80211]
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672706]  process_one_work+0x1eb/0x3b0
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672708]  worker_thread+0x4d/0x400
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672709]  kthread+0x104/0x140
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672710]  ? process_one_work+0x3b0/0x3b0
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672711]  ? kthread_park+0x90/0x90
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672712]  ret_from_fork+0x22/0x40
Jun 11 21:39:24 siragan-X570-AORUS-ELITE-WIFI kernel: [27173.672712] ---[ end trace 251d8bc5dd6bb4b1 ]---

```

---

### Post by wildmanne39 on 2020-06-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ActionParsnip on 2020-06-12
What is the output of:
```

sudo lshw -C network; lsb_release -a; uname -a

```
Thanks

---

### Post by siragan on 2020-06-12
Hello, this is the output:

```

  *-network                 
       description: Wireless interface
       product: Dual Band Wireless-AC 3168NGW [Stone Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 10
       serial: 0c:dd:24:63:aa:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-37-generic firmware=29.1654887522.0 ip=10.0.0.36 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:107 memory:fc800000-fc801fff
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 03
       serial: b4:2e:99:a4:31:47
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.6.0-k firmware=0. 6-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:fc700000-fc71ffff ioport:f000(size=32) memory:fc720000-fc723fff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
Linux siragan-X570-AORUS-ELITE-WIFI 5.4.0-37-generic #41-Ubuntu SMP Wed Jun 3 18:57:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by nyarla33 on 2020-08-08
That looks like what I reported there:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1881214](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1881214)

---

### Post by pbear42 on 2020-08-09
What a stupid bug.  siragan, perhaps this [askubuntu]("https://askubuntu.com/a/515151") will help with the log problem.  Never had occasion to test, so no promises, but worth a shot.

---

