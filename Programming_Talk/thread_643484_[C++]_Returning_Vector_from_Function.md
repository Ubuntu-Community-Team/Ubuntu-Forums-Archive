---
title: "[C++] Returning Vector from Function"
date: 2007-12-17
forum: Programming Talk
---

### Post by TreeFinger on 2007-12-17
Hello, I am currently fixing up a program I handed in for homework. Well the semester is over now, this program is from the very last homework. Anyways, I want to work this bug out, but just for myself because I don't think my teacher cares anymore since he already gave grades out.

What I need to know is if I am returning a vector from a function what does it get returned to? An assignment statement ( assigning it to another vector? )?. The program needs to know the values inside this vector and the number of elements that are present in the vector. I know that the vector object ( is that what it is called? ) will be able to tell me how many elements are in the vector.. I guess my question is: How do I get the vector(and contents) from a 'vector<int> function', back to the main function?

---

### Post by yabbadabbadont on 2007-12-17
You would be better off passing back a reference to a vector, rather than a copy of one.  However, you should be able to just assign it to a "vector<int>" variable.  The copy constructor should handle the rest for you.

---

### Post by aks44 on 2007-12-17
```
std::vector<int> foo()
{
  std::vector<int> v;
  /* fill it */
  return v; // (1)
}

void bar()
{
  std::vector<int> v = foo(); // (2)
  v = foo(); // (3)
}
```

What really happens here?

First off, despite the apparent notation line (2) really is a copy constructor, and not a default constructor + assignment. This is mandated by the standard, and that's the reason why I used both examples (2) and (3).


So...
(2) call foo
(1) copy constructor
(back to 2) copy constructor again (ouch!)

(3) call foo
(1) copy constructor
(back to 3) assignment operator, which is *usually* implemented as a copy constructor (ouch again!) + swap

So as you can see, the problem is that returning an object will trigger a copy. Most modern compilers have an optimization called "Return Value Optimization" (RVO for short) which is *most of the time* able to merge the steps (1) and (back to...). But as with any compiler optimization you shouldn't really count on that...


That leaves us with at least one copy, which could easily be avoided:
```
void foo(std::vector<int>& retVal)
{
  std::vector<int> v;
  /* fill it */
  retVal.swap(v); // (1)
}

void bar()
{
  std::vector<int> v; // (2)
  foo(v); // (3)
}
```
Now we're left with:
(2) default constructor, quite lightweight to say the least
(3) call foo
(1) swapping both vectors, again hyper lightweight
(back to 3) nothing more :)



So as yabbadabbadont put it, the best way to pass big objects back from the callee to the caller obviously is to use a reference argument.
Although this doesn't really matter for small datasets, returning vectors or other containers from a function can quickly introduce huge overhead when the dataset grows (since it involves copying the whole dataset at least once).


Which leads me way off topic:
A class supporting copy / assignment should always have a swap() method too...
- the copy constructor just does its job
- the swap method quickly and safely (as in nothrow-guarantee) exchanges the contents of two objects
- the assignment operator is implemented in terms of copy + swap (after checking for self-assignment of course)

This way you end up with an exception-safe assignment operator for almost no effort, and many use cases can be optimized away thanks to the swap() method. It's a win-win... :)

---

### Post by kmiernik on 2011-04-07
Even if this thread is such old I have a comment. I found this googling the internet on exactly this topic it might be still useful to someone else.

Recently I have been toying with passing large vectors (containing around 16*10^6 records of long int). To my surprise the fastest way I found is to return this large vector by value. Passing a reference is a little bit slower, to give you the numbers on my machine it's 0.79 s versus 0.81 s. Seems that complier's RVO (gcc 4.5) in this case does his job better one might think.

---

### Post by uRock on 2011-04-07
Necromancy. Please start a new thread.

Thread Closed

---

