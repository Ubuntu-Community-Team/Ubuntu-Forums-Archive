---
title: "GUI programming in Linux (.NET convert)"
date: 2011-01-30
forum: Programming Talk
---

### Post by rensell on 2011-01-30
Hi all, I'm interested in learning a new programming language. I have done some googling and "playing" around a little bit, but am coming up short.

The back story:
I'm very good with VB.NET programming (in windows, obviously), I created an application that runs many different departments in my small business. The primary use is for my sales staff. I created a VB.NET front end that ties to my server running MYSQL.

I recently made the switch and installed Ubuntu on my laptop and am growing fond of Ubuntu over windows; especially the cost savings!! Anyhow, I've been playing with python, but I can't seem to find appropriate answers. I'm looking to "redo" my application, so I'm looking to create a program that has a GUI for the users; because the terminal will scare some of my employees. I'm hoping to re-create my entire program, in hopes of windows and linux inter-interoperability. 

Any suggestions on an IDE for python or any other direction to explore? All suggestions are greatly appreciated.

-R

---

### Post by gufide on 2011-01-30
I know there's a cross platform open source .NET framework called [mono]("http://www.mono-project.com/Main_Page"). I don't know if it convert VB.NET, but it can be very useful if you're programming in .NET

---

### Post by GabrielYYZ on 2011-01-30
[http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments)

some IDES for python: monkeystudio, visual python, eric, IDLE, netbeans and the pydev plugin for eclipse.

in my experience, eric was kind of confusing. netbeans is great for java and C++ but i've never tried it with python and eclipse feels good but i just tried it a bit, so i can't give an informed opinion about it.

---

### Post by Rab22 on 2011-01-30
> **rensell said:**
> Hi all, I'm interested in learning a new programming language. I have done some googling and "playing" around a little bit, but am coming up short.

The back story:
I'm very good with VB.NET programming (in windows, obviously), I created an application that runs many different departments in my small business. The primary use is for my sales staff. I created a VB.NET front end that ties to my server running MYSQL.

I recently made the switch and installed Ubuntu on my laptop and am growing fond of Ubuntu over windows; especially the cost savings!! Anyhow, I've been playing with python, but I can't seem to find appropriate answers. I'm looking to "redo" my application, so I'm looking to create a program that has a GUI for the users; because the terminal will scare some of my employees. I'm hoping to re-create my entire program, in hopes of windows and linux inter-interoperability. 

Any suggestions on an IDE for python or any other direction to explore? All suggestions are greatly appreciated.

-R

Since you are familiar with the .NET framework (VB.NET), I would say C# is a good place to begin. There is a Mono project that allows you to develop C# on Ubuntu. I'm not certain of the interoperability, but it might be something to research. I'm sure the mono project has a lot of good information on it. 

Next, there is of course Java. Java is a very good language to learn and provides a means to run code on multiple platforms. [Eclipse]("http://blog.sudobits.com/2010/10/15/how-to-install-eclipse-ide-on-ubuntu-10-10/") is a very well known IDE and is, IMO, one of the best out there presently that runs on Linux.

I would recommend these because my guess is that you are familiar with the Visual Studios IDE for VB development. To the best of my knowledge, there are no stable IDEs that robust that work with python.

---

### Post by Nytram on 2011-01-30
If you wrote it in Java you would just need one version of your program, as it's write-once run anywhere. Python can also run on Windows if the user is willing to install it along with the GUI toolkit.

If you're wanting something like VS, as gufide says, there is **mono develop** in the repo's, although it works best with C#.

---

### Post by Rab22 on 2011-01-30
> **GabrielYYZ said:**
> [http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments)

some IDES for python: monkeystudio, visual python, eric, IDLE, netbeans and the pydev plugin for eclipse.

in my experience, eric was kind of confusing. netbeans is great for java and C++ but i've never tried it with python and eclipse feels good but i just tried it a bit, so i can't give an informed opinion about it.

> **Rab22 said:**
> . To the best of my knowledge, there are no stable IDEs that robust that work with python.

Looks like I was wrong...haha.

Looking at the link GabrielYYZ provided, [PyDev]("http://wiki.python.org/moin/PyDev"), maybe something to look into, as it is a plugin for Eclipse.

---

### Post by kalaharix on 2011-01-30
Gambas is a brilliant frontend for mySQL in the commercial world. It's not the same as vb.net (thankfully :p ) but you should be able to transfer the majority of your skills despite the documentation.

Do not install from Ubuntu repository. Rather run 'sudo apt-get install gambas2' from a terminal. All the supplied examples will open read-only so just save as to your home directory.

If you find this to your liking, be aware that Gambas 2 is reaching the end-of-life. You might consider starting with Gambas 3 which is currently a pre release candidate (but relatively stable though not bug-free). Gambas 3 is not in the repositories and has to be compiled from source (see Gambas website for instructions)

---

### Post by directhex on 2011-01-30
If your code is well-written, you could run your existing app, as-is, on Ubuntu, using Mono. Try installing the mono-complete package, then run "mono myapp.exe"

---

### Post by bouncingwilf on 2011-01-30
I have no personnel knowledge of VB programming under Linux but I came across this link that may help.

[http://www.micahcarrick.com/vb-in-linux-with-gtk.html](http://www.micahcarrick.com/vb-in-linux-with-gtk.html)

Bouncingwilf

---

### Post by rensell on 2011-01-30
Thank you for all the responses. I'll take a look at some of the provided links later today. I'm not really looking for a conversion program, I'm looking to re write my existing program, just to clarify. I've been kicking around the idea of java for awhile now but the few java based programs I currently use do not seem to be as "reliable"performance wise. Does anyone have any experience with java front end to mysql. I'm thinking java may work well because it can be installed on machines or tweaked as a web app and/or smart phone apps. However C# does seem like another valid possiblity.

Thanks again for your responses, I will write more once ive looked into the links.

-R

---

### Post by rensell on 2011-01-30
So, I've been working with this for a little while now, I have decided to "jump" into working with mono and have downloaded and installed MonoDevelop 2.2. However, this is seeming like a lot harder of a task than I had previously thought. I normally use Visual Studios and create a form and can place labels, text boxes, command buttons, etc by using the IDE designer. I'm not able to figure out how to do this using MonoDevelop. Any help is greatly appreciated. I've used google and not coming up with much. I'm not usually one to have issues like these. I know I'll be able to learn the code very quickly, but I like to create my form layout before I start coding. 

TYIA,

-R

---

### Post by drdos2006 on 2011-01-30
If you want a front end to connect to SQL then have a look at [http://dabodev.com/](http://dabodev.com/)
If you want a .NET alternative then it may be what you need, runs under python.

regards

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html)
[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html)

---

### Post by fct on 2011-01-30
> **rensell said:**
> So, I've been working with this for a little while now, I have decided to "jump" into working with mono and have downloaded and installed MonoDevelop 2.2. However, this is seeming like a lot harder of a task than I had previously thought. I normally use Visual Studios and create a form and can place labels, text boxes, command buttons, etc by using the IDE designer. I'm not able to figure out how to do this using MonoDevelop. Any help is greatly appreciated. I've used google and not coming up with much. I'm not usually one to have issues like these. I know I'll be able to learn the code very quickly, but I like to create my form layout before I start coding. 

TYIA,

-R

Haven't touched monodevelop in years, but back then Stetic was supposed to become the UI editor. It should be stable now:

[http://www.mono-project.com/Stetic](http://www.mono-project.com/Stetic)

(But only for GTK#?)

---

### Post by directhex on 2011-01-31
Where did you find MonoDevelop 2.2? Ubuntu has 2.2.1 in Lucid, or 2.4 in Maverick

---

### Post by lavinog on 2011-01-31
I had a project that needed to work on all platforms

I used wxglade to design the gui
wxpython

On windows I compiled the program with py2exe which made it so windows users didn't need to install python or any modules.

[http://www.py2exe.org/](http://www.py2exe.org/)

---

