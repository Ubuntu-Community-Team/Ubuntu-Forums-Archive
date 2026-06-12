---
title: "Java problem [NetBeans]"
date: 2007-04-24
forum: Programming Talk
---

### Post by peter07 on 2007-04-24
I'm using netbeans downloaded from netbeans.org. It's great IDE, but on Ubuntu (6.10 and 7.04) I have noticed annoying bug. Sometimes after using one of creator or dialog box (for example fix imports/add new servlet) keyboard input is blocked. I can't type anything, I may only move mouse. 

I have this problem only under ubuntu (everything is working correctly under XP). I'm not sure, but this could be netbeans error, or java package error (I have the same problems with some swing application, which I wrote myself, but now I can't find the example). 

Is it only my error, or somebody else notice that bug :confused:

---

### Post by Nikitas350 on 2007-04-30
I have the same problem too eith ubuntu feisty fawn. I believe that it is a bug. If there is a way to fix it i want to know how. Thanks

---

### Post by samjh on 2007-05-01
I've never had this problem, and I've been using Netbeans since version 4.

Sounds like a configuration-specific problem with both your systems.

Can you consistently reproduce the problem?  If so, file a bug report on the netbeans website (click on Community, and IssueZilla) with the specific steps you can take to reproduce it.

---

### Post by goldenfri on 2007-05-01
Seems this is a common problem, [http://www.netbeans.org/issues/show_bug.cgi?id=94316](http://www.netbeans.org/issues/show_bug.cgi?id=94316)

Might want to try removing SCIM

---

### Post by flossgeek on 2007-05-11
I also have this issue I am using Netbeans 5.5 and the Java 6 JDK from Ubuntu repositorys. I've noticed some Fedora users have this issue also. 

I removed SCIM but the issue remains. I get the symptom when ever a dialog box is present, then if i go back to the editor, i can't type.

---

### Post by olmedilla on 2007-05-14
I had the same problem with Feisty and found here a solution [http://ubuntuforums.org/showthread.php?t=299335](http://ubuntuforums.org/showthread.php?t=299335)

---

### Post by flossgeek on 2007-05-14
The issue you have stated is different, I am aware how to bring Java(TM) programs to view under AIGLX/XGL using the "AWT_TOOLKIT=MToolkit" by adding the line to the /etc/environment. But the issue I faced was my keyboard would loose focus. I have solved the issue by reverting back the java 5 jdk(was using the java 6 jdk), and now all seems fine so far.

---

### Post by Ragazzo on 2007-05-14
I've encountered that bug since Breezy Badger and it's not limited only to Netbeans but most Java programs. You can try to get the focus to work again by activating other programs (select from the window list) and then reactivating Netbeans or minimizing and maximizing the Java program etc. That's what I always do and it works for me. I have a slight recollection that the bug is connected to the window manager Metacity but I'm not sure about that.

Edit: It seems that I don't get this bug anymore in Feisty but I had it in earlier versions

---

### Post by NawaMan on 2007-05-17
Hi, I encounter the same problem. I am using Ubuntu 7.04 with Netbeans 5 .5 and JVM 1.6.0_01-b06. After trying different things, I am pretty sure that I can reproduce it by simply press Ctrl+F or any dialog. I also found that Just simple click the menu "Help -> Help Content" will simply bring me back the keyboard focus. Hope that this will be useful to someone.
Nawa Man

---

### Post by peter07 on 2007-06-21
I think this problem doesn't occur in netbeans 6 (M9 version), but I don't test it so precisely.

---

### Post by kknd on 2007-06-21
With Beryl / Compiz off and Java 6 update 1, I have no problem =-)

(I also had this problem)

---

### Post by dontcopymusic on 2008-05-27
Hi

I'm using Ubuntu Hardy Heron 8.04 with Java 6 update 1 and NetBeans 6.0.1 with all the latest updates, and have the exact same problem. 

I tried switching compiz off, but that didn't fix it for me. Also minimizing and maximizing netbeans, or switching to another application like firefox don't give me back keyboard input. 

Anyone got another suggestion? It sure is very annoying! I need to restart netbeans over and over again, not cool! So please, anyone?

Thanks!


PS: with NetBeans 5.5 (java6u1), Ubuntu 7.10 (with compiz turned on) I never experienced this problem...

---

### Post by xlinuks on 2008-05-27
Hi,
You should download the latest versions of Java and NetBeans and thanks to Sun, there's an option to download both Java and NetBeans bundled together, go here and choose "JDK 6 Update 6 with NetBeans 6.1":
[http://java.sun.com/javase/downloads/?intcmp=1281](http://java.sun.com/javase/downloads/?intcmp=1281)

Have fun :)

---

### Post by dontcopymusic on 2008-05-27
Hi

I just downloaded the installer. Now I run it but it asks me where I'd like the JDK to be installed. What folder do I need to choose in order to have this JDK as the default? It proposes my home directory, but I rather don't install it there... Any suggestion?

Thanks

---

### Post by xlinuks on 2008-05-27
Install it anywhere you wish (and have write permission), remember - only NetBeans will use that JDk as default - not your Linux system. For Linux to do that there a different way to achieve that, but it's not the problem this post is about.
I generally always create a folder called "apps" in my home folder and store there all applications that ask me where to install them, so I can easily track such apps that I install by hand like firefox, azureus, glassfish, googleearth, netbeans, nexuiz and so on, but that's just me - you might wanna do in some other way that suits you perhaps better.

---

### Post by dontcopymusic on 2008-05-27
Installation succesful, thank you very very much for your helpful posts!

---

### Post by dontcopymusic on 2008-05-27
Sorry, but the problem about the blocking keyboard input remains... :(
I guess I'll do a clean install when my exams are over.

---

### Post by Zugzwang on 2008-05-27
Did you try starting Netbeans from the command line? If yes, when the keyboard starts to block, do you get any exception on the command line?

---

### Post by dontcopymusic on 2008-05-27
I don't get a 'real' exception, but it does give me this output when starting the application:

```
(<unknown>:21458): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:21458): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:21458): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
```

But NO output when the keyboard input blocks...

---

### Post by dontcopymusic on 2008-05-27
Progress!

The 'bug' is caused by doing an export before running NetBeans, namely:
```
export AWT_TOOLKIT=MTOOLKIT
```
I had this export set in my .profile because I need it to run Maple properly. So after all it seems this isn't a bug caused by NetBeans, it is a JDK bug!

More info [here]("http://www.netbeans.org/issues/show_bug.cgi?id=84367") and [here]("http://www.netbeans.org/issues/show_bug.cgi?id=89148").

---

