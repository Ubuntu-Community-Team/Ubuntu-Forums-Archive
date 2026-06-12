---
title: "Java errors (missing files?)"
date: 2007-01-29
forum: Programming Talk
---

### Post by EricDallal on 2007-01-29
I can't open eclipse. I always get an error telling me that an error has occurred and that I should check a log file (attached). When I tried to run gksudo eclipse, I got the following output:

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-1.5.0-sun...found

at which point I got the same error message.

I tried changing the version of Java by running sudo update-alternatives --config java, but that didn't help either. I also changed the file /etc/eclipse/java_home to use Sun's JVM. When I tried running gksudo eclipse again, I got the following output:

searching for compatible vm...
  testing /usr/lib/jvm/java-1.5.0-sun/jre/bin/java...not found
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-1.5.0-sun...found

Can anybody help me figure out what's wrong? Do I need to reinstall some package?

Thanks in advance for any help you can give me.

Eric

---

### Post by amo-ej1 on 2007-01-29
have you tried running eclipse -vm <path/to/your/vm> that way you can force eclipse to use a certain JVM.

---

### Post by EricDallal on 2007-01-29
I thought that's what changing the file /etc/eclipse/java_home does. I'll try it this way too. Is the path to the JVM the same as that given when using the command:
sudo update-alternatives --config java ?

---

### Post by EricDallal on 2007-01-29
I tried doing:
eclipse -vm /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
and I got exactly the same error. From the log file, I see class not found error happening at least once. I would like to try to reinstall the JVM but I'm not sure which package(s) to install to do that.

---

### Post by phossal on 2007-01-29
How did you install Java, and how did you install eclipse?

Please post the output to:
```
sudo update-alternatives --display java
java -version
echo $JAVA_HOME
```

---

### Post by EricDallal on 2007-01-29
eric@eric-laptop:~$ sudo update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/j2se/1.4/bin/java - priority 1411
 slave java.1.gz: /usr/share/man/man1/java.j2se14.1.gz
 slave java.ja.1.gz: /usr/share/man/ja/man1/java.j2se14.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/j2se/1.4/bin/java.
eric@eric-laptop:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Server VM (build 1.5.0_08-b03, mixed mode)
eric@eric-laptop:~$ echo $JAVA_HOME

The command "echo $JAVA_HOME" printed only a blank line.

---

### Post by phossal on 2007-01-29
Try this:
```
sudo gedit ~/.bashrc
```

Copy and paste this at the bottom, save and close:
```
export JAVA_HOME='/usr/lib/jvm/java-1.5.0-sun'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
```

```
source ~/.bashrc
```

Then try to launch eclipse.

---

### Post by EricDallal on 2007-01-29
Thanks, but it still doesn't work. The error is exactly the same. I noticed that your signature had a link for installing Java and Eclipse. Should I try following those instructions?

---

### Post by phossal on 2007-01-29
Yeah. Definitely! I doubt you would have the same troubles, but it will be significantly easier for me to assist you. Currently, I can't figure out what you've done, whether you've installed the JRE, or JDK, etc. Give it a shot, and I'll walk you through it if you have any troubles. Just to note, you *need* the JDK, and not just the JRE. Just one favor, let's walk though it here, because I just asked Taurus to remove previous posts from the tutorial. :)

---

### Post by EricDallal on 2007-01-29
Should I uninstall anything first, or just do the installation of Java and Eclipse over the current installations?

---

### Post by phossal on 2007-01-29
There isn't really a need to download eclipse again. Just download Java. You'll need to complete the installation of the JDK in post #1. You can AIM me, if you want.

---

### Post by EricDallal on 2007-01-29
Do I need to add the line:

alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar'

also (modifying accordingly), since I installed Eclipse from the add/remove programs? If so, I am not certain where the file would be. I could always try using the find command. If not, then I am still having the same bug.

---

### Post by phossal on 2007-01-29
Nope. No need for that. 

Now, try this again:
sudo update-alternatives --display java
java -version

---

### Post by EricDallal on 2007-01-29
eric@eric-laptop:~$ sudo update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/j2se/1.4/bin/java - priority 1411
 slave java.1.gz: /usr/share/man/man1/java.j2se14.1.gz
 slave java.ja.1.gz: /usr/share/man/ja/man1/java.j2se14.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/j2se/1.4/bin/java.
eric@eric-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Server VM (build 1.6.0-b105, mixed mode)

---

### Post by phossal on 2007-01-29
Almost there. What's the output to:

```
echo $JAVA_HOME
echo $PATH
```

---

### Post by EricDallal on 2007-01-29
I obtained the following upon verification:

java - status is manual.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/j2se/1.4/bin/java - priority 1411
 slave java.1.gz: /usr/share/man/man1/java.j2se14.1.gz
 slave java.ja.1.gz: /usr/share/man/ja/man1/java.j2se14.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/man/man1/java.1.gz
/usr/lib/Java6/bin/java - priority 300
Current `best' version is /usr/lib/j2se/1.4/bin/java.

I'm reviewing the steps to make sure I didn't miss anything, and that all the files are in the right place, but I don't think I missed anything.

---

### Post by phossal on 2007-01-29
Do you have a Java folder on your desktop? What is it named?

---

### Post by EricDallal on 2007-01-29
This is the output

eric@eric-laptop:~$ echo $JAVA_HOME
/home/eric/Java6
eric@eric-laptop:~$ echo $PATH
/home/eric/Java6:/home/eric/Java6/bin:/home/eric/Java6/jre/bin:/home/eric/Desktop/Java6:/home/eric/Desktop/Java6/bin:/home/eric/Desktop/Java6/jre/bin:/usr/lib/jvm/java-1.5.0-sun:/usr/lib/jvm/java-1.5.0-sun/bin:/usr/lib/jvm/java-1.5.0-sun/jre/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

---

### Post by EricDallal on 2007-01-29
Actually, I downloaded to /home/eric, so it's in there, not on the desktop. I modified the bashrc file accordingly though.

---

### Post by phossal on 2007-01-29
All right:

```
sudo mv /home/eric/Java6 /usr/lib/Java6
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6/bin/java 300
```

Then update your .bashrc to this (gedit ~/.bashrc):
```

export JAVA_HOME='/usr/lib/Java6'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH

```

```
source ~/.bashrc
```

---

### Post by EricDallal on 2007-01-29
Done, but still getting the same error.

---

### Post by phossal on 2007-01-29
Confirm something for me....

After all of this work, eclipse will likely launch from the command line. If you open a terminal, and type eclipse, I'm almost sure it will launch. But it probably *won't* from the menu. Let's confirm it launches, and we'll fix the second problem.

---

### Post by EricDallal on 2007-01-29
It launches, outputs:
using specified vm: /usr/lib/Java6
and then gives me the same error message and .log file like before. The splash pops up, but the progress bar never starts moving, and the application closes with that error.

---

### Post by phossal on 2007-01-29
I hate this, but you can add this to /etc/eclipse/java_home
```
/usr/lib/Java6
```

---

### Post by EricDallal on 2007-01-29
I should mention that I used to have errors with dpkg (serious warning) whenever I used the add/remove programs. I eventually got rid of them by doing purge, and then trying to reinstall eclipse. This is why I have a tendency to think that there might be some missing files somewhere.

---

### Post by EricDallal on 2007-01-29
That didn't solve the problem.

---

### Post by phossal on 2007-01-29
Well, back to basics. If you download eclipse from eclipse.org, it's as easy as extracting it. You launch it with the java -jar command. As long as JAVA_HOME is set, it will work. The downside is that you'll have to move it around and/or adjust your menus, etc.

---

### Post by EricDallal on 2007-01-29
This time, should I uninstall the current Eclipse?

---

### Post by phossal on 2007-01-29
*IF* you download the file directly from eclipse, and extract it to your desktop, it has nothing to do with anything. It sort of exists in isolation.

Before people started asking all kinds of questions, that's how I *recommended* people do it, which is why post#1 in the tutorial doesn't include any other steps. I download the JDK to my desktop, eclipse to my desktop, and never 'include' them into my system. That way, I can package the files and move them around as I want, as I would during a backup.

---

### Post by EricDallal on 2007-01-29
Fantastic! It works. I would also like to install CDT. Normally, I would do it through the adept package manager. Would I have to do it differently in this case?

---

### Post by phossal on 2007-01-29
Yes, you'll have to do it differently. Same situation as eclipse. You'll download it directly, incorporate the cdt folder/plugins as necessary, and then launch eclipse. In a way, it's *easier*.

---

### Post by EricDallal on 2007-01-30
I changed the menu layout to get the new eclipse to run. Works nicely. I want to thank you for your help. You are far more patient than most people I know.

Thank you :D

---

### Post by phossal on 2007-01-30
lol You're very welcome. To confirm the bit about CDT. I downloaded it myself in the meantime. I transferred the guts of the CDT/plugins folder to Eclipse/Plugins, and the same with features. It's that simple.

Enjoy eclipse. Have a good day/evening. Cheers!

---

