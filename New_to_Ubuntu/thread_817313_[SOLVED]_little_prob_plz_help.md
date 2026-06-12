---
title: "[SOLVED] little prob plz help"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by newpeee on 2008-06-03
i'm a new to Ubuntu and  i've just installed it 4 dayz ago..so if my question looks stupid pardon me ](*,)..any way i was trying the window decoration and i honestly don't know what i did but i can't see the window frame any more so if i want to minimize or maximizes the window i've got ot go to the panel :confused: where did it go??how can i get it back :P?? and oh btw i'm using Ubuntu 8.04 ;)

---

### Post by bbqsandwich on 2008-06-03
Try restarting your session with CTRL-ALT-Backspace. Log back in... are the window parts still missing?

---

### Post by wootah on 2008-06-03
> **newpeee said:**
> i'm a new to Ubuntu and  i've just installed it 4 dayz ago..so if my question looks stupid pardon me ](*,)..any way i was trying the window decoration and i honestly don't know what i did but i can't see the window frame any more so if i want to minimize or maximizes the window i've got ot go to the panel :confused: where did it go??how can i get it back :P?? and oh btw i'm using Ubuntu 8.04 ;)

Ahh, definitely not a stupid question! :) You lost your window manager! To fix, open up a console (Applications -> Accessories -> Terminal) and type:
```
metacity --replace &
```If you had desktop effects enabled (and working properly) then you would use:
```
emerald --replace &
```After you do that, open the run menu (ALT + F2) then close the terminal. You should loose the window decorations (title bar, sizing bars, etc), BUT the run menu should still be open. Run the command that you used above to restore the decorations. After this, you may want to save your session to make sure that it doesn't happen again on reboot. System -> Preferences -> Session. Under one of the tabs is a button that says (to the effect of) "Save my Session".

Let us know if that helps :)

---

### Post by newpeee on 2008-06-03
OMG thanx alot guyz
wootah it worked finally i really don't know how to thank u man ;)

---

### Post by wootah on 2008-06-03
> **newpeee said:**
> OMG thanx alot guyz
wootah it worked finally i really don't know how to thank u man ;)

Click the star icon on my post :)

I'm glad it worked out for you! Let us know if there is anything else you need.

EDIT: Don't forget to mark this thread as solved too (At the top, Thread Tools -> Mark thread as Solved)

---

