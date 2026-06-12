---
title: "Loading QT Interface From Python"
date: 2010-06-08
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-06-08
What's Up?

OK, So my goal today was to find a nice easy GUI maker for python scripts ( Long story short ttk won't work). I've gotten lost now after reading tons of text on the internet, I've made the .ui file using QT designer, But how do I know show that from a python script?

Thanks Bye!

---

### Post by patchwork on 2010-06-08
OK, take this with a grain of salt because I have done this exactly one time.

You need to use pyuic4 (found in the python-dev-tools package in the repos) to create a .py module from the .ui file, then import the module into your script and call the main window.

EDIT: And I should say that the one time I did this I was fumbling through a tutorial, so I may be leaving something important out.

---

### Post by 23dornot23d on 2010-06-08
I have been trying to work this out too ..... the link below shows what I am trying to do
but I seem to be missing something ..... all the python programs in the repositories seem to be loaded ....

[CENTER][Python Tryout]("http://sites.google.com/site/blenderlearn/assignments/project013")
[/CENTER]

Cannot find this one though  -   pyuic4

Was trying PyQt4 ...... but how do you run it ? 

Looked at QT .... and it looks good but do not know how to get started ...... 
How do you set about adding the User Interface to the python program .....
[QT Forum .... looked here too]("http://www.qtcentre.org/threads/29773-Embedding-PyQt4-into-an-Application-running-Python-via-Boost-Python")
Looked at Eric IDE as well and that is pretty good for editing ..... its in the
repositories too ...... [ERIC IDE]("http://eric-ide.python-projects.org/")  

Have an idea that this might do it ....... but do not know how to get QT forms
and the program to work together     ....... :confused: .......... by the way programming is not my
best skill ..... but I need it for writing blender scripts ..... 

I managed to get what I wanted but the long way around .....  
jumped in here as we may both be after the same thing ,, 
hope that someone can help ...... ty

[CENTER]




[/CENTER]

---

### Post by patchwork on 2010-06-08
The pyuic4 command is part of the python-dev-tools package.

Once you install the python-dev-tools package, the pyuic4 command will be available to you.  Use ```
man pyuic4
``` after instaling to see the full syntax and options for using pyuic4.

---

### Post by 23dornot23d on 2010-06-09
OK thanks got it now - cheers ....... patchwork ....  :KS
I will try the next step now ...... 

[IMG]http://img709.imageshack.us/img709/5316/pyuic4.jpg[/IMG]


[http://img411.imageshack.us/img411/4875/pyuic5.jpg](http://img411.imageshack.us/img411/4875/pyuic5.jpg)

used the following commands .... ( just in case anybody else wants to do this )

(To Create the python file)
$ pyuic4 form.ui --execute --output=form2.py

(To run the python file created)
$ python form2.py

The first command here made it into a python file so its executable ...... 
which when I ran it in Blender gave me  the following ......

[http://img155.imageshack.us/img155/2458/pyuic6.jpg](http://img155.imageshack.us/img155/2458/pyuic6.jpg)

(So to edit it and look at what it produced .... use )
$ gedit form2.py

Cheers again - patchwork
Ok I have my first running form thank you ....

---

### Post by Chamillionaire2 on 2010-06-09
Yay it's finally working! I googled around for ages trying to finding a solution but there doesn't seem to be a tutorial out there anywhere, I've marked the thread as solved and hopefully will help others in the future.

---

