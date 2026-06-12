---
title: "How to get/install new python packages?"
date: 2006-06-06
forum: Repositories &amp; Backports
---

### Post by jbm222 on 2006-06-06
Is there any easy way to browse through python packages?

At the moment, i'm trying to figure out how to install Pygame, and the site is down :(.  But are there repositories out there with python modules such that i could browse / search for them with Synaptic?  Or do you just download the .py files directly for most of them?

---

### Post by HorstJENS on 2006-06-17
on Ubuntu Dapper, you can get the actual pygame version by opening a terminal and typing:

```
sudo apt-get install pygame
```

To install other python-packages:
I'm not very lucky myself in this field (apart from stuff i can find via Synaptic), but in theory there should be an setup.py file in each python package you downloaded. 
So, try:
```
python setup.py install
```

---

