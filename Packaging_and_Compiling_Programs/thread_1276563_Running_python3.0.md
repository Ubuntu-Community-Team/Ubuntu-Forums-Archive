---
title: "Running python3.0"
date: 2009-09-27
forum: Packaging and Compiling Programs
---

### Post by McWeirdo on 2009-09-27
Hello, I'm new to Linux and Python(Fresh newbie) , And I have some problems that I can't over come.  I can't even start to work with python , I come from C# background using Visual studio,I've installed yesterday the Ubuntu 9.04 , just FYI.  I've download the python 3.0.1 package from this website(I think, something with jaunty/python3.0) anyway I opened the terminal and wrote python3.0 or just 3 and it said that it works and that I should press help for help and etc.  now, I have some examples in python that I got from a book, and when I doubleclick on them and then pick &quot;Run in terminal&quot; it just opens the terminal and closes it right away, so nothing is happening , and yes I'm sure those files are for python 3, so this is 1 weird thing. The only thing that works, is while I'm in the terminal that I've opened I write: is_the_sun_yellow=1; I press &quot;ENTER&quot; if is_the_sun_yellow: print (&quot;NO WAyZ!!&quot;); and i pressed &quot;ENTER&quot; and it printed &quot;No wayZ&quot; not sure if this is the way i wrote the code,It's from the documentation  , but it's something like that. well, is this the only way i can write a program in python? cause seems weird there is no way to edit things You wrote? so my question is, where do I write python files, and how do I run them?!!  Thank You in advanced!!! Mcw  EDIT: I don't know why the lines are so crowded in the post, can't fix it :| and where it says quotes it means the sign ''

---

### Post by dinxter on 2009-09-27
theres a few things in there. firstly i'd say, no need to install python from source unless you need to for some reason. python is in the ubuntu repositories, i'd just use that if i were you.
you can write python files just like any other type of programming. i.e. you have your python code in a file like 'hello.py' and you run it by calling the interpreter with the file name,
$python hello.py
that being said there is probably no better way to dive into python than[ 'dive into python']("http://diveintopython.org/toc/index.html") which will quickly get you up and running!

---

### Post by dinxter on 2009-09-27
just to add, when you click 'run in terminal' the default is that the terminal closes when the program has finished running. to change this start a gnome terminal, and go to edit->profile properties. then, in the tab 'Title and Command' change 'When command exits' to 'Hold the terminal open'

---

### Post by Copernicus1234 on 2009-09-27
Dont install python from source, it will probably end up not working as you expect considering you are a newbie. Its better to use System -> Administration -> Synaptic Package Manager to install it (unless its not already installed).

You can type in python code with any editor and then run the code by typing python <filename> in a command prompt. You can also type "ipython" to get a interactive python where you can type in commands and see the result right away. Its very cool for testing code without having to type it into a text file.

There are also professional IDE's similar to Visual Studio. A lot of people like Eclipse. You can install a plugin called Pydev to get python intellisense and other things.

---

### Post by McWeirdo on 2009-09-27
Thank You for the comments,  I will check it now and repost.

---

### Post by McWeirdo on 2009-09-27
Ok, here is what happened: What works: 1)The terminal now won't exit after it executed the file. what doesn't work: the examples have errors, syntax errors and couldn't find files etc, which is weird, those examples are from dive into python, i am using the dive into python 3, so what makes me wonder if i installed it properly... and i opened the terminal and wrote ipython, than it said i need to install it , so i wrote sudo apt-get ipython, and it didnt find the package, and i couldn't find it in the admin thing... what's wrong? I would really like to start studying this language , but as for now , those technical stuff hold me back.  I'm really thankful for your comments, MCW

---

### Post by dinxter on 2009-09-27
i'd say 
1. make sure you have the default python environment and packages installed, (apt-get install python), dont use one you've downloaded yourself, its much easier that way :)
2. ipython is in the repositories but you might need to make sure you have the 'universe' repository enabled in synaptic

---

### Post by McWeirdo on 2009-09-27
Hi again, tried 1: says I already have the newest version. and in I really lost you in 2.  I didn't think it would be that complicated... I'll try to get an IDE.

---

### Post by McWeirdo on 2009-09-27
Arghhh, this is so frustrating!!!! I can't even figure out how to install PyDev, I think I should start reading all those linux books before even trying to understand. but I doubt it's so complicated as I see it, isn't Linux made for simplicity ? EDIT:I haven't connected to the internet with my laptop which has the linux on it, but now i see that "universe repository in Ubuntu" If I understood right is something that allows you to get packages from a server etc and therefore requires an internet connection?

---

### Post by dinxter on 2009-09-27
I would recommend getiing a bit more used to the ubuntu desktop, theres plenty of guides and forums here that should help you get more familiar with it, once you're at bit more at home all this will seem a lot easier. try asking around some more dedicated forum and look through some fo the guides and documentation below
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

---

### Post by McWeirdo on 2009-09-27
> **dinxter said:**
> I would recommend getiing a bit more used to the ubuntu desktop, theres plenty of guides and forums here that should help you get more familiar with it, once you're at bit more at home all this will seem a lot easier. try asking around some more dedicated forum and look through some fo the guides and documentation below
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

Ye, you're right, I always try to run before I learn to walk, so I'll get more familiar with ubuntu and I will be back.  Thank You for your help, MCW

---

### Post by dave WB3DWE on 2009-09-27
[SIZE=3][FONT=Lucida Sans Unicode]Thanks for the above help. I have been struggling with Python3 for several months and installed Ubuntu 9.04 a week ago.
Downloaded the python3.1.1 tarball a few days ago, the version python.org recommends. Extracted it.  README says to install with  $./configure  $make   $make test   $sudo make install . It cautions about installing multiple versions as you may overwrite the earlier ver. Recommends using altinstall instead of install.
Put a post in the novice group yesterday and it was recommended not to install 3.1.1   
Have been trying to use 2.6 .  'python' at the Unix prompt brings up the python interactive command line >>> . But where are the modules, the .py files, where do I store my scripts and where do I go to run a .py file from the Unix command line ?  Grep choked as there are over 600 pythons on the machine.
Hear Mark Lutz's book is coming out in a week; maybe this will help.   Any suggestions appreciated
[/FONT][/SIZE]

---

### Post by dinxter on 2009-09-28
Compiling/installing a python version from scratch is something you probably never need to do, the latest ubuntu comes with python 2.4/2.5/2.6/3.0/ and 3.1 all built and available in the package manager.
As to where to put python files, the short answer is that the .py files can be anywhere you like!, if I had hello.py on my desktop then i could run
$python ~/Desktop/hello.py 
the form of the command is simply
$python /path/to/the/python/file/goes/here/hello.py
as mentioned previously it may be a good idea to get some further information from the various ubuntu support options to familiarise yourself a bit more with the structure of a linux system, theres a link below to general terminal guidance below too if it helps
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

