---
title: "printf prints strings twice inside a while loop"
date: 2009-12-06
forum: Programming Talk
---

### Post by utsavgupta on 2009-12-06
Hi,

I wrote a program in C to demonstrate a simple stack data structure.

Now this piece of cade:

...
ile(1)
    {
        printf("1. Push :: 2. Pop :: 3. Display :: 4. Exit: ");
        scanf("%c",&c);
        
        switch(c)
        {
            case '1':
                printf("Please enter an integer:");
                scanf("%d",&d);
                push(d);
                break;
            case '2':
                pop();
                break;
            case '3':
                disp();
                break;
            case '4':
                return;
        }
    }
...

prints "1. Push :: 2. Pop :: 3. Display :: 4. Exit: " twice each time it iterates the while loop.


Here is a sample output:

1. Push :: 2. Pop :: 3. Display :: 4. Exit: 1. Push :: 2. Pop :: 3. Display :: 4. Exit: 1
Please enter an integer:50
1. Push :: 2. Pop :: 3. Display :: 4. Exit: 1. Push :: 2. Pop :: 3. Display :: 4. Exit: 1


Now this is not a system specific problem. It's happening on my personal PC and also happening on the PCs in my college laboratory.

However this works fine on Torbo C and Borland C.

PS: I am new to the Linux and GCC environment.


Regards,


Utsav Gupta

---

### Post by Arndt on 2009-12-06
> **utsavgupta said:**
> 

...
prints "1. Push :: 2. Pop :: 3. Display :: 4. Exit: " twice each time it iterates the while loop.




I think the scanf sometime gives you things your code isn't prepared for. Add a line

printf("read char %d\n", c);

after the first scanf call, and I think you'll see.

Also, use 'code' tags to enclose code here - then it doesn't lose its indentation.

---

### Post by dwhitney67 on 2009-12-06
I agree; this is typical problem with users that neglect to realize that the input stream has not yet been cleared of all characters.

When accepting a single character, using an scanf() such as:
```

scanf("%c",&c);

```
the newline character is still in the input stream.  A similar issue occurs when prompting for integer data, as in:
```

scanf("%d",&d);

```
Thus before attempting to read another data character from the stream, remove the newline.

There are several workarounds to the OP's program:

1) he can scan for an integer, rather than a character after the menu prompt;

2) he can write (and use) a function that will 'bleed' the stdin stream until a newline character is found;

3) use fgets() to read data from stdin.

---

### Post by LKjell on 2009-12-06
Read this too. [http://ubuntuforums.org/showthread.php?t=1336461](http://ubuntuforums.org/showthread.php?t=1336461)
If you use fgets then you can use sscanf on the string you get.

---

