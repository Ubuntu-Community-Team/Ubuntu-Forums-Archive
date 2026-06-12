---
title: "How to downlaod a .jpg-file in c++ using wget"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by slartibartfast2 on 2016-01-22
Hi guys,

I'm new to ubuntu and I was wondering how one can use the wget-function to download a .jpg-file within a c++-program.
I have seen a similar solution for windows, namely using the line

```
system("C:\\Users\\Me\\Desktop\\wget.exe http://pixelcaster.com/yosemite/webcams/ahwahnee2.jpg -O C:\\Users\\Me\\Desktop\\ahwahnee2.jpg");
```

in the c++-code.

I'm looking for a similarly simple solution for ubuntu. 
Help would be much appreciated. Thanks in advance

---

### Post by slartibartfast2 on 2016-01-22
Ok, i found out myself.

```
 system("wget -nd http://pixelcaster.com/yosemite/webcams/ahwahnee2.jpg -O ahwahnee2.jpg"); 
```

/thread

---

### Post by ajgreeny on 2016-01-22
To help anyone else who is searching please mark the thread as SOLVED from the Thread Tools menu at the top.

---

