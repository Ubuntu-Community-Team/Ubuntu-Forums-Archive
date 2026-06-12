---
title: "Race Conditions in pthreads"
date: 2010-04-25
forum: Programming Talk
---

### Post by Abhishek4563 on 2010-04-25
I know what race condtions are. I just wanted to ask that if many threads are accessing the same global variables very frequently (or static members of a class) would it result in some performance cost as only one thread would be able to read the value at a given instant versus the condition where every thread has its own copy of the varibales?
Abhishek

---

### Post by PaulM1985 on 2010-04-25
There would be a performance cost against compared to when each thread has its own variable which it is accessing.  

Performance can be increased by applying appropriate synchronization over the critical region.  If you synchronize over a large area of code which is not critical, you will suffer worse performance than if you only synchronize over the smaller critical area.

These performance issues are really something that you have to deal with and accept that software will slow down if there are many simultaneous accesses to the shared resource.

---

### Post by MadCow108 on 2010-04-25
do you write to the data? (as your talking about race conditions)
if yes a copy is fast because you don't need expensive synchronization

if your only reading it depends heavily on the architecture
if every cpu has its own cache (which is not the case in many desktop multicores) it is probably faster when the threads have its own copy
then one can keep the variable in the cache and it may not have to be written back to main memory at all.

When caches are shared it you somehow have to maintain cache coherence which may mean it may goes back to slow main memory from time to time.

The only way to know for sure what is really better is profiling and knowing your machine and compiler very very good.
Is your problem really worth that trouble?

---

### Post by Cracauer on 2010-04-25
> **Abhishek4563 said:**
> I know what race condtions are. I just wanted to ask that if many threads are accessing the same global variables very frequently (or static members of a class) would it result in some performance cost as only one thread would be able to read the value at a given instant versus the condition where every thread has its own copy of the varibales?
Abhishek

If all accesses are read only, no.

Since you have the option of putting it thread-local I presume you don't write into it.

---

### Post by slavik on 2010-04-25
1. threads accessing a global variable will not create copies of it
2. same goes for writing.
3. there won't be any performance loss, since the variable will be on the CPU

Copy on Write happens to forked processes.

---

### Post by Abhishek4563 on 2010-04-26
Apologies for the late reply. The threads are just reading the data. No need for synchronization. I think madcow answered my question that it depends on the architecture, I am just going with a copy of variables for each thread. Also please suggest a good profiling software I think its time I should start profiling.
Thank You all for your replies.

---

### Post by MadCow108 on 2010-04-26
a good choice is often valgrind and its tools:
cachegrind for profiling of the cpu caches
callgrind for function call profiling
helgrind and dtd race condition checkers
this may be enough for your purpose. But its huge overhead may distort certain results, especially when dealing with input output.
A very good tool to display the results is kcachegrind, highly recommended! It can display cachegrind and callgrind results

gprof has relativ low overhead but its needs a special profiling compilation (-pg flag in gcc)

a more sophisticated tool is oprofile.
This can profile the whole machine including the kernel.
But its more complicated and the big drawback is it needs root privileges which are practically never available in many workspaces and clusters :/

if your working on a supercomputer (which I assume as you seem to be wanting to do low level optimizations) ask the responsibles for appropriate tools, they usually have good machine specific software. Maybe even some automatic performance bottleneck analyzers.

---

### Post by Abhishek4563 on 2010-04-28
I dont want start a new thread therefore asking it here
What is meant by the o/ps "real"  "usr" "sys" times of the time command in Linux?
e.g
real    10m37.196s
user    12m14.462s
sys    0m18.005s

I did a basic google search but it did not yield satisfactory answers.
Abhishek

---

### Post by MadCow108 on 2010-04-28
real approximately real total cpu time elapsed
user is the cpu time elapsed in user space per cpu (=> this gets greater than real when you have multiple cpus and threads)
system is the time spent in kernel space (e.g making system calls)

---

### Post by Abhishek4563 on 2010-05-10
I have to do Gaussian Elimination on a sparse bit matrix(C++ in Ubuntu). I am thinking of using 
vector<bool> container .  I think I read that vector has a special implementation for bool and it actually requires 1 bit of storage etc. Is it true what wud be the advantage of using bitsets ? The problem with bitsets is that I ll have to hardcode the size of bitset I want to use. In my case only after reading the input can I decide what would be the size that I need.
Thanx.

---

### Post by MadCow108 on 2010-05-10
vector bool is a template specialization and does use less memory, but at the cost at slightly slower performance as a normal computer has a byte as smallest addressable unit.
So for each access to a bit it must mask the other bits in the byte first.

But this cost might be worth it if your application is heavily memory bound. This requires profiling again.

Note that the vector<bool> specialization will be removed in the next standard as it does not adhere to the STL container interface (because bits are not adressable)
it will be replaced by something called dynamic_bitset I think.
Backwards compatibility will be preserved by some macros I think, you should look that up.

---

### Post by Abhishek4563 on 2010-05-10
[I]So for each access to a bit it must mask the other bits in the byte first.

[/I]I think you are suggesting that for each bit it actually uses a byte, masking other seven while I thought that if I ask for 50 bits it will use 7 bytes(56 bits) as byte is the smallest data structure and mask the extra six bits. Not that it would actually use 50 bytes. Other wise we could simply use char.

---

