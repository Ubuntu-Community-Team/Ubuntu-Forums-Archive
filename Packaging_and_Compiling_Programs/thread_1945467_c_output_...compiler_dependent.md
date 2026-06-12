---
title: "c output ...compiler dependent ?"
date: 2012-03-23
forum: Packaging and Compiling Programs
---

### Post by bilol on 2012-03-23
I understand that the output of the following code snippet is dependent upon the compilers.Can anybody explain the cases?

```
#include<stdio.h>
main()
{
	int x=7;
        printf("%d %d %d\n",x++,++x,x++);
	
}
```

OUTPUT in ubuntu 10.04 (gcc 4.4.3) :                9 10 7
OUTPUT in dev c++ 4.9.9.2 ( gcc version 3.4.2):     9  9 7
OUTPUT in vc++ 6.0:                                 8  8 7




thanks in advance...

---

### Post by oldos2er on 2012-03-23
Moved to Packaging and Compiling Programs.

---

### Post by SevenMachines on 2012-03-23
Hazy in my mind, but I'll give it a go :)
```
printf("%d %d %d\n",x++,++x,x++);
```is an example of undefined behaviour, all that happens is that different compilers handle undefined behaviour in different ways. Technically the arguments that pre/post increment x are not guaranteed specifically to be carried out in any particular order so any compiler, or the same one with different flags, might choose to do any one of them first. 

As with most undefined behaviour its best understood by understanding the nature of sequence points, points throughout code that mean that all previous statements have been carried out and all side-effects to do with them are also finished.

[EDIT]
[https://en.wikipedia.org/wiki/Sequence_point](https://en.wikipedia.org/wiki/Sequence_point)
[http://stackoverflow.com/questions/4176328/undefined-behavior-and-sequence-points](http://stackoverflow.com/questions/4176328/undefined-behavior-and-sequence-points)
another one!
[http://stackoverflow.com/questions/3812850/output-of-multiple-post-and-pre-increments-in-one-statement](http://stackoverflow.com/questions/3812850/output-of-multiple-post-and-pre-increments-in-one-statement)

---

### Post by codemaniac on 2012-03-23
The C language clearly tells that certain things lead to undefined behavior .
Please refer to wikipedia's page on [sequence point]http://en.wikipedia.org/wiki/Sequence_point[/URL] and [Undefined_behavior]http://en.wikipedia.org/wiki/Undefined_behavior[/URL]

---

### Post by codemaniac on 2012-03-23
try using the volatile type int .
and observe the change in behavior .
```
volatile int x=7;
```

---

