---
title: "Java due Friday: Help Installing!"
date: 2008-02-03
forum: Packaging and Compiling Programs
---

### Post by Sonastylol on 2008-02-03
Hey all, Im new to Ubuntu. I have til friday to finish a programming project.


I don't know how to install Eclipse, or another editor on Ubuntu, or how to install the java runtime environment ( the dev kit which enables the allowance of programming.. ) 


Thank you so much for your immediate attention.

---

### Post by LaRoza on 2008-02-03
[http://ubuntuprogramming.wikidot.com/Java](http://ubuntuprogramming.wikidot.com/Java)

Perhaps that will help?

---

### Post by Sonastylol on 2008-02-03
Thank you for the link, i THINK it installed correctly, but during the installation I noticed a few lines of "error, title something...." and a few other error lines, but for the most part I think it installed properly..

On my desktop I created a document " new file" and typed in that code just as a quick test.  I named it hw.java


in my terminal I typed javac hw
and it returned

[I]error: Class names, 'hw', are only accepted if annotation processing is explicitly requested
1 error
[/I]


What went wrong?

---

### Post by brennydoogles on 2008-02-03
could you post the contents of the file exactly as you have it?

---

### Post by Shin_Gouki2501 on 2008-02-03
try to go with eclipse it really helps a lot..

---

### Post by Sonastylol on 2008-02-03
I use Eclipse on my windows machine..

Can you possible just teach me how to install it on Ubuntu?  I downloaded it but I am not sure entirely... I much prefer to just use the Synaptic Installer ;P

---

### Post by gmclachl on 2008-02-03
Don't use the eclipse that is in the package manager! The easiest thing to do is download a tar file from the eclipse site and  unpack it there is no install as such.


You may also want to check the version of java you are running, on the command line type

java -version 

if you want to see which jvm's you have installed and change the default type

 sudo update-alternatives --config java

---

