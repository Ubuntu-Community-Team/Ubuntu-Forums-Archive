---
title: "[SOLVED] Gimp Help?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Dave B on 2008-08-23
I am coming here because i tried freenode/#Gimp and they were the most mean spirited pompous and unfriendly people i have ever tried to deal with .

"<dindinx> mortuis99: so you are being anoying for 20 minutes about script-fus, only because you are reading an outdated tutorial and only in fact want to save the current selection to a pattern?   "

I am new to trying GIMP and didnt know what i was talking aobut.

i am trying to do a watermark on some photographs a friend whats to post and i cant find the Script-fu.  Is there a good tutorial for this?

can someone please help me

thanks


Dave B

---

### Post by halitech on 2008-08-23
check here and see if this is what you want

[http://registry.gimp.org/node/6703](http://registry.gimp.org/node/6703)

---

### Post by Dave B on 2008-08-23
Yes thank you 

umm what fle fo i install it to

sorry for the dumb questions 

Dave B

---

### Post by halitech on 2008-08-23
welcome

open Nautilus, press Crtl - H (or go to View - Show Hidden files) and look for a folder called .gimp-2.4. If its not there create it (right click create folder). then in that folder, look for (or create ) a folder called scripts. That is where you want to put the file.

---

### Post by Dave B on 2008-08-23
i am at gimp>2.0>scripts and when i try and drag and drop or cut and paste to it says permission denied

Thanks 

Dave

---

### Post by halitech on 2008-08-23
are you in your home folder or another folder?

you want to follow my steps from earlier in your home folder

---

### Post by Dave B on 2008-08-23
> **halitech said:**
> welcome

open Nautilus, press Crtl - H (or go to View - Show Hidden files) and look for a folder called .gimp-2.4. If its not there create it (right click create folder). then in that folder, look for (or create ) a folder called scripts. That is where you want to put the file.

i am confused here where do i het Ctrl-H?  i am at the usr>share>gimp>2.0>scripts dir is this not the right place??

HELP im confused

THanks

Dave

---

### Post by Bucky Ball on 2008-08-23
Hold down Control key on your keyboard, then press the H key. Is that what you're after? Or as halitech says, go to the 'view' drop down menu and choose the option, 'show hidden files'. Welcome :)

---

### Post by Dave B on 2008-08-23
what bllooodddyyy directory?

---

### Post by Bucky Ball on 2008-08-23
[QUOTE=dave b] is this not the right place??
[/QUOTE]

Seems not. Open a terminal and type

```
gksudo nautilus

```
You will get the nautilus GUI, then follow previous instructions.

---

### Post by halitech on 2008-08-23
> **Dave B said:**
> i am confused here where do i het Ctrl-H?  i am at the usr>share>gimp>2.0>scripts dir is this not the right place??

HELP im confused

THanks

Dave

when you first open Nautilus, you will (should be) in your home folder. Press Ctrl - H on your keyboard. Then look for the .gimp-2.4(or .gimp-2.2 depending on what version you have) folder. That is where you want to look for the scripts folder or create it if needed.

---

### Post by Dave B on 2008-08-23
halitech 

thank you for being so patient with me

I have found it 

THANK YOU
:guitar::popcorn:

---

### Post by halitech on 2008-08-23
no problem, glad it worked for you :) 

if you have it solved, please mark the thread as solved so others will know

---

