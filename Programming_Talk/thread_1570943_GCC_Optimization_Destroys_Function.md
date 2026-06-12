---
title: "GCC Optimization Destroys Function"
date: 2010-09-08
forum: Programming Talk
---

### Post by Mr.Macdonald on 2010-09-08
First off, this is a theory! I can't prove it. only observe it.

I have this function
[PHP]void react(struct input_event* ev) {
  if (ev->code == KEY_Q)
    *end=0;

#define IFEV(k) if (ev->code == k)

  IFEV(KEY_A) printf("A");
}[/PHP]

No Problems with the macro, I checked that

This function is programmed into a POSIX Thread, such that when a keyboard event occurs, it calls this function (passing in the event).

This is hard to describe, I don't want to load the code onto you, but here goes.

Scenario 1
I run the code as displayed, when I hit buttons nothing happens. When I hit "a" I would expect and "A" to be printed, but nothing happens. When I hit "q", end goes to 0 and that kills the POSIX Thread. The program ends, and to my surprise a bunch of "A"s get printed.

I believe that the optimizer is holding the Thread back till the main program ends, or just merging the too.

Scenario 2
I put a print statement into that function that prints no matter what button is hit. When this is run, all works perfect. The button presses cause an immediate print and hitting "q" doesn't cause any post-program prints

This is because the optimizer believes that the function will always do something. I have had similar things happen before, but I found a work around. Can't thing of a good one here

---

### Post by slavik on 2010-09-08
buffered output :)

---

### Post by Mr.Macdonald on 2010-09-08
How do I fix it?

---

### Post by slavik on 2010-09-08
man fflush if you really need it, but IMO, you don't :)

---

### Post by Mr.Macdonald on 2010-09-09
Thank you,

But why don't I?
this isn't the final code, just testing bits and pieces so the final gets put together without confusing errors

EDIT:
Does this only apply if I want to print things?

---

### Post by MadCow108 on 2010-09-09
no, it applies to every default input/output function in C.
But the kind of buffering depends on the device.
e.g. terminals a line buffered, whereas block devices are fully buffered.
Buffering has a huge impact on performance, it may save system calls and certain devices work better when handling larger blocks of data (e.g. harddisks are mostly fastest when handling blocks of 4 or 8mb)

you can also control what it is done (or disable it):
[http://www.gnu.org/s/libc/manual/html_node/Controlling-Buffering.html](http://www.gnu.org/s/libc/manual/html_node/Controlling-Buffering.html)

---

### Post by slavik on 2010-09-09
In this instance, you are writing debug output. So it's useless to output as soon as you call printf().

---

