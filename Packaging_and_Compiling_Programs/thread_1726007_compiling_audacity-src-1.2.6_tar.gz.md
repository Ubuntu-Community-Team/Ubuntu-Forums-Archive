---
title: "compiling audacity-src-1.2.6 tar.gz"
date: 2011-04-10
forum: Packaging and Compiling Programs
---

### Post by Gustav521 on 2011-04-10
Hello everyone. I have Ubuntu 10.04 clean installed. Want to install audacity-src-1.2.6 

tar.gz but don't no how to compile it. Can someone help?? I have done his:

cd Desktop then:
tar xfvz audacity-src-1.2.6.tar.gz  which got me this:
Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

And that is where I am! Thank you for your help. -gustav521

---

### Post by MadCow108 on 2011-04-10
is there a reason you need to compile it?
you could install it from the repository:
```
sudo apt-get install audacity
```

the error message you posted says it did not find the file
make sure you are in the same directory where the tar.gz is located

---

### Post by Gustav521 on 2011-04-10
Thank you "MadCow108" for your quick reply! Audacity 1.3.12beta is in the repos. I did 

install it. For one thing the Mixer Toolbar that indicates from what source you wish to

 record from, has been removed. In 1.2.6 recording seems an easy thing. I have 1.2.6 

installed in a XP pc I have, with no problems. The tar.gz file IS on the desktop. Any ideas??

 Thank you!  -gustav521

---

### Post by davidmohammed on 2011-04-10
at a guess - you need to find gunzip the .gz file before you "tar -xvf" the resulting audacity.tar file.

---

### Post by Gustav521 on 2011-04-10
Hello "davidmohammed". How do I do that, as the only file is the tar.gz file? Thank you!
 -gustav521

---

### Post by davidmohammed on 2011-04-10
gunzip audacity-src-1.2.6.tar.gz

this will unpack the compressed file and create a .tar file on the desktop

then

tar -xvf audacity-src-1.2.6.tar

this will untar the .tar file - probably creating an audacity folder on your Desktop.

You will then need to compile audacity

---

### Post by Gustav521 on 2011-04-10
Hello "davidmohammed": this is what I got from: gunzip audacity-src-1.2.6.tar.gz :

gzip: audacity-src-1.2.6.tar.gz: No such file or directory   -Now what? If you know how to 

get the Mixer Toolbar to reappear in 1.3.12beta, that would be good enough for me! Thank you! -gustav521

---

### Post by davidmohammed on 2011-04-10
given the error message - you havent got the correct filename.

whats the output of 

cd Desktop

ls

?

---

### Post by davidmohammed on 2011-04-10
... have you looked at this [wiki]("http://wiki.audacityteam.org/index.php?title=Mixer_Toolbar_Issues") for mixer toolbar issues?

---

### Post by Gustav521 on 2011-04-10
Hello again "davidmohammed": Here is ls output:

audacity-src-1.2.6
lame_enc.dll
lame.exe
Virtualbox User Manual.pdf

And I will look at that Wiki. Thanks! What now?? Thank you. -gustav521

---

### Post by davidmohammed on 2011-04-10
....  there is either a file or folder there called

audacity-src-1.2.6

type

file audacity-src-1.2.6

if it says its a "directory" - you have already untar'ed it.  

cd audacity-src-1.2.6 and look at its contents

if it says its a file then try

gunzip audacity-src-1.2.6

or 

tar -xvf audacity-src-1.2.6

if that doesnt work then rename the file with a .gz extension

i.e.

mv audacity-src-1.2.6 audacity-src-1.2.6.tar.gz

---

### Post by Gustav521 on 2011-04-10
Good news "davidmohammed"! Here is output of:  
file audacity-src-1.2.6 > audacity-src-1.2.6: directory

 It comes up as a directory! Where to now?? Thank you for your patience! -gustav521

---

### Post by davidmohammed on 2011-04-10
google brought up these instructions to [compile]("http://audacity.sourceforge.net/download/beta_source").  Whilst these instructions are for 1.3 - I suspect the instructions will work for your version.

Also have a look in the audacity folder - is there a README or something similar?  This file should have instructions to compile.

---

### Post by Gustav521 on 2011-04-11
Hello "davidmohammed"; Ok, thanks for your help! Someone else sent me this link:

[http://wiki.audacityteam.org/wiki/CompilingAudacityForBeginners](http://wiki.audacityteam.org/wiki/CompilingAudacityForBeginners)  . I will work through it,

and probably be back for more help, lol! Thanks again!! -gustav521

---

