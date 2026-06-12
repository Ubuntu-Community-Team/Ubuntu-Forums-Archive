---
title: "cobol to java conversion"
date: 2008-04-05
forum: Programming Talk
---

### Post by emnaki on 2008-04-05
I'm starting out in Cobol and would like a free software which will convert Cobol to java (which I am more familiar in)  so that I could have a faster understanding of the Cobol code. So far the only softwares which I have found which claim to do this have all been commercial tools. A tool, or a process for doing this would be very much appreciated.

---

### Post by Zugzwang on 2008-04-05
You could use OpenCOBOL to translate COBOL into C code:
> OpenCOBOL translates COBOL into C and compiles the translated code using the native C compiler. You can build your COBOL programs on various platforms, including Unix/Linux, Mac OS X, and Microsoft Windows.

If you're lucky, you can then translate that into C (see e.g. [http://freshmeat.net/projects/c2java/](http://freshmeat.net/projects/c2java/))

---

### Post by pmasiar on 2008-04-05
Why you are "starting in Cobol"? You mean Cobol as your first language?

I don't believe there is much new things happening in Cobol-lands, it is quite obsolete. Automatic translation Cobol to anything might be quite hard, because Cobol is so different from other languages, and dead end to boot. Languages don't do GOTO anymore :-)

But it is just my gut feeling, I don't follow Cobol development (never did), and try to avoid Java if I can, so if someone has better info, you are welcome to prove me wrong. Zugzwang's advice above is good step: C is not bad, but I am afraid C generated from Cobol would by quite mess.

---

### Post by CptPicard on 2008-04-05
Automatic code conversion tools generally produce code only for the target language's compiler, not for human consumption, and certainly not for "learning purposes". Idiomatic, clean transformation is very close to the automatic programming problem, which is provably impossible :)

---

### Post by ZylGadis on 2008-04-05
> **CptPicard said:**
> Idiomatic, clean transformation is very close to the automatic programming problem, which is provably impossible :)

This is very interesting. Is there really a proof that automatic programming is impossible? If there is, then that would mean true AI is impossible, too.

---

### Post by CptPicard on 2008-04-05
There is no general, complete algorithm for proving correctness of formulae in first-order predicate logic.

[http://en.wikipedia.org/wiki/G%C3%B6del's_incompleteness_theorem](http://en.wikipedia.org/wiki/G%C3%B6del's_incompleteness_theorem)

Turing's results about the inherent limits of computation are very closely related to this. In particular, there is no automatic debugger, as the halting problem is not computable :)

And yes, you're correct that this is a huge -- probably the most important -- issue in the philosophy of AI :)

Roger Penrose wrote a nice popular exposition of this whole issue in "The Emperor's New Mind". Recommended. He's a bit of a crackpot with his quantum mechanical conclusions the consensus goes, but the general description of what's going on is nice...

---

### Post by kaivalagi on 2008-04-05
Don't use Cobol, any missing fullstops in code will drive you made!

---

### Post by ibuclaw on 2008-04-05
> **pmasiar said:**
> I don't believe there is much new things happening in Cobol-lands, it is quite obsolete.

Apart from more than 70% of the Retail & Commercial Industries Servers still running on COBOL code (Including my workplace). Most of which were written by programmers who are, if not retired, are long gone with a demand for people to replace them.

Nope, COBOL will have a small rise in the weather forecast over the next ten years. The question is, are companies willing to pay for the time to re-write millions of lines of code into something considered more modern? Or continue to take the cheap alternative and continue to hire COBOL programmers to update their old code.

Or perhaps the question is how long SCO will last, I suppose.

That may determine the future for COBOL.

---

### Post by kaivalagi on 2008-04-05
> **tinivole said:**
> Apart from more than 70% of the Retail & Commercial Industries Servers still running on COBOL code (Including my workplace). Most of which were written by programmers who are, if not retired, are long gone with a demand for people to replace them.

Nope, COBOL will have a small rise in the weather forecast over the next ten years. The question is, are companies willing to pay for the time to re-write millions of lines of code into something considered more modern? Or continue to take the cheap alternative and continue to hire COBOL programmers to update their old code.

Or perhaps the question is how long SCO will last, I suppose.

That may determine the future for COBOL.

At my first  job after uni, working for an insurance company (in the top 5 of Europe), they put all graduate inductees on an 8 week Cobol course. They still run most of the  in-house functions with Cobol/DB2 on OS/370 mainframes...

The pay can be really good, I just can't stomach Cobol anymore, no matter what :)

---

### Post by pmasiar on 2008-04-05
> **tinivole said:**
> Apart from more than 70% of the Retail & Commercial Industries Servers still running on COBOL code ...
 are companies willing to pay for the time to re-write millions of lines of code into something considered more modern? 

I never said Cobol is not used anymore - I just said that it is obsolete, and companies try to move to Java. Of course it is pain and expensive - but finding programmers willing and able to code Cobol code patched for 30 years become more and more expensive.

> the question is how long SCO will last...That may determine the future for COBOL.

I don't believe SCO will emerge from bankruptcy, you do believe it? I hope SCO will die slow and painful death, so other companies will think twice before attacking Linux again. So if Cobol relies on SCO, it would be as good as dead, but there are other companies invested in Cobol, it will survive. [TIOBE](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html) even shows Cobol growing, whatever it might mean, but still not between top 10 languages. Whatever TIOBE measures of course :-)

---

### Post by emnaki on 2008-04-06
> **pmasiar said:**
> Why you are "starting in Cobol"? You mean Cobol as your first language?

Programming is not new for me. I'm quite good at working with OO languages like Java or .NET stuff. I've recently been working in an insurance company whose main system is a Cobol application. The system is really stable so I doubt they will be replacing it any time soon. Well being a programmer/technician, I had to manage and develop that legacy application. The process so far seems really daunting, so I was hoping to convert it to a javaish thing which I could do some refactoring to understand the code. I guess if conversion is not feasible then I'll have to learn some Cobol tracing techniques.

---

### Post by pmasiar on 2008-04-06
Yup. Possible fun thing to do could be to write some sode analyzing/refactoring tools (in Python of course) to help you with that task. :-)

---

### Post by kaivalagi on 2008-04-06
Is it a big/complex system? It's just that converting Cobol into an OO language is definitely not something you could automate in a nice fashion at all. I remember the cobol I worked on didn't even have a  FOR loops available, so you had to use functions instead. If that's anything to go by you'll be hard pushed to convert to a new language easily...

You could knock together some tools to partially do the work, but ultimately the new code would need serious manual labour.

Sounds like the system ideally needs reverse engineering, documenting and rewriting...which will take a lot of man days

---

