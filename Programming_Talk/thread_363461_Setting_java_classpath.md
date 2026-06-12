---
title: "Setting java classpath"
date: 2007-02-16
forum: Programming Talk
---

### Post by Lukeg on 2007-02-16
I recently downloaded and installed Sun's JDK v5 and JRE and set Eclipse up to use suns JRE instead of GNU's.  This works nicely and Eclipse doesn't have a problem with it.  (I was directed in this installation by [the Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0")).

However, whenever I try to run java from the terminal, I get ```
Exception in thread "main" java.lang.NoClassDefFoundError:
```

I was able to determine that this means my CLASSPATH is not set (which was verified).

If I go into the preferences in Eclipse I can view the paths it uses, but I don't know which to set, or how.  Being able to run javac from the terminal isn't as important to me as running java.  Any help would be appreciated.

---

### Post by sdrubolo on 2007-02-17
Hi, have you set up the environment variables?
if not, you should go to /etc and you must modify the environment file. for example mine looks like ```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/    X11:/usr/games:/usr/lib/jdk1.6.0/bin"

```
I only added the last part, that is, :/usr/lib/jdk1.6.0/bin.
After that, restart you computer and then you should be able to run java from the shell.

---

### Post by Unterseeboot_234 on 2007-02-17
The IDE Eclipse and NetBeans work because they slam the project classpaths, library paths and anything else you added to your project whenever you hit the Run button. Then, if you want to work with any of the other tools such as ANT, Jython, Ruby on Rails, Groovy, JavaSound (JMF): those items might have a configuration problem to work in parallel with your IDE. The problem comes from those paths that got set up by the auto-installs from Synaptic for the Free Java package efforts, the 32-bit java plug-in for the web. I've learned to write my own shells for doing testing outside of the IDE -- much like a .bat file from the Windows world. This allows customization for different stand-alone projects.

I swear by this following link, posted in the Ubuntu forums, so we can all learn about the paths in java.

**[Custom Intall Java]("http://www.ubuntuforums.org/showthread.php?t=319138")**

---

### Post by runningwithscissors on 2007-02-17
It's been a while since I wrote anything in Java, but an:
```
$ export CLASSPATH=$PATH:.
```
at a bash prompt ought to take care of that.

You can even put the above line in your .profile so for your logins at least Java programs can be run from either of the diectories in PATH or the current directory.

---

### Post by rko618 on 2007-02-17
I don't know if what I did is the best solution but it works.  I added the following 2 lines to my ~/.bashrc

```
export JAVA_HOME='/usr/lib/jvm/java-6-sun'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
```

NOTE: I use Java6 so you'll have to change that for whatever you use.  It probably won't be java-5-sun so actually check in your /usr/lib/ directory to see what its called.

---

### Post by Lukeg on 2007-02-17
It turns out the problem wasn't the classpath at all.  I was trying to run ```
java myclass.class
``` instead of ```
java myclass
```Sorry for the trouble and thanks for the help.

---

### Post by oerd on 2008-02-04
Yeah, even the pros make these mistakes when using the console, blame eclipse ;)

as for the classpath, I tend to keep a personal collection of jars that gets updated from different sources (rsynced mainly) but a good idea woud be the following in your .bashrc (or in a separate setClasspath.sh script):

```

JARS=/usr/local/share/java
CLASSPATH=.

for j in `ls $JARS`; do
    export CLASSPATH=$CLASSPATH:$JARS/$j
done

```
Of course you should be setting the JARS variable to your java libraries (i.e. jars) folder.

[COLOR="Red"]N.B.[/COLOR]: setting your current directory to you CLASSPATH is considered a security risk by many people... still it is not the same as setting the . directory to your PATH which is really harmfull, as in Java one would have to jump through many loops to have a proper exploit.

Hope that was of any help.

---

