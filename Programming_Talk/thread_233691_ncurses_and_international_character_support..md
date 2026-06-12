---
title: "ncurses and international character support."
date: 2006-08-10
forum: Programming Talk
---

### Post by red_Marvin on 2006-08-10
While trying to learn ncurses, I come across this tutorial: [http://www.linux.com/howtos/NCURSES-Programming-HOWTO/init.shtml#INITEX]("http://www.linux.com/howtos/NCURSES-Programming-HOWTO/init.shtml#INITEX")
which waits for the user to strike a key and then echoes it. But I soon found out that it doesn't support international
characters, such as the Swedish å,ä,ö. I then found out about ncursesw that supports wide characters but I haven't
succeeded in converting the example, and I haven't found any tutorials on how to use which wide char functions.
I tried to change ch=getch(); into get_wch(); but then the program return from that function. the man page for
get_wchr() indicates that the function takes a wint_t pointer as argument but doesn't explain it's purpose.

Could someone explain how I should implement wide character support?

---

