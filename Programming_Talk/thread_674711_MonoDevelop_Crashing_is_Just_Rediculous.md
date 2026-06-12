---
title: "MonoDevelop Crashing is Just Rediculous"
date: 2008-01-22
forum: Programming Talk
---

### Post by Thund3rstruck on 2008-01-22
Ok, I'm running Gutsy with the repo monodevelop 0.14. 

Basically no matter what I do the thing crashes and looses all my work. Even the simplest Gtk# GUI with a single menu bar exits for no apparent reason and discards everything when I try to either save or run the app. 

Is this normal? Is there a stable C# IDE on Ubuntu? I'd think IDE's would be mission critical packages and therefor tested exhaustively prior to deployment??

Any Ideas?

---

### Post by Tuna-Fish on 2008-01-22
monodevelop is in 0.18 right now, perhaps you should try a newer version?

---

### Post by LaRoza on 2008-01-22
> **Thund3rstruck said:**
> Ok, I'm running Gutsy with the repo monodevelop 0.14. 

Basically no matter what I do the thing crashes and looses all my work. Even the simplest Gtk# GUI with a single menu bar exits for no apparent reason and discards everything when I try to either save or run the app. 

Is this normal? Is there a stable C# IDE on Ubuntu? I'd think IDE's would be mission critical packages and therefor tested exhaustively prior to deployment??

Any Ideas?

I have never used Mondevelop, so I can't give any help specifically.

I have heard good things about Monodevelop, and this problem doesn't seem to be universal.

Trying a newer version might help, or reinstalling.

---

### Post by Thund3rstruck on 2008-01-22
If the stable release cannot run without crashing then I'm certain the beta 3 (0.18.1) is not going to be any better.

I just tried the 0.17 release and yea it crashes with any Gtk# work. I guess the next try is 0.18

---

### Post by LaRoza on 2008-01-22
> **Thund3rstruck said:**
> If the stable release cannot run without crashing then I'm certain the beta 3 (0.18.1) is not going to be any better.


You'd be surprised, Opera 9.50b is much better than the "stable" version. (IMO)

---

### Post by loell on 2008-01-22
yes it's crashing , in my case when you're designing the UI through the IDE :(

---

### Post by Thund3rstruck on 2008-01-22
> **loell said:**
> yes it's crashing , in my case when you're designing the UI through the IDE :(

Yea, I can't explain how excited I was when I saw that there was a GUI designer! C# has been my professional language since it's arrival in 2002 and it seemed too good to be true!

No luck.... In any event I guess I'll keep an eye out for a stable version in the future. One of these years Linux will have finally arrived and we'll have reliable cross platform development tools!

---

### Post by LaRoza on 2008-01-22
> **Thund3rstruck said:**
> Y
One of these years Linux will have finally arrived and we'll have reliable cross platform development tools!

Python and its tools are reliable and very cross platform. C, Java, Ruby, C++, Perl, and others are just as good.

C# is cross platform, but (not to start another debate) it has its roots in Windows. The sticky on Programmers New to Linux has links to the discussions on it.

In my opinion, C# is not the best language for reliable cross platform development. Python and Java are, among others.

Python can also be used with .NET and other Window specific things, with some of its libraries and with IronPython. It can be used with Java with Jython, and can be compiled to binary executables, and can use modules written in C. (Interestingly, IronPython is written in C#)

---

### Post by Thund3rstruck on 2008-01-22
There's no debate that most of these languages are cross platform but there's just no substitute for the fact that the .NET framework is sitting on every windows machine out of the box. This means that applications can be targeted towards even the most primitive computer users and can be developed and deployed exceptionally fast. 

If I were to target Python, Perl, or Java then there would have to be a lengthy tutorial on how to install these interpretors and most people walk away at that point. (This statement may be my own ignorance in these areas because surely most of these platforms are capable of compiling to .exe files??)

In any event, I'm a younger programmer so I prefer OOP C# over C any day of the week and my professional skill (and paycheck) depends ,at the moment, on developing for proprietary platforms. It would just be great to leverage my skill in that area on OSS during my spare time.

---

### Post by LaRoza on 2008-01-22
> **Thund3rstruck said:**
> There's no debate that most of these languages are cross platform but there's just no substitute for the fact that the .NET framework is sitting on every windows machine out of the box. This means that applications can be targeted towards even the most primitive computer users and can be developed and deployed exceptionally fast. 

If I were to target Python, Perl, or Java then there would have to be a lengthy tutorial on how to install these interpretors and most people walk away at that point. (This statement may be my own ignorance in these areas because surely most of these platforms are capable of compiling to .exe files??)

In any event, I'm a younger programmer so I prefer OOP C# over C any day of the week and my professional skill (and paycheck) depends ,at the moment, on developing for proprietary platforms. It would just be great to leverage my skill in that area on OSS during my spare time.

Yes, exactly, .NET is Windows, not cross platform. C# is mostly used with .NET thus is not the ideal cross platform tool. 

No, actually, for Windows, the installer (the ActivePython installer) is just a quick installer that requires no thought. In fact, Python is preinstalled on HP and Compaq computers. Python also has .NET available with IronPython (which is written in C#)

Perl and Java are also one click installers, and Java is typically installed on Windows anyway.

I am a younger programmer also, 19. C can be used in an OO way, OO is a way of programming. Python is OO by design also (Perl added it and Ruby is also OO from the start).

Some say that C# is just a copy of Java (read up on Java, which came before C#, it will be very familiar)

C# is a great language (from what I hear) and deserving of use. However, no programmer is limited to a single language... You make it sound like you can learn only one. Learning different programming paradigms and languages make you a better programmer.

As for .exe's, that is the Windows extension for PE files. Python scripts usually run perfectly on Windows, Linux and Macs with no alteration. Python can be compiled to bye code for efficiency, but that is equally cross platform also.

If I wrote a program in Python and a newbie Windows user wanted to use it, I'd give the link for the interpreter installer (it is in my wiki, in case you want it), and tell them to double click it, and say "ok". Then, to run my program, they double click it. Not hard.

---

### Post by clasificado on 2008-01-22
> If the stable release cannot run without crashing then I'm certain the beta 3 (0.18.1) is not going to be any better.
The version in ubuntu repositories is not stable either :KS

The whole project is not in a release candidate situation. If you dont like betas, you should wait or pay for a finished commercial linux c# product

Clasificado

---

### Post by skeeterbug on 2008-01-22
> **Thund3rstruck said:**
> Yea, I can't explain how excited I was when I saw that there was a GUI designer! C# has been my professional language since it's arrival in 2002 and it seemed too good to be true!

No luck.... In any event I guess I'll keep an eye out for a stable version in the future. One of these years Linux will have finally arrived and we'll have reliable cross platform development tools!

Perhaps you should join their development mailing list and let them know about the problem. I am sure there is a logging feature (or one that can be enabled), so they can see what is going on. Maybe there is a fix coming up, or maybe they don't have enough information on the problem? It won't take much time, and you can make the product that much better.

---

### Post by DuneSoldier on 2008-01-22
You can also use Glade to do GUI design for C#.

---

### Post by ihavenoname on 2008-02-25
Same issue confirmed. If you have found a solution please post. 

  People, please don't judge the language that other people choose to use, nobody is forcing mono upon you, and the fact that sitting on everyones Ubuntu (out of box) is mono, means that anything made using c#/mono should work on both windows and Linux computers as well so it's not really a problem.  So if  a developer has chosen this method of cross platform programing so be it. In any case this is not the thread for this. This is about getting support for an application. Thanks.

---

### Post by graabein on 2008-02-25
Even though the newer version is beta it may have cleaned up alot of the bugs in an older version of the software... At least that's how I do it.

---

### Post by ihavenoname on 2008-02-25
> **graabein said:**
> Even though the newer version is beta it may have cleaned up alot of the bugs in an older version of the software... At least that's how I do it.

Actually I just found the issue after playing around with it a bit. I installed "stetic", (from the repos) and uninstalling that package seems to have fixed the issue. Note, stetic is supposed to be a gtk# glade like designer, however monodevelop's interface doesn't seem to depend on this package being installed in order to work. If anyone out there could confirm this it would be nice.

---

