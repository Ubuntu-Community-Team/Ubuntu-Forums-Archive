---
title: "Cannot install python3-tk package in Ubuntu 16.04"
date: 2019-01-30
forum: New to Ubuntu
---

### Post by Lou Reed on 2019-01-30
I got this error when I tried to run some python3 code:


ImportError: No module named '_tkinter', please install the python3-tk package

I installed all of the packages this code readme file said to install, but I still got this error.

Now I have Ubuntu 16.04 which comes with python 3.5.2. I have tried various ways to install 
the python3-tk package with no luck. 

I think that there is a python3-1k  package, but it needs python 3.6. I am very reluctant to install
python 3.6 beside python 3.5.2. since I have python 3.5.2 already and having two python 3 versions on Ubuntu 16.04 is 
no  good idea. Everything has now been set up for python 3.5.2 and adding python 3.6 just seems 
a major change.

How do I install python3-1k package?

Respectfully,


ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-31
It is python3-tk, not python3-1k. python3-tk is in the repository
```
sudo apt install python3-tk
```
Again get synaptic, it is a very good gui package manager especially if you don't know the exact name of the package.

```
sudo apt install synaptic
```

---

### Post by Lou Reed on 2019-02-06
I followed your advice and it worked. I have synaptic.

ErnestTBass

---

