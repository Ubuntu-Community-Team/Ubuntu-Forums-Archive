---
title: "File monitoring without killing battery life"
date: 2010-01-29
forum: Programming Talk
---

### Post by Andruk Tatum on 2010-01-29
How should I go about monitoring file *changes* without killing my laptop's battery life?

---

### Post by Hellkeepa on 2010-01-29
HELLo!

inotify seems to go about that business quite nicely, [Dropbox](http://www.dropbox.com) use it to much success at least.

Happy codin'!

---

### Post by hessiess on 2010-01-30
Keep track of the files `modified data/time' property, if the time changes, the file has bean modified.

---

### Post by Andruk Tatum on 2010-02-01
So with a lot of the tutorials I've seen, they use read(), which is blocking.  They do say that select() is nonblocking, so does anybody know if select() has a non-negligible impact on battery life?

Thanks!

---

### Post by dwhitney67 on 2010-02-01
select() does block; I do not know where you read otherwise.  Of course you can provide it with a miniscule timeout period (with microsecond resolution), thus making select() return after a brief period of time and offering the illusion that it is non-blocking.

Regardless of the definition of blocking vs. non-blocking, select() is generally the preferred function to use when a task must perform more than one function and waiting on a read() or recv() call is undesirable.

As for battery life, if you are monitoring an HDD, access to it will consume more battery power than some application running in RAM (and using your CPU).

Stop worrying so much about the damn battery and write some code!  Chop-chop!!!


P.S.  I should also point out that read() and recv() can be made non-blocking, if you setup the file descriptor appropriately.

---

### Post by kahumba on 2010-02-01
> **dwhitney67 said:**
> 
Stop worrying so much about the damn battery and write some code!  Chop-chop!!!

Haha that's funny are you a teacher or a supervisor :)

---

### Post by Andruk Tatum on 2010-02-02
Here's what I coded up so far.  It works if I want to multithread my application, but if anybody has any ideas on how I can not do that, I'm all ears!

---

### Post by Andruk Tatum on 2010-02-04
So inotify isn't queuing an event when the kernel modifies the file, at least as far as I can tell.  Is this normal?

Here's what happens:
Monitor /sys/devices/platform/hp-wmi/tablet for all inotify events
Look at file (file contains "0") -> Receive inotify  Open, Access, Write events
Rotate physical tablet
Don't receive any inotify events
Look at file (file contains "1") -> Receive inotify Open, Access, Write events
Rotate physical tablet
Don't receive any inotify events
Look at file (file *usually contains "0", although still "1" sometimes) -> Receive inotify  Open, Access, Write events

---

