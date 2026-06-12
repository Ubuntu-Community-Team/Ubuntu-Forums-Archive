---
title: "How do I install Java?"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by Malacath on 2013-03-16
Can somebody please tell me how to install Java?

The Java website has the linux downloads but they are not debian packages.
They are RPM and tar.gz files and I don't have a clue what to do with those. The instructions on the website are complicated and makes it look like I wouldn't be able to uninstall it easily.

I would rather download stuff using the software centre but I can't find java on that. I found something called Icedtea java. Will that do the same thing as normal Java?

---

### Post by r-senior on 2013-03-16
There is a community help page for installing Java in its different forms:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

For most purposes, installing the [openjdk-7-jdk]("http://apt.ubuntu.com/p/openjdk-7-jdk") package will get you what you need for development.

---

### Post by Malacath on 2013-03-16
Thanks

They're the instructions I thought are complicated.

Anyway I just tried installing the icetea and it didn't work at first while using chrome but just tried it in firefox and it seems to work now

---

### Post by mörgæs on 2013-03-16
If you are searching for a plug-in for the browser, you will be fine with

```
sudo apt-get install icedtea-7-plugin
```

---

