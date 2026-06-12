---
title: "Boot Problem, stuck in BusyBox after update, tried LiveUSB"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by usmcfieldmp on 2014-02-21
[COLOR=#333333][FONT=UbuntuRegular]I updated the system (13.10) yesterday and was then prompted to restart. It restarted fine and all seemed normal. I was having trouble watching a stream on BlogTalkRadio while in Chrome, so I opened up Firefox and it streamed fine there. About 15 or so minutes later, I closed Chrome thinking restarting it might help, and then hit Ctrl+T in Firefox to open a new tab... as soon as I hit that, Firefox closed and wouldn't re-open - neither would Chrome. So I reboot the system again, but ever since then it always jumps immediately to the BusyBox terminal. I've tried rebooting with different versions in GRUB, but still get a version of BusyBox every time. I ran the GRUB memory test and a hard drive diagnostics test from the Boot Device Menu (available after hitting F12) - both passed. I ran through some of the threads on here and at AskUbuntu to no avail. I was running the latest version of Ubuntu by itself (Windows hasn't been on this computer since 2010) and I basically have no knowledge when it comes to running terminal code. I created a USB Boot Drive with LinuxLive USB Creator using the 13.10 iso, but every time I try to boot from it, whether in Persistent, Live, or Install, I still get thrown to a BusyBox terminal (albeit a different font this time).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]When I type ***dmesg|tail*** booting from the LiveUSB drive I get:
[/FONT][/COLOR]
```

[   7.702519] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   7.703132] sd 4:0:0:0: [sdc] No Caching mode page found
[   7.703139] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   7.706138] sd 4:0:0:0: [sdc] No Caching mode page found
[   7.706149] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   7.707531]  sdc:
[   7.709754] sd 4:0:0:0: [sdc] No Caching mode page found
[   7.709765] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   7.709773] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   7.762829] Switched to clocksource tsc

```

[COLOR=#333333][FONT=UbuntuRegular]When I run that command booting from the HDD, I get basically the same lines, only with different numbers in brackets and there's a line that comes before the first line that reads ***Write protect is off*** and the final line ***Switched to clocksource tsc*** isn't there either. 

I read to try typing [/FONT][/COLOR]***[FONT=Ubuntu Mono]exit[/FONT]***[COLOR=#333333][FONT=UbuntuRegular] as well, which gives me:

```

/init: line 352: can't open /root/dev/console: no such file
[    6.535057] Kernal panic - not syncing: Attempted to kill init! exitcode=0x00000200
[    6.535057]
[    6.535124] CPU: 0 PID: 1 Comm: init Not tained 3.11.0-17-generic #31-Ubuntu
[    6.535175] Hardware name: Dell Inc.          Dimension XPS Gen 3            /0K3464, BIOS A02 08/23/2004
[    6.535242]  00000000 00000000 f7097f18 c1627735 c18fb3e0 f7097f38 c1623790 c17f955c
[    6.535328]  c1a6a800 f7097f24 c18fb3e0 f7098418 f7098000 f7097f8c c1054dbe c17f9880
[    6.535412]  00000200 00000028 00000004 f709841a 00000001 00000001 00000002 f7097f88
[    6.535496] Call Trace:
[    6.535523]  [<c1627735>] dump_stack+0x41/0x52
[    6.535559]  [<c1623790>] panic+0x87/0x181

```[/FONT][/COLOR]```
[COLOR=#333333][FONT=UbuntuRegular][    6.535593]  [<c1054dbe>] do_exit+0x7de/0x8e0
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][    6.535627]  [<c116b554>] ? vfs_write+0x144/0x1b0
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][    6.535662]  [<c1054f34>] do_group_exit+0x34/0xa0
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][    6.535697]  [<c1054fb6>] SyS_exit_group+0x16/0x20
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][    6.535734]  [<c1634e8d>] sysenter_do_call+0x12/0x28
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][    6.535779] drm_kms_helper: panic occured, switching back to text console
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]_
[/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular]

[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]At this point, it becomes unresponsive. I'm not sure what else to do and can't any other threads that appear to pertain to my situation, so any help is appreciated.[/FONT][/COLOR]

---

### Post by usmcfieldmp on 2014-02-22
Anyone have any ideas on why I can't even load from the LiveUSB?

---

### Post by usmcfieldmp on 2014-02-23
UPDATE: I made a new LiveUSB, but with 12.04 LTS this time. It booted up and worked. However, when I clicked on the Home folder and then clicked on my main hard drive (in an attempt to backup the handful of files I've added since my last backup), I get the error message:

> [B]Unable to mount 247 GB Filesystem

[/B]Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg|tail or so

I opened Disk Utility and ran a quick SMART Data assessment on it, which returned a "healthy".

I then ran "Check Filesystem", which came back with "File system is **not **clean."

Ran Boot-Repair: [http://paste.ubuntu.com/6982054/](http://paste.ubuntu.com/6982054/)

Restart computer. Great success. She booted right up.

---

