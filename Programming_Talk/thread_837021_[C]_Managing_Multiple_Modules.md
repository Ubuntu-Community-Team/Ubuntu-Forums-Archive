---
title: "[C] Managing Multiple Modules"
date: 2008-06-22
forum: Programming Talk
---

### Post by ankursethi on 2008-06-22
I'd posted a question here a few days ago asking what I should do next after having learned basic C and Python. I've followed the advice most people gave me and picked up a good data structures book.

Now my programs are getting larger and managing huge source files is getting tough. I need to know how to use multiple files. After poking around for a while and looking at other people's code, I found these two methods :

1. #include all the *.c files in the file containing the main function.

2. Create header files containing function and global declarations for all the *.c files. Create object files for each C source file. Then #include the header files in the file containing main, compile it and link it with the object files.

Which method should I follow? Or is there any other procedure for managing multiple files?

---

### Post by Tony Flury on 2008-06-22
I would absolutely go down the Header file and code file system. Including all the *.c in your main program seems like a real nightmare to me.

The challenge with multiple *.c files is that your make file will need to include each one to make sure they are compiled and linked correctly.

With your header files - make sure you prevent duplicate definitions by using :
```

#ifdef _HEADER_
#define _HEADER_
<<< declarations >>>
#endif 

```

if you define different macros in each header file - you can easily control multiple header files, and ensure that each *.c file has access to all the definitions and declaration it needs.

I don't know what IDE you are using, but I imagine many IDEs will include those definitions in their file template - I know the Anjuta does.
-- 
Tony Flury

---

### Post by nvteighen on 2008-06-22
The best is what Tony has told you + learning how to use Makefiles. So, if you only changed one module, you only recompile that module and the final executable instead of compiling all modules again each time.

This link may be very useful: [http://crasseux.com/books/ctutorial/Putting-a-program-together.html#Putting%20a%20program%20together](http://crasseux.com/books/ctutorial/Putting-a-program-together.html#Putting%20a%20program%20together)

---

### Post by JupiterV2 on 2008-06-22
Not much else to say but drop the underscore prefix when defining a header name as that naming scheme is used by the standard libraries and you run the risk (as I have done) of using the same name. It will cause you all kinds of grief you don't need.

#define MYHEADER_H (use this style)

vs.

#define _MYHEADER_H (avoid)

---

### Post by WW on 2008-06-22
FYI: The buzz word for what Tony Flury and JupiterV2 are talking about is [#include guard](http://en.wikipedia.org/wiki/Include_guard).

---

