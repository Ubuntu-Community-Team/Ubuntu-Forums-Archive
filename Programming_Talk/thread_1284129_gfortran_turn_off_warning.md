---
title: "gfortran turn off warning?"
date: 2009-10-06
forum: Programming Talk
---

### Post by butsam on 2009-10-06
I am having a hard time finding the option (if it exists) in gfortran to turn off a warning.

Specifically, I like using '-Wall' in general, but in gfortran that results in a complaint for every tab. This is annoying and is the one warning I am willing to ignore.

Is there an easy way to disable the silly "nonconforming tabs" warning? I understand it is technically nonconforming but I will take the chance that most computers I will encounter understand what pressing the tab key means.

---

### Post by butsam on 2009-10-06
I actually just found out the solution to my own problem, finally, after long searching.

For the benefit of others, if you use:

-Wall -Wtabs

Then all warnings will be enabled, except the silly nonconforming tab warning.

I do have another question, though. Using -Wall -Wtabs, I do not get warned when assigning a variable with another variable which is uninitialized. Is there a way to enable such a warning in gfortran?

---

### Post by MadCow108 on 2009-10-06
-Wuninitialized should do it

---

### Post by butsam on 2009-10-06
That worked, although you also need to use -O with -Wuninitialized (the compiler warns of that).

One of these days, I'm going to do gfortran a service and update their manpage, which doesn't include any of this information about -Wuninitialized. :)

(I am a little shocked -Wall does not turn on warnings for uninitialized variables, but there may be a good reason for this.)

---

### Post by MadCow108 on 2009-10-06
you have to look in manpages of gcc and gfortran as noted in the gfortran manpage:
> 
The gfortran command supports all the options supported by the gcc command. Only options specific to gfortran are documented here.


---

### Post by butsam on 2009-10-06
I guess the confusing thing for me was that -Wall in C or C++ using the GNU compiler suite does warn of uninitialized variables used in assignment statements, but in gfortran, -Wall does not do this, and there is no mention that -Wuninitialized -O will give the desired behavior. Since this behavior of -Wall differs from the standard gcc behavior of -Wall, it seems like a brief mention is warranted in the gfortran manpage.

That said, I am very grateful in general to the gcc suite of compilers, and to the fabulous Ubuntu community, to help me when I have a mental block and can't understand English ;)

---

