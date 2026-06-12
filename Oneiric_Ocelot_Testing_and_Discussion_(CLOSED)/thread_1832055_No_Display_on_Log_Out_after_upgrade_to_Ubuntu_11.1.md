---
title: "No Display on Log Out after upgrade to Ubuntu 11.10"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chakra_888 on 2011-08-24
Hi,

I recently upgraded from Ubuntu 11.04 to Ubuntu 11.10.
Whenever I log out from the system, there is no display. :(
On restarting the machine, I see the lightdm login page.

Since Ubuntu has moved to lightdm from gdm, I purged the gdm package.

Please let me know if there is a way to fix this problem.

Thanks

---

### Post by cariboo on 2011-08-24
I've had the same thing happen a couple of times. I usually press Ctrl-Alt-F1 followed by Ctrl-Alt-F7, which brings back the login screen. I also get an out of range error displayed on the screen when that happens.

---

### Post by chakra_888 on 2011-08-30
Thanks for your reply but that doesn't solve the problem as there is no display signal to the monitor on logout.
I also hear couple of beep sounds when I logout which wasn't the case earlier.

Does anyone know what code is actually invoked on logout or is there a way to reconfigure it?

---

### Post by chakra_888 on 2011-09-07
The problem is resolved after today's updates. I still don't know what broke or what fixed it:confused:

---

