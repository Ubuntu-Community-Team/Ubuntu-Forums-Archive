---
title: "Oracle's Java 32bit JRE"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by carolin3 on 2013-04-18
Hello,

I installed Java 7 JRE x86 (couldn't find 32bit) on my computer. However
I can't find it when I want to open a .jar file.

I tried to follow another post that I found regarding this but using the JDK, it didn't
work, so any help would be very much appreciated.

//Caroline

---

### Post by Mopar1973Man on 2013-04-18
Here is what I'm using...

```

sudo add-apt-repositiory ppa:webup8team/java

sudo apt-get update

sudo apt-get install oracle-java7-installer

```

After installing double check with...

```

java -version

```

---

### Post by carolin3 on 2013-04-18
Thanks,

I get this when I try to add the repository, I don't know why I get it, ( I obviously have an internet connection)

xxx@xxx-X101CH:~$ sudo add-apt-repository ppa:webup8team/java
Cannot access PPA ([https://launchpad.net/api/1.0/~webup8team/+archive/java](https://launchpad.net/api/1.0/~webup8team/+archive/java)) to get PPA information, please check your internet connection.

---

### Post by slickymaster on 2013-04-18
> **carolin3 said:**
> Thanks,

I get this when I try to add the repository, I don't know why I get it, ( I obviously have an internet connection)

xxx@xxx-X101CH:~$ sudo add-apt-repository [COLOR=#ff0000]ppa:webup8team/java[/COLOR]
Cannot access PPA ([https://launchpad.net/api/1.0/~webup8team/+archive/java](https://launchpad.net/api/1.0/~webup8team/+archive/java)) to get PPA information, please check your internet connection.

It is **webupd8team** and not [COLOR=#FF0000]webup8team.

[/COLOR]It's better if you copy paste into your terminal:
[COLOR=#FF0000][/COLOR]```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by carolin3 on 2013-04-18
Thanks it worked very well :)

//Caroline

---

### Post by Mopar1973Man on 2013-04-28
For future info.
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

