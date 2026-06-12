---
title: "Eclipse Crashing with Error"
date: 2006-12-27
forum: Programming Talk
---

### Post by sreeraj on 2006-12-27
**Eclipse get closed and the following error is displayed. I am using Ubuntu 6.06 LTS with eclipse3.2.1 and java 1.5.0.09. Exadel 4.0.0 is used in eclipse **

VM terminated. Exit code=1
/usr/bin/java
-Xms40m
-Xmx256m
-jar /home/jobu/programs/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /home/jobu/programs/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 228011
-vm /usr/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /home/jobu/programs/eclipse/startup.jar 

**Please Please Please any one help me [COLOR="Red"][FONT="Arial Black"][SIZE="5"]very urgent[/SIZE][/FONT][/COLOR]**

---

### Post by phossal on 2006-12-28
Is this happening when you first start eclipse? If not, at what point?

---

### Post by rgeddes on 2007-01-05
The same thing is happening to me... I execute /usr/bin/eclipse.  The opening takes a while and eventually displays the 'Overview' screen.  If I select a link on that screen, eg 'Workbench Basics', it crashes followed by a message window:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 8c8015
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

The message says the JVM terminated, but gives no hint as to whether the JVM termination was the cause or the result.  Also, the JVM that is used is java-gcj, I think it's the GNU JVM... can anyone tell me if the Sun JVM is better, and if so, how can I get the Sun JVM to play with Eclipse.

Thnx
Richard

---

### Post by sreeraj on 2007-01-05
It is happening when we are working in eclipse. At start time no problem. Also it is not occuring regularly.

---

### Post by hod139 on 2007-01-05
Have you done all the steps in the [howto]("http://ubuntuforums.org/showthread.php?t=201378") for installing the repository version of eclipse?  My guess is maybe you need to do 
```

sudo update-java-alternatives -s java-1.5.0-sun

```

---

### Post by rgeddes on 2007-01-05
hod139,

That HowTo got me past the 'Welcome' tab.  I can now get Eclipse 'Help' without crashes.  GNU Java seems to be the default JVM, yet I've read quite a few complaints about it.  In many cases, it's too slow, and in my case, it crashed Eclipse (assuming an indirect cause and effect).  

Thanx
Rich

---

### Post by phossal on 2007-01-06
Here is my suggestion...

**[COLOR="#248"]1. Download Java[/COLOR]**
Download the [COLOR="Blue"][32Bit JDK]("http://java.sun.com/javase/downloads/index.jsp")[/COLOR] right from SUN.
You want this:* jdk-6-linux-i586.bin*

**[COLOR="#248"]2. Download Eclipse[/COLOR]**
Download the 32bit Eclipse right from [COLOR="Blue"][eclipse.org]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/")[/COLOR]
You want this: *eclipse-SDK-3.2.1-linux-gtk.tar.gz *


**[COLOR="#248"]Installation[/COLOR]**
**A. **Eclipse simply needs to be extracted. 
**B.** The JDK requires that you run the install script. 
Rename the folder it produces to something simple: JDK6.32
**C.** Configure BASH to export the JAVA_HOME env variable like so: 


```

#BEG Copy and Paste
#Copy and Paste at the bottom of your /home/<user>/.bashrc file
#Then close all of your terminal windows. Reopen one, and type "eclipse"
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~
export JAVA_HOME='/home/<user>/Desktop/JDK6.32'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
#
# The eclipse alias below assumes that you have extracted the eclipse folder 
# to your desktop. It can be anywhere. Edit path as necessary
#
alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar'
#END Copy and Paste

```


**[COLOR="#248"]Additional Info[/COLOR]**
This is a very simple way to install the latest JDK. Obviously this method isn't supported by the package managers. You'll have to update on your own. The advantage is that the cooperation and performance of the two 32bit packages rivals the same on Windows. Also, this way, you can actually have multiple eclipses, JDK's, and, when you decide to, multiple Tomcat instances. They all can be installed in nearly the same way. 


**[COLOR="#248"]Notes[/COLOR]**
A few times I've downloaded the JDK, only to be presented with an error that a file could not be found, and that installation could not continue. It seems that, occasionally, the file available for download has been prepared incorrectly. Once the problem is reported, and a few hours go by, I try again with success. It doesn't happen often, but it's happened more than once.

---

### Post by lemone on 2007-02-26
I read that one easy way to "fix" this problem is to delete the .metadata directory under your workspace directory. ~/.workspace/.metadata is the default.

Of course, this will destroy all of your workspace settings, but it should be "fixed." I never bothered figuring out what the exact cause of the error was, but after removing that .metadata directory everything seemed to be working fine. Eclipse started properly and I could mess around with the workspace. Then I tried to recreate a rails project and got similar errors and the crash. This all started after installing libsvn-javahl, so I simply used synaptic to remove that package. All is well, except now I can't use subclipse.

Somebody more ambitious and/or with more experience might be able to shed some light.

---

### Post by Shadowed on 2008-03-22
> **lemone said:**
> I read that one easy way to "fix" this problem is to delete the .metadata directory under your workspace directory. ~/.workspace/.metadata is the default.

Of course, this will destroy all of your workspace settings, but it should be "fixed." I never bothered figuring out what the exact cause of the error was, but after removing that .metadata directory everything seemed to be working fine. Eclipse started properly and I could mess around with the workspace. Then I tried to recreate a rails project and got similar errors and the crash. This all started after installing libsvn-javahl, so I simply used synaptic to remove that package. All is well, except now I can't use subclipse.

Somebody more ambitious and/or with more experience might be able to shed some light.

Just waned to note that this solution worked for me as well.

My Eclipse with PHP crashed with the error message every time I tried to open most of the PHP files in my project. After deleting the .metadata directory under my workspace folder, I was able to open any of the files.

I also hope that someone more experienced can give a more 'adacemical' solution to this problem.

---

