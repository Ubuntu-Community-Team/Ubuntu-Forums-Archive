---
title: "Cross-platform programming"
date: 2009-05-04
forum: Programming Talk
---

### Post by Stavro on 2009-05-04
Hi All,

I&#8217;m quite new to Ubuntu but am a hobby developer so am quite confident with computers. I&#8217;m very interested in creating a cross-platform application that will utilise standard window widgets and OpenGL. Is this easily achieved? I would like pointers as to what would be the best language and IDE for development on Ubuntu.

Thank you in advance.

---

### Post by myrtle1908 on 2009-05-05
IMO your best bet for ease of portability is Java.  Couple this with the NetBeans IDE and the OpenGL pack and you're away.


Java bindings for OpenGL (JOGL) - [https://jogl.dev.java.net/](https://jogl.dev.java.net/)

NetBeans - [http://www.netbeans.org/downloads/](http://www.netbeans.org/downloads/)

NetBeans Pack for OpenGL Java Development - [https://netbeans-opengl-pack.dev.java.net/](https://netbeans-opengl-pack.dev.java.net/)

---

### Post by Zugzwang on 2009-05-05
There are multiple possibilities to do so. The last poster mentioned Java, which will however not utilise the "standard" widgets (but instead paint its own - you can however choose how they look like). But that shouldn't be a problem. It has very good IDE support (personally I only know Netbeans that can be of enormous help).

You can also program in C and/or C++, for which you have a couple of alternative frameworks you can use, for example Gtk, WxWidgets and QT. Personally I would suggest one of the latter two (need C++), but that's really just personal preference. Often beginners and even people that can program at intermediate levels in other languages are advised against C++ as it has some traps included.

Scripting languages might be interesting for you as well as most of them are also cross-platform, for example Python might be an option. It is also often reported as good for beginners as the learning curve is quite good. People who know other languages can dive into it very quick.

---

### Post by Stavro on 2009-05-09
Thanks for the replies, it&#8217;s most appreciated. I think JAVA will probably be a little bit too slow for the work that I would like to achieve, which is highly mathematical and needs to be executed quickly. I understand JAVA is a very high level interpreter like language. Please correct me if I&#8217;m wrong. I like the sound of GTK+ a lot combined with C++ or C and I was wondering if anyone can recommend a good IDE if one exists that also features a form designer for easily creating widgets. The ability to develop both on Windows and Ubuntu would be really useful.

---

### Post by merlinblack on 2009-05-09
There are a few IDEs, Anjuta is one.  Personally I use a combination of vim, gedit, and nemiver (a stand alone debugger using gdb as a backend) with makefiles in my C++ projects.  wxWidgets is pretty good, and you will feel at home with it if you have done any MFC windows programming.  It also has a python binding, handy for bashing out a prototype, that you might later do in C++ (or leave it as python). :) wxWidgets has a open gl canvas class too.

As for OpenGL, there are bindings for just about any language.  For C/C++ grab libglew, the openGL extension wrangler, very handy, and freeglut perhaps.

Depending on your requirements, and experiance you may find Ogre3d.org an intresting place to visit.  The source code is rather large though (not that you have to read it all) :P

Happy coding! And make sure you wind those vertices in the right order :P.

---

### Post by SKLP on 2009-05-09
> **Stavro said:**
>  I think JAVA will probably be a little bit too slow for the work that I would like to achieve, which is highly mathematical and needs to be executed quickly. I understand JAVA is a very high level interpreter like language. Please correct me if I’m wrong.Java is not really a VERY high level language, and it's usually not interpreted, rather it is JITed (just-in-time compiled). I believe Java is one of the best performing languages (and it's a LOT faster than dynamic languages, e.g. python).
I personally prefer C# though.

---

### Post by HavocXphere on 2009-05-09
> **Stavro said:**
> utilise standard window widgets
That is a bit of an issue because there is no "standard" on the widget
front...every OS does it in its own way.

OpenGL is fairly standard across the platforms, so if you do pretty much
everything in OGL then it should look the same everywhere. I don't think you'll get around some customizing though for each OS....specifically the window & OGL initialization.

Not sure whether OGL and scripting languages work well together. I haven't tried that combo, but in my experience OGL is fairly sensitive on the speed front...especially with the core rendering loop.

I'd be inclined to go with C++...and make everything very modular so that any porting effort is clearly restricted to an interface layer.

---

### Post by hessiess on 2009-05-09
Few options for graphics programming, if you like low-level graphics programming(doing everything manually) you could use OpenGL+SDL, If you want a higher leavel enviroment use one of the open-source graphics engines like IrrLicht. For normal GUI programming you can use GTK, QT, or WXWigits. As for a language, C or C++ is what most Linux apps are written in, though some use higher level langs like Python.

All you have to do to make applications cross platofrm is avoid using *any* OS spasific libs, insted use cross platform libs which invoke the nesoserry underlying functions.

---

### Post by Stavro on 2009-05-14
Thank you all kindly for the replies. Much appreciated. I will stop talking now and play around a little to see what I like the best.

---

### Post by WitchCraft on 2009-05-14
> **Stavro said:**
> Thanks for the replies, it&#8217;s most appreciated. I think JAVA will probably be a little bit too slow for the work that I would like to achieve, which is highly mathematical and needs to be executed quickly. I understand JAVA is a very high level interpreter like language. Please correct me if I&#8217;m wrong. I like the sound of GTK+ a lot combined with C++ or C and I was wondering if anyone can recommend a good IDE if one exists that also features a form designer for easily creating widgets. The ability to develop both on Windows and Ubuntu would be really useful.


GNU C++ & CodeBlocks !!! It works on Windows, Linux, BSD, and Mac!

In combination with wxWidgets and OpenGL/SDL/OpenAl.

apt-get install g++
apt-get install libwxgtk2.8-0 libwxgtk2.8-dbg libwxgtk2.8-dev libwxbase2.8-0 libwxbase2.8-dbg libwxbase2.8-dev
apt-get install codeblocks codeblocks-contrib

---

### Post by jespdj on 2009-05-14
> **Stavro said:**
> Thanks for the replies, it&#8217;s most appreciated. I think JAVA will probably be a little bit too slow for the work that I would like to achieve, which is highly mathematical and needs to be executed quickly. I understand JAVA is a very high level interpreter like language. Please correct me if I&#8217;m wrong.
OK: You're wrong...

Java is not a "very high level interpreter like language". Java source code is compiled to bytecode. At runtime, this is interpreted and compiled into native machine code. Ten years ago, Java used to be slow, but that is not the case anymore today - the Java Virtual Machine has a very sophisticated and efficient Just-In-Time (JIT) compiler, which translates the bytecode into highly optimized and fast machine code. For most applications, Java hardy runs any slower than natively compiled C++ code. With JOGL (the Java OpenGL binding) you can easily create high performance 3D graphics applications.

The great thing about writing your program in Java is that you have to write it only once - the compiled Java program will run on any OS (Windows, Linux, Mac, whatever) for which there is a Java VM available. If cross platform is important to you, then this is very convenient.

Note that it's not called "JAVA", it's not an acronym.

---

### Post by s.fox on 2009-05-14
Hi,

I would say go for Python as it is available on just about every operating system.  More information on it can be found [here]("http://en.wikipedia.org/wiki/Python_%28programming_language%29").

-Ash R

---

### Post by jbruced on 2009-05-14
Been searching for the same thing for 6 months or so, I finally settled on C++ and Qt for the libraries. 

Why C++ for me?

C++ can be as fast and as low level as C with the added benefits of Object Oriented Programming. Cross-platform IDEs, libraries, and compilers can be had for free. Just as powerful as the paid for stuff, it's just that it's free. (Microsoft Operating Systems are written in C++, not that they're any good, but it gives you the idea of it's power)

Why Qt for me?

Qt is cross platform. Develop once, compile everywhere. The KDE environment(which I think is fantastic), is written with C++ using Qt. Qt is now owned by Nokia(recent), and they have a total GPL(free) version, along with great documentation, great IDE, and a full wysiwyg GUI generator. (I hope you understand that part).

I've been studying the tutorials over at cpluplus.com among other places. It's intense, but, you can't get the power without going through the learning pain.

Good luck in your venture.

---

