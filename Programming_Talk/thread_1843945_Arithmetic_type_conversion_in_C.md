---
title: "Arithmetic type conversion in C"
date: 2011-09-14
forum: Programming Talk
---

### Post by tauh on 2011-09-14
Hi! For several days i have been struggling with a homework in C programming. I have Google it, my teacher wont answer my emails and the book i have doesn't talk that much about type conversions.

[IMG]http://i54.tinypic.com/2e5ingh.jpg[/IMG]

double a;
float b;
int c;

b / c? 
(long)a?
(long)a + b / c?
What type will C return?

I am pretty sure about the first one, b / c will return a float.. Correct?

And (long)a will give me a long double? Then (long)a + b / c should give me a long double to? But according to the webpage where i write the answers it tells me thats wrong?

---

### Post by ofnuts on 2011-09-14
> **tauh said:**
> Hi! For several days i have been struggling with a homework in C programming. I have Google it, my teacher wont answer my emails and the book i have doesn't talk that much about type conversions.

[IMG]http://i54.tinypic.com/2e5ingh.jpg[/IMG]

double a;
float b;
int c;

b / c? 
(long)a?
(long)a + b / c?
What type will C return?

I am pretty sure about the first one, b / c will return a float.. Correct?

And (long)a will give me a long double? Then (long)a + b / c should give me a long double to? But according to the webpage where i write the answers it tells me thats wrong?
There is a policy here about doing someone else's homework :) However, the -Wconversion option of GCC will tell you a lot about the conversions that occur, so if you submit the right code to the compiler you'll have all your answers...

---

### Post by tauh on 2011-09-14
> **ofnuts said:**
> There is a policy here about doing someone else's homework :) However, the -Wconversion option of GCC will tell you a lot about the conversions that occur, so if you submit the right code to the compiler you'll have all your answers...

Hi thank you for your answer. I don't want someone to do my homework by giving me the answers. Only to be help me solve it myself. :)

---

### Post by slavik on 2011-09-14
C will convert types to the kind that can store more information. Google is a great help, too. [http://techpubs.sgi.com/library/dynaweb_docs/0650/SGI_Developer/books/CLanguageRef/sgi_html/ch05.html](http://techpubs.sgi.com/library/dynaweb_docs/0650/SGI_Developer/books/CLanguageRef/sgi_html/ch05.html)

---

### Post by Off Shore on 2011-09-16
Itds a nice question you've been set and one which is designed to make you think about how your compiler behaves.
I would assume, if he is worth his salt,your teacher would advise you to find out exactly what your compiler returns.
You need to be aware that not all compilers handle implicit type conversions in the same way. In fact some may return quite surprising results.
Your best course of action ? Submit a code fragment to your compiler and then you will have the answer to your assignment.
An enquiring mind would then proceed to wonder how that answer came about, and Im certain thats exactly what you will do.
Good luck

---

### Post by kr0n1x on 2011-09-16
[http://en.wikipedia.org/wiki/Type_conversion](http://en.wikipedia.org/wiki/Type_conversion)

maybe this could also help you

[http://www.iso-9899.info/wiki/Books](http://www.iso-9899.info/wiki/Books) (you can check the free resources)

---

