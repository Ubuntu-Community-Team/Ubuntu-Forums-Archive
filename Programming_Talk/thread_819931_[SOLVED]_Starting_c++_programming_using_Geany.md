---
title: "[SOLVED] Starting c++ programming using Geany"
date: 2008-06-05
forum: Programming Talk
---

### Post by jjblackfox on 2008-06-05
Hello, I'm using a c++ ide compiler called Geany. I wrote a test program and compiled it and saved it to my desktop. 
It compiled fine and I tried compiling the program by pressing the Execute button in Geany and received the following error:

Failed to execute the terminal program

I read that someone had the same problem and somebody told them that it was because they didn't link it properly. Since I am using an IDE, do I still need to link the program and if so, how do I do it?

---

### Post by LaRoza on 2008-06-05
Ok, a few issues:

[list]
[*] Geany isn't a compiler
[*] If you didn't install the needed packages, you cannot compile from geany or elsewhere.
[*] See the sticky on compiling and running programs in C++ (and C). Do it from the command line (to verify everything works) and then try the IDE again. If you get an error, tell us.
[/list]

---

### Post by jjblackfox on 2008-06-05
> **LaRoza said:**
> Ok, a few issues:

[list]
[*] Geany isn't a compiler
[*] If you didn't install the needed packages, you cannot compile from geany or elsewhere.
[*] See the sticky on compiling and running programs in C++ (and C). Do it from the command line (to verify everything works) and then try the IDE again. If you get an error, tell us.
[/list]
I tried compiling and running the code in the terminal and it worked, but when I tried to run it in Geany it gave me the same error. It compiles fine, but it doesn't execute.

---

### Post by LaRoza on 2008-06-05
> **jjblackfox said:**
> I tried compiling and running the code in the terminal and it worked, but when I tried to run it in Geany it gave me the same error. It compiles fine, but it doesn't execute.

This is the trouble with IDE's, you never know what they are doing easily.

Can you run the program that Geany makes in the terminal?

---

### Post by jjblackfox on 2008-06-05
> **LaRoza said:**
> This is the trouble with IDE's, you never know what they are doing easily.

Can you run the program that Geany makes in the terminal?

Yes, it runs perfectly.

---

### Post by LaRoza on 2008-06-05
> **jjblackfox said:**
> Yes, it runs perfectly.

Sounds like a problem with Geany (aren't I clever?).

The easiest thing to do is not use Geany for now. Or you could look into the problem, but you have all you need to compile, and it works. No reason to use tools that get in the way.

(Gedit and its plug ins make it better than most IDE's IMO)

---

### Post by jjblackfox on 2008-06-05
> **LaRoza said:**
> Sounds like a problem with Geany (aren't I clever?).

The easiest thing to do is not use Geany for now. Or you could look into the problem, but you have all you need to compile, and it works. No reason to use tools that get in the way.

(Gedit and its plug ins make it better than most IDE's IMO)
Is there a tutorial for gedit? All the plugins made it a bit too overwhelming for me, so I decided to just use an ide.

---

### Post by LaRoza on 2008-06-05
> **jjblackfox said:**
> Is there a tutorial for gedit? All the plugins made it a bit too overwhelming for me, so I decided to just use an ide.

They are simple. Install them:

```
sudo aptitude install gedit-plugins
```

To to Edit->Preferences->Plug ins

I recommend the Embedded Terminal and the File Browser Pane at the very least. You will have to go use View->Side Pane|Bottom Pane to see them.

---

### Post by jjblackfox on 2008-06-05
> **LaRoza said:**
> They are simple. Install them:

```
sudo aptitude install gedit-plugins
```

To to Edit->Preferences->Plug ins

I recommend the Embedded Terminal and the File Browser Pane at the very least. You will have to go use View->Side Pane|Bottom Pane to see them.
Thanks a lot for all your help :KS

---

### Post by Can+~ on 2008-06-05
Geany can't run the thing, you must compile it first.

Click on "Compile" (on the menu) then "Run", I added a shortcut to F8, so I have F8-compile F9-run.

But I would follow LaRoza's advince, and learn how to use the shell to compile and gedit as the editor, so you can work in any place, and don't get emotionally attached to an IDE (like most Visual Studio guys do (FLAMEWARS?)).

---

### Post by jjblackfox on 2008-06-05
> **Can+~ said:**
> Geany can't run the thing, you must compile it first.

Click on "Compile" (on the menu) then "Run", I added a shortcut to F8, so I have F8-compile F9-run.

But I would follow LaRoza's advince, and learn how to use the shell to compile and gedit as the editor, so you can work in any place, and don't get emotionally attached to an IDE (like most Visual Studio guys do (FLAMEWARS?)).

It works now, you have to go under build and press build before you can execute. Thanks for the PM Can+~

---

### Post by LaRoza on 2008-06-05
> **Can+~ said:**
> 
But I would follow LaRoza's advince, and learn how to use the shell to compile and gedit as the editor, so you can work in any place, and don't get emotionally attached to an IDE (like most Visual Studio guys do (FLAMEWARS?)).

I agree, you should follow my advise (or advince).

So many people complain about the command line and how great IDE's are, but the most problems are with the IDE's...

---

### Post by Can+~ on 2008-06-05
> **jjblackfox said:**
> It works now, you have to go under build and press build before you can execute. Thanks for the PM Can+~

Yup, for the record, how to compile/run on C/C++:
-Build menu -> click on "Build", not "Compile", it's misleading.
-Click on Run (the cogs).

And how the hell did I typed *advince*?

---

### Post by LaRoza on 2008-06-06
> **Can+~ said:**
> 
And how the hell did I typed *advince*?

The compiler should have flagged it.

```

/tmp/ccYXAVl8.o: In function `post':
ubuntuforums.org:(.text+0x19): undefined reference to `advince'
collect2: ld returned 1 exit status
```

---

### Post by cerberus920 on 2008-06-22
Whether it be LaRoza's *advise*, Can+~'s *advince* I just want to express my appreciation to the two of you for helping to clear up the same trouble that I was having.

I am just starting to dabble in code.  From what I have seen while looking at IDE's, I think I'll try my hand at Gedit.  The IDE's seem to have too many issues, especially with clarity in their interfaces from what I have seen.

So I have one last question regarding Geany.  If you need to build before executing, what is the point of the compile command in the interface?  Is this equal or similar to when I do *make* on source code that I download before a *make install*?  I'm just looking for more trivial information & understanding, as at this point, coding is all Greek (or pascal, fortran, take your pick) to me.

Thanks for all your patience & assistance with us n00bs.

---

### Post by LaRoza on 2008-06-22
> **cerberus920 said:**
> Whether it be LaRoza's *advise*, Can+~'s *advince* I just want to express my appreciation to the two of you for helping to clear up the same trouble that I was having.

So I have one last question regarding Geany.  If you need to build before executing, what is the point of the compile command in the interface?  Is this equal or similar to when I do *make* on source code that I download before a *make install*?  I'm just looking for more trivial information & understanding, as at this point, coding is all Greek (or pascal, fortran, take your pick) to me.


I am always right (even when  I am wrong).

Here is a basic run down of compiling and building. (Using C, C++ works the same probably).

The command for the compiler is gcc, and you can check out its man pages for all the info.

First, it is preprocessed. You can have it stop there with the -E option. After the proprocessor is finished, it is compiled (you can stop it here with the -c option), after it is compiled, it is linked (with "ld"). 

Usually, when dealing with multiple source files, you don't want to recompile everything, so you compile the files and link them as needed. (I guess this would be the difference between "compile" and "build")

By default, gcc compiles and links.

A make file is just a file that gives all the rules and such for automating the process.

---

### Post by amp3030 on 2008-08-26
> **Can+~ said:**
> Yup, for the record, how to compile/run on C/C++:
-Build menu -> click on "Build", not "Compile", it's misleading.
-Click on Run (the cogs).

And how the hell did I typed *advince*?

No. It doesn't work for me. I have just a simple c++ code, without any Makefile, dependency, ... I can compile it in terminal by "g++ filename.cpp" and run it by "./a.out" and I can compile a working executable by Geany. But when I click on Build -> Execute, it says "failed to execute the terminal program"

I know it is not good to be attached to a particular IDE, but pressing Alt-tab to find terminal window each time I change the code (to compile and run it) is very annoying. If you had to run another terminal window to run gnuplot on it to visualize the output, the situaion could be even worse.

Could anyone please test Geany if it can compile and run a simple "hello-world" program (a single source file) from its toolbar?

---

### Post by cmay on 2008-08-26
> Could anyone please test Geany if it can compile and run a simple "hello-world" program (a single source file) from its toolbar?
thats an old tread.
i use almost only geany for c and perl and pascal sources.
i compile and click on the toolbar  whitout any problem at all.
i think you can just change it in the default settings.

---

### Post by Xyc0 on 2008-09-10
Build > Set Includes and Arguments

I used the following arguments to reference the output file

Compile: gcc -Wall "%f" -o "%e"

Build and Execute should be fine as defaults

Build: gcc -Wall "%f"

Execute: "./%e"

________________________________________
"Linux is only free if your time is worthless"

---

### Post by vineeshvs on 2010-09-29
i have installed geany 2 days back. i just specified sudo apt-get install geany. and then i got one version of geany installed in my computer. will that be the latest version???? do i need to install more plugins. 

anyway i have done sudo aptitude install gedit-plugins also.

---

