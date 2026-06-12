---
title: "Random Crash/Screen freeze ubuntu 13.04"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by khaozzer0 on 2013-05-14
Hello,

I had a clean installation of ubuntu 13.04, and the only other modifications I did were to install compiz and ndiswrapper. I am not sure if the crash is originating from ndiswrapper or "
anacron"(Not sure what this does looks something like windows scheduler) since its the last message on the syslog before the crash. 
    
syslog:
```
May 14 12:53:10 NERV avahi-daemon[911]: Registering new address record for fe80::226:f2ff:fe49:b70e on wlan1.*.
May 14 12:53:10 NERV dnsmasq[1531]: cleared cache
May 14 12:53:15 NERV ntpdate[2592]: step time server 91.189.94.4 offset -0.876213 sec
May 14 12:53:28 NERV NetworkManager[949]: <info> (wlan1): IP6 addrconf timed out or failed.
May 14 12:53:28 NERV NetworkManager[949]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 14 12:53:28 NERV NetworkManager[949]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 14 12:53:28 NERV NetworkManager[949]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 14 12:54:12 NERV kernel: [  113.622893] BUG: unable to handle kernel paging request at f8165aa0
May 14 12:54:12 NERV kernel: [  113.622896] IP: [<c1043cbb>] kmap_atomic_prot+0x1b/0x100
May 14 12:54:12 NERV kernel: [  113.622901] *pdpt = 00000000019cd001 *pde = 0000000000000000 
May 14 12:54:12 NERV kernel: [  113.622903] Oops: 0000 [#5] SMP 
May 14 12:54:12 NERV kernel: [  113.622905] Modules linked in: ipt_MASQUERADE(F) xt_state(F) ipt_REJECT(F) xt_tcpudp(F) iptable_filter(F) nf_nat_h323(F) nf_conntrack_h323(F) nf_nat_pptp(F) nf_nat_proto_gre(F) nf_conntrack_pptp(F) nf_conntrack_proto_gre(F) nf_nat_tftp(F) nf_conntrack_tftp(F) nf_nat_sip(F) nf_conntrack_sip(F) nf_nat_irc(F) nf_conntrack_irc(F) nf_nat_ftp(F) nf_conntrack_ftp(F) iptable_nat(F) nf_conntrack_ipv4(F) nf_defrag_ipv4(F) nf_nat_ipv4(F) nf_nat(F) nf_conntrack(F) ip_tables(F) x_tables(F) snd_hda_codec_hdmi ndiswrapper(OF) arc4(F) snd_hda_codec_analog parport_pc(F) ppdev(F) bnep rfcomm bluetooth snd_hda_intel snd_hda_codec snd_hwdep(F) ath5k coretemp kvm_intel snd_pcm(F) ath mac80211 kvm cfg80211 asus_atk0110 snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) mac_hid nvidia(POF) snd(F) x38_edac lpc_ich edac_core drm microcode(F) serio_raw(F) soundcore(F) lp(F) parport(F) pata_acpi hid_apple hid_generic usbhid hid firewire_ohci fl
May 14 12:54:12 NERV kernel: oppy(F) firewire_core sky2 crc_itu_t(F) pata_jmicron ahci(F) libahci(F)
May 14 12:54:12 NERV kernel: [  113.622941] Pid: 2655, comm: ps Tainted: PF     D W  O 3.8.0-19-generic #30-Ubuntu System manufacturer Rampage Formula/Rampage Formula
May 14 12:54:12 NERV kernel: [  113.622943] EIP: 0060:[<c1043cbb>] EFLAGS: 00010202 CPU: 0
May 14 12:54:12 NERV kernel: [  113.622944] EIP is at kmap_atomic_prot+0x1b/0x100
May 14 12:54:12 NERV kernel: [  113.622946] EAX: ec4e6000 EBX: f688c7e0 ECX: 80000000 EDX: 00000163
May 14 12:54:12 NERV kernel: [  113.622947] ESI: f8165aa0 EDI: 00000016 EBP: ec4e7df0 ESP: ec4e7de0
May 14 12:54:12 NERV kernel: [  113.622948]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
May 14 12:54:12 NERV kernel: [  113.622949] CR0: 80050033 CR2: f8165aa0 CR3: 2f017000 CR4: 000407f0
May 14 12:54:12 NERV kernel: [  113.622950] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May 14 12:54:12 NERV kernel: [  113.622951] DR6: ffff0ff0 DR7: 00000400
May 14 12:54:12 NERV kernel: [  113.622952] Process ps (pid: 2655, ti=ec4e6000 task=f685a670 task.ti=ec4e6000)
May 14 12:54:12 NERV kernel: [  113.622953] Stack:
May 14 12:54:12 NERV kernel: [  113.622954]  ec4e7de8 f688c7e0 00000002 00000016 ec4e7df8 c1043db9 ec4e7e2c c1131115
May 14 12:54:12 NERV kernel: [  113.622957]  0002bb16 000800d0 000a00d0 ec4e7e80 2fad5067 00000000 bfa0af29 f8165aa0
May 14 12:54:12 NERV kernel: [  113.622961]  00000016 f688c7e0 eee4d9b0 ec4e7e88 c1132bf9 00000000 00000040 00000000
May 14 12:54:12 NERV kernel: [  113.622964] Call Trace:
May 14 12:54:12 NERV kernel: [  113.622966]  [<c1043db9>] kmap_atomic+0x19/0x20
May 14 12:54:12 NERV kernel: [  113.622969]  [<c1131115>] follow_page+0x255/0x420
May 14 12:54:12 NERV kernel: [  113.622971]  [<c1132bf9>] __get_user_pages+0x119/0x4c0
May 14 12:54:12 NERV kernel: [  113.622973]  [<c113305c>] get_user_pages+0x5c/0x70
May 14 12:54:12 NERV kernel: [  113.622975]  [<c113312e>] __access_remote_vm+0xbe/0x170
May 14 12:54:12 NERV kernel: [  113.622976]  [<c1133485>] access_process_vm+0x45/0x80
May 14 12:54:12 NERV kernel: [  113.622979]  [<c11b1e9c>] proc_pid_cmdline+0x7c/0x100
May 14 12:54:12 NERV kernel: [  113.622981]  [<c11b29bf>] proc_info_read+0x7f/0xd0
May 14 12:54:12 NERV kernel: [  113.622983]  [<c116ccb4>] ? putname+0x24/0x40
May 14 12:54:12 NERV kernel: [  113.622984]  [<c11b2940>] ? proc_pid_attr_write+0x110/0x110
May 14 12:54:12 NERV kernel: [  113.622986]  [<c115fc09>] vfs_read+0x89/0x160
May 14 12:54:12 NERV kernel: [  113.622988]  [<c11b2940>] ? proc_pid_attr_write+0x110/0x110
May 14 12:54:12 NERV kernel: [  113.622990]  [<c115fd27>] sys_read+0x47/0x80
May 14 12:54:12 NERV kernel: [  113.622992]  [<c16198cd>] sysenter_do_call+0x12/0x28
May 14 12:54:12 NERV kernel: [  113.622993] Code: 4c e1 9d c1 e8 f7 f6 ff ff 5d c3 90 8d 74 26 00 55 89 e5 57 56 53 83 ec 04 66 66 66 66 90 89 c6 89 e0 25 00 e0 ff ff 83 40 14 01 <8b> 06 c1 e8 1e 69 c0 40 03 00 00 05 00 61 8f c1 2b 80 0c 03 00
May 14 12:54:12 NERV kernel: [  113.623015] EIP: [<c1043cbb>] kmap_atomic_prot+0x1b/0x100 SS:ESP 0068:ec4e7de0
May 14 12:54:12 NERV kernel: [  113.623017] CR2: 00000000f8165aa0
May 14 12:54:12 NERV kernel: [  113.623019] ---[ end trace 5524947afb70aea2 ]---
May 14 12:54:12 NERV kernel: [  113.623021] note: ps[2655] exited with preempt_count 1
May 14 12:57:32 NERV anacron[1070]: Job `cron.daily' started
May 14 12:57:32 NERV anacron[2721]: Updated timestamp for job `cron.daily' to 2013-05-14
```

Thanks in advance

---

