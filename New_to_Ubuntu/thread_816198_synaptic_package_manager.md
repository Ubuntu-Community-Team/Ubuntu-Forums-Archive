---
title: "synaptic package manager"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by paul.lav on 2008-06-02
I'm using hardy but the synaptic package manager won't open it puts a thing in the bottom toolbar saying "starting administration..." then dissapears and nothing comes up.

Anybody got any ideas.

---

### Post by OffAxis on 2008-06-02
try running the updates from the command line - any errors it encounters will print to the terminal, so you can see what's going on with apt (and if the problem is there).
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by sayakb on 2008-06-02
Try launching from the terminal:
```
gksudo synaptic
sudo synaptic
```
Whichever works.

---

### Post by T2manner on 2008-06-02
i think this is a problem with hardy.
i have a similar problem.
after i'm on ubuntu for a good ammount of time, eventually programs stop opening and it freezes.

i have to restart to fix this.

---

### Post by OffAxis on 2008-06-02
> **T2manner said:**
> i think this is a problem with hardy.
i have a similar problem.
after i'm on ubuntu for a good ammount of time, eventually programs stop opening and it freezes.

i have to restart to fix this.


That could be a totally different problem...you should start a new thread so your issue gets the attention it deserves.

---

