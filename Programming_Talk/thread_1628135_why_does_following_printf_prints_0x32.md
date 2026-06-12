---
title: "why does following printf prints 0x32"
date: 2010-11-22
forum: Programming Talk
---

### Post by jamesbon on 2010-11-22
```
    #include<stdio.h>
    int main ()
    {
    printf("%#04x",50);
    }

```
 I  have used printf in C programs but above why did above code prints output as

```
    0x32
```

Can some one give me a link or reference to some thing so that I can understand it better.

---

### Post by spjackson on 2010-11-22
"man 3 printf" will tell you everything you need to know about it.

What don't you understand? What would you expect it to print and why?

---

### Post by trent.josephsen on 2010-11-22
int main(void)

---

### Post by lisati on 2010-11-22
Good luck with your adventures in programming.

> **spjackson said:**
> 
What don't you understand? What would you expect it to print and why?
Agreed: good question.
@jamesbon: printf() is a tool that can be used to "display" formatted output. A blunt but not particularly helpful answer to your question might be "because you told it to." The meaning of the first argument you have used in your code snippet is where you'll find your answer.

> **trent.josephsen said:**
> int main(void)

Agreed: although not always needed, it's often considered good manners to either provide arguments to a function's declaration or to specify "void" when you are not using any. In the case of "main()", they are commonly set to either a reference to argc and argv (used to analyse information given on the command line when you run your program), or voided out.

---

