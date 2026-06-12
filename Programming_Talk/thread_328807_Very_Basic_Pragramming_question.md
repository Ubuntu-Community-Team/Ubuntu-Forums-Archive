---
title: "Very Basic Pragramming question"
date: 2006-12-31
forum: Programming Talk
---

### Post by jae1227 on 2006-12-31
I have just bought some books on learning how to program Python and Java. I have been learning much about programming but I keep on wondering about other languages. When I was listening to security now this week they said something that made me think. They said to program on windows you really should have visual studios. They also noted that Apple includes its programming stuff on the install disc. So my question is: Is there a universal programming languages or a standard used for windows? I think it is C++ but does visual studios have a special version of   C++. I know on Linux there is the GCC. So if anyone can help me know why Visual Studios is so important to a windows programmer .

---

### Post by radu_chindris on 2006-12-31
Short story: there is the ISO C++ standard which specifies what C++ is in great detail, but C++ compilers may support only part of the standard (C++ is a very complex language). Furthermore, each compiler adds it's own extensions to the language, (see microsoft specific c++ features/etc) . Now, Visual Studio is a **development environment** for the win32 platform, it supports various languages (c++, vb and the managed, CLR stuff), and it is very tempting to use it on m$ platform due to the high level of integration, especially debugging support, etc. in other words it makes it somehow easier to develop apps on win32/clr/etc and to integrate with various m$ (innovative(TM)) technologies. Even if you can afford it, don't use it unless your job requires it. You'll learn a lot more by using just a plain text editor and the command line tools from platform sdk (now windows sdk as I recall)

hope this helps

---

### Post by coder_ on 2006-12-31
Pfff, Visual Studio isn't hard to learn!  It's basically the same as coding in Linux, but different in that you  press the "Build" button instead of writing a Makefile by hand and learning about how the compiler and linker and such work ;)

 *Mostly kidding ;)*

---

### Post by pmasiar on 2006-12-31
> **jae1227 said:**
> Is there a universal programming languages or a standard used for windows? .

There are 3 competing "application stacks" which are designed to be incompatible with each other as "vendor lock-in": MS with .NET and C#, Sun with Java and java libraries and tools (supported by IBM and many proprietary vendors as a way to battle MS's desktop dominance), and open-source stack LAMP: Linux, Apache, MySQL, Perl/Python/PHP/Ruby, with GNU utilities and GCC etc. Some tools from LAMP stack were ported to windows too, some were not, because it is hard: windows made deliberate decisions to be as incompatible as possible from Linux, like using backslash as path delimiter. Then there is BSD Unix and Apple...

C# is windows/.NET only (let's ignore "Mono" and it's unknown patent status), java is platform-independent for the price of being resource-hog and "enterprise-level" complicated. 

C, and C-based dynamic languages are easy to port: Python. Perl, PHP and Ruby run also on windows (with some restrictions)

>  why Visual Studios is so important to a windows programmer .

Statically typed languages like C++ and Java cannot avoid to have complicated libraries with complicated classes (=types), which are inherently hard to learn and big part of steep learning curve. To help write code faster and with less errors, sophisticated IDE (Integrated Design Environment) are used, which track class for every object and provide available methods. In addition, Windows OS has own rather complicated baroque API (Application Program Interface) libraries, which also become easier to use with the help of smart IDE. Big money can be made by selling these tools - so big money are sped to marketing to promote it. :-)

Dynamically typed languages are much simpler by design, with simpler API and libraries. Also, major dynamic languages are open-source (perl, python, php, ruby, bash), with no company behind them (php is exception, and Zend is no match to C#'s promoter MS or java's Sun). Perl, the oldest dynamic language of this family, has no dedicated IDE (and it's over-flexible syntax is not helping to gain one). AFAIK there is no dedicated Ruby IDE.

Exception is Python, which has substantially simpler syntax, and multiple IDEs, one of them (IDLE) part of standard language distribution. Python's policy to allow developing competing libraries "outside" until good "pythonic" (simple and intuitive) solution is found, then including it to language standard also help standardization. So Python2.5 comes with ElementTree as a astandard, and unless you parsed XML without it, you will never appreciate how hard it is - because with ElementTree it is so simple :-)

So as you can see situation is not simple, because companies involved are making money by making it complex, and then selling you tools to solve problems they created... :-)

There is no universal solution, you need to figure out what subset of problems are you interested to solve, and then look at the solutions used in that area. Fortune 500 companies prefer different kinds of solutions than startup aiming to be bought by Google (which btw uses python extensively).

---

### Post by jae1227 on 2006-12-31
So visual studio is just a program to help you program just like Eclipse is a program to help you program. But for Eclipse you can download the JDK from Sun. I just wonder is there a C++ compiler for windows like GCC is for UNIX.

---

### Post by pmasiar on 2006-12-31
> **jae1227 said:**
> I have just bought some books on learning how to program Python and Java. I have been learning much about programming but I keep on wondering about other languages.

If you are just learning to program, python is *much* easier to learn as first programming language than java. With python, you don't have to even know about Object-oriented approach until you need it - just use simple procedural approach and modules. Python library is also much simpler than Java. For reference, $10 Python pocket reference is enough - but java reference books are 1000 pages and more :-)

I started [http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/) - for beginners learning python, links to (online) books to read about language, data structures, and tasks to solve.

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by meng on 2006-12-31
pmasiar: thanks for the link!
jae1227: I recommend you learn one language at a time. Python is good to start with. You may like to branch out into java later. I did it the other way round, and I really think I would have been better off starting with python.

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by meng on 2006-12-31
> **phossal said:**
> I did it the other way around, too. But, while I agree that some might consider it "easier" to learn Python first, I believe it was better to learn a more conventional syntax than Python offers. It's a steeper learning curve at first, but it makes transitioning to something "simple", like Python, a no-brainer.
I would use the term 'rigorous' rather than 'conventional' to describe the syntax. Python syntax is less rigorous, there's no doubt. However, for many users I would argue that rigor is not as much an advantage as a disadvantage. But it's a controversial issue!

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by meng on 2006-12-31
> **phossal said:**
> Now you've convinced me. Not only is a conventional c-syntax a more rigorous way to begin, learning it in a strongly typed language like Java is a great way to go. Python is an awesome language, and it's less rigorous. Unfortunately, like Perl, for those who aren't (or don't know how to be) careful it's too easy to form bad habits while you're learning. 

Conventional c-syntax languages have blocks defined with brackets, and flow control patterns enveloped by parenthesis. Java can allow a person to learn those things without as much freedom to screw up as C++. Learning Java first would allow a new programmer to easily transition "up" to more demanding languages or "down" to less demanding languages, like php, perl, javascript, python, etc.
You raise excellent points, and I still see some advantages to beginning with the more rigorous and moving to the less. The question is whether insisting on rigor may raise the barrier to entry too high for some users, and discourage would-be programmers from taking things further. I don't really know the answer! But I do know that after 500 compilation errors in Java, you start to lose some enthusiasm ...

---

### Post by Mirrorball on 2006-12-31
No! Python's syntax is very rigorous, it even requires proper indentation. Python code is crystal clear, unlike Perl. It forms good habits. It's a lot easier to screw up  code readability with C-syntax and brackets. And Python is a [**strongly** typed language.]("http://www.artima.com/weblogs/viewpost.jsp?thread=7590")

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by Mirrorball on 2006-12-31
> **phossal said:**
> If you want to WRITE device drivers, read binary, program AI Robots, etc. You do that in a language that has brackets and parenthesis.
To do all this, you need to know more than how to press the "{" key. Learning a new language is too easy. Learning how to program, how to design a program, how hardware works, how system security is done, is hard. And while you are learning it all, you will have a better time with Python. The "cheesy" programs are *extremely* useful, they will save you a lot of time to learn how to write device drivers. You can write a 4-line program in Python that does the same thing that a 20-line program in C does. It's a lot easier to get a 4-line program right, and a lot faster to write.

And there are more to Python than quick scripts. Nicotine (the Soulseek client) was written in Python. Portage, the Gentoo package manager, is a Python script.

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by pmasiar on 2006-12-31
> **meng said:**
> I would use the term 'rigorous' rather than 'conventional' to describe the syntax. Python syntax is less rigorous, there's no doubt. However, for many users I would argue that rigor is not as much an advantage as a disadvantage.

I would not call python syntax less rigorous. It has less C-like artifacts, thats all.

It is "for i in range(1,10):" versus "for (i=1, i<10, i++){" --  which one is more "rigorous"? Both are equally rigorous, Python syntax just *looks* simpler -- because it was **designed for readability**. Core developers talk about readability, and features are rejected sometimes based on that. 

I agree with you that so called "rigor" is obstacle when learning language. I was not lucky enough to have Python as my first language (back then it was algol60 and PL/1, Pascal was language for lucky students like Python is now). But I had powerful motivation: I had to learn it to pass the grade, no way around it (and yes I did enjoy it even back then). If someone is learning language for fun by herself, why to start with a language which is more about "rigor" and less fun? I strongly believe that simple language like python, with shallow learning curve, which allows newbie to solve (simple) problems and **have fun along the way**, is more motivational, more useful, more instrumental in reaching the ultimate goal (learn programming) than painful experience with "rigorous" language like C++, C# or java.

Also, after learning so many languages, you will start to understand that some parts of what you thought are parts of programming routine are just artifacts related to selected language: 

I was trained to check return conditions and GOTO if error. Languages without  GOTO was radical idea back then. How you even can handle errors without GOTO they asked? Now we have exceptions, which are much better suited to handle unexpected situations. If you know assembler, you can see how close C is to machine code. Garbage-collected memory management (as java, python, perl etc has) was another recent radical idea, but it is becoming mainstream - C# has it too. Dynamic typing is just yet another idea which will be as mainstream (in couple years in non-kernel userspace code) as GOTO-less languages are now. Just wait and see! :-)

---

### Post by Mirrorball on 2006-12-31
Even kernel programmers know and use bash/Python/Perl/Ruby/etc. When they want to rename 2000 files, I don't think they do it in Assembly, which by the way doesn't have C syntax. :P Like pmasiar, I wish Python had been my first language too.

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by Mirrorball on 2006-12-31
> **phossal said:**
> Okay, you win. I wish everything was written in python. My current project is reversing a data file, and I really, really wish it was written in Python. Give me an obfuscated, decrypted-at-runtime .py file any day. 

:p
I don't know how you do it exactly, but reversing a data file seems a perfect job for a Python script. Why lose a day to write a C program when you can do it in an hour with Python? Then you can use the time you saved to learn Artificial Intelligence. Python is extremely readable (they say it's "executable pseudo code"), no annoying $'s and @'s in variable names. And once a Python script gets translated into a Python bytecode .pyc (or .pyo) file, it doesn't get "decrypted at runtime" anymore.

---

### Post by Mirrorball on 2006-12-31
> **phossal said:**
> The elite still learn assembly, still learn c, still learn c++. I'm fairly sure there are way more operational lines of c and c++, way more lines of assembly ;) than all the python in the world. Just a guess.
I do know assembly, C, and C++. I'm of the opinion anyone should learn as many programming languages as possible. Of course there are more C programs than Python scripts in the world. C is a faster, older, and better known language. It's simple and powerful and a classic. I myself never found a use for Java. Python > Java. And for a novice programmer, I recommend Python. Why struggle with C when you can do everything you need as a novice with Python? Understand what object-oriented programming is first, then C++ will take you a week to learn. Not hard work.

I use C++ for performance, PHP for web development, and Python for everything else, including parsing files and analyzing my experimental data.

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by meng on 2006-12-31
This is a great discussion, but we may have slightly lost sight of the main purpose of the thread, which is to advise the OP on a good programming choice. We don't seem to have an idea what he (making a gender assumption) envisages as the most likely programming tasks he is likely to be involved in over the next 2 years.

---

### Post by Mirrorball on 2006-12-31
> **phossal said:**
> yes, yes. Everything should be done in Python. Rewrite Windows in Python, tell Mr. Torvalds his kernel is "efficient", but it could be much more efficiently "written" in Python, reverse binaries with Python, do your laundry in Python.
I wish I could do my laundry in Python. :( My washing machine must be better than C.
> **phossal said:**
> Torvalds wrote in C - yes, because it was available at the time, but he could still program in Assembly, and even translate from binary.
Let him learn how to write a loop first, will you?

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by pmasiar on 2006-12-31
> **phossal said:**
> lol But I'm inclined to think that anyone who asks, "What's a good first language to learn?", over "How do I rename 2000 files?", might be fantasizing about "being a programmer", which includes some activities that are "hard" as you put it earlier. Security, Hardware, etc. The elite still learn assembly, still learn c, still learn c++. I'm fairly sure there are way more operational lines of c and c++, way more lines of assembly ;) than all the python in the world. Just a guess.

Obviously less lines in python - you need 1/3 lines than in C to solve same problem in Python:-)

Seriously I don't dispute that there are more lines in C than in python. It is possible that there are 50% as much of lines in COBOL than in java. Wanna learn Cobol to maintain it? Why not?

From your comments it looks like you consider kernel problems as most complicated. They are complex, but many other areas are as complicated, or more. Let me tell you that people solve say in R (for statistics) such complicated problems that kernel hacker brain will boil. :-) I know I tried. :-) Or if you have special device and just 16K of RAM, there is only one language to save your A$$ - Forth - and it is still used and loved in device community. And Forth is *the* simplest and most extensible language, with no exceptions (I don't tell about simplicity and safety - Forth is complex, dangerous language - but oh *so* powerful). And where is Lisp in your picture? Not even mentioning real esoteric languages *designed to be hard*, like brainfuck or Befunge  [see here]("http://ubuntuforums.org/showpost.php?p=1947492&postcount=22")

Original question was by someone learning programming. My suggestion is "learn python, then learn whatever language is used in your area of expertise". Not all people hack on kernel in C (fortunately) - some people solve other problems, and other languages are better suited, or traditionally used. But python, ruby and friends will become good enough and fast enough, and will keep creeping in. Languages evolve. And 100 years from now, java will be as obscure as Cobol is now, and the language used will be pretty much something designed to be simple, readable and fast enough. Read more about 100 years language - [like Python is today]("http://www.paulgraham.com/hundred.html").

---

### Post by Mirrorball on 2006-12-31
Well, let him decide if he wants to look 1337 or learn useful stuff easily. (When I was 15, I was learning Qbasic. This new generation has a brighter future ahead.)

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by meng on 2006-12-31
> **phossal said:**
> Are you both retarded?
The discussion has for the most part been worthwhile, on both sides. Please don't spoil it by posting like this.

I understand that comparing languages can be like comparing religions or politics, but really there's no need to turn nasty.

---

### Post by Mirrorball on 2006-12-31
Transitioning from a non-C syntax to a C-syntax is also easy! Do you think he needs years of programming experience in order to write brackets?! Who cares about the difference between:
```
if a < b:
```and
```
if (a < b) { 
```Honestly... Do you think that when he gets to the point of writing device managers, he will be worried about working with a different syntax?

---

### Post by meng on 2006-12-31
Okay, MY advice to the OP is (without really understanding what sort of programming he thinks he might be doing in the near future) that both java and python are reasonable choices for crossplatform programming, and a serious commitment to learning either of these will teach you valuable programming principles (which go beyond mere syntax). I hope the books you have are both decent. If you haven't yet made up your mind, then try one for 1-2 weeks, and then the other for 1-2 weeks and see which one you prefer. Then, once you've made a decision, put the other book away and concentrate on one language for the time being. It is more important to learn about the overall gestalt of programming, not language-specific things like syntax.

Ultimately, I don't think there is a right or wrong choice that applies to all newcomers. So just throw yourself into it, and best of luck!

---

### Post by phossal on 2006-12-31
[Edited]

---

### Post by pmasiar on 2006-12-31
> **Mirrorball said:**
> Honestly... Do you think that when he gets to the point of writing device managers, he will be worried about working with a different syntax?

Not at all.

My worry is, by making emphasis on learning first a "proper rigid" language like java, lots of people will be persuaded that programming is way too hard for them and better left for the "experts". 

I have first-hand experience with non-matematics scientists, like biologists and medical doctors struggling with programming in java. What they need to do is often simple manipulations, but they spend great amount of time to explain programmer (me) what needs to be done and how, and then checking results and finding misunderstandings - because trust me, biology is *very* different. For biologist, "buffer" is the solution (water) used to dissolve something, so "flush the buffers" has a *very* different meaning for her.

Using simple language like python will allow more people get into programming. Not into kernel hacking - just use simple scripts to solve simple problems they have. Because learning biology is so damn hard (I really tried :-) ) and programmer's mind does not wrap easy around fuzzy biology concepts, our only hope to find cure for cancer is biologist themselves to do the programming :-)

I just want you to get out of your basement and see that many people can happily use programming which does not require speed  of C. The faster CPU will become, the less important it will be. My first computer had 1 MB RAM and 12 MHz. I doubt it would boot commandline Linux now. many new users will be very different from what we had until now. More powerful CPU allow more wasteful use of CPU cycles, less experts solving own problems without "high priest" of "real programmer".

Of course your plan might be to force all to learn C/C++/java as first language, many will fail and dislike programming, as result there is *less* programmers on the market and less competitors for you. If so, I have bad news for you - it's not happening :-)

---

### Post by pmasiar on 2007-01-01
It looks like phossal self-censured all his posts. That's sad, because I really enjoy talking about some of these issues - in discussion yoy can learn more about not only about position of others, but you can think more deeply also about your own position, see it from different angles.

Of course having thick skin helps. :-)

I do hope phossal will stay around and will fight for his position in future discussion, so I can learn something.

phossal, you may want to read [Devil's dictionary]("http://en.wikipedia.org/wiki/The_Devil%27s_Dictionary"), especially definition of discussion: 

"DISCUSSION, n.
    A method of confirming others in their errors." 

Lots of other rather cynical definitions too. Fun to read.

---

### Post by jae1227 on 2007-01-03
What I seem to find appelling about Java is the JVM. This seems to make it easy to port software to other OSs.

---

### Post by phossal on 2007-01-03
> **jae1227 said:**
> What I seem to find appelling about Java is the JVM. This seems to make it easy to port software to other OSs.

We used Java at work to shore up some weaknesses in an application that uses a legacy database. Java's JDBC was an alternative because someone actually wrote a commercial JDBC Driver for the DB. It was a no-brainer. ODBC was not really an option because of the additional abstraction, and the unusual inconsistencies (like # for time and date value delimiters).

The Java solution has worked well in our Windows network because the jar files (which can function as executables when you need them to) can sit on our server, and run independently on each node. By creating a shortcut to the desktop, the individual machines load the byte code into their respective JVM's. 

Each time the program was updated, distributing it was a breeze. Copy and paste 1 file - straight from eclipse. 

In addition, we added Ubuntu machines into our network recently. Guess what? With Samba, which allows the Ubuntu machines to access the Windows server, they work "out of the box" too. It's blissful.

The only downside for us is that the auto JRE updates install new folders, which installs new java.policy (etc.) files. If you're using any configuration files, granting permissions to certain code bases, or extensions in the JRE, you have to update those each time.

---

### Post by phossal on 2007-01-03
> **pmasiar said:**
> phossal, you may want to read [Devil's dictionary]("http://en.wikipedia.org/wiki/The_Devil%27s_Dictionary"), especially definition of discussion: 

"DISCUSSION, n.
    A method of confirming others in their errors." 

I read Ambrose Bierce long before I turned 20. His short stories are much better than the dictionary, which is, at best, a distraction. I can quote the first line of many books and stories, but the last line of only one: A Horseman in the Sky, Bierce, A. It is definitely one of my top-ten favorite stories of all time.


[A Horseman in the Sky]("http://www.online-literature.com/bierce/1999/")

---

### Post by Wybiral on 2007-01-03
In the immortal words of phossal....
> **phossal said:**
> [Edited]


Anyway...
> What I seem to find appelling about Java is the JVM
Many interpreted languages use a VM, a VM is just a way to interpret bytecode through functions that act as if it were machine code (with a middle man). Now, the JIT compiler (and I'm not sure how it chooses which to use, from what I've read it's very wise and mysterious, but I guess that will change soon) that's another story...

---

### Post by jae1227 on 2007-01-03
Is python less powerful than java when it come to fulfledged programs. I understand for little things python is great but for something for complicated i am not sure how it stands up.

---

### Post by Wybiral on 2007-01-03
Complicated isn't the issue... Your java program might be a little faster, that's probably the only advantage. But python is well equipped to handle complicated programs, comparable to C++ even. It has a lot of the OOP functionality that C++ and Java have, but unlike Java, python doesn't require you to use OOP.

---

### Post by Mirrorball on 2007-01-03
No, they are just as powerful(-less?) and slow. Java may actually be slower and Python is easier. But Java will run everywhere.

---

### Post by jimcooncat on 2007-01-03
I'm going to python after considering the same situation the OP is. Writing cross platform for the general public consumption is my target though. 

I've experienced very bad behavior from Java on Windows 98 and ME to know that I wouldn't want to that environment. It's not any of Sun's Java crew that's to fault though, M$ changed the virtual machine for the worse, IIRC.

Surprising in my remote area how popular an OS it is, though. If you're writing to include an older audience, you'll find a lot of people with second-hand machines that their kid sets them up with so he can take a brand new one to school. And they run 95 and 98 (till they break), 98SE and ME.

I haven't written any Python for these machines yet (but soon). I can tell you that ActiveState Perl goes very nicely and it's COM interface can help to suck users data out of proprietary formats. That's what I'm hoping Python can do for me. I'd like to deal with a Python class to manage the data, as opposed to the "Perl Way". TIMTOWTDI

Hope my rambling on was enjoyable.

---

### Post by jae1227 on 2007-01-03
I feel that python will be easier to learn that Java but i don't know how portable it will be. Portability is what I find very attractive about Java.

---

### Post by pmasiar on 2007-01-03
> **jae1227 said:**
> I feel that python will be easier to learn that Java but i don't know how portable it will be. Portability is what I find very attractive about Java.

There is no easy painless way to portability. Java is kinda portable, but there might be slight differences in implementation of different JVM (mockingly called "write once, debug everywhere"). Java is slower than C in execution and slower than Python in development - depending of you POV it might be the "sweet spot" between, or both of two evils. :-)

WxPython is said to be reasonably portable. Don't try to bite too much, and don't think you can outsmart everyone. Lot of people care deeply about portability, but there is no known silver bullet (we would know it there is I hope) and to have results they make compromises. Set up and reach your own milestone, and you will learn how it is in your particular case, then you can adjust your course.

You still did not told us (unless I missed it) what kind of app you plan. Is it secret? :-) Portability of web apps is differs from desktop, etc.

---

### Post by Wybiral on 2007-01-03
Another thing that disappoints me about java is it's CPU usage... Every time I open a java app, my computer explodes. 9 times out of 10 java is just too CPU intensive for me to want to use apps that require it. One example is frostwire... I love the program, but hate using it because it takes up all of my CPU resources. Had they wrote it in C++/Python it probably wouldn't do that and I would use it a lot more. Another example is eclipse... It's just too slow and requires too much CPU power.

Often times I think java just has too much overhead and a smaller, simpler solution exists. C++/Python can replace java a lot of the time, and they don't require as much CPU usage.

---

### Post by jimcooncat on 2007-01-05
If you're into GUI programming, why not try wxGlade? It's available in Ubuntu and as a Windows exe installer.

[http://sourceforge.net/project/showfiles.php?group_id=58225](http://sourceforge.net/project/showfiles.php?group_id=58225)

I don't know Python yet, but I'm having fun playing around with it. Supposedly it can write Perl and C++ too.

---

### Post by jae1227 on 2007-01-08
I have a few idea of what sort of programs i would want to make but I really don't know how hard it is to create a program yet. I have an idea for a simple presentation program where your primary monitor controls the secondary monitor to display pictures and then I could go from there. So to some I think it would work is to make a UI for the primary monitor. It could have a list of pictures. So you could drag and drop picures into the UI. Then from the UI you could launch the picture and the second monitor will display the picture. This would be usesfull if the second monitor was a projector. Then the audiance of the second monitor could only see the picture. I hope theat makes sence.

---

### Post by jimcooncat on 2007-01-09
So, you see a file list, and when you select a file, it sends the filename to a full-screen image viewer running it's output to a second display. 

Looks as if qiv might be a good choice for an image viewer. The --watch option reloads the image if it has changed on the disk. So maybe you could just have your file list change a symlink, and qiv would automatically display the linked image for you. (No, I haven't tested it to see if that works.)

Sounds like an excellent first-time programming project. If the qiv thing works, you could just do a simple bash script looping a "zenity --file-selection" command for a fairly nice looking working model. 

You can probably implement the front end (the file selection, loop, and symlink changer) of this in almost any language or environment that lets you write to the file system. Than you can start adding features, such as drag-and-drop.

Replacing the image viewer portion, if you choose to do so, will probably be much more of a challenge. But there are plenty of open source projects out there -- find one you like and figure out how they did it. There are also tools like ImageMagick from which you can pick little pieces of functionality.

---

