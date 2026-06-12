---
title: "Sorta like an automated on-screen keyboard"
date: 2008-07-18
forum: Programming Talk
---

### Post by dr.silly on 2008-07-18
Okay so I saw a demonstration of something very similar to [TextMate]("http://macromates.com/") except that it worked regardless of what program you were using.

My question is how would I go about designing something similar to this for ubuntu. I basically need to be able to see what the user types (regardless of focused program) and then alter what is typed.

Any pointers on how I could go about it?

---

### Post by dr.silly on 2008-07-19
ok so I have to use ```
XSelectInput(display, window, event_mask);
``` but I don't have any specific window what do i do?

---

### Post by jinksys on 2008-08-14
I'm at a loss as to what you are trying to accomplish.  Are you looking to write a keylogger, or are you writing an application that provides on-demand syntax highlighting?

---

### Post by loganwm on 2008-08-14
> **jinksys said:**
> I'm at a loss as to what you are trying to accomplish.  Are you looking to write a keylogger, or are you writing an application that provides on-demand syntax highlighting?

It appears that he is working on a program that inputs text macros into a selected field in a running program?

Correct me if I'm wrong.

---

### Post by Xealot on 2008-08-14
You can capture keyboard strokes with XLib,
The way I did it when I had to do that, was to subscribe to the focused windows events such as KeyPress using XSelectInput,

I also checked for the event FocusOut, which would indicate that the user swapped window, and when that happened, I subscribed for the same events as above, but for the new window

I guess there might be some smarter way of doing it, but I did it for fun and in a short period of time ;).

For examples of how to accomplish it, you can check out my wiki [here]("http://wiki.winsbydefault.com/w/Keyfucker#Source_2")

It should also be noted that not all windows allows "you" (the program) to subscribe to its KeyPress events, so its not guaranteed to work globally this way.

---

