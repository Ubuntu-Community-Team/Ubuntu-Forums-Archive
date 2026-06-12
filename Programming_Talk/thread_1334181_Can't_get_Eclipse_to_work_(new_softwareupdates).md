---
title: "Can't get Eclipse to work (new software/updates)"
date: 2009-11-22
forum: Programming Talk
---

### Post by Olav on 2009-11-22
I thought I'd try Eclipse as an IDE for my programming (still learning) in Python. Mainly because I heard good things about the Pydev plugin. However, I am not having much luck with it so far.

I downloaded two versions of Eclipse 3.5.1, both [eclipse-SDK-3.5.1-linux-gtk.tar.gz]("http://update.eclipse.org/downloads/drops/R-3.5.1-200909170800/index.php#EclipseSDK") (of about 162 MB) and [eclipse-platform-3.5.1-linux-gtk.tar.gz]("http://update.eclipse.org/downloads/drops/R-3.5.1-200909170800/index.php#PlatformRuntime") (47 MB). I am experiencing exactly the same problem with both editions. The version of Java that I have installed (through apt-get) is "1.6.0_15" (packages sun-java6-jre and sun-java6-jdk).

With both Eclipses, after I unpack them, I am unable to get updating or installing new software (plugins) to work. I would go to Help - Install New Software and select an update source from the drop down list, but nothing shows up for selection. Oddly enough, scrollbars show up in the empty list of available software, as if the program "wants" to show some items, but can't. See *(un)available software.jpg*.

Something else that doesn't seem to work is adding a new site to the list. I would click the Add button and give the site's details, like in *can't add site.jpg* but when I click OK nothing happens. The little dialog window just sits there, until I click Cancel.

Am I doing something wrong, or is there some known problem? I would appreciate any sort of insight.

---

### Post by Olav on 2009-11-23
No Eclipse users here?

---

### Post by SevenMachines on 2009-11-23
try running eclipse with 
export GDK_NATIVE_WINDOWS=true
this should sort out both bugs

---

### Post by Olav on 2009-11-23
> **SevenMachines said:**
> try running eclipse with 
export GDK_NATIVE_WINDOWS=true
this should sort out both bugs
Thank you, it did!

---

### Post by ravi25k on 2010-02-21
I am using ubuntu 9.10 have no net connection and have downloaded eclipse_3.5.1+repack~1.orig.tar of 85.7 MB. Please tell me how to install eclipse. i have already installed jdk by downloading sun-java6_6.18.orig.tar 159 MB and extracted it user/lib/jdk1.6.6_18   and set path as PATH="/usr/lib/jdk1.6.6_18/bin:" at etc/environment. Now java is working well.

please provide me help in installing eclipse.

---

### Post by GregBrannon on 2010-02-21
ravi25K,

Unpack the Eclipse tar you've downloaded into a folder named "eclipse" or a name of your choice, off of your own home folder, preserving the folder structure as it exists in the tar.  From there, you can start eclipse from the executable in the top folder, or if you see the problem initially reported above, create a script file that includes the line:

```
export GDK_NATIVE_WINDOWS=1
```

before calling the eclipse executable.

That should do it, but if you have problems, let us know.

---

