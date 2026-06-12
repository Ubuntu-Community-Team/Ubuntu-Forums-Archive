---
title: "Ant cant locate tools.jar"
date: 2012-05-10
forum: Programming Talk
---

### Post by Flame_Phoenix on 2012-05-10
Hello, a few days ago I installed "ant" to use AspectJ in Android:
[http://blog.punegtug.org/2010/11/adding-aspect-to-android.html](http://blog.punegtug.org/2010/11/adding-aspect-to-android.html)

However, I can't use ant because when I invoke it using the terminal I get:
```

Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk-i386/lib/tools.jar
Buildfile: build.xml does not exist!
Build failed

```

I found a similar thread with a few years:
[http://ubuntuforums.org/showthread.php?t=634996](http://ubuntuforums.org/showthread.php?t=634996)

(Decided to not post there to avoid necro posting or necro revival, mainly because it is a bannable offense in some forums. I apologize if I did wrong).

When I do "apt-get install sun-java6-jdk" I also get:
```

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate

```

So, i can't really fix this problem that way. The last post of the thread says that I should change the $HOME/.bashrc file, but since I don't have sun-java6-jdk and since it seems to be discontinued I don't think it's a good idea to do it. 

What insight can you guys give me?
Thanks in advance.

---

### Post by r-senior on 2012-05-10
Try installing the openjdk-7-jdk package to get the JDK and post back if that doesn't get ant working.

---

### Post by Flame_Phoenix on 2012-05-10
I installed it but I still have the same problem:
```

AB9:~$ ant
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk-i386/lib/tools.jar
Buildfile: build.xml does not exist!
Build failed

```

---

### Post by r-senior on 2012-05-10
What happens if you run it like this?

```
ant -noclasspath
```

---

### Post by Flame_Phoenix on 2012-05-10
```

AB9:~$ ant -noclasspath
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk-i386/lib/tools.jar
Buildfile: build.xml does not exist!
Build failed

```

The same thing :s

---

### Post by r-senior on 2012-05-10
OK, let's follow your javac through and see where it is installed:

```
$ which javac
[COLOR="Red"]/usr/bin/javac[/COLOR]
$ ls -l [COLOR="Red"]/usr/bin/javac[/COLOR]
lrwxrwxrwx 1 root root 23 May  2 10:02 /usr/bin/javac -> [COLOR="SeaGreen"]/etc/alternatives/javac[/COLOR]
$ ls -l [COLOR="SeaGreen"]/etc/alternatives/javac[/COLOR]
lrwxrwxrwx 1 root root 43 May  2 10:02 /etc/alternatives/javac -> [COLOR="Blue"]/usr/lib/jvm/java-7-openjdk-amd64/bin/javac[/COLOR]
$ ls -l [COLOR="Blue"]/usr/lib/jvm/java-7-openjdk-amd64/bin/javac[/COLOR]
-rwxr-xr-x 1 root root 6352 Apr 13 04:00 /usr/lib/jvm/java-7-openjdk-amd64/bin/javac
```

Your results may not be quite the same as mine. Just follow through the commands and follow the chain of links until you get to the javac executable.

Post the results.

Did you already have openjdk-6 installed?

Also, do you have CLASSPATH and/or JAVA_HOME variables set?

```
echo $JAVA_HOME 
echo $CLASSPATH
```

Will you be using ant from the command line, or using Eclipse?

Let's also try this:

```
update-alternatives --get-selections | grep ^java
```

---

### Post by Flame_Phoenix on 2012-05-10
Ouch ... that's a lot of command lines 

The first one:
```

AB9:~$ which javac
/usr/bin/javac
AB9:~$ ls -l /usr/bin/javac
lrwxrwxrwx 1 root root 23 May  3 10:51 /usr/bin/javac -> /etc/alternatives/javac
AB9:~$ ls -l /etc/alternatives/javac
lrwxrwxrwx 1 root root 42 May 10 19:03 /etc/alternatives/javac -> /usr/lib/jvm/java-7-openjdk-i386/bin/javac
AB9:~$ ls -l /usr/lib/jvm/java-7-openjdk-i386/bin/javac
-rwxr-xr-x 1 root root 5604 Apr 13 09:39 /usr/lib/jvm/java-7-openjdk-i386/bin/javac

```

It appears my results are very similar to yours: I have an i386 architecture and you have amd64, plus some permissions are different.

Yes, I believe I had jdk-6 installed.

About $JAVA_HOME and $CLASSPATH, they don't seem to be defined ... ops :s

I believe I will be using the Eclipse IDE, though to be honest the tutorial I have indicated before doesn't seem to make much use of it (lol). I have never worked with ant before, so I guess I will have t find my way around this.

As for the final command line sequence:
```

AB9:~$ sudo update-alternatives --get-selections | grep ^java
java                           auto     /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
javac                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javac
javadoc                        auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
javah                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javah
javap                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javap
javaws                         auto     /usr/lib/jvm/java-6-openjdk-i386/jre/bin/javaws
AB9:~$ 

```

And thanks for all the effort and time you are spending to help me. I see no one else doing it.

---

### Post by r-senior on 2012-05-10
Well done for getting all the correct info. =D>

It shouldn't be necessary to define JAVA_HOME and CLASSPATH, I was just checking they weren't defined because they can mess things up.

I think the problem is that ant is running using the JRE from openjdk-6-jre but tools.jar comes from openjdk-7-jdk and it's not finding it.

Do you need openjdk-6-jre for anything? If you were to uninstall it, the JRE should then pick up from openjdk-7-jre (which should be installed as a dependency of openjdk-7-jdk) and you should be OK.

```
sudo apt-get remove openjdk-6-*
```

Or, if you want to keep JDK 6 -- I can't think why anyone would -- this should do it (but I can't test it on my 64-bit machine):

```
sudo update-java-alternatives -s java-7-openjdk-i386
```

Basically you want all this to be java-7-openjdk stuff:

```
AB9:~$ sudo update-alternatives --get-selections | grep ^java
java                           auto     /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
javac                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javac
javadoc                        auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
javah                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javah
javap                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javap
javaws                         auto     /usr/lib/jvm/java-6-openjdk-i386/jre/bin/javaws
```

Then the output you want from ant is this:

```
$ ant
Buildfile: build.xml does not exist!
Build failed

```

That's the message you'd expect with no build.xml in the current directory.

---

### Post by Flame_Phoenix on 2012-05-11
The reason I need openjdk-6 is because of a program calle "Jedit" (with J for java). You should try it, it's a really good text program, and it totally beats the crap out of Gedit :D
I tried running the second command line this is what I got:
```

AB9:~$ sudo update-java-alternatives -s java-7-openjdk-i386
update-java-alternatives: file does not exist: /usr/lib/jvm/.java-7-openjdk-i386.jinfo

```

So, I removed the openjdk-6 and now this is what I have:
```
AB9:~$ sudo update-alternatives --get-selections | grep ^java
java                           auto     /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
javac                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javac
javadoc                        auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
javah                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javah
javap                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javap
javaws                         auto     /usr/lib/jvm/java-6-openjdk-i386/jre/bin/javaws

```

As expected ! Awesome! 
Now when I invoke ant the output is also the one expected:
```
AB9:~$ ant
Buildfile: build.xml does not exist!
Build failed

```
Thanks, that really helped!

The only problem is that now I don't have my good old Jedit =( 
Now all I need to know is where to put that XML file and how to integrate ant with eclipse. Maybe you can give a hint on where to start? (Never used ant before lol).

Anyway thanks for all the help! I would totally give you a bag of coffee beans if I could xD

problem solved!

---

### Post by r-senior on 2012-05-11
Good! 

I tend to use Maven these days but I know Eclipse integrates well with Ant and there's plenty of documentation:

[http://www.eclipse.org/eclipse/ant/index.php](http://www.eclipse.org/eclipse/ant/index.php)
[http://help.eclipse.org/indigo/index.jsp?topic=%2Forg.eclipse.platform.doc.user%2FgettingStarted%2Fqs-81_basics.htm](http://help.eclipse.org/indigo/index.jsp?topic=%2Forg.eclipse.platform.doc.user%2FgettingStarted%2Fqs-81_basics.htm)
[http://ant.apache.org/manual/](http://ant.apache.org/manual/)

Just as a footnote to all of this, anyone who wants to use ant on Ubuntu 12.04 should just install the ant and openjdk-7-jdk packages and it should be good to go.

ps. I'd rather a francesinha than coffee beans but they don't travel well!

---

### Post by gmcgath on 2012-09-09
I'd just like to thank r_senior for this information. I had openjdk 6 on my machine and ran into page after page of bad advice on how to fix the tools.jar problem before finding this, which worked perfectly.

---

### Post by villeit on 2012-09-21
Hi,

I have been running on similar problems but the difference was that I installed the Oracle's JAVA EE version but it never worked for me so I removed it and installed OpenJDK 7.
When I run ant after it but I get the following error:
```
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-7-openjdk-i386/lib/tools.jar
Buildfile: build.xml does not exist!

```This is my JVM directory in "/usr/lib/jvm$"
```
java-1.7.0-openjdk-i386 -> java-7-openjdk-i386
.java-1.7.0-openjdk-i386.jinfo
java-7-openjdk-common
java-7-openjdk-i386

```
I also ran this command:
```
sudo update-java-alternatives -s java-7-openjdk-i386
```

With the following output:
```
update-java-alternatives: file does not exist: /usr/lib/jvm/.java-7-openjdk-i386.jinfo
```

---

### Post by gadakty2012 on 2012-11-22
Hello, this helped me a lot too. In my case, the problem is that I had $JAVA_HOME defined and it was pointing the path of my jre (/usr/local/java/jre1.7.0_05) instead of the jdk(/usr/local/java/jdk1.7.0_05). tools. java is located in the lib path of jdk1.7.0_05

Thanks a great deal.

---

### Post by Code Warrior on 2013-04-17
Hi!

```
update-alternatives --get-selections | grep ^java
java                           auto     /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
javac                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javac
javadoc                        auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
javah                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javah
javap                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javap

```


The below error was due to java7 versus java 1.7.0 naming conflict.


```
/usr/sbin/update-java-alternatives -s java-7-openjdk-i386
update-java-alternatives: file does not exist: /usr/lib/jvm/.java-7-openjdk-i386.jinfo
```


I tried the following ...

```
sudo cp /usr/lib/jvm/.java-1.7.0-openjdk-i386.jinfo /usr/lib/jvm/.java-7-openjdk-i386.jinfo
sudo /usr/sbin/update-java-alternatives -s java-7-openjdk-i386
```


Now you'll see java executable used is from jdk7 instead of jdk6

```
update-alternatives --get-selections | grep ^java
java                           manual   /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
javac                          manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javac
javadoc                        manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
javah                          manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javah
javap                          manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javap
```


so it works!:KS No error from ant in locating tools.jar

---

### Post by Code Warrior on 2013-04-17
[COLOR=#000000]Hi![/COLOR]

[COLOR=#000000]
```
update-alternatives --get-selections | grep ^java
java                           auto     /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
javac                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javac
javadoc                        auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
javah                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javah
javap                          auto     /usr/lib/jvm/java-7-openjdk-i386/bin/javap
```[/COLOR]

[COLOR=#000000]The below error was due to java7 versus java 1.7.0 naming conflict.[/COLOR]


[COLOR=#000000]```
/usr/sbin/update-java-alternatives -s java-7-openjdk-i386
update-java-alternatives: file does not exist: /usr/lib/jvm/.java-7-openjdk-i386.jinfo
```[/COLOR]

[COLOR=#000000]I tried the following ...[/COLOR]

[COLOR=#000000]```
sudo cp /usr/lib/jvm/.java-1.7.0-openjdk-i386.jinfo /usr/lib/jvm/.java-7-openjdk-i386.jinfo
sudo /usr/sbin/update-java-alternatives -s java-7-openjdk-i386
```[/COLOR]

[COLOR=#000000]Now you'll see java executable used is from jdk7 instead of jdk6[/COLOR]

[COLOR=#000000]```
update-alternatives --get-selections | grep ^java
java                           manual   /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
javac                          manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javac
javadoc                        manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
javah                          manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javah
javap                          manual   /usr/lib/jvm/java-7-openjdk-i386/bin/javap
```[/COLOR]

[COLOR=#000000]so it works![/COLOR]:KS[COLOR=#000000] No error from ant in locating tools.jar[/COLOR]


> **villeit said:**
> Hi,

I have been running on similar problems but the difference was that I installed the Oracle's JAVA EE version but it never worked for me so I removed it and installed OpenJDK 7.
When I run ant after it but I get the following error:
```
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-7-openjdk-i386/lib/tools.jar
Buildfile: build.xml does not exist!

```This is my JVM directory in "/usr/lib/jvm$"
```
java-1.7.0-openjdk-i386 -> java-7-openjdk-i386
.java-1.7.0-openjdk-i386.jinfo
java-7-openjdk-common
java-7-openjdk-i386

```
I also ran this command:
```
sudo update-java-alternatives -s java-7-openjdk-i386
```

With the following output:
```
update-java-alternatives: file does not exist: /usr/lib/jvm/.java-7-openjdk-i386.jinfo
```

---

