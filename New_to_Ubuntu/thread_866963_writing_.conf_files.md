---
title: "writing .conf files"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by ja660k on 2008-07-22
hey guys...

i have a little problem.. i need to be able to write .conf files...
and the system doesnt let me, says i dont have permission 
i have no ieda how to write things as super user?


sudo vim ?
...lol

---

### Post by tech0007 on 2008-07-22
with gui, use

gksu gedit [.conffile]

No gui,

sudo nano [.donffile]

---

### Post by northern lights on 2008-07-22
Run

```
gksu gedit NameOfFile.conf
```

---

### Post by brian_p on 2008-07-22
> **ja660k said:**
> 

sudo vim ?
...lol

. . . . would be as good as anything.

---

### Post by ja660k on 2008-07-22
thanks guys... it worked gksu gedit worked good like thanks alot

---

### Post by muteXe on 2008-07-22
> **ja660k said:**
> 
sudo vim ?
...lol

That's what I would use.  Why is that funny? :(

---

