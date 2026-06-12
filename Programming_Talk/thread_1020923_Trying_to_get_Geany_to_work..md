---
title: "Trying to get Geany to work."
date: 2008-12-24
forum: Programming Talk
---

### Post by Arukas on 2008-12-24
My C++ program is 



[PHP]#include <iostream>

int main(int argc, char** argv)
{
	cout << "Vista is bloated!!";
	return 0;
}
[/PHP]

and when I compile I get this

[PHP]
g++ -Wall -c "untitled.cpp" (in directory: /home/revenant)
untitled.cpp: In function ‘int main(int, char**)’:
Compilation failed.
untitled.cpp:27: error: ‘cout’ was not declared in this scope
[/PHP]


Anyone know how to get this program to work?

---

### Post by hanniph on 2008-12-24
cout is declared in std namespace so you need to use std::cout or include this sentence: ```
using namespace std;
``` before your main function

---

### Post by Arukas on 2008-12-24
I did that, and it worked.  Do I need to use the namespace std because I didn't include the ".h" on the iostream or is another reason?


However, the program did compile correctly.  But it says at the bottom of the screen when I try and run it, failed to execute terminal program, how do i fix that?

---

### Post by hanniph on 2008-12-24
Namespace std contains all object, classes, functions of standard C++ library. Whenever you need to use a function from that class - you need to show compiler from where to get it.
see [this]("http://forums.devshed.com/c-programming-42/using-std-namespace-what-does-it-mean-45679.html") link for a better explanation.

Try to compile and run your command from a terminal: 
```
g++ yourprogram.cpp -o yourprogram
```
and
```
./yourprogram
```

---

### Post by Arukas on 2008-12-24
Well, doing it that way defeats the purpose of me using an idea.  I know how to write c/c++ programs with gedit and gcc/g++

But I would like the IDE to work.  I'm been rather upset I can't find a working/useable IDE for C/C++ in linux

---

### Post by hanniph on 2008-12-24
Have you tried Anjuta then? Really cool IDE for C++ development. I was using it before switching to Vim :-)

---

### Post by Arukas on 2008-12-24
Well, I've been trying to use Anjuta, it seems really nice, but I can't seem to get it to work right.  I can't find a current tutorial on Anjuta so I can figure out how to use.  So Geany was next on the list.  

Unless you know where I can find current tutorial or information on how to make Anjuta work, I'd use that.

---

### Post by Arukas on 2008-12-25
So does no one use Geany at all?  The reason I tried it out is it seemed several people actually used it.

---

### Post by pokerbirch on 2008-12-25
I love Code::Blocks for C and C++. It is in the Ubuntu repositories.

For KDE versions, i've read that KDevelop is also good.

---

### Post by Arukas on 2008-12-25
Still want to know how to get Geany to work.  Last person who suggest another IDE wasn't very familiar with it apparently and couldn't answer my questions.  


I'm also posted a seperate post with KDE on a simple compile, and apparently no one knows anything about KDE either, and I'm just following tutorials.

---

### Post by jespdj on 2008-12-27
Your original question wasn't about Geany at all, you just had an error in your C++ program.

Now you're complaining that Geany doesn't work. In what way does it not work? Explain what you're trying to do and what error messages you get, if any. Or is it just that you don't know how to use Geany? What are you trying to accomplish with Geany?

---

### Post by .Maleficus. on 2008-12-27
What exactly is the error you're getting?  I've been doing C, C++ and Python on Geany for a while and its always worked, no config required.  I just did:
[php]#include <iostream>

using namespace std;

int main(int argv, char** argc) {
	cout << "Geany works fine.";
	return 0;
}[/php]
and got:
```
Geany works fine.

_______________________
(program exited with code: 0)
Press return to continue
```
in a new terminal window.  Before you did Execute, did you make sure to Build the file?  If you just run the compiler and then hit the Execute button, you haven't actually made an executable object yet, just bytecode (from what I gather anyways).

---

### Post by Arukas on 2008-12-27
> However, the program did compile correctly. But it says at the bottom of the screen when I try and run it, failed to execute terminal program, how do i fix that?

I got the program to compile just fine after, I put that namespace nonsense in there.  But geany still isn't working like an IDE should.

---

### Post by The Cog on 2008-12-27
I just tried it. I clicked Compile and it compiled OK. Then I clicked Execute and got "Failed to execute". I took a wild guess and clicked the menu Build->Build. After that, the execute button ran the program properly. It seems that Compile creates a .o object file, and Build->Build creates an executable. Execute runs the executable.

---

### Post by Arukas on 2008-12-27
I appreicate it. I guess 14 is a lucky number.  

I've done the majority of my programming in windows.  My linux programming is limited to gcc and gedit, at the moment.  Geany will be my first IDE to work, still can't get KDevelop or Anjuta to work.  

So can you explain something?  What would I be doing with a .o object?  What is that even for?  I having the worst time trying to get started, with programing in linux.

---

### Post by Arukas on 2008-12-27
I've done some more reading.  Apparently a '.o' is an object, and its used for when you have multiple sources files.  It helps save on compile time. 

So why does geany make a '.o' with one source file?

---

### Post by maddog39 on 2008-12-27
> **hanniph said:**
> Have you tried Anjuta then? Really cool IDE for C++ development. I was using it before switching to Vim :-)
Of course we dont want to start a debate about this. But there is a very specific reason many people like to use Geany (such as myself). In my opinion, Ajunta would be considered bloatware. Like most IDE's, they are simply far too heavy and want to try and do everything for you, even when you dont want them to. Which is why many people prefer a lightweight IDE that only does what you want it to and has all the most useful tools and leave the extra junk out.

---

### Post by The Cog on 2008-12-28
> **Arukas said:**
> I've done some more reading.  Apparently a '.o' is an object, and its used for when you have multiple sources files.  It helps save on compile time. 

So why does geany make a '.o' with one source file?

I think it's a general principle with C/C++ files. Your individual source files make individual object files. A large project will have lots of both, perhaps with different programmers working on different parts. They get linked to make a single executable. A single-source program is just the minimal case of this.

An object file can probably be converted into a .so or .DLL library file instead, but I'm hazy (meaning no idea) how to do that.

---

### Post by pokerbirch on 2008-12-28
Haven't read the whole thread word for word, so apologies if i repeat anything. I've recently used Geany for some C code and had same problems with compile and execute. Just clicking 'compile' did not build the project. It was to do with a gcc parameter which i can't remember. Anyway, i modified the 'compile' options button to mirror the build options:
click Build > 'Set includes and Arguments', and set the 'compile:' options to the same as the 'build:' options. In my case it became:
> 
Compile: gcc -Wall -o "%e" "%f"
Build: gcc -Wall -o "%e" "%f"

Not sure if this is even correct as i'm not familiar with compiler options, but it works ok.

I can also give a thumbs up for Code::Blocks. Geany is more lightweight and Code::Blocks is more like Visual Studio.


EDIT:
Should point out that for C++, the compiler will be g++ and not gcc...

---

### Post by Arukas on 2008-12-28
Well, good news is, I figured out how to compile a program in Geany and on top of that, I figure out how to use the Allegro library with it, which is a good start.

---

### Post by shankhs on 2008-12-28
> **Arukas said:**
> Well, good news is, I figured out how to compile a program in Geany and on top of that, I figure out how to use the Allegro library with it, which is a good start.
Can you please tell me how to add third party library to geany???
I want to use OpenCV.

---

### Post by Arukas on 2008-12-28
I didn't do anything fancy.  I just changed some arugments.  This is what I did to get Allegro to work.  Hope that helps you in some way.  

[http://wiki.allegro.cc/index.php?title=Geany]("http://wiki.allegro.cc/index.php?title=Geany")

---

