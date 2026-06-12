---
title: "Another GTK vs QT Debate (Which should I learn?)"
date: 2008-07-17
forum: Recurring Discussions
---

### Post by chris062689 on 2008-07-17
I want to begin programming in one of these toolkits for the sake of UNIX Development.  I just don't know which one!  I'm going to be using Python.

People are saying how ugly GTK is, and how hackish it is.
While people say QT is nice and clean...

GNOME / GTK is the default in Ubuntu,
while KDE / QT isn't.

Can someone give me some (valid) claims as to these rumors, and perhaps code examples of both QT and GTK integration into Python?

---

### Post by LaRoza on 2008-07-17
Use whatever you want. They are both equal in use. 

If you use GNOME/Xfce, use GTK+ and if you use KDE, use QT.

If you use neither (like me) learn whatever one you want. 

You could also just use wxWidgets, which is very good also.

---

### Post by chris062689 on 2008-07-17
Well, that's the problem, I don't know which one I should use!
I can't make up my mind!  :lolflag:

I'd rather not use wxwidgets though, I rather would go all QT or all GTK.
I really don't have a preference in a Desktop Environment (though KDE4.1RC1 does look tempting!)

QT also has KDevelop and a easy GUI Creator. (Whats the package name?)
GTK has Glade.  :(

I want to begin developing apps for KDE / GNOME (mostly geared towards Ubuntu)

---

### Post by ghostdog74 on 2008-07-17
dude, sometimes the best choice is not to have any choices at all. Just get started with one and move on. If you get bored with it, try playing with the other one. Nobody can decide for you except yourself.

---

### Post by samjh on 2008-07-17
> **chris062689 said:**
> Well, that's the problem, I don't know which one I should use!
I can't make up my mind!  :lolflag:

I'd rather not use wxwidgets though, I rather would go all QT or all GTK.
I really don't have a preference in a Desktop Environment (though KDE4.1RC1 does look tempting!)

QT also has KDevelop and a easy GUI Creator. (Whats the package name?)
GTK has Glade.  :(

I want to begin developing apps for KDE / GNOME (mostly geared towards Ubuntu)

First of all, Qt and GTK are not at the same level.  GTK (actually GTK+) is a GUI widget library.  Qt is a much larger library incorporating networking, databases, concurrent programming, and others, including a GUI library.

Secondly, if you can't make up your mind, try both.  Spend about a week on one, and a week on the other.  Look around the web for tutorials (there are plenty) to get a start on them.  Which one feels most comfortable for you?

Thirdly, why restrict yourself to Ubuntu-centric development?  At early stages of learning, you should try to be a generalist.  You can specialise later.

Having said that, Kubuntu uses Qt heavily (or in your case, PyQt), naturally because it is a KDE distro.  Ubuntu uses Gnome and therefore PyGTK would be the natural choice, same with Xubuntu.

---

### Post by chris062689 on 2008-07-17
Well, I know at the beginning I shouldn't be so close-minded, but I am also learning python in the process...
Plus QT programs can be ported to Windows now, so that's cool! :)
(I assume OSX also.)

I think I'm going to go with QT for now..
Thanks a lot guys!

---

### Post by samjh on 2008-07-17
I'm glad you've made up your mind at last. :)

Here are some resources for you...

Official PyQt4 page: [http://www.riverbankcomputing.co.uk/software/pyqt/download](http://www.riverbankcomputing.co.uk/software/pyqt/download)
PyQt4 tutorial: [http://zetcode.com/tutorials/pyqt4/](http://zetcode.com/tutorials/pyqt4/)
But learn Python first: [http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

---

### Post by chris062689 on 2008-07-17
What are most of the KDE4 applications developed with?

I just started with the tutorial; and it's actually quite clean code compared to the little dab I did with PyGTK!

---

### Post by samjh on 2008-07-17
KDE4 uses Qt4.  All of KDE4 and its core applications are written in C++, I believe.

---

### Post by SledgeHammer_999 on 2008-07-17
> **chris062689 said:**
> Well, I know at the beginning I shouldn't be so close-minded, but I am also learning python in the process...
Plus QT programs can be ported to Windows now, so that's cool! :)
(I assume OSX also.)

I think I'm going to go with QT for now..
Thanks a lot guys!

As far as I know you can port GTK+ apps too... (take a look at deluge-torrent.org)

---

### Post by chris062689 on 2008-07-17
So if I wanted to help out KDE 4 development, I would have to learn C++...
All right!  I figured I would have to learn C++ someday, and plus it's widely used, so I better start learning!  :lolflag:
Got any ideas on any good tutorials? :D

---

### Post by qamelian on 2008-07-17
> **SledgeHammer_999 said:**
> As far as I know you can port GTK+ apps too... (take a look at deluge-torrent.org)
And Gaim and Gimp as well.

---

### Post by kknd on 2008-07-17
GTK works on MS-Windows too.

---

### Post by ub520 on 2008-07-17
wxwigets is on windows too

---

### Post by LaRoza on 2008-07-17
> **chris062689 said:**
> 
Plus QT programs can be ported to Windows now, so that's cool! :)

GTK+ and QT can be used on other platforms, however, wxWidgets is the only one designed to be cross platform.

---

### Post by lukjad on 2008-07-17
Is this one of those vi/emacs type threads?

---

### Post by Felson on 2008-07-17
Na.... Looks more like KDE vs Gnome. :D

---

### Post by LaRoza on 2008-07-17
> **lukjad007 said:**
> Is this one of those vi/emacs type threads?

No. Vim is obviously better than Emacs, but in this case it is purely preference.

---

### Post by smartboyathome on 2008-07-17
> **chris062689 said:**
> Well, I know at the beginning I shouldn't be so close-minded, but I am also learning python in the process...
Plus QT programs can be ported to Windows now, so that's cool! :)
(I assume OSX also.)

I think I'm going to go with QT for now..
Thanks a lot guys!

GTK programs can be ported to Windows as well. Just check out Inkscape/GIMP. They both use GTK and are available for windows.

---

### Post by Diabolis on 2008-07-17
Which one is heavier in resources? Since KDE is heavier than GNOME I would guess that QT is heavier than GTK.

---

### Post by smartboyathome on 2008-07-17
> **Diabolis said:**
> Which one is heavier in resources? Since KDE is heavier than GNOME I would guess that QT is heavier than GTK.

It is all relative. Since Qt involves more than just a GUI toolkit like GTK (see above), it is expected to be heavier.

---

### Post by LaRoza on 2008-07-17
> **Diabolis said:**
> Which one is heavier in resources? Since KDE is heavier than GNOME I would guess that QT is heavier than GTK.

Think about that. It doesn't make any sense.

It has nothing to do with the toolkit, but how it is programmed, and KDE isn't heavier than GNOME.

Opera is faster than Firefox and Opera uses QT and Fx can use GTK.

Speed here doesn't matter at all. You are using Python, and you are going to be waiting for people not the computer.

Just choose one. No one can make the decision for you. Here, I'll make it easy. Use wxPython.

---

### Post by Redrazor39 on 2008-07-17
QT!

Idk anything about programming, but I love KDE and would love to see more devs on the UI.

---

### Post by StOoZ on 2008-07-17
I would go with wxWidgets :guitar:

---

### Post by chris062689 on 2008-07-17
I'm probably going to go with QT.
Now, as people were saying before, everything within KDE 4 (all of the programs) were made in C++?  Well, guess I'm just going to have to learn that then.  *sighs*  Well, at least C++ is used in a lot of businesses, so it will look good on a resume.

I've been looking around Google, and really can't find any that teach C++ and QT at the same time...

---

### Post by GeneralZod on 2008-07-18
> **chris062689 said:**
> I'm probably going to go with QT.
Now, as people were saying before, everything within KDE 4 (all of the programs) were made in C++?  Well, guess I'm just going to have to learn that then.  *sighs*  Well, at least C++ is used in a lot of businesses, so it will look good on a resume.

I've been looking around Google, and really can't find any that teach C++ and QT at the same time...

There's no reason why you can't write a KDE4 *program* in a language other than C++, although the number of these in KDE svn is very low - in fact, I think there is just one, added very recently.  I don't know how many third-party non-C++ apps there are, though.  In any case, learning C++ is probably still worthwhile, from a CV-point of view :)

---

### Post by chris062689 on 2008-07-18
Though most programs written with GTK toolkit are written in python right? (in Linux / Ubuntu?)
Python seems a lot easier to learn than C++.

---

### Post by Erunno on 2008-07-18
> **chris062689 said:**
> Though most programs written with GTK toolkit are written in python right? (in Linux / Ubuntu?)
Python seems a lot easier to learn than C++.

There are Python bindings for Qt4 [1]. Nobody forces you to write Qt4 in C++ same way nobody is forced to use pure C for developing with GTK+. And without wanting to step on anyone's toes but a lot of people will recommend you GTK+ here simply because they like GNOME better than KDE and not based on the technical merits of the toolkits. Plus, KDE applications usually use KDE-specific libraries (kdelibs, etc.) which are build on top of Qt.

Developing applications is a tad different from just using applications. A programming language is just a tool and some tools are better for a specific purpose than other (e.g. Java or Python for RAD). So knowing a language won't make you a capable developer, it's basically the first step to take out of many. The true art is to formulate a solution to a given problem with the tools at hand in an "elegant" way. I don't want to give you a lecture on developing but newcomer to programming usually seem to have a mistaken fixation on programming languages.

[1] [http://wiki.python.org/moin/PyQt]("http://wiki.python.org/moin/PyQt")

---

### Post by Felson on 2008-07-18
Agreed. Erunno is right. The most important things for a programmer are logic, problem solving and a good understanding of data structures and there uses. The language you can learn as you need it. While I like standard C best, I have written in C++, VB, COBAL, VAX/VMS, Java, pascal, Perl, PHP, Bash, Fash AS2 & 3, and even had to use JavaScript as a real language. If you talk to most of the professional programmers here they will likely have a similar, and equally useless list, of languages they have needed at any given time to solve the problem of the day. Logic is your best tool for any problem :)

---

### Post by chris062689 on 2008-07-18
So I should really just be a jack of all trades?
I know a bit of PHP, a pint of Python, a bit of HTML, and a quite a bit working with various DBs.  Should I just proceed onword with learning PHP / Python without focusing on one toolkit?

---

### Post by doorknob60 on 2008-07-18
QT because I like KDE better :lolflag:

---

### Post by Felson on 2008-07-18
@chris062689
No no. What we are saying, is pick a language and learn. The language you pick isn't as important as the logic and problem solving you learn while learning it. A good programmer "should" be able to pic up almost any language as s/he needs it. But you still need to start somewhere. Python, Ruby, C++ doesn't matter. As long as while you are learning it, you keep in mind to focus more on how an array works, what you use a linked list for, how the logic of the sorting function you wrote or a million other points of logic, rather then focusing on memorizing the exact syntax of a given language.

---

### Post by samjh on 2008-07-18
> **chris062689 said:**
> So I should really just be a jack of all trades?
I know a bit of PHP, a pint of Python, a bit of HTML, and a quite a bit working with various DBs.  Should I just proceed onword with learning PHP / Python without focusing on one toolkit?

Focus on learning a language first.  For Ubuntu, the developers encourage using Python, so if you are interested in Ubuntu-centric development, learning Python is a good idea.

[quote=chris062689]Though most programs written with GTK toolkit are written in python right? (in Linux / Ubuntu?)[/quote]No.  Most GTK+ programs are written in C (including the Gnome desktop and its many components).

C# (ie. Mono) and Python are the next most popular.

Similar for Qt.  C++ is the main language used for Qt development, followed by Python and Java.

Whatever you do, do NOT focus on a toolkit.  Focus first on a language.  Learn how to program using that language.  And then you'll be in a position to pick a toolkit.

GTK+ have bindings in numerous languages, including C, C++, C#, and Python.

Qt also have bindings in many languages, including C++, Java, and Python.

Your programming and design skills are infinitely more important than your choice of toolkit.

---

### Post by bruce89 on 2008-07-18
> **samjh said:**
> No.  Most GTK+ programs are written in C (including the Gnome desktop and its many components).

They are indeed written in C, but mostly using the GObject library which is a language-independent object system.

---

### Post by samjh on 2008-07-18
> **bruce89 said:**
> They are indeed written in C, but mostly using the GObject library which is a language-independent object system.

Let's not confuse Chris with irrelevancies.

GObject library is not a "language", therefore not relevant to his notion of one language being more popular than another.

---

