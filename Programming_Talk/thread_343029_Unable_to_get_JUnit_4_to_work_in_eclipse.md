---
title: "Unable to get JUnit 4 to work in eclipse"
date: 2007-01-20
forum: Programming Talk
---

### Post by Yarias on 2007-01-20
I'm dual booting Ubuntu Edgy and Windows XP on this machine.

No matter what I seem to try in edgy (which is not all that much, as I'm pretty unfamiliar with linux) I cannot get JUnit 4 working in eclipse.

I'm using the java-sun package from the repository and it seems to be set up correctly as java -version returns

```
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
```

In eclipse, under Window -> Preferences -> Java -> Installed JREs the same version is there.

On my windows version of eclipse, adding the junit4.2.jar file to the installed JRE resolves all the import problems and JUnit tests run just fine.

Doing the same thing in Edgy resolves the eclipse generated errors, but when I go to run the JUnit test, eclipse comes back with the following error:

```
An internal error occurred during: "Launching".
```

I did a bit of searching and the only thing that even seemed remotely related was mention that JUnit 4 was disabled in Edgy.  If that is true, could someone please tell me why it is disabled?  And is there any work around?  My professor is requiring that we use Java Generics and JUnit 4 and I would rather not have to boot into windows every time I need to work on a project.

Thanks,

---

### Post by Yarias on 2007-01-21
I tried a manual install of eclipse with the Sun JDK6, and it seemed to work, but I have to open eclipse from within a terminal or else I get the same error.  I've tried a ton of different things to launch it, but nothing seems to work except the terminal ](*,)

---

### Post by Prof_NARF on 2007-01-24
Hi,

I had the same problem. I fixed it by locally downloading and unpacking Eclipse 3.2.1. I then copied the directory org.junit4_4.1.0.1 and the file org.eclipse.jdt.junit4.runtime_1.0.1.r321_v20060905.jar from the local eclipse plugins to the system eclipse plugins (/usr/lib/eclipse/plugins) directory. After a restart of eclipse JUnit4 tests should work.

I hope this helps.

Greetings,
Prof_NARF

---

### Post by drewshaver on 2007-02-09
Thanks for the tip, Prof_NARF!

---

### Post by phossal on 2007-02-09
I can't figure out what your problem is by reading the preceding posts. Is it that it won't launch at all, or that it won't launch except by using the terminal?

---

### Post by lloyd mcclendon on 2007-02-09
TestNG is so far ahead of JUnit these days, unless you have a bunch of existing JUnit tests, you should check it out.  actually i believe there's an easy way to convert them, so you should definately check it out.

---

### Post by Prof_NARF on 2007-02-16
> **phossal said:**
> I can't figure out what your problem is by reading the preceding posts. Is it that it won't launch at all, or that it won't launch except by using the terminal?

The problem is that JUnit 4 is disabled when you install Eclipse from the Ubuntu repositories. When you download and install Eclipse manually JUnit 4 is included. I think Yarias' Eclipse works when starting from the terminal just because the local installation is being launched when entering "eclipse" in the terminal. (@Yarias: what is the output of "which eclipse") When he uses his desktop link this problably refers to the Ubuntu version without JUnit 4.

---

### Post by Ramses de Norre on 2007-02-17
Isn't there a way to get junit 4 to work in ubuntu's eclipse? 
I got eclipse set up perfectly like I need it and I now need to use junit for unit tests for an OOP course I'm following, so I'd hate to go through all the preferences and libraries stuff and such again...

I've downloaded the junit 4 jar and added it to my system libraries, but I get the same error as the OP when trying to launch a test.

---

### Post by Yarias on 2007-02-17
> **Prof_NARF said:**
> The problem is that JUnit 4 is disabled when you install Eclipse from the Ubuntu repositories. When you download and install Eclipse manually JUnit 4 is included. I think Yarias' Eclipse works when starting from the terminal just because the local installation is being launched when entering "eclipse" in the terminal. (@Yarias: what is the output of "which eclipse") When he uses his desktop link this problably refers to the Ubuntu version without JUnit 4.

That's exactly what is happening.  The launcher for eclipse brings up the default Edgy repo Eclipse, which has JUnit 4 disabled.

I editted bash (IIRC) so that typing 'eclipse' in the terminal launches my own custom install of eclipse (which has JUnit 4 disabled).

Eclipse launches fine in both setups.  But in the default Edgy one, if you try to run a JUnit 4 test, the tests fail to run in eclipse.  Nothing crashes, you just can't use them.

This setup is perfectly usable, although a bit akward, and I don't really have time to mess with stuff too much because I have a lot of work this semester.

Thanks for all the responses though.

---

@lloyd mcclendon : The course I use eclipse for requires writing JUnit tests (as they reuse their same tests every year on projects), so I can't use TestNG

---

### Post by lloyd mcclendon on 2007-02-17
take a different course j/k


maybe junit is disabled?  help > software updates > manage configuration look around in there

if it's enabled and you one of the 1800000 people on here using the eclipse from the repository that does NOT work, [www.yoxos.com](www.yoxos.com) download a vanilla eclipse with the junit plugin & whatever else you want.  extract it and it will work

---

### Post by Prof_NARF on 2007-02-25
> **Ramses de Norre said:**
> Isn't there a way to get junit 4 to work in ubuntu's eclipse?

See my first post in this thread. That's how I fixed ubuntu's eclipse. After copying the relevant files you can delete the local installation, of course.

---

### Post by Magni on 2007-03-12
> **Prof_NARF said:**
> Hi,

I had the same problem. I fixed it by locally downloading and unpacking Eclipse 3.2.1. I then copied the directory org.junit4_4.1.0.1 and the file org.eclipse.jdt.junit4.runtime_1.0.1.r321_v20060905.jar from the local eclipse plugins to the system eclipse plugins (/usr/lib/eclipse/plugins) directory. After a restart of eclipse JUnit4 tests should work.

I hope this helps.

Greetings,
Prof_NARF

great! easy and clean (or cleanly?) solution

---

### Post by Rob_H on 2007-06-15
Thanks for the workaround. Wonder why the plugin was stripped from the Ubuntu package.

---

### Post by KeighleHawk on 2007-06-21
actually, you can fix this a little more cleanly.  You still have to step out of the Ubuntu way, but the Eclipse way works just fine.  You'll need to start eclipse via sudo from a command line:

sudo eclipse

Just let it take the default Workspace, it doesn't matter.  Then do Help->Software Updates and update from the Eclipse repository (or one of the mirrors).  This will give you the latest release as well as the JUnit4 libraries.

---

### Post by komasoftware on 2007-08-23
workaround (copying directory + jar file, as mentioned above) from my collegue's Windows machine fixed the prob for me

---

### Post by mollison on 2007-09-05
> **KeighleHawk said:**
> actually, you can fix this a little more cleanly.  You still have to step out of the Ubuntu way, but the Eclipse way works just fine.  You'll need to start eclipse via sudo from a command line:

sudo eclipse

Just let it take the default Workspace, it doesn't matter.  Then do Help->Software Updates and update from the Eclipse repository (or one of the mirrors).  This will give you the latest release as well as the JUnit4 libraries.

This worked perfectly for me - thanks!!

---

### Post by wozzinator on 2008-02-02
[http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.3.1.1-200710231652/eclipse-SDK-3.3.1.1-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.3.1.1-200710231652/eclipse-SDK-3.3.1.1-linux-gtk.tar.gz)

That right there is an easier site to navigate then Yoxos when it comes to downloading Eclipse 3.3.1.1 for Linux, I looked around Yoxos and it got kind of confusing so I figured I should just post this one if anybody else had the same problem as I did.

---

