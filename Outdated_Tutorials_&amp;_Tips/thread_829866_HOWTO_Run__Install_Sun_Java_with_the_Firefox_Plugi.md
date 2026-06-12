---
title: "HOWTO: Run / Install Sun Java with the Firefox Plugin on an Ubuntu Live CD or USB"
date: 2008-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by aMeR1CaN_aUsSie on 2008-06-15
[SIZE="5"]_**How to: Run / Install Sun Java with the Firefox Plugin on an Ubuntu Live CD or USB**_[/SIZE]

[SIZE="4"]_**NOTE: This should work with Hardy Heron 8.04, Gutsy Gibbon 7.10, Feisty Fawn 7.04 and others (but definitely Hardy Heron 8.04 ).**_[/SIZE]

[SIZE="4"]_**Introduction**_[/SIZE]
Firstly, I'm a complete noob at ubuntu, and only look like I know what I'm talking about from the research I have done trying to solve this problem.

[SIZE="3"]_**THE PROBLEM**_[/SIZE]
When running Ubuntu from a live cd or live usb, and trying to install java, the following errors appear:

> java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
OR
> Setting up sun-java6-bin (6-06-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.


[SIZE="4"]_**Getting and Preparing the files**_[/SIZE]

[SIZE="3"]_**Adding the Multiverse and Universe Repositories**_[/SIZE]
Go to 'System', 'Administration', 'Software Sources'. 
On the 'Ubuntu Software' tab tick the multiverse and universe boxes.
Click 'Close'. It will ask you to reload/refresh; DO IT!

[SIZE="3"]_**Getting and Installing Java**_[/SIZE]
[SIZE="2"]_**Online Install**_[/SIZE]
Do this in a terminal for JRE (basically if you're not a java developer):
[LIST]
[*]sudo apt-get install sun-java6-jre sun-java6-plugin
[/LIST]
Do this in a terminal for JDK (basically if you ARE a java developer):
[LIST]
[*]sudo apt-get install sun-java6-jdk sun-java6-plugin
[/LIST]
[SIZE="2"]_**Offline Install**_[/SIZE]
This is actually the method used for reasons specific to me.
Just do this: [http://kzhvnkv.com/ubuntu-java-offline]("http://kzhvnkv.com/ubuntu-java-offline")


Say yes to whatever either method asks. If you are on a live CD or USB (even if it is Feisty 7.04, Gutsy 7.10, or Hardy 8.04 - I tried them all) you will probably get something like this:
> Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-00-2ubuntu2) | ia32-sun-java6-bin (= 6-00-2ubuntu2); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-plugin
 sun-java6-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)

[SIZE="3"]_**Fixing that Error**_[/SIZE]
Go into a terminal and do the following:
(Copy and paste using right-click so you don't get any of them wrong)
[LIST=1]
[*]```
sudo su
```
[*]```
LD_LIBRARY_PATH=CHANGEME dpkg --configure -a
```
-----The CHANGEME part should be changed to the location of libjli.so
-----Open your File System, go Ctrl+F, search for 'libjli'
-----Mine was in '/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jli'
----------so I used LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jli dpkg --configure -a
[*]```
ln -s / /cow
```
[*]Run whichever of these you used before again:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo apt-get install sun-java6-jdk sun-java6-plugin
```
-----Say yes to anything it asks.
-----It should work perfectly this time with no errors.
[/LIST]

[SIZE="3"]_**Verification of Success**_[/SIZE]
In a terminal type: 
```
java -version
```
Something like this should appear:
> 
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)


In firefox, where you would type a website type:
```
about:plugins
```
You should see something like this (you might have to scroll to find it):
> 
[SIZE="4"]Java(TM) Plug-in 1.6.0_06-b02[/SIZE]

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06
With a huge table underneath it.

Go to this website: [http://java.com/en/download/help/testvm.xml]("http://java.com/en/download/help/testvm.xml")

An applet will run near the bottom if you java is working correctly.

[SIZE="4"]_**Conclusion and Credits**_[/SIZE]
I have no idea why any of this is, so please don't reply here thinking that I know what I'm talking about. If you reply here with a problem, however, some other helpful soul might just come along.

I was only able to write this due to hours of research, eventually leading me to these three significant pages:
[http://ubuntuforums.org/archive/index.php/t-414851.html]("http://ubuntuforums.org/archive/index.php/t-414851.html")
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/103933]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/103933")
[http://ubuntuforums.org/showpost.php?p=1947183&postcount=12]("http://ubuntuforums.org/showpost.php?p=1947183&postcount=12")
So, for those pages and to the people on them, thank you.

I hope someone finds my tutorial useful.

aMeR1CaN_aUsSiE

---

### Post by xenolalia on 2008-08-02
Thank you so much!  Your HOWTO was very, very helpful!

---

### Post by aMeR1CaN_aUsSie on 2008-08-02
No problems xenolalia. Glad to help.

---

### Post by misiu_mp on 2008-08-19
Hm, i still have a problem:
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jli dpkg --configure -a
Setting up sun-java6-bin (6-06-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java6-bin (--configure):
...

As you see i added the path to libjava.so (/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386 in my case) and it still doesn't find it. Notice that it now does find the libjli.so library as it had trouble finding it before.

---

### Post by aMeR1CaN_aUsSie on 2008-08-19
Basically you didn't do steps 3 and 4.

Doing this:
```
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jli dpkg --configure -a
```
solves this problem:
> java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
but creates this problem:
> Setting up sun-java6-bin (6-06-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment. 

So run this command exactly (which it appears you did, but do it again anyway):
```
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jli dpkg --configure -a
```
[SIZE="5"][COLOR="Blue"]Then FROM THE SAME TERMINAL [COLOR="Red"]DO STEPS 3 AND 4[/COLOR] as I posted above.[/COLOR][/SIZE]

aMeR1CaN_aUsSiE

---

### Post by redy on 2008-10-08
Thank you very much.....

It works for me, and now i can playing my Dosbox Game Launcher :P

---

### Post by aMeR1CaN_aUsSie on 2008-10-11
No problems. Enjoy your Dosbox Game Launcher, whatever that is. =D

---

### Post by marmac on 2008-10-26
Thanks a lot very much!
it's working fine with me with: Ubuntu 8.04 on a WD Passport USB disk.

Bye Marco

---

### Post by jamesstansell on 2008-10-28
I think I've heard that these steps won't be needed for Intrepid (Ubuntu 8.10)  Can anyone confirm that?

---

### Post by linusr on 2008-10-29
Ubuntu 8.10 RC, did download & install openjdk fireox plugin

having said tht, couldn't find sun java plugin in synaptic though sun java 5/6 is available

---

### Post by setan_666 on 2009-08-26
I'm sory for asking this problem....
but i've try this,
```
root@devil-weapon:~# locate libjli
/home/devil/Desktop/SweetHome3D-2.0/jre1.6.0_14/lib/i386/jli/libjli.so
/usr/jre1.6.0_15/lib/i386/jli/libjli.so
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
/usr/lib/openoffice/basis3.0/program/libjli_g.so
```and then
```
root@devil-weapon:~# sudo LD_LIBRARY_PATH=/usr/jre1.6.0_15/lib/i386/jli dpkg --configure -a
root@devil-weapon:~# ln -s / /cow

```and testing, but the result is
```
root@devil-weapon:~# java -version
java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
```no idea for this..... :(

*using JauntyJackalope

please help me......

---

