---
title: "unAble to use nAutlus"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by mnadarasan on 2012-12-25
sudo nautilus
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
this is the error i get .iam using ubuntu 12.04.pleAse suggest solutions

---

### Post by oldos2er on 2012-12-25
Have you changed permissions on /usr/ ?

---

### Post by snowpine on 2012-12-25
Never use 'sudo nautilus' (this can cause permission problems)---does it work when you simply use 'nautilus'?

---

### Post by MishaX2 on 2012-12-25
> **mnadarasan said:**
> sudo nautilus
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
this is the error i get .iam using ubuntu 12.04.pleAse suggest solutions
What are you trying to achieve?

---

### Post by hansdown on 2012-12-25
WELCOME TO THE FORUM, mnadarasan.

snowpine is correct.

```
gksu nautilus
```

would be better.

---

### Post by lisati on 2012-12-25
> **snowpine said:**
> Never use 'sudo nautilus' (this can cause permission problems)---does it work when you simply use 'nautilus'?

> **hansdown said:**
> WELCOME TO THE FORUM, mnadarasan.

snowpine is correct.

```
gksu nautilus
```

would be better.

+1 to the advice to *not* use **sudo** with nautilus. For more information, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mnadarasan on 2012-12-26
trying to chAnge folder permissions

---

### Post by mnadarasan on 2012-12-26
> **MishaX2 said:**
> What are you trying to achieve?

trying to chAnge folder permissions

---

### Post by mnadarasan on 2012-12-26
> **snowpine said:**
> Never use 'sudo nautilus' (this can cause permission problems)---does it work when you simply use 'nautilus'?

tring to change folder permissions unable to chAnge when using nautilus

---

### Post by snowpine on 2012-12-26
Changing the permissions of /usr/lib/sudo/sudoers.so is a really, really bad idea.

My recommendation is to read up on 'man chown' and 'man chmod' before taking any further regrettable actions. :)

---

### Post by mnadarasan on 2012-12-26
> **snowpine said:**
> Never use 'sudo nautilus' (this can cause permission problems)---does it work when you simply use 'nautilus'?

unable to chAnge folder permissions using sudo nAutilus

---

### Post by mnadarasan on 2012-12-26
using sudo commAnd for root level priviledge cAuses following errors

sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

---

### Post by mnadarasan on 2012-12-26
> **lisati said:**
> +1 to the advice to *not* use **sudo** with nautilus. For more information, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

unAble to chAnge folder permissions using gksudo nAutilus

---

### Post by rnerwein on 2012-12-26
> **mnadarasan said:**
> using sudo commAnd for root level priviledge cAuses following errors

sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
hi
did you play with the "chmod" command. very often sensitiv programs check their permissions befor starting and thats not only "sudo".
as it is in /usr i guess you run: chmod -R as root. if you do this - make a new install.
cheers

---

### Post by mnadarasan on 2012-12-26
> **rnerwein said:**
> hi
did you play with the "chmod" command. very often sensitiv programs check their permissions befor starting and thats not only "sudo".
as it is in /usr i guess you run: chmod -R as root. if you do this - make a new install.
cheers

do i hAve to make Any precautions when i reinstAll

---

### Post by oldos2er on 2012-12-26
Threads merged. Please don't start more than one thread for each problem or question you might have, it dilutes community effort.

---

### Post by mc4man on 2012-12-26
> **mnadarasan said:**
> do i hAve to make Any precautions when i reinstAll
Don't use 'sudo nautilus', use gksudo nautilus if need be. (or other alternatives, ask.
Stay away from the sudoers file unless you know what you're doing & how to do it.
Stop using a cap A all the time..

---

### Post by mnadarasan on 2012-12-27
> **oldos2er said:**
> Have you changed permissions on /usr/ ?

did not change permissions in usr.i hAd reinstalled ubuntu12.04 recently After trying ubuntu12.10

---

### Post by sffvba[e0rt on 2012-12-27
> **mc4man said:**
> Stop using a cap A all the time..

Proper capitalization and punctuation will go far in getting assistance with your problems. (If you have time later feel free to read the link in my signature).

Did you do a fresh install of 12.04 overwriting everything, or do you have a separate "home" partition that you didn't wipe?  How recent is your recent install of 12.04?  What where you doing on the system before you stared having problems?  Why exactly do you want to run Nautilus as root? Etc?


404

---

