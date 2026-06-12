---
title: "VERY simple C++ cin.get question"
date: 2007-04-14
forum: Programming Talk
---

### Post by qpwoeiruty on 2007-04-14
I'm trying to get a single character from the keyboard and I can't figure out why I have to press enter first for cin.get to grab a character. I don't remember it working this way in Borland on Windows...

```
	do{
		cin.get(ch);
	} while(!isprint(ch));
```

---

### Post by samjh on 2007-04-14
I don't think there is any way to obtain a single character without entering whitespace (space, enter, tab, etc.) using standard C++.

get() and its sister functions require a delimiter (whitespace) or EOF to stop reading from input.

In C, you can use getchar(), but using C libraries in C++ is generally not recommended.

---

### Post by qpwoeiruty on 2007-04-14
Maybe I was using something Windows specific similar to get()...

For some reason, it seems somewhat harder making a simple console app using nothing but the standard libraries and all of the long annoying /e[ ANSI escape codes than it is to make a full blown GUI app with extra libraries...

---

### Post by samjh on 2007-04-15
Were you using Borland C++ Builder?  It was designed for rapid application development using C++ and Borland's VCL framework, so it's not surprising that you find making GUI apps easy.  I felt the same way when using Visual C++ with MFC to make GUI apps.

If all else fails, you can still use the C libraries within C++.

---

### Post by dsl on 2007-04-15
To disable line buffering you can use termios (man termios, with manpages-dev installed).
Example:
```

#include <termios.h>
termios before, after;
tcgetattr (STDIN_FILENO, &before);  // fill 'before' with current termios values
after = before;                     // make a copy to be modified
after.c_lflag &= (~ICANON);         // Disable canonical mode, including line buffering
after.c_lflag &= (~ECHO);           // Don't echo characters on the screen (optional)
tcsetattr (STDIN_FILENO, TCSANOW, &after); // Set the modified flags
/*
Here you can work without line buffering.
Use 'select' (man select) and 'read' to get the char if you need to monitor other sources of events (eg sockets, timeouts)
When you're done, reset the original state with:
*/
tcsetattr (STDIN_FILENO, TCSANOW, &before);
```

HTH

Daniele

---

### Post by bluewagon on 2007-04-15
at school we use.. getch() .. i think it is, you need to conio.h library

---

### Post by WW on 2007-04-15
dsl: Thanks, that's good to know.

Here's an example that uses dsl's code:
```

#include <termios.h>
#include <iostream>
#include <iomanip>

using namespace std;

int main()
    {
    termios before, after;
    tcgetattr (STDIN_FILENO, &before);  // fill 'before' with current termios values
    after = before;                     // make a copy to be modified
    after.c_lflag &= (~ICANON);         // Disable canonical mode, including line buffering
    after.c_lflag &= (~ECHO);           // Don't echo characters on the screen (optional)
    tcsetattr (STDIN_FILENO, TCSANOW, &after); // Set the modified flags
    char ch;
    cout << "Hit Escape to quit.\n";
    do
        {
        cin.get(ch);
        cout << "ch = " << setw(3) << (int) ch;
        if (isprint(ch))
            cout << " '" << ch << "'";
        cout << endl;
        }
    while((int) ch != 27);
    tcsetattr (STDIN_FILENO, TCSANOW, &before);
    return 0;
    }

```

bluewagon: [conio.h]("http://en.wikipedia.org/wiki/Conio.h") appears to be a Windows/DOS header.

---

### Post by qpwoeiruty on 2007-04-16
That must have been it. getch sounds familiar.

Termios is *nix specific though too, right?

I'm trying to make a simple console adventure game sort of like [Adventure](http://en.wikipedia.org/wiki/Colossal_Cave_Adventure) with basic textmode graphics.
I had wanted to hotkey the arrow keys to north,south,east, and west.

If termios is *nix specific, could I hotkey those keys to be both arrow and enter?
Something like: \e[224;72;224;72;13p

---

### Post by Ragazzo on 2007-04-16
Have you looked into **ncurses**?

---

