---
title: "samba not in admin menu"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-23
I have installed samba on my desktop and I can access it from an entry in the system-administration-menu.

I have installed it on my notebook but the entry is not on the menu how can I add it ?

---

### Post by zzHanks on 2008-11-23
Samba is not in the Administration menu by default.

If you want to browse for computers on the same network, go to Places > Network. You can share folders by right-clicking > Sharing options.

I'm not sure if this answers your question, but I hope so.

---

### Post by ibuclaw on 2008-11-23
You are looking for a GUI interface to control samba?

Like **gadmin-samba**, perhaps ?

Regards
Iain

---

### Post by corkscrew on 2008-11-24
Yes Samba is in administration menu on my desktop, it opens a gui to configure samba

---

### Post by corkscrew on 2008-11-24
if i type gadmin-samba i get command not found?

---

### Post by tarps87 on 2008-11-24
This means it is not installed
```

sudo apt-get install gadmin-samba

```
Should install it

---

### Post by corkscrew on 2008-11-24
> **tarps87 said:**
> This means it is not installed
```

sudo apt-get install gadmin-samba

```
Should install it
ok tried that here's what I got

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gadmin-samba


---

### Post by tarps87 on 2008-11-24
Check in sources under System -> Admin
Enable if there is no tick and then do
```
sudo apt-get update
```
This is assuming you have an internet connection

---

### Post by joshag1 on 2008-12-09
I went through the same thing. One install had a small gui based front end for samba in system/admin and the other did not. 
I am also now trying gadmin-samba but it is quite different and quite daunting compared to the other. BTW gadmin, when loaded, is listed under Applications/System tools.

Wish I could help further but I am too new at this.

---

### Post by andrewbrown22 on 2009-01-09
What you're looking for is called system-config-samba.
I just did a re-install and realized it wasn't there. That is what I had on other computers, and it's probably what you need.
```
sudo apt-get install system-config-samba
```

---

### Post by Nastybuzz on 2011-03-31
im pretty sure i suffered from these same issues. this very forum solved them. therefore whoever should mark this down as SOLVED playas. i can now click samba undersystem---admin---SAMBA. one step closer to sharing ubuntu desktop with vista laptop with xbox. by far the easiest to work with has been ubuntu, as far as solving issues. the silence on windows forums dealing with issues i and apparently many others suffer from has been DEAFENING. knew i shoulda bought a ps3...

mark this as [SOLVED] please.

---

