---
title: "[SOLVED] Disable selective warning in GCC"
date: 2007-09-08
forum: Programming Talk
---

### Post by ansi on 2007-09-08
Hello,

 I've a block of code which is a reason for produced warnings by GCC while compiling. Is there any way to tell GCC not to show any kind of warnings for that block?

I've found *"#pragma GCC system_header"* which does what I want well, but it is obscurely how to enable warnings back :). So I mean smth. like that:
```

<code/>

#if defined __GNUC__
#pragma DISABLE_WARNINGS
#endif
   <my code is here/>
#if defined __GNUC__
#pragma ENABLE_WARNINGS_BACK
#endif

<code/>

```


Thank you,

---

### Post by gnusci on 2007-09-08
I think you should give us a snip of your warning so we can help you...

---

### Post by ansi on 2007-09-08
> **gnusci said:**
> I think you should give us a snip of your warning so we can help you...

Ok, it is easy. I have a C-header file with the contents like this:

```
<code/>
static const char* MyArr = {..};
#define STR_ARR(x)    (MyArr[x])
<code/>
```

And according to these definitions I get a warning about unused variable:
```
file.h: warning 'MyArr' defined but not used
```

So, apparently *MyArr* is used, but is used by macros.
Yes, I have a few ways to avoid this warning:
[LIST]
[*]Make an inline function instead macros
[*]Use MyArr[] directly in the rest part of the code
[/LIST]
But... but I like current implementation so it is why I'd like to get rid of this warning ;).


Thank you,

---

### Post by DougB1958 on 2007-09-08
I would think (although I have to admit that I haven't tried it to be sure) that if you ever use the STR_ARR macro, it will expand into a use of MyArr, which the compiler will see and therefore not print the warning message. Are you sure you are actually using the macro at least once? If not, the warning is pointing you to a real concern.

(Another thought, looking at your error message: you aren't compiling the header file by itself, are you, i.e., saying something similar to "gcc file.h"? Typically, header files don't get compiled that way, they get read by the compiler when you compile another file that "#include-s" them. This might be a reason why the compiler isn't seeing any uses of the macro and printing the warning....)

---

### Post by gnusci on 2007-09-08
an easy way is just changing the code for:

```

static const char* MyArr __attribute__ ((unused)) = {...};
#define STR_ARR(x)    (MyArr[x])

```

I just specified to this variable the attribute to be unused.

---

### Post by ansi on 2007-09-09
> **gnusci said:**
> an easy way is just changing the code for:

```

static const char* MyArr __attribute__ ((unused)) = {...};
#define STR_ARR(x)    (MyArr[x])

```

I just specified to this variable the attribute to be unused.

Gotcha! it does work! :) Thank you very much for your help! Question has been solved.

---

### Post by dwhitney67 on 2007-09-09
Darn!  I was hoping that someone would tell you that writing macros is considered poor programming, especially in the case you are implementing.

Write a function that returns a specific data type (in your case a const char).

---

### Post by ansi on 2007-09-09
> **DougB1958 said:**
>  Are you sure you are actually using the macro at least once? If not, the warning is pointing you to a real concern.


So, I just compile *.c* file (*.h* file is a part of the interface) to *.o* for further linking with main part of program where this macro is used. So, it is a reason why GCC shows warning :).


> **dwhitney67 said:**
> Darn!  I was hoping that someone would tell you that writing macros is considered poor programming, especially in the case you are implementing.

I agree with you on 50/50. Macros were invented to make programming easy, and  "writing macros is considered poor programming" causes only one question: why they were invented? ;)


> **dwhitney67 said:**
> 
Write a function that returns a specific data type (in your case a const char).


If I made a standalone function which does so, it would cause non-required call of function in a place where it is not really required; so, from time to time I'm trying to keep some ideas about optimization in mind :).

---

