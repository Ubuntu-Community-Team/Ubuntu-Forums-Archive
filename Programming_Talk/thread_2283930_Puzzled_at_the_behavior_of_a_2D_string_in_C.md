---
title: "Puzzled at the behavior of a 2D string in C"
date: 2015-06-25
forum: Programming Talk
---

### Post by shawon2 on 2015-06-25
I noticed a problem while writing a program for homework. The code was quite long but the troubling part was that
code:
```
#include <stdio.h>

int main()
{
    int x, y;
    char string[3][10];
    scanf("%d", &x);
    for(y = 0; y < 3; y++) {
        gets(string[y]);
    }
    printf("%s\n", string[0]);
    return 0;

}
```
in this program you should have the right to give three strings as input and expect the first one as output.
But both aren't true:mad:
What's the problem?I am not that experienced in C or programming.

---

### Post by TheFu on 2015-06-25
Simplify and test.  For example, does it work without a 2-dim array?

I honestly cannot help much because preallocating strings in this way is not very safe, so it is NEVER done in professional code that I've seen.  Now using an array of char* - that is a different story.

Also ... to write safer code, initialize all variables to known values.  and be careful reading anything from user input directly into anything other than a getline() call. If you need a number, convert it after the data is entered ... after you validate it doesn't contain anything except numbers.

---

### Post by steeldriver on 2015-06-25
How are you testing the program?

If you are entering something like

```

3
qwerty
asdfgh
zxcvbn

```
i.e. pressing the ENTER key after the initial digit, then the newline will still be in the buffer after the call to 'scanf' I think, and will be read by 'gets' as the first 'string'

Regardless, your code has issues - see for example [Why is the gets function so dangerous that it should not be used?]("http://stackoverflow.com/questions/1694036/why-is-the-gets-function-so-dangerous-that-it-should-not-be-used")

---

