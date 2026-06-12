---
title: "Cannot install Java."
date: 2013-04-05
forum: New to Ubuntu
---

### Post by guillaumesoucy on 2013-04-05
Hi, 

I have downloaded Java from java.com, I have followed the instructions on the Java website but Java is not installed. The terminal said the package is brocked.

Need help please. 

Thanks, 

Guillaume

---

### Post by r-senior on 2013-04-05
What do you want to do with Java:

Run Java applets in your web browser?
Run Java programs?
Write Java programs?

---

### Post by guillaumesoucy on 2013-04-05
Hi, 

Its for running Java applets in Firefox.

Thanks!

Guillaume

---

### Post by claracc on 2013-04-05
To install java from oracle, you have to follow the instructions in this link: [http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

---

### Post by slickymaster on 2013-04-05
Before everything, let's clean up your previous Java 7 installation that could later on create you problems. Open a terminal and run the following:
```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
```

Then run the following commands
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Edit: Let us know how it went.

---

### Post by QIII on 2013-04-05
The webupd8 method is simply the easiest way by far and your version will be updated automatically when you do your normal updates. That's why I put it in the Community Wiki.

The webupd8 team has automated the download from the official site, installation and configuration.

---

### Post by guillaumesoucy on 2013-04-05
Hi, 

Thanks thats work now!

Guillaume

---

### Post by fernetekhd on 2013-04-05
@Slickymaster I followed your instructions, but it doesn't look like Java was installed, either the JDK or the web plugin or...anything (java -version returns a message stating that the directory doesn't exist). Any idea as to why :S?

---

### Post by claracc on 2013-04-06
> **guillaumesoucy said:**
> Hi, 

Thanks thats work now!

Guillaume

As you get fixed your problem, please mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by claracc on 2013-04-06
> **fernetekhd said:**
> @Slickymaster I followed your instructions, but it doesn't look like Java was installed, either the JDK or the web plugin or...anything (java -version returns a message stating that the directory doesn't exist). Any idea as to why :S?

I suggest you open a new thread asking for  your problem, you can refer to this thread in the description. what is the ubuntu you are running?

Could you post the output of any of the commands addressed in order to install oracle java?

First of all, you have to run the command: sudo apt-get purge openjdk* as it is indicated in the link: [http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

---

