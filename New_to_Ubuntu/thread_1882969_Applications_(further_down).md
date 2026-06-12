---
title: "Applications (further down)"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by tnob on 2011-11-18
Hello all,

A new kid on the block - and an absolute beginner in all things Ubuntu, to boot - I'm still trying to pick my way. One essential thing I haven't worked out yet is where exactly, further down in the system, Applications (like Accessories, Games Multimedia, Office, etc) are located. No problems finding those on the desktop, of course - but digging a little deeper and I am lost. 

My hardback beginners' handbook and several manuals found on the web all say that everything you need is in the Home Folder - but Applications are definitely not there! And since I'd like at least some manual control of applications NOT downloaded from Ubuntu Software Centre (the command line still being a little scary, at this stage), I wonder where best to go to.

Any helpful suggestions? Thanks!

tnob

---

### Post by thatguruguy on 2011-11-18
Which version of Ubuntu are you running?

---

### Post by sureshsaragadam on 2011-11-18
Firstly what version of Ubuntu you are running, If you are running Ubuntu 11.10
[B]
'Dash Home[/B]' is what you want, Nothing but '**widows key**' on your key board!

Just press that key, you will get a search box, You can search for your application,

Initially it will be difficult to work this way, When you are used to this it will be more comfortable.

You can use shortcuts

Dash Home + s                 to search for applications
Dash Home + f                 to search for files


The launcher is left pane of your Ubuntu 11.10 installation, there you can see some application icons
In the launcher (you will find the '**home folder**', that is the second icon after dash home)

Surf for 'Ubuntu Shortcuts' of your Version.

All the best.

---

### Post by WasMeHere on 2011-11-18
Hi tnob,

If you know the name of the program behind the application name it is easy when you run from a terminal window. You start a terminal window with ***ctrl + alt + t***. Type commands etc and finish by pressing the Enter key! For example: ```
nautilus
``` will start the file browser.```
which nautilus
``` will give you the full path to it.

It is also valuable to learn the most important commands in ***bash*** (the shell interpreter, the 'language of the terminal'. Browse the internet for ***tutorials linux bash***. You can also read the built-in manual ```
man bash
```

To search for any file with wild-cards, you can use ***find***. Read ```
man find
``` and browse the internet for tutorials!

Have fun finding out about Ubuntu :-)
Olle

---

### Post by mcduck on 2011-11-18
> **tnob said:**
> Hello all,

A new kid on the block - and an absolute beginner in all things Ubuntu, to boot - I'm still trying to pick my way. One essential thing I haven't worked out yet is where exactly, further down in the system, Applications (like Accessories, Games Multimedia, Office, etc) are located. No problems finding those on the desktop, of course - but digging a little deeper and I am lost. 

My hardback beginners' handbook and several manuals found on the web all say that everything you need is in the Home Folder - but Applications are definitely not there! And since I'd like at least some manual control of applications NOT downloaded from Ubuntu Software Centre (the command line still being a little scary, at this stage), I wonder where best to go to.

Any helpful suggestions? Thanks!

tnob

Do you mean something like "Program Files" folder on Windows, or "Applications" on OSX?

There is no such thing in Linux. Instead of placing all the program's files into same place, they are distributed around the filesystem based on the purpose of each file. Libraries go to /usr/share/lib, images to /usr/share/pixmaps, documentation goes to /usr/share/doc, system-wide setting files go to /etc, user-spcific setting files to that suers home directory and so on. You'll usually find the executable file for your program in /usr/share/bin, and all the files with no specific location in /usr/share/*nameoftheprogram*.

The actual launcher files that you see in the menus are in /usr/share/applications. And of course ~/.local/share/applications for the launchers you have created for a specific user only (with the Main Menu-tool, for example) instead of configuring one system-wide.

This might seem a bit of a mess for somebody new to Linux, but it's actually quite convenient, once you've learned the most common locations you'll always know exactly where to look for e certain type of file, no matter what program it belongs to. For example every time you need to find the executable of a program instead of browsing through each program's directories inside Program Files like you'd have to do on Windows, you can just go to /usr/share/bin and know your program's executable will be there, right next to all the other executables for all your programs. And of course managing all the the files isn't a problem either, as we have the package manager to handle that for us automatically. :)

---

### Post by sureshsaragadam on 2011-11-18
> **Olle Wiklund said:**
> Hi tnob,

If you know the name of the program behind the application name it is easy when you run from a terminal window. You start a terminal window with ***ctrl + alt + t***. Type commands etc and finish by pressing the Enter key! 

Finding a name of an application is bit difficult, Ubuntu 11.10 going far away from terminal and desktop......It is targeting Notebooks and Tablets, 

Now default Alt-F2 is not supported, We have to make ourself available with this tradition of Alt F2 to function, 

Earlier i used to find the command of an application by dragging the icon to the panel and finding the command from properties of it.

Now right click is not working, If i try to use right click it is launching the application,
In that case finding a terminal command to run will be bit difficult.

In-fact digging a litter deeper is bit difficult with Ubuntu 11.10.

---

