---
title: "Why Linux has an &quot;OOM killer&quot; and..."
date: 2007-11-19
forum: Recurring Discussions
---

### Post by j_g on 2007-11-19
This thread is about **Why Linux has an "OOM killer" and what programmers can do to help get rid of it**. If someone thinks it's about something else, he's wrong.

I'm going to try to explain this for the layman. That's what I like to do. If anyone thinks that the explanation sounds too simplistic, or omits lots of technical details, so be it. I just want it to be understandable to people who may not ordinarily be able to follow a discussion like this.

Linux has what some people have dubbed "an OOM Killer". The "OOM" stands for "Out Of Memory". What is Linux's "OOM Killer"? It's part of the Linux operating system that springs into action when there's a really bad problem with some app trying to allocate/use memory. The bad problem is that there isn't enough free memory to satisfy how much memory the app now wants to allocate/use. And all the swap space on your hard drive has also been already filled up with previously swapped-out stuff. So, the operating system can't even free up some RAM by moving stuff out of RAM and into the swap space (usually called "virtual memory") on your hard drive.

In short, your system is completely out of free RAM, as well as free swap space. It's all used up... but now some app wants more RAM.

So, the Linux operating system (OOM Killer) selects some software currently running on your system, and abruptly terminates it, hoping that this will free up some RAM. There are a bunch of "rules" that the OOM Killer uses to pick which software is going to get killed. But it doesn't ask you, the enduser, which software you would like killed. (Nor does it tell you that the system is low on memory, and give you a chance to try some things yourself to free up RAM. For example, maybe you'd close some unneeded windows, or choose which software programs to terminate, or disconnect USB devices to see if that frees up RAM, or stop services/daemons to see if that frees up RAM, etc). No, Linux makes the choice for you, and that's that. Maybe it terminates a running copy of Open Office with a currently unsaved document you've been working on for the past two hours. Maybe. You never know. Obviously, it's a bad thing that the OS never gives you an opportunity to try and recover some RAM yourself, but instead terminates some software and makes the choice of which software for you. (P.S. Windows doesn't do this. Some other Unix derivatives, such as Solaris, don't either. I don't think the BSD's do. Not sure. Oh, and Mac OS is like Windows. Warns you about low memory, and lets you take action).

Why in hell does Linux do this? Well, we need to learn about some other aspects of Linux.

There is a function named fork(). It allows a program to essentially make another running copy of itself, except the new copy doesn't start back at main() -- it starts after the call to fork() which is usually some bit of code that only the second copy is meant to do. Sometimes, programmers make that second bit of code do something trivial, which shouldn't require a lot of memory, nor copies of all the global variables/data in the program. Nevertheless, Linux makes copies of all those global variables/data, just in case the second bit of code may use them. Linux doesn't know whether the code will or won't. But fork() is designed so that the bit of code _may_ do that... so it must be supported. So, if the program has, for example:

```
char MyBuffer[60000];
```

... this means the second running copy of the program has access to its own 60000 byte copy of MyBuffer, even if that bit of code never even needs it at all.

That could be an awful lot of wasted RAM if the bit of code doesn't actually use it. So Linux doesn't really allocate actual RAM. It sort of says "I won't make actual RAM copies of that global stuff. But if that bit of code tries to access MyBuffer, the CPU's MMU will tell me about it, and I'll actually allocate RAM for the second copy right then and there. The app doesn't even need to know it happened. All the app has to do is try to write to MyBuffer, and bang, there's a new copy of it actually in RAM."

Ok, so Linux has delivered an IOU to the app for 60000 bytes right there.

Now there may be other forked apps as well, to which Linux has also issued outstanding IOU's for RAM.

Now, let's talk about what malloc() does. Let's say you do:

```
char *ptr;

ptr = malloc(60000);
```

Have you allocated 60000 bytes? Yes and no. You think you have. The operating system may tell you that you have. (ie, malloc may not return 0). But what Linux has done is write out another IOU for 60000 bytes. It hasn't actually allocated the RAM yet. Linux is going to wait until you actually write something to the buffer before it allocates RAM. So as soon as you do this:

```
ptr[0] = 0;
```

... then the CPU's MMU kicks Linux in the butt and says "Someone just cashed in your IOU. You told him he had 60000 bytes, and now he wants (some of) it. Give it to him". And so Linux looks for some free RAM to fullfill its IOU. It finds some, gives it to the MMU, and then your above instruction works, and you're now writing to actual, real RAM. (Well, that assumes everything goes well, which it may not on Linux).

So, everytime some app calls malloc(), Linux writes out an IOW, to be cashed in at any time by the app.

Now, this would be ok if Linux made sure that all its IOU's are covered by the amount of available RAM in the system, and the amount of available swap space. But it doesn't. Why?

Because there are too many Linux programmers who call fork() just to run a trivial bit of code. And as we've seen from "real experts, with known names and project" who say things like *"spending much time thinking about handling malloc() returning NULL is generally a waste of it*, obviously there are lots of Linux programmers who take a lax attitude toward memory allocation. For example, some of them actually believe that malloc will never return a 0 on Linux, so they don't even check for that. Too many Linux programs ask malloc to write them out an IOU for lots and lots and lots more memory than they'll ever use (because after all, it isn't allocated until you use it, so the hell with being reasonable with your request), and they leak memory all over because they're totally careless and nonchalant in their error handling.

So Linux makes the assumption that all Linux software is badly written when it comes to memory use. Linux assumes that a program will fork() to run a trivial bit of code that doesn't access all its global vars/data, and that a Linux program will ask for more memory than it will ever actually use, and it will do crummy error handling such as not bother checking if malloc returns a 0 (so Linux will try to, but not always, return something other than 0 when it really shouldn't). With these assumptions, Linux therefore gives out more IOUs than it has the capacity to fullfill. Linux hopes that not all those IOUs will be called in. This is called "over-committing". In other words, Linux makes more promises than it can keep (because the IOUs are for more than the available free RAM and available swap space).

So what happens if apps suddenly do start calling in enough of those IOUs such that, finally Linux realizes "OMG! I've already given out all the available free RAM. And I also already filled up the swap space, by writing out stuff in order to free up more RAM. What can I do? I already promised the app some RAM, and now that app is writing to that RAM at this very moment". That's when the OOM Killer kicks in. Linux picks out some running software to abruptly terminate, and grabs back its RAM. "Ack!", says Bill the Cat, as he coughs up a furball.

So what can you, as a programmer, do to help this situation?

1) Do proper error checking. Check for a malloc 0 return. Don't leak memory.
2) Don't ask for ridiculous amounts of RAM that you're not necessarily going to use, just because malloc allows you to ask for a lot of RAM without necessarily allocating it all at once. Ask for RAM in sensible increments.
3) Don't fork() to run trivial code, especially in a program with lots of resources that the secondary bit of code doesn't need. Try to use more versatile techniques such as pthreads.
4) Tell kernel writers we need functions like Win32's VirtualAlloc, so the OS can inform us of a failure without ugly signal handling. Give apps more direct, simple control of the fullfilling of those IOUs, so we can better recover from a failure to fullfill, and the OOM Killer won't have to kick in.
5) Ask kernel and GUI developers to try to work together to come up with a system like Windows, where an enduser is notified of a low memory condition, and given the option to manually attempt to free up RAM in a way he prefers.
6) Get the word out to other developers about doing the above.
7) If you think that moderators are allowing discussion to be stifled/side-tracked, let them know.

---

### Post by dwhitney67 on 2007-11-19
I'd be more concerned about applications that require so much memory that they exhaust all memory available on a system.

If one has a general idea of how much memory their application will use, it is more efficient to allocate that chunk of memory all at once, and then manage it using a memory pool.

I'm a software engineer.  For those of you who like to write poor code, please continue to do so.  I will keep me employed until the day I retire.

---

### Post by CptPicard on 2007-11-19
> **dwhitney67 said:**
> 
If one has a general idea of how much memory their application will use, it is more efficient to allocate that chunk of memory all at once, and then manage it using a memory pool.

I really wish software stopped doing that (especially if the "general idea" is not a fairly good idea). It removes granularity from OS memory management and then we get apps like Firefox and Java VM and OpenOffice(?) that do their own memory pooling and end up hogging RAM just in case it might need it again... and eventually forcing the OOM to intervene faster than it otherwise would have to.

---

### Post by j_g on 2007-11-19
> **dwhitney67 said:**
> I'd be more concerned about applications that require so much memory that they exhaust all memory available on a system.

Don't worry. Linux has an "OOM Killer".

---

### Post by LaRoza on 2007-11-19
Another discussion about this?

I have never experienced the above scenerio, and if it were a major flaw of the Linux kernel, it would have been fixed.

The kernel has to be functional, having a potential problem is a tradeoff in most cases. Either way, it is better than how Windows will treat an out of memory error, it my experience.

If there is a bug, file a bug report, if it won't be fixed, get the source, [http://kernel.org/](http://kernel.org/), and fix it.

---

### Post by LaRoza on 2007-11-19
> **j_g said:**
> 
So what can you, as a programmer, do to help this situation?

1) Do proper error checking. Check for a malloc 0 return. Don't leak memory.
2) Don't ask for ridiculous amounts of RAM that you're not necessarily going to use, just because malloc allows you to ask for a lot of RAM without necessarily allocating it all at once. Ask for RAM in sensible increments.
3) Don't fork() to run trivial code, especially in a program with lots of resources that the secondary bit of code doesn't need. Try to use more versatile techniques such as pthreads.
4) Tell kernel writers we need functions like Win32's VirtualAlloc, so the OS can inform us of a failure without ugly signal handling. Give apps more direct, simple control of the fullfilling of those IOUs, so we can better recover from a failure to fullfill, and the OOM Killer won't have to kick in.
5) Ask kernel and GUI developers to try to work together to come up with a system like Windows, where an enduser is notified of a low memory condition, and given the option to manually attempt to free up RAM in a way he prefers.
6) Get the word out to other developers about doing the above.
7) If you think that moderators are allowing discussion to be stifled/side-tracked, let them know.

0. Ok, it makes sense for programmer to do that.

1. Again, makes sense.

2. True.

3. Ah! Windows != Linux

4. Again! Windows != Linux

5. ?

6. I was one of those who reported the last thread. 

What do you hope to gain by posting this here? If you have concerns, file bug reports, a patch, or use another OS.

This is a very well disguised post promoting Windows and bashing Linux. If you don't like Linux, you have other choices and you can even modify the source to your heart's content. I also reported this thread, as it is a very good example of an expert troll.

---

### Post by j_g on 2007-11-19
> **CptPicard said:**
> I really wish software stopped doing that

There are advantages and disadvantages. It's so hard to say without looking at a specific application.

I used the "private memory pool" thing in an interpreter, because it really sped up the execution of scripts, and avoided memory fragmentation since I knew exactly how handles to that memory were used and could therefore "rearrange" things when it suited me. I mean, the script could theoretically cause lots and lots of little memory allocations, big allocations, and freeing things in whatever order. It could really fragment the system if I let it.

But I haven't done that in my other apps, because the OS usually manages memory in a multi-tasking environment better than I can.

I can see why the JVM would do it. Maybe not so much with Open Office.

---

### Post by j_g on 2007-11-19
> **LaRoza said:**
> Another discussion about this?

There is no other discussion about how Linux's OOM Killer works, and how to avoid triggering it.

> I have never experienced the above scenerio

What "scenario"? Your post fails to identify what "scenario" to which you're referring. I can't very well reply to something that isn't identified.

> Windows != Linux

What possible bearing does that have upon the discussion?

> What do you hope to gain by posting this here?

Less programs that cause the OOM Killer to kick in.

> This is a very well disguised post promoting Windows and bashing Linux.

Incorrect, and unsubstantiated.

> I also reported this thread, as it is a very good example of an expert troll.

Then perhaps _you_ should be reported for calling others who engage in programming discussion "trolls".

---

### Post by bapoumba on 2007-11-19
Whoo hooo !
This thread has been reported left and right.

Another remotely related thread is closed and undergoing staff evaluation. Please wait several of us have a look into both. Thanks.

---

### Post by pmasiar on 2007-11-19
j_g, first thank you for writing this post about complicated deep kernel matters in terms understandable by a layman like me. I do not claim being expert on kernel, and it is fascinating to glance how it works deep inside.

Saying that, I don't share with you the alarmist's feeling - sky is not falling. I don't know nothing about you - what I tried to learn, following [link]("http://home.roadrunner.com/~jgglatt/me.htm") you provided yourself for visitors, let me say, you did not gained a friend, and you did not even tried.

As they say, there is one chance to make first impression, and my impression about you up-close is based on word "ratface" from your page. Not a mature and balanced person, even if maybe aspiring expert.

So maybe there are reasons why real Linux gurus do things as they do, which **you** cannot comprehend. Can you imagine that? maybe that problem is really hard, and it is not fixed not for lack of trying. They cannot be all stupid, and there is no secret kabal to exclude your brilliant solutions. You don't have any. Your solution works in perfect universe - but not in ours. I prefer Linux to work in the universe I live, and it mostly does - and better than Windows, AFAICT.

And of course if you have better solution, you can always submit you to the kernel.

But I would suggest to fix the page about you first.

---

### Post by bapoumba on 2007-11-19
I've reopened the thread for pmasiar to post the reply he could not post while I was locking the thread.

Edit: reopened.

---

### Post by apenny0 on 2008-11-03
> **pmasiar said:**
> j_g, first thank you for writing this post about complicated deep kernel matters in terms understandable by a layman like me. I do not claim being expert on kernel, and it is fascinating to glance how it works deep inside.

Saying that, I don't share with you the alarmist's feeling - sky is not falling. I don't know nothing about you - what I tried to learn, following [link]("http://home.roadrunner.com/~jgglatt/me.htm") you provided yourself for visitors, let me say, you did not gained a friend, and you did not even tried.

As they say, there is one chance to make first impression, and my impression about you up-close is based on word "ratface" from your page. Not a mature and balanced person, even if maybe aspiring expert.

So maybe there are reasons why real Linux gurus do things as they do, which **you** cannot comprehend. Can you imagine that? maybe that problem is really hard, and it is not fixed not for lack of trying. They cannot be all stupid, and there is no secret kabal to exclude your brilliant solutions. You don't have any. Your solution works in perfect universe - but not in ours. I prefer Linux to work in the universe I live, and it mostly does - and better than Windows, AFAICT.

And of course if you have better solution, you can always submit you to the kernel.

But I would suggest to fix the page about you first.


Why are people here attacking the original poster? All he did was raise a valid issue with the Linux kernel. He is not trolling or trying to make people convert to Windows. The programming tips are very sound. According to most experts (real published experts) I have read, pthreads are far more efficient than forks. They are a Unix/Linux tool not a Windows tool as suggested by a previous poster. Linux is a very stable operating system. I like the API and enjoy working in Linux land. But it is not perfect and never will be. So don't take criticism as an insult, but rather as ideas for improvement.

On a side note, right now a program I wrote is being killed by the OS after running for about 5 hours, and I suspect the OOM killer. It does use allot of memory, but I don't think there is a memory leak. Is there anyway to verify that it is the OOM without a kernel rebuild?

---

### Post by lukjad on 2008-11-03
> **apenny0 said:**
> Why are people here attacking the original poster? All he did was raise a valid issue with the Linux kernel. He is not trolling or trying to make people convert to Windows. The programming tips are very sound. According to most experts (real published experts) I have read, pthreads are far more efficient than forks. They are a Unix/Linux tool not a Windows tool as suggested by a previous poster. Linux is a very stable operating system. I like the API and enjoy working in Linux land. But it is not perfect and never will be. So don't take criticism as an insult, but rather as ideas for improvement.

On a side note, right now a program I wrote is being killed by the OS after running for about 5 hours, and I suspect the OOM killer. It does use allot of memory, but I don't think there is a memory leak. Is there anyway to verify that it is the OOM without a kernel rebuild?
Ummm... I have no idea what this thread is really about but... isn't this ancient history? I mean, how did you even find this thread?

---

### Post by apenny0 on 2008-11-03
> **lukjad007 said:**
> Ummm... I have no idea what this thread is really about but... isn't this ancient history? I mean, how did you even find this thread?

Sorry, just noticed the time stamp. It came up in a google search.

---

### Post by lukjad on 2008-11-03
> **apenny0 said:**
> Sorry, just noticed the time stamp. It came up in a google search.
Ah, I see. I was really wondering what happend.

---

### Post by bapoumba on 2008-11-03
Well well well, let us sit in there for eternity :)
Closing.

---

