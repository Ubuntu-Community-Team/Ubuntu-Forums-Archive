---
title: "Temporarily specify different Java version."
date: 2010-05-19
forum: Programming Talk
---

### Post by nateperson on 2010-05-19
We have a server running 64 bit Ubuntu 9.10 workstation all set up and configured.  I need to run some 32 bit java programs on it after ssh'ing on it sometimes, without effecting any of the other users.  So, I downloaded and expanded the jdk into my home folder and added the home/nateperson/jdk1.6/bin path to my PATH and JAVA_HOME path's...  and it doesn't work.  It errors out saying -bash: /home/nateperson/jdk/bin/java No such file or directory...  so I renamed jdk1.6 to java and pointed PATH and JAVA_HOME to there, and it does nothing and continues to point to the 64 bit... 

I'm pretty sure that what I'm doing should work and has so before on other linux systems...  So I'm at a loss can anyone help me?

thanks

---

### Post by Reiger on 2010-05-19
Okay assuming that your Java is installed in $MY_JAVA_HOME/bin/java you should ensure it is executable. You did issue "chmod u+x $MY_JAVA_HOME/bin/java" didn't you?

---

### Post by nateperson on 2010-05-19
Yeop.  I did a chmod 777 just to be sure...

---

### Post by nateperson on 2010-05-19
I got ia32-sun-java6-bin installed and it worked.  I guess it needs the 32bit JRE installed properly, even though its not configured to run, in order to latch on to the java compiler my homedir. 

Thanks anyway.

---

