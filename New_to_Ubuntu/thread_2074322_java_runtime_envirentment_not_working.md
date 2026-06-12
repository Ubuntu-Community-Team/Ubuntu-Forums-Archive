---
title: "java runtime envirentment not working"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-10-21
i need to install jre in ubuntu 12.10 to run web based applications on internet but i installed open jdk runtime envirentment  but its not working with apps is that a wrong downloadings on ubuntu but its installed correctly says java runtime envirentment but java .com not detecting jaava

---

### Post by Cheesemill on 2012-10-21
You may need to use Oracle Java instead of the open source version as some applications refuse to recognise Open JRE.

To install just copy and paste the following commands into a terminal one line at a time:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by marlow59 on 2012-10-21
If that solved your problem please mark the topic as solved using the Thread tools menu.

---

