---
title: "unicode on ncurses"
date: 2011-05-11
forum: Programming Talk
---

### Post by johnny3k on 2011-05-11
> #include <ncurses.h>
// compile and link: gcc <program file> -lncurses
int main()
{    
    initscr();            /* Start curses mode           */
    printw("&#1055;&#1088;&#1080;&#1074;&#1077;&#1090; &#1084;&#1080;&#1088;!");    /* Print Hello World          */
    refresh();            /* Print it on to the real screen */
    getch();            /* Wait for user input */
    endwin();            /* End curses mode          */
    return 0;
}

ubuntu@ubuntu-machine:~/projects/ncurses$ g++ hello.cpp -o hello -lncurses
ubuntu@ubuntu-machine:~/projects/ncurses$ ./hello && rm hello
&#65533;~_&#65533;~@&#1080;&#1074;&#1077;&#65533;~B &#1084;&#1080;&#65533;~@!

It possible to use Unicode strings on ncurses? :popcorn:

---

### Post by johnny3k on 2011-05-11
#include <linncursesw.h>
hello.cpp:2:26: fatal error: linncursesw5.h: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
compilation terminated.  // there is not this file or catalog

#include <ncursesw.h>
say  there is not this file or catalog

---

### Post by nvteighen on 2011-05-11
Look at this post: [http://ubuntuforums.org/showpost.php?p=5518749&postcount=2](http://ubuntuforums.org/showpost.php?p=5518749&postcount=2)

Be sure you've installed libncursesw5-dev.

---

### Post by johnny3k on 2011-05-11
i have good news. it's compile with success :D, but i cannot see unicode text :(


> 
// [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/helloworld.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/helloworld.html)
#include <locale.h>
#include <ncursesw/ncurses.h>
int main(int argc, char *argv[])
{
  setlocale(LC_ALL,"");
  initscr();
  curs_set(0); //remove cursor
  printw("&#1055;&#1088;&#1080;&#1074;&#1077;&#1090; &#1084;&#1080;&#1088; !!!");
  refresh(); //update screen
  getch();  //wait for input
  endwin();
  return 0;
}

ubuntu@ubuntu-machine:~/projects$ g++ code01.cpp -o code01 -lncurses
ubuntu@ubuntu-machine:~/projects$ ./code01
M-P~_M-Q~@M-PM-8M-PM-2M-PM-5M-Q~B M-PM-<M-PM-8M-Q~@ !!!

---

### Post by Arndt on 2011-05-11
> **johnny3k said:**
> i have good news. it's compile with success :D, but i cannot see unicode text :(

I haven't tried it, but can you link using -lncursesw instead?

---

### Post by johnny3k on 2011-05-11
Thanks! It's working!

---

