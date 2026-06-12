---
title: "Grab keystrokes in c++"
date: 2012-05-21
forum: Programming Talk
---

### Post by Harry.k on 2012-05-21
I want to grab a single keypress, like getch in conio.h. I cant use ncurses since i use cout. Is there any other simple way?

---

### Post by Bachstelze on 2012-05-21
You have to switch stdin to unbuffered. I don't remember how to do that from the top of my head, use Google.

---

### Post by dwhitney67 on 2012-05-22
> **Bachstelze said:**
> You have to switch stdin to unbuffered. 

+1.

Here's an example, which I must admit, is a cross between C and C++:
```

#include <iostream>
#include <string>
#include <cstdio>
#include <cstring>
#include <termios.h>
#include <unistd.h>

#ifdef TRUE
#undef TRUE
#endif
#ifdef FALSE
#undef FALSE
#endif

#define TRUE  1
#define FALSE 0

/*
 *  @fn non_blocking_input(int fileno, int enable)
 *  @brief For enable or disabling non-blocking input on the specified stream.
 *  @param fileno - file number of stream to alter
 *  @param enable - set to TRUE or FALSE
 */
int non_blocking_input(int fileno, int enable)
{
    static struct termios old;

    if (enable)
    {
        struct termios tmp;

        if (tcgetattr(fileno, &old))
        {   
            return -1;
        }

        memcpy(&tmp, &old, sizeof(old));

        tmp.c_lflag &= ~ICANON & ~ECHO;

        if (tcsetattr(fileno, TCSANOW, (const struct termios*) &tmp))
        {
            return -1;
        }
    }
    else
    {
        tcsetattr(fileno, TCSANOW, (const struct termios*) &old);
    }

    return 0;
}

int main()
{
    std::string input = "";

    non_blocking_input(STDIN_FILENO, TRUE);

    std::cout << "Enter a sentence ending with a .:" << std::endl;

    int ch = -1;

    while ((ch = getchar()) != -1 && ch != '.')
    {
        putchar(ch);
        input += ch;
    }
    puts(".");
    input += '.';

    non_blocking_input(STDIN_FILENO, FALSE);

    std::cout << "You entered: " << input << std::endl;
}


```

---

### Post by Harry.k on 2012-05-22
Yay! It works. Thanks a lot. I found this helpfull too : [http://www.dreamincode.net/code/snippet5395.htm](http://www.dreamincode.net/code/snippet5395.htm) . I'll mark this as solved.

---

