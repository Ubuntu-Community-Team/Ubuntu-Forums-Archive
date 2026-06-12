---
title: "I'm a beginner, can I write this program? [C]"
date: 2010-03-02
forum: Programming Talk
---

### Post by jasperyate on 2010-03-02
I'm very much a beginner to C, and it's my first foray into programming, so I want to know if this is going to involve advanced syntax or idioms I wont understand. It's not important, just for fun.

I have an excel document with names in one column and email addresses in the other. I want to write a simple program that takes the name from column A and puts it in a prewritten string, like:

hello {name}, its nice to met you.

preferably id like to be able to execute this for individual lines of text (for example row a2 in an excel file, but this is probably much more complicated than it sounds. maybe if i put it in plain text?) so that when i execute the command for a given email address or name it will output the preset text with the name in the text.

thanks for any input, directions where to learn how to do it.

---

### Post by dwhitney67 on 2010-03-02
You might want to consider exporting the xls file to a comma-separated-values (csv) file.  It would make parsing each line much easier.

Your code would be something like:
```

1.  open file

2.  for each line read from the file

3.     tokenize line to extract name and email address

4.     do whatever you want with 'name' and 'address'

5.  close file

```

---

### Post by Simon17 on 2010-03-02
Doing it in Excel format might be difficult for you. I agree that csv or tab delimited text would make it much easier for you.

+1 for plain text.

---

### Post by lavinog on 2010-03-03
Does it have to be c?
Something like this could be done in just a couple of lines of python.

---

### Post by Lux Perpetua on 2010-03-03
1. I agree completely with dhitney67 that you should export it into a plain text format (CSV probably being the simplest). Excel's native format is *proprietary*, and you're going to have a hell of a time doing anything with it.

2. This isn't a difficult task, but it might be too tedious if C is completely new to you, since you'll have to parse your input. Luckily, I think the standard function strtok() should work nicely with CSV. (Are you familiar with strtok? If not, read the manual page. If it seems confusing of complicated, then get some more familiarity with C before attempting this (even if you end up deciding not to use strtok).)

---

### Post by TheStatsMan on 2010-03-03
> **lavinog said:**
> Does it have to be c?
Something like this could be done in just a couple of lines of python.

I agree with this, no need for csv with python, xls is not a problem.

---

### Post by leg on 2010-03-03
I think you should not start with C as you will come against some confusing issues that may put you off. Having said that if you really want to use C then go ahead just be ready for some hard work. Python has been suggested and is considered a very good language to start learning programming with.

---

### Post by whirlwind on 2010-03-03
I disagree, I think C is an excellent place to start.  I would have fallen into some bad habits if I started off with a scripting language I think.

WW

---

### Post by Simon17 on 2010-03-03
I second what whirlwind said.

People who learn python don't learn to program; they learn to use libraries.

---

### Post by Martin Witte on 2010-03-03
> **Lux Perpetua said:**
>  Excel's native format is *proprietary*, and you're going to have a hell of a time doing anything with it. That is the native format upto Excel 2007, which was [difficult to grasp]("http://www.joelonsoftware.com/items/2008/02/19.html"). Since Excel 2007 it uses [Office Open XML]("http://en.wikipedia.org/wiki/Microsoft_Excel#File_formats"), which is a tad easier to parse, although I agree with the others that a .csv file is still a lot easier for the sort of exercise your doing.

---

### Post by NathanB on 2010-03-03
> **Simon17 said:**
> I second what whirlwind said.

People who learn python don't learn to program; they learn to use libraries.

I both agree and disagree with that.  Allow me to explain.

First, whether we are talking about use of library functions from C, or from Python doesn't matter.  So let's please drop the language choice from the discussion.  The choice has already been given:  the original poster(OP) said C... so C it is.  Any persuasion towards Python is obvious trolling from the OP's point of view.

Second, people have different preferred learning styles.  Some people are more motivated to continue learning more if they make use of 'pre-build' components like library functions that give them instant gratification.  Others might be annoyed by these mystery "black boxes" called library functions -- they will want to understand what's inside.. they will build their own library functions from scratch and gain a tremendous amount of programming skill as a result.

We might think of libraries as a crutch, but some people need to delay some of the learning process, they need to use the 'strtok' detour until they are comfortable enough with the language that they feel ready to tackle the detail-oriented aspects of problem-solving.  Others will say, "Heck, it can't be THAT HARD to scan a string to locate a comma," and they {brave souls that they be} will dive in with gusto to construct their very own 'strtok' function.  But remember, there is a lot of "hair-pulling" so it takes a lot of persistence to learn in this fashion...  it isn't for everyone.  Yes, a high learning curve, high stress, and persistence are all the everyday experience of every programmer, but it doesn't have to be EVERYBODY'S first experience of the craft.

Nathan.

---

### Post by Shpongle on 2010-03-03
yea c is grand it can be hard to follow when looking at os code i find (pointers all over the place) , but i wanna learn python i plan to do my final year project in python,

as for libraries , why reinvent the wheel , if it can get the job done *well* use it. you can use that time to actually solve other problems!

if you wanna learn programming  start with a book or guide with exercises on each topic and slowly work your way through them and ask as many questions as you feel you need to understand each topic.

as for the task at hand , flat file is the way to go!

best of luck

---

### Post by nvteighen on 2010-03-03
> **Simon17 said:**
> I second what whirlwind said.

People who learn python don't learn to program; they learn to use libraries.

And when learning C, you're mostly learning the C Standard Library... (as you know 'printf' is not interpreted by the compiler, but by the linker) Try coding in C without using it...

No. The idea is another one: you use the language you need the same as you use the libraries you need for a certain case. Most cases don't need the low-levelness of C and could be programmed more easily with other languages of which Python is just one good example.

I disagree on using C as the first language because of this; it introduces too much computer-internal details which are just accidental in programming. It forces you to learn implementational details when programming is a lot about hiding those details; see how any decent API works and you'll see what I mean... I couldn't imagine managing GTK+ if I had to know know how GtkWidget is implemented...

But ok, the OP wants it in C...

@OP: As others have said, Excel would be a burden... mainly because that's a binary format which will require a Microsoft API to have it work correctly. OpenDocument Spreadsheets would be a bit easier to deal with it, but again, if you're a beginner, it will be too hard for you to manage. A plain text file is the way in which very surely all of us started our first steps in file parsing :)

---

### Post by CptPicard on 2010-03-03
As the C vs. some other language issue pops up pretty much regularly here, let me post again the MegaThread for reference, as this exact issue was discussed to death a few years ago (with a lot of really interesting people involved who are no longer around):

[http://ubuntuforums.org/showthread.php?t=851794](http://ubuntuforums.org/showthread.php?t=851794)

C is at least a very "small" language, so in that sense it is not "hard" to learn per se. Then again, it's tedious -- a lot of busy-work -- to get going in, and more importantly it doesn't expand the programmer's mindset nearly as fast regarding different possible solutions as higher-level languages do. I do quite a lot subscribe to Dijkstra's view that programming is mostly about working on (computable) solutions to problems, and only secondarily about working on computers. There is of course a loud philosophically opposed school of thought ;)

Scripting languages are underrated... they both get in your way very little and facilitate solution-building (and I really mean this even in a case where you are *not* using a library call). Many higher-level languages also genuinely give you pieces to work with that make the language behave sufficiently differently to a language like C, that it makes you actually think differently about the whole process of programming. This kind of point of view difference stays with you even when working with C.

I know some don't actually believe this, but those guys have almost always without exception been ones who have *not* ever coded in something like Lisp, and/or lack a formal background (and thus don't really understand the implications of things like Turing-completeness).

The whole point that whatever goes on in the interpreter is *already a solved problem* -- a mere mapping from one language to another -- and is by definition something a machine can handle. At this point we need to pause and appreciate that civilization advances by increasing the number of automated operations. 

The language that gets interpreted *is still* computationally equivalently strong; it can even be used to write a CPU emulator, so there is nothing special at the "hardware level" in that sense. Also, any problem that is actually open at this point and you need to solve, still requires the human input to actually solve that particular problem: there is no "automated programming" in the general case. But, now we have a language that maps to your mind better as far as that *interesting* part of the problem goes, with the *automatable boring* stuff pushed onto the machine...

---

### Post by JDShu on 2010-03-03
> **DillByrne said:**
> 
as for libraries , why reinvent the wheel , if it can get the job done *well* use it. you can use that time to actually solve other problems!


Agree 100%

---

