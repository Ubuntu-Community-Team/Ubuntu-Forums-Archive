---
title: "Simple C Question"
date: 2009-02-10
forum: Programming Talk
---

### Post by Tek-E on 2009-02-10
Im having an issue in a really simple C program.
I have been working with C lately just trying to learn the basics ( work from the ground up )
I wrote this really simple timer program under Ubuntu and when I compile it it runs fine, But when I compile it under windows I get error messages and it wont compile
Here is the code
```

#include <stdio.h>
int main()
{
    int x = 29;
    while ( x != 29 )
    {
        printf( "Number: %d\n", x );
        system( "sleep 1" );
        x--;
    }
    printf( "\nTime is Up!!!\n" );
}

```
Like I said it works fine running it on a *nix OS but when I try to compile it on windows I get error messages refering to "system"  I guess my question what would I need to do to get this script compile under windows?  is there another way of doing this?

Any help is greatly appreciated thank you!

---

### Post by cabalas on 2009-02-10
Just off the top of my head try including stdlib.h as well I'm not 100% sure that that will do the trick as I don't have a windows machine handy to test with.

---

### Post by eye208 on 2009-02-10
The system() function is declared in stdlib.h. You have to include that header too.

---

### Post by Tek-E on 2009-02-10
Thanks guys Ill try that and let you know what happens. It will be a while though.  Thanks very much!!

---

### Post by dwhitney67 on 2009-02-10
You may also want to change your while-loop into a do-while loop, or initialize x to something other than 29, or your program isn't going to do much.

---

### Post by cb951303 on 2009-02-10
also make sure that the command "sleep 1" is valid for windows too

---

### Post by Tek-E on 2009-02-10
> **dwhitney67 said:**
> You may also want to change your while-loop into a do-while loop, or initialize x to something other than 29, or your program isn't going to do much.
I know it wont do much. I was only messing around when I wrote this. It was only supposed to be a 30 second timer.

---

### Post by dwhitney67 on 2009-02-10
> **Tek-E said:**
> I know it wont do much. I was only messing around when I wrote this. It was only supposed to be a 30 second timer.
What I was attempting to say is that your program will never enter the while loop because you initialize x to 29, and your conditional clause in the while-loop will be false.

---

### Post by Tek-E on 2009-02-10
> **dwhitney67 said:**
> What I was attempting to say is that your program will never enter the while loop because you initialize x to 29, and your conditional clause in the while-loop will be false.
Oops Sorry about that.  Yeah thats A typo on my part. I meant for it to be a 0 instead of 29. Sorry bout that.

What I meant for it to be was
```

int x = 29;
while ( x != 0 )
{
     blah blah blah
}

```

Sorry if i came off as being a jerk in the way I replyed.

---

### Post by jpkotta on 2009-02-11
Unless you're trying to figure out the system() function, you should use the sleep() function instead.  In fact, nanosleep() is even better, but more complicated.  These are declared in unistd.h and time.h, respectively.  There's a chance it will work on Windows then (I'm not sure).  

As a rule of thumb, you shouldn't use == or != to get out of a loop, use <, <=, >, or >= instead.  It's best to have the most general possible test, because general tests make fewer assumptions, and assumptions are sources of bugs.

---

