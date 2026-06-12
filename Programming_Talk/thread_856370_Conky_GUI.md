---
title: "Conky GUI"
date: 2008-07-11
forum: Programming Talk
---

### Post by Diabolis on 2008-07-11
[**[SIZE="4"]Conky GUI web site[/SIZE]**]("http://conkygui.sourceforge.net/")

I am developing this tool, so if you have any questions or suggestions you can:
1.- use this thread
2.- or get support through the project page:
[http://sourceforge.net/projects/conkygui/support](http://sourceforge.net/projects/conkygui/support)

**Get the latest news about Conky GUI:**
Thread Tools / Subscribe to this thread
I'll post in this thread for each new release.

---

### Post by era86 on 2008-07-11
Looks promising.  I'll test it when I get on my laptop. ;)

---

### Post by Diabolis on 2008-07-11
Thank you for your interest. Please post back with any comments or suggestions.

I would prefer it if you do it through the [sourceforge]("http://sourceforge.net/projects/conkygui/") page, but if you don't have an account I guess this thread will serve the purpose.

---

### Post by Diabolis on 2008-07-17
I'm thinking about translating the application from java to another language. Which one do you think it will be better? c++/qt or python/gtk ?

I thought about this because I was getting a lot of negative feedback about being written in java.

I'll keep on working on the java version tho.

---

### Post by era86 on 2008-07-17
I think the majority of your responses will be to use Python/GTK.  Though, you might be a little bit more comfortable with the C++ route considering you are transforming it from Java.

In this case, it is all in what you're comfortable with.

My vote, however, would be to do it in Python.

---

### Post by urukrama on 2008-07-17
Do you have any screenshots?

---

### Post by Diabolis on 2008-07-17
Screenshots up: [https://sourceforge.net/project/screenshots.php?group_id=233002&ssid=87281](https://sourceforge.net/project/screenshots.php?group_id=233002&ssid=87281)

---

### Post by y-lee on 2008-07-17
Wow that is pretty cool. I'll give it a try too tho i wonder  who would want this as the whole fun of conky for me is messing with its configuration file directly, lol. Anyway it is a nice idea for an app and maybe it will make conky more usable for those who are not code monkeys. lmao.

peace :)

---

### Post by Sealbhach on 2008-07-18
Hi.

I downloaded the tar.gz file and extracted everything to my home folder but I don't know how to get it working and I can't see any instructions anywhere.

.

---

### Post by Diabolis on 2008-07-18
It has a file called **conkygui.jar** you should be able to just double click that file and it will run.

If not right click the file and you should see an option that says **"open with Sun Java 6 Runtime".**

Installation instructions are in the project website, which will be up shortly, I hope. Sourceforge is doing a migration of data and that or something else is giving hiccups to their servers, I already reported the problem with the project web site.

Sorry for the inconvenience.

---

### Post by Sealbhach on 2008-07-18
OK, cool, it opened with Java Runtime.
Thanks.


.

---

### Post by Beaker Bongload on 2008-07-21
I just ran it and liked the idea. My suggestions for improvement are adding variables for all of the built in conky options for starters. Most of what I saw was the very basic stuff that is self explanatory in the conkyrc itself and use of the variable page on thier website.

---

### Post by slavik on 2008-07-21
I suggest Perl/GTK :P

just ran it ... looks nice (is this swing?), IMO no real reason to switch :)

---

### Post by WiTcHkInG on 2008-07-21
Hi
trying to run this but when i open it, it just flashes up then dissapears :confused:

Updated java to make sure that wasnt the problem.
Any ideas?

---

### Post by Diabolis on 2008-07-21
Can you run it from the terminal please?

You would have to **cd** to the where the **conkygui.jar** file is and then type this:
```
java -jar conkygui.jar
```

---

### Post by WiTcHkInG on 2008-07-21
> **Diabolis said:**
> Can you run it from the terminal please?

You would have to **cd** to the where the **conkygui.jar** file is and then type this:
```
java -jar conkygui.jar
```

That worked, cheers.

---

### Post by Diabolis on 2008-07-30
I just uploaded a new version, **Conky GUI v1.2**

Change Log 
 
What was fixed: 
 
- "undo" action under the edit menu 
- font parsing when reading conky files 
- corrected a bug in the syntax highlight algorithm that caused high cpu usage 
 
What was added: 
 
- saved file pop up message 
- shell windows with buttons 
- open recent files menu option 
- added a new color for syntax highlighting 
- application icon (conky image) 
 
What was improved: 
 
- syntax highlight 
- word completion

---

### Post by aktiwers on 2008-07-30
Looks very cool!

---

### Post by Diabolis on 2008-08-01
> **aktiwers said:**
> Looks very cool!

Thank you.

Now there is a **.deb** available for easier installation.

conky gui v1.2 .deb download

---

### Post by gdg2k5 on 2008-08-04
right well, I installed it and it seemed to work great, exited out, tried to install a package and its telling me "E: The package conkygui needs to be reinstalled, but I can't find an archive for it."... my whole package manager is frozen now... help?

btw, it wont let me remove it or reinstall it

---

### Post by Diabolis on 2008-08-04
mm ok I'll check that.

Type this to fix it:
```
sudo dpkg --remove --force-remove-reinstreq conkygui
```

It will completely delete Conky GUI.

I'm already working on making a better .deb.

I just updated the site.

---

### Post by gdg2k5 on 2008-08-05
So, i just tried doing that and it returned
```
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 168984 files and directories currently installed.)
Removing conkygui ...
/var/lib/dpkg/info/conkygui.prerm: 3: update-menus: not found
dpkg: error processing conkygui (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/conkygui.postinst: 3: update-menus: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 conkygui

```

---

### Post by Diabolis on 2008-08-05
This is very strange. The scripts in the .deb are trying to execute this command **update-menus** and apparently thats what is causing the error.

Can you execute that command in a terminal to see if its really causing the problems, please.

---

### Post by gdg2k5 on 2008-08-06
mmm ya, its giving me command not found. So im guessing that i need to install it somehow? i wouldnt know how to do it without use of synaptic...

---

### Post by Diabolis on 2008-08-06
so, did you got it solved?

---

### Post by gdg2k5 on 2008-08-07
no, not really. can you give me a link to the .deb so i can try reinstalling it... idk if that would give me any help though

---

### Post by Diabolis on 2008-08-07
Ok, if you still don't have the **update-menus** command available, you can delete it from the scripts.

You have to edit 2 files:
[B]sudo gedit /var/lib/dpkg/info/conkygui.postinst
sudo gedit /var/lib/dpkg/info/conkygui.prerm[/B]

---

### Post by Diabolis on 2008-09-20
****

---

### Post by FiatScientia on 2009-01-23
Error city.

I just spent a long, long time trying to figure out how to change Netbeans and the Java L&F with substance, so it's not really exciting to see it again.

My terminal output from "java -jar conkygui.jar":

```
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at sun.java2d.pisces.Renderer.crossingListFinished(Renderer.java:778)
	at sun.java2d.pisces.Renderer._endRendering(Renderer.java:466)
	at sun.java2d.pisces.Renderer.endRendering(Renderer.java:478)
	at sun.java2d.pisces.PiscesRenderingEngine.getAATileGenerator(PiscesRenderingEngine.java:327)
	at sun.java2d.pipe.AAShapePipe.renderPath(AAShapePipe.java:93)
	at sun.java2d.pipe.AAShapePipe.draw(AAShapePipe.java:61)
	at sun.java2d.pipe.ValidatePipe.draw(ValidatePipe.java:154)
	at sun.java2d.SunGraphics2D.draw(SunGraphics2D.java:2392)
	at org.jvnet.substance.border.StandardBorderPainter.paintBorder(StandardBorderPainter.java:113)
	at org.jvnet.substance.SubstanceImageCreator.paintBorder(SubstanceImageCreator.java:99)
	at org.jvnet.substance.SubstanceImageCreator.paintBorder(SubstanceImageCreator.java:126)
	at org.jvnet.substance.SubstanceBorder.paintBorder(SubstanceBorder.java:175)
	at org.jvnet.substance.SubstanceBorder.paintBorder(SubstanceBorder.java:238)
	at javax.swing.border.CompoundBorder.paintBorder(CompoundBorder.java:111)
	at javax.swing.JComponent.paintBorder(JComponent.java:933)
	at javax.swing.JComponent.paint(JComponent.java:1039)
	at javax.swing.JComponent.paintToOffscreen(JComponent.java:5147)
	at javax.swing.BufferStrategyPaintManager.paint(BufferStrategyPaintManager.java:302)
	at javax.swing.RepaintManager.paint(RepaintManager.java:1145)
	at javax.swing.JComponent._paintImmediately(JComponent.java:5095)
	at javax.swing.JComponent.paintImmediately(JComponent.java:4905)
	at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:740)
	at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:696)
	at javax.swing.RepaintManager.prePaintDirtyRegions(RepaintManager.java:676)
	at javax.swing.RepaintManager.access$700(RepaintManager.java:57)
	at javax.swing.RepaintManager$ProcessingRunnable.run(RepaintManager.java:1550)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
```

---

### Post by jjgomera on 2009-01-23
you could try with other java vm, open a terminal and run:

```
sudo update-alternatives --config java
```

---

### Post by Diabolis on 2009-01-26
To use Substance instead of the default look and feel right click the **project folder** inside Netbeans in the projects panel. A menu will appear, click on **properties** and a window will show up. Inside the window, under the categories panel, go to **application** / **Desktop app**. There you'll find the look and feel field where you can select any of the many Substance themes or select a different jar file.

---

### Post by Ectara on 2009-05-20
How did you solve the issue you had before while building the .deb?

I am having the same exact issue, and can't figure it out.

[Your previous post]("http://ubuntuforums.org/showpost.php?p=5503569&postcount=3")

---

### Post by Diabolis on 2009-05-21
Please don't reply to threads in a different thread, your question is off topic here.

Your post shouold be here: [http://ubuntuforums.org/showthread.php?p=5503569#post5503569](http://ubuntuforums.org/showthread.php?p=5503569#post5503569)

---

### Post by Diabolis on 2009-05-26
Conky GUI now uses subversion, [http://sourceforge.net/scm/?type=svn&group_id=233002]("http://sourceforge.net/scm/?type=svn&group_id=233002").

If you want to browse the code go here: [http://conkygui.svn.sourceforge.net/viewvc/conkygui/](http://conkygui.svn.sourceforge.net/viewvc/conkygui/)

---

### Post by Diabolis on 2009-07-31
A new version of Conky GUI has been released. [http://sourceforge.net/projects/conkygui/](http://sourceforge.net/projects/conkygui/)

---

### Post by kebabbaro on 2009-08-26
> **Diabolis said:**
> A new version of Conky GUI has been released. [http://sourceforge.net/projects/conkygui/](http://sourceforge.net/projects/conkygui/)
After a few failed attempts to run conkygui I tried the terminal with the command (given in the proper directory) 
```
java -jar conkygui.jar
```but here's the output:
```
SEVERE: Application class conkygui.ConkyguiApp failed to launch
java.lang.NullPointerException
    at conkygui.ConkyguiView.initComponents(ConkyguiView.java:104)
    at conkygui.ConkyguiView.<init>(ConkyguiView.java:73)
    at conkygui.ConkyguiApp.startup(ConkyguiApp.java:42)
    at org.jdesktop.application.Application$1.run(Application.java:171)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
Exception in thread "AWT-EventQueue-0" java.lang.Error: Application class conkygui.ConkyguiApp failed to launch
    at org.jdesktop.application.Application$1.run(Application.java:177)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
Caused by: java.lang.NullPointerException
    at conkygui.ConkyguiView.initComponents(ConkyguiView.java:104)
    at conkygui.ConkyguiView.<init>(ConkyguiView.java:73)
    at conkygui.ConkyguiApp.startup(ConkyguiApp.java:42)
    at org.jdesktop.application.Application$1.run(Application.java:171)
    ... 8 more

```any hints on how to fix the problem :confused:

thank you

---

### Post by Diabolis on 2009-08-26
The bug has been reported and fixed: [https://sourceforge.net/tracker/?func=detail&aid=2840870&group_id=233002&atid=1088609](https://sourceforge.net/tracker/?func=detail&aid=2840870&group_id=233002&atid=1088609)

As a temporal workaround you can do the following:
```
mkdir ~/.conkygui/
touch ~/.conkygui/preferences.xml
```

The contents of preferences.xml should be:
> <?xml version='1.0' encoding='UTF-8'?>
<root>
	<comment>#</comment>
	<command>killall conky; conky -c $FILE &amp;</command>
</root>


Now it should work.

---

### Post by Diabolis on 2009-08-26
A new version of Conky GUI has been released.
[https://sourceforge.net/projects/conkygui/files/](https://sourceforge.net/projects/conkygui/files/)

---

### Post by Diabolis on 2009-10-03
Conky GUI 1.2.3 is up.

[http://sourceforge.net/projects/conkygui/](http://sourceforge.net/projects/conkygui/)

---

### Post by rbolio on 2009-10-04
Conkygui 123 isn't working for me.... i get this when i run it...

```
rbolio@laptop:~/Downloads/conkygui$ ./conkygui.sh
Using default value for $SCALA_HOME 
   /usr/share/java
Classpath: 
   /usr/share/java/lib/scala-library.jar:lib/substance.jar:lib/swing-worker-1.1.jar:lib/appframework-1.0.3.jar:conkygui.jar
[Fatal Error] preferences.xml:1:1: Premature end of file.
Exception in thread "AWT-EventQueue-0" java.lang.NoClassDefFoundError: scala/ScalaObject
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	at components.prefpanels.ShellStyledDocument.remove(ShellStyledDocument.java:57)
	at javax.swing.JEditorPane.setText(JEditorPane.java:1495)
	at components.prefpanels.PreferencesExecutionPanel.setCommand(PreferencesExecutionPanel.java:147)
	at components.PreferencesWindow.setCommand(PreferencesWindow.java:157)
	at components.PreferencesWindow.<init>(PreferencesWindow.java:48)
	at conkygui.ConkyguiView.<init>(ConkyguiView.java:77)
	at conkygui.ConkyguiApp.startup(ConkyguiApp.java:42)
	at org.jdesktop.application.Application$1.run(Application.java:171)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.lang.ClassNotFoundException: scala.ScalaObject
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	... 28 more

```

I have no idea what that means.... i think the "premature end of file" has something to do.... 
help?

---

### Post by Diabolis on 2009-10-04
Ouch! the shell script is wrong, I'll re-upload it now.

---

### Post by rbolio on 2009-10-04
Wish I could be of more help....Cheers! and good luck!

---

### Post by Diabolis on 2009-10-04
Corrected Conky GUI v1.2.3 is up.

---

### Post by Diabolis on 2009-11-22
Conky GUI v1.3 is up
[http://sourceforge.net/projects/conkygui/](http://sourceforge.net/projects/conkygui/)

---

### Post by Diabolis on 2009-11-22
[[IMG]http://farm3.static.flickr.com/2572/4126357194_eed4e264fe_m.jpg[/IMG]]("http://www.flickr.com/photos/silvag/4126357194/")

---

### Post by duanedesign on 2010-03-11
I think this is a great idea. Definitely the creation of a config file was a little daunting for the average user. Even something like [ConkyColors]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328") was not all that easy. Cant wait to try this out.

Maybe I missed it in the thread. You were mentioning a rewrite from Java to possibly Python. Did this ever happen?

thanks,
duanedesign

---

### Post by Diabolis on 2010-03-11
I started it in Java because that was the language in which I had a deeper knowledge at the moment. Since then I've learned some other languages and rewrote half of Conky GUI in Scala, because it is very easy to do the "syntax highlight" part with it. I'm not sure what will be next as I have juggled with the idea of going from swing to Qt also. I don't mind rewriting it many times, but for now I don't have much spare time.

---

### Post by 2hot6ft2 on 2010-04-26
Hi Diabolis,

I actually found the program from the hardcore conky forum and installed it before finding this thread.
I installed 1.3 extracted it in my home folder so now it's in ~/conkygui
I can start it if I open a terminal in that folder and run ./conkygui.sh
But that keeps a terminal open while the program is open which I don't care for.

What I'm trying to do is create a launcher in the menu for it but I'm having a little trouble getting the command right. So my question is how to set the launcher up for that.

Type: Appication or Application in Terminal?
Command: ? This is the one that's really stumping me.

I've tried so many variations I can't believe I haven't got it right yet.:confused:
The closest I've come is
~/conkygui/./conkygui.sh
but that brings up these errors
```
Exception in thread "main" java.lang.NoClassDefFoundError: conkygui/ConkyguiApp
Caused by: java.lang.ClassNotFoundException: conkygui.ConkyguiApp
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
Could not find the main class: conkygui.ConkyguiApp. Program will exit.

```
And thanks for creating it. I think it will make it a little easier to understand the formatting once I learn to use it.
I see you don't visit here very often anymore so please PM me when you drop back in to answer.

---

### Post by Diabolis on 2010-04-26
The problem is that the shell script uses paths relative to the place from where it is executed. That is why it only works if you run it within the conkygui folder.

I've been working on a installation script and also a .deb package. They are pretty much done, but I haven't released them yet. I am being very cautious with them and I want to be sure they'll be right once I upload them. I've been very busy this days and probably I won't release this files soon, maybe in a month. However, I could provide you, at your own risk, the latest tarbz2 package.

---

### Post by Diabolis on 2010-06-23
New installer and .deb, try them out:
[https://sourceforge.net/projects/conkygui/files/](https://sourceforge.net/projects/conkygui/files/)

---

### Post by kton on 2010-06-26
sorry for the n00b comment but what do you mean when the readme says:

1.- Make conkygui.sh executable:
	chmod u+x conkygui.sh

2.- Execute it:
	./conkygui.sh

im typing it in the terminal and nothing is happening. is that right?

---

### Post by Diabolis on 2010-06-26
Sorry, my bad, ignore the readme file. I forgot to update it. You can find the installation instructions at the website.

Just install it:
```
sudo ./INSTALL
```

---

### Post by Damiox on 2010-12-01
installed from deb ... all good  :)

---

