---
title: "C++ problem"
date: 2011-05-23
forum: Programming Talk
---

### Post by rpmp on 2011-05-23
Hello first of all im new here.

i been tryng to learn C++ and im practicing making program like Hello world but when i write what says my tutorial and hit save all it does is the letters change colors am i doing something cause im new to C++ so im not so sure if im doin it right?

---

### Post by jamesjenner on 2011-05-23
> **rpmp said:**
> Hello first of all im new here.

i been tryng to learn C++ and im practicing making program like Hello world but when i write what says my tutorial and hit save all it does is the letters change colors am i doing something cause im new to C++ so im not so sure if im doin it right?

G'day mate, 

First we need to know a couple of things. Could you please tell us the following:


[LIST]
[*]What's the url for your tutorial?
[*]Are you doing this under Windows or Linux?
[*]If under Linux, what are you using to edit the program, is it at the command line via vi or via a graphical text editor or maybe via an IDE (Integrated Development Environment, eg Eclipse)?
[/LIST]
I suspect your problem is that all your doing is saving the program but your not compiling it and running it. Even if you are running it, most hello world programs just output to the standard text device which means under Linux you wouldn't see anything, under windows you'd see the command window flick up and disappear very fast.

Cheers,

James

---

### Post by rpmp on 2011-05-23
i dont know what you mean by url but im using ubuntu 11.04 (Natty Narwal)  and im using text editor and im not sure how to compile it and run it.

---

### Post by cgroza on 2011-05-23
Install Code Blocks from the software center.
Open a terminal and do:
```

sudo apt-get install build-essential

```
This will install the C++ compiler.
Open your file with Code Blocks and there is a button in the toolbar which says Build and Run.
Press it, and you should have your program running.

Now,
Every C++ program needs to go through a process called compilation. Under Linux, the program that does that, the compiler, is called g++.
To run it you do this at terminal:
```

g++ [your file here] -o myprogram

```And then you run it by:

```

./myprogram

```
Hope this helped.

---

### Post by jamesjenner on 2011-05-23
> **rpmp said:**
> i dont know what you mean by url but im using ubuntu 11.04 (Natty Narwal)  and im using text editor and im not sure how to compile it and run it.


Ahh ok. When I said URL, I meant the web link (URL stands for the link to a web site) for your tutorial.

As your using the text editor all pressing save will do is save the file to the filesystem. Most prob your desktop or maybe your documents folder. 

What you have typed is the c program, for it to run it has to be compiled into machine code so that Ubuntu can run it. Once it has been compiled then you can execute it.

The easiest way to do all this is via the command line, so you want to open a terminal window. Since your on 11.04 you should have a pic on the side that is a terminal. When you open it up you will have a prompt with a cursor (the prompt will be $). 

Change directory to where your program is (you will start in */home/<username>* where *<username>* is the name that you log in with). If you saved it under your desktop (ie you can see it on the desktop) then type in:
```
cd Desktop
```

The prompt will redisplay. To confirm that your in the correct directory you can type in:
```
pwd
```
This should respond with */home/<username>/Desktop*. 

Now the command to list files in a directory within Ubuntu is *ls*, type this in and you should see your file with any other files you have there. You can also type in *ls -l* which will show you details about every single file, including it's permissions.

Now that you see your c program (it should be something like *helloworld.c*) let's try and compile it. To compile it you use the c compiler which you can use as follows:
> cc helloworld.c
Just replace *helloworld.c* with the name of yours if it's different. Now if you do the ls command again you should have a few more files, one will be a *a.out*. You should now be able to type in:
> ./a.out
and it should show you the output.

If you have any problems then just post your code or any errors in here using the code tags (the # symbol on the toolbar).

oh, btw *a.out* is just the default output for the compiler. You can change this by using the -o option, so you could do:
> cc -o helloworld helloworld.c 

You may have to replace cc with g++, been a while since I played in ubuntu with c and I don't have a ubuntu box handy to check what's installed by default.  You can follow the following guide which is for ubuntu and shows how to install g++ so there is no problems:

[http://talkbinary.com/programming/c/how-to-write-and-compile-c-program-in-linux/](http://talkbinary.com/programming/c/how-to-write-and-compile-c-program-in-linux/)

Good luck.

---

### Post by cgroza on 2011-05-23
Also, I do recommend geany as a beginner's text editor. It has the compile - build - run buttons so you don't have to use the terminal.

---

### Post by jamesjenner on 2011-05-23
> **cgroza said:**
> Also, I do recommend geany as a beginner's text editor. It has the compile - build - run buttons so you don't have to use the terminal.

Well it makes it easier to support but personally I'm old school and would recommend not using any type of integrated development environment so you can understand what is going on, ie, compiling the code to make object code, linking object code to make executable, etc. But it sure does make support easier :)

---

### Post by rpmp on 2011-05-23
what does your file here mean? and thanks for the advice on geany but i rather learn first with text editor even thought im a newbie in C++.

---

### Post by rpmp on 2011-05-23
it says file has not been built.when i hit run

---

### Post by Mr. Shannon on 2011-05-23
[[COLOR="Blue"]Here[/COLOR]]("http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html") is a tutorial on how to compile C++ code.  This tutorial uses a (.C) file extension for C++ files.  There is nothing wrong with this it is just not standard.  It is better to end the source files (the files with text) with (.cpp) without the parenthesis.

You replace
```
[your file here]
```
with the filename of your source code.  Since you are writing a hello world program you probably saved your code as hello.cpp.  In that case you would replace the brackets and the stuff in the brackets with hello.cpp

---

### Post by Mr. Shannon on 2011-05-23
What are you hitting run on?

---

### Post by jamesjenner on 2011-05-24
> **rpmp said:**
> it says file has not been built.when i hit run

You should be doing all this in a command window/shell. Could you cut and paste all the text from when you tried to compile it to when you tried to run it please.

---

### Post by Blackbug on 2011-05-24
I would suggest if using linux use emacs/vi editor to type your code.
and compile and run it manually with g++.
This way you will learn basic things related to compilation and g++ optimization levels also.
 
IDE are good when you are familiar with the language and process of compilation. Because it abstracts all the basic things and provides you an easy interface.
May be others might disagree, but I feel this is best way to start learning not only c++ but any other lanugage even java for which a beautiful IDE eclipse is available. But I always preferred manual compilation and settings.

---

### Post by jamesjenner on 2011-05-24
> **Blackbug said:**
> I would suggest if using linux use emacs/vi editor to type your code.
and compile and run it manually with g++.
This way you will learn basic things related to compilation and g++ optimization levels also.
 
IDE are good when you are familiar with the language and process of compilation. Because it abstracts all the basic things and provides you an easy interface.
May be others might disagree, but I feel this is best way to start learning not only c++ but any other lanugage even java for which a beautiful IDE eclipse is available. But I always preferred manual compilation and settings.

agree with you totally mate except about emacs and vi. Two very complicated editing programs that will make the effort harder for someone who is new to all this (which I suspect the op is). I mean don't get me wrong, I love vi and even now still use it a lot, but at the end of the day, it's a large learning curve to learn such an editor and takes a long time to become proficient at it. Using gedit is more than okay for the OP. Otherwise, agree totally with everything else. avoiding IDE's makes it easier to understand what is going on behind the scenes.

---

### Post by Blackbug on 2011-05-24
fine suggestion. I almost forgot about gedit. I even liked it when i started coding. Its easy to edit and to start with.
And, as soon as you are more comfortable, can use VI/EMACS VI is more easy to handle or may be just seems to me because I am average with emacs use ( so emac loves dont kill me..)
well, gedit is best option for you as suggested in the above post..

---

### Post by nvteighen on 2011-05-24
Please, do the following:

0. Copy and paste the following C++ Hello World into Gedit or any text editor you prefer. Save it as 'hello.cpp':
```

#include <iostream>

int main()
{
    std::cout << "Hello world!" << std::endl;
    return 0;
}

```

1. Open a Terminal, enter the directory where hello.cpp is saved and type the following:
```

g++ -o hello hello.cpp -Wall

```

The -o option defines the name the produced executable will have. I've chosen 'hello'. The -Wall flag enables all warnings; this is very useful as it allows to catch some bugs at compile-time. There are other stricter setups available, but let's ignore them for this post.

2. We'll run 'hello' now:
```

./hello

```

If everything went fine, then the code you were using is likely to be incorrect. If "Hello world!" isn't printed when 'hello' is executed or you can't even compile the program, please, post the terminal output here.

---

### Post by rpmp on 2011-05-24
hey thnaks i realised i had a little error (¨ instead of ") but i fixed and it worked with using codeblocks and also the terminal so thanks.

---

### Post by jamesjenner on 2011-05-24
> **rpmp said:**
> hey thnaks i realised i had a little error (¨ instead of ") but i fixed and it worked with using codeblocks and also the terminal so thanks.

No worries mate, we're all happy to help someone who is taking their first steps :)

Remember to use the thread tools and mark the thread as solved please.

---

