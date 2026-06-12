---
title: "Code::Blocks build error"
date: 2014-01-03
forum: Programming Talk
---

### Post by jjclonker on 2014-01-03
I tried to build this in Code::Blocks:

```
#include <iostream.h>

main()
{
    cout << "Hello World!";
    return 0;
}

```

and I get this error:

```
Compiling: main.cpp
s: 1: s: Syntax error: Unterminated quoted string
Process terminated with status 2 (0 minutes, 0 seconds)
0 errors, 0 warnings
```

I am not sure why. Is it realy a Syntax error? If it is a syntax error could you give me a simple "Hello World" code to test my Code::Blocks program?=P~

Thanks ubuntu people for the increadible ubuntu OS!!!:KS

---

### Post by Bucky Ball on 2014-01-03
*Thread moved to **Programming Talk**.*

---

### Post by leg on 2014-01-03
[http://programmers.stackexchange.com/questions/127023/why-is-include-iostream-h-bad](http://programmers.stackexchange.com/questions/127023/why-is-include-iostream-h-bad)

Has this:

> The header iostream.h is a non-standard header and does not exist on all platforms. As a matter of fact it does not exist on my system (using g++ and the GNU libstdc++). So any code using it would simply not compile on my system.

The iostream.h header used to be common before C++ was first standardized in 1998. But since the 98 standard used <iostream> instead of <iostream.h>, the latter has fallen out of favor (being non-standard and all) and is no longer supported on all platforms. Code that uses it should be considered non-standard legacy code and is not portable. Books that teach it should be considered outdated and avoided.

So I suspect the compiler does not recognise the iostream as a header file and thinks it must be a unquoted string.

---

### Post by spjackson on 2014-01-03
A correct version of your code would be for example:
```

#include <iostream>

int main()
{
    std::cout << "Hello World!\n";
    return 0;
}

```
However, your error isn't coming from your code. "Syntax error: Unterminated quoted string" isn't coming from the compiler, it is coming from the shell. i.e. there is something wrong with your settings in Code::Blocks such that no code will compile. Check the configuration of your Code::Blocks project.

---

### Post by jjclonker on 2014-01-03
Sory Bucky Ball I am very new to the tread and did not know where to post it. :oops:

---

### Post by Bucky Ball on 2014-01-03
> **jjclonker said:**
> Sory Bucky Ball I am very new to the tread and did not know where to post it. :oops:

All good. Thought you might have more success here and looks like I was right. Good luck. ;)

---

### Post by jjclonker on 2014-01-03
spjackson how would I check Code::Blocks project configuration? Sory I am very new to progaming and the programs for programing. :)

---

### Post by jjclonker on 2014-01-03
Thanks Bucky Ball!!!:KS You guys are the best!!!

---

### Post by spjackson on 2014-01-03
> **jjclonker said:**
> spjackson how would I check Code::Blocks project configuration? Sory I am very new to progaming and the programs for programing. :)
I can't help much on that I'm afraid; I don't use Code::Blocks. However, if you look in the manual [http://www.codeblocks.org/docs/main_codeblocks_en.html](http://www.codeblocks.org/docs/main_codeblocks_en.html) , see section 1.11.6. There could be unterminated strings in the search paths or something. A google hit [http://forums.codeblocks.org/index.php/topic,8682.0.html](http://forums.codeblocks.org/index.php/topic,8682.0.html) shows a similar problem when the project path contains an apostrophe.

It is often stated in this forum that it is not a good idea for beginners to use an IDE because the IDE gets in the way and you can't see what's going on. I agree with this sentiment. Perhaps a Code::Blocks user might be able to help you some more.

---

### Post by jjclonker on 2014-01-03
YES!!!! spjackson your second link told me what the problem was.

 Never ever use apostophy's or spaces (or other symbols I am guessing) for the name of any directory that you want to build (or run).

Solved!!! :guitar::popcorn::KS

---

