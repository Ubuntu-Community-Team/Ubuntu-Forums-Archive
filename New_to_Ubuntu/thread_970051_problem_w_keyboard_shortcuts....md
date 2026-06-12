---
title: "problem w/ keyboard shortcuts..."
date: 2008-11-03
forum: New to Ubuntu
---

### Post by fignig on 2008-11-03
i need help w/ my keyboard shortcuts they dont seem to be working, like when i hit the right super button, it won't lock my screen...wats up w/ that?

and yes i have the right side, b/c it worked w/ 8.04 but after i upgraded to ibex, it stopped working, and no, no other keyboard shortcut is the same as it.

[[IMG]http://img98.imageshack.us/img98/5965/desktopmg6.th.gif[/IMG]](http://img98.imageshack.us/my.php?image=desktopmg6.gif)[[IMG]http://img98.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by nhasian on 2008-11-04
no other keyboard shorts are the same?  even in compiz?  theres a bunch of different keyboard shortcuts in compiz.  i'm not sure how to list them all...

---

### Post by fignig on 2008-11-05
> **nhasian said:**
> no other keyboard shorts are the same?  even in compiz?  theres a bunch of different keyboard shortcuts in compiz.  i'm not sure how to list them all...

can you read?

---

### Post by fignig on 2008-11-05
no one has had this problem?

---

### Post by fignig on 2008-11-06
wow, no one can help me?

---

### Post by fignig on 2008-11-06
this almost seems like a small problem, but it's been bothering me a lot. no one has any idea?

---

### Post by fignig on 2008-11-06
actually now that i try, none of the combination or single key buttons work to lock the screen...

---

### Post by nhasian on 2008-11-08
try these Hotkeys to Blank screen or lock workstation:

go to Systems/Preferences/Advanced Desktop Settings
in General Options, Commands tab in one of the command lines, enter "gnome-screensaver-command -l" to immediately start the screensaver and lock the workstation, or you can enter "sleep 1 && xset dpms force off" if you'd just like to make the monitor go to sleep.  Then go to key bindings and you can set whichever key combination you want to invoke the commands we entered.  I like to use Super-Z to make my monitor sleep and Super-L to lock the screen.  (Super is the windows key)

---

### Post by fignig on 2008-11-08
> **nhasian said:**
> try these Hotkeys to Blank screen or lock workstation:

go to Systems/Preferences/Advanced Desktop Settings
in General Options, Commands tab in one of the command lines, enter "gnome-screensaver-command -l" to immediately start the screensaver and lock the workstation, or you can enter "sleep 1 && xset dpms force off" if you'd just like to make the monitor go to sleep.  Then go to key bindings and you can set whichever key combination you want to invoke the commands we entered.  I like to use Super-Z to make my monitor sleep and Super-L to lock the screen.  (Super is the windows key)

 that actually worked, but i just want to hit the right super button, is there anyway to add that to the bindings? b/c when i hit the right one, it just says super, and doesn't specify.

---

### Post by nhasian on 2008-11-10
what is a "right super button?"  I've only ever seen one windows key to the left of the spacebar.

---

### Post by JKBurton on 2008-11-10
You post asking for help. Someone tries to help. You reply rudely. Now everyone's ignoring you.

Learn from it.

---

### Post by fignig on 2008-11-11
> **JKBurton said:**
> You post asking for help. Someone tries to help. You reply rudely. Now everyone's ignoring you.

Learn from it.

lol, how were any of my replies rude?

---

### Post by fignig on 2008-11-11
anyway, i kinda still need help. when i upgraded to 8.10 is when the problem really occurred, anyone have this problem as well? or am i really the only one. and i kinda still need some help w/ solving this problem. props to nhasian for the temp fix tho. still looking for the permanent fix tho.

---

### Post by fignig on 2008-11-11
> **nhasian said:**
> no other keyboard shorts are the same?  even in compiz?  theres a bunch of different keyboard shortcuts in compiz.  i'm not sure how to list them all...

i looked through every single one. every single box i have checked i looked through. and none of them have just the right windows key as the shortcut. compiz, and the keyboard shortcuts thing, in system > preference > keyboard shortcuts

---

