---
title: "Setting Java Path HELP !!!"
date: 2009-12-22
forum: Programming Talk
---

### Post by D3mon_Spawn on 2009-12-22
Wuts up everyone, I recently just installed Java w/Netbeans on my computer and can't seem to figure out how to set the PATH for Java. I have the JDK installed here: /home/john/jdk1.6.0_17, and Netbeans installed here: /home/john/netbeans-6.8. I'm not sure if there is a better place to install the JDK and Netbeans, but I just let it stay in my home dir since that was where the default installer put them. Anyway, Java works fine when I'm writing and compiling in netbeans, but when I'm doing stuff from the terminal it doesn't even recognize that I have Java: 

john@Blue-Box:~/Desktop$ javac HelloWorld.java
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
javac: command not found

Any suggestions....??

---

### Post by Queue29 on 2009-12-22
If I were you, I'd just install the Sun JDK (or open JDK) and call it done, but you can set your path (in a bash shell) with the command:

PATH=/path/to/files/:$PATH

If you want it to stick between reboots, you'll need to add it to your .bashrc file, located in ~/.bashrc

Welcome to the linux way! :KS

---

### Post by jtuchscherer on 2009-12-23
You can also just add a symlink:

sudo ln -s /home/john/jdk1.6.0_17/bin/javac /usr/bin/javac
sudo ln -s /home/john/jdk1.6.0_17/bin/java /usr/bin/java

If you go that route you might want to create a symlink for your java installation so that when you upgrade you only need to update the first symlink:

ln -s  /home/john/jdk1.6.0_17 /home/john/jdk1.6
sudo ln -s /home/john/jdk1.6/bin/javac /usr/bin/javac
sudo ln -s /home/john/jdk1.6/bin/java /usr/bin/java

---

### Post by Zugzwang on 2009-12-24
@OP: Please use the last advice only in a modified form, if at all. *Never* put some file to /usr/share/bin, /usr/bin or /bin manually. If you want to do things like that, always use /usr/local/bin as in the other directories, files might need to be overwritten by the packaging system.

By the way, the "Ubuntu" way of installing the Sun jdk is just to run "sudo apt-get install sun-java6-jdk" instead of installing it manually (as the message you got suggested). This would have also fixed your problem. Also see the stickies if you have problems and multiple JDKs installed.

---

### Post by jtuchscherer on 2009-12-27
> **Zugzwang said:**
> @OP: Please use the last advice only in a modified form, if at all. *Never* put some file to /usr/share/bin, /usr/bin or /bin manually. If you want to do things like that, always use /usr/local/bin as in the other directories, files might need to be overwritten by the packaging system.

By the way, the "Ubuntu" way of installing the Sun jdk is just to run "sudo apt-get install sun-java6-jdk" instead of installing it manually (as the message you got suggested). This would have also fixed your problem. Also see the stickies if you have problems and multiple JDKs installed.

I agree with the first part of your post. The link should go into /usr/local/bin/

But I disagree on your second point. If you develop java software (and that is the main reason to install the jdk) I would go with the release from sun. Ubuntu is always behind with its jdk packages. The current version in karmic is the jdk6 update 16 release. Nearly two month ago sun released the update 17 version which contains critical security fixes. Obviously I want my server to run the newest version and since I develop software that is supposed to run on that server I need that version locally as well. Therefore I never use the java version from the ubuntu repos. I cannot advise following the 'ubuntu' way, if you develop java software.

---

