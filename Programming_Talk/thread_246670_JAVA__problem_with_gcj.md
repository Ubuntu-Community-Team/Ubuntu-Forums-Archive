---
title: "JAVA : problem with gcj"
date: 2006-08-29
forum: Programming Talk
---

### Post by skaboss on 2006-08-29
Hello,

I installed Sun's JDK via apt and Tomcat 4 manually. Was very happy with it, and then had the very bad idea to install Tomcat 5 via apt...

Some java appz won't work anymore, and when i type 
```
java -version
```, i get 
```
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```
in place of my wonderful Sun's jdk 5.0  :cry: 

When i try to purge gcj and all that messy stuff, i meet dependancies problems....

Please, how can i get out of this hell and revert to Sun's jdk ?

---

### Post by kaamos on 2006-08-29
```
sudo update-alternatives --config java
```

---

### Post by meng on 2006-08-29
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
Look at Selecting the default java version, see if that works for you.

---

### Post by skaboss on 2006-08-29
Thanks a lot guys !

This one 

```
sudo update-alternatives --config java
```

worked perfect =D>

---

### Post by hod139 on 2006-08-30
> **skaboss said:**
> Thanks a lot guys !

This one 

```
sudo update-alternatives --config java
``` 
worked perfect =D>

You really shouldn't be using that.  You should be using:
```
 sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by skaboss on 2006-08-31
Heeeellllpppp !!!

I followed the instructions above. It works fine, but everytime i restart my system, the infamous libgcj and friends take precedence over Sun's java.
Please, how to get out from this permanently ?

---

### Post by skaboss on 2006-08-31
Ok, i finally solved this problem, putting /usr/lib/jvm/java-1.5.0-sun at the very beginning of the path in /etc/environment.
Don't know if this is the best way to get rid of gcj, but at least it works.

Still i can't make Tomcat start at system boot (i have to start it manually via "sudo /etc/init.d/tomcat5 start"), although it seems to be correctly configured in the various /etc/rc links.

Any clue ?

---

### Post by ifokkema on 2006-09-02
Regarding to Tomcat; any errors in it's error log?

---

### Post by skaboss on 2006-09-02
Actually, no entry at all in tomcat's logs until i start it manually, which makes me think of something like tomcat can't find java in the path at boot up time, but finds it when i launch it manually...
Do you know of a way to set up the path correctly ?

---

### Post by ifokkema on 2006-09-02
That should leave errors in the syslog / dmesg... I think. Anything useful in there?

---

### Post by skaboss on 2006-09-02
Thank you for your answer, but no, nothing related to tomcat nor java...  :confused:

---

### Post by ifokkema on 2006-09-02
Hmm... My theory is, since that your problem started with the system using the **wrong** version of Java, that the problem is not that the when starting Tomcat at boot time, it can't find Java. I think that maybe it's not configured to start automatically...
What's the output of:
```
find /etc/rc?.d/ -iname \*tomcat\*
```

---

### Post by skaboss on 2006-09-02
Thanks a lot for your patience.
Here is what i get : 
```
landry@AlBundy:~$ find /etc/rc?.d/ -iname \*tomcat\*
/etc/rc0.d/K20tomcat
/etc/rc0.d/K20tomcat5
/etc/rc1.d/K20tomcat
/etc/rc1.d/K20tomcat5
/etc/rc2.d/K20tomcat
/etc/rc2.d/S20tomcat5
/etc/rc3.d/K20tomcat
/etc/rc3.d/S20tomcat5
/etc/rc4.d/K20tomcat
/etc/rc4.d/S20tomcat5
/etc/rc5.d/K20tomcat
/etc/rc5.d/S20tomcat5
/etc/rc6.d/K20tomcat
/etc/rc6.d/K20tomcat5
landry@AlBundy:~$

```

---

### Post by ifokkema on 2006-09-02
Well.. let's see. Just a guess:
You're in runlevel 2 (Ubuntu default). The system should start tomcat5, but stop tomcat. Maybe they interfere.

What if you:
```
sudo mv /etc/rc2.d/K20tomcat /etc/rc2.d/__K20tomcat
```
and reboot?

---

### Post by ynef on 2006-09-03
> **skaboss said:**
> Ok, i finally solved this problem, putting /usr/lib/jvm/java-1.5.0-sun at the very beginning of the path in /etc/environment.
Don't know if this is the best way to get rid of gcj, but at least it works.

I think the correct way to do this is to put it at the top of the file /etc/jvm

---

### Post by skaboss on 2006-09-03
> **ifokkema said:**
> Well.. let's see. Just a guess:
You're in runlevel 2 (Ubuntu default). The system should start tomcat5, but stop tomcat. Maybe they interfere.

What if you:
```
sudo mv /etc/rc2.d/K20tomcat /etc/rc2.d/__K20tomcat
```
and reboot?

nothing : still no tomcat after reboot...

---

### Post by skaboss on 2006-09-03
> **ynef said:**
> I think the correct way to do this is to put it at the top of the file /etc/jvm

I already did this, without effect : that's why i changed the path directly.

---

### Post by ifokkema on 2006-09-03
> **skaboss said:**
> nothing : still no tomcat after reboot...
Wow... quickly running out of ideas here...

This is the last I can think of:
- The /etc/rc2.d/S20tomcat5 script is not linked to the correct script.
```
ls -lah /etc/rc2.d/S20tomcat5
```
to check.
- It's indeed, as you suggested, a path problem. Usually, though, these scripts do not rely on any path setting and directly call the executables using the full path. But since this is my last idea: you might as well try to dig in your /etc/init.d/tomcat5 to see what it's doing. It's a bash script. Check for the executable it should start up and make sure the correct paths are added (you may want to create a backup of this script).

Good luck!

---

### Post by LordHunter317 on 2006-09-03
I'm pretty sure tomcat won't start without editing /etc/default/tomcat5 if you installed it from packages.

---

### Post by skaboss on 2006-09-03
Thank you very much for your great help. My problem is solved !
First, as you mentioned, ifokkema, i edited /etc/init.d/tomcat5 and changed the path there : it worked all right !
After your post, LordHunter317, i restored /etc/init.d/tomcat5, and edited /etc/default/tomcat5, and just put JAVA_HOME, and now tomcat will start at boot.
There's only one mystery left : why do i have to define JAVA_HOME in /etc/default/tomcat5, when it is already defined in the path (echo $JAVA_HOME returns the correct path) ?

---

### Post by LordHunter317 on 2006-09-03
> **skaboss said:**
> There's only one mystery left : why do i have to define JAVA_HOME in /etc/default/tomcat5, when it is already defined in the path (echo $JAVA_HOME returns the correct path) ?I forget the exact reasoning, but the tomcat5 startup process does a bunch of wierd stuff with the environment.  Also, I didn't read the thread, but if you defined JAVA_HOME /etc/profile or /etc/bash.bashrc, neither are read when init scripts are run.

---

