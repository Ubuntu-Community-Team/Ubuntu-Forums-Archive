---
title: "[SOLVED] installing java, If i cant i am going to replace ubuntu with win 2000"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by mikeftl on 2008-11-08
Dear everyone,
recently i have installed ubuntu to my micro sd card.
I actually loved it.
I thought it was very cool, almost better than windows.
However,
Windows is more advanced,less buggy,and has more software
I am trying to install java, If i cannot install java to ubuntu i am going to have to remove it and replace it with windows.
My questions are,
 can i actually install java (ive tried atleast 20 times with no avail)
 if i am going to install w2k can i install it to my micro sd card?
 will the installation change the boot process so that it would start windows 2k instead of vista by default (there are other users that use my computer and i am not trying to interrupt their useage.)
(its a 4gb micro sd card)
thank you

---

### Post by sirebral on 2008-11-08
It's easy.  Relax.

I had problems with this too.

Install Java:
I just discovered this is much easier then I thought.  Download the java BIN file from the Java web page
	[http://www.java.com/en/download/](http://www.java.com/en/download/)
Download the (self extracting file.  Then open a Terminal window and CHMOD it so you can run it.
	chmod  a+x <javafile>
Then while you are in the terminal run the file.
	./<javafile>

---

### Post by taurus on 2008-11-08
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by mikeftl on 2008-11-08
another thing is, I am running out of space.
The weird thing is i just installed it.
I updated ubuntu to 8.10 and now i only have like 500 mb of space left.
and i had 3gb before i updated.

---

### Post by bumanie on 2008-11-08
The / of 8.10 on my computer is 3.6gb - have a few extra things installed but not too many. The basic install takes about 3gb. Expecting to run a full ubuntu off 4gb is cutting things a bit fine IMO.

---

### Post by taurus on 2008-11-08
Reclaim some space with

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by mikeftl on 2008-11-08
> **taurus said:**
> Reclaim some space with

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
Thanks!
I got 1g back :)
im gonna try the java now i hope it works :|

---

### Post by mikeftl on 2008-11-08
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

wow it actually worked.
If they just put those 3 easy steps instead of all that other garbage then it would have made my life so much easier.
THANKS!!

---

### Post by igknighted on 2008-11-08
> **mikeftl said:**
> wow it actually worked.
If they just put those 3 easy steps instead of all that other garbage then it would have made my life so much easier.
THANKS!!

Because those are Ubuntu's directions.  They do not apply to all linux distributions.  Read about installing packages in ubuntu (via package repositories), and always look there first.  There are 20,000+ programs pre-packaged and as easy to install as java was for you, so always look there first.  It is recommended that an internet search or the manufacturers website is a last chance search for programs and drivers in linux.

---

