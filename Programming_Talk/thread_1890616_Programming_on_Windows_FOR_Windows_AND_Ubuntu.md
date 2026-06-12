---
title: "Programming on Windows FOR Windows AND Ubuntu"
date: 2011-12-03
forum: Programming Talk
---

### Post by JoeSabido on 2011-12-03
I need to build a graphical application that will run as an EXE under Windows and be able to be installed/run under Ubuntu (>=10.04)

The application must be able to print to local printers (dot matrix on lp0) and interact with a remote MySQL database.

I've looked into **Python + wxPython** and I think I can achieve what I need (hopefully) without too much trouble.

Due to "company policy" I can't install Ubuntu on my computer, so all my development must be done under Windows.

For what I've read I think that I can develop the app with the aforementioned tools and then "build it" for windows using Py2exe, but I haven't found (maybe I don't know what to look for) how to package the application as a .deb file or something like that, that can be installed on Ubuntu and be run the same way Windows applications run, and by that I mean that the user will just double-click an icon on the Desktop and the app will launch (without a python shell or a terminal popping up).

If for this to work I need to run a couple of "apt-get install" commands on the Ubuntu computer before the application is installed (to install any Python/wxPython dependencies), that's fine. Of course, if I could include them with the installer that would be even better, but I don't think that's necessary, is it?

I've searched the net on "packaging python for Ubuntu" and stuff like that but whatever I've found looks very obscure and complicated for me, and it assumes that I know way more than I actually do.

Can I write the app under Windows and then copy the files to an Ubuntu machine and use Quickly or other software like that to build a package?

The more "natively" the app runs (the less dependencies it has), the better.

Please be gentle, this would be my first app for Linux (I'm a PHP programmer but PHP just won't cut it this time).

I really want this to work, but coming from a Windows/PHP background I feel a little lost. :(

Thanks for any help you can provide.

Joe

---

### Post by Bachstelze on 2011-12-03
> **JoeSabido said:**
> 
If for this to work I need to run a couple of "apt-get install" commands on the Ubuntu computer before the application is installed (to install any Python/wxPython dependencies), that's fine. Of course, if I could include them with the installer that would be even better, but I don't think that's necessary, is it?

When you have a working package, you can put it on a PPA, and then only two commands will be needed to install it (one to add the PPA and one to install the package, which will also install all the dependencies).

Building the package will probably be the most challenging part, because you will basically need to learn everything about packaging, so that's quite a learning curve. Of course, you *will* need an Ubuntu system in irder to work on a package. It can be a virtual machine or a remote system that you will access with SSH, but you need one. FOr the code itself, you should be fine writing it in Windows, but you will need an Ubuntu system to test that it works there, of course.

---

### Post by JoeSabido on 2011-12-04
Thanks for your reply.

I think I rather go without the PPA, for now.

What software on Windows would you use to make the actual package for Ubuntu? Is there such thing at least?

---

### Post by JoeSabido on 2011-12-04
Wait... I think I'm being dense here...

Can't I just install python and python-wxversion on the Ubuntu computer, then copy the files of the app and just run the script by running a bin file from a Launcher that just executes "python myprogram.py"??????

---

### Post by Bachstelze on 2011-12-04
Regardless of how you distribute your Ubuntu package (PPA or otherwise), you must build it on Ubuntu or at least another Debian-based distribution.

Of course just copying the file should work as well (but you still need an Ubuntu machine to test it).

---

### Post by Petrolea on 2011-12-04
> **JoeSabido said:**
> Wait... I think I'm being dense here...

Can't I just install python and python-wxversion on the Ubuntu computer, then copy the files of the app and just run the script by running a bin file from a Launcher that just executes "python myprogram.py"??????

Well yes, once you got everything set you can pretty much just run the app. Porting the GUI isn't that big of a problem, but the rest might be.

First, you'll need to find a portable MySQL library and if you'll fail to find one, you'll have to make your code check whether you're on Windows or Linux and then make it use the appropriate code and library. Same goes for printing. 
I'm not very familiar with Python but I know that in some other languages this could be a real pain to do.

---

### Post by JoeSabido on 2011-12-04
> **Bachstelze said:**
> Regardless of how you distribute your Ubuntu package (PPA or otherwise), you must build it on Ubuntu or at least another Debian-based distribution.

Of course just copying the file should work as well (but you still need an Ubuntu machine to test it).

Yes, of course. I'll probably bring my own laptop to perform the Ubuntu testing, or I'll do it at home.

> **Petrolea said:**
> First, you'll need to find a portable MySQL library and if you'll fail to find one, you'll have to make your code check whether you're on Windows or Linux and then make it use the appropriate code and library. Same goes for printing. 
I'm not very familiar with Python but I know that in some other languages this could be a real pain to do.

I don't **think** that's the case, at least not with MySQL. Based on what I've read, all I need to do is install python-wxversion and python-mysqldb on the Ubuntu machine (using apg-get install) and that way the native libraries would be installed and all I'd need to copy is the .py file.

---

### Post by Petrolea on 2011-12-04
Well if you can use same libraries on both Windows and Linux, then you have no problem here. 

Can't tell if the same applies for printing, never done it before.

---

### Post by epicoder on 2011-12-04
Keep in mind that if you build a .deb package for Ubuntu, you can have the installer automatically install all the dependencies for it (python, mysql, etc.) For running the script, you can install it in the /usr/bin directory and be able to call it as "myscript" without explicitly invoking python. Just have this code be the absolute first line of your script:
```
#!/usr/bin/env python
```If you aren't going to be distributing it via a PPA or similar repository, then you can make a simple binary .deb using the instructions [here]("http://ubuntuforums.org/showthread.php?t=910717").

---

### Post by JoeSabido on 2011-12-04
> **sh228 said:**
> Keep in mind that if you build a .deb package for Ubuntu, you can have the installer automatically install all the dependencies for it (python, mysql, etc.) For running the script, you can install it in the /usr/bin directory and be able to call it as "myscript" without explicitly invoking python. Just have this code be the absolute first line of your script:
```
#/usr/bin/env python
```If you aren't going to be distributing it via a PPA or similar repository, then you can make a simple binary .deb using the instructions [here]("http://ubuntuforums.org/showthread.php?t=910717").

Thank you! :)

---

### Post by drdos2006 on 2011-12-04
Have a look at what QT4 can do for you. Runs on all sorts of OS, can be designed for desktop, tablet, mobile phone etc.
Communicates with SQL.

regards

---

