---
title: "Prevent GCC from fixing my Mistakes"
date: 2016-04-19
forum: Packaging and Compiling Programs
---

### Post by 3djake on 2016-04-19
Hi there

How do I stop GCC from fixing my mistakes? It seems that the version of GCC that comes with Ubuntu tries to fix mistakes, this is bad for academic reasons. If I make a mistake and it successfully compiles regardless without warnings and runs as expected, I  might hand  in the assignment thinking my program is finished and it might not compile for my Professor and I will lose some marks.

As an example if I did not declare all my function prototypes then it should not even compile or it should at least be giving me warnings but instead GCC is not complaining and is successfully compiling my programs.

How do I turn these features off?

Thanks, 
Regards, Jake.

---

### Post by 3djake on 2016-04-19
I found the solution, for future people who come across this thread I will post the solution.

the argument 
-Wall
This enables all the warnings about constructions that some users consider questionable, and that are easy to avoid.
This argument enables and disables lots of flags that some compilers have as default, such as the version of Windows GCC that some universities use, regardless we want to write good code and get better at programming so we do not want GCC to ignore our mistakes because we will not learn anything. 
-Werror
Turns all warnings into errors(Your program will not compile if something is wrong).

To make these default I used an alias
alias gcc='gcc -Wall -Werror -pedantic -std=c99'

---

