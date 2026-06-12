---
title: "Running Commands over SSH"
date: 2009-10-19
forum: Programming Talk
---

### Post by Gwasanaethau on 2009-10-19
Hi all.

I've created a Java programme to synchronise files between my desktop and laptop computers. I also have a bash shell script harness that uses ssh to copy the Java programme to the remote computer and then execute it there. The Java programme compiles and runs perfectly on both systems, and the bash script copies the Java file across fine, but when I'm trying to execute it, the ssh command seems to mangle the non-ASCII characters in the file name.

To illustrate, my script does this:
```
#!/bin/bash
REMOTE="${1}"
ssh "${REMOTE}" mkdir -p ~/.céanna-temp
scp -Cpr ~/.céanna/list "${REMOTE}":~/.céanna-temp
scp -Cpr ~/Céanna.java "${REMOTE}":~
ssh "${REMOTE}" sed -i 's/[.]céanna/.céanna-temp/g' ~/Céanna.java
[COLOR="Red"]ssh "${REMOTE}" javac Céanna.java
ssh "${REMOTE}" java Céanna &[/COLOR]
java Céanna
```
The lines in red fail with the following errors:
```
**ssh "${REMOTE}" javac Céanna.java**

javac: file not found: C??anna.java
Usage: javac <options> <source files>
use -help for a list of possible options
```
```
**ssh "${REMOTE}" java Céanna**

Exception in thread "main" java.lang.NoClassDefFoundError: C??anna
Caused by: java.lang.ClassNotFoundException: C??anna
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: C&#65533;&#65533;anna. Program will exit.
```
I know the second one is caused partially by the **javac** command failing, but it is still mangling the non-ASCII character **é**. Any ideas on how to execute this over ssh?

---

### Post by Sub101 on 2009-10-19
Can you not change the class name to use standard characters? 

ie. replace the é with e

---

### Post by Gwasanaethau on 2009-10-19
> **Sub101 said:**
> Can you not change the class name to use standard characters? 

ie. replace the é with e
I could, but I would prefer to keep é if at all possible. Thanks for the suggestion, though! :)

EDIT: Hmm, logging in to an interactive ssh session and manually issuing those commands seems to work fine. Is there an issue with how ssh passes the sub-command on to the remote shell?

---

### Post by stylishpants on 2009-10-19
Seems to work for me.

```
bob@cob~$ touch /tmp/Céanna.java
 
bob@cob~$ ssh localhost file /tmp/Céanna.java
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
/tmp/Céanna.java: empty

bob@cob:~$

```

This is GNU bash, version 3.2.48(1)-release on jaunty.

Perhaps the problem comes in only when java is introduced?

---

### Post by Gwasanaethau on 2009-10-19
Yeah, now that you mention it, I think you're right. The sed and mkdir commands prior to these work fine with é (I checked the Java source to be sure). Hmm, it sure boggles the mind&#8230;

EDIT: The problem is definitely with Java (it doesn't like any of the non-ASCII characters in the source code either), but only when it's executed as part of the ssh command. Looks like I might not be able to automate this yet.

Thanks guys for your suggestions! :)

---

### Post by stylishpants on 2009-10-19
Also confirm that your scp command worked.

The scp command used in your script fails on my system, it appears that it tries to use the name of the home dir itself for the name of the new file created on the target system.

Appending a slash fixes the problem though:

```
bob@cob:~$ scp -Cpr ~/Céanna.java "${REMOTE}":~
scp: /home/bob:: Permission denied

bob@cob:~$ scp -Cpr ~/Céanna.java "${REMOTE}":~/
Céanna.java                             
```

---

### Post by Gwasanaethau on 2009-10-19
Hmm, that's interesting now&#8230;though the scp commands work fine for me without the trailing slash.

EDIT: I've tried using a bash script on the remote computer to call **javac** and then executing the script over ssh &#8211; same problem. That's really weird!

---

