---
title: "Change Java"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by skymera on 2008-05-08
Currently i have Sun-Java-6.

It wont work with my FrostWire. Don't know why, i've tried everything.

Is there any alternatives (JRE) that are opensource?

I read about IcedTea but thats only a dummy package in the repos.

Thanks

---

### Post by glennric on 2008-05-08
I don't think frostwire will work with anything but sun-java.
Are you sure that you have sun-java selected as your default java?  If you just installed sun-java and did nothing more then you don't have it selected. 
Type 
```
sudo update-alternatives --config java
```
and make sure that there is a * by the java-6-sun line.

---

### Post by skymera on 2008-05-08
Yes it's default.
Ive ran that command several times.

I read on another thread IcedTea fixed it =S so im just curious.

---

### Post by glennric on 2008-05-08
Have you tried running frostwire from a terminal to see what errors it is giving?

---

### Post by skymera on 2008-05-08
I followed a command from another website

Which linked a Java file to Frostwire so all if well.
Thanks for you posties.

---

### Post by glennric on 2008-05-08
Let me know if it works.  Another problem could be if you are using dash instead of bash.  If you don't know then you are using dash.  That is the default for Ubuntu.  Type
```
sudo dpkg-reconfigure dash
```
and select No when it asks you if you want to install dash as /bin/sh.

---

