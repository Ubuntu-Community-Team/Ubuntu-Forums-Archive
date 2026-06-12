---
title: "What programing language...?"
date: 2007-09-05
forum: Programming Talk
---

### Post by Shoot3r101 on 2007-09-05
Hello I recently switched to Ubuntu and am wondering what is the *good*, *best*, and *better* programming languages for Ubuntu. Please also include links to the compiler's for the "Good, Best, and Better" programing languages you picked...

btw I am not a starter. Been programing for years in Visual Basic and now C#.

---

### Post by rharriso on 2007-09-05
A lot of people are really high on Python. 
Bash shell script is a must. 
I like using C++ personally, but thats only because I learned it first.
And I like saying "C plus plus"

---

### Post by rharriso on 2007-09-05
I use the g++ compiler for c++ 
bash doesn't have a compiler.
I've never tried another compiler for python other than the standard one.

---

### Post by softtower on 2007-09-05
This is Linux and you're not getting anywhere without a decent knowledge in C. That's the first thing you'd have to understand. Lots of libraries for Perl, Python and Ruby have C back-ends.

Historically, the second most important language on Linuxes has been Perl, although recently it is getting rapidly replaced with Python.

And, finally, I think you should learn Bash scripting language. This is what I am doing right now myself. :)

---

### Post by Shoot3r101 on 2007-09-05
> **softtower said:**
> **This is Linux and you're not getting anywhere without a decent knowledge in C.** That's the first thing you'd have to understand. Lots of libraries for Perl, Python and Ruby have C back-ends.

Historically, the second most important language on Linuxes has been Perl, although recently it is getting rapidly replaced with Python.

And, finally, I think you should learn Bash scripting language. This is what I am doing right now myself. :)lol I have been programing in C# for many years. But can you guys point me to a C# compiler for Ubuntu maybe?

---

### Post by lisati on 2007-09-05
> **Shoot3r101 said:**
> lol I have been programing in C# for many years. But can you guys point me to a C# compiler for Ubuntu maybe?

You might want to look at [www.programmersheaven.com](www.programmersheaven.com)

---

### Post by fct on 2007-09-05
> **Shoot3r101 said:**
> lol I have been programing in C# for many years. But can you guys point me to a C# compiler for Ubuntu maybe?

Sure, mono:

[http://www.go-mono.com](http://www.go-mono.com)

It's included in the ubuntu packages, with the experimental ide monodevelop. You might want to get that last one from [http://www.getdeb.net](http://www.getdeb.net) though, it provides more updated packages.

Don't forget that not all MS .NET functions are implemented in Mono. On the other hand, it provides some libraries (GTK#, System.Posix) that you don't find in MS's solution.

But I suggest you get a nice C book and build on that, then you will get access to many esoteric Unix libraries that aren't always available from other languages.

Java is another good option too, and easy to adapt from C# (not to mention the most demanded language in job offers). If you install netbeans you will get a nice IDE with the best java GUI editor I've used.

---

### Post by xtacocorex on 2007-09-05
Not to be rude, but all the information you require is in the sticky threads at the beginning of this subforum.

You already know programming methodology so it shouldn't be too hard for you to pick up syndax.  You should know that languages are tools and choosing one for a project is like picking the right tool.

---

### Post by LaRoza on 2007-09-05
[http://laroza.pbwiki.com/](http://laroza.pbwiki.com/)

(No such thing as "best")

---

### Post by pmasiar on 2007-09-05
> **Shoot3r101 said:**
> wondering what is the *good*, *best*, and *better* programming languages for Ubuntu. .... Been programing for years in Visual Basic and now C#.

Best language to do what? Do you want to learn something new? etc etc.
drivers or kernel? C
desktop or web-based apps: Python
participate in some project? they already have the language - use it.

Linux is not proprietary silo, everybody uses (and improves, and promotes :-) ) tools best for the small niche where the project is.

I am just curious how "expert" were the "experts" answering your question, who "know" what language you should use without bothering to ask what **kind** of program you want to write? Very interesting, perhaps they recommended you the only tool **they** know? :twisted:

---

### Post by Tomosaur on 2007-09-05
> **Shoot3r101 said:**
> lol I have been programing in C# for many years. But can you guys point me to a C# compiler for Ubuntu maybe?


C# is not C. C# is a proprietary language developed by Microsoft to rival Java (Java is being open-sourced gradually).

C# and Java are C-like, but C isn't inherently object oriented (for that you'll want C++).

The compiler for C on Linux is gcc.
The compiler for C++ on Linux is g++.
The compiler for C# on Linux is provided by the Mono project.
Java's compiler is provided by Sun, but there are other compilers available (but I just use the Sun compiler).

Python is Ubuntu's favoured language for user-land software, but if you want to do stuff like Kernel development or write system software / drivers and such, then you'll be wanting to use C or C++.

---

### Post by pmasiar on 2007-09-05
> **Shoot3r101 said:**
> lol I have been programing in C# for many years. But can you guys point me to a C# compiler for Ubuntu maybe?

You asked for the "best". C# is **far** from preferred language for Linux development. Python and C are among the most popular. I know some interesting projects are using C#, you may want to join those.

---

### Post by slavik on 2007-09-05
> **pmasiar said:**
> Best language to do what? Do you want to learn something new? etc etc.
drivers or kernel? C
desktop or web-based apps: Python
participate in some project? they already have the language - use it.

Linux is not proprietary silo, everybody uses (and improves, and promotes :-) ) tools best for the small niche where the project is.

I am just curious how "expert" were the "experts" answering your question, who "know" what language you should use without bothering to ask what **kind** of program you want to write? Very interesting, perhaps they recommended you the only tool **they** know? :twisted:

Use Perl for everything. For everything else: Perl. :P

---

### Post by ubuntukerala1980 on 2007-09-05
Python otherwise ruby
:guitar:

---

### Post by emperon on 2007-09-05
> **Tomosaur said:**
> C# is not C. C# is a proprietary language developed by Microsoft to rival Java (Java is being open-sourced gradually).


This is definitely wrong. C# is an ECMA standard language and does not belong to Microsoft and it is not a propriety language. 

 C# on mono is quite usable, stable and up to date and it is my preferred way for Platform Independent applications.

---

### Post by gnusci on 2007-09-05
My favourite is:

[IMG]http://gcc.gnu.org/img/gccegg-65.png[/IMG]

[http://gcc.gnu.org/](http://gcc.gnu.org/)

To prepare your machine for compiling you will need:

**$ sudo apt-get install build-essential** (compiling tools)
**$ sudo apt-get install freeglut3-dev**   (open gl)
**$ sudo apt-get build-dep xorg-dev**    (x11 for developing)

Extras:

**$ sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2**

---

### Post by Wybiral on 2007-09-05
> ... what is the good, best, and better programming languages for Ubuntu ...

It's been proven beyond conceivable doubt that [BF]("http://www.muppetlabs.com/~breadbox/software/tiny/bf.asm.txt") is clearly the "good, best, and better" of all languages past and present.

That link will give you the instructions to assemble it (you will need NASM). The language BTW is BrainFuck :)

---

### Post by Tomosaur on 2007-09-05
> **emperon said:**
> This is definitely wrong. C# is an ECMA standard language and does not belong to Microsoft and it is not a propriety language. 

 C# on mono is quite usable, stable and up to date and it is my preferred way for Platform Independent applications.

[According to Wikipedia]("http://en.wikipedia.org/wiki/C_Sharp"), C# was developed by Microsoft, then later approved by ECMA and ISO. Microsoft has its own implementation of C# - Microsoft Visual C#, and you're right - technically speaking, a language cannot be 'owned'. It is possible to create a purely open-source version of C#, since it is, after all, only a language., which is 'kind of sort of' the point of Mono.

However, Mono is an attempt to allow .NET development on platforms other than Windows, which goes above and beyond just creating a Linux implementation of C#. .NET is a set of libraries and such to allow development on Windows, originally intended to allow cross-platform development but never quite got there, Mono aims to improve the situation.

Microsoft applied for patents on some key areas of .NET. Novell (who sponsor Mono) and Microsoft made a deal not to sue each other, and said that this deal extends to Mono, but only for Novell users and developers. This is what much of the anger in the Linux world was about when the Novell/MS deal first came about. When I use 'proprietary', I mean that the product is non-free in the philosophical sense. Mono, and thus by extension C# on Linux are in shady territory regarding 'freedom'. If you don't want the hassle of dodgy licensing, and the shadow of Microsoft patents looming over you, then I would suggest you avoid Mono.

Don't get me wrong, I'm not trying to deride the quality of Mono in anyway, the results speak for themselves, but Mono is not just an implementation of C#, it is an implementation of Microsoft's .NET, which wouldn't be a problem if Microsoft hadn't gone the patent route and then claimed everyone was ripping them off. People should just use whatever they like the best - if that means C# on Mono, then who am I to tell you what to do?

If, however, you want to use a C# style language, then I would suggest you give Java a go. Java is essentially the same kind of thing as C# and .NET - its focus is on standard ways of doing things, and platform independence. Java was also proprietary in every sense, but Sun seem to be realising the error of their ways, and are GPLing it. This will allow people to create GPL implementations of Java and the JVM and such - the current open source implementations leave a lot to be desired.

You may also want to keep an eye on the D programming language, which isn't really complete yet, but looks very promising.

---

### Post by emperon on 2007-09-05
> **Tomosaur said:**
> [According to Wikipedia]("http://en.wikipedia.org/wiki/C_Sharp"), C# was developed by Microsoft, then later approved by ECMA and ISO. Microsoft has its own implementation of C# - Microsoft Visual C#, and you're right - technically speaking, a language cannot be 'owned'. It is possible to create a purely open-source version of C#, since it is, after all, only a language., which is 'kind of sort of' the point of Mono.

However, Mono is an attempt to allow .NET development on platforms other than Windows, which goes above and beyond just creating a Linux implementation of C#. .NET is a set of libraries and such to allow development on Windows, originally intended to allow cross-platform development but never quite got there, Mono aims to improve the situation.

Microsoft applied for patents on some key areas of .NET. Novell (who sponsor Mono) and Microsoft made a deal not to sue each other, and said that this deal extends to Mono, but only for Novell users and developers. This is what much of the anger in the Linux world was about when the Novell/MS deal first came about. When I use 'proprietary', I mean that the product is non-free in the philosophical sense. Mono, and thus by extension C# on Linux are in shady territory regarding 'freedom'. If you don't want the hassle of dodgy licensing, and the shadow of Microsoft patents looming over you, then I would suggest you avoid Mono.

Don't get me wrong, I'm not trying to deride the quality of Mono in anyway, the results speak for themselves, but Mono is not just an implementation of C#, it is an implementation of Microsoft's .NET, which wouldn't be a problem if Microsoft hadn't gone the patent route and then claimed everyone was ripping them off. People should just use whatever they like the best - if that means C# on Mono, then who am I to tell you what to do?

If, however, you want to use a C# style language, then I would suggest you give Java a go. Java is essentially the same kind of thing as C# and .NET - its focus is on standard ways of doing things, and platform independence. Java was also proprietary in every sense, but Sun seem to be realising the error of their ways, and are GPLing it. This will allow people to create GPL implementations of Java and the JVM and such - the current open source implementations leave a lot to be desired.

You may also want to keep an eye on the D programming language, which isn't really complete yet, but looks very promising.

Stop spreading FUD. Learn the facts. C# and Core library of .NET framework is not a property of Microsoft. The only patented technolgoies are Windows Forms , ASP.NET and ADO.NET.  You can definitely develop applications without those. And as long as you don't use these you are 100% safe.
And finally Mono is Open Source , Java is NOT (Java 7 has not been released which will then later be named Open Java or Open JDK and sun will also promote its own Java version )

taken from : [http://www.mono-project.com/FAQ:_Licensing]("http://www.mono-project.com/FAQ:_Licensing")
 Could patents be used to completely disable Mono?

First some background information.

The .NET Framework is divided in two parts: the ECMA/ISO covered technologies and the other technologies developed on top of it like ADO.NET, ASP.NET and Windows.Forms.

Mono implements the ECMA/ISO covered parts, as well as being a project that aims to implement the higher level blocks like ASP.NET, ADO.NET and Windows.Forms.

The Mono project has gone beyond both of those components and has developed and integrated third party class libraries, the most important being: Debugging APIs, integration with the Gnome platform (Accessibility, Pango rendering, Gdk/Gtk, Glade, GnomeUI), Mozilla, OpenGL, extensive database support (Microsoft only supports a couple of providers out of the box, while Mono has support for 11 different providers), our POSIX integration libraries and finally the embedded API (used to add scripting to applications and host the CLI, or for example as an embedded runtime in Apache).

The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission. Jim Miller at Microsoft has made a statement on the patents covering ISO/ECMA, (he is one of the inventors listed in the patent): here ([http://web.archive.org/web/20030424174805/http://mailserver.di.unipi.it/pipermail/dotnet-sscli/msg00218.html](http://web.archive.org/web/20030424174805/http://mailserver.di.unipi.it/pipermail/dotnet-sscli/msg00218.html))

Basically a grant is given to anyone who want to implement those components for free and for any purpose.

For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless.

Not providing a patented capability would weaken the interoperability, but it would still provide the free software / open source software community with good development tools, which is the primary reason for developing Mono.

The patents do not apply in countries where software patents are not allowed.

For Linux server and desktop development, we only need the ECMA components, and things that we have developed (like Gtk#) or Apache integration.
With the new Novell/Microsoft agreement, will the patent policy change?

Mono is a community project, and as such, we will continue to implement the policy of not integrating knowingly infringing code into Mono.

And we will continue to follow the steps outlined in the previous topic if code that potentially infringes is found: finding prior art, finding different implementation techniques, or if none of those are possible, removing the code from Mono.

---

### Post by Tomosaur on 2007-09-05
> **emperon said:**
> Stop spreading FUD. Learn the facts. C# and Core library of .NET framework is not a property of Microsoft. The only patented technolgoies are Windows Forms , ASP.NET and ADO.NET.


FUD? Mono contains (or at least aims to contain) patented stuff - just because you don't have to use that patented stuff doesn't mean it isn't there.

The issue extends beyond Mono - there are other patent issues elsewhere. The problem is not Mono, it is the patent system. If you use Mono, regardless of whether you make use of the patented bits or not, you are giving support to the patent 'industry' (because that's what it is these days). It doesn't matter if Mono does actually infringe on patents or not - the mere risk of patent warfare can cause massive disruption, especially to smaller businesses and individuals who are unable to innovate because of these patents, for fear of a legal battle.

It is a stated Mono goal to implement patented Microsoft code (ie Windows.Forms, ASP.NET and ADO.NET). This means that they will either:
a) Disregard the patents and do it anyway.
b) Cross-licence the patents (The Novell/MS deal may already have accomplished this, I'm not sure).

If they choose option a - then they run the risk of an MS patent attack. Even if the Mono devs think they have worked their way around the patents (which is what they want to do), MS is a vastly more powerful machine, and could probably do a lot of damage without having to enter into messy patent battles.

If they choose option b - they're supporting the idea of software patents. Whether you agree that this is a bad thing is up to you.

For me - software patents are just plain wrong. It is entirely subjective whether you think supporting Mono means supporting the patent system, but I do. I have no ill feeling towards the Mono devs, and I think what they're doing is very commendable, but I do think they're playing in dangerous territory. Just because they have free reign to implement most of .NET and C# - the fact that there is a small portion of .NET which they cannot implement freely is enough for me to avoid it.

I realise that much of what I'm saying is based on a philosophical viewpoint, but I stand by it whole-heartedly.

It's like playing with a handgun - if you don't point it at yourself you're safe. You're still playing with a deadly weapon, though.

Finally - I know Java is not currently open-source, that's why I said it is BEING open-sourced. I am not 100% behind Java either, but I feel it is less cumbersome with regards to these issues than Mono.

I admit I shouldn't have said C# is proprietary - I think I use that word too broadly.

---

### Post by pmasiar on 2007-09-05
I agree with Tomosaur. I just don't see need to **follow** some proprietary development, if we can **lead**. Much safer is to develop ideas based from common principles and publically available information, that to rely on some shady patent deals. I just don't see the urgent need. What is user-level reason to follow .NET? Beyond compatibility, what else it gives us?

I don't see why superior, time-proven platform like Unix/Linux should strive to be compatible with bloody mess like Windows Vista is. MSFT cannot manage to be compatible with themselves, why we should follow all mistakes they do on their way to obscurity? 

Everybody knows that MSFT is shadow of former self, and in 30 years it will be another former Borland. So why to embrace it now?

---

### Post by Shoot3r101 on 2007-09-06
Well I do not intend to stay with C# if it cause's the fellow folks at Microsoft(R) problems. I am willing to step forward and move up to a more complex programming language that doesn't evolve around .NET. Python for example; it is entirely based on Linux and if I am wrong please correct me but python is well-developed programming language and should offer same amount of power that .NET provides. On top of all that python has been upgrading and been very reliable since IRC was  discovered and perhaps before that too.

---

### Post by emperon on 2007-09-06
> **Shoot3r101 said:**
> Well I do not intend to stay with C# if it cause's the fellow folks at Microsoft(R) problems. I am willing to step forward and move up to a more complex programming language that doesn't evolve around .NET. Python for example; it is entirely based on Linux and if I am wrong please correct me but python is well-developed programming language and should offer same amount of power that .NET provides. On top of all that python has been upgrading and been very reliable since IRC was  discovered and perhaps before that too.

No Way in deed. I am also a Ruby programmer which is supposed to be better than python. Comparing to C# , dynamic languages like Python and Ruby are nicer. C# seems to be (at least on pre 3.0 era) too verbose for same stuff. Comparing libraries Python has tremendous amount of bindings for linux. .NET Library is also intense. However I would still go with Mono for the following reasons:

1-) Mono offers you the following learn 1 platfrom and do everything (Desktop applications , Web applications , Multi Threaded applications , localized apps, Distributed Apps)

2-) Mono offers true cross platformity without any extra runtime installed. You know Gnome has mono installed. Most XP and all Vista's have .net already installed. So you can write your application and it would work 100% on other platforms without any glitch (winforms 2.0 is mostly complete, other than that if it would work 100%)

3-) C# is too Verbose ? Well you've got Boo. I like Boo better than python and ruby every which way. It's static but it allows duck typing. So we got best of both worlds. Not enough ?  We've got IronPython, IronRuby (alpha) , Ruby.NET (beta) , Nemerle, dotList, F#  all can interplay with each other

4-) You can reuse libraries designed for MS.NET like NHibernate, Nunit... they work seamlesly on mono

---

### Post by Wybiral on 2007-09-06
> **emperon said:**
> I am also a Ruby programmer which is supposed to be better than python.

Really? Damn... I must not have got that memo. Who decided this?

So Ruby is simply, in general, better than Python?

---

### Post by emperon on 2007-09-06
> **Wybiral said:**
> Really? Damn... I must not have got that memo. Who decided this?

So Ruby is simply, in general, better than Python?

Which language is better ? 
BASIC or Python ?

I think you know the answer. But who decided this ?

---

### Post by pmasiar on 2007-09-06
> **emperon said:**
> Which language is better ? 
BASIC or Python ?

I think you know the answer. But who decided this ?

You are trying to weasel out. **You** claimed that Ruby is better that Python, and **you** have to support that claim, or withdraw it as unsupported personal opinion.

---

### Post by Wybiral on 2007-09-06
> **emperon said:**
> Which language is better ? 
BASIC or Python ?

I think you know the answer. But who decided this ?

1. Not everyone shares that answer (there are hundreds of VB programmers that beg to differ.

2. The answer to that can be backed up by facts comparing the two, but primarily the OOP and dynamic features of Python are what (to me) make it better.

3. Python is a language, NOT a dialect. It has it's own standard library. The two don't compare.

4. BASIC is largely dead in programming (with the odd exception of VB). Python and Ruby are both about equally active.

The fact is that you can't make an argument like this as I've programmed in several dialects of BASIC (when I was learning to program), Ruby, AND Python. And I see no obvious reason why Ruby would be, in general, "better" then Python.

---

### Post by frenchcr on 2007-09-06
removed

---

### Post by Shoot3r101 on 2007-09-07
Okay well I took your guy's advice and went with mono I just hope Microsoft(R) is still my friend:(... Although I will most likely try out Ruby(R) and Python(R) later on in the future. Thanks for your guy's help :guitar:.

---

