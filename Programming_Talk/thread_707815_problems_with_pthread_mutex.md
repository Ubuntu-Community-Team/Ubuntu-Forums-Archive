---
title: "problems with pthread_mutex"
date: 2008-02-25
forum: Programming Talk
---

### Post by sgrantham on 2008-02-25
Before I report this a a bug, has anyone had problems in gutsy with pthread_mutex's.  I tried to add one to an application I'm writing, which is already successfully threaded through the use of the pthread library.  But I get all sorts of strange "bad memory" references when trying to use the pthread mutexs.  Some of it I can't even get to compile.  For instance, trying to compile just the basic hello world program with the addition of a reference to pthread_mutex_attr_t won't compile:

#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

**pthread_mutex_attr_t tmp;  // This should have not problem compiling**

int main(int argc, char *argv[])
{
  pthread_mutextattr_init(&tmp);

  printf("Hello, world!\n");

  return EXIT_SUCCESS;
}

give the compile error (at the commented line):

       expected '=', ',', ';', 'asm' or '__attribute__' before 'tmp'

and trying....

#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

**struct pthread_mutex_attr tmp; // this should also compile unless a macro called**

int main(int argc, char *argv[])
{
  pthread_mutextattr_init(&tmp);

  printf("Hello, world!\n");

  return EXIT_SUCCESS;
}

give the compile error (at the commented line):

             storage size of 'tmp' isn't known

Is this a bug in the distribution or have I just done something stupid?

Anybody?

---

### Post by aks44 on 2008-02-25
FWIW the errors you got simply mean that the compiler has no knowledge of this type.

A google search for the function you use (pthread_mutexattr_init) would have given you the function's signature, which uses **pthread_mutexattr_t** (note the "missing" underscore). ;)

---

### Post by uljanow on 2008-02-25
*deleted*

---

### Post by sgrantham on 2008-02-25
> **aks44 said:**
> FWIW the errors you got simply mean that the compiler has no knowledge of this type.

A google search for the function you use (pthread_mutexattr_init) would have given you the function's signature, which uses **pthread_mutexattr_t** (note the "missing" underscore). ;)

Of course I searched the internet and what I found was **with** the underscore on the declaration (as opposed to your reference which is the function call.)

For example @ IBM: [http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.genprogc/doc/genprogc/mutexes.htm](http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.genprogc/doc/genprogc/mutexes.htm)
 
and in the O'Reilly book "pthreads".

Both credible sources.  But thanks, I should have gone to the standard.  You were correct in as fashion.

---

### Post by aks44 on 2008-02-26
> **sgrantham said:**
> Of course I searched the internet and what I found was **with** the underscore on the declaration (as opposed to your reference which is the function call.)

For example @ IBM: [http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.genprogc/doc/genprogc/mutexes.htm](http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.genprogc/doc/genprogc/mutexes.htm)

What's even more strange in this link is that in the first part of the page ("Mutex Attributes Object") they spell it without the underscore, and after that they spell it with the underscore. Bravo IBM... :-k


Anyway I was not implying you didn't do any research, I was just pointing out how I found it in a few clicks. No hard feelings. :)

---

