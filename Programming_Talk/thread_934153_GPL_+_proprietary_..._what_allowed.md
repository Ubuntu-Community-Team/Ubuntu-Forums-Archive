---
title: "GPL + proprietary ... what allowed?"
date: 2008-09-30
forum: Programming Talk
---

### Post by Galar on 2008-09-30
Hello,

Now something completly different;)

Im programming some Software in Matlab on windows and its proprietary (not for me, writing at work). It's not delivered yet and will not be delivered in the next months. But it will not to be released on GPL or another free licenence. 

I've used several GPLv2-licenced Software till now (calling on several ways):

- 2 external Programm, called by commandline (generate some input, parse the output)
- a Matlabclass for unittests (something like `derive from this class, configure this, that ...' they key: `derive from this class')

At the moment, everything is fine because our software isn't released but hopefully, this will change in some time (the release-state, not the other). What about the GPL-Software? What I've found out till now is:
- external programms are okay. If I want to distribute our software, either the source of these Programms have to be distributed also or these Software have to be installed seperatly by the customer from another source.
- The unittests will be removed, so we will not derive from something, what is GPLed. (is it posible to reelease the unittests in another Version then the mainsoftware?)

Am I right/ on the right path/ totaly wrong?

thanks in advance

---

### Post by Tomosaur on 2008-09-30
> **Galar said:**
> Hello,

Now something completly different;)

Im programming some Software in Matlab on windows and its proprietary (not for me, writing at work). It's not delivered yet and will not be delivered in the next months. But it will not to be released on GPL or another free licenence. 

I've used several GPLv2-licenced Software till now (calling on several ways):

- 2 external Programm, called by commandline (generate some input, parse the output)
- a Matlabclass for unittests (something like `derive from this class, configure this, that ...' they key: `derive from this class')

At the moment, everything is fine because our software isn't released but hopefully, this will change in some time (the release-state, not the other). What about the GPL-Software? What I've found out till now is:
- external programms are okay. If I want to distribute our software, either the source of these Programms have to be distributed also or these Software have to be installed seperatly by the customer from another source.
- The unittests will be removed, so we will not derive from something, what is GPLed. (is it posible to reelease the unittests in another Version then the mainsoftware?)

Am I right/ on the right path/ totaly wrong?

thanks in advance

You seem to be on the right track.

In short: You cannot use GPL stuff in non-GPL software. Calling an external program which is GPLd is ok.

---

### Post by nvteighen on 2008-09-30
It seems fine to me... Calling an external program is just usage of that program, not a derivative work... at least in USA and EU.

If you don't distribute binaries of the external programs, then you don't have to distribute their source codes.

---

### Post by techmarks on 2008-09-30
In general if GPL source code is required for your program to compile, the program must be under the GPL. Static linking to a GPL library will require your program to be under the GPL.

Putting software together, as when multiple programs are put on one disk, does not count as including GPLed programs in non-GPLed programs.

However what they do absolutely require is that anyone distributing GPL'd works or works made from GPL'd works must in turn distribute them under the GPL.

The output of a program does not count as a derivative work. That's why we can use the gcc compiler in commercial environments without legal problems.

The Linux kernel is under the GPL, any code statically linked with the Linux kernel must be GPLed. 

I still don't really think it's a good idea to use GPL code or programs in proprietary software.

While you may be able to out manouver the legal quagmire that is the GPL, you are still against the spirit of the GPL, as they absolutely have it in for proprietary software.

---

### Post by nrs on 2008-09-30
AFAIK You can link/derive against proprietary libraries in a GPL'd app -- look at all the GPL'd Windows & and OS X programs, but you can't link/derive against GPL'd libraries in a proprietary program.

---

### Post by Galar on 2008-10-01
At first: thank you for all your replies. 

> **techmarks said:**
> ...

I still don't really think it's a good idea to use GPL code or programs in proprietary software.

While you may be able to out manouver the legal quagmire that is the GPL, you are still against the spirit of the GPL, as they absolutely have it in for proprietary software.

My oppinion is a little different. I would like to write on software here at work, that will be released under GPL but thats just a dream. But using GPLed software and explain what that means (for example: free does not only mean free of charge) will be a greater benefit than without. If I can show my professor (I'm sitting here at a university) that free software is a real alternative, he may `advertise' them to other students so they will come in contact with it. And that cant be to bad ;)

MfG

---

### Post by dwhitney67 on 2008-10-01
As a mid-career s/w engineer, I feel shivers run through me when someone implies that if I rely on a GPL product to produce my code that I must in turn give that product away for free.

I think that nvteighen stated it correctly.  As long as you do not include copy snippets (or the entire code) of a GPL s/w product within your own project, you will not be required to release source code.

Making library calls within your code (to say the C-library) will not make your project vulnerable to GPL license restrictions.

If the world were to succumb to the point where all s/w must be developed free of cost because of GPL restrictions, then innovation (at the corporate level) will stop.  The world is ruled by money lovers, and likewise money earners, not by good ol' Samaritans.

Btw, I'm am not a lawyer; thus my interpretation of GPL may be wrong.  God forbid I am wrong.

A little off topic, but have any of you s/w engineers seen this [hilarious clip]("http://develop-one.net/blog/2008/08/27/HugADeveloper.aspx")?

---

### Post by elbarto_87 on 2008-10-01
It is my understanding that there is alot of software out there released under a BSD style license (such as matplotlib, numpy) which is less restrictive for proprietary software. Is this true?

---

### Post by Galar on 2008-10-01
> **dwhitney67 said:**
> 
...
Making library calls within your code (to say the C-library) will not make your project vulnerable to GPL license restrictions.
...

Linking a GPL-library to a proprietary Software isn't allowed in USA and EU. Thats not explicitly said in the GPL-licence but the lawyers interpret it in this way. GPL is very restrictive and I haven't known how restrictive exactly (and no clear awnsers in the FAQs), so I started this thread ;) Maybe you become confused by the LGPL?

@elbarto_87: BSD is another free licence and much less restrictive. For example, it can be used in comercial applications with some conditions. _[wiki knows it]("http://en.wikipedia.org/wiki/BSD_licenses")_ ;) There are other free licence out there (to many of them for my taste). The software I need is ... say ... special. So I have no real choice. For example, I found no alternative to [http://view3d.sourceforge.net/](http://view3d.sourceforge.net/), neither free nor comercial.

EDIT: DOH! view3d is public domain (?) from the US-Gouvernement. But the other ones are GPLed.. shure :?
MfG

---

### Post by Tomosaur on 2008-10-01
> **dwhitney67 said:**
> As a mid-career s/w engineer, I feel shivers run through me when someone implies that if I rely on a GPL product to produce my code that I must in turn give that product away for free.

I think that nvteighen stated it correctly.  As long as you do not include copy snippets (or the entire code) of a GPL s/w product within your own project, you will not be required to release source code.

Making library calls within your code (to say the C-library) will not make your project vulnerable to GPL license restrictions.

If the world were to succumb to the point where all s/w must be developed free of cost because of GPL restrictions, then innovation (at the corporate level) will stop.  The world is ruled by money lovers, and likewise money earners, not by good ol' Samaritans.

Btw, I'm am not a lawyer; thus my interpretation of GPL may be wrong.  God forbid I am wrong.

A little off topic, but have any of you s/w engineers seen this [hilarious clip]("http://develop-one.net/blog/2008/08/27/HugADeveloper.aspx")?

If your software won't compile without GPLd libraries, then your project should be under the GPL - is the general rule of thumb. If you statically link to GPLd libraries, your project should be under the GPL.  It is not enough to just avoid using actual snippets of code.

---

### Post by nvteighen on 2008-10-01
> **dwhitney67 said:**
> 
Making library calls within your code (to say the C-library) will not make your project vulnerable to GPL license restrictions.

The C Standard Library is a bit tricky, as it's licensed under LGPL. The C++ Standard Library is even trickier, as it uses the "GPL + linking exception" License...

The rule of thumb seems to be as simple as, as long you don't distribute code you can't distribute (either in binary or in source), you're fine. IMO, if you distribute a program written in C that uses a library, you're bound to the library's terms because you're distributing the header files' code compiled inside the binary... and if you statically link, you have the whole code inside too...

If you distribute in source, the recipient could compile the code against another implementation of a certain library... or code the library by himself/herself too... So, you're not bound to anything.

But, this interpretation has some flaws when we refer to languages like Python. When importing a module, are you including third parties' code at the Python object code (the .pyc, which is what's actually executed) or not?

Also, under this interpretation of mine, popular applications would be not complying the "Keep all copyright and license notices intact" requirement of (L)GPL when using GTK+, Qt or even the C Standard Library (but in this last case, it could be argued that it's a "System Library" and therefore, excluded from the "Corresponding Source" as GPLv3 defines it... but that's true only for UNIX/Unix-like systems).

These seem to be very borderline cases, where neither the GPL has a clear language.

---

### Post by Tomosaur on 2008-10-02
> **nvteighen said:**
> 
But, this interpretation has some flaws when we refer to languages like Python. When importing a module, are you including third parties' code at the Python object code (the .pyc, which is what's actually executed) or not?

I was thinking about this the other day. I can't remember if I talked about it in the other 'confused about GPL' thread (you know, the billionth one? :P ).

Let's say you write a python program. It uses GPLd libraries, and in fact won't run without them. You don't want to release your code under the GPL. Since Python is JIT compiled, can you just send the .py files with an indicator that 'oh yes, you need GPLd module X, get it from here...' and still avoid GPL infringement? Until the user tries to run the program, the GPLd code isn't used. Your source code only contains a reference to the GPL module. Since compilation is done on the user's machine, does the fact that your non-GPL code won't compile or run unless the user gets the GPLd code themselves matter?

Provided the user doesn't then go and distribute the .pyc files, the GPL doesn't ever seem to be infringed by the developer. What are people's thoughts on this? Is simply referencing a GPL module the same thing as using it? If so, then what if you include a method which is never run (by design) which makes use of a GPLd module? The program doesn't depend on the GPL code, and you're not distributing it, but the source file makes use of it.

Of course I may be completely wrong here, but I guess scripted languages are in a kind of 'grey area'. You couldn't exploit this problem (if it even exists and I'm not just completely wrong) with say, C or Java since the difference between the source code (the part which is covered by the GPL) and the actual binary or bytecode is very distinct. In Python however, the source code arguably IS the program - since that's what the user runs. Yes, we (as programmers) are aware that there is a difference between the python sources and what is actually run, but for the average user - this distinction is probably never made. To them, Python source code is the same thing as a python program. Albeit a program which won't run unless they go and acquire some GPL module.

However this is all obviously against the spirit of the GPL, and probably does infringe it anyway, but I think it's an interesting question.

---

### Post by nvteighen on 2008-10-02
> **Tomosaur said:**
> I was thinking about this the other day. I can't remember if I talked about it in the other 'confused about GPL' thread (you know, the billionth one? :P ).

I think it was in the 194567999th one :D

Anyway, I agree entirely with your post.

My doubt is what is included in Python's bytecode. If it only includes a reference to where the module is located (dynamic loading), or it actually includes a symbol and relocation tables from the module (dynamic linking) or the whole module itself (static linking).

If the bytecode just has the path where the module is located, then it's just a reference like the "import ..." statement which IMO, it doesn't constitute a derivative work. But, in the other cases, your bytecode would be a derivative work. Can someone please help us on that?

The spirit of the GPL is to preserve the freedom to share and modify some code. If I distribute some (restrictively licensed) Python source code that makes use of a GPL module, I'm not affecting the freedoms that GPL gives over that module's code. Even if I'm referring to functions located at that module, the references will just be that, references and not the module's code. I could write a non-GPL implementation complying to the same module's API (unless patented, of course) and interchange them without trouble... But, in the bytecode (if it doesn't rely on dynamic loading) you force the use of an implementation and make the imported module be effectively part of your program...

---

