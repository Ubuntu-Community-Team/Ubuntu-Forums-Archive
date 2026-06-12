---
title: "Scheduled Function"
date: 2010-03-05
forum: Programming Talk
---

### Post by rockom on 2010-03-05
Hi,

I've got a function I want to call every day at midnight.  I intend to use a time structure (struct tm) and compare the hours and minutes to that of midnight (00:00).  Simple enough I think.  However, I was curious if there is a more elegant approach.  Possibly a cron library or some other set of functions/libraries to schedule events.  For now, I'm only doing this once but if I were scheduling multiple events all at different times, I'd like to know if a better option is available.

using C

Thanks,
-Rocko

---

### Post by Lux Perpetua on 2010-03-05
Why can't you just use cron? You even mentioned it in your post.

---

### Post by rockom on 2010-03-06
> **Lux Perpetua said:**
> Why can't you just use cron? You even mentioned it in your post.

Because I'm not scheduling a program, I need to schedule an event within a program.


-Rocko

---

### Post by Lux Perpetua on 2010-03-06
Oh. Well, there are many solutions, then, and I don't claim to know the best one. If you're using a third-party package for events, then it probably has a ready-made solution for this, and I'd go with that. For example, with SDL, there's [SDL_AddTimer](http://www.libsdl.org/cgi/docwiki.cgi/SDL_AddTimer). Other suggestions: 

- Use two different threads. Have one of them sleep() until midnight, wake up, do what it needs, and go back to sleep, ad infinitum. The other thread does whatever your program normally does. 

- Use alarm() to send your program a SIGALRM at the desired time. Install a signal handler to do whatever you need and reset the alarm for 24 hours. This can be somewhat delicate, however, being asynchronous. (Consider what happens if your signal handler is called while your program is copying data into a buffer. If the signal handler looks at the buffer, then it will see a mixture of old & new data.)

If you want any more specific advice, you'll have to give more information. It's not clear at all what you're really trying to do, and specifically how the function you want to schedule is related to the rest of the program.

---

