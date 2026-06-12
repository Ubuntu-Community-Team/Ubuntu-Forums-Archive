---
title: "getting a C++ IDE to work (any is fine)"
date: 2008-02-09
forum: Programming Talk
---

### Post by sujinge9 on 2008-02-09
Hi, I'm relatively new to linux and only starting to learn C++. After switching to Ubuntu, I thought it would be easier to program but I discovered it was not so. Back on windows I used Dev C++ and doing Hello world was as easy as typing in the code and hitting compile. But as I tried various IDEs, such as anjuta and geany, I have not been able to complile a single program. Would someone please help me get any IDE to work on a almost fresh install? Thanks.

---

### Post by mike_g on 2008-02-09
Well you can edit your code in any text editor then compile from the command line.

Just type:
```
g++ -Wall filename
```
As long as g++ dosent moan too much you will be left with an executable called a.out. You can run it like so:
```
./a.out
```
I'm sure theres probably a FAQ about it here somewhere that explains this stuff better, but with that you should be able to compile and run simple progs.

---

### Post by sujinge9 on 2008-02-09
Yeah, g++ is great and everything, but I would prefer an IDE that can do it all because it is so much simpler like that. So please, can someone help me to get an IDE to work?

---

### Post by chris200x9 on 2008-02-09
geany :)

---

### Post by sujinge9 on 2008-02-09
I have tried geany and I have it installed, yet I am unable to compile anything. Will you please show me how to get it to work?

---

### Post by chris200x9 on 2008-02-09
do you keep getting compile errors? if so prolly do a sudo apt-get install build-essential or you can do it via synaptic :)

---

### Post by LaRoza on 2008-02-09
Look in the stickies, there are threads on C++ and IDE's.

---

### Post by shaggy999 on 2008-02-09
Do you perhaps have an IDE installed but not the compiler?(try **sudo apt-get install build-essentia**l) It's kind of hard to help you out without telling us exactly what your problem is. Are you getting any error messages? You need to walk us through your process to where you get an error.

---

### Post by mike_g on 2008-02-09
> Yeah, g++ is great and everything, but I would prefer an IDE that can do it all because it is so much simpler like that. So please, can someone help me to get an IDE to work?
Thats strange, after using DevC++ on windows I found compiling & linking through the command line very simple.

Anyway thats what I do in Ubuntu. If you want an IDE to do that stuff for you Netbeans is awesome, but id think you need to get a C/C++ plugin for it. Still if you get that done then you can compile and run at the touch of a button.

---

### Post by LaRoza on 2008-02-09
I just installed Geany to see how using an IDE works on Linux.

It is easy, install build-essential and geany

```

sudo aptitude install build-essential geany

```

Start Geany (Applications->Programming->Geany), enter your code, and compile with Build->Compile, then link Build->Build, and you can execute it (and it won't close it like Dev-C++ does)

(F8 and F9 are the shortcuts for the compile and link)

---

### Post by sujinge9 on 2008-02-09
It appears the the essentials weren't installed, but even after I installed it, There is no difference. There are no errors, my problem is simply that I cannot even compile anything through ANY IDEs. Under geany, the compile button is simple greyed out. Under Anjuta, I get Can not compile "Programming /hello world.cpp ": No compile rule defined for this file type.

I just wanted something that lets me type some stuff in and compile without any issues like what I had back on windows.

---

### Post by LaRoza on 2008-02-09
What file extension are you using?

To manually set it, go to Build->Set Includes and Arguments

For Compile:
```

g++ -Wall -c "%f"

```

For Build:
```

g++ -Wall "%f"

```

For Execute:
```

"./%e"

```

---

### Post by sujinge9 on 2008-02-09
when I wrote my initial hello world program I named it "hello world.cpp". But now that I've made a new file using the option New-C++ source file, the compiling option is now usable. But as I try to compile, I get this error: g++: hello world.cpp : linker input file unused because linking not done

---

### Post by LaRoza on 2008-02-09
> **sujinge9 said:**
> when I wrote my initial hello world program I named it "hello world.cpp". But now that I've made a new file using the option New-C++ source file, the compiling option is now usable. But as I try to compile, I get this error: g++: hello world.cpp : linker input file unused because linking not done

It worked fine on my end...

What commands is it using? See if they are the ones I posted above.

---

### Post by sujinge9 on 2008-02-09
well I am getting "compilation successful", but nothing is popping up but I do get a beep and a message saying g++: hello world.cpp : linker input file unused because linking not done

But yeah, the commands are the same as the one's you have.

---

### Post by LaRoza on 2008-02-09
> **sujinge9 said:**
> well I am getting "compilation successful", but nothing is popping up but I do get a beep and a message saying g++: hello world.cpp : linker input file unused because linking not done

But yeah, the commands are the same as the one's you have.

You have to execute it.

Build->Execute

---

### Post by sujinge9 on 2008-02-09
lol, right, I'm retarted. OK, thanks a lot for the help everyone especially LaRosa. Hopefully I will not run into any more issues with basic compiling. 

Jinge

---

### Post by LaRoza on 2008-02-09
> **sujinge9 said:**
> lol, right, I'm retarted. OK, thanks a lot for the help everyone especially LaRosa. Hopefully I will not run into any more issues with basic compiling. 

Jinge

It is ok, IDE's are actually more complicated than the command line.

(LaRoza)

---

### Post by mridkash on 2008-02-10
I use netbeans IDE for C C++

Dont know much but its good for a try.

[http://netbeans.org](http://netbeans.org)

---

### Post by PuckStopper31 on 2008-02-10
With the Synaptec Package Manager you can install everything you need. I don't have the exact list of packages in my head but you can install the compilers and such and eclipse with the various plugins for doing C++ development and it works VERY smoothly. It doesn't have much for doing gui work but there are other tools for that purpose. Glade comes to mind.

Hope this helps.

PS.

---

### Post by dynamethod on 2008-02-29
gedit + terminal works fine

open up gedit, save the file as a .cpp, then gedit recognises the syntax, so it highlights it

then once your done writing the code, go to terminal and type in
g++ yoursourcode.cpp -o whateveryouwantocallyourexe

piece of cake, things like eclipse and so forth i just find overkill

---

### Post by Kazade on 2008-03-01
I would recommend [CodeBlocks]("http://www.codeblocks.org")

---

### Post by stratavarious on 2008-03-01
.

---

### Post by tubasoldier on 2008-03-01
For someone just learning programming a simple text editor like gedit, kate, kwrite, vim, emacs, or even nano is much better than an IDE. You shouldn't try to learn programming with an IDE because they can do so much for you and you loose out on learning how to really get down and dirty with the code.
I took an intro to Java course one time and the teacher insisted we used NetBeans to do it. Unfortunately at the end of the class not too many people knew much about java programming. However, they all knew how to get netbeans to make circles and boxes in java applets.

---

### Post by Kazade on 2008-03-01
I'm not sure I totally agree when it comes to C++...

C++ is an ugly beast, it requires a lot of duplication (class/function definitions and declarations) and it's difficult to debug and keep memory leaks in check and you spend a lot of time switching between files (headers and source). IMO a decent IDE with code completion, class browser and built in debugging tools (watches, breakpoints etc,) and easy configuration of the build makes life loads easier when coding in C++. 

I *could* code C++ in Geany/Vim/etc,, but I don't, there are too many times I just wanna shove a breakpoint in somewhere and debug the program. For languages like Python however Geany is perfect :)

It's definitely up to personal preference, my mate codes C++ entirely in VIM and on the command line, I think that would just drive me insane ;)

It also depends on the size of the project, if your program is only a few classes then a full IDE is probably overkill, but if your program is hundreds of classes, well, then that's when a full IDE really helps.

---

### Post by amarant on 2008-03-01
> **Kazade said:**
> I'm not sure I totally agree when it comes to C++...

C++ is an ugly beast, it requires a lot of duplication (class/function definitions and declarations) and it's difficult to debug and keep memory leaks in check and you spend a lot of time switching between files (headers and source). IMO a decent IDE with code completion, class browser and built in debugging tools (watches, breakpoints etc,) and easy configuration of the build makes life loads easier when coding in C++. 

I *could* code C++ in Geany/Vim/etc,, but I don't, there are too many times I just wanna shove a breakpoint in somewhere and debug the program. For languages like Python however Geany is perfect :)

It's definitely up to personal preference, my mate codes C++ entirely in VIM and on the command line, I think that would just drive me insane ;)

It also depends on the size of the project, if your program is only a few classes then a full IDE is probably overkill, but if your program is hundreds of classes, well, then that's when a full IDE really helps.

So, whats the best IDE in terms of code completion, debuggers etc?

---

### Post by rye_ on 2008-03-01
I'm afraid I haven't trawled the thread, so apologies if this  is a repetition...

codeblocks is a beauty and they have a nice stable release that's recently been upped to their website

Ryan

---

### Post by Kazade on 2008-03-01
Yep, CodeBlocks is what I use, it's awesome! ;)

---

### Post by monoufo on 2008-03-02
I just started literally hours ago.  Yesterday I didn't understand a single line of C.  I have been using Code::Blocks 8.02.  I chose it because it is cross platform and recommended by the guy whose tutorial i am following.  It's great so far,

---

### Post by intel on 2008-03-04
Eclipse CDT is in the same league as visual studio.

visual studio is better because the people from Borland (remember turbo C?) helped microsoft design it

---

### Post by DrMega on 2008-03-04
> **intel said:**
> Eclipse CDT is in the same league as visual studio.

So its torturously slow and full of bugs then?:)

I agree with others that Code::blocks is ace.

---

### Post by Joeb454 on 2008-03-04
Code::Blocks is a good choice, and I've found Anjuta is quite good as well, at the minute I'm using Anjuta :)

---

### Post by alecz20 on 2008-03-12
On Windows I used Visual Studio, and I got it to compile and run a Hello World program in about 5 minutes.

On Ubuntu I tried KDevelop, or something like that, it installed a bunch of applications, and shortcuts in the main menu.

I tried the one for C++, but I never got it to compile a simple Hello World program.
I guess that KDE has a lot of stuff, for a lot of things, but if it can't compile, then what's the point???
(It would give errors, like "no compile rules defined", or Run & make Friends issue, or no make defined)
I didn't understand how can they release an application that does not run?
Lately i found that you actually had to install other stuff, but nobody would tell you because they think it's common sense. After installing you had to configure hell lot of stuff, and so on.

Basically.... using an IDE to compile even a simple program si not worth it.

Recently, I tried Geany, and it worked "out of the box" (also I think I had plenty of compilers and library installed because I had compiled Wine).
The problem with Geany is that if you create a project, and then add a .cpp file with code, it will not compile. For some reason it will try to access a root's folder and get permission denied. But if you open a .cpp file outside of a project, it works fine.

Quite complicated and strange, isn't it?

---

### Post by tengobotas on 2008-05-03
I just setup gedit for simple c++ code with a terminal plugin and for someone just starting to learn programming its perfect. Most IDEs are just overkill and end up making things more confusing than they need to be for a person whos just starting out.

Truth is, vi/emacs are easy to learn the basics of and are quite forgiving because of the easy switching between editing mods. If I didnt have an extensive linux background then I would definitely suggest one of the two, not to mention they are both cross platform.

---

