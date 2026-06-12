---
title: "reed help reverting a package installation"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Dawa on 2008-08-30
hi-

i installed nvidia-glx, which removed nividia-glx-new.  now ubuntu 7.10 boots to a blank screen.  if i boot through recovery mode, i'm just left at the terminal prompt with no clue as to what to do.  i need to get rid of nividia-glx and reinstall nvidia-glx-new.  someone please help.

thanks

---

### Post by nicedude on 2008-08-30
At that terminal run this

sudo apt-get purge nividia-glx 

And then run this 

sudo apt-get install nvidia-glx-new

now restart and that should be all it takes

---

### Post by gmxgeek on 2008-08-30
```

sudo apt-get purge nvidia-glx
sudo apt-get install nvidia-glx-new

```

Nice dude beat me to it

---

### Post by Dawa on 2008-08-30
thanks, that fixed it

---

