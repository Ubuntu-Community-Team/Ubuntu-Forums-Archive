---
title: "Ubuntu 18.04"
date: 2019-06-03
forum: New to Ubuntu
---

### Post by yneopany on 2019-06-03
Have installed Ubuntu 18.04. The restart and shutdown process freezes Everytime and I have to force shutdown.. anyone can help me in this regard?

---

### Post by Frogs Hair on 2019-06-03
Try shutting down from the terminal then try from the menu the next time. 
 
```
sudo poweroff
```

---

### Post by yneopany on 2019-06-05
I tried but I got nothing.... Any other option?

---

### Post by CatKiller on 2019-06-05
Does it freeze, or does it simply take a long time? The default timeout period for waiting for services to terminate is 90 seconds, which means that misbehaving software can cause the shutdown to have to wait for a minute and a half.

---

### Post by yneopany on 2019-06-05
Yes it does freeze because I waited for like an hour still same screen... Tried using quit flash solution still didn't work.. I always have to forcibly shut down by power button

---

### Post by CatKiller on 2019-06-05
> **yneopany said:**
> Yes it does freeze because I waited for like an hour still same screen... 
And which screen is that? We can only help you identify the problem; we can't do it for you. 
> Tried using quit flash solution still didn't work..  
I have no idea what you're trying to say here. 
> I always have to forcibly shut down by power button
Sometimes it can't be helped, but you should try to avoid doing that. The [SysRq REISUO](https://en.m.wikipedia.org/wiki/Magic_SysRq_key) is more gentle if you're in a position to use it.

---

### Post by yneopany on 2019-06-05
It's Ubuntu logo screen where it gets freezes.

---

### Post by Rubi1200 on 2019-06-05
We need to see some system specifications.

Open a terminal with CTRL+ALT+T and enter the following commands:

```
sudo apt install inxi
```

Once installed run this:

```
inxi -Fzr
```

Post the results here using code tags (go advanced and look for # symbol)

Thanks.

---

### Post by yneopany on 2019-06-06
```
 inxi -fzrCPU:       Quad core Intel Core i5-8250U (-MT-MCP-) cache: 6144 KB
           clock speeds: max: 3400 MHz 1: 846 MHz 2: 1560 MHz 3: 1547 MHz
           4: 1482 MHz 5: 2400 MHz 6: 1057 MHz 7: 1465 MHz 8: 1636 MHz
           CPU Flags: 3dnowprefetch abm acpi adx aes aperfmperf apic arat
           arch_perfmon art avx avx2 bmi1 bmi2 bts clflush clflushopt cmov
           constant_tsc cpuid cpuid_fault cx16 cx8 de ds_cpl dtes64 dtherm dts
           epb ept erms est f16c flexpriority flush_l1d fma fpu fsgsbase fxsr
           ht hwp hwp_act_window hwp_epp hwp_notify ibpb ibrs ida intel_pt
           invpcid invpcid_single lahf_lm lm mca mce md_clear mmx monitor
           movbe mpx msr mtrr nonstop_tsc nopl nx pae pat pbe pcid pclmulqdq
           pdcm pdpe1gb pebs pge pln pni popcnt pse pse36 pti pts rdrand
           rdseed rdtscp rep_good sdbg sep smap smep ss ssbd sse sse2 sse4_1
           sse4_2 ssse3 stibp syscall tm tm2 tpr_shadow tsc tsc_adjust
           tsc_deadline_timer tsc_known_freq vme vmx vnmi vpid x2apic xgetbv1
           xsave xsavec xsaveopt xsaves xtopology xtpr
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://in.archive.ubuntu.com/ubuntu/ bionic main restricted
           deb http://in.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
           deb http://in.archive.ubuntu.com/ubuntu/ bionic universe
           deb http://in.archive.ubuntu.com/ubuntu/ bionic-updates universe
           deb http://in.archive.ubuntu.com/ubuntu/ bionic multiverse
           deb http://in.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
           deb http://in.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu bionic-security main restricted
           deb http://security.ubuntu.com/ubuntu bionic-security universe
           deb http://security.ubuntu.com/ubuntu bionic-security multiverse
           Active apt sources in file: /etc/apt/sources.list.d/atareao-ubuntu-atareao-bionic.list
           deb http://ppa.launchpad.net/atareao/atareao/ubuntu bionic main
           Active apt sources in file: /etc/apt/sources.list.d/google-chrome.list
           deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main



```

---

### Post by drv9977 on 2019-06-06
Whats the size of RAM your are using??? have you tried shutting it down instantly after booting???

---

### Post by cruzer001 on 2019-06-06
Anything in systemd shutdown?
```
journalctl -u systemd-shutdownd
```

---

### Post by yneopany on 2019-06-06
It's 8gb ram and yes I did shut down instantly after booting

---

