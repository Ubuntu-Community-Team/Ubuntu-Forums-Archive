---
title: "Arrys programm - C"
date: 2011-06-16
forum: Programming Talk
---

### Post by stamatiou on 2011-06-16
Hey guys,
I have recently started learning C from the boot "The C Programming Language". There is an array example that I have partially understood.
The example is:
```
 #include <stdio.h>     /* count digits, white space, others */    main()    {        int c, i, nwhite, nother;        int ndigit[10];         nwhite = nother = 0;        for (i = 0; i < 10; ++i)            ndigit[i] = 0;         while ((c = getchar()) != EOF)            if (c >= '0' && c <= '9')                ++ndigit[c-'0'];            else if (c == ' ' || c == '\n' || c == '\t')                ++nwhite;            else                ++nother;         printf("digits =");        for (i = 0; i < 10; ++i)            printf(" %d", ndigit[i]);        printf(", white space = %d, other = %d\n",            nwhite, nother);    }
```
At the spot where it says ++ndigit[c-'0'], why does it say c-'0' and not just c, isn't it the same?
Also why in this particular spot the numbers are written with ' ? ```
if (c >= '0' && c <= '9')
++ndigit[c-'0'];
```
shouldn't it say 
```
if (c >= 0 && c ,=9)
++ndigit[c-0]
```?

---

### Post by simeon87 on 2011-06-16
The index of an array is an integer. In this case c is a character so you cannot have c as index of the array: the ASCII value of a character is often much larger than the indices 0 till 9 in this array.

So to map the character '0' to index 0, the character '1' to index 1 and so on, you have to subtract '0' from the character. That means you'll get 0 for the character '0', 1 for the character '1' and so on, as intended.

---

### Post by lisati on 2011-06-16
The formatting was a bit weird in my browser, so in the interests of making it readable, here goes:
```

#include <stdio.h>
/* count digits, white space, others */
main()
{
    int c, i, nwhite, nother;
    int ndigit[10];
    nwhite = nother = 0;
    for (i = 0; i < 10; ++i)
        ndigit[i] = 0;
    while ((c = getchar()) != EOF)
        if (c >= '0' && c <= '9')
            ++ndigit[c-'0'];
        else if (c == ' ' || c == '\n' || c == '\t')
            ++nwhite;
        else
            ++nother;
    printf("digits =");
    for (i = 0; i < 10; ++i)
        printf(" %d", ndigit[i]);
    printf(", white space = %d, other = %d\n",
           nwhite, nother);
}

```

As simeon87 has noted, the program is starting with a text representation of the number, and some conversions need to happen before you can treat it as if it was raw binary.

---

### Post by stamatiou on 2011-06-16
> **simeon87 said:**
> The index of an array is an integer. In this case c is a character so you cannot have c as index of the array: the ASCII value of a character is often much larger than the indices 0 till 9 in this array.

So to map the character '0' to index 0, the character '1' to index 1 and so on, you have to subtract '0' from the character. That means you'll get 0 for the character '0', 1 for the character '1' and so on, as intended.
This is the answer for the first question?

---

### Post by simeon87 on 2011-06-16
> **stamatiou said:**
> This is the answer for the first question?

Yes. The answer to the second question is that '0' is a character and 0 is a number. In this case, you're reading characters so characters are used. The expression c - '0' means that you're subtracting the ASCII value of the character '0' from the character c.

---

### Post by lisati on 2011-06-16
> **stamatiou said:**
> This is the answer for the first question?

Short answer: yes.

The computer makes a distinction between the number 0, the character '0', the letter 'o', and the capital letter 'O'. When you type the character '0' on your keyboard, the computer has to change it to a number 0 before it can use it as an index to an array. 

Edit: <snip>

---

### Post by stamatiou on 2011-06-16
> **lisati said:**
> Short answer: yes.

The computer makes a distinction between the number 0, the character '0', the letter 'o', and the capital letter 'O'. When you type the character '0' on your keyboard, the computer has to change it to a number 0 before it can use it as an index to an array. 

Edit: <snip>
So an aray can handle only strings, that's why the numbers are between quotes, and if not  when do I  have to put it between quotes and when not?

---

### Post by cgroza on 2011-06-16
> **stamatiou said:**
> So an aray can handle only strings, that's why the numbers are between quotes, and if not  when do I  have to put it between quotes and when not?
Arrays can handle any data type. You put quotes when you want a char* and no quotes when you want an int.

---

### Post by lisati on 2011-06-16
> **stamatiou said:**
> So an aray can handle only strings, that's why the numbers are between quotes, and if not  when do I  have to put it between quotes and when not?

As cgroza said, arrays can handle any data type.

The need to subtract '0' might seem a little strange when you are learning programming, but there is a reason for it. When you use getchar() and someone presses one of the keys 0-9, your program will see one of the **character**s 0-9, not the **number**s 0-9 that would be of more useful as an index to your array. 

Say, for example, someone pressed '0', and your program retrieved it using getchar() and put it in a variable. If we were to inspect the memory used for the variable, it would contain the number 48 (decimal), not zero.

Have a look here: 
[http://en.wikipedia.org/wiki/Ascii](http://en.wikipedia.org/wiki/Ascii)

---

### Post by cgroza on 2011-06-16
See atoi() if you want conversion between them:
[http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/](http://www.cplusplus.com/reference/clibrary/cstdlib/atoi/)

There is whole bunch of them...

---

