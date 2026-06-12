---
title: "I have add -lncurses ,but still can't link."
date: 2008-05-09
forum: Programming Talk
---

### Post by intijk on 2008-05-09
code:

#include <ncurses.h>
int main()
{
      initsrc();
      endwin();
      return 0;
}

then:

gcc  test.c -lncurses

but  it shows :

/tmp/ccOtOxfi.o: In function `main':
hellocurses.c:(.text+0x12): undefined reference to `initsrc'


I have install the libncurses5.dev

and I can make sure I have the libncurses.a now.

But still the problem exist.

Anyone could help me ?

Thank you!

---

### Post by samjh on 2008-05-09
The function is init**scr**();

:)

---

### Post by intijk on 2008-05-10
Thank you very much!:)

---

