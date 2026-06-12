---
title: "Ubuntu as a Java development platform"
date: 2008-03-02
forum: Programming Talk
---

### Post by brian.pedersen on 2008-03-02
I am currently evaluating Ubuntu and its ability to fit in as a professional Java development platform.

When trying to install a Sun JDK, I have tried using the apt-get which did not work as I was unable to accept the license agreement.

I have tried using the Add/Remove as well as the Synaptic Package Manager, which in both cases downloaded and installed some packages, but unfortunately ended up crashing without successfully completing the installations.

Finally I have tried manually converting and installing the .bin packages from the Sun web site by following this guide: [http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package), which seems to do fine until I to do a java -version and get an error.

These problems has been consistent when trying to install any of the following Sun JDK's: 1.4.2, 1.5, 1.6.

Browsing the internet I find more questions than answers regarding Java development on Ubuntu.

I have seen many similar questions being answered with something like "This is Sun's fault as they have not open sourced their JDK, use <insert your favorit GNU JDK> instead".

As much as I appreciate anyones opinion, please consider if such a statement represents a viable solution to the problem.
When working profesionally with Java you do not have the option of freely choosing a JDK, you have to go with whatever is supported by your application server vendor.

I know Sun's JDK's works very well on a number of other platforms, including other GNU/Linux distros.
I am however not very experienced with Ubuntu, and it could be that I am simply doing some basic step wrong.

My current evaluations are all performed using an Ubuntu 7.10 LiveCD, as it allows me to easily roll back everything, by simply restarting the computer.

Is anyone here doing professional Java development on Ubuntu ? Are you using Sun JDK's ?

Thanks ...
/Brian

---

### Post by LaRoza on 2008-03-02
What command are you using to install?

I don't know if there are any problems with installing it on a Live session, but it works fine (as far as I use it, I am not a big Java user at the moment) for me.

Enable all the repositories, and run this command:
```

sudo aptitude install sun-java6-jdk

```

If it fails, post the error messages.

---

### Post by dicecca112 on 2008-03-02
are we talking x86 or x86-64?  I know I had tons of problems installing the SDK in 64bit, but I currently program java in 32bit with no issue whatsover

---

### Post by brian.pedersen on 2008-03-02
I used to have issues accepting the license when doing this, now however I figured that i can use the TAB key :)

Still however, I end up having a crashed installation.

/Brian

```

...
Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

Setting up sun-java6-jre (6-03-0ubuntu2) ...

Setting up sun-java6-bin (6-03-0ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.03/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Setting up sun-java6-jdk (6-03-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java6-bin (6-03-0ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.03/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 sun-java6-bin
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
ubuntu@ubuntu:~$ java -version
java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
ubuntu@ubuntu:~$ 

```

---

### Post by brian.pedersen on 2008-03-02
32 bit.

/Brian

---

### Post by brian.pedersen on 2008-03-02
I am glad to hear you saying that it works for you, this indicates that my issues could be caused by running from a LiveCD.

I will try doing a real installation and see if this fixes my issues.

Thanks ...
/Brian

---

### Post by pmasiar on 2008-03-02
I installed JDK + Tomcat on ubuntu/32 with no problems via synaptic, much smoother experience than on Windows.

LiveCD is to test compatibility/autodetection of your hardware. IMHO you cannot expect installing couple hundreds of MBs apps - where it should go? LiveCD does not have the disk, right? It just fakes disk with RAMdisk, AFAIK.

---

### Post by sloggerkhan on 2008-03-02
I use sun java with eclipse for my University CS coursework all the time.
It works pretty well, the thng to keep in mind is you might have to set which java because there are a number of alternatives.
I think eclipse is better downloaded from the eclipse website and run as a binary than installed from the repos, but that's just my opinion.

---

### Post by a9bejo on 2008-03-02
We  do Java/J2EE development at work, and my work pc is running Ubuntu.

```

sudo aptitude install sun-java6-jdk && sudo update-java-alternatives

```

This should normally be everything that's needed to make it work.  Apart from that, many of the other tools you usually install for development (like Maven2, Eclipse or Glassfish) are already in the repositories.  

> 
I have seen many similar questions being answered with something like "This is Sun's fault as they have not open sourced their JDK, use <insert your favorit GNU JDK> instead".


Such advice would be obsolete today anyway, since Sun has released Java as free software some time ago.  The current sun-java6-jdk package is still sun's closed solution, but Java 7 will be a completely free release. The current java7 trunk is already in the repositories under the codename "icedtea" too.

---

### Post by Can+~ on 2008-03-02
Try it with installed ubuntu either:
-Get an old HDD/PC and use it.
-Install ubuntu it via Wubi (maybe waiting for 8.04?).
-Run it from a pen drive (there's a guide online I think)

---

### Post by brian.pedersen on 2008-03-03
Hi everyone

Thanks for all the answers, this is indeed a great forum and I really appreciate all the helpful answers I have been getting.

I got stuck during my Wubi installation yesterday evening, as I got hit by some startup issues.
I don't suspect they will be hard to nail, but it simply got too late as I need to go to work today.

I will continue my experiments this evening, and let you know how it works out.

> LiveCD is to test compatibility/autodetection of your hardware. IMHO you cannot expect installing couple hundreds of MBs apps - where it should go? LiveCD does not have the disk, right? It just fakes disk with RAMdisk, AFAIK.

A valid point, running on a computer with 2GB of RAM however, there should be plenty of room to install a JDK in memory.
I have been checking my RAM usage regularly during my experiments, and nothing has been indicating that I have been even close to running out of RAM.

> We do Java/J2EE development at work, and my work pc is running Ubuntu.

Im happy to hear that, to me this indicates that it makes sense to continue my work on this.

Thanks a lot everyone, your help is much appreciated.
/Brian

---

### Post by pmasiar on 2008-03-03
> **brian.pedersen said:**
> 
> LiveCD is to test compatibility/autodetection of your hardware. IMHO you cannot expect installing couple hundreds of MBs apps - where it should go? LiveCD does not have the disk, right? It just fakes disk with RAMdisk, AFAIK.

A valid point, running on a computer with 2GB of RAM however, there should be plenty of room to install a JDK in memory.
I have been checking my RAM usage regularly during my experiments, and nothing has been indicating that I have been even close to running out of RAM.


maybe JDK overruled symlinking magic what makes LiveCD possible. When you think about it, even running from CD is incredible: OS expects to be run from disk, which is writable. Then, you install big package, what expects to be run from disk - but parts  of system are still on CD. 

Why you just don't create 5-10GB partition of your disk and install Linux there? I am sure that Wubi is great and what not, but why even rely of Windows being around? Installing double-boot with ubuntu is trivial - even I can do it :-)

---

### Post by brian.pedersen on 2008-03-04
Just a quick update.

Having decided to go for a "real" installation, I have been haunted by various installation issues.

My first issue appeared after the initial 7.04 Wubi installation had completed.
When logging in, Ubuntu would hang in a white screen without responding to anything.
I believe this was caused by leftovers from a previous 8.04 Wubi installation, and I therefore did a reinstallation with a cleanup and everything worked fine.

Unfortunately the Wubi installer is not included in the 7.10 image and downloading it from wubi-installer.org, only enables you to install 7.04, so I had to use the built in upgrade feature to get my 7.04 installation upgraded to 7.10.

This took quite a bit longer than expected, and once it had completed, I was hit by the "failed to initialize HAL" bug.

Having found a proposed solution to this issue, which should ensure dbus starts before hal, I realized that I was now unable to start my Ubuntu installation.
Whenever I choose to start Ubuntu, it hangs in the load screen, and never gets around to the login screen.

I guess the next step will be to once again reinstall everything.

Does anyone now how to do a Wubi installation of 7.10 without having to do 7.04 first ?

> maybe JDK overruled symlinking magic what makes LiveCD possible. When you think about it, even running from CD is incredible: OS expects to be run from disk, which is writable. Then, you install big package, what expects to be run from disk - but parts of system are still on CD. 

I must admit I have no knowledge of the internal plumbing involved in making LiveCD's possible.
I thought it was achieved by simply mounting the OS on a RAM disc, but I guess I'm wrong.

> Why you just don't create 5-10GB partition of your disk and install Linux there? I am sure that Wubi is great and what not, but why even rely of Windows being around? Installing double-boot with ubuntu is trivial - even I can do it

The reason for not doing so, is that i want to have an easy way of recovery while doing my initial experiments.
Whenever I mess something up, I would rather roll back everything and start from a fresh, instead of having to fix a broken operating system.

This is easily achieved with a LiveCD, as you can simply restart the computer, with a Wubi installation I can backup the wubi directory inside windows, and simply replace my broken wubi installation with the backup, once something goes wrong.

If I want to do an installation on dedicated partions, the backup approach is still possible, but it is more complex and time consuming.

Once I have completed my evaluation and choose to actually move to Ubuntu, I will of course wipe my Windows installation, install Ubuntu on its own dedicated partions and set fire to all of my Windows CD's :)

Once again, thanks for the help everyone ...
/Brian

---

### Post by CptPicard on 2008-03-04
There's one gotcha in your approach... you're getting more problems with Wubi than you'd be getting with a "normal" Ubuntu installation, so you might actually start believing it's not worth it.

My Ubuntu installations have always  gone perfectly well, and I've used Linux for Java development for all of this millennium now, the past few years professionally. Works great, and things like Netbeans and Eclipse are identical to what they are on Windows -- and in some ways, feel more at home on Linux...

---

### Post by jay019 on 2008-03-04
Not sure if this post will help much in any way other than offering hope, but...

I am developing java apps (albeit not professionaly) on my Ubuntu 7.04 laptop. I downloaded the sdk from sun direct and ran it. It installed in a folder in my home directory (/home/me/jdk1.6.0) so to uninstall I will just remove the folder. I then installed netbeans in the same manner and I have had no issues so far. All I had to do was edit my .bashrc file to add the JAVA_HOME and CLASSPATH variables.

I have even gone further and installed launch4j and Inno Setup to create windows executables from my desktop. Being able to create windows apps without using windows is the best feeling!

---

### Post by pmasiar on 2008-03-04
As i said before, and also CptPicard, you struggle with Wubi and think it has something common with ubuntu. Seems like Wubi is not as stable as it is cool - because Wubi still has to rely on windows to access disk file system.

Defragment your disk, create a new partition if free space (Vista can do that [and use it's tool, Vista complains if you change partitions], for XP you can do it from LiceCD), and install ubuntu there. Double-boot is years old stable and mature technology.

---

### Post by brian.pedersen on 2008-03-04
Hmmm, guess you just might end up convincing me to do a proper installation on dedicated partitions ;)

/Brian

---

### Post by tux87 on 2008-03-04
[QUOTE=brian.pedersen]Hmmm, guess you just might end up convincing me to do a proper installation on dedicated partitions  [/QUOTE]


Go for it,  Im a bit of a newbie for ubuntu. (and linux in general) 

Ive had Sun's JDK 6, eclipse and tomcat 5.5 runing on ubuntu 7.10 for a few weeks now with no problems at all.  It all installed fine with no problems. (well the jdk and eclipse... tomcat was a bit harder)

I followed this tutorial, written by a friend of mine.

[[COLOR="Sienna"]**_http://www.thelinuxsociety.org.uk/content/how-to-set-up-eclipse-in-ubuntu-using-sun-java-jdk-6_**[/COLOR]]("http://www.thelinuxsociety.org.uk/content/how-to-set-up-eclipse-in-ubuntu-using-sun-java-jdk-6")

---

### Post by jespdj on 2008-03-05
I'm a Java software developer. At work, I use Windows XP - I'm not allowed to install a different OS on my work PC.

But at home I use Ubuntu 7.10 on my computers and I frequently use it to program in Java.

Ubuntu by default comes with GNU Java (gcj), which is a free but not really useable implementation of Java 1.4 (it's very slow and incomplete). Installing Sun Java 6 is very easy, and it works great. In addition to the newest update of Sun's JDK, things like Apache Tomcat, Eclipse, GlassFish etc. are all available in the Ubuntu software repository.

Sun seems to support Ubuntu for Java development, see this: [http://www.sun.com/software/linux/developer.xml](http://www.sun.com/software/linux/developer.xml)

---

### Post by naugiedoggie on 2008-03-07
> **brian.pedersen said:**
> I am currently evaluating Ubuntu and its ability to fit in as a professional Java development platform.

When trying to install a Sun JDK, I have tried using the apt-get which did not work as I was unable to accept the license agreement.

I have tried using the Add/Remove as well as the Synaptic Package Manager, which in both cases downloaded and installed some packages, but unfortunately ended up crashing without successfully completing the installations.

Finally I have tried manually converting and installing the .bin packages from the Sun web site by following this guide: [http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package), which seems to do fine until I to do a java -version and get an error.

These problems has been consistent when trying to install any of the following Sun JDK's: 1.4.2, 1.5, 1.6.

Browsing the internet I find more questions than answers regarding Java development on Ubuntu.

I have seen many similar questions being answered with something like "This is Sun's fault as they have not open sourced their JDK, use <insert your favorit GNU JDK> instead".

As much as I appreciate anyones opinion, please consider if such a statement represents a viable solution to the problem.
When working profesionally with Java you do not have the option of freely choosing a JDK, you have to go with whatever is supported by your application server vendor.

I know Sun's JDK's works very well on a number of other platforms, including other GNU/Linux distros.
I am however not very experienced with Ubuntu, and it could be that I am simply doing some basic step wrong.

My current evaluations are all performed using an Ubuntu 7.10 LiveCD, as it allows me to easily roll back everything, by simply restarting the computer.

Is anyone here doing professional Java development on Ubuntu ? Are you using Sun JDK's ?

Thanks ...
/Brian

Hello,

I'm using NetBeans 6.0 with JDK 6 on 7.10.  I use it as much as I can, although I wind up using NB on my laptop a lot because I travel.

There is no NB package for Ubuntu, so I installed it manually.  I believe I did the same with Java, I can't remember the reason, though.  I may have had some problem like yours, or maybe the package available was not the latest version at the time.

Thanks.

mp

---

### Post by brian.pedersen on 2008-03-07
I finally went for a proper installation on dedicated partitions, and you were of course all right, everything worked like a charm once I was running from a "real" installation.

Conclusion: only use Wubi and LiveCD's for getting that initial impression of the OS.

Unfortunately installing eclipse not only downloaded another JDK that I didn't need, it also replaced my Sun JDK.
This was however fixed by running yet another update-java-alternatives.

```

sudo aptitude install sun-java6-jdk && sudo update-java-alternatives
sudo aptitude install eclipse
sudo update-java-alternatives -s java-6-sun

```

Thanks again everyone.
/Brian

---

