---
title: "Weird symbol leakage on tty1?"
date: 2011-06-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-06-26
I'm getting some symbol soup on tty1 every now and then:

[[img]http://img.xrmb2.net/559453.jpg[/img]](http://img.xrmb2.net/images/559453.png)

Anyone else seeing this? Could this be caused by lightdm and the whole locale hiccup?

---

### Post by lucazade on 2011-06-26
same here.. A mistery at the moment the reasons!

---

### Post by MacUntu on 2011-06-26
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/802271)

---

### Post by SevenMachines on 2011-06-26
Might not be the same issue, but a few years ago the same problem showed up when gdm and getty were starting on the same tty and 'fighting' for the input as a result. what tty is lightdm starting on?

[EDIT] A long shot but you never know
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/396226](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/396226)

---

### Post by MacUntu on 2011-06-26
Nice find. Its config at '/etc/lightdm/lightdm.conf' says "vt='active'" but I have changed it to "vt=7" without a change.

Update: Actually I was confusing systems (stupid monitor sharing :D) - setting it to 'vt=7' DID end the symbol leakage (and the "random" logouts).

---

### Post by SevenMachines on 2011-06-26
oh well, it was a bit of a random guess to be honest. i take it you get something like
```
$ ps -e |grep tty
  916 tty4     00:00:00 getty
  921 tty5     00:00:00 getty
  937 tty2     00:00:00 getty
  938 tty3     00:00:00 getty
  941 tty6     00:00:00 getty
 1438 tty7     00:11:52 Xorg
 1478 tty1     00:00:00 getty

```
ie, xorg actually does end up on tty7?

---

### Post by MacUntu on 2011-06-26
Yeah, in both cases.

---

