---
title: "JDK error in Netbeans install"
date: 2007-04-25
forum: Programming Talk
---

### Post by Redscare on 2007-04-25
Please, I need a solution to this problem; I was installing Netbeans, and when the installer that I downloaded off the site was just starting with root priveleges, it searches for and scans JVM, then I get an error message: No Java Development Kit (JDK) was found on this system. I have installed and reinstalled the JDK multiple times from synaptic (v5 and 6). Please, I really need this program, can someone point me in the right direction?

---

### Post by ssodhi on 2007-04-26
Did you download from [Sun Microsystems]("http://java.sun.com/javase/downloads/netbeans.html")? Their installer shouldn't give you any troubles.

Try downloading just the SDK, and do something similar to me:
```

sanjay@sanjay-desktop:~$ cd Desktop
sanjay@sanjay-desktop:~/Desktop$ ls -l | grep jdk-6u1-linux-i586.bin
-rw-r--r-- 1 sanjay sanjay 62772481 2007-04-26 00:15 jdk-6u1-linux-i586.bin
sanjay@sanjay-desktop:~/Desktop$ chmod +x jdk-6u1-linux-i586.bin
sanjay@sanjay-desktop:~/Desktop$ ./jdk-6u1-linux-i586.bin
...
Done.
sanjay@sanjay-desktop:~/Desktop$ ls -l | grep jdk
drwxr-xr-x 10 sanjay sanjay     4096 2007-03-14 06:57 **jdk1.6.0_01**
-rwxr-xr-x  1 sanjay sanjay 62772481 2007-04-26 00:15 jdk-6u1-linux-i586.bin
sanjay@sanjay-desktop:~/Desktop$

```

The JDK is now installed at *~/Desktop/jdk1.6.0_01/*. You can find your Java binaries (the executable files that will physically run your Java program at  *~/Desktop/jdk1.6.0_01/bin/*.

Try and install netbeans separately and then point it to your SDK installation.

You may need to create an [url ="https://www.ccs.uky.edu/docs/cluster/env.html"]Environment Variable[/url] called **JAVA_HOME** pointing to *~/Desktop/jdk1.6.0_01/*.

-Sanjay Sodhi

---

### Post by rbprogrammer on 2007-04-26
i get the same error when i installed java not from the repositories, but from the sun website.   the way i got around it was when i enter in the command to install netbeans is just did something like this:
```
./netbeans.bin -is:javahome /path/to/jdk
```

try that..

---

### Post by Redscare on 2007-04-26
Thanks for the responses, but I found a solution:
Running the following command and selecting the correct version of java fixed all of my problems (note: I had already installed all java through synaptic):
```
sudo update-alternatives --config java
```

---

