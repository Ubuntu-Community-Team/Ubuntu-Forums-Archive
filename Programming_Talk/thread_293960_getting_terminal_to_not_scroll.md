---
title: "getting terminal to not scroll"
date: 2006-11-05
forum: Programming Talk
---

### Post by oldmanstan on 2006-11-05
ok, i know i've seen this question posted before but i've searched and couldn't find it, maybe i'm slow. how can you output text in the terminal but have the whole thing not scroll up, basically i just want to update text that was previously output.  for instance, to make a progress bar or something (just an example).

thanks

---

### Post by bukwirm on 2006-11-05
You could look into ncurses.

---

### Post by oldmanstan on 2006-11-05
yeah, actually i was sorta of hoping there was a simpler way, ncurses is a little heavy for what i'm doing, i may look into that though if there is no other option

---

### Post by junglepeanut on 2006-11-06
Would it be to simple to have it output a simple "#" or "<" "=" "=" .... which fills up to ">" after regular intervals on the same line up to some predetermined amount?

Also what language are you working in? ie, I am sure you could right something simple that did the  "/" "|" "\" "--" "/" "|" ... all in the same place like during 30th boot up.

Just ideas no real code here.

---

### Post by oldmanstan on 2006-11-06
thanks for the ideas, as for the progress bar that'll work, i would still like to be able to update some lines of text and such things though, i'm using CLI php

---

