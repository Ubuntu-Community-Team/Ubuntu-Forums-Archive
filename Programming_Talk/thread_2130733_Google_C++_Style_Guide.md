---
title: "Google C++ Style Guide"
date: 2013-03-30
forum: Programming Talk
---

### Post by bird1500 on 2013-03-30
Hi,
In the section about "[Use of const]("http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml#Use_of_const")", they say in the "Pros" section:
> Helps people know what functions are safe to use         without locks in multi-threaded programs.

But afaik it's not right. Sample:
```

bool
MyClass::classChanged() const { //THIS CONST
       return myClassChanged;
}

```

Afaik before calling this function/method you still have to lock the corresponding mutex (for the myClassChanged variable) to make sure the value of "myClassChanged" is up to date, that is, that it isn't cached and hasn't been updated in between by some other thread for example thru a setter method call.
Or am I missing something?

---

### Post by trent.josephsen on 2013-03-30
Disclaimer: I am not a C++ programmer so I could be going off on an irrelevant tangent here. The quality of this post is contingent on my understanding of your question, which I have chosen to interpret as not C++ specific.
> **bird1500 said:**
> Afaik before calling this function/method you still have to lock the corresponding mutex (for the myClassChanged variable) to make sure the value of "myClassChanged" is up to date, that is, that it isn't cached and hasn't been updated in between by some other thread

Yes, if you were doing something that required myClassChanged to remain unchanged until you were done, you would need to get a lock on the resource before you called the accessor, and not release it until you were finished. But locks don't ensure your information is up to date, *per se*; locks (properly used) just ensure that your program won't accidentally enter an invalid state, like trying to send two packets of data across the same wire at the same time. Locks enforce consistency, not timeliness.

Say you want to monitor myClassChanged and when it becomes true, open a dialog box or something to alert the user, but allow the main thread to continue operating. You might write a thread that polls classChanged() every 200 ms or so. You could do that without locking the resource, because you know since classChanged() says `const', it's not going to try to modify stuff behind your back. If you didn't have that `const', you couldn't be sure classChanged() might not try to change something in conflict with what the main thread was doing at the time.

"But wait!" you say. "What if classChanged() tries to access the variable at the same time some other thread writes to it?" Well, so what? One of the threads will "win". If it's the writing thread that wins, then classChanged() will return the new value, and everything is peachy. If it's the other thread, then classChanged() will return the old value... in which case you just come back 200 ms later and check it again. The worst case scenario is that the dialog box takes 1/5 second longer than necessary to appear.

Hope this makes it clearer. `const' can't make a necessary lock go away, but it can sometimes tell you if one is not necessary.

---

### Post by bird1500 on 2013-03-30
> **trent.josephsen said:**
> Disclaimer: I am not a C++ programmer so I could be going off on an irrelevant tangent here. The quality of this post is contingent on my understanding of your question, which I have chosen to interpret as not C++ specific.


Yes, if you were doing something that required myClassChanged to remain unchanged until you were done, you would need to get a lock on the resource before you called the accessor, and not release it until you were finished. But locks don't ensure your information is up to date, *per se*; locks (properly used) just ensure that your program won't accidentally enter an invalid state, like trying to send two packets of data across the same wire at the same time. Locks enforce consistency, not timeliness.

No, properly used locks (mutexes):
When writing, ensure serial (in turn) access (write) to a resource (variable), and since it's "in turn" it means no other resource is writing to it, the update is also committed past the (CPU) cache (typically to RAM).
When reading, it means the local (CPU) cache of the resource is basically discarded (by using a technique called "barriers") and it reads the resource from the original source, typically from the RAM, while not allowing other threads to read/write to it (if they properly use mutexes, if not, the result is undefined/unpredictable).

> **trent.josephsen said:**
> 
Say you want to monitor myClassChanged and when it becomes true, open a dialog box or something to alert the user, but allow the main thread to continue operating. You might write a thread that polls classChanged() every 200 ms or so. You could do that without locking the resource, because you know since classChanged() says `const', it's not going to try to modify stuff behind your back. If you didn't have that `const', you couldn't be sure classChanged() might not try to change something in conflict with what the main thread was doing at the time.

No, the method/resource without a mutex lock can be cached in the CPU's cache for an undetermined amount of time and read from there, and in between other thread might write to the RAM (the original source of the resource/variable) while the "main thread" might keep reading from the cache of the CPU core it's running on.

> **trent.josephsen said:**
> 
"But wait!" you say. "What if classChanged() tries to access the variable at the same time some other thread writes to it?" Well, so what? One of the threads will "win". If it's the writing thread that wins, then classChanged() will return the new value, and everything is peachy...
No way, please read a book on (p)threads, I'd recommend "Programming with POSIX threads", it's old but still applies.
In short, if the threads don't use mutexes both threads will win, and it's undefined whose CPU cache will hit the RAM first. Basically the behaviour (that is the result) is undefined.
What you're saying is basically what I was believing **before** I actually read a book on threads.

---

### Post by trent.josephsen on 2013-03-30
> **bird1500 said:**
> In short, if the threads don't use mutexes both threads will win, and it's undefined whose CPU cache will hit the RAM first. Basically the behaviour (that is the result) is undefined.
What you're saying is basically what I was believing **before** I actually read a book on threads.

I think you should reread my post. What I'm saying is that in *some situations*, it really doesn't matter which CPU cache hits RAM first. Furthermore, in such a situation, you can *sometimes* use const-correctness to tell whether you need to apply a lock or not. I disregarded cache only for the sake of illustration; you can add it back without invalidating the point, but I feel no obligation to run through that mental exercise.

---

### Post by bird1500 on 2013-03-30
> **trent.josephsen said:**
> I think you should reread my post. What I'm saying is that in *some situations*, it really doesn't matter which CPU cache hits RAM first.

Of course it matters if you care about predictable behaviour, that's the very point of writing apps that properly (correctly/predictably) deal with threads and shared data - if you don't need it "in some situations" - then sorry, you're writing buggy source code, and the worst part about this approach is that in some cases the app works often correctly and (very) rarely it works wrong - and it might be a nightmare finding out the cause because it's (very) hard to replicate the bug.

> **trent.josephsen said:**
> 
Furthermore, in such a situation, you can *sometimes* use const-correctness to tell whether you need to apply a lock or not.
Here you're just restating that you don't have a correct understanding how threads work and why mutexes/locks exist.

---

### Post by trent.josephsen on 2013-03-30
Ok, let's back up. Disregard my previous posts in their entirety, I was simply trying to construct an example where the outcome of the race wouldn't matter in the long run and perhaps I didn't do a good job. So, bad examples aside, here is what I understand:

1_ Processes are *sometimes* divided into threads.

2_ Threads *sometimes* need to share resources.

3_ Shared resources *sometimes* must be locked.

4_ The decision to lock a resource *sometimes* comes down to whether a particular thread needs to modify it or not.

5_ `const' tells you whether or not a particular function modifies a particular resource.

So given these, I see it as fairly obvious that `const' might sometimes inform your decision *whether or not to lock* a particular shared resource.

Where am I going wrong?

---

### Post by bird1500 on 2013-03-30
1) Yes, not sometimes but always, the "main" function represents the main thread, which is a bit different from other threads, but is still a thread and you can still exit it with pthread_exit() which makes your process look like a zombie, but it will still run if there are other threads running.
2) Yes
3) No, when there's more than 1 thread shared resources must always be locked before being read or written, otherwise you might be reading/writing to the cache of some CPU or CPU core (for CPUs with > 1 cores), which makes shared data management unpredictable.
4) You always need to lock a resource if you're reading or writing to it from another thread - if one doesn't care about bugs or predictability in a multi-threaded environment then one is a bad (threads) programmer and doesn't know properly why mutexes/locks exist.
5) No. First off, a const function can still modify a resource, that's why the word "**mutable**" exists. Secondly, if you don't use a mutex you don't know which version of a resource you're reading from: the (old/outdated) one from your thread's CPU core cache or the  one from the RAM (modified by another thread from another CPU or CPU core), and if you don't know/care which thread when modifies what then you're a bad (threads) programmer.

---

### Post by trent.josephsen on 2013-03-30
10/10 would be trolled again

---

### Post by bird1500 on 2013-03-30
You're free to not know properly how threads and mutexes work, but "10/10 would be trolled again" is not a mature reaction, please don't accuse me of trolling while having a vague/wrong understanding about threads and mutexes, because it's not my problem, it's yours.

---

