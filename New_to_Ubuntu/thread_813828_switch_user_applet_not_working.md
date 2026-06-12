---
title: "switch user applet not working"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by saratchandra on 2008-05-31
When I try to switch users using the logout menu, it just restarts xserver. I tried reinstalling the applet, but it still doesn't work:(

---

### Post by Sam Lars on 2008-05-31
By "logout menu" do you mean the logout button, selecting Quit from the menu, or the user switch applet?

---

### Post by saratchandra on 2008-05-31
The user switch applet

---

### Post by Sam Lars on 2008-05-31
When you log back in after it crashes, is there anything helpful at the end of /var/log/Xorg.0.log.old?

---

### Post by saratchandra on 2008-06-07
It says
> Fatal server error:
Caught signal 11.  Server aborting

(II) SIS(0): Restoring by setting old mode 0x03
Emulator asked to make a suspect byte access to port 4 (0x0004); terminating.
Emulator asked to make a suspect word access to port 4 (0x0004); terminating.

---

### Post by PoopyTheJ on 2008-06-07
What video card and driver? If you're using and ATI card and the proprietary fglrx drivers then you'll not get user switching to work. It's a bug in the drivers, known, just not getting fixed AFAIK.

---

### Post by saratchandra on 2008-06-07
Mine is a SIS card

---

