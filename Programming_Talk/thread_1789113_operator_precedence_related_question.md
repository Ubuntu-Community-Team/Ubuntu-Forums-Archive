---
title: "operator precedence related question"
date: 2011-06-23
forum: Programming Talk
---

### Post by jamesbon on 2011-06-23
Here are  2 programs

Program 1
```
#include<stdio.h>
int main()
{
int b=5;
int c= (b++)+(++b);
printf("%d",c);
}

```
the output of above is ```
12.
```

Program 2
```
#include<stdio.h>
int main()
{
int b=5;
int c= (b++) + (++b) + (++b) + (++b); 
printf("%d",c);
}

```
The output of program 2 is ```
27.
```
I took program 2 from [here]("http://wiki.answers.com/Q/Explain_pre_increment_and_post_increment_operator_with_an_example") the logic with which it has been explained does not give output 29 on my machine the output is 27.

Where as for same logic the output of program 1 is 12.
Which seems correct.
I want to understand why in program2  output is 27 and not 29.

---

### Post by johnl on 2011-06-23
I suspect that you are running into 'undefined behavior' territory.

```

warning: operation on `b` may be undefined [-Wsequence-point]

```

Read about [sequence points](http://en.wikipedia.org/wiki/Sequence_point) to figure out what's going on here.

Specifically, the plus operator is not a sequence point, so any of the (b++) or (++b) in your statement can be evaluated in any order.

---

### Post by geirha on 2011-06-23
27 and 29 are equally correct results, because the behavior of more than one increment operation on the same variable in the same expression is not defined, so it depends entirely on how the compiler decides to process it. The short answer is, don't do it. It makes absolutely no sense to have multiple increments on the same variable in the same expression.

---

### Post by zobayer1 on 2011-06-23
> **geirha said:**
> 27 and 29 are equally correct results, because the behavior of more than one increment operation on the same variable in the same expression is not defined, so it depends entirely on how the compiler decides to process it. The short answer is, don't do it. It makes absolutely no sense to have multiple increments on the same variable in the same expression.

Why do you think multiple increment is not defined? I do such thing (well not that level of complexity) every now and then, never faced trouble.
What is not defined is something like ++b++ (ow this is a CE), but ++b + b++ is perfectly defined. But yes, old compilers like turbo C differs from todays compilers.
As C evaluates assignment operators from right to left, and then, for same precedence, the evaluate from left to right. So it is 27 in my opinion.
int c = b++ + ++b + ++b + ++b; 

You need to resolve the assignments first, and they are from rightmost to left most:
```

b = 5
int c = b++ + ++b + ++b + 6
           b++ + ++b + 7 + 6
           b++ + 8 + 7 + 6
           8 + 8 + 7 + 6
c = 27, b = 9

```What I doing am wrong here?

---

### Post by Arndt on 2011-06-23
> **zobayer1 said:**
> Why do you think multiple increment is not defined? I do such thing (well not that level of complexity) every now and then, never faced trouble.
What is not defined is something like ++b++ (ow this is a CE), but ++b + b++ is perfectly defined. But yes, old compilers like turbo C differs from todays compilers.
As C evaluates assignment operators from right to left, and then, for same precedence, the evaluate from left to right. So it is 27 in my opinion.
int c = b++ + ++b + ++b + ++b; 

You need to resolve the assignments first, and they are from rightmost to left most:
```

b = 5
int c = b++ + ++b + ++b + 6
           b++ + ++b + 7 + 6
           b++ + 8 + 7 + 6
           8 + 8 + 7 + 6
c = 27, b = 9

```What I doing am wrong here?

There was a long discussion in January about this: [http://ubuntuforums.org/showthread.php?t=1668152](http://ubuntuforums.org/showthread.php?t=1668152). I think post #15 is the first worthwhile response to read.

---

### Post by JupiterV2 on 2011-06-23
What everyone should know about undefined behaviour: [http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html]("http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html") Just because it works does not mean you should do it.

---

### Post by zobayer1 on 2011-06-23
Yeah, I have just tested, I was wrong... Glad to know the fact :) Thanks guys...

---

### Post by jamesbon on 2011-06-30
Ok I learned a bit more.There is some thing known as a sequence point.

If within an expression sequence point exists then the behavior would be defined otherwise not.Usually in such expressions sequence point within expression are not defined so the result is not sure.

An example of sequence point is comma operator (**,**) within an expression and if you take statement then **;** is the sequence point.**So a missing sequence point is cause of undefined behavior above.**

---

