---
title: "a lot lot queries about c++"
date: 2011-07-06
forum: Programming Talk
---

### Post by ddimit on 2011-07-06
1: ```
cout << setiosflags(ios::fixed)<<1000000000000.0 << endl;
``` if we skip  setiosflags(ios::fixed) what will it happen

2: does ```
ValueSum += Value;
``` means ```
ValueSum=ValueSum+Value
```3: in our univercity they do not allow us to use math.h library so how can i find the floor of a float number

4: ```
void PrintChar(char c = '=', int n = 80)
``` if we call the above function from main with these 4 options what will happen```
PrintChar('*', 20); PrintChar('-'); PrintChar(); PrintChar(20);
```5: whats the different when we externally declare variables and how can we change them from different locations

6: i cannot understand about the new option i think it somehow bind memory blocks? is it an array or something? when do we have to unbind it? if we dont what will it happen

7: im unable to understand what substr is and how can we use it, also i cannot understand what getline() is 

thanks in advance

---

### Post by nvteighen on 2011-07-06
These are a lot of questions, indeed. Some of them smell like homework, so I won't solve them; just give you some hints.

> **ddimit said:**
> 1: ```
cout << setiosflags(ios::fixed)<<1000000000000.0 << endl;
``` if we skip  setiosflags(ios::fixed) what will it happen


Check it out for yourself, as it's the best/only way to really learn programming. Be curious and get your hands dirty!

> 
2: does ```
ValueSum += Value;
``` means ```
ValueSum=ValueSum+Value
```


Again, check this out for yourself.

> 
3: in our univercity they do not allow us to use math.h library so how can i find the floor of a float number


I can think two reasons of why they don't allow you to use math.h, one very senseful and the one very idiotic:

1) math.h is actually a C header, not C++ and your teacher wants you to learn the right thing. The C++ header is math (without ".h"):

```

#include <math>

```

I hope this is the reason.

2) The teacher thinks you should implement everything, even the standard math functions. That only leads people to ignore the contents of the standard library and lose time in their projects.

Now, about implementing floor. Think about what floor means: it strips the fractional part of a real number and returns its integer part. So you could go by this: find the fractional part and substract it from the original number. Then you have to force that to be an integer.

> 
4: ```
void PrintChar(char c = '=', int n = 80)
``` if we call the above function from main with these 4 options what will happen```
PrintChar('*', 20); PrintChar('-'); PrintChar(); PrintChar(20);
```


Without knowing what PrintChar is defined to do, I can't advance what would happen.

> 
5: whats the different when we externally declare variables and how can we change them from different locations


I barely understand your question. But an externally declared variable is a global variable that you define in some module A and by marking it as 'extern', you can use it in module B.

> 
6: i cannot understand about the new option i think it somehow bind memory blocks? is it an array or something? when do we have to unbind it? if we dont what will it happen


No, it's actually easier. 

When you declare a variable or object in C++ like this:
```

type my_var;

```

it means that you know all the information to create my_var at compile-time. But if you were relying on some user input or some information only available at runtime, you would have to use the new operator. 

But the program actually doesn't know what memory has been allocated by new, so you have to use the delete operator to free that memory, otherwise that memory is lost or "leaked". Ok, modern OSs will free everything when the program is shut down, but in the case of a daemon or long-running program, memory leaks can become a serious issue... So you better always free the memory yourself.

> 
7: im unable to understand what substr is and how can we use it, also i cannot understand what getline() is 


For string::substr, look here [http://www.cplusplus.com/reference/string/string/substr/](http://www.cplusplus.com/reference/string/string/substr/)

getline is a GNU C extension. It allows you to read a line from input and store it somewhere... There's nothing arcane about it, really.

---

### Post by Zugzwang on 2011-07-06
> **nvteighen said:**
> getline is a GNU C extension. It allows you to read a line from input and store it somewhere... There's nothing arcane about it, really.

A short comment on your post: I think that the OP referred to [this getline]("http://www.cplusplus.com/reference/string/getline/"), and not the GNU getline library. :)

---

### Post by nvteighen on 2011-07-06
> **Zugzwang said:**
> A short comment on your post: I think that the OP referred to [this getline]("http://www.cplusplus.com/reference/string/getline/"), and not the GNU getline library. :)

Oh, ok. I'm much more familiar with C than with C++ and didn't know there was that string::getline method.

---

### Post by dwhitney67 on 2011-07-06
> **nvteighen said:**
> 
1) math.h is actually a C header, not C++ and your teacher wants you to learn the right thing. The C++ header is math (without ".h"):

```

#include <math>

```

Actually, it is <cmath>, not <math>.  ;)

---

### Post by Fatman_UK on 2011-07-06
> **ddimit said:**
> 
2: does ```
ValueSum += Value;
``` means ```
ValueSum=ValueSum+Value
```


No. Forget what we know about math symbols for a moment. Let us replace "ValueSum" with "a" and "Value" with "b", to save my fingers. :) 

```
a += b;
```

is (usually) shorthand for

```
a.operator+=(b);
```

You see we are calling the operator+=() member function of object a with object b as a parameter.

```
a = a + b;
```

is (usually) shorthand for

```

a.operator=(a.operator+(b));

```

We have here two function calls. First, we call the operator+() member function of object a with object b as a parameter. Then the output of that is passed into the operator=() member function of object a.

So you see, the second form is quite a bit different from the first.

This explanation is not all there is to it. I've tried to keep it simple. Google "c++ faq lite" if you want to [s]be scared away from C++ forever[/s] learn C++ properly.

---

### Post by Arndt on 2011-07-06
> **Fatman_UK said:**
> No. Forget what we know about math symbols for a moment. Let us replace "ValueSum" with "a" and "Value" with "b", to save my fingers. :) 

```
a += b;
```

is (usually) shorthand for

```
a.operator+=(b);
```

You see we are calling the operator+=() member function of object a with object b as a parameter.

```
a = a + b;
```

is (usually) shorthand for

```

a.operator=(a.operator+(b));

```

We have here two function calls. First, we call the operator+() member function of object a with object b as a parameter. Then the output of that is passed into the operator=() member function of object a.

So you see, the second form is quite a bit different from the first.

This explanation is not all there is to it. I've tried to keep it simple. Google "c++ faq lite" if you want to [s]be scared away from C++ forever[/s] learn C++ properly.

What would you do with a programmer who defined operator+=, operator+ and operator= so that the equivalence in the original question doesn't hold?

---

### Post by Fatman_UK on 2011-07-06
> **Arndt said:**
> 
What would you do with a programmer who defined operator+=, operator+ and operator= so that the equivalence in the original question doesn't hold?


Possibly nothing. It depends entirely on context. The meaning of the operators can be anything or nothing.

For example, take operator/(). What does this snippet mean?

```

a = a / b;

```

In the context of mathematical classes, we might expect it to mean "assign to number a the value of number a divided by number b". But when used in the context of the third-party library Boost.Filesystem, it means "assign to path a the result of appending path b to path a".

> **nvteighen said:**
> 
No, it's actually easier. ... So you better always free the memory yourself.


Good information, but from a sysadmin's point of view. It looks to me like the OP is asking for help on pointers and memory allocation. It's quite arcane and the subject of many lectures, but actually rather simple when you grok it.

Long explanation follows... apologies... I've tried to keep it simple.

First, you need to know that our program has two places to store its data: the "stack" and the "heap". I'll probably get those two names the wrong way round, so I won't mention them again, but you need to have heard of them.

Anyway, the smaller lump of memory can be accessed directly by our program, so we can do this:

```
char c = '$';
```

We can throw 'c' around as much as we like now. The program will do all the housekeeping; we don't need to lift a finger.

Soon, you will find you need a better way to handle memory. You might need large amounts of it, for instance.

So, the other way is to ask the operating system for some memory. Don't worry; what you ask for, you'll usually get. *But you do have to give it back.* That's the key to leak-free code.

```

char *c = new char;

```

Let's analyse this line. We are declaring "char *" rather than a char, and assigning it the value of "new char".

There are two parts to understand here: the pointer and the "new" keyword. You have already met char, I hope. The asterisk (*) means "pointer". So "char *" means "pointer-to-char".

The new keyword asks the operating system for some memory. In this case ("new char"), we are asking for enough memory to hold a char. The new keyword tells us where the memory is: its address. We put the address in the pointer-to-char.

See? We don't use the memory directly, but we know where it lives. The pointer points at the memory's address.

Here, let's go over it again with diagrams. Check out these numbered boxes. Let's pretend they represent our computer's memory. Our computer has 10 bytes of memory.

```

 0  1  2  3  4  5  6  7  8  9
[ ][ ][ ][ ][ ][ ][ ][ ][ ][ ]

```

First, we ask the operating system for enough memory for one char ("new char"). Let's put it in memory location 9:

```

                           char
                            |
                            v
 0  1  2  3  4  5  6  7  8  9
[ ][ ][ ][ ][ ][ ][ ][ ][ ][ ]

```

It's just marked as char.

Next, we've declared a char*, so let's put that in memory location 0:

```

char*                      char
 |                          |
 v                          v
 0  1  2  3  4  5  6  7  8  9
[ ][ ][ ][ ][ ][ ][ ][ ][ ][ ]

```

You see we've marked memory location 0 as char*.

Finally for this line, we assign the char* to contain the address of the char. (That's the "=".) So:

```

char*                      char
 |                          |
 v                          v
 0  1  2  3  4  5  6  7  8  9
[9][ ][ ][ ][ ][ ][ ][ ][ ][ ]
 |                          A
 +--------------------------+

```

See? Now, because memory location 0 contains the address 9, it "points" at our newly allocated memory. That's the first line dealt with.

Now we have a pointer to some memory, we can do something with it, like:

```

c[0] = '$';

```

That will put the '$' symbol in the first memory location after c - in our example, memory location 9.

```

char*                      char
 |                          |
 v                          v
 0  1  2  3  4  5  6  7  8  9
[9][ ][ ][ ][ ][ ][ ][ ][ ][$]
 |                          A
 +--------------------------+

```

Now, let's suppose we've had a lot of fun with our '$' and it's time to close the program. What now? We have to give back the memory.

```

delete c;

```

The "delete" keyword deallocates our borrowed memory. The operating system is now happy. Do not use the pointer-to-char afterwards:

```

char*
 |
 v
 0  1  2  3  4  5  6  7  8  9
[9][ ][ ][ ][ ][ ][ ][ ][ ][ ]
 |                          A
 +--------------------------+

```

Because now it points to nothing, and you will get errors if you try and use it.

Always pair a new with a delete! If you don't, the memory is never released back into the operating system. This is called a memory leak. Leak enough memory and eventually you **will** crash your operating system. So get into good habits early.

---

### Post by Arndt on 2011-07-06
> **Fatman_UK said:**
> Possibly nothing. It depends entirely on context. The meaning of the operators can be anything or nothing.

For example, take operator/(). What does this snippet mean?

```

a = a / b;

```

In the context of mathematical classes, we might expect it to mean "assign to number a the value of number a divided by number b". But when used in the context of the third-party library Boost.Filesystem, it means "assign to path a the result of appending path b to path a".


Fine, so what does a /= b do?

> 
Always pair a new with a delete! If you don't, the memory is never released back into the operating system. This is called a memory leak. Leak enough memory and eventually you **will** crash your operating system.

Maybe if the operating system is called Windows.

---

### Post by Fatman_UK on 2011-07-06
> **Arndt said:**
> Fine, so what does a /= b do?

In fact, in the case of Boost.Filesystem, the equivalence between operator/() and operator/=() holds. It does what you would expect: assign to a the result of appending path b to path a. So my example isn't good.

I guess you need a class where / and = cause a side effect when brought together. How about:

```

RoadMap a;
RoadMap b;
...
a = a / b; // connect roadmap a to roadmap b by a *foot* bridge
a /= b; // connect roadmap a to roadmap b by a *canal* bridge

```

A very contrived, badly designed example. I'll try and think of a better one tomorrow, it's quite late.

> **Arndt said:**
> Maybe if the operating system is called Windows.

Ha! I wouldn't know; I can't keep my build environment sane under Windows 7 x64 long enough to find out. :P

Really, I must start cross-compiling.

---

### Post by cgroza on 2011-07-06
> **Fatman_UK said:**
> 

Always pair a new with a delete! If you don't, the memory is never released back into the operating system. This is called a memory leak. Leak enough memory and eventually you **will** crash your operating system. So get into good habits early.
The operating system always takes back the memory at the exit of the program. It is true that leaking too much will make your program slow and eventually do the same to the OS, but:
```

int main(int argc, char** args)
{
    while(true)
    {
     new int[1000];
    }
}

```It will run for some time, fill up the memory, but it will get killed by the operating system and everything will be back to normal. I have made this experiment on my system.

After abut 5 min, it took 98% of memory and some hundreds of megs of swap, and then the kernel killed it and the memory consumption came back to normal.

---

### Post by Fatman_UK on 2011-07-07
> **cgroza said:**
> It will run for some time, fill up the memory, but it will get killed by the operating system and everything will be back to normal. I have made this experiment on my system.

After abut 5 min, it took 98% of memory and some hundreds of megs of swap, and then the kernel killed it and the memory consumption came back to normal.

That's pretty cool. The kernel protects itself. That makes sense for a modern OS. So you wouldn't crash the kernel, but you would cause the kernel to crash your program instead. Still less than ideal for most purposes.

---

### Post by Arndt on 2011-07-07
> **cgroza said:**
> The operating system always takes back the memory at the exit of the program. It is true that leaking too much will make your program slow and eventually do the same to the OS, but:
```

int main(int argc, char** args)
{
    while(true)
    {
     new int[1000];
    }
}

```It will run for some time, fill up the memory, but it will get killed by the operating system and everything will be back to normal. I have made this experiment on my system.

After abut 5 min, it took 98% of memory and some hundreds of megs of swap, and then the kernel killed it and the memory consumption came back to normal.

Actually, if memory runs out, the Linux kernel will select one memory-intensive process and kill it, it need not be the actual culprit. This thing has a name, but I forget it, and maybe it can be turned off. It may happen that firefox is the one shot down instead, or the window manager. So it is true that one program can crash other programs.

---

### Post by Fatman_UK on 2011-07-07
> **Arndt said:**
> Actually, if memory runs out, the Linux kernel will select one memory-intensive process and kill it, it need not be the actual culprit. This thing has a name, but I forget it, and maybe it can be turned off. It may happen that firefox is the one shot down instead, or the window manager. So it is true that one program can crash other programs.

All very interesting. Anyway, to get back on topic, we all agree that memory leaking is a Very Bad Thing and should be avoided. Yes?

---

### Post by nvteighen on 2011-07-07
> **dwhitney67 said:**
> Actually, it is <cmath>, not <math>.  ;)

Yeah, my mistake. But why doesn't C++ have its own math header?

---

### Post by Fatman_UK on 2011-07-07
> **nvteighen said:**
> Yeah, my mistake. But why doesn't C++ have its own math header?

The C math header works well enough that there's no point writing a new one just to call it "C++'s own math header".

Maybe the new C++ standards (TR1/C++0x, and the newer C++1x) have some higher math modules. I haven't checked.

[EDIT]

C++0x includes some modifications to cmath. Wikipedia mentions beta functions, Legendre polynomials, elliptic integrals, and so on. TR2 doesn't seem to exist yet, so it's hard to speculate on its contents.

Of course, WP is not considered the most reliable source. ;)

---

