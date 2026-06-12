---
title: "C/C++ precompiler code modification?"
date: 2012-02-29
forum: Programming Talk
---

### Post by scu-ba-de-buntu on 2012-02-29
I am trying to have my code self modify prior to compilation based on architecture, but a simple #ifndef will not work. I need the code to change the size of a hard-coded array based on a precompiler macro. I am using the GNU C/C++ Compiler package.

something like:

```
unsigned int8_t array[ _array_based_on_arch_macro(10) ] = _build_hardcoded_info_macro(10);

```
where this would make it at least a 10 dimensional array if possible.

Thanks!


---- PS ----
Shout out to firefox, since my computer crashed/died while writing this and it was back no problem after starting the machine again.

---

### Post by ofnuts on 2012-03-01
> **scu-ba-de-buntu said:**
> I am trying to have my code self modify prior to compilation based on architecture, but a simple #ifndef will not work. I need the code to change the size of a hard-coded array based on a precompiler macro. I am using the GNU C/C++ Compiler package.

#ifdef has been th lmethod of choice to handle architecture differences for the last 40 years,  so what makes you think it wouldn't work this time? How do you detect at compile time what the architecture is? What kind of architecture-dependent code are you generating?

---

### Post by scu-ba-de-buntu on 2012-03-04
My code needs to change various hard-coded aspects which cannot be handled at run time. I am aware of external solutions such as M4, Makefile and Bashscripts but I was really hoping that the GCC preprocessor could handle things like a simple loop.

Since I posted that I am now aware that GCC has a hard time with self-referals. As it will only try one iteration according to the documentation I read, so that work around is I guess out of the question.

Some docs I've read discuss something called metaprogramming / template programming, does that seem right to you?

---

### Post by MadCow108 on 2012-03-04
you still have not specified your problem properly.

From the sparse information you are giving I'm guessing yes the standard preprocessor can do replacement of constructs depending on arches, though the detection of architecture features must mostly be done by an external process (normally configure scripts).

metaprogramming is not really possible in C, you need e.g. C++ for some very ugly way of doing it, have a look at the boost mpl library and boost preprocessor library.
And have fun going crazy with completely unreadable error messages due to typos.

---

