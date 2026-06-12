---
title: "Learning OOP next semester"
date: 2005-12-14
forum: Programming Talk
---

### Post by Buffalo Soldier on 2005-12-14
Hi guys,

Just finished a semester. Next semester i'll be learning OOP. Summary of the subject states that it will be taught using Java. Done some light introductory reading on Java already. Is there extra preparations/reading that I can do to make it easier to understand the class later? What should I pay attentions to? And what pitfalls I should avoid?

(i have basic knowledge in Python and last semester we learned C)

---

### Post by psusi on 2005-12-14
If at all possible, take a class on C++ instead of Java.  I hate Java and if you already know C then learning C++ will be easier ( they share more in common than Java ).  

Did I mention that I hate Java?

Or that Java sucks?

By the way, I really hate Java.

---

### Post by darth_vector on 2005-12-14
^ i second that - java sucks!

the biggest problem that i see is that people keep trying to write sequential programs rather than oo programs.

there is any number of introductory java books out there, but i would recommend the java website: [www.java.sun.com](www.java.sun.com) which has some great tutorials.

---

### Post by simon w on 2005-12-15
[QUOTE=darth_vector]the biggest problem that i see is that people keep trying to write sequential programs rather than oo programs.[/QUOTE]

Surely that means the programmers suck for not understanding the OO methodology?

If the course is focusing on OO programming then it doesn't *really* matter what language it's tought in.  The important thing is that you understand OO.

The best book will probably be the one your tutor has set as the course textbook.  O'Reilly's website might be worth a look as well.

Some keywords off the top of my head (not a complete list)
Inheritance
Encapsulation
Abstraction
Public, Private & Protected methods and variables
Interfaces
Over Loading

---

### Post by gord on 2005-12-15
if you know some python then you'll prolly have an understanding of oop allready, you know all that whatever.moo() stuff? ;)

oop isn't really all that difficult, it is very big and scary at first but once you understand what its all about, it comes naturally. nothing beats having someone explain it to you face to face though :)

the only advice i can give is don't be afraid to ask questions, if you don't understand something there is a rather good chance most of the rest of the class don't too.

---

### Post by Buffalo Soldier on 2005-12-15
thanks guys. i appreciate all the advice.

---

### Post by darth_vector on 2005-12-15
[QUOTE=simon w]Surely that means the programmers suck for not understanding the OO methodology?[/QUOTE]

there is a lot of that. mostly i see this because i help teach a introductory course in computer science that uses java to teach oo programming. sequential programming seems more intuitive to many people - including me.

---

### Post by btdown on 2005-12-15
> sequential programming seems more intuitive to many people - including me
 
I think OOp was created by satan and should be banished back from whence it came.

---

### Post by darth_vector on 2005-12-15
[QUOTE=btdown]I think OOp was created by satan and should be banished back from whence it came.[/QUOTE]

absolutely

---

### Post by vgeddes on 2005-12-16
Actually, we too had to learn Java before C++/C, and for that, I am grateful. Programming in Java helped me to understand OO methodology more clearly and has enabled me to build more robust and elegant programs in C++. I don't use Java anymore, and I prefer not too, but it still is an excellent educational tool for 1st year students.

---

### Post by LordHunter317 on 2005-12-16
> **psusi]I hate Java and if you already know C then learning C++ will be easier ( they share more in common than Java ).  [/quote]**No, it will not,** because as I elaborated many times before, the correct way to do things in C is the wrong way in C++ and vice-versa.

People really need to start pretending they're seperate languages, for all intents and purposes.  The syntax similiarities mean nothing.

[quote=darth_vector]
the biggest problem that i see is that people keep trying to write sequential programs rather than oo programs.[/quote]That's because most programs at an introductory level have no value in being written in an object-oriented fashion said:**
> Programming in Java helped me to understand OO methodology more clearly and has enabled me to build more robust and elegant programs in C++.While they share the same basics, C++ offers you many more mechanisms for providing better encapsulation of your data (e.g., friend functions, non-member functions, implict conversions, overloaded operators).  It's worth reading a C++ book to learn all the wonderful things you can do when you're freed from Java's restrictive constraints.


As for the OP: learn the location of the nearest bar and how to drink, heavily. ;)

---

### Post by thumper on 2005-12-16
Here's my 2 cents (or pence for others in the UK :) )

Learning C first will help with learning C with classes.  Unfortunately that is as far as many people get.  From what I have seen, there are not many classes or courses that teach C++ with the standard library from scratch.

If you want a great book on C++ look at [Accelerated C++](http://www.acceleratedcpp.com) by Andrew Koenig and Barbara Moo.  Here are links to a couple of book reviews, one from the [ACCU](http://www.accu.org/bookreviews/public/reviews/a/a002212.htm) , and another from [Angelika Langer](http://www.angelikalanger.com/Articles/Reviews/KoenigMoo/review.htm).

If you thought that the confusion between C and C++ was bad, look at what is found under the heading [Pure C++](http://msdn.microsoft.com/msdnmag/issues/05/12/PureC/default.aspx).

Here is a snippit:
```

for each( String ^s in Enum::GetNames(
    status::typeid ))
Console::WriteLine( s );

void DisplayType( Object^ o )
{
     if ( !o ) return;

     Type^ t = o->GetType();
     Console::WriteLine( "Type is {0} : {1}",
                          t->Name, t->FullName );

}

Type^ ts = String::typeid;
Type^ ti = Int32::typeid;

array<Type^>^ types = a1->GetTypes();
Type^ query = a1->GetType( "Query" ); 

```

---

### Post by thumper on 2005-12-16
For those not quite in the know, the above code sample is from C++/CLI.

---

### Post by blacklantern on 2005-12-16
[QUOTE=vgeddes]Actually, we too had to learn Java before C++/C, and for that, I am grateful. Programming in Java helped me to understand OO methodology more clearly and has enabled me to build more robust and elegant programs in C++. I don't use Java anymore, and I prefer not too, but it still is an excellent educational tool for 1st year students.[/QUOTE]


I'm going to have to agree with vgeddes on this one. I learned Java first, and even though I much prefer C++ over Java now, I still think that's it better to teach first year students java instead of C. Most of the students (including myself) had never programmed before, so throwing them into memory manipulation and all that jazz to begin with can be kind of daunting.

---

### Post by thumper on 2005-12-16
I also have to agree that C++ is not a good language to learn first.

Personally I started programming before Java existed (I must be getting old :( ) I think that Java is fine to start with as long as you don't end up thinking that Java solves all problems.  It is just one tool in the big tool box of languages.

---

### Post by psusi on 2005-12-16
> **LordHunter317]**No, it will not,** because as I elaborated many times before, the correct way to do things in C is the wrong way in C++ and vice-versa.[/QUOTE]

True... at the macro level, the program design is inside out compared to C.  Making that switch for me was hard at first.  At the micro level though, the syntax is the same so doing simple things like writing a for loop are the same.  

As strange as it felt for me at first trying to turn my thinking inside out, once I finally did, I think understanding both ways and the differences between them was better for me.  

[QUOTE=LordHunter317]
That's because most programs at an introductory level have no value in being written in an object-oriented fashion said:**
> 

True... there is simply no point to using OOP for a hello world type program.  I like the idea of teaching C++ by starting out with only the C subset at first, maybe learning how to implement a linked list say, then learning about std::list.  It keeps it simple at first, then introduces OOP in a way that shows immediately how helpful it can be.  

[QUOTE=blacklantern]I'm going to have to agree with vgeddes on this one. I learned Java first, and even though I much prefer C++ over Java now, I still think that's it better to teach first year students java instead of C. Most of the students (including myself) had never programmed before, so throwing them into memory manipulation and all that jazz to begin with can be kind of daunting.

This is one of the reasons I hate Java so much.  Sure, students allways struggled with memory management in a C/C++ 101 class.  That's a good thing.  Understanding memory is one of the most important things a programmer can know.  Getting by without understanding memory and getting used to just letting the Java VM automagically clean up your junk every now and then only hurts you as a programmer.

---

### Post by LordHunter317 on 2005-12-17
[QUOTE=psusi]True... there is simply no point to using OOP for a hello world type program.[/quote]Somewhere online, there's a page that shows what an OOP 'hello world' that prints a different string based on your platform in Java.  It was a few hundred lines, all said and done.

> I like the idea of teaching C++ by starting out with only the C subset at first, maybe learning how to implement a linked list say, then learning about std::list.Unless the purpose is data structures, that's wasteful.  It's better to start with what the language provides you and then show you how it's implemented and the theory behind it. 

> Sure, students allways struggled with memory management in a C/C++ 101 class.That's because it was a *C/C++* class.  If they'd teach just C++ and C++ ways of doing things, they'd have far less trouble.  

> Understanding memory is one of the most important things a programmer can know.  Getting by without understanding memory and getting used to just letting the Java VM automagically clean up your junk every now and then only hurts you as a programmer.I'm not really sure that's true.

---

### Post by thumper on 2005-12-17
[quote=LordHunter317][quote=psusi]I like the idea of teaching C++ by starting out with only the C subset at first, maybe learning how to implement a linked list say, then learning about std::list.[/quote]
Unless the purpose is data structures, that's wasteful. It's better to start with what the language provides you and then show you how it's implemented and the theory behind it.[/quote]
I'd have to go with LordHunter317 on this one.  I'm all for teaching C++ using the standard library first.  You still need to teach memory management in C++ but you do it in a different way.  You show it using shared pointers and the basis of RAII (resource acquisition is initialisation), rather than the malloc/free C way.
[quote=LordHunter317]That's because it was a C/C++ class. If they'd teach just C++ and C++ ways of doing things, they'd have far less trouble.[/quote]
Agree again.  Teach one or the other.  Don't pretend they are the same!

---

### Post by psusi on 2005-12-17
I didn't mean a class on C and C++, I meant classes on C or C++.  Learning about pointers has allways been difficult for new students, but I believe that understanding pointers is so vital to understanding the machine, and thus, programming it, that you simply can not skip it and rely on the virtual machine.  

Yes, the two languages most definately are not the same, which is why you should learn both and understand how they differ. 

Also in any field I have allways believed in teaching the theory behind it first, not last.  Take calculous.  When I had calc they taught you how to work out derivitives first by hand.  Now I could not work one out by hand today if my life depended on it, but because I had to do it the hard way first, I got a much better understanding of what a derivitive actually is, and appreciated it more when we got to use scientific calculators that could solve derivitives for you.  

I strongly feel that doing it by hand at first, and the understanding that created, is what allowed me to easily solve new and complex real world problems with the help of the calculator, while most other students were scratching their heads because they only learned how to do the work by repetition, without truely understanding it so they were baffled by a problem that was slightly different or more complex than those they had done for homework.  I think the same thing applies to programming.  Learn and **understand** the theory first, then the rest will come easily.

---

### Post by LordHunter317 on 2005-12-18
[QUOTE=psusi]  Learning about pointers has allways been difficult for new students, but I believe that understanding pointers is so vital to understanding the machine, and thus, programming it, that you simply can not skip it and rely on the virtual machine. [/quote]Only, this is a false delimma.

Java, C# et al. *have pointers*.  Sure the language calls them references, but they're really pointers: they point at another object and they can be reseated.  The latter makes them pointers, not references.

And all you need to know about dealing with pointers you can learn from them.  Sure, you can't do pointer arithmetic but that's not usually a desirable thing to learn, either.  C and C++ are rather unique in that ability, and it normally causes more problems then it helps.

> Also in any field I have allways believed in teaching the theory behind it first, not last.  Take calculous.Calculus is a rare exception to the rule.  Certain in circuit theory we learn applications first, raw theory second.  And when you learned Integrals, you didn't learn the Fundamental Theorem of   Calculus first, so what you said isn't really true.

In any case with data structures, teaching the theory before usage at an introductory programming level is simply silly, and that includes how to write them.  That isn't to say it shouldn't be covered, but one can know how/when to use a std::list over std::vector without deeply covering the underlying theory.  Though in an introductory class, I'd doubt you'd care about the Container so much.

> I think the same thing applies to programming.  Learn and **understand** the theory first, then the rest will come easily.I'm pretty sure like most other applied things, it doesn't at all.  You must learn the basic applications first, then the theory, then the application of the theory.  You generally will have a very hard time grasping the theory without some intuition about what it already applies to.

One doesn't teach Newton's laws by going through momentum and the deriviation from there, one teaches it by particle motion and the traditional equations for dealing with it.  Position -> Velocity -> Acceleration -> Force is a much more natural progression, even though the equation F = ma is derived from is an impulse equation, not a kinematics one.

---

### Post by EnGee on 2005-12-18
I tried to learn OO in the past from some books and I couldn't get it. I took a course in Java and in the beginning I suffered from not understanding the idea. Maybe because i started back in the 80's and my mind was not able to think in other way!
Anyway, suddenly it 'clicked' my mind and I understood everything the teacher gave us! So, don't feel disappointed at first, if you have a good teacher, then it will come to you, hopefully he/she will use UML to illustrate the concepts.
As to love or hate Java I don't think this will help you now or during the semester. Maybe you can prepare with 'Beginning Java Objects' book by Wrox, I didn't have the need to read it, but many said is very good book to understand OO in Java, take a look at this [http://java.sun.com/developer/Books/javaprogramming/begobjects/](http://java.sun.com/developer/Books/javaprogramming/begobjects/) 
It is old yes, but nothing changed in OO in Java since that time (i think).
After the course, i felt in love with Java and I abandoned VB6 and .NET, and start to feel the freedom of developing in Windows, or for now Ubuntu with the same IDEs and tools. I wished it is Fully Object Oriented like Ruby, but then no one is perfect. I hope you write your opinion about your experience with OO and Java here after taking the semester.
Good Luck

---

### Post by M3ta7h3ad on 2005-12-18
If your studying java (its a great language by the way :) ignore the other fanboi's but pay attention to the one which said "its just a tool in a big toolbox of other languages" dont just specialise in java, learn others as well.

Some websites I find useful.

[Http://www.google.com](Http://www.google.com) << the greatest help ever! :)
[http://www.javaalmanac.com](http://www.javaalmanac.com) << code snippets demonstrating every class and method in the api
[http://java.sun.com/j2se/1.4.2/docs/api/](http://java.sun.com/j2se/1.4.2/docs/api/) << The API: it'll list all the methods of each class (what you can do with it).

Also consider investing in a copy of "Big Java" from a book store, its a huge book, but its helped me out no end!

---

