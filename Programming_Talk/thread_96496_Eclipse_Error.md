---
title: "Eclipse Error"
date: 2005-11-29
forum: Programming Talk
---

### Post by adduds on 2005-11-29
Hi All!

I'm extremely new to ubuntu (3days old lol), i installed Eclipse 3.1 java editor using synaptic or apt- get i cannot remember. well that doesn' matter ones a gui, but ya so it loads i choose the workspace, create the project "Assignment 4" for class go to run the app (which i have developed and tested a million times on my computer (main computer windows box). and this is what it says:

```

Please enter a move (1-9)

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...

```

ANY HELP WOULD BE MUCH APPRECIATED

---

### Post by amohanty on 2005-11-29
I think its a bug as mentioned here:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=13942](http://bugzilla.ubuntu.com/show_bug.cgi?id=13942)

The most straightforward solution is to install sun-jre from the plf repos and use it for eclipse

add the following to /etc/apt/sources.list -
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

at the terminal type:
apt-get update

fire up synaptic and search for sun
install (I am not 100%sure of the names):
sun-jre1.5
sun-jdk1.5 

download eclipse sdk from:
[http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.1.1-200509290840/eclipse-SDK-3.1.1-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.1.1-200509290840/eclipse-SDK-3.1.1-linux-gtk.tar.gz)

then do:
cd /usr/share
sudo tar xzf <path to downloaded file>

then create a file called eclipse with the following in it:
#! /bin/bash

/usr/share/eclipse/eclipse &

then do:
chmod +x eclipse
sudo cp eclipse /usr/bin

then to launch eclipse just do:
eclipse

viola!

HTH
AM

---

### Post by adduds on 2005-11-29
thank you very much my friend! you have been most helpful, can i give you points? lol

thanks again,
cheers,
ad

---

### Post by amohanty on 2005-11-29
glad to be of help.
AM

---

### Post by amohanty on 2005-11-29
Oh yes, I forgot to add:

remove gcj and make sure that java points to the right jvm by doing a 
java -ver

AM

---

### Post by adduds on 2005-11-29
Hey AM!

1. when i create the file i'm assuming i do it from cd /usr/share/eclipse

2. code: sudo gedit

3. save as "eclipse" in eclipse folder but it asks me if i want to overwrite:

Do you want to replace it with the one you are saving?

should i say yes?

4. is this ALL that goes in the eclipse gedit file:

#! /bin/bash

/usr/share/eclipse/eclipse &

anytime thx! :) cheers

---

### Post by amohanty on 2005-11-29
No create the eclipse file in your home folder and then copy it over to /usr/bin. The reson you create this file and put it in /usr/bin is so that you can access it from anywhere. 

the eclipse file in /usr/share/eclipse is the real executable. but since it would be a pain to type in /usr/share/eclipse/eclipse everytime, I created this file.

HTH
AM

---

### Post by adduds on 2005-11-29
ya it's in the file i d/led it to home, and then extracted it tar xzf /home/adduds/sun-javaetc... while in cd /etc/share (u said share b4 should i put it in bin?) 

what step is the remove gcj?

and do i overwrite the existing eclipse folder with a gedit file named "eclipse" w/ 

```
#! /bin/bash

/usr/share/eclipse/eclipse &
```

written in it? 

IF I NEED to move the unzipped file from share to bin how do i that?

---

### Post by amohanty on 2005-11-29
No.
Once you unzipped the eclipse file to /usr/share let it be.
then do
cd /usr/bin
sudo gedit eclipse

paste:
#! /bin/bash

/usr/share/eclipse/eclipse &

save
then do:
sudo chmod +x eclipse

And you are ready to go.

AM

---

### Post by adduds on 2005-11-29
MAN I'M REALLY REALLY SORRY!!!

do i overwrite the whole file w/ that or do i just paste it at the bottom

really really sorry for all the bother

---

### Post by amohanty on 2005-11-29
Ok I think you are getting confused here. Do exactly as I write here:

NOTE: replace eclipse...tar.gz with the full filename

1. Download the eclipse file  - lets say its in /home/adduds/eclipse...tar.gz
2. In terminal:

cd /usr/share
sudo tar xzf /home/adduds/eclipse...tar.gz
cd
echo "#! /bin/bash" > eclipse
echo "" >> eclipse
echo "/usr/share/eclipse/eclispe &" >> eclipse
chmod +x eclipse
sudo cp eclipse /usr/bin

Thats it.
Let me know how it goes.

AM

---

### Post by adduds on 2005-11-29
do i do this now?:

remove gcj and make sure that java points to the right jvm by doing a
java -ver

or can i just run eclipse?

thx for everything;

---

### Post by adduds on 2005-11-29
k i ran eclipse

now i get this message in (where all my code should be):

Unable to create this part due to an internal error. Reason for the failure: The editor class could not be instantiated. This usually indicates that the editor's class name was mistyped in plugin.xml.

---

### Post by amohanty on 2005-11-29
what does java -ver return?

---

### Post by adduds on 2005-11-29
```
adduds@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by amohanty on 2005-11-29
now do a:
sudo apt-get remove gcj gij eclipse-sdk
better yet do it from synaptic so you can verify what else is removed.

And then java -ver shoudl return:
aseem@kandinsky:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

HTH
AM

---

### Post by adduds on 2005-11-30
Hey i'm at a friends house tonite i'll try to install through synaptic, i'm also gonna d/l the jre1.4 and the j2sdk1.4 and see how that works out tommorow thanks bud

---

