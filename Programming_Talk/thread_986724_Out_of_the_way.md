---
title: "Out of the way"
date: 2008-11-18
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-18
i enoy learning those lesser known out of the way or old languages...any suggestions?

---

### Post by slavik on 2008-11-18
forth, algol60, pascal

---

### Post by cabalas on 2008-11-18
Cobol - I'm told cobol programmers are worth their weight in gold these days.

---

### Post by gpsmikey on 2008-11-18
Froth - a Forth like language that was around for a while for the PC - not sure if it is still out there.  Forth is a good one though - easy to implement on small 8 bit micros for doing various "gadget" type things.  Z-80 assembler was always fun -- I still remember quite a few of the opcodes (hex or octal). :)
We actually had (still do actually) a forth interpreter in many of our avionics boxes that was available during bench testing (disabled for flight conditions).

mikey

---

### Post by pgatrick on 2008-11-18
Ada, Common Lisp.. :)

---

### Post by Sinkingships7 on 2008-11-18
Common Lisp.

---

### Post by slavik on 2008-11-18
I wouldn't say that Ada and CL are out of the way exactly ...

---

### Post by Sorivenul on 2008-11-18
* [Occam]("http://en.wikipedia.org/wiki/Occam_programming_language")
* Modula-2 and/or Modula-3
* [Sather]("http://en.wikipedia.org/wiki/Sather") (Not quite as old)

---

### Post by dekeller on 2008-11-18
If you want to go really old school, PL/1 or APL would get you there.  PL/1 was a Pascal like language before Pascal was around with strong typing and a compliler that would spit out a million lines of error messages if you forgot one ; at the end of a statement.  APL was a math language were every variable was assumed to be a vector or an array.  It also had a ton of matrix algebra operators that other languages do not have.  Also, it scanned from
right to left.  While it was not a good thing, it was possible to write a program of 6 or 7 lines of code that would take someone else 2 weeks to a month to work through or debug.

Darryl Keller

---

### Post by samjh on 2008-11-19
> **slavik said:**
> I wouldn't say that Ada and CL are out of the way exactly ...

Common Lisp isn't really out of the way, as a lot of programmers have been exposed to at least one dialect of Lisp.

Ada is really out of the way if you learned to program post-80s and 90s.  Hardly anyone knows the language these days.

@ OP

For really wacky languages, just see here: [http://en.wikipedia.org/wiki/Category:Esoteric_programming_languages](http://en.wikipedia.org/wiki/Category:Esoteric_programming_languages)

---

### Post by sjbaugh on 2008-11-19
There were two other Algol60 (the first language I learnt) based languages: Coral66 and Algol68. I have also written in a predecessor of C: BCPL.

---

### Post by shadylookin on 2008-11-19
Cobol and I've heard you can make some money maintaining old mainframes with it as well

---

### Post by sjbaugh on 2008-11-19
> **shadylookin said:**
> Cobol and I've heard you can make some money maintaining old mainframes with it as well

open-cobol is in the Ubuntu repositories so that could be a good candidate. It is certainly quite different to modern languages.

Steve

---

### Post by slavik on 2008-11-19
> **samjh said:**
> Common Lisp isn't really out of the way, as a lot of programmers have been exposed to at least one dialect of Lisp.

Ada is really out of the way if you learned to program post-80s and 90s.  Hardly anyone knows the language these days.

@ OP

For really wacky languages, just see here: [http://en.wikipedia.org/wiki/Category:Esoteric_programming_languages](http://en.wikipedia.org/wiki/Category:Esoteric_programming_languages)
I still disagree. Look at the aviation industry. Pretty much all critical software (in the Control Tower and on Planes) is written in Ada.

---

### Post by jimi_hendrix on 2008-11-19
thanks all these look interesting

---

### Post by jimi_hendrix on 2008-11-19
these arnt exactly out of the way...but what would you recommend, MATLAB or Octave...i think either would come in handy for math class

---

### Post by jimi_hendrix on 2008-11-19
only problem with old langauges is lack of tutorials...

---

### Post by snova on 2008-11-19
Probably Octave. MATLAB is proprietary, Octave is the open source equivalent. (There are more, it appears.)

[QUOTE=Wikipedia]Octave is a free computer program for performing numerical computations which is mostly compatible with MATLAB. It is part of the GNU Project.[/QUOTE]

---

### Post by jimi_hendrix on 2008-11-19
if anyone knows any tutorials for those really archaic (algol) languages then feel free to share

octave is fair game too

@snova by proprietary do you mean closed source or pay money for

---

### Post by Cracauer on 2008-11-19
Intercal :)

If you think GOTO is bad you haven't seen COMEFROM.

In more serious news, Prolog might be a good different experience. Smalltalk is dead enough by now to count, is it? Didn't measure heartbeat lately.

---

### Post by Cracauer on 2008-11-19
> **jimi_hendrix said:**
> if anyone knows any tutorials for those really archaic (algol) languages then feel free to share


Archaic Algol language? [No problem](http://www.cplusplus.com/doc/tutorial/)

---

### Post by snova on 2008-11-19
I don't know, I've never tried MATLAB or any variant. All I know is that on the Wikipedia page it says it's under a proprietary license.

It appears to run on Linux, though... (only based on the description under the screenshot! Don't take my word for it.)

I can't tell whether you have to pay for it or not. It won't let me see pricing without logging in.

[http://www.mathworks.com/products/matlab/pricing_licensing.html?tab=student](http://www.mathworks.com/products/matlab/pricing_licensing.html?tab=student)

So it appears to be both, although it might depend on the license...

(How quickly I get used to free software!)

---

### Post by samjh on 2008-11-19
I doubt you'll find an ALGOL compiler for Linux (or at least on Ubuntu).  There are plenty of ALGOL-based languages, but I haven't come across ALGOL itself in any FOSS project.

For Ada, my post in this thread: [http://ubuntuforums.org/showpost.php?p=2914903](http://ubuntuforums.org/showpost.php?p=2914903) contains lots of introductory info and links to online resources.  "Hello Ubuntu" in every programming language - the first example is in Ada: [http://ubuntuforums.org/showthread.php?t=497579](http://ubuntuforums.org/showthread.php?t=497579)

There is also Pascal: [http://ubuntuforums.org/showpost.php?p=2061629](http://ubuntuforums.org/showpost.php?p=2061629)

---

### Post by Gilabuugs on 2008-11-19
Matlab is a bit over 100US for a student license and a few grand for a commercial version, octave has a lot of the functionality that matlab has and even a large amount of the commands

if you go for one of those choose octave and maybe move up to matlab if you feel you want to

---

### Post by jimi_hendrix on 2008-11-19
ok ill do octave...now to explore some of these languages...

---

### Post by jimi_hendrix on 2008-11-19
@samjh

after looking at your pascal post i say the forum should start a library of "how to get started in <language>"  for some of the lesser known languages (ie tutorials and what compiler/interpereter/any ide's or editors that support it)

---

### Post by jimi_hendrix on 2008-11-19
> **Cracauer said:**
> Archaic Algol language? [No problem]("http://www.cplusplus.com/doc/tutorial/")
...

---

### Post by jimi_hendrix on 2008-11-19
anyone got smalltalk tutorials hidden away somewhere?

---

### Post by cabalas on 2008-11-19
> **jimi_hendrix said:**
> anyone got smalltalk tutorials hidden away somewhere?

You should have a look at [squeak]("http://www.squeak.org/") which according to their website is: 

> Squeak is a modern, open source full-featured implementation of the powerful Smalltalk programming language and environment. Squeak is highly-portable - even its virtual machine is written entirely in Smalltalk making it easy to debug, analyze, and change. Squeak is the vehicle for a wide range of projects from multimedia applications, educational platforms to commercial web application development. 

and seem to have a reasonable amount of tutorials: [http://www.squeak.org/Documentation/](http://www.squeak.org/Documentation/)

---

### Post by samjh on 2008-11-19
> **jimi_hendrix said:**
> @samjh

after looking at your pascal post i say the forum should start a library of "how to get started in <language>"  for some of the lesser known languages (ie tutorials and what compiler/interpereter/any ide's or editors that support it)

[http://ubuntuforums.org/showthread.php?p=2061629](http://ubuntuforums.org/showthread.php?p=2061629) ;)

---

### Post by jimi_hendrix on 2008-11-19
i cant decide which to go with...

---

### Post by CptPicard on 2008-11-19
Go with Lisp. The other languages are dead for a good reason, Lisp is alive and strong simply because it got stuff right to begin with.

---

### Post by jimi_hendrix on 2008-11-20
which dialect?

---

### Post by elbarto_87 on 2008-11-20
I mainly use Matlab for my bigger engineering projects as its what I first used and what I am confident with. I found octave to be pretty similar, but my in my opinion matlab "just works". Yes its proprietary software, and my student cost me $100 (under 1/30th of the full price) and it is excellent for what it does. 

Out of all the free alternatives, scilab is probably the nicest language that's free that does matlab style programing (in my opinion). I think python with numpy is also an exelent choice which I hope to get more familiar with, but I read elsewhere that you do not like the idea of python so I wont go into that to much?

Matlab is about the only language that I have enough practice in (although not heaps) to make any useful comments on. What projects are you intending to use matlab/octave for?

Elbarto

---

### Post by pmasiar on 2008-11-20
> **CptPicard said:**
> Go with Lisp. The other languages are dead for a good reason, Lisp is alive and strong simply because it got stuff right to begin with.

Forth is also alive (used for drivers) because nothing can beat in in that area, including C.

---

### Post by nvteighen on 2008-11-20
> **jimi_hendrix said:**
> 
@snova by proprietary do you mean closed source or pay money for

Strictly talking, proprietary means "closed source", not commercial. There is free (=gratis) proprietary software (Freeware) and there's also commercial Free Software like Red Hat Enterprise Linux and the earliest versions of Emacs which Stallman had to sell in order to keep living.

But, usually, people associate the terms "proprietary" and "commercial" because it's the most usual fashion (MS Windows, Antivirus software, whatever).

> **pmasiar said:**
> Forth is also alive (used for drivers) because nothing can beat in in that area, including C.

I also recommend you Forth. Probably you won't ever do anything serious with it (unless you get into drivers programming), but it's quite fun, as it is a structured-procedural language (like C) but stack-based. It also had some Lisp influence on the fact that the compilation process is part of the same language (you can disassemble any function using the 'see' procedure).

If interested, install the gforth package in Ubuntu. And also look at: [GForth's Manual]("http://www.complang.tuwien.ac.at/forth/gforth/Docs-html/") (though it's intended to be a manual, it also serves as a tutorial). And [This beginner's guide to Forth]("http://galileo.phys.virginia.edu/classes/551.jvn.fall01/primer.htm") (it mentions to be referred to Win32Forth. Don't worry, that's the Windows port of GForth)

---

### Post by JohnFH on 2008-11-20
ML - a great functional language that requires a different programming mindset.

[http://www.dcs.napier.ac.uk/course-notes/sml/manual.html]("http://www.dcs.napier.ac.uk/course-notes/sml/manual.html")

[http://www.cs.cmu.edu/afs/cs.cmu.edu/project/fox/mosaic/sml.html]("http://www.cs.cmu.edu/afs/cs.cmu.edu/project/fox/mosaic/sml.html")

---

### Post by drubin on 2008-11-20
> **slavik said:**
> forth, algol60, pascal

Pascal is not old  and lesser known :)
I suggest learning Binary. or assembler.<< Teaches you memory management like you have never seen it before.

---

### Post by Cracauer on 2008-11-20
> **jimi_hendrix said:**
> which dialect?

If you gonna try Lisp, go with Common Lisp. Use SBCL, SLIME and Peter Norvig's book. Your programming brain will never be the same.

I can't recommend Scheme. I wasted too much time on that toy back in the 1990ties and won't put anybody else through it. The only use is if you go on a mission to work through SICP cover to cover.

---

### Post by CptPicard on 2008-11-20
Calling Scheme a toy is a bit harsh... it's meant to be a minimal Lisp that demonstrates what exactly are the required primitives to get a programming language. It's meant to enlighten, not necessarily be a "practical tool", and IMO it does it very well.

Common Lisp is much more complex because it's meant to be practical ... but that results in annoyances such as the function/value namespace difference.

If "learning lisp" is the goal, time spent on Scheme is not wasted. Most of the stuff, in particular the design mindset, transfers as is to CL.

And oh yeah, Scheme has continuations built in... I really miss a "yield" generator statement in CL (and no, I haven't seen a decent macro hack for that yet) :)

---

### Post by pmasiar on 2008-11-20
Assembly is fine language to know too.

BTW simplest way to play with ASM is inside Forth, because Forth provides interactive shell, and includes ASM: any word ("function") can be programmed in Forth or ASM, as you wish.

---

### Post by nvteighen on 2008-11-20
> **Cracauer said:**
> 
I can't recommend Scheme. I wasted too much time on that toy back in the 1990ties and won't put anybody else through it. The only use is if you go on a mission to work through SICP cover to cover.

Toy? Ok, it's not the most suited language for production software (because of lack of libraries... though there are the SLIB and SRFI projects...), but if you "play" with it, you can get some interesting ideas... see my sig.

---

### Post by jimi_hendrix on 2008-11-20
great suggestions...i would not chose ASM because its too hardware specific...

---

### Post by Reiger on 2008-11-20
MIT/Scheme is useful if only because it has reasonably wide support as a 'scripting language'; think GIMP's script Fu, which really is just a scheme lingo welded onto a GIMP/GTK C++ layer.

Similarly, MIT/Scheme has been ported to the Java platform as well, making this the (IIRC) only Lisp-ish language available there -- apart from through the Proccess class 'backdoor' + interpreter.

If out of the way can be defined as easily as 'not Algol-like'; then virtually every language which doesn't *look* like C done differently can be included. One could, on that basis, even argue Python should be counted in; though we are on a much more solid footing with Haskell or ML (or derivatives) even though these are going rather strong 'in the industry'.

---

### Post by jimi_hendrix on 2008-11-20
ive got no problem with algol if i can find a compiler and tutorial

---

### Post by CptPicard on 2008-11-20
> **Reiger said:**
> 
Similarly, MIT/Scheme has been ported to the Java platform as well, making this the (IIRC) only Lisp-ish language available there -- 

"The" lisp for the JVM is Clojure... it is a nice one, too.

---

### Post by Envergure on 2008-11-20
Brainf*ck, Shakespeare.

For real, Processing.

---

### Post by Cracauer on 2008-11-21
> **Reiger said:**
> MIT/Scheme is useful if only because it has reasonably wide support as a 'scripting language'; think GIMP's script Fu, which really is just a scheme lingo welded onto a GIMP/GTK C++ layer.

Similarly, MIT/Scheme has been ported to the Java platform as well, making this the (IIRC) only Lisp-ish language available there -- apart from through the Proccess class 'backdoor' + interpreter.

If out of the way can be defined as easily as 'not Algol-like'; then virtually every language which doesn't *look* like C done differently can be included. One could, on that basis, even argue Python should be counted in; though we are on a much more solid footing with Haskell or ML (or derivatives) even though these are going rather strong 'in the industry'.

What? GIMP's Scheme evalutator is definitely not MIT Scheme. It uses SIOD.

I also don't see MIT Scheme being ported to the Java JVM either, that's Kawa.

All these Scheme have different and incompatible libraries. That's what makes them toys.

---

### Post by nvteighen on 2008-11-21
> **Cracauer said:**
> 
All these Scheme have different and incompatible libraries. That's what makes them toys.

That's because of the anarchy that rules everything in the Lisp world. But I don't see Scheme just as a toy... of course it's not meant for professional software (because of the implementations incompatibilities and the lack of bindings to librarie) but it does allow you to do interesting projects, although with a different development process (not creating applications, but rather languages to solve some task and then use the interpreter as your language's interpreter!)... Take a look at [Savannah]("http://savannah.gnu.org") and search for Scheme.

---

### Post by CptPicard on 2008-11-21
As I said before, Scheme is meant to be an educational, academically enlightening Lisp. It plays that part well, without tangling the programmer up in complexities of a more "complete" implementation. Libraries really are irrelevant in this context, it's all about the core language.

The best part of course is that you can get your enlightenment in Scheme and still you have just gained from it if you choose to move over to something like Common Lisp. In particular, for a beginner, I would not recommend Common Lisp straight away... there is way too much baggage when you're just trying to understand what it all is about.

---

### Post by Reiger on 2008-11-21
> **Cracauer said:**
> What? GIMP's Scheme evalutator is definitely not MIT Scheme. It uses SIOD.

Never said it did. Said GIMP's Script-Fu thing is "just a scheme lingo welded...", which means you should've read that bit a little more closely.

Now as for:
> I also don't see MIT Scheme being ported to the Java JVM either, that's Kawa.

[https://scripting.dev.java.net/](https://scripting.dev.java.net/)

Which mentions "Scheme", and mentions the MIT people behind the language itself. Of course that doesn't automatically render it *MIT* Scheme, that's right. Point is here that MIT/Scheme *or one of its derivatives* has been ported...

---

### Post by Cracauer on 2008-11-21
You make good points and I'm the last one to say that Common Lisp isn't a mess. Lots of stuff that could have been packaged with same functionality in 1/3rd the size.

However, not only does Common Lisp come with a large ANSI standard library which contains most tools you need for implementing algorithms (as opposed to system stuff like threads, graphics etc), as opposed to Scheme.

You have real repositories of portable libraries for Common Lisp these days, of libaries that run on most OpenSource implementations. CLOCC is an example.
[http://clocc.sourceforge.net/](http://clocc.sourceforge.net/)

Many  of these projects are also portable:
[http://common-lisp.net/projects.shtml](http://common-lisp.net/projects.shtml)

The next problem is that all of today's OpenSource Common Lisp implementations are compilers. Many are native code, some via-C, some bytecode machines. That's as low as it gets.

In the Scheme world you often have interpreters compared to which even Python and Ruby look like a F-16.

That's fine as long as your goal is to learn fundamentals of programming, e.g. by working through SICP.

But it is not fine to discover that your -say- string pattern matching runs a factor of 500 slower than in SBCL and is actually slow enough that you can't get through your real-world input files. And these numbers aren't far off the truth.

---

### Post by CptPicard on 2008-11-21
> **Cracauer said:**
> That's fine as long as your goal is to learn fundamentals of programming, e.g. by working through SICP.


Which is sufficient enough. Most of the really interesting stuff I learned in programming came from Lisp-as-Scheme. I apply that stuff all the time all kinds of languages, although I certainly do use Common Lisp as my "practical Lisp"... I still hope that it a) had call/cc and b) was a Lisp-1. Being able to invoke a function in function position from a variable is cool, although probably not as easily compilable.

The fact that SBCL and pals are compilers are, from a practical standpoint, of course a good thing. Personally I am really looking hard at Qi these days...

---

### Post by jimi_hendrix on 2008-11-21
i seem to start arguments wherever i go

---

### Post by jimi_hendrix on 2008-11-21
forget this post

---

### Post by nvteighen on 2008-11-22
> **jimi_hendrix said:**
> i seem to start arguments wherever i go
Well, this at least is an reasonable and rational argument. Not an emotional and irrational flamewar.

---

### Post by drubin on 2008-11-22
> **jimi_hendrix]i seem to start arguments wherever i go [/QUOTE]

Such is the topics you bring up. Not that this is a bad thing. Challenges other to think.

[QUOTE=nvteighen said:**
> Well, this at least is an reasonable and rational argument. Not an emotional and irrational flamewar.

I am surprised how well this thread has actually carried on. Think we as a community are becoming more tollerent of other languages?

---

### Post by CptPicard on 2008-11-22
> **drubin said:**
> Think we as a community are becoming more tollerent of other languages?

Never been intolerant, the problem has always been at the blub low-level guys' end who are in denial and wish to remain so ;)

---

### Post by drubin on 2008-11-22
> **CptPicard said:**
> Never been intolerant, the problem has always been at the blub low-level guys' end who are in denial and wish to remain so ;)

Only one way to fix this.

---

### Post by CptPicard on 2008-11-22
> **drubin said:**
> Only one way to fix this.

Yes... got to evangelize to them whether they want to listen or not.. :)

---

### Post by drubin on 2008-11-22
> **CptPicard said:**
> Yes... got to evangelize to them whether they want to listen or not.. :)

No ban them! :) --Maybe your too:)

What do you think?

---

### Post by CptPicard on 2008-11-22
> **drubin said:**
> 
What do you think?

-1... it's much more fun to just duke it out... :)

[IMG]http://icanhascheezburger.files.wordpress.com/2008/03/funny-pictures-boxing-hamster.jpg[/IMG]

---

### Post by jimi_hendrix on 2008-11-22
> **cptpicard said:**
> it's much more fun to just duke it out... :)

+1

---

### Post by drubin on 2008-11-22
> **CptPicard said:**
> -1... it's much more fun to just duke it out... :)

Much better since you added the pic :)

---

