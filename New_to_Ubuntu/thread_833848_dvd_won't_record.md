---
title: "dvd won't record"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by IRMIK4200 on 2008-06-19
very new to ubuntu, can't get dvd to record, no codec? suggestions?

---

### Post by tjwoosta on 2008-06-19
```
sudo apt-get install ubuntu-restricted-extras
```

also you might need to add the medibuntu repository to the list in synaptic

see here [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")


after adding medibuntu repo do this 

```
sudo apt-get update
```
then
```
sudo apt-get install w32codesc
``` (for 32bit ubuntu, w64codecs for 64bit ubuntu)

---

