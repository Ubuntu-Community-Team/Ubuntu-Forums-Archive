---
title: "Help understanding the stack in assembly"
date: 2011-04-06
forum: Programming Talk
---

### Post by Yes on 2011-04-06
I'm doing all of this in 32-bit NASM, on Linux.

I'm trying to understand the hardware stack, and how it's used to pass parameters to functions.  The way I think you're supposed to use it is like this:

```
function_1:
    push dword 1  ;param 2
    push dword 2  ;param 1
    call function_2

function_2:
    push ebp
    mov ebp, esp
```

So at this point, then [esp] = [ebp], which is the return pointer.  [ebp+4] is edi, and [ebp+8] is the first parameter and [ebp+12] is the second parameter.  Is that right?

Then, if you want local variables you're supposed to move esp back:
```
sub esp,8
```
Will give you room for two 4 byte local variables on the stack.  These are at [esp] and [esp+4], or [ebp-8] and [ebp-4].

And of course before returning, you need to restore everything - 
```
mov esp, ebp
pop ebp
ret
```

Is this all correct?  I read that you're supposed to use ebp to access the function parameters because if you have local variables, using esp to access the parameters is kind of error prone.  I understand that, but then why would I use something like [ebp-4] to access the local variables?  Wouldn't it be easier to just use [esp]?

Any advice would be much appreciated, I've been trying to understand this for a few days now :confused:

---

### Post by johnl on 2011-04-06
> **Yes said:**
> 
Is this all correct?  I read that you're supposed to use ebp to access the function parameters because if you have local variables, using esp to access the parameters is kind of error prone.  I understand that, but then why would I use something like [ebp-4] to access the local variables?  Wouldn't it be easier to just use [esp]?

Any advice would be much appreciated, I've been trying to understand this for a few days now :confused:

If you reference the arguments as [ebp+x] or local variables as [ebp-x] then they are always the same offset from ebp.  

Executing the function might involve pushing things onto and off of the stack -- for example, making another function call.  So now your stack pointer has changed, so you would need to calculate where exactly your local variables/parameters are based on the current state of the stack.


As an aside, what you are looking at is called the 'C calling convention' -- there are [other calling conventions](http://en.wikipedia.org/wiki/X86_calling_conventions) that pass arguments differently, including the x86_64 ABI which passes arguments in registers first prior to pushing anything on the stack.

Hope this helps!

---

### Post by Yes on 2011-04-06
Oh, that makes sense.  When I call a function edi and the the return pointer are pushed onto a stack, right?  Is esp moved back to make room for those, or does calling another function mess up the local variables?

---

