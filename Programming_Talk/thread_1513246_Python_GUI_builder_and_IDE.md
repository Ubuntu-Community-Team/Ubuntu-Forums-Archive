---
title: "Python GUI builder and IDE"
date: 2010-06-19
forum: Programming Talk
---

### Post by Garyu on 2010-06-19
I have finally decided to learn Python programming for real. I have already written a simple script to read from serial ports and save data, just using gedit and a terminal. But now I want to take the next step and put it in a GUI which will work on both linux and windows. And I will add database support, which seems to force me into using Python3.1 rather than the default 2.x that comes with Ubuntu installation. 

After looking around quite a lot, I have decided to purchase the Wing IDE professional. The general consensus from reviews and forums all over the place seems to be that those who try Wing stay with it. And I want a solid IDE that I can stay happy with for a few years forward.

Problem is GUI. I know nothing of wxWidgets or GTK+. The Wing team seems to recommend Boa Constructor as a GUI builder, but when I google that I just get loads of old articles from a couple of years back about how buggy and unstable BC is. So then there is Glade, which I tried a couple of years ago but I thought it wasn't friendly at all. 

Is anyone currently using Boa Constructor? Is it now stable?

Is anyone currently using Glade? Would you recommend it for cross platform development by a total noob like me? Like I said, last time I tried to look at it I couldn't make it work.

What I would really want is something like Visual Studio, which when I used it last time (about 12 years ago) was really easy, just drag and drop GUI elements and attach some code to them. That is what I want. Simple, easy, where I don't have to learn every possible angle of GUI programming to attach my small snippets of code to on-button-click-events.

Other recommendations?





(I have searched this forum, but the search came up blank. I have also read through the stickies, but none of them answered my questions. Neither have a few hours of googling. Just saying before anyone jumps in with a "please use the search function". Most of the information I have found on this topic is outdated and/or lacking)

---

### Post by juancarlospaco on 2010-06-19
[DreamPie]("http://dreampie.sourceforge.net/")

---

### Post by Unterseeboot_234 on 2010-06-19
I will just give you my thoughts. I come from a java background and thus was using NetBeans a lot. I'm picking up on perl, ANSI C and waiting for JavaFX 2.0. Anyhoo...

NetBeans has the plug-in for python and for C/C++. I wouldn't do C code any other way (C is all about linking to make something work). The python editor in NetBeans is fabulous. You would install java also to get NetBeans operational. On Ubuntu, that means using the repositories java install so you can run java programs from desktop and in your browser(s). Then, I install the java-netbeans downloaded bundle, in my home directory, put my code in folder at ~/home/user-myself/NetBeansProjects. I find things work out faster that way. If you use the Ubuntu setup, you will quickly need to learn the chmod 777 folder / file permission stuff. I avoid that when hacking code.

So, you can have a fab python editor for free. Now, about the GUI..., if in truth I need a front-end I use Java. python is just too fuzzy about widgets. GLADE works with C/C++, as does GTK+, but none of them is integrated like java Swing, IMHO. Glade Interface Designer is a hack that writes <XML> that describes an interface. Your python / C / or whatever will have to link a compatible lib with xml to your code. Me? I prefer my Java button calling my C code.

In other words, I never found DnD GUI for python. I can sorta do it java-to-C, and I abandoned several hobby projects with python because I didn't like PIL, wxWidgets or any of the other solutions because they have complex wrappers like: wxButton( 'red' ); It becomes incumbent upon you to get the API for wxWidgets and determine if: Red, 'red', "red", RED, red-simple, color_red, or if that wrapper wants two or more args.

Most things Linux, I think you will find, is GTK+ making calls to python objects.

---

### Post by Garyu on 2010-06-19
> **Unterseeboot_234 said:**
> I didn't like PIL, wxWidgets or any of the other solutions because they have complex wrappers like: wxButton( 'red' ); It becomes incumbent upon you to get the API for wxWidgets and determine if: Red, 'red', "red", RED, red-simple, color_red, or if that wrapper wants two or more args.

According to everyone I've found who has said anything about it, Wing IDE has some of the best code completion available for Python. Which means, the IDE should keep track of args etc. So as far as I understand, that part wouldn't be complicated at all. Everything else you described, sounded very complicated to me. I've tried Java, I didn't like it, so not going back there. Same thing with C/C++. What I have seen from Python so far is only things I like, but the GUI thing seems a bit daunting to me. 

I sent a mail to the team developing Wing IDE, and got the recommendation to go for PyQt and take the time to learn writing code manually. Their opinion is that there are no good GUI builders, so writing code manually is time saving in the long run, or that was what I understood.

So I'll go for Wing and order a book on PyQt design, see how difficult it is to get into. It's too bad (for Python and for linux) that the threshold of getting into GUI design with Python seems to be high, because that only means fewer people will get into working on applications. I know it has kept me back from Python for quite a while now. It's also too bad that there are no epub or pdf books on the topic for sale, because now I have to wait until my shipment from Amazon arrives...

---

