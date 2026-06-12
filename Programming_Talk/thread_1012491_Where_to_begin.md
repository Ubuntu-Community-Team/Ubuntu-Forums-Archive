---
title: "Where to begin?"
date: 2008-12-15
forum: Programming Talk
---

### Post by empthollow on 2008-12-15
I would like to create a program that has a similar front end to the debian installer, or the dpkg-reconfigure screens.  The problem is i have no idea how to make those appear.  I am familiar with bash scripting and could write a bash script to perform the functions i would like to accomplish with this program.  However, i prefer not to have to rely on external programs like zenity or dialog that create prompts for the user.  My objective is to create something that feels a bit more streamlined or glued together rather than a series of questions that leads the user to an end result.  If you are still reading, i want to thank you for taking the time to entertain my ramblings which i hope still make sense to a more experienced programmer. I appreciate any input on which programming language would allow me to create something like this with the smallest learning curve.

---

### Post by jimi_hendrix on 2008-12-15
if you mean installing debian...then i cant help you...

if you mean installing packages in debian...look into python or tcl/tk (a language we dont show nearly enough love around here...)

gui example in tcl/tk (puts hello world in a box)

```

#normally the shabang would go here but this differes from machine to #machine so...

label .foo -text "hello world"

pack .foo

```

label calls...well...label, .foo is the label name -text is an attribute of label "hello world" is what we set -text to

pack .foo

---

### Post by mssever on 2008-12-16
> **empthollow said:**
> I would like to create a program that has a similar front end to the debian installer, or the dpkg-reconfigure screens.  The problem is i have no idea how to make those appear.  I am familiar with bash scripting and could write a bash script to perform the functions i would like to accomplish with this program.  However, i prefer not to have to rely on external programs like zenity or dialog that create prompts for the user.  My objective is to create something that feels a bit more streamlined or glued together rather than a series of questions that leads the user to an end result.  If you are still reading, i want to thank you for taking the time to entertain my ramblings which i hope still make sense to a more experienced programmer. I appreciate any input on which programming language would allow me to create something like this with the smallest learning curve.
dialog is based on ncurses, which I believe is what you're after. There are ncurses bindings for many languages, but since I've never messed with ncurses, I can't comment on any particular binding.

---

### Post by mssever on 2008-12-16
> **jimi_hendrix said:**
> tcl/tk (a language we dont show nearly enough love around here...)
Tcl appears to have some cool ideas. Tk is a hideous GUI toolkit that--regardless of how nice it may be to program--shouldn't be used in any self-respecting program. I know there have been some recent improvements, but they're too little too late.

---

### Post by jimi_hendrix on 2008-12-16
> **mssever said:**
> Tcl appears to have some cool ideas. Tk is a hideous GUI toolkit that--regardless of how nice it may be to program--shouldn't be used in any self-respecting program. I know there have been some recent improvements, but they're too little too late.

the only GUI's i make are in SDL so i have little experience with one toolkit vs the other...all i know is that thats how tcl works and i find that a lot simpler then whatever python does...

---

### Post by iQuizzle on 2008-12-16
i would use **wx**. the learning curve is a little steeper than tk, but it will be pretty since it uses whatever gui your OS uses...and classes are neater to work with in terms of coding. so your gui will look natural in ubuntu for instance since it will draw from gnome.

---

### Post by jimi_hendrix on 2008-12-16
> **iQuizzle said:**
> i would use **wx**. the learning curve is a little steeper than tk, but it will be pretty since it uses whatever gui your OS uses

people in #tcl say tk does this too but i have not tested

---

### Post by empthollow on 2008-12-16
Thanks for all th input.  Wx sounds good because i like my interfaces to be uniform, and i don't mind a little more of a learning curve.  If i'm going to invest some time in learing a language i'd like it to be useful for quite some time.  I have a couple more questions though.  I found some info on wx widgets and wx python.  Which is being suggested.  Also, i'd like to know if there are ncurses binding for this language.  I am definitely interested in doing gui programming in X but i'd like to be able to make some stuff for the console too.  I suppose i could give that up, it's just nice to have versatility. Also, if wx uses the interface you are useing i.e. gnome/kde.  What would it do with fluxbox.  When i use fluxbox, i use mostly gtk applications, would wx follow suit or would i determine that when writing the program.

:popcorn:

---

### Post by nvteighen on 2008-12-16
Wait a bit: do you want a GUI or a text-based graphical interface? dpkg-reconfigure uses the latter, and that's ncurses.

ncurses is written for C, install libncurses5-dev and check the documentation. It's not that difficult, but its API is a bit messy for historical reasons. The Python binding (module curses... just do a regular "import curses") is even better than the original curses, as it is able to automate some nasty stuff (like terminal setting and resetting).

---

### Post by mssever on 2008-12-16
> **empthollow said:**
> Also, if wx uses the interface you are useing i.e. gnome/kde.  What would it do with fluxbox.  When i use fluxbox, i use mostly gtk applications, would wx follow suit or would i determine that when writing the program.
On Linux, wx always uses GTK, even if you're running KDE. If possible, I think you'll find GTK to be a lot easier than wx, though. GTK is already installed on most Linux systems (it's a dependency of such standard apps as GIMP), and you can install it on Windows, too. It's not quite as cross-platform as wx, but my experience with wx has been lots of frustration with its comparative lack of documentation.

---

### Post by empthollow on 2008-12-16
> **nvteighen said:**
> Wait a bit: do you want a GUI or a text-based graphical interface? dpkg-reconfigure uses the latter, and that's ncurses.

ncurses is written for C, install libncurses5-dev and check the documentation. It's not that difficult, but its API is a bit messy for historical reasons. The Python binding (module curses... just do a regular "import curses") is even better than the original curses, as it is able to automate some nasty stuff (like terminal setting and resetting).

I would like to be able to program both, but i figured i would start with a console app because i though it would be easier to learn.

---

### Post by empthollow on 2008-12-16
> **mssever said:**
> On Linux, wx always uses GTK, even if you're running KDE. If possible, I think you'll find GTK to be a lot easier than wx, though. GTK is already installed on most Linux systems (it's a dependency of such standard apps as GIMP), and you can install it on Windows, too. It's not quite as cross-platform as wx, but my experience with wx has been lots of frustration with its comparative lack of documentation.

you say gtk is easier than wx.  I think i need some clarification.  GTK i know to be a library of widgets.  wx i am understanding is a programming language.  I think i am missing something major.  :confused:

---

### Post by mssever on 2008-12-16
> **empthollow said:**
> you say gtk is easier than wx.  I think i need some clarification.  GTK i know to be a library of widgets.  wx i am understanding is a programming language.  I think i am missing something major.  :confused:
WX and GTK are both GUI toolkits. Neither is a programming language.

---

### Post by iQuizzle on 2008-12-17
> **mssever said:**
> WX and GTK are both GUI toolkits. Neither is a programming language.

yeah he's right. wx probably has a larger learning curve (or so i've heard)...but it's structured nicely and uses the object orientedness of python. both have good support and lots of users, so i think either would be a good choice. i learned wx and use it all the time so i can vouch for it.

---

### Post by mssever on 2008-12-17
> **iQuizzle said:**
> yeah he's right. wx probably has a larger learning curve (or so i've heard)...but it's structured nicely and uses the object orientedness of python. both have good support and lots of users, so i think either would be a good choice. i learned wx and use it all the time so i can vouch for it.
PyGTK is also object-oriented.

I'm someone with very little GUI experience. When I tried a project in wxPython, I eventually gave up because I couldn't figure out how to accomplish what I wanted and the only available comprehensive (I use the term loosely) documentation was for the original C++ and I was often unable to follow it since I don't know C++ very well.. The wxPython docs were woefully inadequate. I've since tried PyGTK and found it to be much more manageable, especially with DevHelp docs. GTK's TreeViews are insanely complex (read: flexible), but that's the only part of GTK I've had major problems with.

I hear that Qt is nice to work with. However, since I prefer Gnome over KDE, I've never played with Qt.

---

### Post by empthollow on 2008-12-17
I prefer gnome over kde as well, and since there seems to be more documentation on gtk i would go that route.  So the next question is C or python.  From looking at the source code of python projects vs C projects, i would guess python is going to be more similar to scripting and as such a little easier for me to  learn.  Would you recommend starting with one over the other from that standpoint?

---

### Post by empthollow on 2008-12-17
I found this tutorial, it looks good to me.  It looks like i need to lear python and add in pygtk.  let me know if there is a better tutorial or if i'm wrong.  Thanks for all your help guys.

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

---

### Post by nvteighen on 2008-12-17
> **iQuizzle said:**
> yeah he's right. wx probably has a larger learning curve (or so i've heard)...but it's structured nicely and uses the object orientedness of python. both have good support and lots of users, so i think either would be a good choice. i learned wx and use it all the time so i can vouch for it.

Actually, GTK+ **is** OOP in C. Of course, a native-OOP language like Python is much easier to deal with, but OOP C can do the same... just with different syntax and lots of more work.

---

### Post by mssever on 2008-12-17
> **empthollow said:**
> I found this tutorial, it looks good to me.  It looks like i need to lear python and add in pygtk.  let me know if there is a better tutorial or if i'm wrong.  Thanks for all your help guys.

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)
That's a good plan. Additionally, I suggest that you install Glade 3, DevHelp, and the PyGTK DevHelp docs (possibly in pygtk's -doc package?). Glade 3 is the latest version of the GTK GUI designer, and DevHelp provides a convenient way to display PyGTK documentation. It'd also help to google GTK and Glade tutorials after working through the Python tutorial.

---

### Post by empthollow on 2008-12-21
Thanks for the input, i'll do just that.  Python sounds like a pretty cool language.

---

