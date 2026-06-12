---
title: "Install Java &quot;using any installation method&quot; - &quot;"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by Pat_Heslop-Harriso on 2014-02-16
I'm OK with Windows XP/7 (and Unix on a PDP11), command-lines, regedit etc but frustrated with win8 so deceided to try Linux. So I've a new build with Ubuntu 13.10 (updated, installed fairly easily from USB) on Z87 mobo with i7-4770. Installing java sounded a simple first task - but I'm stuck with lots of odd phrases which lead to another odd phrase when googled. Help please!

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) says "Installation of Java Runtime Environment

[LIST]
[*]Install the [openjdk-6-jre]("http://apt.ubuntu.com/p/openjdk-6-jre") package using any installation method. 


[*]Install the [openjdk-7-jre]("http://apt.ubuntu.com/p/openjdk-7-jre") package using any installation method. "
I assume it means one of these, but I have no idea what "any installation method" means other than double-click on downloaded file, which opens a box saying "choose an application".

Apparently, its all 'SOLVED" at [http://ubuntuforums.org/archive/index.php/t-1506642.html](http://ubuntuforums.org/archive/index.php/t-1506642.html). I've gone to a command window ctrl-alt-t and entered things like "sudo apt-get install sun-java7-jre sun-java7-plugin" and it says "Unable to locate package" and there is no obvious way to locate/download the package.

So move on to [http://justplainobvious.blogspot.co.uk/2010/06/how-to-install-java-jre-in-ubuntu-linux.html](http://justplainobvious.blogspot.co.uk/2010/06/how-to-install-java-jre-in-ubuntu-linux.html) - bit of struggle then need to "enabled the multiverse repository". Click through to something about this, 

and I'm asked to enable under **System** > **Administration**  > **Software Sources - **I have no idea what this means I'm afraid. Onto [http://ubuntuforums.org/showthread.php?t=1509372](http://ubuntuforums.org/showthread.php?t=1509372) - another "SOLVED" and stuff about 'go to synaptics' under "settings repository" ... try to install than run alacarte etc, and so it goes on. Somewhere it says to click on a Linux icon on the corner of the screen - I have firefox top left, various en-cloud-wifi...time-gearWithBarAt12 icons, but nothing else.

So help for a complete Linux Ubuntu newbie getting frustrated.

[/LIST]

---

### Post by The Cog on 2014-02-16
From the command line:
```
sudo sudo apt-get install openjdk-7-jre
```

Or open the Ubuntu software centre and search for the word java. You have a choice of java version 6 or 7.

Edit:
Finding the names of the packages is particularly difficult now that they don't install synaptic by default. Try
```
sudo apt-get install synaptic
```
and use synaptic to search for and install software. It's far more useful than that software-center rubbish that likes to keep you in the dark about what it's really doing.

---

### Post by Pat_Heslop-Harriso on 2014-02-17
Thanks for the very quick and helpful reply - synaptic is certainly useful. However, Java gets some way to running but still gives errorrs from the java-verifying installation page (I've restarted the computer and closded the browser several times). This is the copy from the 'click here for details. An exception has occurred." banner that appears. (new installation of Ubuntu 13.10, updated, Firefox standard browser, 4770 with internal graphics, SSD, Z87).
Thanks.

IcedTea-Web Plugin version: 1.4 (1.4-3ubuntu2)
Mon Feb 17 08:03:18 GMT 2014
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet. For more information click "more information button".
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:734)
    at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:662)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:914)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Application Error: Unknown Main-Class. Could not determine the main class for this application.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:708)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:249)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.createInstance(JNLPClassLoader.java:382)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:444)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:420)
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:700)
    ... 2 more

 Chain: 
1) at Mon Feb 17 08:03:12 GMT 2014
net.sourceforge.jnlp.LaunchException: Fatal: Application Error: Unknown Main-Class. Could not determine the main class for this application.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:708)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:249)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.createInstance(JNLPClassLoader.java:382)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:444)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:420)
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:700)
    at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:662)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:914)
2) at Mon Feb 17 08:03:12 GMT 2014
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet. For more information click "more information button".
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:734)
    at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:662)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:914)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Application Error: Unknown Main-Class. Could not determine the main class for this application.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:708)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:249)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.createInstance(JNLPClassLoader.java:382)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:444)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:420)
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:700)
    ... 2 more

---

### Post by The Cog on 2014-02-17
If you're trying to run java in a browser, you might be missing package icedtea-plugin (again, look for it in synaptic or use "sudo apt-get install icedtea-plugin").

If it's not that then I don't know. I googled for  "java-verifying installation page" and found one at java.com, which eventually gives me a grey rectangle where I suppose one might expect some kind of success message. Although that doesn't seem to work properly, I found an applet here [http://www.falstad.com/ripple/](http://www.falstad.com/ripple/) that does load and run properly, so I have my doubts about that verifying page. 

If you don't need to run javaq in the browser, just running "java -version" from the command line prompt should certainly give you a version print-out.

---

