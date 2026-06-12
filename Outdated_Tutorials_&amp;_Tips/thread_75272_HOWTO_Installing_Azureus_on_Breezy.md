---
title: "HOWTO: Installing Azureus on Breezy"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-13
**UPDATED! NO MORE RESIZING PROBLEMS**[B]
Part 1: Installing Azureus[/B]
Before anything make sure u **uncomment** the **universe** and **multiverse** repositories and add the following in in */etc/apt/sources.list*:
```
sudo gedit /etc/apt/sources.list
```
add at the end:
[PHP]deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free[/PHP]
followed by a 
```
sudo apt-get update
```
Do the following to install azureus:
```
sudo apt-get install sun-j2re1.5 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java
```
[PHP]wget http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-3_all.deb[/PHP]
```
sudo dpkg -i azureus_2.3.0.6-3_all.deb
```

Now set the correct java version by:
```
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
```

**Part 2: Running Azureus**

To make Azureus run smoothly on Breezy u need to make sure that the ports which are used by the torrents are open for file sharing. There are several ways to do this but the easiest way is the following:
first install firestarter (a GUI frontend to iptables firewall)
```
sudo apt-get install firestarter
```
now start firestarter from applications--> system tools
Remember that firestarter runs with sudo. To make firestarter run everytime when u log into GNOME, just add **gksudo firestarter** to System --> Preferences --> Sessions ---> Startup Programs.

alright now that firestarter is up, make sure its configured (first run) and go to edit -->preferences on the firestarter main window and in the Interfaces section check "Minimize to tray on window close".
now save and close the preferences window and look for the three tabs on the firestarter window, namely:**Status** , **Events** , **Policy**
Click on the **Policy** tab.
Click on the **white space** just below **Allow Service | Port | For**. This will activate **ADD Rule** at the top with a big blue PLUS sign. Click on that and choose the **name** of the service as **bittorrent** and the port for that service as 6881.
when u are done, click on **Add** and u are all set!!!
now start azureus and enjoy!!
U might want to remove this rule once u are done seeding or downloading.

---

### Post by zenwhen on 2005-10-13
Thanks for this post. It helped me a lot.

---

### Post by stoffepojken on 2005-10-13
Thank you very much! Worked like a charm :)

---

### Post by PiTT on 2005-10-13
Isn't JRE 1.5 or JDK 1.5 avaiable for breezy? I know it's avaiable for hoary, i have 1.5 installed right now...

---

### Post by arnieboy on 2005-10-13
[QUOTE=PiTT]Isn't JRE 1.5 or JDK 1.5 avaiable for breezy? I know it's avaiable for hoary, i have 1.5 installed right now...[/QUOTE]
breezy uses blackdown's version of jdk which hasnt released its 1.5 version yet.

---

### Post by manicka on 2005-10-14
Thanks for this one arnieboy, works without a hitch as usual :)

---

### Post by thnogueira on 2005-10-14
Maybe the hoary's version works on breezy? I've upgraded from hoary and [B]sun-j2re1.5
Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)[/B] still working here.

---

### Post by davebgimp on 2005-10-14
[QUOTE=arnieboy]Before anything make sure u **uncomment** the **universe** and **multiverse** repositories in */etc/apt/sources.list*
Do the following to install azureus:
```
sudo apt-get install j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java
```
[PHP]wget -c  http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.4-3_all.deb  [/PHP]
```
sudo dpkg -i azureus_2.3.0.4-3_all.deb
```
That should install azureus and get u all set.[/QUOTE]

I'm running Breezy and uncommenting the universe and multiverse sources only results in errors "Couldn't stat source package list", so I'm unable to get java as well as many other programs. I'm using the source list that came with the breezy CD, are they incorrect? This is what I've got:
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

Is there something wrong?

---

### Post by manicka on 2005-10-14
You need to refresh the repos

sudo apt-get update

---

### Post by manicka on 2005-10-14
I'd also comment out the backports repos for a while. They're not working yet.

---

### Post by davebgimp on 2005-10-14
Actually I looked again and noticed that the souces list you get from the CD install doesn't list the multiverse I added that, updated and so far everything is good. Thanks!

---

### Post by Syphin on 2005-10-14
Thanks, works great with my self-compiled jre1.5 :)

---

### Post by freakzilla on 2005-10-14
No problem with install but when i try to run azureus I get a segmentation fault.  Is this a problem related to my amd64 cpu?

---

### Post by Dillius on 2005-10-15
What are the lines you add in order to get Multiverse?

---

### Post by Syphin on 2005-10-15
[QUOTE=Dillius]What are the lines you add in order to get Multiverse?[/QUOTE]

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse

Thats the one I'm using, (change the us part)

---

### Post by clparker on 2005-10-15
Anybody know how to score JRE 1.5 ? Is that gonna be a pain in the ass too? will updating JRE mess w/ azereus?

---

### Post by Syphin on 2005-10-15
[QUOTE=clparker]Anybody know how to score JRE 1.5 ? Is that gonna be a pain in the ass too? will updating JRE mess w/ azereus?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=70428&highlight=fakeroot](http://ubuntuforums.org/showthread.php?t=70428&highlight=fakeroot)

Follow that howto and it should work.  just make sure ya have the multiverse repo added to the sources.list

After its installed, type in "sudo update-alternatives --config java" and have it point to the new one.  Works perfectly for me. :)

---

### Post by RedGhost on 2005-10-15
[QUOTE=davebgimp]I'm running Breezy and uncommenting the universe and multiverse sources only results in errors "Couldn't stat source package list", so I'm unable to get java as well as many other programs. I'm using the source list that came with the breezy CD, are they incorrect? This is what I've got:
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

Is there something wrong?[/QUOTE]

i had the same problem, comment backports (not ready) and add the multiverse lines

```

deb http://us.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy multiverse

```

also, worked great thanks

---

### Post by Nomearod on 2005-10-15
Thanks for the Howto. It really helped!

---

### Post by Samuel on 2005-10-15
thankyou, been messing with this for a while, added the 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy multiverse

and it worked fine, for some reason it wouldnt work with the gb (great britain?) links that was in my sources.list by default

---

### Post by dolny on 2005-10-15
Thank you for the short howto. 2.3.0.4 on board.

---

### Post by Syphin on 2005-10-15
anyone else having a problem, when you resize the window, all of the UI inside the window doesnt resize with it?  the windows smaller, but everything else stays in the position it was when the app was launched first. ><

---

### Post by pelago on 2005-10-15
Yes, I'm seeing the same resize problem. I didn't have this problem in hoary, but I think I was using Sun's 1.5, so maybe that will fix it. For the moment I'm using the 1.4 as described at the top of this thread.

---

### Post by Syphin on 2005-10-15
Well i am using 1.5, and did in hoary also and didnt have this prob. :(

---

### Post by xalphas on 2005-10-15
Older way

[http://www.ubuntuforums.org/showpost.php?p=414757&postcount=16](http://www.ubuntuforums.org/showpost.php?p=414757&postcount=16)

---

### Post by Syphin on 2005-10-16
Thanks xalphas, that fixed the UI problem i was having. But with that you need to chmod the directorys right to be able to update and what-not.

I think the orig problem with the GUI and the method the poster used, is a problem with gtk not working right in it, cause i tried it with both java versions just incase, but no go.. :(

---

### Post by bionnaki on 2005-10-16
I am getting this error:

> bill@ubuntu:~$ sudo apt-get install j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java
Reading package lists... Done
Building dependency tree... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate
bill@ubuntu:~$


any ideas?

---

### Post by zerooo on 2005-10-16
working for me, thx for a nice how to.

---

### Post by bionnaki on 2005-10-16
still getting the error - no idea why....

---

### Post by bionnaki on 2005-10-16
here is my sources.list - am I missing anything?

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe



---

### Post by manicka on 2005-10-16
[QUOTE=bionnaki]here is my sources.list - am I missing anything?[/QUOTE]

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by atomicrod on 2005-10-16
I installed Azureus as outlined and the program starts with the following error.

ava.lang.ClassNotFoundException: org.gudy.azureus2.update.UpdaterPatcher not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/swt-gtk-3.1.jar,file:./,file:/usr/share/java/Azureus2.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(java.io.File) (Unknown Source)
   at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(java.io.File, int, int) (Unknown Source)
   at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(com.aelitis.azureus.core.AzureusCore) (Unknown Source)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.start() (Unknown Source)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run() (Unknown Source)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AERunnable.run() (Unknown Source)
   at java.lang.Thread.run() (/usr/lib/libgcj.so.6.0.0)

The program then starts normally, but when I attempt to downlad a torrent nothing seems to happen.  I have seeds and peers showing, but I get a red status saying not connected to any peer to download.

I am behind a smoothwall box, but I forwared port 6881 and pass the nat test.

Gnome Torrent works fine as an alternative, but I'd really like to use Azureus.  If anyone has some suggestions I'd be thankful.

---

### Post by chajuram on 2005-10-19
Wonderful,

Thanks.

---

### Post by RezDawg on 2005-10-19
Thanks this worked perfect.

---

### Post by Pumpino on 2005-10-25
If I search for Azureus in Synaptic, it's not listed.  I have all the mirrors enabled, as well as the backports mirrors.  Do I need to download the deb from somewhere else?  I had no trouble getting it when I used Hoary.  Thanks.

---

### Post by matthias_k on 2005-10-25
**Question:**
If I select to install the packages you listed, aptitude wants to remove everything related to the Eclipse IDE. How come?

> matthias:~$ sudo aptitude install j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:
  libswt-gtk-3.1-jni
The following packages will be automatically REMOVED:
  eclipse-jdt eclipse-jdt-common eclipse-pde eclipse-pde-common
  eclipse-platform eclipse-platform-common eclipse-rcp eclipse-sdk
  libswt3.1-gtk-java libswt3.1-gtk-jni
The following NEW packages will be installed:
  j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java
  libswt-gtk-3.1-java libswt-gtk-3.1-jni
The following packages will be REMOVED:
  eclipse-jdt eclipse-jdt-common eclipse-pde eclipse-pde-common
  eclipse-platform eclipse-platform-common eclipse-rcp eclipse-sdk
  libswt3.1-gtk-java libswt3.1-gtk-jni
0 packages upgraded, 6 newly installed, 10 to remove and 0 not upgraded.
Need to get 24.3MB of archives. After unpacking 8589kB will be used.
Do you want to continue? [Y/n/?] n
Abort.


---

### Post by matthias_k on 2005-10-25
Hmmm, okay, I just removed Eclipse for now (for whatever reason apt decided to do so) and followed your instructions.

After Azureus throwing errors at me because I'm not using Java5 (and crashing), I just restarted it and updated the Updater, and then it seemed to work.

However, I can't resize the window lol! Whenever I issue a resize, only the window itself will resize, but not the canvas (which is effectively pretty useless). Did you also notice that? Maybe it's because this strange non-Sun Java implementation coming with Breezy is not so good afterall for running Azureus? ^^

Are there any Ubuntu repos for installing Sun's Java 5 RE? I actually don't give a sh** if it's under their non-free license or not, I just want a working Java5 platform on my system. I need Java5 for university work anyway.

---

### Post by ming0 on 2005-10-25
same problem here--the windows aren't being redrawn properly :(

---

### Post by Roybotnik on 2005-10-25
I have the same problem with the window not resizing =c.

---

### Post by matthias_k on 2005-10-26
I guess it's a bug in the SWT library coming with the Blackdown Java implementation. It's the only library I could track down which does not come from Sun's Java5 implementation which I managed to install yesterday evening (I found a very good tutorial on the German Ubuntu forums how to install Java5, maybe it's around here somewhere, too).

The window fails to redraw an invalidated area, this means it's almost certainly a problem with the underlying windowing toolkit (in this case, Java Swing).
Does anyone know whether libswt-3.1-java is a Blackdown library, and how the equivalent official library from Sun is called? I noticed that the script loading Azureus includes the location to this library.

---

### Post by bete on 2005-10-26
When installing i get this error message :

> Error loading speedbar... ignored.
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-opt.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/eieio/eieio-speedbar.el:
  !! Wrong type argument ((stringp nil))
Done
emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Setting up j2re1.4 (1.4.2.02-1ubuntu3) ...

Setting up libcommons-cli-java (1.0-6) ...
Setting up liblog4j1.2-java (1.2.9-1ubuntu4) ...
Setting up libseda-java (3.0-2) ...
Setting up libswt-gtk-3.1-jni (3.1-2ubuntu1) ...
Setting up libswt-gtk-3.1-java (3.1-2ubuntu1) ...

Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)


Should i just ignore this or ?

---

### Post by matthias_k on 2005-10-26
That doesn't look as if it has anything to do with Azureus or the libraries you installed to run it. The errors are related o the emacs text editor; maybe you still had an emacs installation scheduled or so, try asking in another thread because this seems to be off-topic here.

---

### Post by [censored] on 2005-10-27
Followed the HOWTO to the letter. Now if I try:

> 
user@ubuntu:~/downloads/debs$ azureus
/usr/bin/azureus: line 5: exec: java: not found
user@ubuntu:~/downloads/debs$ java
bash: /usr/bin/java: No such file or directory
user@ubuntu:~/downloads/debs$


Everything's installed, as per recommendations, but it's still not working. What does this mean?

---

### Post by arnieboy on 2005-10-27
[QUOTE='[censored]']Followed the HOWTO to the letter. Now if I try:


EDIT: 
damn am sorry.. posted the wrong answer.
please do the following:
```
sudo apt-get remove j2re1.4
```
then download and install and run automatix:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by [censored] on 2005-10-28
arnieboy,

did that.

removed jre1.4 as you suggested. Downloaded and installed automatix, and got it to re install jre1.4 as (I presume) you were intimating, along with the version of azureus that was in the package.

now this what happens when I launch azureus:

 > 
user@ubuntu:~$ azureus
/usr/bin/azureus: line 5: exec: java: not found
user@ubuntu:~$ dpkg -l |grep j2re
rc  j2re1.4                                             1.4.2.02-1ubuntu3              Blackdown Java(TM) 2 Runtime Environment, St
ii  sun-j2re1.5                                         1.5.0+update05              Java(TM) 2 RE, Standard Edition, Sun Microsy


Obviously, I need to set up the path and environment variables for java. Does anybody know of a decent ubuntu-compatible howto on this?

---

### Post by djpeanut on 2005-11-02
It worked after I manually added the multiverse repositories, but I get this error when starting Azureus:

```
java.lang.ClassNotFoundException: org.gudy.azureus2.update.UpdaterPatcher
	at java.net.URLClassLoader$1.run(URLClassLoader.java:199)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:684)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:403)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:322)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:156)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run(Initializer.java:270)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport(SWTThread.java:107)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at java.lang.Thread.run(Thread.java:534)
```

Any ideas?

---

### Post by arnieboy on 2005-11-02
[QUOTE=matthias_k]I guess it's a bug in the SWT library coming with the Blackdown Java implementation. It's the only library I could track down which does not come from Sun's Java5 implementation which I managed to install yesterday evening (I found a very good tutorial on the German Ubuntu forums how to install Java5, maybe it's around here somewhere, too).

The window fails to redraw an invalidated area, this means it's almost certainly a problem with the underlying windowing toolkit (in this case, Java Swing).
Does anyone know whether libswt-3.1-java is a Blackdown library, and how the equivalent official library from Sun is called? I noticed that the script loading Azureus includes the location to this library.[/QUOTE]
alright herez the solution guys:
do a 
```
sudo apt-get remove j2re1.4
```
now do
```
sudo gedit /etc/apt/sources.list
```
and add the following lines at the end:
> deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
now do the following:
```
sudo apt-get update
sudo apt-get install sun-j2re1.5
```
and then run azureus

---

### Post by dolny on 2005-11-02
```
mrplant@milkshake:~$ azureus 
DEBUG::Thu Nov 03 01:14:27 GMT+01:00 2005 
  java.lang.ClassNotFoundException: com.sun.net.ssl.internal.ssl.Provider not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/swt-gtk-3.1.jar,file:./,file:Azureus2.jar,file:/usr/share/java/Azureus2.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}} 
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0) 
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0) 
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Unknown Source) 
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknown Source) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source) 
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source) 
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0) 
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0) 

DEBUG::Thu Nov 03 01:14:28 GMT+01:00 2005 
  java.security.KeyStoreException: JKS 
   at java.security.KeyStore.getInstance(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists(java.lang.String) (Unknown Source) 
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Unknown Source) 
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknown Source) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source) 
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source) 
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0) 
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0) 

DEBUG::Thu Nov 03 01:14:28 GMT+01:00 2005 
  java.security.KeyStoreException: JKS 
   at java.security.KeyStore.getInstance(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists(java.lang.String) (Unknown Source) 
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise() (Unknown Source) 
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance() (Unknown Source) 
   at org.gudy.azureus2.core3.config.COConfigurationManager.initialise() (Unknown Source) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source) 
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source) 
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0) 
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0) 

DEBUG::Thu Nov 03 01:14:30 GMT+01:00 2005::com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector::start()::-1: 
    IncomingSocketChannelManager::start()::-1,IncomingSocketChannelManager::IncomingSocketChannelManager()::-1,NetworkManager::NetworkManager()::-1,NetworkManager::<clinit>()::-1,Class::initializeClass()::-1,AzureusCoreImpl::AzureusCoreImpl()::-1,AzureusCoreImpl::create()::-1,AzureusCoreFactory::create()::-1,Main::Main(java.lang.String[])::-1,Main::main(java.lang.String[])::-1,MainThread::call_main()::-1,MainThread::run()::-1 
java.net.BindException: Adres jest juÅ¼ w uÅ¼yciu 
   at gnu.java.net.PlainSocketImpl.bind(java.net.InetAddress, int) (/usr/lib/libgcj.so.6.0.0) 
   at java.net.ServerSocket.bind(java.net.SocketAddress, int) (/usr/lib/libgcj.so.6.0.0) 
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.start() (Unknown Source) 
   at com.aelitis.azureus.core.networkmanager.impl.IncomingSocketChannelManager.start() (Unknown Source) 
   at com.aelitis.azureus.core.networkmanager.impl.IncomingSocketChannelManager.IncomingSocketChannelManager() (Unknown Source) 
   at com.aelitis.azureus.core.networkmanager.NetworkManager.NetworkManager() (Unknown Source) 
   at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>() (Unknown Source) 
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.AzureusCoreImpl() (Unknown Source) 
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create() (Unknown Source) 
   at com.aelitis.azureus.core.AzureusCoreFactory.create() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.Main(java.lang.String[]) (Unknown Source) 
   at org.gudy.azureus2.ui.swt.Main.main(java.lang.String[]) (Unknown Source) 
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0) 
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0) 
DEBUG::Thu Nov 03 01:14:47 GMT+01:00 2005 
  java.io.FileNotFoundException: /Azureus2.jar (Nie ma takiego pliku ani katalogu) 
   at gnu.java.nio.channels.FileChannelImpl.open(java.lang.String, int) (/usr/lib/libgcj.so.6.0.0) 
   at gnu.java.nio.channels.FileChannelImpl.FileChannelImpl(java.lang.String, int) (/usr/lib/libgcj.so.6.0.0) 
   at java.io.RandomAccessFile.RandomAccessFile(java.lang.String, java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
   at java.io.RandomAccessFile.RandomAccessFile(java.io.File, java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
   at java.util.zip.ZipFile.ZipFile(java.io.File) (/usr/lib/libgcj.so.6.0.0) 
   at java.util.jar.JarFile.JarFile(java.io.File, boolean) (/usr/lib/libgcj.so.6.0.0) 
   at java.util.jar.JarFile.JarFile(java.io.File) (/usr/lib/libgcj.so.6.0.0) 
   at org.gudy.azureus2.core3.internat.MessageText.getLocales() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.mainwindow.StartupUtils.setLocale() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport() (Unknown Source) 
   at org.gudy.azureus2.core3.util.AERunnable.run() (Unknown Source) 
   at java.lang.Thread.run() (/usr/lib/libgcj.so.6.0.0) 

DEBUG::Thu Nov 03 01:14:47 GMT+01:00 2005 
  java.lang.NullPointerException 
   at java.util.Arrays$ArrayList.Arrays$ArrayList(java.lang.Object[]) (/usr/lib/libgcj.so.6.0.0) 
   at java.util.Arrays.asList(java.lang.Object[]) (/usr/lib/libgcj.so.6.0.0) 
   at org.gudy.azureus2.core3.internat.MessageText.getLocales() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.mainwindow.StartupUtils.setLocale() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run() (Unknown Source) 
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport() (Unknown Source) 
   at org.gudy.azureus2.core3.util.AERunnable.run() (Unknown Source) 
   at java.lang.Thread.run() (/usr/lib/libgcj.so.6.0.0)
```

What can i do :( ?

---

### Post by thomax on 2005-11-03
Here is my sources.list, with extras and working backports, have a look at it, it works fine ;)

You just need to change the cdrom part ;)

```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## BREEZY
deb http://be.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## BREEZY-UPDATES
deb http://be.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## BREEZY-UPDATES ftp.rz.tu-bs.de
deb http://ftp.rz.tu-bs.de/pub/mirror/ubuntu-packages/ breezy-updates main universe multiverse restricted
deb-src http://ftp.rz.tu-bs.de/pub/mirror/ubuntu-packages/ breezy-updates main universe multiverse restricted

## BREEZY-SECURITY
deb http://be.archive.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

## BACKPORTS ubuntu-backports.mirrormax.net
deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main universe multiverse restricted

## BACKPORTS ftp2.caliu.info
deb ftp://ftp2.caliu.info/backports/ breezy-backports-staging main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ breezy-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ breezy-extras-staging main universe multiverse restricted

## BREEZY BREEZY-UPDATES BREEZY-SECURITY search.belnet.be
deb http://search.belnet.be/packages/ubuntu/ubuntu/ breezy main universe multiverse restricted
deb http://search.belnet.be/packages/ubuntu/ubuntu/ breezy-updates main universe multiverse restricted
deb http://search.belnet.be/packages/ubuntu/ubuntu/ breezy-security main universe multiverse restricted

deb-src http://search.belnet.be/packages/ubuntu/ubuntu/ breezy main universe multiverse restricted
deb-src http://search.belnet.be/packages/ubuntu/ubuntu/ breezy-updates main universe multiverse restricted
deb-src http://search.belnet.be/packages/ubuntu/ubuntu/ breezy-security main universe multiverse restricted

## BREEZY BREEZY-UPDATES BREEZY-SECURITY godel.cs.bilgi.edu.tr
deb http://godel.cs.bilgi.edu.tr/mirror/ubuntu/ breezy main universe multiverse restricted
deb http://godel.cs.bilgi.edu.tr/mirror/ubuntu/ breezy-updates main universe multiverse restricted
deb http://godel.cs.bilgi.edu.tr/mirror/ubuntu/ breezy-security main universe multiverse restricted

deb-src http://godel.cs.bilgi.edu.tr/mirror/ubuntu/ breezy main universe multiverse restricted
deb-src http://godel.cs.bilgi.edu.tr/mirror/ubuntu/ breezy-updates main universe multiverse restricted
deb-src http://godel.cs.bilgi.edu.tr/mirror/ubuntu/ breezy-security main universe multiverse restricted

## Wine
deb http://wine.sourceforge.net/apt/ breezy/

## LEGALLY QUESTIONABLE antesis.freecontrib.org java divx etc.
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free

deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free

## LEGALLY QUESTIONABLE DVDCSS/xvid/other legally questionable packages
# deb ftp://ftp.nerim.net/debian-marillat/ sarge main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb ftp://ftp.nerim.net/debian-marillat/ etch main

## MPlayer
# deb http://sh.nu/~crimsun/ ./

```

---

### Post by Dotrig on 2005-11-03
Nice :cool: now need i not to use bittornado as not downloading maps :P

---

### Post by MirSPCM on 2005-11-03
> **thomax]Here is my sources.list, with extras and working backports, have a look at it, it works fine  said:**
> / breezy 
## LEGALLY QUESTIONABLE antesis.freecontrib.org java divx etc.
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free

deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free

## LEGALLY QUESTIONABLE DVDCSS/xvid/other legally questionable packages
# deb ftp://ftp.nerim.net/debian-marillat/ sarge main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb ftp://ftp.nerim.net/debian-marillat/ etch main


```


Oh My GOD !

```

## LEGALLY QUESTIONABLE DVDCSS/xvid/other legally questionable packages
# deb ftp://ftp.nerim.net/debian-marillat/ sarge main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb ftp://ftp.nerim.net/debian-marillat/ etch main

```


libdvdcss2 is provided by plf. then this is marillat wich is for debian and is dangerous to use on ubuntu. Then you use qarg sid and etch at the same time .. none sense.
However it's all commented so not activated I suppose you activate it only when needded then. Well be carefull on giveing this to people who don't know what this is .. they can break their stuff thanks to this :-(

```

deb http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free

```
devnotpublic stands for in DEVELOPPEMENT NOT FOR PUBLIC
This rep contains package that can break your distro, it's for plf project testers and devs only.



Please don't advice anybody one useing this list it's dangerous for them.
(You should remove devnotpublic too unless you're plf tester)


Thank you

---

### Post by keyes on 2005-11-03
I agree !!!

Please don't use devnotpublic if you are not a PLF tester. You must read the PLF mailing list to use this repository.
Stuffs are not tested in this repository and anybody can publish a package who make "rm -Rf /"!!!
This can break your system, destroy your data, ...
We remove packages from devnotpublic and publish it to the main repositories when tested!

However we need testers! You are welcomed to join the PLF, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf) (yes this is the Ubuntu-fr Wiki but this page is in English) and join our mailing list.

Thanks.

---

### Post by djlosch on 2005-11-03
> 
~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-j2re1.5: Depends: libasound2 (> 1.0.9) but 1.0.8-1 is to be installed
               Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
E: Broken packages


wtf?  i have both of them....

---

### Post by dolny on 2005-11-04
Edited.

Azureus works now (I downloaded it from official site) - but is veryyyyyyyy slowwww :( (and it doesn't download anything :/ ehhh)

---

### Post by iluminate on 2005-11-04
Had the same problems that everything went really slow, and Azureus behaved VERY buggy.
So I:
1.Uninstalled Azureus.
2.Uninstalled SunJava
And then started all over again. Like magic it works just fine now.
Still having problems with the resize of the window, but hey at least things do work now.
Also don't forgett to "sudo update-alternatives --config java" and then chose the Sun Version.
Then start Azureus.
Before the uninstallation I  got an error message from Azureus saying somthing about "azupdater package not found". Now everything works great...

Cheers

---

### Post by dronug on 2005-11-07
when i enter the command

 sudo apt-get install sun-j2re1.5 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

i get          libcommons-cli-java is already the newest version.
liblog4j1.2-java is already the newest version.
Package libseda-java is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libseda-java has no installation candidate

---

### Post by XDevHald on 2005-11-07
This application works really well in Dapper Drake, but others might experience it differently in Breezy. Solution to that issue is beyond me, I'll check as to why and post a reply back later.

---

### Post by The Warlock on 2005-11-07
May I ask why, exactly, libswt-gtk-3.1-jni conflicts with the Eclipse suite?

---

### Post by arnieboy on 2005-11-09
I have completely rewritten the first post! check it out and make azureus rock! make sure u have all the universe and multiverse repos enabled though. if u dont know what am saying, do the following:
```
sudo gedit /etc/apt/sources.list 
```
and make sure there is no **#** symbol before the universe and multiverse repos

---

### Post by matthias_k on 2005-11-09
Thanks, one thing though:

I think you really should remove the part about firestarter, it's misleading and doesn't belong there (**EDIT**: It's also wrong, see post below). First, it sounds as if one would need firestarter (read: iptables) for Azureus to work (which is of course not true) and second it might even be a bad idea to install it when you're behind a router which already does NAT and IP filtering.

It just hasn't anything to do with Azureus unless you already have iptables installed and set up, in which case one can assume that he/she is already familiar with package filtering and doesn't need this information.

---

### Post by matthias_k on 2005-11-09
On top of that, Azureus (unlike most other BT clients) only binds to TCP port 6881, so opening 6882 to 6889 is useless and an unnecessary security risk (unless you're using another BT client additionally to Azureus which binds to these ports).

---

### Post by arnieboy on 2005-11-09
[QUOTE=matthias_k]Thanks, one thing though:

I think you really should remove the part about firestarter, it's misleading and doesn't belong there. First, it sounds as if one would need firestarter (read: iptables) for Azureus to work (which is of course not true) and second it might even be a bad idea to install it when you're behind a router which already does NAT and IP filtering.

It just hasn't anything to do with Azureus unless you already have iptables installed and set up, in which case one can assume that he/she is already familiar with package filtering and doesn't need this information.[/QUOTE]
iptables is installed by default on ubuntu breezy and most other distros and having firestarter to actually see whats happening is actually a very good idea. u cud also selectively open the ports which are required for sharing torrent files and do it in a manner less complicated than editing iptables. I dont think addition of the firestarter part is irrelevant.

---

### Post by arnieboy on 2005-11-09
[QUOTE=matthias_k]On top of that, Azureus (unlike most other BT clients) only binds to TCP port 6881, so opening 6882 to 6889 is useless and an unnecessary security risk (unless you're using another BT client additionally to Azureus which binds to these ports).[/QUOTE]
great! then select which port u want to open and keep the others closed!

---

### Post by matthias_k on 2005-11-09
[QUOTE=arnieboy]iptables is installed by default on ubuntu breezy and most other distros and having firestarter to actually see whats happening is actually a very good idea. u cud also selectively open the ports which are required for sharing torrent files and do it in a manner less complicated than editing iptables. I dont think addition of the firestarter part is irrelevant.[/QUOTE]
Installed, yes, but no chains or filters are set up. If that part is to stay, you should at least say that it's:
a) Not necessary to run Azureus (though may be helpful)
b) Definitely unnecessary (or even bad) when behind a router

> great! then select which port u want to open and keep the others closed!
Yes, that was my point. Your post doesn't mention that though.

---

### Post by sevenrechlin on 2005-11-09
Ok I tried to do this, and it was downloading fine, but after downloading the terminal spat out a ton of parse errors and then turned into some sort of code.  Now it's just waiting for input in it's weird code.

NM Got it, was a problem with not doing Java correctly :)

---

### Post by arnieboy on 2005-11-09
[QUOTE=sevenrechlin]Ok I tried to do this, and it was downloading fine, but after downloading the terminal spat out a ton of parse errors and then turned into some sort of code.  Now it's just waiting for input in it's weird code.[/QUOTE]
anything weird cannot be magically deciphered at this end unless its reported as is. depends of course on whether u want the problem solved or not in the first place.

---

### Post by bejinxed on 2005-11-10
Thank you.  Got Azureus working except for the window draw resize bug other people have listed above, so Im happy.

---

### Post by skatedawe on 2005-11-11
Thx for the guide! :))
 
 Firestart did it, i couldnt get up the ports even with manually upset the settings in the hardware router.

---

### Post by ollesbrorsa on 2005-11-11
Does anybody else get 404 errors accessing the plf repos?

```

snip

Err http://antesis.freecontrib.org breezy/free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/free Sources
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Sources
  404 Not Found

Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz  404 Not Found

/snip

```

Br,
ollesbrorsa

---

### Post by arnieboy on 2005-11-11
[QUOTE=ollesbrorsa]Does anybody else get 404 errors accessing the plf repos?

```

snip

Err http://antesis.freecontrib.org breezy/free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/free Sources
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Sources
  404 Not Found

Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz  404 Not Found

/snip

```

Br,
ollesbrorsa[/QUOTE]
the plf repos are currently down.
thats why u are getting a 404 from [http://antesis.freecontrib.org/mirrors/ubuntu/](http://antesis.freecontrib.org/mirrors/ubuntu/)

---

### Post by ollesbrorsa on 2005-11-11
[QUOTE=arnieboy]the plf repos are currently down.
thats why u are getting a 404 from [http://antesis.freecontrib.org/mirrors/ubuntu/](http://antesis.freecontrib.org/mirrors/ubuntu/)[/QUOTE]

Any idea when they'll be back up?
Have recently upgraded, the CD way, to breezy and I'm trying to get back on track with all the usual programs... ;) 

Br,
ollesbrorsa

---

### Post by arnieboy on 2005-11-11
[QUOTE=ollesbrorsa]Any idea when they'll be back up?
Have recently upgraded, the CD way, to breezy and I'm trying to get back on track with all the usual programs... ;) 

Br,
ollesbrorsa[/QUOTE]
I am not involved with the plf project, hence I cant give u a heads up on that. we will have to wait and watch. in the meanwhile u can try and mail keyes (the maker of easy ubuntu) to ask him if he knows anything.

---

### Post by bored2k on 2005-11-17
I tend to forget, why the extra
libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java
packages? I know libswt supposedly gives you a speed boost, but I never felt it.

---

### Post by arnieboy on 2005-11-17
[QUOTE=bored2k]I tend to forget, why the extra
libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java
packages? I know libswt supposedly gives you a speed boost, but I never felt it.[/QUOTE]
cuz the debian version of 2.3 depends on them and thats what gets installed here. thats not the case with version 2.2 however.

---

### Post by souled on 2005-11-20
So is there an alternative way to get the packages we need from [http://antesis.freecontrib.org/mirrors/ubuntu/](http://antesis.freecontrib.org/mirrors/ubuntu/) ?

---

### Post by arnieboy on 2005-11-20
[QUOTE=souled]So is there an alternative way to get the packages we need from [http://antesis.freecontrib.org/mirrors/ubuntu/](http://antesis.freecontrib.org/mirrors/ubuntu/) ?[/QUOTE]
open /etc/apt/sources.list
and delete the antesis.freecontrib.org lines and replace them with the following:
[HTML]deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free[/HTML]

---

### Post by souled on 2005-11-21
Ahh, thank you.

Edit: I installed all the packages, but when I put in the command to update java, I don't get a choice on which one to choose. The output is just ```
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.
``` Is this right? When I run Azureus, the window still doesn't resize when I change the geometry...

---

### Post by thermopyl on 2005-11-21
DOH!

Followed the instructions...how do i run azureus as it is not in my menus???:???: 

ta

---

### Post by arnieboy on 2005-11-22
[QUOTE=souled]Ahh, thank you.

Edit: I installed all the packages, but when I put in the command to update java, I don't get a choice on which one to choose. The output is just ```
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.
``` Is this right? When I run Azureus, the window still doesn't resize when I change the geometry...[/QUOTE]
sorry those lines abt choosing remained even after I edited this howto some time back. when u use "set" with update-alternatives it doesnt ask u to choose your java version but just sets your java path to the one in the argument. that was the intention of the edit: to make this howto one step shorter.. but i forgot to delete the older lines. anyway now its been edited again. thanks.

---

### Post by arnieboy on 2005-11-22
[QUOTE=thermopyl]DOH!

Followed the instructions...how do i run azureus as it is not in my menus???:???: 

ta[/QUOTE]
should be in Applications -->Internet
if its not, then try running azureus from terminal by typing:
```
azureus
```

---

### Post by zerwas on 2005-11-27
Hi,

Thank you **very much** for your Howto and your work on Ubuntu :)

I only wanted to mention that this also works fine with
[http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.***_[COLOR="Red"][SIZE="5"]6[/SIZE][/COLOR]_***-1_all.deb]("http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb")

---

### Post by psoleko on 2005-11-27
[QUOTE=zerwas]Hi,

Thank you **very much** for your Howto and your work on Ubuntu :)

I only wanted to mention that this also works fine with
[http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.***_[COLOR="Red"][SIZE="5"]6[/SIZE][/COLOR]_***-1_all.deb]("http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb")[/QUOTE]
Thanks for that zerwas was having some problems updating Azureus

---

### Post by arnieboy on 2005-11-27
the plf mirrors also host a debian package of azureus (not native ubuntu version). I havent checked in a while though whether the plf guys have updated this package to the latest..

---

### Post by Technoviking on 2005-11-27
I have built a new Azureus package under Ubuntu, will try to upload it to my web site later.

Mike

---

### Post by skeezer65134 on 2005-12-01
Thank you SO much for this. The directions for adding backport and extras repositories for Ubuntu is outdated and I can never get the repositories to work right (they are always Ign instead of Get).

Got Azereus running now and it's all good. Now to figure out this Kaffine player and the w32codecs.....

Thanks again!

---

### Post by arnieboy on 2005-12-01
[QUOTE=skeezer65134]Thank you SO much for this. The directions for adding backport and extras repositories for Ubuntu is outdated and I can never get the repositories to work right (they are always Ign instead of Get).

Got Azereus running now and it's all good. Now to figure out this Kaffine player and the w32codecs.....

Thanks again![/QUOTE]
since u have the plf repos added just do:
```
sudo apt-get install w32codecs
```
and it will get installed.

---

### Post by Danielle on 2005-12-03
[QUOTE=arnieboy]. Click on that and choose the **name** of the service as bitorrent and the ports for that service (6881-6889) will get automatically selected.
[/QUOTE]
you spelt Bittorrent incorrectly - the ports won't be automatically selected if you are lazy like me a copied and pasted it into firestarer from your guide. 

thanks for the help O:)

---

### Post by ubuntu_demon on 2005-12-03
azureus_2.3.0.6-1_all.deb is available. This deb should be used instead of the older one.

```

$wget http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb

```

PS :
using the -c option of wget makes no sense since this resumes prior downloads. From the man page :

> 
..........  -c only affects resumption of downloads started prior to this
           invocation of Wget, and whose local files are still sitting around.


---

### Post by Danielle on 2005-12-03
hey, where did it go :confused: i installed azureus_2.3.0.6-1 over the top of 2.3.0.6 but when i open it it's still 2.3.0.6. do i have to reboot for it to take effect?

---

### Post by Danielle on 2005-12-03
i fixed it :)

---

### Post by skeezer65134 on 2005-12-03
[QUOTE=arnieboy]since u have the plf repos added just do:
```
sudo apt-get install w32codecs
```
and it will get installed.[/QUOTE]
Already took care of this. I need to install the xine engine too, but it worked out well. Actually, I did it only a few minutes after posting. That repo is quite useful, thanks again!

---

### Post by arnieboy on 2005-12-03
[QUOTE=ubuntu_demon]azureus_2.3.0.6-1_all.deb is available. This deb should be used instead of the older one.

```

$wget http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb

```

PS :
using the -c option of wget makes no sense since this resumes prior downloads. From the man page :[/QUOTE]
thanks for the update. first post updated.

---

### Post by yorick on 2005-12-08
Sorry to bother you Arnieboy, but I noticed an inconsitency in your first post. After you wget the 2.3.0.6 version of Azureus, the following dpkg line still reffers to the 2.3.0.4 version.

---

### Post by arnieboy on 2005-12-08
[QUOTE=yorick]Sorry to bother you Arnieboy, but I noticed an inconsitency in your first post. After you wget the 2.3.0.6 version of Azureus, the following dpkg line still reffers to the 2.3.0.4 version.[/QUOTE]
thanks. updated.

---

### Post by LucidParody on 2005-12-09
hi, i was able to install azureus and firestarter just fine -- but azureus won't connect to a single peer or seed.  my router is set up properly for port forwarding and i'm sure i followed these directions to a tee...any ideas why this is happening?

---

### Post by thecrust on 2005-12-09
This is an informative thread so I thought you guys might have some idea of what is going on, here's my problem.

Azureus opens extremely slowly it takes a few minutes to open.  After the splash screen and drawing the display window the processor usage jumps to the maximum. (~80% user, ~20% system stuff)

I have installed the Sun's newest java.
java -version gives me:

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

I installed azureus 2.3.0.6 using the instructions given on the first post of this thread.  This '100%' cpu hog problem happens with no torrents running and with one torrent running.

Any ideas?

---

### Post by arnieboy on 2005-12-09
[QUOTE=thecrust]This is an informative thread so I thought you guys might have some idea of what is going on, here's my problem.

Azureus opens extremely slowly it takes a few minutes to open.  After the splash screen and drawing the display window the processor usage jumps to the maximum. (~80% user, ~20% system stuff)

I have installed the Sun's newest java.
java -version gives me:

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

I installed azureus 2.3.0.6 using the instructions given on the first post of this thread.  This '100%' cpu hog problem happens with no torrents running and with one torrent running.

Any ideas?[/QUOTE]
azureus is a confirmed resource hog. if u want somethign lighter try the gnome bittorrent client.. but its severely lacking in options.

---

### Post by thecrust on 2005-12-09
Just an update to my issue, when I run azureus with: gksudo azureus

The debug output streams this NULL Pointer exception over and over.
```
DEBUG::Fri Dec 09 20:25:25 CST 2005
  java.lang.NullPointerException
        at org.gudy.azureus2.ui.swt.StartServer.pollForConnectionsSupport(StartServer.java:99)
        at org.gudy.azureus2.ui.swt.StartServer.access$000(StartServer.java:28)
        at org.gudy.azureus2.ui.swt.StartServer$2.runSupport(StartServer.java:82)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:64)
```

I realize that azureus is hard on the RAM and CPU, but I had a copy running earilier on this hardware with Ubuntu as well as Windows XP and both did not hog the CPU constantly.   Currently azureus is hogging the processor even when it is not dealing with any torrents.

Thanks for your time.
Cheers

---

### Post by Aeon17x on 2005-12-18
It works, even if you don't include the additional repos. Just make sure you already have Sun Java and the universe/multiverse repositories so that when you install Azureus, Synaptic will just fill in the missing dependencies. :)

---

### Post by kurokikaze on 2005-12-28
Does anyone know if this how-to works for AMD64 ubuntu too?

---

### Post by Mosey on 2005-12-29
No matter what ports I try and test...i've tried twenty-six already...I always get a NAT ERROR...

What do I need to do? I'm testing ports i've enabled in firestarter!

*Hmmph*

---

### Post by Rory on 2005-12-31
Arnieboy,

Thanks for the Azureus install instructions.  Question:

I installed sun-j2re1.5 from plf and then installed the same azureus package you note from the debian repos.  Everything works fine.  I didn't have to do anything else.

I never installed, as installing sun-j2re1.5 seemed to install them:
sudo apt-get install libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

And I never did:
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java

And I never installed firestarter.

Are these things really necessary?  

Could the instructions instead say:
```
sudo apt-get install sun-j2re1.5
```

```
wget http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb 
```

```
sudo dpkg -i azureus_2.3.0.6-1_all.deb
```

---

### Post by Rory on 2005-12-31
There's also this second method, found on the new Breezy Ubuntu Guide, that will install the tarball straight from sourceforge.
[http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29.3F](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29.3F)

```

sudo apt-get install sun-j2re1.5  (must have PLF repo added for this)

wget -c [http://heanet.dl.sourceforge.net/sourceforge/azureus/Azureus_2.3.0.6_linux.tar.bz2](http://heanet.dl.sourceforge.net/sourceforge/azureus/Azureus_2.3.0.6_linux.tar.bz2)

sudo tar jxvf Azureus_2.3.0.6_linux.tar.bz2 -C /opt

sudo gedit /usr/share/applications/azureus.desktop 

```
    * Add the following to the new file: 
[Desktop Entry] 
Name=Azureus
Comment=A Bittorrent client
Exec=/opt/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

---

### Post by L33tZ on 2005-12-31
This method works great! Thanks!

---

### Post by Substance on 2006-01-01
are there any other bitorrent programs besides azureus and bt4.0 i was hoping on using utorrent but thats windows only :(

---

### Post by Barrakketh on 2006-01-03
Eclipse and Azureus still don't play nice together.  If I install Azureus it wants to remove Eclipse and it's related packages.  If I install eclipse:
```
$ sudo apt-get install eclipse-sdk
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  eclipse-jdt eclipse-jdt-common eclipse-pde eclipse-pde-common
  eclipse-platform eclipse-platform-common eclipse-rcp libswt3.1-gtk-java
  libswt3.1-gtk-jni
Recommended packages:
  eclipse-jdt-gcj eclipse-pde-gcj eclipse-source eclipse-platform-gcj
  eclipse-rcp-gcj
The following packages will be REMOVED:
  azureus libswt-gtk-3.1-java libswt-gtk-3.1-jni
The following NEW packages will be installed:
  eclipse-jdt eclipse-jdt-common eclipse-pde eclipse-pde-common
  eclipse-platform eclipse-platform-common eclipse-rcp eclipse-sdk
  libswt3.1-gtk-java libswt3.1-gtk-jni
0 upgraded, 10 newly installed, 3 to remove and 3 not upgraded.
```

---

### Post by skaboss on 2006-01-05
[QUOTE=Barrakketh]Eclipse and Azureus still don't play nice together.  If I install Azureus it wants to remove Eclipse and it's related packages.  If I install eclipse:
```
$ sudo apt-get install eclipse-sdk
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  eclipse-jdt eclipse-jdt-common eclipse-pde eclipse-pde-common
  eclipse-platform eclipse-platform-common eclipse-rcp libswt3.1-gtk-java
  libswt3.1-gtk-jni
Recommended packages:
  eclipse-jdt-gcj eclipse-pde-gcj eclipse-source eclipse-platform-gcj
  eclipse-rcp-gcj
The following packages will be REMOVED:
  azureus libswt-gtk-3.1-java libswt-gtk-3.1-jni
The following NEW packages will be installed:
  eclipse-jdt eclipse-jdt-common eclipse-pde eclipse-pde-common
  eclipse-platform eclipse-platform-common eclipse-rcp eclipse-sdk
  libswt3.1-gtk-java libswt3.1-gtk-jni
0 upgraded, 10 newly installed, 3 to remove and 3 not upgraded.
```[/QUOTE]

My 2 cents : install all java related stuff (eclipse, ant, tomcat...) manually. 
Linux purists will say that's dumb, and that doing this you'll miss the power of packages. 
I experienced so much problems with java apps packages : tomcat messing with struts apps, impossibility to correctly set local javadoc for the JDK in eclipse... that i took this resolution, and now everything is running fine  :-)

---

### Post by ububaba on 2006-01-28
[QUOTE=arnieboy]**UPDATED! NO MORE RESIZING PROBLEMS**[B]
Part 1: Installing Azureus[/B]
Before anything make sure u **uncomment** the **universe** and **multiverse** repositories .....[/QUOTE]

At a far simpler level. How does one **comment** or **uncomment**?

---

### Post by Rory on 2006-01-28
This is a fair question.  We just assume that these basic things are self-explanatory, when, of course, they're not.

## comment
     uncomment (remove the '#') from the front of the line.  

## at the beginning of the line means that that line won't be included in your repository (or other script, for that matter).  But, it's still there, in case you want to use it down the line, when all you have to do is remove the #.  

## Sometimes you'll see a file and it will have instructions.  In order for ## the instructions to be there but not seen as code, comments are put ## in from of the lines.  This allows you to write anything you want to users, explainining the contents of the script.  Then you'll see code.

Here's an example: [http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

Simple enough?

Rory

---

### Post by ububaba on 2006-01-28
Thanks a bunch. It was really helpful.

---

### Post by Pettman on 2006-02-12
Will there be an update for the new version of Azureus (2.4.0.0, came out  the 10 of february)?

---

### Post by newuser111 on 2006-02-12
azureus can auto update itself

---

### Post by Pettman on 2006-02-12
[QUOTE=newuser111]azureus can auto update itself[/QUOTE]
Not this version. Or you'd need to run it as root or something.

---

### Post by jamesford on 2006-02-12
i downloaded the tarball and extracted over the old version and it works just great. there were some problems with some paths but it ws easy to fix with the azureus options thingy

---

### Post by Monoman on 2006-02-26
new path for wget

```
wget http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-3_all.deb 
```

---

### Post by arnieboy on 2006-02-26
First post updated.

---

### Post by daredevil on 2006-03-01
arnieboy i did not require firewall to open up port for azureus. dunno y!!

---

### Post by Jawbreaker4Fs on 2006-03-03
Ok... so I've been screwing around with attempting to install Azureus for several hours, and I seem to be at a completed dead end. Following the guide here, I managed to get Azureus to load, got NAT configured correctly, and downloaded the update. Without thinking, I allowed Azureus to install some sort of SWT update... and when it tried to reload the program I got the following error:

[INDENT]```
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3139 in java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:109)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:143)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:158)

```[/INDENT]

I've tried uninstalling Azureus and everything Java... then doing a reinstall of both (several times), as well as ensuring that java is set to the sun version in 
[INDENT]update-alternatives --config java[/INDENT]
but none of this has worked! Any help would be greatly appreciated...

---

### Post by Jawbreaker4Fs on 2006-03-04
After quite a while I managed to get it running using the method described by [Rory here]("http://ubuntuforums.org/showpost.php?p=616305&postcount=103"). Thanks a bunch!

---

### Post by tombott on 2006-03-05
[QUOTE=Rory]There's also this second method, found on the new Breezy Ubuntu Guide, that will install the tarball straight from sourceforge.
[http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29.3F](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29.3F)

```

sudo apt-get install sun-j2re1.5  (must have PLF repo added for this)

wget -c [http://heanet.dl.sourceforge.net/sourceforge/azureus/Azureus_2.3.0.6_linux.tar.bz2](http://heanet.dl.sourceforge.net/sourceforge/azureus/Azureus_2.3.0.6_linux.tar.bz2)

sudo tar jxvf Azureus_2.3.0.6_linux.tar.bz2 -C /opt

sudo gedit /usr/share/applications/azureus.desktop 

```
    * Add the following to the new file: 
[Desktop Entry] 
Name=Azureus
Comment=A Bittorrent client
Exec=/opt/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;[/QUOTE]


Thanks for this.
Worth noting that the link to Azureus no longer works.
But this does:
```

wget -c http://ovh.dl.sourceforge.net/sourceforge/azureus/Azureus_2.4.0.0_linux.tar.bz2
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt

```
Also when creating Icon for Azureus Exec should read:

[Desktop Entry]
Name=Azureus
Comment=A Bittorrent client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

---

### Post by ubunlilluz on 2006-03-05
mine doesn't work: it gives always "dht firewalled" but the nat is ok and i don't have a router, but a 56k analogic modem:cry:

---

### Post by dark_templar on 2006-03-07
[QUOTE=ubunlilluz]mine doesn't work: it gives always "dht firewalled" but the nat is ok and i don't have a router, but a 56k analogic modem:cry:[/QUOTE]

I have the same problem. I configured firestater already, my router has the rules set (and NAT is ok, even according to Azureus). The strangest thing is that, sometimes DHT starts to work out of the blue. :-k

---

### Post by Dogweazel on 2006-05-06
Is the first post outdated, I get some error messages like (translated from dutch):
Couldn't check status sourcepakketlist at [http://packages.freecontrib.org](http://packages.freecontrib.org) etc..
and:
A failure to get some indexfiles or the're used some old packages
and:
Couldn't find sun-j2re1.5
I want to install Azereus, maybe someone has a working tutorial.
Thanks

---

### Post by Alpha_Maverick on 2006-05-06
replace all occurances of "azureus_2.3.0.6-3_all.deb" with "azureus_2.4.0.2-1_all.deb" and it worked great for me.

---

### Post by bitoiu on 2006-09-10
Simply.. THANKS : Easy, simple, straigh foward...

Recommended to everyone!!!

---

### Post by Mujaheiden on 2006-12-20
mmmm. the repositry isn't there, and neither is the azureus_2.4.0.2-1_all.deb file.

---

### Post by psycho5 on 2007-09-27
err.. i am really noob at ubuntu... can you tell me where to post what code? i have no idea what you just told us to do. Thanks alot!

---

