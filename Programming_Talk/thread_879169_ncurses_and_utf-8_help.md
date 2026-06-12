---
title: "ncurses and utf-8 help"
date: 2008-08-03
forum: Programming Talk
---

### Post by Aundy on 2008-08-03
I have been trying, unsuccessfully, to get ncurses to display Unicode characters.

The following sample python program prints out gibberish.

```

import curses
stdscr = curses.initscr()
stdscr.addstr(u'\u2019'.encode('utf_8'))
stdscr.getch()
curses.endwin()

```

I know that my terminal has utf-8 support because this python program prints out the correct character (twice)

```

a = u'\u2019'
b = a.encode('utf-8')
print a  #print unicode string
print b  #print string

```

After searching online it seems as if the python curses wrapper does not support unicode (could someone confirm this).  So I decided to use libncursesw, which I think in supposed to have unicode support.
So, i did 
sudo apt-get install libncursesw5-dev

and then wrote this sample program

```

#include <ncurses.h>
int main(int argc, char *argv[])
{
  initscr();
  curs_set(0); //remove cursor
  addwstr(L"\u2019"); //Print out the unicode character
  refresh(); //update screen
  getch();  //wait for input
  endwin();
  return 0;
}

```

When I run this nothing is displayed on the screen, and if i use addstr("\u2019") then gibberish is displayed.

If someone could write a small sample program that prints out some unicode character and post it here that would be exactaly what I am looking for.  I don't care if this program uses c++, python, ncurses, or s-lang.

---

### Post by Aundy on 2008-08-03
I finially figure out how to do this, I simply needed to set the locale.  Here is the modified c code.
```

#include <ncursesw/ncurses.h>
#include <locale.h>
int main(int argc, char *argv[])
{
  setlocale(LC_ALL,"");
  initscr();
  curs_set(0); //remove cursor
  addstr("\u2019"); //Print out the unicode character
  refresh(); //update screen
  getch();  //wait for input
  endwin();
  return 0;
} 

```


and here is the modified python code

```

import curses
import locale
locale.setlocale(locale.LC_ALL,"")
stdscr = curses.initscr()
stdscr.addstr(u'\u2019'.encode('utf_8'))
stdscr.getch()
curses.endwin()

```

---

