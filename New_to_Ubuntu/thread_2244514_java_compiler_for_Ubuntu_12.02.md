---
title: "java compiler for Ubuntu 12.02?"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by ppalmer347 on 2014-09-16
I am looking for a java compiler and didn't seem to be able to find one at the archive with apt-get install.  I tried all the names I know about java, jdk, openjdk.

I looked in the forum and found only posts from 2008, and a lot of time has gone by, so I thought I should ask again.

---

### Post by pissedoffdude on 2014-09-16
Do you mean 12.04?  If that's the case, either of these should work.

For openjdk6:
```
sudo apt-get update
sudo apt-get install default-jdk

```

For openjdk7:
```
sudo apt-get update
sudo apt-get install openjdk-7-jdk

```

---

### Post by claracc on 2014-09-17
As it is forementioned, you need to have openjdk-7-jdk software package installed in ubuntu in order to compile .java files.

Then you do compilation through command:

javac name_of_file.java

Please, see link: [http://askubuntu.com/questions/145748/how-to-compile-a-java-file](http://askubuntu.com/questions/145748/how-to-compile-a-java-file)

---

