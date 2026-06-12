---
title: "Why is it that eclipse cdt sucks *** so bad in contrast to eclipse for java?"
date: 2009-03-31
forum: Programming Talk
---

### Post by Alcareru on 2009-03-31
Well, to tell you the truth I suppose I have a pretty good idea of it my self. Eclipse was built originally as a java IDE (afaik) so the support is better and java is less complex language than c++. But still... I'm just wondering that how do you all C++ coders out there live with these crappy IDEs? It's such a huge shock.. when writing java applications it's more like I just press ctrl + 1 and eclipse does the code writing for me. With c++ I might get code completion, but the IDE has so far never been able to correct even a simple one leter misspellings or anything. It never gives any suggestions.

Also I had great difficulties adding GTKmm-library to my project. Do I really need to add all dependencies one by one, BY HAND to my project for the compiler? And in addition add them all again for the linker? That's ridiculous!

Any good tips for a java programmer to settle in to the awkward world of c++?

---

### Post by CptPicard on 2009-03-31
> **Alcareru said:**
> Eclipse was built originally as a java IDE (afaik) so the support is better and java is less complex language than c++.

Yes, C++ grammar is much more complex to parse and analyze than Java's. Add to that the fact that the Java compiler itself can be run programmatically by the IDE so that all errors are exact and not parsed and guessed from g++'s output. And that even running Java code can be examined.

A yet further complication is the header/implementation distinction. In Java you have essentially one file per class, and that's it.

> But still... I'm just wondering that how do you all C++ coders out there live with these crappy IDEs?

Try Netbeans or Code::Blocks. I've been happier with them for C/C++ than I have been with CDT.

But generally, just learn to write Makefiles and learn a good text editor and use that. That's the way it works over here, and you'll want to get those skills anyway even though you may end up using an IDE in the long run.

---

### Post by Gordon Bennett on 2009-03-31
No problems here - and I'm writing plus debugging pretty hardcore (C-based) realtime video processing apps and server daemons with it.

In fact it is one of the best C IDE's I've ever used, along with CodeWarrior.

---

### Post by Alcareru on 2009-03-31
> **CptPicard said:**
> 
Try Netbeans or Code::Blocks. I've been happier with them for C/C++ than I have been with CDT.

Well, I tried NetBeans and it don't seem much different. Some things were a bit better and some things were not. It certainly wasn't significantly easier to configure. I have also tried Code::Blocks some time ago, but if I remember right it didn't bring in any significantly better features, when in contrast to java based NetBeans and Eclipse, it seemed immature project and kept crashing periodically. Sure it was a bit quicker for not being java based, but I'm not coding with a Intel 286, so I don't care if java is a bit of resource hog :p.

> **CptPicard said:**
> 
But generally, just learn to write Makefiles and learn a good text editor and use that. That's the way it works over here, and you'll want to get those skills anyway even though you may end up using an IDE in the long run.
I know and I do know the basics of that. I've done a bit more than just helloworld with c++ already :). The thing is just that, I hate the Makefiles. They are a bit like bash. The syntax is unnecessarily cryptic and awkward (though with bash you can usually choose not to write cryptic scripts). A legacy system form the stone age, when someone could actually benefit something from not having to type sensible words or phrases as commands, but instead some mystical magic characters that are in no way self-explanatory.

Anyways, the makefiles I've had to do as of so far have been more or less simple tasks and easily manageable, but I've seen makefiles from bigger projects and they just look like a big bloat of mess. My becoming makefile will not be so simple as I have plans for a much larger project. If I could just somehow avoid the task of having to deal with makefiles and more importantly manage them as the dependencies change, code gets re-factored etc. that would be super.

P.S. It seems I might have found the answer for my prayers. JAM! Anybody has any thoughts on that matter? Good tips and experiences from using jam? Or perhaps you can (try) to convince me to stick with the good old make. What about jam and eclipse? How do they come along?

---

### Post by Alcareru on 2009-03-31
> **Gordon Bennett said:**
> No problems here - and I'm writing plus debugging pretty hardcore (C-based) realtime video processing apps and server daemons with it.

In fact it is one of the best C IDE's I've ever used, along with CodeWarrior.

That's what I was afraid of.. :) It's a good thing if it works for you. Might you have any tips for me, though your working with C and I'm more interested with C++?

---

### Post by sujoy on 2009-03-31
The big messy makefiles you see in large projects are not written manually.
normally you write an autoconf input file that generate a configure script. and you write an automake input file that generates Makefile.in

That configure script is what finally generates the big messy Makefiles, since it has to do lots of checking for making it portable across all Unix (based) systems.

If you want to deploy applications in the linux/unix world, Makefiles are standard stuffs.

---

### Post by Alcareru on 2009-04-01
> **sujoy said:**
> The big messy makefiles you see in large projects are not written manually.
normally you write an autoconf input file that generate a configure script. and you write an automake input file that generates Makefile.in

That configure script is what finally generates the big messy Makefiles, since it has to do lots of checking for making it portable across all Unix (based) systems.


I'm still the process of acquiring information about automake and autoconf, but it seems they are probably not what I'm looking for.

> **sujoy said:**
> 
If you want to deploy applications in the linux/unix world, Makefiles are standard stuffs.
Yes, I know. And I couldn't care any less. I will have "the pleasure" to work with them more than enough. I'm sure you all make sure of that, but on my very own project, I make the rules and I don't have to use an ancient build system just because use it.

---

### Post by CptPicard on 2009-04-01
One other build tool you may want to check out is Scons, being a python hacker among other languages, I quite like it.

---

### Post by Yacoby on 2009-04-01
> **Alcareru said:**
> I have also tried Code::Blocks some time ago, but if I remember right it didn't bring in any significantly better features, when in contrast to java based NetBeans and Eclipse, it seemed immature project and kept crashing periodically. Sure it was a bit quicker for not being java based, but I'm not coding with a Intel 286, so I don't care if java is a bit of resource hog :p.

I found code::blocks quite good (with plugins). The SVN builds ofc, the "stable" builds are about a year out of date. It still crashes every now and again, but no exactly regularly, more like once a month. (I haven't lost any code from a crash either)

It now has a profiler, memory leak checker, wx GUI editor (although I don't like it hugely compared to some others) and code completion. Some bits aren't as good as Visual C++ with Visual Assist X.... Yet. I am just hopeing the llvm c/c++ compiler is releasable soon.

---

### Post by Alcareru on 2009-04-01
> **Yacoby said:**
> code::blocks this and that...
Since your the second to recommend it I suppose I have to re-evaluate the usability of that IDE before I make any final decisions about the IDE I'm going to use.

@CptPicard
I've also bumped into scons and found it interesting. I'm also looking into ant. I'm a big fan of xml-files so that part of it seems promising. Though, as all who have heard of ant know it's number one use is to be a build tool for java and it's support for other languages is...? Well, there is ant-conrtrib that should enable building c/c++, but the project web page isn't quite as informative as I'd hope.
[http://ant-contrib.sourceforge.net/](http://ant-contrib.sourceforge.net/)

---

### Post by Gordon Bennett on 2009-04-01
> **Alcareru said:**
> That's what I was afraid of.. :) It's a good thing if it works for you. Might you have any tips for me, though your working with C and I'm more interested with C++?

Indeed, C++ is a very different beast!  However, it may be worth browsing Eclipse plugins/addons, via the menu 'Help->Software Updates...->Available Software', there may be something there more relevant to what you need in an IDE.

With Eclipse and C/C++ what most do these days is use the Ganymede CDT version (not the full bloat one) and then add any other plugins for a lean and mean system.

However, as mentioned by other posts I have also heard good things about Code::Blocks, so if Eclipse can't offer what you seek, have a go at that too - IDE's are a bit like a pair of pants; if they don't fit, try another pair :D

---

### Post by Alcareru on 2009-04-04
Lately I've been a bit busy and have not been able to spend as much time to tinker with this as I would have liked. As of so far I've looked into 3 options:
- SCons, seems ok, but I dunno.. there's something fishy about it :) I suppose I have to digg a bit further.
- Jam and Boost.Jam, the fact that the c++ coders at Boost have adopted this system makes me think it might suit very well for c++ projects. Then again. though the files seem smaller than makefiles they look a lot like makefiles.
- I've also looked into ant. It seems as nice as one could expect from xml-based system. Files are long but self-explanatory. Though all of these actually had plugins for eclipse (even jam.boost, though you have to compile it your self) I bet ant has the best support..

I'll get back to this later..

---

