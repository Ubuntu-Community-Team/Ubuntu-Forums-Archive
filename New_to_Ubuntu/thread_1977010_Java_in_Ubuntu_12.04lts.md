---
title: "Java in Ubuntu 12.04lts"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by misterrisper on 2012-05-09
I am a newbie to Linux, and I would like to get Java to work with my system so I can play games. Is there a very simple, step-by-step process I could follow that will work? I have a fresh install of Ubuntu 12.04lts on a MSI Wind U123 netbook.  Thanks.

---

### Post by jerome1232 on 2012-05-09
If you just want java in your browser, you can try installing icedtea and openJDK.

To get java6 in your browser
```
sudo apt-get install icedtea-6-plugin
```

To get java7
```
sudo apt-get install icedtea-7-plugin
```

[COLOR="RoyalBlue"]edit: Looks like they switched to Java7 as being the primary java when I wasn't looking.[/COLOR]

Alternativly you can install Oracles Java7 (if openjdk just isn't working for you) by running the installer from java.com, [http://java.com/en/download/manual.jsp?locale=en]("http://java.com/en/download/manual.jsp?locale=en")

After downloading the self-extracting installer, you would browse to it in your file browser, right click it, properies, allow executing as program, then double click it, select "run in terminal"

Edit: They actually have their own set of instructions should you choose this path: [http://java.com/en/download/help/linux_install.xml#selfextracting](http://java.com/en/download/help/linux_install.xml#selfextracting)

---

### Post by iMurshaq on 2012-05-09
There are 2 ways:

1st: Search for OpenJDK in Software Center and install "OpenJDK Java 6 Runtime"

2nd: Open Terminal and type:
```
sudo apt-get install openjdk-6-jre
```or

```
sudo apt-get install openjdk-6-jdk
```Then type your password.


Either way works!
Have fun and welcome to the forums.

---

### Post by d4m1r on 2012-05-09
Be advised that Java is pretty resource intensive and it might not run well on your underpowered netbook.

---

### Post by QIII on 2012-05-09
Neither suggestion is optimal, particularly if your apps depend on Oracle Java.

Although OpenJDK 7 is now the reference implementation of Java 7, much of the world does not recognize OpenJDK as Java.

Furthermore, Oracle Java 6 reaches EOL this fall.

You may install Java 6 per this tutorial if you wish:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

However, as I said, Java 6 is on the brink of EOL.

Since Oracle has withdrawn licensing for anyone to keep Java in their repos, you can't install from there.

I would recommend installing Java 7 via an installer in Webupd8's PPA.  It handles downloading the package from Oracle, installing it and installing the browser plugin.  Also, it will keep up with changes and updates.

[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

---

### Post by jerome1232 on 2012-05-09
> **QIII said:**
> 
I would recommend installing Java 7 via an installer in Webupd8's PPA.  It handles downloading the package from Oracle, installing it and installing the browser plugin.  Also, it will keep up with changes and updates.

[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

Didn't know about the ppa.


off-topic: I miss Sun Microsystems. They let us distribute java.

---

### Post by QIII on 2012-05-09
Off topic again:

Yeap.  Swallowed by the Monstoracle.

---

### Post by iMurshaq on 2012-05-09
Then I guess you should go with the download from the java website.

---

### Post by QIII on 2012-05-09
The problem with the Oracle site is that every time an new update comes out, the package needs to be installed manually.

Webupd8's PPA will act like any repo (except that the Java 7 files are not actually there -- it is basically a script to fetch the files from Oracle and install them) and update the version automatically during normal updates/upgrades.

---

### Post by QIII on 2012-05-09
Webupd8's PPA does the download from Oracle and installs it.

No muss, no fuss, and regular updates.

No need for further ideas.

---

### Post by najames on 2012-05-15
Thanks QIII, quick and easy, plus it works great!!

Jim

---

