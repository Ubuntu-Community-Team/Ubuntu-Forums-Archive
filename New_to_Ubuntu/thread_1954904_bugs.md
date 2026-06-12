---
title: "bugs?"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by milkweed701 on 2012-04-08
ok, yes im a "n00b" and all...

after the most recent update, things seem a lil buggy...

1. the bar up top shows zero "tabs"...
2. chrome does not have the "close/min/max" bubbles, not even on mouseover
3. apps can now cover the bar up top...
4. there is no longer a second workspace on startup (as there should be)

- there may be more, but these are the issues i deal with constantly, and unless there is some awesomeness im not aware of, i feel that these issues should be addressed ASAP. 

please help me

---

### Post by Bucky Ball on 2012-04-08
What release are you using? If 12.04 this is to be expected (beta, testing, not yet released, expect breakages on updates).

If not, this probably needs a bug report anyhow. ;)

---

### Post by milkweed701 on 2012-04-08
im using xfce 4.8 and ive just discovered that i am entirely unable to use my terminal.

the terminal window is frozen over "the bar up top" and part of chrome (its blocking my view as i type this now)

i noticed a few differences, and thought "maybe 'the new stuff' has affected these things" and restarted. that was no help.

---

### Post by Toz on 2012-04-09
Sounds like you're window manager may have crashed. Try Alt+F2, then running:
```
xfwm4 --replace
```

---

### Post by milkweed701 on 2012-04-09
awesome. based on appearance - everything seems to be working great - i even got my second workspace back!!

i now have two concerns:

1) (priorities) my apologies for my slow response, it took me a moment to get back to the laptop, then i had to play with the text field that came up after alt+F2

2) will i have to run that command every startup? how common of an issue is this?

thank you so much! i can move the windows again!!

---

### Post by milkweed701 on 2012-04-09
after a brief "hard knocks" session - it appears as though i will not have to run that command on startup.

everything now seems to be as it should be.

thanks again, 
matt

---

### Post by mörgæs on 2012-04-09
Good, then please mark the thread 'solved'.

---

