---
title: "How to take away bottom bar and customize top bar? 12.10 gnome classic"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by Dharman on 2013-03-15
I'm sporting Ubuntu 12.10 with gnome classic session

How do i take away the bottom bar in the desktop?
How do i customize the top bar?
I want to have my running programs shown in the top bar and i want to be able to add and REMOVE shortcut i put in the top bar.

Please share your wisdom!

---

### Post by ManamiVixen on 2013-03-15
In gnome classic, you push ctrl on the keyboard, and then right click on the panel to change it's settings.

---

### Post by Dharman on 2013-03-15
Hmm.. doesn't seem to work.

I'll add more info:

(First, i'm a beginner!)

I installed ubuntu 12.10 but didn't like Unity so i downloaded and installed gnome3 somehow, guided by some internet post.
Now my desktop look like this:

[ATTACH=CONFIG]240211[/ATTACH]

Neither top nor bottom bar react to ctrl-click or left-click or right-click...

---

### Post by Dharman on 2013-03-15
Could there be some Unity-stuff left behind that's blocking me?

---

### Post by stinkeye on 2013-03-15
In gnome classic...right click+Super+alt    (Super= Windows key)
In gnome classic(no effects)...right click+alt

...but your pic actually looks like gnome-shell or the Gnome session
which I am not familiar with.

What is your terminal output of...
```
echo $DESKTOP_SESSION 
```

---

### Post by Dharman on 2013-03-15
Thankyou so much Stinkeye, it worked with the right click+Super+alt!
Finally!!!

It says "gnome-classic" in the terminal

Cheers!

---

