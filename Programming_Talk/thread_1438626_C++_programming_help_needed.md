---
title: "C++ programming help needed"
date: 2010-03-25
forum: Programming Talk
---

### Post by jjones237 on 2010-03-25
Can anybody run through the steps it takes to get the output for this problem?  This is a practice example I was given.  Help is appreciated.


#include <stdio.h>

#include <ctype.h>

int main() {

  char c;

  while ((c = getchar()) != '0') {

    if (isupper(c))

       putchar(('A' + 15-(c-'A')));

    else if (islower(c))

       putchar(('a' + 5 +(c-'a')) );

    else

       putchar(c);
  }

  return 0;
}

---

### Post by jjones237 on 2010-03-25
The input is :  aBcD!0

---

### Post by abraxas334 on 2010-03-25
So I guess the ouput is fOhM! But you knew that already.
What does the program do?
[http://www.cplusplus.com/reference/clibrary/cstdio/putchar/](http://www.cplusplus.com/reference/clibrary/cstdio/putchar/)
the function putchar returns the character onto the screen.
It is actually working on it as the int value/ascii value.
So upper case A has the value of 65.

> putchar(('a' + 5-(c-'a'))); //here c is 'a'
This becomes in mathematical terms for the first input character:
97+5-(97-97) = 102 -> this corresponds to the ascii charakter of 'f'
the the next letter is capital so it will go into this one:
```
putchar(('A' + 15-(c-'A'))); //where the character is B
```
following the same scheme:
ASCII value for A = 65 B=66
65+15-(1)= 79 -> ASCII is 'O'

I assume this explains the output. Here is a list for all the ASCII codes in case you don't have them in mind like me.
[http://www.ascii-code.com/]("http://www.ascii-code.com/")

---

