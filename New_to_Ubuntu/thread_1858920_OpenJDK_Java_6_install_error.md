---
title: "OpenJDK Java 6 install error"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by lumop on 2011-10-13
I am fairly new to linux. I recently installed Xubuntu 10.04 on my laptop. When I try to install OpenJDK Java 6 runtime from the Ubuntu software center, there is an error message that says...

"Previous installation hasn't been completed" 
"The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

How can I repair this? Thank you.

---

### Post by thatguruguy on 2011-10-13
Open a terminal, and type the following:```

sudo apt-get -f install
```

---

### Post by Gremlinzzz on 2011-10-13
how i install java
first go to synaptic package manager
click settings choose repositories
click other software make sure the canonical boxs are checked.then follow instructions and update or sudo apt-get update
 in terminal 

sudo apt-get install sun-java6-jre sun-java6-plugin


i also uninstall openjdk so it doesn't bump heads with sun Java

reason i play at a game site that OpenJDK Java 6 doesn't work:popcorn:

oh,yeah when it comes to the part where you have to click OK hit the tab button on keyboard then enter.

---

### Post by thatguruguy on 2011-10-13
> **Gremlinzzz said:**
> how i install java
first go to synaptic package manager
click settings choose repositories
click other software make sure the canonical boxs are checked.then follow instructions and update or sudo apt-get update
 in terminal 

sudo apt-get install sun-java6-jre sun-java6-plugin


i also uninstall openjdk so it doesn't bump heads with sun Java

reason i play at a game site that OpenJDK Java 6 doesn't work:popcorn:

If you read the original post, you'd see that the problem is he has broken packages. It's not just that he can't install java, he can't install anything until he fixes the broken packages.

---

### Post by yndesai on 2011-10-13
Follow instructions for the "[**Linux self extracting binary file**]("http://www.java.com/en/download/help/linux_install.xml#selfextracting") "
 
[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)
 
and you will be able to install sun java

---

### Post by Gremlinzzz on 2011-10-13
> **thatguruguy said:**
> If you read the original post, you'd see that the problem is he has broken packages. It's not just that he can't install java, he can't install anything until he fixes the broken packages.

read i did you gave the fix 
sudo apt-get -f install
i just suggested sun Java as a better choice:popcorn:

---

### Post by lumop on 2011-10-13
> **thatguruguy said:**
> Open a terminal, and type the following:```

sudo apt-get -f install
```

This worked. Thanks for all the quick replies. And i'll try out sun java.

---

