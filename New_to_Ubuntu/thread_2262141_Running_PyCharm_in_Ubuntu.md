---
title: "Running PyCharm in Ubuntu"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by rbengr on 2015-01-23
Hi,

I'm trying to run PyCharm in the Ubuntu Terminal.  I have navigated to the bin directory which contains pycharm.sh.  It is green in color.  How do I proceed?  Thanks.

---

### Post by slickymaster on 2015-01-23
Either double click it or at a terminal window run```
pycharm.sh
```Once it opens, it either offers you to create a desktop entry, or if it doesn't, you can ask it to do so by going to the Tools menu and selecting Create Desktop Entry...

Then close PyCharm, and in the future you can just click on the created menu entry. (or copy it onto your Desktop)

---

### Post by rbengr on 2015-01-23
Thanks for your reply.  When I type pycharm.sh in the Terminal it says: pycharm.sh: command not found

---

### Post by slickymaster on 2015-01-23
Try this (assuming you're already in the bin directory):```
[s]sudo[/s]./pycharm.sh
```

---

### Post by rbengr on 2015-01-23
I get  ERROR:  Cannot start Pycharm  No JDK found.

---

### Post by Holger_Gehrke on 2015-01-23
The shell looks for executable files **only** in the directories that are in the list stored in the environment variable $PATH. The current working directory is **not** automatically searched by default (that's a security feature. Imagine someone creating a shellscript, that erases your harddisk and saving it as 'ls' in your home directory ...). You have to explicitly give the directory when you want to execute a program that's not in the $PATH. So try:

```

./pycharm

```

sudo is not needed here, actually even somewhat harmful,since then files created with pycharm in this session - like for example a configuration -  will be owned by root.

---

### Post by slickymaster on 2015-01-23
Apparently you don't have Java installed. Just to confirm this, please post back in the thread the output you get from```
java -version
```and```
javac -version
```

---

### Post by rbengr on 2015-01-23
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.8-jre-headless
 * openjdk-7-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
engine44@engine44-VirtualBox:~/Downloads/pycharm-community-4.0.4/bin$ javac -version
The program 'javac' can be found in the following packages:
 * default-jdk
 * ecj
 * gcj-4.8-jdk
 * openjdk-7-jdk
 * gcj-4.6-jdk
 * openjdk-6-jdk
Try: sudo apt-get install <selected package>

---

### Post by slickymaster on 2015-01-23
> **rbengr said:**
> The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.8-jre-headless
 * openjdk-7-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
engine44@engine44-VirtualBox:~/Downloads/pycharm-community-4.0.4/bin$ javac -version
The program 'javac' can be found in the following packages:
 * default-jdk
 * ecj
 * gcj-4.8-jdk
 * openjdk-7-jdk
 * gcj-4.6-jdk
 * openjdk-6-jdk
Try: sudo apt-get install <selected package>
Right, you don't have it in your system, that's the reason why you got that error message.

Again in a terminal window run the following commands, one at a time```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```Afterwards try again to start PyCharm.

---

### Post by slickymaster on 2015-01-23
> **Holger_Gehrke said:**
> The shell looks for executable files **only** in the directories that are in the list stored in the environment variable $PATH. The current working directory is **not** automatically searched by default (that's a security feature. Imagine someone creating a shellscript, that erases your harddisk and saving it as 'ls' in your home directory ...). You have to explicitly give the directory when you want to execute a program that's not in the $PATH. So try:

```

./pycharm

```

sudo is not needed here, actually even somewhat harmful,since then files created with pycharm in this session - like for example a configuration -  will be owned by root.

You are right, there's no need for sudo in this case, since the OP is in a directory under his home directory.

I think the reason for the error message he got isn't related with the environment variable $PATH, but with the nonexistence of Java in his system.

---

### Post by rbengr on 2015-01-23
Yeah, it worked.  Thank you very much for your time.  One last thing.  I would like to put a PyCharm icon in the Ubuntu launcher.  Is that possible?

---

### Post by slickymaster on 2015-01-23
Once PyCharm opens, it either offers you to create a desktop entry, or if it doesn't, you can ask it to do so by going to the Tools menu and selecting Create Desktop Entry...

Then close PyCharm, and in the future you can just click on the created menu entry (or copy it onto your Desktop).

---

### Post by rbengr on 2015-01-23
The Pycharm icon is now in the launcher.  Thanks

---

### Post by slickymaster on 2015-01-23
You're welcome.

Please [mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that this thread provides a working solution.

---

### Post by Derrick_Katula on 2015-01-23
First, you need to make sure you have Oracle java installed. See [here]("http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-6-7-jre-or-jdk") on how to do that.

  Then, just run the pycharm executable from the expanded archive. It will be in the bin directory.

---

