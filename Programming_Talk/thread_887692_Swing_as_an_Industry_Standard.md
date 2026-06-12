---
title: "Swing as an Industry Standard"
date: 2008-08-12
forum: Programming Talk
---

### Post by badperson on 2008-08-12
Hi,
I've been learning java for the last year or so, I'm just getting into using it where I work, I wrote a swing app that will allow users to select a group of files and run xslt stylesheets, or a perl script, or analyze files and output simple html pages, that kind of thing. 

I'm wondering how widely swing is used in terms of developing complex applications. 

I know eclipse is written in java, but I don't think it uses swing; I had a teacher (object oriented programming class) that said java desktop programming never really took off. 

Also, do you know of any examples of really good swing gui's that are available to look at? 
thanks,
bp

---

### Post by Shin_Gouki2501 on 2008-08-12
Hello!
Eclipse is created by using : SWT, JFace and RCP.
I also agree with you that it is a shame Java Desktop never took of, isntead all VB and such People now runing for Mono...

never mind.
There is actually a very good Swing Demo Application which shows all Components, if i find the link again i'll post it.

If you are bored you can also take a look at Eclipse RCP, its very nice ;)

---

### Post by Shin_Gouki2501 on 2008-08-12
dp

---

### Post by kknd on 2008-08-12
Generalizing (yes, this means that this post isn't the truth), Java is very resource-hungry for desktops, and it doesn't gives you the integration that some programs needs.

Despite this, Swing has a nice API and there are some nice Swing UIs.

---

### Post by NathanB on 2008-08-12
Not sure if they used Swing or an alternative, but I've seen Java used for "one-off" applications (e.g. to walk the user through connecting their DSL modem and testing the line conditions, etc.).

It also enjoys a presence on the desktop in the "off the beaten path" genre of applications.  For instance:

[http://www.jave.de/](http://www.jave.de/)

Heck, even the 'historically non-desktop' Ruby world has such examples:

[http://ifmapper.rubyforge.org/](http://ifmapper.rubyforge.org/)

So, desktop apps DO EXIST -- they just aren't always your "use every day" and "Joe User" style of applications.

Nathan.

---

### Post by Shin_Gouki2501 on 2008-08-12
this is also a nice example of an Eclipse RCP Application:
[http://www.rssowl.org/](http://www.rssowl.org/)

---

### Post by tinny on 2008-08-12
> **kknd said:**
> Generalizing (yes, this means that this post isn't the truth), Java is very resource-hungry for desktops, and it doesn't gives you the integration that some programs needs.

Despite this, Swing has a nice API and there are some nice Swing UIs.

> **kknd said:**
> Generalizing (yes, this means that this post isn't the truth), Java is very resource-hungry for desktops, and it doesn't gives you the integration that some programs needs.

Despite this, Swing has a nice API and there are some nice Swing UIs.

Used to be very hungry. As of Java 6 there have been some good performance gains.

I don't think that any Java GUI framework can be referred to as industry standard (as already stated Java is far from dominant on the desktop), Swing is the most widely used GUI framework for Java.

If you want to see / do some cool things with Java GUI have a look at [Substance]("https://substance.dev.java.net/see.html") and [JavaFX]("http://www.javafx.com/") (both built on swing)

---

### Post by kknd on 2008-08-12
> **tinny said:**
> Used to be very hungry. As of Java 6 there have been some good performance gains.

Java 6 is fast ([http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)), but Swing itself is resource-hungry.

---

### Post by tinny on 2008-08-12
> **kknd said:**
> Java 6 is fast ([http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)), but Swing itself is resource-hungry.

Where are these Java 6 swing stats?

My experience has been that If you write Swing app's correctly they are indistinguishable from native GUI applications. (expect for the JVM boot up time :( )

---

### Post by kknd on 2008-08-13
> **tinny said:**
> Where are these Java 6 swing stats?

My experience has been that If you write Swing app's correctly they are indistinguishable from native GUI applications. (expect for the JVM boot up time :( )

Well, not a scientific research, but my tests:

Memory consumption of a single top-level widget with some buttons and text:

In GTK+ 2: 1,4mb

Java/Swing: 15mb (25mb after 5 min of use).

I've done some applications that used Swing. Nothing really fancy, but all of them consumed 30+ mb (for 2/3 top-level widgets + basic controls).

Just for comparison:

I'm developing a commercial application, with some fancy GUIs and lots of data, using GTK+ 2 and Lua. It uses a fixed amount of 6mb of ram.

---

### Post by tinny on 2008-08-13
> **kknd said:**
> Well, not a scientific research, but my tests:

Memory consumption of a single top-level widget with some buttons and text:

In GTK+ 2: 1,4mb

Java/Swing: 15mb (25mb after 5 min of use).

I've done some applications that used Swing. Nothing really fancy, but all of them consumed 30+ mb (for 2/3 top-level widgets + basic controls).

Just for comparison:

I'm developing a commercial application, with some fancy GUIs and lots of data, using GTK+ 2 and Lua. It uses a fixed amount of 6mb of ram.

Thanks for that.

To be honest I hadn't thought of RAM usage. I was quite wrongly only thinking of UI responsiveness, which ive personally found to be fine in Swing.

I wonder what results a java-gnome, Gtk# or PyGTK application would yield? Maybe the results you are seeing are just the cost of using a high level language?

Edit: Are you using Sun Java 6? Or OpenJDK?

---

### Post by kknd on 2008-08-13
> **tinny said:**
> 
I wonder what results a java-gnome, Gtk# or PyGTK application would yield? Maybe the results you are seeing are just the cost of using a high level language?

Hi,

Lua is a scripting language +/- like Python, with dynamic typing etc. In theory, it should use more memory, but the results where inverted.

Maybe its a characteristic of Swing itself (I've tried Java + SWT: the memory usage was way better).

---

### Post by samjh on 2008-08-13
> **kknd said:**
> Maybe its a characteristic of Swing itself (I've tried Java + SWT: the memory usage was way better).

It sort of is.

SWT uses native calls to draw its widgets (like Java's AWT).  Swing is built entirely on Java itself, so it is very bulky.

There are some nice Swing apps about.  NetBeans, for example.

Don't forget that Lua was designed to be lightweight since day one, and PyGTK uses native GTK+ back-end to draw widgets, so they can run almost as light as C and GTK+.  Swing does not use native calls to draw widgets.

---

### Post by kknd on 2008-08-13
> **samjh said:**
> 
Don't forget that Lua was designed to be lightweight since day one, and PyGTK uses native GTK+ back-end to draw widgets, so they can run almost as light as C and GTK+.  Swing does not use native calls to draw widgets.

Thats a good point.

For Lua, I'm using my own GTK+ 2 bindings, very lightweight.

---

### Post by Shin_Gouki2501 on 2008-08-25
> **Shin_Gouki2501 said:**
> Hello!
..
There is actually a very good Swing Demo Application which shows all Components, if i find the link again i'll post it.
..

i found the Swing example read more here if your still interested:
[http://ubuntuforums.org/showthread.php?t=900550](http://ubuntuforums.org/showthread.php?t=900550)

---

### Post by themusicwave on 2008-08-25
I'm actually working on a SWING application this very moment in Netbeans.  Reading this post, I realized that Netbeans is a great example of what SWING can do.  It is a very nice User Interface.

SWING is a bit on the large side, but it isn't that bad.  I find the Netbeans GUI builder(don't know the official name) to be a great tool that really saves me time.  It is on par with Visual Studio, which is usually considered the Holy Grail of User Interface creation.

Also, SWING comes with Java, so in a way it is standard.  While many applications use other libraries, SWING is the one that Java ships with out of the box(AWT as well).  

SWING also looks perfectly native in my recent experience, the key is this one magical line of code:

```
UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
```

Then, you will get a native GUI.

---

### Post by Shin_Gouki2501 on 2008-08-25
nice for you to discover such enlightment ;)
There is so much more chekc out the demo apps i mention in my post above!
Visual Studio ist not ( and also not the most) about creating GUI's but its about its perfect integration into the windows platform: IIS etc..
reaching from web to database programmer or game developper (XNA) its a really great tool.


But as you mention netbeans and eclipse also have some nice features too!

---

