---
title: "Future Gnome based on Qt?"
date: 2008-08-21
forum: Recurring Discussions
---

### Post by beow on 2008-08-21
I'm a Ubuntu Gnome users since years back. I've tried KDE several times but net been appauled by its user interface, Gnome just looks and handles so much better (IMHO).

At the same time I see that KDE/Qt has some advantages I don't find in Gnome/GTK: 

1) A roadmap towards the future that seems to execute
2) Backing of Qt from a large company (Nokia)

*Now, is this an unrealistic idea?: *

**Could a future Gnome be based on Qt?**

Think of it. A stable development and maintenance of the basic libraries, while keeping the desktop experience of Gnome with HIG an all..

A little bit as Ubuntu vs Debian. Debian is a stable back-end and Ubuntu provides the polished user interface. 

I think this could be a good thing for Linux.

---

### Post by loell on 2008-08-21
only if its named **Qnome** which from the sound of it, makes every real gtk+ users puke! :lolflag:

---

### Post by ibutho on 2008-08-21
Its unlikely to happen. A lot of GNOME apps are written in C or python using the GTK toolkit whereas qt is mainly used in C++ application. It would take a lot of time and effort to port GNOME apps to qt and I doubt that most developers would be bothered to do this unless there is a compelling reason for them to do so. Anyone suggesting that GNOME should move to qt would have to deal with the zealots who see KDE and QT as bad, evil or simply not good as GNOME or GTK.

---

### Post by Keyper7 on 2008-08-21
> **beow said:**
> I'm a Ubuntu Gnome users since years back. I've tried KDE several times but net been appauled by its user interface, Gnome just looks and handles so much better (IMHO).

At the same time I see that KDE/Qt has some advantages I don't find in Gnome/GTK: 

1) A roadmap towards the future that seems to execute
2) Backing of Qt from a large company (Nokia)

*Now, is this an unrealistic idea?: *

**Could a future Gnome be based on Qt?**

Think of it. A stable development and maintenance of the basic libraries, while keeping the desktop experience of Gnome with HIG an all..

A little bit as Ubuntu vs Debian. Debian is a stable back-end and Ubuntu provides the polished user interface. 

I think this could be a good thing for Linux.

Unless you're talking about a fork, I think this is a very bad idea.

Some people prefer GTK+ for perfectly valid reasons. Other people prefer Qt for perfectly valid reasons. Some people prefer Gnome for perfectly valid reasons. Other people prefer KDE for perfectly valid reasons.

So while *making* a Qt-based Gnome-like environment *might* (haven't thought too much about it) be an interesting idea, *moving* Gnome to Qt does little more than killing the user's right to choose.

---

### Post by mrsteveman1 on 2008-08-21
> **Keyper7 said:**
> Unless you're talking about a fork, I think this is a very bad idea.

Some people prefer GTK+ for perfectly valid reasons. Other people prefer Qt for perfectly valid reasons. Some people prefer Gnome for perfectly valid reasons. Other people prefer KDE for perfectly valid reasons.

So while *making* a Qt-based Gnome-like environment *might* (haven't thought too much about it) be an interesting idea, *moving* Gnome to Qt does little more than killing the user's right to choose.

There's a lot of dissatisfaction with the GTK+ toolkit among some developers, particularly when the conversation turns to making Gnome look nice as Shuttleworth and others have been talking about.

Also, having one toolkit for an OS solves one of the biggest problems, consistency. Right now you run a KDE app in Gnome and you get completely different buttons, different menus, different file dialog (in fact, one thats better than the GTK+ dialog). Not only does it look bad it has functional problems. The reverse is true as well even though KDE tries to theme gnome apps for you.

This isn't really about choice. To say that end users specifically choose a toolkit is incorrect, they choose a desktop environment that happens to be based around one of those toolkits. In any case, this stuff is all open source, no one can force anyone to do anything, or take away anyones choice. One choice is an infinite number of choices with FOSS.

---

### Post by loell on 2008-08-21
hmmm, I smell **reccuring**. :popcorn:

---

### Post by Keyper7 on 2008-08-21
> **mrsteveman1 said:**
> There's a lot of dissatisfaction with the GTK+ toolkit among **some** developers, particularly when the conversation turns to making Gnome look nice as Shuttleworth and others have been talking about.

There's been a lot of dissatisfaction with many things among many people, when the conversation turns to many things. And there's been a lot of satisfaction too. Find me a person who doesn't like the current state of GTK and I'll find you one who does. There's no such thing as an universal solution, so this is irrelevant.

> Also, having one toolkit for an OS solves one of the biggest problems, consistency. Right now you run a KDE app in Gnome and you get completely different buttons, different menus, different file dialog (in fact, one thats better than the GTK+ dialog). Not only does it look bad it has functional problems. The reverse is true as well even though KDE tries to theme gnome apps for you.

Developing functional ways to make Qt apps work in Gnome and vice-versa also solves this problem. There's the gtk-qt and the qgtkstyle theme engines to start. I'm not interested in discussing which would be a better solution, just mentioning that using only one toolkit is not the only solution.

> This isn't really about choice. To say that end users specifically choose a toolkit is incorrect, they choose a desktop environment that happens to be based around one of those toolkits.

But developers choose toolkits. You, yourself, used developers's opinions as an argument in the first sentence.

> In any case, this stuff is all open source, no one can force anyone to do anything, or take away anyones choice. One choice is an infinite number of choices with FOSS.

Easy to say. In practice, if Gnome was officially moved to Qt, the choices for GTK developers would be:

1) learn Qt and suck it

2) conform in developing apps for a minor, less used and less supported environment

---

### Post by The Keeper on 2008-08-21
Instead of forking Gnome to QT, why not just change KDE to look like Gnome? Much easier to accomplish without breaking anything, much less delicate minds of developers.

Also, how many GTK applications there are that have no equal QT alternative? OpenOffice comes to mind first, but KOffice 2.0 is progressing along and hopefully will be reach final next year. There is also a branch of Firefox being developed on QT, by the time of Firefox 3.2 it might be officially supported branch along with its GTK derivative.

While Ubuntu is free of QT/KDE applications, I hope Kubuntu will be free of GTK/Gnome applications someday too.

---

### Post by LaRoza on 2008-08-21
Recurring scent has been picked up, on the trail...

Honestly, in the free world any one can do what they want. If you don't like GTK+ based software, use something else.

---

### Post by mrsteveman1 on 2008-08-21
> **Keyper7 said:**
> There's been a lot of dissatisfaction with many things among many people, when the conversation turns to many things. And there's been a lot of satisfaction too. Find me a person who doesn't like the current state of GTK and I'll find you one who does. There's no such thing as an universal solution, so this is irrelevant.

It's very much relevant, there has been some talk recently about making Gnome, or more specifically Ubuntu, look better. And there has been quite a bit of talk among developers about the fact that GTK+ simply can't do certain things that would be needed, while QT apparently can. That's what makes it relevant.

You can be dismissive if you want, but that's what I've seen.

> **Keyper7 said:**
> 
But developers choose toolkits. You, yourself, used developers's opinions as an argument in the first sentence.

Yes, and End users don't. This thread is about developing Gnome around QT, something end users aren't even likely to notice unless the look changes. End users don't really care either way, and developers are the only ones who could actually make concrete arguments about why one toolkit is better than another for specific reasons. 

> **Keyper7 said:**
> 
Easy to say. In practice, if Gnome was officially moved to Qt, the choices for GTK developers would be:

1) learn Qt and suck it

2) conform in developing apps for a minor, less used and less supported environment 

As I said, FOSS is choice to an infinite degree. If Gnome (The main project) moves to QT, GTK+ users don't have to do anything, because the Gnome project can't force anyone to do anything. That's why you have the ability to fork if you want to. Yes, that is fragmentation, but we already have fragmentation right now and people don't seem to mind as long as things remain partially compatible. 

Now, if you want to go further and make the claim that GTK+ and QT serve different purposes or are fundamentally incompatible and necessarily separate, i would disagree. This is not a case where 2 different FOSS projects were started to fill different programming goals or needs. If you look at the history here, the original reasons Gnome exists in the first place are no longer relevant, because QT is now GPL licensed. If QT had been open source in the beginning when KDE was the main desktop, Gnome and GTK (as we know it) would not exist, they were both compromises to ensure that KDE would not become dependent on closed source code, something that is no longer a problem.

At this point, it's really fragmentation for no reason, there are very few, if any things that could not be resolved if the 2 toolkits were to merge in some fashion, and there are plenty of benefits.

Finding new and complex ways to make things compatible ignores the problem at the center of it all.

---

### Post by smartboyathome on 2008-08-21
I try to use GTK+ programs where possible, resorting to Qt only when necessary. Why? Because I use E17, and it is easier for me to change the theme and do all sorts of stuff with GTK which I can't do with Qt. In fact, I don't like many Qt programs, including Amarok, K3B, and KOffice. I rather use Emphasis, Brasero, and OpenOffice respectively, as they are just better imo. The fact that GNOME uses GTK and is dependant on it to an extent that they have made special widgets should be reason enough to see why they stick to GTK. If you want to rewrite GNOME in Qt, go ahead, just don't expect the project to support you.

---

### Post by gletob on 2008-08-21
> **beow said:**
> I'm a Ubuntu Gnome users since years back. I've tried KDE several times but net been appauled by its user interface, Gnome just looks and handles so much better (IMHO).

At the same time I see that KDE/Qt has some advantages I don't find in Gnome/GTK: 

1) A roadmap towards the future that seems to execute
2) Backing of Qt from a large company (Nokia)

*Now, is this an unrealistic idea?: *

**Could a future Gnome be based on Qt?**

Think of it. A stable development and maintenance of the basic libraries, while keeping the desktop experience of Gnome with HIG an all..

A little bit as Ubuntu vs Debian. Debian is a stable back-end and Ubuntu provides the polished user interface. 

I think this could be a good thing for Linux.
I'm sorry but you just made me puke a little GnomeQT No Thanks

---

