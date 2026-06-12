---
title: "Having issues with for loops in C"
date: 2005-12-19
forum: Programming Talk
---

### Post by Iandefor on 2005-12-19
I'm pretty new at programming, and I'm currently attempting to learn C.
In order to play with for loops, I wrote a program which is supposed to accept input of up to 10 characters (The idea is to have it stop inputting once the character array has been filled), enumerate how many characters there actually are, and then return the number of characters. Currently, there are two problems with it:

1. There is no limit to the amount of characters I can input.
2. No matter how many characters I enter, it consistently returns 1 as the
number of characters.


The program is pretty short and simple, so I'll just leave it here in the body of the message.

```
#include <stdio.h>

int main()
{
        char a[11];       /* The character array a[11] used to store user input */
        int b = 0, i;     /* b is used to act as a counter for the number of */
                          /* digits in the character array, whereas i is a */
                          /* counter variable for the for loops */

        for(i = 0; i <= 10; i++)
        {
                a[i] = getchar();
        }

        for(i = 0; a[i] != '\n'; i++);
        {
                b++;
        }

        printf("The string you entered above has %d characters in it.\n", b);

        return 0;
}

```

---

### Post by amohanty on 2005-12-19
The reason is [getchar]("http://www.cplusplus.com/ref/cstdio/getchar.html") will continue accepting input till you insert an EOF char ctrl-d. The reason it return 1 is because it keeps discarding the previous ones. See the link above to see an example.

AM

---

### Post by thumper on 2005-12-19
Just an aside, it is the terminal that is buffering the input not getchar.

There was a big thread on ::ioctl a while back on this.

---

### Post by Iandefor on 2005-12-19
I was a silly bugger in writing the above code... check line 15:

```
 printf("The string you entered above has %d characters in it.\n", b);
``` Note the semicolon.

> The reason is [getchar]("http://www.cplusplus.com/ref/cstdio/getchar.html") will continue accepting input till you insert an EOF char ctrl-d The problem isn't that I can't make it stop inputting; I can't make it stop inputting once it's hit the end of the character array without hitting return, which is, in itself, acceptable for now, since the idea
was to write a program to make sure I had the basic idea behind for loops down. However, I'm a bit puzzled as to why it won't stop inputting at the limit of the character array... the idea is that once i <= 10 becomes false, the loop terminates and the program moves on, so it should stop inputting at 10 characters.

Thumper: I'm extremely new at programming, so if you could expand a little more on what your post *means* I'd appreciate it :).

---

### Post by thumper on 2005-12-19
If you want the loop to terminate when the user hits return then you need to also check for return pressed in your first loop.

Here is your code with a few additions...
```
#include <stdio.h>

int main()
{
        char a[11];       /* The character array a[11] used to store user input */
        int b = 0, i;     /* b is used to act as a counter for the number of */
                          /* digits in the character array, whereas i is a */
                          /* counter variable for the for loops */
	a[10] = 0;
        for(i = 0; i < 10 ; i++)
        {
                a[i] = getchar();
		if (a[i] == '\n') break;
        }

        for(i = 0; a[i] != '\n' && i < 10; i++)
        {
                b++;
        }

        printf("The string you entered above has %d characters in it.\n", b);

        return 0;
}
```
Firstly I initialise the last character of your char buffer to be null.
Next the initial loop stops one before the end of the character array so you don't overwrite the null terminator.
To leave the first loop early, the check was added to break on a return.
Added a length check to the second loop to stop it walking off the end of the array.

You might want to look at memory setting functions like memset, or initialising memory with calloc.

The ioctl function is used to manipulate the underlying device parameters, in this case the terminal.  You really don't need to know about this yet.

---

### Post by Iandefor on 2005-12-19
Looks good. I wasn't aware of break; just makes it that much easier. Thanks!

Sorry if I'm being thick here, Thumper, but do define what a "buffer" is...
the way you used it implied to me that the term is interchangeable with "array".

---

### Post by amohanty on 2005-12-19
>  but do define what a "buffer" is...
A buffer would be any block of memory which can contain data. In this example it is an array but it can be any data structure.

HTH

---

### Post by Iandefor on 2005-12-20
[quote=amohanty]A buffer would be any block of memory which can contain data. In this example it is an array but it can be any data structure.

HTH[/quote]

thanks... that was the cause of more than a little confusion on my part. Thank you!

---

### Post by thumper on 2005-12-20
Iandefor, sorry for the confustion.  amohanty has the same understanding I do with respect to the term "buffer".

char arrays are often just used as a "chunk" of memory to put stuff and I tend to think of them as buffers rather than arrays or strings.

When you declare the char array ```
char a[11];
```that just allocates space on the stack (the local memory for the function is one way of thinking of that), however it does not initialise the contents.  So it could contain anything.  It is often good practice (especially when starting out) to get your variables into a known state first.
```
memset(a, 0, sizeof(a));
```is a handy way of doing that.  memset takes three parameters: the address to alter, the value to set it to, and how many bytes to set.

---

### Post by Iandefor on 2005-12-20
Very cool! Thanks so much for your patience with my inexperience; I just keep 
learning more and more via this thread. I'll have to keep the memset function in mind for the next time I have to declare a character array/buffer.

EDIT: Tried memset, and it's hidden away in string.h. Gave me a spot of trouble there. Just one quick question: do you know why some header files have to be explicitly included in the command line, like math.h, whereas others, such as string.h and stdio.h, are implicitly included?

---

### Post by cyrixware on 2005-12-21
:p hi frends....

---

### Post by Iandefor on 2005-12-21
Hullo! How much experience do you have with C :)? Maybe you can answer my question :-D

---

