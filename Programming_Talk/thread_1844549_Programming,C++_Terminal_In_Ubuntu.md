---
title: "Programming,C++ Terminal In Ubuntu"
date: 2011-09-15
forum: Programming Talk
---

### Post by rahulras1993 on 2011-09-15
Hi Everyone,

Its been a while since I posted ;) , well anyway here's the deal, 

So I am doing Programming in C++ and I need a compiler to work and knowing the stability of Linux I would like to use Linux as my operating system for programming, now the problem I don't really want to install linux as my main operating system for now, so I installed it as a virtual machine, i.e. I used Virtual Box

Now when I go to Terminal and type vi program_name.cpp , and normally you press "i" for the input , but the terminal or should I say Compiler now won't agree with me, and it won't let me type my program , also when I try to delete a line , it goes up to the previous line and doesn't delete at all.

I use The same commands on a friends computer running linux and it works fine 

Any ideas what's wrong? I am using Ubutnu 10.10

Take Care :)

---

### Post by TeoBigusGeekus on 2011-09-15
Install vim (or gvim to get clipboard support).
Pure vi is archaic...

---

### Post by haqking on 2011-09-15
> **TeoBigusGeekus said:**
> Install vim (or gvim to get clipboard support).
Pure vi is archaic...

i thought vi defaulted to vim nowadays anyways ?

also as for faulty key input usually comes down to termtype.

see here for common Vi/vim issues i have seen come up

[http://vim.wikia.com/wiki/Backspace_and_delete_problems](http://vim.wikia.com/wiki/Backspace_and_delete_problems)
[http://vim.wikia.com/wiki/VimTip1290](http://vim.wikia.com/wiki/VimTip1290)

and here [https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)

---

### Post by TeoBigusGeekus on 2011-09-15
I don't know about ubuntu, but on Arch it's a symlink to ex:
```
[[Time:21:36 Location:~/Desktop]]
$ which vi
/usr/bin/vi
[[Time:21:36 Location:~/Desktop]]
$ file /usr/bin/vi
/usr/bin/vi: symbolic link to `ex'
```

---

### Post by docbop on 2011-09-15
> **rahulras1993 said:**
> 
Now when I go to Terminal and type vi program_name.cpp , and normally you press "i" for the input , but the terminal or should I say Compiler now won't agree with me, and it won't let me type my program

If you're going to program you need to get your computer fundamentals down.   VI is a editor not a compiler,  you will compile the source code you write in vi.   You will do all of this in a terminal.  Then another thing you need to start study gdb the debugger you will use to find errors in your programs.   If you are going program in C/C++ you also need to understand memory, stack, and computer basics.   If all that sounds like a lot you might want to consider learning a higher level language first, then move to lower level language like C/C++.

---

### Post by The Cog on 2011-09-15
Unless you're determined to use text-mode only, can I suggest a graphical editor? I use geany, which is in the repositories, and has goodies like syntax highlighting, a compile button and error highlighting.

You will need to install package **build-essential** which installs compiler, header files etc.

Moved to Programming Talk.

---

### Post by Ravenshade on 2011-09-15
Code::Blocks provided you can get it working is a great IDE for C++ 

However for text only I recommend gedit
and gcc || g++ for compiling.

---

### Post by cgroza on 2011-09-15
I see everyone is suggesting editors, so I will just throw Emacs in here :D.

---

### Post by rahulras1993 on 2011-09-16
Thank you all very much for your prompt replies.

However, I am quite familiar with programming in C++ on Windows using Borland C++ (Beginners) , but now I want to do it in Linux, but moving to Linux is quite a change, so I am sorry for my n00bish behavior :P 

Yes I understand "vi" is editor and NOT a compiler, and I know I have to use g++ or gcc to compile.

We use Fedora back in University, but I guess "vi" should work with any distro of Linux right? But does this have something to do with Virtual Box?

---

### Post by haqking on 2011-09-16
> **rahulras1993 said:**
> Thank you all very much for your prompt replies.

However, I am quite familiar with programming in C++ on Windows using Borland C++ (Beginners) , but now I want to do it in Linux, but moving to Linux is quite a change, so I am sorry for my n00bish behavior :P 

Yes I understand "vi" is editor and NOT a compiler, and I know I have to use g++ or gcc to compile.

We use Fedora back in University, but I guess "vi" should work with any distro of Linux right? But does this have something to do with Virtual Box?

no nothing to do with virtual box.

VI is an editor across Linux Distros and has been about since the late 70's i belive first coming as part of BSD unix, it is text editor thats all (well not all, it is a wonderful text editor ;-)

it should be built in to any *nix variant you use, or possibly Vim which is just the VI improved.

---

### Post by rahulras1993 on 2011-09-16
> **haqking said:**
> i thought vi defaulted to vim nowadays anyways ?

also as for faulty key input usually comes down to termtype.

see here for common Vi/vim issues i have seen come up

[http://vim.wikia.com/wiki/Backspace_and_delete_problems](http://vim.wikia.com/wiki/Backspace_and_delete_problems)
[http://vim.wikia.com/wiki/VimTip1290](http://vim.wikia.com/wiki/VimTip1290)

and here [https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)


Hi, Okay so I went through the sites, and I found [http://manpages.ubuntu.com/manpages/hardy/man1/nvi.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/nvi.1.html)

If you go to that page , and scroll down to where it says        i -Insert new text, before the cursor.

That command on my terminal doesn't work at all 

I don't get it.

---

### Post by haqking on 2011-09-16
> **rahulras1993 said:**
> Hi, Okay so I went through the sites, and I found [http://manpages.ubuntu.com/manpages/hardy/man1/nvi.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/nvi.1.html)

If you go to that page , and scroll down to where it says        i -Insert new text, before the cursor.

That command on my terminal doesn't work at all 

I don't get it.


so you mean you have run vi/vim and then when you press the letter i, it does not enter insert mode ?

just press the insert key itself, it does the same thing.

are you using vi or vim which is the vi improved ?

see here [http://vimdoc.sourceforge.net/htmldoc/insert.html](http://vimdoc.sourceforge.net/htmldoc/insert.html)

[http://www.udel.edu/topics/software/general/editors/unix/vi/commonvi.html#ins](http://www.udel.edu/topics/software/general/editors/unix/vi/commonvi.html#ins)

---

### Post by rahulras1993 on 2011-09-16
> **haqking said:**
> so you mean you have run vi/vim and then when you press the letter i, it does not enter insert mode ?

just press the insert key itself, it does the same thing.

are you using vi or vim which is the vi improved ?

see here [http://vimdoc.sourceforge.net/htmldoc/insert.html](http://vimdoc.sourceforge.net/htmldoc/insert.html)

[http://www.udel.edu/topics/software/general/editors/unix/vi/commonvi.html#ins](http://www.udel.edu/topics/software/general/editors/unix/vi/commonvi.html#ins)

Hi,

Yes exactly when I press "i" it doesn't let me insert, and when I press insert it does the same thing it just makes the error noise, 

I am using "vi" and I don't really know what "vim" means. I only understand it is an advanced text editor

---

### Post by haqking on 2011-09-16
> **rahulras1993 said:**
> Hi,

Yes exactly when I press "i" it doesn't let me insert, and when I press insert it does the same thing it just makes the error noise, 

I am using "vi" and I don't really know what "vim" means. I only understand it is an advanced text editor


vim like i said is vi improved.

vi is a little archaic as already mentioned.

vim should be installed by default in 10.10 though.

just do a:

```
sudo apt-get install vim
```

and then when you type vi or vim, vim should load by default

should fix your problem

---

### Post by nvteighen on 2011-09-16
> **rahulras1993 said:**
>  
I am using "vi" and I don't really know what "vim" means. I only understand it is an advanced text editor

vim is an improved version of vi ("ViMproved" or however vi-fans call that). IIRC, in Ubuntu and Debian, vi is replaced by vim when you install the whole thing. The vi that comes out of the box is just vi-core, a very simple version that's meant for system mantaining (reading docs and editing config files).

---

### Post by rahulras1993 on 2011-09-16
> **haqking said:**
> vim like i said is vi improved.

vi is a little archaic as already mentioned.

vim should be installed by default in 10.10 though.

just do a:

```
sudo apt-get install vim
```

and then when you type vi or vim, vim should load by default

should fix your problem


Ok great it worked , I was able to enter the code :D 

Then it gave me an error while compiling , stating g++ was not installed so I did a quick sudo getinstall to get the g++

But now when I type the following code

```
#include <iostream>
int main ()
{
cout<<"Hello World";
return 0;
}

```

It gives me an error
program1.cpp: In function ‘int main()’:
program1.cpp:4: error: ‘cout’ was not declared in this scope

I believe my code is very simple and straight forward, maybe it doesn't recognize the header files?

Also I am unable to type "\" but only "/" works , Don't know what gives.

---

### Post by haqking on 2011-09-16
> **rahulras1993 said:**
> Ok great it worked , I was able to enter the code :D 

Then it gave me an error while compiling , stating g++ was not installed so I did a quick sudo getinstall to get the g++

But now when I type the following code

```
#include <iostream>
int main ()
{
cout<<"Hello World";
return 0;
}

```It gives me an error
program1.cpp: In function &#8216;int main()&#8217;:
program1.cpp:4: error: &#8216;cout&#8217; was not declared in this scope

I believe my code is very simple and straight forward, maybe it doesn't recognize the header files?

Also I am unable to type "\" but only "/" works , Don't know what gives.

Glad you got your Vim sorted.

For C

[http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example/](http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example/)

For C++
[http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example-2/](http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example-2/)

---

### Post by rahulras1993 on 2011-09-16
> **haqking said:**
> Glad you got your Vim sorted.

For C

[http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example/](http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example/)

For C++
[http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example-2/](http://www.thegeekstuff.com/2009/09/how-to-write-compile-and-execute-c-program-on-unix-os-with-hello-world-example-2/)

I forgot to thank you, :) 

Well I think what's missing is using namespace std;, but it gives me an error again stating "g++: rahul: No such file or directory"


"

---

### Post by haqking on 2011-09-16
> **rahulras1993 said:**
> I forgot to thank you, :) 

Well I think what's missing is using namespace std;, but it gives me an error again stating "g++: rahul: No such file or directory"


"


```
whereis c++
```

---

### Post by rahulras1993 on 2011-09-16
> **haqking said:**
> ```
whereis c++
```

Well this is how I compile back at University , g++ object programname.cpp 

It works fine, 

However I gave the c++ a go,but it still says c++: test123: No such file or directory

I changed rahul.cpp to test123.cpp , because I thought there was a mismatch between my system's name and the program name, but nope :(

---

### Post by haqking on 2011-09-16
> **rahulras1993 said:**
> Well this is how I compile back at University , g++ object programname.cpp 

It works fine, 

However I gave the c++ a go,but it still says c++: test123: No such file or directory

I changed rahul.cpp to test123.cpp , because I thought there was a mismatch between my system's name and the program name, but nope :(


have you looked at second link i posted in my post #17 above ?

---

### Post by The Cog on 2011-09-17
I think package **build-essential** is what you want to install.

---

### Post by rahulras1993 on 2011-09-17
> **haqking said:**
> have you looked at second link i posted in my post #17 above ?

Thank you for solving all my problems, it works fine but I have to specifically use the c++ programname.cc 

But as a Student, I find that hard to take in without reason, and I want to deeply understand why do I compile use g++ at university and here I use c++ , what's the difference?

Sorry for my annoying nature , but I think I need to stick around a little more :)

---

### Post by haqking on 2011-09-17
> **rahulras1993 said:**
> Thank you for solving all my problems, it works fine but I have to specifically use the c++ programname.cc 

But as a Student, I find that hard to take in without reason, and I want to deeply understand why do I compile use g++ at university and here I use c++ , what's the difference?

Sorry for my annoying nature , but I think I need to stick around a little more :)


im not an expert but i think the c++ is the sun compiler as oppose to the gcc++ which is the GNU compiler, i think it to do with how you added your compile tools ?

Did you add build-essentials ?

I am not an expert developer though so its might be something completely different, need someone with more of a gcc knowledge than me here i think ;-)

---

### Post by GeneralZod on 2011-09-17
On my install, c++ appears to be (indirectly) symlinked to g++.

---

### Post by haqking on 2011-09-17
> **GeneralZod said:**
> On my install, c++ appears to be (indirectly) symlinked to g++.


yeah i thought it was, guess it depends on how he installed it.

build-essentials is the key here im guessing ?

---

### Post by rahulras1993 on 2011-09-18
> **haqking said:**
> yeah i thought it was, guess it depends on how he installed it.

build-essentials is the key here im guessing ?

Heh,

I found out my error, well I did a build-essentials run also, but everything was already installed, but I found out what went wrong, 

I compiled like this :- g++ rahul rahul.cpp 

But the way you compile is g++ -o rahul rahul.cpp

And then run it as ./rahul and it works fine

Heh, looks like it was my mistake oh well I learnt a lot thank you very much again :)

But I have no idea what "-o" does, wish they taught us what these commands mean instead of memorizing it :(

Take care :)

---

### Post by jramshu on 2011-09-18
Look here for the -o option. Pretty much every program has a 'man' page. Should help you in the future with the thousands of options.
```
man gcc
```

I just compiled one just using "gcc nameoffile.c" 
The -o let's you rename it, otherwise it is saved as "a.out"

Edit: gcc and g++ pretty much use the same options.

---

