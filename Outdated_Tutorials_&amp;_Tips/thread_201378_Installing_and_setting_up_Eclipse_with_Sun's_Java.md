---
title: "Installing and setting up Eclipse with Sun's Java"
date: 2006-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by hod139 on 2006-06-21
This howto explains how to install Eclipse and Sun's Java on Ubuntu 8.04 (Hardy Heron), and how to make Eclipse actually use Sun's Java solving the "Eclipse is horribly slow" problem caused by [bug 45347]("https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/45347").  

The entire install process consists simply of installing the following 2 meta packages: eclipse and sun-java6-jdk.  Note, you can optionally choose to use the openjdk-6-jdk package instead of Sun's package, which is the open-source jdk for ubuntu.
```

sudo apt-get install eclipse sun-java6-jdk

```This will install the required packages, however, Eclipse will run very slowly since it will be using GNU's java, not Sun's (or optionally openjdk).  To make Sun's java the default on the system, use the update-java-alternatives command:

```
 sudo update-java-alternatives -s java-6-sun
```Next, edit the JVM configuration file
```
sudo -b gedit /etc/jvm
``` and add the following to the top of the file
```
/usr/lib/jvm/java-6-sun
```There is a bug right now were Eclipse ignores Ubuntu's java-common settings and uses its own ([bug 45347]("https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/45347")). To work around the bug, you need to edit Eclipse's java_home file
```
sudo -b gedit /etc/eclipse/java_home
``` and add
```
/usr/lib/jvm/java-6-sun
``` to the top of the file.

Lastly, if you have lots of memory you may want to increase the heap size (warning:  If you make the heap size too large then parts of eclipse will continuously swap in and out.).
The settings can be altered by editing the eclipse.ini file. 
```

sudo -b gedit /usr/lib/eclipse/eclipse.ini
```The argument Xms refers to the minimum heap size and Xmx refers to the maximum heap size.
For more on tuning the Eclipse JVM heap size, you can refer to this [IBM article]("http://www7b.boulder.ibm.com/wsdd/library/techarticles/0204_searle/searle.html").

That's it.

**Edit 1:** Make mention of the /usr/share/eclipse/eclipse.ini file for setting heap size (thanks belial6)
** Edit 2:** Added javah to update-alternatives list (thanks anarhistu)
**Edit 3: **Clarified discussion on Eclipse bug (thanks anarhistu for pointing out this was unclear)
**Edit 4**: Use update-java-alternatives instead of update-alternatives. (thanks korny)
**Edit 5:** Updated java to version 6
**Edit 6:** Updated eclipse ini path for feisty users (thanks biTaZ and ksenos)

---

### Post by belial6 on 2006-06-26
For me Eclipse was very slow because the default heap size was relatively small. So I increased the heap.

Since I have 1 gig of ram I put max heap to 256 MB and default to 100MB.

Here is what I changed in **/usr/bin/eclipse** script (that's where my eclipse startup script is):
Before there weren't any vm arguments
VMARGS=""

Changed it to this
VMARGS="-Xms100m -Xmx256m"


And now eclipse is running much faster. Before I had problems working with just 5 editor windows open. Now I can easily open 20 of them 8)

---

### Post by anarhistu on 2006-06-26
Ok, I wanted to post this, but I will just complete your post:

> Lastly, Eclipse for some reason ignores Ubuntu's JVM configuration file and uses its own (bug?). You need to edit eclipes's java_home file
Code:

sudo -b gedit /etc/eclipse/java_home



Well, this is because of the Eclipse init script.Let's look at the script a little (/usr/bin/eclipse) :

```
.....
# If the user has specified a custom JAVA, we check it for validity.
# JAVA defines the virtual machine that Eclipse will use to launch itself.
if [ -n "${JAVA_HOME}" ]; then
    echo "using specified vm: ${JAVA_HOME}"

.....

# If the user has not set JAVA_HOME, cycle through our list of compatible VM's
# and pick the first one that exists.
if [ -z "${JAVA_HOME}" -a ! -n "${JAVACMD}" ]; then
    echo "searching for compatible vm..."
    javahomelist=`cat /etc/eclipse/java_home  | grep -v '^#' | grep -v '^$' | while read line ; do echo -n $line ; echo -n ":" ; done`
    OFS="$IFS"
    IFS=":"
    for JAVA_HOME in $javahomelist ; do
        echo -n "  testing ${JAVA_HOME}..."
....
```


Ok, so what we see here is this: Eclipse searches for the Environment variable named JAVA_HOME which you should have set.If it does not find it, it will go through the vm-s in its list  /etc/eclipse/java_home.

So, we try to see if the script works:

```

~$ export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun 
$ eclipse
using specified vm: /usr/lib/jvm/java-1.5.0-sun
........

```

That is, the script works just fine if you set the env variable.

For a permanent setting add it to ~/.bashrc or ~/.bash_profile or whatever you use for your profile (I think .bashrc is default) 

PS: At configuring the update alternatives.You can just do the old way and simbolic link applications in /usr/bin to the correct applications.Like : ```
ln -sf /usr/lib/jvm/java-1.5.0-sun/bin/java java
``` 

I don't know if it is correct or not, but this is how I did it.
And I also have a javah in my /usr/bin maybe you should list that too in your list.

Greets,
Matei

---

### Post by hod139 on 2006-06-27
[quote=belial6]For me Eclipse was very slow because the default heap size was relatively small. So I increased the heap.

Since I have 1 gig of ram I put max heap to 256 MB and default to 100MB.

Here is what I changed in **/usr/bin/eclipse** script (that's where my eclipse startup script is):
Before there weren't any vm arguments
VMARGS=""

Changed it to this
VMARGS="-Xms100m -Xmx256m"


And now eclipse is running much faster. Before I had problems working with just 5 editor windows open. Now I can easily open 20 of them 8)[/quote]

Correct me if I'm wrong, but doesn't eclipse read
```
/usr/share/eclipse/eclipse.ini
```
for JVM settings, and the default in dapper is 
```

-vmargs
-Xms40m
-Xmx256m

```

Thanks for the suggestion though of making people aware of this file.  I will edit my original post.

---

### Post by elemental666 on 2006-07-01
Just wanted to confirm this worked great in xubuntu dapper.  Eclipse opened much faster than ever, dunno if xfce or the Xms Xmx settings were the kickers, but I'm happy!

Thanks

---

### Post by korny on 2006-07-25
I have an example of a script that sets JAVA_HOME from the update-alternatives controlled path at [http://www.ubuntuforums.org/showthread.php?p=1296484#post1296484](http://www.ubuntuforums.org/showthread.php?p=1296484#post1296484)

- possibly putting this script in your .bashrc might be more reliable than manually setting JAVA_HOME?  Be warned, I haven't really played around with it much.

Also, generally it's better to call update-java-alternatives than update-alternatives - it calls update-alternatives for each of the java programs, not just java and javah.

When I've had a chance to test this properly, I might write it up as a howto...

---

### Post by hod139 on 2006-07-25
> **korny said:**
> I have an example of a script that sets JAVA_HOME from the update-alternatives controlled path at [http://www.ubuntuforums.org/showthread.php?p=1296484#post1296484](http://www.ubuntuforums.org/showthread.php?p=1296484#post1296484)

- possibly putting this script in your .bashrc might be more reliable than manually setting JAVA_HOME?  Be warned, I haven't really played around with it much.

Also, generally it's better to call update-java-alternatives than update-alternatives - it calls update-alternatives for each of the java programs, not just java and javah.

When I've had a chance to test this properly, I might write it up as a howto...
Thanks for the feedback.  I changed my post to use update-java-alternatives.  I'm not going to add your script to my main post since there already exists 
```
/usr/share/java-common/jvm-find.sh
```
and I'm trying to make a minimal set of changes with the smallest amount of side effects to deal with the known ubuntu bugs.  That way upgrades shouldn't be an issue.  Hopefully Ubuntu will have the java-common and java-alternatives working better by 6.10.

---

### Post by korny on 2006-07-25
fair enough - my only problem with that script is that it falls back to /etc/jvm, which is a parallel and alternative way of selecting JVMs to the update-alternatives way.
If people reliable edit /etc/jvm at the same time as running update-alternatives, this will work fine.  I just wish these things could be set in one place!

/etc/jvm is actually slightly nicer in some ways, as it allows a user to override the system-wide default - but it will only work with ubuntu or debian packaged apps; command-line calls to java, or manually installed apps, will typically look for JAVA_HOME, or rely on the "java" command in the path.

---

### Post by hod139 on 2006-07-26
> **korny said:**
>   I just wish these things could be set in one place!

I agree 100%

---

### Post by Pander on 2006-08-24
Very good howto! I have been waiting for this for a while.

It should be one big bug report for update-java-alternatives.

---

### Post by kpkeerthi on 2006-08-24
Thank you for this guide.

---

### Post by gwilma on 2006-08-27
I'd like to echo the thanks of others for this - it worked a treat, and I can now have a go with eclipse :D

---

### Post by zeroepoch on 2006-09-06
Thanks for the tip.  I use eclipse DAILY and this just saved me a crap load of time indexing C/C++ files.

---

### Post by jd_knight on 2006-09-14
I was facing problem while debugging my code, while eclipse used gcj. It looked like it was failing to connect to JVM in debugging mode. So the code just ran without hitting any breakpoint, and then the JVM threw an error. 

Now, after changing my default jre to sun-java, all is well :)

---

### Post by spur on 2006-09-14
"sudo update-java-alternatives -s java-1.5.0-sun" gives me a mesage that the  java-alternatives' does not exist !
I have read this thread and it had not helped!

---

### Post by hod139 on 2006-09-14
> **spur said:**
> "sudo update-java-alternatives -s java-1.5.0-sun" gives me a mesage that the  java-alternatives' does not exist !


How did you install Java, did you use the package available in Dapper, or did you install from Sun's website?  Are you running Dapper or an earlier version of Ubuntu?  What is the exact error message you get?

---

### Post by spur on 2006-09-15
Thanks hod139.:D 
I'm running dapper (Kubuntu 6.06) I tried both downloading and the packages with adept and got my browser working with java ok. I received an error message at last attempt telling me to set JAVA_HOME and I could not figure out how to do that.
It is a little immaterial now as I have downloaded JBuilder foundation and its working fine. Java web start did most of it for me. Then I set the vmmax myself as it was wrong and stopping Jbilder from starting.
Any way now I have my Java IDE and I'm Happy. =D> :biggrin:

---

### Post by blue_chili on 2006-09-15
Woohoo! It works. And it runs faster than with Tiger. Thanks :D

---

### Post by dxxvi on 2006-09-15
Could you tell me the reason why you don't remove GNU Java from your machine and use Sun's Java instead? By doing this way, there's no need to tell the machine which Java it should use. I always go to Application | Add/Remove ..., search for `java' and remove all java-related packages.

Why do you want to use Eclipse from Ubuntu, not Eclipse from eclipse.org? I'm pretty sure that the Ubuntu's Eclipse is not in version 3.2. Frankly, I haven't used any special feature in the version 3.2 yet, but when it comes to open source, I always want the latest :)

I haven't tried use to Sun's Java (which is downloaded from Sun website) in Ubuntu (I did it in Fedora Core 5 before) and it's great because I can always use the latest Java update (e.g. the latest update for Java 5 is 8, while it's only 6 with Ubuntu Java).

Now I'm using IntelliJ IDEA in Ubuntu (about $500 for a commercial license). I have Ubuntu (free) running in vmware player (free). Make a copy of that Ubuntu to save it. Install IntelliJ IDEA in Ubuntu and use it for 30 days, then get rid of this Ubuntu and install IDEA on the Ubuntu copy I saved before. That way, I can use IDEA for free for a quite long time. Is it legal?

---

### Post by spur on 2006-09-15
Doesn't sound legal to me as you are working around a trial period (seems like that is what you are doing) 
I have just installed net beans from sun and its working well. I installed the package deal and it fixed my eclipse as well. So why go to all that trouble to do something that could get you in deap?

---

### Post by hod139 on 2006-09-15
> **dxxvi said:**
> Could you tell me the reason why you don't remove GNU Java from your machine and use Sun's Java instead?

Why should I have to remove GNU Java to use Sun's?  Should I remove firefox to use opera, remove vim for emacs, etc... 

> 
By doing this way, there's no need to tell the machine which Java it should use. I always go to Application | Add/Remove ..., search for `java' and remove all java-related packages.
 Again, why should I have to remove one thing to use another?  Also, what if another package I want to use depends on some gnu java package?  And this doesn't solve the problem of telling the machine which Java it should use (unless you are using a repository version of Java that is).  You still have to manually set up classpaths and library paths.

> Why do you want to use Eclipse from Ubuntu, not Eclipse from eclipse.org? I'm pretty sure that the Ubuntu's Eclipse is not in version 3.2. Frankly, I haven't used any special feature in the version 3.2 yet, but when it comes to open source, I always want the latest :)
 This comes down to personal taste. I too used to always want to run bleading edge, but now that I'm in grad school I don't have the time to do this anymore.  Now I just want everything to work with minimal setup, so I can be most productive.  Ubuntu developers spend lots of time managing the packages and handling dependecies, security fixes, etc so I don't have to.  If that means using a slightly out of date package, then so be it.

> 
I haven't tried use to Sun's Java (which is downloaded from Sun website) in Ubuntu (I did it in Fedora Core 5 before) and it's great because I can always use the latest Java update (e.g. the latest update for Java 5 is 8, while it's only 6 with Ubuntu Java).

Now I'm using IntelliJ IDEA in Ubuntu (about $500 for a commercial license). I have Ubuntu (free) running in vmware player (free). Make a copy of that Ubuntu to save it. Install IntelliJ IDEA in Ubuntu and use it for 30 days, then get rid of this Ubuntu and install IDEA on the Ubuntu copy I saved before. That way, I can use IDEA for free for a quite long time. Is it legal? I'm not sure on the legality, but it is definitely not the intentions of IntelliJ.

The point of this howto is to help people install and setup the repo versions of Sun's java and Eclipse.  I don't want to see this howto get locked or thrown in the backyard for violating any terms, so if you wish to keep talking about this feel free to private message me, but please leave future comments relevant to the initial discussion.  Thanks.

---

### Post by korny on 2006-09-16
> **dxxvi said:**
> Could you tell me the reason why you don't remove GNU Java from your machine and use Sun's Java instead? By doing this way, there's no need to tell the machine which Java it should use. I always go to Application | Add/Remove ..., search for `java' and remove all java-related packages.


The trouble is, if you remove GNU Java you break *any* package that depends on it.  Sure, for things like Eclipse I want to install it myself and get the latest version (and also make things like plugin management much simpler) - but I don't want to eliminate the option of installing *anything* from the Ubuntu apt repositories that needs java.  It's far less effort to install most things from synaptic - or at least it would be, if not for the confusing different ways different apps look for which Java to use.

> **dxxvi said:**
> I haven't tried use to Sun's Java (which is downloaded from Sun website) in Ubuntu (I did it in Fedora Core 5 before) and it's great because I can always use the latest Java update (e.g. the latest update for Java 5 is 8, while it's only 6 with Ubuntu Java).


I prefer in this case to install the ubuntu-checked version of Java as the default - this gives me a greater chance stability for ubuntu-repository apps; there is no guarantee that Sun haven't changed something between version 6 and 8 that breaks a third part app.  If you stick with the ubuntu version, at least you have a chance that someone else has checked the compatibility for you.

And then I install a later version (*if* I need the latest features) as well, and use it for cases where I need the latest and greatest.  (For example, I'm running Java 6 beta, with the latest JEdit, so I get lcd antialiased fonts :)

> **dxxvi said:**
> 
Now I'm using IntelliJ IDEA in Ubuntu (about $500 for a commercial license). I have Ubuntu (free) running in vmware player (free). Make a copy of that Ubuntu to save it. Install IntelliJ IDEA in Ubuntu and use it for 30 days, then get rid of this Ubuntu and install IDEA on the Ubuntu copy I saved before. That way, I can use IDEA for free for a quite long time. Is it legal?

sorry, no, that's almost certainly illegal.  I'd be willing to bet the IntelliJ licences specifically say something like "one trial license per user".  Why not stick to Eclipse?  It's at least 90% as good as IntelliJ, better in some areas I hear, and completely free and legal.

- Korny

---

### Post by Cable on 2006-09-16
I can *not* get this to work for the life of me.  I did
```

sudo update-java-alternatives -s java-1.5.0-sun

```
and the terminal output is
```

Using `/usr/lib/jvm/java-1.5.0-sun/bin/appletviewer' to provide `appletviewer'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/apt' to provide `apt'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/extcheck' to provide `extcheck'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter' to provide `HtmlConverter'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/idlj' to provide `idlj'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jarsigner' to provide `jarsigner'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jar' to provide `jar'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javac' to provide `javac'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javadoc' to provide `javadoc'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javah' to provide `javah'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javap' to provide `javap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/java-rmi.cgi' to provide `java-rmi.cgi'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jconsole' to provide `jconsole'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jdb' to provide `jdb'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jinfo' to provide `jinfo'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jmap' to provide `jmap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jps' to provide `jps'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd' to provide `jsadebugd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstack' to provide `jstack'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstatd' to provide `jstatd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstat' to provide `jstat'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/native2ascii' to provide `native2ascii'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/rmic' to provide `rmic'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/serialver' to provide `serialver'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/ControlPanel' to provide `ControlPanel'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java_vm' to provide `java_vm'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/javaws' to provide `javaws'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `firefox-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-snapshot-javaplugin.so'.

```
Which looks okay to me.  Here is my JVM file.
```

# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr

```
Here is my javahome file.
```

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

```
I believe I've done everything stated in this howto, and Eclipse is still not using Sun JDK.  Specifically, it's not recognizing the Scanner class.  Help please??

---

### Post by hod139 on 2006-09-16
> **Cable said:**
> 
I believe I've done everything stated in this howto, and Eclipse is still not using Sun JDK.  Specifically, it's not recognizing the Scanner class.  Help please??

From your output it looks like you did everything correctly, Sun's java 5 is is installed, it is the default, and eclipse is configured to launch using Sun's JVM.

To me, it sounds like your problem is either:
 1.  Eclipse doesn't have Sun's JDK in its list of installed JREs
 2. Your Eclipse compliance level is set to 1.4.

To check 1, start eclpse, go to Window->Preferences->Installed JREs
and verify Sun's JRE is installed.  If not, click the add button and add it.

For 2, go to Window->Preferences->Compiler, and make sure compliance level is set to 5.0, not 1.4.  In addition, each project can overrride these default settings, so veryfy the compliance level in the project as well:  Right-click the project->Properties->Java Compliance

I hope this helps.  Also, can you tell me what was wrong so I can update the howto accordingly.

---

### Post by dxxvi on 2006-09-16
> **hod139 said:**
> Why should I have to remove GNU Java to use Sun's?  Should I remove firefox to use opera, remove vim for emacs, etc... 

> **hod139 said:**
>  ... but now that I'm in grad school I don't have the time to do this anymore Aha, you're in grad school now :) Congratulations! I hope that you'll continue with the Ph.D (the thing I cannot do). I'm glad that I finished my grad school nearly 2 years ago, have been working for about 1 and a half years since then and not in the don't-have-the-time-to-do-this-anymore situation :)

I know bleeding-edge technologies are painful but I love them, I want to learn them so that when they're mature and any of our clients wants to use it, we're ready.

And to those who choosing GNU Java over Sun Java, could you guys give me some advices (if you're been-there-done-that) in these situations (I haven't tried any of them, so if you did, I really want to hear your opinions):

- will GNU Java work with J2EE (including JSF and JPA), Struts, Spring, Acegi Security, Hibernate, JUnit, TestNG, XDoclet (those are the things I'm using or intend to use in the near future)?

And to those using Eclipse (I should ask this question in Eclipse forum), I am in this problem:

- I have a build.xml file in which I use a property, for example named lib.dir. This property is declared in some other xml files (I mean more than 1 xml file, for example it is declared in windows.properties.xml and unix.properties.xml files). In build.xml, I check to see if the OS is windows or Unix. If windows, I load the windows.properties.xml file, and load the unix.properties.xml file otherwise. Suppose that there are only 2 OS's windows & unix. In either way, lib.dir is declared. In eclipse, when I tell it that build.xml is the Ant build file, Eclipse tells me that lib.dir is used in build.xml but isn't declared, but it works fine with IntelliJ IDEA.

That's not the reason I choose IDEA. I like free software so I used Eclipse before, but my company is having IDEA and all existing projects use the kind of build.xml file I mentioned above. Another reason is that Eclipse uses SWT, not Swing, and I heard that SWT doesn't work well with MacOS (I haven't tried it although I used to have an iBook G4 but I sold it away when I heard that Apple might uses Intel chips).

---

### Post by duality on 2006-09-21
I had to export java to an enviroment variable, and then run eclipse with sudo, and choose java 5.0 when making the project.
Then it worked

---

### Post by FLEO on 2006-10-25
I agree with you guys.

I changed Eclipse's JRE for Sun's Java and it's mutch faster. Like in windows.

Tks,

FLEO

---

### Post by sha_man on 2006-11-29
my eclipse running latest Java is still running SLOWLY and takes a LOT of CPU :mad: 

it takes seconds for auto-completion, and needs 100% cpu for almost all tasks...

What can I do? Is this normal? I have amd643200+ and 1024mb ram... this not happen...

---

### Post by ufalcon on 2006-12-11
I had the same symptoms (ridiculously slow auto-complete was the worst >_<) - on an AMD64 Ubuntu Edgy 64 system.  Just make sure you follow every step of the tutorial...


Honestly, how painful does this have to be???  Maybe now that Sun is open-sourcing (I don't know much about this though) Java I won't ever have to go through 10 steps just to stop using some crap JVM like gcj.

Great tutorial though - thanks!

---

### Post by hod139 on 2006-12-11
> **ufalcon said:**
> I had the same symptoms (ridiculously slow auto-complete was the worst >_<) - on an AMD64 Ubuntu Edgy 64 system.  Just make sure you follow every step of the tutorial...


Honestly, how painful does this have to be???  Maybe now that Sun is open-sourcing (I don't know much about this though) Java I won't ever have to go through 10 steps just to stop using some crap JVM like gcj.

Great tutorial though - thanks!
I'm glad someone on edgy and with and AMD64 machine was able to test this.  Thanks for replying.

I hope with sun open-sourcing Java this howto becomes obsolete, it is far too painful right now for no good reason.

Thanks for the compliment!

---

### Post by alinuxfan on 2007-02-12
I am getting an error and I can't even start eclipse.  I searched the web and I couldn't find much.
I guess not many people are having the problem or not many people are running 64bit OS's to program

Any ideas?

Thanks

Edit: I am using eclipse from the repo and sun java

```
!SESSION 2007-02-12 18:36:18.651 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2007-02-12 18:36:21.616
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-12 18:36:21.623
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-12 18:36:21.624
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-12 18:36:21.624
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-02-12 18:36:21.907
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: memmove
	at org.eclipse.swt.internal.gtk.OS.memmove(Native Method)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.IDEApplication.createDisplay(IDEApplication.java:122)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:75)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
```

---

### Post by Bruce Leeds on 2007-02-27
Hi,
I am new here and hope to find some help regarding to the installation of the java-sun-package.

I did everything that was written in the manual in the first post. But now when I open Eclipse this error message is arising in a window:

```
JVM terminated. Exit code=1
/usr/lib/jvm/java-1.5.0-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/share/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata bd8000
-install /usr/share/eclipse
-vm /usr/lib/jvm/java-1.5.0-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/share/eclipse/startup.jar

```

When I write /usr/lib/jvm/java-1.5.0-sun as a comment in /etc/eclipse/java_home then Eclipse starts, therefore obviously Eclipse is not able to read that file correct.

In the third post in this thread anarhistu mentions the file /usr/bin/eclipse.
I don't understand what he means with the following:

> 
Ok, so what we see here is this: Eclipse searches for the Environment variable named JAVA_HOME which you should have set.If it does not find it, it will go through the vm-s in its list /etc/eclipse/java_home.
 
 So, we try to see if the script works:
 
 
Code:
~$ export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun 
$ eclipse
using specified vm: /usr/lib/jvm/java-1.5.0-sun
........
That is, the script works just fine if you set the env variable.
 
 For a permanent setting add it to ~/.bashrc or ~/.bash_profile or whatever you use for your profile (I think .bashrc is default) 
 
 PS: At configuring the update alternatives.You can just do the old way and simbolic link applications in /usr/bin to the correct applications.Like : 
Code:
ln -sf /usr/lib/jvm/java-1.5.0-sun/bin/java java
I don't know if it is correct or not, but this is how I did it.
 And I also have a javah in my /usr/bin maybe you should list that too in your list.


1) What exactly shall I do? Shall I set a bash-script somewhere? Which? Where?
2) What can I do to get my Eclipse running with the sun-Java?
3) How can I see whether it worked in the end? Is there something where I can see that in Eclipse?

Greetings
Bruce

I am running
Kubuntu 6.06
KDE 3.5.5
Machine: i686

---

### Post by hod139 on 2007-02-27
The fourth line of your error message makes me think that you have not set up eclipse correctly since it is trying to use gcj.  

What's scary to me is that you are getting an error if you put 
```

/usr/lib/jvm/java-1.5.0-sun
``` at the top of ```

/etc/eclipse/java_home
```

Maybe something went wrong with the java install, does the directory
```

/usr/lib/jvm/java-1.5.0-sun
```
exist on your machine?

---

### Post by Bruce Leeds on 2007-02-27
Yes it exists.
My file is:

```

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

```

Any idea?

---

### Post by Bruce Leeds on 2007-02-28
I got it!

I needed to install as well the package:
"sun-java5-jdk"

Either you forgot to write that in your tutorial and should ad it,
or in my case the installation of
"sun-java5-bin"
didn't install
"sun-java5-jdk"
too and it should have done it.

For all German speaker there outside:
[http://wiki.ubuntuusers.de/Java](http://wiki.ubuntuusers.de/Java)
helped me.
It is an excellent wiki if you allow me to advertise a bit - it is German anyway.
Ah, I just saw, it's the same "brand" as ubuntuforums - only the German part of it, so I'm advertising this forum anyway. ;-)

There I read that there is a Java 6.
Can I download and install it the same way as I did with Java 5?
Would you recommend it?

I wasn't able to find it with Adept.
Do I have to set free some repositories?

I know, that I can see which JRE is installed under Windows--Preferences--Java--Installed JRE.
But where can I see which jdk-Java is used by Eclipse?

Greetings
Bruce

---

### Post by hod139 on 2007-02-28
> **Bruce Leeds said:**
> I got it!

I needed to install as well the package:
"sun-java5-jdk"

Either you forgot to write that in your tutorial and should ad it

The second line of my first post says: "the entire install process consists of installing the following 2 meta packages: eclipse **sun-java5-jdk**" (emphasis added).

> 
There I read that there is a Java 6.
Can I download and install it the same way as I did with Java 5?
Would you recommend it?

I wasn't able to find it with Adept.
Do I have to set free some repositories?
You can install it the same way, changing java 5 to 6 where appropriate.  The package name is sun-java6-jdk and is available in the backports repository.  As for recommending it, sure go ahead.  I may even update the first post.

> 
I know, that I can see which JRE is installed under Windows--Preferences--Java--Installed JRE.
But where can I see which jdk-Java is used by Eclipse?
If you start eclipse from the command line it should tell you.  Alternatively, edit 
```

/etc/eclipse/java_home

```That file is the search order eclipse uses to find JREs.

---

### Post by geovino on 2007-03-09
How do install the java file without installing Eclipse? I don't want the program, but because I install it once I keep getting error messages about having to install this java file. I just want to install it but I have gotten any instructions. How do I install a    	j2sdk-1_4_2_13-linux-i586.bin ?

---

### Post by hod139 on 2007-03-09
> **geovino said:**
> How do I install a        j2sdk-1_4_2_13-linux-i586.bin ?
The point of this howto is how to install Java (and Eclipse) using the repositories, not using Sun's website.  To my knowledge, I do not know how to install such an old version of java from the repositories.  I would suggest you don't install such an old version at all.  Add the multiverse repository and install either sun-java5-jdk or sun-java6-jdk.  If you really want to install from Sun's website, see [this guide]("http://phossal.com/thread?view=702216931").

---

### Post by andypaxo on 2007-03-09
Thanks so much for the advice!
It would have taken hours to figure out why Eclipse wasn't doing what it should, but this sorted it out.

---

### Post by Nikron on 2007-03-30
I'd suggest to Fiesty Fawn users that they download eclipse from eclipse.org, because eclipse from the repos, while up to date makes you install 200 megs worth of GCJ

---

### Post by AndyMan1 on 2007-04-29
Many Kudos and internet cookies. After MUCH frustration, this is the thing that got me all fixed up!

---

### Post by biTaZ on 2007-05-24
This is a saver,

Man, I'm working on Eclipse for my Job on both Windows and Linux boxes and I couldn't understand why the Ubuntu version was lagging behind Gentoo and Windows!

Big Thanks for the howto.
If you'll ask me, this eclipse *feature* forcing gcj is purely a bug. The version on my Gentoo box DOES take the global setting into account.

Also, the location of the eclipse.ini was different on my system:
```
$ locate eclipse.ini
/usr/lib/eclipse/eclipse.ini
```

---

### Post by mintcoffee on 2007-05-24
> **AndyMan1 said:**
> Many Kudos and internet cookies. After MUCH frustration, this is the thing that got me all fixed up!

Bah, Keep your *cookies* to yourself!!! We get enough of them surfing the web :grin:

---

### Post by fintan.mcgee on 2007-05-26
Thank You. I was just about to ditch eclipse (with CDT) as a C++ IDE as many features had serious issues (particularly the content assist and C++ Indexer) . This looks like it has sorted it out.

---

### Post by ksenos on 2007-05-27
Thanks for this guide. It seems it really worked. I have to say that the location of eclipse.ini file was also different on my system.

```
/usr/lib/eclipse/eclipse.ini
```

Does anyone know if there is going to be a chance to get eclipse without the gcj dependency?

---

### Post by hod139 on 2007-05-27
> **ksenos said:**
> Thanks for this guide. It seems it really worked. I have to say that the location of eclipse.ini file was also different on my system.
```
/usr/lib/eclipse/eclipse.ini
```
Thanks, I guess the location in was changed in feisty.  I will update the guide to include this new location.

> 
Does anyone know if there is going to be a chance to get eclipse without the gcj dependency?You can follow this [bug]("https://bugs.launchpad.net/ubuntu/+source/libcommons-dbcp-java/+bug/81876").  Hopefully they will have it straightened out by the next release.

---

### Post by nabla on 2007-05-28
why not just get eclipse from eclipse.org, extract to /opt/  , make a menu entry to launch it and it's done. and no gcj dependency crap.

---

### Post by hod139 on 2007-05-28
> **nabla said:**
> why not just get eclipse from eclipse.org, extract to /opt/  , make a menu entry to launch it and it's done. and no gcj dependency crap.
That is another approach, and one that you are free to use.  However, the point of this tutorial is how to use the repository version of eclipse, since many people prefer to use the repository instead of installing from the developers website.

---

### Post by jdunn on 2007-05-29
I'm a java newbie and I'm having alot of trouble with Eclipse.  I downloaded Eclipse from the repositories and I followed your guide.  My "Hello World" program has no syntax errors but when I try to compile, I get this in the console:

Activation.main: warning: sun.rmi.activation.execPolicy system
property unspecified and no ExecPermissions/ExecOptionPermissions
granted; subsequent activation attempts may fail due to unsuccessful
ExecPermission/ExecOptionPermission permission checks.  For
documentation on how to configure rmid security, refer to:

[http://java.sun.com/j2se/1.4/docs/tooldocs/solaris/rmid.html](http://java.sun.com/j2se/1.4/docs/tooldocs/solaris/rmid.html)
[http://java.sun.com/j2se/1.4/docs/tooldocs/win32/rmid.html](http://java.sun.com/j2se/1.4/docs/tooldocs/win32/rmid.html)


Your guide mentions nothing about setting file permissions.  I don't want to run this as root and I have no idea where to set permissions.

**Update**
NM.  I got it working somehow.  I'm not sure what I did to fix it.  :KS

---

### Post by jdunn on 2007-05-31
Okay.  Now that I have Eclipse working, I noticed another problem:  I can't print from Eclipse but I can print from any other Linux Applications including Firefox, OpenOffice, etc.  In Eclipse, File->Print is "greyed out" and I need to print out source code and results for my course.  My printing is done on a remote printer attached to my Windows XP computer via SAMBA.

---

### Post by korny on 2007-05-31
Eclipse has only very recently started to support printing on Linux - it wasn't supported in Eclipse 3.2.2 which is the version available in Feisty.  (Actually when I started this post I assumed it wasn't supported at all, glad to see it is *finally* available in 3.3 ...)

So if you want printing, either use an external program or get Eclipse 3.3 M1 or later.
See [http://www.eclipse.org/swt/faq.php#printOnGTK](http://www.eclipse.org/swt/faq.php#printOnGTK)

Maybe a quick solution would be to get a different Java editor just for printing - try JEdit, it's a nice general-purpose editor written in Java, it should print code quite well.  [http://jedit.org](http://jedit.org)

---

### Post by jdunn on 2007-05-31
Thanks Korny.  That's good to know.  I'm guessing 3.22 is the current stable version.  If I go to the download section of the eclipse web sight, it says the current version for Linux is 3.22

Version 3.3 is a Release Candidate.  I'll wait until its official.

---

### Post by keneida on 2007-06-14
somehow it is all kind of wrong.
I found out that /usr/bin/eclipse has hardcoded javavm options to use gcj
```

-vmargs -Djava.library.path=/usr/lib/jni \
            -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db \
            -Dgnu.gcj.runtime.VMClassLoader.library_control=never \
            -Dosgi.locking=none ${VMARGS}
```
so i commented it out. From the debug it looks that it finally uses proper sun jvm.
However when i run a java program i get:
```

Exception in thread "main" java.lang.NoClassDefFoundError: .....
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: info.fingo.asist.transis.jms.Sender not found in gnu.gcj.runtime.SystemClassLoader{......}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

```

i do not know what to think about it

---

### Post by afasias on 2007-06-14
I am having a very hard time using eclipse on ubuntu feisty.
I have installed eclipse and sun's jdk on two different computers.
On the first computer (the one I use at work) I have installed both eclipse and sun's jdk 1.6 simply by extracting all files in folders and call it from there.
On the other computer (the one I use at home) I have installed both eclipse and sun's jdk 1.6 using the ubuntu packages (eclipse and java-6-sun).
I took care of making eclipse using the sun's jdk instead of gcj. I can say that eclipse works pretty fast most of the time, but there are some other issues.
code assistance is so slow that makes it unusable. The first time the code assistant is enabled it takes 5-6 minutes (it's not a typo: minutes) for the assistance window to appear. the eclipse windows gets grayed (not responding). after that first time, code assistance comes up pretty fast (like 1 sec or less). While eclipse is not responding, I see high levels of cpu usage by java and no disc activity.
Also, another delay occurs when trying to select a suggestion. if I have an error in the code, and red mark appears on the left, i click on it to see what eclipse suggests me to do. instantly eclipse is getting in the not-responding-mode and I have to wait for about 2 mins to get the suggestions window. And it does not only do this on the first time, it does this *every* time I click on the red mark.
Any logical explanation of why all these problems occur? Any solutions? Please help..

---

### Post by tarek on 2007-06-18
Thanks! Works just fine on Feisty.

---

### Post by questpro on 2007-08-05
working fine,

Thank you.

---

### Post by rvdavid on 2007-08-06
Works flawlessly on Xubuntu Gutsy Gibbon
Eclipse 3.2.2 (from repository)
Java 6 Sun

I was getting choppy performance when I first installed. The culprit was eclipse still using GCJ even after I had installed and updated alternatives to use sun java 6. 

I had to update java_home in /usr/lib/eclipse/ for it to be effectively using sun suns jvm.



Regards,

---

### Post by labreche on 2007-08-14
hi,
i run into problem while using ubunt eclipse package under feisty . I've followed the thread(installed java6  from backport , ...) , but eclipse does not want to start, hanging up with message saying me to read the log bellow :

```



!SESSION 2007-08-14 19:11:04.580 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=fr_FR
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-08-14 19:11:05.725
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-14 19:11:05.725
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-14 19:11:05.725
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-08-14 19:11:05.726
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-08-14 19:11:05.744
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (106).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2389)
	at java.lang.Class.getConstructor0(Class.java:2699)
	at java.lang.Class.newInstance0(Class.java:326)
	at java.lang.Class.newInstance(Class.java:308)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
	... 62 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2389)
	at java.lang.Class.getConstructor0(Class.java:2699)
	at java.lang.Class.newInstance0(Class.java:326)
	at java.lang.Class.newInstance(Class.java:308)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-08-14 19:11:05.758
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (91).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	... 32 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-08-14 19:11:05.764
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.throwException(RegistryStrategyOSGI.java:165)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:149)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)


```

 i don't know where is the first error. 
Any help would be  apprecied

---

### Post by Lazarenko on 2007-09-06
Great! Thank you very much for this FAQ! It is extremely useful!!

---

### Post by Freaky#Funga on 2007-11-26
I've followed all instructions on 1st  page, but my eclipse still says that it cannot connect to VM when debugging. When I try to download from eclipse's pages, this version says that it cannot comunicate with VM socket. I'm totaly desperate about this, because I really need to debug. ANY suggestions are most welcomed!

This is what is written in my output when I run "eclipse -deubug" and grep for "java"
```

  testing /usr/lib/jvm/java-6-sun...found
Start VM: /usr/lib/jvm/java-6-sun/bin/java
-Djava.library.path=/usr/lib/jni
-vm /usr/lib/jvm/java-6-sun/bin/java
-Djava.library.path=/usr/lib/jni

```

---

### Post by hod139 on 2007-11-26
I'm not sure what you are trying to do, but from the man page
> 
-debug [optionsFile]
              Puts the platform in debug mode and loads the debug options from the file at the given location, if specified.  This  file  indicates which debug points are available for a plug-in and whether or not they are enabled. If a file location is  not  given,  the platform  looks  in  the directory that eclipse was started from for a file called ".options". Both URLs and  file  system  paths are allowed as file locations.

       Note: On Debian, eclipse expects that the following arguments is a path to a option file. You are not allowed to omit this file!

What exactly are you trying to do?  Does eclipse work normally, that is did it install properly?  If so, then maybe you should consider starting a new thread about this problem since this guide is mainly for installation of eclipse, and I don't really know how to help you more on this problem.

---

### Post by Freaky#Funga on 2007-11-28
> **hod139 said:**
> I'm not sure what you are trying to do, but from the man page

What exactly are you trying to do?  Does eclipse work normally, that is did it install properly?  If so, then maybe you should consider starting a new thread about this problem since this guide is mainly for installation of eclipse, and I don't really know how to help you more on this problem.

I've tried to get most verbose output by using -debug option in order to find where is problem with my Java VM. I'm not able to run debug in Eclipse.

What I mean is that the -debug option and debuging in eclipse are 2 different things.


I've already solved my problem this way:
in Eclipse: Window -> Preferences -> Java -> Installed JREs and Search in my /usr/bin and then selecting "Java-6-sun" :KS

---

### Post by hod139 on 2007-11-28
Thanks for posting your solution!

---

### Post by whitespy9 on 2007-11-28
I checked my install so many times. This step was key for me...
Why Eclipse defaults to the crappiest version of jre to compile is beyond me....
Thank you for the post!

For 2, go to Window->Preferences->Compiler, and make sure compliance level is set to 5.0, not 1.4. In addition, each project can overrride these default settings, so veryfy the compliance level in the project as well: Right-click the project->Properties->Java Compliance

---

### Post by frajer762 on 2007-12-26
thx, it works for me!

---

### Post by agibby5 on 2007-12-27
I followed the instructions in the first post.  However, I'm still having some "issues"

When I click the Eclipse shortcut from the menu, I get the following error: "The custom VM you have chosen is not a valid executable."

However, when I launch Eclipse from the command line, it launches successfully:
```

andy@c2d6400:~$ eclipse
using specified vm: /usr/lib/jvm/java-6-sun
```

How can I see what's being executed when I click the menu link?  I have a feeling that its not using the proper JVM...

Thanks in advance.

---

### Post by Shroin on 2008-01-09
Thanks a lot for the guide. It provided me with all of the information I was looking for. I'm a new to linux (just replaced vista with it after taking my first quarter of comp classes at college) and I had absolutely no trouble following the instructions.

Cheers,

Shroin

---

### Post by MockY on 2008-01-14
Great How-To.
It solved the issues I had.

Thanks.

---

### Post by Phkillah on 2008-05-17
Espectacular :)

---

### Post by InfoSec812 on 2008-09-09
> **hod139 said:**
> This howto explains how to install Eclipse and Sun's Java on Ubuntu 6.06 LTS (Dapper Drake), and how to make Eclipse actually use Sun's Java solving the "Eclipse is horribly slow" problem.  This tutorial should work fine for more recent versions of Ubuntu.
*snip*

VERY HELPFUL, Thanks!!!

---

### Post by spinlock99 on 2008-09-09
Wow searching through old posts really works.  This is exactly what I was trying to do.  Thanks!

> **belial6 said:**
> Since I have 1 gig of ram I put max heap to 256 MB and default to 100MB.

Here is what I changed in **/usr/bin/eclipse** script (that's where my eclipse startup script is):
Before there weren't any vm arguments
VMARGS=""

Changed it to this
VMARGS="-Xms100m -Xmx256m"



Just one follow up question: "-Xmx256m" should (tm) set eclipse to use 256 megs of ram.  What does "-Xms100m" do?

Thanks again.

---

### Post by hod139 on 2008-09-09
> **spinlock99 said:**
> 
Just one follow up question: "-Xmx256m" should (tm) set eclipse to use 256 megs of ram.  What does "-Xms100m" do?
Xms sets the minimum heap size, Xmx sets the maximum heap size.

---

### Post by Znupi on 2008-09-27
Hopefully no one will bash me for bumping an old thread.
I downloaded eclipse from eclipse.org and simply unpacked and ran it. It was painfully slow, so I found this thread and installed SUN's Java, but I can't edit the /etc/eclipse/java_home file, since there is no such file. If I go to Window -> Preferences -> Java -> Installed JREs there's only one in the list and it is /usr/lib/jvm/java-6-sun-1.6.0.06 . Does that mean Eclipse is using SUN's Java? If not, what can I do to make it use it? Thanks.

---

### Post by hod139 on 2008-09-28
> **Znupi said:**
> Hopefully no one will bash me for bumping an old thread.
I downloaded eclipse from eclipse.org and simply unpacked and ran it. It was painfully slow, so I found this thread and installed SUN's Java, but I can't edit the /etc/eclipse/java_home file, since there is no such file. If I go to Window -> Preferences -> Java -> Installed JREs there's only one in the list and it is /usr/lib/jvm/java-6-sun-1.6.0.06 . Does that mean Eclipse is using SUN's Java? If not, what can I do to make it use it? Thanks.
The configuration file /etc/eclipse/java_home is where the ubuntu package of eclipse puts it.  You will have to find the corresponding file in your install location.  To see which JRE eclipse is using, you should be able to (at least it works with the ubuntu package) run eclipse from the command line:
```

$ /usr/bin/eclipse 
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found

```
From the output, we see eclipse started with java-6-sun

---

### Post by Znupi on 2008-09-28
> **hod139 said:**
> The configuration file /etc/eclipse/java_home is where the ubuntu package of eclipse puts it.  You will have to find the corresponding file in your install location.  To see which JRE eclipse is using, you should be able to (at least it works with the ubuntu package) run eclipse from the command line:
```

$ /usr/bin/eclipse 
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found

```
From the output, we see eclipse started with java-6-sun
Thanks for your answer, but it doesn't apply for me. Starting eclipse from the command line outputs nothing to the terminal. And there is no java_home file in my eclipse installation directory.

---

### Post by Znupi on 2008-09-30
Hey, I think I fixed my problem. I reinstalled Ubuntu (I had to anyway) and redownloaded Eclipse (I need the newest version for Android :D). This time I downloaded a smaller one -- I downloaded "Eclipse IDE for Java Developers" instead of "Eclipse IDE for Java EE Developers" which was almost double in size, but I don't think that matters.
When trying to start Eclipse, an error would pop up saying it can't find the Java Virtual Machine. Here's how I changed my eclipse.ini file:
```
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vm
/usr/lib/jvm/java-6-sun/bin
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
```
I basically added the -vm option. [This page](http://wiki.eclipse.org/Eclipse.ini) was of great help.
Btw, it seems Eclipse modifies the Eclipse.ini file itself, so here's how it looks after first Eclipse launch:
```
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-framework
plugins/org.eclipse.osgi_3.4.2.R34x_v20080826-1230.jar
-vm
/usr/lib/jvm/java-6-sun/bin
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-XX:MaxPermSize=256m
```
Hope I save someone else's trouble :)

---

### Post by Znupi on 2008-10-01
I think this should be added in the first post? I think lots of users download eclipse from their website, especially now with Android.

---

### Post by ddilley on 2008-11-21
It is almost 4 years since you poted this guide and you are still getting "Thank you"'s for it. Thank you for posting this!
"

---

### Post by NeuB27 on 2009-03-10
Thanks for the help on the heaps size changing, it seems to speed things up a bit, but now my other problem.

Whenever I run an application it freezes up. Not eclipse, or the computer, but the application freezes and does not accept any input, not even the exit button or the 'OK' on a simple hello world with JOptionPane.  It seems to be some type of setup problem because I can use the system console and everything works well.
Any ideas?

---

### Post by hod139 on 2009-03-11
> **NeuB27 said:**
> Thanks for the help on the heaps size changing, it seems to speed things up a bit, but now my other problem.

Whenever I run an application it freezes up. Not eclipse, or the computer, but the application freezes and does not accept any input, not even the exit button or the 'OK' on a simple hello world with JOptionPane.  It seems to be some type of setup problem because I can use the system console and everything works well.
Any ideas?

If you haven't already, I would suggest posting your question in the programming talk forum.

---

### Post by NeuB27 on 2009-03-11
Thanks I will.

---

### Post by praveenmarkandu on 2009-03-29
All I can say is "Thank You"

---

### Post by pbidwell on 2009-07-30
Sorry, I am completely new to Linux.
I do alright up until I have to edit the jvm file under /etc :(.  The problem lies in the fact that I have no jvm file under that directory.
Any ideas what I'm doing wrong and what I should do?

---

### Post by Phkillah on 2009-07-30
> **pbidwell said:**
> Sorry, I am completely new to Linux.
I do alright up until I have to edit the jvm file under /etc :(.  The problem lies in the fact that I have no jvm file under that directory.
Any ideas what I'm doing wrong and what I should do?

When you're new to Linux it's a headache to configure internal stuff. It's normal, don't stress :)

About your error, are you sure you did ALL the steps above?

Do them again and post the outputs of each.

Cheers :popcorn:

---

### Post by pbidwell on 2009-07-30
> **Phkillah said:**
> When you're new to Linux it's a headache to configure internal stuff. It's normal, don't stress :)

About your error, are you sure you did ALL the steps above?

Do them again and post the outputs of each.

Cheers :popcorn:

Thanks for the reply and encouragement.

Here are my commands and outputs up until I get the problem.  Doesn't seem as if there is anything out of the ordinary.  (You can see by the outputs that I have tried the steps a million times :)).

Command:
```
sudo apt-get install eclipse sun-java6-jdk
```Output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
eclipse is already the newest version.
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 libjack0 libmikmod2 classpath-gtkpeer tcl8.5 classpath-common
  libsdl-mixer1.2 classpath libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Command:
```
sudo update-java-alternatives -s java-6-sun
```Output:
```
No alternatives for firefox-3.0-javaplugin.so.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-1.9-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.
Using '/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide 'appletviewer'.
Using '/usr/lib/jvm/java-6-sun/bin/apt' to provide 'apt'.
Using '/usr/lib/jvm/java-6-sun/bin/extcheck' to provide 'extcheck'.
Using '/usr/lib/jvm/java-6-sun/bin/HtmlConverter' to provide 'HtmlConverter'.
Using '/usr/lib/jvm/java-6-sun/bin/idlj' to provide 'idlj'.
Using '/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide 'jarsigner'.
Using '/usr/lib/jvm/java-6-sun/bin/jar' to provide 'jar'.
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.
Using '/usr/lib/jvm/java-6-sun/bin/javadoc' to provide 'javadoc'.
Using '/usr/lib/jvm/java-6-sun/bin/javah' to provide 'javah'.
Using '/usr/lib/jvm/java-6-sun/bin/javap' to provide 'javap'.
Using '/usr/lib/jvm/java-6-sun/bin/java-rmi.cgi' to provide 'java-rmi.cgi'.
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
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
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
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
No alternatives for xulrunner-1.9-javaplugin.so.
No alternatives for xulrunner-javaplugin.so.

```Command:
```
sudo -b gedit /etc/jvm
```Output:
*Opens up a blank gedit page.  I checked the /etc directory manually using the File Browser and there is absolutely no /jvm file.


I see this tutorial is for 8.04.  I recently upgraded to 8.10.  Could that be part of my issue?  I assumed the tutorial would work 8.10 also.  If this is the problem, is there any other place I can find a similar tutorial that corresponds to my version of Ubuntu?

Thanks

---

### Post by pbidwell on 2009-07-31
Never mind.  I have fixed my own problem.  I simply downloaded Eclipse from [eclipse.org]("http://eclipse.org").  I have no problems now, and Java runs flawlessly with it.  Maybe the Eclipse version in Synaptic is too old?

I appreciate the help!

---

### Post by cmastrangelo on 2010-01-25
Hey i did everything and then when i type this one:
```
 sudo update-java-alternatives -s java-6-sun
```
It shows on the terminal: "update-alternatives: no update alternatives for ..." 3 times

and then when i type:
```
sudo -b gedit /etc/jvm
```
says: "Cannot open display"

can someone help me out w/ that?

---

### Post by HonzaPokorny on 2010-06-06
Can someone please update this thread for Lucid? Thanks

---

### Post by jbraswell on 2010-06-30
Yes, that'd be helpful.  I, also, have no jvm file.

---

### Post by ka3sem on 2010-10-13
How to install the skyway version of eclipse?

[http://www.skywayperspectives.org/portal/web/guest/downloads/overview]("http://www.skywayperspectives.org/portal/web/guest/downloads/overview")

---

