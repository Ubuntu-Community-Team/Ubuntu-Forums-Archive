---
title: "How Exactly do I Install C and C++?"
date: 2013-04-23
forum: Programming Talk
---

### Post by VicariousToast on 2013-04-23
I'm obviously not smart enough to figure this out on my own, so I've come to the forums for help with this xD

I need some help installing C and C++. I searched google, but I didn't come up with anything that made sense to me. I'm still new to Linux, so I don't know what most of the stuff that I found means.

So could someone post a newb-friendly guide for me? I'm using Xubuntu 12.04.

---

### Post by schragge on 2013-04-23
```
sudo apt-get install build-essential
``` should take care of it.

---

### Post by VicariousToast on 2013-04-23
I pasted the code into the terminal and ran it, but I can't find c or c++ with the Application Finder or Catfish. Where should the files be located?

---

### Post by steeldriver on 2013-04-23
What are you trying to do exactly?

C and C++ are languages (not applications) the build-essential package installs all the command line tools you should need to compile and run C/C++ code - but if you are expecting some kind of complete development environment like Microsoft's Visual Studio then you will need to install an IDE separately.

---

### Post by VicariousToast on 2013-04-23
Ah, I see now. I was under the assumption that Linux used some other method that I didn't know about, instead an IDE. There was no mention of IDEs in any of the guides I found(which were specifically for Linux), and I never thought to search for IDEs(I'm having one of those days where I just can't think straight.).

---

### Post by steeldriver on 2013-04-23
Well you don't *need* an IDE, in fact if you're just getting started there's lots to recommend just using a regular text editor and command line tools - it's often easier to get a feel for what's going on under the hood that way

---

### Post by kuifje09 on 2013-04-23
Then the next question is do you want just build a program or a windows/gui  program.

---

### Post by shawnhcorey on 2013-04-24
> **schragge said:**
> ```
sudo apt-get install build-essential
``` should take care of it.

Also:
```
sudo apt-get install manpages-dev
```
These are the manual pages for the development environemnt.

> **VicariousToast said:**
> I pasted the code into the terminal and ran it, but I can't find c or c++ with the Application Finder or Catfish. Where should the files be located?

Try:
```
man gcc
```

---

### Post by alan9800 on 2013-04-24
if you wish an IDE for C++, you might try [Code::Blocks]("https://apps.ubuntu.com/cat/applications/codeblocks/").

---

### Post by VicariousToast on 2013-04-24
> **steeldriver said:**
> Well you don't *need* an IDE, in fact if you're just getting started there's lots to recommend just using a regular text editor and command line tools - it's often easier to get a feel for what's going on under the hood that way

So how does that work? Is there any particular place you have to put the text file? And how is the command line used?

> **kuifje09 said:**
> Then the next question is do you want just build a program or a windows/gui  program.

I don't really know. I started learning C# on one of the other computers in my house, and I think it's fun. So right now I'm not looking to do anything in particular, I'm just trying to learn the basics. Later on when I get good at it I'm going to start designing games.

> **shawnhcorey said:**
> Also:
```
sudo apt-get install manpages-dev
```
These are the manual pages for the development environemnt.



Try:
```
man gcc
```

Thanks

> **alan9800 said:**
> if you wish an IDE for C++, you might try [Code::Blocks]("https://apps.ubuntu.com/cat/applications/codeblocks/").

I'll check it out, thanks.

---

### Post by trent.josephsen on 2013-04-24
3 easy commands: edit, compile, run.

```
gedit file.c
```
(You may replace gedit with your editor of choice.) Write your code in the editor, save it, then
```
gcc -std=c99 -Wall -Wextra -pedantic file.c
./a.out
```

Boom. It's a similar process for C++ (although I would suggest you pick one and stick with it for a while; C and C++ are quite different).

The -std=c99 -Wall -Wextra -pedantic bit is strictly speaking not necessary. Those flags just tell gcc what dialect of C to compile (C99, in this example) and turn on a bunch of warnings that will probably help you avoid some dumb mistakes when getting started. You can alias that whole bit to something shorter; just add the following line to ~/.bash_profile and use "cc file.c" instead:

```
alias cc="gcc -std=c99 -Wall -Wextra -pedantic"
```

Just a few tips. Have fun.

---

### Post by VicariousToast on 2013-04-27
Thank you for the help everyone.

---

### Post by kuifje09 on 2013-04-28
Maybe another tip.
If not very familiar with C and C++ it would be helpfull to use a developers gui with commandcompletion.

I used a few days ago the QT- developers suit.  That is a real nice tool to create smal and big progs.
Also some helpfull tutorial files are shiped with it.

This package is also almost a wysiwyg , at least the gui designer is build-in.

---

### Post by kuifje09 on 2013-04-28
Would it be better to also add -march="your processor/architecture" to make the fastest executable for you machine.
And when using the math routines add -lm at the END of the cc/gcc commandline

Note: this in reaktion to post #11 .

---

