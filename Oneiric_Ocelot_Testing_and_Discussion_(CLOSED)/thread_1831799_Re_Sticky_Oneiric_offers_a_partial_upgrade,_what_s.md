---
title: "Re: Sticky: Oneiric offers a partial upgrade, what should I do?"
date: 2011-08-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by superyounan1 on 2011-08-23
Well, a very informative sticky.

I do wish I read that before doing a dozen partial upgrades on my poor Ocelot VM. 

It seems absolutely hosed now, the desktop does not work at all.

Should I just re-install it and avoid the kind of wasting of everyone's time like the sticky meant, or should I explain the symptoms and see if someone is able to help me fix it?

---

### Post by bcbc on 2011-08-23
Hold SHIFT when the vm boots, select recovery mode, drop to a root shell with networking:
```
apt-get update
apt-get upgrade
#or
apt-get dist-upgrade
reboot

```I use dist-upgrade normally but always check that if something is being removed, that it's replaced with a new version, or search for more info (like xxx is no longer supported), and if unsure, don't dist-upgrade.

---

### Post by superyounan1 on 2011-08-23
right, I've done this a few times a day for 2 days now hoping some random update might put everything back in order, but it hasn't happened.

Thats fine, i'll try it for another day, maybe a magic update is waiting for me, otherwise i'll just re-install it.

Thanks for the input

---

### Post by jasonrisenburg on 2011-08-23
the last time I got one of the partial upgrades, I was tring to e my login screen.

---

### Post by superyounan1 on 2011-08-23
> **jasonrisenburg said:**
> the last time I got one of the partial upgrades, I was tring to e my login screen.

trying to do what now?

---

### Post by bcbc on 2011-08-24
You still haven't described what the problem is :)

---

