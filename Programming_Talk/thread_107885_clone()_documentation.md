---
title: "clone() documentation"
date: 2005-12-24
forum: Programming Talk
---

### Post by scorpio2002 on 2005-12-24
Hi there! Do you know where I can find good documentation about the syscall clone()? I need a lot of examples and code... thx

---

### Post by m87 on 2005-12-24
# apt-get install manpages-dev
# man 2 clone

---

### Post by scorpio2002 on 2005-12-24
oh yeah, you're right... but manpages are very far from myconcept of good documentation :-)
I need help on how to create the stack area. The man pages don't say anything about that:

> The  child_stack  argument  specifies the location of the stack used by
       the child process.  Since the child and calling process may share  mem&#8208;
       ory,  it  is  not possible for the child process to execute in the same
       stack as the calling process.  The calling process must  therefore  set
       up memory space for the child stack and pass a pointer to this space to
       clone.  Stacks grow downwards on all processors that run Linux  (except
       the  HP  PA  processors),  so child_stack usually points to the topmost
       address of the memory space set up for the child stack.

so far so good. But it should've gone on explaining how to create that stack :| Shall I use malloc? plz help :-) I'd like an example, I can't find any on the web...

---

