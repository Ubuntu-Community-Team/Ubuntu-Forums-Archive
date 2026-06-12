---
title: "C++ string corruption"
date: 2009-07-26
forum: Programming Talk
---

### Post by Xegeth on 2009-07-26
Hi,

I've recently started programming on ubuntu and I've been having some trouble with strings. When a string is passed into a function, it becomes corrupted. Here is an example of the problem:

```

#include <string>

std::string stringTest(std::string input)
{
    return input;
}
int main( int argc, char** argv )
{
    std::string new_input = "Testing";
    stringTest(new_input);
}

```If I run a debugger, it shows that the string is "\02424un\210..." while inside stringTest. This problem only started earlier today, after the IDE crashed. Does anyone have any advice on how to fix this?

---

### Post by dwhitney67 on 2009-07-26
I do not see a problem with the code, other than it is inefficient.  You should declare your function to receive the parameter as a reference, and if you have no plans to modify it, then declare it as const.

For example:
```

#include <string>
#include <cassert>

std::string stringTest(const std::string& input)
{
   return input;   // btw, what's the point of this?
}

int main()
{
   std::string str = "test";

   assert(str == stringTest(str));
}

```

---

### Post by Xegeth on 2009-07-26
I am aware that the code is inefficient. I was just attempting to show the shortest example of the problem that I could. The return input line was just included so I could easily set a breakpoint there.

After trying your code, I've found that references are the only way of accessing the strings that does actually work. The debugger says it can't resolve (null)c_str if a pointer is used.

It looks like the problem may be with the packages but reinstalling both code::blocks and the standard GNU development libraries did nothing.

---

### Post by c0mput3r_n3rD on 2009-07-26
Are you missing the iostream header file?

---

### Post by Xegeth on 2009-07-26
I've just recompiled it with <iostream> but it made no difference.

---

### Post by MadCow108 on 2009-07-26
are you using gdb correctly?
debug it with cout's and see if that gives correct results.

---

### Post by dwhitney67 on 2009-07-26
> **Xegeth said:**
> I am aware that the code is inefficient. I was just attempting to show the shortest example of the problem that I could. The return input line was just included so I could easily set a breakpoint there.

After trying your code, I've found that references are the only way of accessing the strings that does actually work. The debugger says it can't resolve (null)c_str if a pointer is used.

It looks like the problem may be with the packages but reinstalling both code::blocks and the standard GNU development libraries did nothing.
If you are able to compile and successfully run the example program I provided, I would say that your development package(s) are A-Ok.

---

### Post by stair314 on 2009-07-26
There's no reason including <iostream> should make a difference, except that it will enable you to use cout. I think madcow is right, you probably are just misunderstanding gdb's output. If you use cout I think you will find the string is not corrupted.

---

### Post by Xegeth on 2009-07-26
I've just reinstalled gdb the problem seems mostly fixed now. I'm running it using code::blocks and it seems to work correctly now except for still not being able to read strings in the Function Arguments section. This does not seem to be too much of a problem because the local variables can be read and the code does run normally.

Thank you for your help.

---

### Post by Sockerdrickan on 2009-07-27
Who says the string is corrupted when you don't even print it...

---

### Post by Xegeth on 2009-07-27
I have tried printing the strings. That's what showed me that it was the debugger that wasn't working properly. Since the compiler is working, I think I'll just not bother fixing the debugger.

---

