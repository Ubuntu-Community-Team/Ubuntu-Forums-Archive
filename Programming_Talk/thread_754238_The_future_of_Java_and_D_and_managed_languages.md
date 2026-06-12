---
title: "The future of Java and D and managed languages"
date: 2008-04-13
forum: Programming Talk
---

### Post by n1kol@! on 2008-04-13
I have a little bit of experience in Java, but before I delve too deep into the language I want to know whether this is the right direction.  I have read in many places that java is at the the end of its time and that it is crippled.  Is this true?  And how suitable is java for application development?  As far as I know a lot of the more complicated but very powerful features of c++ have been removed from Java.  I am also interested in D, which still has most of these features. So basically I am deciding between Java and D.  Which one is more suitable for application development?  I have also read that many projects want to move to a managed language auch as Java or c#.  What are the reasons for this?  Is Java more productive than D?  And if so, how much more?  Are most new applications written with managed languages?  What about Jobs for each? I know that there won't be many jobs for D, but what about c++ vs Java?  I am still in school, but this might affect me in future.  Some people say Java is messy - in what way is that true? And is Java dying?

I am sorry if that are a bit too many questions, but these are the questions I ahve been asking myself for a long time now.

---

### Post by slavik on 2008-04-13
Depending on the application, but Java is used a lot in the financial industry (they also use C++ and still have COBOL).

---

### Post by CptPicard on 2008-04-13
> **n1kol@! said:**
> I have a little bit of experience in Java, but before I delve too deep into the language I want to know whether this is the right direction.

Do you have experience in other languages? If you're going to be a competent programmer and are just beginning, any language pretty much is the right direction. You're not going amiss with Java, although you could be doing just as well in most other languages. You will have to know a lot of them anyway, so considering your long term situation, there is no "wrong" language to invest in (well, unless it's Basic or somesuch.. ;)

Java is a good representative general OOP language. Not less, not much else.

> I have read in many places that java is at the the end of its time and that it is crippled.  Is this true?

Hardly. Java is very entrenched in industry, although it has maybe lost some of its coolness in recent years. Just comes with maturity I suppose.

> And how suitable is java for application development?

Quite. Because Swing hasn't quite caught on with proper desktop integration, it's more an enterprise server-side language though. There's nothing to stop you from writing a desktop app with Java though, and you'll get a crossplatform one to boot.

> As far as I know a lot of the more complicated but very powerful features of c++ have been removed from Java.  I am also interested in D, which still has most of these features.

Do you actually know what those features are and do you know to miss them, or are you just parroting something? :)

Yes, Java does not have templates, operator overloading or multiple inheritance, but they're not showstoppers. Many people would say that those are complications of C++, not pluses ... but YMMV. You'll have to actually know for yourself, and decide for yourself.

> So basically I am deciding between Java and D.  Which one is more suitable for application development?

Too general a question. D wins on compiling to native code and having easier access to low-level if you need it, but as an application developer you rarely do. Why you do have something like garbage collection in Java (which D has as well if you want it), however, is exactly because you're an application developer, not a kernel hacker, and want to have those things handled by someone for you so that you can focus on your application.

> I have also read that many projects want to move to a managed language auch as Java or c#.  What are the reasons for this?

Productivity, ease of development, general modernity, good APIs and standard library (which is the same everywhere)?

> Is Java more productive than D?

Probably yes, as D is still in its infancy... if you're looking for *productivity* some people would say use Lisp...

> Are most new applications written with managed languages?

Hard to quantify. I don't think you can make it into a popularity contest like that. You use what suits you best. No reason not to use a managed language if you specifically need something else.

> What about Jobs for each? I know that there won't be many jobs for D, but what about c++ vs Java?

The big mass of programming work is certainly moving away from C++, but if you're a very good C/C++ geek, as there are less of them, you can also ask more in pay of course.

> Some people say Java is messy - in what way is that true?

A lot of it is matter of opinion. Java is rather verbose, and esp. before the time of generics, you needed a lot of casting (in particular when coding with collections) which, in  long expressions, could make them hard to read.

On the other hand, Java is more consistent (out of the box) and has less elements to the language than something like C++... so messiness can be in the eye of the beholder and the hands of the coder.

> And is Java dying?

Are you a troll? ;) No, it is not dying.

---

### Post by LaRoza on 2008-04-13
> **n1kol@! said:**
> I have a little bit of experience in Java, but before I delve too deep into the language I want to know whether this is the right direction.  I have read in many places that java is at the the end of its time and that it is crippled.  Is this true?  And how suitable is java for application development?  As far as I know a lot of the more complicated but very powerful features of c++ have been removed from Java.  I am also interested in D, which still has most of these features. So basically I am deciding between Java and D.  Which one is more suitable for application development?  I have also read that many projects want to move to a managed language auch as Java or c#.  What are the reasons for this?  Is Java more productive than D?  And if so, how much more?  Are most new applications written with managed languages?  What about Jobs for each? I know that there won't be many jobs for D, but what about c++ vs Java?  I am still in school, but this might affect me in future.  Some people say Java is messy - in what way is that true? And is Java dying?


Don't be too worried about learning the "wrong" language. Java is widely used, and will be for a long time.

See my wiki if you are interested in learning other languages (including D), but I also recommend learning a higher level language with dynamic typing [Perl|Python|Ruby], a lower level language, C, and an other paradigm [Lisp|Haskell].

---

### Post by nanotube on 2008-04-13
<obligatory python plug>if you are just thinking what language to learn, you could to worse than try python. it's growing significantly in popularity, and google, for one, use it a lot.</obligatory python plug>

---

### Post by LaRoza on 2008-04-13
> **nanotube said:**
> <obligatory python plug>if you are just thinking what language to learn, you could to worse than try python. it's growing significantly in popularity, and google, for one, use it a lot.</obligatory python plug>

If you (OP) are concerned about job oppurtunities, see: [http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

---

### Post by CptPicard on 2008-04-13
I should point out that being concerned about job opportunities too early on will just make you a sad tool. Being a corporate cog is no fun, but if you make yourself generally competent in handling computation in general, the sky is your limit and you can choose your fights.

Corporations have it in their interest to push you into a box where you hack things their way. You don't want that.

---

### Post by kknd on 2008-04-13
Managed languages usually are very productive. For commercial applications, you will see that if you code faster, then you win more $$ =). Just kidding.

I like to write libraries in plain C and control then with Lua (a script language like python).

---

### Post by pmasiar on 2008-04-13
As LaRoza said, you should plan to learn more and more different languages than just Java and D. A dynamically typed ("scripting") language is a must, especially if you are concerned about productivity - because for many tasks, HLL language might be 3-10 times more productive (even if resulting code will be 20%-50% slower, it might not matter).

Re jobs: if your plans include getting rich by your startup being bought by Google, Python is the first choice :-)

---

### Post by n1kol@! on 2008-04-14
Thanks for all the answers. I think I will quickly learn python (I expect this to be relatively easy as I know the basics of Java already). Next I will learn Java (because it has such great tools and because it is more mature than D), and then I will learn D.

Thanks again for all the answers.

---

### Post by LaRoza on 2008-04-14
> **n1kol@! said:**
> Thanks for all the answers. I think I will quickly learn python (I expect this to be relatively easy as I know the basics of Java already). Next I will learn Java (because it has such great tools and because it is more mature than D), and then I will learn D.

Thanks again for all the answers.

If you are doing Python and Java first, learning C might make more sense.

---

### Post by n1kol@! on 2008-04-14
> If you are doing Python and Java first, learning C might make more sense.

is C still widely used? I thought it was really old and mainly used for writing kernels (although i know that gnome is written in C).

---

### Post by themusicwave on 2008-04-14
> **n1kol@! said:**
> is C still widely used? I thought it was really old and mainly used for writing kernels (although i know that gnome is written in C).

On Linux it is still used.  Also for things like games or other high performance tasks it is popular.

One place C is still king is the embedded market.  Almost every embedded system I have ever written was C.  The rest were Assembly.

---

### Post by LaRoza on 2008-04-14
> **n1kol@! said:**
> is C still widely used? I thought it was really old and mainly used for writing kernels (although i know that gnome is written in C).

Number Tw: [http://www.tiobe.com/content/paperinfo/tpci/index.html](http://www.tiobe.com/content/paperinfo/tpci/index.html)

It the basic programming language. The first thing a new system has to have is a C compiler.

It isn't old, the current standard (that is widespread) is from 1999. It was originally created in the 70's, but has changed as it grew.

For "old" languages not dying, look at Fortran. Originally made in 1954, its current status version is Fortran 2008 (although Fortran 2003, Fortran 95, Fortran 90, and Fortran 77 are the ones used I believe). It is the number one programming language used in super computers.

---

### Post by themusicwave on 2008-04-14
> **LaRoza said:**
> Number Tw: amming language. The first thing a new system has to have is a C compiler.

No the first thing it needs is an instruction set, then an Assembler and then a C compiler. :)

Point taken though it is a very important language.

---

### Post by LaRoza on 2008-04-14
> **themusicwave said:**
> No the first thing it needs is an instruction set, then an Assembler and then a C compiler. :)

Point taken though it is a very important language.

I should have said "A new system needs a C compiler to survive". Obviously, the C compiler doesn't come first.

---

### Post by pmasiar on 2008-04-14
> **themusicwave said:**
> No the first thing it needs is an instruction set, then an Assembler and then a C compiler. :)

ASM is rarely used these days - C is portable ASM. If you know ASM, you can see what approx instruction and C statement creates, but it is still more productive to do C than ASM. If you need high-performance library, C will be the tool of first choice. I don't think C will become "obsolete" any time soon - performance is niche market, but when you need it, you need C.

---

### Post by n1kol@! on 2008-04-14
But isn't D very similar to C, with a few new features and garbage collection? would there then be a point in learning C at all?

---

### Post by LaRoza on 2008-04-14
> **n1kol@! said:**
> But isn't D very similar to C, with a few new features and garbage collection? would there then be a point in learning C at all?

D is like C++ in more ways.

C is a standard and well developed language. It is used extensively in all aspects of Linux programming. It has a long history, and is available for all platforms.

D is an entirely different language, and not designed with the same goals as C.

C is a small language. It is very simple (which makes it hard to do compicated things)

You can learn as many languages as you want. The rules of D are not that different from all stictly typed, C style, imperative languages.

[http://xkcd.com/409/](http://xkcd.com/409/)

---

### Post by nanotube on 2008-04-14
> **LaRoza said:**
> 
[img]http://imgs.xkcd.com/comics/electric_skateboard_double_comic.png[/img]

i've noticed lately some people linking directly to image files on imgs.xkcd, instead of to the main comic page. that makes recipients miss out on the [frequently delightful] alt text. so please, stop the madness, and link to the page. :)
[http://xkcd.com/409/](http://xkcd.com/409/)

---

