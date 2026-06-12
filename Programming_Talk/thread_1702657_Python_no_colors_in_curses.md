---
title: "Python: no colors in curses"
date: 2011-03-08
forum: Programming Talk
---

### Post by mewski on 2011-03-08
Hi all,

I can't get curses to show colors in Python. Even though curses.has_colors() returns True, .start_color doesn't, and any kind of formatting for stdscr.addstr and the like doesn't work as well. Everything shows as black, except for A_STANDOUT, which shows as grey on grey.

I'm using xterm with KDE, but also tried aterm, to no avail. Also tried with pythons 2.6, 2.7, 3.1 -- no difference.

Ansi color codes do work, but I'd prefer to do it in a nicer way :/

Any help would be greatly appreciated, as it's been driving me nuts since yesterday :)

---

### Post by johnl on 2011-03-08
```

curses.start_color()

# color pair 1 = red text on white background
curses.init_pair(1, curses.COLOR_RED, curses.COLOR_WHITE)

stdscr.addstr( "Hello world", curses.color_pair(1) )
stdscr.refresh()


```

give that a shot.

---

### Post by mewski on 2011-03-09
Thaks Johnl, that works :) It seems I was confused about color pairs and how they relate to attributes.

---

