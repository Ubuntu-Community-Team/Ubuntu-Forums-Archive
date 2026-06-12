---
title: "adding user session to the panel"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by jacklsw2008 on 2008-05-19
initially installed ubuntu has 2 panels, one on top and another at the bottom. previously i can see the user name is in the top panel. but somehow when i log in this session, the user name is not there anymore. how do i restore this?

---

### Post by TeoBigusGeekus on 2008-05-19
Right click the panel-> Add to panel -> User Switcher

---

### Post by N.N. on 2008-05-19
Right-click on the top panel and select "Add to panel". Choose the applet called "user switcher" or something along those lines (freely translated from Danish, sorry) and click "Add".

---

### Post by jacklsw2008 on 2008-05-19
that's the problem. i can't find the user switcher in the list. must i manually add it from custom application ?

---

### Post by N.N. on 2008-05-19
> **jacklsw2008 said:**
> that's the problem. i can't find the user switcher in the list. must i manually add it from custom application ?

In that case, try simply reinstalling the fast-user-switch-applet. You can either do this from the Synaptic package manager or by using a package manager from the terminal, e.g.: ```
sudo aptitude install fast-user-switch-applet
```

---

### Post by jacklsw2008 on 2008-05-19
thanks. problem solved now. :)

---

### Post by N.N. on 2008-05-19
You're welcome. :)

---

