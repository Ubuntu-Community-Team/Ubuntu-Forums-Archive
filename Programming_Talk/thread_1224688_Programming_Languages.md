---
title: "Programming Languages"
date: 2009-07-27
forum: Programming Talk
---

### Post by BillHudson on 2009-07-27
I'm new to Ubuntu. Been on Windows programming with VB6 and now .NET and also Asm. I was writing stand alone Asm programs and mixing with VB. I would like some suggestions on what I should go for as far as programming. I was looking into Mono, it looks like they have/gonna have VB.NET Looks like you need to put Mono in front of your programs to run them. Is that interpreting? I definetly want stand alone programs. Maybe VB.net isn't a good option, I just have no direction at all. I've been fighting C for 25 years, maybe I need to give in to C# or something.

It's pretty overwhelming learning the operating system and directory structures and commandline and all so thought I'd get some help with suggestions on what others are using for programming as far as Languages, IDE's, and Environments.

Thanks

---

### Post by Can+~ on 2009-07-27
The popular choice in ubuntu is Python, because it already comes with the OS and it's easy to learn and has a truckload of libraries. Besides is good for the mind having some Functional paradigm.

Other than that, if you want to stick to statically-typed Object Oriented, go with Java, it's (more) cross-platform.

---

### Post by Mirge on 2009-07-27
> **Can+~ said:**
> The popular choice in ubuntu is Python, because it already comes with the OS and it's easy to learn and has a truckload of libraries. Besides is good for the mind having some Functional paradigm.

Other than that, if you want to stick to statically-typed Object Oriented, go with Java, it's (more) cross-platform.

Seconded... Python is already popular and widely supported, and is only gaining more popularity. It is an interpreted language, but it comes pre-installed on most Linux distro's, and is easy to obtain on any "popular" OS really.

I don't have any experience with Java, and very limited experience with C# .NET... so I can't really comment on that part.

EDIT: But before you really dive into programming on Linux, you might just spend a little time familiarizing yourself with the new environment and enjoying it! :)

---

### Post by efikkan on 2009-07-27
Use C/C++ for backends, Python for scripting and maybe frontends. Java is not well suited for anything but applets.

What kind of applications do yo want to create?

---

### Post by Mirge on 2009-07-27
> **efikkan said:**
> Use C/C++ for backends, Python for scripting and maybe frontends. Java is not well suited for anything but applets.

What kind of applications do yo want to create?

Eclipse is written in Java, and I love it :).

---

### Post by CptPicard on 2009-07-27
> **efikkan said:**
> Java is not well suited for anything but applets.

... and large enterprise application architectures...

---

### Post by directhex on 2009-07-27
> **BillHudson said:**
> I'm new to Ubuntu. Been on Windows programming with VB6 and now .NET and also Asm. I was writing stand alone Asm programs and mixing with VB. I would like some suggestions on what I should go for as far as programming. I was looking into Mono, it looks like they have/gonna have VB.NET Looks like you need to put Mono in front of your programs to run them. Is that interpreting? I definetly want stand alone programs. Maybe VB.net isn't a good option, I just have no direction at all. I've been fighting C for 25 years, maybe I need to give in to C# or something.

It's pretty overwhelming learning the operating system and directory structures and commandline and all so thought I'd get some help with suggestions on what others are using for programming as far as Languages, IDE's, and Environments.

Thanks

Consider Vala if you want to make "native" binaries, i.e. no need for an interpreter or JITter. It has a vaguely C#-like syntax, but nothing resembling the standard .NET class library

---

### Post by efikkan on 2009-07-27
> **CptPicard said:**
> ... and large enterprise application architectures... It's quickly to write small applications in Java, but larger applications is slower and more difficult to write than e.g. C++. Due to the slow performance in Java, performance-dependent applications should be written in a more suitable programming language(perferly native binaries).

In addition, Java can sometimes be difficult to set up on GNU/Linux, especially on 64 bit platforms. And Java apps often got problems running on some computers, even though Java is correctly set up.

---

### Post by Mirge on 2009-07-27
> **efikkan said:**
> It's quickly to write small applications in Java, but larger applications is slower and more difficult to write than e.g. C++. **Due to the slow performance in Java**, performance-dependent applications should be written in a more suitable programming language(perferly native binaries).
[B]
In addition, Java can sometimes be difficult to set up on GNU/Linux, especially on 64 bit platforms[/B]. And **Java apps often got problems running on some computers, even though Java is correctly set up**.

Not to start some huge heated debate or anything, but can you please cite sources/examples for these comments in bold?

---

### Post by CptPicard on 2009-07-27
> **efikkan said:**
> It's quickly to write small applications in Java, but larger applications is slower and more difficult to write than e.g. C++.

Actually, Java is in a lot of ways more suited to relatively large applications in the desktop sense (think Eclipse) as the VM's relative size no longer dominates the memory footprint, for example. There is a performance difference, but I never could claim that Java is under any circumstances actually harder to write apps in than C++ is.

In particular when it comes to clustered, networked enterprise-style applications, J2EE is hard to beat in robustness and ease of development (at least by anything in C++, that I'm aware of)

> Due to the slow performance in Java, performance-dependent applications should be written in a more suitable programming language(perferly native binaries).

Well, Java does JIT-compile to native. Probably the greatest performance bottleneck in Java are the object references -- pretty much everything is on the heap, so chances for register-allocation optimizations are less. Another important thing to watch is how much one is thrashing the garbage collector...

I actually do fairly heavy number-crunching in Java, and performance is sufficient, that is, I have not been able to justify reimplementation in C/C++.

---

### Post by directhex on 2009-07-27
> **Mirge said:**
> Not to start some huge heated debate or anything, but can you please cite sources/examples for these comments in bold?

Well, certainly for applets, 64-bit sucks (proprietary java only gained a 64-bit plugin in 6u13, and the Free plugin is crap)

---

### Post by &#32 Greg on 2009-07-27
> **BillHudson said:**
> 
It's pretty overwhelming learning the operating system and directory structures and commandline and all so thought I'd get some help with suggestions on what others are using for programming as far as Languages, IDE's, and Environments.

Thanks

I've been programming in Cuda and Scheme from within Emacs.

---

### Post by directhex on 2009-07-27
> **BillHudson said:**
> It's pretty overwhelming learning the operating system and directory structures and commandline and all so thought I'd get some help with suggestions on what others are using for programming as far as Languages, IDE's, and Environments.

C# in MonoDevelop

I'm not above stealing a decent framework, even if it's from Microsoft.

---

### Post by Mirge on 2009-07-27
> **directhex said:**
> C# in MonoDevelop

I'm not above stealing a decent framework, even if it's from Microsoft.

Haha. I'm still toying around with C# on Vista in my spare time... I tried MonoDevelop, then realized that I can't "out of the box" I suppose, use System.Windows.Forms in MD, but rather GTK#. So, for the time being, I'm just playing around with it in Vista.

---

### Post by slavik on 2009-07-27
> **CptPicard said:**
> ...
In particular when it comes to clustered, networked enterprise-style applications, J2EE is hard to beat in robustness and ease of development (at least by anything in C++, that I'm aware of)
...

You, sir, have been converted. :)

---

### Post by CptPicard on 2009-07-27
> **slavik said:**
> You, sir, have been converted. :)

Well FWIW Enterprise Java really is the only game in town. ;) But yeah, you can blame EJB3.0 and tinny for me having taken a second look and kinda liking what I see... EJB2 *was* an awful mess of XML, and of course, the whole stack is still rather complex... but I guess there is no free lunch there.

---

### Post by schmendrick on 2009-07-28
> **Mirge said:**
> Haha. I'm still toying around with C# on Vista in my spare time... I tried MonoDevelop, then realized that I can't "out of the box" I suppose, use System.Windows.Forms in MD, but rather GTK#. So, for the time being, I'm just playing around with it in Vista.

then i guess you're doing something wrong. 
AFAIK monodevelop should now run out of the box on ubuntu 9.04.
plus you can also use windows.forms. i use quite some of my simple GUI apps (based on windows.forms ) under ubuntu. 


to the original topic:
i'd also go for monodevelop with C#. you will feel most at home when you come from visual basic. plus, mono is installed by default on all ubuntu's. 
so when you distribute your programs they will run out of the box under win and under ubuntu, centOS, suse... i dont know other distros though. 

if you go for python your programs wont run out of the box under windows :p

---

### Post by Mirge on 2009-07-28
> **schmendrick said:**
> then i guess you're doing something wrong. 
AFAIK monodevelop should now run out of the box on ubuntu 9.04.
plus you can also use windows.forms. i use quite some of my simple GUI apps (based on windows.forms ) under ubuntu. 


to the original topic:
i'd also go for monodevelop with C#. you will feel most at home when you come from visual basic. plus, mono is installed by default on all ubuntu's. 
so when you distribute your programs they will run out of the box under win and under ubuntu, centOS, suse... i dont know other distros though. 

if you go for python your programs wont run out of the box under windows :p

MonoDevelop worked out of the box, but I meant it was lacking some sort of WinForms designer, or what not.

---

### Post by monraaf on 2009-07-28
> **schmendrick said:**
> 
i'd also go for monodevelop with C#. you will feel most at home when you come from visual basic. plus, mono is installed by default on all ubuntu's. 
so when you distribute your programs they will run out of the box under win and under ubuntu, centOS, suse... i dont know other distros though. 

if you go for python your programs wont run out of the box under windows :p

Yeah, I wonder how long it takes before the writers of malware will find out. I guess Ubuntu's market share isn't high enough yet.

---

### Post by JordyD on 2009-07-28
> **monraaf said:**
> Yeah, I wonder how long it takes before the writers of malware will find out. I guess Ubuntu's market share isn't high enough yet.

Put VB on Linux and the virus writers will follow.

---

