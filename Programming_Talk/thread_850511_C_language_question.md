---
title: "C language question"
date: 2008-07-05
forum: Programming Talk
---

### Post by Gorgonkernel on 2008-07-05
:popcorn:I want to learn the c language, and i have some questions about it. I found out that in order to writte programs in C you need a compiler. If you know the language you can writte programs on every compiler or you have to change something at the program in order to make it run on that compiler? Also i have a book about C and c++ language and it is a bit old written by Khris Jamsa and Lars Klander can i still learn from it?
There is an example:
```
#include <stdio.h>
void main(void)
{
printf("This is an example");
}
```
Has the c language changed? I am asking that because a friend told me that now you writte <stdio> not <stdio.h>.
Sorry but i am a complete beginner in computer programming.
PS:Also some links to webpages that will help me in this quest of learning the c language will be great! Thanks very much and big congratulations for the Ubuntu project!

---

### Post by scragar on 2008-07-05
keep the .h, but there's nothing wrong with that code.

You can run C and C++ code using binfmtc which will compile when you try to run the program, handy for testing small programs(but bad for large programs). I can't help you any with a guide though.

---

### Post by LaRoza on 2008-07-05
> **Gorgonkernel said:**
> If you know the language you can writte programs on every compiler or you have to change something at the program in order to make it run on that compiler? 
A compiler translates the C into machine code. The compiler is used once (so to speak) the resulting program is then runnable on the platform for which it was compiled.

Using standard C will enable you to use C wherever you can find a standard C compiler.

> 
There is an example:
```
#include <stdio.h>
void main(void)
{
printf("This is an example");
}
```
Has the c language changed? I am asking that because a friend told me that now you writte <stdio> not <stdio.h>.

That code is non standard. The only difference is that main() returns and int. So:

```

#include <stdio.h>
int main(void)
{
    puts("Hello world");
    return 0;
}

```

Your friend is wrong. It is stdio.h. In C++, the *.h files were dropped and it would be cstdio, not stdio.

> 
Sorry but i am a complete beginner in computer programming.
PS:Also some links to webpages that will help me in this quest of learning the c language will be great! Thanks very much and big congratulations for the Ubuntu project!

The sticky and my wiki have everything you need.

---

### Post by henchman on 2008-07-05
At first: read the stickies :)

And no, probably the c standard hasn't changed that much. There are standard functions, which every standard compliant compiler has to bring with him. If you stick to these standard functions, you should be able to compile your program one more than one compiler.

You should really read about the differences between C and C++, where C++ is like "C with classes". all foobar.h headers are "c headers" and if you omit the .h, you will get the c++ header with exact the same functions. The only opposite is that they are wrapped into the std namespace.

Stick to the stickies for some good c/c++ tutorials :)

---

### Post by LaRoza on 2008-07-05
> **scragar said:**
> keep the .h, but there's nothing wrong with that code.


Er, yes there is. The code isn't valid anymore.

---

### Post by DoDoENT on 2008-07-05
see [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Although this tutorial is made for c++, it covers the basics of programming and is very good. I learned much of the c++ from this tutorial.

---

### Post by era86 on 2008-07-05
> **LaRoza said:**
> Er, yes there is. The code isn't valid anymore.

I'm sure the code will compile, but it does not follow standards.

---

### Post by CptPicard on 2008-07-05
> **Gorgonkernel said:**
> If you know the language you can writte programs on every compiler or you have to change something at the program in order to make it run on that compiler?

If you know the language you can write programs for every compiler *for that language*. The whole point of a compiler is to take a predefined language and then compile that into something else (such as machine code, which then runs on the CPU).

If you had to change something in your C code you would by definition no longer then be writing for a *C compiler*, but for a compiler for some other language.

(Mind you, there are some little inconsistencies between different compilers but the general point still holds)

> Also i have a book about C and c++ language and it is a bit old written by Khris Jamsa and Lars Klander can i still learn from it?

C and C++ are two different languages.

> 
Has the c language changed? I am asking that because a friend told me that now you writte <stdio> not <stdio.h>.

Your friend is confusing C and C++. Your example is C. Your friend is suggesting a way to use a header in C++.

To save pmasiar the trouble: Python is a much nicer language for a complete beginner.

---

### Post by LaRoza on 2008-07-05
> **henchman said:**
> 
You should really read about the differences between C and C++, where C++ is like "C with classes". all foobar.h headers are "c headers" and if you omit the .h, you will get the c++ header with exact the same functions. The only opposite is that they are wrapped into the std namespace.

C++ is much more than that. It is an entirely different language, with an entirely different ABI and is not at all like C.

> 
Stick to the stickies for some good c/c++ tutorials :)

C and C++, there is no C/C++.

I recommend to the OP to stick with C, rather than C++.

---

### Post by Gorgonkernel on 2008-07-05
Thanks very much for all the replies. Sorry if this was asked...next time i will do some investigations hehehe before posting something. I runned that example i posted here on turbo c++ lite and it works fine. But when i try on Dev-c++ holly mother of Linux...only errors. I will try to read all of the other posts. I think that the book i have about c language is not good anymore. 
Thanks very much and i hope after reading other posts and stickies i will learn to code in c correctly. If you have other suggestions or i don`t know please post them.

---

### Post by LaRoza on 2008-07-05
> **Gorgonkernel said:**
> Thanks very much for all the replies. Sorry if this was asked...next time i will do some investigations hehehe before posting something. I runned that example i posted here on turbo c++ lite and it works fine. But when i try on Dev-c++ holly mother of Linux...only errors. I will try to read all of the other posts. I think that the book i have about c language is not good anymore. 

Are you using Linux? Check out the sticky for step by step guides to compiling and running.

The internet is full of free resources. Eventually, you'll likely want to get K&R (if you don't know, google will help)

---

### Post by pmasiar on 2008-07-05
as a complete beginner to programming consider start with much more beginner-friendly language, like Python. You can learn syntax in shell one line at a time, and don't have to fight with types as hard as in C.

Just a thought, you are spending your own free time, do whatever makes sense to you.

---

### Post by Stshow on 2008-07-06
New Standard C++ code:

#include <cstudio>//plus a "c" in front of the "studio"


and i am Reading Thinking in C++

it is good for a beginner

---

### Post by LaRoza on 2008-07-06
> **Stshow said:**
> New Standard C++ code:


This is for C, not C++.

---

### Post by cmay on 2008-07-06
[http://computer.howstuffworks.com/c.htm](http://computer.howstuffworks.com/c.htm)
hi
i linked to a in my opinion nice c tutorial 
its not enough to master c language but good for a beginner.
good luck.

---

### Post by nvteighen on 2008-07-06
Ok, you want C. So forget anything related to C++ for a while. Repeat with me "C and C++ are two different languages".

The best C resource is, IMO, the GNU C Tutorial you can find here:
[http://crasseux.com/books/ctutorial/](http://crasseux.com/books/ctutorial/)

But, if you don't have any programming experience, you'll need a lot of time to first learn to program and then learn to program in C. The language is great and powerful, but the power it gives you requires a lot of responsability. (and a lot of manual work too)

That's why Python is usually recommended: it gives you a hand and helps you to focus on the problem.

I recommend you to look around some more programming languages and choose what you like more and what fits to your needs/goals. An informed decision is a way better than a blind one, no matter what language you finally choose.

---

### Post by pmasiar on 2008-07-06
> **Stshow said:**
> and i am Reading Thinking in C++

it is good for a beginner

... for some values of "beginner". :-)

Author mentions that TiC++ is **NOT** intro book to C++. Every advice you get on internet from strangers is worth double-checking.

---

