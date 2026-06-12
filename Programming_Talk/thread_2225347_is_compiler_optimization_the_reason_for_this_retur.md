---
title: "is compiler optimization the reason for this return value"
date: 2014-05-21
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-21
Hello,
 I have thought about this for some time, but can't figure out a reason apart from Compiler optimization for the following observation.

Please see the code below and the question that follows :
```
#include <stdio.h>

int main(void)
{
 printf("inside main : %d",fun(5));


 return 0;
}


int fun(int i)
{
 int ret = 99;


 if(i < 0)
  return 98;


 printf("hello [%d]\n",i);
 ret = fun(i-1);

 [COLOR=#ff0000]**//please note that I'm not doing a return ret; here**[/COLOR]
}

```

I understand that the stack which has i==-1 will return the value 98 to the previous stack which has i==0.
_But my question is,_ **how are the stacks which have i value as 0,1,2,3,4,5 also returning the value 98 ?**

My attempts
1. If we were doing a return ret; in the comment I mentioned in code, it would have made sense as to why the other stacks are returning 98, but since I'm not doing a return ret; I can't figure out the reason.
2. Initially I was doing a return 0 instead of return 98; and since they all returned the same value 0, I thought it's probably because the default return value of a function if nothing is returned is 0, and so changed the return to 98. But as I said, here also I observe that all the invocations return the same vaue(98)

_Can you help me along these lines - what is the default value of an int function if it doesn't have a return at the end ?_

Please advise.
Thanks.

---

### Post by Vaphell on 2014-05-21
i'd say that compiler, seeing that you don't care about > -1, used the undefined situation to remove the check.

instead of *if(i<0) return 98* you get *return 98*

Btw, you have an interesting way of learning, studying failures and undefined states.

---

### Post by ofnuts on 2014-05-21
I don't undertsand your vocabulary... a "stack" doesn't return anything because a stack is data and not executable code.

You are wasting your time trying to understand what is fundamentally undefined behavior. In most cases the return value of a function is some conventional register (it's not even put in the stack) to if you don't explicitly return something the caller sees whatever value was left in that register. However, registers can also be used to pass parameters, so what you are seeing could also be the parameter to your printf() left in a register than is considered as a return value elsewhere.

You can ask GCC to generate the equivalent assembler code if you are curious.

---

### Post by IAMTubby on 2014-05-21
> **Vaphell said:**
> i'd say that compiler, seeing that you don't care about > -1, used the undefined situation to remove the check.
instead of *if(i<0) return 98* you get *return 98*
Vaphell, you mean to say, it's undefined behavior ?
"used the undefined situation to remove the check." - did not understand those words.

> Btw, you have an interesting way of learning, studying failures and undefined states.
Thanks, you actually made my day :cool:

---

### Post by IAMTubby on 2014-05-21
> **ofnuts said:**
> I don't undertsand your vocabulary... a "stack" doesn't return anything because a stack is data and not executable code.
Sorry, ofnuts, I meant to say particular invocation of the recursive function. What is the correct word to use here ? Invocation ?

> 
You are wasting your time trying to understand what is fundamentally undefined behavior. In most cases the return value of a function is some conventional register (it's not even put in the stack) to if you don't explicitly return something the caller sees whatever value was left in that register. However, registers can also be used to pass parameters, so what you are seeing could also be the parameter to your printf() left in a register than is considered as a return value elsewhere.
ofnuts, I promise not to drag this too long.
See this
```
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ cat test.c #include <stdio.h>


int main(void)
{
 printf("inside main : %d",fun(5));

 return 0;
}


int fun(int i)
{
 int ret = 99;

 if(i < 0)
  return 98;

 ret = fun(i-1);
 **printf("return value from stack at i==[%d] is : [%d]\n",i-1,ret);**
}
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ ./a.out 
return value from stack at i==[-1] is : **[98]**
return value from stack at i==[0] is : **[45]**
return value from stack at i==[1] is : **[44]**
return value from stack at i==[2] is : **[44]**
return value from stack at i==[3] is : **[44]**
return value from stack at i==[4] is : **[44]**

```
I counted the characters inside printf and it comes to 45.
_So can we close this saying it's undefined behavior and the return value depends on some conventional register which may also be used to hold the parameter to printf ?_

> You can ask GCC to generate the equivalent assembler code if you are curious.
I'll do that next, I have generated the .s file using the -S flag, but I need to go through some tutorials to understand assembly code. No worries!

---

### Post by ofnuts on 2014-05-21
in your latest try, the return value from printf() (the count of characters) is left in place so the next level up still sees it as the value returned by fun()

---

### Post by Vaphell on 2014-05-21
what i meant was
i<0: return X
i>=0: return ??? // undefined, the function will return "something"

compiler sees undefined scenario and "thinks": *hmmm, he seems not to care about the 2nd case at all, so if i put X in place of ??? too, I will be able to remove the [I]if (i<0)* test entirely. Simpler code, no conditional jump = win!
[/I]
i<0: return X
i>=0: return X
=
return X


No idea if that's what actually happens, though it seemed plausible. Either way, just like ofnuts i think you are largely wasting time. Trying to tame undefined behavior to do your bidding is the shortest path to shooting yourself in the foot. You want the exact opposite - no place for compiler or the architecture to screw you over with some obscure implementation detail.

---

### Post by IAMTubby on 2014-05-23
> **ofnuts said:**
> in your latest try, the return value from printf() (the count of characters) is left in place so the next level up still sees it as the value returned by fun()
Thanks ofnuts.

> **Vaphell said:**
> what i meant was
i<0: return X
i>=0: return ??? // undefined, the function will return "something"

compiler sees undefined scenario and "thinks": *hmmm, he seems not to care about the 2nd case at all, so if i put X in place of ??? too, I will be able to remove the [I]if (i<0)* test entirely. Simpler code, no conditional jump = win!
[/I]
i<0: return X
i>=0: return X
=
return X

Thanks Vaphell.

---

