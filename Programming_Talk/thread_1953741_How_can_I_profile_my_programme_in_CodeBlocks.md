---
title: "How can I profile my programme in CodeBlocks ?"
date: 2012-04-06
forum: Programming Talk
---

### Post by DaviesX on 2012-04-06
If I have written a programme and I want to optimize the algorithm. But I want to know which module consumes most of the time. How can I profile the programme in CodeBlocks IDE ?

It seems that I have missed some plugins because it didn't do anything even if I have submitted the profile option.

Can you tell me how to fix it ? Thank you :popcorn:

---

### Post by Zugzwang on 2012-04-07
Short answer: Don't.

Long answer: Documentation for such stuff is a bit hard to find, as for every combination of programming language and IDE, the answer will be different, and in particular outdates quite soon.

However, there is no need for this. Profiling a program compiled with gcc/g++ is very simple even from the command line. So there is noting wrong with trying to do it without the IDE. You only need to follow three steps:

1. Compile your program with debug symbols. You can do so by compiling it  in debug mode.
2. Run your program form the terminal as follows: "valgrind --tool=callgrind ./your_program your_options"
3. View the results by invoking "kcachegrind callgrind.out.****", where **** is the process ID displayed by valgrind in the previous step.

You will see a nice GUI for analysing where most time is spent in your program. You might have to install the packages for "valgrind" and "kcachegrind" beforehand, however.

---

### Post by DaviesX on 2012-04-07
Thanks you very much ! I'll try it ! :-)

---

