---
title: "beginner programmer"
date: 2011-06-12
forum: Programming Talk
---

### Post by sydox on 2011-06-12
This is my first thread so my apologies if I'm in the wrong topic area.

Here's a little background info; I'm novice in C++ for windows. I took courses at my local college and got an A.S. degree in Computer Science (mainly C++ programing). I'm currently going for my B.S. in Computer Engineering (half Programming and half electrical). I'd like to say I'm an "expert" in windows, and this is why I HATE windows, but I'm novice in Linux. I'm sorry if this info doesn't seem relevant I would just like you to know where I stand in programming and computer knowledge, I believe it may be helpful to answering my question.

I would like to understand and start programming in Linux. for example I'd like to make a word pad program. I have made one in C++ for windows but don't know where to begin in Linux. Or I'd like to change lines in my current setup, so i can customize it more

I've looked at some Linux books and tutorial videos but either everything seems too simple (for instance the books tell you how to use Linux not program in it) or simply above my head (I'm watching tutorials from LinuxCBT and the information is going too fast as if I'm supposed to know what "less" does or "ls")

I'm assured I'm missing vital steps in learning Linux correctly. I understand A LOT of Linux should be by commands and I'm new to what different commands do. 

I have a separate machine with Ubuntu 11.4 on it, and nothing important on it. If I mess something up I don't care because at this stage I got the mind set that it only take a half hour to re-install Linux and get a fresh slate (sorry if that's a bad mindset). 

Any help as to what topics or subjects I should be learning would be very appreciated.

---

### Post by Wim Sturkenboom on 2011-06-12
I usually write server apps, so a wordpad like app in C++ is outside my league. If I write GUI apps in Linux, I use either Tcl/Tk (from scratch) or Java (using Netbeans). So not much help there either. I use those as they are basically platform independent so what I write in Linux will also work in Windows.

There are basically 2 graphical frameworks, Gtk and Qt. To my knowledge, the former is more C oriented and the latter C++ oriented. So I would look at those if you want to start coding GUI apps in C and C++. I guess that you can use both frameworks for either languague.

I consider the Linux Programming Bible a very good book to get going in programming under Linux; it tought me a lot but does not really cover GUI stuff.

PS 1
Customizing is not really programming related; it often involves modifying config files.

PS 2
To know what a command does, use man (e.g. *man ls*).

PS3
[the linux documentation project](http://tldp.org/) can be a good source for general info

---

### Post by cchristian on 2011-06-12
Not sure if it's what you're looking for, but if you wanted to brush up on some basic commands and such, I found these Google University pages to be very useful:

[http://code.google.com/edu/tools101/linux/basics.html](http://code.google.com/edu/tools101/linux/basics.html)
[http://code.google.com/edu/tools101/linux/ownership_permissions.html](http://code.google.com/edu/tools101/linux/ownership_permissions.html)
[http://code.google.com/edu/tools101/linux/grep.html](http://code.google.com/edu/tools101/linux/grep.html)

Here's their general 'courses' page.  They have some things about C++, which from what I saw, assumes you're programming in linux.  You may want to take a look:

[http://code.google.com/edu/courses.html](http://code.google.com/edu/courses.html)

---

### Post by mali2297 on 2011-06-12
If you would want to make a text editor using GTK+ and C++, there is [gtkmm]("http://www.gtkmm.org/"). The official website contains links to documentation. Check out the textview widget.

Also, for general information on programming in Linux, see this [sticky]("http://ubuntuforums.org/showthread.php?t=1766253") in the programming subforum.

---

### Post by coldraven on 2011-06-12
This could be handy [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Don't forget that the TAB button will autocomplete for you.
So if you have really-really-really-long-filename.so in your directory, just type "re" and hit tab.
End of lesson :)

---

### Post by Rocket2DMn on 2011-06-12
Moved to Programming Talk. Check out this sticky for more info on getting started with programming in linux - [http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)
Cheers and welcome to Ubuntu.

---

### Post by mbeach on 2011-06-12
> **sydox said:**
> start programming in Linux. for example I'd like to make a word pad program. I have made one in C++ for windows but don't know where to begin in Linux.

you might be interested in Glade:
[http://glade.gnome.org/](http://glade.gnome.org/)

---

### Post by cgroza on 2011-06-12
I have already made a text editor in wxWidgets. It has that nifty wxStyledTextCtrl which is scintilla based.

I recommend you wxWidgets as a GUI toolkit. It is native in C++ and has a tons of bindings for Python, Ruby, Perl, and others.

---

### Post by sydox on 2011-06-23
THANX!!!!! I love how friendly and helpful folks are in the Linux world.

This is a lot of content to search through, and I honestly don't get much time to dabble in software programming. It's more of a hobby. I'm more of a micro-controller programmer which, of course, is a different world than software programming.

Once again sorry for putting this is the wrong forum section.

---

### Post by boast on 2011-06-23
> **sydox said:**
> I'm more of a micro-controller programmer which, of course, is a different world than software programming.


cool! I'm an electrical engineering student with a concentration in embedded systems. 

What kinda embedded applications do you usually work on with micros?

---

### Post by sydox on 2011-06-24
I'm in college as well, so I'm really not a good person to ask as for what the "work force" uses. sorry

As for what I've worked with are Motorola boards and "easypic" (MikroElektronica) boards

---

