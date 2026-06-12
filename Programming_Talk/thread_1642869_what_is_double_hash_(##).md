---
title: "what is double hash (##)"
date: 2010-12-11
forum: Programming Talk
---

### Post by c2tarun on 2010-12-11
I read about ## on the internet that it concatenates the string before it to string after it.

so
```

 #define FILENAME(extension) test_##extension
```

if we call FILENAME(black) then output should be

```
 test_black
```

but when i executed this code:

```

#include<stdio.h>
#define test_ "test_"
#define FILENAME(extension) test_##extension


int main(void)
{
  char p[]=FILENAME(black);
  printf("%s",p);
}


```

i m getting error: test_black not defined

can anyone please explain.

---

### Post by GeneralZod on 2010-12-11
> **c2tarun said:**
> 
i m getting error: test_black not defined

can anyone please explain.

Expand it yourself:

```

#include<stdio.h>
#define test_ "test_"
#define FILENAME(extension) test_##extension


int main(void)
{
  char p[]=test_black;
  printf("%s",p);
}


```

---

### Post by StephenDavison on 2010-12-11
That will not work either.  You're trying to initialize char []p to a string literal, but your function macro is not creating a string literal.  Try this:

#include <stdio.h>
#define FILENAME(extension) "test_"  #extension

int main(int argc, char *argv[]) {
    /* FILENAME(black)expands to the string literal "test_" "black" */
  char p[]=FILENAME(black);
  printf("%s",p);
}

---

### Post by nvteighen on 2010-12-11
C preprocessor macros are just a very primitive (though useful) text substitution feature. If you do:

```

#define x y

```

You'll be replacing every time **x** appears in your source file by **y**. And as I guess you already know, you can also create macro functions when your macro's results should depend on some parameter.

Now, the concatenation feature (##) allows you to make your macro take an argument and compose a new literal from it. Kind of what you get from strcat(), but alwys keep in mind that macros alter the source code, they don't work at runtime.

---

### Post by Arndt on 2010-12-11
> **nvteighen said:**
> C preprocessor macros are just a very primitive (though useful) text substitution feature. If you do:

```

#define x y

```

You'll be replacing every time **x** appears in your source file by **y**. And as I guess you already know, you can also create macro functions when your macro's results should depend on some parameter.

Now, the concatenation feature (##) allows you to make your macro take an argument and compose a new literal from it. Kind of what you get from strcat(), but alwys keep in mind that macros alter the source code, they don't work at runtime.

Remember single #, too. It makes a string literal out of an identifier, which may be relevant in the OP's context.

---

