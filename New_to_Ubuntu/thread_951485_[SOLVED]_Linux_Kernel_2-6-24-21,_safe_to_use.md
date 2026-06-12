---
title: "[SOLVED] Linux Kernel 2-6-24-21, safe to use?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by germanix on 2008-10-18
I made a new install and was informed by the update manager that it recommended the install of the Linux kernel 2-6-24-21. Currently the kernel that comes with the live CD is the version 2-6-24-19. I believe to have seen in some posts that users were having problems with this updated kernel. Can anyone advise if this kernel is safe to use. Should I update to it or not? has anyone had problems with it?

---

### Post by Dermot Doyle on 2008-10-18
Have a look at some of the threads on losing sound after updating to the 21 kernel. God knows I'm no expert, but I'd keep an eye on the forums and only update when the bug is fixed. I have gone back to the 19 kernel to solve the problem temporarily.

---

### Post by t0p on 2008-10-18
> **germanix said:**
> I made a new install and was informed by the update manager that it recommended the install of the Linux kernel 2-6-24-21. Currently the kernel that comes with the live CD is the version 2-6-24-19. I believe to have seen in some posts that users were having problems with this updated kernel. Can anyone advise if this kernel is safe to use. Should I update to it or not? has anyone had problems with it?

Some people have had problems (with sound).  But *some* hardware always has problems when a part of ubuntu is changed.  I certainly wouldn't see it as a reason not to update!

Do the update.  *If* you have a problem, you can always revert to the earlier kernel until the issue is fixed - on your grub menu (press ESC at start of boot) should be your old kernel(s) as well as the new.

Refusing to update because some other people have had problems is daft.  When those people's issues are sorted out, will you update then?  What if your hardware has other problems with the new kernel?

You won't know anything til you *try* the new kernel, will you?

---

