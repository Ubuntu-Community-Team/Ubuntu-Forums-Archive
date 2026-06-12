---
title: "Help with downloading Java?"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by regice9 on 2012-10-07
Hello. I am trying to download java, because for some reason it does not seem to come with Ubuntu. I tried to follow the directions at the website, but I did not understand most of the directions. I tried a YouTube tutorial, with rootilus used to place the file in the usr/lib/jvm/ file, but in addition to not working, it also seems to have removed the jvm file. I have no idea what to do, because I can't just make a new folder called jvm because Ubuntu does not allow it, it is just grayed out. I don't have a clue what to do.

---

### Post by agillator on 2012-10-07
Assuming what you want is the runtime so you can run java programs, open the application menu (the main menu) and select Ubuntu Software Center. When that finishes loading type java in the search bar at the top right of the window. Then click on the OpenJDK 7 runtime entry and finally click on the install button that will appear. When asked, enter your password.

---

### Post by regice9 on 2012-10-08
I already have the Java 6 one, but I don't know how to upgrade to 7, because when I downloaded the Java 7 on the software center, nothing happened. Terminal still says that it is the sixth version.

---

### Post by agillator on 2012-10-09
Then what I think you will need to do is remove the 6 version through whatever means you installed it. Then see [http://openjdk.java.net/install/](http://openjdk.java.net/install/) for instructions on installing 7.

---

### Post by DuckHook on 2012-10-09
Not all Java is the same. Bear with me, because you need to understand a little history here.

Java was originally created by Sun Microsystems and, after some years, was licensed under the GPL (General Public License). Once it was released under the GPL it became open source and the Linux community adopted it happily. However, in 2010, Sun was sold to Oracle. We don't need (or want) to get into the ongoing controversy here, but that event triggered a fork in the development of Java. Ubuntu ships with the version of Java called OpenJDK which is developed and supported by the Open Source community and is licensed under the GPL. However, the "original" Java became Oracle's property when they bought Sun.

Therefore, before installing Java. you must choose whether you wish to install the Open Source variant (available through the Software Center) or Oracle's variant. If you want to install Oracle's variant, you must follow the instructions in this guide under the subtitle (Oracle Java 7):

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Hope this helps.

---

### Post by critin on 2012-10-09
I would recommend getting java from Synaptic Package manager or Software Center.    It should install the proper package for your system.  Just type java in search bar.

Restricted packages used to have it, but it doesn't seem to be included any longer.

---

### Post by spcwingo on 2012-10-09
This is the easiest way:

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")

---

### Post by regice9 on 2012-10-09
> **critin said:**
> I would recommend getting java from Synaptic Package manager or Software Center.    It should install the proper package for your system.  Just type java in search bar.


Like I said, it did not work because java 7 didn't do anything, and when I tried to remove java 6, somehow it downloaded itself again.

---

### Post by DuckHook on 2012-10-10
Both Synaptic and Software Center will not get you any version later than V6. This is due to the fact that the repository for every version of Ubuntu tends to be frozen with the apps and modules that have been proven to work with that version of Ubuntu. This is a conservative approach that deprives users of new features, but greatly decreases incompatibilities and support issues. I like this approach, but that is another matter entirely.

If you wish to install the latest version of Java, you must follow the instructions in the link that I have already given you in my prior post. Deleting and reinstalling from Software Center or Synaptic will not get you where you want to go.

---

### Post by DuckHook on 2012-10-10
> **spcwingo said:**
> This is the easiest way:

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")
With the greatest of respect, this is not recommended, esp for new users (the sort who tend to ask for advice on this forum). Version 8 is a development release and will only cause trouble (requiring further support) when something wonky happens to their system. I also shy away from recommending the addition of PPAs for new users. Again, unless one knows how to chase down signing keys, repair broken PPAs, delete obsolete PPAs, etc. one is just asking for trouble in the future.

---

### Post by regice9 on 2012-10-10
> **DuckHook said:**
> With the greatest of respect, this is not recommended, esp for new users (the sort who tend to ask for advice on this forum). Version 8 is a development release and will only cause trouble (requiring further support) when something wonky happens to their system. I also shy away from recommending the addition of PPAs for new users. Again, unless one knows how to chase down signing keys, repair broken PPAs, delete obsolete PPAs, etc. one is just asking for trouble in the future.
As it happens to be, I already followed the instructions for and downloaded Java 8. What should I really do?

---

### Post by DuckHook on 2012-10-10
As a new user, I suggest that you avoid Java 8, which is still in development and may have bugs, and download Java 7 instead. I have explained the difference between openJDK and Oracle Java, so won't bore you by doing so again. I would suggest trying opnJDK first and going to Oracle's Java only if the community version doesn't do what you want it to.

If you've downloaded version 8 but not yet installed it, then don't. Just delete the file that was downloaded and no harm done.

If you've already installed it, then you can decide to just live with it or you can remove it. Once removed, follow the instructions on this link:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Specifically, just click on the link to: openjdk-7-jre

This should download the version 7 runtime and you can install it by following installation instructions from there.

If you want browser support, download and install the iced tea plugin by clicking the link to: icedtea-7-plugin

The instructions on the help page in the above link are clear and simple. Read it thoroughly before installing and install by following its procedures.

---

