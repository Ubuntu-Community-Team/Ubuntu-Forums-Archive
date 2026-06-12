---
title: "Setting the path to the Java executable"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by jhvillegas2 on 2008-11-07
How do I set the path to the Java executable on my Kubuntu 8.10 box?

Thanks,
jhvillegas2

---

### Post by RequinB4 on 2008-11-07
You're going to have to provide a bit more information... what executable are you talking about, one you created?  Step back and tell us what you are trying to do!

Thx.

---

### Post by jhvillegas2 on 2008-11-07
the java.exe, i guess.  it is the program called whenever the runtime is needed.  thanks!:guitar:

---

### Post by jhvillegas2 on 2008-11-07
i am trying to install a program and it won't go because the java executable can't be found by the program installer.

---

### Post by RequinB4 on 2008-11-07
If I understand you correctly, you're looking for hte location in the filesystem of the java binary.  There are multiple in /usr/bin if you have java installed.

Edit: Apparently not - what program are you trying to install and how and what exact error message are you getting?

You probably just need to install java.

Please take the time to read the first link in my signature :)

---

### Post by jhvillegas2 on 2008-11-07
i am asking how to set the path.  Please read my original question.  Thanks:guitar:

---

### Post by jhvillegas2 on 2008-11-07
I am trying to install Vuze since Ktorrent sucks.

The error message that I get consists of the following:

> 
$./azureus
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls:  cannot access /usr/java/latest:  No such file or directory
ls:  cannot access /usr/java:  No such file or directory
ls:  cannot access /usr/lib/jvm/latest:  No such file or directory
Re-checking with GCJ (Sun Java recommended)...
Java exec not found in PATH, starting auto-search...
ls:  cannot access /usr/java/latest /usr/java /usr/lib/latest/jvm/latest /usr/lib/jvm hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)


I am trying to get 1.6.10 going.

Thank you for your help.

---

### Post by Axos on 2008-11-07
Java is not installed by default. If you haven't explicitly installed it, it isn't on your system.

I run Ubuntu and have no Kubuntu experience but the package I think you need is: sun-java6-jre. I don't recommend the OpenJDK because it just doesn't work the same as Sun's JRE yet.

If you've installed Java and Azureus still doesn't work, post again and I'll suggest one other thing (editing the azureus startup script).

---

### Post by jhvillegas2 on 2008-11-07
I looked in Adept for sun-java6-jre with no results.  Sorry 'bout that.  Anything else?

Thanks,
:guitar:

---

### Post by jhvillegas2 on 2008-11-07
> **Axos said:**
> Java is not installed by default. If you haven't explicitly installed it, it isn't on your system.

I run Ubuntu and have no Kubuntu experience but the package I think you need is: sun-java6-jre. I don't recommend the OpenJDK because it just doesn't work the same as Sun's JRE yet.

If you've installed Java and Azureus still doesn't work, post again and I'll suggest one other thing (editing the azureus startup script).

My concern with this is that it may work for Azureus Vuze, but when I go to install anything needing the JRE again it may crap out like it is doing now.  What are your thoughts about this?

Thanks,
:guitar:

---

### Post by Axos on 2008-11-07
You have to enable the "multiverse" in order to see that package. Not sure how that's done under Kubuntu. Under Ubuntu it's "System -> Administration -> Software Sources".

If you've already manually installed the Sun JRE (downloaded from Sun's web site rather than the *buntu repository), you don't have to install the package above. You just have to make a change to the azureus start-up script. In the section at the top there is a JAVA_PROGRAM_DIR variable. Edit it to point to the Java bin directory. Be sure to include the trailing slash. Since I manually installed the JRE as a dedicated java user on my system, this is what I've got in my azureus script. Change this to point to wherever you installed the JRE (if you installed it manually).

JAVA_PROGRAM_DIR="/home/java/jdk1.6.0_10/bin/"

If you haven't already installed Java, your best bet is probably to install it from the *buntu repository. That way it's installed in the standard place and you don't have to edit the Azureus start-up script. I booted the LiveCD, installed Java from the multiverse, installed azureus, and verified it started without having to edit the start-up script.

---

### Post by kukibird1 on 2008-11-07
/usr/lib/jvm/java-6-sun-1.6.0.10/bin/java

---

### Post by jhvillegas2 on 2008-11-07
> **kukibird1 said:**
> /usr/lib/jvm/java-6-sun-1.6.0.10/bin/java

What does this path mean?  Thank you.:guitar:

---

### Post by Axos on 2008-11-07
That's where the java executable ends up if you do an install from the Ubuntu repository. But it also (indirectly) ends up in /usr/bin as well, which is in the PATH by default. So if you install sun-java6-jre you don't have to worry about anything. Just run the azureus script as-is and Vuze will launch. I tried it myself and it worked.

If you are still having problems, please describe.

---

