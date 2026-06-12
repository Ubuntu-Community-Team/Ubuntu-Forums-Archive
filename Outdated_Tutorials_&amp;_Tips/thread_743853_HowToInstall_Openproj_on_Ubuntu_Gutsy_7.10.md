---
title: "HowTo:Install Openproj on Ubuntu Gutsy 7.10"
date: 2008-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Sabot on 2008-04-03
I was looking for a replacement for MS Project and I found it in Openproj. It did not work on my machine at first so here is how I got it to run.  It would load, but it would just come up to a blank gray screen.

You can download the Openproj .deb from:
[http://sourceforge.net/project/platformdownload.php?group_id=199315&sel_platform=4043](http://sourceforge.net/project/platformdownload.php?group_id=199315&sel_platform=4043)

Install Openproj just by double clicking the .deb file you downloaded above.

You need to have Sun Java 6 installed.  You can get it by using synaptic to download the package called sun-java6-bin.

Now you are ready to open Openproj. You will find it under Applications>Office>Openproj in the upper left of your screen.

If it opens to just a gray screen, then you have Java 5 installed and you will need to tell Openproj to use Java 6.

Open a terminal and enter:
```
gedit .openproj/run.conf

```
Edit the JAVA_EXE Line to look like this:

```
JAVA_EXE="/usr/lib/jvm/java-6-sun/bin/java"
```

Now we have just one last thing to do.  There is a printing error in Java that we need to fix. Go to System>Administration>Printing and  Select the printer you will be using.  Click the Job Options tab and.  Change the orientation from Automatic to Portrat or landscape.  You will now be able to print from Openproj.

Enjoy!

---

### Post by wieman01 on 2008-04-03
Cool. Nice one. I did not know there is such a nice replacement for MS Project. Thank you for this guide, I will certainly use it one day (rather sooner than later). :-)

---

### Post by JarG0n on 2008-06-03
Someone should maintain this as a package in Ubuntu.  I need the same app.

---

### Post by FuePi on 2008-07-22
Thanks for the guide Sabot.

Installation of openproj_1.2-1.deb works fine on Ubuntu 8.04 Hardy.
Sometimes I get a blank window or dialog, when I retry (a couple of times) it usually works.

I followed the printing instructions, but OpenProj won't print.
Any ideas about that?

P.S.
I followed the printing instructions correctly and OpenProj does print. ;)

---

### Post by rodolphoarruda on 2009-02-26
Thank you! OpenProj is beautiful!

---

### Post by kblood on 2009-05-24
Sorry to revive an old thread, but OpenProj documentation is pretty much inexistent.

I am trying to use OpenProj 1.4, but I'm running into an annoying problem. I thought that using project management software would help be to schedule tasks, but I still need to do it by hand.

When I create tasks, and assign resources, I end up with a bunch of tasks on the same day, and resources used waaaaay above 100% (800%, 900%...).

According to the website, OpenProj has one of the best schedulers in the industry, but I don't see it anywhere.

Am I not understanding it correctly?

PS: Open Workbench has an autoschedule tool that works really well, but it's not fully open source, and I need to use Wine to run it.

---

