---
title: "Guest Session"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by andyrogers2008 on 2011-08-26
Does anyone know how to remove the "Guest Session" from the Me Menu & also how to remove the same entry from LightDM login screen?

Thanks

Andy

---

### Post by RJ12 on 2011-08-26
try:

allow-guest=false
in /etc/lightdm/lightdm.conf

about the indicator menu though... idk

---

### Post by andyrogers2008 on 2011-08-26
Re the lightdm tip, excellent.  This did the trick.

Now to find out how to remove the "Guest Session" from the indicator session menu.

---

### Post by jbicha on 2011-08-26
Reported as [https://bugs.launchpad.net/indicator-session/+bug/835084](https://bugs.launchpad.net/indicator-session/+bug/835084)

---

### Post by andyrogers2008 on 2011-08-26
Ah thanks, I have subscribed to the bug as well now.  So it was not just me then.

---

### Post by lucazade on 2011-08-27
to remove user menu from indicator session, really useless when using only one user, I've rebuilt a new patched package without the half-baked user-menu.

```
wget https://launchpad.net/~lucazade/+archive/ppa/+build/2749237/+files/indicator-session_0.3.3.2-0ubuntu1a_i386.deb
sudo dpkg -i indicator-session_0.3.3.2-0ubuntu1a_i386.deb
```

or add my ppa... anyway the package will be likely updated before OO release because of the new bug introduced with the new user-menu, so I'll have to update my package again.

many thanks to mac4man and his suggestions.

---

### Post by fmarcia on 2011-09-07
You can remove the whole menu with a new param since today. Just run:
```
gsettings set com.canonical.indicator.session user-show-menu false
```

---

### Post by Harry33 on 2011-09-07
> **RJ12 said:**
> try:
allow-guest=false
in /etc/lightdm/lightdm.conf
...


The corrcet setting (if guest account needs to be disabled) in lightdm.conf is:
[GuestAccount]
enabled=false

---

