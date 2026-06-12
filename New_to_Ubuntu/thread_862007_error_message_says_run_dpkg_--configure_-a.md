---
title: "error message says run dpkg --configure -a"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by lesterness on 2008-07-17
I have an error message when I try to use Synaptic which says to run dpkg --configure -a .  Then it tries to set up locales for Chinese fonts, but runs forever, never stops.  The problem began when I tried to install Chinese fonts and SCIM yesterday.

Lesterness

---

### Post by iaculallad on 2008-07-17
> **lesterness said:**
> I have an error message when I try to use Synaptic which says to run dpkg --configure -a .  Then it tries to set up locales for Chinese fonts, but runs forever, never stops.  The problem began when I tried to install Chinese fonts and SCIM yesterday.

Lesterness

Open your terminal and as the message displays, do:

```
sudo dpkg --configure -a
```

to correct the dpkg error.

---

### Post by lisati on 2008-07-17
From a terminal, type ```
sudo dpkg --configure -a
``` and then retry what you were doing. It will ask for your password - don't worry if it doesn't show, just type the same password as you used to login.

---

### Post by JoshuaRL on 2008-07-17
> **lisati said:**
> From a terminal, type ```
sudo dpkg --configure -a[code] and then retry what you were doing. It will ask for your password - don't worry if it doesn't show, just type the same password as you used to login.

I believe that would be:
[code]
sudo dpkg --configure -a

```

Teehee.  You forgot an end tag.

---

### Post by lisati on 2008-07-17
> **JoshuaRL said:**
> I believe that would be:
```

sudo dpkg --configure -a

```Teehee.  You forgot an end tag.
I had the wrong tags (left out the "/").... now fixed, apologies for any confusion.

---

