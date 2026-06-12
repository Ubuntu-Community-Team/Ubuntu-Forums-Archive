---
title: "[Java 6] Debugging system classes"
date: 2008-05-23
forum: Programming Talk
---

### Post by jambalaya on 2008-05-23
Hi.
I'm using sun Jdk 6 installed from the restricted repositories, and latest eclipse downloaded from their site (3.3). (I installed eclipse 3.2 from the repos, and then simply replaced the appropriate directory trees, so that I have all the icons and menu entries ready)
When I debug my application and step into system classes code, when I look at Variables view, all I see is a set of arg0, arg1 and so on instead of method parameters names, and I don't see any local variables at all. From windows, I am sure this can be configured so that I can actually fully scrutinize the locals and see the method parameter names. I must be doing something wrong in my setup, but I don't know what. I added my jvm 6 to installed jre in eclipse, and I also don't have any other java installed (like Blackhawk or openjvm).
Could you please help me deal with this?
Thanks.

---

### Post by Quikee on 2008-05-24
> **jambalaya said:**
> Hi.
I'm using sun Jdk 6 installed from the restricted repositories, and latest eclipse downloaded from their site (3.3). (I installed eclipse 3.2 from the repos, and then simply replaced the appropriate directory trees, so that I have all the icons and menu entries ready)
When I debug my application and step into system classes code, when I look at Variables view, all I see is a set of arg0, arg1 and so on instead of method parameters names, and I don't see any local variables at all. From windows, I am sure this can be configured so that I can actually fully scrutinize the locals and see the method parameter names. I must be doing something wrong in my setup, but I don't know what. I added my jvm 6 to installed jre in eclipse, and I also don't have any other java installed (like Blackhawk or openjvm).
Could you please help me deal with this?
Thanks.

Can you make a screenshot with what exactly you mean?

---

### Post by jespdj on 2008-05-24
First of all, make sure you have the Java 6 source code installed:
```
sudo apt-get install sun-java6-source
```
Then, in Eclipse, go to Window / Preferences / Java / Installed JREs. Select your JRE and click the Edit button on the right.

In the list of JRE System Libraries, select the line that ends with **rt.jar**. Click the Source Attachment button on the right. Enter the location to src.zip in your JDK installation directory. On my system it is:

/usr/lib/jvm/java-6-sun-1.6.0.06/src.zip

After that, when you're debugging, you should be able to see the Java source code for the system classes.

---

