---
title: "Need a Newer JDK"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by pteri498 on 2008-10-25
I am using Ubuntu Hardy. I need to install a newer version of the JDK than is available from the repositories.

The version that Aptitude installs for me is this:
```

$ javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.
$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

```

The version that I need (and my school uses) is this:
```

$ javac -version
javac 1.6.0_06
$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

I picked up jdk-6u10-linux-i586.bin from the Sun web site, but the installation guide is very vague on what to do next.

Does anyone have any ideas?

Thank you.

---

### Post by pteri498 on 2008-10-25
Solved!

I found this post: [http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=get_topic&f=13&t=001844](http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=get_topic&f=13&t=001844)

Basically I ran the following command to update the symlink of /bin/java and /bin/javac

```

$ sudo update-java-alternatives --set java-6-sun
...
$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
$ javac -version
javac 1.6.0_07

```

Not quite the newest version available, but it'll work.

---

### Post by __Frank__ on 2008-10-25
Hi Pteri,

Actually JDK 1.6 is available from the repository.

to install:
<code>
sudo aptitude install sun-java6-jdk
</code>

If after installing the sun jdk you're still not running the correct version, run this code:
<code>
sudo update-alternatives --config java
</code>
That last command allows you to switch the version you're using.

Hope this helps.

Cheers,
Frank

Edit: just saw that I was too late you found the answer yourself

---

