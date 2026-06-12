---
title: "How do I print messages from a daemon?"
date: 2009-11-05
forum: Programming Talk
---

### Post by manualqr on 2009-11-05
I have a program that works like this;
> 
1. main()
2. fork()
3. daemonize (setsid, fork, umask, chdir)

global mutex { list of tasks }
4. new pthread: runs a server on port FOO, adds tasks to list
5. main-loop: pops tasks off the list and evaluates them


Whenever I try to use cout/clog/cerr, however, the messages only get printed to the terminal I started the daemon from. For example, I start the daemon on terminal 1, open up terminal 2, send a task to the daemon from terminal 2, the daemon prints output on terminal 1 (instead of 2).

Is there a way I can re-direct output to the calling terminal? This must work on cygwin, freebsd, and unix-like operating systems, by the way.

Thanks!

note: I didn't post the code because it's fairly long, but if you want to take a look at it, I will.

---

### Post by lloyd_b on 2009-11-06
> **manualqr said:**
> I have a program that works like this;


Whenever I try to use cout/clog/cerr, however, the messages only get printed to the terminal I started the daemon from. For example, I start the daemon on terminal 1, open up terminal 2, send a task to the daemon from terminal 2, the daemon prints output on terminal 1 (instead of 2).

Is there a way I can re-direct output to the calling terminal? This must work on cygwin, freebsd, and unix-like operating systems, by the way.

Thanks!

note: I didn't post the code because it's fairly long, but if you want to take a look at it, I will.

The question - how is the daemon supposed to know which terminal to send the message to?  Unless you have some mechanism to send this information to the daemon, then the daemon has no way to know this.

You really need to implement this in the protocol that communicates between requesting program and daemon.  Sure, you *could* just send the terminal device to the daemon, and have it write directly to the "/dev/..." entry for that device, but that's kinda sloppy...

Lloyd B.

---

### Post by manualqr on 2009-11-06
> 
You really need to implement this in the protocol that communicates between requesting program and daemon. Sure, you *could* just send the terminal device to the daemon, and have it write directly to the "/dev/..." entry for that device, but that's kinda sloppy...


I do have a mechanism for sending messages to the daemon. And I don't think your idea is too hacky. I think unistd's ttyname() is what I was looking for.

So I could do;
```

$ ./myprog start
starts daemon ...
$ ./myprog send request foo
sends request foo to daemon, along with ttyname(0)...

The daemon does;
stdout = fopen(<ttyname>, "a");
fprintf(stdout, "stuff");

```

I'll implement this and let you know how this goes.

---

### Post by manualqr on 2009-11-06
I can't believe it! This actually worked perfectly. Implementing it is fairly simple; the only compile warning I got the first time was about my printf flag for size_t's =p.

If you want to see how I did this, you can browse the source here;
[http://code.google.com/p/udc/source/checkout](http://code.google.com/p/udc/source/checkout)

The interesting bits (for you) are near;
request.cpp:68
kernel.cpp:98
kernel.cpp:203

Thanks!

---

