---
title: "Python Idle"
date: 2010-08-05
forum: Programming Talk
---

### Post by Planetes on 2010-08-05
I am trying to learn python and i'm using Idle.

My question(s): When i activate idle through the terminal why does the terminal stick around but without the command prompt?

           Also how to i store my defined keywords so they don't get reset every time.

---

### Post by Bachstelze on 2010-08-05
> **Planetes said:**
> 
My question(s): When i activate idle through the terminal why does the terminal stick around but without the command prompt?


Because you can have only one process running in the foreground at a given time in a given terminal, so if idle is running in the foreground, your shell can't runin the foreground as well, hence no command prompt.  You can run idle in the background by appending an ampersand (&) to the command:

```
idle &
```

(The space is optional.) Don't know about your other question.

---

### Post by Planetes on 2010-08-05
Interesting, thanks for the response.

---

### Post by ricegf on 2010-08-06
> **Bachstelze said:**
> Because you can have only one process running in the foreground at a given time in a given terminal, so if idle is running in the foreground, your shell can't runin the foreground as well, hence no command prompt.  You can run idle in the background by appending an ampersand (&) to the command:

```
idle &
```

(The space is optional.) Don't know about your other question.

You can also switch Idle to background after it is running.  In the terminal, press Control-Z. The terminal will show a number in brackets (that's the number of background processes) and the word "Stopped".  Idle has paused, and won't respond to you any more.

You can switch Idle to run in the background now by typing "bg" (for background) in the terminal. The terminal will show the number in brackets again, followed by "idle &". Voila - Idle is active again.

(You could also put IDle back into the foreground by typing "fg" instead of "bg".)

If you find this fun (which would mean you're weird like me ;-), google "linux job control".  There's more.  Sooo much more. :-D

Have fun!

---

