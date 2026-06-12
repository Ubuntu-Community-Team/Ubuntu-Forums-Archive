---
title: "compiling a java file"
date: 2005-04-08
forum: Programming Talk
---

### Post by stasch on 2005-04-08
can i compile a java file in ubuntu?  do i need to download an sdk or jre and if so were can i get it?

---

### Post by Leif on 2005-04-08
You can download it from the sun site and run the installer. I prefer to add this to my sources :

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java

and apt-get it

---

### Post by stasch on 2005-04-08
Thanx but when i clicked on ur likn i got the following msg

"Access forbidden!
You don't have permission to access the requested directory. There is either no index document or the directory is read-protected. 

If you think this is a server error, please contact the webmaster. 

Error 403
ubuntu.tower-net.de
Fri Apr 8 21:06:37 2005
Apache/2.0.49 "

---

### Post by stasch on 2005-04-08
Thanx but when i clicked on ur link i got the following msg

"Access forbidden!
You don't have permission to access the requested directory. There is either no index document or the directory is read-protected. 

If you think this is a server error, please contact the webmaster. 

Error 403
ubuntu.tower-net.de
Fri Apr 8 21:06:37 2005
Apache/2.0.49 "

---

### Post by Leif on 2005-04-08
Sorry for not being clear. Do this :

1) open a terminal
2) type sudo gedit /etc/apt/sources.list
3) place that whole line (deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java) at the end of your file
4) close gedit
5) start synaptic*
6) reload
7) search for sun-j2sdk1.5
8) install

* alternatively, just type these instead at the terminal :
5) sudo apt-get update
6) sudo apt-get install sun-j2sdk1.5

---

### Post by taygan on 2005-04-09
Hmm I'm running hoary, but put in the warty java repository, and it gives me this:

sun-j2sdk1.5:
 Depends: sun-j2sdk1.5debian  but it is not installable

any ideas?

---

### Post by Leif on 2005-04-09
Unfortunately I'm not savvy enough to figure out where packages I installed come from. Do you have universe/multiverse enabled ?

---

### Post by defkewl on 2005-04-11
Why don't you download java sdk from java.sun.com?
They have the installer for linux too.
Pick the .bin ones since you're using ubuntu.

---

### Post by thePythonAlchemist on 2005-04-11
I put the Sun SDK on my system; it's not really any harder than installing a package. Just remember to add these lines to /etc/bash.bashrc for better usability:

```
JAVA_HOME=/path/to/java/dir
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
```

---

### Post by flightcrank on 2005-05-05
[QUOTE=thePythonAlchemist]I put the Sun SDK on my system; it's not really any harder than installing a package. Just remember to add these lines to /etc/bash.bashrc for better usability:

```
JAVA_HOME=/path/to/java/dir
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
```[/QUOTE]
 thanks worked a treat !

---

### Post by jerome bettis on 2005-05-05
[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

that an automated script that sets up java and lots of other good stuff.

---

