---
title: "Advise on IPC data streaming"
date: 2012-03-02
forum: Programming Talk
---

### Post by Hetepeperfan on 2012-03-02
Hello

I would like to have some help with the following program. I've have something running now, however I feel it's not good enough currently. I would like gain some information about how I can make it myself easier to operate on the same data in different threads. I use C++ and pthreads to achieve this goal. From which originates the first question is Pthreads not a to low level tool to use in an application?

I have to program an application that is quite multi threaded. there is a thread that "generates" data ( video_media alike) and then there are other threads that operate on this data, gain some information on it and try to display the data. Now I've never studied Computer Science so I'm now really struggeling with getting the design right. I'm searching for software tools that can help me stream this data between the threads without copying the data to often.
Currently I'm using some globally allocated buffers (uint8_t**)to accommodate the data and use pthread_mutex_t to synchronise the access. And use pthread_cond_signal the tell the next thread some data has arrived thus it can try to lock the mutex that  guards the data use the data and try to pass the data on to the next stage. So this results in kind a pipeline that looks likes this:

get_data | process/analyse data | log_relevant data | display data

Now the question is what kind of API libraries can assist me in streaming the data through the different threads, when should one decide to use a thread, a new process or even a different program.
I tried looking at ACE, but I have a hard time to find up to date examples or books that explain ACE. Does anyone knows about these kinds of problems? Any help would be much appreciated.

kind regards,

Maarten

---

### Post by MadCow108 on 2012-03-02
my standard answer to this type of problem is zeromq. It is conceptually very simple (just beefed up sockets really) and allows you to abstract the messaging so that you can handle threads, local processes and nonlocal processes in the same way and helps you get away from hard to handle mutex based approaches which are often hard to scale and bug prone.

it does have non-copying sends, but not non-copying receives so if that is a problem you have to look for something else (MPI has them so far I know but is significantly more complex and probably not appropriate for your use case).

It also has quite good docs (though they do not really address your use case so well, they are more focused on reliable networking)
[http://zguide.zeromq.org/page:all](http://zguide.zeromq.org/page:all)

It is quite low level and will only handle the actual communication and queuing, nothing more but hopefully thats all you need.

---

### Post by Hetepeperfan on 2012-03-03
> **MadCow108 said:**
> my standard answer to this type of problem is zeromq. It is conceptually very simple (just beefed up sockets really) and allows you to abstract the messaging so that you can handle threads, local processes and nonlocal processes in the same way and helps you get away from hard to handle mutex based approaches which are often hard to scale and bug prone.

it does have non-copying sends, but not non-copying receives so if that is a problem you have to look for something else (MPI has them so far I know but is significantly more complex and probably not appropriate for your use case).

It also has quite good docs (though they do not really address your use case so well, they are more focused on reliable networking)
[http://zguide.zeromq.org/page:all](http://zguide.zeromq.org/page:all)

It is quite low level and will only handle the actual communication and queuing, nothing more but hopefully thats all you need.


Hi MadCow,

Thanks for your reply:)!! I'll have to look in to it and wrestle with some examples, but it at least it looks promising.
Many of these IPC tools are mainly concerned with network processing like ACE is. But if I can pass the data between threads/processes in an efficient and well manageable way I'm really happy. I hope working with it is a bit more enjoyable than synchronising everything manually between those threads.

thanks Maarten

---

