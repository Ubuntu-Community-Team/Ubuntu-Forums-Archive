---
title: "c relational operator question"
date: 2016-03-08
forum: Programming Talk
---

### Post by shahin on 2016-03-08
Request: Please let me know if this question is too basic, and perhaps out of scope of this forum, and I won't post again 

I am brushing up on my C, and can not understand why I get the following output. Speciffically, I don't see how I get '0' for the '==' in my printf statement. The way I see it, I set x to equal 35. How come I get '0' when I print "x==35"?

Here is the code...

```
#include <stdio.h>
int main()
{
  int x=35, y=20;

     printf("\n%d %d %d", x==35, x=50, x>40);


}

```

Here is the output...

```
0 50 0
```

---

### Post by spjackson on 2016-03-08
Your problem is not with the relational operators. The order of function argument evaluation is undefined. It appears that in your case x=50 is being evaluated before x==35. If you compile with 'gcc -Wall' you will get a warning about this.

---

### Post by shahin on 2016-03-08
Thanks. I got this question from a C book, and the chapter covers the hierarchy of logical operators. However, I just do not see the order in which would give me the output I get. The book says the hierarchy is as follows
!
* / %
+ - 
< > <= >=
== !=
&&
||
=
So given the above order, the == sign should be processed befor =. How does x get the value of 50 before it is compared with 35 to result in the value of 0?

By the way, I did run gcc with the -Wall switch, and the output is below:

gcc -Wall  exc1c.c -o exc1
exc1c.c: In function &#8216;main&#8217;:
exc1c.c:6:35: warning: operation on &#8216;x&#8217; may be undefined [-Wsequence-point]
      printf("\n%d %d %d", x==35, x=50, x>40);
                                   ^
exc1c.c:6:35: warning: operation on &#8216;x&#8217; may be undefined [-Wsequence-point]
exc1c.c:4:13: warning: unused variable &#8216;y&#8217; [-Wunused-variable]
   int x=35, y=20;
             ^

How did you interpret these warning as an issue related to the order of processing though?

---

### Post by Rocket2DMn on 2016-03-08
I think the problem is that the two operations, although on the same line of code, are not part of the same logical expression. The order of operations only applies to terms in the same expression.  Alternatively, the compiler can optimize out the original assignment of x.

---

### Post by 1clue on 2016-03-08
If you assume that the printf is taking arguments  last to first, then your results make sense.

---

### Post by spjackson on 2016-03-08
> **shahin said:**
> 
By the way, I did run gcc with the -Wall switch, and the output is below:

gcc -Wall  exc1c.c -o exc1
exc1c.c: In function ‘main’:
exc1c.c:6:35: warning: operation on ‘x’ may be undefined [-Wsequence-point]
      printf("\n%d %d %d", x==35, x=50, x>40);
                                   ^
exc1c.c:6:35: warning: operation on ‘x’ may be undefined [-Wsequence-point]
exc1c.c:4:13: warning: unused variable ‘y’ [-Wunused-variable]
   int x=35, y=20;
             ^

How did you interpret these warning as an issue related to the order of processing though?
If you look at the gcc man page and search for -Wsequence-point you might get a clue.

---

### Post by trent.josephsen on 2016-03-08
> **Rocket2DMn said:**
> I think the problem is that the two operations, although on the same line of code, are not part of the same logical expression. The order of operations only applies to terms in the same expression.  Alternatively, the compiler can optimize out the original assignment of x.

You'd think that, but it's not true. Order of operations is determined by operator precedence, but order of *evaluation* is determined by sequence points. The usual example is something like

```
a[i] = i++;
```

(which has undefined behavior), but it's true of any expression. The most relevant C FAQ is probably [3.4](http://c-faq.com/expr/precvsooe.html). Also see [3.8](http://c-faq.com/expr/seqpoints.html) for a discussion of sequence points.

---

### Post by shahin on 2016-03-10
Thank you everyone. I read the FAQ  references, and the gcc man page. So it is my understanding that I see the output I do due to an ambiguity in C's evaluation order? But you see, this code is from Exercise A (g) from the book called Let us C. So I have to assume that there is an expected answer if the author put this in as a question. And that there is some reason for it. I do realize that by using '>' and "==", I introduced more sequence points. But do not you think there should be an expected answer? The book just says "what will the output of the following items?". I feel somehow I got to justify why I see the behaviour I see. I also had a look at [https://en.wikipedia.org/wiki/Sequence_point]("wiki/Sequence_point") .

---

### Post by shahin on 2016-03-10
@ jpjackson-You are absolutely right. Thank you so much. I got it now. At least, I can know when I am using code which is undefined and may result in different outputs.

---

### Post by spjackson on 2016-03-11
> **shahin said:**
> So it is my understanding that I see the output I do due to an ambiguity in C's evaluation order? But you see, this code is from Exercise A (g) from the book called Let us C. So I have to assume that there is an expected answer if the author put this in as a question. And that there is some reason for it.

All books contain mistakes; some books contain very many mistakes. Your assumption is only valid for the best quality books. I know nothing of this book or its author. The [Wikipedia page for the author]("https://en.wikipedia.org/wiki/Yashavant_Kanetkar")  says "His best-selling books include *Let Us C*, *Understanding Pointers In C* and *Test Your C Skills*. These books are specific to the long outdated Turbo C compilers, and do not contain reliable information on standard C language."
> 
 I feel somehow I got to justify why I see the behaviour I see.

When you have code that contains undefined behaviour as far as the C standards are concerned, as in your original post, there isn't much merit in justifying behaviour seen in one context, with one compiler, on one platform. You could perhaps look at the assembler code that the compiler generates and you may notice that, perhaps, the arguments are evaluated right to left. This might satisfy your curiosity, but it would be foolish to then assume that this will always be the case. Undefined behaviour is best avoided.

---

### Post by shahin on 2016-03-11
I really appreciate your feedback. I feel I got the understanding that I needed to move on. Thank you all for your patience and complete comments. 

Can I ask one final question please? Do you think I should continue to use the book I am, or perhaps visit the library for something more recent? I am a IT PhD student, and have access to a good variety of books. Do you recommend any other text? I do have a copy of K&R book

---

