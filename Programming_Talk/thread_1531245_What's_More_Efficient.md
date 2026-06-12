---
title: "What's More Efficient?"
date: 2010-07-14
forum: Programming Talk
---

### Post by KdotJ on 2010-07-14
Hey people, I'm sure someone will be able to help me out.

Let's say, for scenario sake that I have a program which adds a square to a window repeatedly after every 2 seconds. The square is an instance of an object. Let's say I know that I want 50 instances to be created and added over the time span.

Which is more efficient:

1)
Every 2 seconds, create a new instance of the object and add it to the screen.

2)
Create 50 instances and store them in a vector, then every 2 seconds, take the instance at index 0 and add it to the screen, and remove it from the vector.

I'm asking as I want to know if it more efficient to create all of the instances in one go at at the beginning, rather than creating a new one every 2 seconds during runtime. Or, will the resizing of the vector every 2 seconds cancel out the effect?

Thanks for any help

---

### Post by CptPicard on 2010-07-14
> **KdotJ said:**
> 
I'm asking as I want to know if it more efficient to create all of the instances in one go at at the beginning, rather than creating a new one every 2 seconds during runtime.

You're still creating 50 instances total, so their sum is the same regardless of how you do it. Of course if the creation is so slow that it will slow an animation or something, then you may want to pre-initialize things. It's very hard to tell from such a generic example.

> 
 Or, will the resizing of the vector every 2 seconds cancel out the effect?


Unless you really need the pre-initialization, it seems to me that messing with the vector here is just unnecessary. In particular the vector resizings are going to be, theoretically speaking, the heaviest part of anything you'll be doing (quadratic operation).

---

### Post by KdotJ on 2010-07-14
Thanks for the reply, and apologies for the vague generic example, it's just too long to go into the details of the program. I tested bother versions while watching the CPU and RAM usage while doing nothing else on my machine. The difference was non-existent lol. Thanks again

---

### Post by soltanis on 2010-07-14
You'll only notice the difference if you were trying to create a lot of objects at once (allocating a lot of heap memory). Heap memory allocation is a relatively expensive process, so you try to avoid it in speed critical applications. That being said, once every two seconds is absolutely negligible (the speed difference is on the microseconds level). If you were doing something where you needed to have a load of objects and go through them with some kind of operation in much less than a second (i.e. in a game where you need to render many frames per second) then allocating and storing the objects first would be a better call. Otherwise, you'll never tell the difference.

---

### Post by simeon87 on 2010-07-15
Always do the simplest thing that could possibly work and only optimize when that's not fast enough. If you don't notice any difference, definitely take the simplest option.

---

### Post by slavik on 2010-07-15
> **CptPicard said:**
> You're still creating 50 instances total, so their sum is the same regardless of how you do it. Of course if the creation is so slow that it will slow an animation or something, then you may want to pre-initialize things. It's very hard to tell from such a generic example.



Unless you really need the pre-initialization, it seems to me that messing with the vector here is just unnecessary. In particular the vector resizings are going to be, theoretically speaking, the heaviest part of anything you'll be doing (quadratic operation).
1. Cpt. you know better than to say such things
2. As has been pointed out, this is negligible when creating a new object every 2 seconds. You really need to consider how often malloc() (a system call) may be called. If you can allocate the space for 50 objects at once, it is the same cost as allocating space for 1 object. This is the reason production java application servers are started with Xms (starting heap size) and Xmx (maximum heap size) settings being the same, to cause jvm to call malloc() exactly once at the beginning of the program.

---

### Post by CptPicard on 2010-07-15
> **slavik said:**
> 1. Cpt. you know better than to say such things

Ok, I'll grant your malloc point marginally.

As I knew that there was not going to be any difference here anyway, memory allocation cost was not primarily on my mind :p It may be a vector-of-pointers or vector of object references, and then we're mallocing the vector separately and then new'ing the objects. Mallocing memory also does not initialize yet so we may have the vector, regardless of what it's shape in memory is, but we still have to go through it afterwards... the memory allocation part is a part of the initialization cost, and yes, we may be able to group it but it's not the whole deal.

---

### Post by MadCow108 on 2010-07-15
the generic answer to this generic question is simple:

if the object creation (including allocation, initialization, ...) is very slow compared to the frequency of creation (or desired latency), precreate at some more convinient time and reuse the objects later.

if not choose the easier, more maintainable way.

Discussing memory allocation schemes is a far to low level for this question, in many more complex problems initialization time outweighs allocation time by factors.

Remember:
premature optimization is the root of all evil

---

### Post by CptPicard on 2010-07-15
> **MadCow108 said:**
> 
if the object creation (including allocation, initialization, ...) is very slow compared to the frequency of creation (or desired latency), precreate at some more convinient time and reuse the objects later.


Reuse is the key here. In a case where the object is created at some point and then used once, it does not matter how you group the creation operations. Of course if the alternative is creation-use-destruction cycles and "caching" objects for multiple use, it's a whole different situation.

---

### Post by slavik on 2010-07-15
Sounds like we're on our way of inventing garbage collection ;)

---

