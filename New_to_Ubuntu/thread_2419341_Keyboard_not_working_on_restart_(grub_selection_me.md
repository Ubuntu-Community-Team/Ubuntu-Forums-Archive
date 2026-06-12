---
title: "Keyboard not working on restart (grub selection menu) + clock problem too...."
date: 2019-05-20
forum: New to Ubuntu
---

### Post by 1byte on 2019-05-20
Hi all

Iam new to Linux and I have dual-OS booting (Win10/Ubuntu Studio), now when i RESTART in Linux the keyboard does not work on the GRUB menu (Win10 is default) - yet every time it does this and boots into windows, when I restart, the keyboard IS working, very strange, it happens every single time too, its like to restart Linux I HAVE to boot into windows first to trigger the keyboard into a working state??

2nd issue: every time I go into Win10 after using Linux the clock is one hour behind....every time...

if anyone can help with these problems I would really appreciate it

thanks in advance

---

### Post by CatKiller on 2019-05-20
> **1byte said:**
> 2nd issue: every time I go into Win10 after using Linux the clock is one hour behind....every time...

Both Windows and Linux set the hardware clock to a time that they retrieve from the Internet, since the hardware clock is terrible at keeping time.

Windows sets the hardware clock to local time. Everything else sets the clock to UTC and converts to local time. The difference between UTC and local time, for you, in the summer, is one hour; hence the disparity.

It's just editing a text file to make Ubuntu use local time for the hardware clock instead. I can't remember *which* text file, since I haven't used Windows in over a decade.

---

### Post by #&amp;thj^% on 2019-05-20
> **CatKiller said:**
> Both Windows and Linux set the hardware clock to a time that they retrieve from the Internet, since the hardware clock is terrible at keeping time.

Windows sets the hardware clock to local time. Everything else sets the clock to UTC and converts to local time. The difference between UTC and local time, for you, in the summer, is one hour; hence the disparity.

It's just editing a text file to make Ubuntu use local time for the hardware clock instead. I can't remember *which* text file, since I haven't used Windows in over a decade.

+1 


In Ubuntu releases that use systemd the command to change time to local and update the clock right away is

```
timedatectl set-local-rtc 1 --adjust-system-clock

```
If you run timedatectl, it will show a warning

```
Warning: The system is configured to read the RTC time in the local time zone.
         This mode can not be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.
```

This warning doesn't mean that it is set to 0, it suggests a command to switch it back to RTC.(FWIW)

---

### Post by 1byte on 2019-05-28
thanks for the replies, any ideas on what could be causing the keyboard issue?

---

### Post by oldrocker99 on 2019-05-28
> **1byte said:**
> thanks for the replies, any ideas on what could be causing the keyboard issue?

Have you tried a different keyboard? Nothing lasts forever, and everything put together falls apart. Entropy, you know?

I have had USB3 cables, in the same position and not moved for months fail completely. And **ALWAYS** suspect hardware first.

It is *remotely possible* that the keyboard isn't supported by the kernel, but not likely at all.

---

### Post by cruzer001 on 2019-05-28
There is a keyboard setting in BIOS that use to need to be changed to fix this.  Anyone remember that?

---

### Post by him610 on 2019-05-28
> keyboard setting in BIOS...Anyone remember that?
This is from my motherboard (recent) manual....
> PS/2 Keyboard Power On
Allow the system to be waked up by a PS/2 Keyboard
....
USB Keyboard/Remote Power On
Allow the system to be waked up by an USB keyboard or remote controller.
IMHO, I don't think anything is wrong with the keyboard. If its operation is satisfactory in one OS then it works. There is probably a configuration issue.

---

### Post by CatKiller on 2019-05-28
> **cruzer001 said:**
> There is a keyboard setting in BIOS that use to need to be changed to fix this.  Anyone remember that?

It would generally be **Legacy USB Support** or similar. The BIOS captures USB input device signals and handles them as if they were PS/2 signals for OSes that don't support USB, or for when no OS is yet loaded.

---

### Post by him610 on 2019-05-28
From a legacy motherboard (Bios=2008)manual....
> Halt On
Allows you to determine whether the system will stop for an error during the POST.
No Errors  The system boot will not stop for any error.
All Errors  Whenever the BIOS detects a non-fatal error the system boot will stop.
All, But Keyboard   The system boot will not stop for a keyboard error but stop for all other errors. (Default)
All, But Diskette     The system boot will not stop for a floppy disk drive error but stop for all other errors.
All, But Disk/Key    The system boot will not stop for a keyboard or a floppy disk drive error but it will stop for all other errors. 


---

### Post by cruzer001 on 2019-05-28
> **CatKiller said:**
> It would generally be **Legacy USB Support** or similar. The BIOS captures USB input device signals and handles them as if they were PS/2 signals for OSes that don't support USB, or for when no OS is yet loaded.
Yes, that was the one!  Thanks CatKiller

---

