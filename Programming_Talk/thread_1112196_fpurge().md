---
title: "fpurge()"
date: 2009-03-31
forum: Programming Talk
---

### Post by jrothwell97 on 2009-03-31
Right, I'm attempting to flush stdin in a C++ app (because otherwise the menu in my program behaves oddly - it uses getchar().)

On attempting to do an fpurge(stdin), I found that it wasn't declared. I searched the 'net, and found [this thread](http://ubuntuforums.org/showthread.php?t=1051954&highlight=fpurge()) which points out that fpurge() is non-standard C and that fflush() doesn't work on GNU/Linux.

All I'm looking for here is a simple answer: how do I flush/purge stdin when compiling on Ubuntu using g++?

---

### Post by dwhitney67 on 2009-03-31
The getchar() problem surfaces again... but why in a C++ app?

When reading in a single char, the last char you typed (a newline) is still in the buffer.  If you are programming in C++, then is buffer is within std::cin.  To clear out the buffer, use something similar to the following:
```

char ch;
std::cout << "Choice: ";
std::cin >> ch;
std::cin.ignore(128, '\n');   // ignore the next 128 characters

```

Or you can choose to use one of these choices:

1.  use ncurses library;
2.  create your own getc() function that manipulates the terminal settings so that the terminal does not block when reading input;
3.  read in a string in lieu of a single character

Here's an example for option 3:

```

#include <string>
#include <iostream>

int main()
{
  std::cout << "Menu:\n"
            << "\n\t1.  option one"
            << "\n\t2.  option two"
            << "\n\t3.  option three"
            << "\n\tq.  quit"
            << "\n\n"
            << "Enter a choice: ";

  std::string choice;

  getline(std::cin, choice);

  switch (choice[0])
  {
    case '1':   ...
    case '2':   ...
    ...
    case 'q':   ...
  }
}

```

---

### Post by nvteighen on 2009-03-31
> **dwhitney67 said:**
> The getchar() problem surfaces again... but why in a C++ app?


And again I feel ncurses is the best you can use, as it is designed to be a higher level solution to getchar() and such... Though, I don't know how well does ncurses play in C++.

---

### Post by dwhitney67 on 2009-03-31
> **nvteighen said:**
> And again I feel ncurses is the best you can use, as it is designed to be a higher level solution to getchar() and such... Though, I don't know how well does ncurses play in C++.
ncurses works well with C++... I have experience using it back in '97 to develop a simple spreadsheet application when I was taking a course at a community college.

Personally, though, if all that is needed is the ability to get one lousy character, and to discard the trailing newline char, I would not bother with ncurses.  It's too much baggage, and the std::cin approach is probably best (whether reading a single-char and ignoring the rest, or reading a string).

---

### Post by jrothwell97 on 2009-03-31
Thanks for the help.

std::cin.ignore worked excellently. Note to self: learn C++ properly instead of hotchpotching between it and pure C...

---

