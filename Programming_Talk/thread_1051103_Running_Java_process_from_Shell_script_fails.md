---
title: "Running Java process from Shell script fails"
date: 2009-01-26
forum: Programming Talk
---

### Post by mdevine82 on 2009-01-26
So I have a self-extracting binary file that will be used for installation of something.  After it extract, it then launches an install shell script to configure a few things.  This shell script leverage's some ANT scripts.  However when the script gets run, I get the following error when it tries to execute those Ant scripts.

```
install.sh: 176: /home/username/modules/jre/bin/java: not found
```

The line in question looks like this(the CP variable is populated with the necessary JAR files for ANT)

```
/home/username/modules/jre/bin/java -classpath "${CP}" org.apache.tools.ant.Main -q -f install.xml
```

This install script has worked on CentOS, Fedora & OpenSuse so far with no problems.  Does anybody have any ideas?

Thanks,

Matt

---

### Post by sarath_it on 2009-01-26
$> echo $JAVA_HOME

if it points to /home/username/modules/jre, it is probably wrong.. 

To check where java is..
$> which java

---

### Post by mdevine82 on 2009-01-26
This is for an installation that bundles a specific version of Java.  Therefore I don't want to access the systems default version.  The java binaries do exist in the folder(/home/username/modules/jre/bin/).  

What I will try to do is export JAVA_HOME with the correct path from above.  After I do that, I will simply call java instead of attempting the absolute path to the binary.

Still confused as to why it was saying java not found, even though it exists in the directory.

Thanks again,

Matt

---

### Post by bettlebrox on 2009-01-26
> **mdevine82 said:**
> Still confused as to why it was saying java not found, even though it exists in the directory.


Perhaps it's not executable? What does the following command show:

ls -l /home/username/modules/jre/bin/java

And is username really your username?

The other thing it might be, is that there could be hidden characters in the script (it's happened to me in the past) that's causing the problem.

---

