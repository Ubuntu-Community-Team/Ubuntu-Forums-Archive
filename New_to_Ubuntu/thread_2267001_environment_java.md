---
title: "environment java"
date: 2015-02-26
forum: New to Ubuntu
---

### Post by programmer2 on 2015-02-26
how can i make java_home for jdk7 in my envirment system ?!

---

### Post by yetimon_64 on 2015-02-26
> **programmer2 said:**
> how can i make java_home for jdk7 in my envirment system ?!

I'm assuming you mean you want an environment variable called JAVA_HOME to be set for use with jdk7.

1. To do so open your home folder and press "ctrl + h" on your keyboard to show hidden files and folders.

2. In the hidden files and folders look for and open the file ".profile" in your text editor. 

3. At the end of the file on a new line add the contents of the next code box, *_alter "/path/to/jdk/home/folder" to the actual location of the jdk home folder. _*  

```
export JAVA_HOME=/path/to/jdk/home/folder
```

4. Save the file and exit.

5. Log out of the desktop, then log back in and the JAVA_HOME environment variable should be set.

6. To check if set, open a terminal (ctrl + alt + t, in Unity DE) and copy/paste the next code box and press enter.

```
echo $JAVA_HOME
``` If set correctly the terminal will reply with the actual path for "/path/to/jdk/home/folder".

---

