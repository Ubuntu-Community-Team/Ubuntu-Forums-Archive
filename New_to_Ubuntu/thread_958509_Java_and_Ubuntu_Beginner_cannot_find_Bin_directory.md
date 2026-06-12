---
title: "Java and Ubuntu Beginner cannot find /Bin directory"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by gentlemanmasher on 2008-10-25
I am fairly new to the command line with Ubuntu and am trying to use it more often.  I also just bought a book to learn Java.  

My first question is:

Where does Java install on Ubuntu?  I am needing to create an entry to my PATH environment variable that points to the /bin directory.

I found a couple items in my /usr/share/ directory but cannot find the bin directory for for my install?

I installed sun-java6-jdk from syaptic.

Second Question:  I have been looking at google and the forums on how to create a PATH so I can use the Java Binaries.  I need to create a path so I can use the command % javac.

Any help would be appreciated or a direction to some reading materials.

---

### Post by dracayr on 2008-10-25
You won't need to do that... to install java, open a terminal (Applications&#8594;Accessories&#8594;Terminal), and type

sudo apt-get install sun-java6-jdk

Java is now installed. You won't need to change your Path variable. Just jump the chapter about the installation and start learning java :)

EDIT: oh, I saw you already installed sun-java6-jdk. you won't need to do that stuff about "sudo apt-get install sun-java6-jdk" then... But, nevertheless, you won't need to change your path variable... You should already be able to use the command javac. (it's javac, not %javac). Just open a terminal and type 

javac -help

That should output some help :)



dracayr

---

### Post by gentlemanmasher on 2008-10-25
Nice.  One question for my well being though.  Where does the /bin file get installed?  I have google desktop and still couldn't find it.

---

### Post by Morpheun on 2008-10-25
Also, if you really need to know where java is located after that just type "whereis javac"

---

### Post by drtre on 2008-10-25
These 2 may help you.

[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")
[https://help.ubuntu.com/community/JavaInstallation]("https://help.ubuntu.com/community/JavaInstallation")

Post your further questions if any remained.

---

### Post by drtre on 2008-10-25
> **gentlemanmasher said:**
> Nice.  One question for my well being though.  Where does the /bin file get installed?  I have google desktop and still couldn't find it.

Your installed jvms are usually located at /usr/lib/jvm. You'll find the bin in any of your JDKs installed.

---

### Post by oldos2er on 2008-10-25
You can use Synaptic to check where each file in a package is installed. Open Synaptic, in the lower left corner click 'Status,' then in the upper left corner click 'Installed.' Right-click on a package, click 'Properties' then 'Installed Files.'

---

### Post by gentlemanmasher on 2008-10-25
Thanks I'm sure there will be more at some point but for now this is great.

---

### Post by bruce64 on 2008-10-25
As an FYI you might want to look into Eclipse.  It is very easy to use and is suited to a beginner.  You can find it in Synaptic

---

### Post by cariboo on 2008-10-25
@gentlemanmasher

Go to Places-->Home Folder-->Filesystem, you will see the whole directory tree. Also there are two bin directories on at /bin and the other at /usr/bin

Jim

---

