---
title: "Programming languages getting better"
date: 2009-07-23
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-23
I read somewhere that Java is improving on speed.How does that happen.Stuff usually slows down with addition of more features.Is there a similar trend with C hash or Python or Perl.
Has C or C++ speeded up in their long journey

---

### Post by benj1 on 2009-07-23
java is an interpretted language so its speed depend on how good the interpreter is, so the speed increases are down to better interpreter design, or want they want to do better. yes larger programs tend to run slower, but computer power tends to increase faster than features are added, so it doesn't realy make a difference. 
I think python 3 is faster relative to python 2, not sure about perl or c#

c and c++ have speeded up in that their compilers have got better, but not to the same extent, and im sure you could get almost the same speeds using the correct compiler flags etc

---

### Post by JordyD on 2009-07-23
> **nipunreddevil said:**
> I read somewhere that Java is improving on speed.How does that happen.Stuff usually slows down with addition of more features.Is there a similar trend with C hash or Python or Perl.
Has C or C++ speeded up in their long journey

Programming languages speed up when the people that work on the language's compilers/interpreters improve how the source code is translated into machine code. If, for example, I was to make a C compiler, it would likely be crap slow compared to GCC, because I've never made a compiler, and I'm most definitely not an expert in machine code.

As for C(++) increasing in speed, I have no idea. I imagine that with time they have found better ways to convert peices of code, but I don't know.

It actually wouldn't slow down with the addition of features unless those are slow features and you're actually using them. For example, if they came out with a for loop in C, that was slower than the existing loop, but did not replace it, as long as I didn't use it, it wouldn't slow down my code.

---

### Post by SunSpyda on 2009-07-23
Basically, every now and then, a language higher level than the current ones comes out. Hex to ASM, ASM to C, C to C++/Obj-C, C++/Obj-C C#/Java. Or something like that.

You, as a programmer, have to decide what "level" is most appropriate for the thing you are doing. Writing device drivers in Java would be silly, & so would writing a massive maintainable project in ASM. Pick the right level for the job.

Rule of thumb - The higher the level, the slower it is - not always, but generally. The lower the level, the harder it is to read and maintain - not always though.

EDIT - I forgot to say - Languages get faster to to better interpreter/compiler implementations. C/C++ compilers have been around a while, so the compilers for them have been fine tuned pretty well.

---

### Post by Reiger on 2009-07-23
The main reason why languages "get better" is that the language features are more thoroughly researched than they were (N) years ago. Just like how cars tend to get more efficient at transporting people even when a lot of additional extras are thrown in for comfort, so too do language implementations (the virtual machine, the compiler, etc.) get more efficient at what they do because of the continuing research that is done in those fields. Some language-designer or researcher propose new features or extends the theoretical knowledge of how features (should) work and this it picked up by others who improve on the original work, that kind of stuff.

For a reference you may want to read up (briefly, because it is fairly exhaustive) on the history of the relational data base with research into Armstrong's axioms, closures, normal forms; but also with research into RAID setups, index granularity etc. etc.

---

### Post by MadCow108 on 2009-07-23
just look at, for example, the gcc changelogs to see what kind of stuff improves with time.
example gcc 4.4 under General Optimizer Improvements:
[http://gcc.gnu.org/gcc-4.4/changes.html](http://gcc.gnu.org/gcc-4.4/changes.html)

---

### Post by nipunreddevil on 2009-07-23
is there a theoretical possibility of interpreted languages getting faster than compiled ones?
What about scripting languages

---

### Post by Reiger on 2009-07-23
JVM languages or Mono VM languages (for want of a better word) aren't interpreted if that is what you were referring to. They are compiled, Just In Time. This is important because a certain code snippet that gets executed often in a optimizing JIT environment can -in theory- be "bootstrapped" to a much more efficient form than something that has to make do with the details available Ahead Of Time.

You'll notice this with large Java programs like Netbeans. They do not merely take a while to start up, they also take a while to "get going": it takes some time before the program responds quite as fast as it can do. (Although the tendency of the JVM to load things &#8220;on demand&#8221; may skew my perception here...)

---

### Post by dlmarti on 2009-07-23
> **nipunreddevil said:**
> is there a theoretical possibility of interpreted languages getting faster than compiled ones?
What about scripting languages

Yes, but it would have to be a really good interpreter, and a really lousy compiler.
Compiled code will always have the run-time edge, since it doesn't incur the overhead of converting the script to code.

---

### Post by Shin_Gouki2501 on 2009-07-23
> **benj1 said:**
> java is an interpretted language ...
that is plain wrong.. ever heard about JIT?

back to topic:
[http://olabini.com/blog/2009/04/languages-should-die/](http://olabini.com/blog/2009/04/languages-should-die/)

the jvm (and yeah its open source too) is a pretty nice place for evolving programming languages take a look at Scala, Clojure, jython, Groovy or JRuby.

Java and the jvm grow together but today there is a broad landscape.

Too bad that linux folks tend to like Mono more for 'UI'- Programming. But that maybe is a reason of  java's graphics stack.

---

### Post by soltanis on 2009-07-23
It might also be because Java in general is damn annoying, but that's a completely different discussion.

As languages mature, they tend to become faster as better methods for optimizing them are found and as better schemes for managing memory emerge. C and C++ have as you pointed out a head start in this realm by virtue of having been around for a very long time. For the most part, they are not advancing by great leaps and bounds any longer -- most optimizations have already been discovered and applied, especially in large, complex compilers like gcc. The problem is actually more of how fast gcc can compile the code, and that's I think a large subject of improvements made to its code.

Newer languages like Java are reaping the benefits of faster JIT compilers, better garbage collectors, and better integration of native graphics/sound libraries.

PS. Python 3 is slower than Python 2 currently -- they haven't optimized the code yet.

---

### Post by NathanB on 2009-07-23
> **SunSpyda said:**
> 
You, as a programmer, have to decide what "level" is most appropriate for the thing you are doing. Writing device drivers in Java would be silly, & so would writing a massive maintainable project in ASM. Pick the right level for the job.


A programmer rarely gets the opportunity to make this decision -- his/her employer/client determines what tools must be used.

Also, "writing a massive maintainable project in ASM" is certainly not silly -- unless you call making {at a minimum} $1,000 USD per month from every client silly.  Niche enterprise and financial applications have steep requirements that cannot be easily met using {for instance} Java.

Do you think banks use MS Windows or Linux on their critical computers that track un-imaginable transactions per day?  They certainly don't want to make it easy for someone to hack those machines.  Right?  That is why they use custom-built proprietary Operating Systems and supporting software that you will never hear about.  A programmer must write his application in whatever language happens to be available on that OS.

---

### Post by jero3n on 2009-07-23
> **NathanB said:**
> A programmer rarely gets the opportunity to make this decision -- his/her employer/client determines what tools must be used.

Also, "writing a massive maintainable project in ASM" is certainly not silly -- unless you call making {at a minimum} $1,000 USD per month from every client silly.
If your client asks you an ERP written in assembly, yes it is silly. On the other hand you can make $1000 per month even writing in .NET

The point here is the employer/client has to be a programmer in order to choose correct tools. So "You, as a programmer, have to decide what "level" is most appropriate for the thing you are doing." is absolutely true. In our office, we programmers have the freedom to decide the necessary tools. This is part of a programmer's job, taking into consideration various parameters, most of them already stated in this thread.

---

### Post by NathanB on 2009-07-23
> **jero3n said:**
> If your client asks you an ERP written in assembly, yes it is silly. On the other hand you can make $1000 per month even writing in .NET

The point here is the employer/client has to be a programmer in order to choose correct tools. So "You, as a programmer, have to decide what "level" is most appropriate for the thing you are doing." is absolutely true.

When your .NET application doesn't run on your client's computer, then you will not receive the money.  You will have to look for other work while hoping the client doesn't call the cops on you for running a scam.

So, the programmer only has two items to choose from:

1)  Do the work using the tools that the employer/client requires you to know how to use.  Make $20,000 per month.

2)  Pretend to do the work using the tools that *you* want to use.  Employer/client will be unhappy that the work wasn't done.  Make $0 per month.  Risk going to jail.

Which of the above routes do you think most programmers choose?

---

### Post by jero3n on 2009-07-23
> **NathanB said:**
> When your .NET application doesn't run on your client's computer, then you will not receive the money.
Receiving the money and not going to jail is part of the parameters a programmer has to take into consideration :D
> 
1)  Do the work using the tools that the employer/client requires you to know how to use.  Make $20,000 per month.

I  understand your idea, but IMO you missed my point as well **SunSpyda**'s. Choosing tools is job of someone experienced on how to use that tools. Period.

---

### Post by Mirge on 2009-07-23
> **NathanB said:**
> When your .NET application doesn't run on your client's computer, then you will not receive the money.  You will have to look for other work while hoping the client doesn't call the cops on you for running a scam.

So, the programmer only has two items to choose from:

1)  Do the work using the tools that the employer/client requires you to know how to use.  Make $20,000 per month.

2)  Pretend to do the work using the tools that *you* want to use.  Employer/client will be unhappy that the work wasn't done.  Make $0 per month.  Risk going to jail.

Which of the above routes do you think most programmers choose?

$20,000 per month? Hey you hiring? :KS

---

### Post by TheStatsMan on 2009-07-23
In numerical computing where speed can be extremely important important features have been added to languages to make them faster. In C the restricted keyword was added so that C could be competitive with fortran. Template meta-programming was not originally implemented in C++ but it now allows C++ to be much faster than both C and fortran for some problems. Expressive templates can be used to make coding in C++ to be as easy as matlab, without any significant speed penalty, unlike the original implementations, which had to create temporaries when overloading addition, multiplication, etc. and were hence very slow. Programming languages also have to evolve to take advantage of improvements in technology. Multicore processors are now standard and C++0x will have in built features to handle parallel programming.

---

### Post by HotCupOfJava on 2009-07-23
> **Mirge said:**
> $20,000 per month? Hey you hiring? :KS

Indeed - I would love to write some code for that kinda green. A couple of month's work, and I could take the rest of the year off...

---

### Post by Mirge on 2009-07-23
> **HotCupOfJava said:**
> Indeed - I would love to write some code for that kinda green. A couple of month's work, and I could take the rest of the year off...

That kinda money I don't think I'd take any time off until the employer couldn't afford me any longer :).

---

### Post by dlmarti on 2009-07-24
> **Mirge said:**
> That kinda money I don't think I'd take any time off until the employer couldn't afford me any longer :).

Jobs like that don't last long, if they did they would hire someone full time.
I once had a contract for $4000 per day, but it only lasted three days.

A company found itself in a bind, and needed a fix fast, I lucked out.

---

### Post by Mirge on 2009-07-24
> **dlmarti said:**
> Jobs like that don't last long, if they did they would hire someone full time.
I once had a contract for $4000 per day, but it only lasted three days.

A company found itself in a bind, and needed a fix fast, I lucked out.

Yeah, I've been lucky enough to find myself in those scenarios a few times. Wish it would happen more often.

---

