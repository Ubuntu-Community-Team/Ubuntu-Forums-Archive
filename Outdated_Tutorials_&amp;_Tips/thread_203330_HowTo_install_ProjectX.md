---
title: "HowTo: install ProjectX"
date: 2006-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by ultima on 2006-06-25
Howto install Projectx on Ubuntu

I didn't find much info on this program here so I thought I'd write a
quick howto

ProjectX is useful for demuxing and correcting the video/audio sync 
in .ts (Transport Stream) video files recorded from dvb cards.

I am running Kubuntu Dapper but this should work on all versions of Ubuntu

First we need to install Java
```
sudo apt-get install sun-java5-bin
```
Specific instructions on how to install java can be found here [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Since this application is OS independent we will
Download the Projectx Binary from [http://www.doom9.org](http://www.doom9.org)

Extract and move to the ProjectX directory 
```
unzip ProjectX_0.90.4.zip
cd ProjectX_Source_0.90.4
```

Execute the ProjectX binary

```
java -jar ProjectX.jar
```

ProjectX should now open


If you get errors when executing please refer to the Java install page
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

UPDATE: You may need to run the following commands to configure Java
 
sudo update-alternatives --install /usr/bin/java java /usr/local/java/bin/java 3
sudo update-alternatives --config java

---

### Post by Jose Catre-Vandis on 2006-10-08
Have upped a deb of the projectx for easy installation

```
http://www.zen77933.zen.co.uk/Files/projectx_0.90.4.00-1_all.deb
```

If I could just figure out how to use the thing :D

---

### Post by wildchild on 2006-10-09
Thanks for the .deb!

---

### Post by knick620 on 2007-02-18
Yes thanks for the Deb, I am a newbie trying ubuntu and was dependent on WInXP for Toppy et all.   I was managing to find my way around ubuntu from other helpful sites, however with a steep learning curve the debs make life alot easier for a commute from XP.  Thanks

---

### Post by RangerOne on 2007-04-21
Damn...

I have been running ProjectX without any trouble in various Linux and Windows flavours for years; just upgraded my edgy eft to feisty fawn and ProjectX 0.90.4.00 stopped working! :confused: 

I run it as usual (either from the icon or with 'java -jar <whatever>/ProjectX.jar'); I get the initial agreement splash (which displays perfectly, by the way), and when the main window opens it's completely grey and empty! Nothing to do with it apart from closing it :( 

Has anybody run into a similar problem? I have tried switching VMs (java 5, java 6, etc.) to no avail. I have rebuilded the package with the same results. I have installed the provided .deb, just in case it helped: nothing. I have tried to run previous version's jars (0.81, 0.82) and... they work fine !!! I'm clueless and can't think of anything else to try... hence the call for help :)

Any tips would be much appreciated. Thanks!

---

### Post by RangerOne on 2007-04-21
I reply myself with new data on the subject.

The short anwser: Beryl.

The long answer: ProjectX 0.90 doesn't get along well with Beryl desktop enhancements, and doesn't display the window correctly (at all!). Selecting Metacity (default Gnome window manager) as window manager solved the problem. Haven't tried with Compiz yet.

Hope this helps somebody else!

---

### Post by vertigo1980 on 2007-04-23
> Hope this helps somebody else!

it did! ;)

i had to do everything via cli. if i have to turn of beryl each time, guess i'll just continue doing so. would be great if beryl could be disabled for certain apps though

---

### Post by ls8 on 2007-04-30
> **RangerOne said:**
> Damn...
...I get the initial agreement splash (which displays perfectly, by the way), and when the main window opens it's completely grey and empty! Nothing to do with it apart from closing it...

Same here. Running Feisty too. Tried ProjectX 0.90.3.00, 0.90.3.01, 0.90.4.00.

---

### Post by ykpaiha on 2007-06-18
you probably run with beryl
just edit projectx.sh
so just verify to add 2 lines in your file::

#!/bin/sh
#
# startscript for ProjectX
#
export J2SE_PREEMPTCLOSE=1
export AWT_TOOLKIT=MToolkit 

cd /usr/share/projectx
java -jar ProjectX.jar


it will work

---

### Post by bawbagg on 2007-08-10
Sweet!!

I'm running compiz and had the blank screen problem. I edited projectx.sh in /usr/bin asper your instructions and it worked perfectly.

Many thanks,

BB

---

