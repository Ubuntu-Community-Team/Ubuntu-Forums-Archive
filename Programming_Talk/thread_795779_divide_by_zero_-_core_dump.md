---
title: "divide by zero - core dump?"
date: 2008-05-15
forum: Programming Talk
---

### Post by HunterSBuntu on 2008-05-15
I'm practicing my C++ programming and the book I'm reading presents an exercise which intentionally causes a divide by zero error to illustrate the concept of run time errors.  In the description of the example the author says 'On a UNIX system, you might get a core dump'.

My question is should I get a core dump for division by zero errors on Linux (and Ubuntu in particular)?  Right now it just says floating point exception

Does it depend on the settings of the particular distribution?  I did notice in other threads that core dumps can be disabled. What is the rationale for some doing it and some not?  Simply to save storage space?

I feel I should add a little disclaimer saying that I'm not looking for instructions to enable core dumps, I did notice that there were already several threads about that.  Just looking to understand generally what sort of conditions normally generate them.

---

### Post by LaRoza on 2008-05-15
> **HunterSBuntu said:**
> I'm practicing my C++ programming and the book I'm reading presents an exercise which intentionally causes a divide by zero error to illustrate the concept of run time errors.  In the description of the example the author says 'On a UNIX system, you might get a core dump'.

My question is should I get a core dump for division by zero errors on Linux (and Ubuntu in particular)?  Right now it just says floating point exception

Does it depend on the settings of the particular distribution?  I did notice in other threads that core dumps can be disabled. What is the rationale for some doing it and some not?  Simply to save storage space?


That is a very vague statement of the author. Here is what a core dump is: [http://en.wikipedia.org/wiki/Core_dump](http://en.wikipedia.org/wiki/Core_dump)

---

### Post by Mr A Mouse on 2008-05-15
> **HunterSBuntu said:**
> Does it depend on the settings of the particular distribution?

More specifically, it depends on how the distro is built.

The purpose of a core dump is to give you a partial image of the memory state at the moment in time that something went sproing. It's intended to be a diagnostic tool, so you can find the error and correct it--this was used when compilers were not made to try to catch coding errors, and sometimes you would run what looked like terrific code only to find that your code was a train wreck.

Nowadays, compilers are much more efficient not only at finding errors, but at telling you where they are and what error was made. Core dumps have only limited usefulness today.

---

### Post by pmasiar on 2008-05-16
Modern languages have exception handling for that. Coredumping on trivial error is like buing groceries in a tank. Stacktrace is much more useful when analyzing cause of error. That books seems strange.

BTW if you are programming beginner, C++ is overkill. You can learn be decent Python hacker in 1/10 time than it takes to learn C++.

---

### Post by HunterSBuntu on 2008-05-20
Thanks for the info everyone, much appreciated.


> BTW if you are programming beginner, C++ is overkill. You can learn be decent Python hacker in 1/10 time than it takes to learn C++.

I'm not a total beginner, I've got a good handle on the syntax and all that.  I'm at that stage in my programming learning where it's more the design phase that stumps me, not the actual coding.  I get caught in an endless cycle of analyzing the problem and thinking about all the different ways to solve the problem.  So I figured I'd go back and work through the exercises in some books to just practice it.

I have been meanign to pick up Python though :)

---

### Post by stroyan on 2008-05-20
The floating point side of this matter is covered by "man fenv" and related
manual pages.  There are functions that control how floating point
exceptions behave.  The feenableexcept() and fedisableexcept() functions
can be used to decide whether specific floating point events will raise a
SIGFPE signal.  It is also possible to change the handling of fatal signals
like SIGFPE with the sigaction() function and other related functions.
(But masking out or handling some fatal functions like SIGFPE can result
in an infinite loop as the cause of the signal repeats again and again.)

The prctl() function can limit core dumping on linux.  The setrlimit()
function and related shell ulimit builtin can limit core file size or
prevent core files from being written.  Ubuntu includes the apport
package which uses /proc/sys/kernel/core_pattern to insert the python
script /usr/share/apport/apport into the handling of core dumps.  Each
core image is actually piped to that script.  It may then create a core
file or create a crash report under /var/crash/.  The behavior is
configured by /etc/default/apport.

---

### Post by Cracauer on 2008-05-20
Whether you get a coredump or not is determined by the `ulimit -c` setting. On most modern Unix systems for end users it is set to 0 by default, which disabled coredumps.

Dealing with this in Unix/C is usually done by setting a SIGFPE handler and have that signal handler longjmp to some upstream location that you designated for that by using setjmp.

---

