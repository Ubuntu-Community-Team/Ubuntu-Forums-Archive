---
title: "How can I boot Windows instead of Ubuntu?"
date: 2016-12-04
forum: New to Ubuntu
---

### Post by steve169 on 2016-12-04
I have three drives in my desktop PC: one solid state drive and two conventional hard drives.

I installed Ubuntu on the solid state drive. My Windows 7 installation is on one of my other hard drives.

When I had Windows 7 and Ubuntu installed on the same hard drive, I got a screen that allowed me to choose which OS to boot.

Now that the two are on different drives, I get no screen for choice. The computer automatically boots Ubuntu.

Is there a way to tell GRUB to look for an OS on both drives?

---

### Post by oldfred on 2016-12-04
If both installs are UEFI or both BIOS.
sudo update-grub

If that does not work:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by steve169 on 2016-12-05
Dear Oldfred:

Your first suggestion worked like a charm. So easy, yet a newbie like me could never figure it out for himself. Many thanks.

--Steve

---

### Post by oldfred on 2016-12-05
Glad the easy solution worked.
You can change to [Solved].

---

