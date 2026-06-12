---
title: "No command 'java' found"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Coralin on 2013-02-17
I've been running a Minecraft server on my ubuntu box successfully for a few days, now; but last night, I needed to restart the server because it was giving me some performance hiccups. It stopped successfully, but when I went to re-start, I got the following:

> coralin@PC:~$ java -Xms1G -Xmx1G -jar /srv/minecraft-server/ftbserver.jar nogui
No command 'java' found, did you mean:
 Command 'java' from package 'openjdk-6-jre-headless' (universe)
 Command 'java' from package 'gcj-4.6-jre-headless' (main)
 Command 'java' from package 'gcj-4.7-jre-headless' (main)
 Command 'java' from package 'default-jre' (main)
 Command 'java' from package 'openjdk-7-jre-headless' (main)
java: command not found

After searching, I tried the following: 

> coralin@PC:~$ java -version
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.1) (6b27-1.12.1-2ubuntu0.12.10.2)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

Which seems to indicate that Java IS installed. I decided to try "installing" one of the packages the error seemed to indicate were not in place - 
> coralin@PC:~$ sudo apt-get install openjdk-6-jre-headless openjdk-7-jre-headless 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jre-headless is already the newest version.
openjdk-6-jre-headless is already the newest version.
openjdk-6-jre-headless set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
OK... so now, it appears Java is installed, but for some reason, isn't available as a command? 
(Also- same with SUDO)- 
> coralin@PC:~$ sudo java -Xms1G -Xmx1G -jar /srv/minecraft-server/ftbserver.jar nogui
sudo: java: command not found

I've searched all over for these errors, tried several solutions- but it all ends up right here again. 
Any help would be greatly appreciated; thanks!

---

### Post by stmiller on 2013-02-17
What is the output of:

```
which java
```

?

---

### Post by Bashing-om on 2013-02-17
How about the path environment ?
What script is invoking java at startup ?

[INDENT]just my thoughts

[/INDENT]

---

### Post by Coralin on 2013-02-17
> **stmiller said:**
> What is the output of:

```
which java
```

?

```
coralin@PC:~$ which java
/usr/bin/java[CODE]
```[/CODE]

Bashing; I don't really know how to answer those questions; where would I find that info?

Thanks so much for the help!

---

### Post by schragge on 2013-02-17
To display path environment
```
echo $PATH
```
The second question I don't understand either.
Please post the output of
```
update-alternatives --display java
namei -l /usr/bin/java

```

---

### Post by Coralin on 2013-02-17
```
coralin@PC:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

```
coralin@PC:~$ update-alternatives --display java
java - manual mode
  link currently points to /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
/usr/lib/jvm/java-6-openjdk-i386/jre/bin/java - priority 1061
  slave java.1.gz: /usr/lib/jvm/java-6-openjdk-i386/jre/man/man1/java.1.gz
/usr/lib/jvm/java-7-openjdk-i386/jre/bin/java - priority 1071
  slave java.1.gz: /usr/lib/jvm/java-7-openjdk-i386/jre/man/man1/java.1.gz
Current 'best' version is '/usr/lib/jvm/java-7-openjdk-i386/jre/bin/java'.
```

```
coralin@PC:~$ namei -l /usr/bin/java
f: /usr/bin/java
drwxr-xr-x root root /
drwxr-xr-x root root usr
drwxr-xr-x root root bin
lrwxrwxrwx root root java -> /etc/alternatives/java
drwxr-xr-x root root   /
drwxrwxr-x root root   etc
drwxrwxr-x root root   alternatives
lrwxrwxrwx root root   java -> /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
drwxr-xr-x root root     /
drwxr-xr-x root root     usr
drwxr-xr-x root root     lib
drwxr-xr-x root root     jvm
drwxr-xr-x root root     java-7-openjdk-i386
drwxr-xr-x root root     jre
drwxr-xr-x root root     bin
-rwxr-xr-x root root     java
```

---

### Post by schragge on 2013-02-17
Weird.
Try
```

env PATH=/usr/bin:/bin java -Xms1G -Xmx1G -jar /srv/minecraft-server/ftbserver.jar nogui

```

---

### Post by Coralin on 2013-02-17
> **schragge said:**
> Weird.
Try
```

env PATH=/usr/bin:/bin java -Xms1G -Xmx1G -jar /srv/minecraft-server/ftbserver.jar nogui

```


That successfully ran the server; any idea what I could do for a "permanent" fix; or what could be causing this?

---

### Post by schragge on 2013-02-17
Hmm&#8230; Do you have something java-related installed in */usr/local/bin*?
What does *whereis java* show?

---

### Post by Coralin on 2013-02-17
No; That folder is empty.

---

### Post by Coralin on 2013-02-17
OK, wow. There is something messed up going on here... now I'm getting 
> No command '&#65279;env' found, did you mean:
 Command 'env' from package 'coreutils' (main)
env: command not found


---

### Post by Coralin on 2013-02-17
> **schragge said:**
> 
What does *whereis java* show?

```
java: /usr/bin/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz

```

---

### Post by schragge on 2013-02-17
Can you still invoke it as */usr/bin/env*? At this point, I'd reboot into repair mode and check the filesystem for errors.

---

