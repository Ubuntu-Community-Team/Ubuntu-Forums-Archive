---
title: "I want to &quot;speak&quot; a new language"
date: 2006-01-05
forum: Programming Talk
---

### Post by otey on 2006-01-05
Hi

I know PHP, but where does that leave me, when i want to write some of them cool textbaced linux programs. I want to learn some of the heavy stuff :p 

I've been looking at some "c" but I don't know where to start. I found this tutorial though. [http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html](http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html)

but i'm a little confused..

When i try to compile the first example with gcc, i get errors. 

The example is: 
```
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}
```

The errors are:
```
otey@osys:~/otey_development/c$ gcc hello.c
hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function 'main':
hello.c:5: warning: incompatible implicit declaration of built-in function 'printf'
hello.c:4: warning: return type of 'main' is not 'int'
```

If i replace #include < stdio.h> with #include <stdio.h> i get some of the same errors, but the code is compiled to an a.out file.

Should i 
a) Proceed with the tutorial, and just remove the whitespace in every #include thingee
b) Get a new tutorial somewhere
c) Correct something on my system 
d) Forget about the stupid idea about programming, and go back to bed

Hope to get answers

---

### Post by kairu0 on 2006-01-05
The About.com tutorial isn't bad: [http://cplus.about.com/od/beginnerctutoria1/l/blctut.htm](http://cplus.about.com/od/beginnerctutoria1/l/blctut.htm)

And C compiles the binary as a.out when you don't specify an output file.

Try:

```
gcc hello.c -o hello
```

---

### Post by skirkpatrick on 2006-01-05
Something isn't right with your tutorial.  There should be no whitespace between < and > in the include.

Since you didn't tell gcc what to call your resulting executable file, it defaults to a.out.  You can run it by using **./a.out** from the commandline.  Also, you can specify it when you compile it: **gcc -o hello hello.c**

---

### Post by m87 on 2006-01-05
[quote=otey] If i replace #include < stdio.h> with #include <stdio.h> i get some of the same errors, but the code is compiled to an a.out file.

Should i 
a) Proceed with the tutorial, and just remove the whitespace in every #include thingee
b) Get a new tutorial somewhere
c) Correct something on my system 
d) Forget about the stupid idea about programming, and go back to bed

Hope to get answers[/quote] 
you will still get this warning
```
hello.c:4: warning: return type of 'main' is not 'int'
``` but you should definitely change tutorial, I don't have any suggestions, though :confused:
and don't give up! :)

---

### Post by Burke on 2006-01-05
The reason for the return type error is that The newer revisions of C don't support a return type of void for main.  You'll have to use "int main" instead.  Then as the last statement inside your curly braces put "return 0;". I'll find a good tutorial for you and post it here in a few.

---

### Post by Burke on 2006-01-05
Here's a great one.  Its what I used to get started:

[http://www.cprogramming.com/tutorial/lesson1.html](http://www.cprogramming.com/tutorial/lesson1.html)

That's actually C++, which I would recommend over C any day. The only real difference is that you'll use g++ in place of gcc.

You'll probably get bogged down a few lessons in, but as has already been said, don't give up. C++ is one of the best things you'll ever learn. 

And if you want cool Linux textbased programs, I would consider Perl as well...

---

### Post by bored2k on 2006-01-05
For C && C++, I have been reading [The C Programming Language]("http://www.amazon.com/gp/product/0131103628/002-6053480-3710439?v=glance&n=283155") and [Teach Yourself C++ in 21 Days]("http://www.amazon.com/gp/product/0672327112/qid=1136521279/sr=2-2/ref=pd_bbs_b_2_2/002-6053480-3710439?s=books&v=glance&n=283155").

---

### Post by Burke on 2006-01-06
I would recommend the same.  Then once you've got a bit of experience under your belt, spring for a copy of the C++ programming language. IMO, its one of the very best.

---

### Post by otey on 2006-01-06
Thank you for your answers.. I forgot to ask if I should learn C or C++, but you answered that anyway.. Thank you!

---

### Post by thumper on 2006-01-06
Book wise I think that the best one to learn C++ from is "Accelerated C++" by Koenig and Moo.

Bjarne's "C++ programming language" I didn't find as useful as "The C++ Standard Library: A Tutorial and Reference" by Nicolai Josuttis.  I have a copy, but I don't tend to refer to it.  It's not even on my desk at work :)

---

### Post by noob_Lance on 2006-01-06
it should be int main() {} 
yes its stupid... but jsut do it and it should work

---

### Post by otey on 2006-01-06
[QUOTE=noob_Lance]it should be int main() {} 
yes its stupid... but jsut do it and it should work[/QUOTE]

Works now. But don't think i should continue with the tutorial. But thanks anyway

---

