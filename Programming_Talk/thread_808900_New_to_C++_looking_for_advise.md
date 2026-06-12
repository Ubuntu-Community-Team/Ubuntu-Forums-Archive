---
title: "New to C++ looking for advise"
date: 2008-05-26
forum: Programming Talk
---

### Post by rick3878894 on 2008-05-26
My friend gave me a book on C++ and I need a Compiler. I have no experince with c++, so I am looking for a very simple compiler. One that wont overwhem my newbi mind. Looking for one that is GUi, wouldn't ask a lot of advanced questions to set up and run, and maybe one with newbi hints.

Recomendations?

---

### Post by dwhitney67 on 2008-05-27
You'll will got lots of replies on this topic.  But if you want to get started now, then stick to the basics.

First, install the GCC compiler:
```
$ sudo apt-get install build-essential
```
Then pick a program from your book, launch the gedit(or), enter the program, then save as a file with a .cpp extension.
```
$ gedit hello.cpp
```
[PHP]#include <iostream>

int main()
{
  std::cout << "Hello World" << std::endl;
  return 0;
}[/PHP]

To compile it:
```
$ g++ hello.cpp -o hello
```

To run it:
```
$ ./hello
```

---

### Post by LaRoza on 2008-05-27
> **rick3878894 said:**
> My friend gave me a book on C++ and I need a Compiler. I have no experince with c++, so I am looking for a very simple compiler. One that wont overwhem my newbi mind. Looking for one that is GUi, wouldn't ask a lot of advanced questions to set up and run, and maybe one with newbi hints.

Recomendations?

See the sticky. There is a link to how to compile and run C++ from start to finish, and there is a thread on editors/IDE's.

Here's a newb hint: Programming Tools and References, Learning Computer Programming,  Programming Talk FAQ's

---

### Post by rick3878894 on 2008-05-27
Thanks I found that one and I was unsure of how to use it.

This should hold me over till I find one that is more to a my liking. I like GUI. I am not exactly an IT geek anymore. I just hate windows and mac. All that left was Linux. Thats why I wana get into programing. So that I can make programs that are more to my liking and works the way I think it should. Long road I know, but I think that's worth it. I'll let you know if I give up.

---

### Post by LaRoza on 2008-05-27
> **rick3878894 said:**
> Thanks I found that one and I was unsure of how to use it.

This should hold me over till I find one that is more to a my liking. I like GUI. I am not exactly an IT geek anymore. I just hate windows and mac. All that left was Linux. Thats why I wana get into programing. So that I can make programs that are more to my liking and works the way I think it should. Long road I know, but I think that's worth it. I'll let you know if I give up.

I doubt you'll find a compiler more to your liking than gcc (of which g++ is a part).

All that is left? No, you still have Solaris, BSD and a bunch of others.

You might want to check out some other languages also (check out my site)

---

### Post by rick3878894 on 2008-05-27
> **LaRoza said:**
> I doubt you'll find a compiler more to your liking than gcc (of which g++ is a part).

All that is left? No, you still have Solaris, BSD and a bunch of others.

You might want to check out some other languages also (check out my site)


I use to be the AD to a network at one of my highschools (age 15). It ran a little over 800 Windows boxs and around 30 Mac's. Then we had a bunch of servers some for the school and some for the whole district. They were a mix of Windows (server 2003 I think) and Linux (redhat) servers. Then I went to a trade school and when I finished there I wrote half of the corse for their A+ class and worked as intern at some small ISP. There I learned a great deal about linux.

When compleated the school in 2005 I was just bearly 18 and had no family to help me out so I went back to the street and couldn't get a good job that suited my skills. So I got a crap job or two the then joined the Army Guard where I got and intro Solaris and some prorams you've never heard of, that I am not really sappose to talk about.

What I meant when I said "it was the only one that is left" is that I only really know what I am doing amoungst the four and I like this one the most. 

Linux is very customizable and some distro are very user friendly.

---

### Post by dwhitney67 on 2008-05-27
Have you written your first C++ program yet?  I thought that the instructions I gave you would put you on a solid path to creating/running the venerable "Hello World" application.

---

### Post by rick3878894 on 2008-05-27
> **dwhitney67 said:**
> Have you written your first C++ program yet?  I thought that the instructions I gave you would put you on a solid path to creating/running the venerable "Hello World" application.

Nope. Not yet but I just found my book so I will be getting started.

---

### Post by irrdev on 2008-05-27
Compiling programs from the terminal is a headache. Using an IDE is an absolute must. I would suggest that you download CodeBlocks; it can be found at [http://codeblocks.org/](http://codeblocks.org/). There is a Ubuntu Deb Package in the download section, so installation is a breeze. ;)

---

### Post by dwhitney67 on 2008-05-27
> **irrdev said:**
> Compiling programs from the terminal is a headache. Using an IDE is an absolute must. I would suggest that you download CodeBlocks; it can be found at [http://codeblocks.org/](http://codeblocks.org/). There is a Ubuntu Deb Package in the download section, so installation is a breeze. ;)
For you maybe, but for me and countless others an IDE is NOT required.  With reliance on the command line, one can compile/link simple programs (i.e. those found found in a book).  For more complex programs, then a Makefile can be used.

IDEs are favored by many developers, but as I stated, they are not required, nor essential to the success in developing a project.

---

### Post by Joeb454 on 2008-05-27
I use Vim to write my C++ apps.

And in the example above, would you not need to put ```
using namespace std;
``` in there?

---

### Post by dwhitney67 on 2008-05-27
Good choice... I also use vim (vi)... and have for over 18 years.

In the example above, one has 3 choices:

1)  Add the "using namespace std;" statement.
2)  Add separately the "using std::cout;" and "using std::endl;" statements.
3)  Specify the namespace "std" with each usage of a standard library object (e.g. std::cout, std::endl).

I chose option 3 because of the simplicity of the code.  For more complex code, I would choose option 1.  It is good programming practice to avoid employing option 1 in a header file; always use option 3.

---

### Post by pmasiar on 2008-05-27
OP: Is C++ your first language?

Everyone here will shout at me to let you learn whatever you want, but trust me, C++ is NOT a language for beginner. Python is much better for a beginner, you have better chance to wrestle C++ with come previous programming experience - it is  rather unforgiving for newbies.

See sticky FAQ and wiki in my sig for links.

---

### Post by dempl_dempl on 2008-05-27
> **pmasiar said:**
> OP: Is C++ your first language?

Everyone here will shout at me to let you learn whatever you want, but trust me, C++ is NOT a language for beginner. Python is much better for a beginner, you have better chance to wrestle C++ with come previous programming experience - it is  rather unforgiving for newbies.

See sticky FAQ and wiki in my sig for links.

pmasiar,

You have a text template for this don't you? You just fill in the appropriate nickname, and post it, am I right ?   :-P

Cheers!

---

### Post by Joeb454 on 2008-05-27
I have to agree with pmasiar though. I don't think C++ is the best choice for a beginning language, I've had quite a strange progamming introduction ;) Visual Basic - C - C++, dabbled in Python a little as well, though never took that much interest in it.

---

### Post by LaRoza on 2008-05-27
> **rick3878894 said:**
> 
When compleated the school in 2005 I was just bearly 18 and had no family to help me out so I went back to the street and couldn't get a good job that suited my skills. So I got a crap job or two the then joined the Army Guard where I got and intro Solaris and some prorams you've never heard of, that I am not really sappose to talk about.

What I meant when I said "it was the only one that is left" is that I only really know what I am doing amoungst the four and I like this one the most. 

Linux is very customizable and some distro are very user friendly.

You sound most interesting :-) Linux is a great OS, I hope you have fun with it.

---

### Post by LaRoza on 2008-05-27
> **irrdev said:**
> Compiling programs from the terminal is a headache. Using an IDE is an absolute must. I would suggest that you download CodeBlocks; it can be found at [http://codeblocks.org/](http://codeblocks.org/). There is a Ubuntu Deb Package in the download section, so installation is a breeze. ;)

Interestingly, all the hard problems with compiling involve IDE's. "How do I static link from <IDE>?", "How do I make <IDE> use <library>?", "How do I <dothis> that is <trivial in the command line> in <IDE>?".

---

### Post by pmasiar on 2008-05-27
> **dempl_dempl said:**
> You have a text template for this don't you?


No I don't. maybe I should :-) 

It is sad that 30% of my posts is the same FAQ advice, which is supported by many forum regulars, and then I am attacked for... for what? 

What is **your** problem about me giving this advice? Do you disagree? 
If you do, can you argue about the facts, not your prejudices: why it is not valid?
If you agree, are you just mad I beat you to it?

BTW, re-reading whole thread - I missed Rick's second post (#6). If he likes his admin's work, Python is even better choice that for any random newbie. So what is exactly your problem, dempl_dempl?

---

### Post by dempl_dempl on 2008-05-27
> **pmasiar said:**
> No I don't. maybe I should :-) 

It is sad that 30% of my posts is the same FAQ advice, which is supported by many forum regulars, and then I am attacked for... for what? 

What is **your** problem about me giving this advice? Do you disagree? 
If you do, can you argue about the facts, not your prejudices: why it is not valid?
If you agree, are you just mad I beat you to it?

BTW, re-reading whole thread - I missed Rick's second post (#6). If he likes his admin's work, Python is even better choice that for any random newbie. So what is exactly your problem, dempl_dempl?

Naah ...  My post was elegant mixture of joke and observation. :)

Not everything you see is made as an argument for debate. I never meant to say something against you, or anything you might think about this or that. I've just noticed that you tend to post *"Use python, if you're beginner"* a lot of times . 


While at it, I believe that  any language could be good for beginner, as long as it's not something like  asm ( or BrainFuck ) . 
People can understand  C++ very easily if someone explains them things nicely. 

I've started my programming with C++ on my own when I was 14, and I don't remember having some big issues with learning it  , and I'm not some kind of a wunderkind .


> 
 So what is exactly your problem, dempl_dempl?


I don't have problems, at least not big ones. I live creative life full of joy :) , although I like practising  killing time from time to time :D   .

On the other hand , Your question reveals to me some kind of frustration over something [ besides IT, I also study psychology ]
Would you like to talk about it?
If you don't,  I believe you can use Emacs plug-in for that.

....

But I don't want to go into flaming. I'm sorry if I sounded like I was having something against you. 

Please, take it all as a joke :D  , because , sincerely,  it was only a joke.

Cheers!

---

