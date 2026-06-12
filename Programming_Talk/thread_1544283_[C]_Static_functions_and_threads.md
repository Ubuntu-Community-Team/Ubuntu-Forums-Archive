---
title: "[C] Static functions and threads"
date: 2010-08-02
forum: Programming Talk
---

### Post by dawwin on 2010-08-02
Is this safe to use static functions in threads? (for example "static int doit()") 
Is there something except static/global variables and standard thread-unsafe functions, what can make my function thread-unsafe?

---

### Post by worseisworser on 2010-08-02
> **dawwin said:**
> Is this safe to use static functions in threads? (for example "static int doit()") 

Hm. The `static' keyword in a C context doesn't "mean" anything in particular in relation to threads and thread safety.


> **dawwin said:**
> Is there something except static/global variables and standard thread-unsafe functions, what can make my function thread-unsafe?

[http://en.wikipedia.org/wiki/Thread_safety#Identification](http://en.wikipedia.org/wiki/Thread_safety#Identification)

---

### Post by napsy on 2010-08-02
Using static on functions means the function scope is limited to that source file and is not exported.

---

### Post by rnerwein on 2010-08-02
> **dawwin said:**
> Is this safe to use static functions in threads? (for example "static int doit()") 
Is there something except static/global variables and standard thread-unsafe functions, what can make my function thread-unsafe?
hi
i think the kind of programming thread is to get rid of static and/or global functions. about the thread save
functions you have to use: man -k thread save to be on the real road of the road. 
my experince is - sorry: don't use threads on the systen s we now get. never endeing power abaout the
memory - disk space to get grazy ..... :  have a look at the apache server ( sqawm child processes ) - works perfekt for me.
why ??? ---> you got limiteds per processs ( a thread is one process !!! ). 
but my last commet is --> muluti threading can be a ticket to helll.
ciao

---

### Post by dwhitney67 on 2010-08-02
> **rnerwein said:**
> hi
i think the kind of programming thread is to get rid of static and/or global functions. about the thread save
functions you have to use: man -k thread save to be on the real road of the road. 
my experince is - sorry: don't use threads on the systen s we now get. never endeing power abaout the
memory - disk space to get grazy ..... :  have a look at the apache server ( sqawm child processes ) - works perfekt for me.
why ??? ---> you got limiteds per processs ( a thread is one process !!! ). 
but my last commet is --> muluti threading can be a ticket to helll.
ciao
Were you in the tunnel last week?  Somebody step on your head?  What are you babbling about?

---

### Post by MadCow108 on 2010-08-02
> **worseisworser said:**
> Hm. The `static' keyword in a C context doesn't "mean" anything in particular in relation to threads and thread safety.


he probably confused it with static local variables.
These do make a function non-threadsafe (if they are not protected somehow)

The three meanings of static depending on context:
```

static int global_variable;
static int function(void() {}
//the global_variable and function symbol is not exported to other
// object files (you'll get an undefined reference when linking)
// this has nothing to do with thread-safeness, this is just used to
// reduce scope and can be helpful for compiler optimizations

/* --------------- */

int function(void) {
  static int a;
  return a++;
}
//here static is a single memory location used by each call to function
// thus it is a kind of local scope "global" variable
// this is not threadsafe, but it can be made so by e.g. using mutexes or atomic operations

/* ------------------ */
/C++ only

class Class {
  static int function(void) {
     return a++;
  }
  static int a;
};
static int Class::a = 5;
// static member function, can be called without an instance of the object 
// => similar to a normal function, but has access to static members of the class (here: a)
// the use of a static member makes it non-threadsafe again if not protected


```

---

### Post by rnerwein on 2010-08-03
> **dwhitney67 said:**
> Were you in the tunnel last week?  Somebody step on your head?  What are you babbling about?

hi
sorry i only want to tell people what they sehll do and i wasn't in a tunnel last week.
but i want to tell other people is that they have to be very carefull ( may be my english is not so good)
using threads if they must do it. ( and  i am sure you aint't know the difference of one and 128 processors - programming threads - much fun !!! )
on the other side i can tell you - the only ( nearly ) perfect handling of thread is where they are come from
and that is sun solaris ( not pthreads in linux ) - no more comment.
ciao:(

---

### Post by donsy on 2010-08-03
> **rnerwein said:**
>  may be my english is not so good

Your English is just fine. I don't know German so you're way ahead of me. Shame on you dwhitney67.

---

