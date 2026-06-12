---
title: "using the mono C# compiler"
date: 2007-12-20
forum: Packaging and Compiling Programs
---

### Post by zivxx on 2007-12-20
hey guys i installed the mono c# compiler for ubuntu...but how do i use it?i used to work with visual studio until now, so will anyone explain to me how to use the mono compiler?

---

### Post by emperon on 2007-12-21
Hello. You can work with mono's C# compiler exactly the same way you work with C# compiler on windows. Note that compilers and IDE's are different things. So although you were using Visual Studio, that internally uses C# compiler which is csc.exe

Coming back to mono from the command line you can do this:

gmcs Test.cs

which will produce Test.exe  and then you can run either with mono Test.exe or ./Test.exe

for switches type man mcs 

gmcs and mcs are two compilers of mono which are basically the same thing. The difference is gmcs supports generics so it is .net 2.0 compatible where as mcs is not


finally C# 3.0 support is also available with gmcs (with an extra switch I don't remember atm)

If you want to use an IDE you can use MonoDevelop which is nice . Not as full featured as VS but you can do serious development on it.

At the time being latest mono is 1.2.6 and latest MD is 0.18. Unfortunately Ubuntu lags behind these versions and it might be painful to install latest versions

---

### Post by zivxx on 2007-12-21
i don't think i get it, first, what are IDEs? im pretty noob both to linux and both to compiling...and second i think i should ask to be more spesific, is there a way to work with mono like with Visual Studio, i mean that can mono be a graphical program that you can both write in it then build the project?

---

### Post by vek on 2007-12-22
> **zivxx said:**
> i don't think i get it, first, what are IDEs? im pretty noob both to linux and both to compiling...and second i think i should ask to be more spesific, is there a way to work with mono like with Visual Studio, i mean that can mono be a graphical program that you can both write in it then build the project?

Visual Studio is an IDE (An Integrated Debugging Environment).  It allows you to click to run things, build things, drag buttons around, make forms, etc.  If you want to do that kind of thing, try installing SharpDevelop (use add/remove), it is very similar. 

Only problem, and its a HUGE problem, is that there's no way to graphically debug mono apps in linux.  Yes, there are ways to muddle around with textmode debuggers, but it really feels like banging sticks together to light a fire when everyone else is using a lighter.

I'd go off on a rant here how ridiculous it is that debuggers are not the #1 priority for the mono team, but hey, whatever.

---

### Post by emperon on 2007-12-23
Vek you are right. There are summer of code projects for graphical debuggers also. The problem is, mono's core is changing (and improving) so fast, that causes debuggers to break. I think they first want to stabilize the core. It is a priority goal for 2008

---

### Post by vek on 2007-12-28
> **emperon said:**
> Vek you are right. There are summer of code projects for graphical debuggers also. The problem is, mono's core is changing (and improving) so fast, that causes debuggers to break. I think they first want to stabilize the core. It is a priority goal for 2008

I was under this impression too.  Its just a bit frustrating and a pity.  I do a heck of a lot of application dev, and the lack of a real, smart debugger means I'd be insane to even consider mono for a serious project.  I hope they get it working soon.  Until there's a debugger, I don't even consider it pre-alpha.

---

### Post by rekahsoft on 2008-01-18
> **vek said:**
> Visual Studio is an IDE (An Integrated Debugging Environment).  It allows you to click to run things, build things, drag buttons around, make forms, etc.  If you want to do that kind of thing, try installing SharpDevelop (use add/remove), it is very similar. 

Only problem, and its a HUGE problem, is that there's no way to graphically debug mono apps in linux.  Yes, there are ways to muddle around with textmode debuggers, but it really feels like banging sticks together to light a fire when everyone else is using a lighter.

I'd go off on a rant here how ridiculous it is that debuggers are not the #1 priority for the mono team, but hey, whatever.

Just a Note: "IDE" Stands for "Integrated Development Environment" NOT "Integrated Debugging Envinronment"

[http://en.wikipedia.org/wiki/Integrated_development_environment](http://en.wikipedia.org/wiki/Integrated_development_environment)

---

### Post by Shin_Gouki2501 on 2008-01-18
krkr
just same thing i was about to say its not important buts its word ^^
If u were on linux and for coding using an IDE i would suggest ..maybe eclipse?!

---

### Post by emperon on 2008-01-18
> **Shin_Gouki2501 said:**
> krkr
just same thing i was about to say its not important buts its word ^^
If u were on linux and for coding using an IDE i would suggest ..maybe eclipse?!

Absolutely Monodevelop. With 0.18 version it became quite nice. But not available on repos. you have to compile it yourself (which is very difficult).

---

### Post by JackBak on 2008-01-18
@Emperon

Any version of Monodevelop including 0.18 for me is unusable. I did not have time to chase down all the interlocking dependencies in Ubuntu 7.10 and build from src so I grabbed an unused machine and put Suse 10.3 along with MD 0.18 on it. Yes it is nice but to get real work done is next to impossible. Crashes consistantly and if not that then Suse 10.3 spawns tasks randomly.

Right now I am using glade3, emacs and the CLI to compile on 7.10. This is virtually no different than if I wrote the app in C with glade2 C code but then I would have fits trying to get it to work correctly in Win box.

I wish the folks over at Novell would concentrate a little bit on the IDE's stability.

---

### Post by emperon on 2008-01-19
> **JackBak said:**
> @Emperon

Any version of Monodevelop including 0.18 for me is unusable. I did not have time to chase down all the interlocking dependencies in Ubuntu 7.10 and build from src so I grabbed an unused machine and put Suse 10.3 along with MD 0.18 on it. Yes it is nice but to get real work done is next to impossible. Crashes consistantly and if not that then Suse 10.3 spawns tasks randomly.

Right now I am using glade3, emacs and the CLI to compile on 7.10. This is virtually no different than if I wrote the app in C with glade2 C code but then I would have fits trying to get it to work correctly in Win box.

I wish the folks over at Novell would concentrate a little bit on the IDE's stability.

I get 0 crashes for mono develop . And I am using it extensively (for a 5 month project). I never used glade. I am only doing web development with it and asp.net. And I am very happy with current stability of monodevelop. Possibly there is something else wrong in your setup.

---

### Post by Shin_Gouki2501 on 2008-01-19
[http://emonic.sourceforge.net/](http://emonic.sourceforge.net/)

or this

[http://sourceforge.net/projects/emonic](http://sourceforge.net/projects/emonic)

give it a try :)

and share ur results!

Eclipse for java rocks and this plugin looks very promising!!

---

### Post by JackBak on 2008-01-19
> **emperon said:**
> I get 0 crashes for mono develop . And I am using it extensively (for a 5 month project). I never used glade. I am only doing web development with it and asp.net. And I am very happy with current stability of monodevelop. Possibly there is something else wrong in your setup.

Well that's good for you but not my experience on at least 4 different machines (AMD or Intel CPUs, Gentoo, Ubuntu or OpenSuse from MD 0.10 onwards). I'd say I've given Mono Develop a pretty good chance (not to say I've given up but one does need to get real work done).

Maybe asp.net and web stuff is different I've done none of that I only write local applications and firmware.

@Shin_Gouki2501

Thanks I'll look into that.

---

