---
title: "How to find a full installation path of Java8 JDK?"
date: 2015-09-27
forum: Programming Talk
---

### Post by pavelexpertov on 2015-09-27
Hello, I downloaded oracle developer sql and I installed the openjdk-8 via terminal xubuntu 15.04. Once I have done that, I have used the command locate to find full path of jdk8, but found only two paths that lead to jre8 (I think so). since then i struggled to get the full path. Can anyone help on how to find the path because the sql developer only uses java 8 and nothing else. Thanks.

---

### Post by TheFu on 2015-09-27
locate provided the answer. Sorry you don't like it.
Are you certain that Oracle's SQL doesn't require the proprietary Oracle JDK? Will it work with OpenJDK at all?

---

### Post by Habitual on 2015-09-27
Let's start with what we can know.
Open a terminal and issue:
```
java -version
``` and paste the results.

Thank you.

---

### Post by sam_baker2 on 2015-09-27
Don't know if this helps but I use this to show which java's I have installed with path, plus, lets you change to what you want:

```

sudo update-alternatives --config java
exit 0

```

---

