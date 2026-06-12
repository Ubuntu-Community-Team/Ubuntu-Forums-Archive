---
title: "Functions in C"
date: 2009-05-25
forum: Programming Talk
---

### Post by MechWarrior001 on 2009-05-25
I think I'm starting to understand Functions in C a little better, but Terminal gives me this:
```
functions.c: In function ‘main’:
functions.c:11: warning: incompatible implicit declaration of built-in function ‘exit’
functions.c: At top level:
functions.c:14: warning: conflicting types for ‘add_two_numbers’
functions.c:8: warning: previous implicit declaration of ‘add_two_numbers’ was here
functions.c: In function ‘add_two_numbers’:
functions.c:19: warning: incompatible implicit declaration of built-in function ‘printf’

```when I try to compile this:
```

int main()
{
  int var1, var2;

  var1 = 2560;
  var2 = 1600;
  
  add_two_numbers (var1, var2);
  add_two_numbers (1280, 1024);

  exit(0);
}

void add_two_numbers (int a, int b)               /* Add a and b */
{
  int c;

  c = a + b;
  printf ("%d\n", c);
}

```

And how do I get it to give me a pop-up window displaying the integers instead of having to run it in terminal to get any feedback?

Also, how do I get it to name itself something other than "a.out"?

---

### Post by OutOfReach on 2009-05-25
Well first of all, to correct those errors you need to include this at the top of your file:
```

#include <stdio.h>
#include <stdlib.h>
void add_two_numbers(int a, int b);

```
The first two lines include the files with the functions printf() and exit() (they're called include files)
the last line is what is called a prototype which basically lets the compiler know that you included that function and it is call-able from anywhere in the file.

GUI's (the pop-up window) are a little harder to do, I suggest just sticking to command line right now.

What command did you compile your program with? You can assign the name like this:
```

gcc -o OUTPUT_FILENAME_YOU_WANT SOURCE_FILE_NAME.c

```

(Please excuse me, I'm not a very good teacher)

---

### Post by MechWarrior001 on 2009-05-25
Thanks. Also, do you know any better tutorials than this: [http://crasseux.com/books/ctutorial/index.html#Top](http://crasseux.com/books/ctutorial/index.html#Top)? It seems pretty bland, and I don't entirely understand what its saying.

And what else would I need besides functions to make a simple guess-the-number game in C?

---

### Post by soltanis on 2009-05-25
You'd need to accept user input. This is commonly done with the function [scanf]("http://linux.die.net/man/3/scanf"), although, if you don't quite understand pointers yet, this might not be the optimal choice.

To give you a quick overview, scanf does input formatting the same way printf does output formatting:

```

printf("%d\n", integer); /* I want to print integer as decimal digits */
scanf("%d", &integer); /* note the & before integer, very important */
printf("%d\n", integer); /* now it prints whatever number you typed in */

```

If you ran this code snippet (see end of post for full code example), you'd find that it prints the integer, then waits for your input on a blank line. Type in a number (in decimal format), and it will read that number into the integer variable. The next line of code prints that number back to you.

There are other functions you can use to get input as well, such as fgets, but if you haven't read about file I/O yet, you won't understand how to use them.

Bottom, unfortunate line is, things in C are not always what they seem. Keep on it though, you'll eventually get it.

```

#include <stdio.h>

int main()
{
        int integer;

        integer = 12;

        printf("%d\n", integer); /* prints 12 and newline */

        scanf("%d", &integer);
        /* the second argument is, as you'll discover later,
         * a pointer to the variable integer, which allows scanf
         * to modify the value of that variable so that your
         * function can "see" it. */

        printf("%d\n", integer); /* prints whatever integer you entered */
        return 0;
}

```

---

### Post by MechWarrior001 on 2009-05-25
Alright, how would I make it randomly select a number between 1-100 and add, subtract, multiply or divide it by whatever the user inputs?

---

### Post by soltanis on 2009-05-25
Use the rand() and srand() functions in stdlib.h.

[man 3 rand]("http://linux.die.net/man/3/rand")

---

