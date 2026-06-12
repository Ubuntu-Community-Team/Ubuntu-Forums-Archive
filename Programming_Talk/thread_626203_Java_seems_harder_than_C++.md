---
title: "Java seems harder than C++"
date: 2007-11-28
forum: Programming Talk
---

### Post by bluewagon on 2007-11-28
I see a lot of people say things like Java is a good starting language because its easy to learn and what not, but so far it seems more confusing than C++.
For instance,
in C++ to have a user input something (lets say an int) you type 
cin >> int_variable;
but in Java, you have to have a buffer reader, and have a string variable for every int(or any other type) and then have to convert from string to int(or any other type)

---

### Post by LaRoza on 2007-11-28
Java is not an "easy" language.

It is not really well suited to CLI programs.

People who say it is good for starting probably only know that language, or have started with it.

---

### Post by samjh on 2007-11-28
You could hardly have picked a worse example.

Java is easier than C++ mainly because of automatic memory management, and reduction of error-prone features of C++ such as multiple inheritance, pointers, operator overloading, etc.

Syntax has very little to do with Java's ease of use.

The console input and output example is particularly bad because Java was never designed for such applications.  Java's two target application areas were embedded software and web applications, neither of them involve much - if any - use of a terminal console.

> People who say it is good for starting probably only know that language, or have started with it.Considering that Java is (probably) the most popular introductory programming language at university level, a lot of educators seem to disagree with you.

I wouldn't pick it as a first language myself, but it is easier than trying to learn C++ from scratch.

---

### Post by sonofusion82 on 2007-11-28
> **samjh said:**
> You could hardly have picked a worse example.

Java is easier than C++ mainly because of automatic memory management, and reduction of error-prone features of C++ such as multiple inheritance, pointers, operator overloading, etc.

Syntax has very little to do with Java's ease of use.

The console input and output example is particularly bad because Java was never designed for such applications.  Java's two target application areas were embedded software and web applications, neither of them involve much - if any - use of a terminal console.

Considering that Java is (probably) the most popular introductory programming language at university level, a lot of educators seem to disagree with you.

I wouldn't pick it as a first language myself, but it is easier than trying to learn C++ from scratch.


yes, for a simple CLI programs, java syntax is probably a little more verbose than C++ but they are definitely safer for beginners.
for advanced stuff, C++ is much harder to master than Java especially on advanced things like templates, exception, memory management and all those meta-programming stuffs not possible in Java.

also, to really understand the example:
cin << int_variable;
you will need to understand how operator overloading and stuff work while in java, they are basically function call.

---

### Post by LaRoza on 2007-11-28
> **samjh said:**
> 
Considering that Java is (probably) the most popular introductory programming language at university level, a lot of educators seem to disagree with you.

I wouldn't pick it as a first language myself, but it is easier than trying to learn C++ from scratch.

Who makes these decisions? The educators or a board?

MIT uses Python, after Scheme.

Some say to start with HLL, like Python, Perl, etc, some say start low, assembly, C, I can think of reasons to support both of these recommendations, however, I cannot think of a reason to use Java as a first language over others.

---

### Post by nhandler on 2007-11-28
At my high school, they tought C++ and Java in the intro computer programming course. In c++, we focused on terminal based programs. In java, we mainly did applets. Most of the students didn't have much of a problem when we made the switch from c++ to java.

P.S. It's cin >> int_variable; cout uses <<.

---

### Post by Meiscooldude on 2007-11-28
It all depends on what version of Java you are using, I use Java 1.6 (aka Java 6) jdk, But im pretty sure the Scanner class came with the 1.5 release of java.

I can use terminal input by doing this:

```

import java.uti.Scanner; //required import

...

Scanner sInput = new Scanner(System.in);
Scanner input = new Scanner(System.in);   // little glitchy when mixing String input with int and double

System.out.print("Enter your name: ");
String yourName = sInput.nextLine();

System.out.print("Enter your age: ");
int yourAge = input.nextInt();

System.out.print("Give me a double: ");
double yourDouble = input.nextDouble();

System.out.println("Your name is " + yourName);
System.out.println("Your age is " + yourAge);
System.out.println("Your double is " + yourDouble);


 
```


try that, its alot easier than using a buffered reader :)


Just fyi, there is a little anoying thing when mixing String input with int and double. I fix it by having two Scanner Objects, one for String input, one for simple data type input.


Personally I started with Java, and i love it, I recomend it to anyone, but I would recomend VB for a starting programmer.

---

### Post by ameba on 2007-11-28
h

---

### Post by ameba on 2007-11-28
did

---

### Post by dwhitney67 on 2007-11-28
I've been s/w development for almost two decades.... what is CLI??  Is that a new 21st century acronym or an Ubuntu Forum creation?

Ahh... I figured it out... I think.... Command Line Interface!

---

### Post by ameba on 2007-11-28
y

---

### Post by uljanow on 2007-11-29
> **bluewagon said:**
> but in Java, you have to have a buffer reader, and have a string variable for every int(or any other type) and then have to convert from string to int(or any other type)

Additionally you need to catch exceptions that might occur during converting. :)
> Java is easier than C++ mainly because of automatic memory management, and reduction of error-prone features of C++ such as multiple inheritance, pointers, operator overloading, etc.
Multiple inheritance is not allowed in java because it's hard to implement. So sun chose interfaces instead. The "It's just too error-prone"-argument is an excuse. If you design a language with this attitude in mind only idiots will use the language.

Java is easier than C++ but at what cost?

---

### Post by Modred on 2007-11-29
> **uljanow said:**
> Java is easier than C++ but at what cost?

I cannot agree more.  Our university switched the introductory programming courses from C++ to Java this semester, and I had the lovely job of TAing for this first semester.  Perhaps it was just a case of misplaced priorities, but the curriculum was broken from the beginning; while the professors showed examples of Swing, us lab instructors had to teach if-else logic, while loops, and come up with some way to explain  to students what all these errors dealing with classes are without explaining OO programming (which is not a part of the course and would only confuse them).

With C++, there was never the temptation to teach how to make something "fancy" like an applet before learning simple constructs like if-else blocks, loops, and methods.

---

### Post by slavik on 2007-11-29
> **LaRoza said:**
> Who makes these decisions? The educators or a board?

MIT uses Python, after Scheme.

Some say to start with HLL, like Python, Perl, etc, some say start low, assembly, C, I can think of reasons to support both of these recommendations, however, I cannot think of a reason to use Java as a first language over others.

We all know that Python can be used to program in the 3 largest paradigms (OO, declarative, functional). Scheme can only do functional.

When MIT taught using Scheme, they taught functional programming.

Since MIT switched to Python, how do they introduce Python?

Is it using the OO paradigm? Doubt it, since C++ or Java or even C# can handle that one as well as Python can.

Is it using functional paradigm? Doubt it, then what's the point of switching?

Are they teaching Python as a declarative language? I would say yes. I would further say that a vast majority of Python code is written using the declarative paradigm (just like Perl and C).

MIT's shift from Scheme to Python doesn't say anything about either language (whether one is better than the other). To me their switch is a paradigm shift from functional to declarative.

Please note that I haven't taken their new CS course, nor do I know anything about it. If you do know how it is taught, please do reply and correct any mistakes/errors I have made.

a Perl line:
map { $words{lc($_)}++ } split /\W/, $input;
#generates a key value pair from input counting how many times each word appears. (makes all words lowercase) (may contain some garbage data)

---

### Post by LaRoza on 2007-11-29
> **slavik said:**
> 
MIT's shift from Scheme to Python doesn't say anything about either language (whether one is better than the other). To me their switch is a paradigm shift from functional to declarative.


Yes, but it shows the language chosen (could have been a few others, including Perl and Ruby) will enable the introduction of programming in a logical way.

I am saying there isn't much sense to learning Java as a first language. 

It is a lucrative language and popular, but isn't the best for instructional purposes.

Imagine teaching it "This language is called Java, it isn't compiled, well sort of, I'll explain later. Here is the first tradtional program, the 'Hello world' program, I know you don't understand it, but I'll explain all that during the course, but for now, this is what the smallest program looks like."

Or one could expain OO, Functions, and syntax immediately.

Whereas in Perl, Python, and Ruby, such concepts can be introduced logically and without confusion.

Or with Assembly, learning the inner workings with the simplest possible programs, will be more benificial than immediate exposure to a rather developed science all at once.

---

### Post by slavik on 2007-11-29
I agree that Java is not the best choice as an introductory language.

My point in MIT case that they switched from functional programming as instroductory to CS to declarative programming as introductory to CS. And it doesn't show anything about the language. :)

---

### Post by dwhitney67 on 2007-11-29
> **LaRoza said:**
> Yes, but it shows the language chosen (could have been a few others, including Perl and Ruby) will enable the introduction of programming in a logical way.

I am saying there isn't much sense to learning Java as a first language. 

It is a lucrative language and popular, but isn't the best for instructional purposes.

Imagine teaching it "This language is called Java, it isn't compiled, well sort of, I'll explain later. Here is the first tradtional program, the 'Hello world' program, I know you don't understand it, but I'll explain all that during the course, but for now, this is what the smallest program looks like."

Or one could expain OO, Functions, and syntax immediately.

Whereas in Perl, Python, and Ruby, such concepts can be introduced logically and without confusion.

Or with Assembly, learning the inner workings with the simplest possible programs, will be more benificial than immediate exposure to a rather developed science all at once.

Your argument is very good.  I am not here to weigh upon its merit.

However, there are many cases where Java _is_ compiled.  Look up JIT, or Just In Time.  If you have been around long enough, you would know that Java was conceived to be a language that could be used anywhere, including toasters and microwave ovens (and obviously other embedded applications); not just the WWW and desktop computers where it must be "interpreted".

---

### Post by LaRoza on 2007-11-29
> **dwhitney67 said:**
> Your argument is very good.  I am not here to weigh upon its merit.

However, there are many cases where Java _is_ compiled.  Look up JIT, or Just In Time.  If you have been around long enough, you would know that Java was conceived to be a language that could be used anywhere, including toasters and microwave ovens (and obviously other embedded applications); not just the WWW and desktop computers where it must be "interpreted".

I know all about that. It is compiled to byte code, then executed in the "JVM", and about JIT and its original intent (appliances).

Java is a versitle language, but requires a grasp of programming concepts to learn it. With other languages, concepts are introduced one at a time, whereas Java is written for programmers.

That was my only argument against Java. I am not a Java hater, although I do not have a use (yet?) for the language for my personal use.

---

### Post by CptPicard on 2007-11-29
Hmm, Java isn't *that* bad. Yes, I'm sure that it's probably better to start off with something else, but especially in comparison to C++, Java is just so much simpler if you start with the assumption that you're going to be learning OOP concepts in your introductory course, as I did -- my introductory programming language at uni was Java. I, for one, can't think of a reason for having C++ as the first language... having System.out.println in your Hello World isn't much better than std::cout <<. (Simplicity of Hello World is a really bad argument in general though).

Java is a kind of general compromise language, and this why it seems a bit bland in some respects. That's also probably it is probably popular :)

Modred's example just shows the person who designed the class was incompetent as a teacher, not that Java is the problem.

And slavik -- Scheme *can* do even imperative programming... that's what the (foo (x) (y) (z)) constructions are for. x and y are side-effects, z provides the value. And OOP in Scheme is simple -- you just create a lambda with a closure, and process messages in that lambda that manipulate the values in the closure.

It's sort of sad that MIT decided to move away from Scheme as introductory language -- after all, the syntax part of Scheme is explained really quickly, so you can then move on expressing problems in that language...

---

### Post by LaRoza on 2007-11-29
>Simplicity of Hello World is a really bad argument in general though)

I wasn't comparing the languages, just the teaching of them. 

>Java is a kind of general compromise language, and this why it seems a bit bland in some respects. That's also probably it is probably popular :)

Java isn't the most exciting language, true, but it works for what it is used

>Modred's example just shows the person who designed the class was incompetent as a teacher, not that Java is the problem.

Exactly. The people who decide what should be taught are rarely those able to make such decisions.

>It's sort of sad that MIT decided to move away from Scheme as introductory language -- after all, the syntax part of Scheme is explained really quickly, so you can then move on expressing problems in that language...

For one who has never taken courses in programming, I can't be sad because I feel no matter what is taught in school, a real programmer will learn without formal instruction.

---

### Post by CptPicard on 2007-11-29
> **LaRoza said:**
> 
For one who has never taken courses in programming, I can't be sad because I feel no matter what is taught in school, a real programmer will learn without formal instruction.

Yet, universities do choose to teach intro courses in programming.. ;) although I agree that for anyone who deserves to be in that school, probably doesn't need to take the class.

Mind you, one of my most brilliant student mates -- and the only lady in our age group who went on to being a researcher -- started from the very scratch and is now writing her doctoral thesis... so it is doable.

The whole point of Scheme is really that you can get the syntax part out of the way quickly, and then move on to the ideas part. That's what you get an education for, really -- teaching programming language syntax is a stupid exercise and is mostly wasted.

---

### Post by sloggerkhan on 2007-11-29
At my university the computer science department starts with Java. In engineering (for computer engineers and systems engineers and such) they start with c. 
I personally think if you have used any language besides java before using java, parts of java will always seem extra weird. And it definately isn't a CLI oriented language. 
However, it works decently for a beginner language witha propper curiculum, IMO.

I will, however, vouch for profs who can't teach it because they always sidetrack themselves into minutae when their students need the overall concepts.

---

### Post by meatpan on 2007-11-29
> **bluewagon said:**
> 
For instance,
in C++ to have a user input something (lets say an int) you type 
cin << int_variable;


Professors teaching introductory courses are frequently faced with a catch-22 when selecting programming languages.  Many have been assigned  the responsibility to preparing the student for the competitive 'real-world' where you must know the most recently hyped language.  They also receive pressure from the department that they need to use various other languages to teach specific programming paradigms, or to completely avoid syntax and system related frustrations so the student can focus on more abstract computer science principles.    

One technique that is difficult, but tends to produce good results, is to focus your class work on learning CS fundamentals and principles.  Take some applied math and statistics.  Don't be afraid to take an AI course from a good instructor that makes you write Scheme, or ML, or whatever.  The lessons learned in these courses will help you over the course of the career, regardless of which language is currently popular.    Now, apply for work studies or internships or volunteer to do work  that uses the 'real' programming languages to solve problems.  This is where you can build up the specific pre-req experience typically necessary for your first job or two.

On an unrelated note, what happens when you run the code snippet above?

---

### Post by dwhitney67 on 2007-11-29
> **LaRoza said:**
> I know all about that. It is compiled to byte code, then executed in the "JVM", and about JIT and its original intent (appliances).

Java is a versitle language, but requires a grasp of programming concepts to learn it. With other languages, concepts are introduced one at a time, whereas Java is written for programmers.

That was my only argument against Java. I am not a Java hater, although I do not have a use (yet?) for the language for my personal use.

JIT does not just compile to the byte code, which needs to be interpreted, but to the opcode which is understood by the CPU itself.  Java can be just as "efficient" as other programming languages, but in it's general common-place use, it is not because it is compiled with "javac" which produces the byte-codes which must be interpreted.

As for being a versitle language, well that's open for debate.  However, if it is not for programmers, then what is it for... English composition?  One thing that can be said for Java is that it enforces the OO paradigm, whereas some other languages do not (e.g. they allow the usage of global variables).

P.S.  Above, I placed "efficient" in quotes because I have never done a study, nor have I read any documentation, as to whether a Java application is just as quick as say C++, to execute.  But in theory it is as efficient... as long as it doesn't have to be interpreted.

---

### Post by [h2o] on 2007-11-29
> **LaRoza said:**
> because I feel no matter what is taught in school, a real programmer will learn without formal instruction.
Honestly, then you are a bit of a fool. I have never understood why so many people keep claiming this. No one would ever say "a real surgeon will learn without formal instructions", because it is clearly ********.
Yes, I think programming at home improves your programming skills, but I doubt that most people who only program at home will have the same width of knowledge as someone who have attended a good formal education. There are tons of information that you will just never touch unless someone forces you to.

As for my education, they start teaching functional programming with Lisp. Then we move to imperative programming with Ada, and finally OOP with Java. That gives a solid base which makes it easy to use and learn other languages which frequently crops up in other courses.
Add to that courses in math, data-structures, operating systems and concurrent programming, computer engineering ... and tell me how the h-ck someone should learn all this from their basement.

Ok, sory for the rant, but the whole "real programmers are not educated" really pisses me off.

---

### Post by samjh on 2007-11-29
> **LaRoza said:**
> Who makes these decisions? The educators or a board?At my alma mater, it was the individual professors.  With a faculty where the most senior professors taught intro courses, they exercised considerable liberty at choosing what to teach. :)

For Information Technology, the intro language was Java, and later any .NET language.

For Electrical Engineering, the only languages were Assembly, C, and C++.

For Computer Science, students could choose whatever, although Java was mandatory.

Software Engineering students (which I was) had to learn all of the above. :(

> I cannot think of a reason to use Java as a first language over others.Easy.  Java is the easiest mainstream general purpose programming language.  It has the best balance of ease of learning, ease of use, and industry relevance. :)

---

### Post by CptPicard on 2007-11-29
> **'[h2o] said:**
> Honestly, then you are a bit of a fool. I have never understood why so many people keep claiming this. No one would ever say "a real surgeon will learn without formal instructions", because it is clearly ********. ...
Add to that courses in math, data-structures, operating systems and concurrent programming, computer engineering ... and tell me how the h-ck someone should learn all this from their basement.


I fully support LaRoza's position -- the *programming* bits as far as syntactic and API knowledge issues are concerned, can be learnt on your own. I have. I didn't gain anything from taking the classes that teach the *languages* -- I just took the exams for the credit (and because some of them, I had to).

The latter part of your argument goes beyond what I think LaRoza and I are arguing. Those that you mention are non-language-specific conceptual things, that you *do* need to go to school for, and they are actually things I'd want to see emphasized more in formal CS education, instead of turning more and more CS programs into code monkey schools.

I would go as far as stating that you can't really "teach" the fundamentals of programming. You have to work at it on your own anyway. It's a bit like learning a foreign language -- you can't just pour it into someone's head.

---

### Post by sonofusion82 on 2007-11-29
math, data-structures, cryptography, OS and stuffs cannot easily be self-taught. but there are somethings that can never be taught in schools, programming skill, good OO design and software architecture will only come with experience. books may help but ultimately, it depends to a programmer's creativity and good problem solving skills to write good codes. 
i guess this is similar situation for business schools, these days anyone can easily get an MBA but that does not automatically make someone a good businessman.

---

### Post by tyoc on 2007-11-29
Being a person that learned alone by his own way different langs (dont know how "skilled" Im in those langs), but C++, java, asm, PHP, JS, TXL, and others langs I can count in the list.

My personal experience, for me was more easy to learn C++ (the major part of what I know of I learned it in a day... less than) with jave it taked more time. Thats just my case. Also I havent programmed in any of them to this day at work... IIRC I learn java and C++ at the same time.

---

### Post by iharrold on 2007-11-29
> **dwhitney67 said:**
> Your argument is very good.  I am not here to weigh upon its merit.

However, there are many cases where Java _is_ compiled.  Look up JIT, or Just In Time.  If you have been around long enough, you would know that Java was conceived to be a language that could be used anywhere, including toasters and microwave ovens (and obviously other embedded applications); not just the WWW and desktop computers where it must be "interpreted".

There are a few Java native processors on the market as well. [www.ajile.com/downloads/jemcoreproductbrief.pdf](www.ajile.com/downloads/jemcoreproductbrief.pdf)

Of course, I think Java is too high level for teaching introductory languages.  But I guess I am old fashioned, I still remember being in 6th grade writing Basic'ish languaged programs for my VIC-20 computer and storing them on Cassette tape.  Then when Dos came around I hopped on board and took up Pascal, then stepped backwards to Assembly then went forwards with C++.

---

### Post by jespdj on 2007-11-29
In my opinion it is good if people in schools learn **low-level** programming languages, not just high-level languages like Python, Ruby or Java.

Someone who is learning information technology or computer science should understand exactly how a computer works - what a microprocessor does and how data is stored in the computer's memory.

I'm regularly visiting different programming forums and there are a lot of people asking questions that show that they have no idea how a computer works internally. For example, they don't know how numbers are stored in the computer's memory, and they think that a hexadecimal number is a special kind of number that is different from a decimal number or a binary number. Many people don't understand what IEEE-754 floating point numbers are and that they are not infinitely precise. Many people have no idea how text is stored in the computer's memory and what ASCII or other character encodings are.

I'm not saying that people should learn **only** low-level languages, but if you want to be a serious software developer, you must know how a computer works.

---

### Post by [h2o] on 2007-11-29
> **CptPicard said:**
> I fully support LaRoza's position -- the *programming* bits as far as syntactic and API knowledge issues are concerned, can be learnt on your own. I have. I didn't gain anything from taking the classes that teach the *languages* -- I just took the exams for the credit (and because some of them, I had to).
That I can accept. I have not had special classes for languages. Only programming classes that happened to use a specific language.

> The latter part of your argument goes beyond what I think LaRoza and I are arguing. Those that you mention are non-language-specific conceptual things, that you *do* need to go to school for, and they are actually things I'd want to see emphasized more in formal CS education, instead of turning more and more CS programs into code monkey schools.
I agree.

I might have overreacted or misunderstood. If that is the case, I apologize. My opinions on the matter still stands though, since I have come across it before.

---

### Post by pmasiar on 2007-11-29
> **'[h2o] said:**
> the whole "real programmers are not educated" really pisses me off.

It is not about being educated or not. Of course is good to be educated. But programming is a craft, passing exams and certification tells nothing about if you can design system, code and debug it. And this is learned only in the trenches. Someone said you need 10 years to become programmer - it is beyond syntax. In schools, they teach mostly syntax, or general courses not specific to any language, as CptPicard mentioned. 

My warmest memories are for "comparative study of programming languages" where we went through basics of syntax and concepts of many languages, stopping for a week or two on each. FORTRAN, COBOL, PL/1, Algol, Pascal, Lisp, ML, ADABAS SEQUEL (it was before SQL :-) ) and many more.

---

### Post by LaRoza on 2007-11-29
> **'[h2o] said:**
> Honestly, then you are a bit of a fool. I have never understood why so many people keep claiming this. 

As for my education, they start teaching functional programming with Lisp. Then we move to imperative programming with Ada, and finally OOP with Java. That gives a solid base which makes it easy to use and learn other languages which frequently crops up in other courses.

Add to that courses in math, data-structures, operating systems and concurrent programming, computer engineering ... and tell me how the h-ck someone should learn all this from their basement.


I agree with you are saying (other than the part about me being a fool).

Courses in math, data-structures, OS, and concurrent programming, computer engineering, etc are where the **focus should be**. At my school, the CS majors are taking classes in VB, Java and C++. There is a class on "web development" (html) and project management. I asked the program director why there were no worthwhile class (he knows I am a self taught programmer) and he agreed, but it is not his decision what classes are taught.

Anyone can learn syntax, learning the other programming concepts is harder. I do have books on data structures (really good and in depth book), operating systems (Minix) and other CS topics. I wish I could get an experienced programmer to teach me these things.

---

### Post by LaRoza on 2007-11-29
> **'[h2o] said:**
> 
I might have overreacted or misunderstood. If that is the case, I apologize. My opinions on the matter still stands though, since I have come across it before.

You did misunderstand, and since I agree with you position mostly, I can add no more.

(Learning the syntax and API's of a language is an easy thing to do and should be mostly self taught)

---

### Post by Tomosaur on 2007-11-29
I don't know what kind of crappy education system you guys have worked through, but my university teaches all of these things. In fact, we only really brushed over actual languages (we mostly used Java, but they were pretty lenient, particularly this year, my final year, where they just said 'do whatever you want, just make sure your software fits the requirements').

Most of the work has been theoretical in nature, looking at systems, math, set-theory and all of the 'surrounding stuff'. My course? Software Development. Very little of it is based on how to actually go in and write software, they teach you all of the surrounding stuff, and the ability to actually write code comes kind of naturally. We're expected to learn any languages we want to learn in our own spare time - the only languages we were ever officially 'taught' (and only really enough for the in-class demonstrations) were Java, a bit of C, and some assembly.

---

### Post by bluewagon on 2007-11-29
yea, i did make a mistake its cin >> int_variable, I always at first want to use << because i use cout a lot -_-

anyways, yea I guess my statement isnt fair sense I havnt done much in memory management in C++ aside from sometimes using new and delete and never in Java, and havnt gotten to do what you guys are saying what makes it easy

but off-topic, from what i read in the responses, you guys are saying that the best way to learn languages is to first study data structures and other programming topics? is there a thread talking about the best books to read? (Don't worry ill search for it, just wandering if anyone knew of it quickly) as most threads I see are debating over which language first, not which concepts

---

### Post by [h2o] on 2007-11-29
> **pmasiar said:**
> Of course is good to be educated. But programming is a craft, passing exams and certification tells nothing about if you can design system, code and debug it. And this is learned only in the trenches. Someone said you need 10 years to become programmer - it is beyond syntax. In schools, they teach mostly syntax, or general courses not specific to any language, as CptPicard mentioned. 
I both agree and disagree. I recently took a course in software production theory (as a preparation for next years big software production project), and I feel much more comfortable with the whole concept of working with software. I have written quite  alot of code before, but always on my own. Thinking of stages, methods, testing, specifications and all that are part of the real world was not something I could have learnt at home. Sure, I would probably get the hang of it once I start working, but now I will have tried it and read about it in school.

If the schools you have seen only teach syntax, then I really feel sorry for your schools. I've had crappy programming classes as well, but that was at high school. On University level all courses have been very helpful, and quite often damned hard.

---

### Post by [h2o] on 2007-11-29
> **Tomosaur said:**
> We're expected to learn any languages we want to learn in our own spare time - the only languages we were ever officially 'taught' (and only really enough for the in-class demonstrations) were Java, a bit of C, and some assembly.
I recognize this. We are currently doing a lot of stuff in C (robot project and a course in operating systems) but there has been no previous course in C. It is assumed that we learn what we need to solve the problem at hand. Sure, I need to look at the documentation frequently, but I don't think that is a problem.

---

### Post by iharrold on 2007-11-29
> **'[h2o] said:**
> I recognize this. We are currently doing a lot of stuff in C (robot project and a course in operating systems) but there has been no previous course in C. It is assumed that we learn what we need to solve the problem at hand. Sure, I need to look at the documentation frequently, but I don't think that is a problem.

You'll find this "learn" is the way it is after college.  I contracted to a research facility (which I won't name) to help them with some work (not software related.  Anyways, I remember the manager a really great guy by the way, say "Your an engineer with a higher education,  That means we expect that if you don't know something you will go figure it out on your own through your own research".  I think those are words to live by.

---

### Post by LaRoza on 2007-11-29
> **Tomosaur said:**
> I don't know what kind of crappy education system you guys have worked through, but my university teaches all of these things.


What university?

---

### Post by Tomosaur on 2007-11-29
University of Liverpool - UK.

The worst thing about the computer science department is the picture they have on their home page: [Clicky](http://www.csc.liv.ac.uk).

---

### Post by LaRoza on 2007-11-29
> **Tomosaur said:**
> University of Liverpool - UK.

The worst thing about the computer science department is the picture they have on their home page: [Clicky](http://www.csc.liv.ac.uk).

Not everybody can go to the best universities where the programs are well designed albeit with weird visual tastes.

---

### Post by Tomosaur on 2007-11-29
> **LaRoza said:**
> Not everybody can go to the best universities where the programs are well designed albeit with weird visual tastes.

I never said they could :/

Just because a badly designed course is all you have available to you doesn't mean it's not bad.

---

### Post by [h2o] on 2007-11-30
> **LaRoza said:**
> Not everybody can go to the best universities where the programs are well designed albeit with weird visual tastes.
Then I think it is time to complain to the people in charge of education in your country.
Or find a university abroad.

---

### Post by Balazs_noob on 2007-11-30
> **'[h2o] said:**
> Then I think it is time to complain to the people in charge of education in your country.
Or find a university abroad.

1, by the time anything would change it is already late :(
2. Just a few people can afford that :(

---

### Post by [h2o] on 2007-11-30
> **Balazs_noob said:**
> 2. Just a few people can afford that :(
I guess that depends on where you are heading, how things work in your country and how poor you are.
As for now, Swedish universities are free of charge (except a fee to the student union, which is like 100$ a year, can't remember exactly though) even for foreign students. I am not sure whether or not foreign students are elegible for student loans and/or student allowance though. I guess there might be more countries which have the same generous rules as well.

---

### Post by kvorion on 2007-11-30
I dont think that Java should be taught in universities as a first programming language. The simple reason is that Java is not hard enough. I started out with basic as my first programming language in school and then I moved on to C and C++.

I have been developing software on the .NET framework for quite a while now and I feel that these managed languages like Java and C# really do not do justice as far as computer science is concerned. If you start out with a language like java, you can never hope to learn how pointers or recursion work. Agreed, that Java is hip in the market today, but without studying a functional programming language like C one can never expect to do things like study the linux kernel. Maybe studying the linux kernel is not one's requirement, but dealing with things like recursion and pointers trains one's mind to work at an altogether different level of abstraction that one can never get when working with a managed language like Java or C#.

---

### Post by [h2o] on 2007-11-30
> **kvorion said:**
> but without studying a functional programming language like C one can never expect to do things like study the linux kernel.  C is not a functional language. It's an imperative language. Otherwise I agree, but I don't think C should be used as a first language either.

---

### Post by LaRoza on 2007-11-30
> **'[h2o] said:**
> Then I think it is time to complain to the people in charge of education in your country.
Or find a university abroad.

There are two very good universities in my city, and a bunch of other schools. They all have strengths and weaknesses.

Not everybody can learn CS at MIT.

---

### Post by CptPicard on 2007-11-30
> **LaRoza said:**
> 
Not everybody can learn CS at MIT.

While I'm of course not underestimating MIT, I don't you *need* to go to MIT to go study CS -- although it's probably cool to. Your typical Master's programme in CS is something you can do at any half-decent university and be competent, and if you're good, you're still not limiting your future options to the slightest.

Just as an example, my alma mater certainly isn't MIT but I'm perfectly happy with the piece of paper I got from there when I graduated -- after all, the guy who wrote Linux has exactly the same one... ;) The Master's program is "as good as any" and even the research isn't all that bad...

Some of the posts in this thread compare apples to oranges... it's the Computer Science vs. Software Engineering distinction. Personally I found the mandatory SE classes horribly dull, and took as little of them as possible... it made me feel like I was getting an MBA. The CS theory classes on the other hand never really made you write code, as the general sentiment was that it's too much work for little gain -- it does not neccessarily add to understanding. Plus, there is the added burden of someone actually having to grade programming projects...

---

### Post by Tomosaur on 2007-11-30
> **LaRoza said:**
> There are two very good universities in my city, and a bunch of other schools. They all have strengths and weaknesses.

Not everybody can learn CS at MIT.

Why do people insist on using this as some kind of excuse? You should be ANGRY that the education available to you is not the best it can be, not complacent about it. Just because you can't go to MIT doesn't mean you should have to put up with a poorly designed education.

---

### Post by CptPicard on 2007-11-30
And oh yeah LaRoza, if you're wanting to get into the data structures etc part of programming, you really really want to get your hands on **Cormen, Leicerson, Rivest, Stein: Introduction to Algorithms**. Go get it already -- it takes you a long way and is very readable for your level. Gives you a nice toolkit too, once you're through.

---

### Post by tyoc on 2007-11-30
lol, the fact is that the education all around the world is bad. 

Goverments know that, people know that, but that will not change.

Where I live, Im sure that also the "pay for enter" schools are as bads as public ones or worse, no way (still they have best reputation for being paid), there is a minor part of schools that can save this... also I remember a independent school (from 12 to 15 year old), time after I terminate it, it has pass to the state/goverment institution that "care" about education for manage it, and it fall from being in the first places and recognogized in my country to a "normal shape" or the status quo of the rest of schools at that level, you know schools are like a factory for blue print similar minds (and almost not very good the major part of them).

Why I would be angry for that?, Im amused because like I see, is almost the same all around the world, there are the less countries where you can count a "good education", still I think it can be best even in those places...

---

### Post by kknd on 2007-11-30
Java is very verbose and aren't easy to learn. I wouldn't leran programming logic with C++ or Java. I suggest Lua or Pascal for learning the basics of procedural programming, then something OO / functional.

---

### Post by tyoc on 2007-11-30
at school they teachme first pascal and then C, in fact I almost fail in pascal (I "hate" that lang procedures/funcitons?? shame on me!!!), C was a miracle for me, all the things I dont liked of passcal where clear and gone when I learn C, and I think o yea, this is a lang (for me).

Lua is interpreted, isnt?, perhaps it will skip somethings that C can show some errors that you will need to know, understand handle, and "manage" aka write good code, C is the more near to asm you can go in an HLL.

---

### Post by kvorion on 2007-12-08
> **'[h2o] said:**
> C is not a functional language. It's an imperative language. Otherwise I agree, but I don't think C should be used as a first language either.

Yup, my bad.

---

### Post by Old Schoolz on 2009-05-05
For me, I learnt java as a starter program. I code runescape servers, so i didnt really have a choice. However, my school teaches basic for the kids that want to learn coding. I guess it is the easiest to learn hense-forth "basic".

---

### Post by Kilon on 2009-05-05
People think differently , even though our brain is pretty much the same machine , each person falls under diffirent kind of category. 

So choice of language is not mere preference. People try to find what fits their thinking pattern. Because if you can understand the language it will be easy to understand the solution to a problem that you try to solve with the language. 

So I think it is more than a simple statement of "Java is easier/ harder than C++". That is why people keep making computer languages as if there are not already too many of them. The differences migh be small but still can be gravely important. 

When you know that you will spent hundred , thousands or in short a large part of your life coding then you want to be certain that you choose the one close to your way of thinking. Even the smallest difference becomes hugely important.      

Of course escaping the familiar pattern (also known "comfort zone") can be also a good reason to choose the "harder language" , it might be an opportunity to expand your horizons beyond your normal understanding , get used to different ways of thinking.

---

### Post by cobolt01 on 2009-05-05
> **bluewagon said:**
> I see a lot of people say things like Java is a good starting language because its easy to learn and what not, but so far it seems more confusing than C++.
For instance,
in C++ to have a user input something (lets say an int) you type 
cin >> int_variable;
but in Java, you have to have a buffer reader, and have a string variable for every int(or any other type) and then have to convert from string to int(or any other type)

When people talk about how easy or hard a language is, they're not referring to something simple like how text is read from the keyboard.

It's not really that complicated to declare a buffered reader.
```

import java.io.*;
// import the package
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
//This looks complicated but if you understand it, it will make it easier //to read other types of streams eg. from files
int value = Integer.parseInt(br.readLine());
//as Java is strongly typed (like C/C++) you need to convert the data type

```
If you just understand what is being done, its not hard to remember the names, letters whatever. _Java is easier to understand than C++, but beginner programmers need to understand the difference between understanding and just remembering the code._
If you think understanding is remembering a line of code like a parrot, then yes that line of C++ is easier, but what about when it comes to methods, objects, inheritance, real concepts you cant just regurgitate it mindlessly.

---

### Post by Vyder on 2009-05-05
> **bluewagon said:**
> 
For instance,
in C++ to have a user input something (lets say an int) you type 
cin >> int_variable;
but in Java, you have to have a buffer reader, and have a string variable for every int(or any other type) and then have to convert from string to int(or any other type)

But everything is pretty much ready-made in Java. You just have to use a bunch of pre-made classes. 

For instance, in java, the easier way would be to use the Scanner class to read input. And you may find having strings and such really useful.

I started in C++, but am completely converted to Java now.

---

