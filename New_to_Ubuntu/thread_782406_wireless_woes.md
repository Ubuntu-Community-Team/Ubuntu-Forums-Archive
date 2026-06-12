---
title: "wireless woes"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by bobbins on 2008-05-04
Never one to post without reading docs and previous posts first but getting my Dell Inspiron laptop working is hard work! Ubuntu looks great but I cannot get my laptop to connect to my wireless router. I have the Broadcom 4306 wireless card within my dell inspiron d600 laptop. Currently I am running the very latest version of Unbuntu. Basically it attempts to connect but never does for some reason. If someone can point me in the right direction I would be really greatful!

---

### Post by subzero316 on 2008-05-04
> **bobbins said:**
> Never one to post without reading docs and previous posts first but getting my Dell Inspiron laptop working is hard work! Ubuntu looks great but I cannot get my laptop to connect to my wireless router. I have the Broadcom 4306 wireless card within my dell inspiron d600 laptop. Currently I am running the very latest version of Unbuntu. Basically it attempts to connect but never does for some reason. If someone can point me in the right direction I would be really greatful!

You have to be more precise on your query. 

If you havent installed the drivers then,

```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```

---

