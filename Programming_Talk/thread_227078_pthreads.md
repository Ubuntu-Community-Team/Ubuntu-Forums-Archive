---
title: "pthreads"
date: 2006-08-01
forum: Programming Talk
---

### Post by Grey on 2006-08-01
I'm not really new to Linux/UNIX programming, but I have just recently decided to finally get around to learning pthreads.  It's actually my first dive into concurrent programming.  I have a couple of stylistic questions to ask, and then I have a question about the runtime results.  I would greatly appreciate any input that the more experienced people here might have for me.

1)  The basic architecture of my program is as such.  (I realize that the sheer number of threads here is inefficient, but I am emulating the API of a specific piece of hardware (Nintendo DS)).  I am writing two seperate low level pieces of code that has an identical high level API.  As such, I wish for the low level code to be as similar as possible.  (If I compile for NDS or Linux, it should run the same on either system.  But only development is done on Linux.  The program is intended to be run on a DS).  So I wish to keep the basic threading architecture (The DS contains 2 CPUs, one of which is dedicated for menial tasks such as outputting sound, the other that contains the main program.), but am looking for someone to tell me if something is glaringly wrong, as I have never done this before.

- Main program spawns sound server thread
- Sound server thread spawns 16 helper threads, which are each capable of playing a 1-channel sound via libao.  They start up and wait for a signal from the sound server thread, and repeat indefinitely.
- Main program waits for signal from sound server thread announcing that it's done initialization (thread is created, and helper threads are at least in the process of being initialized)
- Sound server thread waits for signals from main thread, and checks a common global variable, which contains a int and a union inside of a struct, that can contain a vast variety of different information.  (Mutex is used to keep them from stepping on eachother's toes).  Up to 16 messages may be passed at once.  The global variable is an array.
- If the sound server receives a request to play a sound, then it relays a message to a free sound thread.  The data on which threads are free is kept in a global array, and protected by mutexes.
- Mutexes and conditions are used liberally.  There's a mutex and condition for checking if the sound server thread is initialized yet (to prevent messages from being passed before it's ready), there's a mutex and condition for message passing to the sound server, and there's a mutex and condition for each of the helper threads.
- Please be as harsh as you feel is necessary when reviewing my architecture.  I won't take offense.  :)

2)  My second question is about the runtime results.  I am getting a whole lot of debug output, which is leading me to believe that either my system is not set up quite properly, or I am not running the program properly, or there's something wrong with my code.  Here's what I get:
```

sound server ready
sending signal...
     10679:     checking for version `GLIBC_2.2.4' in file /lib/tls/i686/cmov/libc.so.6 required by file /lib/libgcc_s.so.1
     10679:     checking for version `GLIBC_2.1.3' in file /lib/tls/i686/cmov/libc.so.6 required by file /lib/libgcc_s.so.1
     10679:     checking for version `GLIBC_2.0' in file /lib/tls/i686/cmov/libc.so.6 required by file /lib/libgcc_s.so.1
     10679:
     10679:     relocation processing: /lib/libgcc_s.so.1 (lazy)
sound server signal received
quit signal received
     10679:
     10679:     runtime linker statistics:
     10679:                final number of relocations: 176
     10679:     final number of relocations from cache: 7

```

Anything prefixed by 10679 is NOT something that I intentionally outputted.

---

### Post by LordHunter317 on 2006-08-01
> **Grey said:**
> - Main program spawns sound server thread[
- Sound server thread spawns 16 helper threads, which are each capable of playing a 1-channel sound via libao.  They start up and wait for a signal from the sound server thread, and repeat indefinitely.This is excessive.  You want a single thread.  This thread will need to mix the channels together and send it out.  You do not want to be attempting to play 16 1-channel sounds at once (it likely won't work right) and the sychronization will be too complicated to make it work in a useful fashion.

One thread for sound is enough.  It takes inputs and mixes them together.  If you need to support 16 1-channel inputs, then worse-case make a array with 16 fixed entries other threads can access.  Simple.

But I don't think that's the best design either.  Threads should just signal the sound thread and give a pointer to where the sound data to render is located.


> - Sound server thread waits for signals from main thread, and checks a common global variable, which contains a int and a union inside of a struct, that can contain a vast variety of different information.  (Mutex is used to keep them from stepping on eachother's toes).  Up to 16 messages may be passed at once.  The global variable is an array.Startup information should be passed when you spawn the thread.  You can pass any argument you like when you first spawn the thread.  Don't wait, you're complicating your architecture for no good reason.

If you want the main thread to block until the sound thread is ready, use a condition variable to wait.

> The data on which threads are free is kept in a global array, and protected by mutexes.Such data should never be global, if you choose to go this route.  That's private to the master sound server thread.  

You seem big on global variables.  Even in a threaded application, where there may be a bigger need for global variables, you want to minimize them to the greatest extent possible.  Limited scoping is your friend.  Passing pointers is also your friend, as long as you're careful about ownership issues.

> Anything prefixed by 10679 is NOT something that I intentionally outputted.You need to read up on how signals are handled in threaded applications.

---

### Post by Grey on 2006-08-01
Thanks for the response.  Like I said, I am grateful for any and all input.  And although you didn't mean it that way, I get the impression that I am on the right track.  ;)

I have been using this page as a guide to learning pthreads.  Is it good in your opinion?  Or is there a better resource?
[http://www.llnl.gov/computing/tutorials/pthreads/](http://www.llnl.gov/computing/tutorials/pthreads/)

Anyways, I have a few follow up questions based on your input, and I am actually posting my source this time if you should like to read it yourself.  (compile with gcc -lao -ldl -lm -pthread -o thread thread.c).  Still very incomplete, but serves quite well in showing you the architecture.  When complete, this will be merged with another project as a low level module with a few accessing functions, such as snd_init, snd_play, snd_stop, snd_quit, etc.  But for the time being, it's just a test file.  Anyways, my questions.

1)  As you can see, I have 3 global variables that aren't mutexes.  I have them as global because I was under the impression that local variables are not shared amongst threads.  If I were to declare the variables in the creating thread and pass a pointer, and the function that created the thread were to go out of scope, then the variable would be undefined, would it not?  I declared them as static globals in an attempt to get the best of both worlds.  I might take your advice in the sound server thread though, as it should never go out of scope.  But I think that the main ipc_mesg struct needs to be global.

2)  I am completely new to sound programming on a PC system.  I am accustomed to embedded systems, where I set a few values in memory mapped registers, and the sound will automatically play asynchronously.  Mixing audio in a single thread sounds a little difficult to me.  In order to promptly play audio when requested, I would have to play very small chunks of audio at a time, and mix them by adding the values, would I not?  This just seems like a lot of work to get something working perfectly that honestly isn't that important at this point in time (merely working is good enough for this release, I can perfect it later, for the time being it doesn't matter if it's a ms off in timing, or horribly inefficient).  (NDS is the target system for the finished product)  Anyways, my main problem is that I can't seem to find a way of playing audio asynchronously without threading the sound playback threads.

Anyways, thanks for the feedback so far, and I look forward to more.

---

### Post by Grey on 2006-08-02
Sorry for the double post, but this thread has slipped to page 2.  I just want to say that I stopped being hard headed, and took your advice.  My IPC_mesg struct is now the only global, and is now a linked list (for reasons stated in my previous post, I want to ensure that the two threads share the same memory for that variable).  I also am now running only 2 threads.  I am currently writing functions to do software mixing in the sound thread, and play samples in very small chunks.

Still a work in progress, but just thought you might like to know.  Thanks again for the advice.

---

### Post by LordHunter317 on 2006-08-03
If you want to post your new code, I'll be happy to look at it.  I meant to look at your old code eventually, but things have been rather hectic here and I've simply had other priorites.

---

