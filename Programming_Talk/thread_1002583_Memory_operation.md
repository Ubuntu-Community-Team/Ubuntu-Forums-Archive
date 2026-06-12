---
title: "Memory operation"
date: 2008-12-05
forum: Programming Talk
---

### Post by LlmL on 2008-12-05
I'm working on a large project concerning many memory operations.
Our program has got a "core.*" for many times. From the core information, I am sure that some invalid memory operation has coursed that. But the project is so complicated that reviewing codes costs too much time, besides, this program started up over 80 threads, and it seems that the "core" shows up irregularly. 
I am thinking about setting some "hooks" in the system memory operations like memcpy, malloc .etc. How can I do this? Should I rewrite & recompile the gnu libs?

---

### Post by samjh on 2008-12-05
I'm sorry, but I cannot understand what you're trying to say.

What is "core.*"?  What do you mean that you have it "many times"?  What do you mean by "hooks"?

---

### Post by iponeverything on 2008-12-05
> **samjh said:**
> I'm sorry, but I cannot understand what you're trying to say.

What is "core.*"?  What do you mean that you have it "many times"?  What do you mean by "hooks"?

His program is segfaulting and dumping a core. Do a man core or man signal.

@LlmL Its quite hard to debug an application if you can't reliably reproduce the condition.

---

### Post by thk on 2008-12-05
Take a look at valgrind and similar solutions.

---

### Post by Cracauer on 2008-12-05
> **LlmL said:**
> I'm working on a large project concerning many memory operations.
Our program has got a "core.*" for many times. From the core information, I am sure that some invalid memory operation has coursed that. But the project is so complicated that reviewing codes costs too much time, besides, this program started up over 80 threads, and it seems that the "core" shows up irregularly. 
I am thinking about setting some "hooks" in the system memory operations like memcpy, malloc .etc. How can I do this? Should I rewrite & recompile the gnu libs?

You are confused.

It's not the memory options that cause the segfaults that presumably are behind the core dumps. It is regular code messing in memory areas where it shouldn't.


As people have said, try a memory checker that introduces bounds guard VM pages.

---

### Post by LlmL on 2008-12-07
> **Cracauer said:**
> You are confused.

It's not the memory options that cause the segfaults that presumably are behind the core dumps. It is regular code messing in memory areas where it shouldn't.


As people have said, try a memory checker that introduces bounds guard VM pages.


What is memory checker/bounds guard VM pages?
How can I do that?

---

### Post by LlmL on 2008-12-07
> **thk said:**
> Take a look at valgrind and similar solutions.

Using valgrind slows down my program and it takes longer and is harder to reproduce this condition (possibly over one year).

---

### Post by wmcbrine on 2008-12-07
Yes, well, you should've tested it better as you were building it. Now it's harder. But you'll have to do the work, or be stuck with a buggy program. There's no magic shortcut.

Why are you using 80 threads, anyway?

---

### Post by LlmL on 2008-12-08
> **wmcbrine said:**
> Yes, well, you should've tested it better as you were building it. Now it's harder. But you'll have to do the work, or be stuck with a buggy program. There's no magic shortcut.

Why are you using 80 threads, anyway?

This program serves as a server for socket connections. Some of the threads are managing connections, some are dealing with package event. It has a large client population. We are trying to add memory hooks on these operations to solve it.

---

### Post by dwhitney67 on 2008-12-08
"Memory Hooks" to solve what?  If your application is crashing with a core dump, it is either because it is accessing memory at an illegal address (i.e. an area outside the program space), or because memory that has been allocated has been trampled on by some operation.

Typically it is the latter situation that occurs most often.  Here's a C++ example that compiles fine, but generates a segmentation violation when ran.

[php]
#include <iostream>
#include <cstring>

int main()
{
  char str[10] = {0};
  int* val1 = new int(5);
  int  val2 = 10;

  memcpy(str, "Hello World", 12);

  std::cout << "str  = " << str   << std::endl;
  std::cout << "val1 = " << *val1 << std::endl;
  std::cout << "val2 = " << val2  << std::endl;

  delete val1;

  return 0;
}
[/php]

Here the problem is with the copying of 12 bytes into a 10-byte array; this will cause a data overflow, which in turn affects the next variable (val1).

Anyhow, I do not know what effort was placed into developing your server application, but there probably is one thread to accept client connections, and then other threads to deal with client requests.  Each of the client request handling threads should be identical, thus it does not seem impossible for you to go back and review the code for some silly mistake a programmer may have made when performing a memory operation.

Off the top of my head, these are some of the operations you should look for:
malloc
memcpy
memset
strcpy (note, this function should never be used; use strncpy instead)
recv
recvfrom

Since the application crashes unpredictably, I would focus your attention on the threads that accept client data.  It is probably there where the issue lies.

---

### Post by wmcbrine on 2008-12-08
Really you have to look at every pointer dereference. And that includes every array access (a[b] is the same as *(a + b)).

---

### Post by nvteighen on 2008-12-08
> **LlmL said:**
> Using valgrind slows down my program and it takes longer and is harder to reproduce this condition (possibly over one year).

Well, take it or not.

Maybe you could try using a lab test suit? I mean, simulate your program in a smaller scale (reduce that 80 threads to, say, 3 or 4... that won't affect any memory related bug). First use **gdb** to check the conditions of your program just before the error occurs. Then use **valgrind** to detect where the error occurs and also where the memory was allocated (gdb will only tell you where the segfault occurs).

And take your conclusions... but I'd always use valgrind along with gdb. Never just valgrind.

---

### Post by Cracauer on 2008-12-09
Overrunning the stack can also cause segfaults.

I didn't use a checker for a while, but I spotted that OpenBSD's malloc(3) has a guard page option. That sounds like what is needed (not that the Op is still around :)).

Using just guard VM pages around malloc'ed blocks doesn't slow down normal progra operations at all. But of course it makes malloc itself an order of magnitude (or two) slower.

Of course, even if you have this and you get the segfault, then you still need gdb to debug it. Which is what you needed in the first place. The best course of action probably is to run the whole damn thing in gdb, as-is and wait for the segfault. If you are lucky it's a direct operation without previous corruption.

---

### Post by dribeas on 2008-12-10
See? you scared the poster :P

Now, seriously, since the poster does have cores, you can open the core with gdb and at least get a stact trace at the point where the program died. That helps figure what is wrong. Now it is usually much harder to detect what made it go wrong... or when

---

