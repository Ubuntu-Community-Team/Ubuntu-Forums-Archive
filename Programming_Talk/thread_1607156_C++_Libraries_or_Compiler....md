---
title: "C++ Libraries or Compiler..."
date: 2010-10-27
forum: Programming Talk
---

### Post by Devio on 2010-10-27
Hi there, for my final year project at university I'm working on some genetic programming code in C++ and also I'm freshly experimenting with Ubuntu let alone Linux in general(purely for the experience).

I have experience with Java so I kind of recognise what I'm looking at.  Without previously downloading anything I tried to use the command g++ ****.cpp in terminal, however, it threw up lots of errors.  The errors I'm concerned with mainly are *condefs.h No such file or directory* and similar errors for *mem.h* and *conio.h.  *The rest of the errors I have a feeling will go when I sort this problem out.
I was just wondering with these errors whether there was a specific library set or compiler I could download to sort these first few problems out.

Sorry this looks like I'm jumping in at the deep end to some extent, and also sorry if this is in the wrong section, it was a toss up between this and the Absolute Beginners section.

Thanks for reading!

---

### Post by Zugzwang on 2010-10-27
Do a search in the forum on "conio.h" - this is the keyword that should lead you to a couple of posts here in which your problem is discussed.

---

### Post by Vox754 on 2010-10-27
> **Devio said:**
> Hi there, for my final year project at university I'm working on some genetic programming code in C++ and also I'm freshly experimenting with Ubuntu let alone Linux in general(purely for the experience).

I have experience with Java so I kind of recognise what I'm looking at.  Without previously downloading anything I tried to use the command g++ ****.cpp in terminal, however, it threw up lots of errors.  The errors I'm concerned with mainly are *condefs.h No such file or directory* and similar errors for *mem.h* and *conio.h.  *The rest of the errors I have a feeling will go when I sort this problem out.
I was just wondering with these errors whether there was a specific library set or compiler I could download to sort these first few problems out.

Short answer: if you want to complete your program on time, forget about messing with Linux and go with what you know in Windows.

Long answer: essentially, the "g++" compiler is not magic. You need to know what you are doing. First thing to do, install "build-essential" as it will install the most common tools and libraries. Then, most probably you are using Windows-specific headers and libraries that are not compatible with Linux. You will need to rewrite your code to use only standard C++ code, or use libraries that are available everywhere, such as GNU or boost. Then there is the genetic programming. Are you using an external library? Is it proprietary? Is it binary-only? Is it Windows-only? Is it provided by the professor? Etc. There is a ton of things to consider.

Read the FAQs, stickies, and other threads with "conio.h", to learn to compile a simple C++ program in Linux. There is much to read, and no person will want to spoon-feed you answers if you cannot prove that you know at least the basics (post the code!). Actually, there are times when people in here wake up with the best attitude ever, and actually spoon-feed newbies. It's not everyday, but it happens!

> 
Sorry this looks like I'm jumping in at the deep end to some extent, and also sorry if this is in the wrong section, it was a toss up between this and the Absolute Beginners section.

Thanks for reading!
It does look like you are jumping from a plane without a chute.

I am always appalled by the decision of some people to ask programming questions in the Absolute Beginners section. Programming is nowhere an absolute beginner's topic, let alone working on your University final year's project, genetic programming in C++!

---

### Post by Devio on 2010-10-27
> **Vox754 said:**
> Short answer: if you want to complete your program on time, forget about messing with Linux and go with what you know in Windows.

Long answer: essentially, the "g++" compiler is not magic. You need to know what you are doing. First thing to do, install "build-essential" as it will install the most common tools and libraries. Then, most probably you are using Windows-specific headers and libraries that are not compatible with Linux. You will need to rewrite your code to use only standard C++ code, or use libraries that are available everywhere, such as GNU or boost. Then there is the genetic programming. Are you using an external library? Is it proprietary? Is it binary-only? Is it Windows-only? Is it provided by the professor? Etc. There is a ton of things to consider.

Read the FAQs, stickies, and other threads with "conio.h", to learn to compile a simple C++ program in Linux. There is much to read, and no person will want to spoon-feed you answers if you cannot prove that you know at least the basics (post the code!). Actually, there are times when people in here wake up with the best attitude ever, and actually spoon-feed newbies. It's not everyday, but it happens!


It does look like you are jumping from a plane without a chute.

I am always appalled by the decision of some people to ask programming questions in the Absolute Beginners section. Programming is nowhere an absolute beginner's topic, let alone working on your University final year's project, genetic programming in C++!

I wasn't asking to be spoon fed, just pointed in the right direction, I'm perfectly capable of researching a slight bit but got lost with the mess.  What you've given me so far is more than helpful so thanks for that.

And yes the code I have is written by my supervisor and I'm not sure I have the right to publish it so unless I'm desperate I wont and then it'll only be in PM.

Thanks again to both replies!  I'll have a crack at this over the next couple of days and see if I can get used to it, I do have a feeling I'll revert to Windows eventually though and learn Linux gradually.

---

### Post by Tony Flury on 2010-10-28
Specifically - the header files you mention : conio.h, condefs.h and mem.h are windows specific and wont exist on a Linux install.

If you have to use the code provided by your supervisor, and you need to extend it - but not port it - then Windows is your only route.

You might well find that porting to linux could be easy - or could be very difficult - it all depends on how Window specific it is : 
[LIST]
[*]If it is a simple text based terminal program then porting to stdio type calls should be relatively easy.
[*]If the programm uses more complex text base stuff (pseuodo graphical displays, updates without scrolling etc), then you would probably need to port that to ncurses which could be medium difficulty.
[*]If the programm has a full GUI (mouse, Icons, points, Menus etc) then porting it will be hard and potentially very time consuming.
[/LIST]
Within the scope of a final year project where presumably you actually have to add some useful functionality to the application (and not just port it to Linux), then i would say stick to extending the Windows version (uggh that is horrible to have to say that).

---

