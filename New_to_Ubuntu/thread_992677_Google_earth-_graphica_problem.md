---
title: "Google earth- graphica problem"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by suffer1989 on 2008-11-25
Im running Intrepid, and ive got a sufficent system [2Gh C2D/3GB Ram/ 128 MB shared intel GFX], but google earth has some weird graphical bug :

[[IMG]http://img92.imageshack.us/img92/797/screenshotkl0.png[/IMG]](http://imageshack.us)

Is it a driver problem ? 
Ive got an intel X3100 GFX chip [on a laptop]

---

### Post by suffer1989 on 2008-11-25
Oh, and open windows "hide" behind the google earth viewing area..

---

### Post by ddiger on 2008-11-25
I'm having a similar problem. At least you get a globe of some sorts to come up. All I get is a screen full of stars. I was beginning to think it was my ATI x1600. Also notice how the text looks funny, not clear & crisp.

-Can anybody think of anything we can try?

---

### Post by suffer1989 on 2008-11-26
Bump ?

---

### Post by Doug77 on 2008-11-27
I have the exact same problem.  Runing Intrepid 8.10 x64 on a Dell Inspiron laptop.  Any help would be appreciated!

---

### Post by mjwhitfield on 2008-11-27
Same problem with an Intel 950 card.  I think it's compiz that's causing the issues.

---

### Post by tibellus on 2008-11-27
You could try disabling Compiz Fusion, although it might seem some sort of videocard driver related problem.

---

### Post by Doug77 on 2008-12-01
Under "system -> preferences -> appearance", I set visual effects to "none" - I guess that is disabling Compiz Fusion?  Is that what people mean by that?  Anyway, it works, and now Google Earth works!

---

### Post by tibellus on 2008-12-02
> Under "system -> preferences -> appearance", I set visual effects to "none" - I guess that is disabling Compiz Fusion? Is that what people mean by that? Anyway, it works, and now Google Earth works!

Yes, that's the one. So it was a Compiz Fusion problem, then. :) Glad it works now.

---

### Post by Doug77 on 2008-12-03
Thanks for the help!  

One more - even though it works now, it's not perfect.  I can't read my elevation numbers and other things at the bottom of the screen, and a lot of the words that are printed on the map only partially show up.  Is that the same for everyone?

---

### Post by tjwoosta on 2008-12-03
this is a well known issue with opengl apps and compiz fusion

it happens to not only google earth but almost any applications that use opengl (mostly games)

a simply and quick solution is to temporarily disable compiz while using the application

press alt-f2 and run theese commands (**DO NOT USE THE TERMINAL FOR THIS**)

```
metacity --replace
```  (this will replace compiz with the standard metacity desktop)

now run your app

after your done you can reenable compiz like this  (again **don't** use the terminal)

```
compiz --replace
```




also an even easier solution for switching compiz on and off is to use compiz-fusion-icon

---

