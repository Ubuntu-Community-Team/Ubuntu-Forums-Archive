---
title: "sched.h - INIT_TASK(tsk) - kernel programming/syntax question"
date: 2009-05-26
forum: Programming Talk
---

### Post by MoToR on 2009-05-26
Hi, everyone,

I've got an assignment to add some functionality to a linux kernel in educational purposes.

I need to add a new processes group management functionality to the kernel. In order to do so, among some other things, I need to add a field to the **task_struct** structure in the file **sched.h** and therefore I need to update **INIT_TASK** (sched.h file) definition to initialize my added fields during system initialization.

I added new fields to the **task_struct** and went to update the **INIT_TASK** macro. Unfortunately I've met a C syntax there that I found somewhat difficult to comprehend:

```
482 #define INIT_TASK(tsk)  \
483 {                                                                       \
484     state:              0,                                              \
485     flags:              0,                                              \
486     sigpending:         0,                                              \
487     addr_limit:         KERNEL_DS,                                      \
488     exec_domain:        &default_exec_domain,                           \
489     lock_depth:         -1,                                             \
490     counter:            DEF_COUNTER,                                    \
491     nice:               DEF_NICE,                                       \
492     policy:             SCHED_OTHER,                                    \
493     mm:                 NULL,                                           \
494     active_mm:          &init_mm,                                       \
495     cpus_runnable:      ~0UL,                                           \
496     cpus_allowed:       ~0UL,                                           \
497     run_list:           LIST_HEAD_INIT(tsk.run_list),                   \
498     next_task:          &tsk,                                           \
499     prev_task:          &tsk,                                           \
500     p_opptr:            &tsk,                                           \
501     p_pptr:             &tsk,                                           \
502     thread_group:       LIST_HEAD_INIT(tsk.thread_group),               \
503     wait_chldexit:      __WAIT_QUEUE_HEAD_INITIALIZER(tsk.wait_chldexit),\
504     real_timer:         {                                               \
505         function:               it_real_fn                              \
506     },                                                                  \
507     cap_effective:      CAP_INIT_EFF_SET,                               \
508     cap_inheritable:    CAP_INIT_INH_SET,                               \
509     cap_permitted:      CAP_FULL_SET,                                   \
510     keep_capabilities:  0,                                              \
511     rlim:               INIT_RLIMITS,                                   \
512     user:               INIT_USER,                                      \
513     comm:               "swapper",                                      \
514     thread:             INIT_THREAD,                                    \
515     fs:                 &init_fs,                                       \
516     files:              &init_files,                                    \
517     sigmask_lock:       SPIN_LOCK_UNLOCKED,                             \
518     sig:                &init_signals,                                  \
519     pending:            { NULL, &tsk.pending.head, {{0}}},              \
520     blocked:            {{0}},                                          \
521     alloc_lock:         SPIN_LOCK_UNLOCKED,                             \
522     journal_info:       NULL,                                           \
523 }
```

(the numbers on the left are just a line numbering from the TOMOYO Linux cross reference, see links below)


I would be very thankful if someone could clarify how exactly does **INIT_TASK(tsk)** work, what does its syntax mean and where can I learn more about this.

As far as I was able to understand, these are designated initializers, but why colons? Why not .field syntax? What am I missing?

If we look inside **init_task.c** we'll find something like:
```
__asm__(".section \".text\",#alloc\n");
union task_union init_task_union =
                { INIT_TASK(init_task_union.task) };
```

Why do we initialize a union with so many fields? Isn't only the first field used for that?

Any explanation of how exactly these lines work will be most appreciated.

Thank you!



P.S. The next cross reference might be helpful if you don't have time or opportunity to look inside your distribution source files:

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/include/linux/sched.h?v=linux-2.4.37.1-ccs-1.6.7#L482](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/include/linux/sched.h?v=linux-2.4.37.1-ccs-1.6.7#L482)

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/arch/sparc/kernel/init_task.c?v=linux-2.4.37.1-ccs-1.6.7#L19](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/arch/sparc/kernel/init_task.c?v=linux-2.4.37.1-ccs-1.6.7#L19)

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/ident?v=linux-2.4.37.1-ccs-1.6.7&i=INIT_TASK](http://tomoyo.sourceforge.jp/cgi-bin/lxr/ident?v=linux-2.4.37.1-ccs-1.6.7&i=INIT_TASK)

Thanks to the guys that provided the reference.

---

### Post by MoToR on 2009-05-27
* bump *

By the way explanation in any level of complexity below the original will be welcome. I'm not a beginner in C, so to speak.

---

### Post by MoToR on 2009-05-30
No replies in three days.

That's just sad.

Well I figured out the second question, and I understood what the first code does, I'd just like to know what syntax is used in the first piece of code. The colon thing is undocumented.

---

### Post by MoToR on 2009-06-02
* bump *

---

### Post by hod139 on 2009-06-02
> **MoToR said:**
> No replies in three days.

That's just sad.

Well I figured out the second question, and I understood what the first code does, I'd just like to know what syntax is used in the first piece of code. The colon thing is undocumented.

The "colon thing" is a gcc extension to the C language (C89 standard anyways) that allows you to use element labels to initialize a union ([http://gcc.gnu.org/onlinedocs/gcc-4.4.0/gcc/Designated-Inits.html#Designated-Inits](http://gcc.gnu.org/onlinedocs/gcc-4.4.0/gcc/Designated-Inits.html#Designated-Inits))

---

### Post by MoToR on 2009-06-02
Awesome! Thank you for your reply! I've found tons of useful info at that page.

To sum up the thread, here's the explanation I was looking for of the syntax, as can be found on the page you guided me to:

> ...
In a structure initializer, specify the name of a field to initialize with `fieldname:' before the element value. For example, given the following structure, 

[INDENT]struct point { int x, y; };[/INDENT]


the following initialization 

[INDENT]struct point p = { y: yvalue, x: xvalue };[/INDENT]

 
is equivalent to 

[INDENT]struct point p = { xvalue, yvalue };[/INDENT]

 
Another syntax which has the same meaning is `.fieldname ='., as shown here: 

[INDENT]struct point p = { .y = yvalue, .x = xvalue };[/INDENT]

 
You can also use an element label (with either the colon syntax or the period-equal syntax) when initializing a union, to specify which element of the union should be used. For example, 

[INDENT]union foo { int i; double d; };[/INDENT]

[INDENT]union foo f = { d: 4 };[/INDENT]

 
will convert 4 to a double to store it in the union using the second element. By contrast, casting 4 to type union foo would store it into the union as the integer i, since it is an integer.
...


Thank you again! That was very helpful.

---

