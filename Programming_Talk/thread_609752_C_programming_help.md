---
title: "C programming help"
date: 2007-11-11
forum: Programming Talk
---

### Post by crashovaride on 2007-11-11
Hello all,

I'm beginning my journey in C programming and i'm getting the hang of it (slowly). However, each time i search for what i need to get done in C, i can never seem to find it on the net. Does anyone know of any good resources to help me with programming in the linux C code? I have even purchased books on linux C but these books really suck! Half the time they error, and i'm completely lost. Any suggestions. They would be greatly appreciated.

Thank you.

---

### Post by slavik on 2007-11-11
IMO, the only book you need to get started (that teaches you to use C) is the C Programming Language 2nd edition by Kernighan and Ritchie (referred to as the K&R book).

Also, this forums is a great resource. :) What problem are you having?

---

### Post by LaRoza on 2007-11-11
K&R is very good, but for learning at no cost my wiki has a lot that might be of interest to you.

---

### Post by stroyan on 2007-11-11
I started with the original K&R book about25 years ago.  I started with that at a point where  I was already familiar with a couple of other programming languages.  It was very appropriate for picking up C as an additional language.  I don't know if it would be as useful for a person new to programming.  The current edition is certainly worth picking up as a good reference.

  You would probably benefit by working through a tutorial.  That will let you get familiar with the many features in an order that builds from simple to advanced.  There is a good looking set of tutorials at [http://cyberdiem.com/vin/tutorials.html](http://cyberdiem.com/vin/tutorials.html) .  I really like the look of number 7 in that list- [ftp://svr-ftp.eng.cam.ac.uk/pub/misc/love_C.ps.Z](ftp://svr-ftp.eng.cam.ac.uk/pub/misc/love_C.ps.Z)
It is about C on unix rather than specifically targeting linux.  That means a few references to programming tools are not directly applicable.  But the subjects that it covers are really good.

---

### Post by Kadrus on 2007-11-11
Euh..how about: [http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

I think those are some nice tutorials..
And a language is better learned by reading a book of course..so try this

[http://freeprogrammingebooks.com/free_ebook_c++_free_ebooks_c++/the_new_c_standard.php](http://freeprogrammingebooks.com/free_ebook_c++_free_ebooks_c++/the_new_c_standard.php)

Hope that was helpful :)

---

### Post by wolfbone on 2007-11-11
[http://publications.gbdirect.co.uk/c_book/](http://publications.gbdirect.co.uk/c_book/)

---

### Post by scourge on 2007-11-11
I second the suggestion to buy K&R's book and learn it well. When you're comfortable with ANSI C you can move on to programming specifically for Linux. I have a Linux programming book by Warren W. Gay which I found to be excellent.

---

### Post by Compyx on 2007-11-12
> **Kadrus said:**
> Euh..how about: [http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

I think those are some nice tutorials..


The tutorials are horrible, the very first example doesn't even compile.

Like others have said, K&R2 is an excellent book to start programming in C, perhaps followed by "Expert C Programming - Deep C Secrets" by Peter van der Linden.

If you really want to learn C from tutorials on the web, [Steve Summit's notes]("http://www.eskimo.com/~scs/cclass/notes/top.html") are at least correct. Another good resource for finding out about some of C's common pitfalls is the c.l.c. FAQ: [http://www.c-faq.com/]("http://www.c-faq.com/")

But in my opinion the best way to learn a new language is to read books and perhaps trying to find a mentor, someone how actually knows the language and has a lot of experience with it.

Of course, you can always ask questions here, there are a quite a few knowledgeable people around here.

---

### Post by samjh on 2007-11-12
Very fast crash-course on C:
[http://www.physics.drexel.edu/courses/CompPhys/General/C_basics/](http://www.physics.drexel.edu/courses/CompPhys/General/C_basics/)

Some of the materials is not-so-good, but a reasonable tutorial if you want to grab the language by the throat and dive into the deep end of the pool.

---

### Post by Compyx on 2007-11-12
> **samjh said:**
> Very fast crash-course on C:
[http://www.physics.drexel.edu/courses/CompPhys/General/C_basics/](http://www.physics.drexel.edu/courses/CompPhys/General/C_basics/)

Some of the materials is not-so-good, but a reasonable tutorial if you want to grab the language by the throat and dive into the deep end of the pool.

Aargh, the very first program:
```

#include < stdio.h>

**void main()**
{
    printf("\nHello World\n");
}

```

You might as well ask Bill Gates to give you a tutorial on ethics.

---

### Post by samjh on 2007-11-12
lol

I thought you might want to pick that out!  A little surprised you didn't jump at the lack of void in the empty parameter bracket. ;)

---

### Post by Compyx on 2007-11-12
> **samjh said:**
> lol

I thought you might want to pick that out!  A little surprised you didn't jump at the lack of void in the empty parameter bracket. ;)

Well, I put the whole line in bold.. I'm also wondering if the space in:
```

#include < stdio.h>

```
is legal.
I'll check that out once I get home. :D

---

### Post by samjh on 2007-11-12
> **Compyx said:**
> I'm also wondering if the space in:
```

#include < stdio.h>

```
is legal.
I'll check that out once I get home. :D

I don't think it is.

C99 stipulates:

```
#include <h-char-sequence> new-line
```

Therefore, no spaces!

---

### Post by KentS on 2007-11-12
And you shouldn't use 
```
void main
```
but
```
int main
```
(Yeah, I know there should be a parameter bracket after main, but I'm lazy)
So there should also be a 
```
return 0;
```
at the end.

---

### Post by pmasiar on 2007-11-12
If OP is new to programming, I disagree with choice of language. C is not friendly to beginners. Python is much better choice, but of course you are free to do whatever you want - if you hurt only yourseft that is.
Also, K&R "big blue C" book is not for beginners too, but for ppl with programming experience in other languages, as they clearly state in the book. It is amazing how many forum posters do not distinguish between books for beginners and experts, and, being experts, suggest book **they** liked.

---

### Post by Can+~ on 2007-11-12
> **Compyx said:**
> Aargh, the very first program:
```

#include < stdio.h>

**void main()**
{
    printf("\nHello World\n");
}

```

You might as well ask Bill Gates to give you a tutorial on ethics.

void in the main? When main ends, it returns to the OS the exit status, 0 is success, any other numbers is failure, so, not returning nothing is plain wrong.

The best way to understand C, and almost every programming language, is to make parallels with mathematics, for instance:

> Math:
I define my function f(x) as f(x) = x²+2x+3. Then, I call it.

y = f(x).

f(x) returns a value, and passes it to y.

```
C:
int myfunction(int x)
{
   int r;
   r = x*x + 2*x + 3
   return r;
}

int main()
{
   y = myfunction();
   printf("%d", y); // This prints the output.
   return 0;
}
```

---

### Post by LaRoza on 2007-11-12
You aren't passing any ints to your function. You also don't need y, you could have just used:

[php]
int myfunction(int x)
{
   int r;
   r = x*x + 2*x + 3
   return r;
}

int main(int argc,char ** argv)
{
   printf("%d", myfunction(10)); // This prints the output.
   return 0;
}
[/php]

---

### Post by Compyx on 2007-11-13
> **LaRoza said:**
> You aren't passing any ints to your function. You also don't need y, you could have just used:

[php]
int myfunction(int x)
{
   int r;
   r = x*x + 2*x + 3
   return r;
}

int main(int argc,char ** argv)
{
   printf("%d", myfunction(10)); // This prints the output.
   return 0;
}
[/php]

You don't need r either:
```

return x * x + 2 * x + 3;

```
and an #include <stdio.h> would be nice for the prototype of printf()
;)

---

### Post by LaRoza on 2007-11-13
> **Compyx said:**
> You don't need r either:
```

return x * x + 2 * x + 3;

```
and an #include <stdio.h> would be nice for the prototype of printf()
;)

True, but I would alter that function to make it safer. If someone passes a large enough int, it will overflow.

I was also only passing the important code, I also left the prototype out.

---

### Post by Compyx on 2007-11-15
> **LaRoza said:**
> True, but I would alter that function to make it safer. If someone passes a large enough int, it will overflow.


True, overflow can be a nasty beast. Although with this particular function it's trivial to detect overflow before it happens.

---

### Post by crashovaride on 2007-12-03
All, i'm very sorry for the long duration of my postings and me being absent from replying. I seem to have had a problem with my spam filters. Basically i want to start small and learn and work my way up. My first C project will be to scan files for strings. And, report what it finds back. I got the hand of finding and locating the files needed to scan, but when it comes to reading these files, i'm lost.

The internet always gives me C resources to Windows, and i hate it! My 2 machines away from going completely Linux, and the only crutch i got on linux is that i can program in VB and there is no equivalent in linux.  I appreciate all the resources that everyone has posted. And, i do intent to take a deeper look. If it helps anyone, the book "C and Unix programming a comprehensive guide" has not helped me with **anything** it's sad. If anyone has additional resources, please send them over. I'm very grateful. 

Thanks

Anthony.

---

### Post by LaRoza on 2007-12-03
[http://laroza.pbwiki.com/C](http://laroza.pbwiki.com/C)

What you described could be done with the standard library.

---

