---
title: "How do I get Java to work in Firefox?"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by Qu0ll on 2011-10-30
In Ubuntu 11.10 I installed OpenJDK Java 6 Runtime but I cannot run Java applets in Firefox.  I would have thought that would work automatically.  How can I get Firefox to use my newly installed version of Java to run applets?

---

### Post by jtarin on 2011-10-30
In a terminal make your way to your firefox plugins directory
- In your firefox plugins directory, type the following:
```
ln -s pathtoyourjavadirectory/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
```
- This will make a symbolic link from the java plugin to your firefox plugins directory.
- For what it's worth you can do the same thing in the ./mozilla/plugins directory. Depending on the plugin, you need to put it in one or the other.
You will need to determine your java directory.Mine is /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7

---

### Post by Qu0ll on 2011-10-30
Thanks.  Does that apply to OpenJDK java as well?  I have no idea where that is installed.

Actually, I would rather install Sun/Oracle Java but I couldn't find it in the Software Center.  How did you install it?

---

### Post by Lildirt on 2011-10-30
I really recommend downloading either Oracle Java 7, or OpenJDK 7.
Either one will probably work for you better.
I was not able to input into any java applet with OpenJDK6.

---

### Post by Qu0ll on 2011-10-30
> **Lildirt said:**
> I really recommend downloading either Oracle Java 7, or OpenJDK 7.
Either one will probably work for you better.
I was not able to input into any java applet with OpenJDK6.

Yes, Oracle Java 7 is what I really want to install but am I right in that there are no packages for Ubuntu and that I would have to manually install it and configure it?

---

### Post by Perfect Storm on 2011-10-30
> **Qu0ll said:**
> Yes, Oracle Java 7 is what I really want to install but am I right in that there are no packages for Ubuntu and that I would have to manually install it and configure it?

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

It was removed due to license issue (Oracle changed license on Java).

---

### Post by Spyderkid on 2011-10-30
install ubuntu restricted extras from the software centre
ubuntu restricted extras enables all the important things, flash, java, mp3, etc

or you can install it from the terminal by running....
```

sudo apt-get install ubuntu-restricted-extras

```



then if you want Java 7  install JavaJDK 7 from the software centre

---

### Post by Perfect Storm on 2011-10-30
> **Spyderkid said:**
> install ubuntu restricted extras from the software centre
ubuntu restricted extras enables all the important things, flash, java, mp3, etc

or you can install it from the terminal by running....
```

sudo apt-get install ubuntu-restricted-extras

```



then if you want Java 7  install JavaJDK 7 from the software centre

That have changed in ubuntu 11.10
ubuntu-restricted-extra installs icedtea-plugin

---

### Post by Qu0ll on 2011-10-30
> **Artificial Intelligence said:**
> [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

It was removed due to license issue (Oracle changed license on Java).

Thanks. I followed the instructions and it all works now :p

---

