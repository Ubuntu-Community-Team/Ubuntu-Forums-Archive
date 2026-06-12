---
title: "C PROGRAMMING - Somethings wrong with... my library... or something..."
date: 2011-02-28
forum: Packaging and Compiling Programs
---

### Post by squareff255 on 2011-02-28
So I was trying to do some programs and I kept getting this error so I tried a simple "Hello World" program to make sure it wasn't me, and sure enough: same thing. I recently installed the 64-bit Ubuntu 10.04, so that could be part of it I guess... here are some screenshots...

[CLICK ME!]("http://www.dropbox.com/gallery/21461447/1/c%20error?h=2b0c3b")

The first one is the output and such, the second is my program...

Thanks in advance! :)

---

### Post by squareff255 on 2011-02-28
For those of you who would rather I posted the output in text, rather than images, here it is:

The program is THIS:

```
#include <stdio.h>

main ()
{
  printf("Hello World!\n");
}
```

and the output is this:


```
./helloworld.c: line 5: syntax error near unexpected token `"Hello World!\n"'
./helloworld.c: line 5: `  printf("Hello World!\n");'

```

---

### Post by ibuclaw on 2011-02-28
Oh man...

gcc outputs the executable as 'a.out' - you run ./a.out to execute the compiled binary...

---

### Post by jwbrase on 2011-02-28
> **ibuclaw said:**
> Oh man...

gcc outputs the executable as 'a.out' - you run ./a.out to execute the compiled binary...

It doesn't output an executable if there's an error, and the OP reports that he's run into errors.

---

### Post by SaintDanBert on 2011-02-28
You wrote:
```

#include <stdio.h>

main ()
{
  printf("Hello World!\n");
}

```

I think that your problem lies with the declaration of the main function. Programs return an integer that reflects a success or error status. In addition, main() takes parameters for the command line and the process environment.

Try this:
```

int main( int argc, char * argv[] )

```
"int" provides a place for the return value
"int argc" is an integer count of the number of command line items
"char * argv[]" is an array of pointers to characters (strings) where each is one, blank separated, command line parameter.

Now I'm using gcc v4.4.3 and both versions of the program work fine when I compile **hello.c**

The **gcc** compiler will work with either 'C' or 'C++' source code.
There are many features of C++ that parallel plain C and help one write better code -- strong typing, void data type, and so on. One can write plain-C programs using a C++ compiler, but you must learn how. Until then, it is easy to wander back and forth.

~~~ 0;-Dan

---

### Post by onandcorei on 2011-03-01
Problem is that helloworld.c is executable by default or you gave this (chmod +x helloworld.c)
That is not appropriate to execute source code using itself.

---

### Post by squareff255 on 2011-03-01
......... -_- Whoops... THAT'S embarrassing...

---

