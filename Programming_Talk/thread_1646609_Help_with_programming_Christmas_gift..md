---
title: "Help with programming Christmas gift."
date: 2010-12-16
forum: Programming Talk
---

### Post by StephanG on 2010-12-16
I've recently started to learn C++ programming in anticipation of my studies that are starting next year.  But as I was busy cracking my way through several tutorials, I came up with an ideal gift for my brother.

He is currently a 3rd year electrical engineering student and works on several separate projects, some university related, others work related, and still more are just projects that he likes to tinker with on his own.

Each project usually requires that several PDFs be opened, as well as an IDE, a web browser and a program that I have no idea as too its function.

What I want to do, is program a simple GUI that he can use to group files under a project.  Then, clicking on said project will open all the relevant files and programs.

I thought that the simplest way to do it, would probably be to have the program write a simple script that will open the relevant files.  Then I was planning on putting all of the projects he created on a gadget like the one in the attached picture.


The problem, is that I can't seem to find any comprehensive Windows scripting tutorials, and I can't quite shake the gut feeling that there has to be a better way to do this.

So, if anyone has any advice on how I could go about this, it would be appreciated.  Like I said, I already know some C++, but I haven't yet learned how to create a GUI in it.  Would it be easier to do it in Python?  (I hear that its great for scripting)  And if so, are there any great website tutorials that you could point me to?

Thanks for the help :)

Edit:  P.S.  I forgot to mention, he uses Windows 7 (despite my best conversion attempts) so it has to work on Windows.  I am dual booting Windows 7, so I can compile on a Windows PC if necessary.

---

### Post by trivialpackets on 2010-12-16
Not so sure about the fancy gui type thing, but the scripting part of it to me seems pretty straight forward.  Python would work.  I'm picturing an object, of type "*project*", which contains objects of type "*application*", and each of these objects contains at least two things, the path to the particular filename and the command needed to open the file.  You could define a set of commands based upon the filetype and add it dynamically.  At least those are my thoughts.

---

### Post by StephanG on 2010-12-16
Well, that's exactly what I was thinking as well.  I used to be able to program in Java, but after two years of inactivity...

Anyway, I've found out how to script the opening of several programs in Windows, and save the file in a .bat.  Now all I need is to have a simple gui that is capable of selecting a bunch of files and writing the script.

The "fancy GUI type thing" already exists.  Its called Circle Dock.  If I can get the GUI to write the batch files, it would be a trivial matter to add them to the dock.

I just want a simple "Click here to write batch files" GUI, and then he can add them to the dock himself.

But, I have just begun to explore Python as a possible solution.  Would you happen to know of any good "Python for beginners" websites?

---

### Post by trivialpackets on 2010-12-16
Google "A Byte of Python".  It's a good dive into the language from the ground up and is a short read, but I'm a fan.

---

### Post by StephanG on 2010-12-16
Arigato!  This is exactly what I'm looking for!

I'll read up a little bit, and let you know how it goes.

And thank you :)

---

