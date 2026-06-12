---
title: "Problem with scrolling and ncurses."
date: 2009-04-21
forum: Programming Talk
---

### Post by O|O on 2009-04-21
Hi, first of all I hope that I have opened the thread in the correct section.

Here is my problem:
I am trying to do some sort of text editor. As part of the system requirements, the user must be able to scroll up and down.

I did manage to achieve that using the following ncurses functions:
idlok (strdscr,true)
scrl(stdscr,-1) to scroll down and
scrollok(stdscr,true) to scroll up.
where stdscr is the default logical screen.

The problem is that this procedure basically removes any lines that where outside the scroll region, so instead of seeing the text I previously wrote, I see blank lines.

My question is; Is it possible to have some decent scrolling with ncurses? I am fairly new to the whole Linux and C deal, so I would appreciate if replies aren't too technical.

Thanks and Regards,
O|O

---

### Post by StuartN on 2009-04-21
You need to locate the cursor at the beginning of the just-exposed blank line and rewrite the missing text. The terminal has no memory of off-screen data, so although you can scroll the displayed data, it is lost when it scrolls off the screen.

---

### Post by O|O on 2009-04-21
Yeah, something like that did cross my mind, but this editor will be shared across processes(it will be a localized version of Gobby), so storing these lines can be problematic, at least the way I see it:
-Since the application is to be shared between users within different sessions, I don't know which user will be allowed to access what files within any particular session.
-Although I think that an IPC would solve the above problem, the problem with IPC's is that the amount is limited, and the size of the structure is OS dependent, so I will still be tied to a certain boundary.

I have came across some threads on other forums that said that the solution would be padding. I did manage to find the prototypes of these functions, the problem is that when I tried to build something, I got a segmentation fault. Anyone could link me to a decent tutorials or maybe give some tips?

Thanks,
O|O

---

### Post by O|O on 2009-04-23
Anyone? :confused:

---

### Post by O|O on 2009-04-24
I have solved this problem by using an IPC as a buffer.

---

