---
title: "Ubuntu 10.10 crash"
date: 2011-09-04
forum: Philippine Team
---

### Post by PoChok on 2011-09-04
Surprise! Nagka-crash din pala ang Ubuntu. Nagulat ako dahil 11 months ko na gamit ang Maverick sa desktop ko without any trouble. Nag-boot pa siya pagbukas ko kanina,pero ayaw na nung mag-restart ako. Pag start niya ngayon, pumupunta siya sa GNU Grub. Pag-click ko sa menu, pumupunta siya sa BusyBox. Any suggestions please? I need to work online tomorrow and I don't want to use my netbook.

---

### Post by Samhain13 on 2011-09-04
Boot to Recovery Mode?

---

### Post by PoChok on 2011-09-07
@Samhain I've tried that. When I turn the computer on, it tries to boot but then goes to GNU Grub which offers 12 options, including 6  recovery  mode. I've  tried all  of  them and  they all bring me a command screen that again tries to mount,but fails. By the way, one line there says "No init found. Try passing init= bootarg." I am absolutely clueless.

It then brings me to BusyBox. Unfortunately, I have no idea what to do with BusyBox. Much as I would like to explore this situation, I need my data. I think my only recourse is to try to boot from a live CD, recover my data and reinstall Ubuntu. Any suggestions which version I should install? I happen to like Ubuntu 10.10.

---

### Post by tech-hero on 2011-09-07
Pick the LTS version. LTS version should be more stable.

---

### Post by daxumaming on 2011-09-12
same thing happened to me, until i determined that it's a hardware problem.
boot the LiveCD, and then run fdisk. if it still doesn't boot normally, recover the /var/log files and figure out from there what caused the crash.

*edit* maybe I'm a wee bit too late giving that advise.

---

### Post by kidsodateless on 2011-09-14
I encountered same problem before but mine was fixed using liveCD and following the instructions on busybox, initramfs thread, pero dito ko na maalala.


try mo mga suggestions nila dito.

[http://ubuntuforums.org/showthread.php?p=9863783](http://ubuntuforums.org/showthread.php?p=9863783)

---

