---
title: "How to make window pop-up after log-in"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by gkrules on 2008-05-05
when i had gutsy, i had it set up so that when i logged in, a window would pop-up and say "Welcome, [name]"
i thought it was really neat
i just upgraded to hardy heron and i forgot how to make the window pop-up

will anyone remind me how to do it?

---

### Post by pro003 on 2008-05-05
are you talking about log on window and the text that is appearing... you can change that in system > administration > logon window... if i understood you right :confused:

---

### Post by PinkFloyd102489 on 2008-05-05
You can use Zenity to do so.


In System > Preferences > Sessions, add a new entry and put:

```
export DISPLAY=:0 && zenity --info --text="Hello, $USER"
```


Obviously, you can replace the text part with whatever you want.

---

### Post by gkrules on 2008-05-05
> **pro003 said:**
> are you talking about log on window and the text that is appearing... you can change that in system > administration > logon window... if i understood you right :confused:

no i meant that after i logged in, the message would come up




and pinkfloyd 
i tried that but it didnt work...

1. i installed zenity
2. i added the entry
3. i rebooted and logged in
4. nothing happened


it worked when i typed it into the terminal somehow though...

---

### Post by pro003 on 2008-05-06
can u describe this window with this welcome message ? what is it like?

---

