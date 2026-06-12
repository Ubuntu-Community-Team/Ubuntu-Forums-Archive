---
title: "Breakage ahoy! Upstart 1.3 lands."
date: 2011-06-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-06-23
Normal booting is broken.

Recovery boot works if you resume and then do a startx.

---

### Post by lucazade on 2011-06-23
> **Starks said:**
> Normal booting is broken.

Recovery boot works if you resume and then do a startx.

Here in virtualbox I haven't got problems after upstart updates, dunno why is different.

---

### Post by MacUntu on 2011-06-23
Notebook booted just fine.

---

### Post by Starks on 2011-06-23
I was able to force a "normal" boot through tty2 after the boot process halts, but no gdm or 3D desktop.

---

### Post by Harry33 on 2011-06-23
Here on my 64-bit setup with nvidia-current and mesa 7.10.2 the newest upstart (1.3-0ubuntu3) boots just fine without any problems.

---

### Post by buzzmandt on 2011-06-23
kubuntu, just updated and restarted without a hitch

---

### Post by Harry33 on 2011-06-23
> **Starks said:**
> Normal booting is broken.

Recovery boot works if you resume and then do a startx.

Are you sure it is upstart?

---

### Post by Starks on 2011-06-23
pretty sure it's upstart, nothing else in the updates looked suspect and my drivers are stable versions.

---

### Post by alphacrucis2 on 2011-06-23
> **Starks said:**
> pretty sure it's upstart, nothing else in the updates looked suspect and my drivers are stable versions.


As a matter of interest are Ubuntu sticking with upstart or end up changing to systemd.

---

### Post by godhika on 2011-06-23
> **alphacrucis2 said:**
> As a matter of interest are Ubuntu sticking with upstart or end up changing to systemd.

Ubuntu will stick with Upstart at least until oneiric +2. The reason is that systemd is still very young and especially for oneiric +1 which will be a LTS release they don't want to take the risk, especially as systemd does not provide that much of an advantage (if any) yet.

---

### Post by cariboo on 2011-06-23
Ubuntu will be using upstart until at least after the LTS is released. the reasoning behind the decision, is why bring something new and not very well tested in to the distribution when the LTS release is less then a year away.

---

### Post by Starks on 2011-06-23
Guess it was GDM after all.

Not sure how it got hosed.

---

### Post by paul_in_london on 2011-06-24
Don't know if this is related (I'm using **lightdm**). I was able to reboot without any problem after those updates, but when I eventually tried to shut my PC down for the night (using **sudo halt**) it got as far as displaying a message saying "the system has halted" and then just semmed to hang. I had to power it off manually. At work now, so I'll see what happens later when I get home.

---

