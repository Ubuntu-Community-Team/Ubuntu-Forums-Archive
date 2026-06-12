---
title: "Help installing .jar files"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-09-12
Hy all.Finally I manage to install Warcraft III and play on BattleNet.I have a question though.In windows I used banlist, but I can't make it run through wine.I found an alternative here:
[http://sourceforge.net/project/showfiles.php?group_id=183941&package_id=213826](http://sourceforge.net/project/showfiles.php?group_id=183941&package_id=213826)
It's still in alpha stage, but I decided to give it a go.Unfortunately, when I unpack it, it's a .jar file.I have no idea how to install such a file.Can you help me?

---

### Post by MegaJim on 2008-09-12
you run java files by using 

```
java -jar /path/to/jar/file.jar
```

---

### Post by Troll_the_Great on 2008-09-12
> **MegaJim said:**
> you run java files by using 

```
java -jar /path/to/jar/file.jar
```

This is what I get...
```
troll@My-precious:~$ java /home/troll/Desktop/jwc3banlist-0.2/jwc3banlist.jar
Exception in thread "main" java.lang.NoClassDefFoundError: /home/troll/Desktop/jwc3banlist-0/2/jwc3banlist/jar
Caused by: java.lang.ClassNotFoundException: .home.troll.Desktop.jwc3banlist-0.2.jwc3banlist.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: /home/troll/Desktop/jwc3banlist-0.2/jwc3banlist.jar. Program will exit.
```
Any ideas?


EDIT:sorry for this post, I saw too late that I made a syntax error...

---

### Post by Troll_the_Great on 2008-09-12
> **MegaJim said:**
> you run java files by using 

```
java -jar /path/to/jar/file.jar
```

I've run the command but nothing seems to happen....
```
troll@My-precious:~$ java -jar /home/troll/Desktop/jwc3banlist-0.2/jwc3banlist.jar
troll@My-precious:~$
```
Does this means that is installed?Where did it go?

---

### Post by MegaJim on 2008-09-12
It could mean anything, but most likely the program encountered an error and couldn't start.  If you don't have access to any documentation, your best bet is to try executing the jar in verbose mode to see if you can trace down the problem

```
java -verbose -jar /path/to/jar/file.jar
```

---

### Post by Troll_the_Great on 2008-09-12
> **MegaJim said:**
> It could mean anything, but most likely the program encountered an error and couldn't start.  If you don't have access to any documentation, your best bet is to try executing the jar in verbose mode to see if you can trace down the problem

```
java -verbose -jar /path/to/jar/file.jar
```

Did that and I got a bunch of lines (too many to see them all in the terminal).
Should I paste the ones I got?

---

### Post by MegaJim on 2008-09-12
I just found this:

[http://ubuntuforums.org/showpost.php?p=5587895&postcount=10](http://ubuntuforums.org/showpost.php?p=5587895&postcount=10)

try it out and let me know


Edit: I see, that you posted in that thread !

You should send that dev a message :)

Have you tried running it as root like he says?

---

### Post by MegaJim on 2008-09-12
Ok, I just downloaded it and got it working, try using these commands and let me know how you get on:

```
sudo apt-get install sun-java6-jdk libpcap0.8
```

```
wget http://netresearch.ics.uci.edu/kfujii/jpcap/jpcap-0.7.deb | gdebi-gtk jpcap-0.7.deb

```

Then start it like before, this time prepending the command with sudo

You can also create a shortcut using that command, except that you would need to change sudo for gksu and java with its full path (usually /usr/bin/java).

Let me know how it goes

---

### Post by Troll_the_Great on 2008-09-12
> **MegaJim said:**
> Ok, I just downloaded it and got it working, try using these commands and let me know how you get on:

```
sudo apt-get install sun-java6-jdk libpcap0.8
```

```
wget http://netresearch.ics.uci.edu/kfujii/jpcap/jpcap-0.7.deb | gdebi-gtk jpcap-0.7.deb

```

Then start it like before, this time prepending the command with sudo

You can also create a shortcut using that command, except that you would need to change sudo for gksu and java with its full path (usually /usr/bin/java).

Let me know how it goes


OK, I got it working, but I close it and I don't know how to start it anymore.Where did it go?Can you give me the exact command for the shortcut?

---

