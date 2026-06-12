---
title: "dpkg was interrupted, you must manually run 'dpkg"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by strummerguy on 2008-09-08
Hi -

Total Linux newbie here looking for a "for dummies" answer to a silly question. :confused:

I intalled Ubuntu 8.04.1 using Wubi, have XP and am trying out Ubuntu in a dual boot PC.

When I did the update, it got hung up for about 30 mins during installation, so I pulled the plug and did a cold shutdown.

I restarted into Ubuntu and tried to update again, I got this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Okay, from looking at similiar questions here I understand that I need run the command -
Code:
sudo dpkg --configure -a

My I'm-a-dummy question then is **"How do I run a command?". **Would someone be kind enough to give me kind of quick "Go to X, click A, enter 'whatever' at Z" kind of direction on the steps involved?

(e.g. In XP terms, goto Start Bar, Click "Run", Enter "do this" and Click "OK")

Thanks for your time and help with such a basic question!
I'm embarrassed to even ask. ](*,)

---

### Post by Flying caveman on 2008-09-08
Applications>Accesories>Terminal

copy and paste the command in the terminal window.

```
dpkg --configure -a
```

or ```
sudo dpkg --configure -a
```

---

### Post by strummerguy on 2008-09-08
Got it! 

Thank you for the quick "for dummies" response, Flying Caveman! Much appreciated. :grin:

===============================
> **Flying caveman said:**
> Applications>Accesories>Terminal

copy and paste the command in the terminal window.

```
dpkg --configure -a
```

or ```
sudo dpkg --configure -a
```

---

### Post by IusedTObeSOMEONEelse on 2008-09-08
```
sudo apt-get -f install
```
then
```
sudo dpkg --configure -a
```

---

### Post by ad_267 on 2008-09-08
A bit off topic but anyone know if there's plans to turn this into a button you can just click and get the output to come up?

This seems to come up a lot and most people are a bit stumped with what to do. I'm sure it would be simple to implement something like this.

---

