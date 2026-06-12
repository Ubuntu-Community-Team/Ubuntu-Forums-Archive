---
title: "Best language for multi-core processors, multi threaded apps?"
date: 2005-05-19
forum: Programming Talk
---

### Post by NoTiG on 2005-05-19
Just wondering... I always thought C++ was the best.. to me it just looks the prettiest but maybe that is because its what i started with. but i recently read a comment somewhere of someone saying that its not best for multi threaded apps. what is then???

---

### Post by mendicant on 2005-05-19
I would think it is a question of (standard) library and OS support here.  Assuming you want to use Linux across the board, then it's more a question of what libraries are designed for multithreaded use.  For C++ you might be interested in this:

[http://www.codesourcery.com/archives/c++-pthreads/maillist.html](http://www.codesourcery.com/archives/c++-pthreads/maillist.html)
and the second thread in this view:
[http://www.codesourcery.com/archives/c++-pthreads/threads.html](http://www.codesourcery.com/archives/c++-pthreads/threads.html)
and
[http://groups-beta.google.com/group/comp.std.c++/browse_thread/thread/edf2eb1d3f0f9755/158390632f4667fb#158390632f4667fb](http://groups-beta.google.com/group/comp.std.c++/browse_thread/thread/edf2eb1d3f0f9755/158390632f4667fb#158390632f4667fb)

They discuss various issues with C++ and threads.  You might also want to look at Boost.Threads as a portable threading example.  Of course, then you have to look at the thread safety of the libraries you use (and not create).

Java seems like it should be a natural fit for multithreaded apps, since Threads were in the standard library from the start.  Again, though, it depends on what external libraries you want to use--it's quite easy to create non-thread safe/optimized code in Java.

---

### Post by LordHunter317 on 2005-05-19
Just about any language is fine for threading... what is you want to do?  That should have more bearing than anything.

---

### Post by randy on 2005-05-19
For simple multi threaded programming under Unix you'll probably want to go with Java.  It's thread interface is extermely well designed and easy to use.

---

### Post by jerome bettis on 2005-05-20
if speed isn't much of a concern i would definately use java .. managing threads is easy over there.

i've actually never written a multithreaded program in c++ but i'd be willing to bet it's more compilicated.

---

### Post by JonahRowley on 2005-05-20
This all depends on what you're doing.  C or C++ (since neither of them actually have any thread-specific features, I'll lump them together) would be at the top of my list if performance is the goal.  Nothing touches them, but development time will be longer.  Also, since C and C++ have direct access to the API, they can utilize any thread API available on the OS.

Whatever you choose, read about its threading model.  User-space threads are bad.  They don't do anything good for performance, and are problematic with blocking IO.  I belive until recently, on Linux systems, POSIX threads are implemented as user-space threads.  Breezy will have native POSIX threads, I don't know if many other distros have them.

Then again, you don't have to use "threading", you can use processes.  They're not as light-weight, but depending on the task, they can be efficient.  Most programming languages will be able to do this well, having a decent socket API is a plus.  If you're coding a network app, for example, you can spawn worker threads and pass them accept()ed sockets through a socket to the main process, and the worker threads can handle the request.  This is what Apache HTTPD does, and it works well.

So, I guess you have to tell us a bit more about your goals.  Do you just want to learn threaded programming (an artform in itself, race conditions can be tricky), or did you have something specific in mind?

---

### Post by ltmon on 2005-05-20
If you Google for Java threading performance on Linux you'll probably find a lot of derogatory posts... most with good reason as they were posted before NPTL (new posix thread library?) was added to the kernel.  

Just a heads up in case you were finding such posts.  With NPTL threading in Java on Linux is much better.

I think NPTL was added about 2 years ago and started making it into standard kernel builds (i.e. RedHat, SuSE builds) about 6 months after this.

L.

---

### Post by mendicant on 2005-05-20
[QUOTE=jerome bettis]
i've actually never written a multithreaded program in c++ but i'd be willing to bet it's more compilicated.[/QUOTE]

It's not much more complicated, if at all (minus issues with language features, perhaps).  It's more a matter of using appropriate abstractions, usually provided by a third party library such as the ACE framework, Boost.Threads, OpenThreads etc.  Just don't try to cancel a thread, especially when using something like C's printf.

The thing with Java is that since Threads have always been a standard part of the library, it's a bit more likely that other libraries are thread safe.

---

### Post by LordHunter317 on 2005-05-20
[QUOTE=JonahRowley]Whatever you choose, read about its threading model. User-space threads are bad.[/quote]No, they're not.   They're perfectly acceptable for some tasks and some operatings systems still use a M:N threading model.

Just because it's not what Linux uses doesn't make it automatically bad.

>  I belive until recently, on Linux systems, POSIX threads are implemented as user-space threads.Linux hasn't used userspace threads since the 2.0 days. 

>  Breezy will have native POSIX threads, I don't know if many other distros have them.Ubuntu has NPTL now as does every other distribution using 2.6.  Some 2.4 using distrbutions like RHEL 3 also have NPTL.

> If you're coding a network app, for example, you can spawn worker threads and pass them accept()ed sockets through a socket to the main process, and the worker threads can handle the request. This is what Apache HTTPD does, and it works well.Actually, one thread per connection doesn't scale very far.  Google for the C10K problem.

Apache uses one thread or one process per connection for other reasons, though.  But if your goal is maximum scalability that's not the way to go about it.

[quote=mendicant]  Just don't try to cancel a thread, especially when using something like C's printf.[/quote]What? Umm, no.

---

### Post by vague- on 2005-05-20
You might be interested in Occam, here is a site I found about it:  [http://vl.fmnet.info/occam/](http://vl.fmnet.info/occam/)

I do not know much about Occam, but know that it was pretty much designed for this type of usage.  Even if you do not use it, you may find some interesting principles, concepts and patterns for your own programs.

---

### Post by mendicant on 2005-05-20
[QUOTE=LordHunter317]
[QUOTE=mendicant]
 Just don't try to cancel a thread, especially when using something like C's printf.
[/QUOTE]
What? Umm, no.[/QUOTE]

Right.  I should have been more precise, and double checked the function (which should be cout instead of printf).  I should have said, "avoid cancels when there is a catch(...) in some code that you're using", and left it at that..

I mentioned the printf (which should have been cout) because I had ported a win32 program that used OpenThreads and deferred cancels and which aborted during a cancel.  It seemed to be related to this problem:
[http://gcc.gnu.org/ml/gcc/2003-12/msg00743.html](http://gcc.gnu.org/ml/gcc/2003-12/msg00743.html)
[http://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=118490](http://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=118490)

So the moral is to be careful with cancelling threads and the exception handler.

---

### Post by LordHunter317 on 2005-05-20
[QUOTE=mendicant][]("http://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=118490")So the moral is to be careful with cancelling threads and the exception handler.[/QUOTE]Yes, but it should be noted this is a GCC/libstdc++ "feature" too.   This is why I love the C++ standard sometimes.

---

