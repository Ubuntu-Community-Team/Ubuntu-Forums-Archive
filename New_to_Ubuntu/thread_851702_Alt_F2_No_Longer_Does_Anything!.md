---
title: "Alt F2 No Longer Does Anything!"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by mrgnash on 2008-07-06
Exactly like the topic says... Pressing Alt + F2 in conjunction no longer brings up the run dialogue :( It's very annoying and I don't know how to go about fixing it. I would be very grateful if anyone could shed some light on this dilemma.

---

### Post by scragar on 2008-07-06
System>preferences>Keyboard Shortcuts

take a look for **Show the panel run application dialogue**

---

### Post by reeseslover531 on 2008-07-06
also if your keyboard is like a lot of keyboards make sure the f keys are enabled and not any other function that might be on the f keys.

---

### Post by mrgnash on 2008-07-06
Thanks guys :) It ended up being the F lock :-# How embarrassing. Anyway, thanks again.

---

### Post by ben2talk on 2009-10-20
I don't have f-lock

However, I did decide to enable some 'layout options' in the keyboard - third level chooser to 'any alt'.

This kind of messes up your ALT+F2 option

---

### Post by 1-L on 2011-03-23
The solution to the F-Lock problem on Microsoft keyboards is to add the following lines to the end of the file /etc/rc.local (You need to edit it as root):
setkeycodes bb 59 # Help  -> F1
setkeycodes 88 60 # Undo  -> F2
setkeycodes 87 61 # Redo  -> F3
setkeycodes be 62 # New   -> F4
setkeycodes bf 63 # Open  -> F5
setkeycodes c0 64 # Close -> F6
setkeycodes c1 65 # Reply -> F7
setkeycodes c2 66 # Fwd   -> F8
setkeycodes c3 67 # Send  -> F9
setkeycodes a3 68 # Spell -> F10
setkeycodes d7 69 # Save  -> F11
setkeycodes d8 70 # Print -> F12

---

