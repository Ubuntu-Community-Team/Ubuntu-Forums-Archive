---
title: "Boxes in Curses"
date: 2013-03-06
forum: Programming Talk
---

### Post by tomzie on 2013-03-06
Hi, I have this screen. Somehow, I don't get the complete box as shown. Please see attached and advice. Thanks.

Here is my code below.


       WINDOW *sbox1, *sbox2, *sbox3;

        sbox1 = newwin(6, 10, 11, 13);
        box(sbox1, 0, 0);
        wrefresh(sbox1);
        sbox2 = newwin(6, 10, 11, 23);
        box(sbox2, 0, 0);
        wrefresh(sbox2);
        sbox3 = newwin(6, 10, 11, 33);
        box(sbox3, 0, 0);
        wrefresh(sbox3);
        mvprintw(12,1,"BLEND DESC:");
        mvprintw(13,1,"BLEND NO.:");
        mvprintw(14,1,"WEIGHT:");
        mvprintw(15,1,"STATUS:");
        mvprintw(12,14,"TESTBLND");
        mvprintw(13,14,"999999");
        mvprintw(14,14,"999");
        mvprintw(15,14,"Ready");
        mvprintw(12,24,"TESTBLND");
        mvprintw(13,24,"999999");
        mvprintw(14,24,"999");
        mvprintw(15,24,"Ready");
        mvprintw(12,34,"TESTBLND");
        mvprintw(13,34,"999999");
        mvprintw(14,34,"999");
        mvprintw(15,34,"Ready");
        delwin(sbox1);
        delwin(sbox2);
        delwin(sbox3);
        getch();
        endwin();

---

