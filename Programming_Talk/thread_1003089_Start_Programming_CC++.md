---
title: "Start Programming C/C++"
date: 2008-12-05
forum: Programming Talk
---

### Post by corujask8 on 2008-12-05
Hi, I'm new at Ubuntu and I want to start programming. I chose C to start, and I want to know what compiler can I use. I tried to to use GCC, but when I put gcc in terminal, appears some message saying "no input files". Do you know what should I do?

---

### Post by ibutho on 2008-12-05
What command did you run and what was the detailed output. Try something like
```
gcc hello.c -o hello
```

---

### Post by Daveski on 2008-12-05
Try:
```
man gcc
```
or
```
gcc --help
```

These work with most Linux commands.
Reading the documentation (or at least scanning it) will give you some clue how the command is expecting to work. In this case the compiler expects at least the source code. If you were expecting a development environment, then you need to look elsewhere as the compiler is just a compiler.

---

### Post by corujask8 on 2008-12-05
At first, I put only "gcc", but I put these commands too and nothing...
Remembering that I not a programmer, I'm starting to learn...
Thank's.

---

### Post by juanoleso on 2008-12-05
Daveski is right, GCC will only compile your program, which means turn it from C to something that the computer will be able to use (binary file).  An IDE (integrated development environment) is probably what you are looking for.  An IDE is a program that will help you write code by doing different things.  Eclipse is used a lot, but I have never so I'm sorry I can't give you any advice with it and I don't even know if it supports C...

Also, for graphical programs, you may want to look into the GTK or Qt libraries.  Libraries are sections of code that have already been written and that you can use in your code so you don't have to "re-invent the wheel."

After you have written your code, you will then use GCC or another compielr to compile your files into a program.

I don't know how much you know, so I am putting what I know.  =-D  I am not a programmer either, though, so anybody please correct me.

---

### Post by kcy29581 on 2008-12-05
To the OP:

I am currently teaching myself C++ and I am using Netbeans as my IDE. It helps a lot, as your main focus is writing good code and the IDE assists with compiling/linking.

Eclipse was mentioned earlier as well, and I strongly suggest you install both and try them out to see which you prefer. I advise that you get the latest versions from their respective websites as the versions in Ubuntu are not up to date.

Hope this helps!

---

### Post by Daveski on 2008-12-05
> **corujask8 said:**
> At first, I put only "gcc", but I put these commands too and nothing...
Remembering that I not a programmer, I'm starting to learn...
Thank's.

Do you have a specific reason to try C? If not, then I recommend Python as a good intro to programming. You'll need to find a nice Python tutorial to follow, but if you just type *python* at the terminal, you will be in an interactive interpretor.
You can graduate to writing in a text editor quite quickly. There is no compilation, so you can just run *python myprogram.py* to interpret your code you have written in a text editor (and saved as myprogram.py).

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

---

### Post by newbee70 on 2008-12-05
> **corujask8 said:**
> Hi, I'm new at Ubuntu and I want to start programming. I chose C to start, and I want to know what compiler can I use. I tried to to use GCC, but when I put gcc in terminal, appears some message saying "no input files". Do you know what should I do?

*****@hooters:~$ cd Documents/cprogram
*****@hooters:~/Documents/cprogram$ ls -a
.       characters.cpp                 l_cproc_p_11.0.074_Release_Notes.zip
..      characters.cpp~                number.out
1.cpp   c_ug_lnx.pdf                   powers.cpp
2.cpp   l_cproc_p_11.0.074_ia32.tgz    powers.cpp~
2.cpp~  l_cproc_p_11.0.074_README.txt  powers.out
a.out   l_cproc_p_11.0.074_redist.tgz  stringstreams.cpp


*******@hooters:~/Documents/cprogram$ g++ 1.cpp   to compile the program
*******@hooters:~/Documents/cprogram$ ./a.out     to run the program
HEY, you, I'm alive! Oh, and Hello World!

???????@hooters:~/Documents/cprogram$ 

simple enough.

---

### Post by cmay on 2008-12-05
the reason why it say gcc:no input files 
is simply that ubuntu does not ship the gcc compiler and development essentials with the default install.  so everytime anyone experienced or pure newbie wants to compile some thing they ask this same question. the cure is to install the build-essential package. there is absolutely nothing wrong with what you are doing (or asking) but i believe this should do the trick for you
[php]sudo apt-get install build-essentials[/php]when you test it you may not use a tittle called test.c since it will conflict with the program in ubuntu called test so choose hello.c or my_file.c or what ever instead. 
then write a simple test program like this 
[php]#include <stdio.h>
int main(int argc ,char **argv)
{
    printf("woohooo it works \n");
return 0;
}
[/php]and save it in your home folder. this is as exampel hello.c
then as someone already showed you use gcc this way 
[php]gcc -o hello  ./hello.c[/php]and run the program with the command 
[php]./hello[/php]and then have fun ;)

ohh by the way i am getting a bit tired of having the build-esssential package missing on the cd of ubuntu but i like ubuntu very much anyway. its also very great they put code blocks in the repositories and you will maybe use that a lot sometime maybe as its a good IDE but there is also netbeans or geany which is the best light wight and to me most usefull application there is when it comes to handy little IDE . 

so to get a good ide use gedit i can reccomend " sudo apt-get geany "or sudo apt-get codeblocks. 

hope it helps..

---

### Post by Primefalcon on 2008-12-05
```
g++ fileToCompile.cpp -o programName
```

After you have gcc installed the above will compile it

---

### Post by cmay on 2008-12-06
> **Primefalcon said:**
> ```
g++ fileToCompile.cpp -o programName
```After you have gcc installed the above will compile it
yes but 
> I chose C to start, and I want to know what compiler can I use. I tried to to use GCC, but when I put gcc in terminal, appears some message saying "no input files". Do you know what should I do?not so good an idea if he tries to learn c first and get stuck at this compiling c code examples from his tutorials as if they where c++ 

OP has not returned anyway so we will never know if he found out what he needed to. but if anyone else reads this tread all the information needed is here already by now. 
expect off course that gcc stands for the gnu compiler collection and there is more than just a c compiler  in that . if one wants to learn c++ then the compiler to use is not gcc but g++ and  still the package to fetch trough apt - get will still be the build essentials . to get rid of the annoying gcc cant find any input files message. sometimes it also helps too use .'/' current directory in front of the file name so gcc knows where to find the file to compile. there is too many of these post asking this question by now where some gets moved and put in the programming talk section that i am not going to ask the mods to move the tread but i think there is already given all info needed to compile a single hello world program and if op just could mark it tread solved or something then others will have a chance at finding this information with out having to open a whole new tread once again.

---

### Post by corujask8 on 2008-12-06
Thank's for all comments, but I tried all ways to use GCC and G++, and nothing...
I tried to download the IDE's in terminal, but I only did it in synaptic.
I'll try to use, and some error or success I'll report here.
Thank's again!;)

---

### Post by cmay on 2008-12-06
did you get the build-essential package ???

what i have posted of directions has to work. otherwise it can be a failure in the gcc installation which i however higly doubt. as i seen many ,many post where the only problem is the missing build.-essentials and only one time i heard of an actually broken installtion of gcc - i may add i have installed this many many times by now and i have never had a broken or misconfigured gcc installation. 

can you please post what ever you do. everything is not easy to figure out what means exactly. besides that  there is only a few ways to do it right.

can you post what you do and the compiler log /messages.

---

### Post by bapoumba on 2008-12-07
Moved to PT.

---

### Post by pmasiar on 2008-12-07
> **corujask8 said:**
> Hi, I'm new at Ubuntu and I want to start programming. I chose C to start, ... Do you know what should I do?

Sadly, I am first from the "experts" around to challenge your choice.

C is not, never was, and never will be, a good language for a beginner like you. Of course you are free to do whatever you want when wasting your own time, but according to my 20+ years experience, simpler language targeted to first time programmers wold be more productibe for you, more fun, and less time spent on answering  questions for rest of us.

See stickies, see poll, see discussion about this issue.

Of course I do not care personally about you, learn C if you want, or LOLOCODE or brainfuck, I am not going to answer your questions anyway. 

But before dismissing my advice, try for hour Python's interactive shell, and couple tutorials from wiki in my sig. I know for sure you will advance further into programming in that hour than in a week of studying C.

Good luck, whichever way you decide to go!

---

### Post by Daveski on 2008-12-07
> **pmasiar said:**
> Sadly, I am first from the "experts" around to challenge your choice.

I mentioned Python as a better place to start earlier.

> 
But before dismissing my advice, try for hour Python's interactive shell, and couple tutorials from wiki in my sig. I know for sure you will advance further into programming in that hour than in a week of studying C.

Good luck, whichever way you decide to go!

+1

---

### Post by mike_g on 2008-12-07
I agree that python would be a better starting point but that:
> Of course I do not care personally about you, learn C if you want, or LOLOCODE or brainfuck, I am not going to answer your questions anyway.
That was uncalled for.

---

### Post by eeeandrew on 2008-12-07
Hi, I also recently started learning C++ coding at University. I am using the eclipse IDE. To install it go to synaptic package manager(under system->administration) and search for eclipse. You need to install the eclipse package itself and all its dependencies. You also want to install eclipse-cdt and its dependancies(the latter is the C++ coding tools). When creating the project use the "managed make C++ program" option. Also be aware that for the source files you need to specify the file extension which for most purposes is .cpp . I had a few difficulties getting this to work but this covers most of them. 

Hope this is useful,
Andrew

---

### Post by namegame on 2008-12-07
> **mike_g said:**
> 
That was uncalled for.

I disagree, the "resident experts" on this forum (CptPicard and pmasiar, just to name two.) usually don't concern themselves with "trivial" discussions, such as this one. The points they make are both valid and insightful. I enjoy reading what they have to say, but I never comment on them as I am not qualified compared to them.

Anyhoo, I think pmasiar makes a very valid point. C is probably a waste of time as a first language, especially in this case.

---

### Post by pmasiar on 2008-12-07
> **mike_g said:**
> That was uncalled for.

Well, usually after I challenge some beginner struggling to learn C++, and suggest to start with Python, 20 posters attack me, and 50-posts flamewar is about my right (or lack of it) to suggect different language if OP wants C/C++. Happened so many times. So  I just wanted to say do do not care about that flamewar.

As always, for me it would be easier just to igore poor schmo and not waste time responding: let him get burned by C++. I got involved only because this is so obviously FAQ and no poster mentioned reading stickies (and poll), where far better arguments were given.

---

### Post by slavik on 2008-12-08
What have we learned so far?

1. C++ is not C (and vice versa).
2. pmasiar considers himself an expert in quotes (whatever those mean).
3. pmasiar was a starting computer science student well before Python or C++ existed. I am pretty sure at that time PASCAL and BASIC were used to teach programming to beginners (and MIT used Scheme).
4. Somehow, a question of beginning with C turns into C++ vs. Python as a first language. Would be funnier if it turned into Java vs. Python.
5. pmasiar says explicitly that he does not care what you do, but gives advice anyway. Feels like reverse psychology to me. (I am in agreement with what mike_g said, it was uncalled for IMO). I know, pmasiar, that you don't care for the flamewar, but then maybe there needs to be a discussion on encouragement, even if the learner is bound to fail.
6. There are experts here??? Sorry, but I do not think that anyone on this forum has code base big enough to be considered an expert in anything. Everyone knows something about something a little more than the rest, but it doesn't qualify them as a unilateral expert.

Also, why is it that NO ONE suggested to corujask8 to read the sticky entitled "Programming Tools and References for Many Languages" which has a link in plain view to a thread entitled "FAQ: Compiling your first C or C++ programs." LaRoza made a very good effort to organize some nicely written information (thanks go out to those members as well, in this case, aks44 for writing the above mentioned FAQ). Let her effort (as well as the effort of other members) not be spent vain.

---

### Post by jdong on 2008-12-08
Guys this is absolutely **ridiculous** -- does every newcomer's programming question have to turn into a language debate?


Whether or not you think the OP should've used Python or Ruby or Java or LISP or whatever is NOT THE POINT. He came asking a question about C/C++ and that's the question that would be appropriate to answer, not an attempt to derail the OP to try the language of your choice that you believe is suitable for a beginner. If the OP instead asked which language is best for a beginner, then that's a different story.

In the future, please respect that. For now I don't see this thread going anywhere useful, so I am closing it. Sincere apologies to the OP for our inability to answer questions without changing the question.

---

