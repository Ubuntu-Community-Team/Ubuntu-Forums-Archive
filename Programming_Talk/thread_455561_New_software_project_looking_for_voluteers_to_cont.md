---
title: "New software project looking for voluteers to contribute"
date: 2007-05-26
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-05-26
Hi 

I have seen in recent times there is a need for a simple GUI system to auto compile source code for applications and was wondering if anyone would like to get involved in developing this app with me.

I'm gonna start developing it on my own but would appreciate and help or advice from the community. 

I have a fair idea how to create a GUI using Qt4 and how to execute xterm commands through it etc, what I lack is ideas on how to determine the compilation methods etc and if the required libraries are installed. So if you know how to do this please post your info or and code you can generate.

The chosen language is C++ as that my first choice, but if you have code that can be interfaced with it please post it along with the way I can include it.

Lets make installing software easy as clicking a button!

Mike

---

### Post by madmetal on 2007-05-26


hello Mike!
although i support such efforts , why dont you preffer making some .debs or packages for programs that are not in the repos?
i think what you want to do it something like klik [http://klik.atekon.de/](http://klik.atekon.de/) or/and autopackage [http://autopackage.org/](http://autopackage.org/)
whats also important for me at this point is new programs bakcported to dapper which is the first LTS version of ubuntu..
;):KS

---

### Post by KIAaze on 2007-05-26
I agree.
Making a .deb file is simply better.

Usually, to install from source, all that is necessary is ./configure, make, make install.
If that doesn't work, a GUI won't make it easier...

However, I would really like to have some app to create .deb packages. :)
I have tried with KDevelop. However it only offers to create an .rpm file, not a .deb.
Does anybody know how to easily create .deb packages?

edit: This autopackage thing looks interesting. :)

---

### Post by Mickeysofine1972 on 2007-05-26
Of course your right, maybe this can become a option available in the program.

A program that can do all these things will be a major boost to the community because it will make it easy for developer as well as users to get the software installed but also make it distributable.

Keep up the suggestions and info, already we have a plan forming!

Mike

---

### Post by Mickeysofine1972 on 2007-05-27
I have created a wiki page for anyone who wants to test or use or even contribute to this project:

[http://ubuntu-utils.wikispaces.com/](http://ubuntu-utils.wikispaces.com/)

This is also the home of the excellent Ubuntu Games Developer Wiki [http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Mike

---

### Post by KIAaze on 2007-05-27
So if I understand you correctly, you want to make a program which allows installation from source while taking care of all the most common compilation problems encountered (especially missing dependency).
Sounds great, but complicated. :)

You might want to check out [checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/"), which also creates .deb packages. ;)

---

### Post by MrHorus on 2007-05-27
> **Mickeysofine1972 said:**
> Hi 

I have seen in recent times there is a need for a simple GUI system to auto compile source code for applications and was wondering if anyone would like to get involved in developing this app with me.


Not with you here.

You mean a continuous build system like Cruise Control or just a GUI for make/configure?

---

### Post by Mickeysofine1972 on 2007-05-27
Here is a list of requirements for the app:

[http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator](http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator)

If we do this right it will get included in a future release of ubuntu.

Mike

---

### Post by u04f061 on 2007-05-27
this is a nice application . actually the thinking is too nice. I highly appreciate this project and for the time being i am busy in preparing my exams , so i can't take active role in this project. the language choosen for this project and GUI library is also the best choice. C++ and Qt4 give the charming look to GUIs this is the main reason i like KDE.

plz start it with full effort. i will be joining you soon

Best Of Luck

---

### Post by Mickeysofine1972 on 2007-05-27
Ok I just posted a very basic gui to start the ball rolling

[http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator](http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator)

This is the very basic window for loading the target zip/gzip etc. If you have any extra code to add please email it to me at [email]hibbert_michael@hotmail.com[/email]

MIke

---

### Post by raja on 2007-05-27
> **KIAaze said:**
> I agree.
However, I would really like to have some app to create .deb packages. :)
I have tried with KDevelop. However it only offers to create an .rpm file, not a .deb.
Does anybody know how to easily create .deb packages?


If you have an existing application to make rpm files, why cant you use alien with it to convert those .rpms to .debs?

---

### Post by u04f061 on 2007-05-27
> **Mickeysofine1972 said:**
> Ok I just posted a very basic gui to start the ball rolling

[http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator](http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator)

This is the very basic window for loading the target zip/gzip etc. If you have any extra code to add please email it to me at [email]hibbert_michael@hotmail.com[/email]

MIke

that is very nice. I would be supporting you soon after my exams. i only know how to run an application within C program. i don't know how to do it in C++ or Qt. do they provide any efficient way of doing this? because c does not as far as i know. please direct me to some useful link for this as well. thanks

---

### Post by ankursethi on 2007-05-28
Why don't you use a scripting language (Perl/Python/Ruby) to create this? Won't it be easier to do it that way, what with all the regex support and easy integration with the command line tools?

---

### Post by ArieT on 2007-05-28
And why do you use QT? Ubuntu is by far the most popular flavor and uses GTK.

---

### Post by Mickeysofine1972 on 2007-05-28
wow lots of questions!

Ok easy ones first:

[http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com) has a QT4 howto.

Second, I did consider using Python but as I don't know enough about Python I wouldnt be able to get the ball rolling, as also the case about GTK.

Is there a designer for GTK? if so I may well at this early stage switch as this was my first goal but was not able to find much info. After all, the goal is not to have to do anything technical to use this app, that would include install extra libs that don't ship with the default Ubuntu.

Mike

---

### Post by u04f061 on 2007-05-28
> Why don't you use a scripting language (Perl/Python/Ruby) to create this? Won't it be easier to do it that way, what with all the regex support and easy integration with the command line tools?

he is creating GUI for novice. why should he use > Perl/Python/Ruby

> And why do you use QT? Ubuntu is by far the most popular flavor and uses GTK.

Qt provides rich facilities than gtk. moreover it is more charming and more beautiful. compare the look of Kubuntu and Ubuntu

---

### Post by ruy_lopez on 2007-05-28
My first thought was Perl/Python, too. The application has to search for headers in order to chase down dependencies. Perl/Python are made for that kind of thing. In fact, CPAN is probably a perfect example of source code dependency chasing.

I'd be interested, but Qt rules me out. There's proprietary issues with Qt.

---

### Post by ankursethi on 2007-05-28
@u04f061
The advanced features are meant for the programmer's use, not the user's.

Apparently there seem to be no legal issues with Qt, but if you use Qt then this app will not be bundled with Ubuntu because Ubuntu uses GNOME which is all GTK. Installing Qt apps will require the Qt libraries. Why do you think Ubuntu doesn't ship with AmaroK and K3B?

---

### Post by christhemonkey on 2007-05-28
There is a GUI designer for GTK it is called Glade, and the propriety issues of Qt were sorted out a (long) while back.

---

### Post by seamless on 2007-05-28
[QUOTE="ruy_lopez"]There's proprietary issues with Qt.[/QUOTE]
How does a GPL licensed toolkit have proprietary issues? It's simply dual licensed much like MySQL. Which does not remove the fact that if you use the GPL version of Qt your application will be GPL and that cannot be changed unless you change the license.

[QUOTE="ankursethi"]if you use Qt then this app will not be bundled with Ubuntu because Ubuntu uses GNOME which is all GTK.[/QUOTE]
If the application is designed correctly with abstraction between the core components and the GUI then making multiple GUIs would be trivial. A GTK+ GUI for Ubuntu and a Qt/KDE GUI for Kubuntu would simply involve porting the GUI code, which would comprise a small amount of overall code. Being that it should be mainly visual elements and not the core functionality creating a new GUI will not be an issue.

---

### Post by pmasiar on 2007-05-28
> **Mickeysofine1972 said:**
> need for a simple GUI system to auto compile source code for applications ...
I have a fair idea how to create a GUI using Qt4 ...
The chosen language is C++ ...

IMNSHO you lack the deep understanding of creating distribution packages, and another red flag: you are not too concerned about this :-) One of hints for it is your selection of implementation language: C++ is one of the *worst* possible languages to for it. Nice GUI is nice - but not all-important. It is lipstick on a pig. There are deeper problems in package installation beyond nice GUI. 

Think about it: You cannot automate something you don't know how to do manually. 

Your C++ GUI skills can be used in some projects of course. Check wordforge or any other game project, there are many to choose from.

Or think about learning other languages: ubuntu developers use Python for packaging for some reason, don't you think so?

---

### Post by Mathiasdm on 2007-05-28
What's the problem with using C++?

It might be a bit older, and slightly harder than Python, but that doesn't mean it won't get the job done.

---

### Post by Mickeysofine1972 on 2007-05-28
> **pmasiar said:**
> IMNSHO you lack the deep understanding of creating distribution packages, and another red flag: you are not too concerned about this :-) One of hints for it is your selection of implementation language: C++ is one of the *worst* possible languages to for it. Nice GUI is nice - but not all-important. It is lipstick on a pig. There are deeper problems in package installation beyond nice GUI. 

Think about it: You cannot automate something you don't know how to do manually. 

Your C++ GUI skills can be used in some projects of course. Check wordforge or any other game project, there are many to choose from.

Or think about learning other languages: ubuntu developers use Python for packaging for some reason, don't you think so?

IMNSHO you seem to have nothing positive to add to this project except personal criticism based on what you assume you know about me.

That said I have seen that there are issues that more constructive posts have raised with using QT on the Gnome desktop and agree that a GTK+ GUI also would be a good idea.

As for Python being very good at the whole dependencies thing, isn't there the possibility that we can create an interface to use some of that code in our C++ app? I have seen this done before with other languages being interfaced and seeing as Python is able to use C/C++ libraries the opposite mus be possible.

Alternatively, I'm not ruling out Python etc, i just know that it takes less time to develope a program if you start with the resources you have instead of jumping in at the deep end with a new language and learn as you go.

I'm very pleased with the interest this has generated and the suggestions, keep em coming. 

Finally, one other post made the point that the QT gui already underway could still be incorporated into Kubuntu instead so I think I will still keep it around and incorporate core functions to it as we go. This is still in the planing stage so to speak so as much positive input as possible is a great thing and opens up the pros and cons of the idea on the OS.

Mike

UPDATE: I have started to look into the GTK+ stuff and have managed to create a basic gui for anyone who wants to try out any experiments. You can get it here:
[http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator](http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator)

Is there anything like Glade and QT Designer for Python?

---

### Post by hod139 on 2007-05-28
Looks like someone has suggested this idea on the Gutsy development forum: [http://ubuntuforums.org/showthread.php?t=455288](http://ubuntuforums.org/showthread.php?t=455288)

---

### Post by raja on 2007-05-28
I have to say I admit with the essence of what pmasiar says. 
It is not clear at all what this project is trying to accomplish. A GUI for 'configure-make-make install' is a waste of time. I also dont think making a GUI first is the right way to do things. I would leave the GUI for the end and instead look at producing some code or pseudocode. Also, have a look at [this thread]("http://ubuntuforums.org/showthread.php?p=2736995#post2736995").

---

### Post by christhemonkey on 2007-05-28
You can use glade with python (in a just as easy if not easier way than C with gtk+ and C++ with gtkmm) just do something like this at the start:
```
#!/usr/env python

import pygtk
pygtk.require("2.0")
import gtk

import gtk.glade

def gui():
        gladefile = "./your.glade"

        wTree = gtk.glade.XML(gladefile)

        window = wTree.get_widget("MainWindow")

if __name__ == "__main__":
        gui()
        gtk.main()

```

Of course you'll have to create a your.glade file in the same directory with glade and this only loads a main window.
But yeah i've forgotten my point... think it was that its simple using pygtk and glade...

---

### Post by winch on 2007-05-28
[GoboLinux]("http://gobolinux.org/") has a intersting approx to the problem.
[http://www.linux.com/article.pl?sid=07/02/09/1817227](http://www.linux.com/article.pl?sid=07/02/09/1817227)

It takes a much simpler approach instead of the very complex task of somehow parsing the build system to to find dependancies.

---

### Post by Mickeysofine1972 on 2007-05-28
First of all I would like to say Hi to hod ... welcome back its great to see you still read this forum ;-)

Raja, you seem to be a pessimist, and maybe your a bit afraid i might succeed and steal the glory? if its not clear dude try reading the posts and the wiki. I read the thread you posted and saw only the post that suites your 'nay sayer' position. Please can we have some serious and more sensible suggestions than its a 'waiste of time'. Is that what the Ubuntu team say when mark gives them a goal of making Ubuntu a real competitor to the likes of windows?

lol. seriously though, we shall see in the end just as we saw with the ubuntu games developers wiki, which has a great beginners resource for developers and beginners alike, (some people said that was a waiste of time too XD [http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com))

Time will tell if I'm wrong, and I have time to make it right lol

Keep up the Ubuntu Spirit guys!

Mike

---

### Post by Mickeysofine1972 on 2007-05-29
> **christhemonkey said:**
> You can use glade with python (in a just as easy if not easier way than C with gtk+ and C++ with gtkmm) just do something like this at the start:
```
#!/usr/env python

import pygtk
pygtk.require("2.0")
import gtk

import gtk.glade

def gui():
        gladefile = "./your.glade"

        wTree = gtk.glade.XML(gladefile)

        window = wTree.get_widget("MainWindow")

if __name__ == "__main__":
        gui()
        gtk.main()

```

Of course you'll have to create a your.glade file in the same directory with glade and this only loads a main window.
But yeah i've forgotten my point... think it was that its simple using pygtk and glade...

Thanks for the info, this seems to be a great starting point for a python version too.

I'm in the process of generating a script that will use this method. 

Mike

---

### Post by KIAaze on 2007-05-29
I know how to create GTK+ apps.
It's actually pretty easy with Anjuta+Glade.
The only thing I still have to learn is how to integrate it correctly with C++.
(The Anjuta+Glade combo works well with C code (gtk-2.0 app), but less well with C++ (gtkmm app)).

It is of course possible to just use Glade to generate the .glade file and then use with any other IDE or without IDE to create programs.

About QT vs GTK:
Having tried both Gnome and KDE, I must say that I was usually more impressed by apps on KDE. :)
Not because of the look, but also because of a lot of nice functionalities like the bottom/left bars.
Amarok for example, is one of the greatest KDE applications I have seen. :)

Another solution would be WXwidgets, which apparently adapts to the desktop environment's look.
Unfortunately, I know neither QT or wxwidgets for now... :/

> **raja said:**
> If you have an existing application to make rpm files, why cant you use alien with it to convert those .rpms to .debs?

Yes, I think that's what I will be doing. ^^
But why isn't there any .deb creation support in most IDEs?
What do the developers usually use to create them? The command line?

---

### Post by ankursethi on 2007-05-29
Can't the dependencies be found out using the makefile and the error messages that "make" generates (if any)? I really don't know enough about this stuff to comment on it, though.

BTW, first make a command line back end for the task. It could just be invoked (like make) in a directory and produce the DEB. Then you can write a GUI front end in Qt for Kubuntu and somebody else can do it in GTK+ for Ubuntu. If you provide proper error messages and everything, it would also make it easy for the backend to interface with frontends in other languages.

---

### Post by Mickeysofine1972 on 2007-05-29
I agree,

I've been looking at checkinstall andits looking good so far, thats for the generating a deb option.

As for make/configure stuff I know that QT4 has a QProcess object that can execute a command like 'xterm -e make' which make xterm execute the make in the current path. It seems to have functions to read in stdout and stderr too so that could be parsed if need be.

I'm not sure how this is done in GTK+ or Python but if you do have and idea please post it.

Mike

---

### Post by KIAaze on 2007-05-29
The [system()]("http://www.cppreference.com/stdother/system.html") function does this in C/C++.
It's not recommended to use it but it works.

Here's an [example]("http://www.thescripts.com/forum/thread62897.html") and here's general info about [system calls]("http://en.wikipedia.org/wiki/System_call").

---

### Post by Mickeysofine1972 on 2007-05-29
> **KIAaze said:**
> The [system()]("http://www.cppreference.com/stdother/system.html") function does this in C/C++.
It's not recommended to use it but it works.

Here's an [example]("http://www.thescripts.com/forum/thread62897.html") and here's general info about [system calls]("http://en.wikipedia.org/wiki/System_call").

Thanks for the info, it lead me to look a bit further and it seems that GLib is the library to use in the case of GTK+ stuff. Apparently it has a Spawn process function that does the same but in a more stable way than the system function. Thanks for the lead

It does indeed look like a Python script would be the best choice to deploy on the Gnome and KDE desktops as this would get rid of a lot of code that doesn't need to be written.

Mike

---

### Post by seamless on 2007-05-29
> **KIAaze said:**
> 
Another solution would be WXwidgets, which apparently adapts to the desktop environment's look.
wxWidgets is a wrapper to the native toolkit used by the support platform. So on Windows it will use the win32 widgets, OS X it uses Coca and on Linux it uses GTK+. So writing it in wxWidgets won't do much good in regard to look and feel between Gnome and KDE because in KDE it will still be GTK. The only place wxWidgets really shines is in cross platform applications. It doesn't do anything cross desktop environment on the same platform.

---

### Post by Mickeysofine1972 on 2007-05-29
> **seamless said:**
> wxWidgets is a wrapper to the native toolkit used by the support platform. So on Windows it will use the win32 widgets, OS X it uses Coca and on Linux it uses GTK+. So writing it in wxWidgets won't do much good in regard to look and feel between Gnome and KDE because in KDE it will still be GTK. The only place wxWidgets really shines is in cross platform applications. It doesn't do anything cross desktop environment on the same platform.

Good point

So what we need is a tool kit that will go across both Gnome & KDE. Or a Python module that runs one or the other(GTK+ and QT) depending on the desktop. 

Is this possible?

Mike

---

### Post by KIAaze on 2007-05-29
I would say it's simply not necessary.
If a QT version and a GTK version are available, people can just choose which one is right for them (or it will taken care of by the ubuntu/kubuntu people).

[SIZE="1"]
By the way, I have been trying to create a QT app by following your tutorial on the ubuntu games dev site.
However, I get the following errors:
> $make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o main.o main.cpp
In file included from main.cpp:2:
MyGUI.h:2:23: error: QMainWindow: No such file or directory
MyGUI.h:3:19: error: QWidget: No such file or directory
MyGUI.h:6: error: expected class-name before &#8216;{&#8217; token
MyGUI.h:7: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
MyGUI.h:9: error: expected &#8216;;&#8217; before &#8216;public&#8217;
MyGUI.h:12: error: &#8216;Ui&#8217; has not been declared
MyGUI.h:12: error: ISO C++ forbids declaration of &#8216;MainWindow&#8217; with no type
MyGUI.h:12: error: expected &#8216;;&#8217; before &#8216;ui&#8217;
MyGUI.h:13: error: expected `:' before &#8216;slots&#8217;
MyGUI.h:14: error: expected primary-expression before &#8216;void&#8217;
MyGUI.h:14: error: ISO C++ forbids declaration of &#8216;slots&#8217; with no type
MyGUI.h:14: error: expected &#8216;;&#8217; before &#8216;void&#8217;
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:6: error: &#8216;QApplication&#8217; was not declared in this scope
main.cpp:6: error: expected `;' before &#8216;app&#8217;
main.cpp:10: error: &#8216;class MyGUI&#8217; has no member named &#8216;show&#8217;
main.cpp:12: error: &#8216;app&#8217; was not declared in this scope
main.cpp: At global scope:
main.cpp:4: warning: unused parameter &#8216;argc&#8217;
main.cpp:4: warning: unused parameter &#8216;argv&#8217;
make: *** [main.o] Error 1

Where do I get the headers QMainWindow.h and QWidget.h if I use Ubuntu(gnome)?
[/SIZE]

---

### Post by FuriousLettuce on 2007-05-29
Please please use a scripting language rather than something like C/C++ for the actual work - they just really aren't suited to this kind of thing. Most scripting languages have advanced text-processing capabilities (Perl being the king by repute), but python's probably your best bet.

As someone mentioned before in the thread, the first thing to do in an properly modular application is to first write the functions that you will need. The GUI can be created completely seperately - this will make it easier to port to different toolkits if you do want it to be both QT and GTK enabled (don't forget that GTK and QT will run on both GNOME and KDE). For example, you might write the function 'installSoftware(install_script)' which just handles the actual installation and returns a meaningful value on completion - this way it can be run from the command line if you fancy a quick make install alternative, and it can be run through the GUI with full support.

Many a good project has gone awry due to priorities being in the wrong place - don't let this be one of them. Pretty GUI's are secondary to functionality!

---

### Post by Mickeysofine1972 on 2007-05-29
> **FuriousLettuce said:**
> Please please use a scripting language rather than something like C/C++ for the actual work - they just really aren't suited to this kind of thing. Most scripting languages have advanced text-processing capabilities (Perl being the king by repute), but python's probably your best bet.

As someone mentioned before in the thread, the first thing to do in an properly modular application is to first write the functions that you will need. The GUI can be created completely seperately - this will make it easier to port to different toolkits if you do want it to be both QT and GTK enabled (don't forget that GTK and QT will run on both GNOME and KDE). For example, you might write the function 'installSoftware(install_script)' which just handles the actual installation and returns a meaningful value on completion - this way it can be run from the command line if you fancy a quick make install alternative, and it can be run through the GUI with full support.

Many a good project has gone awry due to priorities being in the wrong place - don't let this be one of them. Pretty GUI's are secondary to functionality!

Ok I'm gonna nip this in the bud, this is an app for beginners who want to install source packages and create deb to have a backup for possible redistribution or backup later .

Before you go all 'commandline' on me you should read the thread. I have already said in earlier posts that the chosen language will indeed be python for the sake of that fact that Its core functionality will be transferable to either gui.

I'm not going to code a command line app as its already there. remember 'make' and 'configure' and 'checkinstall'? the whole point is that there are commandline utils that do this but nothing for the new user who just wants to compile and install an app that would normally get used more often if the software writers had half a clue what normal 'users' need.

-= RANT FINISHED =-

Really this is just the type of nerdy crap that we need to step over and get to the meat of the matter that is ubuntu needs a new app to make it accessible to non-coders so they can get the kewl apps that only exsist in source format.

Mike

---

### Post by seamless on 2007-05-29
> **"Mickeysofine1972"]Really this is just the type of nerdy crap that we need to step over[/QUOTE]
Mike, you have missed the point of what was said. The point is proper application design in order to avoid redundant work and code. One way is though the use of a command line tool that the GUI calls. Another is through the use of shared libraries or in the case of python, modules. The command line tool, the shared library or the module (which every way you go) would be the one doing the actual work with the GUI an interface to call the needed functionality. In this manner you would have one core and a GUI interface with minimal glue code binding the two together. This is a approach and will made updates to the core functionality easier as well as provide a way for others to take advantage of the core's capabilities.

[QUOTE="Mickeysofine1972"]I'm not going to code a command line app as its already there. remember 'make' and 'configure' and 'checkinstall'?[/QUOTE]
Two things about this. Your proposed application does more than this as it also handles dependences. Also checkinstall generates non-standard debs that &#8220 said:**
> So what we need is a tool kit that will go across both Gnome & KDE. Or a Python module that runs one or the other(GTK+ and QT) depending on the desktop. Is this possible?
No. Like I said, you will need to use a MVC pattern for this application to work with multiple tool kits as you intend. Since you want to use Python, you should thus put all of the core code into a module and code the GUI around the model. This will allow you to easily and quickly add GUIs (even command line ones) because really the only code changing will be the GUI code itself and not any code for the core functionality.

---

### Post by FuriousLettuce on 2007-05-29
EDIT: This comment was a reply to Mike - seamless posted whilst I was writing this, and wrote must of what I've written, just must more succinctly!

No, you misunderstand, I'm not saying that you should make simply a replacement for make etc. You mentioned that you were thinking of making it available with both a QT and a GTK front end. The only way to make it toolkit-independent is to seperate the functionality from the user interface. However, any functions you write in python are automatically available via the command line. I'm not saying that you should develop it with the aim for it to be a command line app - as you say, they already exist. However, it's a very small extension to make a command-line interface to already available functions - I'll happily do it if you ever need it. The command line functionality could really help in some cases - for example, some people prefer to do things via the command line, and even though make already exists, if the functionality that this project promises is available, it makes sense to use it even over make - automatic dependency resolution makes it a very useful app! [Sorry for the run-on sentence.] 

To reiterate, I'm not suggesting that you aim for it to be a command line app. Most big apps are written with the functionality tested first, and the GUI written on top of the functionality but abstracted from the functionality itself (that's why it's a "front-end"). I know that my argument is a bit all over the place, but the basic idea is that the functionality ought to be written above and beyond the GUI, with the GUI coming after the basic functionality is in place. As I said in the first post, 'pretty GUI's are secondary to functionality' - but as soon as you have the functionality, make the GUI as pretty as you can!

---

### Post by pmasiar on 2007-05-29
> **Mickeysofine1972 said:**
> Ok I'm gonna nip this in the bud, ...

Really this is just the type of nerdy crap that we need to step over 


Just two meta-comments for you, really do contemplate about that:

1) you cannot automate something what you have no idea how to do manually. This is *not* a simple problem, otherwise would be solved long time ago. And GUI is the simplest part of it.
2) attitude is *not* a substitute for competence. It is funny how you rant against good advice from more experienced developers.
3) It is not called "pessimist". It is "realist". 10 years of experience does not mean anything only to someone lacking 10 years of experience.

Summary: you'll need to learn *a lot* before you will be ready to tackle this one. By time you learn what you have to, you will be yourself giving such "nerdy" advice you reject with such attitude now... :-)

Happy learning!

---

### Post by ankursethi on 2007-05-30
Looks like Mickey is getting annoyed, what with all of us beating around the bush which, incidentally, happens to be *his* bush.

All that had to be said has been said. Now get coding!

---

### Post by Mickeysofine1972 on 2007-05-30
> **ankursethi said:**
> Looks like Mickey is getting annoyed, what with all of us beating around the bush which, incidentally, happens to be *his* bush.

All that had to be said has been said. Now get coding!

Lol, First an appology to FuriousLettuce, After yours and others clarification I now see clearly that you are of course right. Infact in a strange way we are or were saying the same thing but  in different ways lol, so I am sorry. Actually, That rant should have gone to pmasiar whom has patronised the project from the start. Yes I did just say that pmasiar. Although, on second thoughts you may just be trying to recommend yourself in some veiled way ;) 

That being said, I think that its is indeed time to get coding, and I will post progress in here and the wiki.

Thanks for all the help and advice guys I think this will be a major advancement for the OS and you have all contributed so much.

Mike

---

### Post by Mickeysofine1972 on 2007-05-30
> **pmasiar said:**
> Just two meta-comments for you, really do contemplate about that:

1) you cannot automate something what you have no idea how to do manually. This is *not* a simple problem, otherwise would be solved long time ago. And GUI is the simplest part of it.
2) attitude is *not* a substitute for competence. It is funny how you rant against good advice from more experienced developers.
3) It is not called "pessimist". It is "realist". 10 years of experience does not mean anything only to someone lacking 10 years of experience.

Summary: you'll need to learn *a lot* before you will be ready to tackle this one. By time you learn what you have to, you will be yourself giving such "nerdy" advice you reject with such attitude now... :-)

Happy learning!

Shush

---

### Post by Mickeysofine1972 on 2007-05-30
Ok after an hours  reading how to do Python I've come up with a basic python package idea that I'm sure will get the ball rolling.

It doesn't contain any __main__ yet but it does begin to broach the core functionality of the program.

I will start adding in more code as I research how my ideas get done in Python. and also a __main__ so that tests can be done on the 'commandline' ,(never gonna live that down lol).

The code is here [http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator](http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator)

Mike

---

### Post by pmasiar on 2007-05-30
> **Mickeysofine1972 said:**
> Shush

very curious way to apologise indeed.

All attitude and no code.

---

### Post by Mickeysofine1972 on 2007-05-30
> **pmasiar said:**
> very curious way to apologise indeed.

All attitude and no code.

You still not reading posts from this thread?

lol the code is on the wiki now shush! lmao 

[http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator](http://ubuntu-utils.wikispaces.com/A+GUI+Source+Package+Creator)

Mike :D

BTW now contains a test program and its ....... waite for it! ......... commandline! :-O

But not for long! Muahahahahahahahaa!

---

### Post by raja on 2007-05-30
> **Mickeysofine1972 said:**
> 
Raja, you seem to be a pessimist, and maybe your a bit afraid i might succeed and steal the glory? 

Boy ! You sure do have a lot of growing up to do. Good to see some 'code' up there, though when I checked it out, it isnt any code really - still no hint of what the idea is.

And before you rant about the command line, I wish you look more closely at some Unix applications. Maybe read 'The Art of Unix Programming' by Eric Raymond.

---

### Post by Mickeysofine1972 on 2007-05-30
> **raja said:**
> Boy ! You sure do have a lot of growing up to do. Good to see some 'code' up there, though when I checked it out, it isnt any code really - still no hint of what the idea is.

And before you rant about the command line, I wish you look more closely at some Unix applications. Maybe read 'The Art of Unix Programming' by Eric Raymond.

I will 'grow up' when you stop taking yourself so seriously lol

Yes there isn't a great deal of code your right but will change in time and maybe if you and certain others might like to get involved instead of being a bunch of 'nay sayers' then it might get coded faster.

But looks like I will get all the glory and you will have to look like a ninny lmao :-P

Mike

---

### Post by u04f061 on 2007-06-02
> 
Boy ! You sure do have a lot of growing up to do. Good to see some 'code' up there, though when I checked it out, it isnt any code really - still no hint of what the idea is.

please shut up now Raja. this is a constructive effort and let the volunteers work

---

### Post by pmasiar on 2007-06-02
Yes, let them work.

Everybody is free to do what they want in own free time, but ... to participate in a project where principal developer has Mickey's attitude to any (even constructive and valid) critique? Not interested, thank you.

---

### Post by samjh on 2007-06-02
> 1.  Create a GUI using a GUI system that doesn't need to be installed, or can be easily installed by a new user.Fantastic idea. :)  But what GUI system doesn't need to be installed?  Using Python will require the user the install pyGTK.  The only GUI applications that do not require a user to install a GUI system on Ubuntu is a pure C/C++ program using GTK+.

 > 2. Create code that can qualify the different compilation methods that a source package uses, 'configure' or 'make' etc.It would be very complicated, but interesting.  I have no idea how this could be achieved, though.

>  3. Create code that can read the library dependencies and install them to ensure code can compile first time.One could potentially derive this from various config and make files in the source package.  The problem will be the actually finding and installation of the dependencies.  You will need to translate the dependencies specified in the source package with the package files in the Ubuntu repositories, which is not always intuitive.  Some dependencies require specifying parameters when running ./config in Ubuntu, such as libX11.  Matching dependencies can be a real slog for large  and complex source packages.

>  4. Create code that will spawn the compiler. 'make' etc.Easy if the compiler and make system is gcc and standard make.  Will you also extend support to other build methods like ant, scons, etc.?

>  5. Create code that makes a .deb package out of the installed application so it can be backed up or redistributed.Creating .deb packages is difficult and long.  But I lack knowledge in this matter.  What documentation I have read about it isn't encouraging.

Overall, I think this idea could be beneficial.  You should keep at it.  I will help when I can find spare time, as this is the sort of thing I wish I had when first starting out on Linux.

---

### Post by raja on 2007-06-02
> **u04f061 said:**
> please shut up now Raja. this is a constructive effort and let the volunteers work

I dont know if you would still say that if you read this thread from the beginning. Any effort from any of us to provide constructive input has been criticized as being an attempt to steal someone's glory. Please dont quote me before reading what that was in response to.

---

### Post by WW on 2007-06-03
I would recommend choosing a half dozen or so "case studies" to start.  For example, here are a few programs that people have asked about in the forums:

[xrdp]("http://xrdp.sourceforge.net/")
[Gnofract4D]("http://gnofract4d.sourceforge.net/")
[minicom]("http://alioth.debian.org/projects/minicom/") (This is available in the repositories, but someone running dapper might want to install the latest version.)

Try installing them "by hand", and keep track of what you had to do.  Then work on how the process could be automated.

---

### Post by u04f061 on 2007-06-03
> I dont know if you would still say that if you read this thread from the beginning. Any effort from any of us to provide constructive input has been criticized as being an attempt to steal someone's glory. Please dont quote me before reading what that was in response to.

if u have read this thread from the beginning then you would  come to know that i remained with it from the beginning and not taking part in its development only because i am busy in exams.

however for all those interested in developing this softwares , GEDA a tool for electrical engineers comes with iso image from it page[http://www.geda.seul.org/]("http://www.geda.seul.org/")
it has a GUI tool which only installs and builts its own package and checks dependencies.

---

### Post by jorgerosa on 2007-06-03
**Mickeysofine1972:** (...)"Lets make installing software easy as clicking a button!"(...) - UAU! That is really a good idea! I dont know how difficult it could be, but going in that direction is a good thing!

**pmasiar:** (...)"Not interested, thank you."(...) - You NEVER are interested in others projects, dont you? Start your own, and make something useful*snip*

Ei, **Mickeysofine1972**, i noticed that you are a **C++** coder, and i know that u are busy at your own project, but, if u can and have some free extra time, can u help us here in [iteam project]("http://ubuntuforums.org/showthread.php?t=427011") ? Thx in advance. Good luck to your own project! (Just never quit!) Cya.

---

### Post by pmasiar on 2007-06-03
> **jorgerosa said:**
> You NEVER are interested in others projects, dont you? Start your own

jorgerosa, NEVER is a big word you should not throw lightly - of course unless you are used to waste words away without thinking :-)

Check project in my sig. Where is something *you* contributed?

I have no problems with supporting good projects with some chance of success. When I see "bad" project, I see as professional courtesy to pinpoint possible future problems, so they can be handled and avoided, if possible. It would *much* simpler for me just ignore project than waste time on any response, don't you think so?

---

### Post by Mickeysofine1972 on 2007-06-03
LOL

I go away for a few days and all hell lets loose!

Firstly, pmaiser & Raja, If you guys spent as much time coding as you go trying to come across as the authority on everything then maybe I would listen to you. 

As it is you haughty and self righteous 'airs' put me off and so it seems it has the same effect on others. 

To be honest, I have closed my ears to you both, the reason can be found if you re-read your posts. All you have said is that this is way to hard for someone like me. You know absolutley nothing about me. But let me bring you upto speed.

I am a software developer of about 14 years on various platforms but not until recently, Linux. I have more than a handful of programming languages under my belt including machine code/C/C++/VB/Pascal........and the list goes on and now includes Python (three guesses why?). I also have been a teacher of programming for about 6 years in various educational facilities around the UK.  2 of those years I spent making games, 12 of those I spent programming websites and databases and what ever the hell goes in between.

So when your quite finished trying to scare me off from this so called 'very complex' problem you might like to take you head out of you backsides and start to off some help.

If YOU check you posts you will see that all you have said is that this is too hard and I should go and read up on this and maybe try when I'm not such of a noob. 

three words..... THE HACKERS ETHIC

if you don't know what that is then go Google it, in short it says my opinion as a programmer, however small or seemingly meaningless, is as valid as yours.

so, why haven't I said this before? .... because I shouldn't have too, my views as a noobie or not should be respected by you.... but are not..... Do you work for MICROSOFT?

MIke

BTW I'm coding and I'm getting somewhere.... are you?

---

### Post by winch on 2007-06-03
All people have to go off is your very broad overview, There really isn't much to discuss other than to say it's a pretty hard problem.

As the saying goes, garbage in garbage out. If you went into more detail there would be more to discuss.
For example with projects that use GNU autotools how will you work out the dependencies? Will you parse the configure script and try to determine what it is doing? Or perhaps run it, trick it into thinking all dependencies are met and keep track of what it looks for? Or perhaps a huge database of what all the different autoconf macros produce so you can match bits of the configure script against them.
Any details at all on how it could work would give people something to discuss and perhaps even get them interested.

---

### Post by JT673 on 2007-06-03
That's kind of interesting.  This project will appeal to the developers and uber-geeks who want their software compiled on their machine for maximum performance.

However, that's...kind of already a routine with "gksudo bash;./configure;make;make install;exit".  Anyone with enough ruby-tk/pyQT experience can make this a few hours, file lock, trap and all.

So...anyone want to attempt this?

---

### Post by WW on 2007-06-03
> **JT673 said:**
> 
However, that's...kind of already a routine with "gksudo bash;./configure;make;make install;exit".  Anyone with enough ruby-tk/pyQT experience can make this a few hours, file lock, trap and all.


I think you miss an important point: what happens when ./configure fails?  How do you *automate* the tracking down and installing of the missing pieces that caused ./configure to fail?

---

### Post by JT673 on 2007-06-03
Dependencies are another thing...They could attach a file along with the .tar file that specify the dependencies...That's basically how .deb and .rpm work...

Now, if you really want it to install without the developers specify the dependencies, sure, we can put in an AI that scans the configure file, and a database that link to the libraries (Ruby on Rails time!).  But that would take months...

---

### Post by Mickeysofine1972 on 2007-06-04
> **JT673 said:**
> Dependencies are another thing...They could attach a file along with the .tar file that specify the dependencies...That's basically how .deb and .rpm work...

Now, if you really want it to install without the developers specify the dependencies, sure, we can put in an AI that scans the configure file, and a database that link to the libraries (Ruby on Rails time!).  But that would take months...

Great now we are starting to think around the problem. agreed this may take months of work. but of course this is going to be a seriously great application.

My first ideas where that we could parse the makefile and maybe use apt-gets search features to see if we had the relevant libraries installed and what packages they are in if they aren't. I noticed that apt now gives advice on the terminal when you try to install something and it doesn't have all its dependencies. Maybe this is a usable feature?

Also, I was thinking that we could link tat functionality to a function that parses output from ./configure to install dependencies for that too. This is all just brain storming really and I have no solid ideas at the moment.

I have been looking at tseliots envy package as it seems to already do some of the stuff we want and Alberto has kindly provided some excellent information to me about making debs.

Here's a link to a video on creating debs:

[http://showmedo.com/videos/video?name=linuxJensMakingDeb&fromSeriesID=37](http://showmedo.com/videos/video?name=linuxJensMakingDeb&fromSeriesID=37)

Mike

---

### Post by christhemonkey on 2007-06-05
Can i just add, for normal GNU make programs with a ./configure you can just use this bash script to get all -dev packages that need to be installed.
```
       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done

```

Its from here:
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

Enjoy!

---

### Post by Mickeysofine1972 on 2007-06-05
Excellent! that one less think to code! Do you think you could make that a Python function?

Mike

---

### Post by FuriousLettuce on 2007-06-05
Why bother? You could just call the script from python. Any remotely recent install of *nix will have bash installed, especially if they have python installed.

---

### Post by Mickeysofine1972 on 2007-06-05
True 

Suppose it wouldn't hurt really as we would probably have to tun those commands through a shell anyway

BTW, I just created my first DEB file and if worked like a charm! now all I have to do is turn my experiences into aa script.

Mike

---

### Post by christhemonkey on 2007-06-05
Can i ask if you made the deb through checkinstall or through proper dh_make etc methods?

---

### Post by Mickeysofine1972 on 2007-06-06
Hey

I used the dh method but I have also used checkinstall in the but I wanted to do it this way as I have heard, (but not sure why), that this generates a ubuntu compliant deb.

I followed the excellent video from [www.showmedo.com](www.showmedo.com) and it worked first time too :-D

Mike

---

### Post by Mickeysofine1972 on 2007-06-18
Well its been some time since i posted in this thread but i have news!

I have posted a new set of code on the wiki ([http://ubuntu-utils.wikispaces.com](http://ubuntu-utils.wikispaces.com)) and its geting nearer to being usable from the command line!

Next stop is creating a GUI that uses all the functions in the package to do the same but in a more visual type way.

Mike

---

### Post by leibowitz on 2007-06-18
Ok, so the whole point is to install software from source code, in an efficient and easy manner.

I don't know how to check dependency and install each needed package could be done (mainly because if you need a package that isn't in the main/universe than you need to download another source package and compile stuff, which go into a deep recursive problem)

But AFAIK, the best thing you can do is to automate the process of ./configure, make, and make install.

And if something fail during configure (which is the most important part of failure detection) then just say what package is needed. This is supposing that the configure script is well writed by the developers of the project, which is not always true.

See how it's hard ?

Now check what have already been done, and try to improve it.

XFCE Installer is a tool created by Xfce developers a while ago, that is very similar to what I just explained.
[http://www.os-cillation.de/index.php?id=30&L=5](http://www.os-cillation.de/index.php?id=30&L=5)

I already used it, and it's far from perfect. But I don't think it's wise to start from scratch again, unless you have some very good points against it.


Note: apparently there was another project born from XFCE installer, but it never really started (I really never heard of it before) It's called InstallIt
[http://installit.xfce.org/](http://installit.xfce.org/)

So I would suggest you discuss with Benedikt Meurer, he seems to be the original creator of the XFCE Installer. And discuss where the project is today, and where you want it to be tomorrow.
[http://www.foo-projects.org/~benny/](http://www.foo-projects.org/~benny/)

Just my two cents.

---

### Post by Mickeysofine1972 on 2007-06-19
And a very good two cents too!

Thanks for the info and leads thats most i can hope for from anyone! and its very much appreciated.

Its true that the configure errors are the main show stopper here and I have been looking into ways to find out ways to search for sources of the dependencies. The script mention earlier in this thread seems to work for some cases but not others but I still think its going in the right direction.

Anymore help or leads are gratefully accepted. in the mean time i think I will indeed have a chat with the guy you mentioned.

Mike

---

### Post by vexorian on 2007-06-19
personally I think source packages should stay like this, being hard to be installed by newbies and all.

The thing is that a project acquires binary package distribution once it is polished and stable, otherwise it is just starting or the programmer is lazy, both things make letting anyone install them with a click a very bad  thing.

BUT, I would like to say that I have already seen something like this project go live already, I remember a linux.com article describing it.

--
If you ask, autoconf, automake, ./configure and make are just broken, they are way too hard to learn and painful to use, If you really want to make this better (And easier to code I would say) I think that changing the very way source distibutions work is a good idea. It would then be easier to make an interface for it.

--
Actually I think I found it: [http://www.gnu.org/software/sourceinstall/sourceinstall.html](http://www.gnu.org/software/sourceinstall/sourceinstall.html)

don't have the time to download and test and verify that it is the project I remember, but sounds good?

---

### Post by KIAaze on 2007-06-19
And then there are new methods of Makefile creation that are appearing like cmake (KDE4.0 switched to cmake for example)...

---

### Post by Mickeysofine1972 on 2007-06-19
Yeah that GNU source installer does look pretty much like what I'm trying to do.

But still it been interesting looking into Python as I had to learn it to do this project. Another plus is that it helped me get through a week of food poisoning lol!

I think I will continue anyway as its always good to offer more choice and maybe along the way I might learn some more.

Thanks for all the help so far guys!

Mike

---

