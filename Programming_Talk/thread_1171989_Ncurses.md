---
title: "Ncurses"
date: 2009-05-27
forum: Programming Talk
---

### Post by nmccrina on 2009-05-27
I never really understood what this was until about half an hour ago! It turns out, that this is exactly what I've been looking for, since I'm a bit beyond the boring old terminal applications but I become hopelessly lost trying to understand full-fledged GUI programming (I'm using C). Ncurses seems to be a great intermediate step! I'm not sure why I'm posting, except to gloat about my newfound sense of purpose and maybe to offer a suggestion to all the other newbies posting about what they should learn next. :popcorn:

---

### Post by nvteighen on 2009-05-28
ncurses is an intermediate step, though it's a really weirdly designed library. Sadly, it has to comply to an outdated standard just for backwards compatibility and that makes it use some mechanisms no modern library should use (e.g. relying on hidden global variables).

But ncurses is a highly recommendable skill to learn. And not only in C, but also in Python and other languages that have bindings for it.

---

### Post by glotz on 2009-05-28
Some old ncurses apps are real masterpieces. Love it.

---

### Post by phrostbyte on 2009-05-28
ncurses is quite fun to program with and not a big step up from basic standard input and output. There is a function like mvprintw which is basically like printf except it has two additional parameters x,y cords.

---

