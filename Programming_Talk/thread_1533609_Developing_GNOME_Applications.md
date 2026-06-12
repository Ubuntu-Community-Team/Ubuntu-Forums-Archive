---
title: "Developing GNOME Applications"
date: 2010-07-18
forum: Programming Talk
---

### Post by FieldDoc on 2010-07-18
Hi,

I'm new to Ubunutu (having come from OS X) and I'm very impressed. I'm a hobbyist programmer but fairly fluent in Objective-C (and thus C) and some Java.

I have several ideas for applications that I would like to write for the Linux community. I would like them to look 'native' on Ubuntu which I assume means they should be written using GTK+ frameworks? I have been thinking about writing in Java as it would be good to improve my skills in that language and Android apps are written in it to (something I'd like to do at a later date).

How should I go about getting started? I've come from using the only development IDE on the Mac (Xcode). I believe I need to use the java-gnome bindings and I see that NetBeans and Eclipse are popular IDEs on Linux. 

What would people recommend?

Thanks,

FieldDoc

---

### Post by nvteighen on 2010-07-18
> **FieldDoc said:**
> Hi,

I'm new to Ubunutu (having come from OS X) and I'm very impressed. I'm a hobbyist programmer but fairly fluent in Objective-C (and thus C) and some Java.

I have several ideas for applications that I would like to write for the Linux community. I would like them to look 'native' on Ubuntu which I assume means they should be written using GTK+ frameworks? I have been thinking about writing in Java as it would be good to improve my skills in that language and Android apps are written in it to (something I'd like to do at a later date).

How should I go about getting started? I've come from using the only development IDE on the Mac (Xcode). I believe I need to use the java-gnome bindings and I see that NetBeans and Eclipse are popular IDEs on Linux. 

What would people recommend?

Thanks,

FieldDoc

Welcome!

Ok, let's see... In GNU/Linux you'll soon find that usually your issue is that you have too many choices :D

GTK+ is just a GUI toolkit used for GNOME (but not just GNOME... Xfce as well) and will provide your application a native look-and-feel in that particular Desktop Environment. But, what if you want to have a KDE look-and-feel? Well, there's Qt. And then you could use GNUStep (NeXTStep clone) or Motif or Tk or wxWidgets or the Java Swing API (which IIRC, defaults to the native underlying toolkit).

---

### Post by FieldDoc on 2010-07-18
> **nvteighen said:**
> Welcome!
But, what if you want to have a KDE look-and-feel? Well, there's Qt. And then you could use GNUStep (NeXTStep clone) or Motif or Tk or wxWidgets or the Java Swing API (which IIRC, defaults to the native underlying toolkit).

Wow!

Coding OSX apps was relatively easy because of Apple's draconian hold on the UI. One thing I like(d) about developing for OSX was the MVC paradigm. Let's say I want to make a todo app that looks pretty and native in Ubuntu. How easy is it to make it look native for both KDE and GNOME desktop environments? Is it best to just pick one? I detest the Swing look as it just doesn't look quite right on any platform...

---

### Post by kvarley on 2010-07-18
You may want to look at Glade for creating your GUI's.

Eclipse is a good IDE.

Mono for C#

All are available in the USC.

---

### Post by FieldDoc on 2010-07-18
> **kvarley said:**
> You may want to look at Glade for creating your GUI's.

I'm not sure how familiar you are with developing on the Mac but it looks like Glade is a little like Interface Builder? Is it possible to link a Java backend to a Glade-created GUI then? Are there any helpful tutorial/pointer sites to help with this?

Thanks for everyone's help so far.

---

### Post by nvteighen on 2010-07-18
If you use Python, being a dynamical environment, you could have multiple interfaces coded for a single program and being activated depending on what Desktop Environment is being used. Not a trivial task, but it's been done. Other languages just force you to do so... If you wanted to create a dual Qt/GTK+ C++ application (no C... there's no Qt for C), you'd have to link your application to those massive libraries... creating a monster... and I'm not sure whether it'd even compile. 

But usually, one targets to a certain DE, even in languages like Python where the above can be done. But there are practical reasons to do so: when creating an application, it's much easier to consider DEs in GNU/Linux pretty much as "platforms" on their own... Of course, a way to compensate this is and avoid code duplication is to split applications into a common implementation (as a shared library) and then distribute different interfaces that communicate with that library (this is seen in APT as x-common, x-gtk, x-kde... where "x" is some fancy project's name).

Be aware that a GTK+ application will run perfectly on KDE if the libraries are installed... You can run GNUStep stuff on GNOME or KDE if the libraries are there... The issue will be the obvious visual mess and ugliness, but the program's behaivor won't be affected.

There are GUI designers for the most important libraries; usually they create an XML(-like) representation of your GUI which you have to import to your program by using the designer's API. Glade is one for GTK+, QtDesigner is another for Qt... I'm not much of a GUI programmer so I can't tell you how good they are... (and when I do I usually code GUIs by hand because they tend to be rather simple ones).

---

### Post by KdotJ on 2010-07-18
another thing you could do, if you still want to use Swing with Java, is that you can set the LookAndFeel to system (or GTK explicitly). This will give you a pretty good match to GTK. It's not perfect I'll admit, and you have to change the size of the buttons / textfields so they look correct in Ubuntu. 

Just another idea

---

### Post by lkjoel on 2010-07-18
> **FieldDoc said:**
> I'm not sure how familiar you are with developing on the Mac but it looks like Glade is a little like Interface Builder? Is it possible to link a Java backend to a Glade-created GUI then? Are there any helpful tutorial/pointer sites to help with this?

Thanks for everyone's help so far.
Yes, I think it is like the Interface Builder, though I don't have a Mac.
It is a GUI to creating Gui's.

---

### Post by KdotJ on 2010-07-18
If you do choose Java and use the GTK LookAndFeel, Netbeans is a great IDE with a good GUI builder

---

### Post by lkjoel on 2010-07-18
> **FieldDoc said:**
> Wow!

Coding OSX apps was relatively easy because of Apple's draconian hold on the UI. One thing I like(d) about developing for OSX was the MVC paradigm. Let's say I want to make a todo app that looks pretty and native in Ubuntu. How easy is it to make it look native for both KDE and GNOME desktop environments? Is it best to just pick one? I detest the Swing look as it just doesn't look quite right on any platform...
To see what desktop environment the user is running, check the $DESKTOP_SESSION variable.
If you want to see what it outputs, open up a Terminal (Applications->Accessories->Terminal) window, and type in it:
```
echo $DESKTOP_SESSION
```

---

### Post by nvteighen on 2010-07-19
> **lkjoel said:**
> To see what desktop environment the user is running, check the $DESKTOP_SESSION variable.
If you want to see what it outputs, open up a Terminal (Applications->Accessories->Terminal) window, and type in it:
```
echo $DESKTOP_SESSION
```

No, that doesn't work really well... IIRC, that variable is set only by GDM (remember: you could be launching KDE from GDM).

What we did in LaRoza's project can be seen here: [http://bazaar.launchpad.net/~laroza/sysres/sysres/annotate/head:/sysres](http://bazaar.launchpad.net/~laroza/sysres/sysres/annotate/head:/sysres)

Basically, it looks if KDE's kicker (a fundamental KDE component) is being run... if it finds it, it's KDE. If it doesn't, but a X server display is running, we default to GTK+ as it is GNOME or Xfce. If nothing worked, it's a console. Besides that, you could force which interface to use by passing a command line argument.

Not very practical, but after several approaches this one was which worked at best

---

### Post by FieldDoc on 2010-07-19
So many choices!
 
What about Python? I've noticed that Exaile (which I'm loving) is written in Python. I always thought that Python was just a webscript - I didn't realise you could write GUI apps with it. Does this use the PyGTK framework? Are Eclipse and NetBeans good for Python development?

---

### Post by lkjoel on 2010-07-19
> **nvteighen said:**
> No, that doesn't work really well... IIRC, that variable is set only by GDM (remember: you could be launching KDE from GDM).

What we did in LaRoza's project can be seen here: [http://bazaar.launchpad.net/~laroza/sysres/sysres/annotate/head:/sysres]("http://bazaar.launchpad.net/%7Elaroza/sysres/sysres/annotate/head:/sysres")

Basically, it looks if KDE's kicker (a fundamental KDE component) is being run... if it finds it, it's KDE. If it doesn't, but a X server display is running, we default to GTK+ as it is GNOME or Xfce. If nothing worked, it's a console. Besides that, you could force which interface to use by passing a command line argument.

Not very practical, but after several approaches this one was which worked at best
So what I get is that it is nearly impossible to know what DE the user is using right?

---

### Post by mcphargus on 2010-07-19
I'm currently building a CRUD app in python using Glade to develop the interface and sqlalchemy/sqlite for the database backend. You can take a look at the project at [http://launchpad.net/eesu]("http://launchpad.net/eesu")

Mine started as a quickly application, but it's sort of outgrown its quickly surroundings. IMHO, [quickly]("https://wiki.ubuntu.com/Quickly") is probably the fastest way to start building GUI apps in python.

Python supports native ctypes, meaning that a lot of frameworks built on c++ or c have been ported to python. Python has tons of libraries. OpenCV (computer vision, like face recognition) is available, gstreamer provides a framework for media editing/playback from within python (on GTK or otherwise), webkit allows you to integrate html documents and browsing within a GTK application, the list really goes on.

system -> administration -> synaptic package manager, then search for python and you can see a sampling of all the libraries available.

Good luck.

---

### Post by nvteighen on 2010-07-20
> **lkjoel said:**
> So what I get is that it is nearly impossible to know what DE the user is using right?

No, not impossible: that code works. The issue is that there's no API for it... I mean, no DE seems to provide a trivial way to tell you if they're running.

---

### Post by lkjoel on 2010-07-20
I do not understand the least bit of that code.
I am not a python programmer.
Could you explain it to me?
Thanks!

---

### Post by nvteighen on 2010-07-20
> **lkjoel said:**
> I do not understand the least bit of that code.
I am not a python programmer.
Could you explain it to me?
Thanks!

The relevant part starts at line 103. In line 85 starts what you could call the "main" module, which first tries to start the interface by checking what command argument was passed... this isn't of interest for this thread because it worked on demand: if the user wanted a Qt interface, it'd try to load it no matter what (and fail if necessary).

From 103 forward, you'll see an if/elif/else-clause (elif = else if). What it tries first (103-105) is to check if the process for KDE's "kicker" is running. If it is, we consider that as good evidence to think the user is running KDE... therefore, we start the Qt interface with that function call in 105. But, if kicker is not running, but the DISPLAY environment variable is set (by X), then it means that there's an X Window System session open that it isn't KDE... therefore it is any of the GTK+ based/capable DEs (GNOME, Xfce, other minor DEs), so we start the GTK+ interface. If everything fails, we start a text-based interface because it means that we're on a pure GNU/Linux console (not a terminal emulator).

That's it.

---

### Post by lkjoel on 2010-07-20
> **nvteighen said:**
> The relevant part starts at line 103. In line 85 starts what you could call the "main" module, which first tries to start the interface by checking what command argument was passed... this isn't of interest for this thread because it worked on demand: if the user wanted a Qt interface, it'd try to load it no matter what (and fail if necessary).

From 103 forward, you'll see an if/elif/else-clause (elif = else if). What it tries first (103-105) is to check if the process for KDE's "kicker" is running. If it is, we consider that as good evidence to think the user is running KDE... therefore, we start the Qt interface with that function call in 105. But, if kicker is not running, but the DISPLAY environment variable is set (by X), then it means that there's an X Window System session open that it isn't KDE... therefore it is any of the GTK+ based/capable DEs (GNOME, Xfce, other minor DEs), so we start the GTK+ interface. If everything fails, we start a text-based interface because it means that we're on a pure GNU/Linux console (not a terminal emulator).

That's it.
Thanks, but that does more than what I want!
I made a shell script, with the help of that script you gave me.
Check DEtools.tar.gz
And to the OP: DEtools.tar.gz is a tool to find the Desktop Environment.
It uses BASH, and the script you are mostly going to need is showde.

---

### Post by moephan on 2010-07-23
This is easy to answer. You definitely want to use Quickly. This is designed to get you started writing apps. It makes all the choices of technology and tools for you, and integrates into launchpad and such.

```

$sudo apt-get install quickly
$quickly tutorial ubuntu-application

```

have fun!

---

### Post by nvteighen on 2010-07-23
> **moephan said:**
> This is easy to answer. You definitely want to use Quickly. This is designed to get you started writing apps. It makes all the choices of technology and tools for you, and integrates into launchpad and such.

```

$sudo apt-get install quickly
$quickly tutorial ubuntu-application

```

have fun!

There's something really bad about Quickly... It's an Ubuntu-specific thing... Ok, I guess it's good for someone that is learning, but I've stepped into some Launchpad project that uses it and as I'm using Debian, I just can't do much with it... :(

---

