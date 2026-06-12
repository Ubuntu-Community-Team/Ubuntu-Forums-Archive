---
title: "Using old C headers in C++"
date: 2007-10-03
forum: Programming Talk
---

### Post by glennr on 2007-10-03
I have some old C++ code which uses the old "std*.h" style headers and recent versions of g++ won't compile it.

Rather than change all of the headers to the new "c*" style, is there some other way to make it compile?

I couldn't find a command line switch but maybe there is one?

---

### Post by Wybiral on 2007-10-03
Despite being bad practice, I don't see why it wouldn't compile. Are you sure that's the problem?

---

### Post by dwhitney67 on 2007-10-03
Please provide an example of one of your source code modules that won't compile.  I would like to test it myself.

---

### Post by LaRoza on 2007-10-03
> **glennr said:**
> I have some old C++ code which uses the old "std*.h" style headers and recent versions of g++ won't compile it.


Give a little code, but I am thinking this "old C++" code isn't standard, at least, not now.

I have never had any problem compiling with g++ with stdio.h and friends.

---

### Post by glennr on 2007-10-03
That's what I thought too.

On further investigation, the issue is that the code uses strcpy() and includes <strings.h> but not <string.h> where strcpy is defined.

So that means I will have to change that.

Thanks for your help.

---

### Post by dwhitney67 on 2007-10-03
You should also change any instance of strcpy() to strncpy().

The use of strcpy() is not secure in the sense that it can be used to overrun a buffer, and hence the stack.  Many organizations that employ programming standards forbid the use of strcpy().

---

