---
title: "conio.h?"
date: 2005-07-20
forum: Programming Talk
---

### Post by Luggy on 2005-07-20
I've been taugh c/c++ under microsoft visual studio 6.0 and I've noticed that whenever I'm compiling code with g++ it cannot find the conio.h header file.

Is this library just a windows thing? Is the header file hiding somewhere? Is there an equivilant I should be using?

I miss getch() :(

---

### Post by tomchuk on 2005-07-20
conio.h and getch() are windows specific. For a good explination read: [http://www.ale.org/archive/ale/ale-2000-07/msg00442.html](http://www.ale.org/archive/ale/ale-2000-07/msg00442.html)

---

### Post by vintem on 2005-07-22
Use <iostream> instead of <conio.h>.
Then you have cin to get input and cout to output.
For example this small menu:

int selection
cout << "1) new file" << endl;  // endl jumps to the nextline
cout << "2) open file" << endl;
cout << "3) exit" <<endl;
cout << "Enter your choice (1,2 or 3): ";
cin >> selection;

The user is invited to type his choice (1,2,3) which will be stored in selection, which can be processed in a switch-statement.

The double arrows show the direction: with cin ">>" points to the variable in which the input should be stored.
With cout "<<" points to the standard output device (your screen).
cin can also handle datatypes other than int.

Use <iostream> instead of <iostream.h> because the latter isn't in ANSI C++.
Once you get used to cin, you won't miss getch().

---

### Post by Hanj on 2005-07-22
> Once you get used to cin, you won't miss getch().getch returns the next character typed (without waiting for return), and afaik there is no way to do that with cin. Under linux, take a look at curses.h ('man ncurses'). It contains the functions you need.

---

### Post by glacierre on 2008-01-18
Quite an old thread but just was searching something related. There are some (lower level) ways of getting single key presses without curses:

```

#include <termios.h>
#include <unistd.h>

int getkey( ) {
struct termios oldt,
newt;
int ch;
tcgetattr( STDIN_FILENO, &oldt );
newt = oldt;
newt.c_lflag &= ~( ICANON | ECHO );
tcsetattr( STDIN_FILENO, TCSANOW, &newt );
ch = getchar();
tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
return ch;
}

```

---

### Post by hjum6316 on 2012-10-13
conio.h only works in windows compilers..

Try this command to clear screan...
I've tried it with visual studio and netbean etc...

By trial and error I've discovered it but can't put to word how it works..........

       printf("\033[H\033[J");

---

### Post by overdrank on 2012-10-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

