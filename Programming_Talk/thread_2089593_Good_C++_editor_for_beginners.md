---
title: "Good C++ editor for beginners"
date: 2012-11-29
forum: Programming Talk
---

### Post by cheatos on 2012-11-29
Hi all,

I have to write a C++ program which does a FFT on some data input and I am unsure which editor will be best for me. As I am a physicist, a simple editor would completely satisfy my needs. However I downloaded vim and it was horrible, I didn't even get it to compile some example code...
I was thinking about eclipse but as far as I know eclipse is an editor for java. Will it also understand C++? And are there some editors with some sort of syntax highlighting or however you call that in C++?

Thanks for any help!

---

### Post by mevun on 2012-11-29
I've never used **gedit** for programming, but it is built-in to Ubuntu and is supposed to be friendly since it is GUI-based.    It probably understands C++ syntax, but I'm not sure.

As for Eclipse, it can understand C++.  Might be overkill, if you aren't really going to set up a whole 'project'.  The download for Eclipse is several hundred megabytes.

As for FFT, I think you should look for a library that does that already or some source code.  You shouldn't really need to re-write it from scratch.

---

### Post by MG&amp;TL on 2012-11-29
> **cheatos said:**
> Hi all,
I have to write a C++ program which does a FFT on some data input and I am unsure which editor will be best for me. As I am a physicist, a simple editor would completely satisfy my needs. However I downloaded vim and it was horrible, I didn't even get it to compile some example code...
I was thinking about eclipse but as far as I know eclipse is an editor for java. Will it also understand C++? And are there some editors with some sort of syntax highlighting or however you call that in C++?

Thanks for any help!

*vim* is an advanced editor for those who do a lot of text editing. Incidentally, it won't compile anything, it's just an editor. Worth learning if you ever have to do a lot of editing. 

*Eclipse* is good for C++ (although probably not for beginners), but I suggest you install the *eclipse-cdt* package (I understand CDT stands for C Developer Tools). Makes life easier.

What I would actually recommend is Geany, a lightweight IDE/text editor. 

Brave physicist. FFTs with C++ isn't a beginner's project. Good luck!

---

### Post by steeldriver on 2012-11-29
I'm liking geany at the moment

For the FFT itself you should probably check out FFTW - even if it's not what you want it will give you a starting point - although it's a C library there are C++ headers for it iirc

---

### Post by trent.josephsen on 2012-11-29
I use Vim, myself, but I like to recommend jEdit for beginners and people in general who don't wish to invest time in learning Vim or Emacs. jEdit is vaguely Emacs-like but it has a much friendlier interface (IMHO) along with support for a vast array of languages and all the features we have come to expect from our general-purpose editors (and then some).

If you're looking for an IDE and not just an editor, I'm not the one who can help you.

As for the FFT stuff, I don't envy you ;)

Edit: Oh no, I got sucked into another of *these* threads...

---

### Post by Unterseeboot_234 on 2012-11-29
C and C++ are all about linking. Legacy C++ code is readable about where the links came from. With C you have to maintain external documentation. For that reason, I like NetBeans with the added C/C++ plug-in.

You would have to have Java installed for the NetBeans IDE, then add the C++ plug-in. You get syntax coloring, matching braces as niceties for an editor and GUI-dialogs for pre-process and post-process compiling.

See if you can follow along in this linked [[COLOR="Blue"]tutorial[/COLOR]]("http://netbeans.org/kb/docs/cnd/quickstart.html") on setting up a C++ project.

Good luck in whatever choice you go with.

---

### Post by overcast on 2012-11-29
Sublime text 2 can be used for free. Geany is also not a bad choice for C++ IDE.

---

### Post by vanangamudi on 2012-11-30
Emacs. use Emacs. awesome editor.... Emacs and Vim are considered to be the complete text editors by thousands of people...

---

### Post by shaktiman1234 on 2012-11-30
try using Gedit for editing and terminal for executing . That is besy way to learn.
If you can use vim, that will be added advantage but learning curve can be quite steep.

---

### Post by Majorix on 2012-11-30
I use emacs (check the avatar :D), however it is not for "beginners". You could have a look at SciTe instead.

---

### Post by muteXe on 2012-11-30
I'll probably be shot for this but...
If you got a windows box an express edition of visual studio is pretty good.

---

### Post by MG&amp;TL on 2012-11-30
> **muteXe said:**
> I'll probably be shot for this but...
If you got a windows box an express edition of visual studio is pretty good.

You won't be. 

I concur fully, visual studio, for all the platform's many flaws (not windows-bashing, but .NET makes me want to scream sometimes), is an exceptionally good IDE.

---

### Post by Majorix on 2012-11-30
VS is best if you are developing in C# or VB.NET, hands down. However many people still use it for C++ too. I haven't tried doing so, since I feel it is not the best platform to do so.

---

### Post by cheatos on 2012-12-01
First of all, thanks for your fast responses.

However, I will have to write the program by myself, as it is part of the experiment to develop a FFT C++ program.

I also found SciTe when I was looking around for some editor but wasn't sure about that one. I'll try gedit as well.

However, despite being only optimal for writing C#, I somehow dislike the Windows version, as my computer is pretty old already and I don't want to program in a virtual machine.

(By the way, would that be recommended, so my program can't mess with my main system?)

Greetings to all of you!

---

### Post by MG&amp;TL on 2012-12-01
Unless you're going to be opening and writing to important files, don't worry about sandboxing your programs. They won't mess anything up, trust me.

---

### Post by zobayer1 on 2012-12-02
Did anyone mention CodeBlocks yet? That's a good IDE too. However, if you are learning programming, you should not really try to use an IDE at an early stage. Because, you will not grow the ability to find bugs without the help of a debugger. Also, you can learn more ins and outs of programming and how systems work and interact among themselves. For example, as someone mentioned earlier, by using vim, you can also master a lot of tricks than just writing code, clicking auto completion and hitting the cute green play button.

---

### Post by cheatos on 2012-12-02
Hello again,

so now I donwloaded gedit and gcc but when I try to compile a primitive program, which I copied from here:
[HTML]http://www.cplusplus.com/doc/tutorial/program_structure/[/HTML]I get the following error code:
```

gcc: error: cplusplustest: No such file or directory
gcc: fatal error: no input files
compilation terminated.

```What exactly am I doing wrong?

---

### Post by MG&amp;TL on 2012-12-02
My guess is what it's telling you: the file doesn't exist. Make sure it is where you think it is (and it isn't!) by running the "ls" command, or running a file manager.

EDIT: You *have* saved the file, right?

---

### Post by cheatos on 2012-12-03
I have saved the file, and here is my terminal window:

```

michael@MichaelsPC:~/Documents/HAWS1213/FP$ ls cplus*
cplusplustest
michael@MichaelsPC:~/Documents/HAWS1213/FP$ gcc -o /home/michael/Documents/HAWS1213/FP/cplusplustest cplusplustest.c
gcc: error: cplusplustest.c: No such file or directory
gcc: fatal error: no input files
compilation terminated.

```

So exactly where I am searching for the file...

---

### Post by zobayer1 on 2012-12-03
> **cheatos said:**
> I have saved the file, and here is my terminal window:

```

michael@MichaelsPC:~/Documents/HAWS1213/FP$ ls cplus*
cplusplustest
michael@MichaelsPC:~/Documents/HAWS1213/FP$ gcc -o /home/michael/Documents/HAWS1213/FP/cplusplustest cplusplustest.c
gcc: error: cplusplustest.c: No such file or directory
gcc: fatal error: no input files
compilation terminated.

```So exactly where I am searching for the file...

first try the simple things, just open a folder and create something.c there
write a few lines of c codes
```

int main() { return 0; }

```

on terminal, use cd to move to your folder.
then
```

gcc something.c
./a.out

```

See if this works.

---

### Post by MG&amp;TL on 2012-12-03
> **cheatos said:**
> 
michael@MichaelsPC:~/Documents/HAWS1213/FP$ ls cplus*
**cplusplustest**
michael@MichaelsPC:~/Documents/HAWS1213/FP$ gcc -o /home/michael/Documents/HAWS1213/FP/cplusplustest **cplusplustest.c**
gcc: error: cplusplustest.c: No such file or directory
gcc: fatal error: no input files
compilation terminated.
So exactly where I am searching for the file...

1. *cpluplustest* isn't the same as *cplusplustest.c, *so you need to rename it.

2. Are you using C, or C++? If you're using C++, use *g++*.

---

### Post by cheatos on 2012-12-03
Hi, first of all, good news.
After installing g++ instead of gcc and renaming the file from cplusplustest to cplusplustest.c it works now. However, how can I "execute" the program, now that I have compiled it? By the instructions on the website (and as far as I understand the program) it should display Hello World now...

---

### Post by zobayer1 on 2012-12-03
> **cheatos said:**
> Hi, first of all, good news.
After installing g++ instead of gcc and renaming the file from cplusplustest to cplusplustest.c it works now. However, how can I "execute" the program, now that I have compiled it? By the instructions on the website (and as far as I understand the program) it should display Hello World now...

As you are using g++, you should name your files with extension .cpp instead .c and to run the program, just write the address of your executable file on the terminal.

If you specify a -o parameter, then the executable have the name you specified after -o and if you haven't done so, the executable will have the name "a.out" by default. So if you are in your current working directory in terminal, just put ./a.out or ./yourexe assuming you put "-o yourexe" during compilation.

Here is an example:
```

zobayer@precise:Temporary$ cat test.cpp
#include <cstdio>

int main() {
    printf("Hello World\n");
    return 0;
}
zobayer@precise:Temporary$ g++ test.cpp -o test
zobayer@precise:Temporary$ ./test
Hello World
zobayer@precise:Temporary$ g++ test.cpp
zobayer@precise:Temporary$ ./a.out
Hello World
zobayer@precise:Temporary$ 

```

---

### Post by cheatos on 2012-12-07
Thanks zobayer, now I can compile and rename the program.

I also found out, that nano has syntax highlighting and may be used for editing. Probably I'll try that first.

---

### Post by zobayer1 on 2012-12-07
> **cheatos said:**
> Thanks zobayer, now I can compile and rename the program.

I also found out, that nano has syntax highlighting and may be used for editing. Probably I'll try that first.

I haven't used nano yet, for small programs, I use either gedit or vim (both has highlighter and vim has lots of other tricks), but for larger projects, I would always go for an IDE as they offer easier and cleaner organization of sources and resources.

---

### Post by jon zendatta on 2012-12-07
> **shaktiman1234 said:**
> try using gedit for editing and terminal for executing . That is besy way to learn.
If you can use vim, that will be added advantage but learning curve can be quite steep.
:ks

---

### Post by verzx on 2012-12-07
It makes it better/easier in the long run if you can type it in a text editor and use a debugger to execute it.

---

### Post by cheatos on 2012-12-08
So, what actually is a debugger?
is it a part of vim?
And won't the compiler tell me when I did something wrong?

---

### Post by Majorix on 2012-12-08
It's what its name implies: A tool to help you debug your program. It has the ability to run your code part by part, line by line, function by function, ... letting you see what is happening on each step. You can print the status of variables, and even change them at place.

You could have a look at gdb, which stands for GNU Debugger. Check the web for information on how to use it, as it is out of the scope of this post to explain all that.

---

### Post by cbennett926 on 2012-12-08
CodeBlocks!!!

---

### Post by MG&amp;TL on 2012-12-08
> **cheatos said:**
> So, what actually is a debugger?
is it a part of vim?
And won't the compiler tell me when I did something wrong?

To expand a little on what Majorix said:

What is a debugger? Well, a debugger allows you to step, line by line, instruction by instruction, through a binary executable, looking at the content in your programs, and changing it if you wish. It's extremely useful for finding bugs like memory faults (i.e. where you've done something you're not supposed to and the compiler can't catch it), and logic errors, where your program doesn't do what it is supposed to do, but you can't work out why.

It's not a part of vim, no. You can boot it up with "gdb <executable>", preferably if you compile it with debug flags enabled. It's not an intuitive interface, but there are tutorials online.

Yes, the compiler will tell you if you're doing something obviously wrong. However, the compiler is only so smart, and won't trace all the paths your program could take. It's also no good at all for logic errors.

---

### Post by cheatos on 2012-12-09
So, if I understand you correctly, I would compile my program and then run the debugger on the compiled program, right?

So if I made a mistake my debugger will tell me and if the compiler won't compile I get an error code of the compiler.

Sorry for these pretty stupid questions...

---

### Post by MG&amp;TL on 2012-12-09
> **cheatos said:**
> So, if I understand you correctly, I would compile my program and then run the debugger on the compiled program, right?

So if I made a mistake my debugger will tell me and if the compiler won't compile I get an error code of the compiler.

Sorry for these pretty stupid questions...

Yup, you got it. Development (at least for me) goes:

(0. Design)
1. Code
2. Compile (there is errors, go back to 1)
3. Run (there are memory problems)
4. Debug (and fix).
5. Run (There are problems, go back to 4)

(6. Go back to 0 with a new featureset).

---

### Post by cheatos on 2012-12-09
Well thank you then, I'll do the project with some guy who has already programmed in java and assembly, so I won't need to do it on my own but still wanted to at least have the reqiurements to code and compile something...

Thanks to all of you!

PS is there an option to mark the thread as solved? I know there is one in the beginners section...

---

### Post by zobayer1 on 2012-12-11
Reply deleted, sorry wrong post.

---

