---
title: "Howto: Manually (non-repo) install jre-1_5_0_06 on Dapper"
date: 2006-03-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Arktis on 2006-03-21
I noticed people were still using my [old manual java howto thread]("http://ubuntuforums.org/showthread.php?t=76754").  I've since updated the instructions to apply to the newer firefox on dapper.

[COLOR="Red"]These manual install instructions should only be used if for some reason you cannot follow the java-package install method.  Also, 
[QUOTE=jdong]In Dapper, Sun Java is available in the Multiverse section as **sun-java5-jre** and **sun-java5-jdk** (JDK is the development kit that contains the Java compiler)[/QUOTE][/COLOR]

So, here we go:
=============

First, download the linux runtime installer [here]("http://java.com/en/download/manual.jsp"). Do NOT get the rpm! Get the one that says Linux (self-extracting file).

After downloading, cd to where you downloaded the file and run:
```
sudo mv jre-1_5_0_06-linux-i586.bin /usr/local
cd /usr/local
sudo chmod a+x jre-1_5_0_06-linux-i586.bin
sudo sh jre-1_5_0_06-linux-i586.bin
```

Say 'yes' to the license agreement and watch it extract the files into a folder called jre1.5.0_06
You're almost done. Now you want to install the plugin for firefox:

```
cd /usr/lib/firefox/plugins
sudo ln -s /usr/local/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so
```

Firefox is now happily running java applets (once you restart it).
The final steps are:

```
sudo ln -sf /usr/local/jre1.5.0_06/bin/java_vm /usr/bin/java_vm
sudo update-alternatives --install /usr/bin/java java /usr/local/jre1.5.0_06/bin/java 1
```

And now the java runtime environment appears in your list of choices when running ***'sudo update-alternatives --config java'***! Go ahead and run that, and chose the sun java option. Then to check to make sure it worked, run ***'java -version'***, which should output something like this:

```
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
```
Done!

If you want to do some configurating with the java control pannel, run

```
sh /usr/local/jre1.5.0_06/bin/ControlPanel
```

Enjoy!

=========================
Removal Instructions

If the time comes when you need/want to remove java, these commands will do the trick if you followed the howto exactly:

```
sudo rm /usr/lib/firefox/plugins/libjavaplugin_oji.so
sudo rm /usr/bin/java_vm
sudo update-alternatives --remove java /usr/local/jre1.5.0_06/bin/java
```


Then you'll want to open up a root nautilus and go to /usr/local/ and delete the jre1.5.0_06 folder.

---

### Post by lptr on 2006-05-06
Worked like a charm. Thank you!

---

### Post by bierpullen on 2006-05-06
It worked like a charm. Thank you!  :p 



-----------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php](http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php)

---

### Post by hamil on 2006-05-06
Thank you. 
Running latest Sun Java now!

---

### Post by JeronimoGe on 2006-05-06
java installed on dapper but mozilla plugin not 

i've made whith my way 

> sudo apt-get install java-package
chmod +x jre-1_5_0_06-linux-i586.bin
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb

after reboot mozilla

---

### Post by LuisC-SM on 2006-05-22
[QUOTE=Arktis]I noticed people were still using my ......
So, here we go:
=============

First, download the linux runtime installer [here]("http://java.com/en/download/manual.jsp"). Do NOT get the rpm! Get the one that says Linux (self-extracting file).

After downloading, cd to where you downloaded the file and run:
```
sudo mv jre-1_5_0_06-linux-i586.bin /usr/local
cd /usr/local
sudo chmod a+x jre-1_5_0_06-linux-i586.bin
sudo sh jre-1_5_0_06-linux-i586.bin
```
..........
.[/QUOTE]
Should this also work for Breezy ?

I'm having troubles not finding java-package on the repos and just got tired of enableing/disableing repos... so any advice will be appreciated.

Kind Regards

Luis C. Suárez

PS. this is my sources.list (just in case)
> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [http://code.campware.org/debian/](http://code.campware.org/debian/) unstable main


---

### Post by LuisC-SM on 2006-05-22
Yes it works !!!!
Thank u so much

Kind Regards

Luis C. Suárez

PS1: I think this should be the java totorial instead of the one in the wikky. It's so simple and faster
PS2: Here is the link for breezy and I believe is almost the same.
[http://ubuntuforums.org/showthread.php?t=76754](http://ubuntuforums.org/showthread.php?t=76754)

---

### Post by learning on 2006-05-22
I though I followed the instructions right but when I run java version here is what I get:

jason@jason-desktop:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: version not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

Anyone know what I could have done wrong and what I should do to fix it?

---

### Post by husky_tdawg on 2006-06-03
[QUOTE=learning]I though I followed the instructions right but when I run java version here is what I get:

jason@jason-desktop:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: version not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

Anyone know what I could have done wrong and what I should do to fix it?[/QUOTE]


you had "java version"

you forgot the '-'

it should be:  "java -version"

---

### Post by jdong on 2006-06-03
What would be the advantage of installing Java using either this or the java-package method?

In Dapper, Sun Java is available in the Multiverse section as **sun-java5-jre** and **sun-java5-jdk** (JDK is the development kit that contains the Java compiler)

---

### Post by Fornie on 2006-06-03
geezz i'm so slow and i need your help...i already download the file on my desktop (by default the file(s) are saved on my desktop) and followed the instructions...

***STEP 1 - I typed the command***
fornie@fornie:~$ sudo mv jre-1_5_0_07-linux-i586.bin /usr/local
***STEP 2 - I entered my login password which unfortunately failed***
Password:
mv: cannot stat `jre-1_5_0_07-linux-i586.bin': No such file or directory
***STEP 3 - I typed the command sudo -i***
fornie@fornie:~$ sudo -i
***STEP 4 - I typed the command again***
root@fornie:~# sudo mv jre-1-5-07-linux-i586.bin /usr/local
mv: cannot stat `jre-1-5-07-linux-i586.bin': No such file or directory
root@fornie:~#


hmmm...? I somewhat got the idea that the problem is with the location of the file...help pls! thanks im kinda slow please bear with me hahhaa

---

### Post by Fornie on 2006-06-03
geezz sorry...i got it already...

what i did, i transferred the file on /home/fornie/
go to konsole 
> fornie@fornie:~$ sudo chmod a+x jre-1_5_0_07-linux-i586.bin /home/fornie/
> fornie@fornie:~$ ls -
> fornie@fornie:~$ ./jre-1_5_0_07-linux-i586.bin

then whoa!...I'm so happy!!! this is fun!! i'm learning...

---

### Post by elephas on 2006-06-04
[quote=jdong]
In Dapper, Sun Java is available in the Multiverse section as **sun-java5-jre** and **sun-java5-jdk** (JDK is the development kit that contains the Java compiler)[/quote] 

it works too, but only from command line:
```
sudo apt-get install sun-java5-jdk
```

If you try to run it from adept client, you'll get in plenty of trouble.](*,)

---

### Post by jdong on 2006-06-04
That is an Adept bug, then... the Java package uses Debconf to display the license agreement to you, and as per the redistribution terms, you must indicate acceptance of the license. This requires a Debconf-interactive terminal (or another debconf method of interacting with a human). I believe Synaptic handles it fine, as does command line. If Adept doesn't, that's an Adept bug and should be filed as such in Launchpad.

---

### Post by Arktis on 2006-06-07
[QUOTE=jdong]What would be the advantage of installing Java using either this or the java-package method?

In Dapper, Sun Java is available in the Multiverse section as **sun-java5-jre** and **sun-java5-jdk** (JDK is the development kit that contains the Java compiler)[/QUOTE]
IMHO, it's always good to cover your bases.  I've now edited the first post to contain that information.

---

### Post by jdong on 2006-06-08
Thanks for doing so!

There are numerous advantages to using the distribution's packages, including easier management of upgrades (both possible security updates AND in 6 months when you want to do a distribution upgrade) and better integration (nobody knows how to do it better than the distribution developers themselves!) with the distribution.

However, as you said, it's always good to have this fallback if something doesn't work out.

---

### Post by elephas on 2006-06-10
[quote=jdong]That is an Adept bug, then... the Java package uses Debconf to display the license agreement to you, and as per the redistribution terms, you must indicate acceptance of the license.[/quote] 
Exactly. This package, like some others, launches interactive text-mode terminal session; Adept by default keeps it hidden, all the user sees by default is the frozen progress bar. Even if you show details and see the session, sometimes you can interact with it by pressing Tab, Space and Enter, sometimes you can't. Can't use the mouse either....:-k

---

### Post by NoWhereMan on 2006-06-10
guys, alien-ized rpm from suns [https://mustang.dev.java.net/](https://mustang.dev.java.net/) (Java 6!) works pretty well. With Java6 you can get rid of its "alien" gui, and get finally a better gtk look and feel (some glitches @16-bit video mode) whit themed applications.

bye

---

### Post by equilibrium on 2006-07-15
cool I can try sloth now :)

---

### Post by jordi_rc on 2006-09-23
Nice tutorial for java jse!

I have not internet connection at this time and need to have JDK installed in Xubuntu.

How can I install the JDK? The same way that JRE?
How should I do it?

Please help!

Jordi

---

### Post by rangi500 on 2009-07-12
Thanks! It worked perfectly. I tried this after various attempts installing with apt-get failed.

One thing that caught me out for a second - when you download the self extracting file, the java version is newer, so the filename is different. So anyone following the steps in the original post should bear this in mind and remember to use the filenames relevant to the file you download.

---

