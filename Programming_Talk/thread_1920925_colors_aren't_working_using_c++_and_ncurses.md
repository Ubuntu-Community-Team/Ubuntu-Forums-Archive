---
title: "colors aren't working using c++ and ncurses"
date: 2012-02-05
forum: Programming Talk
---

### Post by korgoth28 on 2012-02-05
In main I have:

  ```

  start_color();
  init_pair(1, COLOR_RED, COLOR_BLACK);
```then I call a function which has:

      ```

      attron(COLOR_PAIR(1));
      addch(theMap[x][y].getGraphic());
      attroff(COLOR_PAIR(1));
```It prints, but in the default color, no matter what I set the color pair  to. I'm using bash in xubuntu (fully updated), though it doesn't work in ksh or csh (in terminal or xterm)  either. All of the colors are correct in emacs (which uses curses,  right?). Any ideas?

---

