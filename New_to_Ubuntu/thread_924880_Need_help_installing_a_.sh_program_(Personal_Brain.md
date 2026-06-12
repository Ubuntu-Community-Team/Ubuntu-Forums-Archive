---
title: "Need help installing a .sh program (Personal Brain)"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by diablo75 on 2008-09-20
I am trying to help someone install an application they downloaded to their computer.  I'm not certain, but it looks like there might be a missing dependency...  Here's the terminal output:

```
paul1111@Pau-Matt:~/Desktop$ ./PersonalBrain_unix_4_5_1_4.sh 
Starting Installer ...
Could not display the GUI. This application needs access to an X Server.
If you have access there is probably an X library missing.
*******************************************************************
You can also run this application in console mode without
access to an X server by passing the argument -c
*******************************************************************
An error occurred:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
Error log: /tmp/install4jError44337.log
paul1111@Pau-Matt:~/Desktop$ 
```

Any ideas?

---

### Post by Pro-reason on 2008-09-20
Do this:

```

sudo apt-get install **sun-java6-jre**

```

Or install it via Synaptic.

---

### Post by diablo75 on 2008-09-23
Here's what that produced:

```
paul1111@Pau-Matt:~$ sudo apt-get install sun-java6-jre
[sudo] password for paul1111: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
The following packages were automatically installed and are no longer required:
  libdns32 libxalan110 libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
paul1111@Pau-Matt:~$ ./PersonalBrain_unix_4_5_1_4.sh
bash: ./PersonalBrain_unix_4_5_1_4.sh: No such file or directory
paul1111@Pau-Matt:~$ cd desktop
bash: cd: desktop: No such file or directory
paul1111@Pau-Matt:~$ cd Desktop
paul1111@Pau-Matt:~/Desktop$ ./PersonalBrain_unix_4_5_1_4.sh
Starting Installer ...
Could not display the GUI. This application needs access to an X Server.
If you have access there is probably an X library missing.
*******************************************************************
You can also run this application in console mode without
access to an X server by passing the argument -c
*******************************************************************
An error occurred:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
Error log: /tmp/install4jError57526.log
paul1111@Pau-Matt:~/Desktop$ 
```

Not sure what to try next...  :(

Also, I should have categorized this thread under [COLOR="RoyalBlue"]Kubuntu[/COLOR].  I believe that's the distro he is attempting to install this on, and I don't know if that makes a difference...

---

### Post by Pro-reason on 2008-09-23
Hmm, it seems that you already have the latest Java from Sun Microsystems, and it's not sufficient.  It's absolutely insisting on the OpenJDK one.

Do this:

```

sudo apt-get instal **openjdk-6-jdk openjdk-6-jre**

```

If it still doesn't work after that, try following the suggestion it gives, and start the installer like this:

```

./PersonalBrain_unix_4_5_1_4.sh **-c**

```

This should be filed under &#8220;all variants&#8221;, because the desktop environment is probably not relevant to the problem.

---

### Post by blackest_knight on 2010-09-25
I just had a similar issue which I resolved by changing the version of java
I was using. The program required sunjava

---

