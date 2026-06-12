---
title: "GTK, QT or something else?"
date: 2007-07-09
forum: Programming Talk
---

### Post by akudewan on 2007-07-09
Hi,

I have to make a SuDoku program for my college project. Now, I'm familiar with C and C++, but I don't know how to make any GUI. My teacher recommended VB for the project, but I'm not happy with VB since it doesn't work on Linux. At the same time, the program must compile on windows as well, since I have to present it on a windows computer.

I don't want to learn a new language like Java or Python or something, since time is limited. I was thinking I could use a toolkit widget like QT or GTK to make the GUI in C++.

So here's my list of questions:
1) GTK Vs. QT. Which is easier? and more "portable" ?
2) Will I have to make any changes in the code when compiling on windows or linux ?
3) Is it really worth learning a new language for this project?
4) Any web resources or books to learn GTK or QT will be a great help.

Thanks for for time.

---

### Post by LaRoza on 2007-07-09
> **akudewan said:**
> Hi,

3) Is it really worth learning a new language for this project?
4) Any web resources or books to learn GTK or QT will be a great help.

Thanks for for time.

I am not an expert on GUI programming, but using Python with Tkinter or another graphics library might be better.

Since you already know C++, Python will be a cinch, and since you don't know any particular graphics library, Tkinter will be easy to learn.

If you want to use C++, try SDL at [http://www.libsdl.org/](http://www.libsdl.org/) it is easier, (I hear).

---

### Post by destructchaos on 2007-07-09
i don't know about gtk, but i had mad problems just getting one qt program to compile without errors on various flavors of linux, let alone on windoze.

never learned python, but picking up java was a really easy switch after i learned c++.

---

### Post by deepclutch on 2007-07-09
qt maybe.but license wise gtk+ seems better(if that matters) and u know gtk+ is on C(c++ wrappers available)

---

### Post by akudewan on 2007-07-09
> **LaRoza said:**
> I am not an expert on GUI programming, but using Python with Tkinter or another graphics library might be better.

Since you already know C++, Python will be a cinch, and since you don't know any particular graphics library, Tkinter will be easy to learn.

If you want to use C++, try SDL at [http://www.libsdl.org/](http://www.libsdl.org/) it is easier, (I hear).

I understand that SDL is a multimedia development API. What I need is just the ability to draw windows, buttons etc. I'm looking into Pyton and Tkinter. They seem to have a lot of good documentation.

And thanks to everyone for replying :)

---

### Post by Smygis on 2007-07-09
Perhaps wxWidgets. Its an easy to use API.
Qt vs GTK+... Using Qt tour app will look odd in Gnome/Xfce and you have to GPL your code. Thats about all i know about it. 
GTK+ might be a better chose between those, But if you like KDE better then Gnome/Xfce you might want to use Qt.

wxWidgets is my choise tho.

Tkinter is soooo ugly. If you try out Python, Use wxWidgets (wxPython). And this is what i recommend. Python. Perhas i shuld not cuz the Java gurus gets angry :D

---

### Post by AlexThomson_NZ on 2007-07-09
> **Smygis said:**
> And this is what i recommend. Python. Perhas i shuld not cuz the Java gurus gets angry :D

Hehe, as a "Java guru", I have to say GUI programming with Java is a snap (I don't think it's harder than Python, especially if you haven't used Python before, but have used C or especially C++), you have some nice, mature IDE's to help you, infinite tutorials and resources on the internet, and will get brownie points from your instructor! (maybe things have changed, my all my old instructors where the bearded Java types) :)

---

### Post by rekahsoft on 2007-07-09
I would use gtk and C++ for the project. Then all you would have to learn is gtkmm (the C++ gtk wrapper). It is pretty simple to get a hold of..go to the documentation on their site or install devhelp and the gtkmm doc package.

---

### Post by LuisAugusto on 2007-07-09
QT 4, and that's all, the other option aren't at the level.

See you.

---

### Post by kknd on 2007-07-09
Both QT and GTK are portable and mature, but I recommend wxWidgets, because it include native wrappers for the GUI (uses GTK or X in *nix, and Microsoft things on Windows, etc) plus portable file system, net, etc libraries.

QT is the most advanced GUI that I know, but you cannot use it in a commercial application without buying a expensive license. Maybe that not a disvantage after all =).

---

### Post by runningwithscissors on 2007-07-10
If you already know VB, use VB. It's made for these kind of quick-and-dirty projects.

GTK is not the easiest of toolkits to wrap your head around, and you'll have problems setting Qt up for development work on Windows.

---

### Post by akudewan on 2007-07-10
I found a good book on Qt: [http://www.phptr.com/bookstore/product.asp?isbn=0131240722&rl=1](http://www.phptr.com/bookstore/product.asp?isbn=0131240722&rl=1) (there's also a QT4 book available). Its a great book, and gives simple explainations.

I think I'll try Qt for the time being. If I get into trouble with it in windows, I'll try something else. I'll keep my options open. I don't know VB, I'd have to learn that as well.

Thanks for all the replies. More suggestions are always welcome :)

---

### Post by pete83 on 2007-07-13
Hey, I am under the impression that you might be able to use VB in Linux, using the monodevelop IDE. Definitely check it out!

---

### Post by hod139 on 2007-07-13
For cross platform C++, your 3 main choices are 
1) wxwidgets
2) gtkmm
3) qt

As for which is better, that is hard to say.  People who use wx will say wx, people who use gtk will say gtkmm, etc.  All 3 are under very active development and will do the job you want.  I say look at some of the tutorials and pick the one you like best.

---

### Post by deepclutch on 2007-07-15
If Linus says qt,will ya all use it?I mean when it comes to Gnome vs Kde.Gnome sucks right?also gtk+ 2 :x
^ that is what i felt,most of the time.
gtk+ 2 should grow to the level as with qt4.there is a huge gap created when Qt4 vs other gui programming options. :(

---

### Post by wth_china on 2007-07-15
java is better.

---

### Post by akudewan on 2007-07-15
> **deepclutch said:**
> If Linus says qt,will ya all use it?I mean when it comes to Gnome vs Kde.Gnome sucks right?also gtk+ 2 :x
^ that is what i felt,most of the time.
gtk+ 2 should grow to the level as with qt4.there is a huge gap created when Qt4 vs other gui programming options. :(

Only reason why I'm using Qt for now is because I found a good book on it. I really can't judge which is better since I don't know anything ;)

As for Java, I'll learn that in  my second term in college, for now I want to stick to C++

---

