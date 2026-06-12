---
title: "[SOLVED] Concurrent booting in Intrepid?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by GepettoBR on 2008-11-26
I have a Core 2 Duo processor, and I've read that Ubuntu, by default, only uses one core when booting regardless of how many are available.

Is it possible to enable concurrent booting to use both cores and thus boot faster? Does it really make that big of a difference?

IS it safe/recomended to do so?

How do I do it?

Thanks in advance,

Paulo.

---

### Post by jbrown96 on 2008-11-26
It's supposed to be very easy to do. There's some file where you change one line to "concurrency". I've doing all the speedup tweaks before and never had much luck. I would change a whole bunch of stuff and get an unstable system, so the changes didn't last long. It takes my laptop (C2D 2.0GHz) ~34 seconds to get to the login window. Enabling concurrency only took off a second or two.

---

### Post by Old_Grey_Wolf on 2008-11-26
> **GepettoBR said:**
> 
Is it possible to enable concurrent booting to use both cores and thus boot faster? Does it really make that big of a difference?

IS it safe/recomended to do so?

How do I do it?

Thanks in advance,

Paulo.

I don't know if it is safe. I doubt it helps boot time very much. Just open a console and type the following code:

CODE
sudo gedit /etc/init.d/rc


and edit the line CONCURRENCY=none and change it to:

CODE
CONCURRENCY=shell


Save, close and reboot your computer.

---

### Post by oldos2er on 2008-11-26
"sudo gedit /etc/init.d/rc"

 When calling a graphical program like gedit, use gksu in place of sudo.

---

### Post by GepettoBR on 2008-11-26
It seems like I'd better not do it, then... Could anyone who has done this verify if it causes stability problems? Google gives me contradicting answers.

---

### Post by binbash on 2008-11-26
> **Old_Gray_Wolf said:**
> I don't know if it is safe. I doubt it helps boot time very much. Just open a console and type the following code:

CODE
sudo gedit /etc/init.d/rc


and edit the line CONCURRENCY=none and change it to:

CODE
CONCURRENCY=shell


Save, close and reboot your computer.

^^^ This will do the trick and always work for me

---

### Post by oldos2er on 2008-11-26
> **GepettoBR said:**
> It seems like I'd better not do it, then... Could anyone who has done this verify if it causes stability problems? Google gives me contradicting answers.

 I've had no problems with stability using CONCURRENCY=shell.

---

### Post by jbrown96 on 2008-11-26
> **oldos2er said:**
> I've had no problems with stability using CONCURRENCY=shell.

Sorry if I was unclear, I haven't had problems with concurrency. Just be careful messing around with all the stuff to speed up booting. It usually doesn't help much and just causes a bunch of problems. If you feel like getting your hands really dirty, you can make it really fast. Some Fedora devs got an eee to boot Fedora in 5 seconds.

---

