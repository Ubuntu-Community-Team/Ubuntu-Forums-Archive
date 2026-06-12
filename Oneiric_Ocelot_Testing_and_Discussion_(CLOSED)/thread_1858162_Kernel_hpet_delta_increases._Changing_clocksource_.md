---
title: "Kernel hpet delta increases. Changing clocksource issues"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-10-11
```

[07:29 ][al:AL-DESK:~]
$ uname -a
Linux AL-DESK 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```Since yesterday I started having these messages in dmesg:

```
CE: hpet increasing min_delta_ns to 22500 nsec
```Apparently this had been fixed in kernel 2.6.39.

The known workaround is to change clocksource.
I have changed from hpet to tsc, yet my boot seems to make a mess with it.

I specify clocksource=tsc.
```

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c03a4fd5-c162-48ce-9d91-d549a8f02b64 ro crashkernel=384M-2G:64M,2G-:128M nomodeset **clocksource=tsc** video=uvesafb:mode_option=1600x1200-24,mttr=3,scroll=ywrap
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c03a4fd5-c162-48ce-9d91-d549a8f02b64 ro crashkernel=384M-2G:64M,2G-:128M nomodeset **clocksource=tsc** video=uvesafb:mode_option=1600x1200-24,mttr=3,scroll=ywrap

```Then it decides to go **hpet**?
```

[    0.000000] hpet clockevent registered
[    0.773068] **Switching to clocksource hpet**
[    1.515925] rtc_cmos 00:03: setting system clock to 2011-10-11 15:46:21 UTC (1318347981)

```But it seems like a good idea to readjust tsc?
```

[    1.888267] Refined TSC clocksource calibration: 3712.392 MHz.
[    1.888271] Override clocksource tsc is not HRT compatible. Cannot switch while in HRT/NOHZ mode
[    1.888274] **Switching to clocksource tsc**

```Any kernel wizard in the room? I'm not sure, but all this really doesn't seem normal.

Regards,
Effenberg

**EDIT:**
My Northbridge supports hpet. Enabling / disabling C1E support in BIOS makes no difference in the symptoms described above. NOHZ is auto-enabled to support "Turbo Core" feature of Black Edition CPU - I have no control over it.

---

