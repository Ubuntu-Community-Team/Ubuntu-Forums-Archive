---
title: "Compiling C programs"
date: 2009-02-08
forum: Programming Talk
---

### Post by lcruz007 on 2009-02-08
Hi,

I used to program many C/C++ programs before... and compiled them without a problem using Ubuntu. 
Now I cannot compile any of my programs, as an example this hello world...

```
//Hello World

#include <stdio.h>

void main()
{
  printf("Hello World!");

}
```

This is the output I get:

```
luis@luis-laptop:~/Documents$ gcc hlw.c
hlw.c: In function ‘main’:
hlw.c:6: warning: return type of ‘main’ is not ‘int’
luis@luis-laptop:~/Documents$ 
```


Do you know what's the problem???


Thanks in advance.

---

### Post by mike_g on 2009-02-08
use: int main()

---

### Post by Taidgh on 2009-02-08
And make main() return 0 (0 == success).

---

### Post by Tek-E on 2009-02-08
Yes void main() needs to be int main()
and shouldnt you comments be like this /* Hello World */
Because I didnt think that the C compilers read a comment only until the 
EOL??   You dont "have" to return the 0 on success but it is usefull.

---

### Post by hanniph on 2009-02-08
> **Tek-E said:**
> and shouldnt you comments be like this /* Hello World */ Because I didnt think that the C compilers read a comment only until the 
EOL??  

It does with // comments. 
Comments like 
> //Hello World
 are correct

---

### Post by jespdj on 2009-02-08
// comments are a new feature of C99, the standard version of the C programming language from 1999.

In older versions of C, only /* ... */ comments were allowed.

---

### Post by dwhitney67 on 2009-02-08
> **lcruz007 said:**
> Hi,

I used to program many C/C++ programs before... and compiled them without a problem using Ubuntu. 
Now I cannot compile any of my programs, as an example this hello world...

```
//Hello World

#include <stdio.h>

void main()
{
  printf("Hello World!");

}
```

This is the output I get:

```
luis@luis-laptop:~/Documents$ gcc hlw.c
hlw.c: In function ‘main’:
hlw.c:6: warning: return type of ‘main’ is not ‘int’
luis@luis-laptop:~/Documents$ 
```


Do you know what's the problem???


Thanks in advance.

It's not a problem; that is merely a warning.  Naturally, you should attempt to correct the issue, since that is good programming practice.  The other posts prior to mine have provided the solution.

Concerning GCC, by default C-1989 standards are used when compiling, probably because there is still a lot of legacy s/w applications that were coded to that standard (and it would be too costly to upgrade them).

If you want to use features from the 1999 standard (such as the comments in the code you posted), then you need to specify either -std=gnu99 or -std=c99 (each of these has their own little quirks).

Btw, for those who have been programming for ages, do you remember this style of C programming?  Note the function declarations.  :-)
[php]
#include <stdio.h>

void function(val1, val2)
  int val1;
  int val2;
{
  printf("%d, %d\n", val1, val2);
}


int main(argc, argv)
  int argc;
  char** argv;
{
  function(10,20);
}
[/php]

---

