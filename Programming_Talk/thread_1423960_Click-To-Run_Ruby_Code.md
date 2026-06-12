---
title: "Click-To-Run Ruby Code"
date: 2010-03-07
forum: Programming Talk
---

### Post by Majorix on 2010-03-07
Imagine you write a Ruby code, and want it to run when you click on it.

I am trying to do it under Gnome, and when I click, it asks me if I want to execute it or just view the code. I have already set the script to be executable.



I have heard of Rubinius too, and tried it yesterday. No luck:
```
An exception occurred running main.rb
    no such file to load -- tk (LoadError)
```Besides, if I were to succeed in running Rubinius, would the end user need Rubinius installed? Seeing as how it is not in a default Ubuntu install, and not even in the repos; it might cause trouble.

I believe there is a compile() function with Python, is there some sort of a Ruby equivalent? Or any other way? Please help me out!

Also, is there a way to compile Ruby code to binary code, since most of the companies I will work for won't want the script to be immediately available to competitors.

Thanks.

---

### Post by crush304 on 2010-03-07
you prob need to copy your script to a folder in the execution path, (usr/local/bin) then you can create a shortcut on your desktop (or wherever you want it) pointing to that file

don't know anything about Rubinius, you might also look into jruby, it is in the repos and will allow you to compile to java bytecode

---

### Post by Majorix on 2010-03-07
Thanks for the reply.

I have tried creating a symlink (ln -s) to the script, but it still asks if I want to view or run. Perhaps you meant another way?

About JRuby... Is it possible to make a JRuby sourcecode to act just like a Java sourcefile?

---

### Post by erginemr on 2010-03-07
I have tried the same with this following über-simple Python code:
```
#!/usr/bin/env python
print "Hello World!"
raw_input("Press ENTER to exit")
```

Made the script executable. Yet still, Gnome welcomed me with a dialog to "edit / run / run in terminal" when I double-clicked it.

I think Gnome is designed to act this way, in such a way that it gives you the choice to do whatever you want with the code (which is very convenient if you ask me). It also adds a new layer of security against accidentally running malicious code.

---

### Post by Majorix on 2010-03-07
Maybe you should try using Python's compile() method from the library.

[http://effbot.org/zone/python-compile.htm](http://effbot.org/zone/python-compile.htm)
[http://docs.python.org/library/compiler.html](http://docs.python.org/library/compiler.html)

---

### Post by kahumba on 2010-03-07
It's not "Gnome" asking, it's really Nautilus under the hood since the desktop is also rendered by Nautilus.
To get rid of this question open a Nautilus window, then Edit->Preferences->Behavior and check the first option  in "Executable Text Files".

Again, it's not Linux (the kernel) nor the distribution, it's the decision of the file manager. If you install some other file manager it could skip the question by default, it's really a matter how paranoid you (or Nautilus in this case) are about executing such files at double click.

---

### Post by erginemr on 2010-03-07
> **kahumba said:**
> It's not "Gnome" asking, it's really Nautilus under the hood since the desktop is also rendered by Nautilus.
To get rid of this question open a Nautilus window, then Edit->Preferences->Behavior and check the first option  in "Executable Text Files".


That does it! Thanks for this great tip! :popcorn:

EDIT: Hmm, on a second thought, this option does not correctly run scripts which reads from and writes to the terminal screen...:-k

---

### Post by kahumba on 2010-03-07
Huh your case is pretty seldom (an app requiring terminal but still run by double click).
You need to create (yourself) a .desktop file and specify there that your app needs a terminal.

Here's an example of a file with the .desktop extension
```

[Desktop Entry]
Version=1.0
Name=Your-app-name, for example Firefox
Comment=Short comment
Exec=/full/path/to/the/executable
Icon=/full/path/to/the/icon/for/your/app
Type=Application
Categories=Application;
#next line specifies that your app needs a terminal
Terminal=true

```Read more here:
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

to edit a .desktop file drag it into the gedit window cause double clicking them just opens their executable or yields an error.

Actual examples of .desktop files are in the folder /usr/share/applications

---

### Post by Majorix on 2010-03-08
> **kahumba said:**
> It's not "Gnome" asking, it's really Nautilus under the hood since the desktop is also rendered by Nautilus.
To get rid of this question open a Nautilus window, then Edit->Preferences->Behavior and check the first option  in "Executable Text Files".

Again, it's not Linux (the kernel) nor the distribution, it's the decision of the file manager. If you install some other file manager it could skip the question by default, it's really a matter how paranoid you (or Nautilus in this case) are about executing such files at double click.

That seemed to do the trick, thanks a lot! :D

There is one question left now: How to close the source?

---

### Post by Majorix on 2010-03-09
> **Majorix said:**
> There is one question left now: How to close the source?

Nobody?

---

### Post by kahumba on 2010-03-09
Hiding the code is usually one of the favorite questions of the beginners and the bad news is that there's no universal solution that wouldn't introduce other problems or wouldn't in fact be a half backed solution or wouldn't have (some other) side effects.

If your program is valuable it will be cracked even if compiled to binary, (big) companies invest into DRM tons of money with little to no success. I doubt you're willing to go this way and that you have that much money to spend (almost in vane if your app is very valuable).

Also, once you make it binary ("hide the source") you'll have to create a version of your program for every OS and maybe further separate version for 32 & 64 bit chips. Do you really think it's worth it?

---

