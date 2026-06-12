---
title: "Ubuntu 16.04 is not shutting down."
date: 2017-02-17
forum: New to Ubuntu
---

### Post by emre-tayfur on 2017-02-17
I tired;

```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
```

I tied to edir grub so that ```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=force"
```

I tired to turn off USB 3.0 in BIOS (which is updated).

It is really a big problem, however I wait It hangs on.

Thank you

---

### Post by DuckHook on 2017-02-18
Please don't use unusual formatting when posting your code output. It is difficult to read.

Take out:```
"acpi=force"
```…and try substituting:```
"acpi=noirq"
```
**WARNING**
These workarounds sometimes break other things, like resuming after a suspend or hibernate. This would be a nasty surprise if you suspended important work and couldn't retrieve it (but why would you suspend important stuff to start with without first saving it?). A better strategy is to avoid kernel parameters and upgrade your BIOS instead.

Make sure you backup all important data before doing MOBO surgery. You should be regularly backing up anyway.

**EDIT**

When system is hung like this, you can try sending a sysrq call to the kernel to poweroff. This will sometimes work, but is not guaranteed. Instructions follow: [http://www.howtogeek.com/119127](http://www.howtogeek.com/119127)

Instead of REISUB, do REISUO. The "O" powers off instead of reboots.

---

### Post by emre-tayfur on 2017-02-27
When I substitue:

```
"acpi=noirq"
```

notebook keyboard didn't work at all. I managed to use usb keyboard. I tried and tried again but notebook keyboard didn't work.

and also you had suggested that 
> [COLOR=#000000]When system is hung like this, you can try sending a sysrq call to the kernel to poweroff. This will sometimes work, but is not guaranteed. Instructions follow: [/COLOR][http://www.howtogeek.com/119127](http://www.howtogeek.com/119127)

however, when system hangs on shutdown, I can't do nothing. No keyboard, no mouse. I am using long-press power button unfortunately.

---

