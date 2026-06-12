---
title: "Bunch of problems (Lubuntu)"
date: 2018-05-07
forum: New to Ubuntu
---

### Post by cforyourself on 2018-05-07
So I just installed Lubuntu and I have few problems.

- When I connect my laptop to my TV via HDMI cable, the sound doesn't come from TV.
- When videos play on the TV, the sound sometimes comes twice, so it basically echoes.
- Also sometimes when I switch the screen between laptop and TV, the mouse cursor completely disappears.

How can I fix these issues?

---

### Post by dino99 on 2018-05-07
Glance at logs (journalctl -b) to find 'warnings' (bright lines) & 'errors' (red lines). Then it will be easier to help.

---

### Post by cforyourself on 2018-05-07
> **dino99 said:**
> Glance at logs (journalctl -b) to find 'warnings' (bright lines) & 'errors' (red lines). Then it will be easier to help.

Here you go:

```
main_user@G50:~$ journalctl -b
-- Logs begin at ti 2018-05-01 20:22:28 EEST, end at ma 2018-05-07 17:56:51 EEST
touko 01 20:22:28 G50 systemd-journald[220]: Runtime journal (/run/log/journal/)
touko 01 20:22:28 G50 kernel: **random: get_random_bytes called from start_kernel+**
touko 01 20:22:28 G50 kernel: **Linux version 4.13.0-39-generic (buildd@lcy01-amd6**
touko 01 20:22:28 G50 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-39-g
touko 01 20:22:28 G50 kernel: KERNEL supported cpus:
touko 01 20:22:28 G50 kernel:   Intel GenuineIntel
touko 01 20:22:28 G50 kernel:   AMD AuthenticAMD
touko 01 20:22:28 G50 kernel:   Centaur CentaurHauls
touko 01 20:22:28 G50 kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floa
touko 01 20:22:28 G50 kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE regi
touko 01 20:22:28 G50 kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX regi
touko 01 20:22:28 G50 kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]: 
touko 01 20:22:28 G50 kernel: x86/fpu: Enabled xstate features 0x7, context size
touko 01 20:22:28 G50 kernel: e820: BIOS-provided physical RAM map:
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x000000000009f400-0x000000000009f
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000ff
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000ba0bb
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000ba0bc000-0x00000000baabb
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000baabc000-0x00000000bf6be
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000bf6bf000-0x00000000bfabe
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000bfabf000-0x00000000bfbbe
lines 1-23...skipping...
-- Logs begin at ti 2018-05-01 20:22:28 EEST, end at ma 2018-05-07 17:56:51 EEST. --
touko 01 20:22:28 G50 systemd-journald[220]: Runtime journal (/run/log/journal/) is 4.2M, max 34.0M, 29.8M free.
touko 01 20:22:28 G50 kernel: **random: get_random_bytes called from start_kernel+0x42/0x507 with crng_init=0**
touko 01 20:22:28 G50 kernel: **Linux version 4.13.0-39-generic (buildd@lcy01-amd64-024) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.9)) #44~16.04.1-Ubuntu SMP Thu Apr 5 16:43:10 UTC 2018 (Ubuntu 4.13.0-39.44~16.04.1-generic 4**
touko 01 20:22:28 G50 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-39-generic root=UUID=2d243037-c5aa-4357-b6bb-3280a6e89913 ro quiet splash vt.handoff=7
touko 01 20:22:28 G50 kernel: KERNEL supported cpus:
touko 01 20:22:28 G50 kernel:   Intel GenuineIntel
touko 01 20:22:28 G50 kernel:   AMD AuthenticAMD
touko 01 20:22:28 G50 kernel:   Centaur CentaurHauls
touko 01 20:22:28 G50 kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
touko 01 20:22:28 G50 kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
touko 01 20:22:28 G50 kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
touko 01 20:22:28 G50 kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
touko 01 20:22:28 G50 kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
touko 01 20:22:28 G50 kernel: e820: BIOS-provided physical RAM map:
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f3ff] usable
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x000000000009f400-0x000000000009ffff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000ba0bbfff] usable
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000ba0bc000-0x00000000baabbfff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000baabc000-0x00000000bf6befff] usable
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000bf6bf000-0x00000000bfabefff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000bfabf000-0x00000000bfbbefff] ACPI NVS
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000bfbbf000-0x00000000bfbfefff] ACPI data
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000bfbff000-0x00000000bfbfffff] usable
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000bfc00000-0x00000000dfffffff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000fec01fff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000fed80000-0x00000000fed80fff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
touko 01 20:22:28 G50 kernel: BIOS-e820: [mem 0x0000000100000000-0x000000011effffff] usable
touko 01 20:22:28 G50 kernel: NX (Execute Disable) protection: active
touko 01 20:22:28 G50 kernel: **random: fast init done**
touko 01 20:22:28 G50 kernel: SMBIOS 2.8 present.
touko 01 20:22:28 G50 kernel: DMI: LENOVO 80E3/Lancer 5B2, BIOS A2CN26WW(V1.08) 10/29/2014
touko 01 20:22:28 G50 kernel: tsc: Fast TSC calibration using PIT
touko 01 20:22:28 G50 kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
touko 01 20:22:28 G50 kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
touko 01 20:22:28 G50 kernel: e820: last_pfn = 0x11f000 max_arch_pfn = 0x400000000
touko 01 20:22:28 G50 kernel: MTRR default type: uncachable
touko 01 20:22:28 G50 kernel: MTRR fixed ranges enabled:
touko 01 20:22:28 G50 kernel:   00000-9FFFF write-back
touko 01 20:22:28 G50 kernel:   A0000-BFFFF uncachable
touko 01 20:22:28 G50 kernel:   C0000-FFFFF write-through
touko 01 20:22:28 G50 kernel: MTRR variable ranges enabled:
touko 01 20:22:28 G50 kernel:   0 base 0000000000 mask FF80000000 write-back
touko 01 20:22:28 G50 kernel:   1 base 0080000000 mask FFC0000000 write-back
touko 01 20:22:28 G50 kernel:   2 base 00BFBA8000 mask FFFFFFF000 uncachable
touko 01 20:22:28 G50 kernel:   3 base 00FF800000 mask FFFF800000 write-protect
touko 01 20:22:28 G50 kernel:   4 disabled
touko 01 20:22:28 G50 kernel:   5 disabled
touko 01 20:22:28 G50 kernel:   6 disabled
touko 01 20:22:28 G50 kernel:   7 disabled
touko 01 20:22:28 G50 kernel: TOM2: 000000011f000000 aka 4592M
touko 01 20:22:28 G50 kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
touko 01 20:22:28 G50 kernel: e820: last_pfn = 0xbfc00 max_arch_pfn = 0x400000000
touko 01 20:22:28 G50 kernel: Scanning 1 areas for low memory corruption
touko 01 20:22:28 G50 kernel: Base memory trampoline at [ffff9ce340099000] 99000 size 24576
touko 01 20:22:28 G50 kernel: Using GB pages for direct mapping
```

The text I **bolded** above are seen as bolded and colored in white instead of gray in the LXTerminal. There was no text colored in red. Hopefully you can help me now, because I have no idea what this all stuff means.

---

### Post by dino99 on 2018-05-08
What you have posted into #3 show a very shorten part of journalctl, and is useless as is. Please reproduce your #1 post then check again: 'journalctl -b > journal.txt'. And post the output here.

---

### Post by cforyourself on 2018-05-16
> **dino99 said:**
> What you have posted into #3 show a very shorten part of journalctl, and is useless as is. Please reproduce your #1 post then check again: 'journalctl -b > journal.txt'. And post the output here.

So, let's try this again. Here is the larger data set: [https://paste.ubuntu.com/p/RkZmqF5vTB/](https://paste.ubuntu.com/p/RkZmqF5vTB/)

---

### Post by dino99 on 2018-05-16
hm, the log does not expose the problems from #1; so cant help about that.

(1)  gpu-manager[627]: Error: can't open /lib/modules/4.13.0-41-generic/updates/dkms
(2)  ntpd[867]: error resolving pool 0.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
(3)  lightdm[1362]: PAM unable to dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or directory

but the errors above can be fixed (hopefully)
(1) run: sudo apt-get update && sudo apt-get install --reinstall lubuntu-desktop && sudo apt-get install --reinstall build-essential  && sudo apt-get install --reinstall linux-generic
            sudo apt-get autoremove && sudo apt-get purge readahead && sudo dpkg --configure -a
(2) command seems loaded too early, solved later
(3) run: sudo apt-get install --reinstall libpam-systemd

---

