---
title: "Ada?"
date: 2007-04-11
forum: Programming Talk
---

### Post by myquidproquo on 2007-04-11
I think that this is the time for me to start programing so I've started to research about c++. I've learned c ansi at school and I guess that c++ could be a good starting point.

While researching I've read about Ada. I had never heard about it before.

I don't find much information about it so I don't know if people use it. And don't know if I should learn it.

---

### Post by pmasiar on 2007-04-11
[Ada](http://en.wikipedia.org/wiki/Ada_%28programming_language%29) was supposed to be THE silver bullet, but is long time obsolete (unless you work for a military), because it came in just before [OOP](http://en.wikipedia.org/wiki/Object-oriented_programming) (it was added later - 10 years too late :-) )

Another [paradigm shift](http://en.wikipedia.org/wiki/Paradigm_shift) in programming is imminent: [dynamically typed](http://en.wikipedia.org/wiki/Dynamic_typing) languages will take over [agile](http://en.wikipedia.org/wiki/Agile_development) application development, and C/C++ will be used for libraries/low level infrastructure.

Edit:
Was: You are much better served by Python - easier to learn, read, scales well.
Now: 70% of application developers are  better served by [Python](http://en.wikipedia.org/wiki/Python_%28programming_language%29) ... :-)

Have a look at my wiki: [http://learnPython.pbwiki.com/HowToStart](http://learnPython.pbwiki.com/HowToStart)

---

### Post by phossal on 2007-04-11
Embedded systems programmers (and the military, as pmasiar mentioned) like ADA, if they're not using C or Assembly. Some people "in the know" prefer ADA. Pmasiar prefers Python for *everything*, I think, but he has admitted fairly recently he 'hangs out' at a pretty high level. Ada is an OO-Language - but different from C++.

---

### Post by pmasiar on 2007-04-11
I agree. Python is not a silver bullet either, it is NOT for everything - only for 70% of apps :-) myquidproquo never said what kind of programming, what kind of applications he is interested, so my guess is as good as yours.

Maybe in fact he is interested in military apps - how else he would ever known about ADA?

Last time when I tried to start a thread explaining that different languages are for different kind of apps, like we have different cars for different tasks, I was accused of inciting flamewar. :-(  

I still think it would be great to get a sticky explaining that there is NO silver bullet language in programming, and all these different  languages are here for a reason, every one best in its own niche, but I cannot afford getting another infraction for doing that. Any risk-takers? :-)

---

### Post by phossal on 2007-04-11
Pmasair likes wikipedia, I think. 

Here is a blurb: [http://en.wikipedia.org/wiki/Ada_programming_language](http://en.wikipedia.org/wiki/Ada_programming_language)
> Because Ada is a strongly-typed language, it has been used outside the military in commercial aviation projects, where a software bug can mean fatalities. The fly-by-wire system in the Boeing 777 runs software written in Ada. The Canadian Automated Air Traffic System (completed in year 2000 by Raytheon Canada) was written in 1 million lines of Ada (SLOC count). It featured advanced (for the time): distributed processing; a distributed Ada database; and object oriented design.

Many new programmers think of programming in very narrow terms - mainly for the desktop - but there are a handful of commercial products around the house that require a programmer or two to give them life. ;) Personally, I find the idea of programming my coffee pot exiting, and I enjoy learning about hardware. How much more so to work on live systems for an automobile or a jet. Awesome. Maybe Ada is useful learning if you see yourself doing such things.

If I were going to learn it, I would start here: [http://www.amazon.com/Programming-2005-International-Computer-Science/dp/0321340787/ref=pd_bbs_sr_2/102-0055398-2013727?ie=UTF8&s=books&qid=1176335276&sr=1-2](http://www.amazon.com/Programming-2005-International-Computer-Science/dp/0321340787/ref=pd_bbs_sr_2/102-0055398-2013727?ie=UTF8&s=books&qid=1176335276&sr=1-2)

---

### Post by samjh on 2007-04-11
> **myquidproquo said:**
> I think that this is the time for me to start programing so I've started to research about c++. I've learned c ansi at school and I guess that c++ could be a good starting point.

While researching I've read about Ada. I had never heard about it before.

I don't find much information about it so I don't know if people use it. And don't know if I should learn it.

Ada is a very strongly-typed and strongly type-enforced system programming language, originally designed for programming military computer systems.

It is still the #1 choice for military, aviation, high-risk industries, and space technology.  Its strongest competitor is Assembly!

Basic features are:
[list][*]Strong typing.
[*]Strong type-enforcement (as opposed to weak enforcement in C).
[*]In-build measures to guard against buffer-overflows and other common safety weaknesses in lower-level languages (as opposed to C and C++)
[*]Very fast execution speed (comparable to C++ and Pascal).
[*]Low-level hardware-centric features (similar to C and PL/1).
[*]Syntax which forces structured code layout for maintainability (similar to Pascal and Modula-2).[/list]

The de-facto official implementation of Ada is GNAT (sponsored by the US Air Force), which is in the Ubuntu repositories.  Wikipedia and other sources have good tutorials for learning the language.  If you are interested in getting into military, avionics, or other critial system (eg. nuclear power, space technology, air traffic control, etc.) programming, then Ada is a useful tool in your box.

---

### Post by xtacocorex on 2007-04-12
If you get into VHSIC Hardware Description Language (VHDL) for programming Field Programmable Gate Arrays (FPGA), it is very similar to ADA, which is how the US Government wanted it.

I can see ADA useful if myquidproquo is interested in hardware programming because the two syntax are almost identical.

---

### Post by myquidproquo on 2007-04-12
I just want to learn. For fun :D 

I'm studying electrical engineering and to date my favorite subjects was Microprocessors. It was more like computer architecture, I guess. The ALU and all that stuff :)

I think I will try C++ and have a look into Ada. Many people use C++ and it would be good for learning more about Linux, too.

---

### Post by bpcarlson on 2008-01-14
Ada can be a very useful language and will help extensivily with avoiding many common programming faults in c and c++. However, it can be rather frustrating and it is not used much any more. It is still used (and was primarily created) for safety critical and military applications. Indeed, I work for a defense contractor and we use it quite a bit. While I have found the language easier to use than c++, I have been very frustrated with the lack of quality books for Ada. There are many out there and, unfortunatly most of them suck!!!

On that note, does anyone know if Ubuntu comes with an Ada compiler (GNAT perhaps)?

---

### Post by wolfbone on 2008-01-14
> **pmasiar said:**
> [Ada](http://en.wikipedia.org/wiki/Ada_%28programming_language%29) was supposed to be THE silver bullet, but is long time obsolete (unless you work for a military), because it came in just before [OOP](http://en.wikipedia.org/wiki/Object-oriented_programming) (it was added later - 10 years too late :-) )

Hmm... obsolete eh? Thanks for the warning, pmasiar - I never much liked flying anyway ;-)


[http://www.adacore.com/2007/06/19/adacore-gnat-pro-chosen-for-uk-next-generation/](http://www.adacore.com/2007/06/19/adacore-gnat-pro-chosen-for-uk-next-generation/)

---

### Post by LaRoza on 2008-01-14
see my wiki, it has Ada on it.

I found the language to be easy to learn, but didn't fulfill my programming needs.

Ada can be expensive with its strict typing: [http://en.wikipedia.org/wiki/Ariane_5_Flight_501](http://en.wikipedia.org/wiki/Ariane_5_Flight_501)

---

### Post by LaRoza on 2008-01-14
> **pmasiar said:**
> 
I still think it would be great to get a sticky explaining that there is NO silver bullet language in programming, and all these different  languages are here for a reason, every one best in its own niche, but I cannot afford getting another infraction for doing that. Any risk-takers? :-)

I already suggested this, and even gave the content's basis as being my wiki's FAQ page: [http://laroza.pbwiki.com/FAQ](http://laroza.pbwiki.com/FAQ) (leaving out the stuff on me, of course)

Started thread, hoping for stickification: [http://ubuntuforums.org/showthread.php?t=667422](http://ubuntuforums.org/showthread.php?t=667422)

The "Suggestions for Beginners Sticky" somewhat fulfills your request.

---

### Post by pmasiar on 2008-01-14
> **wolfbone said:**
> Hmm... obsolete eh? Thanks for the warning,

I remember when in mid - '80ties Ada was touted as the ultimate language, first and last you will ever need, not unlike Java is treated now. Is Ada still used? Yes, it is, but so what? Plenty of old languages are still used (COBOL anyone :-) ) , but they failed to have  the promised impact. In this sense, it is obsolete: modern development underwent paradigm shift, first to OOP, and now to Agile/TDD, for which dynamically typed languages are more appropriate.

Of course, Ada was designed to be super-safe, not agile :-)

BTW, [requirement to use Ada](http://en.wikipedia.org/wiki/Ada_%28programming_language%29#History) was lifted in 1997, so even government realized that Ada is not a silver bullet.

In general, IMHO small group of smart hackers have better chance to develop "good" language (and test it immediately and improve/change) than a language designed by a committee. This is IMHO main reason why "open" languages like Perl, Python, Ruby became popular and successful even when competing with languages promoted by government mandate (Ada) or huge marketing budget by rich companies (Java, C#). Those "open" languages have to be really good, or nobody would even bother :-)

---

### Post by ThinkBuntu on 2008-01-14
> **pmasiar said:**
> I remember when in mid - '80ties Ada was touted as the ultimate language, first and last you will ever need, not unlike Java is treated now.
That would be '80s.

---

