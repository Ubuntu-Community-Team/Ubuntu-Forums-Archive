---
title: "[SOLVED] java 6"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by uzzo2 on 2008-07-01
I was in the process of downloading the java 6 packages and got an error saying that i needed to go to java's website and download these 2 files "jdk-6-doc.zip and jdk-6-doc-ja.zip". i went to the website and couldn't figure out how to download just these 2 files just the packages. anyway i just rebooted and now i can't open up synaptic i'm getting this error.
E:dpkg was interuppted, you must manually run "dpkg--configure-a' to correct the problem.
E: _cache->open()failed,please report
i put the command in terminal like this, sudo dpkg --configure -a, this is what i get.
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by uzzo2 on 2008-07-01
> **uzzo2 said:**
> I was in the process of downloading the java 6 packages and got an error saying that i needed to go to java's website and download these 2 files "jdk-6-doc.zip and jdk-6-doc-ja.zip". i went to the website and couldn't figure out how to download just these 2 files just the packages. anyway i just rebooted and now i can't open up synaptic i'm getting this error.
E:dpkg was interuppted, you must manually run "dpkg--configure-a' to correct the problem.
E: _cache->open()failed,please report
i put the command in terminal like this, sudo dpkg --configure -a, this is what i get.
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
i guess i just need to return to xp cause i don't have a clue what i'm doing.

---

### Post by bumanie on 2008-07-01
Go to synaptic package manager and type jre into search. Check the boxes next to sun-java6-bin,sun-java6-fonts, sun-java6-jre and sun-java6-plugin and install that way. Not sure whether you will have to remove what you've tried so far or not. Try it. Post back if it doesn't work.

---

### Post by uzzo2 on 2008-07-01
> **bumanie said:**
> Go to synaptic package manager and type jre into search. Check the boxes next to sun-java6-bin,sun-java6-fonts, sun-java6-jre and sun-java6-plugin and install that way. Not sure whether you will have to remove what you've tried so far or not. Try it. Post back if it doesn't work.
i can't even open synaptic right now, i'm getting an error when i try and open.
E:dpkg was interuppted, you must manually run "dpkg--configure-a' to correct the problem.
E: _cache->open()failed,please report

i found one of files it was telling me to download from java the jdk-6-doc.zip and installed it but i can't find the other one.

---

### Post by philinux on 2008-07-01
In a terminal, Accessories> Terminal use.

sudo dpkg --configure -a

Great OS it even tells you how to correct itself. :lolflag:

---

### Post by Mornedhel on 2008-07-01
You do not need the -ja version. It's the same as the other one, only in Japanese. Note that the installer does actually tell you to get one OR the other.

Move the file to /tmp :

sudo mv wherever/it/is/jdk-6-doc.zip /tmp

Change its ownership :

sudo chown root /tmp/jdk-6-doc.zip
sudo chgrp root /tmp/jdk-6-doc.zip

(Do not unzip it.)

Start the procedure again (with dpkg --configure -a) and when you get to
[Press RETURN to try again, 'no' + RETURN to abort]
just press RETURN as per instructions. Rebooting is never really necessary. You could just have typed "no" and pressed RETURN.

---

### Post by uzzo2 on 2008-07-01
> **Mornedhel said:**
> You do not need the -ja version. It's the same as the other one, only in Japanese. Note that the installer does actually tell you to get one OR the other.

Move the file to /tmp :

sudo mv wherever/it/is/jdk-6-doc.zip /tmp

Change its ownership :

sudo chown root /tmp/jdk-6-doc.zip
sudo chgrp root /tmp/jdk-6-doc.zip

(Do not unzip it.)

Start the procedure again (with dpkg --configure -a) and when you get to
[Press RETURN to try again, 'no' + RETURN to abort]
just press RETURN as per instructions. Rebooting is never really necessary. You could just have typed "no" and pressed RETURN.

ok, tried to move the file and got this error.
phillip@phillip-desktop:~$ sudo mv wherever/it/is/jdk-6-doc.zip /tmp
mv: cannot stat `wherever/it/is/jdk-6-doc.zip': No such file or directory

it's sitting on my desktop so i don't know:confused:

---

### Post by Mornedhel on 2008-07-01
You need to replace wherever/it/is by the actual path to your file. Sorry, I thought that was obvious.

Since it's on your desktop, it probably looks like ~/Desktop (you may need to replace Desktop with its translation if you have Ubuntu installed in another language).

So the command would be :

mv ~/Desktop/jdk-6-doc.zip /tmp

The rest does not change.

By the way, the entire process is the standard way to install Sun's documentation for the Java API, since the doc cannot be hosted by the Ubuntu repositories. You should just have followed the instructions you were given (go to Sun's website, download doc, move doc to /tmp, change ownership, resume installation). No harm done though.

---

### Post by uzzo2 on 2008-07-01
> **Mornedhel said:**
> You need to replace wherever/it/is by the actual path to your file. Sorry, I thought that was obvious.

Since it's on your desktop, it probably looks like ~/Desktop (you may need to replace Desktop with its translation if you have Ubuntu installed in another language).

So the command would be :

mv ~/Desktop/jdk-6-doc.zip /tmp

The rest does not change.

By the way, the entire process is the standard way to install Sun's documentation for the Java API, since the doc cannot be hosted by the Ubuntu repositories. You should just have followed the instructions you were given (go to Sun's website, download doc, move doc to /tmp, change ownership, resume installation). No harm done though.

thanks, that looks as if it worked, i'm starting to think that linux is above my intelligence level. i'd gotten directions from another thread to just go to synaptic and mark all the boxes with sunjava 6 for installation and that's where the fun started.

---

