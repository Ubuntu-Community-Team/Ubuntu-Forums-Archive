---
title: "Oh no! &quot;my language is bigger than yours&quot; all over again"
date: 2007-01-10
forum: Programming Talk
---

### Post by pmasiar on 2007-01-10
Yet another pissing contest which language is better. I can give you simpler task: **which car is better**? 
[LIST]
[*]**Toyota Camry** you say? ROFL LMAO how are you going to use it to stock local grocery shop, everyone knows trucks are for that you fool.
[*]**truck** you say? LOLOL you idiot let me see you commuting to your work in truck - and how you will park it? you have no clue whatsoever about cars you moron.
[/LIST]

See what I mean? It does not make sense to ask "which" language in general - **languages are specialized tools** - each specialized in their areas. They were designed to solve problems in some specialized areas, and are bad fit outside the intended area. Don't hammer the screw in - use screwdriver. We can discuss (1) how wide or narrow the area is, (2) how good fit language is for the intended area, (3) how area is changing and in (4) which direction, (5) what other contenders are emerging in each area. Talking about the superiority of one language over another without mentioning what is intended usage area is as stupid as above mentioned car comparison. For some reason foolishness of comparison of languages "in general" is less than obvious to some people :evil:

Lets look what we have:
[LIST]
[*]**Assembler**: copies processor architecture. But: processors implementing high-level languages are possible, like Forth and Lisp. So we will see.
[*]**C**: Layer on top on (traditional) assemblers. Almost as fast as Assembler, easier (but still rather hard) to code in. Couple hundreds of millions of lines of code was written in it, and that code will stay for very long time.
[*]**C++**: C with OOP. Slower than plain C, but helps manage big projects better. Same as C.
[*]**Java**: Goal was multiplatform high-level language like C++, but easier to code in, which you can distribute in binaries on many platforms. Now we are down to 2 platforms (GNU/Linux and Windows), and java created reimplementation of most features of both. MS has own java-like language (C#) and has lots of motivation to make life of java on windows uncomfortable. Linux has all the tools java reimplemented, and now as java is GPL can cherry-pick and integrate the rest. But additional abstraction layer java adds does not make any sense for GNU/Linux: we distribute sources, not binaries. So my position is, java is dead end like Cobol: target area evaporated.
[*]**C#**: MS own improved C++, competing with java. Although implementation for GNU platform exists (Mono), viability on other platforms is questionable (and certainly is NOT a goal for MS - quite the opposite, they see C# as tool for platform vendor lock)
[*]**Forth**: high-level language designed to run directly on stack architecture of CPU. Extremely compact and fast interpreter: champion for devices.
[*]**Perl**: flexible text processing and system administration. Designed to be very expressive and flexible, like a human language. Big part of what other languages have in libraries is included as part of language - so language was designed to be flexible to be able to ignore big parts of it. As a result - way too overflexible to be usable for big projects. Still great for quick one-off ten-liners for sysadmin work, if you remember all the quirks. Pioneered dynamic typing and scripting apporach in mainstream languages. Once was "duck tape of the internet", but losing mind-share. OOP was bolted on, and looks ogly.
[*]**Ruby**: Improved OOP Perl for web applications done right. Less quirky than perl, but you can feel perlishness. Popularity based on great web framework, Rails, which mainstreamed "conventions instead of configuration" approach. Rails did not invented [Model-View-Controller]("http://en.wikipedia.org/wiki/Model-view-controller") paradigm, but made it popular. Especially java programmers, for so long struggling with static typing and overconfigured frameworks, liked and hyped it.
[*]**Python**: Universal dynamically typed multi-paradigm OOP language optimized to be readable and easy to learn, yet great for RAD (Rapid App Development). Although it is great for text processing, for some time neglected web applications (giving opening to Ruby). Catching up big time now. 
[*]**PHP**: For creating web-pages by beginners. Because PHP does not know OOP, and low skill level of average coders, bigger projects gets really messy. Idea of "code within the web page" was reimplemented for most other languages (including java, VBasic, and even python: yes you can have "Active Python Pages").
[/LIST]
... and many more languages. Cobol, Fortran, PL/1, Ada, Pascal, Lisp, Erlang, Haskell, Logo, Smalltalk, Prolog, XSLT ... 8K+ of them.

So we have two big areas: 
**Low-level systems programming**, with clear winners: Asm and C in their respective areas, optimized for processing speed (NOT for productivity in application development). Question is, with increase of CPU cores, they might want to do something else in core, like implement Forth in core.
**Application development**, where productivity is important, and most important speed is "speed to market". In that area, as CPU speed increases and prices fall, dynamic typing and interpreters (vs. compilers) become very popular. In most areas of app development, Python is either a leading candidate, or good enough right now, with direction toward improving. In multiplatform deployment, java has currently slight edge - but NOT in productivity, and for the price being (1) staically typed (2) incompatible with the GNU application stack.

Ok enough for now - I can feel we will have heated discussion, but at least we will not compare apples to apes ;-)

---

### Post by laxmanb on 2007-01-10
OK... Java is incompatible with the GNU application stack... does that stay with the GPLing of Java??

---

### Post by laxmanb on 2007-01-10
And it's a lot better to have precompiled binaries!! compiling from source is not easy and would hinder the growth of any OS in the average home user area...

---

### Post by yaaarrrgg on 2007-01-10
I generally agree, except for your conclusion about Java and C#.... the additional layer of abtraction is here to stay.  Even Python's interpretor somewhat resembles a virtual machine nowadays.

---

### Post by Tomosaur on 2007-01-10
Abstraction is a good thing in many cases. Good coding practice actually encourages abstraction, as does OO programming. There is no sense tying one part (module) to another part. Parts of a system should communicate as little as possible except when communication is the purpose of the system. The vast majority of OOP projects should strive for modularity. Reuse is another common goal, but is rarely achieved since most projects require some specific ability which cannot really be applied in other projects. This 'abstraction is bad' idea is misleading. I approve of the Java requirement for a virtual machine. Not only does it help to ensure things cannot go wrong at a very low level, which can lead to severe damage, it also improves compatibility with other systems, despite their architecture. An extension to a Java program on one platform can be applied to the same program on a different platform.

The same can be said about python, but because python is so flexible, it hinders its own development. Any discussion about coding in python normally ends up in 'well I prefer this way'.  This slows development on large projects, and thus python is rarely seen being applied to anything 'big'. It also requires an interpretor - but its ability to function 'live' is a major improvement over Java's JIT compiler.

C# is just horrible in my experience, I'm not going to get into it but it just seems to be different for the sake of being different rather than actually improving on Java.

---

### Post by Sasa_Ivanovic on 2007-01-10
What are you saying ? That Java will die 'cause it distributes binary's. Well you can package *.java in jar.
And just the fact that you can easily run java app anywhere without compiling stuff is good.
Also Sun JRE rules!

---

### Post by pmasiar on 2007-01-10
> **laxmanb said:**
> OK... Java is incompatible with the GNU application stack... does that stay with the GPLing of Java??

GPL-ed java still cannot run under Apache, use GTK or Qt for GUI and link to C libraries. Only minor licence change, nothing substantial. And I cannot see anybody investing loads of time to improve the situation. C++ is good enough, and works with GNU.

The only difference is: java is now easier to distribute, and interesting parts of GPL libraries can be cherry-picked and moved to GNU stack.

> **laxmanb said:**
> And it's a lot better to have precompiled binaries!! compiling from source is not easy and would hinder the growth of any OS in the average home user area...

Distributing application in binaries... Yet another problem where community-developed solution (Linux distro) is way better than solution invented by huge rich corporation. As Ubuntu user, you might be aware that **all linux distros can distribute compiled C/C++ binaries**  :-) Look mom, no java!

But you are again comparing apples to apes. Having compiled binaries is better because....? what exactly? What is your goal? Yoi like wait for your app to compile? Compiling allows you to develop application faster? 

Which "fast" do we talk about? "speed to market" ? Is it fast application development?

Neither Java nor C++ nor C# are [agile ]("http://en.wikipedia.org/wiki/Agile_software_development") enough for [RAD]("http://en.wikipedia.org/wiki/Rapid_application_development"). Python or Ruby are way faster and leaves all in the dust. Java is used for web development - but you might be aware how text processing in Java sucks - big time. 

Did you ever tried to parse a file using some scripting language, so you have at least a little clue what are you talking about? What your competitors can do? Do you bother to base your beliefs on facts?

Sorry for flames - nothing personal agains you. This discussion is repeating every week, same arguments. If anybody can link previous discussions, please do so - I need to go back to my java/struts I hate so much... :-(

---

### Post by pmasiar on 2007-01-10
> **Sasa_Ivanovic said:**
> Also Sun JRE rules!

Another gem - another well-researched and documented fact from the well-known expert. Yeah, now I see error in my ways.  I wish I was as smart as you are. :evil: 

Your position is (not here, but in most of your other posts): Why bother with thinking if i can vomit my narrow-minded prejudices. Listening to what my oponent has to say is for n00bz  ](*,)

---

### Post by Sasa_Ivanovic on 2007-01-10
Java isn't only for web development. The fact is that everyone use it for web dev, but it can do much more.

Java is the only language that aims to be programmer friendly.
Do you wan't to be a slave of all the dark corners of C ? Or would you rather type 10101110 to gain some speed ?

If Java was as fast as tutrtle i would still use it.

---

### Post by Sasa_Ivanovic on 2007-01-10
> **pmasiar said:**
> Listening to what my oponent has to say is for n00bz  ](*,)

I'm not the one saying that. I listen to everyone, just that rarely anyone is aware of Java power! So it seems i'm not listening to ya, but it's the other way around.

---

### Post by laxmanb on 2007-01-10
Precompiled binaries are a good thing bcoz the average joe user will probably find it difficult to compile from source... i can tell u... i had a lot of trouble to successfully compile a single program(It was ZSNES, i think).... apt-getting is a lot better...

...Source gives you freedom to modify... but how many of us(All computer users) use that freedom??

---

### Post by meng on 2007-01-10
As pointless as it is to argue over which programming language (or desktop environment or operating system) is better, it is also somewhat pointless to attempt to avoid such arguments! People love their language/DE/OS/football team and will not think twice about jumping into a heated discussion about which is the best.

---

### Post by Sasa_Ivanovic on 2007-01-10
> **meng said:**
> As pointless as it is to argue over which programming language (or desktop environment or operating system) is better, it is also somewhat pointless to attempt to avoid such arguments! People love their language/DE/OS/football team and will not think twice about jumping into a heated discussion about which is the best.
that's true. I'm ready to die for Java.

---

### Post by meng on 2007-01-10
> **Sasa_Ivanovic said:**
> that's true. I'm ready to die for Java.
Yes, I think you made that very clear!!

---

### Post by Tomosaur on 2007-01-10
I hate language evangelists. Just pick whichever one is best for the job. It makes absolutely no sense to hold one language above all others. Each language has advantages and disadvantages - there's no 'correct language' to use. I like Java because it makes it easy to do the things I need to do, but there's still things which irritate me about it, and it's API is occasionally illogical and badly documented. Python is great for getting something done fast, and is arguably more object oriented than Java. Most of the time I just use shell scripts if it's quicker than coding.

---

### Post by pmasiar on 2007-01-10
[Expert Panel on Languages]("http://www.traceback.org/2007/01/10/expert-panel-on-languages-at-codemash/") At [CodeMash]("http://www.codemash.org/") Held January 18-19, 2007 at the lush  Kalahari resort in Sandusky, Ohio.

There will be an expert panel on languages Wednesday night before the conference begins. [Bruce Eckel]("http://en.wikipedia.org/wiki/Bruce_Eckel") will be moderating. His best known works are Thinking in Java and Thinking in C++.

Could be expensive but you Ohioans might be able to sneak in. Good luck!

---

### Post by Wybiral on 2007-01-10
> that's true. I'm ready to die for Java.

That doesn't make any sense, and it doesn't enlighten me to use Java. It tells me that you have it stuck in your mind to use it no matter what you find out or what anyone says. C++ and Java bare remarkable similarity, but C++ programs don't require the VM or the JIT. So when you can compile for the major platforms, why use Java over C++

I'm not saying that C++ is better... I'm just raising some questions.

As for portability - I believe Java was written in C... Notice how the JRE has been implemented in all of the big platforms? You can do the same with your C programs by being smart about your libraries use and cross compiling for the major platforms.

As for speed - As for speed... "Speed to market" as pmasiar argues so much, C and C++ are just as easy to program in as Java. And being compiled to native machine code is always faster, I don't want to start a flamewar, but it's true. Java's JIT compiler actually does more damage than good be gobbling up all of the CPU that the program could use.

As for memory management - Everyone argues about garbage collection and memory management, any decent C/C++ programmer knows how to handle these things on their own. Not to mention that most programs wont even require any special cleanup, plus there are good libraries for C and C++ that solve these problems.

Still, I'm not saying C++ is better than Java, but C and C++ can definitely compete with Java...

---

### Post by PriceChild on 2007-01-10
"Oh my language is better than yours" will get you no-where in this life.

Please spend the time you would normally be pointlessly bickering, on something useful, like programming that killer app... maybe then your choice of language would be noticed and respected more.

*Thread closed*

In this world everyone is free to program using whatever tools they desire, and without the requirement to defend their choice.

---

