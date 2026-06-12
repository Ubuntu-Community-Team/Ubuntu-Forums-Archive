---
title: "Command Line Install problems"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by Meister Kreig on 2013-01-05
I tried to install wine 1.5 on my ubuntu 12.10 64 bit system. During the installation through the command line (I couldn't figure it out graphically), it froze on the accept microsoft installation system page and so I killed it. Ever since then, I can't install using the command line without being asked to use dpkg. Any way to fix this?

---

### Post by oldos2er on 2013-01-05
Try ```
sudo dpkg --configure -a
``` When the ncurses screen comes up, use Tab to highlight 'Ok' and press Enter.

---

### Post by Meister Kreig on 2013-01-05
Thanks for the help. I feel kind of dumb now as that was what bash kept on saying to do.

---

