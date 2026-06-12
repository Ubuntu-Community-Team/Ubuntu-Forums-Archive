---
title: "Installing Eclipse Indigo on Ubuntu 10.04"
date: 2013-06-01
forum: Repositories &amp; Backports
---

### Post by wannabegeek on 2013-06-01
Good day....

I'm trying to install Eclipse Indigo on a laboratory system running Ubuntu 10.04. 

There must be a way to install it from a ppa or something...? I'm hoping there's not a bunch of dependencies that will need fixing, but I'd rather work those out
than upgrade a dedicated data acquisition machine. 

Cheers,
wbg

---

### Post by wannabegeek on 2013-06-01
maybe I didn't google enough...

[http://askubuntu.com/questions/26632/how-to-install-eclipse](http://askubuntu.com/questions/26632/how-to-install-eclipse)

any comments...?

---

### Post by T.J. on 2013-06-09
Check your JVM/Java version to make sure you don't have Java issues.

---

### Post by wannabegeek on 2013-06-09
HI there,

I did end up get Eclipse installed  by downloading the tar file and unpacking in /opt .

There's a couple of different ways to link a the executing shell script, 
I made a script in /usr/bin/eclipse
```

#!/bin/sh
export ECLIPSE_HOME="/opt/eclipse"
$ECLIPSE_HOME/eclipse $*

```

Now I get this error:
```

plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.v20120913-144807: cannot open shared object file: No such file or directory
Eclipse:
The Eclipse executable launcher was unable to locate its 
companion shared library.

```

I'm not in front of the computer now and I can't forward X11, but even when I am, I get the same error.

Cheers,
wbg


EDIT:
Changing directories into the /opt/eclipse and tried calling the eclipse bin.
Now, I can see a detail:

[/CODE]
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.v20120913-144807: cannot open shared object file:[COLOR=#ff0000] Permission Denied[/COLOR]
Eclipse:
The Eclipse executable launcher was unable to locate its 


[CODE]

---

### Post by wannabegeek on 2013-06-09
I tried again as su and got:

[/code]
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/opt/eclipse/jre/bin/java
[code]

I'll google the java issue...but don't understand why the permissions are messed up.

wbg

---

### Post by wannabegeek on 2013-06-09
Actually I could use some help with getting JRE installed...it's not as easy to maintain an old version of Ubuntu...

cheers,
wbg

---

### Post by T.J. on 2013-06-09
Well, let's tackle the problems one by one - self upgrading on an older OS is a process of elimination.  I'd be happy to help you as long as you have the patience for it. =)  

The "cannot open shared object file: No such file or directory" error occurs when a needed library file cannot be found on the default locations.  This does not mean that it is not there, but that it is not cached in the linker.  We'll worry about that AFTER you deal with the JRE problem.  Given your situation and the fact that you are installing a copy of Eclipse from upstream - that is Eclipse.org instead of Ubuntu - you probably want to download the appropriate JRE from Oracle and use that.

[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

---

### Post by wannabegeek on 2013-06-09
Thanks T.J., I'm very patient .... :)

I'm dl-ing the JDK for 64 bit.

I'm not sure where to put the Java files however... 

wbg

---

### Post by wannabegeek on 2013-06-10
Hi, so I was a little impatient and decided to try some "fixing" on y own...

I downloaded jdk from the link above, and put it into /opt where my eclipse is.
I have an eclipse start script that sets the environment variables:

    export ECLIPSE_HOME="/opt/eclipse"
    export JAVA_HOME="/opt/jdk1.7.0_21/bin/java"

I added /opt/jdk1.7.0_21/bin/ to me PATH variable.

Eclipse still complained that it couldn't find java in "/opt/eclipse/jre/bin/java"
I hacked out a "fix" by creating that directory and putting a symbolic link to the java above.

I think it might work...when trying to start eclipse via ssh with no X11 forwarding, I got a fail message and read the log...looks like 
it might have worked sans X11.

I'll be at the computer tomorrow afternoon to work on this...

Cheers,
wbg


UPDATE: Eclipse still does not load. But it does try...I have to use sudo eclipse, then nothing appears to happen and the process is stopped and won't easily die.

---

### Post by wannabegeek on 2013-06-10
OK....got eclipse to load up...the owner of the jdk directories and files were set to uucp.
Changing them to root makes the program run with sudo eclipse.

Now, to make it run without sudo....still unable to locate the permission issue.
wbg

---

### Post by T.J. on 2013-06-16
Sorry Wannabegeek.  Been busy this week.  

In my opinion, solely - if this is on your personal workstation, you should install with your permissions only,  in your home directory in a folder with your own permissions.  That way, when you run the update process in Eclipse you wont need to sudo, or when you update via your package manager, you won't have to worry about it damaging your installation of the JVM

---

### Post by wannabegeek on 2013-06-16
Those are good reasons...it is a shared computer but no one else but myself is going to use eclipse. 

I'll try that Monday...gonna practice some numpy this weekend too ....

cheers,
wbg

---

