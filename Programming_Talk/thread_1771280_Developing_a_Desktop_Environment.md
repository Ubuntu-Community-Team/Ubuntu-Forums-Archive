---
title: "Developing a Desktop Environment"
date: 2011-05-30
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-05-30
Hey there,

I have a question. Suppose i have some ideas on making a new Desktop Environment, and suppose that i am not that good at programming, in fact i'm a novice. That means i have ideas but no clue as to how to implement them. How can i go about making my project?

What various things do i need to consider when thinking of making a Desktop Environment? I assume i should think of its relation to the OS, to the WM and to the GUI toolkits which the program windows will come with. Am i on track?

How do i present my ideas? How to i "recruit" developers (assuming these ideas are inspiring?). How many developers will be require to produce it?

Are there any other considerations?

I realise this may be an odd question, but if i don't ask, i won't learn :)

Thanks.
Benjamin

---

### Post by LoneWolfJack on 2011-05-30
It is an odd question because everyone who is able to build his/her own desktop environment would at least know where to start looking for information.

It's certainly nothing for a programming novice.

As long as you don't put some serious effort and/or money into your project yourself, nobody will volunteer to do any work for it.

If you are serious about this, learn C/C++ and then join the GNOME or KDE mailing lists and try to contribute to those projects. In about five years, you could become a pretty good C/C++ programmer and get a good understanding of how desktop environments work and how you would go about building one from scratch.

---

### Post by jesuisbenjamin on 2011-05-31
Well thanks for answering.

---

### Post by Thewhistlingwind on 2011-05-31
> **LoneWolfJack said:**
> 
If you are serious about this, learn C/C++ and then join the GNOME or KDE mailing lists and try to contribute to those projects. In about five years, you could become a pretty good C/C++ programmer and get a good understanding of how desktop environments work and how you would go about building one from scratch.

You would also need to be borderline legendary to accomplish this in anything less then that time, don't try and cut corners dude.

---

### Post by jesuisbenjamin on 2011-05-31
> **Thewhistlingwind said:**
> You would also need to be borderline legendary to accomplish this in anything less then that time, don't try and cut corners dude.

Thanks for the warning. I'm not so much trying to cut corners though, i'm just asking information, because i admittedly am beginner which means i don't know where i'm going into. There is no "how to become a desktop environment developer's comprehensive guide" out there, if you know what i mean :)

Although my questions are bald (or silly, call it what you want) there's nothing wrong with having ideas and wanting to know how to achieve them. As i said: if one doesn't ask one doesn't learn.

---

### Post by tdrusk on 2011-05-31
Maybe start off smaller. Make a text-based environment in which the user can interact. For example:

```
1) Internet
2) Text Editor
3) Package Manager

What would you like to open?
```

Get that down, then try to expand from it. You may not get much support, but you will learn a lot.

---

### Post by DangerOnTheRanger on 2011-05-31
A desktop environment is nothing more than a collection of applications, a window manager, and possibly some development libraries.

I'd recommend starting out in the app category, like making a text editor, calculator, and maybe an IM client. Next, I'd study an existing window manager, and look for libraries that help me to make my own (if you know Python, the **python-plwm** package in the repos will greatly help you here).

Hey, you could just reuse a standalone window manager, like BlackBox, OpenBox, or maybe Enlightenment.

Hope this helps!

---

### Post by jesuisbenjamin on 2011-05-31
> **DangerOnTheRanger said:**
> A desktop environment is nothing more than a collection of applications, a window manager, and possibly some development libraries.

I'd recommend starting out in the app category, like making a text editor, calculator, and maybe an IM client. Next, I'd study an existing window manager, and look for libraries that help me to make my own (if you know Python, the **python-plwm** package in the repos will greatly help you here).

Hey, you could just reuse a standalone window manager, like BlackBox, OpenBox, or maybe Enlightenment.

Hope this helps!

Thanks Danger.

---

### Post by Simian Man on 2011-05-31
> **jesuisbenjamin said:**
> I have a question. Suppose i have some ideas on making a new Desktop Environment, and suppose that i am not that good at programming, in fact i'm a novice. That means i have ideas but no clue as to how to implement them. How can i go about making my project?
I hate to break it to you, but ideas are worth next to nothing when it comes to programming.  Everybody has ideas; it's getting them implemented that is the hard part.  Look at how many projects there are on places like Sourceforge that start with great ideas and never get finished (I have one or two myself).  And that is with people who are already experienced developers.

> **jesuisbenjamin said:**
> What various things do i need to consider when thinking of making a Desktop Environment? I assume i should think of its relation to the OS, to the WM and to the GUI toolkits which the program windows will come with. Am i on track?
As DangerOnTheRanger said, a desktop environment is just a collection of applications that are designed to work together.  Eg a panel, window manager, file manager and so on.  If I was starting a DE project, I'd pick one to start working on that other people can use inside of existing DEs.  That would allow you to get feedback without having everything up and running.

> **jesuisbenjamin said:**
> How do i present my ideas? How to i "recruit" developers (assuming these ideas are inspiring?). How many developers will be require to produce it?
As I said before all developers have their own ideas, so that isn't enough.  No matter how good yours is.  What you'd need is to learn how to program so you can bring your ideas to reality yourself.  Or pay people.  There are lots of good developers who can use some extra cash :).

---

### Post by jesuisbenjamin on 2011-05-31
> **Simian Man said:**
> I hate to break it to you, but ideas are worth next to nothing when it comes to programming.  Everybody has ideas; it's getting them implemented that is the hard part.  Look at how many projects there are on places like Sourceforge that start with great ideas and never get finished (I have one or two myself).  And that is with people who are already experienced developers.
Yeah, true. I realised that, but i don't want my ideas put down by others'(failed) attempts.

> **Simian Man said:**
>  If I was starting a DE project, I'd pick one to start working on that other people can use inside of existing DEs.  That would allow you to get feedback without having everything up and running.
Good, because that's exactly how i proceeded till now. I am working on a panel-like application and i worked on cairo-dock too.

> **Simian Man said:**
> What you'd need is to learn how to program so you can bring your ideas to reality yourself.  Or pay people.  There are lots of good developers who can use some extra cash :).
Haha, i could use some extra cash too :D

Thanks.

---

