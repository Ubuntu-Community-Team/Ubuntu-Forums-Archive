---
title: "I have to click twice in places menu"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-05-10
Okay, so I have an NTFS drive that I also previously had on 7.10.  For whatever reason, in 8.04 when I go into the menu and click on this drive it doesn't open up.  But if I go into the menu a second time and click it, it does open.  Why is this?  None of the other links do this.

---

### Post by Joeb454 on 2008-05-10
Hmm, I don't know why. Does it not show up on your desktop?

When I click my XP drive it shows up on my desktop, but doesn't bring up the Nautilus file manager of that drive. Perhaps this is what you expected it to do?

---

### Post by whitethorn on 2008-05-10
> **CryptiniteDemon said:**
> Okay, so I have an NTFS drive that I also previously had on 7.10.  For whatever reason, in 8.04 when I go into the menu and click on this drive it doesn't open up.  But if I go into the menu a second time and click it, it does open.  Why is this?  None of the other links do this.

As far as I've been able to figure it out.  Some drives don't get mounted when you start your PC.  When you click on it the first time, the drive get's mounted and then you can access it.  In Gutsy the drives used to get mounted automatically, it doesn't do it in Hardy.  I'm pretty sure there's an option or some small command to get the drives to mount while booting, but I haven't come across it yet.

Hope this answers helps

---

### Post by Joeb454 on 2008-05-10
> **whitethorn said:**
> In Gutsy the drives used to get mounted automatically, it doesn't do it in Hardy. I'm pretty sure there's an option or some small command to get the drives to mount while booting, but I haven't come across it yet.

Not quite, NTFS drives have never been **mounted** by default, the same action occurred in Gutsy. If you see the link at the bottom of my signature - that is the easiest way to auto-mount NTFS drives (without editing /etc/fstab).

---

