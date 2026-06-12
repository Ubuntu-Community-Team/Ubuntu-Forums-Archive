---
title: "What is ubuntu written in?"
date: 2008-02-23
forum: Programming Talk
---

### Post by DaveGiant on 2008-02-23
I was curious to find out what programming language has been used to write ubuntu.

Is it a single language or a combination?

Maybe a more tricky question. How is this language interpretted by hardware. Does Ubuntu come with som thing which reads the code and turns it into 1's and 0's?

---

### Post by luisito on 2008-02-23
Ubuntu is made from a lot of programs, and they are typically written in different languages. The answer would be "a combination".

The linux kernel is written mostly in C.
GTK+ is written in C.
Qt and KDE are written in C++.
Most of the programs you run are written in either C or C++. There are quite a few things written in Python too.

---

### Post by LaRoza on 2008-02-23
Ubuntu is a lot of different programs.

Linux, the kernel, is written in C and a little bit of Assembly.

C is used for many apps and libraries. C is compiled and is run on the processor.

Many languages are used, Python, Perl, Java, and C++ are probably the most used. (I have no desire to take inventory)

I know Ubuntu recommends Python. The Python interpreter used is written in C also.

---

### Post by steveneddy on 2008-02-23
Very interesting.

I was wondering that recently myself.

---

### Post by Yes on 2008-02-23
There's also some assembly in the kernal, if I'm not mistaken.

---

### Post by bobbocanfly on 2008-02-23
> **Yes said:**
> There's also some assembly in the kernal, if I'm not mistaken.

Yep. I read somewhere that there are also tiny amounts of other languages in there (mostly build processes but still in there) like shell script and perl.

A lot of the ubuntu native packages are written in Python like Ubiquity (the graphical installer) and update-manager etc.

---

### Post by Fbot1 on 2008-02-23
This probably isn't helpful but here: [http://www.ohloh.net/projects/4265/analyses/latest](http://www.ohloh.net/projects/4265/analyses/latest) .

---

### Post by Jessehk on 2008-02-23
I would also add that Ubuntu itself varies only slightly from all the other versions of Linux available such as Fedora, Suse, Gentoo, Arch etc. All of these distributions use a common foundation including the Kernel (C), standard libraries (glibc, posix stuff, etc), and some standard utilities such as mkfs, cat, more, wc, etc.

Then, things start to change as you get more distribution specific and start dealing with things such as package management and configuration. Ubuntu is based almost entirely off of Debian. Standard tools such as apt and apt-get/aptitude are written in C. Synaptic is also written in C. Where things change is where there are Ubuntu-specific programs such more friendly printer and network configuration. I think Python is heavily used here along with gtk+ (which is written in C, but has bindings for many languages).

Another common toolkit used on Linux is Qt, which is written in C++ and one of the main components of KDE.

The main point is that Ubuntu (and any Linux distribution in general) is not a single unified whole. There are many components written by different people in different languages that work together.

---

### Post by pmasiar on 2008-02-23
All the projects included in any Linux distro use any language they wish. Distro  just packages code developed by "upstream" developers, with possibly small changes/patches, and some minimal custom development.

Difference between distros are, what language(s) are used by distro developers to distro-specific tasks and applications. Ubuntu prefers Python, other distros might prefer other languages, I assume Perl, C, C++ would be rather popular, also depending of GUI toolkit used.

---

### Post by Zwack on 2008-02-23
Nobody else seems to have answered the second part...

Some of the languages (C, C++) are compiled into binary machine code instructions and those "just run" 

Assembler has a one to one correspondence to the binary instructions that the processor uses, so that is "translated" at one point in time.

Some languages (Perl, Python, Shell) are interpreted at run time by a compiled interpreter.  (Although compilers for some of these languages are also available)...

Some (Java) are a mixture...  They are compiled into a byte code for a virtual machine and then interpreted at run time (at least that's the best way I can think of describing it).

This is not an exhaustive list, but those are the three strategies...  For all intents and purposes Assembler and compiled languages are the same, you end up with an OS specific, architecture specific binary that should just work.  Interpreted languages require an interpreter but run the same on any OS/architecture combination that has an interpreter...

And things like Java run their "compiled code" anywhere their virtual machine runs.

Z.

---

### Post by slavik on 2008-02-24
perl/python are compiled to bytecode :)

bash scripts might be, too.

---

### Post by LaRoza on 2008-02-24
> **slavik said:**
> perl/python are compiled to bytecode :)

bash scripts might be, too.

And C can be interpreted (I use tcc)

---

### Post by slavik on 2008-02-24
I didn't mean it in a sarcasting sense, python and perl ARE compiled to bytecode (right before execution). The reason the shell might do it with shell scripts is that once you generate the bytecode, it is easier to execute bytecode.

---

### Post by LaRoza on 2008-02-24
> **slavik said:**
> I didn't mean it in a sarcasting sense, python and perl ARE compiled to bytecode (right before execution). The reason the shell might do it with shell scripts is that once you generate the bytecode, it is easier to execute bytecode.

Neither did I. I was pointing out that there is more to it then was hinted in previous posts. ELF, JIT, Byte code, interpreted, etc.

---

### Post by Zwack on 2008-02-24
Too true...

I was going for the rough overview...

Java is usually compiled into byte code prior to runtime while Perl/Python/Shell aren't and C is usually compiled but can be translated... and BASIC compilers exist... 

There is no reason why any given language has to follow the "normal" strategy for that language.  You could write a compiler and an interpreter for any language, but some languages tend to use one strategy over another.

I don't think that shells usually compile bytecode (what advantage would that give for an interactive session?) but that isn't to say that it couldn't be done, and it would be odd (to say the least) to use interpreted C for an OS kernel.

However in the case of "Ubuntu" the general strategies are that C, C++ and Assembler are converted into binaries prior to distribution while Perl/Python/Shell are distributed as "interpreted" scripts.

Which, I believe, answers the original question.  :-)

Z.

---

### Post by Fbot1 on 2008-02-24
> **Zwack said:**
> 
There is no reason why any given language has to follow the "normal" strategy for that language.  You could write a compiler and an interpreter for any language, but some languages tend to use one strategy over another.

Well, the language could specify the implementation.

> **Zwack said:**
> 
I don't think that shells usually compile bytecode (what advantage would that give for an interactive session?)


Korn shell, Z shell, and PowerShell can. It's more for distributing it.

---

### Post by pmasiar on 2008-02-24
There is also slight difference between Python and Perl: Perl discards bytecode after executing it, Python saves it (as .pyc), so Python can execute it next time (and automatically recompiling if source was changed). So in most cases, Python can directly execute bytecode without parsing sources, saving time. You can also distribute .pyc bytecode files instead of .py sources.

---

### Post by slavik on 2008-02-24
```
perl -MO=Bytecode
```

---

### Post by LaRoza on 2008-02-24
> **slavik said:**
> ```
perl -MO=Bytecode
```

I never doubted it, thanks for the tip.

---

### Post by Zwack on 2008-02-24
> **Fbot1 said:**
> Well, the language could specify the implementation.


And someone could write a tool that used the same language but ignored the standards as far as implementation.  i.e. it looks like Fbot1script but it's compiled instead of interpreted.  It would be a non standard Fbot1script compiler but it would still use Fbot1script...

And as for Shells and byte code...

> 
Korn shell, Z shell, and PowerShell can. It's more for distributing it.

I did say that I didn't think that any shell USUALLY compiled to byte code as there is no advantage for interactive sessions...  

For the Korn shell there is a separate shell compiler shcomp that will compile the shell script to an intermediate form that can be recognised by the shell.  This is not strictly speaking the same as the shell can compile bytecode.

Z.

---

