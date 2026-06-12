---
title: "Java Programming &amp; Linux Distros"
date: 2011-05-11
forum: Programming Talk
---

### Post by TheStroj on 2011-05-11
Hi everyone!

Lately, I've been programming in Java (only the basic stuff) and I kinda liked it. I mean, I really liked it. But my question is this: **Is it worth learning Java to program on Ubuntu or any other Linux distro? **

People usually say it's best to learn C or Python, but Java code looks cool and I think I want to program in it. But the problem is that I want to learn languages that I can use to make something useful and good looking (that means a nice GUI). **Is Java ok for that?**

Any recommendations about other languages that are commonly used on Linux distros, any tips on what to learn or something like that are highly appreciated.

Thanks in advance :)!

---

### Post by ve4cib on 2011-05-11
There are lots of Linux programs written in Java.  Use whatever language you like is usually the best answer to these kinds of questions.

Java programs tend to share a common "look and feel" when it comes to GUIs.  That's neither good nor bad IMO.  It just is.  Provided the GUI is laid out well and works it doesn't really matter if it integrates perfectly with a Qt or GTK desktop.

The advantage of using Java (besides the fact that you just want to use it) is that your program will (probably) work under Windows and OSX if you want to redistribute it.

---

### Post by worseisworser on 2011-05-11
If you're concerned your Java software will look "weird" or slightly out of place on a Linux desktop, there's always SWT: 
  [http://www.eclipse.org/swt/](http://www.eclipse.org/swt/)

..as you can see, Java can use the standard Linux Gnome/Gtk+ UI components.

About languages in general; there's plenty of languages available for Linux that fit your requirements. There's even several languages available for the Java platform (the JVM) besides Java-the-language itself. E.g. Clojure and Scala.

There's no good general answer as to which language is "the best" -- at least not until you add more constraints with regards to requirements than what you have already done above.

---

### Post by cgroza on 2011-05-11
Python is often used in Linux. It has great bindings for everything in gnome. So is C# and Ruby.

Java is a great tool too. With it, you code in linux, but in the same time, for all the platforms too.

---

### Post by Telengard C64 on 2011-05-11
I think it is worthwhile. IMHO Java is a great way to learn OOP. As mentioned, Java programs can be made cross-platform without much extra work. That means your Java programs aren't only relevant to Ubuntu and other Linux distros, but also to Windows, OS X, and any platform with a modern Java implementation.

You can make useful applications in Java. You can make nice looking applications in Java. You can make your Java application GUI integrate well with the rest of the desktop.

[list]
[*][Minecraft](http://www.minecraft.net)
[*][Eclipse](http://www.eclipse.org/)
[*][RuneScape](http://runescape.com/)
[*][Aquataxx](http://www.mactech.com/articles/mactech/Vol.19/19.12/CocoaAppsinJava/)
[*][HamWare](http://hamware.info/ham_ware/index.html)
[*][jEdit](http://www.jedit.org/index.php?page=screenshots)
[*][Lobo](http://lobobrowser.org/java-browser.jsp)
[*][RText](http://fifesoft.com/rtext/)
[*][Phex](http://www.phex.org/mambo/content/view/35/41/)
[*][Areca](http://www.areca-backup.org/screenshots.php)
[*][UltraMixer](http://www.ultramixer.com/)
[*][Vuze](https://www.vuze.com/)
[*]too many more to list
[/list]

Don't fall prey to [common misconceptions and myths](http://www.theregister.co.uk/2008/05/22/java_performance_myths/) about Java. Java programs don't have to be [slow](http://devnulled.com/content/2007/02/correcting-logical-fallacies-why-java-is-not-slow/).

Other languages worth learning and using on Linux.

[list]
[*][Bash](http://www.gnu.org/software/bash/manual/html_node/index.html)
[*][AWK](http://www.gnu.org/software/gawk/manual/html_node/index.html)
[*][Python](http://python.org/)
[*][perl](http://www.perl.org/) is also very prominent, although I really can't stomach the stuff myself
[*][C](http://en.wikipedia.org/wiki/K&R2)
[*][Ruby](http://www.ruby-lang.org/en/) is less prominent, but it does look interesting
[/list]

> **worseisworser said:**
> There's even several languages available for the Java platform (the JVM) besides Java-the-language itself. E.g. Clojure and Scala.

Not to forget [Ruby](http://en.wikipedia.org/wiki/JRuby), [Python](http://en.wikipedia.org/wiki/Jython), and [JavaScript](http://en.wikipedia.org/wiki/Rhino_(JavaScript_engine)).

---

### Post by stchman on 2011-05-11
> **worseisworser said:**
> If you're concerned your Java software will look "weird" or slightly out of place on a Linux desktop, there's always SWT: 
  [http://www.eclipse.org/swt/](http://www.eclipse.org/swt/)

..as you can see, Java can use the standard Linux Gnome/Gtk+ UI components.

About languages in general; there's plenty of languages available for Linux that fit your requirements. There's even several languages available for the Java platform (the JVM) besides Java-the-language itself. E.g. Clojure and Scala.

There's no good general answer as to which language is "the best" -- at least not until you add more constraints with regards to requirements than what you have already done above.

As far as look and feel, this line usually does me very well.

```

try {
    UIManager.setLookAndFeel( UIManager.getSystemLookAndFeelClassName() );
}
catch( Exception g ) {}

```I have found that everything looks as it should in GTK+ except the file open dialog.

---

### Post by PaulM1985 on 2011-05-11
> **stchman said:**
> As far as look and feel, this line usually does me very well.

```

try {
    UIManager.setLookAndFeel( UIManager.getSystemLookAndFeelClassName() );
}
catch( Exception g ) {}

```I have found that everything looks as it should in GTK+ except the file open dialog.

+1.  This is the sort of thing that I do with my programs.

Paul

---

### Post by cgroza on 2011-05-11
> **PaulM1985 said:**
> +1.  This is the sort of thing that I do with my programs.

Paul
Where do you get the UIManager class. What package contains it. I tried to do it too but it complained for an undefined symbol.

---

### Post by NovaAesa on 2011-05-11
UIManager is in javax.swing

[http://download.oracle.com/javase/6/docs/api/javax/swing/UIManager.html](http://download.oracle.com/javase/6/docs/api/javax/swing/UIManager.html)



EDIT: in case you don't know, you can always go to this website [http://download.oracle.com/javase/6/docs/api/](http://download.oracle.com/javase/6/docs/api/) that lists and documents all of the classes that come with Java.

---

### Post by cgroza on 2011-05-11
> **NovaAesa said:**
> UIManager is in javax.swing

[http://download.oracle.com/javase/6/docs/api/javax/swing/UIManager.html](http://download.oracle.com/javase/6/docs/api/javax/swing/UIManager.html)



EDIT: in case you don't know, you can always go to this website [http://download.oracle.com/javase/6/docs/api/](http://download.oracle.com/javase/6/docs/api/) that lists and documents all of the classes that come with Java.
Ok, thank you.

---

### Post by Telengard C64 on 2011-05-11
I forgot to mention the obvious. Lots more interesting info about Java:
[http://ubuntuforums.org/showpost.php?p=1997993](http://ubuntuforums.org/showpost.php?p=1997993)

---

### Post by TheStroj on 2011-05-12
> **Telengard C64 said:**
> I think it is worthwhile. IMHO Java is a great way to learn OOP. As mentioned, Java programs can be made cross-platform without much extra work. That means your Java programs aren't only relevant to Ubuntu and other Linux distros, but also to Windows, OS X, and any platform with a modern Java implementation.

You can make useful applications in Java. You can make nice looking applications in Java. You can make your Java application GUI integrate well with the rest of the desktop.

[list]
[*][Minecraft](http://www.minecraft.net)
[*][Eclipse](http://www.eclipse.org/)
[*][RuneScape](http://runescape.com/)
[*][Aquataxx](http://www.mactech.com/articles/mactech/Vol.19/19.12/CocoaAppsinJava/)
[*][HamWare](http://hamware.info/ham_ware/index.html)
[*][jEdit](http://www.jedit.org/index.php?page=screenshots)
[*][Lobo](http://lobobrowser.org/java-browser.jsp)
[*][RText](http://fifesoft.com/rtext/)
[*][Phex](http://www.phex.org/mambo/content/view/35/41/)
[*][Areca](http://www.areca-backup.org/screenshots.php)
[*][UltraMixer](http://www.ultramixer.com/)
[*][Vuze](https://www.vuze.com/)
[*]too many more to list
[/list]

Don't fall prey to [common misconceptions and myths](http://www.theregister.co.uk/2008/05/22/java_performance_myths/) about Java. Java programs don't have to be [slow](http://devnulled.com/content/2007/02/correcting-logical-fallacies-why-java-is-not-slow/).

Other languages worth learning and using on Linux.

[list]
[*][Bash](http://www.gnu.org/software/bash/manual/html_node/index.html)
[*][AWK](http://www.gnu.org/software/gawk/manual/html_node/index.html)
[*][Python](http://python.org/)
[*][perl](http://www.perl.org/) is also very prominent, although I really can't stomach the stuff myself
[*][C](http://en.wikipedia.org/wiki/K&R2)
[*][Ruby](http://www.ruby-lang.org/en/) is less prominent, but it does look interesting
[/list]



Not to forget [Ruby](http://en.wikipedia.org/wiki/JRuby), [Python](http://en.wikipedia.org/wiki/Jython), and [JavaScript](http://en.wikipedia.org/wiki/Rhino_(JavaScript_engine)).

Thanks for so much info, I really appreciate it. I will stick to Java for a while, I got 2x700 pages long books about Java and it should be enough to learn to make something useful.

My biggest concern was the bad looking GUI and slowness but all the posts in this thread helped me to decide that I'll try it anyway (and I totally forgot that Minecraft was written in Java, it is indeed a great game).

Thanks to everyone else who contributed with info, will mark this as SOLVED now :)

---

### Post by Telengard C64 on 2011-05-13
> **TheStroj said:**
> My biggest concern was the bad looking GUI and slowness but all the posts in this thread helped me to decide that I'll try it anyway (and I totally forgot that Minecraft was written in Java, it is indeed a great game).

My own Java programs had very ugly GUIs because I was too lazy to make them look good. That is most likely the case with every other *ugly* Java GUI you have seen. This isn't the fault of the language at all. It is possible to make terrible GUIs in any language.

/me reflecting on many Windows programs written in VB or Delphi which had god awful GUIs
:popcorn:

---

### Post by stchman on 2011-05-13
> **Telengard C64 said:**
> My own Java programs had very ugly GUIs because I was too lazy to make them look good. That is most likely the case with every other *ugly* Java GUI you have seen. This isn't the fault of the language at all. It is possible to make terrible GUIs in any language.

/me reflecting on many Windows programs written in VB or Delphi which had god awful GUIs
:popcorn:

Netbeans and Eclipse are written in Java.  I would say they are far from ugly.

---

### Post by Telengard C64 on 2011-05-13
> **stchman said:**
> Netbeans and Eclipse are written in Java.  I would say they are far from ugly.

Agreed!  :P

---

