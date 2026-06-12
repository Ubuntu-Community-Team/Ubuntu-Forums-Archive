---
title: "Programming Newbie"
date: 2008-04-13
forum: Programming Talk
---

### Post by Toasted Donut on 2008-04-13
Hi, I am a big newbie when it comes to Linux and open source. I switched from Windows because I wanted more freedom and challenges. I soon realized that to do a lot of things I want to do I will need to learn to program. So my question is, can anyone recommend what programming languages I should learn and where I can learn (books, websites, etc.)

I just want to have a general knowledge of programming, and I am willing to take several years to learn.

---

### Post by CptPicard on 2008-04-13
Python... Google Is Your Friend.

---

### Post by LaRoza on 2008-04-13
> **Toasted Donut said:**
> Hi, I am a big newbie when it comes to Linux and open source. I switched from Windows because I wanted more freedom and challenges. I soon realized that to do a lot of things I want to do I will need to learn to program. So my question is, can anyone recommend what programming languages I should learn and where I can learn (books, websites, etc.)

I just want to have a general knowledge of programming, and I am willing to take several years to learn.

See the sticky.

---

### Post by Can+~ on 2008-04-13
1. Download geany, easiest pseudo IDE (IMO).

2. Copy paste:
[PHP]#!/usr/bin/env python

print "Hello world"[/PHP]

3. Click on "Execute" (F9 I think).

---

### Post by LaRoza on 2008-04-13
> **Can+~ said:**
> 1. Download geany, easiest pseudo IDE (IMO).

2. Copy paste:
[PHP]#!/usr/bin/env python

print "Hello world"[/PHP]

3. Click on "Execute" (F9 I think).

You never know what you are going to get...

To learn Python, see my wiki (or the sticky) for the Python tutorial, and open a command prompt and type "python". You shouldn't use IDE's from the beginning, and certainly not for Python!

---

### Post by untermensch on 2008-04-13
i would recommend python. and i'd try [www.sthurlow.com](www.sthurlow.com). it has some pretty good python tutorials for beginners.

---

### Post by LaRoza on 2008-04-13
> **untermensch said:**
> i would recommend python. and i'd try [www.sthurlow.com](www.sthurlow.com). it has some pretty good python tutorials for beginners.

The tutorial on that site isn't that good.

---

### Post by Can+~ on 2008-04-13
I learnt with the Alan Gauld guide, but the only reason I didn't post it before, it that the page was down for months.

Now is back, and please, try to download the backup from there:
[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)

---

### Post by coolkid5 on 2008-04-13
"How to Think Like a (Python) Programmer" is good:
[http://www.greenteapress.com/thinkpython/](http://www.greenteapress.com/thinkpython/)

---

### Post by pmasiar on 2008-04-14
You are newbie without any programming expereince? Or programmer who is newbie in Linux?

See wiki in my sig for selected best links for Python beginners, and also training tasks to solve.

---

### Post by nanotube on 2008-04-14
> **Can+~ said:**
> ...

3. Click on "Execute" (F9 I think).

F5 :)

---

### Post by atsukoarai86 on 2008-04-14
I recommend learning C++! C++ is a massive comprehensive language, and is, I believe, embedded in Unix platforms. Just another opinon! I believe taking some college courses in various programming languages would be a great idea.

---

### Post by LaRoza on 2008-04-14
> **atsukoarai86 said:**
> I recommend learning C++! C++ is a massive comprehensive language, and is, I believe, embedded in Unix platforms. Just another opinon! I believe taking some college courses in various programming languages would be a great idea.

What is your programming experience?

No offense, but it seems likely that you know Blub (based on your other post and this one)

C is most used for *nix systems.

---

### Post by Toasted Donut on 2008-04-14
Both a Linux Newbie and and a programming newbie. Thank you all very much for your answers. I guess I will be learning python first.
And I will check out those links too, i've clicked ona  couple and they are very useful.

---

### Post by Wybiral on 2008-04-14
> **atsukoarai86 said:**
> I recommend learning C++! C++ is a massive comprehensive language, and is, I believe, embedded in Unix platforms. Just another opinon! I believe taking some college courses in various programming languages would be a great idea.

What does C++ offer over other languages?
What does "massive comprehensive language" mean?
Can you explain how C++ is embedded in Unix platforms?

---

### Post by P_Hansson on 2008-04-14
Java or Python, doesn't really matter.

C++ isn't the best beginner language IMO, it tends to make things seem more complex than they are.

---

### Post by LinuxGuy1234 on 2008-04-14
To begin programming and test it follow these steps (use the terminal, go to Applications-Accessories-Terminal).
1. sudo apt-get install build-essential
2. echo "#include <stdio.h>" > test.c
3. echo "int main() { printf('Hello world!'); }" >> test.c
4. gcc -o test test.c
5. ./test
It should print "Hello world!".

---

### Post by P_Hansson on 2008-04-14
C is a reasonable language, still I believe Java is better for learning actual programming rather than focusing on technical details. It also depends on what you intend to do. If working close to hardware Java isn't really an option.

---

### Post by nanotube on 2008-04-14
> **LinuxGuy1234 said:**
> To begin programming and test it follow these steps (use the terminal, go to Applications-Accessories-Terminal).
1. sudo apt-get install build-essential
2. echo "#include <stdio.h>" > test.c
3. echo "int main() { printf('Hello world!'); }" >> test.c
4. gcc -o test test.c
5. ./test
It should print "Hello world!".

hehe, save some steps: open a terminal, and type:
```
echo "Hello world!"
```
It should print "Hello world!".
:lolflag:

edit: sorry, just couldn't resist... ;)

---

### Post by Toasted Donut on 2008-04-14
Wow, thanks a lot, you guys are a big help. I think I will learn Python First though, maybe C later. What languages should I learn after?

---

### Post by LaRoza on 2008-04-14
> **Toasted Donut said:**
> Wow, thanks a lot, you guys are a big help. I think I will learn Python First though, maybe C later. What languages should I learn after?

See my wiki and page.

---

### Post by ghostdog74 on 2008-04-14
> **Toasted Donut said:**
> What languages should I learn after?

take it one step at a time. what's the rush

---

### Post by pmasiar on 2008-04-14
> **Toasted Donut said:**
> Wow, thanks a lot, you guys are a big help. I think I will learn Python First though, maybe C later. What languages should I learn after?

Depends where you want to go.

SQL (for databases) is useful, HTML+CSS for web applications, Javascript for AJAX - more dynamic web applications. After couple languages, syntax of any language from Algol family(C, Pascal, Java etc) is easy: what is hard is libraries, and idiomatic use (patterns).

---

### Post by SteveNorman on 2008-04-15
I think my question is relavent here,, but if not sorry to highjack...

I have a book called "Begining Programming" by Wrox, everything was good until I reached the chapter on c++

It recommends the Borland compiler,,which of course as a beginner I cannot get to work. So I thought I could just go to linux and use g++. 

I did this

sudo aptitude install build-essential

and tried typing this from the text:
// C++ code template
#include <isostream.h>
void main()
       {
            cout << "Hello World!"  << endl;
       }

tried compiling and got a list of errors


it didnt work in windows and it doesnt work here. Is this book obsolete? If so can I download an older compiler so this book will work? I dont understand why something would be in pint that no longer works

I see in LaRoza's wiki the same program but there are some big differences in the way the code is written.  Very confusing and any help would be great.

---

### Post by nvteighen on 2008-04-15
> **SteveNorman said:**
> 
// C++ code template
#include <isostream.h>
void main()
       {
            cout << "Hello World!"  << endl;
       }


The error is in the #include line. It should be:
```

#include <iostream> //Not <isostream.h>!

```

That's all my C++ knowledge, by the way :p.

---

### Post by LaRoza on 2008-04-15
> **SteveNorman said:**
> 
and tried typing this from the text:
// C++ code template
#include <isostream.h>
void main()
       {
            cout << "Hello World!"  << endl;
       }

it didnt work in windows and it doesnt work here. Is this book obsolete? If so can I download an older compiler so this book will work? I dont understand why something would be in pint that no longer works

I see in LaRoza's wiki the same program but there are some big differences in the way the code is written.  Very confusing and any help would be great.

Take software recommendations with a grain of salt. Try to use free software. This isn't a philosophical issue, it is practicle. 

The book is out of date, and that code is bad.

Here it is:
[php]
#include <iostream>

int main(int argc, char ** argv)
{
    std::cout << "Hello world" << std::endl;
    return 0;
}
[/php]

Some issues:

[list]
[*] iostream.h is old, use iostream
[*] main should return an int. Those arguments are optional. They are for command line arguments. argc is the number, and argv is the "array".
[*] std:: is a namespace.
[*] return 0 is the value returned by main (the program)
[/list]

---

### Post by pmasiar on 2008-04-15
> **SteveNorman said:**
> I have a book called "Begining Programming" by Wrox, everything was good until I reached the chapter on c++

Skip it. Start with Python instead :-)

---

### Post by SteveNorman on 2008-04-15
That sux,,I just blew 40 bucks. 

thanks wrox

---

### Post by LaRoza on 2008-04-15
> **SteveNorman said:**
> That sux,,I just blew 40 bucks. 

thanks wrox

Most of it is probably valid. Programming isn't tied to a language or syntax. The book may be behind on C++, but I am sure the rest of it is fine.

You'll just have to modernize your code.

This is what main() should look like:
```

int main(int argc,char ** argv)
{
 
    return 0;
}

```

Use:

```

<iostream>

```

(if there are other headers used, drop the .h from them unless you wrote the header yourself.)

For the lack of namespaces, use:

```

using namespace std;

```

After the headers are #included.

For compiling, use gcc (g++). For Windows: [http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html) (it uses g++ for compiling, but it is a modern Windows IDE)

---

### Post by CaptainLinux94 on 2008-04-15
> **LaRoza said:**
>  You shouldn't use IDE's from the beginning, and certainly not for Python!

Hey LaRoza,

I'm not criticizing you at all...  I've heard the statement "Don't start with IDE's," reiterated many times.  I would really like to know why, because every time someone responds it's the usual "Well, I'm not sure why, someone on another forum told me why."

I'm really indecisive whether or not to use IDLE on my computer (7.10 Gutsy Ubuntu), or simply use GEdit and a terminal window.

I've already got some minimal experience in C++ (by minimal, little to none, enough to run basic input/output programs) but I've found Python to be much easier on the eyes and the brain since I'm just starting into programming.

Thanks in advance,
CL94

---

### Post by LaRoza on 2008-04-15
> **CaptainLinux94 said:**
> Hey LaRoza,

I'm not criticizing you at all...  I've heard the statement "Don't start with IDE's," reiterated many times.  I would really like to know why, because every time someone responds it's the usual "Well, I'm not sure why, someone on another forum told me why."

I'm really indecisive whether or not to use IDLE on my computer (7.10 Gutsy Ubuntu), or simply use GEdit and a terminal window.


IDE's are intergrated development environments. lnostdal made a great statement about them, I will try to find it later.

For seeing why not to use IDE's, find all the threads on those that only knew how to use Visual Studio ;)

An IDE usually has the editing, debugging, compiling, linking and making all in one program. It hides what is really happening. It may be good for those who know what is going on, but pressing F9 or whatever, isn't really that informative.

Using gcc, gdb is important. If you use an IDE, you learn the IDE, not the real tools.

Geany, IDLE, and probably others are rather light though. 

IDLE is an editor and interactive terminal, so it isn't an "IDE" like MonoDevelop or something.

See my blog for my wmii screenshot (it is the latest image). That is my "IDE". I have one terminal for editing (with Vim, with multiple tabs), one for file management, and one for building and running. 

When I used gedit primarily, I had two plugins I used a lot. A directory panel, and the terminal plugin. 

For Python, all you need is a good editor (gedit, scite, geany, vim, kwrite, kate, etc) and someway to run (a terminal). So it doesn't matter for Python as much.

---

### Post by danbuter on 2008-04-15
I personally think it is much easier to learn how to program using an ide. For one thing, it will point out where the errrors in your code are.

---

### Post by Can+~ on 2008-04-15
> **CaptainLinux94 said:**
> Hey LaRoza,

I'm not criticizing you at all...  I've heard the statement "Don't start with IDE's," reiterated many times.  I would really like to know why, because every time someone responds it's the usual "Well, I'm not sure why, someone on another forum told me why."

Maybe to learn how to compile your own files?

For instance, on the introductory C course on my University, they just told everyone to install DevCpp on windows and use it. A semester later, on data structure, we're asked to compile files on linux, NO ONE knew how to do it (lucky for me, I moved to linux months before), also, everyone who did the task on devcpp started with a default .cpp file, and devcpp automatically compiled it with g++ rather than gcc, and did all the library linkage for them.

The problem was, that the IDE was too friendly, so, people who learns with an IDE, associate the language they work with the IDE they use. When the IDE is removed they think they're screwed. Also, I suggested using an IDE on the start of the thread, since geany just does "python pythonfile.py" with the run button, so it won't be a big issue after all... Now C, C++ is a different story.

---

### Post by LaRoza on 2008-04-15
> **danbuter said:**
> I personally think it is much easier to learn how to program using an ide. For one thing, it will point out where the errrors in your code are.

Compilers do that anyway. IDE's just capture the output.

> **Can+~ said:**
> Maybe to learn how to compile your own files?

For instance, on the introductory C course on my University, they just told everyone to install DevCpp on windows and use it. A semester later, on data structure, we're asked to compile files on linux, NO ONE knew how to do it (lucky for me, I moved to linux months before), also, everyone who did the task on devcpp started with a default .cpp file, and devcpp automatically compiled it with g++ rather than gcc, and did all the library linkage for them.


DevCpp uses gcc. When I used Windows, I added the gcc path to my $PATH (whatever it was called in Windows) and used gcc from the command line, and used Crimson Editor as my editor.

---

### Post by CaptainLinux94 on 2008-04-15
> **LaRoza said:**
> 
See my blog for my wmii screenshot (it is the latest image). That is my "IDE". I have one terminal for editing (with Vim, with multiple tabs), one for file management, and one for building and running. 


Freaky...  Before I moved to Python from my small amount of C++ experience and I was programming C++ on Ubuntu, that was *exactly* what I did.

I mean.... down to the last detail.(rather than specific programs)

GEdit on the left. Terminal/nautilus browser on right.

Thanks LaRoza,
CL94

---

### Post by LaRoza on 2008-04-15
> **CaptainLinux94 said:**
> Freaky...  Before I moved to Python from my small amount of C++ experience and I was programming C++ on Ubuntu, that was *exactly* what I did.

I mean.... down to the last detail.(rather than specific programs)

GEdit on the left. Terminal/nautilus browser on right.

Thanks LaRoza,
CL94

If you get Gedit's plugins, you will be able to have a terminal and directory panel part of gedit.

wmii is a tiling manager, so those windows aren't being shuffled around.

[[IMG]http://img171.imageshack.us/img171/4083/screenshoteu9.th.png[/IMG]](http://img171.imageshack.us/my.php?image=screenshoteu9.png)

---

### Post by CaptainLinux94 on 2008-04-15
Well, I'm not very familiar with Linux.

How do I go about installing/using those plug-ins?

---

### Post by CaptainLinux94 on 2008-04-15
Oh, forget what I last said.

Just browsed through the preferences window and i found a python console window and a file browser window to plug-in to it.... how do i apply the settings?

Even after checking the box and closing preferences no changes occur.

Thanks,
CL94

---

### Post by LaRoza on 2008-04-15
> **CaptainLinux94 said:**
> Oh, forget what I last said.

Just browsed through the preferences window and i found a python console window and a file browser window to plug-in to it.... how do i apply the settings?

Even after checking the box and closing preferences no changes occur.

Thanks,
CL94

Go to "View" and chose to see the bottom pane or something.

My system is in Spanish, don't know what it says in English exactly.

---

### Post by CaptainLinux94 on 2008-04-15
That did the trick, thank you.

No habla espanol(if only I knew how to make the squiggly thing...).

I thought there was something Hispanic about your name :)


Ubuntu has quite the diverse community.

---

### Post by LaRoza on 2008-04-15
> **CaptainLinux94 said:**
> That did the trick, thank you.

No habla espanol(if only I knew how to make the squiggly thing...).

I thought there was something Hispanic about your name :)

Ubuntu has quite the diverse community.

"No habl**o** español"

(It is called a tilde)

My name is euskara, not Spanish. It is entirely different from Spanish (the meaning isn't what it sounds like). The Spanish surname "LaRosa" is popular, but "LaRoza" is distinct.

(In case you are interested, I live in the USA, and not the least bit Hispanic or Latino. I am learning spanish, and have gotten used to my system being in Spanish)

---

### Post by Can+~ on 2008-04-15
Es cierto, cambiando el lenguaje al sistema operativo se aprende mas rápido el idioma, así yo aprendí Inglés :).

(It's true, changing the OS language is a quick way to learn a new language, that's how I learnt English.)

Oh, and I just checked my Virtual box:

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1.png[/IMG]

---

### Post by SteveNorman on 2008-04-16
Thank you LaRoza, the code in the book is in fact working with the mods you listed. I cant get devc++ to do what I want, but in Linux its woking well!
Thanks

---

### Post by tseliot on 2008-04-17
> **LaRoza said:**
> "No habl**o** español"

(It is called a tilde)

My name is euskara, not Spanish.
I think you mean "euskera", es decir la lengua que se habla en el País Vasco.

---

### Post by days_of_ruin on 2008-04-17
> **coolkid5 said:**
> "How to Think Like a (Python) Programmer" is good:
[http://www.greenteapress.com/thinkpython/](http://www.greenteapress.com/thinkpython/)

+1
also "a byte of python"[http://www.swaroopch.com/byteofpython/]("http://www.swaroopch.com/byteofpython/")

---

### Post by nvteighen on 2008-04-17
> **tseliot said:**
> I think you mean "euskera", es decir la lengua que se habla en el País Vasco.
Properly it's name is "euskara"; "euskera" is in Spanish...

---

### Post by phidia on 2008-04-17
LaRoza, Thank you muy mucho for the "Learn to Program" link I've found it very helpful and I'm actually enjoying Swaroop's ["A Byte of Python"]("http://www.swaroopch.com/byteofpython/")

---

