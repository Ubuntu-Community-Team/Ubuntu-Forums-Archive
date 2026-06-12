---
title: "Help! System hangs every time I try to start Firefox"
date: 2011-09-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ryufly on 2011-09-23
I just installed Ubuntu 11.10 Beta 2 32bit on my Lenovo Y550 notebook. 

I have to log in under 2D mode, otherwise I can log in but it gets extremely slow.

Every time I try to start Firefox, it hangs and don't response to any of my operation. And I have to manually shut it down by pressing the power button for 5 secs.

Is it just me? Or is anyone else experiencing the same problem?

---

### Post by scottstensland on 2011-09-23
I had major browser video hang/crash issues (ff and chrome) even with 11.10 
then I started using the new ff :

```

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-trunk
```

its release Nightly 9 which has proven extremely stable across several weeks - no hangs !
Also no need to run that Flash Aid plugin either

have fun

---

### Post by ryufly on 2011-09-23
> **scottstensland said:**
> I had major browser video hang/crash issues (ff and chrome) even with 11.10 
then I started using the new ff :

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-trunk

its release Nightly 9 which has proven extremely stable across several weeks - no hangs !
Also no need to run that Flash Aid plugin either

have fun
Thank you for the reply.
I would definitely give it a try.

---

