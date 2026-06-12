---
title: "How to determine if computer is idle (c++)"
date: 2010-05-30
forum: Programming Talk
---

### Post by Cz-David on 2010-05-30
Hi,
I am building an application which needs to know if the system is idle, as in the user did not move the mouse or touched the keyboard... plus if he is watching video. I have absolutely no idea how to get this information without making cpu heavy periodic checks...

I have tried looking up gnome-screensaver source, found something and did not understand the implementation.

---

### Post by nvteighen on 2010-05-30
> **Cz-David said:**
> Hi,
I am building an application which needs to know if the system is idle, as in the user did not move the mouse or touched the keyboard... plus if he is watching video. I have absolutely no idea how to get this information without making cpu heavy periodic checks...

I have tried looking up gnome-screensaver source, found something and did not understand the implementation.

Well, I'm not sure whether there's something like a 100% idle system when X is running, as it constantly checks for events to be signalled.

Maybe what you need is interfacing to X in order to know when mouse and keyboard are used. For video, I don't have any idea...

What are you trying to write?

---

### Post by Cz-David on 2010-05-30
I am writing a idle time tracker :)

Yes... but there has to be something simpler, I do not want to check every second if the mouse is moving...

---

### Post by SledgeHammer_999 on 2010-05-30
I searched a little bit through google and I found that everybody was using the XScreenSaver extension. The simplest approach I found(but not tested) is here->[http://coderrr.wordpress.com/2008/04/20/getting-idle-time-in-unix/](http://coderrr.wordpress.com/2008/04/20/getting-idle-time-in-unix/)

(also read the comments, they contain useful info)

---

### Post by lostinxlation on 2010-05-30
> **Cz-David said:**
> Hi,
I am building an application which needs to know if the system is idle, as in the user did not move the mouse or touched the keyboard...
Xlib has a few functions to detect the events.
 
EDIT: Oops, C++ ?  Then I don't know..I was talking about C.

---

### Post by uOpt on 2010-06-01
How do you know the user isn't sitting there watching a movie?

---

### Post by Cz-David on 2010-06-01
> **uOpt said:**
> How do you know the user isn't sitting there watching a movie?

"top" probably... Anything that is taking over 15% cpu is doing something, then I'll consider the computer not idling...

edit: as I am watching my system, I should give the user choice on the percentage... when my computer is idling, nothing goes over two percent at extreme cases

---

### Post by uOpt on 2010-06-01
> **Cz-David said:**
> "top" probably... Anything that is taking over 15% cpu is doing something, then I'll consider the computer not idling...

edit: as I am watching my system, I should give the user choice on the percentage... when my computer is idling, nothing goes over two percent at extreme cases

I see iconized Mozillas (Firefox and similar dirt) take up 30% CPU time and more all the time.

Also, what do you do if the guy is just running seti-at-home or reencoders the mp3 library for a week?

---

### Post by Cz-David on 2010-06-01
> **uOpt said:**
> I see iconized Mozillas (Firefox and similar dirt) take up 30% CPU time and more all the time.

Also, what do you do if the guy is just running seti-at-home or reencoders the mp3 library for a week?

That's why there will be percentage setting... anyway my firefox, though with blocked flash, does not take 30% (at 15 tabs about 4%)... 

As for seti and encodings, those will not be a problem, because... the computer is not exactly idle while doing those things.

---

### Post by uOpt on 2010-06-01
> **Cz-David said:**
> 
As for seti and encodings, those will not be a problem, because... the computer is not exactly idle while doing those things.

The way I read the OP his definition of idle is when nobody is actively using the console.

You just changed the definition of idle.

---

### Post by Cz-David on 2010-06-01
> **uOpt said:**
> The way I read the OP his definition of idle is when nobody is actively using the console.

You just changed the definition of idle.

Yes I did, it is a program development process... New ideas have a distressing way of getting into my head and forcing me to rewrite some already written procedures... 

It is going to track active programs, which it does now, but the idle function is a "new idea"... From my point the user will want to track the time of, lets say seti, even when he is not at his computer...

---

### Post by uOpt on 2010-06-01
> **Cz-David said:**
> Yes I did, it is a program development process... New ideas have a distressing way of getting into my head and forcing me to rewrite some already written procedures... 

It is going to track active programs, which it does now, but the idle function is a "new idea"... From my point the user will want to track the time of, lets say seti, even when he is not at his computer...

Then why not just use the existing data for CPU time used since boot?

---

