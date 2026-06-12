---
title: "[Py] Rewritable display buffer type thing?"
date: 2008-08-16
forum: Programming Talk
---

### Post by linkmaster03 on 2008-08-16
I don't really know what to call it, but I'm wondering if there is a way in Python to create a sort of rewritable display buffer, where normally you'd have to reprint the whole thing on all these new lines according to the terminal height. Also it would flicker. If you still don't understand what I mean, something like an ASCII movie (blinkenlights starwars telnet kinda) or an ASCII RPG.

But yeah, is there any way to do this in Python? Maybe even resizing the terminal, and writing to it by line number and column.

---

### Post by days_of_ruin on 2008-08-16
Are you using the ncurses module?

---

### Post by linkmaster03 on 2008-08-16
Uhh... I'm not using any module. I asked a question. Can ncurses do this?

---

### Post by linkmaster03 on 2008-08-18
Eh... if the ncurses module can do this, is there any good Python documentation for it?

---

### Post by jinksys on 2008-08-18
> **linkmaster03 said:**
> Eh... if the ncurses module can do this, is there any good Python documentation for it?

:neutral: 
First hit on google. GIYF.
[http://www.amk.ca/python/howto/curses/](http://www.amk.ca/python/howto/curses/)

---

### Post by linkmaster03 on 2008-08-18
Thanks. I was barely even getting ncurses documentation, Google seems to show very different results for different people and their SafeSearch settings. -.-

---

### Post by jinksys on 2008-08-18
> **linkmaster03 said:**
> Thanks. I was barely even getting ncurses documentation, Google seems to show very different results for different people and their SafeSearch settings. -.-

I searched for **python ncurses**.

---

### Post by nvteighen on 2008-08-18
ncurses seems to be what you want. Install it using:

```

sudo apt-get install libncurses5-dev

```

The "problem" is that ncurses has some weird way to do things. It relies a lot in "switch" functions that change the screen's attributes, instead of directly accessing those attributes. Personally, I don't like how it works, but I don't know of any alternative either.

---

