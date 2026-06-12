---
title: "metacity"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-06
How can I make it so that metacity doesn't start up at login?

---

### Post by Fixman on 2008-07-06
You want another window manager (like kWin or Compiz) or just want to use X without a window manager?

---

### Post by pikabuntu on 2008-07-06
> **Fixman said:**
> You want another window manager (like kWin or Compiz) or just want to use X without a window manager?

just x

---

### Post by Fixman on 2008-07-06
> **pikabuntu said:**
> just x

I think GNOME automatically loads metacity, so the only way is adding a new entry to the GNOME session menu saying
```
 killall metacity 
```

Note that this wont work if compiz loads at startup.

---

### Post by pikabuntu on 2008-07-06
> **Fixman said:**
> I think GNOME automatically loads metacity, so the only way is adding a new entry to the GNOME session menu saying
```
 killall metacity 
```

Note that this wont work if compiz loads at startup.

how do i get to the session menu?

---

### Post by Fixman on 2008-07-06
> **pikabuntu said:**
> how do i get to the session menu?

system->preferences->session.

BTW, you want no desktop effects? Then just go to system->preferences->appareance, visual effects tab, select none. You should leave X alone if you don't have a good reason to do it (and I can't think of a good reason).

---

### Post by pikabuntu on 2008-07-06
> **Fixman said:**
> system->preferences->session.

BTW, you want no desktop effects? Then just go to system->preferences->appareance, visual effects tab, select none. You should leave X alone if you don't have a good reason to do it (and I can't think of a good reason).

i dont think that that worked... i may have done somethiong wrong

---

### Post by pikabuntu on 2008-07-06
where exactly would i put it in the sessions menu?
in the box labled "command"?

---

### Post by pikabuntu on 2008-07-06
also im having a bit of trouble trying to get flash to work in firefox...

---

