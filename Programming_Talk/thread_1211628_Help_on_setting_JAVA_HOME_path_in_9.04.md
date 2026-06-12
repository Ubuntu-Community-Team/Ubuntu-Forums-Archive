---
title: "Help on setting JAVA_HOME path in 9.04"
date: 2009-07-12
forum: Programming Talk
---

### Post by cwrighta70 on 2009-07-12
Hey all,

Okay, I'm brand new to Linux, and am running Ubuntu 9.04.  I've installed Java SE 6u14 into /usr/local/  and edited the bash.bashrc file as follows:

```
PATH=$PATH:/usr/local/jdk1.6.0_14/bin
export PATH
```

and edited the environment variables as follows:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/local/jdk1.6.0_14"
CLASSPATH="/usr/local/jdk1.6.0_14/lib"
```

However, something is not right.  When trying to run a project in NetBeans, I get a "JAVA_HOME is not defined" error.

Any help would be greatly appreciated.

Thanks,
Chris

---

### Post by slavik on 2009-07-12
why not install 1.6u14 from the repo?

---

### Post by cwrighta70 on 2009-07-12
I would love to do that, granted I knew how.  If you could provide a link to a writeup, or some directions, that would be wonderful.  Thanks

---

### Post by slavik on 2009-07-12
```

sudo apt-get install sun-java6-jdk
# say yes when prompted
# and to set up all the proper links in the alternatives system
sudo update-java-alternatives -s java-6-openjdk
# Peanut butter jelly time!

```

EDIT: this installs the JDK, which has everything. :)

---

### Post by cwrighta70 on 2009-07-12
> **slavik said:**
> ```
# and to set up all the proper links in the alternatives system
sudo update-java-alternatives -s java-6-openjdk

```

Okay, everything went smooth up until this step.  Typing "sudo update-java-alternatives -s java-6-openjdk" gave me 

```
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-openjdk
```

---

### Post by slavik on 2009-07-13
what does `sudo update-java-alternatives -l` output?

---

### Post by cwrighta70 on 2009-07-13
The above gave me:

```
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

---

### Post by jespdj on 2009-07-13
Try this instead:
```
sudo update-java-alternatives -s java-6-sun
```
(Note: java-6-sun instead of java-6-openjdk).

---

### Post by cwrighta70 on 2009-07-13
Thank you, slavik and jespdj, for your help.  Everything is working as it should.

Chris

---

