---
title: "Unable to install sun java 6 documentation on Ubuntu 12.04"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by maanu2k on 2013-05-01
Hi,

I am trying to install the java 6 sun documentation on 12.04 and have been unable to do so. I have tried the following steps :
 
1. Downloaded the jdk-6u30-doc.zip from sun.java.com
2. moved the zip file to /tmp and renamed it to jdk-6-doc.zip
3. changed the owner of the file to root using chown root:root jdk-6-doc.zip
4. ran the command sudo apt-get install sun-java6-doc.zip

All I get as output is :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sun-java6-doc

Please help![IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]

---

### Post by claracc on 2013-05-01
You just need to download the .zip file an extract the files inside the  .zip (compressed) with the unzip command  (run it in a xterm), more information about unzip command: man unzip. When you do the extraction of the files, a /docs folder will appear, below the folder you are, inside it, it will be all the documentation.

 As the .zip file probably will be downloaded to you /home/name_of_user/Downloads folder, you can move it to any other folder in your /home directory, in this case you don't need to use the root user.

The 4 step which you have tried " ran the command sudo apt-get install sun-java6-doc.zip" doesn't have any sense, since the file .zip in not a .deb one (executable).

---

### Post by hendrel on 2013-05-02
Step 1: 

sudo apt-get install unzip

Step 2: 

unzip jdk-6-doc.zip

---

### Post by mörgæs on 2013-05-02
Is there a particular reason that you are using Java 6 and not 7?

---

### Post by maanu2k on 2013-05-06
Claracc, the steps which I mentioned are the steps which I got from searching through the forum e.g. [here]("http://ubuntuforums.org/showthread.php?t=1232175&p=7747882#post7747882"). However, there is an error in my step 4, it should be [COLOR=#000000] " ran the command sudo apt-get install sun-java6-doc" rather than [/COLOR][COLOR=#000000] " ran the command sudo apt-get install sun-java6-doc.zip". [/COLOR]

---

### Post by maanu2k on 2013-05-06
Thanks for replying morgaes. I am not sure of a reason why I am using Java 6. I am trying to learn Java and the Ubuntu 12.04 on my laptop has Java 6 on it and I have not yet updated it to Java 7.

---

### Post by maanu2k on 2013-05-06
Thanks hendrel. Where should I unzip the docs zip file, in /usr/lib/jvm/java-1.7.0-openjdk-amd64? I actually installed jdk7 and jre7.

---

### Post by QIII on 2013-05-06
If you are trying to install Oracle Java 7, please see the Java wiki in my signature.  Look for the section "Oracle Java 7", "Command line methods" and follow the link "Using webupd8.org's strikingly simple method"

---

### Post by sammiev on 2013-05-06
Here is the [manual]("https://sites.google.com/site/easylinuxtipsproject/java") way of doing it for jre7 (sun java 7)

Auto way using a [PPA]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html").

---

### Post by hendrel on 2013-05-07
You can place your documentation in your home directory. /usr/share/doc will also work. :)

---

### Post by slickymaster on 2013-05-07
> **claracc said:**
> You just need to download the .zip file an extract the files inside the  .zip (compressed) with the unzip command  (run it in a xterm), more information about unzip command: man unzip. When you do the extraction of the files, a /docs folder will appear, below the folder you are, inside it, it will be all the documentation.

 As the .zip file probably will be downloaded to you /home/name_of_user/Downloads folder, you can move it to any other folder in your /home directory, in this case you don't need to use the root user.

The 4 step which you have tried " ran the command sudo apt-get install sun-java6-doc.zip" doesn't have any sense, since the file .zip in not a .deb one (executable).
claracc is right.
Javadoc is a documentation in HTML format that holds every standard class in the java programming language. The HTML format is used to add the convenience of being able to hyperlink related documents together.
Basically all you have to do is to download it, unzip it and use your web browser to access it.
> **mörgæs said:**
> Is there a particular reason that you are using Java 6 and not 7?
[COLOR=#000000]mörgæs is also right when he asked you why Java 6 and not Java 7.
[/COLOR][COLOR=#000000]Java 7 is a major feature release and includes lots of features and enhancements like [/COLOR][COLOR=#000000]strings in switch statements, multi-catch exception handling, try-with-resource statements, the new File System API, extensions of the JVM, support for dynamically-typed languages, the fork and join framework for task parallelism. Check this: [/COLOR][COLOR=#000000][Java SE 7 Features and Enhancements]("http://www.oracle.com/technetwork/java/javase/jdk7-relnotes-418459.html").

Another thing, as you say you're trying to learn Java, you might be interested in checking these, also:
[/COLOR][Java Tutorials Learning Paths]("http://docs.oracle.com/javase/tutorial/tutorialLearningPaths.html")
[Collected Java Practices]("http://www.javapractices.com/home/HomeAction.do")
[Learn basics of java, tutorial for beginners, examples online]("http://www.java2all.com/")

---

