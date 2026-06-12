---
title: "Big HELP!!!!!!!!"
date: 2012-10-03
forum: Programming Talk
---

### Post by Mohan1289 on 2012-10-03
Hey guys while i'm studying about java.. i got a few Questions.. It will be very beneficial for me if  you guys tell me


What's the Difference between 

&& and &
|| and |

what's the use of &,|,~,^??

Why we encounter a error if we write the following code?

int a=10;
double b=10.1;
int c=(b=a)?10:20;
System.out.println(c);

How is it possible ??

byte x=2;
byte y=4;
System.out.println(x&y); // why it prints 0 ??
System.out.println(x|y); // why it prints 6 ??
System.out.println(x^y); // why it prints 6 ??
System.out.println(~x);  // why It prints -3??


If so what's the value of (~-2)??
and how will SHIFT's work

<< SHIFT LEFT
>> SHIFT RIGHT
>>> UNSIGNED SHIFT RIGHT

how come these output's possible??

System.out.println(2<<1); //why it prints 4 ??
System.out.println(2<<2); //why it prints 8 ??
System.out.println(2<<5); //why it prints 64??

what does 2 and 1 represents??? i mean does the above statement says shift 2 bits to left from 1 or shift 1 bit to left from 2

If so Does that mean the numbers look like as shown below???

......9 8 7 6 5 4 3 2 1 0 -1 -2 -3 -4 -5 -6 -7 -8 -9 .....
                     (OR)
......-9 -8 -7 -6 -5 -4 -3 -2 -1 0 1 2 3 4 5 6 7 8 9 .....

Which is correct???

System.out.println(-1>>5); //why it prints -1 ??
System.out.println(-1>>>5); //why it prints 134217727 ??

why we lost data when we are converting from 
int --> float
long --> float
long --> double

like suppose if
i=85689012
float f=i;
why f=8.5689008E7?
What does that E mean??
what's the difference between UPPER CASE and LOWER CASE in Floating point Literals??

63.5D, 4F2C, 3e-1D, 63.5d,4f2c

what does float f=2.4f21e means??

Integer Literals are by default 4 types rigt??
Decimal
Octal??
Hexa decimal
Long literals

how come 0xE ,0xe, 0x22
In Hexa Decimal there are alphabets from A to F right??
What does x means then??
What are the values of above numbers??

Can anyone explain these to me i don't understand these at all??

---

### Post by albandy on 2012-10-03
Why we should do your homework?

---

### Post by Mohan1289 on 2012-10-03
> **albandy said:**
> Why we should do your homework?

LOL that's a Good joke :lolflag::lolflag::lolflag::lolflag:
It's not Home Work albandy

Those are my doubt's after reading.
In fact i am an employee not a student.

I am learning Java recently that's all

---

### Post by albandy on 2012-10-03
> 
What's the Difference between

&& and &
|| and |

what's the use of &,|,~,^??


&& and &: 
&& Logical Opertator (returns true or false)
& bitwise AND: returns the result of doig an AND operation bit by bit.

The same with | and ||

take a look:

[http://www.tutorialspoint.com/java/java_basic_operators.htm](http://www.tutorialspoint.com/java/java_basic_operators.htm)

---

### Post by Mohan1289 on 2012-10-03
> **albandy said:**
> && and &: 
&& Logical Opertator (returns true or false)
& bitwise AND: returns the result of doig an AND operation bit by bit.

The same with | and ||

take a look:

[http://www.tutorialspoint.com/java/java_basic_operators.htm](http://www.tutorialspoint.com/java/java_basic_operators.htm)

ummmm.. Sorry albandy in our company they almost blocked all sites except for few.
I can't open that site

---

### Post by drmrgd on 2012-10-03
In that case, not sure what sites you can visit.  Try a Google search for "java boolean operators", and you should get the relevant information.  As Albandy says, these are logical Boolean operators (&& = AND, || = OR, etc.).

---

### Post by Mohan1289 on 2012-10-03
I understood the working Logical And(&&) but not Bitwise And(&)

If you can send me the link i will refer them when i got to home....

Thank you

---

### Post by The Cog on 2012-10-03
[http://en.wikipedia.org/wiki/Bitwise_operation](http://en.wikipedia.org/wiki/Bitwise_operation)

Moved to Programming Talk

---

### Post by shreepads on 2012-10-03
You need to read a basic book on data types and programming...

Some of the things you're asking are too elementary to be explained in a forum question...

---

### Post by Mohan1289 on 2012-10-03
may be shreepad i am reading a book but i didn't understand at all that's why i asked in the forum Since you guys are experts in various fields

---

### Post by albandy on 2012-10-03
> **Mohan1289 said:**
> may be shreepad i am reading a book but i didn't understand at all that's why i asked in the forum Since you guys are experts in various fields


Imagine you have an integer1 with number 2 in it, and integer2 with number 3 in it.

2 in binary is 10
3 in binary is 11

so interger1 & integer2 = 
```

    10
    11
AND========   
    10

```

---

### Post by Mohan1289 on 2012-10-03
> **albandy said:**
> Imagine you have an integer1 with number 2 in it, and integer2 with number 3 in it.

2 in binary is 10
3 in binary is 11

so interger1 & integer2 = 
```

    10
    11
AND========   
    10

```

Got it... Thank you albandy

---

### Post by 1clue on 2012-10-03
Maybe we should back up a bit.

If you're a programmer and for some reason have never been exposed to a heavily typed language like Java, AND you have suddenly been put on the spot by your boss to write something for a Java virtual machine (JVM) then you might want to look at something else.

Is there a specific project you have?  If it's a web-based application that needs to run on a JVM for some reason then maybe you should look at groovy/grails instead.  Groovy is much more lenient about typing (double vs int for example) and it's a lot more compact without losing readability.  Grails is a web framework using groovy.

The thing is, if your company blocks so many sites and you are being told by your boss to research this, you might want to point out that you need more Internet access, or some paid time off site.  Java has a lot of information in books, but the most current stuff is online, and access to any of the dozens of forums are pretty critical, at least for searching and probably for asking questions.  For any of the hundreds of languages which generate Java byte code and run on the JVM, it's even more web-oriented for documentation.  You will need to see the forums, you'll need to see documentation sites, you'll need to have access to tutorials and access example code.

And seriously, go to your local college and take a programming class.  I don't mean to be insulting in any way, but if you're asking these questions you need a solid foundation we can't give you.  I've been put on the spot by an employer before, and by the time I got done with it it would have been simpler and faster to go take a class.

Good luck and have fun.

---

### Post by Mohan1289 on 2012-10-03
> **1clue said:**
> Maybe we should back up a bit.

If you're a programmer and for some reason have never been exposed to a heavily typed language like Java, AND you have suddenly been put on the spot by your boss to write something for a Java virtual machine (JVM) then you might want to look at something else.

Is there a specific project you have?  If it's a web-based application that needs to run on a JVM for some reason then maybe you should look at groovy/grails instead.  Groovy is much more lenient about typing (double vs int for example) and it's a lot more compact without losing readability.  Grails is a web framework using groovy.

The thing is, if your company blocks so many sites and you are being told by your boss to research this, you might want to point out that you need more Internet access, or some paid time off site.  Java has a lot of information in books, but the most current stuff is online, and access to any of the dozens of forums are pretty critical, at least for searching and probably for asking questions.  For any of the hundreds of languages which generate Java byte code and run on the JVM, it's even more web-oriented for documentation.  You will need to see the forums, you'll need to see documentation sites, you'll need to have access to tutorials and access example code.

And seriously, go to your local college and take a programming class.  I don't mean to be insulting in any way, but if you're asking these questions you need a solid foundation we can't give you.  I've been put on the spot by an employer before, and by the time I got done with it it would have been simpler and faster to go take a class.

Good luck and have fun.

Yeah i am thinking that too but the problem is he is not giving clarity at all.
Like in which project he is putting me in.

If it's mobile apps i will go to J2ME classes if it's for J2EE and J2SE i will learn them... he is not giving clarity that's why i am desperately trying to get a solid base. they are allowing only Technincal sites. Though some are useful they are blocking them..

---

### Post by albandy on 2012-10-03
I recomend you this book:
[http://shop.oreilly.com/product/9780596004651.do](http://shop.oreilly.com/product/9780596004651.do)

---

### Post by 1clue on 2012-10-03
Forum access is huge in this.

Tell him you're going to take a class, tell him which ones are available and let him tell you which is most appropriate.

Have you been exposed to any real-world programming?  If so what languages?  If you have experience then we can help point out the differences between what you're used to and what you're going to expect.  If you're a beginner and are expected to deliver commercial quality goods right away it won't happen.  There's a difference between a tutorial project, a class project and a commercially viable product.

---

### Post by shreepads on 2012-10-04
For binary numbers and operations (& ! ~ << >> etc) have a look at:

[http://en.wikipedia.org/wiki/Binary_numeral_system](http://en.wikipedia.org/wiki/Binary_numeral_system)

[http://en.wikipedia.org/wiki/Bitwise_operation](http://en.wikipedia.org/wiki/Bitwise_operation)

---

### Post by Mohan1289 on 2012-10-05
> **1clue said:**
> Forum access is huge in this.

Tell him you're going to take a class, tell him which ones are available and let him tell you which is most appropriate.

Have you been exposed to any real-world programming?  If so what languages?  If you have experience then we can help point out the differences between what you're used to and what you're going to expect.  If you're a beginner and are expected to deliver commercial quality goods right away it won't happen.  There's a difference between a tutorial project, a class project and a commercially viable product.

Then you can say i am beginner....
I didn't develop a real time project, i mean i am still a trainee as you said there's  difference b/w Tutorial Projects and Real Time Projects..

---

### Post by pqwoerituytrueiwoq on 2012-10-05
> **Mohan1289 said:**
> ummmm.. Sorry albandy in our company they almost blocked all sites except for few.
I can't open that site
This is when Google's Cache comes in handy
i actually made a greasemoneky script to route blocked pages to Googles cache back in high school

---

### Post by 1clue on 2012-10-05
Not to be fussy, but if you start saying Real Time that's a whole different ball game.  Real Time is generally not an event driven scenario, it's a single-purpose system designed to do exactly one thing in real time.  Could be industrial assembly line stuff or it could be something that controls a fighter jet.  I've never done real time projects either.

Real world is a much more accurate term.

---

### Post by Mohan1289 on 2012-10-06
> **1clue said:**
> Not to be fussy, but if you start saying Real Time that's a whole different ball game.  Real Time is generally not an event driven scenario, it's a single-purpose system designed to do exactly one thing in real time.  Could be industrial assembly line stuff or it could be something that controls a fighter jet.  I've never done real time projects either.

Real world is a much more accurate term.

Yes that's correct...

Real World is correct

---

