---
title: "gets() does not append '\0'?"
date: 2012-07-17
forum: Programming Talk
---

### Post by Tk007LwZFJW5ej on 2012-07-17
Whenever I use the c function gets() to input a string, then try to parse the string with a pointer in a loop using pointer != '\0' as the loop termination condition, the pointer always goes way out of the bounds of the string anyhow.

```

#include <stdio.h>

#define string_terminator    '\0'
#define MAX_CHARS            80

void main()
{
    char input[MAX_CHARS];
    char *ptr_to_string  = input;

    gets ( input );

    for (input; input != string_terminator; input++)
        puts ( input );


```This code outputs all kinds of stuff outside of the array of chars. It does the exact same thing if I use

```

for (ptr_to_string; ptr_to_string != string_terminator; ptr_to_string++)

```What am I doing wrong?

---

### Post by MadCow108 on 2012-07-17
from its own manpage:

**_Never_  use  gets()**

its so bad it has even been removed from the C standard!

use fgets instead

as for your problem *ptr_to_string != string_terminator* compares a pointer and will thus always be true
you have to dereference input to get the value it points to:
```
*ptr_to_string != string_terminator
```

---

### Post by trent.josephsen on 2012-07-17
The *pointer* `input` never becomes 0. The *referent* of input, i.e. the character it points to, will become 0 when input points 1 past the end of the string. You need to change the test to `*input` instead of just `input`. A C-idiomatic way to do this might be more like
```
while (*input++) {
    puts(input);
}
```

However you should really not use gets in the first place.

---

### Post by Bachstelze on 2012-07-17
Incidentally, you should probably stop using whatever learning material you are using right now which gave you the idea to use gets().

---

### Post by Tk007LwZFJW5ej on 2012-07-17
> **Bachstelze said:**
> Incidentally, you should probably stop using whatever learning material you are using right now which gave you the idea to use gets().

I would, but the library doesn't have any other books on c available, and I don't have internet access at home. I read in the documentation of gets() that it should not be used, but I haven't learned how to manipulate streams yet so I don't know how to use fgets.

---

### Post by trent.josephsen on 2012-07-17
It's easy.

```
fgets(buf, sizeof buf, stdin);
```

Nothing magic about it, `stdin` just represents that you want to read from standard input (usually a terminal). You can replace it with other things later when you want to read from files.

(Edit: In case it wasn't clear, `buf` here should be the array you want to read into.)

---

### Post by Lux Perpetua on 2012-07-18
> **trent.josephsen said:**
> ```
fgets(buf, sizeof buf, stdin);
```This is partially correct, but it's important to note that it will only work if buf is allocated statically; it will fail horribly if buf is allocated dynamically. This trips up beginners all the time. 

**StarKid** - Instead of ```
gets(buf);
```use```
fgets(buf, buf_size, stdin);
```buf_size is however many characters the buffer can hold. (In your example, it's MAX_CHARS.) stdin is stdin; don't mess with it. Later, you'll learn about reading from files, which is what that third argument lets you do. 

Seriously, though, don't ever use gets.

---

### Post by trent.josephsen on 2012-07-18
> **Lux Perpetua said:**
> This is partially correct, but it's important to note that it will only work if buf is allocated statically; it will fail horribly if buf is allocated dynamically. This trips up beginners all the time.

It would be more accurate to say that it works only when buf is an *array object* and not when buf is a *pointer object*. Whether the memory itself is statically or dynamically allocated is irrelevant, as **sizeof** is evaluated at compile time and the first argument will decay to a pointer anyway.

You're quite right to warn about it, though.

---

