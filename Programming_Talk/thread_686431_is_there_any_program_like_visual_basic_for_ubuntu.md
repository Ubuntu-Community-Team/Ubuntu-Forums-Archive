---
title: "is there any program like visual basic for ubuntu?"
date: 2008-02-03
forum: Programming Talk
---

### Post by arvindenrique on 2008-02-03
is there any program like visual basic for ubuntu?

---

### Post by LaRoza on 2008-02-03
Visual Basic is a programming language, and yes, there are BASIC like languages for Linux.

Visual Studio is an IDE, which may be what you are asking about. See the stickies in the Programming Talk.

---

### Post by Alx c on 2008-02-03
You can download WINE wich lets you use any windows programs on ubuntu

---

### Post by webdr on 2008-02-03
Give GAMBAS a try, if I understood you correctly, you seek a linux based replacement for VB. GAMBAS is a nice fit for that.
ALSO,
I know it may not sound ultra-appealing, but if you take time to learn Python, you'll find it to be well worth it.

I hope you find this helpful.
-Mark Williams

---

### Post by M$LOL on 2008-02-03
> **Alx c said:**
> You can download WINE wich lets you use any windows programs on ubuntu

Wine does not let you run any Windows program in Ubuntu, there are quite a few which it will not run, and from what I remember, I think Visual Basic is one of them.

---

### Post by Shin_Gouki2501 on 2008-02-03
u might try eclipse(the best IDE on linux?!) and then use what suites u(PHP, Java etc..):
[www.eclipse.org](www.eclipse.org)

---

### Post by CptPicard on 2008-02-03
[IMG]http://wasteddomain.com/gallery/d/568-1/picard-sigh.jpg[/IMG]

You really should not try to migrate your Windows Experience (tm) as is to Linux. They are different platforms, and if you want to code for MSFT stuff, you should stay on Windows. On Linux it's a whole new world out there, and a better one IMO if you embrace it. Try something like Python, it's far better and about as easy, if not more.

---

### Post by LaRoza on 2008-02-03
@CptPicard I like it. Mind if I use it someday? :)

---

### Post by CptPicard on 2008-02-03
Sure, it's out there in the open. It does suit *me* particularly well though ;)

Really, the thought of Visual Basic on Linux maybe on top of WINE is enough to make Jean-Luc Picard cry. :(

And nobody wants that... right?

---

### Post by pmasiar on 2008-02-03
lol this is exactly my feelings too. CptPicard, you made my day!

---

### Post by LaRoza on 2008-02-03
> **CptPicard said:**
> Really, the thought of Visual Basic on Linux maybe on top of WINE is enough to make Jean-Luc Picard cry. :(

And nobody wants that... right?

I think it is a funny concept, if anyone wants to try it, go ahead. Just be sure to make a video of it and put it on youtube so we can all get a laugh.

---

### Post by aks44 on 2008-02-03
> **CptPicard said:**
> Really, the thought of Visual Basic on Linux
Doesn't Mono already provide that?


Ok, I'll get my coat... :p

---

### Post by scorp123 on 2008-02-03
> **aks44 said:**
> Doesn't Mono already provide that?  You misunderstand a few concepts here. "Visual Basic under WINE on Linux" means you run a native made-for-Windows application and run it under an emulation (= Wine) on another operating system (Linux in this case). Mono however is a port (=  translated to Linux so it will run as native program!) of the C# programming language and ".Net" programming concepts to Linux. Mono is not an emulation! And it has nothing to do with Visual Basic, the language it is based on is C# (C sharp) which shares some similarities with C, C++ and Java.

---

### Post by M$LOL on 2008-02-03
The connection with Mono and Visual Basic is that VB uses the .net framework/runtime, and a port of that is provided by Mono.

As for Wine, it's not an emulator, it's a compatibility layer, but yes you're right in saying that it's designed to run native Windows applications on linux.

---

### Post by aks44 on 2008-02-03
> **scorp123 said:**
> You misunderstand a few concepts here.
Just in case you didn't notice, it was quite a tongue in the cheek comment...



Now, to *your* misunderstanding of some concepts / facts... ;)

> **scorp123 said:**
> "Visual Basic under WINE on Linux" means you run a native made-for-Windows application and run it under an emulation (= Wine) on another operating system (Linux in this case).
**W**ine **I**s **N**ot an **E**mulator, it is a "compatibility layer for running Windows programs".

BTW as you probably noticed it I took care to leave out the "under Wine" part in my previous quote. ;)


> **scorp123 said:**
> Mono however is a port (=  translated to Linux so it will run as native program!) of the C# programming language and ".Net" programming concepts to Linux. Mono is not an emulation! And it has nothing to do with Visual Basic, the language it is based on is C# (C sharp)
Mono is *not* a port of .Net, it is an independent implementation of the CLI (*Common Language Infrastructure*, which is both an ECMA and an ISO standard), just like .Net is.
Both Mono and .Net are VMs that allow CIL (*Common Intermediate Language*, which is just a glorified name for "bytecode") programs to be executed (usually through *Just In Time* compilation, just like the Java VM does BTW). Of course, both also provide a bunch of runtime libraries so that CIL programs can do something useful.
FWIW these bytecode programs can be generated from a number of different languages, including C#, **VB.Net**, IronPython, ...  (again, just like the Java VM which supports the Java language itself, but also Jython and many more).

If I wanted to be picky, I'd say that Windows programs running on Linux thanks to Wine run natively (remember? Wine's implementation of the Win32 API just consists of native Linux libraries) as they execute directly on the CPU without modification (nor intermediate virtualization layer), while Mono and .Net (again, just like Java) actually are virtual machines, IOW emulators.


So there. :D

---

### Post by scorp123 on 2008-02-03
> **aks44 said:**
>  Just in case you didn't notice, it was quite a tongue in the cheek comment...  Oh :)  In that case let's just forget what I wrote up there. :)

> **aks44 said:**
>  Now, to *your* misunderstanding of some concepts / facts... ;)  I kept stuff as simple as possible (and maybe even over-simplified stuff) ... because I totally misjudged you. Sorry for that. :)

As for the rest ... I am fully aware of all this. As I said ... I misjudged you and totally missed the nature of your earlier comment. Sorry about that too :)

---

### Post by pmasiar on 2008-02-04
> **arvindenrique said:**
> is there any program like visual basic for ubuntu?

to OP:

Do you want to have same syntax and functionality as VB/VS on Windows? Then stay on Windows. Please take no offense, I just want to make your life simple.

Do you want to learn something different, to see how Linux-based tools and solutions are superior to those on Windows? **Then obviously you need to learn those tools!** :-)

In area of simple but powerful language for programmers who don't want to handle the power and responsibility of using C/C++/C#, there are couple of dynamically typed languages (VB can do that too, but not as flexible). Python is my favorite, see stickies and wiki in my sig for links and training tasks.

---

### Post by clasificado on 2008-02-04
For a simple question, a simple answer:

Try monodevelop, its in repostories.

---

### Post by aks44 on 2008-02-04
> **clasificado said:**
> For a simple question, a simple answer
You're not quite used to this subforum, are you? Don't worry you'll get used to that... :p


[SIZE="1"](sorry, I couldn't help it... I'll get my coat ;))[/SIZE]

---

### Post by skippi90 on 2008-02-13
> **webdr said:**
> Give GAMBAS a try, if I understood you correctly, you seek a linux based replacement for VB. GAMBAS is a nice fit for that.
ALSO,
I know it may not sound ultra-appealing, but if you take time to learn Python, you'll find it to be well worth it.

I hope you find this helpful.
-Mark Williams

I probably sound like a total **** but should GAMBAS be able to open vbp (visual basic project) files?

I need a program that can work with these file types on Ubuntu for my coursework.

---

### Post by LaRoza on 2008-02-13
> **skippi90 said:**
> I probably sound like a total **** but should GAMBAS be able to open vbp (visual basic project) files?

I need a program that can work with these file types on Ubuntu for my coursework.

No, it shouldn't. I don't know if it can, but it is not VS so it shouldn't try to be.

You are using Visual Studio, and .NET for school? Then use Windows and Visual Studio. 

If you don't have Windows at home, use a school computer.

Linux != Windows

---

### Post by ogwilson on 2008-02-13
Now, completely oblivious to THAT guy's (skippi's) intentions, Is GAMBAS just a front end gui designer to many languages (kind of like QT4 or Glade) or does it incorporate its own language? And does Monodevelop exclusively use C#?

---

### Post by LaRoza on 2008-02-14
> **ogwilson said:**
> Now, completely oblivious to THAT guy's (skippi's) intentions, Is GAMBAS just a front end gui designer to many languages (kind of like QT4 or Glade) or does it incorporate its own language? And does Monodevelop exclusively use C#?

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

Monodevelop doesn't just use C#.

---

### Post by johnboy82 on 2013-02-28
I was going to try QT basic.  I do not know if it will open vb files.

---

### Post by Drakx on 2013-03-16
[http://www.realsoftware.com/realstudio/](http://www.realsoftware.com/realstudio/) failing that MonoDevelop and Mono.

---

### Post by QIII on 2013-03-16
Thank you for sharing.  Everyone’s questions are important and answers are valuable.

This zombie has been walking around for two weeks...

&#65279;If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

*Thread **closed.***

---

