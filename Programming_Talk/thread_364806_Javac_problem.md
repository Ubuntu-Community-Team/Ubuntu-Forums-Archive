---
title: "Javac problem"
date: 2007-02-18
forum: Programming Talk
---

### Post by Chaos-Energy on 2007-02-18
I used the following commands to set my paths

```
export JAVA_HOME=/usr/java/jdk1.5.0_11
export PATH=$JAVA_HOME/bin:$PATH
```

and everything works great (javac & java) but when I exit the terminal, restart it and try javac again it says "command not found". "java" still works but it already worked before I set the paths. It's like it forgets me setting the paths. :S

---

### Post by gtratter on 2007-02-18
I am just a beginner so hopefully what I say is true.
this is your code"
```

export JAVA_HOME=/usr/java/jdk1.5.0_11
export PATH=$JAVA_HOME/bin:$PATH

```

I don't see were you set your path, i.e.
```

JAVA_HOME=$PATH /usr/java/jdk1.5.0_11
export JAVA_HOME

```

and then I am not sure about your second line...so others will help out....

---

### Post by Kingsley on 2007-02-18
Try
export JAVA_HOME='/usr/java/jdk1.5.0_11'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH

And then type "source .bashrc" into the terminal.

---

### Post by Chaos-Energy on 2007-02-18
Still the same problem. :(

---

### Post by Unterseeboot_234 on 2007-02-19
Boy, the java paths seems to be a big deal on Ubuntu. Be aware there are three approches.

1. The IDEs such as NetBeans and Eclipse work because they slam the full pathname to the myjava_1.6/bin to find javac, java_vm, appletviewer, etc. every time you hit the Run button.

2. I never had luck modifying the CENTRAL .bash source file within ubuntu so any terminal window you open after that edit will have the correct paths. If you've ever done a .bat file to double-click in Windows while doing java, you can do the same thing with a shell script that you save inside whatever project folder. I prefer this way, because I can make sure the final java will work with the libraries and jars I am going to deploy.

```
#!/bin/sh
JAVA_HOME="/home/vcbrad/jdk1.5.0_10"
PATH=$JAVA_HOME/bin:$PATH
export PATH JAVA_HOME

java -version
java -classpath ./:/home/vcbrad/javaWork_1_5/java_stoffPlan_4/xperiments/stoffPlan_x_Mar01
java StoffPlanDesk
```

I deploy the above, composed in Text Editor, saved as java_StoffPlan.sh. I double-click it. Gnome pops up a four-choice dialog and I select "Run In Terminal" Note the colon ( : ) separates classpaths. Note -classpath is all one line. This would be how you run java from a university and/or corporate linux network sitting at the terminal. A shell script lets me include other things like Groovy Script, JMF libraries and jars from other projects included in my final application. I do most of my java code in NetBeans. When I'm ready, a shell script is the blueprint for making a small program written in C to launch a finished product with a desktop icon. And, I usually include the JRE inside the application and make the java link to it.

3. Check out this link, from the forums, to customize your installation of java.
[B][URL="http://www.ubuntuforums.org/showthread.php?t=319138"]
Java Custom Install[/URL][/B]

---

### Post by Chaos-Energy on 2007-02-19
I went through the HowTo guide and it seems to work perfect now. :)

Thanks!

---

### Post by Keffin on 2007-02-19
I know the OPs issue is now resolved, but since people have written odd things about the .bashrc file....

Putting the lines you require in your ~/.bashrc file will ensure that any new terminal you open has these variables set. i.e. edit ~/.bashrc and add the following lines to the bottom:
```
export JAVA_HOME=/usr/java/jdk1.5.0_11
export PATH=$JAVA_HOME/bin:$PATH
```
Then either run "source ~/.bashrc", or just close that terminal and fire up a new one. These variables will now always be set. Test using "echo $JAVA_HOME".

---

### Post by phossal on 2007-02-20
I advocated modifying .bashrc to include the JAVA_HOME variable when doing a manual installation (ie, SUN's .bin file) of the Java Development Kit (JDK). It doesn't solve a lot of the problems associated with mixed installation methods of java-dependent programs though. At least, it doesn't do it as cleanly and easily as it could be done. 

The package installation of Java takes advantage of update-alternatives, which is a path of links all the way from /usr/bin/java to /etc/alternatives/java to the actual JDK. The best way to enable *javac* and *javaws* then (so they're available for updates, etc) is to include them in update-alternatives by doing an installation using the update-alternatives command. Skipping that step though, you can make direct links from the JDK home to /usr/bin like this (in the case of the op):
```
sudo ln -s /usr/java/jdk1.5.0_11/bin/javac /usr/bin/javac
sudo ln -s /usr/java/jdk1.5.0_11/jre/javaws/javaws /usr/lib/javaws
```
The additional benefit to this approach is that the commands are available for multiple users.

---

