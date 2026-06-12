---
title: "I think my terminal is broken...or my brain is."
date: 2012-09-11
forum: Programming Talk
---

### Post by davidson27 on 2012-09-11
so I started reading up on how to program in C++ yesterday, and at the end of the first section you end up with a hello world program.

I wrote the program in emacs and saved it as a .cpp file

I went to open it through the terminal and tried to change the CD to get to the folder it was saved in, the terminal returned that the directory didn't exist which is a complete load.

now, from the home directory if I type command ls it does list my downloads folder but if I command cd /home/downloads or cd /downloads I get the same response.

now onto my second problem.

since I wasn't able to change the directory with the terminal I thought I could bypass that problem by saving my .cpp file in the home folder and compile it that way but when I type command "G++ filename.cpp" I get a response saying command not found and a "did you mean" list 

again new to programming, new to linux, not too sure what I'm doing wrong here, please help.

---

### Post by Hadaka on 2012-09-11
Hi, yup clear case of brain melt from c++ :p

try  cd Downloads

tis a capitol "D"

---

### Post by dodo3773 on 2012-09-11
Your home folder is actually /home/yourusername/foldername. / is the root of your filesystem. So of course /Downloads won't work. It would still be /home/yourusername/Downloads. There is a shortcut for $HOME as "~". So, "cd ~/Downloads" will work as long as you are logged in as your normal user and not root (because root's $HOME is different from yours).

---

### Post by davidson27 on 2012-09-11
Thanks for the quick response, that takes care of the directory issue but any thoughts on why I'm unable to compile .cpp stuff, I thought maybe I messed up on the code after I wrote it the first time but then I did a drag and drop into emacs and it still wasn't working.

---

### Post by anewguy on 2012-09-11
Just make sure of a couple of things:

- you have the build-essential package installed (not sure, you might need to install g++ separately - I've used gcc for normal c)

- remember the command is "gcc" or "g++" -> linux is case sensitive so you can't use "Gcc" or "G++".

---

### Post by dodo3773 on 2012-09-11
> **davidson27 said:**
> Thanks for the quick response, that takes care of the directory issue but any thoughts on why I'm unable to compile .cpp stuff, I thought maybe I messed up on the code after I wrote it the first time but then I did a drag and drop into emacs and it still wasn't working.

I do not know what you mean by drag and drop or how that affects compiling code (I didn't know you could drag and drop in emacs (ignorant vim user here haha)). You save a file and then compile it. That's it. You should post the code you are trying to compile, your gcc version, etc, etc.. It would probably be in your best interests to start a new thread though in the appropriate section. Should be something similar to this:

```

g++ -o binaryname sourcefilename.cpp

```

If you are having problems with using emacs there are a lot of gui editors out there (in the end you will probably be happy if you stick with and learn emacs or vim though).

---

### Post by davidson27 on 2012-09-11
ok so heres the code that was on a site

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

im using emacs 23.3.1 and i just updated the build package 

and in the terminal the command I'm typing is just "g++ filename.cpp"
what is  "-o binaryname" about?

---

### Post by dodo3773 on 2012-09-11
> **davidson27 said:**
> ok so heres the code that was on a site

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

im using emacs 23.3.1 and i just updated the build package 

and in the terminal the command I'm typing is just "g++ filename.cpp"
what is  "-o binaryname" about?

You have to tell the compiler what you want to save your program as. -o is the outfile (if that makes sense) and the second argument is the source file (filename.cpp). So after it compiles in that directory you will have a binary (or a compiled application) called whatever you told -o to send it to.

---

### Post by davidson27 on 2012-09-11
so would g++ -o program1 program.cpp work?

---

### Post by dodo3773 on 2012-09-11
> **davidson27 said:**
> so would g++ -o program1 program.cpp work?

It should. If the source file for your hello world program was saved as "program.cpp". After that you would have to allow the binary to execute "chmod +x program1" and then run it "./program1" to test.

Edit: By default it should have executable permissions probably. Doubt chmod is needed.

---

### Post by davidson27 on 2012-09-11
I'm still having some issue with it if i type the command "g++ -o program1 program.cpp(which is the name of the saved file)" the terminal gives me a huge error message and it wont even display all of it.

---

### Post by dodo3773 on 2012-09-11
> **davidson27 said:**
> I'm still having some issue with it if i type the command "g++ -o program1 program.cpp(which is the name of the saved file)" the terminal gives me a huge error message and it wont even display all of it.

I am probably running a different version of gcc than you but it shouldn't matter. Anyways, I tried it and it compiled fine for me. cat out the source file to make sure it is correct (no misspelling, case sensitive errors, indentation problems, etc..) like this "cat program.cpp"

---

### Post by davidson27 on 2012-09-11
ok so I did that and terminal showed me the code that I wrote and as far as I can tell it's right like I said I copied and pasted that from a website into emacs, and other first programs I've found are the same. could it be an underlying issue with my operation system?

---

### Post by dodo3773 on 2012-09-11
> **davidson27 said:**
> ok so I did that and terminal showed me the code that I wrote and as far as I can tell it's right like I said I copied and pasted that from a website into emacs, and other first programs I've found are the same. could it be an underlying issue with my operation system?

The code is so simplistic that I do not see how it could fail. Check your version of g++ "g++ --version" and inspect your code. Other than that I am not really sure what to tell you. If the compiler in the repos cannot handle that (I am almost positive it is a user error somewhere) then you should probably go distro shopping. Wish I could help more or test this further but I do not run Ubuntu.

---

### Post by davidson27 on 2012-09-11
It might be an OS problem because I tried to learn C++ a couple months ago and I didn't have this issue at all. dodo thanks for all your help, it was much appreciated.

---

### Post by anewguy on 2012-09-11
Run your g++ line again, but append > ~/junktest.txt to the end of it.  This will hopefully pipe that error message to a file called junktest.txt in your home folder.  Post back and attach that file so we can see the entire thing.  Also, I admittedly didn't take the time to look on my own, but I believe there is a way on the g++ line to direct messages, etc., to a file as well.

---

### Post by anewguy on 2012-09-11
BTW - I can't see it being an OS problem - more likely something else (like as stupid as I am I *thought* name space std was a Windows thing).  At any rate, after seeing the error in the file we can go from there.

---

### Post by dodo3773 on 2012-09-11
> **anewguy said:**
> Run your g++ line again, but append > ~/junktest.txt to the end of it.  This will hopefully pipe that error message to a file called junktest.txt in your home folder.  Post back and attach that file so we can see the entire thing.  Also, I admittedly didn't take the time to look on my own, but I believe there is a way on the g++ line to direct messages, etc., to a file as well.

I just compiled it on my system and it worked fine. Can't you just test it real quick if you don't mind? It only takes about 1.5 seconds to compile. I am running a different distro and gcc so the results may be different.

---

### Post by anewguy on 2012-09-11
Don't have Ubuntu up now, plus I'd need to install g++, and I need to get to bed.  What I can do is try it tomorrow.  As I said, it would help a lot to actually see your entire error message.  Just it may or may not work on my system doesn't mean that it won't work on yours - it's a matter of seeing the exact problem you are having and resolving it.

Also, you could try a couple of things:

change the include of iostream to iostream.h (the old way).  I seem to remember reading somewhere you would still need to do this at least in some situation in linux.

add:

namespace std{} prior to your using namespace std.  This will help with cross-platform usage, and I also seem to remember reading something about this with certain situations in linux as well.

---

### Post by oldos2er on 2012-09-11
Moved to Programming Talk.

---

### Post by coldcritter64 on 2012-09-11
```
yetiman@xxxxxxxx:~/Desktop$ **g++ --version**
g++ (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

yetiman@xxxxxxxx:~/Desktop$ **ls**
program1.cpp
yetiman@xxxxxxxx:~/Desktop$ **cat program1.cpp**
#include <iostream>
using namespace std;

int main ()
{
cout << "Hello World!";
return 0;
}

yetiman@xxxxxxxx:~/Desktop$ **g++ -o HelloWorld program1.cpp**
yetiman@xxxxxxxx:~/Desktop$ ls
**HelloWorld  program1.cpp**
yetiman@xxxxxxxx:~/Desktop$ ./HelloWorld
**Hello World!**yetiman@xxxxxxxx:~/Desktop$
```Nothing wrong here. Just compiled my first program ever :wink:.

OP, posting (copying and pasting) your actual errors here in code tags will help out a lot. Regards, coldcritter64.

---

### Post by davidson27 on 2012-09-11
this is what i get from the command g++ -o program program.cpp

---

### Post by spjackson on 2012-09-11
> **davidson27 said:**
> this is what i get from the command g++ -o program program.cppPlease attach program.cpp since it does not appear to be what you posted. I know this forum won't let you attach .cpp so copy it to .txt and attach that, without any editing.

---

### Post by davidson27 on 2012-09-12
i did post the code but here it is again as .txt

---

### Post by anewguy on 2012-09-12
Look at your error message file - what's up top?  Problems with your comments, hence the error message with "This".  Try removing your comments and see what happens.

---

### Post by dodo3773 on 2012-09-12
That is not the code you posted before. Take out the comments like anewguy said and remove the "system("pause");" line.

---

### Post by coldcritter64 on 2012-09-12
> **davidson27 said:**
> ....```
#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

```...
 I've put the code tags around your previous code for clarity.

Your .cpp file attached above (last post),

```
#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!\n";
  system("pause");
}
```Not the same.

Edit: sorry, dodo3773 beat me at posting :-)

---

### Post by davidson27 on 2012-09-12
ok i took out the return 0; line and the buffer from the top and it worked. thanks guys!!

enjoy this popcorn:popcorn:

edit: i meant i took away the system pause and replaced it with return 0; and it worked

edit again: i at the site that code came from and the author was using windows, is there a difference in c++ commands between windows and linux? if so any ideas on how to avoid that in the future?

---

### Post by lisati on 2012-09-12
> **davidson27 said:**
> 
edit again: i at the site that code came from and the author was using windows, is there a difference in c++ commands between windows and linux? if so any ideas on how to avoid that in the future?
Generally speaking, if you stick with text based programs that work from the command line or terminal, and use only "standard" library calls, it's usually fairly straightforward to write code that's portable between Windows and Linux. Developing portable programs with a graphical interface is another story.....

---

### Post by davidson27 on 2012-09-12
is that because linux uses opengl and windows uses directx?

---

### Post by anewguy on 2012-09-12
No, it's a completely different idea between the 2 - different ways of doing things to develop the GUI.  See GTK or QT for examples of things you can use that are also available for Windows.  I've written C code using GTK in Linux and just took it straight to Windows and compiled and ran fine - I just had to install the GTK package in Windows first and I used mingw so I have a linux-feel command line to do the compiling in Windows.  After that, ran as a straight Windows' GUI'd applications.

---

### Post by anewguy on 2012-09-12
BTW - I *think* the system("pause") is still valid in Linux, but I would have to double-check.  I seem to remember people defining a "wait_for_user" as "system("pause")" and then just using "wait_for_user", which is still using "system("pause")".  I know for sure your comments were hosing you up before.  You might want to take the code that does compile and run and try putting the system("pause") back in to test if that works.

---

### Post by trent.josephsen on 2012-09-12
I don't know about you but

```
% pause
zsh: command not found: pause
```

---

### Post by anewguy on 2012-09-12
Hummmmm - bash shell?  I'll have to try somethings here.  That may be why the define was there that I mentioned - you could change just that one define if the action had a different name in a different OS.

EDIT:  Indeed, no equivalent of the old msdos pause in bash, however I did find another post on the internet that provided the answer:

 read -n1 -r -p "Press any key to continue..." key

So, in the case of this program, it should read:

  system(" read -n1 -r -p \"Press any key to continue...\" key");

That is, *IF* I'm remembering how to get the imbedded quotes past the compiler! ;)

There's one other thing I'm not sure of here - if this particular use of system would be synchronous or asynchronous to the executing program - in other words, would the program wait for system to return, or would it just make the call and continue (in this case exiting).


Thanks!
Dave ;)

---

### Post by dodo3773 on 2012-09-12
Please read this:

[http://www.gidnetwork.com/b-61.html](http://www.gidnetwork.com/b-61.html)

and see this thread:

[http://www.cplusplus.com/forum/unices/39066/](http://www.cplusplus.com/forum/unices/39066/)

From thread above ^^:
```

cin.ignore().get(); //Pause Command for Linux Terminal

```

---

### Post by anewguy on 2012-09-13
Yea, using c++.  I was just trying to find a way using the original system call idea the OP had.  No arguements from me!

Dave ;)

---

### Post by spjackson on 2012-09-13
> **anewguy said:**
> 
 read -n1 -r -p "Press any key to continue..." key

That works in bash but system() does not invoke bash it invokes sh. See man system.

> 
There's one other thing I'm not sure of here - if this particular use of system would be synchronous or asynchronous to the executing program - in other words, would the program wait for system to return, or would it just make the call and continue (in this case exiting).

OK, from man system...
> 
system()  executes a command specified in command by calling /bin/sh -c
command, and returns after the command has been completed.

That sounds like synchronous to me. If the command is explicitly backgrounded, i.e. with &, then we get into murkier waters, but we don't have that situation, so it's clearly synchronous.

---

### Post by anewguy on 2012-09-13
> **spjackson said:**
> That works in bash but system() does not invoke bash it invokes sh. See man system.
Ooppsss - didn't actually realize that.

> That sounds like synchronous to me. If the command is explicitly backgrounded, i.e. with &, then we get into murkier waters, but we don't have that situation, so it's clearly synchronous.
also nice to know.  Seems the same problems I ran into in the programming talk forum still exists.

---

### Post by Lux Perpetua on 2012-09-13
> **dodo3773 said:**
> 
...and see this thread:

[http://www.cplusplus.com/forum/unices/39066/](http://www.cplusplus.com/forum/unices/39066/)I hope every novice programmer reads the discussion in that thread. **system("pause");** or any of its Unix equivalents appearing at the end of a program is the result of a failure to understand what one is doing. If you run your console programs from a console, the way they're supposed to be run, then there's no need to force the user to press <Enter>, and doing so basically results in a broken program. 

Also, unrelated note: that nonsense at the top of the OP's source file shouldn't be called "comments." C++ Comments look like ```
// Comment
``` or ```
/* Comment */
```This crap:```
;; This buffer is for notes you don't want to save, and for Lisp evaluation.
;; If you want to create a file, visit that file with C-x C-f,
;; then enter the text in that file's own buffer.
```is what happens when you write your program in Emacs's ***scratch*** buffer, which (as it says) is for an entirely different purpose. (In fact, the text is even nice enough to tell you exactly what to do instead.)

---

