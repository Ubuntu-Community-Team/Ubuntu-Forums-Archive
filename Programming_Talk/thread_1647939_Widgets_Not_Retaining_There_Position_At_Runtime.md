---
title: "Widgets Not Retaining There Position At Runtime"
date: 2010-12-18
forum: Programming Talk
---

### Post by J a c k on 2010-12-18
Hi, I'm relatively new to application development on Linux, I've been testing out Glade to create GUI frontends for my python apps, but a problem I've noticed is the top level window size set in design time doesn't seem to retain in run time. I've attached some images below. Also another question I have is that I've noticed that there is no snap to grid functionality on by default when using the fixed container, is there an option to enable this in glade 3.6.7?

---

### Post by nvteighen on 2010-12-18
Position or size? Position shouldn't change as the button is contained by your window, possibly set to fill the whole container as much as possible. But, probably you're referring to the widgets resizing when you resize your window?

I've never touched Glade... for some reason I always liked to do my UIs by hand... :P

---

### Post by J a c k on 2010-12-18
> **nvteighen said:**
> Position or size? 

Size. It's actually the window resizing itself during run time, deviating from the size set in design time, I've edited the OP now.

---

### Post by J a c k on 2010-12-20
Bump.

---

### Post by J a c k on 2010-12-28
Bump

---

### Post by nvteighen on 2010-12-29
Hm... it's weird why anyone else with more knowledge on Glade hasn't answered this yet.

Well, maybe the problem is that you're not setting the widgets' attributes right. For example, GTK+ containers can be homogeneous or not, meaning whether you allocate each children the same amount of space or not. Or windows size should be set explicitly or otherwise is recalculated.

All of this will be set and done during runtime, so it's possible that what you design on the GUI designer might not be what you see when running the program.

If you were coding this by hand I'd be way much more helpful. Hopefully someone more qualified takes a look on this thread.

---

