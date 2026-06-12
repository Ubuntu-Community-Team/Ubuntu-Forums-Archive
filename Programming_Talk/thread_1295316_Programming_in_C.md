---
title: "Programming in C"
date: 2009-10-19
forum: Programming Talk
---

### Post by mocatz187 on 2009-10-19
I am new to Linux. I have been programming in C for about 5 months in windows.
In Kubuntu I cannot figure out how to use the compiler or even how to get into the text editor.
I wan't this to be simple and basic like pico / nano with gcc. 
I am not interested in trying special or different text editors at this time. 
I was under the impression that most Linux distributions had some basic developement tools but I can't access ANYTHING!
If these developement tools are not available then can someone recommend a Linux distro that allows developement work. I don't want to patch and install my way to an OS that that does this, it must work in the most basic form.
 
 
thanks

---

### Post by benj1 on 2009-10-19
gcc is in the build essential package

```
sudo apt-get install build-essential
```

editors you have vim and nano and you have kate (i think) which is gui.

to get syntax highlighting in nano you need to copy the file from /etc/nanorc and copy it to ~/.nanorc 

```
cp /etc/nanorc ~/.nanorc
```
then modify/uncomment that to point to /usr/share/nano/c.nanorc

---

### Post by korvirlol on 2009-10-19
> I wan't this to be simple and basic like pico / nano with gcc. 

what kind of problems are you having with this? at the very least, i know the text editor vi is installed (very good to get familiar with).

As for the compiler, gcc comes installed as default. Simple compile syntax(on the terminal):
```

gcc -o executeablename filename.c
```

---

### Post by Zugzwang on 2009-10-19
First of all, try to open up a console. It's somewhere in your "Applications" menu. "Konsole" or "xterm" are both fine.

In the console, you can always open a text editor by, e.g., typing "gedit <yourfile>" or "kate <yourfile>" and pressing enter.

Then look into the stickies of this forum for information on how to compile your first program. Follow the steps carefully.

---

### Post by mocatz187 on 2009-10-19
I have Kate but how do invoke the compiler.
I was using Miracle C in windows previously and all you do is click open, you write, compile, link, then run. these were all simple links at the toolbar.
maybe I need a command prompt tutorial.

---

### Post by benj1 on 2009-10-19
never used it but it uses plugins so i would assume there would be a gcc plugin or as someone posted earlier

```
gcc -o executeablename filename.c
```

but if you want to do anything more complicated im sure google will find you something

---

### Post by jessiebrownjr on 2009-10-19
I use Gedit for my editing.. its like notepad, but you can select "C" on the bottom and it will color-code it as such... you can also save it as filename.c and it will turn it into C format as well..

Now when you do the terminal stuff heres some stuff I glanced over too

you type this to compile...

gcc sourcename.c -o nameofoutputfile

If you just type gcc sourcename, it compiles it into a .o file, named a-b-c etc
the -o (the letter) makes it straight to machine code ( im guessing is what it is) exe equiv...
There are alot of commands you can put into the command line to make it do various things, research them.

Also, to run your file... if you are in the current directory you type ./sourcefilename
Even if you are in the directory with the file, it wont run if you just type the name, unless you have that directory added to bash I(i think correct me if im wrong)

---

### Post by openfly on 2009-10-19
eclipse and anjuta can provide you with a decent IDE for development once the base dev software is in place.

---

### Post by mocatz187 on 2009-10-19
I've found Pico and it even has tabs for opening bash. I think I'll be alright now.:)
Thanks all

---

### Post by Can+~ on 2009-10-19
When I moved from Windows to Ubuntu, I found Geany quite good, had a simple Compile + Run buttons on top for single C files.

---

### Post by jessiebrownjr on 2009-10-19
> **Can+~ said:**
> When I moved from Windows to Ubuntu, I found Geany quite good, had a simple Compile + Run buttons on top for single C files.
That sounds like just what the doctor ordered for me! testing it out now.

---

### Post by nvteighen on 2009-10-20
> **jessiebrownjr said:**
> I use Gedit for my editing.. its like notepad, but you can select "C" on the bottom and it will color-code it as such... you can also save it as filename.c and it will turn it into C format as well..

Now when you do the terminal stuff heres some stuff I glanced over too

you type this to compile...

gcc sourcename.c -o nameofoutputfile

If you just type gcc sourcename, it compiles it into a .o file, named a-b-c etc
the -o (the letter) makes it straight to machine code ( im guessing is what it is) exe equiv...
There are alot of commands you can put into the command line to make it do various things, research them.

Also, to run your file... if you are in the current directory you type ./sourcefilename
Even if you are in the directory with the file, it wont run if you just type the name, unless you have that directory added to bash I(i think correct me if im wrong)

No... It's almost all wrong.

[LIST]
[*]The -o flag just specifies the output's name. If you don't use -o, the executable will be called a.out by default.
[*]To compile a source file into an object file (.o), you use the -c flag.
[*]What you say about directories is that in order to be able to run your program as a command, you have to put that program into a directory included in $PATH. Either copy it to /usr/local/bin (it's the safest... don't use /usr/bin for handmade programs) or include a directory of yours into bash's $PATH (this is maybe the best, but you'll have to edit your ~/.bashrc). If you don't do any of these, you have to run your program by entering the whole path (or ./application if it's in the current directory).
[/LIST]

---

### Post by sprince09 on 2009-10-20
+1 for Geany, that is an excellent IDE for C programs (at least for the smallish ones that I do...).

---

