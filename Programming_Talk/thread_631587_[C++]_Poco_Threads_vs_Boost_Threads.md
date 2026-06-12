---
title: "[C++] Poco Threads vs Boost Threads?"
date: 2007-12-04
forum: Programming Talk
---

### Post by iharrold on 2007-12-04
Any one have any experience with using [Poco]("http://www.appinf.com/poco/docs/") library implementation of threads vs. [Boost]("http://www.boost.org/") library implementation of threads?

I am using the boost libraries currently, but I am not happy with the thread libraries as it doesn't give me the fidelity and thread control I want. So I am looking at other libraries.  I have found the Poco library and it looks promising.  I installed the library with:
```
sudo apt-get install poco*
```
This got the development files, the document files and library.

So anyone have experience using Poco Threads and an opinion of it over Boost threads?

---

### Post by iharrold on 2007-12-07
Anyone used Poco before?

---

### Post by tyoc on 2007-12-10
No, but it look interesting.

Also it has return a memory from a library that 1 time I see, I have ask where I remember I have found the link [http://www.ogre3d.org/phpBB2/viewtopic.php?p=261137](http://www.ogre3d.org/phpBB2/viewtopic.php?p=261137) but aparently now that I see it, it doesn't has thread support, it was [http://tinytl.sourceforge.net/](http://tinytl.sourceforge.net/) also people when trying to hit the nail about my remote memory describing I what I saw,  this links has jump from one reason or other:  [http://loki-lib.sourceforge.net/](http://loki-lib.sourceforge.net/) and [http://www.cs.wustl.edu/~schmidt/ACE.html]("http://www.cs.wustl.edu/%7Eschmidt/ACE.html")

By now I guess you have already managed what you want, but those links perhaps can help too.

---

### Post by HueyLuey on 2007-12-14
I'm glad you've come across POCO. I've been using it on my project at work and I think it is brilliant (but not without niggles). It wraps up so much of the nasty low-level OS specifics.

I haven't used boost threads in anger, but POCO does give you some pretty cool features with threads:
- Active methods
- Tasks and task management
- thread pools to improve performance of spawning new threads

There are other libraries out there that do similar things e.g. ACE. However the documentation freely available for ACE leaves a lot to be desired; it is really difficult to get started with.

Good luck with it :)

---

### Post by dumbsnake on 2007-12-14
Have you considered just using the OS directly?

I found it wasn't all that hard to call fork, clone etc...  I guess it really depends on what you are doing though.

---

### Post by slavik on 2007-12-14
> **dumbsnake said:**
> Have you considered just using the OS directly?

I found it wasn't all that hard to call fork, clone etc...  I guess it really depends on what you are doing though.
fork does not create threads. :) maybe you were thingking of pthreads?

---

### Post by dumbsnake on 2007-12-14
clone can do anything.  fork does create threads technically, but I'll give you that since it really is just  technicality.  My point was only that you could call linux directly.  It gives you the ultimate flexibility.  I personally
 only really use clone for threads.

---

### Post by jmartrican on 2008-04-20
I like Zthreads personally.  Have you checked zthreads out?  I am learning Boost now only because it's suppose to be a prelude to the C++ standard implementation of threads (whenever it comes out).  So far I prefer zthreads.

---

### Post by kknd on 2008-04-21
++Poco;

---

### Post by Zdravko on 2008-04-21
++Boost.

---

### Post by petervn1 on 2009-04-27
> **dumbsnake said:**
> clone can do anything.  fork does create threads technically, but I'll give you that since it really is just  technicality.  My point was only that you could call linux directly.  It gives you the ultimate flexibility.  I personally
 only really use clone for threads.


For those doing cross-platform development using OS directly is not an option, hence we end writing layers to abstract OS. I've used boost thread libraries, and was pleased with their implementation of threading groups and barriers. Without boost, I would have ended up implementing barries on Win32 myself. There are some other aspects of boost I don't like, but that's a different discussion altogether.

---

