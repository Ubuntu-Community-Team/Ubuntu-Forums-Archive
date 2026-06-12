---
title: "Why Python?"
date: 2006-09-05
forum: Programming Talk
---

### Post by dmjohnson on 2006-09-05
I am new to Linux but have been programming in other environments for almost a decade.  I have been reading in the forums and saw some comments that lead me to the understanding that most Linux programming is done in Python.  Is that true?

If so... I just wondered if anyone knew why.  Not that I have anything against Python but Python is an interpreted language.  As a general rule I have always been told that interpreted languages are best for smaller amounts of code such as using Javascript for formatting in Web development.

I was under the beleif that use of a compiled language was better for mass coding.  This is neither a bash or a challenge against Linux or Python - just trying to expand my knowledge.  Thanks for any comments.

---

### Post by blaamann on 2006-09-05
> **dmjohnson said:**
> I am new to Linux but have been programming in other environments for almost a decade.  I have been reading in the forums and saw some comments that lead me to the understanding that most Linux programming is done in Python.  Is that true?


No it is not. Most part of "Linux" (both the kernel and apps running on top of the kernel) is written in C. 

Python is a popular language gaining momentum for some time and is increasingly used for user and system application, but it can't be used for everything.

---

### Post by sysops on 2006-09-05
Linux programming is a broad term and depending on which part of this spectrum you refer to, different programming languages have their niches. But there are reasons why some languages are right for some kinds of programming while others might be able to do the same jobs but invloving them in doing so is overkill.

Interpreted languages like python are easier to code in, they were designed with the goal of achieving simple, modular and scalable code in mind (atleast  that's true for most of the newer interpreted languages anyway).And also since python is object oriented the modularity or achieving it is made easier and programs written in python scale well, which makes python a great choice (almost ubiquitous) for writing applications for the gnome/kde desktop enironments, a good majority of desktop applications in these environments are the product of python code.

But interpreted languages lack what compiled languages like C and C++ offer, the fine grained data structures, the ultimate control in the hands of the programmer, the ability to interact directly with hardware, services, etc. Which makes C/C++, etc well suited for writing kernels or those apps that require tight integration with the kernel, perhpas even those that depend on realtime speed. The downside to these languages which probably gave rise to interpreted languages was predominantly gargage collection which had to be done manually. Code that wasnt written properly could end up having a memory leak and data structures that werent tied or secured properly could be exploited and since the end programs are usually tied closer to the system than their counterparts, they end up exposing the system in attacks e.g. buffer overflows etc.

So again, your choice of language depends on the job at hand. choosing C to develop a desktop application might work, but it's more cleaning up after yourself and tougher troubleshooting. Choosing python to go about writing a kernel-mode driver would be impossible because of the lack of the datastructures and the need for the interpreter to be around to interpret the code. Also, Are you a applications designer or are you a systems/network administrator? Python would work for both but object oriented code is generally lenghtier and therefore quite unsuitable for generating simple throw-away code used in administration -- come in perl. Do you want your applets avaiable across browsers and platforms - come in Java. Do you want .NET -- ehh, let's not go there.

:)

---

### Post by maddog39 on 2006-12-17
I hate compiled languages for the mere fact that they have data structures, I find them very hard to use and difficult to understand, I have a good deal of knowledge in C/C++/Java and have written small programs in all of them. GUI's included. Although, the statement that interpreted languages are only meant for or arent/cant be used for big applications is definetly irrelavent. For example, this very forum software you are using rght now to view this message, is written with somewhere around 50,000 lines of PHP code and probably about a thousand or so lines of JavaScript. Also, many applications, especially graphics/3D ones use python. A few examples would be: GIMP, Blender, and 3D Studio Max, all use Python.

---

### Post by Wybiral on 2006-12-17
GIMP and Blender use python as a scripting language, they weren't written in python. I use python as a scripting language in a lot of my programs too, I believe the reason they use it isn't because it handles graphical stuff well, but because it is object oriented and easy to embed in a program to act as a scripting language.

I'm going to have to agree that python is hard to write large projects in... I like python a lot, but I much prefer C++ for my large stuff than python. It's very restriction in terms of isolating data, globals and constants are very difficult to work with and the speed for CPU intensive programs is not too great.

But, if you need someone easy and quick to write, and speed isn't a main concern, go ahead and try python. It does very well with smaller applications and has a lot of good GUI toolkits. Python is a very useful language, but it's perks that make it so convenient for small applications make it a nightmare to write large programs in.

---

### Post by pmasiar on 2006-12-17
> **dmjohnson said:**
>  I was under the beleif that use of a compiled language was better for mass coding.  This is neither a bash or a challenge against Linux or Python - just trying to expand my knowledge. 

C/C++/java as compiled, strongly typed languages vs. python/ruby/perl as interpreted, dynamically typed languages was discussed in last week at least 6 times. To avoid repeating same arguments, let's link:
[LIST]
[*][c++ for dummies???]("http://ubuntuforums.org/showthread.php?t=320259") comment #15 and later
[*][Comparing C++ to Python]("http://ubuntuforums.org/showthread.php?t=316601") speed is discussed in comment #10 and later
[*][PHP vs Python]("http://ubuntuforums.org/showthread.php?t=315087")
[*][Ruby on Rails vs Python]("http://ubuntuforums.org/showthread.php?t=317309")
[*][ Python or Ruby?]("http://ubuntuforums.org/showthread.php?t=308831")
[*] [Best crossplatform programming language]("http://ubuntuforums.org/showthread.php?t=314348")
[/LIST]

---

### Post by pmasiar on 2006-12-17
> **dmjohnson said:**
>  As a general rule I have always been told that interpreted languages are best for smaller amounts of code

Why dynamic typed language like python can be *especially good* for big systems? because when you program big systems:

[LIST]
[*]You have unit testing - testing for valid types is the easy start for other tests
[*]You need to build prototype fast, to show users, to get faster to inevitable changes in specifications
[*]When (not if) specifications change, with dynamic language it is easier to make happen
[*]After code is working, you can profile performance and find 5% which takes 80% of the time. As they say, you cannot guess it, you need to measure it. Then, reprogram 5% as C library
[*]Less lines of code - easier to maintain and add new features
[*]Most important speed in code project is speed to market
[/LIST]

Of course if you programming kernel, do it in C. For embedded devices, I heard FORTH is still popular - and it is ultimate interpreted language. If you have government contract, you do it in ADA, not in free language. But test scaffolding  might be done faster still in python. :-)

---

### Post by Wybiral on 2006-12-17
I still don't think "Most important speed in code project is speed to market"...

But, python can be fast if used correctly. However, most of the time C/C++ will win. Another advantage of C/C++ is that they don't require your user to have python installed, obviously this works both ways because the advantage python has is that most code in it will be portable because the python interpreter handles the portability issues. I've attempted large projects in python and can tell you that it becomes very messy.

However, one advantage python has, is that you can write modules for it in C/C++... That means that if you have a chunk of code that python doesn't handle well, write it in C/C++ and compile it as a module (I'm in the process of writing a tutorial on this, I'll post it soon).

I'm not the kind of person to say that the majority is right, and in most cases the majority is wrong... But there is a reason most python projects stay small... Because it becomes challenging to maintain when they get big. Partially due to a lack of convention... C++ has it's headers and source, so if you need to find a function without sifting through code, you can check the header.

Variables must be declared in C/C++ so if you are working with a large project, you can often find the declaration to determine the type... You cannot do this in python, you would have to sift through to find it's origin and that can be very time consuming with large projects.

Global variables that you need to use between functions are also very difficult to work with in python, as are constants. It seems to be more of a hassle than a blessing... C++ allows for globals, constants, and scoped variables with ease. It doesn't force you.

Also, a key point in object oriented programming is data encapsulation... Python offers very little ability to hide things. This could cause problems in larger programs as well...

But, I mean well... I'm not trying to bash python, I actually like python a lot, but I don't think it handles large projects as elegantly as C++.

---

### Post by pmasiar on 2006-12-18
> **Wybiral said:**
> I still don't think "Most important speed in code project is speed to market"...

That's easy, just ask your boss: is she ready to pay you 3 months salary so you possibly may shave .2 sec off of execution time? :twisted: 

>  I've attempted large projects in python and can tell you that it becomes very messy. 

What are your biggest codebase (KLOC or KB of code) in C++ and python? maybe you could use more experienced project manager or lead programmer? Or maybe try better code editor than gedit, like SPE? :twisted: 

>  But there is a reason most python projects stay small... Because it becomes challenging to maintain when they get big. Partially due to a lack of convention... 
Variables must be declared in C/C++ so if you are working with a large project, you can often find the declaration to determine the type... You cannot do this in python,

I teach you one trick: All my programs have globals/constants section:
```
##--- Package Globals (comments like ##--- creates bookmark in SPE)
GLOBAL1 = None # comment about usage and init
CONSTANT1 = x # explanation 
```

You are not **required** to do that, but it is smart thing to do, if you need that. IMHO.

Constants (if you need them) can be implemented in 6 lines of code, I provided you link last time you complained about "lack of constants in python", and you can customize it as (and if) you need. Put code in your big project standard program header, and forget about it. Even cool trick how to fake 'include const' in every module was in the recipe, I liked it.

>  a key point in object oriented programming is data encapsulation... Python offers very little ability to hide things. This could cause problems in larger programs.

Python philosophy wrt encapsulation is "convention, not coercion". Prefix your own private properties with underscore, and don't intrude into private properties of other modules, unless you have **very** good reason (and be prepared for punishment if caught rwedhanded).

> I don't think python handles large projects as elegantly as C++.

Battle of opinions: Wybiral against [YouTube, IL&M, Google, Thawte and NASA]("http://www.python.org/about/quotes/"). Sorry Wybiral you know this one is coming, right? :twisted:

---

### Post by Wybiral on 2006-12-18
> Wybiral against YouTube, IL&M, Google, Thawte and NASA. Sorry Wybiral you know this one is coming, right?

Just me? I'm not the only C++ programmer that prefers it for large projects over python... And none of the things you mentioned were strictly python, suggesting it wasn't enough for them.

I'm not saying that large projects are *possible* in python, I just think they are easier to manage in C++. And yeah, I think developing in python is faster than C++, but not three months faster in most cases (unless you really suck as C++).

Anyway... I am on your side with this, I think python is a great language, I just prefer C++ for large stuff because it's easier to keep track of and manage (for ME, I am not applying that as a general rule for everyone).

It IS a matter of opinion, and python for small project, C++ for large projects is MY opinion. I understand that you disagree, and that's fine, I see where you are coming from. But I am very comfortable and efficient in C++, so there isn't THAT big of a difference in development time. But yeah... Python is easier for a lot of projects.

---

### Post by DavidBell on 2006-12-19
> **Wybiral said:**
> And yeah, I think developing in python is faster than C++, but not three months faster in most cases (unless you really suck as C++).


and maybe sometimes we are talking about cutting more than 0.2 sec :-)

---

### Post by ifokkema on 2006-12-19
> **maddog39 said:**
> I hate compiled languages for the mere fact that they have data structures, I find them very hard to use and difficult to understand
Huh? Interpreted languages **don't** have data structures?

> **Wybiral said:**
> C++ has it's headers and source, so if you need to find a function without sifting through code, you can check the header.
I'd say you'd need a better IDE or better documentation. :)

> **Wybiral said:**
> Variables must be declared in C/C++ so if you are working with a large project, you can often find the declaration to determine the type... You cannot do this in python, you would have to sift through to find it's origin and that can be very time consuming with large projects.
What about Hungarian Notation? Problem solved. :)

I'm not actually a Python user, but since you mentioned stuff that basically holds for any other popular interpreted dynamically typed language I know of, I felt compelled to post ;)

I totally agree to your points, all I want to say is that these can be circumvented quite easily. I use PHP myself and my IDE (gPHPEdit) gives me a list of my function headers with a push of a button. Furthermore, I use Hungarian Notation so that I know the variables' types and sometimes, scope.

---

### Post by Wybiral on 2006-12-19
Read reply #3 of this thread: [http://www.ubuntuforums.org/showthread.php?t=321465](http://www.ubuntuforums.org/showthread.php?t=321465)

I often do use hungarian notation, but this isn't always going to be an option. When you have to work as a group, you cannot monitor everyone else's coding style, nor can you change the coding style of a project you jump into... Imagine diving into a huge python project where you haven't the slightest clue how the program works.

You WILL eventually figure it out, but chances are it will be very difficult to figure out what everything does. Now... A C++ project on the other hand, is very easy to jump into, even with ambiguous naming conventions and little commenting because C++ is designed with conventions that make it easier to see what is going on.

> I'd say you'd need a better IDE or better documentation.

You don't always have the option of better documentation and even the best IDE can't explain the complicated use of ambiguous variables and classes with operator overload. An IDE isn't going to make that big of a difference unless you have poor programming skills to begin with.

---

### Post by maddog39 on 2006-12-19
> But, I mean well... I'm not trying to bash python, I actually like python a lot, but I don't think it handles large projects as elegantly as C++.
However, my argument to all that stuff you were talking about how python is hard to manage, would be, then how do huge commercial and non-commercial PHP projects. For example, as I stated above, vBulletin has a very high LOC, probably the biggest LOC (lines of code) of any PHP forum on the market (include non-commercial). PHP operates (as far as your code/file structure, not to be confused with coding style) much like python in that it doesnt have datatypes and variables are automatically initiated and the such.

---

### Post by Wybiral on 2006-12-19
Well, then my argument to all of that stuff about LOC, is that LOC doesn't mean much between languages. Have you ever tried ASM? It takes pages of code to do something trivial in either C++ or python. Anyway, these boards using that much php doesn't really justify a large program between C++ and python. It's just too different.

But... I have been coming around to python a lot more lately and I might give a large project a shot soon and see if I can't find some good solutions... But, C++ is easier for large stuf (my opinion).

---

### Post by Tomosaur on 2006-12-20
I think a lot of Ubuntu's interfaces are written in python, simply because it's easy and quick. It also plays nicely with the open-source philosophy. 

Most of linux is written in C, however.

---

### Post by ifokkema on 2006-12-20
> **Wybiral said:**
> I often do use hungarian notation, but this isn't always going to be an option. When you have to work as a group, you cannot monitor everyone else's coding style, nor can you change the coding style of a project you jump into... Imagine diving into a huge python project where you haven't the slightest clue how the program works.
I luckily never had to jump in any project that had as little coding style as you describe. Sounds like a biiig pain in the rear. Well, OK, I had to rewrite my own projects after a while, though :)

> **Wybiral said:**
> Now... A C++ project on the other hand, is very easy to jump into, even with ambiguous naming conventions and little commenting because C++ is designed with conventions that make it easier to see what is going on.
Good point :)

> **maddog39 said:**
> PHP operates (as far as your code/file structure, not to be confused with coding style) much like python in that it doesnt have datatypes and variables are automatically initiated and the such.
?What is your definition of data type? Mine includes bool, int, float, etc... and PHP has all of those.

---

### Post by pmasiar on 2006-12-20
> **Wybiral said:**
> I... When you have to work as a group, you cannot monitor everyone else's coding style, nor can you change the coding style of a project you jump into... 

If you do not have naming convention and code style in a big project, your project manager failed you. Fire him, or run away, screaming. Regardless of language. C++ will NOT help you save mismanegd project.

---

### Post by maddog39 on 2006-12-27
> **ifokkema said:**
> I luckily never had to jump in any project that had as little coding style as you describe. Sounds like a biiig pain in the rear. Well, OK, I had to rewrite my own projects after a while, though :)


Good point :)


?What is your definition of data type? Mine includes bool, int, float, etc... and PHP has all of those.
What I mean by data types is where you have to explicitly set datatypes for everything, e.g. variables, functions, etc. So in PHP you might have:
[PHP]
$x = 72;
$y = -3.41324;
$t = "fadsfasdfsadf";
$b = false;
echo $t."=".$x+y."is".$b;
[/PHP]
and in C++:
```

int main() {
     int x = 72;
     float y = -3.41324;
     string t = "fadsfasdfsadf";
     bool b = false;
     std::cout << t << "=" << x+y << "is" << b << std::endl;
}

```
That obviously doesnt work, because the data types dont match at all. First, your taking, int's and bool's, etc into a string stream (i think that works normally though) and then you have an int adding a float which wont work to my understanding. Where as interpreted languages will automatically convert or mask data types so they are compatible and such. This is a huge pain with explicit data types in most other languages. I dont know a single compiled language that doesnt have these stupid things. :/

---

### Post by Wybiral on 2006-12-27
Yes... But that's why C++ has features like typecasting, overloads, and templates, to provide an abstraction layer for data types. I understand it's complex at first, but it offers a great deal of freedom and readability once you get used to it. Your interpreted languages do all of that for you, but this can be a problem when dealing with user defined data types like classes and structures. C++'s strict type definitions actually make my life a lot easier when writing in C++ because everything can be looked up and the source of functions and data types are very easy to locate, and once located, you know exactly the type you are dealing with. Not to mention the user defined type safety and abstraction abilities...

Cout isn't string based, it accepts different types of data, just like your echo. C++ doesn't actually have "strings" just character arrays... Languages like PHP DO have data types, you just don't have to worry about them... Which is good in some cases, but a pain in others. I'm a control freak when it comes to my programs and I value the amount of control, abstraction, and type safety that C++ offers, especially with large, complex projects.

Data is just sequences of bits... Data types are just collects and rules for bit operators... Try programming in asm (which is about the closest to what the computer understands you can get) and you'll realize that C++ is pretty abstractive about it's data types... Higher up languages are just even more abstractive and ambiguous. In C++, a "string" is literally a STRING or array of characters, ASCII character codes...

That makes perfect sense to me. Bool, int, float, char are just different sized containers to store bitwise values. Type safety for them is just making sure the bit's stay in order and are used correctly, its not hard to do yourself, and I don't know why everyone is so opposed to static typed variables.

---

### Post by ifokkema on 2006-12-28
> **maddog39 said:**
> What I mean by data types is where you have to explicitly set datatypes for everything, e.g. variables, functions, etc. So in PHP you might have:
[PHP]
$x = 72;
$y = -3.41324;
$t = "fadsfasdfsadf";
$b = false;
echo $t."=".$x+y."is".$b;
[/PHP]
and in C++:
```

int main() {
     int x = 72;
     float y = -3.41324;
     string t = "fadsfasdfsadf";
     bool b = false;
     std::cout << t << "=" << x+y << "is" << b << std::endl;
}

```

Ah, you're referring to strong typing vs. dynamic typing.

> **maddog39 said:**
> That obviously doesnt work, because the data types dont match at all. First, your taking, int's and bool's, etc into a string stream (i think that works normally though) and then you have an int adding a float which wont work to my understanding.
Sure it will. The compiler writers were smart enough to allow floats and integers to be added to each other, since they are both numbers. The result will be a float. This sort of type juggling is called coercion. The language silently changes one datatype into another. PHP does that all the time. I understand how this bothers you, but they definiately have a good point as well. Consider you accidentally adding an array to an integer. PHP will actually do that. It will **not** throw an error, but your program is likely to produce false output as your calculation will not return a valid value. This can result in big problems. In C++, your program will not even compile. Thus, you will **always** find these errors before your program even runs.

---

