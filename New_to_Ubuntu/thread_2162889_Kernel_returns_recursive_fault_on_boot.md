---
title: "Kernel returns recursive fault on boot"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by HantifuTriplera on 2013-07-16
I have installed Lubuntu 13.04 on an eMac (powerpc 7447a G4), which has a Radeon 9200 graphics card installed. Maybe if more specifications are needed to help solve my question you could show me how to diagnose what hardware is in my eMac?

So I have been able to boot Lubuntu a couple of times but now it will lock on boot, the following screen is visible. Am I correct that this is output of the kernel?

[    20.266920] [efgbbef0] [c0067ac8] kthread+0xb4/0xb8
[    20.269140] [efgbbf40] [c001702c] ret_from_kernel_thread+0x64/0x6c
[    20.271526] Instruction dump:
[    20.273587] 91240048 80010014 38210010 7c0803a6 4e800020 700802a6 90010004 60000000
[    20.276265] 9421fff0 7c0802a6 90010014 80630178 <8123003c> 2f890000 409e0018 38600000
[    20.279114] --- [end trace 8b603f1dd701b40a ]---
[    20.281537]
[    20.318271] apm_emu: PMU APM Emulation initialized.
[    20.478921] Unable to handle kernel paging request for data at address 0xffffffec
[    20.481762] Faulty instruction address: 0xc0068094
[    20.484417] OOps: kernel access of bad area, sig : 11 [#2]
[    20.487178] SMP NR_CPUS=4 PowerMac
[    20.489598] Modules linked in : apm_emu (F) apm_emulation (F) cfg980211 (F) snd_powermac (F) snd_pcm (F) snd_page_alloc (F) snd_seq_midi (F) snd_seq_midi_event (F) snid_rawmidi (F) snd_seq (F) snd_seq_device (F) snd_timer (F) uninorth_agp (F) snd (F) soundcore (F) hid_generic (F) usbhid (F) hid (F) firewire_ohci(F) sungem (F) sungem_plug (F) firewire_core (F) crc_itu_t (F) ssb (F)
[    20.499946] NIP: c0068094 LR: c0061f38 CTR: c00858b4
[    20.803065] REGS: ef9bbb20 TRAP: 003 Tainted: GF      D (3.8.0-10-powerpc-smp)
[    20.506565] MSR: 000001032 <ME, IR, DR, RI> CR: 42104028 XER: 00000000
[    20.509917] DAR: ffffffee DSISR: 40000000
[    20.513018] TASK=ef90de80 [23] 'kworker/0:1' THREAD: ef9ba000 CPU : 0
GPR00: c0061f38 ef9bbbd0 ef90de80 ef90dc80 00000000 0007d560 00000000 0000000f
GPR08: 0000000b 00000000 00000000 000001f0 82104022 00000000 c09a0000 c00444cc
GPR16: c0945f80 c0945f80 c0945f80 c06d0000 00000000 c1192f80 ef90de80 c09b0000
GPR24: c09aa5a4 c0945f80 c0945f80 c09ab7e8 efgba000 c0945f80 0084d000 00000000
[    20.531170] NIP [c0068094] kthread_data+0x1c/0x30
[    20.534403] LR [c0061f38] wq_worker_sleeping+0x24/0x124
[    20.537913] Call trace:
[    20.541103] [ef9bbbd0] [c0945f80] runqueus+0x0/0x620 (unreliable)
[    20.544369] [ef9bbbeo] [c0061f38] wq_worker_sleeping+0x24/0x124
[    20.547904] [efgbbbf0] [c06a9ac0] _schedule+0x5c8/0x7c0
[    20.551281] [ef9bbd10] [c00444cc] do_exit+0x5c8/0x908
[    20.554589] [ef9bbd60] [c000370] die+0x23c/0x394
[    20.557771] [efgbbd90] [c0017408] handle_page_fault+0x7c/0x80
[    20.561090] --- Exception: 300 at tumbler_detect_headphone+0x1c/0x50 [snd_powermac]
[    20.561090] LR = device_change_handler+0x44/0x264 [snd_powermac]
[    20.567620] [ef9bbe50] [c003fab4] console_unlock+0x220/0x44c (unreliable)
[    20.571046] [ef9bbe60] [f2926068] device_change_handler+0x44/0x3+5 [snd_powermac[
[    20.574555] [ef9bbe80] [c0060c18] process_one_work+0x18c/0x4ac
[    20.577649] [ef9bbeb0] [c0061330] worker_thread+0x190/0x424
[    20.580873] [ef9bbef0] [c0067ae8] kthread+0xb4/0xb8
[    20.584021] [ef9bbf40] [c001702c] ret_from_kernel_thread +0x64/0x6c
[    20.587281] Instruction dump:
[    20.589857] 5463f7fe 80010014 38210010 7c0803a6 4e800020 7c0802a6 90010004 60000000
[    20.593389] 9421fff0 7c0802a6 90010014 81230290 <8069ffec> 80010014 38210010 7c0803a6
[    20.596973] --- [ end trace 8b603f1dd701b40b] ---
[    20.599933]
[    20.602672] Fixing recursive fault but reboot is needed!

How to diagnose why Lubuntu won't boot?

---

### Post by ptn107 on 2013-07-16
From what I read around the web it could be a faulty memory module.  To rule this out, reboot and choose the option 'memory test (memtest86+)' from the boot menu.  If you don't see a grub menu I think you have to hold 'shift' to make it visible.

---

### Post by BreizhPositive on 2013-08-14
Hello.

I think I have exactly the same problem on an G4 eMac like yours.

The first install + updates worked well.
But no sound / sound card enabled so I followed this instructions :

> 
edit file /etc/modprobe.d/blacklist.local.conf and comments this lines:

#blacklist snd-aoa-codec-tas
#blacklist snd-aoa-fabric-layout
#blacklist snd-aoa-i2sbus
#blacklist snd-aoa-soundbus
#blacklist snd-aoa

edit file /etc/modules and add this lines:

snd-aoa-codec-tas
snd-aoa-fabric-layout
snd-aoa-i2sbus
snd-aoa-soundbus
snd-aoa

restart the OS


And now I have the "recursive fault on boot" and impossible to re-edit this files : "Linux single" does not working at the yaboot prompt.
What is the trick ?

---

### Post by BreizhPositive on 2013-08-14
OK. I installed pulseaudio and pavumeter.
After reboot I get the sound control in the bottom bar.

When launching the sound control panel or the pavumeter, I can see the bar level moving when playing a mp3 file with gnome player.
But no sound comes out the emac because the system does not know any sound card / harware outpu device. Only a "sortie factice".

I finally found this bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1066435](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1066435)
Read the post 71 and followers.

This seems to be a kernel bug specific to powerPC  :(
Kown since 2012 but not fixed again :(
maybe in ubuntu 13.07 ?

---

