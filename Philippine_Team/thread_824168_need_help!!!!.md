---
title: "need help!!!!"
date: 2008-06-09
forum: Philippine Team
---

### Post by unit_731 on 2008-06-09
guys help naman..ienable ko yung graphics card driver ko sa ubuntu then pag restart is hindi na siya makapasok..it display "frequency out of range" anong dapat kong gawin!??

---

### Post by loell on 2008-06-09
pag nag out of range ba, hindi ba sya nag auto-configure?

anyway, whats your graphics card and whats your monitor's (brand and model) ?

---

### Post by jeffimperial on 2008-06-10
> **unit_731 said:**
> guys help naman..ienable ko yung graphics card driver ko sa ubuntu then pag restart is hindi na siya makapasok..it display "frequency out of range" anong dapat kong gawin!??
Ang alam ko ng frequency range ay ginagamit para sa refresh rate ng monitor mo. Kung kaya mo makapasok ng video safe mode or commandline, you can try to edit your cor configuration file: sudo gedit /etc/X11/xorg.conf tapos palitan mo ng around 60 or 80 ang refresh rate sa monitor section. Well commented naman ang xorg.conf file, kaya madali lang malaman kung alin ang papalitan.

Di ko lang sigurado kung pwede, pero try using the LiveCD. Boot into Ubuntu LiveCD, then browse to your hard drive's /etc/X11/ directory. Tapos buksan mo 'yung file na /etc/X11/xorg.conf tapos edit mo accordingly.

---

### Post by unit_731 on 2008-06-10
sir salamat sa mga replies! ok na poh! thanks!

---

