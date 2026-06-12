---
title: "Making Linux Applications"
date: 2011-06-28
forum: Programming Talk
---

### Post by life in color on 2011-06-28
Hi, I would like to start learning how to make Linux applications and I was wondering where the best place to look for free lessons would be? I have a very small amount of experience with Python, HTML, and PHP but that's it, I installed QT but it's hard to find tutorials for QT and I don't know how to use C++ any suggestions?

---

### Post by Ozymandias_117 on 2011-06-28
Two good sites for C++ (And C) programming:

[http://cplusplus.com/](http://cplusplus.com/)
[http://www.cprogramming.com/](http://www.cprogramming.com/)

Is there a particular reason you're looking at C++?

---

### Post by nzjethro on 2011-06-28
I would say that Python is a fine language for creating Linux apps. It's easy to write and read, it works with any Linux computer (well, just about any), and it's great to see FOSS using FOSS.

Only downside is that it is slower than a compiled language (like C++), but if you are creating apps it shouldn't make too much of a difference. Why were you thinking of writing in a different language?

---

### Post by idoitprone on 2011-06-28
> **life in color said:**
> Hi, I would like to start learning how to make Linux applications and I was wondering where the best place to look for free lessons would be? I have a very small amount of experience with Python, HTML, and PHP but that's it, I installed QT but it's hard to find tutorials for QT and I don't know how to use C++ any suggestions?

[http://doc.qt.nokia.com/](http://doc.qt.nokia.com/)

qt is one of the best documented opensource tool sets. Here the link for the docs. If you want free lessons. go try to volunteer for an opensource project. Nothing is better than real world experience

---

### Post by life in color on 2011-06-28
@ Ozymandias_117 I will try them both, and no particular reason I just figured C++ was a good programming language, but I want to use whatever is best suited for Linux.

@nzjethro I just assumed C++ would be better design wise because of qt, but from your response I may just go back to using python! Whatever is used most by Linux-ers, I do remember that Linus Torvalds insulted C/C++ as a programming language so Python may be my best option.

---

### Post by nzjethro on 2011-06-28
> **life in color said:**
> 
@nzjethro I just assumed C++ would be better design wise because of qt, but from your response I may just go back to using python! Whatever is used most by Linux-ers, I do remember that Linus Torvalds insulted C/C++ as a programming language so Python may be my best option.

I should mention that I haven't dealt with qt, so I may not be the best to give advice. I say that you should use what you like to use, but I'm not sure what Python/qt compatibility is like.

---

### Post by idoitprone on 2011-06-28
> **life in color said:**
> @ Ozymandias_117 I will try them both, and no particular reason I just figured C++ was a good programming language, but I want to use whatever is best suited for Linux.

@nzjethro I just assumed C++ would be better design wise because of qt, but from your response I may just go back to using python! Whatever is used most by Linux-ers, I do remember that Linus Torvalds insulted C/C++ as a programming language so Python may be my best option. 

actually...linus torvalds just plainly hated c++. c++ is just c with more features. In terms of commputing, the best features are one that are not even there. It convient, but it just make things worse. The linux kernel is written in c. Why would Linus, the egotiscal bastard, use a tool that he hated. It kidda like Linux writing a microkernel.

> Programming languages should be designed not by piling feature on top of feature, but by removing the weaknesses and restrictions that make additional features appear necessary.
          — RnRS
here a long list a rants. Please note that these people used the language when the first compilers came out. So it was a giant pain in the *** for them to use. Also, some of the heavy critics are also people who view languages by design instead of practicalty. 

[http://harmful.cat-v.org/software/c++/](http://harmful.cat-v.org/software/c++/)

---

### Post by Lars Noodén on 2011-06-28
You can use python with Qt using [PyQt](http://www.riverbankcomputing.com/software/pyqt/intro)

---

### Post by slooksterpsv on 2011-06-28
> **life in color said:**
> Hi, I would like to start learning how to make Linux applications and I was wondering where the best place to look for free lessons would be? I have a very small amount of experience with Python, HTML, and PHP but that's it, I installed QT but it's hard to find tutorials for QT and I don't know how to use C++ any suggestions?

PyQT4 -
[http://zetcode.com/tutorials/pyqt4/](http://zetcode.com/tutorials/pyqt4/)

That site teaches a lot, and quite well too. It doesn't use the qt designer, which with the QT Designer you place the objects and save an XML file then you can use a pyuic program to convert from the xml to python. Then hard code what you need in the python file =D.

If anything learn the above, then just google pyuic tutorial

---

### Post by lisati on 2011-06-28
*Thread moved to **Programming Talk**.*

---

### Post by b@sh_n3rd on 2011-06-28
@OP: As many already mentioned, you could stick to Python. I now use Python over C/C++ for my coding needs. I still *do* use C/C++ but to get something done fast, Python is easier. Especially if you know the language already. And, again as mentioned, you could check out PyQt4 or even mix it up with GTK instead...well, that's what *I'm* trying to do :P Nevertheless, since most of my apps are CLI based, there's not much I could say about GUI programming just yet...

PS: I use Python 3

---

### Post by life in color on 2011-06-29
Well I thank you all for your quick replies and I will try out pyQT. Does it need to be compiled from source or can you just use an apt-get code in Terminal?

---

### Post by Lars Noodén on 2011-06-29
> **life in color said:**
> Well I thank you all for your quick replies and I will try out pyQT. Does it need to be compiled from source or can you just use an apt-get code in Terminal?

Gentoo is the only distro where it is common to compile from source.

For Ubuntu, I would start with the package [pyqt-tools](http://packages.ubuntu.com/natty/pyqt-tools).

---

### Post by boast on 2011-06-29
> **life in color said:**
> I installed QT but it's hard to find tutorials for QT and I don't know how to use C++ any suggestions?


[https://www.youtube.com/user/VoidRealms#p/u/94/Id-sPu_m_hE](https://www.youtube.com/user/VoidRealms#p/u/94/Id-sPu_m_hE)

and QT is quicktime, I hope you meant Qt :P

---

### Post by life in color on 2011-06-29
[HTML]> Gentoo is the only distro where it is common to compile from source.

For Ubuntu, I would start with the package pyqt-tools. 
[/HTML] I installed the .deb package then went into terminal and this is what happened 
[HTML]```

hunter@ubuntu:~/Downloads$ sudo dpkg -i pyqt-tools_3.18.1-4ubuntu3_amd64.deb
[sudo] password for hunter: 
(Reading database ... 252116 files and directories currently installed.)
Preparing to replace pyqt-tools 3.18.1-4ubuntu3 (using pyqt-tools_3.18.1-4ubuntu3_amd64.deb) ...
Unpacking replacement pyqt-tools ...
Setting up pyqt-tools (3.18.1-4ubuntu3) ...
Processing triggers for man-db ...

```
[/HTML]
Any help?

---

### Post by life in color on 2011-06-29
[HTML]```

https://www.youtube.com/user/VoidRea...94/Id-sPu_m_hE

and QT is quicktime, I hope you meant Qt 
```[/HTML]
Thank you for the correction I didn't realize QT=Quicktime while Qt=Nokia Qt and I will check out the link!. This is kind of off topic but how do you do the proper non-HTML quote and code boxes because I haven't been able to figure it out.

---

### Post by NovaAesa on 2011-06-30
It's probably easiest to get pyqt-tools straight from the repos, i.e. use ```
sudo apt-get install pyqt-tools
```

EDIT: to use the code block, use the [ code ] and [ /code ] tags (with no spaces).

2nd EDIT: I didn't realise the last reply was 14 hrs ago... so you've probably already got your pyqt-tools installed from that deb file, if it's working, ignore what I said about installing from the repos!

---

### Post by life in color on 2011-06-30
```
hunter@ubuntu:~$ sudo apt-get install pyqt-tools
[sudo] password for hunter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package rhythmbox-desktop-art needs to be reinstalled, but I can't find an archive for it.

```
Well I'm not really sure what to do now...

---

### Post by slooksterpsv on 2011-07-01
> **life in color said:**
> ```
hunter@ubuntu:~$ sudo apt-get install pyqt-tools
[sudo] password for hunter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package rhythmbox-desktop-art needs to be reinstalled, but I can't find an archive for it.

```
Well I'm not really sure what to do now...

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install pyqt-tools

```

Although I'm thinking you already have pyqt-tools installed. Either way when it says it can't find something in the repos, I usually do an update then an upgrade in case it can resolve issues.

---

### Post by life in color on 2011-07-01
@slooksterpsv
```

sudo apt-get install pyqt-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pyqt-tools is already the newest version.
The following packages were automatically installed and are no longer required:
  mesa-utils libknewstuff2-4 python-wxgtk2.8 libindicate-qt1 libdiscid0
  libtag-extras1 libkcddb4 libasyncns0 wine1.0-gecko kdemultimedia-kio-plugins
  libmusicbrainz3-6 liblastfm0 libloudmouth1-0 python-wxversion
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
The first 2 commands went fine, then I ran this and apparently I have it already installed though I couldn't find it when I searched with the applications searcher on the side panel, and I couldn't find it in usr/bin :( 


I also recently found out about pygtk and I was wondering if I could use that instead?

---

### Post by slooksterpsv on 2011-07-01
> **life in color said:**
> @slooksterpsv
```

sudo apt-get install pyqt-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**pyqt-tools is already the newest version.**
The following packages were automatically installed and are no longer required:
  mesa-utils libknewstuff2-4 python-wxgtk2.8 libindicate-qt1 libdiscid0
  libtag-extras1 libkcddb4 libasyncns0 wine1.0-gecko kdemultimedia-kio-plugins
  libmusicbrainz3-6 liblastfm0 libloudmouth1-0 python-wxversion
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
The first 2 commands went fine, then I ran this and apparently I have it already installed though I couldn't find it when I searched with the applications searcher on the side panel, and I couldn't find it in usr/bin :( 


I also recently found out about pygtk and I was wondering if I could use that instead?

See the bold above, it's already installed.

Sure I think its like:

sudo apt-get install python-gtk2

---

### Post by life in color on 2011-07-01
Thanks and is IPhone development possible with Linux? I even tried Mac On Linux but couldn't get it to install

---

### Post by life in color on 2011-07-01
python-gtk2 is already installed as well!! Why can't I find either of these applications?

---

### Post by slooksterpsv on 2011-07-01
> **life in color said:**
> python-gtk2 is already installed as well!! Why can't I find either of these applications?

The pyqt-tools may include tools like pyuic (converting qt xml files to python files) and that. The python-gtk2 is a library not a program so when you make a program that's python and uses gtk2 for it's GUI elements, you'll use the python-gtk2 libraries for those elements and the functionality of them.

What tools do you need? If you need GUI designers, try glade, qt-designer, or I think boa constrictor does gtk2 GUIs

If you need an IDE, I like Eclipse personally, but you can use IDLE, or other IDEs listed in the software center.

---

### Post by juancarlospaco on 2011-07-01
Why dont just make web apps, so can be used on any toolkit/os/de/* ?

This is a Hello World on Python[ with Bottle:]("http://bottlepy.org/")

```
from bottle import route, run

@route('/')
def index():
    return "Hello World"

run()
```

You dont have to know HTML, you can use Kompozer  :)

---

### Post by life in color on 2011-07-01
> 
The pyqt-tools may include tools like pyuic (converting qt xml files to python files) and that. The python-gtk2 is a library not a program so when you make a program that's python and uses gtk2 for it's GUI elements, you'll use the python-gtk2 libraries for those elements and the functionality of them.

What tools do you need? If you need GUI designers, try glade, qt-designer, or I think boa constrictor does gtk2 GUIs

If you need an IDE, I like Eclipse personally, but you can use IDLE, or other IDEs listed in the software center.

You've lost me now, I have a bunch of .py files, say I wanna design a GUI for them where would I start?

---

### Post by life in color on 2011-07-01
> 
Why dont just make web apps, so can be used on any toolkit/os/de/* ?

This is a Hello World on Python with Bottle:

```

from bottle import route, run

@route('/')
def index():
    return "Hello World"

run()

```
You dont have to know HTML, you can use Kompozer  

Hmm, I'm not fond of Kompozer, I'd rather just try the HTML myself but this doesn't look anything like the Hello-World I made and it barely resembles anything else I've done.

---

### Post by slooksterpsv on 2011-07-01
> **life in color said:**
> You've lost me now, I have a bunch of .py files, say I wanna design a GUI for them where would I start?

Get used to the words, you'll hear them a lot:

Glade - Used for GTK+ 2
Qt 4 Designer - Used for Qt GUIs
wxFormBuilder - Used for wx

Those 3 I know for sure work with Python (although the Qt 4 Designer you use pyuic to convert the XML file to a .py file). With the Glade files it looks like you have to import it in your code lik.... well...

[http://www.overclock.net/application-programming/342279-tutorial-using-python-glade-create-simple.html](http://www.overclock.net/application-programming/342279-tutorial-using-python-glade-create-simple.html)

Do that tutorial it'll help, but install glade first. I haven't programmed with GTK+ or that, I use Qt 4 more.

---

### Post by slooksterpsv on 2011-07-01
Ya know what, I have a program here, I'm working on it, it's a WIP. It works, it's a python qt program I'm working on. So look it, look at the source, and see what you think:

It's a simple program so far, but the GUI was easy to create in Qt 4 Designer

EDIT:

Requires python-qt4

---

### Post by life in color on 2011-07-02
```

Ya know what, I have a program here, I'm working on it, it's a WIP. It works, it's a python qt program I'm working on. So look it, look at the source, and see what you think:

It's a simple program so far, but the GUI was easy to create in Qt 4 Designer

EDIT:

Requires python-qt4
Attached Files
	stk-crp-p1.py (16.3 KB, 0 views)
__________________

```
I love it!!! I see you're using Python 2.7.5
I've been using 3.2, but I can manage 2.7.5 if I have to.




```

Get used to the words, you'll hear them a lot:

Glade - Used for GTK+ 2
Qt 4 Designer - Used for Qt GUIs
wxFormBuilder - Used for wx

Those 3 I know for sure work with Python (although the Qt 4 Designer you use pyuic to convert the XML file to a .py file). With the Glade files it looks like you have to import it in your code lik.... well...

http://www.overclock.net/application...te-simple.html

Do that tutorial it'll help, but install glade first. I haven't programmed with GTK+ or that, I use Qt 4 more.

```
Will do!

---

### Post by life in color on 2011-07-02
sorry I meant to use quote brackets!

---

### Post by slooksterpsv on 2011-07-02
Yeah with Python there's a lot of talk about fragmentation within python itself. I have a feeling that due to this 3.x won't be a standard for a bit, because 2.x is used quite a bit more and the changes are kind of big between the two. 

PyGame, I think, just recently started supporting Python 3.x with version 1.91 and the SVN.

If you have any issues using one UI with python, make sure it's supported under the 3.x version you're using.

EDIT: And if I'm wrong, correct me.

---

### Post by slavik on 2011-07-02
Back to the topic of qt and C++, I found this tutorial: [http://zetcode.com/tutorials/qt4tutorial/](http://zetcode.com/tutorials/qt4tutorial/)

---

### Post by life in color on 2011-07-02
@slooksterpsv btw thanks for all the help so far and with the glade tutorial you gave me I can't seem to figure out how to edit the size of the buttons.

> 
Back to the topic of qt and C++, I found this tutorial: [http://zetcode.com/tutorials/qt4tutorial/](http://zetcode.com/tutorials/qt4tutorial/)



Thank you I will give it a try!

---

### Post by cgroza on 2011-07-02
I think you should take a look at wxWidgets too. It has bindings for python2.7.
The 3.x is not supported yet.

---

### Post by life in color on 2011-07-02
> 
I think you should take a look at wxWidgets too. It has bindings for python2.7.
The 3.x is not supported yet.

Yes sir! Any instructions on installation?

---

### Post by life in color on 2011-07-02
> 
Back to the topic of qt and C++, I found this tutorial: [http://zetcode.com/tutorials/qt4tutorial/](http://zetcode.com/tutorials/qt4tutorial/)

Great tutorial!! It's helping a lot!

---

### Post by slooksterpsv on 2011-07-03
> **life in color said:**
> Yes sir! Any instructions on installation?

python-wxglade - GUI designer written in Python with wxPython
python-wxgtk2.8 - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)

Just install those 2 packages via:

sudo apt-get install python-wxglade python-wxgtk2.8

---

### Post by slavik on 2011-07-03
a question to the original poster: Do you care for the suggestions of using GTK and Python, although you had only mentioned that you are looking for tutorials involving QT and C++?

---

### Post by cgroza on 2011-07-03
> **life in color said:**
> Yes sir! Any instructions on installation?
Also, wxWidgets is written in C++, just like Qt.

---

### Post by life in color on 2011-07-03
> 
a question to the original poster: Do you care for the suggestions of using GTK and Python, although you had only mentioned that you are looking for tutorials involving QT and C++?

I do! My friend just recently suggested that the two of us make an iPhone app, after doing some research I've found out that Apple absolutely doesn't except any iPhone apps not made completely on a Mac using XCode. My friedn has multiple macs and xcode so we're covered there but I need to be able to use C++ in order to make the app so I just planned on making certain areas of the app on Linux for testing then re-writing it in cocoa. I also would still like to know how to make Linux applications as well as Android apps (I figured I could make these on my Linux computer since Android is Linux)

---

### Post by life in color on 2011-07-03
> 
python-wxglade - GUI designer written in Python with wxPython
python-wxgtk2.8 - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)

Just install those 2 packages via:

sudo apt-get install python-wxglade python-wxgtk2.8

Check!

---

### Post by life in color on 2011-07-03
> 
Also, wxWidgets is written in C++, just like Qt.

Not a problem, I've come to the conclusion that C++ is something I must learn if I'm serious about applications, I still like Python but its not good for everything.

---

### Post by cgroza on 2011-07-03
> **life in color said:**
> Not a problem, I've come to the conclusion that C++ is something I must learn if I'm serious about applications, I still like Python but its not good for everything.
wxWidgets has bindnigs for python so you can enjoy both.
The bindngs is called wxPython and it is the repos.

---

### Post by life in color on 2011-07-05
> 
wxWidgets has bindnigs for python so you can enjoy both.
The bindngs is called wxPython and it is the repos.

Would you recommend it? Qt was a good GUI but I didn't really like Glade.

---

### Post by slavik on 2011-07-05
in that case, I suggest Perl and GTK.

---

### Post by llanitedave on 2011-07-05
> **life in color said:**
> Would you recommend it? Qt was a good GUI but I didn't really like Glade.

I'm learning wxPython now and I'm really liking it.  I didn't care for Glade, but you don't need it for wx.

---

### Post by cgroza on 2011-07-05
I wrote a 4000 line project in wxPython and I found it very easy to use and flexible.
It is definitely an option to consider.

---

### Post by life in color on 2011-07-06
> 
in that case, I suggest Perl and GTK.

Perl sounds interesting I'll have to look into it.

---

### Post by life in color on 2011-07-06
> 
I'm learning wxPython now and I'm really liking it. I didn't care for Glade, but you don't need it for wx.

> 
I wrote a 4000 line project in wxPython and I found it very easy to use and flexible.
It is definitely an option to consider.

Well, two positive suggestions makes it sound quite good, I will definitely look into it.

---

