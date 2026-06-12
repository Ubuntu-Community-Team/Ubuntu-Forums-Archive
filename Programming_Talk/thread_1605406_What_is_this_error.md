---
title: "What is this error?"
date: 2010-10-25
forum: Programming Talk
---

### Post by newport_j on 2010-10-25
cilk: 5: error expected constructor destructor or type conversion before 'int'
 
I got the above error when i tried to compile a Cilk c++ program. I am not sure what it is. I took the code directly out of a document, I still got the error.
 
The code is shown below. cilk int fib (int n) is line 5.
 
 
 
#include <cilk.h>
#include <stdlib.h>
#include <stdio.h>
 
cilk int fib (int n)
{
if (n<2) return n;
else
{
int x, y;
x = spawn fib (n-1);
y = spawn fib (n-2);
sync;
return (x + y);
}
}
cilk int main (int argc, char *argv[1])
{
int n, result;
 
n = atoi(argv[1]);
result = spawn fib (n);
printf("Result: %d\n", result);
return 0;
} 
 
 
I believe that this is a c++ error and not a Cilk error.
 
Newport_j

---

### Post by Zugzwang on 2010-10-25
Could you please copy&paste the *whole* error message you get, including the command you used for compiling. Example:

```

me@my-computer:/tmp$ g++ test.cpp 
test.cpp:1:18: error: cilk.h: No such file or directory
test.cpp:5: error: expected constructor, destructor, or type conversion before ‘int’

```

---

### Post by dwhitney67 on 2010-10-25
newport_j... after posting over 200 times on this forum, I would've figured that by now you would know to post code within CODE tags.

Btw, what is "cilk" in the context below?
```

cilk int fib (int n)
{
  ...
}

cilk int main(...)
{
  ...
}

```

---

### Post by GeneralZod on 2010-10-25
After having a quick look through here:

[http://supertech.csail.mit.edu/cilk/manual-5.4.6.pdf](http://supertech.csail.mit.edu/cilk/manual-5.4.6.pdf)

it looks like cilk code needs to be run through the "cilkc" pre-processor i.e it cannpt be run through a standard C compiler like GCC - newport_j: is this what you're doing? There's not much detail in the OP.

---

### Post by talonmies on 2010-10-25
No, that isn't a "C++ error". 

It is a pretty common "newport_j error" - trying to use a parallel programming environment which he doesn't understand, which sits over a programming language he doesn't understand, running on an operating system he doesn't understand. The only difference in this case seems to be that instead of NVIDIA CUDA, he seems to has switched to Cilk++.

To answer the question: you can't compile Cilk code with the standard C++ compiler.

---

### Post by newport_j on 2010-11-22
Talonomies:
 
I like you too. What a nice person. You clearly undertsand little and need to learn more.
 
 
Newport_j
 
PS. A lot more.

---

### Post by newport_j on 2010-11-22
Whoops!!! 
 
I meant Talonmies not Talonomies.
 
Talonmies, you have never worked under a deadline have you? 
 
I assume you have a job. May be a big assumption?
 
Newport_j

---

### Post by nvteighen on 2010-11-22
> **newport_j said:**
> Whoops!!! 
 
I meant Talonmies not Talonomies.
 
Talonmies, you have never worked under a deadline have you? 
 
I assume you have a job. May be a big assumption?
 
Newport_j

Ok, please let's stop this right here before it gets worse. 

Now, could you please answer whether you tried to use the Cilk preprocessor or not?

---

### Post by newport_j on 2010-11-22
Yes, I did. it was a question of using an outdated manual on Cilk nothing more. They changed the code around from my outdated manual. I was using sample code from an outdated manual with the current compiler. 
 
Everything is fine now.
 
Newport_j

---

