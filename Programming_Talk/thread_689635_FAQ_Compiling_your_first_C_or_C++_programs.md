---
title: "FAQ: Compiling your first C or C++ programs"
date: 2008-02-06
forum: Programming Talk
---

### Post by aks44 on 2008-02-06
So you're willing to write your own C or C++ programs, or simply compile someone else's code? This guide will get you started...

This FAQ assumes you're trying to compile *error-free* code. To actually learn the C or C++ languages, see the [How to start programming](http://ubuntuforums.org/showthread.php?t=333867) thread.
If you encounter compilation problems, you may want to check this thread: [Troubleshooting common C and C++ compilation errors](http://ubuntuforums.org/showthread.php?t=691451).




[SIZE="5"]**0. Make sure the [COLOR="Blue"]build-essential[/COLOR] package is installed**[/SIZE]

This package installs the essential tools needed to build C and C++ programs. Don't try to install individual tools by yourself, experts made that package for a good reason...
```
sudo apt-get install build-essential
```




[SIZE="5"]**1.a Compiling your [COLOR="Blue"]first C program[/COLOR]**[/SIZE]

Copy & paste this code into a new file. Save the file as **main.c**
```
#include <stdio.h>

int main()
{
  printf("Hello World!\n");
  return 0;
}
```
Open a terminal, go to the directory where you saved **main.c**, and type:
```
gcc main.c -o test
```If all went fine, nothing is printed and you get back to the shell. Now, run it:
```
./test
```"Hello World!" gets printed in the terminal.

**Explanations:**[list][*] **[COLOR="Navy"]gcc[/COLOR]** is the C compiler
[*] obviously, **[COLOR="Navy"]main.c[/COLOR]** means that the compiler must compile this file. If you want to compile several source files into a single executable, just list them all here.
[*] **[COLOR="Navy"]-o test[/COLOR]** means "***[COLOR="Navy"]o[/COLOR]**utput the result of the compilation to an executable file named **[COLOR="Navy"]test[/COLOR]***". If this part is omitted, the executable will be named **a.out** by default.
[*] **[COLOR="Navy"]./test[/COLOR]** runs the newly compiled executable. The **./** is needed because of the way the shell works (the current directory **.** is not in the PATH by default).[/list]



[SIZE="5"]**1.b Compiling your [COLOR="Blue"]first C++ program[/COLOR]**[/SIZE]

Most of what I just said regarding the compilation of C programs also apply to C++ programs.
The two main differences (besides the language itself) are:
[list][*] **[COLOR="Navy"]g++[/COLOR]** is the compiler that you must use.
[*] you should use a **[COLOR="Navy"].cpp[/COLOR]** file extension rather than a **[COLOR="Navy"].c[/COLOR]** one[/list]
```
#include <iostream>

int main()
{
  std::cout << "Hello World!" << std::endl;
  return 0;
}
```
```
g++ main.cpp -o test
./test
```




[SIZE="5"]**2. [COLOR="Blue"]Paranoid programming[/COLOR] is good for your health!**[/SIZE]

Many beginners want to avoid compiler errors and warnings at *any* cost, which often leads them to ignore the "cryptic" messages the compiler outputs and to tinker anxiously with the relevant line until the error goes away.
**Don't fall in that trap!** The compiler is your friend, the messages it outputs are *kind advices* rather than *punishments*. You should really take the time to try and understand those messages, this is a very good way to improve your code's quality.

As a matter of fact, most seasoned programmers set the compiler's warning level as high as possible, so that it catches the little errors they make when they aren't paying much attention.

Here are a few command line switches to enable some warnings and language features (check the manual for detailed information):[list][*] **[COLOR="Navy"]-std=gnu99[/COLOR]** (C only) enforces the latest C standard (1999), plus GNU extensions ***(must be explicitely specified)***
[*] **[COLOR="Navy"]-std=gnu++98[/COLOR]** (C++ only) enforces the 1998 C++ standard (but the STL now supports most of C++0x TR1 anyway), plus GNU extensions *(this is the default for C++ code)*
[*] **[COLOR="Navy"]-Wall[/COLOR]** enables most warnings ***(very useful)***
[*] **[COLOR="Navy"]-Wextra[/COLOR]** enables more warnings ***(very useful)***
[*] **[COLOR="Navy"]-Wwrite-strings[/COLOR]** warns when you misuse plain old C string constants (aka. deprecated cast from const char* to char*) ***(very useful)***[SIZE="1"] (see [[SIZE="1"]this discussion[/SIZE]]("http://ubuntuforums.org/showthread.php?p=4331515#post4331515") for more in-depth information)[/SIZE]
[*] **[COLOR="Navy"]-pedantic[/COLOR]** issues warnings when strict ISO compatibility is not met *(the name says it all: pedantic, but it can be useful once in a while)*
[*] **[COLOR="Navy"]-Woverloaded-virtual[/COLOR]** (C++ only) warns when virtual functions are overloaded in derived classes ***(very useful)***
[*] **[COLOR="Navy"]-Weffc++[/COLOR]** (C++ only) warns when some key point of Scott Meyer's *Efficient C++* and *More Efficient C++* books are not met ***(good practice)***
[*] **[COLOR="Navy"]-Wold-style-cast[/COLOR]** (C++ only) warns when you use old-style C casts in a C++ program ***(good practice, you should be using the new-style C++ casts)***[/list]



[SIZE="5"]**3. [COLOR="Blue"]Useful tips[/COLOR]**[/SIZE][list][*] the **[COLOR="Navy"]-g[/COLOR]** flag instructs the compiler to include debugging information, so that you can debug your program with **gdb** itself or any **gdb** frontend.
[*] **sudo apt-get install manpages-dev** to help you make sense of compiler warnings and errors.[/list]



[SIZE="5"]**4. [COLOR="Blue"]Read the manual![/COLOR]**[/SIZE]

Plain old manpage:
```
man gcc
```

HTML version of the gcc manual:
```
sudo apt-get install gcc-doc
```
Once installed, point your browser to **[COLOR="Navy"]/usr/share/doc/gcc-doc/gcc.html[/COLOR]**






Thanks to so many people @UF for their very useful help, this FAQ wouldn't be the same without them (you know who you are ;)).

---

### Post by lnostdal on 2008-02-06
suggestion: people should use -Wall and -g when compiling

* -Wall makes the compiler talk more and gives hints about potential problems in your code
* -g makes the resulting binaries usable in a debugger

---

### Post by aks44 on 2008-02-06
lnostdal you're perfectly right. There are also other useful switches, like (from the top of my head, so it may not be accurate) --std=C99, --pedantic-warnings, --Wold-style-casts etc.

I'll research them & update my post tomorrow. For now it's almost time I go to sleep, so I'm done with technical stuff... ;)


Keep the suggestions coming!

---

### Post by LaRoza on 2008-02-06
[http://ubuntuprogramming.wikidot.com/cpp](http://ubuntuprogramming.wikidot.com/cpp)

Or is the wiki no longer of interest? I thought it would be better suited for things such as this.

---

### Post by Sockerdrickan on 2008-02-06
I find -Wextra useful when I am programming, it makes the code even more strict.

---

### Post by aks44 on 2008-02-06
> **LaRoza said:**
> is the wiki no longer of interest? I thought it would be better suited for things such as this.

IMO this post has its place on the forum. I guess you'll agree that the questions addressed are *very* common (if not overwhelming). I'm pretty sure I answer one of those questions almost every day.


My reasoning is, despite the proven fact that most people don't read the stickies or search the forum, having this information on the forum itself will hopefully help the few people who actually use the search function.


Besides that, I think the wiki deserves more in-depth articles. IMHO this post addresses very common issues in a very superficial way (quick and dirty Q/A). As I stated in another thread, writing a comprehensive C++ resource (and C to some extent) is on my agenda, and it will (amongst other things) quite probably cover those topics way more in-depth, including the whys that are behind the hows I just posted. Using the wiki will then make full sense to me. ;)

---

### Post by LaRoza on 2008-02-06
Ok.

May I recommend having a more uniform style? Blue is being used by others, and it is easier to read and stands out just as well.

---

### Post by pmasiar on 2008-02-06
We need FAQ about how to write FAQs :-)

---

### Post by aks44 on 2008-02-06
> **LaRoza said:**
> May I recommend having a more uniform style? Blue is being used by others, and it is easier to read and stands out just as well.
That I can do... **/"Red"/"Blue"/g** :D

(sorry, I tend to associate errors with the red colour ;))

---

### Post by ruy_lopez on 2008-02-06
```
sudo apt-get install manpages-dev
```

For further reading, and for when "-Wall" starts bleating.

---

### Post by LaRoza on 2008-02-06
> **aks44 said:**
> That I can do... **/"Red"/"Blue"/g** :D

(sorry, I tend to associate errors with the red colour ;))

Also, I used blue on mine for highlighting, but another consideration is that red #FF0000 has special significance for me, and we'd have rainbow threads.

---

### Post by aks44 on 2008-02-07
The warnings & tips sections have been added.
More input is warmly welcomed. :)

> **LaRoza said:**
> we'd have rainbow threads.
But I like rainbows... :(
:p

---

### Post by pmasiar on 2008-02-07
Trivial formatting suggestion to OP:

1) To emphasis, and bold is not good enough, IMHO try increase sice. Underlined text s/b a link, if not, is kinda confusing.

2) your headers are size="6". I prefer relative size, not forcing my font size to people, so I used size=+3. Not sure what we settle on. 

Some web designer wants to chime in? I might even be wrong and my vbCode will break later :-/

---

### Post by LaRoza on 2008-02-07
> **pmasiar said:**
> Trivial formatting suggestion to OP:

1) To emphasis, and bold is not good enough, IMHO try increase sice. Underlined text s/b a link, if not, is kinda confusing.

2) your headers are size="6". I prefer relative size, not forcing my font size to people, so I used size=+3. Not sure what we settle on. 

Some web designer wants to chime in? I might even be wrong and my vbCode will break later :-/

0. I think color stands out more than bold, but only if there isn't a lot.

1. I think the large size fonts make it difficult to read. With a table of contents, such headers seem to be wasting space

It I suggest trying to keep each post readable on one or two pages (scrolls).

---

### Post by aks44 on 2008-02-07
> **LaRoza said:**
> I suggest trying to keep each post readable on one or two pages (scrolls).

A "page scroll" is quite a vague measurement unit IMHO, but I get your point. ;)

Maybe I should be splitting it:
- Compiling your first C and C++ programs
- Troubleshooting the most common errors

The "build-essential" part has some overlap on both parts, but its Q/A part definitely belongs to the "troubleshooting". I guess I'll go with the apt-get command only for the "compiling" part.

What do you people think about that?


When it comes to presentation... it's a bit late right now but I promise I'll try and sort it out tomorrow or during the weekend.



EDIT:
> **pmasiar said:**
> your headers are size="6". I prefer relative size, not forcing my font size to people, so I used size=+3.
I may be wrong, but AFAIK the *only* browser that forces font size on people is IE, and we don't expect it too much around here. Any decent browser should be able to scale fonts, just like Firefox and Konqueror do...

---

### Post by pmasiar on 2008-02-07
Yup, splitting is good.

If in description you have "and", chances are, you need to split :-)

Splitting has 2 pluses:
1) newbie who needs just run first code, is not scared how FAQ page is too long
2) someone who managed to compile and has errors, does not have to skip over irrelevant (for the moment) description. Less chance to give up and ask in forum.

"How to Compile C or C++ Program"
"Common Errors in C or C++"

---

### Post by Vox754 on 2008-02-08
Some advice.

Q: What is *syntactically correct* code?
A: Essentially, code without spelling errors, missing parentheses or semicolons, etc. (Please explain.)

Why would you read the GCC manual (11 085 lines) from the terminal?
Also suggest
```

sudo aptitude install gcc-doc

```
to read it in HTML.

People who underline headings have obviously not used LaTeX. In general, this is considered an ugly practice.
Consider numbering the sections.

---

### Post by slavik on 2008-02-08
aks44, great faq :)

---

### Post by pmasiar on 2008-02-08
I was thinking about how to make that more readable. Suggestions:
> So you're willing to write your own C or C++ programs, or simply compile someone else's code.
But due to the nature of those languages, the compilation steps themselves can be quite tricky for newcomers.
> 
Learning C or C++, or compiling sources? It can be tricky, read on, we have the answers.

Have errors? Check "FAQ: C and C++ Compile Errors"  (link)

> Here's a little guide which hopefully will help you avoid / solve the most common compilation-related problems. It assumes you are trying to compile syntactically correct code.

(skip small talk: less is more!)

> 1) Check and fix syntax errors. To learn C, go to (link to Wyb's thread)

2) Make sure you installed **build-essential** package (essential tools needed to build C and C++ programs). If you don't know **why** you should not install them by yourself, you don't know how :-) so use apt or synaptic.

apt-get ...

3) Let's check if all is installed correctly by compiling simple valid code (a good habit):...

-------

Consider to NOT using underline for emphasis - only links s/b underlined.

Split errors even for build-essential, with explanation linking to first part of FAQ.

The smaller part of page reader need to skip to get to meat, the better chance we have people will read and understand. Short sentences with active verbs are more powerful and easier to read.

---

### Post by aks44 on 2008-02-08
> **Vox754 said:**
> Why would you read the GCC manual (11 085 lines) from the terminal?
Also suggest
```

sudo aptitude install gcc-doc

```
to read it in HTML.
Hmm I don't know about GNOME, but KDE has a GUI help application which handles plain man-pages in a readable format, so I *never* actually use the terminal (to me, *man* actually means *khelpcenter*). Bad habit I guess.
Thanks for your suggestions, I'll take them into account. :)


> **pmasiar said:**
> To learn C, go to (link to Wyb's thread)
Did I miss something? I didn't find any such thread that Wybiral made. :oops: Care to give me the link?

---

### Post by pmasiar on 2008-02-08
Wybiral's thread: more than a year old:
[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867) how to start, in many languages. Looking at it, it's idea was close to "clean" FAQ - so Wybiral started it, year ago! :-)

---

### Post by Snowball on 2008-03-24
This was all I needed!!!

---

### Post by gavinm on 2008-04-17
I've hit a problem with step 0.
When I sudo apt-get install build-essential
I get informed that 8 new packages will be installed, then:

Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main linux-libc-dev 2.6.22-14.52 [653kB]
Media Change: Please insert the disc labelled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Unfortunately I've mislaid my installation CD - and with just seven days until 8.04 comes out, I don't really want to burn a new 7.10 installation CD.

Can anyone explain:
(a) Why I'm being asked to insert my installation CD
(b) How I can get round the fact I've mislaid the CD

Thanks in advance,
Gavin

---

### Post by LaRoza on 2008-04-17
Go to System->Administration->Software Sources and uncheck the CD.

---

### Post by JupiterV2 on 2008-04-17
Would it be a worthy idea to cover optimization flags here too or is that beyond the scope of this post? Ie. that -O0 is default for compiling code with g++ and using a higher optimization level or setting other optimization flags can make debugging more difficult?

---

### Post by needsleep on 2008-05-29
Thanks, this was exactly what I was looking for.

---

### Post by sarthorks on 2008-07-12
well thanks a lot! this FAQ was a great help!

---

### Post by tom1234 on 2008-07-25
Bump - useful post.  Thanks.

---

### Post by dribeas on 2008-07-25
Is there a way to upgrade this post to sticky? or reference it from the sticky post already existing?

---

### Post by LaRoza on 2008-07-25
> **dribeas said:**
> Is there a way to upgrade this post to sticky? or reference it from the sticky post already existing?

It is referenced in the sticky (see third link in sticky)

---

### Post by Anbin89 on 2008-11-30
sudo apt-get install build-essential

I tried this but it says but it shows some errors. These are the errors

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

Any idea how to solve this? Thanks

---

### Post by Anbin89 on 2008-11-30
Sorry guys. Found the solution. I was running the synaptic updater when i entered this code. Now it is installing fine.

---

### Post by stmartin on 2008-12-02
Why I must write **./** I still can't understand:
> (the current directory . is not in the PATH by default).

---

### Post by jagannatham on 2008-12-18
When i try to install build essential package using the following command

sudo apt-get install build-essential

jagan@jagan-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
jagan@jagan-desktop:~$ 


this error is coming. How to sort this problem

Jagan

---

### Post by Kamron on 2010-01-09
I have a similar problem when I try to install codeblocks on 
8.04, this is the error I get:

kamron@alciann:~$ sudo apt-get install codeblocks
[sudo] password for kamron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  codeblocks: Depends: libcodeblocks0 (= 8.02svn6023-0ubuntu1~hardy) but it is not going to be installed
              Depends: libwxbase2.8-0 (>= 2.8.10.1) but 2.8.7.1-0ubuntu3 is to be installed
              Depends: libwxgtk2.8-0 (>= 2.8.10.1) but 2.8.7.1-0ubuntu3 is to be installed
E: Broken packages

Anyone knows what the solution for this is?

---

### Post by Zugzwang on 2010-01-10
> **Kamron said:**
> Anyone knows what the solution for this is?

Maybe your package source list is messed up. Apart from that, what is the result of trying to install "libcodeblocks0" manually? (Command: "sudo apt-get install libcodeblocks0")

---

### Post by nvteighen on 2010-01-10
Try 'sudo apt-get update' before anything... Then try what Zugzwang has told you

---

### Post by kneedragon on 2010-07-23
Hi all, complete n00b here.
Thank you for this thread - it's been very useful to me. You'd think help on installing and configuring gcc would be pretty common, but ...
I got Netbeans - for the java, and found it could front multiple other languages, so I decided on a whim to get it working with c and c++ as well.

Suggestion - after 'Hello world", how about a simple demo that does something? One file, 50 ~ 100 lines, demonstrates correct use of pointers, char, int, float, string ... could perhaps do a version2 which accepts params, like the user's name and says 'Hello [name]' when it starts? I could write one, but I'm VERY sure you guys could do it better.

---

### Post by simpleblue on 2011-09-08
For C++0x:

To compile C++0x simply add **'-std=c++0x'** to your compile paramaters.

So, if you are compiling a file named **'main.cpp'** (or **main.cxx**), and you want the executable file to be named '**run**' then you'd type:

```
g++ main.cpp -o run -std=c++0x
```A very popular library is called ncurses. You add the paramater '**-lncurses**'. You'll bump into it sooner or later so might as well know how to add the command that will allow you to properly compile it (I added c++0x support to the paramaters as well, but you don't need it to run ncurses):

```
g++ main.cpp -o run -std=c++0x -lncurses
```The great thing about this is that you don't need to be using c++0x commands or ncurses library to using these compile paramaters.

---

### Post by dwhitney67 on 2011-09-09
simpleblue - You just posted to a thread that is more than 2 1/2 years old!  (excuse me... first post was in 2008.)

---

### Post by simpleblue on 2011-09-11
> **dwhitney67 said:**
> simpleblue - You just posted to a thread that is more than 2 1/2 years old!  (excuse me... first post was in 2008.)
It's a great thread and worth keeping around. Just needed some new info to include the new C++0x, otherwise it seems perfectly relevant.

---

### Post by bedroomCod3r on 2011-09-27
Are there any way of running the executable without  the ./ ?

---

### Post by karlson on 2011-09-27
> **bedroomCod3r said:**
> Are there any way of running the executable without  the ./ ?

Yes but it's considered a security hole for one.
Secondly if you don't specify this and run a.out (for example) you may actually be running a.out that is different from the one you wanted.

---

