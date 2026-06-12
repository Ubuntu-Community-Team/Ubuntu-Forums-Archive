---
title: "Guide for NachOS 5J?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Spadoof on 2011-09-27
Dear readers,

I was wondering if anyone had an easy to follow guide for implementing NachOS 5J on Ubuntu 11.04? I have found a few step-by-step guide on Youtube.com but they seem to be for NachOS version 4. If anyone could help I would sincerely appreciate it.

I have already attempted to implement NachOS 5J on my machine, but I keep getting errors when I try to execute the program. Here is what I did:

1) I downloaded and extracted nachOS 5 to my home directory.
2) I installed sun-java6-jdk package.
3) I then try to execute the nachos file.

I receive this error:
java.lang.ClassNotFoundException: nachos.machine.Machine
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: nachos.machine.Machine. Program will exit.

Again, any help you could provide would be greatly appriciated.

Thanks,
-Spadoof

Here is a link to Nachos's 5J:
[http://inst.eecs.berkeley.edu/~cs162/fa05/Nachos/index.html](http://inst.eecs.berkeley.edu/~cs162/fa05/Nachos/index.html)

---

### Post by ubudog on 2011-09-28
Run:
```
chmod +x filename
```

Then you should be able to run it.

---

### Post by Spadoof on 2011-09-29
I typed in the command that you provided and it still will not work (I receive the same error message). I think the problem is that NachOS does not see Java library for some reason. Is there anything else you would suggest?

Thanks,
-Spadoof

---

### Post by ubudog on 2011-09-29
> **Spadoof said:**
> I typed in the command that you provided and it still will not work (I receive the same error message). I think the problem is that NachOS does not see Java library for some reason. Is there anything else you would suggest?

Thanks,
-Spadoof

Hmm, after typing that command, try:
```
filename.jar
```
(where filename is NachOS of course)

---

### Post by Spadoof on 2011-09-29
~$ cd nachos
~/nachos$ cd bin
~/nachos/bin$ chmod +x nachos
~/nachos/bin$ nachos.jar
nachos.jar: command not found
~/nachos/bin$

Still no dice unfortunately. I talked with my professor today. He said that nachos was not able to find Java. He told me to put this in my ~/.profile file:

 if [ -d "$HOME/nachos/bin" ] ; then
          PATH="$HOME/nachos/bin:$PATH"
        fi

along with a path to Java. Does this make any sense to anyone?

-Spadoof


P.S:
By the way I am using Ubuntu 11.04 64-bit

So in my .bashrc file I added the lines:
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64
export PATH=$JAVA_HOME/bin:$PATH

I still get an error when trying to execute the nachos file in /home/*name*/nachos/bin

but when I run the command "env" I get this output:
PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Shouldn't nachos be working now? My path is set to see java from any directory. If this is incorrect how can I fix it?

P.S.S
Alright, How can I set a path so it can see java?
I add these lines to my .bashrc file:
export JAVA_HOME=/usr/bin/jvm/java-6-openjdk
export PATH=$JAVA_HOME/bin:$PATH

It is still giving me an error (T-T)

When I type which java in I get:
/usr/bin/java

---

