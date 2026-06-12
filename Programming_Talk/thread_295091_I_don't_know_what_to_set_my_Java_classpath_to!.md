---
title: "I don't know what to set my Java classpath to?!"
date: 2006-11-07
forum: Programming Talk
---

### Post by lilalfyalien on 2006-11-07
Hi,

I've automatically installed Java via apt-get. It seems to of worked fine. However I can't execute the programs that I'm developing because I haven't set my classpath. I know how to set my classpath (sudo gedit /etc/environment) but how do I know where Java is actually installed?

I typed in "which java" and got this response:

/usr/bin/java

When I browse to this path though it's just a symbolic link to /usr/lib/j2sdk1.5-sun/bin/java. What do I exactly put in my classpath, java_home and path variables? I've tried:

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: /usr/lib/j2sdk1.5-sun/"
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"
JAVA_HOME="/usr/lib/j2sdk1.5-sun"
CLASSPATH="/usr/lib/j2sdk1.5-sun/lib/tools.jar:/usr/lib/j2sdk1.5-sun/jre/lib/rt.jar

```

but that doesn't work (I've restarted my system). 

If I put in java -classpath . Test it works, otherwise no!
Can someone tell me what to put please?

Thanks in advance,

Lilalfyalien

---

### Post by lilalfyalien on 2006-11-07
Please help- any suggestions are very welcome!

---

### Post by hod139 on 2006-11-07
You shouldn't have to set your classpath manually.  See this post: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)
and ignore the eclipse stuff (unless you want to install eclipse)

---

### Post by koala114 on 2006-11-08
You need Export your environment variables, the /etc/environment you listed just declare the JAVA_HOME, CLASSPATH, so it will have no effect.
For instance:
export JAVA_HOME="/usr/lib/j2sdk1.5-sun"
exprot CLASSPATH="/usr/lib/j2sdk1.5-sun/lib/tools.jar:/usr/lib/j2sdk1.5-sun/jre/lib/rt.jar

---

