---
title: "ncurses - adding letters overwrites window border"
date: 2009-06-04
forum: Programming Talk
---

### Post by JordyD on 2009-06-04
I'm using ncurses to write a small text editor, but whenever I add lettering to the window, it overwrites the border. Is there a way to define a start to a window that's not on the border? Or a border outside the window?

I'm using C, if it matters.

Thanks,
Jordy

EDIT: I added the source if anybody wants to look at it.

---

### Post by dwhitney67 on 2009-06-04
I added this to your code; do the same and see if your requirements are met.

```

...
        /* Main logic */
        int y = 2;
        int x = 2;
        wmove(main_win, y, x);
        wrefresh(main_win);
        while((ch = getch()) != EOF) {
                switch(ch) {
                        ...

                        default:
                                getyx(main_win, y, x);
                                mvwaddch(main_win,y, x++, ch);
                                if (x == width - 2) {x=2; y++;}
                                wrefresh(main_win);
                                break;
                }
                wmove(main_win, y, x);
        }

```

---

### Post by JordyD on 2009-06-04
> **dwhitney67 said:**
> I added this to your code; do the same and see if your requirements are met.

```

...
        /* Main logic */
        int y = 2;
        int x = 2;
        wmove(main_win, y, x);
        wrefresh(main_win);
        while((ch = getch()) != EOF) {
                switch(ch) {
                        ...

                        default:
                                getyx(main_win, y, x);
                                mvwaddch(main_win,y, x++, ch);
                                if (x == width - 2) {x=2; y++;}
                                wrefresh(main_win);
                                break;
                }
                wmove(main_win, y, x);
        }

```

Thanks. That's exactly what I needed. :D

---

