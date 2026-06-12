---
title: "Using Terminal - it won't accept my password - won't type text"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by winlinuser-gmail on 2013-10-21
This is driving me nuts - I can enter a command i.e sudo apt-get...  and it enters.  When it prompts me for the password nothing types on the screen - nothing at all!

PLEASE help before I set fire to the laptop.....

---

### Post by papibe on 2013-10-21
Hi winlinuser-gmail.

That is the standard behavior, i.e., nothing is shown while passwords being typed on the terminal.

Is the system not recognizing your password when you enter it?

Regards.

---

### Post by QIII on 2013-10-21
Hi!

That's perfectly normal.

Your password is not echoed in the terminal.  Just type it in carefully and press enter.

Cheers!

---

### Post by winlinuser-gmail on 2013-10-21
Oh no - DOH!!!

Many thanks Guys

---

### Post by squakie on 2013-10-21
As mentioned - it's standard.  In the "old" days some OS's used to do things like echo  astericks for each typed character of a password, etc..  This was usually eventually dropped so that nothing was echoed so that (1) nobody could see your password - you wouldn't want others knowing it and (2) not echoing any character, such as the asterick, so nobody would know the length of your password either.

It's been a lot of years, but I seem to remember Unix used to echo a dummy character at one time, but I know that was dropped.

It's all just a security thing.

---

