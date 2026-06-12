---
title: "How to convince a CompSci teacher to switch from VS to Code::Blocks?"
date: 2009-04-14
forum: Programming Talk
---

### Post by Jiraiya_sama on 2009-04-14
I'm not sure if this is the right forum for this question, but whatever. I am tired of dealing with Visual Studio in my class. My teacher wants to teach us ANSI C++, but we're learning it on Visual C++? How would you suppose I could convince her to switch?

---

### Post by cabalas on 2009-04-14
You probably won't have all that much luck getting them to swap if the department has some sort of deal with microsoft.  If the don't have any such detail sit down and write out a list of pros and cons, come up with a proposal to give to your lecturer explaining why it would be a good idea.

People tend to take you more seriously if you have something for them to read (and also to take to their superiors) - makes them think you have sat down and seriously thought about it.  Another idea is to try a petition grab some signatures and then take that to the lecturer/department head.

---

### Post by Jiraiya_sama on 2009-04-14
They're giving the students copies of VS temporarily for free (of course we don't get Windows with it) so I suppose they do have a deal, but they are no doubt spending a lot for licenses. I guess I'll try the petition, there are a lot of mac users on my campus and I doubt they like having to load up Windows or go to the school to double check their projects. Problem is they teach C# and VB(though I think they use 2k7 instead of the 2k5 for C++) so they can't totally remove the cost of licensing.

God I hate this :(

---

### Post by samjh on 2009-04-14
[quote=Jiraiya_sama]I'm not sure if this is the right forum for this question, but whatever. I am tired of dealing with Visual Studio in my class. My teacher wants to teach us ANSI C++, but we're learning it on Visual C++? How would you suppose I could convince her to switch?[/quote]

What's wrong with Visual C++?  Although I'm not a fan of their CLI extensions, Visual C++ 7.1 onward have quite good standards compliance if you ignore the CLI extensions, at least comparable to g++ and ICC.  So as far as learning ANSI/ISO C++ is concerned, Visual C++ is not a detractor.

A better argument for you would be on the basis of cost.  Code::Blocks and MinGW cost nothing.  Visual C++ and the Visual Studio IDE would cost at least several hundred dollars per installation.  And if your college or university is not a member of the MSDN Academic Alliance program, then the cost of obtaining VC++ and VS would be prohibitively expensive for most students, thereby severely limiting their ability to learn or practice at home.

[EDIT]

I just read your latest post.  It seems you won't be able to escape VC++ then.  Not to worry, it won't harm you.  What do you hate about it so much?

On second thoughts, petitioning for Code::Blocks and MinGW might still be worthwhile.

---

### Post by Jiraiya_sama on 2009-04-14
> What do you hate about it so much?

Some of MS's non-ANSI functions have crept into my tutor's material. Things like fflush(stdin).

---

### Post by samjh on 2009-04-14
> **Jiraiya_sama said:**
> Some of MS's non-ANSI functions have crept into my tutor's material. Things like fflush(stdin).

Well, that's not exactly non-standard.

fflush is part of ANSI C.  It's *bad practice* to use fflush to clear input streams as its behaviour is undefined.  Despite that, fflush(stdin) works in g++ too, so switching to g++ won't solve that particular gripe. ;)

---

### Post by Jiraiya_sama on 2009-04-14
> **samjh said:**
> Well, that's not exactly non-standard.

fflush is part of ANSI C.  It's *bad practice* to use fflush to clear input streams as its behaviour is undefined.  Despite that, fflush(stdin) works in g++ too, so switching to g++ won't solve that particular gripe. ;)

If it's supposed clear stdin, it doesn't work. cin.ignore(1024,'\n') will clear (most) bad input from stdin, but fflush(stdin) didn't do anything.

---

### Post by slavik on 2009-04-14
What exactl version of VS is being used? You can always argue the point of availability/support.

---

### Post by Jiraiya_sama on 2009-04-14
2005 is the version we use for C++. I think the VB/C# people use 2007.

---

### Post by Lux Perpetua on 2009-04-15
> **Jiraiya_sama said:**
> I'm not sure if this is the right forum for this question, but whatever. I am tired of dealing with Visual Studio in my class. My teacher wants to teach us ANSI C++, but we're learning it on Visual C++? How would you suppose I could convince her to switch?If you are in fact writing ANSI C++ code, then the IDE or compiler you use should be inconsequential as long as it supports the standard. 

Regarding fflush(stdin), (1) you should definitely point out to your teacher that this is nonportable code, and (2) WTF? is this a C++ class? Why are you using C functions?

I would actually recommend that you **not use an IDE at all** and compile all your projects from the command line while you are learning the language. Once you feel comfortable with that, then pick up an IDE if you feel like it. I say this because it's very important to keep the IDE and the compiler itself separate in your mind. If you learn to write code without an IDE, then you'll be in a good position to start using any IDE. On the other hand, if you always had the IDE, you might have trouble switching it for something else or getting rid of it. 

On other programming forums, I often see threads with titles like "Code crashes on Dev-C++" or similar. Of course, their bug has nothing to do with Dev-C++; it's invariably a general C++ issue, but they don't know where C++ ends and their IDE begins.

---

### Post by Jiraiya_sama on 2009-04-15
> **Lux Perpetua said:**
> If you are in fact writing ANSI C++ code, then the IDE or compiler you use should be inconsequential as long as it supports the standard. 

Regarding fflush(stdin), (1) you should definitely point out to your teacher that this is nonportable code, and (2) WTF? is this a C++ class? Why are you using C functions?

I would actually recommend that you **not use an IDE at all** and compile all your projects from the command line while you are learning the language. Once you feel comfortable with that, then pick up an IDE if you feel like it. I say this because it's very important to keep the IDE and the compiler itself separate in your mind. If you learn to write code without an IDE, then you'll be in a good position to start using any IDE. On the other hand, if you always had the IDE, you might have trouble switching it for something else or getting rid of it. 

On other programming forums, I often see threads with titles like "Code crashes on Dev-C++" or similar. Of course, their bug has nothing to do with Dev-C++; it's invariably a general C++ issue, but they don't know where C++ ends and their IDE begins.

I have been using vim/g++/make to write and compile my code for class. Unfortunately, my teacher forces us to turn our code in wrapped in a zip file with the appropriate VS project files. I haven't had problems with VSC++ and my code, other than the obnoxious "strncpy is not safe, please use strcpy_s" errors. The biggest problem I have with it is that I **must** have a copy of Windows or run down to the library in order to get the VS project files added to my program files.

I have actually thought about testing exactly which of these files VS needs to load up a project, and if it's the human readable-ish one, making a parser which will generate the file for me on linux.

---

### Post by cabalas on 2009-04-15
> **Jiraiya_sama said:**
> I have been using vim/g++/make to write and compile my code for class. Unfortunately, my teacher forces us to turn our code in wrapped in a zip file with the appropriate VS project files. I haven't had problems with VSC++ and my code, other than the obnoxious "strncpy is not safe, please use strcpy_s" errors. The biggest problem I have with it is that I **must** have a copy of Windows or run down to the library in order to get the VS project files added to my program files.

I have actually thought about testing exactly which of these files VS needs to load up a project, and if it's the human readable-ish one, making a parser which will generate the file for me on linux.

Can't MonoDevelop produce legitimate Visual Studio project files? Or is that feature only in MonoDevelop2.0?

---

### Post by samjh on 2009-04-15
> **Jiraiya_sama said:**
> If it's supposed clear stdin, it doesn't work. cin.ignore(1024,'\n') will clear (most) bad input from stdin, but fflush(stdin) didn't do anything.Well, its behaviour is undefined if it's used as fflush(stdin), according to the standard.  It's just that popular compilers happen to support the usage.

I'll take your word that it doesn't work on g++ though.

> **Jiraiya_sama said:**
> I have been using vim/g++/make to write and compile my code for class. Unfortunately, my teacher forces us to turn our code in wrapped in a zip file with the appropriate VS project files. I haven't had problems with VSC++ and my code, other than the obnoxious "strncpy is not safe, please use strcpy_s" errors. The biggest problem I have with it is that I **must** have a copy of Windows or run down to the library in order to get the VS project files added to my program files.

I have actually thought about testing exactly which of these files VS needs to load up a project, and if it's the human readable-ish one, making a parser which will generate the file for me on linux.

Try Monodevelop.  It supports Visual Studio projects and MS Build files.

Otherwise, ask your teacher if it's OK to just hand in the source files, and say you don't own Windows to run VS.

If there is no way around it, just grin and bear it.  Visual Studio is very widely used, so it doesn't hurt to be familiar with it.

Judging by the sounds of it, if your teacher is teaching you fflush(stdin), then standard C++ isn't one of their objectives - not to mention the use of C functions in C++, so forget about "standard" C++.

---

### Post by sloggerkhan on 2009-04-15
> **Jiraiya_sama said:**
> They're giving the students copies of VS temporarily for free (of course we don't get Windows with it) so I suppose they do have a deal, but they are no doubt spending a lot for licenses. I guess I'll try the petition, there are a lot of mac users on my campus and I doubt they like having to load up Windows or go to the school to double check their projects. Problem is they teach C# and VB(though I think they use 2k7 instead of the 2k5 for C++) so they can't totally remove the cost of licensing.

God I hate this :(

Ummm.... what degree are you getting?
I'm pretty sure any curriculum based particularly on MS coding environments and technologies isn't in line with ACM standards for computer science education...

---

### Post by Jiraiya_sama on 2009-04-15
I haven't tried anything mono so I'll try out monodevelop. Oh, and is there a problem with mixing C++ and C functions? I do it myself sometimes.

> 
Ummm.... what degree are you getting?
I'm pretty sure any curriculum based particularly on MS coding environments and technologies isn't in line with ACM standards for computer science education...

Community college transferring to a 4yr for my bachelors. We also learn java if that means anything.

---

### Post by samjh on 2009-04-15
> **Jiraiya_sama said:**
> Oh, and is there a problem with mixing C++ and C functions? I do it myself sometimes.

For trivial programs, no.

For substantial programs, potentially yes.  You have to know what you are doing.  C code can be behave in mysterious ways when compiled as or with C++.

These links explain the nuances better than I could:
[Compatibility between C and C++]("http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B")
[How to mix C and C++]("http://yosefk.com/c++fqa/mixing.html")
[Mixing C and C++ code in the same program]("http://developers.sun.com/solaris/articles/mixing.html")
[Stroustrup FAQ: C and C++]("http://www.research.att.com/~bs/bs_faq.html#C")
[Stroustrup: C++ Style and Techniques FAQ]("http://www.research.att.com/~bs/bs_faq2.html")

---

### Post by crush304 on 2009-04-15
> **slavik said:**
> What exactl version of VS is being used? You can always argue the point of availability/support.

there are free express versions of visual studio for 2005 and 2008. I haven't used the c++ versions much but the c# versions are very good and generally not lacking in features despite the "express" label

---

### Post by dribeas on 2009-04-15
If the cost of licencing is already paid by the university, there is no sound reason not to use VS. It has a great debugger, and besides a couple of quirks with intellisense its a fine solution. The debugger (I must insist) is great for learning when you hit a hard problem. Linux debuggers are way behind. 

Intellisense is also more precise (even if heavier) than the rest of the solutions I have tried (I have not extensively used Xcode, but I have tried KDevelop, Eclipse CDT3/4/5, Netbeans for C++... I mostly use vim and I am now trying CDT6.

Now, if you are using standard c++, you can consider using cmake (simple project configurations are really simple) as it will generate VS solutions for you (as well as makefiles, kdevelop, eclipse cdt, code::blocks, xcode projects...) The syntax is rather simple:

```

#CMakeLists.txt
PROJECT( Name_of_solution ) 

INCLUDE_DIRECTORIES( /my/include/dir1 /my/include/dir2 )
LINK_DIRECTORIES( /my/library/dir1 )

ADD_LIBRARY( name_of_library SHARED 
    file1.cpp
    file2.cpp
)
ADD_EXECUTABLE( name_of_exe
    file3.cpp
    file3.cpp
)
TARGET_LINK_LIBRARIES( name_of_exe
    name_of_library
    another_library
)

```

Now, run cmake (or cmake -G <Generator> -check the name of the generator for VS, must be on a windows cmake) and you will end up with a solution.

---

### Post by doorman on 2009-04-15
> **Lux Perpetua said:**
> I would actually recommend that you **not use an IDE at all** and compile all your projects from the command line while you are learning the language. Once you feel comfortable with that, then pick up an IDE if you feel like it. I say this because it's very important to keep the IDE and the compiler itself separate in your mind. If you learn to write code without an IDE, then you'll be in a good position to start using any IDE. On the other hand, if you always had the IDE, you might have trouble switching it for something else or getting rid of it. 

On other programming forums, I often see threads with titles like "Code crashes on Dev-C++" or similar. Of course, their bug has nothing to do with Dev-C++; it's invariably a general C++ issue, but they don't know where C++ ends and their IDE begins.

Qouted (again) for truth! Especially in the case of VS. What are the actions of an aspiring developer in such a tool:
1) open up the IDE
2) new project (I bet this step is the most obscure one - all those projects, every single one of them meaning something else - thoughts like "what the heck are those???" they are there for a good reason - a very good one, I might add)
3) type in some code the teacher told us to (or even worst, paste it from a lecture)
4) Run

and magically that pasted code actually does something. What the hell happened between steps 3 and 4? No one knows...

I'm not writing this post from a "M$ hater" point of view, just trying to show the level of comprehension needed to become a "developer".

As far as the original thread question is concerned, to program in any IDE at all is a bad idea to start with - people who know how to compile their oen code can later on code in any given IDE, whereas people who learn to use only one IDE, chances are they'll have a very had time adjusting to another one (not to mention the possibility of compiling code themselves)

---

### Post by slavik on 2009-04-15
that's why I asked ;)

Another point you can argue is that VS is not available on "your" platform (your == Linux) and that you want to use something gcc based, but a compiler choice is a department wide decision, so it is most likely not just your lecturer.

Best thing to do would be to gather 10-20 Linux geeks, start a club and complain to the chair ... also complain that you don't get enough Unix/Linux exposure (if you don't) ...

---

### Post by ddrichardson on 2009-04-15
> **Jiraiya_sama said:**
> They're giving the students copies of VS temporarily for free (of course we don't get Windows with it) so I suppose they do have a deal, but they are no doubt spending a lot for licenses. I guess I'll try the petition, there are a lot of mac users on my campus and I doubt they like having to load up Windows or go to the school to double check their projects. Problem is they teach C# and VB(though I think they use 2k7 instead of the 2k5 for C++) so they can't totally remove the cost of licensing.

God I hate this :(
Microsoft has been running the [Dreamspark]("https://www.dreamspark.com/default.aspx") promotion for a while now, where any student can get their software free, providing they can prove they're a student. No saying this is entirely altruistic - makes a lot of sense for MS creating a generation who like their tools.

---

### Post by Jiraiya_sama on 2009-04-15
> **doorman said:**
> Qouted (again) for truth! Especially in the case of VS. What are the actions of an aspiring developer in such a tool:
1) open up the IDE
2) new project (I bet this step is the most obscure one - all those projects, every single one of them meaning something else - thoughts like "what the heck are those???" they are there for a good reason - a very good one, I might add)
3) type in some code the teacher told us to (or even worst, paste it from a lecture)
4) Run

and magically that pasted code actually does something. What the hell happened between steps 3 and 4? No one knows...

As far as the original thread question is concerned, to program in any IDE at all is a bad idea to start with - people who know how to compile their oen code can later on code in any given IDE, whereas people who learn to use only one IDE, chances are they'll have a very had time adjusting to another one (not to mention the possibility of compiling code themselves)

I doubt we would switch to learning to compile w/o an IDE. On my last test, getting your code to compile and do what it's supposed to do netted you extra credit. I was one of the rare few that did it.

> that's why I asked 

Another point you can argue is that VS is not available on "your" platform (your == Linux) and that you want to use something gcc based, but a compiler choice is a department wide decision, so it is most likely not just your lecturer.

Best thing to do would be to gather 10-20 Linux geeks, start a club and complain to the chair ... also complain that you don't get enough Unix/Linux exposure (if you don't) ... 

I can try and get my linux professor to help me push this. Most likely what I'll end up doing is pushing for my C++ professor (did I mention, she's the only one, and I'm in the only C++ class on campus?) to distribute material explaining how to use monodevelop to do class assignments and the pitfalls associated (must use #include <string>, etc.).

---

### Post by slavik on 2009-04-15
> **Jiraiya_sama said:**
> I doubt we would switch to learning to compile w/o an IDE. On my last test, getting your code to compile and do what it's supposed to do netted you extra credit. I was one of the rare few that did it.

 

I can try and get my linux professor to help me push this. Most likely what I'll end up doing is pushing for my C++ professor (did I mention, she's the only one, and I'm in the only C++ class on campus?) to distribute material explaining how to use monodevelop to do class assignments and the pitfalls associated (must use #include <string>, etc.).
what's wrong with #include <string> in C++? that's the string library, no?

---

### Post by Jiraiya_sama on 2009-04-15
g++ doesn't require #include <string> to use strings by default, but VSC++ does.

---

### Post by slavik on 2009-04-16
hmm, maybe there is some magic going on, but I am pretty sure that you have to #include <string> in order to use the class.

---

### Post by Jiraiya_sama on 2009-04-16
Well, here's the code I just compiled:

```
#include <iostream>

using namespace std;

int main()
{
  string s = "hello world";

  cout << s.substr(1,4) << endl;

  return 0;
}
```

I've tried using -ansi, -std=c++98, -pedantic, and -Wall. No error ever. In Visual C++ if you even tried to compile this code it would error out badly. 

In fact it says something about ostream not defining any operator being able to handle types of std::basic_string and there being no conversion for it.

I wonder if strings being accessible w/o #include <string> is part of the 98 ansi standard? It seems VSC++ knows the type without the include.

---

### Post by slavik on 2009-04-16
hmm, that might be because string library defining operator<<() for strings ... although I can't say I've researched this to any length.

---

### Post by Jiraiya_sama on 2009-04-16
> **slavik said:**
> hmm, that might be because string library defining operator<<() for strings ... although I can't say I've researched this to any length.

I've looked into it a bit, and Visual studio does put the overload for operator<< for strings in string.h.

---

### Post by samjh on 2009-04-16
> **Jiraiya_sama said:**
> I wonder if strings being accessible w/o #include <string> is part of the 98 ansi standard? It seems VSC++ knows the type without the include.

Firstly, you contract yourself.  You said in the other posts that g++ allows the use of strings without #include <string>, but VC++ throws errors.

To follow the standard strictly, you should #include <string> in the source file where C++ strings are used.  The standard doesn't prescribe whether or not the header needs to be included, but it does state that the header defines the template classes, traits, functions, and operators for C++ strings.  The general rule of thumb when dealing with standards or regulations is to implement the standard without ambiguity, and in this case, that would include requiring the use of #include <string>.

Having said that, since the standard says that any header can include any other system header, it's probably that for g++, the <iostream> header includes <string>.  But that's obviously not something you can rely on for all compilers.

For safety and stylistic reasons, I say you should always #include <string> if the source file uses C++ strings.

It seems you are very focused on the use of standard C++.  You should know that there is no C++ compiler which complies strictly with the standard (currently ISO/IEC 14882:1998[noparse])[/noparse].  The three most popular compilers (g++, ICC, VC++) implement the standard very closely, but all of them have some "enhancements" for convenience and convention.

---

