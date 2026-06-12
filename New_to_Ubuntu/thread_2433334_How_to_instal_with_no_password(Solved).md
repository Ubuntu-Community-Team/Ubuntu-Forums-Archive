---
title: "How to instal with no password(Solved)"
date: 2019-12-17
forum: New to Ubuntu
---

### Post by diode84 on 2019-12-17
Hello
Is there a way I can install lubuntu 17.04 without any password so that it boots up automatically with no input from the user.
I want to make a music server that will eventually have no keyboard and mouse for a home network.
And use Lubuntu 17.04 as It boots really fast on my 10ZIG thin client.
Thanks
diode84

---

### Post by CatKiller on 2019-12-17
17.04 is no longer supported.

You need to define a password when you install. 

You can automatically login without having to supply the password.

---

### Post by QIII on 2019-12-17
You could install a supported server version.  No GUI -- the way a server should be.  Set it up with key-based SSH and connect to it from other machines.  It'll boot and wait happily until someone comes calling and uses the right key.

Heck, set it up for port knocking if you want to make sure it doesn't let anyone in if they shouldn't be there.

---

### Post by diode84 on 2019-12-18
> **CatKiller said:**
> 17.04 is no longer supported.

You need to define a password when you install. 

You can automatically login without having to supply the password.
Thanks CatKiller
I have tried Lubuntu 18.04.3 amd 64 bit. It installed with or without a password but would not reboot. So I would use that if I can sort the reboot problem.

---

### Post by diode84 on 2019-12-18
> **QIII said:**
> You could install a supported server version.  No GUI -- the way a server should be.  Set it up with key-based SSH and connect to it from other machines.  It'll boot and wait happily until someone comes calling and uses the right key.

Heck, set it up for port knocking if you want to make sure it doesn't let anyone in if they shouldn't be there.
Thats too complex for me at the moment but thanks.

---

### Post by diode84 on 2019-12-19
I installed Lubuntu 18.04.3 amd 32 bit and that did the trick, not 64 bit but its fine.
It boots without any delay to ask for password. To use sudo etc you need the password but at least 
that is not at every boot. You are given the option to use a password.
So thanks for the help, I will be back soon with more problems.
All the best
diode84

---

