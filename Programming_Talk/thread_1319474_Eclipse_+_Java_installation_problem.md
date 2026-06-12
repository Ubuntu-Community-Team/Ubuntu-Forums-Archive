---
title: "Eclipse + Java installation problem"
date: 2009-11-08
forum: Programming Talk
---

### Post by pearlygate on 2009-11-08
Hi,

I am using Karmic Koala. I installed eclipse using Ubuntu software center and I installed sun java package using this command :
sudo apt-get install sun-java6-jdk

My problem is, my eclipse does not detect java for some reason, because when I go to eclipse I cannot create java project. I searched the internet and it seems there is this file /etc/eclipse/java_home file in which I can setup the path to my java bin but for some reason I don't have that eclipse directory in my /etc. Did I miss anything? how can I make eclipse "recognize" java language exist in my computer?

Thank you for your help.

---

### Post by diafanos on 2009-11-08
You can specify where java is located by editing the file eclipse.ini which is in /usr/lib/eclipse directory.

Add the following line just before the -vmargs:

```

-vm <path_to_the_java_executable>

```

I use OpenJDK and the location is: 
/usr/lib/jvm/java-6-openjdk/jre/bin/java

---

### Post by pearlygate on 2009-11-08
It turns out I was installing bare-bone eclipse. That's why I don't even have any plug-in for anything. I am now installing the plugin for java development. Thanks for the help :)

---

