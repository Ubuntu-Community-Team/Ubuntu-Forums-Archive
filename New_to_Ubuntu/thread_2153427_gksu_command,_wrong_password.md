---
title: "gksu command, wrong password?"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by gigenieks on 2013-06-11
Hello!

```

gksu gedit /etc/grub.d/40_custom

```
When I enter password, it tells me it's wrong. Which is really weird because password is 100% correct. I use the same password I created installing Ubuntu, the password I use to log in.

Edit: Found solution.
> 
Run gksu-properties [Alt+F2] and make sure that the Authentication mode is set to sudo.


---

### Post by Mariane on 2013-06-11
Thank you for posting the solution, I've had the same problem :)

---

### Post by gigenieks on 2013-06-11
No problem. :rolleyes:

---

