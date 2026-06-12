---
title: "set javac classpath"
date: 2011-12-13
forum: Packaging and Compiling Programs
---

### Post by ntesla123 on 2011-12-13
I have several jar files in a specific folder, but I can't get javac to understand it.

How do I set the classpath for javac. It is NOT the same classpath as the java command. And it's not enough with one jar file. I have several.

---

### Post by adit on 2011-12-14
> It is NOT the same classpath as the java command
Both java and javac get classpath settings from the same environment variable called CLASSPATH.
To set classpath for multiple jar files in a folder:
```
export CLASSPATH=Name_of_folder/*:.
```
Replace Name_of_folder with your own folder name.  Note the colon(:) and the dot(.) immediately following the folder name.
The colon is the separator for multiple entries.
The dot means current directory.

---

