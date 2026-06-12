---
title: "Ubuntu freezing inevitably and randomly"
date: 2017-07-31
forum: New to Ubuntu
---

### Post by ethanweegee on 2017-07-31
I am new to Linux, please keep this in mind! Thanks!

Recently, I installed Ubuntu (ubuntu-16.04.2-desktop-amd64.iso from the downloads page; used Rufus and a 16GB USB flash drive) on my HDD alongside Windows 10 on my Dell Inspiron 20 3052 (Preinstalled with W10). 'Try without installing' worked fine, out of the box, so I installed it. When I rebooted, it was still fine. I didn't install anything. I left my computer on for the night. I rebooted to Windows 10 in the morning, and upon booting back into ubuntu, it freezes at the loading screen. (The logo and dots) I force shut down and try again. This time, it freezes after logging in, without a desktop ever appearing. Force shut down, try again, and this time it freezes before the login page appears. Next time, I got in and started an update. It was downloading, when I started typing in the search and the system froze again. Never do the mouse and keyboard actually *do* anything. The mouse LED actually goes off after a minute or so.

I know that logs are probably important, but I don't have access to the partition (Since it is in ext4) and I wouldn't know what to look for if I had access. If anyone can tell me *how* to get logs, I'll go look for them. I still have my Live USB, and Windows 10 is working. Any help is appreciated, thank you!

---

### Post by QIII on 2017-07-31
Hello!

First things first:  did you check the md5sum after downloading?  Some issues may only become evident after installation if your image is corrupt.

---

### Post by ethanweegee on 2017-07-31
> **QIII said:**
> Hello!

First things first:  did you check the md5sum after downloading?  Some issues may only become evident after installation if your image is corrupt.
Here is what I got:
```
MD5 hash of file ubuntu-16.04.2-desktop-amd64.iso:
1400884cec8e40a1a876b2678f81494b
CertUtil: -hashfile command completed successfully.


```
I couldn't find any place to verify this, so if this isn't correct, let me know.

---

### Post by QIII on 2017-07-31
For future reference, [http://releases.ubuntu.com/16.04/MD5SUMS](http://releases.ubuntu.com/16.04/MD5SUMS)

Just replace the release number when you download.

You are getting the right hash.

Next:  Can you tell us the specs of your machine?  (Generally not a good idea to ask people to go look it up, but I did.)  Specifications can and do change during the manufacturing lifetime of a model.

---

### Post by ethanweegee on 2017-07-31
> **QIII said:**
> For future reference, [http://releases.ubuntu.com/16.04/MD5SUMS](http://releases.ubuntu.com/16.04/MD5SUMS)

Just replace the release number when you download.

You are getting the right hash.

Next:  Can you tell us the specs of your machine?  (Generally not a good idea to ask people to go look it up, but I did.)  Specifications can and do change during the manufacturing lifetime of a model.
Not sure *exactly* what to put here, so I included a report from dxdiag in case.
CPU: Intel Pentium Inside; 1.6GHz, Quad Core 64-Bit
4GB RAM
Intel HD Graphics (Ubuntu reported which version, but I didn't record that)
500GB HDD
I double checked, and the swap partition is there; [https://puu.sh/wYgrG/709d55538a.png](https://puu.sh/wYgrG/709d55538a.png)
DxDiag report: [https://puu.sh/wYgAb/5eac863542.txt](https://puu.sh/wYgAb/5eac863542.txt)

---

### Post by ethanweegee on 2017-08-01
I just went into recovery mode and tried 'fix filesystem.' Well, it booted, and I was about to comment that it hadn't frozen, (In ubuntu) when it did just that.
Funny, huh?
I got a screenshot of the system details before that happened, however. (And saved it to my C: drive)
It reports Intel HD Graphics 405: [https://puu.sh/wYtji/a24fa47342.png](https://puu.sh/wYtji/a24fa47342.png)
**EDIT:**  Also, unrelated but every time I boot into ubuntu and back into Windows 10, the time is off by 4 hours. Nothing huge but it's annoying, and what fixes *that?*

---

### Post by BenginM on 2017-08-01
Hiya , since this is a fresh install, i would like to save you from the headaches of troubleshooting X and debuggin' the kernel!

[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)
[https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging)
[https://wiki.ubuntu.com/Kernel/KernelDebuggingTricks](https://wiki.ubuntu.com/Kernel/KernelDebuggingTricks)


 .. with the 16.04 desktop image and from the screenshot of the GPU Intel HD Graphics 405 (Braswell) , we see that you're using the Unity desktop , witch is heavy like KDE & Gnome, with your machine specs .. i suggest trying Xubuntu or lubuntu , they're lightweight desktop entertainments , i haven't tried ubuntu-mate or ubuntu-Budgie  .

[https://www.ubuntu.com/download/ubuntu-flavours](https://www.ubuntu.com/download/ubuntu-flavours)

[https://xubuntu.org/getxubuntu/#lts](https://xubuntu.org/getxubuntu/#lts)

[http://lubuntu.me/downloads/](http://lubuntu.me/downloads/)

I usually go with a minimal installation using the mini netboot iso ...

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

check the hashes .. 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

cat or dd the iso to usb ..

connect to wired ethernet. and it goes like this...

[https://www.youtube.com/watch?v=U42Ln3k7VK0](https://www.youtube.com/watch?v=U42Ln3k7VK0)

when i reach the software selection screen , i highlight and select either Xubuntu-desktop package or lubuntu-desktop by pressing the space key ... i end up with a minimal system.

---

### Post by ethanweegee on 2017-08-01
> **BenginM said:**
> Hiya , since this is a fresh install, i would like to save you from the headaches of troubleshooting X and debuggin' the kernel!

[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)
[https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging)
[https://wiki.ubuntu.com/Kernel/KernelDebuggingTricks](https://wiki.ubuntu.com/Kernel/KernelDebuggingTricks)


 .. with the 16.04 desktop image and from the screenshot of the GPU Intel HD Graphics 405 (Braswell) , we see that you're using the Unity desktop , witch is heavy like KDE & Gnome, with your machine specs .. i suggest trying Xubuntu or lubuntu , they're lightweight desktop entertainments , i haven't tried ubuntu-mate or ubuntu-Budgie  .

[https://www.ubuntu.com/download/ubuntu-flavours](https://www.ubuntu.com/download/ubuntu-flavours)

[https://xubuntu.org/getxubuntu/#lts](https://xubuntu.org/getxubuntu/#lts)

[http://lubuntu.me/downloads/](http://lubuntu.me/downloads/)

I usually go with a minimal installation using the mini netboot iso ...

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

check the hashes .. 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

cat or dd the iso to usb ..

connect to wired ethernet. and it goes like this...

[https://www.youtube.com/watch?v=U42Ln3k7VK0](https://www.youtube.com/watch?v=U42Ln3k7VK0)

when i reach the software selection screen , i highlight and select either Xubuntu-desktop package or lubuntu-desktop by pressing the space key ... i end up with a minimal system.
Seriously, you are telling me that my system is underpowered? I believe you, but this is the most powerful system I have...
The mini version was very confusing to install, so I didn't bother. I'm downloading xubuntu right now, but my internet is slow.

Anyway, I have access to the log files now, and pulled 'syslog' for troubleshooting. If more are required, let me know.
(syslog) [https://puu.sh/wYZu2/ea29ded369](https://puu.sh/wYZu2/ea29ded369)
It frequently freezes at the screen with black and a cursor. I got an admittedly funny crash when the startup sound looped as well.
**EDIT:** (kern.log) [https://puu.sh/wZ0iU/62ddce002e.log](https://puu.sh/wZ0iU/62ddce002e.log)

---

### Post by ethanweegee on 2017-08-02
So, I replaced my keyboard with one with the sysrq key (Since it's kind of important and my old one didn't have one) and then I booted successfully and did this:
[https://askubuntu.com/a/796484](https://askubuntu.com/a/796484)
Not sure which fixed it :P   Hasn't crashed after 30 minutes where it usually crashes in the first 5. Even won a chess game.
I'm going to wait and see if anything really fixed.

---

### Post by BenginM on 2017-08-02
So you think you're hitting [this bug]("https://bugzilla.kernel.org/show_bug.cgi?id=109051") with your CPU!

---

### Post by ethanweegee on 2017-08-02
> **BenginM said:**
> So you think you're hitting [this bug]("https://bugzilla.kernel.org/show_bug.cgi?id=109051") with your CPU!
Honestly, I don't know. Maybe. But if it works (And for what it's worth, still hasn't crashed) then that's fine by me.
I have installed chess, VLC, and other minor packages with no problem.
But more importantly, this bug is from 2015, and hasn't been patched?! Why not? And how do I tell that this bug **is** the problem?

---

### Post by ethanweegee on 2017-08-02
It finally crashed again! Guess this isn't *much* of a solution... Anything else I can try?
This comment:

[COLOR=#000000][FONT=Verdana]**   Vladimir Jicha 2015-12-08 10:13:29 UTC**[/FONT][/COLOR]
   For me setting max_cstate=1 didn't solve the bug. It improved the time to freeze from a couple of minutes to a couple of hours. But it is not a fully and universally working workaround.

And it still is crashing upon boot occasionally! Argh...

---

### Post by BenginM on 2017-08-02
Is this now happeinng in Xubuntu ..!

you may want to test the behaviour booting with a newer kernel ..

you can truobleshoot/debug this if you want..

[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

[https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html](https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html)

[URL="https://wiki.ubuntu.com/Kernel/CrashdumpRecipe"]https://wiki.ubuntu.com/Kernel/CrashdumpRecipe

[https://wiki.ubuntu.com/DebuggingKernelOops](https://wiki.ubuntu.com/DebuggingKernelOops)


[/URL]https://stackoverflow.com/questions/4943857/linux-kernel-live-debugging-how-its-done-and-what-tools-are-used/42316607#42316607


## this is the interesting bits in the kern.log ..

```

Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.060263] dpm_run_callback(): platform_pm_resume+0x0/0x50 returns -19
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.060270] PM: Device i8042 failed to resume: error -19
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.061788] sd 0:0:0:0: [sda] Starting disk
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.070439] r8169 0000:03:00.0 enp3s0: link down
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.081931] ------------[ cut here ]------------
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082004] WARNING: CPU: 1 PID: 3405 at /build/linux-hwe-eyfT8D/linux-hwe-4.8.0/drivers/gpu/drm/i915/intel_uncore.c:802 __unclaimed_reg_debug+0x4f/0x60 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082006] Unclaimed read from register 0x1e1110
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082068] Modules linked in: ccm rfcomm bnep nls_iso8859_1 rtsx_usb_ms memstick dell_wmi dell_wmi_aio dell_smbios sparse_keymap dcdbas dell_smm_hwmon intel_rapl coretemp kvm_intel kvm uvcvideo arc4 irqbypass rtl8723be videobuf2_vmalloc videobuf2_memops btcoexist rtl8723_common rtl_pci videobuf2_v4l2 videobuf2_core punit_atom_debug rtlwifi videodev mac80211 crct10dif_pclmul media crc32_pclmul ghash_clmulni_intel aesni_intel hid_multitouch joydev aes_x86_64 cfg80211 lrw glue_helper snd_hda_codec_realtek snd_intel_sst_acpi snd_hda_codec_generic snd_soc_rt5670 snd_soc_rl6231 ablk_helper cryptd intel_cstate snd_hda_intel input_leds snd_hda_codec serio_raw snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_sst_match btusb snd_hda_core btrtl snd_soc_core snd_hwdep snd_seq_midi snd_seq_midi_event snd_rawmidi snd_compress snd_seq ac97_bus hci_uart snd_pcm_dmaengine snd_seq_device snd_pcm btbcm btqca lpc_ich btintel nxp_nci_i2c bluetooth snd_timer nxp_nci snd nci shpchp nfc soundcore rfkill_gpio dwc3 mei_txe processor_thermal_device mei udc_core intel_soc_dts_iosf ulpi 8250_dw i2c_designware_platform i2c_designware_core dw_dmac dw_dmac_core spi_pxa2xx_platform int3400_thermal acpi_thermal_rel int3403_thermal int340x_thermal_zone int3406_thermal pwm_lpss_platform pwm_lpss tpm_crb mac_hid parport_pc ppdev lp parport autofs4 hid_generic rtsx_usb_sdmmc rtsx_usb i915 i2c_algo_bit drm_kms_helper syscopyarea psmouse sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi fjes video i2c_hid sdhci_acpi sdhci pinctrl_cherryview usbhid hid
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082129] CPU: 1 PID: 3405 Comm: kworker/u8:23 Not tainted 4.8.0-36-generic #36~16.04.1-Ubuntu
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082130] Hardware name: Dell Inc. Inspiron 20-3052/0C2YT8, BIOS 3.8.3 05/16/2017
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082139] Workqueue: events_unbound async_run_entry_fn
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082144]  0000000000000086 0000000071720d63 ffff8c35b7a23ba0 ffffffffbde2d7b3
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082148]  ffff8c35b7a23bf0 0000000000000000 ffff8c35b7a23be0 ffffffffbda8313b
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082152]  00000322b7a23c10 0000000000000000 00000000001e1110 0000000000000001
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082153] Call Trace:
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082160]  [<ffffffffbde2d7b3>] dump_stack+0x63/0x90
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082164]  [<ffffffffbda8313b>] __warn+0xcb/0xf0
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082168]  [<ffffffffbda831bf>] warn_slowpath_fmt+0x5f/0x80
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082172]  [<ffffffffbdaaf012>] ? wake_up_q+0x32/0x70
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082219]  [<ffffffffc054f94f>] __unclaimed_reg_debug+0x4f/0x60 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082265]  [<ffffffffc05549db>] chv_read32+0x32b/0x360 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082270]  [<ffffffffbe293dab>] ? mutex_unlock+0x1b/0x20
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082309]  [<ffffffffc04fca15>] i915_hpd_irq_setup+0xa5/0x100 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082356]  [<ffffffffc05898b2>] intel_hpd_init+0x72/0x90 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082395]  [<ffffffffc04f5fcf>] i915_drm_resume+0xef/0x180 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082433]  [<ffffffffc04f607e>] i915_pm_restore+0x1e/0x30 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082471]  [<ffffffffc04f60ae>] i915_pm_resume+0xe/0x10 [i915]
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082475]  [<ffffffffbde83d44>] pci_pm_resume+0x64/0xa0
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082477]  [<ffffffffbde83ce0>] ? pci_pm_thaw+0x90/0x90
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082481]  [<ffffffffbdfa7ebe>] dpm_run_callback+0x4e/0x130
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082484]  [<ffffffffbdfa8453>] device_resume+0xd3/0x1f0
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082486]  [<ffffffffbdfa858d>] async_resume+0x1d/0x50
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082488]  [<ffffffffbdaa6aa7>] async_run_entry_fn+0x37/0x150
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082492]  [<ffffffffbda9d8eb>] process_one_work+0x16b/0x4a0
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082494]  [<ffffffffbda9dc6b>] worker_thread+0x4b/0x500
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082497]  [<ffffffffbda9dc20>] ? process_one_work+0x4a0/0x4a0
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082500]  [<ffffffffbdaa4008>] kthread+0xd8/0xf0
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082504]  [<ffffffffbe29679f>] ret_from_fork+0x1f/0x40
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082507]  [<ffffffffbdaa3f30>] ? kthread_create_on_node+0x1e0/0x1e0
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.082509] ---[ end trace 83de94d81b070037 ]---
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.374429] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.382165] ata2.00: configured for UDMA/100
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.403814] usb 1-5: reset high-speed USB device number 4 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.663770] usb 1-4: reset high-speed USB device number 3 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  937.923275] usb 1-3: reset full-speed USB device number 2 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  938.144152] usb 1-5.4: reset high-speed USB device number 7 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  938.323802] usb 1-5.1: reset high-speed USB device number 5 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  938.504071] usb 1-5.2: reset full-speed USB device number 6 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  938.871927] usb 1-5.4.3: reset low-speed USB device number 9 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.428177] usb 1-5.4.2: reset low-speed USB device number 8 using xhci_hcd
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.539541] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.606450] ata1.00: configured for UDMA/133
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.731891] PM: resume of devices complete after 2682.356 msecs
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.732181] usb 1-5.2:1.0: rebind failed: -517
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.732199] usb 1-5.2:1.1: rebind failed: -517
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.733285] PM: Finishing wakeup.
Jul 31 12:16:19 ethan-Inspiron-20-3052 kernel: [  939.733293] Restarting tasks ... done.
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.247602] ------------[ cut here ]------------
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.247810] WARNING: CPU: 3 PID: 1065 at /build/linux-hwe-eyfT8D/linux-hwe-4.8.0/drivers/gpu/drm/i915/intel_display.c:13711 intel_atomic_commit_tail+0x1093/0x10a0 [i915]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.247816] pipe A vblank wait timed out
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.247820] Modules linked in: ccm rfcomm bnep nls_iso8859_1 rtsx_usb_ms memstick dell_wmi dell_wmi_aio dell_smbios sparse_keymap dcdbas dell_smm_hwmon intel_rapl coretemp kvm_intel kvm uvcvideo arc4 irqbypass rtl8723be videobuf2_vmalloc videobuf2_memops btcoexist rtl8723_common rtl_pci videobuf2_v4l2 videobuf2_core punit_atom_debug rtlwifi videodev mac80211 crct10dif_pclmul media crc32_pclmul ghash_clmulni_intel aesni_intel hid_multitouch joydev aes_x86_64 cfg80211 lrw glue_helper snd_hda_codec_realtek snd_intel_sst_acpi snd_hda_codec_generic snd_soc_rt5670 snd_soc_rl6231 ablk_helper cryptd intel_cstate snd_hda_intel input_leds snd_hda_codec serio_raw snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_sst_match btusb snd_hda_core btrtl snd_soc_core snd_hwdep snd_seq_midi snd_seq_midi_event snd_rawmidi snd_compress snd_seq ac97_bus hci_uart snd_pcm_dmaengine snd_seq_device snd_pcm btbcm btqca lpc_ich btintel nxp_nci_i2c bluetooth snd_timer nxp_nci snd nci shpchp nfc soundcore rfkill_gpio dwc3 mei_txe processor_thermal_device mei udc_core intel_soc_dts_iosf ulpi 8250_dw i2c_designware_platform i2c_designware_core dw_dmac dw_dmac_core spi_pxa2xx_platform int3400_thermal acpi_thermal_rel int3403_thermal int340x_thermal_zone int3406_thermal pwm_lpss_platform pwm_lpss tpm_crb mac_hid parport_pc ppdev lp parport autofs4 hid_generic rtsx_usb_sdmmc rtsx_usb i915 i2c_algo_bit drm_kms_helper syscopyarea psmouse sysfillrect sysimgblt fb_sys_fops r8169 mii drm ahci libahci wmi fjes video i2c_hid sdhci_acpi sdhci pinctrl_cherryview usbhid hid
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248264] CPU: 3 PID: 1065 Comm: Xorg Tainted: G        W       4.8.0-36-generic #36~16.04.1-Ubuntu
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248269] Hardware name: Dell Inc. Inspiron 20-3052/0C2YT8, BIOS 3.8.3 05/16/2017
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248280]  0000000000000286 000000003538021d ffff8c35b920fa90 ffffffffbde2d7b3
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248300]  ffff8c35b920fae0 0000000000000000 ffff8c35b920fad0 ffffffffbda8313b
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248317]  0000358fc0579635 0000000000000000 0000000000000000 ffff8c35b27f0000
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248334] Call Trace:
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248356]  [<ffffffffbde2d7b3>] dump_stack+0x63/0x90
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248371]  [<ffffffffbda8313b>] __warn+0xcb/0xf0
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248384]  [<ffffffffbda831bf>] warn_slowpath_fmt+0x5f/0x80
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248397]  [<ffffffffbdac7025>] ? finish_wait+0x55/0x70
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248575]  [<ffffffffc05772a3>] intel_atomic_commit_tail+0x1093/0x10a0 [i915]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248588]  [<ffffffffbdac74d0>] ? wake_atomic_t_function+0x60/0x60
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248765]  [<ffffffffc05776f0>] intel_atomic_commit+0x440/0x570 [i915]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248874]  [<ffffffffc04046c7>] ? drm_atomic_check_only+0x187/0x610 [drm]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.248927]  [<ffffffffc04c40b9>] ? __drm_atomic_helper_crtc_duplicate_state+0x89/0xa0 [drm_kms_helper]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249028]  [<ffffffffc0404b87>] drm_atomic_commit+0x37/0x60 [drm]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249079]  [<ffffffffc04c4f6d>] drm_atomic_helper_connector_dpms+0xed/0x1a0 [drm_kms_helper]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249176]  [<ffffffffc03f8dcd>] drm_mode_obj_set_property_ioctl+0x23d/0x250 [drm]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249273]  [<ffffffffc03f8e1f>] drm_mode_connector_property_set_ioctl+0x3f/0x60 [drm]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249294]  [<ffffffffc0c0c0c0>] ? rtl8723be_dm_watchdog+0x420/0x11c0 [rtl8723be]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249377]  [<ffffffffc03e9d67>] drm_ioctl+0x1e7/0x4c0 [drm]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249473]  [<ffffffffc03f8de0>] ? drm_mode_obj_set_property_ioctl+0x250/0x250 [drm]
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249489]  [<ffffffffbda3a60b>] ? __fpu__restore_sig+0x7b/0x590
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249503]  [<ffffffffbdc47861>] do_vfs_ioctl+0xa1/0x5f0
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249515]  [<ffffffffbdc47e29>] SyS_ioctl+0x79/0x90
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249532]  [<ffffffffbe296576>] entry_SYSCALL_64_fastpath+0x1e/0xa8
Jul 31 12:16:20 ethan-Inspiron-20-3052 kernel: [  940.249540] ---[ end trace 83de94d81b070038 ]---
Jul 31 12:16:21 ethan-Inspiron-20-3052 kernel: [  941.332825] i8042: Can't write CTR while closing KBD port
Jul 31 12:16:21 ethan-Inspiron-20-3052 kernel: [  941.864035] i8042: Can't reactivate KBD port
Jul 31 12:16:23 ethan-Inspiron-20-3052 kernel: [  942.927050] i8042: Can't write CTR while closing KBD port
Jul 31 12:16:23 ethan-Inspiron-20-3052 kernel: [  943.458152] i8042: Can't reactivate KBD port

```


[https://puu.sh/wZ0iU/62ddce002e.log](https://puu.sh/wZ0iU/62ddce002e.log)

---

### Post by ethanweegee on 2017-08-02
Ah, completely forgot about xubuntu! Well, I never finished the download (Was downloading on the same machine and had it paused for 75% of the day) but I'm resuming it and will install and report back tomorrow.

---

### Post by ethanweegee on 2017-08-02
It seems as though xubuntu works fine. No crashes so far! I like the user interface, but ubuntu was so much prettier! :P
**EDIT: **Well, it just crashed... Bummer.

---

### Post by BenginM on 2017-08-02
This is an unfortunate situation , and as it appears to be a kernel bug , so your best bit is to report a bug 

in terminal run :
ubuntu-bug linux

set the title to something like " Xbuntu system freeze/crashes with Intel atomic 1915/drm "

you'll be asked to collect more information with apport , and probable test a mainnline kernel , so lets get ahead of the game ..

after you report with a ubuntu-bug linux , run apport-collect -p linux <replace-with-bug-number>


test the latest upstream kernel available following [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds) ? It will allow additional upstream developers to examine the issue. do not test the kernel in the daily folder, but the one all the way at the bottom. [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
 Once you've tested the upstream kernel, please comment on which kernel version specifically you tested and remove the 'needs-upstream-testing' tag. This can be done by clicking on the yellow pencil icon next to the tag located at the bottom of the bug description and deleting the 'needs-upstream-testing' text.

If this bug is fixed in the mainline kernel, please add the following tag 'kernel-fixed-upstream-VERSION-NUMBER', where VERSION-NUMBER is the version number of the kernel you tested.

If the mainline kernel does not fix this bug, please add the tag: 'kernel-bug-exists-upstream-VERSION-NUMBER', where VERSION-NUMBER is the version number of the kernel you tested.

If you are unable to test the mainline kernel, please comment as to why specifically you were unable to test it and add the tag: 'kernel-unable-to-test-upstream'.

[https://wiki.ubuntu.com/Bugs/Upstream/kernel](https://wiki.ubuntu.com/Bugs/Upstream/kernel)

## Helpful Bug Reporting Links:
[https://wiki.ubuntu.com/ReportingBugs](https://wiki.ubuntu.com/ReportingBugs).
[https://help.ubuntu.com/community/ReportingBugs#A3._Make_sure_the_bug_hasn.27t_already_been_reported](https://help.ubuntu.com/community/ReportingBugs#A3._Make_sure_the_bug_hasn.27t_already_been_reported)
[https://help.ubuntu.com/community/ReportingBugs#Adding_Apport_Debug_Information_to_an_Existing_Launchpad_Bug](https://help.ubuntu.com/community/ReportingBugs#Adding_Apport_Debug_Information_to_an_Existing_Launchpad_Bug)
[URL="https://help.ubuntu.com/community/ReportingBugs#Adding_Additional_Attachments_to_an_Existing_Launchpad_Bug"]https://help.ubuntu.com/community/ReportingBugs#Adding_Additional_Attachments_to_an_Existing_Launchpad_Bug
[/URL]
the official Ubuntu documentation:
Ubuntu Bug Control and Ubuntu Bug Squad: [https://wiki.ubuntu.com/Bugs/BestPractices#X.2BAC8-Reporting.Focus_on_One_Issue](https://wiki.ubuntu.com/Bugs/BestPractices#X.2BAC8-Reporting.Focus_on_One_Issue)
Ubuntu Kernel Team: [https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies#Filing_Kernel_Bug_reports](https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies#Filing_Kernel_Bug_reports)
Ubuntu Community: [https://help.ubuntu.com/community/ReportingBugs#Bug_reporting_etiquette](https://help.ubuntu.com/community/ReportingBugs#Bug_reporting_etiquette)

---

### Post by ethanweegee on 2017-08-02
I'm going to be honest here; I have no idea exactly how to do what you just explained.
That being said, I did create the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-hwe/+bug/1708191](https://bugs.launchpad.net/ubuntu/+source/linux-hwe/+bug/1708191)
And you suggested testing later kernels? I am not sure how to do that from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/)
Also, I reapplied the fix from before, in the hopes that it will fix [I]something.

[/I]**EDIT: **The previous workaround didn't fix the crashing and I still eventually crashed. Unlike ubuntu, this time it doesn't seem to have an effect on how *long *it takes to freeze, interestingly.

**EDIT 2:** I looked up the bug you had linked before. Do you think disabling SpeedStep can fix the problem?
[B]
EDIT 3:[/B] It hasn't crashed for a few hours! Yay! I didn't change, do, or configure anything, so it's probably a streak of luck.

---

### Post by BenginM on 2017-08-02
That's understandable , you did a good job failing the bug report , some users wont even bother to and will just drop the OS .. so now that you bug is reported, it's time to install and test a mainline kernel , will use the .debs files from [URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/"]http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/ 
[/URL]as advised by [Andy Whitcroft (apw)]("https://launchpad.net/%7Eapw") in freenode #ubuntu-kernel IRC channel.
 
For 32 bit systems, download and install the i386 debs. For 64 bit systems, download and install the amd64 packages:

$ cd /tmp

$ wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/linux-headers-4.13.0-041300rc3_4.13.0-041300rc3.201707301631_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/linux-headers-4.13.0-041300rc3_4.13.0-041300rc3.201707301631_all.deb) & wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/linux-headers-4.13.0-041300rc3-generic_4.13.0-041300rc3.201707301631_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/linux-headers-4.13.0-041300rc3-generic_4.13.0-041300rc3.201707301631_amd64.deb) & wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/linux-image-4.13.0-041300rc3-generic_4.13.0-041300rc3.201707301631_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13-rc3/linux-image-4.13.0-041300rc3-generic_4.13.0-041300rc3.201707301631_amd64.deb)

install the kernel ...

$ sudo dpkg -i linux-headers-4.13*.deb linux-image-4.13*.deb

make sure it updates grub , if not run $ sudo update-grub

then reboot and from grub menu select the new 4.13-rc3 .. and test it 

later will dell with this bit :

```

Once you've tested the upstream kernel, please comment on which kernel  version specifically you tested and remove the 'needs-upstream-testing'  tag. This can be done by clicking on the yellow pencil icon next to the  tag located at the bottom of the bug description and deleting the  'needs-upstream-testing' text.

If this bug is fixed in the mainline kernel, please add the following  tag 'kernel-fixed-upstream-VERSION-NUMBER', where VERSION-NUMBER is the  version number of the kernel you tested.

If the mainline kernel does not fix this bug, please add the tag:  'kernel-bug-exists-upstream-VERSION-NUMBER', where VERSION-NUMBER is the  version number of the kernel you tested.

If you are unable to test the mainline kernel, please comment as to why  specifically you were unable to test it and add the tag:  'kernel-unable-to-test-upstream'.

```

am not sure if disabling SpeedStep would help ..

BTW, which CPU exactly is it ..
$ sudo lshw -C CPU
and which driver is in use for the Intel GPU
$ inxi -G
also have look at the BIOS reversion 
$ inxi -M

---

### Post by BenginM on 2017-08-02
see andy's comment , keep an eye on 

[https://bugs.launchpad.net/ubuntu/+source/linux-hwe/+bug/1708191](https://bugs.launchpad.net/ubuntu/+source/linux-hwe/+bug/1708191)

---

### Post by ethanweegee on 2017-08-03
```
ethan@ethan-Inspiron-20-3052:~/Desktop$ sudo lshw -c CPU[sudo] password for ethan: 
  *-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) CPU  N3700  @ 1.60GHz
       vendor: Intel Corp.
       physical id: 39
       bus info: cpu@0
       version: Intel(R) Pentium(R) CPU N3700 @ 1.60GHz
       slot: SOCKET 0
       size: 1830MHz
       capacity: 2400MHz
       width: 64 bits
       clock: 80MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
       configuration: cores=4 enabledcores=4 threads=4
ethan@ethan-Inspiron-20-3052:~/Desktop$ inxi -G
Graphics:  Card: Intel Device 22b1
           Display Server: X.Org 1.19.3 drivers: (unloaded: fbdev,vesa)
           Resolution: 1600x900@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 405 (Braswell)
           GLX Version: 3.0 Mesa 17.0.7
ethan@ethan-Inspiron-20-3052:~/Desktop$ inxi -M
Machine:   System: Dell product: Inspiron 20-3052 v: 3.8.3
           Mobo: Dell model: 0C2YT8 v: A00
           Bios: Dell v: 3.8.3 date: 05/16/2017
```
I'm going to try updating the kernel now.
By the way, is there any way to tell if it worked right away, besides "Wait for a crash?"
[B]
EDIT 1: [/B]During the installation, this warning occurred:
```
ethan@ethan-Inspiron-20-3052:/tmp$ sudo dpkg -i linux-headers-4.13*.deb linux-image-4.13*.deb[sudo] password for ethan: 
Selecting previously unselected package linux-headers-4.13.0-041300rc3.
(Reading database ... 199424 files and directories currently installed.)
Preparing to unpack linux-headers-4.13.0-041300rc3_4.13.0-041300rc3.201707301631_all.deb ...
Unpacking linux-headers-4.13.0-041300rc3 (4.13.0-041300rc3.201707301631) ...
Selecting previously unselected package linux-headers-4.13.0-041300rc3-generic.
Preparing to unpack linux-headers-4.13.0-041300rc3-generic_4.13.0-041300rc3.201707301631_amd64.deb ...
Unpacking linux-headers-4.13.0-041300rc3-generic (4.13.0-041300rc3.201707301631) ...
Selecting previously unselected package linux-image-4.13.0-041300rc3-generic.
Preparing to unpack linux-image-4.13.0-041300rc3-generic_4.13.0-041300rc3.201707301631_amd64.deb ...
Done.
Unpacking linux-image-4.13.0-041300rc3-generic (4.13.0-041300rc3.201707301631) ...
Setting up linux-headers-4.13.0-041300rc3 (4.13.0-041300rc3.201707301631) ...
Setting up linux-headers-4.13.0-041300rc3-generic (4.13.0-041300rc3.201707301631) ...
Setting up linux-image-4.13.0-041300rc3-generic (4.13.0-041300rc3.201707301631) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-041300rc3-generic /boot/vmlinuz-4.13.0-041300rc3-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-041300rc3-generic /boot/vmlinuz-4.13.0-041300rc3-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-041300rc3-generic
**W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915**
**W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915**
**W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915**
**W: Possible missing firmware /lib/firmware/i915/kbl_huc_ver02_00_1810.bin for module i915**
**W: Possible missing firmware /lib/firmware/i915/bxt_huc_ver01_07_1398.bin for module i915**
**W: Possible missing firmware /lib/firmware/i915/skl_huc_ver01_07_1398.bin for module i915**
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.13.0-041300rc3-generic /boot/vmlinuz-4.13.0-041300rc3-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-041300rc3-generic /boot/vmlinuz-4.13.0-041300rc3-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-041300rc3-generic /boot/vmlinuz-4.13.0-041300rc3-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-041300rc3-generic /boot/vmlinuz-4.13.0-041300rc3-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.13.0-041300rc3-generic
Found initrd image: /boot/initrd.img-4.13.0-041300rc3-generic
Found linux image: /boot/vmlinuz-4.10.0-28-generic
Found initrd image: /boot/initrd.img-4.10.0-28-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```

**EDIT 2:** When I booted, the WiFi driver was gone! I looked it up and tried this:
[https://askubuntu.com/a/843869](https://askubuntu.com/a/843869)
And sure enough, the extra image is missing. However, when I attempt to type the command to install it, the terminal does nothing. It doesn't respond to input, although it appears. Nothing further is displayed on the screen. Also, opera doesn't run!

**EDIT 3: **Not even sudo echo x works, same result.

---

### Post by BenginM on 2017-08-03
You can ignore that worning as your cpu is 
Graphics:  Card: Intel Device 22b1, Intel HD Graphics 405 (Braswell) 

[URL="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Eighth_generation"]https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Eighth_generation
http://ark.intel.com/products/87261/Intel-Pentium-Processor-N3700-2M-Cache-up-to-2_40-GHz[/URL]

well, you do what you usually do before the crash occurred and try to notice any strange behavior , you might want to detached any medium attached other than the mouse and keyboard, open system monitor or run top and keep an eye on the CPU & RAM usage. note down the apps that is runin'..   i usually keep the system idle in a situation like this..

So when you used : 
dpkg -l | grep '^ii' | grep `uname -r`

did the extra image showed up..!

linux-image-`uname -r` just tries to reinstall the kernel you already have, not the linux-image-extra- .. that you want!
 
I've installed the exact mainline kernel ,didn't get that warning .. i haven't boot to it yet though .. maybe i should test it too.


[So this is the machine]("https://www.walmart.com/ip/Dell-Black-Inspiron-3052-All-in-One-Desktop-PC-with-Intel-Pentium-N3700-Processor-4GB-Memory-19-5-touch-screen-500GB-Hard-Drive-and-Windows-10/47089096")

Nice, that's a good one.

I received [this one]("https://www.amazon.com/HP-Omni-120-1034-Computer-processor/dp/B0073IWEWO") as a gift few years back..

---

### Post by BenginM on 2017-08-03
Strange , I just booted with kernel 4.13.0-rc3 on the desktop, wifi working as expected :

```


sary@blu:~$ inxi -b
System:    Host: blu Kernel: 4.13.0-041300rc3-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.3 Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: 120-1034
           Mobo: Quanta model: 2AC7 v: 011
           Bios: AMI v: ARM_702 date: 07/26/2011
CPU:       Dual core AMD E-450 APU with Radeon HD Graphics (-MCP-)
           speed/max: 1646/1650 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Wrestler [Radeon HD 6320]
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1600x900@58.03hz
           GLX Renderer: Gallium 0.4 on AMD PALM (DRM 2.50.0 / 4.13.0-041300rc3-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.7
Network:   Card-1: Ralink RT5390 Wireless 802.11n 1T/1R PCIe driver: rt2800pci
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
Drives:    HDD Total Size: 1500.3GB (1.8% used)
Info:      Processes: 156 Uptime: 10 min Memory: 729.8/3559.7MB
           Client: Shell (bash) inxi: 2.2.35 
sary@blu:~$ 


```

---

### Post by BenginM on 2017-08-03
I'am curious if kernel 4.8.0 will work fine and stable with no crashes , install and test kernel 4.8 from the repo , 

$ apt search linux-headers-4.8
$ apt search linux-image-4.8
$ apt search linux-headers-4.8

install the latest one , boot into it and test it ...

$ sudo apt install linux-headers-4.8.0-58-generic linux-image-4.8.0-58-generic linux-image-extra-4.8.0-58-generic

reboot , and select the kernel 4.8.0-58-generic

tell us how it goes.

---

### Post by ethanweegee on 2017-08-03
No, that wasn't my machine. Mine is that model, but it has 4 GB RAM and is underclocked at 1.6 GHz. I didn't realize that @Qll was right. 
inxi -b does show my wireless adapter. I tried your suggested commands, but sudo anything still doesn't work. I'm going to try to restart in an older kernel from advanced options.
Oh yeah, and with this new kernel, it never finishes shutting down. The loading circle still spins, but the only way to actually shut down is by force.

**EDIT 1:** Strangely, the 4.8.0 kernel was already in my advanced options. As was 4.1.3 and 4.1.0. Upon booting this kernel, the WiFi does work!

**EDIT 2: **...Well... sudo works.
```
ethan@ethan-Inspiron-20-3052:~$ sudo echo hi
[sudo] password for ethan: 
hi
```
But now the software app isn't working correctly. The 'Installed' and 'Updates' tabs are not loading.

**EDIT 3:** I got Software working after a reboot.
[B]
EDIT 4:[/B] "i usually keep the system idle in a situation like this.."[COLOR=#000000]
[/COLOR]Well, it usually works fine when idle. I don't think I mentioned this, but I had ubuntu on all night and woke up the next morning with it still on.
It seems to only crash when I'm *doing* something.

**EDIT 5:** CPU usage isn't going above 70% on anything. The highest was 65% when reloading in Opera, and that's it! Hovers around 5-15% normally.

---

### Post by ethanweegee on 2017-08-03
Oh yeah, and about that SpeedStep idea. I was pretty vague about it.
So I was reading about the problem you linked, and it had something to do with a low power state the CPU attempts to fall into, which the kernel does not support.
I wouldn't exactly call SpeedStep a low power thing, however.
What it does is automatically underclocks the CPU if the temperature gets too high.
[https://en.wikipedia.org/wiki/SpeedStep](https://en.wikipedia.org/wiki/SpeedStep)
Wait...
"[FONT=sans-serif]However, when the same processor is run at a lower frequency (speed), it generates less heat **and consumes less power.**"
[/FONT]

---

### Post by ethanweegee on 2017-08-04
Well, I used xubuntu kernel 4.8.0 since the other post 12 hours ago. It worked very long, and *then* it crashed. Can't say I'm disappointed; first it worked maybe for 5 minutes, then worked for 10 minutes, then 30 minutes, then a few hours, and now, the whole day!

---

### Post by BenginM on 2017-08-04
That's a good thing!

---

### Post by ethanweegee on 2017-08-04
It's becoming unstable again. It froze while web browsing, and wouldn't login after that without crashing. This time, I suspected cairo-dock, and sure enough, (CTRL+ALT+F1) in the terminal when I uninstalled the program and tried again, it worked. However, when I opened a new page in Opera, it froze. Upon reboot, it froze when I logged in again. After reboot AGAIN, it worked, but when I opened a new page in Opera, it froze. (Deja Vu?) Currently, I'm (re)installing kernel 4.8.0 as seen in the commands you provided earlier. I'll update later.

**EDIT 1:** Didn't work.
**EDIT 2:** Trying this [https://puu.sh/x1Lgt/8cd85ab671.png](https://puu.sh/x1Lgt/8cd85ab671.png)

---

### Post by BenginM on 2017-08-06
Ok..

---

### Post by cariboo on 2017-08-07
I have been running into the same problem, although I have a slightly different cpu and graphics chipset:

```
inxi -CG
CPU:       Quad core Intel Pentium N3530 (-MCP-) cache: 1024 KB 
           clock speeds: max: 2582 MHz 1: 985 MHz 2: 965 MHz 3: 589 MHz
           4: 501 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: x11 (X.Org 1.19.3) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel Bay Trail version: 4.2 Mesa 17.1.4
```

I'm running Xubuntu 17.10 and with the latest kernel:

```
uname -a
Linux alexis 4.11.0-13-generic #19-Ubuntu SMP Thu Aug 3 15:14:11 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

and so far since installing it yesterday I haven't had a lockup. If you want to try a newer kernel, you can get it here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11/)

Download and install the following 3 files:

```
linux-headers-4.11.0-041100_4.11.0-041100.201705041534_all.deb
linux-headers-4.11.0-041100-generic_4.11.0-041100.201705041534_amd64.deb
linux-image-4.11.0-041100-generic_4.11.0-041100.201705041534_amd64.deb
```

and give the 4.11 kernel a try.

---

### Post by ethanweegee on 2017-08-07
> **cariboo said:**
> I have been running into the same problem, although I have a slightly different cpu and graphics chipset:

```
inxi -CG
CPU:       Quad core Intel Pentium N3530 (-MCP-) cache: 1024 KB 
           clock speeds: max: 2582 MHz 1: 985 MHz 2: 965 MHz 3: 589 MHz
           4: 501 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: x11 (X.Org 1.19.3) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel Bay Trail version: 4.2 Mesa 17.1.4
```

I'm running Xubuntu 17.10 and with the latest kernel:

```
uname -a
Linux alexis 4.11.0-13-generic #19-Ubuntu SMP Thu Aug 3 15:14:11 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
and so far since installing it yesterday I haven't had a lockup. If you want to try a newer kernel, you can get it here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11/)

Download and install the following 3 files:

```
linux-headers-4.11.0-041100_4.11.0-041100.201705041534_all.deb
linux-headers-4.11.0-041100-generic_4.11.0-041100.201705041534_amd64.deb
linux-image-4.11.0-041100-generic_4.11.0-041100.201705041534_amd64.deb
```

and give the 4.11 kernel a try.


I just upgraded to Xubuntu 17.10 and no problems so far! Although, I'm running a slightly lower kernel.
```
Linux ethan-Inspiron-20-3052 4.10.0-30-generic #34-Ubuntu SMP Mon Jul 31 19:38:17 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by 4x4prepper on 2018-04-09
re:freezing screen with Ubuntu 16.04  This only started recently with me, after watching in the monitor I noticed the process Web Content was taking almost all the CPU time and a lot of memory until I ran out of my 6 GB.   I solved it by using these following procedures, after removing a Cookie editor extension:    #1 Under Firefox pref: Accept 3rd party cookies only from visited websites!    #2 change this in GRUB  [https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly](https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly)      There is a line in that: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (like this), replace with: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"       #3 My SWAP was not being used at all!  I doubled my swap space to that of my memory (12 GB)  [https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)   Would still freeze or run very slow, finally solved with this:    #4 I installed noscript from Firefox/Tools/extensions and only allow a select few site to run JS.  noscript.net/forums

---

### Post by QIII on 2018-04-09
Goodnight, old (and already marked solved) thread.

---

