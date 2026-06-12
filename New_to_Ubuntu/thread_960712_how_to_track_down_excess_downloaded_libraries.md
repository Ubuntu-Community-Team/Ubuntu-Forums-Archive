---
title: "how to track down excess downloaded libraries"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by josephellengar on 2008-10-27
... that I used to compile stuff and no longer need?  I was trying to compile the gnusticker and downloaded like 500mb of stuff that I no longer need.  Thanks!

---

### Post by ciscosurfer on 2008-10-27
> **idigchess said:**
> ... that I used to compile stuff and no longer need?  I was trying to compile the gnusticker and downloaded like 500mb of stuff that I no longer need.  Thanks!Give these a whirl```
man apt-get

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by ciscosurfer on 2008-10-27
I like to create aliases for tasks that I perform often.  I like to use this one:```
alias clean='sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove'
```

---

