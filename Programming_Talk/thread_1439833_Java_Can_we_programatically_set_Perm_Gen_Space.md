---
title: "Java: Can we programatically set Perm Gen Space?"
date: 2010-03-26
forum: Programming Talk
---

### Post by andrew222 on 2010-03-26
Hello,

I have a question relating to Java memory Management.

I wanted to know if there is a way that we can programmatically pass the JVM the argument for Permanent Generation space?


We are currently using Java 1.4 (I know...it's old)

---

### Post by myrtle1908 on 2010-03-26
Can't you use: -XX:MaxPermSize=nnnM

Where n = your desired max MB.

---

