---
title: "Ubuntu 12.04 LTS 32 bit freezes frequently"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by nns2006 on 2013-08-26
Hello,
I have ubuntu 12.04.2  32bit installed on my dell vostro1500. For last few days I am experiencing this frequent freezing of ubuntu- no mouse movement, no keyboard response, no Alt + REISUB response - nothing except PRESS POWER button to shutit down. and upon restarting up it happens again in few mins. I can't do anything.
I have seens many responses in community, it all says about checking log file in ```
/var/log
```. But  nothing is understandable to me. 
As far as I can say it is not limited to only one program, I have experienced it with multiple programs at different times.

Please tell me how to correct this erratic behaviour. If you need any information from me I will post it as soon as possible.

Thanks and regards,

---

### Post by nenadlatinovic on 2013-08-26
Maybe you still post the output of var/log for someone who knows what he's doing to read and maybe help you .

---

### Post by nns2006 on 2013-08-26
there are 5000 lines, in the system log itself. which I think will be irrelevant to the problem concerned. What specific things I should look for?

---

### Post by mikewhatever on 2013-08-26
It's hard to tell what to look for, before knowing what's wrong. If you are set on cracking it yourself, look for errors, warnings, kernel panics, but if you want others to check it, compress it,  attach to a post a post. You can copy a syslog to the desktop with this command:
```
cp /var/log/syslog ~/Desktop
```

---

### Post by nns2006 on 2013-08-27
Here is the log file. please see if there is any problem in it.

---

### Post by mikewhatever on 2013-08-27
Well, I am no expert, but there are errors right at the top:
```
Aug 27 07:45:08 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:01:08 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:15:20 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:17:01 nityanand-Vostro-1500 CRON[17127]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 08:18:20 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:29:14 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:30:08 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 19:00:36 nityanand-Vostro-1500 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug 27 19:00:36 nityanand-Vostro-1500 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1064" x-info="http://www.rsyslog.com"] start

```

The log stops at Aug 27 08:30:08 and then continues with "Aug 27 19:00:36 nityanand-Vostro-1500 kernel: imklog 5.8.6, log source = /proc/kmsg started.", which indicates the machine had been turned off or frozen.
So, does it freeze if you turn off wifi?

---

### Post by nns2006 on 2013-08-28
> **mikewhatever said:**
> Well, I am no expert, but there are errors right at the top:
```
Aug 27 07:45:08 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:01:08 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:15:20 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:17:01 nityanand-Vostro-1500 CRON[17127]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 27 08:18:20 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:29:14 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 08:30:08 nityanand-Vostro-1500 NetworkManager[1155]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug 27 19:00:36 nityanand-Vostro-1500 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug 27 19:00:36 nityanand-Vostro-1500 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1064" x-info="http://www.rsyslog.com"] start

```

The log stops at Aug 27 08:30:08 and then continues with "Aug 27 19:00:36 nityanand-Vostro-1500 kernel: imklog 5.8.6, log source = /proc/kmsg started.", which indicates the machine had been turned off or frozen.
So, does it freeze if you turn off wifi?

No. I checked it just now. 
It is happening with now on attaching USB drive also. Moment I insert the drive it freezes. attaching the log file for that also. 3 frequent freezing upon attaching USB Hard drive. and I t has to be shut down by pressing power button.

---

### Post by mikewhatever on 2013-08-28
Well, this time, there are quite a few of these:
> Aug 28 08:04:03 nityanand-Vostro-1500 kernel: [38953.093214] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.016959] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.016966] FAT-fs (sdb1): Filesystem has been set read-only
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227627] BUG: scheduling while atomic: pool/16149/0x10000001
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227633] Modules linked in: nls_iso8859_1 usb_storage pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) dm_crypt rfcomm bnep parport_pc bluetooth ppdev binfmt_misc joydev snd_hda_codec_idt snd_hda_intel coretemp arc4 snd_hda_codec r852 uvcvideo snd_usb_audio sm_common nand snd_hwdep videobuf2_core nand_ids snd_usbmidi_lib videodev psmouse dell_laptop dell_wmi videobuf2_vmalloc r592 mtd b43 snd_pcm videobuf2_memops dm_multipath nand_bch gpio_ich snd_seq_midi bch scsi_dh sparse_keymap snd_seq_midi_event microcode snd_rawmidi snd_seq memstick serio_raw dcdbas nand_ecc snd_timer mac_hid snd_seq_device mac80211 snd cfg80211 soundcore snd_page_alloc bcma lpc_ich ssb_hcd lp parport dm_raid45 xor dm_mirror dm_region_hash dm_log btrfs zlib_deflate libcrc32c b44 hid_generic sdhci_pci firewire_ohci sdhci firewire_core crc_itu_t usbhid hid wmi ssb i915 drm_kms_helper drm i2c_algo_bit video zram(C)
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227756] Pid: 16149, comm: pool Tainted: G        WC O 3.5.0-40-generic #62~precise1-Ubuntu
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227759] Call Trace:
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227771]  [<c15cd4ed>] __schedule_bug+0x52/0x5e
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227778]  [<c15e0e6f>] __schedule+0x60f/0x630
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227785]  [<c12d5144>] ? rb_erase+0xb4/0x120
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227792]  [<c107b775>] ? pick_next_entity+0x65/0xc0
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227797]  [<c1074431>] ? finish_task_switch+0x41/0xc0
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227803]  [<c15e0b39>] ? __schedule+0x2d9/0x630
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227809]  [<c102d6b7>] ? smp_reschedule_interrupt+0x27/0x30
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227814]  [<c102d6b7>] ? smp_reschedule_interrupt+0x27/0x30
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227820]  [<c1075c9b>] __cond_resched+0x1b/0x30
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227825]  [<c15e0f09>] _cond_resched+0x29/0x30
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227830]  [<c15e05a0>] down_write+0x10/0x30
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227841]  [<f842e189>] zram_slot_free_notify+0x29/0x50 [zram]
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227850]  [<f842e160>] ? zram_stat64_inc+0x30/0x30 [zram]
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227857]  [<c1137fa9>] swap_entry_free+0xd9/0x160
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227862]  [<c15e1d00>] ? rwsem_down_failed_common+0xe0/0xf0
 Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227870]  [<c1138b88>] swap_free+0x28/0x40
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227875]  [<c11279e2>] do_swap_page+0x3a2/0x6a0
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227881]  [<c1129282>] handle_pte_fault+0x232/0x2c0
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227886]  [<c112a022>] handle_mm_fault+0x1e2/0x280
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227892]  [<c15e5578>] do_page_fault+0x158/0x4c0
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227899]  [<c1092f6b>] ? ktime_get_ts+0xeb/0x120
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227905]  [<c12db72f>] ? __copy_to_user_ll+0x1f/0x40
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227911]  [<c12db790>] ? copy_to_user+0x40/0x60
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227916]  [<c1066598>] ? sys_clock_gettime+0x48/0x70
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227921]  [<c15e5420>] ? vmalloc_fault+0x195/0x195
Aug 28 08:04:04 nityanand-Vostro-1500 kernel: [38954.227927]  [<c15e2843>] error_code+0x67/0x6c
Aug 28 08:04:11 nityanand-Vostro-1500 kernel: [38961.380611] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Aug 28 08:05:46 nityanand-Vostro-1500 kernel: [39056.104110] BUG: scheduling while atomic: dbus-daemon/2176/0x00000001
Aug 28 08:05:46 nityanand-Vostro-1500 kernel: [39056.104116] Modules linked in: nls_iso8859_1 usb_storage pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) dm_crypt rfcomm bnep parport_pc bluetooth ppdev binfmt_misc joydev snd_hda_codec_idt snd_hda_intel coretemp arc4 snd_hda_codec r852 uvcvideo snd_usb_audio sm_common nand snd_hwdep videobuf2_core nand_ids snd_usbmidi_lib videodev psmouse dell_laptop dell_wmi videobuf2_vmalloc r592 mtd b43 snd_pcm videobuf2_memops dm_multipath nand_bch gpio_ich snd_seq_midi bch scsi_dh sparse_keymap snd_seq_midi_event microcode snd_rawmidi snd_seq memstick serio_raw dcdbas nand_ecc snd_timer mac_hid snd_seq_device mac80211 snd cfg80211 soundcore snd_page_alloc bcma lpc_ich ssb_hcd lp parport dm_raid45 xor dm_mirror dm_region_hash dm_log btrfs zlib_deflate libcrc32c b44 hid_generic sdhci_pci firewire_ohci sdhci firewire_core crc_itu_t usbhid hid wmi ssb i915 drm_kms_helper drm i2c_algo_bit video zram(C)
Aug 28 08:05:46 nityanand-Vostro-1500 kernel: [39056.104238] Pid: 2176, comm: dbus-daemon Tainted: G        WC O 3.5.0-40-generic #62~precise1-Ubuntu
Aug 28 08:05:46 nityanand-VoAug 28 08:13:14 nityanand-Vostro-1500 kernel: imklog 5.8.6, log source = /proc/kmsg started.

---

### Post by tgalati4 on 2013-08-28
How old is the machine?  It looks like you have a hardware problem.  Such a problem will spit out different errors because they are happening in a random fashion.  Does this machine dual-boot?  If so, does it happen in both operating systems?

Try a LiveDVD or USB and boot from that.  See how long the machine stays up.  If it freezes when running from RAM, then you likely have a hardware problem.  The machine may need cleaning and reseating of RAM and cables.

---

### Post by rock2 on 2013-08-28
Are you using Chrome as a browser? I have 12.04.1 installed and it freezes when i open Chrome. But it generally unfreezes after 2 minutes or so.

---

### Post by nns2006 on 2013-08-28
> **tgalati4 said:**
> How old is the machine?  It looks like you have a hardware problem.  Such a problem will spit out different errors because they are happening in a random fashion.  Does this machine dual-boot?  If so, does it happen in both operating systems?

Try a LiveDVD or USB and boot from that.  See how long the machine stays up.  If it freezes when running from RAM, then you likely have a hardware problem.  The machine may need cleaning and reseating of RAM and cables.

It is 7 years old dell vostro 1500 laptop. It is dual boot with windows7 and Ubuntu 12.04.2 both 32bit. It happens only in Ubuntu as far as I can remember as I use windows very seldom for some official work. There I haven't encountered this problem. Actually I think this problem first started with freezing at shutdown and now it is freezing very frequently and randomly. At that time ```
sudo shutdown -P now
``` solved the shutdown problem. BUt now I have no idea what is wrong. 

You mean to say I should use live session to test if it freezes in there or not. How long one can see this?

---

### Post by nns2006 on 2013-08-28
> **rock2 said:**
> Are you using Chrome as a browser? I have 12.04.1 installed and it freezes when i open Chrome. But it generally unfreezes after 2 minutes or so.

No, I use firefox. But it happens to me even when I am using synaptic to install or updating the ubuntu or opening a folder. So it is completely random.

---

### Post by sceptre78 on 2013-08-28
could it be a hard drive related issue, The times he claims it happens is when the HDD is being read or written too.

-Installing
-transferring files
-plugging in usb hdd
-booting/shutting down

all of which puts a load on the drives even if for a moment.

---

### Post by eternal243 on 2013-08-28
Well, try to use a live cd for a bit as suggested, try all the tasks on the live cd that usually makes your system to freeze(synaptics/plugin usb drive/whatever). If it freezes in on the live cd/usb, then it might be a problem on your ram-memory, if it doesn't it might be a harddrive problem. If it is the harddrive, it could be a damaged sector, which would explain why it happens in linux and not in windows, implying that linux is installed over the damaged sector.

You could also try to run a memory-test.

---

### Post by nns2006 on 2013-08-29
> **eternal243 said:**
> Well, try to use a live cd for a bit as suggested, try all the tasks on the live cd that usually makes your system to freeze(synaptics/plugin usb drive/whatever). If it freezes in on the live cd/usb, then it might be a problem on your ram-memory, if it doesn't it might be a harddrive problem. If it is the harddrive, it could be a damaged sector, which would explain why it happens in linux and not in windows, implying that linux is installed over the damaged sector.

You could also try to run a memory-test.

I did check with live-USB there was no freezing on that neither it was on my laptop today. (may be it got scared that I am going to wipe it out :P again). memory test does not give any error. All test pass.  

All programs which has caused freezing yesterday is not causing it to freeze today! There is absolutely no change ubuntu besides installation/uninstallation of Wine. 
Now, I am really confused. I will post log file once I get freezing again. (I hope this time never come, hoping against hope?)

---

### Post by nns2006 on 2013-09-01
Hello,
Yesterday, I have installed ubuntu 13.04. Since then I have kept my laptop ON doing all the stuff (including putting external hard disk, USB, running mutilple programs and 18-20 prgrams ans several windows!!) which were causing 12.04 to freeze. To my surprise, ubuntu 13.04 is not only fast but also gives no freezing to me. So, I conclude it was something with 12.04 and some of programs which I might have installed.

Thankyou everyone for your replies and support.

---

### Post by Thomas_Dejanovic on 2013-09-03
hi all,

not sure how this is marked as solved.  installing 13.04 is not really a solution.

anyway, I'm having the same problem.  I've rebuilt the machine twice, new motherboard, memory, drives in varying combinations.

nothing interesting in syslog.  it just ends and starts again when I reboot.

nothing in kern.log, again just ends and starts again when I reboot.

freezing up is highly correlated with using chrome.  I'm not certain but it could have frozen once or twice before while was using lyx.


any help would be appreciated.

Regards, Thomas D.

---

