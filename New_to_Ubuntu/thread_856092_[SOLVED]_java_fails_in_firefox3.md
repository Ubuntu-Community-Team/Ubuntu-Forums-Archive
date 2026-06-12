---
title: "[SOLVED] java fails in firefox3"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-07-11
i installed firefox3 and java failed to work. i deleted xpti.dat and let firefox to rebuild it, reinstalled java plugin, but still didn't work.

thanks for help!

---

### Post by alienexplorers on 2008-07-11
WHere did you install the plugin to?  It should be installed in your /usr/lib/firefox (firefox-3.0) plugins folder.

---

### Post by tinny on 2008-07-11
Does "Edit > Preferences > Content" have "Enable Java" checked?

---

### Post by ajgreeny on 2008-07-11
Which java are you using?  The OS version seems to work less well than the sun java version so I removed the following four packages from my machine and installed the sun-java version instead.

icedtea-gcjwebplugin
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

Give it a try, you can always restore them with synaptic if you don't find any difference.  This is a great pity, as it would be nice to stick with the open source version, but if it is not working properly, there's no real contest.

---

### Post by afeasfaerw23231233 on 2008-07-11
> alienexplorers  	
Re: java fails in firefox3
WHere did you install the plugin to? It should be installed in your /usr/lib/firefox (firefox-3.0) plugins folder. 

i don't know where i installed the plugin to :(
the plugin seems not in the /usr/lib/firefox folder

```
wong@wong-desktop:/usr/lib/firefox$ ls
browserconfig.properties  greprefs           libnss3.so          libxpcom.so
chrome                    icons              libnssckbi.so       libxpistub.so
components                libgfxpsshar.so    libplc4.so          plugins
defaults                  libgkgfx.so        libplds4.so         res
dictionaries              libgtkembedmoz.so  libsmime3.so        run-mozilla.sh
extensions                libgtkxtbin.so     libsoftokn3.so      searchplugins
firefox                   libjsj.so          libssl3.so
firefox-bin               libmozjs.so        libxpcom_compat.so
firefox.cfg               libnspr4.so        libxpcom_core.so
wong@wong-desktop:/usr/lib/firefox$ cd plugins
wong@wong-desktop:/usr/lib/firefox/plugins$ ls
flashplugin-alternative.so  mplayerplug-in-qt.so   mplayerplug-in-wmp.so
libjavaplugin.so            mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libunixprintplugin.so       mplayerplug-in-rm.so   mplayerplug-in.xpt
mplayerplug-in-dvx.so       mplayerplug-in-rm.xpt  nphelix.so
mplayerplug-in-dvx.xpt      mplayerplug-in.so      nphelix.xpt

```
> 
tinny  	
Re: java fails in firefox3
Does "Edit > Preferences > Content" have "Enable Java" checked? 
yes it is checked.
> ajgreeny  	
Re: java fails in firefox3
Which java are you using? The OS version seems to work less well than the sun java version so I removed the following four packages from my machine and installed the sun-java version instead.

icedtea-gcjwebplugin
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

Give it a try, you can always restore them with synaptic if you don't find any difference. This is a great pity, as it would be nice to stick with the open source version, but if it is not working properly, there's no real contest. 

i didn't install these four 
```

icedtea-gcjwebplugin
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
```
i check my synaptic and these have been installed.

---

### Post by tinny on 2008-07-11
Looks like you have a few versions of Java installed. 

What is the output of the following...

```

java -version

```

This will tell us the Java version that is being used by default.

If you are using the Sun version you show be able to navigate to (on your desktop) System >  Preferences > Sun Java Plug in Control Panel.

In the Advanced tab what is the value of "Command to launch default browser"?

In the Java tab what are the settings for "Java Applet Runtime Settings"?

Your using Ubuntu 7.10 correct?

---

### Post by alzie on 2008-07-11
In your second thumbnail you have ALL the javas installed?

I checked mine and I only have java-common installed.  I also have sun-java5-bin, sun-java5-jre and sun-java5-plugin installed.  (I don't have sun-java6-* installed as it conflicts with some sites I use.  Personal preference)

I'm wondering if having all those packages installed maybe causing some of your headaches.

---

### Post by afeasfaerw23231233 on 2008-07-13
> **tinny said:**
> Looks like you have a few versions of Java installed. 

What is the output of the following...

```

java -version

```

This will tell us the Java version that is being used by default.

If you are using the Sun version you show be able to navigate to (on your desktop) System >  Preferences > Sun Java Plug in Control Panel.

In the Advanced tab what is the value of "Command to launch default browser"?

In the Java tab what are the settings for "Java Applet Runtime Settings"?

Your using Ubuntu 7.10 correct?
```
 java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```
in the system - preference:
there are java plugin control panel 1.4 , java policy tool 1.4
sun java 5.0 plugin control pane, policy tool
sun java 6.0 plugin control pane, policy tool

there are 3 java installed 
here's are the screenshots

[ATTACH]77579[/ATTACH]
[ATTACH]77578[/ATTACH]
sorry for laziness
yes i am using 7.10

>  alzie  	
Re: java fails in firefox3
In your second thumbnail you have ALL the javas installed?

I checked mine and I only have java-common installed. I also have sun-java5-bin, sun-java5-jre and sun-java5-plugin installed. (I don't have sun-java6-* installed as it conflicts with some sites I use. Personal preference)

I'm wondering if having all those packages installed maybe causing some of your headaches. 
i searched java for synaptic and reinstall all 1.4, 5 and 6 and hoped java would work.

thanks for help and sorry for my no0b1sh!

edit: i run "locate firefox" in the terminal and find out firefox is not installed in /usr/bin/firefox

---

### Post by alzie on 2008-07-13
In order to get java and firefox 3 working I went to psychocats' tutorial here: [http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

The site he refers to in the tutorial is: [http://www.geocities.com/Im_havoc/](http://www.geocities.com/Im_havoc/)

If you haven't tried this method I'd give it a go.  If you have already tried this then I am stuck.

I hope this is helpful.

---

### Post by pemur1 on 2008-07-13
I'm having problems with Java at a certain site. Please see attached image.

---

### Post by tinny on 2008-07-13
> **pemur1 said:**
> I'm having problems with Java at a certain site. Please see attached image.

This is a very unhelpful post. Did you read this thread at all? Please don't hijack this thread.

---

### Post by tinny on 2008-07-13
> **afeasfaerw23231233 said:**
> ```
 java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```
in the system - preference:
there are java plugin control panel 1.4 , java policy tool 1.4
sun java 5.0 plugin control pane, policy tool
sun java 6.0 plugin control pane, policy tool

there are 3 java installed 
here's are the screenshots

[ATTACH]77579[/ATTACH]
[ATTACH]77578[/ATTACH]
sorry for laziness
yes i am using 7.10

 
i searched java for synaptic and reinstall all 1.4, 5 and 6 and hoped java would work.

thanks for help and sorry for my no0b1sh!

edit: i run "locate firefox" in the terminal and find out firefox is not installed in /usr/bin/firefox

You really need to only have one Java runtime installed. My advice to you would be to remove all but Java 5. It is very hard to help you when you have sooo many variables thrown into the equation.

---

### Post by pemur1 on 2008-07-13
> **tinny said:**
> This is a very unhelpful post. Did you read this thread at all? Please don't hijack this thread.

How is this hijacking?!? I'm having a problem with Java in Firefox. I've uninstalled and re-installed Java, but I'm still having problems.

BTW, that was an unhelpful post.

---

### Post by philinux on 2008-07-13
Run this to see whats set as default.

sudo update-alternatives --config java

---

### Post by tinny on 2008-07-13
> **pemur1 said:**
> How is this hijacking?!? I'm having a problem with Java in Firefox. I've uninstalled and re-installed Java, but I'm still having problems.

BTW, that was an unhelpful post.

Have you tried any of the instructions stated in this thread? If so you must have a set of results you are ready to post. Can we see them please. (That would be helpful, remember your the one asking for help not me)

---

### Post by afeasfaerw23231233 on 2008-07-14
i removed all version java from synaptic and reinstall sun java 5.0 plugin, sun java 5.0 runtime and sun java 5.0 console from Add/Remove Applcation.
```
:~$ java -version
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

```
> 
In the Advanced tab what is the value of "Command to launch default browser"?
```
/usr/bin/firefox
```
> In the Java tab what are the settings for "Java Applet Runtime Settings"?
JRE  1.5.0._13  /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre
JRE  1.6.0._03  /usr/lib/jvm/java-6-sun-1.6.0.03/jre

---

### Post by tinny on 2008-07-14
So it looks like we have successfully broken your Java install. :(

```

:~$ java -version
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

```

When it comes to Java ive always used apt-get from the command line to install / uninstall.

Try this.

```

sudo apt-get remove --purge sun-java*
sudo apt-get clean
sudo apt-get install sun-java5*
java -version

```

The above commands will remove all sun Java installs then reinstall sun Java 5 (properly this time hopefully). The last command should produce Java 5 version information if all has worked.

If it works try navigating to a Java applet.

---

### Post by afeasfaerw23231233 on 2008-07-15
i follow your steps but this still occurs
 java -version
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
> If it works try navigating to a Java applet.
how to navigate to a java applet?
it seems that my ff3 is not installed in the right folder. how can i know if it is installed correctly?

---

### Post by tinny on 2008-07-15
> 
how to navigate to a java applet?


[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

This may even give you the option of installing the Java plugin.

> 
it seems that my ff3 is not installed in the right folder. how can i know if it is installed correctly? 


Firefox runs right? If so dont worry about this for now.

Does this command give you any options for selecting your default Java install?
```

sudo update-alternatives --config java 

```

---

### Post by afeasfaerw23231233 on 2008-07-16
> **tinny said:**
> [http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

This may even give you the option of installing the Java plugin.



Firefox runs right? If so dont worry about this for now.

Does this command give you any options for selecting your default Java install?
```

sudo update-alternatives --config java 

```
firefox seems not running right. it sometimes switches back to 2. 0 version when i click the launch icon. i start a new thread asking  about reinstalling ff3 here : [http://ubuntuforums.org/showthread.php?p=5395817#post5395817](http://ubuntuforums.org/showthread.php?p=5395817#post5395817)

 ```
sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.
``` it says nothing to configure

---

### Post by gandaran on 2008-07-16
> **afeasfaerw23231233 said:**
> firefox seems not running right. it sometimes switches back to 2. 0 version when i click the launch icon. i start a new thread asking  about reinstalling ff3 here : [http://ubuntuforums.org/showthread.php?p=5395817#post5395817](http://ubuntuforums.org/showthread.php?p=5395817#post5395817)

 ```
sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.
``` it says nothing to configure

so your problem is you running firefox 2, for firefox 2 you have to install the java plugin manually.
only firefox 3 works with the installed java plugin!
now which of the two firefox you want to keep?

---

### Post by jamesstansell on 2008-07-16
> **gandaran said:**
> so your problem is you running firefox 2, for firefox 2 you have to install the java plugin manually.
only firefox 3 works with the installed java plugin!
now which of the two firefox you want to keep?

In ubuntu 7.10 there should be no need to install the java plugin manually for firefox 2.

afeasfaerw23231233, have you tried these steps?  In 7.10 I'm not sure if they'll work for firefox 3 but they should work for firefox 2.

```
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun
```

If that doesn't work for firefox 3 we can still get it sorted out, but it might take a little more effort.

Just to be sure, you're not running a 64bit system, right?

---

### Post by gandaran on 2008-07-16
you are right!
I didn't check he's running 7.10, sorry for the post.

---

### Post by afeasfaerw23231233 on 2008-07-17
i get my problem solved in this thread: 
[http://ubuntuforums.org/showthread.php?t=860884&page=2](http://ubuntuforums.org/showthread.php?t=860884&page=2)
thanks for help.

---

