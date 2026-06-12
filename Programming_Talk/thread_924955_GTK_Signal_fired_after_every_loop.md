---
title: "GTK: Signal fired after every loop"
date: 2008-09-20
forum: Programming Talk
---

### Post by EndOn9 on 2008-09-20
Hi guys :)

Looking at how to go about writing a game engine using GTK and one of the first things that has me stuck is how to go about calling a function to handle the game cycle.

Having had some Windows programming background I've been used to setting up the message handling loop by myself but as gtk connects functions to signals prior to entering the event loop I assume there must be a signal that is emitted to mark every iteration? If there is I haven't found one.

Could someone enlighten me of the existence of such a signal? Or am I missing a trick here?

---

### Post by EndOn9 on 2008-09-21
*Bump*

No-one know?

---

### Post by doorman on 2008-09-21
Maybe the guys at [GtkForums]("http://www.gtkforums.com/") might help you...

---

### Post by EndOn9 on 2008-09-21
Ah, good thinking!

Thanks :)

---

### Post by Vadi on 2008-09-21
Install [devhelp]("apt:devhelp") and the [gtk docs]("apt:libgtk2.0-doc") for it, it's the best thing ever.

The 'Main loop and Events' section has some related functions.

---

