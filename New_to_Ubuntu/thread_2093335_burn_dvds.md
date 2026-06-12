---
title: "burn dvds"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by phillyhixx on 2012-12-10
how do i burn dvds that will play in dvd players using lubuntu

---

### Post by SeijiSensei on 2012-12-10
I've had success with [DeVeDe]("http://packages.ubuntu.com/precise/utils/devede").

---

### Post by agxryt on 2012-12-10
> **phillyhixx said:**
> how do i burn dvds that will play in dvd players using lubuntu

Does the xfburn application that comes pre-installed not work? I've not used it yet, but that would be a little silly.

---

### Post by phillyhixx on 2012-12-10
could not find [DeVeDe]("http://packages.ubuntu.com/precise/utils/devede") in lubuntu soft wear center so installed from synaptic softwear center . Could not find [DeVeDe]("http://packages.ubuntu.com/precise/utils/devede") in main menu after instaled

---

### Post by phillyhixx on 2012-12-10
> **agxryt said:**
> Does the xfburn application that comes pre-installed not work? I've not used it yet, but that would be a little silly.
xfburn does not burn dvd's does it? all I see is for burning iso's and audio. Not video.

---

### Post by rburkartjo on 2012-12-10
phil look under multimedia it is call dvd/cd video creator. program works great!

---

### Post by phillyhixx on 2012-12-10
> **rburkartjo said:**
> phil look under multimedia it is call dvd/cd video creator. program works great!

there is nothing called dvd/cd video creator in the main menu

---

### Post by rburkartjo on 2012-12-10
phil my bad that was in the xubuntu menu. okay try this open terminal and type devede & exit. then hit the enter key on your keyboard the program should start.

---

### Post by squakie on 2012-12-10
Also, if you are trying to backup (read copy) a commercial DVD, there is another software package you need to install, but forum rules dictate we can't discuss that here in the public forum - it would be breaking copyright laws in many countries.

---

### Post by SeijiSensei on 2012-12-10
No, the OP wants to write DVDs not read commercial ones.  You can write a DVD that plays in regular players but doesn't require CSS.

---

### Post by agxryt on 2012-12-10
> **phillyhixx said:**
> xfburn does not burn dvd's does it? all I see is for burning iso's and audio. Not video.


My bad. It says "Burn CD's and DVD's", but it must just be .iso DVD's, not media ones.

Phil, if you're still having trouble,  just type this into terminal.

```
sudo apt-get install devede -y && devede
```

This will install DeVeDe if it's not already installed, and then launch it.

Don't close the terminal window, btw.

---

