---
title: "[C] Waiting for event?"
date: 2009-08-15
forum: Programming Talk
---

### Post by OutOfReach on 2009-08-15
Hey guys, I am making a TODO/reminder system and I have completed the backend library and I'm moving on to the daemon.

Theoretically, the daemon is supposed check for the TODO list with the latest alarm date, sleep() until that date and then show a notification. (Now, I know this might not be the best way to do it but I'm open to ideas)

Then I began thinking, what if a new TODO, with an alarm less than the one currently being waited for, is added?

For example, we have a TODO with an alarm date of 8/15/09 4:50.
The daemon will sleep until then, but then the user decides to add another task with an alarm date of 8/15/09 **2:30**.


So basically my question is, what kind of system can I use in this type of situation? Ordinary sleep()? Signals? Callback functions?

Thanks

---

### Post by napsy on 2009-08-15
The most primitive way would be pooling. Meaning you create a function that has a period of one second and checks the whole todo list.

---

### Post by OutOfReach on 2009-08-15
> **napsy said:**
> The most primitive way would be pooling. Meaning you create a function that has a period of one second and checks the whole todo list.

Hmm, I'm not quite sure what you mean, mind explaining?

---

### Post by napsy on 2009-08-15
Read the manual page for alarm(). Alternatively, you could use the glib framework and g_timeout_add to periodically call a function. But then you must create a glib event loop for your program.

---

### Post by OutOfReach on 2009-08-15
Hmm, ok I read and done some research. But im not sure if it'll work. The shared library and the daemon are separate, so would I'm not sure if alarm() would work. Maybe registering the daemon's pid in the library and sending it a signal everytime a TODO is added?

I apologize if I am not correctly understanding you

---

### Post by Habbit on 2009-08-15
You could try to use DBus, though it might be a bit of an overkill depending on your needs.

---

### Post by dwhitney67 on 2009-08-15
@ the OP

I would suggest you do is define/create a priority queue (actually a linked-list) in which TodoAction records are inserted based on their expiration time.

A TodoAction record could have the following information:
[LIST]
[*]expiration time (in number of seconds since Unix/Linux epoch)
[*]action function to call
[*]data to pass to the function
[/LIST]

Then periodically poll to see if the item at the front of the queue has expired, and if so, execute it.  Since the expiration times are on the order of seconds, just check the queue every half-second, which is pretty modest.

Why, btw, are you writing this application in C?  Surely there are more convenient languages to use.  Even C++ would be easier.

---

### Post by OutOfReach on 2009-08-15
> **dwhitney67 said:**
> @ the OP

I would suggest you do is define/create a priority queue (actually a linked-list) in which TodoAction records are inserted based on their expiration time.

A TodoAction record could have the following information:
[LIST]
[*]expiration time (in number of seconds since Unix/Linux epoch)
[*]action function to call
[*]data to pass to the function
[/LIST]

Then periodically poll to see if the item at the front of the queue has expired, and if so, execute it.  Since the expiration times are on the order of seconds, just check the queue every half-second, which is pretty modest.

Why, btw, are you writing this application in C?  Surely there are more convenient languages to use.  Even C++ would be easier.

heh, funny thing is that most of the things you mentioned are already implemented. The todo list is indeed a managed linked list and I do store the alarm date in time_t's. But I hadn't thought of your last two points you mentioned. But, wouldn't the consistent polling cause for 100% CPU usage? Well, maybe 1/2 second delays are enough to decrease that.

But yes, I see were you're going and I must thank you for the idea. :)

Oh, and I'm writing this in C just to get more familiar with it. One thing that ALWAYS troubled me with C is memory management, and I thought this would be good to practice. I would've written it in C++, but I don't know much of it so going into a project like this with a language I half-know would be suicide. :)

---

### Post by soltanis on 2009-08-15
Another way to do it (keeping most of what you described) is to wake up the process every time a new task is scheduled. Then the process should find the nearest-task in the future, schedule an alarm, then go to sleep. If the algorithm schedules the wake-up for the next task, it should always wake up when the next task is.

---

### Post by dwhitney67 on 2009-08-15
One should be cautious using the alarm() library function, especially if the main app is using sleep(), or usleep(), to lie dormant, before polling the list of events.

Also, one can only set one alarm at a time.  Thus if there are multiple events that need to be processed at the "same" time, then this might prove to be a challenge.

One can consider forking a child-process that blocks while a select() is used (for a timer), and then the action can be executed.  Something like:

```

...

// schedule an event to take place in the future

pid_t child_pid = fork();

if (child_pid == 0)
{
   struct timeval t = { seconds, microseconds };

   select(0, 0, 0, 0, &t);   // delay some time t

   // perform action...

   exit(0);   // child process exits
}

...

```

P.S.  Forking a child-process is CPU-"expensive".  Perhaps creating a pool of child-threads that can be used to execute the event might be better.

---

