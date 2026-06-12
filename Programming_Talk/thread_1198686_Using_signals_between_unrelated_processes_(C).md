---
title: "Using signals between unrelated processes (C)"
date: 2009-06-27
forum: Programming Talk
---

### Post by sauronnikko on 2009-06-27
Hi. I'm having quite a headache trying to communicate two processes which have no relation (one is not the child of the other). I use SIGUSR1 for this purpose. i just want to send one signal from process 1 to process 2 so that this last process prints something in the console. Instead, it prints "User defined signal 1" and exits. I know this is the default behaviour but i'm installing a signal handler which supposedly just prints something. Any help'll be appreciated. Thanks

---

### Post by soltanis on 2009-06-27
Show us the code for the signal handler you're trying to execute, and the relevant section of code where you assign the handler with signal (2).

---

### Post by sauronnikko on 2009-06-27
This is the signal handler function:

void signalHandler (int sig)    {
    printf ("PRINT\n");
}

This is where I install the signal handler (I do this in main):

signal (SIGUSR1, signalHandler);

And now this is where I try to send a signal to the other process (id is that process id):

kill (id, SIGUSR1);

All of this is written in the process which sends the signal. The other process has nothing related to signals. Of this I am doubting, perhaps it should have something. Anyway, my objective is to have the program which receives the signal print "PRINT" as shown in signalHandler.

---

### Post by stroyan on 2009-06-27
A signal handler only affects the reaction when a signal is received by the process that set up the signal handler.  It won't affect the behavior of another process that you are sending a signal to.

Signals have other drawbacks as a means of interprocess communication:
[LIST=1]
[*]A signal can be deadly to a process that is not ready for it.
[*]Multiple signals will not be queued and delivered if they are received when the process is handling one signal.  (Additional signals will either be dropped or may cause a process to exit if you are using "signal" instead of "sigaction" to set up the handler.)
[*]Very few library and system calls are safe to use within a signal handler.  Event printf is not safe to call in a handler.
[/LIST]

You may be much happier in the long run using a different mechanism such as sockets or message queues.  Have a look at [http://en.wikipedia.org/wiki/Inter-process_communication](http://en.wikipedia.org/wiki/Inter-process_communication) for some options.

---

### Post by sauronnikko on 2009-06-28
Thank you. You were right, I needed to set up a signal handler for the process that was receiving the signal. Also, I know that other ways of communications such as pipes are better, but I was curious about how to deal this kind of thing with signals

---

