---
title: "Installing Java for games"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by fcogburn on 2013-03-04
Hello everyone, I'm sure this has been asked over and over again, but I very new to Ubuntu and need to know how to install Java, It is required for some games my wife plays. Thanks for any assistance.

---

### Post by siddharth007 on 2013-03-05
Well you might need a java runtime(JRE) and integrate it with the web browser you play games on.You can download JRE from [here]("http://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html").I am assuming that you use Ubuntu,so download the 'tar' file(the one with extension .tar.gz).Also download the package according to your processor.(For 32 bit processor it is x86 and 64 bit it is x64).Once you have downloaded the package,untar it.Use this command on the command line. 
```
tar -zxvf packagename
```

Once done run the setup script to install JRE.You can google out to find out how to integrate the JRE plugin with the browser.

---

### Post by siddharth007 on 2013-03-05
For the complete procedure follow this [link]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux")

---

### Post by Cheesemill on 2013-03-05
Have you read the wiki page?
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by fcogburn on 2013-03-05
Hey thanks everyone! Got it solved. Just Googleed it and went to, [www.julianfernandez.com]("http://www.julianfernandez.com"), and bingo! Downloaded, installed it and worked like a champ! Thank you Julian Fernandez for a great site! Mark this one solved!

---

### Post by flyfishingphil on 2013-03-18
Not crazy yet but just about to get there. Not real "up to speed" on how to do this but not having any luck at all installing Java 7-17 following the step-by-step ggiven above. I only get a short distance and run into the wall on going any further. Below is what shows up as I follow the directions. Any suggestions for somebody that doesn't "speak" linux or computer?

Thanks for the assist. Here's what I get in terminal:

flyfishingphil@flyfishingphil-Satellite-L305:~$ java -version
java version "1.7.0_15"
Java(TM) SE Runtime Environment (build 1.7.0_15-b03)
Java HotSpot(TM) Server VM (build 23.7-b01, mixed mode)
flyfishingphil@flyfishingphil-Satellite-L305:~$ cd /home/"flyfishingphil"/Downloads
flyfishingphil@flyfishingphil-Satellite-L305:~/Downloads$ sudo -s cp -r jre-7u17-linux-i586.tar.gz /usr/local/java
[sudo] password for flyfishingphil: 
flyfishingphil@flyfishingphil-Satellite-L305:~/Downloads$ cd /usr/local/java
bash: cd: /usr/local/java: Not a directory
flyfishingphil@flyfishingphil-Satellite-L305:~/Downloads$ 

Do I need to go in somewhere and remove everything java related and start over? If so, any place there are step-by-steps on that? Do I need to get into "Root" and, if so, how do I do that?

Thanks for helping somebody that is lost in the "forest"!

ffp

---

### Post by Cheesemill on 2013-03-18
Instead of downloading and installing Java manually just use the following commands...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
This method is under the title 'Using webupd8.org's strikingly simple method' on the Ubuntu Java wiki page.


In case you are still interested in continuing with the manual installation you've got a typo in the following command...
```
sudo -s cp -r jre-7u17-linux-i586.tar.gz /usr/local/java
```
What you've done is copied the jre-7u17-linux-i586.tar.gz file to a file called java in the /usr/local directory.
If you intended to copy the file into the /usr/local/java directory you needed an extra / at the end of the command...
```
sudo -s cp -r jre-7u17-linux-i586.tar.gz /usr/local/java[COLOR=#ff0000]/[/COLOR]
```

---

### Post by QIII on 2013-03-18
The absolutely easiest way to do this is to go to the Java wiki in my signature, "Oracle Java 7", "Command line methods", "Using webupd8.org's strikingly simple method"

Edit:  Ninja'd by Cheesemill!

I used the word "strikingly" in the wiki for a reason!

---

### Post by flyfishingphil on 2013-03-18
Muchas Gracias!!!

Tood bad I hadn't come across that earlier! Several hours of frustration cleared out in just the download/install times. Everything seems to be working right again but will be back if I come across any problems.

Great solution that should be put in a permanent post.

ffp

---

