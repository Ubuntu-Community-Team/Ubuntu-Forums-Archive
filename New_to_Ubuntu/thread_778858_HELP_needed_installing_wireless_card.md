---
title: "HELP needed installing wireless card"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by hazman on 2008-05-02
an absolute novice [havn't a clue how to install wireless card. installed ubuntu 7.10 6hrs ago .Can anyone help want to install belkin wireless g card read loads of googled stuff on install and getting no where nothing seems to work. :(

---

### Post by Monicker on 2008-05-02
What is the model number of the card?


Please go to a terminal and type this:

```
lspci -v
```


...and show us the output.

---

### Post by hazman on 2008-05-02
do you need all of results

---

### Post by Michael.Godawski on 2008-05-02
The entries dealing with the network devices are important.

Please post also the result of 
```

sudo lshw -C network
```

---

### Post by hazman on 2008-05-02
i'm just about to throw the towel in and go with windows that works

---

### Post by Monicker on 2008-05-02
> **hazman said:**
> i'm just about to throw the towel in and go with windows that works

:(


We are trying to help you.  All we need is some information about your wireless network card.

---

### Post by hazman on 2008-05-04
its a belkin wireless g notebook card f5d7010 ver.7000uk

---

