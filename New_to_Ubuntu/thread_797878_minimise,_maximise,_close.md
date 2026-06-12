---
title: "minimise, maximise, close"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by greenygrog on 2008-05-17
Hi all
I have a problem with my window. I have lost the min max close option completely, just not there. Started in Gutsy and is still there in hardy. On advice I have checked out gconf-editor', apps->metacity->general, then button_layout but apparently this is configured correctly 'menu:minimize,maximize,close'. Any kind person out there know what the chuff I've managed to do?

---

### Post by jimmy the saint on 2008-05-17
have you tried going into system > preferences > appearance and selecting a new theme?  Whenever my windows used act up selecting a new theme fixed it and then I would just go back to the one I was using before.

---

### Post by nowshining on 2008-05-17
u can change the layout of the buttons,

the names before the ":" will on the left side & the ones after it will be on the right.

U can also remove them all if u'd like.


example: if u don't want menu, u can try using:

```
:minimize,maximize,close
```

:)

---

### Post by Oldsoldier2003 on 2008-05-17
> **greenygrog said:**
> Hi all
I have a problem with my window. I have lost the min max close option completely, just not there. Started in Gutsy and is still there in hardy. On advice I have checked out gconf-editor', apps->metacity->general, then button_layout but apparently this is configured correctly 'menu:minimize,maximize,close'. Any kind person out there know what the chuff I've managed to do?

```
metacity --replace
```

---

### Post by greenygrog on 2008-05-20
> **Oldsoldier2003 said:**
> ```
metacity --replace
```

Thanks Oldsoldier. I did not understand your reply? Could you explain?

---

### Post by forestpixie on 2008-05-20
run it in a terminal - should start metacity as the window manager

---

### Post by nowshining on 2008-05-21
add an "&" for "&&" at the end not stop it when u close the terminal.

---

### Post by Living2007 on 2008-05-21
> **greenygrog said:**
> Hi all
I have a problem with my window. I have lost the min max close option completely, just not there. Started in Gutsy and is still there in hardy. On advice I have checked out gconf-editor', apps->metacity->general, then button_layout but apparently this is configured correctly 'menu:minimize,maximize,close'. Any kind person out there know what the chuff I've managed to do?
I've had a similar problem. When I changed the buttons to look like the traffic lites on OS X, It failed and I have to redo the trick, It worked.

All you need to do is, find the code and copy it.

---

### Post by greenygrog on 2008-05-27
Thanks to everyone for your help. All working fine now!!!

---

