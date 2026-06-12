---
title: "recursion vs iterative"
date: 2011-03-21
forum: Programming Talk
---

### Post by cybo on 2011-03-21
can anybody explain when would i use recursion approach as opposed to the iterative one? any help is appreciated.

---

### Post by Arndt on 2011-03-21
> **cybo said:**
> can anybody explain when would i use recursion approach as opposed to the iterative one? any help is appreciated.

Can you give more context?

It depends on many things, so it's like asking when would you use linked lists as opposed to arrays.

If you have to choose one and don't know why one would be better, just toss a coin.

---

### Post by psld on 2011-03-21
A good thing to know is that since recursion is a stack of function calls, it also takes up stack memory to save all local variables. (if not optimized by the compiler, however this is not always possible anyway).

---

### Post by Simian Man on 2011-03-21
You can solve any problem with both, but some problems will be far easier to solve with one or the other.  It often depends on your data structure.  Arrays typically lend themselves to iterative solutions while trees and graphs typically lend themselves to recursive ones.

---

### Post by Npl on 2011-03-21
You can turn iterative problems into recursive quite easily (tail-recursion), but its not so simple the other way around.
In fact I`d argue that the only way to create a "iterative implementation" for eg. quicksort is to manually keep a stack of open partitions, which is merely doing the same thing the compiler does automatically in the recursive implementation.

---

### Post by WinstonChurchill on 2011-03-21
An iterative implementation will ALWAYS be faster than a recursive one, due to the overhead of repetitive function calls in recursion - although for some things, a recursive implementation will be much easier to conceptualize.

Compilers often cannot optimize out recursion - consider:
```

unsigned int factorial(unsigned int num)
{
        return ((num > 1) ? (num * factorial(num - 1)) : num);
}

```This is un-optmizable if the number to be factorialized is not a compile-time constant: since the compiler can't know what number will be passed to the function, it has no way to "inline" the recursion. (If it IS a compile time constant, however, it could easily be optimized out). Furthermore, it places a limit on the size of the integer you can factorialize: on x86-64, for instance, (assuming the stack is permitted to grow to any size) you're limited to factorializing integers equal to the amount of memory in your machine in bytes divided by 16 (return address plus the implied variable on the stack).

Then consider:
```

unsigned int factorial(unsigned int num)
{
    unsigned int result = num;
    while(num > 1) {
        result *= --num;
    }
    return result;
}

```Not only will this run faster, but it permits you to take the factorial of arbitrarily large integers (although you will eventually overflow the integer you're storing the result in).

(Neither of these implementations correctly handle the case where we want to take the factorial of zero)

---

### Post by Simian Man on 2011-03-21
> **Npl said:**
> You can turn iterative problems into recursive quite easily (tail-recursion), but its not so simple the other way around.
In fact I`d argue that the only way to create a "iterative implementation" for eg. quicksort is to manually keep a stack of open partitions, which is merely doing the same thing the compiler does automatically in the recursive implementation.
You're confusing problems with solutions.  Quicksort is a solution, not a problem.  You can convert solutions between iterative and recursive, like you said, but that wasn't what I meant exactly.

> **WinstonChurchill said:**
> An iterative implementation will ALWAYS be faster than a recursive one, due to the overhead of repetitive function calls in recursion


That isn't true.  Consider the following code:
```

int fact(int x) {
  int fact1(int n, int result) {
    if(n == 0)
      return result;
    else
      return fact1(n - 1, result * n);
  }

  return fact1(x, 1);
}

```
When compiled with gcc -O3 this code contains no recursive calls.  This implementation is implemented recursively, but is the same basic algorithm as in your second example.  It also handles the x = 0 case unlike yours.  

The two examples you posted are different algorithms, so comparing them is just comparing those two specific algorithms - not recursion in general.  I can write an iterative version of your recursive function and it would be just as bad.

---

### Post by Reiger on 2011-03-21
An iterative implementation will not necessarily be faster than a recursive one: consider the case of x^y for integer x and positive integer y. The complexity of this computation using iterative multiplication is O(y). The complexity of this computation using recursion (factoring out terms of x^2 in each step) is O(log(y)):

```

def iter_power(x,y):
  result=1
  count=1
  while y>= count:
    result = result * x
    count = count +1
  return result

def recursive_power(x,y):
  if y == 0:
    return 1
  elif y == 1:
    return x
  elif y == 2:
    return x*x
  else:
    v = y/2
    w = int(v)
    if v > w:
      return x*x*x* recursive_power(x,w)
    else:
      return x*x * recursive_power(x,w)

```

Of course you can convert the recursive code above back into a loop and get equivalent performance, the point is that recursive solutions lend themselves to thinking in terms of such algorithms in the first place.

---

### Post by slavik on 2011-03-21
> **WinstonChurchill said:**
> An iterative implementation will ALWAYS be faster than a recursive one, due to the overhead of repetitive function calls in recursion - although for some things, a recursive implementation will be much easier to conceptualize.

and if you write your code properly (tail recursion), then the compiler can optimize that and then you are not building a stack.

---

### Post by WinstonChurchill on 2011-03-21
> **Simian Man said:**
> 
When compiled with gcc -O3 this code contains no recursive calls

> **Reiger said:**
> 
Of course you can convert the recursive code above back into a loop and get equivalent performance

Okay, I often forget how ridiculously sexy GCC is (It also optimizes the recursion out of Reiger's x^y implementation). But that doesn't change my original point: if the recursion is actually present in the machine code (which it would be, if you take literally what both of you wrote), it cannot be as fast (or as memory-efficient, for that matter) as a non-recursive solution, simply due to the overhead of the function calls. It doesn't seem like it can be a good thing to write intrinsicly slower code with the excuse that the compiler will fix it for us - even neglecting the argument of portability to other compilers that might not do the same, why not just actually write what we want the machine to do? Of course, there are times where that isn't practical (We don't write (x << 1), we write x * 2 and know that the compiler will convert that into a left shift...), but when it comes to the general structure of the implementation of an algorithm, why not do it right?

---

### Post by NovaAesa on 2011-03-22
> **WinstonChurchill said:**
> why not just actually write what we want the machine to do?If we all did that, we would all be writing in assembly or even in pure machine code. There's a reason for higher level languages - they make programming easier. A recursive solution is often much easier to understand than an equivalent iterative solution because of the implicit stack used (the call stack).

---

### Post by Some Penguin on 2011-03-22
And even if one were using a pathetically primitive compiler which didn't implement well-known and widespread optimizations, optimizing for 0.000001% improved machine performance at the cost of a significantly greater penalty in terms of clarity is not a smart trade.  Human time is *much* more expensive than machine time.

---

### Post by slavik on 2011-03-22
> **Some Penguin said:**
> And even if one were using a pathetically primitive compiler which didn't implement well-known and widespread optimizations, optimizing for 0.000001% improved machine performance at the cost of a significantly greater penalty in terms of clarity is not a smart trade.  Human time is *much* more expensive than machine time.
and once PHBs realise this, code stops scaling well.

---

### Post by Simian Man on 2011-03-22
> **WinstonChurchill said:**
> if the recursion is actually present in the machine code (which it would be, if you take literally what both of you wrote), it cannot be as fast (or as memory-efficient, for that matter) as a non-recursive solution, simply due to the overhead of the function calls.

In addition to what others have said, it's also worth noting that some languages, such as Lisp, Ml and Haskell actually guarantee TCO in the language standard.  In those languages you aren't relying on the implementation to do this for you, but the language itself.  Even in C, no decent compiler will fail to optimize the examples given in this thread.

---

### Post by Arndt on 2011-03-22
> **Simian Man said:**
> In addition to what others have said, it's also worth noting that some languages, such as Lisp, Ml and Haskell actually guarantee TCO in the language standard.  In those languages you aren't relying on the implementation to do this for you, but the language itself.  Even in C, no decent compiler will fail to optimize the examples given in this thread.

Another addition: some languages don't have an iteration construct at all, but uses only recursion, like Erlang.

---

### Post by Reiger on 2011-03-22
> **WinstonChurchill said:**
> But that doesn't change my original point: if the recursion is actually present in the machine code (which it would be, if you take literally what both of you wrote), it cannot be as fast (or as memory-efficient, for that matter) as a non-recursive solution, simply due to the overhead of the function calls.
Do you understand big O notation at all? My recursive solution pays off once the cost of iterations is larger than the cost of O(log(y)) function calls. For instance for y = 2^5000, you have (approximately) 2^5000 iterations versus (approximately) 5000 function calls. That changes the picture somewhat.

Now, in theory, the compiler can implement my function calls by shoving things in registers instead of main memory because the variables do not require modification beyond their point of initialisation (there is no destructive update) and this code will run in constant memory, just like the iterative approach. With, incidentally exactly the same number of variables involved (x,y,v,w) versus (x,y, result, count). In practice, my recursive implementation will probably run in O(log(y)) memory cost as well (new variables allocated per function call, with O(log(y)) function calls).

---

### Post by WinstonChurchill on 2011-03-22
> **Reiger said:**
> Do you understand big O notation at all?
Yes, I actually do. You yourself said that an iterative solution equally  as (although in reality it would be slightly more) efficient as the  recursive one could be written: I wasn't saying that the particular  iterative one in your post was more efficient. 

> **slavik said:**
> and once PHBs realise this, code stops scaling well.
Exactly.  I can't help but feel that sacrificing computational efficiency for  code readability is a bad thing. (Even though, yes, in the case of  recursion the compiler is often smart enough to fix our code for us)

---

### Post by Some Penguin on 2011-03-22
Having less readable code in the name of misguided optimization is an excellent way to introduce subtle bugs that make your "faster" code only faster at failing.  This becomes clearer when you've worked on non-tiny projects and not some toy 10000-line program.

Using a linear-time approach instead of a sort or a constant-time lookup vs. a binary search is smart; fussing about iteration vs tail recursion in the name of efficiency is almost always not.  If you're going to avoid non-tail-recursion, do it not because of meaningless alleged gains in speed but to avoid running out of stack space.

---

### Post by Reiger on 2011-03-22
> **WinstonChurchill said:**
> Yes, I actually do. You yourself said that an iterative solution equally  as (although in reality it would be slightly more) efficient as the  recursive one could be written: I wasn't saying that the particular  iterative one in your post was more efficient.

Ah, I see: I took that “if you take literally what both of you wrote” as referring to the code examples rather than the post as whole. My bad.

---

