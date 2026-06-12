---
title: "openjdk vs sun java"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Louis de Broglie on 2008-06-30
Hello,

I need to run applet from this site:

[http://www.topcoder.com/tc](http://www.topcoder.com/tc)

I have installed sun-java but i have found no executable javaws file. Do u think uninstalling openjdk can fix this problem ?:)

If so, do i need openjdk when I have sun java?

---

### Post by lenards on 2008-06-30
openjdk is just an implementation of java with a more "friendly" open source license.  I don't believe installing one versus the other will help your problem.  

Did you do the install via Synaptic Package Manager? What version of sun-java did you install?  sun-java6? or sun-java5?

---

### Post by lenards on 2008-06-30
Louis, 

I did some research so that I hope I get this right for you.  I'm a java developer at my day-job. 

I'm guessing that you have sun-java5-bin or sun-java6-bin installed, right?  But the `javaws` executable I believe is part of the 'jdk' install. Which makes your original question's answer a 'yes.'  

You want to have the *-bin, *-jdk, *-jre of whichever you chose.  I would go with the latest release, sun-java6-bin, sun-java6-jdk, sun-java6-jre. 

I'm not positive that I'm correct - as you can see I'm a green poster.  But I think this will fix the issue.  

If not - you might want to look if you need the java plugin installed for your browser.

---

### Post by txcrackers on 2008-07-01
> **lenards said:**
> Louis, 
But the `javaws` executable I believe is part of the 'jdk' install.
The Java WebStart executable ('javaws') is included in the **JRE** (runtime) installation: you don't need the JDK to *run* java programs.

However, you may need to register the javaws executable as the program to run when you run across *.jnlp* files. It's actually supposed to be registered in your $HOME/.mime.types file, but I'm not entirely sure that's working in Firefox 3.0 (mostly because I haven't tried to use it).

---

### Post by MegaJim on 2008-07-01
I had this problem and installed the sun-java release instead of openjdk.  Webstart isn't the only buggy aspect of the open jdk either.  If i were you I'd stick to the sun binaries for the moment.

---

### Post by kpkeerthi on 2008-07-01
> **Louis de Broglie said:**
> Hello,

I need to run applet from this site:

[http://www.topcoder.com/tc](http://www.topcoder.com/tc)

I have installed sun-java but i have found no executable javaws file. Do u think uninstalling openjdk can fix this problem ?:)

If so, do i need openjdk when I have sun java?

It could be because sun-java is not configured as the default Java VM in your setup. To change this, open a terminal window and run ```
sudo update-alternatives --config java
``` and select Sun's as the default Java runtime.

... [More Info]("https://help.ubuntu.com/community/Java") ...

---

### Post by Louis de Broglie on 2008-07-01
Firefox opens window when I click on the O(n) button of that site and I browse for the 'javaws' and tick make this default program to run this kind of file. But after unstalling openjdk and then reinstalling sun-java-6 via synaptic, I could not find the javaws:confused:

So I downloaded java from sun . And extracted the .bin file in a folder. Then I selected javaws when firefox opened the window and it worked:D

But I am experiencing some problems running the applet. Like sometimes when I click buttons, nothing happens.:confused:

---

### Post by lenards on 2008-07-01
I think kpkeerthi was right - I think you didn't have the sun-java jvm configured as your default.  I would try re-installing sun-java6-bin & sun-java6-jre - then config it as mentioned. 

I try to stick with the packages distributed via apt-get/synaptic because you'll be able to get security updates and bugfixes without having to redownload the .bin, etc.

---

### Post by Louis de Broglie on 2008-07-01
I tried to configure but I receive this error message :

> 
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so


---

### Post by kpkeerthi on 2008-07-02
> **Louis de Broglie said:**
> I tried to configure but I receive this error message :

Install the package from repository

---

### Post by Louis de Broglie on 2008-07-03
Well, i have just found out that java does not work in firefox 64. I guess i will just wait till java for 64 bit comes out. It's not too important right now.:popcorn:

---

