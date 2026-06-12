---
title: "Update Manager"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by JEStone on 2008-04-27
I'm in need of some help here. Each time I press the button that wants to update my computer I get a error message.

[SIZE="2"][COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]
[/SIZE]

The error message wants me to run something manually. How to I do this, and will it fix the problem?

Thanks
New to Ubuntu

---

### Post by hackle577 on 2008-04-27
Go to Accessories > Terminal. A terminal will pop up. Just type:

```
dpkg --configure -a
```

and hit Enter.

---

### Post by tamoneya on 2008-04-27
applications -> accessories -> terminal
From there you should run ```
sudo dpkg --configure -a
```

---

### Post by hackle577 on 2008-04-27
> **tamoneya said:**
> applications -> accessories -> terminal
From there you should run ```
sudo dpkg --configure -a
```

Ah yes, correct. sudo is required. Thanks!

---

### Post by JEStone on 2008-05-03
Thanks for the help.  the fix worked beautifully. Sorry about not replying sooner, a few moments after posting this message my computer started to shut down every two minutes, which would most likely explain why I was getting this error. Power supply issue. - everything is working great now.

thanks again.

---

