---
title: "Java Problems"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Warpster Buntu on 2008-10-01
I downloaded Java quite some time ago, when I first started Ubuntu.

But now, it doesn't work, but yet it doesn't say it is not an uninstall plugin; just a blank screen.

This started happening a coupe days ago.

---

### Post by Michael.Godawski on 2008-10-01
Let's first check which version do you have installed:

```
java -version 
``````

sudo update-java-alternatives -l
```I had to install the following packages to run Java on my machine:

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Warpster Buntu on 2008-10-01
Still isn't working.

And yes,I have version 6.

However, I am in need of sleep. Please post your replies, but I will not be able to look at them until tomorrow evening.

---

### Post by kpkeerthi on 2008-10-01
How did you install java?

---

### Post by Warpster Buntu on 2008-10-01
I went to a site that required it, then downloaded the "missing plug in"

---

