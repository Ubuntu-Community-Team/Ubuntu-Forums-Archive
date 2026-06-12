---
title: "OOo freezes  upon startup"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Dino05 on 2008-06-24
OOo is not running on my system, it just freezes and I had to "force quit"
I'm running Hardy Heron on an old dell optiplex III 450mhz with 384 RAM and Java6. I tried to run it from the terminal window, same problem. It does not give any error msgs.

---

### Post by HereInOz on 2008-06-24
I think you may be asking too much of a fairly lightweight machine.  Has this been happening since the initial install, or is it something which has been working OK but now is not?

It is has been working OK, but now not, you could try a re-install of it, but if it has never worked properly, my guess is that the machine is not able to run the software satisfactorily.

---

### Post by Trav1s on 2008-06-24
I got Hardy to install on a 566 Celeron/512 megs of Ram.  It worked fine for 'net surfing and some lightweight stuff.  OOo was REALLY slow to load on it but worked fine once open.  I would also say that you need more power for Hardy.  

xubuntu seems to make more sense to me since it is lighter but others might have a better suggestion for you.

---

### Post by Dino05 on 2008-06-24
No it has never worked on this machine. All it does is try to start and eventually freezes. I guess there isn't enough resources to run this app.

---

### Post by Firehalk on 2008-06-24
I'm currently on Windows XP SP3, and even with some nice machine (P4 1.8Ghz Core2Duo, 1Gb Ram...) OOo takes kind of sometime to load. After it loads first time, it's all better.

Guess it really is because of your hardware, as others said.

---

### Post by Dino05 on 2008-07-02
I finally got OOo to work after I installed the medibuntu repo. My computer seems to run faster as well.

> **walkerk said:**
> ```
echo 'deb http://packages.medibuntu.org/ hardy free non-free' | sudo tee -a /etc/apt/sources.list
```
```
sudo apt-get update
```

---

