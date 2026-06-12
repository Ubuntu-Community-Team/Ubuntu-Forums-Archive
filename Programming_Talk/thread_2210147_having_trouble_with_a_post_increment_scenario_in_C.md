---
title: "having trouble with a post increment scenario in C"
date: 2014-03-09
forum: Programming Talk
---

### Post by IAMTubby on 2014-03-09
Hello,
 Please refer to this code. I am aware of the difference between pre and post increment and also that C parses from Right to Left. But I expected that the answer would be 1001 and not 1000 as it prints currently. I expected the i(in blue, on the extreme right) to increment itself it's value 0 had been added. So basically, I expected something like
1. Starting, from the right, the value 0 from the i in blue would be added to the result. At this point in time, val==0
**2. Then this i in blue gets incremented to 1. **At this point in time, val==0, but i==1
3. This then gets added to 1000. At this point in time, the value is 1000
4. This then gets added to the 'i'  in orange, in the extreme left. At this point in time, the value is 1001
5. Finally, i gets incremented to 2.

```
#include <stdio.h>

int main(void)
{
 int i=0;

 printf("val==%d ",[COLOR=#ff8c00]**i**[/COLOR]++ +1000 + **[COLOR=#0000ff]i[/COLOR]**++);
 return 0;
}

```

However, in java, I do get the expected value of 1001
```
class Now{
 public static void main(String[] args)
 {
  int i=0;


  System.out.println(i++ + 1000 + i++);
 }
}

```

I would like to know why the output is 1000 and not 1001 in C. Thanks.

---

### Post by spjackson on 2014-03-09
In C the behaviour is undefined; it might print 1000 and it might not. If you change the compiler, the compilation flags or the context, you might get a different result. You must not modify a variable twice without an intervening sequence point, see [http://c-faq.com/expr/seqpoints.html](http://c-faq.com/expr/seqpoints.html)

Compiling with -Wall gives...
```

$ gcc -Wall -o seq seq.c
seq.c: In function ‘main’:
seq.c:7: warning: operation on ‘i’ may be undefined

```

---

### Post by trent.josephsen on 2014-03-09
> **IAMTubby said:**
> Please refer to this code. I am aware of the difference between pre and post increment and also that C parses from Right to Left.
I think you mean left to right, but even so, how the language is parsed does not affect in what order the expressions are evaluated. C's grammar dictates that
```
i++ +1000 + i++
```
is parsed as
```
(((i++) + 1000) + (i++)) // this
((i++) + (1000 + (i++))) // NOT this
```
(not that it matters in this case), but it is explicit that the order of evaluation of the subexpressions is indeterminate. This is Question 3.2 of the comp.lang.c FAQ, but I see spjackson has already linked a related question.

---

