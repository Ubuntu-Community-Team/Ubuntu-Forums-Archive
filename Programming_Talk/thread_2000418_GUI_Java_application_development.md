---
title: "GUI Java application development"
date: 2012-06-09
forum: Programming Talk
---

### Post by imbjr on 2012-06-09
I thought I'd check out the current state-of-play with regards to developing Java GUI application under Ubuntu:

Netbeans 7.0.1: I used the New Project wizard to start with and was told that the Swing Application Framework was no longer being developed and that I should try the Netbeans platform. So, OK, I will give that a go and sure enough I got a blank GUI application running. Then I thought, where's the JAR for this? Seems that there is not just one but a few and no obvious way to package them together. Plus, what was actually generated would be over-kill for many GUI applications.

So I thought, let's try the Swing option and ignore the warning. So I get a Swing application generated and it compiles, but it does not run. Seems that various parts of the GUI are never instantiated and so there's a lot of null pointer exceptions about.

Eclipse Indigo: I generate a blank Java application, but it's so blank there's not actually any Java generated. Plus: no sign of any tool to help create a GUI application and nothing in the repos to help do this.

This is disappointing. Netbeans used to work fairly well in this regard, but it looks like things have moved on, and perhaps my understanding of how things are done in Java/Netbeans needs to move on. As for what was up with Eclipse, I do not know - but I've never really cared for that IDE anyway.

This all compares badly with the likes of QT and MonoDevelop, where I can get a basic GUI application running very quickly.

Am I doing something wrong here?

---

### Post by imbjr on 2012-06-09
Well after installing the Windows version of Netbeans under 7 and pottering about I got a NewJPanel to display, so at least that's a start.

---

### Post by imbjr on 2012-06-09
Now, when I come to add graphical components to my JFrame, it sits there with "Loading ..." in the middle. Under Windows, I briefly see that but then it loads.

---

### Post by imbjr on 2012-06-09
Well, it looks like 7.0.1 in Ubuntu is buggy:

[http://stackoverflow.com/questions/10791221/netbeans-gui-builder-loading-message](http://stackoverflow.com/questions/10791221/netbeans-gui-builder-loading-message)

---

### Post by imbjr on 2012-06-09
> **imbjr said:**
> Well, it looks like 7.0.1 in Ubuntu is buggy:

[http://stackoverflow.com/questions/10791221/netbeans-gui-builder-loading-message](http://stackoverflow.com/questions/10791221/netbeans-gui-builder-loading-message)

And on the Debian bug tracker I found a work-around. Run netbeans like so:

netbeans -cp:a /usr/share/java/xercesImpl.jar

---

### Post by PaulM1985 on 2012-06-09
> **imbjr said:**
> I thought I'd check out the current state-of-play with regards to developing Java GUI application under Ubuntu:

Netbeans 7.0.1: I used the New Project wizard to start with and was told that the Swing Application Framework was no longer being developed and that I should try the Netbeans platform. So, OK, I will give that a go and sure enough I got a blank GUI application running. Then I thought, where's the JAR for this? Seems that there is not just one but a few and no obvious way to package them together. Plus, what was actually generated would be over-kill for many GUI applications.

So I thought, let's try the Swing option and ignore the warning. So I get a Swing application generated and it compiles, but it does not run. Seems that various parts of the GUI are never instantiated and so there's a lot of null pointer exceptions about.

Eclipse Indigo: I generate a blank Java application, but it's so blank there's not actually any Java generated. Plus: no sign of any tool to help create a GUI application and nothing in the repos to help do this.

This is disappointing. Netbeans used to work fairly well in this regard, but it looks like things have moved on, and perhaps my understanding of how things are done in Java/Netbeans needs to move on. As for what was up with Eclipse, I do not know - but I've never really cared for that IDE anyway.

This all compares badly with the likes of QT and MonoDevelop, where I can get a basic GUI application running very quickly.

Am I doing something wrong here?

When you do a clean and build in Netbeans it creates the JAR for you in a dist folder that you will find in the project.  Usually it will run from the class files that are automatically created from the java files as soon as they save.  Netbeans tends to try to compile automatically on save and if it is successful the compiled files are put in the build folder.

In Netbeans you still can get a GUI running quickly, as far as I know.  It seems to run ok for me.

I don't use Eclipse for "plain" Java dev, only Android.  For that I tend to edit everything by hand rather than use UI designers (they might not even exist, I just know I prefer to manually edit stuff since it is faster for me).

Paul

---

### Post by macachuto on 2012-10-13
I faced the same problem.
Kubuntu 12.04 x86_64

To make JFrame works, I also need to start netbeans with -cp:a /usr/share/java/xercesImpl.jar

We need to fill a bug.

---

