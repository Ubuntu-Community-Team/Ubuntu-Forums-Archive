---
title: "Stuck key, but which is it?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by brallan on 2008-06-27
I have a laptop with a stuck key, most likely one of the F1-12 keys or something like that. 

I know the laptop has a key which is stuck, because if i try and boot from the CDROM with no CDROM in, instead of asking me to press any key to retry, it just keeps spitting out the dialogue endlessly.

otherwise it works fine, I was able to install Hardy, except that it often acts funny, like firefox (just the active window) pauses and goes dim, then recovers after 5-6 seconds and remembers everything i was typing while it was dimmed.

is there any way to find out what key is stuck and then how to get this key turned off? i looked at the bios level and couldnt find anything.

---

### Post by mjwhitfield on 2008-06-27
Pull them all off and then replace them 1 by 1.

Be gentle :)

---

### Post by brallan on 2008-06-28
I thought of that, and i sprayed canned air under every key. If its a shortcircuit, i suppose I won't see anything anyway.  there must be some kind of app that reports keystrokes in their machine code format like alt0123 so one can know what each key is.

---

### Post by waldir on 2010-06-30
> **brallan said:**
> there must be some kind of app that reports keystrokes in their machine code format like alt0123 so one can know what each key is.

type "xev" (X events) in a terminal, it opens a window and dumps any keyboard or mouse events (or others) to the terminal, and you can see the key codes there. Since it can output quite a bit of text, you might want to redirect its output to a file, with something like
```
xev > eventsdump.txt
```

---

### Post by matt-fender on 2010-06-30
on screen keyboard? find one that highlights keys pressed?

---

### Post by overdrank on 2010-06-30
> **waldir said:**
> type "xev" (X events) in a terminal, it opens a window and dumps any keyboard or mouse events (or others) to the terminal, and you can see the key codes there. Since it can output quite a bit of text, you might want to redirect its output to a file, with something like
```
xev > eventsdump.txt
```

The date of the thread. June 28th, 2008
Thread closed

---

