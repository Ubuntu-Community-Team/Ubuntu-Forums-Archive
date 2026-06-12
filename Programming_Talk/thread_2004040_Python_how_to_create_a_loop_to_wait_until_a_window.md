---
title: "Python how to create a loop to wait until a window is being closed"
date: 2012-06-15
forum: Programming Talk
---

### Post by ybas123 on 2012-06-15
Hi All,

I need help to write script in Python that enable my code to step through to the next line of code after an object window has been closed

currently I have something like :

while object.exists
time.sleep(1)

but it seems Python does not really like it.

Anyone could help me with this ? 

Cheers,
Yudo

---

### Post by David Andersson on 2012-06-15
> **ybas123 said:**
> 
I need help to write script in Python that enable my code to step through to the next line of code after an object window has been closed

currently I have something like :

while object.exists
time.sleep(1)

but it seems Python does not really like it.


What gui toolkit? (pygtk, tkinter, wxgtk, etc)

Or do you mean wait for another programs window?

Gui toolkits generally are event driven. It has a hidden main loop that waits for events from mouse, keyboard, window manager, timers, or files. When it happens, it runs functions that should complete fairly quickly, after it waits for the next event.

Your function will not complete quickly. If will block the rest of the python program until the object is closed. If the object normally is closed by another part of the python program (e.g. user clicking close button in a python controlled window) the program is in a dead-lock.

This is what I think. It may not be so in all gui toolkits, and there may be ways around it. However, I think it is better to let your program react to a window close event, than to block and wait.

---

### Post by jobix on 2012-06-17
Can you elaborate by what you mean by "Python does not really like it"?

Do you get an error message? Do you get a warning? Does it seem to ignore that line? ...

---

### Post by Bodsda on 2012-06-17
We're not going to be able to help much if you don't post your code.

---

