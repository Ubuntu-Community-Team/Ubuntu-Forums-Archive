---
title: "Eclipse  3.5 + Visual Editor 1.4.0 + Java (Ubuntu 9.04)"
date: 2009-10-18
forum: Programming Talk
---

### Post by Ubuntooid on 2009-10-18
I've downloaded "Eclipse IDE for Java Developers" from eclipse.org with accordance with [this]("http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/") page (exact link: [http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/galileo/SR1/eclipse-java-galileo-SR1-linux-gtk.tar.gz]("http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/galileo/SR1/eclipse-java-galileo-SR1-linux-gtk.tar.gz")) and I've also installed Visual Editor 1.4.0 in it (exact link: [http://www.eclipse.org/downloads/download.php?file=/tools/ve/downloads/drops/1.4.0/R200909301124/VE-Update-1.4.0.zip]("http://www.eclipse.org/downloads/download.php?file=/tools/ve/downloads/drops/1.4.0/R200909301124/VE-Update-1.4.0.zip")) deselecting the following components in it: Java EMF Model, Java EMF Model SDK, Java EMF Model Source, Visual Editor All-in-One SDK.

When creating a visual class there is an error: "Error trying to set new file into editor. Reason: java.lang.NullPointerException". There are suggestions on the web to clean all cache using menu "Project->Clean...->Clean All" and to start eclipse from terminal with "eclipse -clean", but these didn't work for me.

---

### Post by myrtle1908 on 2009-10-19
When you say "visual" I assume you mean that you wish to create a GUI of some sort.  Whilst the following is not an answer to your original question, I strongly suggest that for Java GUI development you consider using NetBeans.  Eclipse is great for many many things but IMO GUI design is not one of them.  NetBeans wins the GUI war hands down.

---

### Post by jespdj on 2009-10-19
As far as I know, the Eclipse Visual Editor is unfortunately more or less a dead project. It seems it hasn't been developed on for a few years, I wouldn't be surprised if it doesn't work properly with the latest version of Eclipse.

There are some alternatives: you could try [Jigloo](http://www.cloudgarden.com/jigloo/) or use [NetBeans](http://www.netbeans.org/) instead of Eclipse, which has a very good built-in GUI builder.

---

### Post by Bad Sector on 2009-10-19
Visual Editor is under development under a new maintainer and i think the latest release "1.4.0" is under this new maintainer, which however was the previous version made to work with Eclipse 3.5. All the new work is done for the next "1.5.0" release.

I installed VE just fine in my 3.5 Eclipse. I used "Eclipse Classic", but this shouldn't be a problem. Note that i also used the update site they mention in the wiki instead of downloading the ZIP file. Moreover, the Visual Editor *does* need EMF so it is a good idea to have it.


My gripe with the editor is its speed (and as it seems, what most people want as the first improvement is the performance). Its barely usable as it is now. [I wrote about this here](http://badsectoracula.blogspot.com/2009/10/java-trick-for-swt-goodness.html) yesterday with a trick to make the development easier, but they really need to fix it.

NetBeans has a better experience for editing (although it has a tendency to screw the layout a lot), but the produced code is sub-par and litters the code with comments, uneditable areas and adds extra files to the project for each form. Eclipse's designer reads your code and builds the GUI from that so you can develop it even outside the editor and if you later decide you don't want a visual editor you'll have your own code to work with.

---

### Post by myrtle1908 on 2009-10-20
> **Bad Sector said:**
> NetBeans has a better experience for editing (although it has a tendency to screw the layout a lot), but the produced code is sub-par and litters the code with comments, uneditable areas and adds extra files to the project for each form.

This is true and why it is generally best to create your GUIs from scratch (at least in Java).

> **Bad Sector said:**
> Eclipse's designer reads your code and builds the GUI from that so you can develop it even outside the editor and if you later decide you don't want a visual editor you'll have your own code to work with.

That is good to know.  I'd like to see how it goes with a complex GUI.  Does it mangle your existing code if you decide to change something eg. visually move a widget from one panel to another?

---

### Post by animefan82 on 2009-11-05
> **myrtle1908 said:**
> When you say "visual" I assume you mean that you wish to create a GUI of some sort.  Whilst the following is not an answer to your original question, I strongly suggest that for Java GUI development you consider using NetBeans.  Eclipse is great for many many things but IMO GUI design is not one of them.  NetBeans wins the GUI war hands down.

I also prefer NetBeans for GUI editing, although I'd say NetBeans is the Windows of Java visual editing, whilst Eclipse would be the linux counterpart, since it's more customizable.

---

