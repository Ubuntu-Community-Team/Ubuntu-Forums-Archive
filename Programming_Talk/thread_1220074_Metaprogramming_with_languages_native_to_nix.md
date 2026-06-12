---
title: "Metaprogramming with languages native to *nix"
date: 2009-07-22
forum: Programming Talk
---

### Post by rootless on 2009-07-22
I have been scripting with bash for a while now, and I'm looking to move up to a more fully featured language. I had heard that learning lisp will make one a better programmer, and so I have been reading about it, and I've become profoundly interested in metaprogramming.

The obvious suggestion here is to learn lisp- and indeed, I plan on doing so eventually, but for the sake of practicality, I also want focus on languages natively found on *nix systems.

It would really help me if someone could point me towards a language to learn, and why. Thanks.

---

### Post by JordyD on 2009-07-22
What do you mean by 'native'?

---

### Post by monraaf on 2009-07-22
I'm not quite sure what you mean with 'languages native to *nix'.

---

### Post by CptPicard on 2009-07-22
I am not really sure how you mean with "native" languages -- SBCL runs on Linux just fine. ;) Then again if you're thinking about stuff like C, perl, or awk -- "most common" languages on *nixes if you will, you're more out of luck with the metaprogramming part.

I would suggest you just start hacking Lisp and do what interests you...

---

### Post by benj1 on 2009-07-22
first off im not sure what you mean by native to *nix but if lisp is native to anything its probably a *nix environment.

regarding the finer points of lisp i don't know, cpt pickard is quite knowledgeable, hopefully hes hanging around
EDIT: he here already, those damn transporters, "engage".

what kind of thing are you wanting to program?
thats probably the main thing you need to know when choosing a programming language.
if youre going to be doing something processor intensive probably c or c++ (although lisp can be compiled and as i understand is only marginally slower than c)
python is more high level and alot easier to program with, and you can program just about anything in it although it is interpreted and so slower.

---

### Post by raronson on 2009-07-22
Shell scripting, awk, lisp (use emacs-slime & SBCL), C, python; and then, perl, java, c++, whatever...

Some good IDE's: the terminal and your environment, Emacs, IDLE (python), Anjuta, Eclipse.

There's no definite path, but I posed the same question long ago and this is what I've come up with.  Good luck.

---

### Post by rootless on 2009-07-22
Sorry, my question was ambiguous. What I mean by 'languages native to *nix' is, languages which *nix can compile without having to install an interpreter- for instance, ubuntu comes with the perl and python interpreters, and GCC, but if I wanted to run anything written in Java, I would have to install the JVM.

The reason for my odd request is that I am doing a lot of work on remote servers, which are usually left as generic as possible for purposes of security and intelligibility.

---

### Post by nvteighen on 2009-07-22
Hm... Lisp code (Common Lisp and Scheme) compiles into native code, but you'll still need the Lisp runtime to start that code. Other way could be to use SBCL "Lisp images", which embed the interpreter into the code (but I'm not sure if the Lisp code gets compiled natively... or saved into some bytecode).

Other idea could be Clojure, a Lisp that runs on the Java Virtual Machine.

---

### Post by rootless on 2009-07-22
Interesting. Thanks. I've only just begun learning about lisp and I've had several epiphanies. I think it's going to take me a while to wrap my head around 'lisp images...' The code contains it's own instructions to compile itself? I think my brain is melting.

I was also wondering whether anything like clojure existed. That also sounds like a pretty decent option- as long as the JVM is installed.

Presuming my research into self-compiling-lisp doesn't work out, or my brain has a stack overflow trying to comprehend it, is python decent at metaprogramming?

---

### Post by benj1 on 2009-07-22
well if you want compiled your choices are lisp (as mentioned) c and c++, but note that neither compiler comes as standard in ubuntu, if you want a language that is guaranteed to work on all *nixes then you are probably limited to sh although bash and awk are common (in linux anyway). python and perl are common in linux so it would be fair to rely on those aswell.

the problem is linux is very modular so there aren't realy any standards about what is installed (except the kernel, or it wouldn't be linux :)) so youre not guaranteed to get anything.

---

### Post by rootless on 2009-07-22
I thought GCC could compile C without a frontend?

And yeah, you're right, linux is highly modular, but certain languages are there by default, and *nix servers are far more standardized than desktops.

For instance, you actually can't get a *buntu without perl or python and GCC, unless you remove them after install.

---

### Post by CptPicard on 2009-07-22
well, if you have root, it's just a single command to install anything... but mind you, for security reasons, a server should probably not even have gcc installed.

A Lisp image is... hmm... a memory dump of everything that has been defined in some lisp "session". Combination of code and data. Not really self-compiling Lisp, although the compiler itself probably is written in Lisp :)

EDIT: I stand corrected, looks like the image is standalone, it does have the compiler too...

---

### Post by soltanis on 2009-07-22
Well since the lisp core contains everything that the lisp instance 'knew' when it was dumped, it follows that the core also contains the compiler used to compile the software (which was part of the running lisp instance). And yes, the lisp does compile the lisp (this kind of stuff sounds profound but after a while just gets annoying).

But anyway, if you want metaprogramming without the lisp, you can still metaprogram in other languages. Lisp is the easiest to do it with because the basic data structure in lisp also happens to be the way programs are represented (i.e. lists). Seeing as how both perl and python have the notion of the "eval" function (and the associated performance hits + security concerns) you could ostensibly write code-writing-code in those languages as well.

Python has lambdas, which makes this a bit easier as well.

Finally, a language you probably haven't considered, Javascript, has some roots in Scheme (a lisp variant) and also has metaprogramming facilities.

---

### Post by CptPicard on 2009-07-22
> **soltanis said:**
> Well since the lisp core contains everything that the lisp instance 'knew' when it was dumped, it follows that the core also contains the compiler used to compile the software (which was part of the running lisp instance).

IMO it wouldn't necessarily be so, right? We could keep that stuff in the separately installed libraries and just link there from the image that would contain just "user definitions"... but yes, the compiler is included...

---

