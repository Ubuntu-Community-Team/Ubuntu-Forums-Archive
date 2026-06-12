---
title: "ncurses - refreshing windows"
date: 2008-12-21
forum: Programming Talk
---

### Post by BattlePanic on 2008-12-21
Quick question regarding ncurses.  Why does the following code not display anything onscreen?

```
#include <ncurses.h>

int main(void)
{
  WINDOW *a;

  initscr();

  a = newwin(0,0,0,0);

  waddstr(a,"This is window A.\n");
  wrefresh(a);
  getch();

  endwin();
  return 0;
}
```

If I add refresh(); after initscr(); it does display the text.  In other words, it seems I have to refresh the standard screen before I can draw any other window.  I'm not sure why this would be.  Any thoughts?

---

### Post by wmcbrine on 2008-12-22
Because your call to getch() does an implicit refresh of stdscr. Think of it as wgetch(stdscr), which is what it really is. And since the refresh of stdscr comes after the refresh of a, it overwrites it.

I'd suggest using wgetch(a) instead. You should input from the window where you want the input to appear.

---

### Post by BattlePanic on 2008-12-22
Very helpful.  Thank you, wmcbrine.

---

