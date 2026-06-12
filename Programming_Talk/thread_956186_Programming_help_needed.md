---
title: "Programming help needed"
date: 2008-10-23
forum: Programming Talk
---

### Post by vandorjw on 2008-10-23
For a programing assignment at school, I have to make a two part program.
The first part, which is called,

"program.c" 

has two functions in it, called "helpme" and "ubuntu" for example.
> 

#include <stdio.h>
#include <math.h>

int ubuntu(int y);
int helpme(int x);

int ubuntu(int y)
{
...do stuff

   ...printf("%d \n" y);
}

int helpme(int x)
{
...do stuff;
...printf(%d \n, x);
}

---------------------------------------------
Now, the second file, called "test.c"

should contain something to test the functions.

I imagine I would do it like
> 
#include <program.c>

helpme(1);
helpme(2);
helpme(3);

ubuntu(1);
ubuntu(2);
ubuntu(3);


----------------------------

If anyone understood what I am trying to say here, and know how to do link the program.c file to the test.c file, then please let me know ASAP.

Thanks a million,
CC7

---

### Post by dwhitney67 on 2008-10-23
Your second module (file), test.c, requires a main() function declaration/implementation.

You will also need to declare the ubuntu() and helpme() functions as "extern".
[php]
extern int ubuntu(int);
extern int helpme(int);

int main()
{
  ubuntu(10);
  helpme(20);

  return 0;
}
[/php]

To compile and run the program:
```

gcc test.c program.c -lm -o output
./output

```

P.S.  The -lm is needed to link in the math library, should you use it.  It appears that this is your intent since you have included math.h in program.c

---

