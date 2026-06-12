---
title: "setting the classpath for java"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by suman garg on 2012-06-10
i m very new to ubuntu..and i want to run java on it
i downloaded the  jdk-7u3-linux-i586 but when i tried to run a java program then terminal showed  the following error

Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

during surfing the net i found that i need to set the classpath  but after trying so much
i m unable to resolve this problem...
so plz help mee......

---

### Post by coffeecat on 2012-06-10
Post moved to its own thread from very old Forum Feedback thread.

@suman garg, please do not add posts to threads about other topics. You can start your own thread by going to the appropriate forum or sub-forum and clicking on the orange "New Thread" button near the top left of the page.

---

### Post by Cheesemill on 2012-06-10
If you just downloaded the   jdk-7u3-linux-i586 file then you haven't installed Java yet.
However, instead of telling you how to install that I'm going to suggest a better method, install Java from a PPA instead. This way it will be integrated with the Ubuntu package management system and automatically stay up to date.

To install Java:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by suman garg on 2012-06-15
@coffeecat  thanks for the info.
i'll take care of it for future threads..

---

### Post by suman garg on 2012-06-15
thanks a lot..now i can run my programs without a hitch....

---

