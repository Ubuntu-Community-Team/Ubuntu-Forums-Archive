---
title: "Anyone having problems with no window borders"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2011-08-26
As the title - no window decorations.

---

### Post by VinDSL on 2011-08-26
Not having any problem, at the moment, but...

I've had this problem, off-and-on, the whole time I've been running the alphas.

The workaround is simple enough:

```

unity-window-decorator --replace

```

That'll get you going again, without having to restart, et cetera.  ;)

---

### Post by Peter09 on 2011-08-26
Thanks

---

### Post by sgage on 2011-08-26
> **Peter09 said:**
> As the title - no window decorations.

Yes. Unity started running for me after updates, but no window decorations. Oh well, 2 steps forward, on step back...

---

### Post by Peter09 on 2011-08-26
Mmmm - no unity-window-decorator and do the below gives a surorising result

> peter@sammy-dev:~$ compiz-decorator --replace
Couldn't find a perfect decorator match; trying all decorators
Starting kde4-window-decorator
/usr/bin/kde4-window-decorator: Could not enable decorations on display ":0"
peter@sammy-dev:~$ 

---

### Post by sgage on 2011-08-26
> **Peter09 said:**
> Mmmm - no unity-window-decorator and do the below gives a surorising result

sudo apt-get install compiz-gnome

Then log out/log back in.

Window decorations should be there - worked for me!

---

