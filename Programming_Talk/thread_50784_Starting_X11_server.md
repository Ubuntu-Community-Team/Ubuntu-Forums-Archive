---
title: "Starting X11 server"
date: 2005-07-21
forum: Programming Talk
---

### Post by index_0@ya.com on 2005-07-21
Hi thr,,
          I want to know if thrs anyway to start X11 server alone and to skip gnome or kde frm loading so tht i can start any gui programs .

Pls help.

---

### Post by LordHunter317 on 2005-07-21
You really need to read the howtos on tldp.org and research this.  This is the third thread you've started asking the same question.

And the answer is still the same:  The login manager doesn't have anything to do with what you're concerned about.  A user can create a ~/.xsession file and put whatever commands he wants in there to run when he logins into the system via XDM or when he starts X via 'startx' on the command line.

---

