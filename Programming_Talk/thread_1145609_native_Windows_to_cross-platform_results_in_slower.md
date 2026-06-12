---
title: "native Windows to cross-platform results in slower app?"
date: 2009-05-01
forum: Programming Talk
---

### Post by deleyd on 2009-05-01
We're going to rewrite the kernel, currently written in Delphi, of our text editor program, to make it unicode compatible, and we're considering the possibility of making it run on Linux too. But we're not sure if that's a good idea. Some people suggest the program will run significantly slower if we do:

> I've seen other projects switch from native Windows to a cross-platform library, resulting in a bigger, slower app. For instance the new Perforce GUI client. They've switched from native Windows to, I think, QT. And their new app is a nightmare to work with, partly because of the poorer performance, partly because it doesn't behave as one would expect from a Windows app. Or compare the .NET-based Delphi IDE's with the latest 'normal' version 7. Not surprising that a lot of developers stick with version 7.

There's also discussion if we should write the kernel in **Java** so it will be cross platform:

anti-Java comments:
> ...the few java apps I have (or have used) are significantly slower than their native counterparts and can have other issues (of course, an app written in any lang can have issues, but I think the issues are in part from the JRE, which I've kept up-to-date).

> I have similar experience with Java apps. They're exceptionally slow and ugly.

> I've used a free editor for awhile (jEdit, I think). The launching performance (in part, because it had to load java) was really bad. I've also had garbage collection (memory) and redraw issues in a Java SQL app. Overall, I haven't been that impressed with desktop apps written in java.


Pro Java Comments: 
> At the risk of being branded a heretic, Java is the ultimate cross-platform choice. And before people trot out the usual old saw about performance, you need to check out some quality Java applications: Eclipse, IDEA, Borland JBuilder's IDE from years ago, etc. Even jEdit is pretty fast if not a bit klunky. Memory intensive, sure, but what isn't (.NET certainly is) and memory is cheap and plentiful these days. Writing fast Java is certainly not impossible, and you'll have cross-platform capability out of the box. Put it this way: I was an ASM/C/C++ snob for 20 years. I was dragged into the Java world virtually kicking and screaming, only to fall in love with it. The only C/C++ I write these days is by strict necessity (drivers, JNI wrappers, etc.). Java is always my first choice now unless there is a compelling reason otherwise, which is a rare occurrence. In fact we're now writing Java apps to interface with industrial control systems, historically an exclusive realm of C/C++. And I've taken my Java GUI's that were developed entirely on one platform, dropped them on another (like Linux), and they Just Work(tm). Realistically there might be a small amount of platform-specific tweaking required, but generally nothing to speaking of.[SIZE="1"](We've also looked into **QT** and **wxWidgets**.)[/SIZE]

So I'm looking for further comments & suggestions on creating cross-platform applications.

---

### Post by Claus7 on 2009-05-01
Hello,

I think that it depends on how well you know to handle the tools you will use so as to create the project you want. Could we know the name of the project? And which will be the main and special characteristics of it?

Regards!

---

### Post by lisati on 2009-05-01
I'd go for making native binary executables in preference to something interpreted, if possible. The GUI and OS specific stuff can easily be handled by having their own routines, called in as necessary.

---

### Post by doas777 on 2009-05-01
ok, you have two phenoma at work here. one is interpretation vs compilation, and the other open vs closed.

basically, yes, java and python are slow. are they too slow? maybe so maybe not. .net on windows is also slower than win32 binary code, but not as bad as either of the others.

ultimatly, the reality is that the java dream of "write once, run everywhere" is more like "write once, debug everywhere".  
I recently adjusted a java app for linux use, and it isn't really all that differant, but you do have to query the environment to get things like the current path, path seperators, and environment vars. 

suprisingly enough, the biggest problem i had, was that when java on windows reads a csv file and parses the strings, it does not quote the values, whereas java on ubuntu adds quotes as characters within the string, so if I inspect the variable DebugMode, it comes out ""True"" rather than "True". weird wot?

good luck

---

### Post by soltanis on 2009-05-01
Let me guess, those people use Windows.

It is not the virtue of making your *application* cross-platform that seems to be the stickler, but rather, the *library* you will use to make that happen. These criticisms seemed to be largely aimed at things like Qt.

So first of all, what is your application written in? I'm going to assume C++, since Qt came up; if that's so, you have several options available to you:

I. Rewrite your GUI code using a cross-platform library of your choosing. Some are better than others, but most all of them will end up in slower code for a very good reason - OS-agnostic calls are being translated into OS-specific calls, and no matter what you use, that is going to slow things down. Whether or not anyone actually *notices* that really depends on the performance of their computer, how fast your application was to begin with, and how well the library was written.

II. Rewrite your code in an interpreted language, or at least part of it. This will definitely make your application slower (probably moreso than 1 will) but will give it the blessings of compatibility with a (usually, anyway) wide range of platforms, not just Linux and Windows but also Mac and Solaris and AIX and...etc. Note that when I say "interpreted language", I'm talking mostly about python, perl, or maybe ruby.

III. Rewrite your code with Java/.NET frameworks. I don't really like these myself, but to be fair to Java, it is not as slow as it used to be. More likely the performance problems people are complaining about is due to poorly written code, not necessarily the inability of the JIT Compiler to produce efficient code -- which by the way, they usually do.

IV. Rewrite your GUI, using your own OS-agnostic library that you wrote yourself. This library would ideally present the same semantics to the rest of your application, under the hood translating those calls into OS-specific calls. Especially since you would be writing this yourself, and since all you really want is GUI (whereas Qt provides a ton of other things), and since it is tailored to your application, this will result in the lowest performance hit (unless you really mess it up, I doubt anyone will notice). This is, by the way, the most work.

EDIT.

Reading helps; Delphi isn't renowned for being the fastest language anyway, so if you are considering porting to something a little more super-assembler like, C or C++ will help you out if speed is your concern.

Not to mention make you more cross-platform - almost every modern computer and its mother has a C compiler.

---

