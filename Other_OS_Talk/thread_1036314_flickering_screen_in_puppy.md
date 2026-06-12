---
title: "flickering screen in puppy?"
date: 2009-01-10
forum: Other OS Talk
---

### Post by Baffo on 2009-01-10
hello!
how can i fix my screen flickering in puppy linux?
i've got an nvidia tnt2 video card.

thanks in advance, please don't tell me to ask on their forums, because they can't help me.

---

### Post by oilchangeguy on 2009-01-10
> **Baffo said:**
> hello!
how can i fix my screen flickering in puppy linux?
i've got an nvidia tnt2 video card.

thanks in advance, please don't tell me to ask on their forums, because they can't help me.

please explain how, when you can't get help in a forum for that os. that you expect to get help in a forum for ubuntu.
have you even tried their forum?
[http://www.murga-linux.com/puppy/](http://www.murga-linux.com/puppy/)

---

### Post by trucker33377 on 2009-01-10
the puppy forum is good. and this is like apples and oranges.

---

### Post by Baffo on 2009-01-10
yes.
i guess there are more experienced people on these forums.

---

### Post by oilchangeguy on 2009-01-10
> **Baffo said:**
> yes.
i guess there are more experienced people on these forums.

experienced mainly with UBUNTU.

---

### Post by spcwingo on 2009-01-11
I had the same problem in Puppy.  Try adjusting the refresh rates.  To do that drop out of X and type:

```
xorgwizard
```

Select xorg, not vesa.  Select your res and color depth.  Then test X (remember to exit the test by pressing CTRL+ALT+BKSP).  When asked if finished select tweak and try different refresh rates.  Always remember to test before selecting done (if you accidentally select done prematurely just drop out of X again and rerun xorgwizard).  This will completely rewrite xorg.conf.  This worked for me...let me know if it does the same for you.;)

---

### Post by Baffo on 2009-01-12
i already ran xorgwizard and tweaked settings, but didn't improve much :\

maybe that's all because i've got a crappy nvidia tnt2 video card..

---

