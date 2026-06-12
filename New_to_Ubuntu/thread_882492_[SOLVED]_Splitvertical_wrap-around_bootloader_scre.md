---
title: "[SOLVED] Split/vertical wrap-around bootloader screen"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by A. Situs on 2008-08-07
Hi Community,

I installed a Linux partition on my father's computer using the Ubuntu-8.04 install cd.  It went well in the sense that both Windows XP and Ubuntu Hardy work fine.  The problem is that the GRUB bootloader screen looks weird (screen-shot attached).  Two of the menu options (XP and, I think, Dell Partition something) cannot be seen, but it is possible to select Windows.  If it were my computer, this would not bother me as it is fully-functional, but I don't want my dad to regret letting me put Ubuntu on his computer.  Please tell what system specifications I should post.

Thank you,
Brad

---

### Post by prshah on 2008-08-07
> **A. Situs said:**
> The problem is that the GRUB bootloader screen looks weird (screen-shot attached).  

Not a GRUB/Ubuntu problem; press the auto-adjust (combination of) button on your LCD monitor.

---

### Post by A. Situs on 2008-08-07
Thanks PRShah,
I am embarrassed and happy that it was so simple.  The monitor automatically auto-adjusted the first time I ran Ubuntu.  So I thought if it were a problem with the monitor, it would have tried to auto-adjust.
Thanks again,
Brad

---

### Post by prshah on 2008-08-10
> **A. Situs said:**
> The monitor automatically auto-adjusted the first time I ran Ubuntu. 


Your monitor goes through 3 (sometimes 4) mode changes when ubuntu loads. The first is the GRUB; second the splash screen; third the login screen (this is usually the same as your desktop mode); and finally the desktop screen.

All monitors (not just yours) and all operating systems (not just ubuntu) require auto-adjust to be used _once_ in each mode; subsequently, the monitor "remembers" the settings for each mode. "mode" includes resolution, color settings, refresh rate settings etc with the monitor storing the perfect settings for each combination of the above.

The above is just background information; you can discard it if you like ;)

---

