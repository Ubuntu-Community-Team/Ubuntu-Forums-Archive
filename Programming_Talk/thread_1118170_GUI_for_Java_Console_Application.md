---
title: "GUI for Java Console Application"
date: 2009-04-06
forum: Programming Talk
---

### Post by shatterblast on 2009-04-06
Hello,

I am looking for something to integrate with a console application that works from the command shell.  I know I can create dialog boxes and text output areas like in the Text Editor, but it's not really the same thing.  The Console class also doesn't seem to be a solution since it focuses on output and input within a command shell, cmd.exe for Windows, and whatever else for Macintosh.  The GUI layout may roughly have the appearance of an IRC client or Pidgin.

For the moment, I am interested in output only.  I am wanting to eventually work the code into a larger application as a personal project.  So far, I am thinking QT Jambi for Eclipse or Jython may provide some sort of solution.  Swing itself doesn't seem to since it requires something extra like an AWT import, though the two often may go together.

Or if someone could point me in the direction of a Java application that works like a chat client of some sort, I would appreciate it.  The two I came across so far worked from terminal only.

---

### Post by Firestom on 2009-04-06
I would strongly suggest QtJambi. Qt is a powerful framework not only including GUI but also Core Classes. To make a "command line"-like interface, you should use a QTextEdit with the colors you want (default console is black background and white foreground) and append your output with the append function. Try it out, you'll be surprised!

---

### Post by shatterblast on 2009-04-06
I have read that QtJambi is very quick as opposed to Jython, due to Python.  I have also seen good critiques on it over all.  It at least appears to not require a license until going open source or whatever else, which doesn't bother me.  Thanks for the input.

---

### Post by Firestom on 2009-04-06
I could make you an example source code, but it would be in C++, since this is the programming language I am using. It is very easy and with his SLOT-SIGNAL system, you'll see it's way simplier!

---

### Post by shatterblast on 2009-04-07
I am aware writing a console-style application with C++ is much easier than Java, probably because of the significant age difference between the two languages.  I prefer Java because of its cross-platform nature.  I will deal with mathematics more in my future, and from my understanding two years ago, coding C++ software for various operating systems can require considerable rewrites if relying on a math library.  If the situation has recently changed for that, then I'm not aware.  I have read a "universal" math library exists that can import into C++, but it causes the language to act slower than Java or something similar.  It's just simple for me to not have to adjust my code for different audiences.

It's good to know someone thinks C++ as simple.  ;)  On the side, I did contemplate integrating a C++ console with my Java project.  The Java Native Interface's nature though last I checked causes noticeable hits to memory and also performance to some lesser extent.  I guess Qt Jambi does it much more effectively than what I know.

I noticed LGPL 2.1 for Qt may fit for me.  Ubuntu Intrepid also seems to have Qt 4 available pre-installed.  I guess that means packaging an extra library into the JAR file or something.  I will check this out.  The advice appears good.

---

