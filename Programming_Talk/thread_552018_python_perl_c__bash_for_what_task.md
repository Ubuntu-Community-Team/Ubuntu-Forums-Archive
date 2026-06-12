---
title: "python/ perl/ c / bash for what task?"
date: 2007-09-15
forum: Programming Talk
---

### Post by adhg on 2007-09-15
hi there,
I have a very abstract/conceptual question: I'm a J2EE developer and I'm just getting familiar with Linux. Truth is that lots of the stuff that I used to program in Java could have been easily solved with a simple bash script.

I realized that some of you write in python/perl/C. My question is this: When will you develop your script in python/perl/bash? Of course this depends on the task...so for what task will you choose python (eg)?

thanks
adhg

---

### Post by Stephen Howard on 2007-09-15
With scripting languages, I don't think the choice is really based on the programming task.  Instead, I see the key factor being the size of the project:

small:   bash
bigger (but not much): perl
big: python

I've ignored C because it isn't a scripting language.

---

### Post by adhg on 2007-09-15
thank Stephen for your prompt reply.
ok...I get the idea. Q: can python translate a bash script? in other words, can python execute the same thing as bash do? if the answer is yes, I think I'll give a try to python because  it is more robust (I looked at the code and it has some similarities to Java)

what do you think?

---

### Post by ghostdog74 on 2007-09-16
> **adhg said:**
> . Q: can python translate a bash script? 
in other words, can python execute the same thing as bash do?

yes..and much more.
> 
 if the answer is yes, I think I'll give a try to python because  it is more robust (I looked at the code and it has some similarities to Java)

what do you think?
go ahead. It will be easy for you to pick up, since you came from a Java OO background.

---

### Post by slavik on 2007-09-16
small: bash
medium: perl (since my sed/awk skill aren't as nice)
big: perl

---

### Post by Cappy on 2007-09-16
I'm going to sort those by function:

---

bash: system maintenance scripts with minimal effort. Well suited for automating tasks or performing many operations with a few lines of code.

perl: modules you can add on to cut down on the work. Good for anything where a data structure matters.

python: preferred for a graphical interface, supposed to have better text handling support than perl. Preferred by ubuntu developers. Used for scripting in a number of open source programs (GIMP for instance).

C: Heavyweight utilities, device drivers, most programs.

---

The size of the project is rather irrelevant imo. A 500 line bash script may be better suited to a task than 5000 lines of python. What happens though is that a large project may need advanced utilities that may already be implemented in a language like python. Speed is only really a factor in bash because bash can be VERY slow if a script is written sloppily.

---

### Post by Compyx on 2007-09-16
Personally I use the following criteria:

**Bash**: small scripts to automate some tasks where speed isn't important.

**Perl**: Larger scripts and anything to do with text-parsing, I prefer Perl over Python when it comes to regexes and as a glue-language.

**C**: Large projects, data manipulation and when speed is of the essence. I mainly use C when coding, but I'm usually working on assemblers, compilers and tools that work with binary data from C64's.


I've left out Python because I haven't used it for a while, it's a great language though: very clean and well designed. I'd probably recommend Python to people as a first language. Perl can be very cryptic, C makes it very easy to shoot yourself in the foot and Bash is, well ... Bash.

---

### Post by pmasiar on 2007-09-16
Bash: If all you need is to execute couple of shell commands

Perl: Was "duck tape holding internet together" until about 5 years ago, when Python became popular, and then Ruby on Rails demonstrated how web apps could be simple if you use "conventions instead of configurations" approach. Perl is moribund project (slavik is the last standing defender of it :-) ), OOP is bolted on, and has no syntax features to facilitate development of big projects. Big projects are possible, but hard, and you have to have very strong coding standards and project management. 

Python: for everything :-) If you find out later (when your code is running and tested and correct) that you have performance bottleneck, you recode **this part only** in C (and you have tests to prove it is still correct).

C: Tool of last resort for performance only.

---

### Post by maddog39 on 2007-09-16
Bash: redundant tasks, workarounds, cronjobs, other small things
Perl: too mesy, never
Python: accasional PyGTK app
PHP: Everything

---

### Post by adhg on 2007-09-16
yep! thanks I got the idea.
I started with some python script and it looks cool. 
thank you all for your input.

---

### Post by pmasiar on 2007-09-17
> **maddog39 said:**
> PHP: Everything

... but only if your definition of "everything" is websites (and based on messy code to boot). MVC is the right way to interactive apps, separating model (data access), view (templates) and controller (business logic). PHP puts all together, resulting in the mess.

---

### Post by Stephen Howard on 2007-09-17
before committing to Python have a look at Ruby.

---

### Post by Stephen Howard on 2007-09-17
...especially after looking at  [this Ruby book]("http://www.poignantguide.net/ruby/").

---

### Post by ghostdog74 on 2007-09-17
OP has already chosen his path, so let's stop this.

---

### Post by Stephen Howard on 2007-09-17
oh pls, chill a bit - its not as if anyone is challenging a religious belief.

...not yet anyways.

---

### Post by pmasiar on 2007-09-17
> **Stephen Howard said:**
> before committing to Python have a look at Ruby.

Sure, take look at Ruby - you will appreciate more how clean and readable Python code looks :-P

---

