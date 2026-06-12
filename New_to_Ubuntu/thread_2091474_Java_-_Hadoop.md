---
title: "Java - Hadoop"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by Riham on 2012-12-05
Hello,
I installed Java Sun 6 for Hadoop file system but everytime I try to set it as Java Home, it gets back to be not set as soon as I close the terminal. 
Can anyone tell me what to do ?

I used the commands :
sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
export JAVA_HOME=/usr/lib/jvm/java-1.6.0_24
echo $JAVA_HOME

Thanks in advance.

---

### Post by Riham on 2012-12-05
any help ?

---

### Post by fbicknel on 2013-02-21
Based on a tip I found here: [http://ubuntuforums.org/archive/index.php/t-1010605.html](http://ubuntuforums.org/archive/index.php/t-1010605.html) (near the end of the thread), I installed the following in /etc/profile.d/set_java_home.sh:

```
export JAVA_HOME=$(dirname $(dirname $(readlink -e /usr/bin/java)))
```

Not sure this is the best way, but it so far seems the most automatic way.  Before I did this, the static entry I had there became outdated every time Java was updated.

Anyway, hopefully someone will find this helpful.

---

### Post by Riham on 2013-02-24
Indeed, this link has the solution!
the solution lied in the reply of December 14th, 2008, 05:59 AM.
Thank you so much ! :D

---

