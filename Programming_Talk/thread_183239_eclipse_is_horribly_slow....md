---
title: "eclipse is horribly slow..."
date: 2006-05-27
forum: Programming Talk
---

### Post by orlox on 2006-05-27
I'm currently using xubuntu dapper, and eclipse run's very, very, VERY SLOW. I tried both the one that can be downloadedwith synaptic, and one of those that can be downloaded from eclipse and are like, "untar an use it", both with the same problem...
I used to run eclipse on ubuntu breezy with no problems...
does anyone know a way to increase eclipse's performance??

---

### Post by jvictor on 2006-05-27
which JDK are u using ?

I use the Sun JDK 1.5.0_06 + Eclipse 3.1 from eclipse.org 

The Default jdk that comes with Ubuntu doesnt work well wth eclipse

Also wts UR ram ? and do u have a lot of plugins installed ?

---

### Post by orlox on 2006-05-27
I have like 7 hundred an something of ram, an I used to run eclipse with ubuntu's jdk. I recently installed the JDK 1.5.something to use the tomcat server, but I don't know wich one eclipse is using, or where do I specify it...
The clipse I downloaded from eclipse.org comes with the web tools platform plugins, but I don't think that has much to do with the performance...I tested it on Fedora, and it worked pretty much fine...

---

### Post by jvictor on 2006-05-28
[QUOTE=orlox]I have like 7 hundred an something of ram, an I used to run eclipse with ubuntu's jdk. I recently installed the JDK 1.5.something to use the tomcat server, but I don't know wich one eclipse is using, or where do I specify it...
The clipse I downloaded from eclipse.org comes with the web tools platform plugins, but I don't think that has much to do with the performance...I tested it on Fedora, and it worked pretty much fine...[/QUOTE]

By default theres a link in /usr/bin/java that points to Ubuntu's Java .. U need to remove it and make it to point to the 'java' of where ur Sun JDK is .

Run as sudo

rm /usr/bin/java
ln -s [ur_tgt_java]  /usr/bin/java

---

### Post by beytu on 2006-05-28
Hi,
I'm using Dapper but i resolve this problem by using sun's JVM when  i was on Breezy.


To change your JVM, you should use 'sudo update-alternatives --config java' instead of 
> 
rm /usr/bin/java
ln -s [ur_tgt_java] /usr/bin/java


You can have a list of available JVM's (and libs) by typing :
'update-alternatives --list java'
If you don't have Sun's one, you should install it. It's true the default one which come with Dapper seem's to be faster on my computer ;).


For the problem about eclipse, you should also take a look into **/etc/eclipse/java_home** and add at the top of the list java's home path (e.g */usr/lib/jvm/java-1.5.0-sun/jre/bin/java* for me on Dapper)

The **/etc/eclipse/java_home** should be present if you installed eclipse using 'apt-get' 

i hope it will help you

---

### Post by orlox on 2006-05-28
How do I install sun's JVM?? I tried finding it on sun's site to no avail...I only have installed sun's JDK on my computer, and "update-alternatives" doesn't give any choice from sun...

---

### Post by kunnk on 2006-05-29
[QUOTE=orlox]How do I install sun's JVM?? I tried finding it on sun's site to no avail...I only have installed sun's JDK on my computer, and "update-alternatives" doesn't give any choice from sun...[/QUOTE]

Here are instructions, link stolen from java devel packages thread: [https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

Im using eclipse with sun jdk and can confirm that it runs fast.

---

### Post by hod139 on 2006-05-29
Sun's Java is now an official package in Dapper multiverse, so it may be easiest to upgrade to Dapper (very stable now).  

The entire install process to install Eclipse and Sun's Java (on Dapper) is to install the following 2 meta packages: eclipse sun-java5-jdk

However, as noted Eclipse will now run very slowly since it will be using GNU's java, not Sun's.  We now need to make Sun's java the default.  First,
```
sudo update-alternatives --config java
``` and select Sun's java.  You might want to do the same for jar, javac, javadoc, javap, and javaws.

Next, edit the JVM configuration file
```
sudo -b gedit /etc/jvm
``` and move the line 
```
/usr/lib/jvm/java-1.5.0-sun
``` to the top.

Lastly, Eclipse for some reason ignores Ubuntu's JVM configuration file and uses its own (bug?).  You need to edit eclipes's java_home file
```
sudo -b gedit /etc/eclipse/java_home
``` and add
```
/usr/lib/jvm/java-1.5.0-sun
``` to the top of the file.

That's it.  Does anyone think I should post these instructions as a HOWTO ?

---

### Post by beytu on 2006-05-29
great idea hod139, a lot of people asking for this (also in french forum for exemple).

But i have another little problem with this sun's java package about rmiregistry ... :
```

beytu@proteus:~$ ls -l /usr/bin/rmiregistry
lrwxrwxrwx 1 root root 29 2006-05-27 18:38 /usr/bin/rmiregistry -> /etc/alternatives/rmiregistry
beytu@proteus:~$ ls -l /etc/alternatives/rmiregistry
lrwxrwxrwx 1 root root 41 2006-05-27 19:25 /etc/alternatives/rmiregistry -> /usr/lib/jvm/java-gcj/jre/bin/rmiregistry

```

And the selected JVM is sun's one ... is it me or a bug ? ;)

NB : i didn't noticed this /etc/jvm file ... :-k . Which apps use this file ? It will problably prevent me to edit the /etc/init.d/tomcat file the next time (i hope) ;)

---

### Post by riverfr0zen on 2006-06-05
thanks hod139 -- that solution totally solved my sluggish eclipse problem

---

### Post by Amablue on 2006-06-06
Hod, when I type that first line into the terminal, I get this:```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java

```

None of those give any mention of Sun I've already used synaptic to get sun-java5-jdk and eclipse.

---

### Post by hod139 on 2006-06-27
Sorry for taking so long to respond, I failed to notice there was even a question.  Are you still having a problem?  I posted all the instructions as a [howto]("http://ubuntuforums.org/showthread.php?t=201378"), so if you are still having this problem it might be good to post it there.  You can try reinstalling the sun-java5-jdk package.

---

### Post by umuro on 2006-08-07
This should be a howto.

Before finding this post, I was sheepishly looking at all the exception logs and wondering why java 1.5 is ignored by eclipse at all. Anybody getting started on Eclipse and switching JVM is bound to hit those problems...

---

### Post by hod139 on 2006-08-07
> **umuro said:**
> This should be a howto.
It is: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by ecor6633 on 2006-11-23
Ok then can someone explain me what I did wrong... ?
I downloaded jdk-1_5_0_09-linux-i586.bin from sun's website.
I also downloaded latest version of eclipse on eclipse.org (eclipse-SDK-3.2.1-linux-gtk.tar.gz).

I ran the jdk installer in /home/login/local/jdk1.5.0_09 and untar eclipse in /home/login/local/eclipse.

I changed the /etc/alternatives to sun jre and ran eclipse.

Normally as i understood with the latest eclipse and sun jre it should be as fast as a windows version.
Can you tell me why it takes nearly 20 minutes to display the window that lets me "find and install" new packages ?

I was used to download my plugin with the plugin manager but 20 minutes only to get the window appear is too slow.

Does anybody expierienced the same ?

---

### Post by Ian0107 on 2006-11-24
thank you for you so detailed solution:-D

---

### Post by hod139 on 2006-11-24
> **ecor6633 said:**
> Ok then can someone explain me what I did wrong... ?
I downloaded jdk-1_5_0_09-linux-i586.bin from sun's website.
I also downloaded latest version of eclipse on eclipse.org (eclipse-SDK-3.2.1-linux-gtk.tar.gz).

I ran the jdk installer in /home/login/local/jdk1.5.0_09 and untar eclipse in /home/login/local/eclipse.

I changed the /etc/alternatives to sun jre and ran eclipse.


Is there any particular reason you downloaded Sun's jdk from their website instead of using the version in the repository?  Also, you'll want to run 
```
java-update-alternatives
```
First, run it with the -l switch to find the name of Sun's java, and then run it with the -s switch.  If you used the version of java in the repository, it would be
```

sudo update-java-alternatives -s java-1.5.0-sun

```but as I said earlier, you may want to run 
```

update-java-alternatives -l 
```to find the name of the java installed by Sun.

Lastly, also make sure you edit 
```
/etc/jvm
``` and move the line (or add it if it doesn't exist) containing the path to the java jvm to the top of the file.

All of this is mentioned in my howto.  Hope this helps.

---

### Post by ecor6633 on 2006-11-25
Thanks a lot but i have tried those package from synaptic and had same problems.

One collegue suggest me to upgrade to edgy that's what i'll try.
(Anyway i prefer using eclipse 3.2 which is not in dapper)

I hope it will help.

---

### Post by lloyd mcclendon on 2006-11-26
it's really not that hard people.  no need to piss around with alternatives, which i think is one of the most over-engineered unintuitive things i've seen on linux yet.


1. use the automatix script on here to install suns java
2. download eclipse from their website, check one of the prebundled distros or jboss ide, they have some nice stuff

3. untar the eclipse tar ball
4. sudo mv eclipse /usr/share -v
5. sudo vim /usr/bin/eclipse
6.  paste this in

#!/bin/bash

eclipse_dir="/usr/share/eclipse/"
eclipse="${eclipse_dir}/eclipse"
eclipse_args="-vmargs -Xverify:none -XX:+UseParallelGC -XX:PermSize=40M -XX:MaxNewSize=64M -XX:NewSize=64M -Xmx512m -Xms512m"

${eclipse} ${eclipse_args} $*

7. sudo chmod 755 /usr/bin/eclipse
8. eclipse

---

### Post by hod139 on 2006-11-26
> **lloyd mcclendon said:**
> it's really not that hard people.  no need to piss around with alternatives, which i think is one of the most over-engineered unintuitive things i've seen on linux yet.

Just because you don't like alternatives doesn't mean you should be telling people not to use it, it is the Debian (and by relation) Ubuntu way!  It's really not that hard :)

> 
1. use the automatix script on here to install suns java
2. download eclipse from their website, check one of the prebundled distros or jboss ide, they have some nice stuff
Personally, I don't like using automatix, I like to know exactly what is going on, and using too many 3rd party scripts can really bork up a system (nothing against automatix, I think it is a great idea for people that just want the most common stuff to work and don't want to spend the time to figure it all out.  That's just not me.).  

Also, the howto is specifically for the version of Sun's Java and Eclipse in the repositories.  I have no problem if people "need" the latest versions of software and want to download them and install manually.  I  prefer to let Ubuntu handle the package management, as that is its main function as a distribution.

>  
eclipse_args="-vmargs -Xverify:none -XX:+UseParallelGC -XX:PermSize=40M -XX:MaxNewSize=64M -XX:NewSize=64M -Xmx512m -Xms512m"
Where did you get that list of args, I'm not familiar with all of them and would like to know what they are doing before recommending them.

---

### Post by lloyd mcclendon on 2006-11-26
if you can't figure out what they are just by looking at them, i don't think you're in any position to recommend anything.  the only thing someone may want to change is the last two down to 256 if you have < 1G of ram


letting ubuntu manage applications such as eclipse is pointless.  i did that a long time ago and it's just a big waste of time for being insecure about yourself. a lot of times the packages are old, sometimes really old. apt-get is the best package manager but i've had more than my share of bugs within the package.


plus WHY do you need a package for eclipse?  what is wrong with the vanilla version on ecilpse's website?  apparently the ubuntu version is a piece, look at all the problems right here with it.  i type eclipse & and i have a fast fully working version of eclipse.  


i don't even know how to install suns java on here, cause automatix did a nice job of it and didn't screw anything up.  i see no reason not to use that script.  keep wasting time _installing java_ and i'll keep working on my website here that is the next myspace.

---

### Post by hod139 on 2006-11-26
> **lloyd mcclendon said:**
> if you can't figure out what they are just by looking at them, i don't think you're in any position to recommend anything.  the only thing someone may want to change is the last two down to 256 if you have < 1G of ram

This doesn't answer my question and I seriously doubt you know what the options do, nor even if you did, would it qualify you to make recommendations; I don't see how knowing obscure java virtual machine arguments qualifies or disqualifies someone for writing a howto on installing the repository versions of eclipse and Sun's java :confused:.  

Since you didn't feel like answering my question, I decided to do some searching myself. First of all, XX JVM switches are officially "unsupported", and the switches you provided will only work with Sun's java 1.5.

First, the -Xverify:none switch: this switch 
> turns off Java bytecode verification, making classloading faster, and eliminating the need for classes to be loaded during startup solely for the purposes of verification.  This switch improves startup time, and there is no reason not to use it.
([source]("http://performance.netbeans.org/howto/jvmswitches/index.html"))
Thanks for this switch, I'll add it to my guide.

Next, -XX:+UseParallelGC.  This is a very interesting switch.  [According to Sun]("http://java.sun.com/docs/hotspot/gc5.0/gc_tuning_5.html"), using this switch on uni-processor systems will result in a performance loss.  Yet, according to the [above source]("http://performance.netbeans.org/howto/jvmswitches/index.html"), 
> 
some tests have shown that, at least on systems fairly well equipped with memory, the durations of minor garbage collections is halved when using this collection algorithm, on uniprocessor systems.  Note that this is paradoxical - this collector is designed to work best on multiprocessor systems with gigabyte heaps.  No data is available on its effect on major garbage collections.
So thanks, but I don't think I will be recommending that option.

Next, -XX:PermSize=40M.  I can't really find much of anything about this switch, except for some obscure IBM [article]("http://publib.boulder.ibm.com/infocenter/wasinfo/v6r0/index.jsp?topic=/com.ibm.websphere.base.doc/info/aes/ae/tprf_tunejvm.html") suggeting a value of 128MB.  Again, I don't think this is worth recommending to everyone.

Next, -XX:MaxNewSize=64M -XX:NewSize=64M.  Again, I couldn't really find much about these options except
> 
The parameters [FONT=Courier New, Courier, mono]NewSize[/FONT] and [FONT=Courier New, Courier, mono]MaxNewSize[/FONT] bound the *young* generation size from below and above. Setting these equal to one another fixes the *young* generation, just as setting [FONT=Courier New, Courier, mono]-Xms[/FONT] and [FONT=Courier New, Courier, mono]-Xmx[/FONT] equal fixes the total heap size. This is useful for tuning the *young* generation at a finer granularity than the integral multiples allowed by [FONT=Courier New, Courier, mono]NewRatio[/FONT].
([source]("http://java.sun.com/docs/hotspot/gc5.0/gc_tuning_5.html"))
Since I have no idea what this will do to a typical users need (the site is more for server installs) I don't think this is a good suggestions either.

Lastly, -Xmx512m -Xms512m.  I also suggested users increase these values, however it is very important that Xms is not set higher than your physical ram.  Also, 32m is probably plenty of initial heap to load eclipse, and as java needs more it can grow to the max specified by  Xmx. Similarly, the Xmx value should be set based on the users specific amount of RAM, not a magic number.  If you make the heap size too large then parts of eclipse will continuously swap in and out or memory.

> **lloyd mcclendon said:**
> 
letting ubuntu manage applications such as eclipse is pointless.  i did that a long time ago and it's just a big waste of time for being insecure about yourself. a lot of times the packages are old, sometimes really old. apt-get is the best package manager but i've had more than my share of bugs within the package.

plus WHY do you need a package for eclipse?  what is wrong with the vanilla version on ecilpse's website?  apparently the ubuntu version is a piece, look at all the problems right here with it.  i type eclipse & and i have a fast fully working version of eclipse.  

i don't even know how to install suns java on here, cause automatix did a nice job of it and didn't screw anything up.  i see no reason not to use that script.  keep wasting time _installing java_ and i'll keep working on my website here that is the next myspace.Again, these are your own personal opinions which are contrary to popular belief.  Calling someone insecure for letting ubuntu manage all their packages will probably aggrevate a lot of the ubuntu developers, since that is their main job!!  Yes a lot of the packages are old (usually no more than a  year and often times less than that), but they will all work!  That is the point of letting ubuntu manage my packages, I know they will work with each other and I don't have to worry about the inter-dependencies.

---

### Post by dustman on 2007-11-19
Thanks hod139 !! It solved the problem for me too. I would have just a little question: before following your solution, i was working with an eclipse downloaded from the official eclipse.org site, and a jdk downloaded from sun.java.com.... from eclipse i set the path to the jre to be a path to my downloaded jre (from java). So that means i was using sun's java or not?


Cheers!


Radu

---

### Post by hod139 on 2007-11-19
Wow, what an old thread.  To answer your question, you can always type
```
java -version
```and 
```
javac -version
```If you install java from the repository (I doubt the downloaded jdk integrates with Debian's alternative's system, but I could be wrong), you can use 
```

update-java-alternatives -l

```to list the available java implementations
 and 
```
 sudo update-java-alternatives -s [name] 
```to select an implementation.

If you used my howto ([http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)) feel free to post questions about it there, not here.

---

