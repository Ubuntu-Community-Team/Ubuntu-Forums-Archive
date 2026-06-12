---
title: "A feel a bit silly asking..."
date: 2008-02-04
forum: Programming Talk
---

### Post by b3n87 on 2008-02-04
... Basicly I used to program with Visual Basic 6. I was no professional, all i did was download code, edit it, see how it reacted, and thats how I learnt to program in VB6.

I never made anything huge, or life changing, but i enjoyed doing. No i want to get into programming again, and I dont have time to do courses, so i just want to download code and play with it :D

I;m an engineer, and ive used CAD a lot, so i download SagCad, located here:

[SagCad]("http://sagcad.sourceforge.jp/")

Basicly I was wondering if anyone knew what is the best program to use, to view, edit and "test run" this. just so i can have a little tinker :)

Or do I need to compile it each time Ive edited the program.

I appologis for my lack of technical knowledge, all i need is someone to put me in the right direction and ill be ok :)

Best regards

---

### Post by LaRoza on 2008-02-04
<edit>
You are better off learning a language. That application is written in C and GTK+, and not really suitable for tinkering with without knowledge of both languages. You would have to rebuild it each time it is edited.
</edit>

Python may be just what you are looking for, it doesn't need to be compiled, and it can be run from the command line interactively as well as writting scripts, and even large applications.

See my wiki for it.

You might want this to go with it once you learn it: [http://www.scipy.org/](http://www.scipy.org/)

---

### Post by b3n87 on 2008-02-04
thank you for your quick reply. Ive heard a lot about python, so i shall have a look at that.

ive done minimal work with C++, command line stuff. So basicly, that SagCad and other C++ programs are all written in standard text files, then compiled when ready?

all those commands, variables, etc that are in each file, are they all remembered of the top of there heads then?

in VB it used to pop up with a list of commands as you were typing. I understand VB was extremely basic, but im just trying to learn where it all stands if you follow me :)

thank you again

---

### Post by LaRoza on 2008-02-04
> **b3n87 said:**
> 
ive done minimal work with C++, command line stuff. So basicly, that SagCad and other C++ programs are all written in standard text files, then compiled when ready?

all those commands, variables, etc that are in each file, are they all remembered of the top of there heads then?

in VB it used to pop up with a list of commands as you were typing. I understand VB was extremely basic, but im just trying to learn where it all stands if you follow me :)

thank you again

There are many files in the program you downloaded (in src directory). C is very different than VB, and it is not something one could easily tinker with.

You are talking about Visual Studio, an IDE. There are many IDE's that can be used in Linux (although I don't use them), and the stickies address the IDE question.

---

### Post by pmasiar on 2008-02-04
VB is not very strong on Linux. There is Mono, which is reimplementing .NET on Linux, but... it is following someone's else lead, and not leading.

One of popular emerging languages is Python (was chosen by TIOBE as "Language of 2007", search thread in last 2-3 weeks, it was pretty opinionated discussion about merits of both TIOBE and Python :-) ). 

Luckily for you, there is a  CAD package in Python, [http://www.pythoncad.org/](http://www.pythoncad.org/) . Python is much simpler to read than C/C++ so you should have easier time to help developing it/adding new feature/hack for fun if this is what you want.

See wiki in my sig to get you started with Python. I promise it will be simpler that the VB you half forgot. :-)

BTW you should also read how to ask questions - at least how to get better title for your post  :-)

---

### Post by b3n87 on 2008-02-05
thank you very much for your help :D

ill give Python a try!

---

