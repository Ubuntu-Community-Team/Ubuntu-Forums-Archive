---
title: "int and char C"
date: 2011-08-14
forum: Programming Talk
---

### Post by shashanksingh on 2011-08-14
I was under the impression that int and char are understandable of each other, and each char type can be type-casted into an int implicitly.

I have a strange problem

```

#include <stdio.h>

int main()
{
        int i=0;
        while(i!=1)
        {
                printf("Enter 1");
                scanf("%d",&i);
        }
        return 0;
}

```

while execution, if I enter an integer value in the scanf, the loop works fine.

But if I enter a char value, i becomes zero, and the program really doesn't wait for an input in scanf and goes into an infinite loop.:confused:

why is it so?

---

### Post by schauerlich on 2011-08-14
When you use the %d format with scanf, it tries to read in a series of digit characters (ie '0' through '9'), and try to figure out what integer that string of characters represents. However, if you enter something that isn't a digit, scanf gets confused and all hell breaks loose. This is why it's generally best to use fgets to read in an entire line, and then parse the input yourself (using atoi, atof, strtok, etc).

---

### Post by NovaAesa on 2011-08-14
I'm not sure what you mean by "understandable to each other", this seems like very inexact wording.

Have a look at the man page for scanf, specifically to find out what happens when whatever is in your input stream doesn't match the format string. When scanf looks at the input stream and finds input that doesn't match the format string, it doesn't alter the input stream and simply returns (error flags are also set internally, these can be accessed of course). So of course, this results in an infinite loop because the state of the input stream (and the entire program) stays the same between loop iterations.

---

### Post by Bachstelze on 2011-08-14
Thank you very much, your program is a very good example of why you should never use scanf, I will keep it. ;)

> I was under the impression that int and char are understandable of each other, and each char type can be type-casted into an int implicitly.

A char can always be cast to an int, the resulting int will have the same value as the char. The opposite is not true, an int can be cast to a char only if its value can be represented as a char. Otherwise the result is undefined. Note that this is only for signed char and int. For unsigned values, other rules apply.

Now for your problem: when you are using scanf, you must enter a value of the appropriate type for the conversion. If you use %d you must enter something that can be converted to an integer, otherwise the conversion will fail. When the conversion fails, the character remains in stdin, so when your program goes into the next loop and calls scanf, it will try to read the same character and fail again, ad infinitum.

The return value of scanf is the number of successful conversions, so you can use it to check whether the conversion was successful or not before calling scanf again:

```
firas@wakaba ~ % cat test.c 
#include <stdio.h>

int main()
{
        int i=0;
        int n, ch;
        while(i!=1)
        {
                printf("Enter 1 ");
                n = scanf("%d", &i);
                if (n == 0) {
                    printf("Input was not an integer!\n");
                    /* Discard all characters left in stdin */
                    while ((ch = getchar()) != '\n' && ch != EOF)
                        ;
                }
        }
        return 0;
}
firas@wakaba ~ % gcc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@wakaba ~ % ./test                                             
Enter 1 a
Input was not an integer!
Enter 1 z
Input was not an integer!
Enter 1 e
Input was not an integer!
Enter 1 2
Enter 1 1

```

But better yet is to use fgets so that you don't have this problem if a conversion fails:

```
firas@wakaba ~ % cat test.c 
#include <stdio.h>

int main()
{
        int i=0;
        int ch;
        char buf[3];
        while(i!=1)
        {
                printf("Enter 1 ");
                fgets(buf, 2, stdin);
                /* Discard any leftover charachers */
                while ((ch = getchar()) != '\n' && ch != EOF)
                    ;
                sscanf(buf, "%d", &i);
        }
        return 0;
}
firas@wakaba ~ % gcc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@wakaba ~ % ./test                                             
Enter 1 a
Enter 1 z
Enter 1 e
Enter 1 rt
Enter 1 2355
Enter 1 1

```

---

