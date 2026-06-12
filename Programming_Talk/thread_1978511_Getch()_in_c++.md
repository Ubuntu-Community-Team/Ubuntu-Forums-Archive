---
title: "Getch() in c++"
date: 2012-05-11
forum: Programming Talk
---

### Post by Harry.k on 2012-05-11
Could someone help me with using getch or something similar in gcc? I know about ncurses, but i use cin and cout extensively, so ncurses screws up the output. I'm porting some code into linux, and i cant convert al l the couts and cins into cprintf. Any help appreciated

---

### Post by souravc83 on 2012-05-11
Do you mean porting from C++ to C?
you can use cin and cout perfectly fine in linux. 
Or are you looking for a replacement of the getch() function in conio.h?

If you want to get a character without any buffer, ncurses is the best way. Otherwise, there is a more ugly way of doing it by writing a function in C++. I had used the function once I think, but found it way worse that ncurses.

---

### Post by lisati on 2012-05-12
*Thread moved to **Programming Talk**.*

---

### Post by codemaniac on 2012-05-12
> **Harry.k said:**
> Could someone help me with using getch or something similar in gcc? I know about ncurses, but i use cin and cout extensively, so ncurses screws up the output. I'm porting some code into linux, and i cant convert al l the couts and cins into cprintf. Any help appreciated

You can consider writing up your custom getch() routine and include that in gcc .
[http://zobayer.blogspot.in/2010/12/getch-getche-in-gccg.html](http://zobayer.blogspot.in/2010/12/getch-getche-in-gccg.html)

---

