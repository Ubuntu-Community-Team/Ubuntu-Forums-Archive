---
title: "How to Locate the Error Line in Eclipse"
date: 2009-04-21
forum: Programming Talk
---

### Post by huangyingw on 2009-04-21
hello, just forgive me for such a naiive queston, for I am a new bird just switching from Windows IDE.
I met problem when using eclipse to debug.
I am using eclipse+CDT to programe in Ubuntu environment.
For example, in vs IDE, I could simply start a debug action. And the programm would stop when an error occur. And what is more, the cursor would be located at the line that cause error.
This is useful for me to find the run time error.
While in eclipse, I am in lost to debug the run time error. When the IDE throw out errors, but I don't know the last line in code the program used to be running.
Could eclipse support this?

---

### Post by dwhitney67 on 2009-04-21
Step through the code, or better yet set a breakpoint (or two) where you think the code is breaking.

---

### Post by huangyingw on 2009-04-26
> **dwhitney67 said:**
> Step through the code, or better yet set a breakpoint (or two) where you think the code is breaking.
yes, thank you. For me, a little terrible and fresh experience with Eclipse:(.

---

### Post by dwhitney67 on 2009-04-26
I personally dislike Eclipse, but that is what my employer uses.  Of course, they do not require me to use it to develop code (I can use vim), but to integrate my code into the final product, I have to use Eclipse.

When debugging, Eclipse calls upon gdb for debugging.  You could do this yourself, or use 'ddd' or 'kdbg' as GUI front-ends.

The other thing you can do is to strategically place assert() statements in your code where you think there might be issues, such as when you access a pointer.  For example:

```

#include <assert.h>    // or <cassert> for C++

void function(const MyStruct* ms)
{
  assert(ms != 0);   // make sure ms is not null

  ms->field = 10;
  ...
}

```

---

### Post by huangyingw on 2009-04-28
> **dwhitney67 said:**
> I personally dislike Eclipse, but that is what my employer uses.  Of course, they do not require me to use it to develop code (I can use vim), but to integrate my code into the final product, I have to use Eclipse.

When debugging, Eclipse calls upon gdb for debugging.  You could do this yourself, or use 'ddd' or 'kdbg' as GUI front-ends.

The other thing you can do is to strategically place assert() statements in your code where you think there might be issues, such as when you access a pointer.  For example:

```

#include <assert.h>    // or <cassert> for C++

void function(const MyStruct* ms)
{
  assert(ms != 0);   // make sure ms is not null

  ms->field = 10;
  ...
}

```

Yes, thank you for pointing to a new way.

---

