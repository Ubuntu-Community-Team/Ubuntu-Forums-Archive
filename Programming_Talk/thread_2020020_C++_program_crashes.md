---
title: "C++ program crashes"
date: 2012-07-07
forum: Programming Talk
---

### Post by Lymphocyte on 2012-07-07
hi, 
  I am just learning about arrays. I know this isnt real world usage, but how come when i create a variable with 30 million arrays the program crashes? Shouldnt the kernel first go to the swap file before crashing? My laptop has 6GB ram and 12GB swap. Or is this just a c++ limitation?

---

### Post by trent.josephsen on 2012-07-07
That is pretty aggressive in terms of memory usage, and there are usually plenty of ways to avoid using something that large. There are probably options you can pass to the compiler to allow your program to handle such large objects, but that's almost certainly solving the wrong problem.

It's a bit like the fellow who complained, ["Hey! I hate these Microsoft guys! What a rotten compiler! It only accepts 16,384 local variables in a function!"]("http://www.rinkworks.com/stupid/cs_programming.shtml") Limits like that, and like the one you're running into (whatever exactly it may be), aren't often encountered in the wild because smart programmers don't often write programs that exceed them.

tl;dr -- "Well, don't do that then."

---

### Post by snip3r8 on 2012-07-08
I do not mean this in offensive way , but i read your question over three times to make sure i wasnt reading it wrong, 30 million is huge ,  are you talking about using 30 million arrays or putting 30 million elements in an array?

---

### Post by ofnuts on 2012-07-08
> **Lymphocyte said:**
> hi, 
  I am just learning about arrays. I know this isnt real world usage, but how come when i create a variable with 30 million arrays the program crashes? Shouldnt the kernel first go to the swap file before crashing? My laptop has 6GB ram and 12GB swap. Or is this just a c++ limitation?
The program crashed, not the kernel... Care to show us the source?

Btw, the day your computer starts using all that swap, you better find a good book because it's going to crawl.

---

### Post by OM55 on 2012-07-08
> **Lymphocyte said:**
> hi, 
  I am just learning about arrays. I know this isnt real world usage, but how come when i create a variable with 30 million arrays the program crashes? Shouldnt the kernel first go to the swap file before crashing? My laptop has 6GB ram and 12GB swap. Or is this just a c++ limitation?

chances are that your problem is not with Linux and its swap file but with your source code and the way you define and use your array variables. In C++ you have less protection than in C# and it could be that you are overriding a boundary which causes the program to crash.

If you can post the source code (at least all the areas where you define the array and set values to the array) it will be very helpful to help you identify the problem.

I also concur with the previous replies - there are probably much better ways to accomplish the task without using a 30 million item array. although doable, it is extremely inefficient.

---

### Post by ziekfiguur on 2012-07-09
How are you creating that variable? 
If you are allocating it on the stack, your program is going to fail. IIRC swap memory is never used for extra stack space. 
If you did this, you could try allocating it on the heap.

---

### Post by Lymphocyte on 2012-07-10
ok, i am creating it like this. Segmentation fault (core dumped). Now i thought the kernel would go to the swap file instead of seqmentation fualt.


> //test
#include <iostream>
using namespace std;

int main()
{
  cout << "I will now create an array of 3 million elements" << endl;
  
  int crash[3000000];
  return 0;
}

---

### Post by satsujinka on 2012-07-10
> **Lymphocyte said:**
> ok, i am creating it like this. Segmentation fault (core dumped). Now i thought the kernel would go to the swap file instead of seqmentation fualt.
Your array is being created on the stack. There simply isn't that much space... so it crashes. The stack is where your program actually lives, so using it up means your program can't do anything (and trying to fails as you noticed.)

---

### Post by Lymphocyte on 2012-07-10
so if i allocate it on the heap it wont crash then right?

---

### Post by satsujinka on 2012-07-10
Maybe. You can overflow the heap too... In all probability, you'd probably not run into troubles. There are limits to the size of the heap, but you're not going to run into them anytime soon.

---

### Post by trent.josephsen on 2012-07-10
It might not crash if you create it with new, but that's just avoiding the real problem, which is located between your keyboard and chair.

If and when you someday need to handle a very large array, you'll probably be suitably equipped to deal with the consequences at that point. Right now you should focus on learning to program and not get involved in the details of one implementation's built-in limits.

---

### Post by xb12x on 2012-07-10
> **trent.josephsen said:**
> It might not crash if you create it with new, but that's just avoiding the real problem, which is located between your keyboard and chair.

If and when you someday need to handle a very large array, you'll probably be suitably equipped to deal with the consequences at that point. Right now you should focus on learning to program and not get involved in the details of one implementation's built-in limits.

You probably didn't mean to sound harsh, but your answer could be construed as a little off the mark, don't you think?

Lymphocyte asked why his code didn't work and others with more experience pointed out his attempted use of the stack.

---

### Post by trent.josephsen on 2012-07-10
Harsh, yes. Off the mark, no.

It's true that the (most likely) immediate cause of the problem is trying to create a data structure larger than the stack can hold. But that's an implementation detail that programmers shouldn't have to worry about under normal circumstances. It's really irrelevant because *practically*, the solution is to not depend on very large data structures.

It's a bit like debating whether to use an int or a float to store some numeric amount. *Yes*, there are built-in limits that constrain what you can do with those types. But when a new programmer asks "Should I use an int or a float to store amounts of money?" the best response *isn't* "Well, the maximum value of an int is 2147483647, and..." The best response is "What makes sense?"

Let's not confuse *giving information* with *teaching*.

---

### Post by 11jmb on 2012-07-10
> **trent.josephsen said:**
> But when a new programmer asks "Should I use an int or a float to store amounts of money?" the best response *isn't* "Well, the maximum value of an int is 2147483647, and..." The best response is "What makes sense?"


*Obviously* the answer is to use integers because fixed-point arithmetic is usually faster than floating-point. Beginners should always remember to optimize first, and think later :P

On a more serious note, I understand your intent, but I'd hate to see a beginner leave this community because they mistook your teaching for an insult.

---

### Post by trent.josephsen on 2012-07-10
I take your point and I will moderate my vitriol in the future. :) OP, I apologize for the offensiveness in my tone.

---

### Post by SirWhy on 2012-07-10
I had to comment on this..... 30 million elements? Damn, that's a lot of memory usage. I'm interested in knowing why you needed that many. When I learned about arrays it was to display my name or similar. 

I also concur with allocating it onto the heap but even then.... 30 million....

---

### Post by the_unforgiven on 2012-07-11
> **SirWhy said:**
> I had to comment on this..... 30 million elements? Damn, that's a lot of memory usage. I'm interested in knowing why you needed that many. When I learned about arrays it was to display my name or similar. 

I also concur with allocating it onto the heap but even then.... 30 million....

30M may SOUND a lot, but in terms of memory usage, it entirely depends on **what** is it that's being stored.

For example, 30M of long longs (8bytes) amounts to only 240MBytes of memory - which is not all that much considering the address space of a typical process on 32-bit platform is 4GBytes. You could easily accommodate 240MBytes on heap. 

I'm sure there are use-cases that gobble up memory in GBs at a time :) - like CAD apps or video editors or even some games.

---

### Post by 11jmb on 2012-07-11
As has been pointed out before, OP's superficial mistake was declaring a large sequential array on the stack, but I can't think of a solution where using 30e6 element array is useful. Of course a large, complex program might command larger amounts of memory, but the point that people on this thread have made is that declaring a such a large array is probably a poor way to solve any problem

---

### Post by Lymphocyte on 2012-07-11
i wasnt insulted, it was probably a dumb question outside of real world usage. I was just wondering why the program crashed

---

### Post by |{urse on 2012-07-11
I see a lot of people being snobby, sure, it's not good practice to  create an array that large but that's how people learn new things. Telling OP the problem exists between the keyboard and chair only shows your arrogance, not OP's ignorance. I will lmao when he/she invents a new method for memory management and you look like a simpleton.

---

### Post by SirWhy on 2012-07-11
> **the_unforgiven said:**
> 30M may SOUND a lot, but in terms of memory usage, it entirely depends on **what** is it that's being stored.

For example, 30M of long longs (8bytes) amounts to only 240MBytes of memory - which is not all that much considering the address space of a typical process on 32-bit platform is 4GBytes. You could easily accommodate 240MBytes on heap. 


Good point, even then, 30 million is a lot of elements. I really just wondered why the OP needed so many. By the sounds of it they were just testing the limitations of their computer/code. 

You see 30M and immediately think that's a lot of space needed.... But what you say is completely true. It would be fine on the heap (not the stack like our OP allocated it to)

---

### Post by ofnuts on 2012-07-13
> **11jmb said:**
> As has been pointed out before, OP's superficial mistake was declaring a large sequential array on the stack, but I can't think of a solution where using 30e6 element array is useful.
A 12Mpx picture in memory is 36Mbytes (at 8bit/Channel). 30MB is also about 3 minutes of a 16-bit stereo sound sampled at 44KHz.

---

### Post by trent.josephsen on 2012-07-13
I've never stored a 12 megapixel image as a multi-million-element array. I've never stored a sound as a multi-million-element array, either. I *can* think of instances where I might find it useful to do so, but those uses are *not typical*.

---

### Post by compiz addict on 2012-07-13
An array of 30,000,000 integers is 120000000 bytes and thus 114.4 MB. That is pretty large for most computational tasks, but if you were coding some sort of graphics library and needed to store large arrays, I don't see why 144.4 MB should cause a program to crash... then again, I'm a little ignorant to the internal workings of these things...

---

### Post by compiz addict on 2012-07-13
Wait... did anybody mention pointers?

when you declare an array like:
int asdf[30000000];
you're limited by the size defined by your compile.
If you use a pointer like:
int *asdf=new int[30000000];
then your limited only by the OS (and of course the actual amount of RAM you have), which usually gives your process 2-4GB.

EDIT: It seems Sir Why and The Unforgiven both did without specifically mentioning pointers, but that's the difference between declaring something on the stack and the heap.

---

### Post by ofnuts on 2012-07-13
> **compiz addict said:**
> Wait... did anybody mention pointers?

when you declare an array like:
int asdf[30000000];
you're limited by the size defined by your compile.
If you use a pointer like:
int *asdf=new int[30000000];
then your limited only by the OS (and of course the actual amount of RAM you have), which usually gives your process 2-4GB.

EDIT: It seems Sir Why and The Unforgiven both did without specifically mentioning pointers, but that's the difference between declaring something on the stack and the heap.
Not to be pedantic but pointers <> heap_allocation...

---

