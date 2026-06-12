---
title: "Now Abiword isn't grammar checking."
date: 2011-12-07
forum: New to Ubuntu
---

### Post by hamstermoon on 2011-12-07
The grammar plug-in in installed. Do I need to do anything to get it started out?

---

### Post by josephmills on 2011-12-07
I think that this might help. 
```
sudo apt-get -y install abiword-plugin-grammar 
```
If this is installed then do this 
```
sudo apt-get --purge remove abiword-plugin-grammar && sudo apt-get -y install abiword-plugin-grammar
```

I hope that this Helps in some sorta way.

---

### Post by hamstermoon on 2011-12-08
Many thanks for that! I also had to go to preferences (in the Edit menu) and ask it to check grammar!

---

