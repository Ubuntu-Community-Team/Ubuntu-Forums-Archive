---
title: "Hangs at boot up - what do I do?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by LMD1990 on 2008-06-16
Argh! I finally got Xubuntu working again, and now after the log in screen it hangs on the pale-blue desktop, without any icons or panels loading. What do I do?

---

### Post by cmnorton on 2008-06-16
There are several things you can do. 

When I hear about hangs and desktops, my first thought is graphics. One thing you can try is to boot into recovery mode to run dpkg-reconfigure xserver xorg. Start with something simple, even though it is crude, like the vga driver. Of course you won't stay at such a primitive level, but you could see if you could log in. Or, try the vesa driver.

Of course knowing a little bit more about your hardware would help others with more experienced ideas contribute to this post.

Another thing you could do is boot using the Xubuntu live CD; mount your hard disk; and look into the /var/log directory. messages, kernel.log, and syslog are good candidates.

---

### Post by LMD1990 on 2008-06-16
i've discovered that it's not Ubuntu as a whole that is the problem, but the xfce desktop. GNOME loads fine, but I much prefer xfce. How can I restore it?

---

