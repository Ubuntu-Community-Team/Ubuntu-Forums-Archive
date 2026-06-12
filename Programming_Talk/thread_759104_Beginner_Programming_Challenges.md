---
title: "Beginner Programming Challenges"
date: 2008-04-18
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-04-18
I'm a beginning student in C++ (self-taught, couple months in).

I was wondering if anyone here would be kind enough to post some problems for me to solve using my limited knowledge. Please refrain from directing me towards Project Euler. I know of the source, but would prefer something less math-related.

I just don't want to keep learning without actually using the knowledge I've retained. Below is a (shamefully short) list of all the topics I've covered so far, so you can know how to level my challenges, presuming you have any for me:

- Conditional statements
- Loops
- Functions
- Switch/case
- Structures
- Arrays
- Strings (and string functions)

I also know quite a bit about pointers, but don't feel comfortable using them yet.


I know this might be to generous of a request to fulfil, but if you can't come up with any exercises on your own (or simply don't want to), could you at least give me some good links to programming exercises?

Thank you very much. I get on everyday after school and read these forums, and I spend the majority of my time right here in the programming section. You're all a great bunch of people. I can't wait until I know enough to participate in the challenges. They sound like so much fun!

---

### Post by LaRoza on 2008-04-18
You might want to cover the rest of C++ first. 

You didn't list classes (and OO in general). Any use of C++ without them is difficult.

---

### Post by pmasiar on 2008-04-18
I don't think that it is impossible to program C++ without OO - it will be not idiomatic code, but so what. Of course, you will be gaining bad habits which you will need to unlearn later, using idiomatic C++ code, but certainly you can do some coding without OO.

Try these simple tasks: [http://learnpydia.pbwiki.com/TasksBeginners](http://learnpydia.pbwiki.com/TasksBeginners)

---

### Post by Sinkingships7 on 2008-04-18
Well, of course I still plan on learning more. I just wanted to stop and apply what I've learned so far.

---

### Post by LaRoza on 2008-04-18
> **pmasiar said:**
> I don't think that it is impossiblr to program C++ without OO - it will be not idiomatic code, but so what. Of course, you will be gaining bad habits which you will need to unlearn later, using idiomatic C++ code, but certainly you can do some coding without OO.

Try these simple tasks: [http://learnpydia.pbwiki.com/TasksBeginners](http://learnpydia.pbwiki.com/TasksBeginners)

True. You'd end up using all the C headers though, as the C++ standard library is full of objects.

```

#include <cstdio>

int main(void)
{
    printf("Hello world\n");
    return 0;
}

```

---

### Post by Joeb454 on 2008-04-18
Thanks **pmasiar** I'm going to try doing the Battleships one now :)

Only difference is I'll be doing it in plain old C :) I might even post the source code up when I'm done if you like? :lolflag: OSS ftw ;)

---

### Post by pmasiar on 2008-04-18
Another option might be to learn Python "on the side" first. If you know basics of C/C++, difference will be rather trivial (you can learn basic Python syntax over one weekend, max). Solving problems will be simpler in Python (it is easier to build rather sophisticated data structures in Python than in C++). You can also learn OOP in Python easier, then go back to C++ and learn OOP the hard way. :-)

IMHO it will be more useful that way, because you will be able to solve (trivial homework) problems sooner, and as bonus you will learn two slightly different languages (and both useful) so you will see which part is semantic of the problem (real inherent problem) and which part is difference in syntax sugar between languages. Very useful difference to know. :-)

---

### Post by Joeb454 on 2008-04-18
Well so far, I'm struggling with it....though it was 2am when I started...it's now 4am and I'm going to bed.

I might try it in python, though I've _*never*_ written anything in python before :p

---

### Post by pmasiar on 2008-04-18
Well, you never should start new code at 2am (although I did my share of late night debugging, but it was because  at those times, I could get mainframe time only during the night :-) ). It is well known fact in psychology (an one more reason to get good well-rounded college education) that around 3am, human brain circadian cycle works the worst of all 24 hours. Best thing to do is to go sleep, so next morning you are fresh.

---

### Post by LaRoza on 2008-04-18
> **pmasiar said:**
> Well, you never should start new code at 2am (although I did my share of late night debugging, but it was because  at those times, I could get mainframe time only during the night :-) ). It is well known fact in psychology (an one more reason to get good well-rounded college education) that around 3am, human brain circadian cycle works the worst of all 24 hours. Best thing to do is to go sleep, so next morning you are fresh.

I agree. No matter how good an idea seems, I will refrain from coding when I am sleep deprived.

I have had awoken to some nasty code and didn't recognize it as my own at first. The things I thought about the stupid writer of that code shocked even me (and I was most displeased when I realized it was me)

---

### Post by Wybiral on 2008-04-18
Really? Some of my best code has come from those hours. But I have a pretty skewed sleeping schedule, so maybe it's just normal for me.

---

### Post by LaRoza on 2008-04-18
> **Wybiral said:**
> Really? Some of my best code has come from those hours. But I have a pretty skewed sleeping schedule, so maybe it's just normal for me.

Then pick a time about 4 hours after you should have gone to bed (weird hours seems to be a coder thing).

---

### Post by pmasiar on 2008-04-19
There is old programmers joke about young son coming to dad, struggling with code, bloody eyes etc, and asking: "Dad, why sun comes up every morning?". He notes to himself: "Really, it's morning, sun is up" and then answers son: "Don't change anythig! For god's sake, don't change anything!" :-)

Obviously, this joke was before GPLed CVS, cannot happen now, can it? :twisted:

I originally expected LaRoza coming to defense of late-night hacking :-) but obviously in just about a year, you become more mature and experienced hacker than I realized. Keep good hacking!

---

### Post by Sinkingships7 on 2008-06-24
I'm resurrecting my old thread to re-request challenges, should anyone have any in mind.

It has been 2 months since I started this thread. If you go back to my original post, you'll see what I knew then. Ever since, my knowledge has expanded (what I believe to be) greatly. At least for 2 months ;)

Here's a list of what I've currently covered (C/C++):

- All the obvious basics + what was mentioned before
- Loops
- Functions
- Pointers
- Enumeration & Typedef
- Structures
- Data files (mostly sequential concepts)
- Object Oriented Programming (classes (using and creating), reusability,
  containment, and inheritance)
- Strings 
- Arrays
- Templates
- Vectors
- Multi-Dimensional arrays
- Matrices (same as above, I know)
- Linked lists (single, double, circle, double-circle)
- Stacks
- Queues
- Binary trees
- Recursion
- Binary and sequential searching
- Searching binary trees
- Hashing (basics)
- Sorting algorithms ("incremental" and "divide & conquer")

This is mostly just a thank you post. The people in this forum have helped me quite a few times to get where I am, and I appreciate everyone's input. You've all been absolutely amazing.

---

### Post by hessiess on 2008-06-24
if you havent alredy, try a simple 2D/3D game. Thay use alot of vector matamatics, matrices and the like. You would need to learn a graphics libary like OpenGL(3D), or SDL(2D).

---

