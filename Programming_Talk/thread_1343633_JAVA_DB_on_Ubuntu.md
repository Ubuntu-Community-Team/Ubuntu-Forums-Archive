---
title: "JAVA DB on Ubuntu"
date: 2009-12-02
forum: Programming Talk
---

### Post by appraveen on 2009-12-02
Hi,

I plan to write a small application. Now, Need help with the DB stuff. I plan to use JavaDB for the backend. Please tell me. Provide me with some links tutorials as to how do I find out if JavaDB is installed.

I have OpenJDK installed that got installed as part of some other installation.

Please help.

---

### Post by byStanderone on 2009-12-02
...javadb is in the repo, check your software source and update.

---

### Post by lykeion on 2009-12-03
How to install Java DB:
```
sudo apt-get install sun-javadb-client sun-javadb-core
```

How to enable Java DB:
Add the bin directory for Java DB to your PATH environment variable, and set a new DERBY_HOME environment variable.
Add these lines to the end of the .bashrc file in your home directory:
```

export PATH=$PATH:/usr/share/javadb/bin/
export DERBY_HOME=/usr/share/javadb
```
How to use Java DB:
[http://www.stuartellis.eu/articles/derby-javadb/]("http://www.stuartellis.eu/articles/derby-javadb/")

---

