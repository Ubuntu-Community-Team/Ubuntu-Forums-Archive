---
title: "How to compile java programs in Ubuntu"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-05-26
I am a beginner dto java and want a step by step procedure as to how to compile java programs in Ubuntu Linux.

---

### Post by Inxsible on 2008-05-26
Same way as you would on a Windows machine. Remember, Java is platform independent.

The java compiler can be used like ```
javac /pathToJavaFile
```

---

### Post by ginger_meggs on 2008-05-27
You'll most likely have to download the Sun JDK as it's not packaged with Ubuntu by default due to licensing issues. You can get the JDK from java.sun.com

Once you've installed the JDK you will probably need to use update-alternatives from the terminal to set your shiny new JDK as the default target for all calls to java and javac otherwise it will still be pointing to the old non-Sun JRE.

After that all should be well and you should be away!

---

### Post by Inxsible on 2008-05-27
you can also install sun java 6 from the repos, provided you enable the universe and multiverse repos.
```
sudo aptitude install sun-java6-jdk sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

