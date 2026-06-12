---
title: "usb drive not working"
date: 2015-02-26
forum: New to Ubuntu
---

### Post by regin.mallari on 2015-02-26
Hi, there are times when my USB drive does not work. I don't know what is wrong with it. I know it's not the USB stick because it works on other machines, and it's not the actual usb port because when I leave the thing plugged in and restart my computer, it recognizes the usb drive (light flashes), but then once Ubuntu starts I can no longer access it l

also, my computer is a touchscreen laptop. I'll know when the drive is working because the touchscreen will work as well. But when it isn't, the touchscreen isn't working either. So I suspect there's a link between the two somewhere. Plz help.

[IMG]http://i.imgur.com/f7nxT3q.png[/IMG]

---

### Post by yancek on 2015-02-26
Accessing it may require installing 'sudo apt-get install exfat-utils exfat-fuse', you could check to see if this software is installed.  How exactly are you trying to access the flash drive?  The message /dev/sdb1 does not exist would seem to indicate another problem.  Is the flash drive recognized in the BIOS?

---

### Post by regin.mallari on 2015-02-26
well, I left the thing plugged in when I restarted it, and then I went to files, and I saw the drive name, so I clicked it, but it spewed out that error

normally when i plug it in nothing happens, which i why i decided to leave it plugged in and then restarted the computer. the USB lights flashed during boot time so I suppose it works then, but not after ubuntu loads up.

I went to /dev and I don't see sdb1

---

### Post by nerdtron on 2015-02-27
Filesystem on the usb drive could have been corrupted. Probably you did not safely removed it before you unplugged it. Your drive will still be usable, but I think it needs to be reformatted.

---

### Post by regin.mallari on 2015-02-27
> **nerdtron said:**
> Filesystem on the usb drive could have been corrupted. Probably you did not safely removed it before you unplugged it. Your drive will still be usable, but I think it needs to be reformatted.

I don't think so. It works on other computers, and I have tried plugging in other devices, also to no avail.

---

### Post by gmulak on 2015-02-27
Regin, what OS were the other computers running?  Does the drive have an OS image or some other software that will boot a machine?  What happened, if anything, when you followed Yanik's suggestion of running: 'sudo apt-get install exfat-utils exfat-fuse'?

---

### Post by sandyd on 2015-02-28
Hi, please run the following commands and post the output when you plugin your usb drive
```

dmesg | grep 'usb\|sd'
lsusb
sudo fdisk -l
```

Thanks!

---

### Post by regin.mallari on 2015-03-02
```


[    0.250775] usbcore: registered new interface driver usbfs
[    0.250783] usbcore: registered new interface driver hub
[    0.250810] usbcore: registered new device driver usb
[    1.347724] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.347727] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.347729] usb usb1: Product: EHCI Host Controller
[    1.347731] usb usb1: Manufacturer: Linux 3.13.0-44-generic ehci_hcd
[    1.347733] usb usb1: SerialNumber: 0000:00:1d.0
[    1.348393] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.348396] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.348398] usb usb2: Product: xHCI Host Controller
[    1.348400] usb usb2: Manufacturer: Linux 3.13.0-44-generic xhci_hcd
[    1.348402] usb usb2: SerialNumber: 0000:00:14.0
[    1.351108] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.351111] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.351113] usb usb3: Product: xHCI Host Controller
[    1.351115] usb usb3: Manufacturer: Linux 3.13.0-44-generic xhci_hcd
[    1.351117] usb usb3: SerialNumber: 0000:00:14.0
[    1.472928] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo only pio slum part deso sadm sds apst 
[    1.659693] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.791937] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.791939] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.879905] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.879918] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.879920] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.880001] sd 1:0:0:0: [sda] Write Protect is off
[    1.880004] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.880031] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.880776]  sda: sda1 sda2 < sda5 >
[    1.881282] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.959564] usb 2-1: new high-speed USB device number 2 using xhci_hcd
[    1.985288] usb 2-1: New USB device found, idVendor=1bcf, idProduct=2c66
[    1.985290] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.985292] usb 2-1: Product: Lenovo EasyCamera
[    1.985293] usb 2-1: Manufacturer: J5CE9I0FC
[    2.151527] usb 2-5: new full-speed USB device number 3 using xhci_hcd
[    2.169022] usb 2-5: New USB device found, idVendor=0cf3, idProduct=3004
[    2.169025] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.335441] usb 2-6: new full-speed USB device number 4 using xhci_hcd
[    7.359521] usb 2-6: New USB device found, idVendor=048d, idProduct=8386
[    7.359526] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    7.359529] usb 2-6: Product: ITE Device(8386)
[    7.359531] usb 2-6: Manufacturer: ITE Tech. Inc.
[    7.397647] usbcore: registered new interface driver usbhid
[    7.397650] usbhid: USB HID core driver
[    7.525560] usb 2-7: new full-speed USB device number 5 using xhci_hcd
[    7.550801] usb 2-7: New USB device found, idVendor=03eb, idProduct=8c1d
[    7.550806] usb 2-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    7.550809] usb 2-7: Product: Atmel maXTouch Digitizer
[    7.550811] usb 2-7: Manufacturer: Atmel
[    7.563010] hid-generic 0003:03EB:8C1D.0003: hiddev0,hidraw0: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:14.0-7/input1
[   44.805826] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   44.820044] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   45.056823] input: Atmel Atmel maXTouch Digitizer as /devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/input/input7
[   45.057058] hid-multitouch 0003:03EB:8C1D.0002: input,hidraw1: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:14.0-7/input0
[   45.073123] usbcore: registered new interface driver btusb
[   45.140833] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/input/input13
[   45.140940] usbcore: registered new interface driver uvcvideo
[   45.177768] usbcore: registered new interface driver ath3k
[   45.183881] usb 2-5: USB disconnect, device number 3
[   45.238427] type=1400 audit(1425316120.372:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=669 comm="apparmor_parser"
[   45.239497] type=1400 audit(1425316120.372:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=669 comm="apparmor_parser"
[   45.455763] usb 2-5: new full-speed USB device number 6 using xhci_hcd
[   50.454041] WARNING: CPU: 3 PID: 0 at /build/buildd/linux-3.13.0/drivers/usb/host/xhci-ring.c:1582 handle_cmd_completion+0xe46/0xe50()
[   50.454043] Modules linked in: hid_sensor_accel_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_gyro_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common joydev snd_seq_midi snd_seq_midi_event snd_rawmidi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp arc4 kvm bnep ath9k rfcomm snd_seq ath9k_common ath9k_hw ath mac80211 uvcvideo serio_raw videobuf2_vmalloc snd_hda_codec_hdmi videobuf2_memops snd_seq_device cfg80211 ath3k videobuf2_core snd_hda_codec_conexant mei_me hid_sensor_hub videodev lpc_ich snd_hda_intel hid_multitouch snd_hda_codec btusb bluetooth snd_hwdep snd_pcm mei snd_page_alloc snd_timer snd soundcore parport_pc ppdev lp parport mac_hid hid_generic usbhid hid dm_crypt crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel i915 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd i2c_algo_bit drm_kms_helper drm ahci psmouse libahci video
[   50.658063] usb 2-5: Device not responding to set address.
[   50.861862] usb 2-5: device not accepting address 6, error -71
[   50.973888] usb 2-5: new full-speed USB device number 7 using xhci_hcd
[   50.991295] usb 2-5: New USB device found, idVendor=0cf3, idProduct=3004
[   50.991301] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   52.413357] usb 2-1: USB disconnect, device number 2
[   52.449569] usb 2-5: USB disconnect, device number 7
[   52.450118] usb 2-6: USB disconnect, device number 4
[   52.454370] usb 2-7: USB disconnect, device number 5
[   75.355552] type=1400 audit(1425316150.500:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2521 comm="apparmor_parser"
[   75.356080] type=1400 audit(1425316150.500:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2521 comm="apparmor_parser"


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x287b84af


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   976771071   488134656   83  Linux


Disk /dev/mapper/sda5_crypt: 499.8 GB, 499847790592 bytes
255 heads, 63 sectors/track, 60769 cylinders, total 976265216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000




Disk /dev/mapper/ubuntu--vg-root: 495.6 GB, 495611543552 bytes
255 heads, 63 sectors/track, 60254 cylinders, total 967991296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000




Disk /dev/mapper/ubuntu--vg-swap_1: 4185 MB, 4185915392 bytes
255 heads, 63 sectors/track, 508 cylinders, total 8175616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


--------------------------


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by sandyd on 2015-03-02
Seems to be a USB-Related issue.

Drive is plugged in, lsusb does not show drive, and there is a warning on XHCI driver
```

[   50.454041] WARNING: CPU: 3 PID: 0 at /build/buildd/linux-3.13.0/drivers/usb/host/xhci-ring.c:1582 handle_cmd_completion+0xe46/0xe50()
[   50.454043] Modules linked in: hid_sensor_accel_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_gyro_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common joydev snd_seq_midi snd_seq_midi_event snd_rawmidi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp arc4 kvm bnep ath9k rfcomm snd_seq ath9k_common ath9k_hw ath mac80211 uvcvideo serio_raw videobuf2_vmalloc snd_hda_codec_hdmi videobuf2_memops snd_seq_device cfg80211 ath3k videobuf2_core snd_hda_codec_conexant mei_me hid_sensor_hub videodev lpc_ich snd_hda_intel hid_multitouch snd_hda_codec btusb bluetooth snd_hwdep snd_pcm mei snd_page_alloc snd_timer snd soundcore parport_pc ppdev lp parport mac_hid hid_generic usbhid hid dm_crypt crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel i915 aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd i2c_algo_bit drm_kms_helper drm ahci psmouse libahci video
[   50.658063] usb 2-5: Device not responding to set address.
[   50.861862] usb 2-5: device not accepting address 6, error -71
[   50.973888] usb 2-5: new full-speed USB device number 7 using xhci_hcd
[   50.991295] usb 2-5: New USB device found, idVendor=0cf3, idProduct=3004
[   50.991301] usb 2-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
```

---

### Post by regin.mallari on 2015-03-02
So by USB do you mean the actual USB stick? or the USB port?

Because the stick works perfectly fine on other (Windows) machines.

---

### Post by regin.mallari on 2015-03-03
bump

---

### Post by Vladlenin5000 on 2015-03-03
> **regin.mallari said:**
> So by USB do you mean the actual USB stick? or the USB port?

The USB port (actually the hub), obviously. _And probably just a software/drivers issue with the USB3.0_. 
I've noticed you didn't have any internet connection when you took that screen capture. Have you connected it to the internet and performed the system updates already? If not, please do it because probably it's just what it need in order to install/update the proper support for USB3.0.

---

