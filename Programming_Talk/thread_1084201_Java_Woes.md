---
title: "Java Woes"
date: 2009-03-01
forum: Programming Talk
---

### Post by lvleph on 2009-03-01
Symptoms:
1. I developed an agent based model using java and REPAST J package. This works perfectly under windows, but when I start the program in Linux the GUI starts up and then if I click any part of the GUI it crashes. There is no error just a crash.

2. Matlab gives the following error:

```

Unable to initialize com.mathworks.mwswing.MJStartup
Fatal Error on startup: Failure loading desktop class
```

3. ```
sudo update-java-alternatives -s java-6-sun
No alternatives for firefox-3.0-javaplugin.so.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.
Using '/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide 'appletviewer'.
Using '/usr/lib/jvm/java-6-sun/bin/apt' to provide 'apt'.
Using '/usr/lib/jvm/java-6-sun/bin/extcheck' to provide 'extcheck'.
Using '/usr/lib/jvm/java-6-sun/bin/idlj' to provide 'idlj'.
Using '/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide 'jarsigner'.
Using '/usr/lib/jvm/java-6-sun/bin/jar' to provide 'jar'.
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.
Using '/usr/lib/jvm/java-6-sun/bin/javadoc' to provide 'javadoc'.
Using '/usr/lib/jvm/java-6-sun/bin/javah' to provide 'javah'.
Using '/usr/lib/jvm/java-6-sun/bin/javap' to provide 'javap'.
Using '/usr/lib/jvm/java-6-sun/bin/jconsole' to provide 'jconsole'.
Using '/usr/lib/jvm/java-6-sun/bin/jdb' to provide 'jdb'.
Using '/usr/lib/jvm/java-6-sun/bin/jhat' to provide 'jhat'.
Using '/usr/lib/jvm/java-6-sun/bin/jinfo' to provide 'jinfo'.
Using '/usr/lib/jvm/java-6-sun/bin/jmap' to provide 'jmap'.
Using '/usr/lib/jvm/java-6-sun/bin/jps' to provide 'jps'.
Using '/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide 'jrunscript'.
Using '/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide 'jsadebugd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstack' to provide 'jstack'.
Using '/usr/lib/jvm/java-6-sun/bin/jstatd' to provide 'jstatd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstat' to provide 'jstat'.
Using '/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide 'native2ascii'.
Using '/usr/lib/jvm/java-6-sun/bin/rmic' to provide 'rmic'.
Using '/usr/lib/jvm/java-6-sun/bin/schemagen' to provide 'schemagen'.
Using '/usr/lib/jvm/java-6-sun/bin/serialver' to provide 'serialver'.
Using '/usr/lib/jvm/java-6-sun/bin/wsgen' to provide 'wsgen'.
Using '/usr/lib/jvm/java-6-sun/bin/wsimport' to provide 'wsimport'.
Using '/usr/lib/jvm/java-6-sun/bin/xjc' to provide 'xjc'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so

```

4. I am sure there is some other errors that I have not come across yet, but they are there hiding just waiting to be found.

---

### Post by roshanjose on 2009-03-01
just check whether you haveinstalled the essential pakages relating to java...go through your synaptic manager

---

### Post by lvleph on 2009-03-01
I selected the sun-java6-jdk and sun-java6-jre. Not sure what else I was suppose to select. I even tried to reinstall the java packages, but that didn't help.

---

### Post by lvleph on 2009-03-08
Nothing?

---

### Post by lvleph on 2009-03-09
Eclipse finally through me an error.
[quote=eclipse]java: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.[/quote]

Now how to fix this?

---

### Post by drubin on 2009-03-09
Firstly which version of java are you running? 

from the command line,  java -version    and javac -version

---

### Post by lvleph on 2009-03-09
Yeah, I guess I should have put that up.
```
java -version && javac -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)
javac 1.6.0_10
```
I am about to try java-1.5.0-sun

EDIT:
running ```
sudo update-alternatives --config javac
``` and selecting 1.5.0 did not solve the problem.

---

### Post by lvleph on 2009-03-09
After a complete system fresh install with only my home folder remaining I still get the eclipse issue.

I really need to fix this issue.

---

### Post by CptPicard on 2009-03-09
Google Is Your Friend...

[http://nwn.bioware.com/forums/viewtopic.html?topic=631703&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=631703&forum=72)

They seem to have the same problem, see if those linked posts help.

---

### Post by lvleph on 2009-03-09
?txet sdrawkcab eht xif I od woh woN .depleh sknil esoht fo enoN

EDIT: Sorry for the backwards text. Not sure why it was typing backwards.
Anyway, I google before I ever post. None of those solutions helped.

---

### Post by mmix on 2009-03-11
Remove JDK 6, try JDK 7
[http://download.java.net/jdk7/binaries/](http://download.java.net/jdk7/binaries/)

---

### Post by lvleph on 2009-03-11
You know, I think I am using Java 7 on Windows. I will try this.

---

### Post by lvleph on 2009-03-11
I am feeling kind of retarded right now, but I can't figure out how to install java 7.

---

### Post by HotCupOfJava on 2009-03-11
> **lvleph said:**
> Eclipse finally through me an error.
 ```
Originally Posted by eclipse
java: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
```

Now how to fix this?

Interesting......Java is asserting that "XGETXCBuffer" is supposed to return a positive integer, but it isn't (hence the error). I don't suppose there is any way you can run down that method.....

A google of "xcb lock" quickly brought [this]("http://processing.org/discourse/yabb_beta/YaBB.cgi?board=Integrate;action=display;num=1210090458") up.

Now that doesn't mean I know how to solve the problem, though......;)

---

### Post by lvleph on 2009-03-11
So I tried this workaround and it didn't work for me. Essentially, what I have read was that they switched from XINERAMA to FAKEEXT (or XINERAMA is broken) so you have to find any instace of XINERAMA and replace it with FAKEEXT using the following.
```

sed -i 's/XINERAMA/FAKEEXT/g' libmawt.so
```
The thing is I have the following instances of that file
```

/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/headless/libmawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/motif21/libmawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/xawt/libmawt.so
/usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/amd64/headless/libmawt.so

```
Not sure if it should be changed in all of them or not. What I have seem was just in one of them, but I cannot remember which one, and of course
```
cat .bash_history | grep XINERAMA
``` gives me nothing. I know I used that sed command before, but...

---

### Post by HotCupOfJava on 2009-03-11
OK - don't get mad, but I followed cpt. picard's posted link and got to this:

> It seems that there's a problem using the nwn built-in SDL.

Please try the following:
1. make sure you have SDL installed (run software management and search for packages with string SDL in their name and install most of them, I'm really not sure what is required)
2. edit the file named "nwn" (the one you use to run the game) and find the line with "export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH" and delete "./lib" so that the line will look like this:
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
3. try to run the game again

Please also make sure you have your color depth in X set to 24, not 16. At first I had performance issues as suse set my color depth to 16 during the system installation.


It is related to a game, but the OP was getting the exact error message you posted. There were several reply posts from people for whom the fix worked.

Good luck.

---

### Post by HotCupOfJava on 2009-03-11
Forget my previous post - I took a harder look and the files they edited were game-specific, which is not what you're doing. Apparently this is a common problem.

---

### Post by lvleph on 2009-03-11
Just in case someone is waiting for a solution to this; the following was in the thread linked by HotCupOfJava
> **SamMartin]I think I've found a decent workaround for ubuntu now, but I have no idea what's actually wrong tbh. I've posted my workaround to the 'ubuntu installation thread', and posted all the remaining details here.
 
Fyi, Ubuntu install thread is here:
[url]http://processing.org/discourse/yabb_beta/YaBB.cgi?board=Integrate said:**
>  n=display;num=1210090496;start=15
 
It appears there are several commonly occuring java-related bugs associated with 'xcb locks', whatever they are! And likely aren't restricted to the official Sun runtime. Whilst looking for a solution to this I discovered that glxgears was dying on exit, as described in this bug report:
 
[https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/91077](https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/91077)
 
I fixed that problem by uninstalling the 'OpenJava' runtime.
 
Sun has an extensive thread on the subject here, fairly little of which I care to understand, but it was  informative all the same:  
 
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373)
 
Two other threads with useful workaround info on the problem are these:
 
"Java problems after upgrade"
[http://ubuntuforums.org/showthread.php?t=816018&highlight=xcb](http://ubuntuforums.org/showthread.php?t=816018&highlight=xcb)
 
and, "Cannot start matlab..."
[https://answers.launchpad.net/ubuntu/+question/26562](https://answers.launchpad.net/ubuntu/+question/26562)
 
Anyway, I believe the lock problem doesn't occur with the latest install of java-6-sun-1.6.0.06 but processing doesn't use this version. It ships with it's own runtime - 1.5 by the looks of things. This runtime does appear to do 'the bad thing' whatever that may be. Simply renaming the directory and creating a link to the ubuntu installed version works for me (/usr/lib/jvm/java-6-sun-1.6.0.06/).
 
Painful Wink
 
Cheers,
Sam 

---

### Post by HotCupOfJava on 2009-03-11
I see where one fix may be to build Java from source on your machine.

[Link]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373")

---

### Post by lvleph on 2009-03-11
If I could just figure out how to install Java 7. Then I think I would be ok.

---

### Post by lvleph on 2009-03-11
Okay, this is stupid. I noticed something when I tried running my program. It said something about java5. I was like wth. Anyway, I went into eclipse and changed the default jdk in eclipse to java6 and now everything works perfectly.

As far as maple not running, I had to use ./xmaple instead of just xmaple and that solved that issue.

Matlab, I think I just used 2008a instead of 2008b and that fixed that.

---

