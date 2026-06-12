---
title: "Decompress files"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by Phizzurp on 2012-06-30
I'm in the process of installing Java (JRE and JDK). I'm at the part where I need to extract the tar.gz's into my usr/local/java folder. The command I'm trying to extracts them into the Downloads folder. How do I make it so it extracts it into /usr/local/java?

 tar xvzf jdk-7u5-linux-x64.tar.gz

That's the command I was trying to use.

---

### Post by yabbadabbadont on 2012-06-30
tar xvzf jdk-7u5-linux-x64.tar.gz -C /usr/local/java

---

### Post by Phizzurp on 2012-06-30
> **yabbadabbadont said:**
> tar xvzf jdk-7u5-linux-x64.tar.gz -C /usr/local/java

tar (child): jdk-7u5-linux-x64.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

Note the "jdk-7u5-linux-x64.tar.gz" is already located in /usr/local/java. I just need to extract it to the same folder.

---

### Post by yabbadabbadont on 2012-06-30
Make sure that you are in the /usr/local/java directory.  ```
cd /usr/local/java
```  Then run the command you initially posted, but add "sudo" to the front so that you have permission to write in that directory.  ```
sudo tar xvzf jdk-7u5-linux-x64.tar.gz
```

Have you read the docs for installing Java?  There might be an easier way.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

