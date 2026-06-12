---
title: "Objective-C"
date: 2012-04-24
forum: Programming Talk
---

### Post by Drenriza on 2012-04-24
Hey guys.

Is their anyone who can tell me what the difference between C and Objective-C is?
Can C do something Objective-C cant or the other way around?
Also can you use Objective-C on Linux, Windows & OS X. Along with their corresponding Mobile platforms or was it designed for a specific purpose / task?

I have tried and google it a bit but i cant seam to find a straight answer anywhere.

My experience with OOP languages is C# and Java.

Thanks for your time guys.
Kind regards.

---

### Post by schauerlich on 2012-04-24
Objective-C is a superset of C. That is, Objective-C is just the normal C language, plus some other stuff. This other stuff mostly has to do with Object Oriented programming. Objective-C has most of the normal OOP features you'd expect from C# or Java, but it also has some other cool things that those two languages don't. Objective-C was heavily influenced by Smalltalk, one of the original object oriented languages that does things differently than most 'modern' OO languages.

Since Objective-C is a superset of C, by definition Objective-C can do anything C can. After all, any valid C code is also valid Objective-C code. The inverse, however, is not true: C cannot do everything that Objective-C can do (directly). Objective-C has a bunch of OO features that are not included in C, and has a run time to support these features (such as dynamic typing, message forwarding, etc) as well as reference-counting garbage collection. You could implement all of these features yourself in C, or write code that is functionally equivalent, but Objective-C has built in features that C does not.

Objective-C is almost exclusively used for development for OS X and iOS. Objective-C is developed by Apple, and although the code they've contributed to gcc is open source, the runtime that it uses is not. That fact, combined with the fact that apple's fork of gcc is sufficiently diverged to make it difficult to backport their changes, has caused GNU's gcc's Objective-C support to be consistently behind Apple's. The main draw of Objective-C is the Cocoa and Foundation frameworks, which are APIs for developing applications and GUIs. These are all proprietary and owned by Apple, though the [GNUstep](http://www.gnustep.org/) project is trying to implement an open source version of them that could run on Linux. Last I checked, though, they were incomplete, incompatible, and well behind Apple in terms of quality and ease of use.

In short, if you want to use Objective-C, you should do so from OS X, targeting OS X or iOS. Writing Objective-C for Linux is possible, but difficult and not recommended.

---

### Post by Drenriza on 2012-04-24
I see.

So i should learn something that can be used on Windows, OS X and Linux i should learn C++?

From what i have heard C++, can be used to create games and applications (window and console). But what is the limitations of C++ as a OOP language.

Kind regards.

---

### Post by lykeion on 2012-04-24
> **Drenriza said:**
> But what is the limitations of C++ as a OOP language.
It was created by someone from Denmark...

No, kidding aside, it's very hard to give an answer to such a vague question. Some criticism of C++ from Wikipedia [HERE]("https://en.wikipedia.org/wiki/C%2B%2B_%28programming_language%29#Criticism").

> **Drenriza said:**
> So i should learn something that can be used on Windows, OS X and Linux i should learn C++?
Why not go for Java instead? If C++ is your first programming language the learning curve is quite steep.

---

### Post by imachavel on 2012-04-24
don't know much about c except how to compile it:

./configure
"make"
"make install"

if you have a library to access. Otherwise

gcc -o "input file name".c "filename"

where an e.g. is:

gcc -o whatyoulike.c whatyoulike

usually when you write the code you include the compiler reference and the library, for example when I write hello world I reference <stdio> and I believe <init>

Not great with this language yet at all.

c is classless, c++ is with two classes I think. I think gnome gui for linux is written in c and windows gui is written in c++, did I get that right?

as for variable, numbers, base binary, subnet base two binary for octets and cidrs, don't ask me I'm not a mathematician.

---

### Post by schauerlich on 2012-04-24
> **Drenriza said:**
> I see.

So i should learn something that can be used on Windows, OS X and Linux i should learn C++?

From what i have heard C++, can be used to create games and applications (window and console). But what is the limitations of C++ as a OOP language.

Kind regards.

There are any number of languages that can be used on all three platforms. Unless a language is specifically tied to a platform (like C# is to Windows/Windows Phone or Objective-C is to OS X/iOS), it's usually available for all 3. Now, some languages are easier to port programs in than others. Java is one of the easier - the JVM and JDK are designed to be platform agnostic. "Write once, run everywhere" and all that.

C++ can also be used on all three platforms, but it will in general be less portable. I haven't tried to port anything big, so I can't speak to the difficulty, but in general C++ tends to be lower level than the others and therefore might suffer from portability issues. C++ is also (IMO) harder to work with and more complex, so unless you have a specific need, I'd stick with Java. The only real advantage C++ gives you is better speed, but in many cases Java can be just as fast. So it's not really worth the added complexity, especially if you're not very experienced.

---

### Post by imachavel on 2012-04-24
amazing, java can be compiled and ported anywhere. Makes sense c++ can't be ported since it's compiled pretty directly to assembly right?

c# for windows, object-c for mac, proprietary file systems need a proprietary code language right? c# is what that ntfs fragmented garbage is written in? :lolflag:

well, who can argue with a 60 billion dollar OS, it must do something right I still use it

---

### Post by schauerlich on 2012-04-24
> **imachavel said:**
> amazing, java can be compiled and ported anywhere. Makes sense c++ can't be ported since it's compiled pretty directly to assembly right?


Yes. C++ is compiled directly to assembly, but Java is compiled to something called bytecode. When you run a Java program, what you're actually doing is asking a program called the JVM to interpret this bytecode, converting it to assembly on-the-fly and running it. This process is called Just-In-Time (JIT) compilation.

> 
c# for windows, object-c for mac, proprietary file systems need a proprietary code language right? c# is what that ntfs fragmented garbage is written in?

It's not the filesystems that require the C#/Objective-C languages. The file system support is a driver in the kernel, so it is probably written in C in OS X's case and C or C++ in Windows' case (I don't know much about NT). What you need C#/Objective-C for is using the GUI and other programming frameworks that Windows, OS X and iOS offer: .NET, Cocoa and CocoaTouch respectively.

---

