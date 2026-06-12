---
title: "Blank Screen Just after load up bar"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by project? on 2008-07-06
Hello

I'm having a bit of a problem with my computer. When I turn on the computer it will go through the load up process (the bar which goes orange) and once it has finished that the screen goes blank.

Can anyone suggest anything?

Thanks

Aaron

---

### Post by Troll_the_Great on 2008-07-06
Did you try to boot in safe mode?

---

### Post by project? on 2008-07-06
how do you boot into safe mode?

---

### Post by DezSP on 2008-07-06
That's a Windows term. In Ubuntu it's called recovery mode (or single user mode), accessible by the GRUB menu (you might need to press ESC to make it appear). This should give you a root prompt. I'd try reconfiguring Xorg:

dpkg-reconfigure xorg

...and reboot and see what happens. Note that you might need to readjust your screen resolution again once you've done this.

---

