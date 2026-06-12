---
title: "HOWTO: Installing Java J2SDK | J2RE with firefox plugins"
date: 2005-04-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-04-02
Hello,
i don't know if this solution has been discussed before, because it differ than the one available in [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) if yes i apologise for this

the purpose of this HOWTO: is how to install J2SDK or J2RE (i will consider you will install J2SDK in this HOWTO) with mozilla-firefox java plugin as debian packages, not directly from sources..

first you need to download J2SDK or J2RE from [http://www.blackdown.org/java-linux/java-linux-d2.html](http://www.blackdown.org/java-linux/java-linux-d2.html)

go to the folder where you downloaded the .bin file (j2sdk-1.4.2-01-linux-i586.bin in my case)

```

$ sudo apt-get install java-package fakeroot
$ fakeroot make-jpkg j2sdk-1.4.2-01-linux-i586.bin

```

you don't have to fill your mail and other info asked just press enter, when this finished you will find blackdown-j2sdk1.4_1.4.2+01_i386.deb in the same folder

```

$ sudo dpkg -i blackdown-j2sdk1.4_1.4.2+01_i386.deb

```

verify that java has been installed correctly as a java envirement and mozilla-firefox plugin,
```

java -version

``` to verify the envirement

in mozilla-firefox
```

about:plugins

``` you should see Java(TM) Plug-in Blackdown-1.4.2-01

Enjoy!!! :D

---

### Post by bored2k on 2005-04-02
If that does not work, visit [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java) .

I have yet to test Blackdown; is it faster than Sun's own ?

---

### Post by Gandalf on 2005-04-03
[QUOTE=bored2k]If that does not work, visit [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java) .

I have yet to test Blackdown; is it faster than Sun's own ?[/QUOTE]
 well i'm quite happy with it, i run it on ubuntu on my laptop and on my debian sarge server working great

---

### Post by kelean on 2005-04-03
Here is the guide for warty but installing java with this works well just make sure the the version is correct.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
I just installed java with no problems ans it runs very well.

---

### Post by bored2k on 2005-04-03
[QUOTE=kelean]Here is the guide for warty but installing java with this works well just make sure the the version is correct.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
I just installed java with no problems ans it runs very well.[/QUOTE]
 This is the **Hoary** HOW-TO section, isn't it ? :roll:

---

### Post by Gandalf on 2005-04-03
[QUOTE=bored2k]This is the **Hoary** HOW-TO section, isn't it ? :roll:[/QUOTE]
 ** Unofficial Ubuntu 4.10 Starter Guide**

 
so apprently it's warty not hoary

---

### Post by bored2k on 2005-04-03
[QUOTE=Gandalf]** Unofficial Ubuntu 4.10 Starter Guide**

 
so apprently it's warty not hoary[/QUOTE]
 My point was: you posted on 
Ubuntu Linux Forums > Ubuntu Hoary Hedgehog 5.04  > Hoary 5.04 FAQs & HOWTOs

Wich means we don't care about Warty.

---

### Post by Gandalf on 2005-04-03
[QUOTE=bored2k]My point was: you posted on 
Ubuntu Linux Forums > Ubuntu Hoary Hedgehog 5.04  > Hoary 5.04 FAQs & HOWTOs

Wich means we don't care about Warty.[/QUOTE]
 oh ok sorry :S my HOWTO is for hoary in any case, i run hoary and did it to my distro myself, anyway sorry for the miss-understanding

---

### Post by jiyuu0 on 2005-04-04
[QUOTE=bored2k]My point was: you posted on 
Ubuntu Linux Forums > Ubuntu Hoary Hedgehog 5.04  > Hoary 5.04 FAQs & HOWTOs

Wich means we don't care about Warty.[/QUOTE]

Unofficial Ubuntu 5.04 Starter Guide
[http://www.ubuntuguide.org/temp](http://www.ubuntuguide.org/temp) 
the update java section is also there
*this is still the temp page

---

### Post by dejitarob on 2005-04-05
I would be careful running an old version of java. [http://ubuntuguide.org/#jre]("http://ubuntuguide.org/#jre") links to the latest version (other binaries on Sun's [Java download page]("http://java.sun.com/j2se/1.5.0/download.jsp"))

---

### Post by bored2k on 2005-04-05
[QUOTE=dejitarob]I would be careful running an old version of java. [http://ubuntuguide.org/temp/#jre](http://ubuntuguide.org/temp/#jre) links to the latest version.[/QUOTE]
 Careful ? why? as long as the application doesn't demand it, they should work [some old versions work faster than others... supposedly]. Even Limewire for Windows, downloads a very old java version, the one that works, not necessarily new. On old java's I have used azureus, limewire and  websites like dslreports.

But, if a new version is available, there is no point in using an old one.

---

### Post by dejitarob on 2005-04-05
[QUOTE=bored2k]Careful ? why?[/QUOTE][http://secunia.com/product/784/#advisories](http://secunia.com/product/784/#advisories)

---

### Post by remkio on 2005-04-10
I tried to install the Sun J2SDK 1.5.0 update 2 using the method above, however it still didn't install the plugin.

After some research I found out that the firefox plugin is "installed" by creating a symbolic link to a symbolic link in the /etc/alternatives directory, which points to a non-existing file. 

Whether or not this is because Sun changed the directory layout, or the make-jpkg doesn't set it up properly I am not sure, however by changing the symbolic link for
**/etc/alternatives/firefox-javaplugin.so** 
from:

**/usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so**

to

**/usr/lib/j2sdk1.5-sun*/jre*/plugin/i386/ns7/libjavaplugin_oji.so**

I've been able to get firefox to work.

I guess that by changing the **mozilla-javaplugin.so** and the **netscape-javaplugin.so** one will be able to get these programs to work properly as well..

Another way to solve this problem is to update the **install** file in **/usr/share/java-package/sun-j2sdk1.5** by changing:
> 
# assemble the plugin path
plugin_dir="$j2se_base/plugin/$arch_dir"

to:
> 
# assemble the plugin path
plugin_dir="$j2se_base/jre/plugin/$arch_dir"

before building the package with make-jpkg.

---

### Post by Z-Bo on 2005-04-10
I have tried just about every solution offered (I think) and have yet to find a workable answer.  Here is what confuses me, I do:

**$ java -version**

```
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)
```

**$ firefox about:plugins**

```
Java(TM) Plug-in 1.5.0_02-b09

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_02

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_02 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_02 	Java 		Yes
```

Judging by the confirmations I am getting from running from terminal, I should be able to run java without crashing, right...?  So far the best I get is the browser no longer crashes.  I then decided to right click in the browser document of a page that contains an embedded applet, and View Page Info > Tab "Media"... There is no media content in the Media tab related to java.  I doublecheck the page source to make sure there is an embedded applet and sure enough it is there.  Please, any suggestions would be welcome so I can stop  ](*,)

Edit: I tried symlinking with the "alternatives" directory.  What change did I get? about:plugins no longer registers java as a plugin, BUT Firefox acknowledges applets in the Media "Tab" under View Page Info.  Am I getting closer or further away?  Hmm...

---

### Post by remkio on 2005-04-10
[QUOTE=Z-Bo]I have tried just about every solution offered (I think) and have yet to find a workable answer.  Here is what confuses me, I do:

...

Judging by the confirmations I am getting from running from terminal, I should be able to run java without crashing, right...?  So far the best I get is the browser no longer crashes.  I then decided to right click in the browser document of a page that contains an embedded applet, and View Page Info > Tab "Media"... There is no media content in the Media tab related to java.  I doublecheck the page source to make sure there is an embedded applet and sure enough it is there.  Please, any suggestions would be welcome so I can stop  ](*,)
[/QUOTE]

Mmm.. None of the applets I looked at showed up in my "Media" tab... However, they do run properly... and therefor I don't mind...

> 
Edit: I tried symlinking with the "alternatives" directory.  What change did I get? about:plugins no longer registers java as a plugin, BUT Firefox acknowledges applets in the Media "Tab" under View Page Info.  Am I getting closer or further away?  Hmm...


Looks like you lost the plugin... Just a question: how did you install your java?

---

### Post by WMCoolmon on 2005-04-10
Question: I installed Sun Java before I realized there was no firefox plugin for the AMD64...is it OK if I just install blackdown Java over it?

---

### Post by Z-Bo on 2005-04-10
@remkio

Thanks for replying.  What do you mean "lost the plugin?"  You are referring to libjavaplugin_oji.so correct?  I have it...

One thing that might be screwing things up is all the installs and removals of Java I have done in the past week or so to get Java to work...

---

### Post by dejitarob on 2005-04-10
[QUOTE=WMCoolmon]Question: I installed Sun Java before I realized there was no firefox plugin for the AMD64...[/QUOTE]There are AMD64 binaries on Sun's Java [download page](http://java.sun.com/j2se/1.5.0/download.jsp) (click on 'Download JRE 5.0 Update 2'). Follow the install instructions in the [unofficial guide](http://ubuntuguide.org/#jre), substituting i386 for your binaries of course.

---

### Post by WMCoolmon on 2005-04-11
That's exactly what I did; the problem is, there's no firefox/mozilla plugin for the versions on Sun's site.  :|

---

### Post by RastaMahata on 2005-04-11
Thank you Thank you Thank you Thank you Thank you Thank you Thank you Thank you.
I finally have java in firefox (efter i don t know how many repositories added)... Someone should fix the wiki at ubuntulinux.org and state that those instructions are for warty! (/me hits his forehead):(

---

### Post by dejitarob on 2005-04-11
[QUOTE=WMCoolmon]That's exactly what I did; the problem is, there's no firefox/mozilla plugin for the versions on Sun's site.  :|[/QUOTE]That is why the [ubuntu guide](http://ubuntuguide.org/#jre-mozilla) was linked.

---

### Post by punkinside on 2005-04-28
```
sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

```

?!?!?! I have almost every imaginable repository enabled whats the problem here?! I already installed it from a non-supported one just added some other repositories and did apt-get install j2sdk-dont remember what else.... but this concerns me I also couldnt get the firefox plugin

---

### Post by Gandalf on 2005-04-28
[QUOTE=punkinside]```
sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

```

?!?!?! I have almost every imaginable repository enabled whats the problem here?! I already installed it from a non-supported one just added some other repositories and did apt-get install j2sdk-dont remember what else.... but this concerns me I also couldnt get the firefox plugin[/QUOTE]
 look here
[http://packages.ubuntu.com/hoary/misc/java-package](http://packages.ubuntu.com/hoary/misc/java-package)

---

### Post by punkinside on 2005-04-28
hey thanx Gandalf... now where do I put it? apt-get should work now right? but does it need to be somewhere specific? sorry, complete n00b here..

---

### Post by Gandalf on 2005-04-29
[QUOTE=punkinside]hey thanx Gandalf... now where do I put it? apt-get should work now right? but does it need to be somewhere specific? sorry, complete n00b here..[/QUOTE]
 hmmmmmmm... just make sure that the source (that that page mentioned) is actually inside your /etc/apt/sources.list

---

### Post by angrykeyboarder on 2005-05-01
[QUOTE=Gandalf]Hello,
i don't know if this solution has been discussed before, because it differ than the one available in [http://ubuntuguide.org/#jre]("http://ubuntuguide.org/#jre") if yes i apologise for this

the purpose of this HOWTO: is how to install J2SDK or J2RE (i will consider you will install J2SDK in this HOWTO) with mozilla-firefox java plugin as debian packages, not directly from sources..

first you need to download J2SDK or J2RE from [http://www.blackdown.org/java-linux/java-linux-d2.html]("http://www.blackdown.org/java-linux/java-linux-d2.html")

go to the folder where you downloaded the .bin file (j2sdk-1.4.2-01-linux-i586.bin in my case)

```

$ sudo apt-get install java-package fakeroot
$ fakeroot make-jpkg j2sdk-1.4.2-01-linux-i586.bin

```

you don't have to fill your mail and other info asked just press enter, when this finished you will find blackdown-j2sdk1.4_1.4.2+01_i386.deb in the same folder

```

$ sudo dpkg -i blackdown-j2sdk1.4_1.4.2+01_i386.deb

```

verify that java has been installed correctly as a java envirement and mozilla-firefox plugin,
```

java -version

``` to verify the envirement

in mozilla-firefox
```

about:plugins

``` you should see Java(TM) Plug-in Blackdown-1.4.2-01

Enjoy!!! :D[/QUOTE]

Or you could download [ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-i586/j2sdk1.4_1.4.2.01-1_i386.deb]("ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-i586/j2sdk1.4_1.4.2.01-1_i386.deb")

or [ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-i586/j2re1.4_1.4.2.01-1_i386.deb]("ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-i586/j2re1.4_1.4.2.01-1_i386.deb") if you want the JDK

or for us AMD64 kids, there is..

[ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-amd64/j2sdk1.4_1.4.2.01-1_amd64.deb]("ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-amd64/j2sdk1.4_1.4.2.01-1_amd64.deb") or [ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-amd64/j2re1.4_1.4.2.01-1_amd64.deb]("ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian/pool/j/j2se1.4-amd64/j2re1.4_1.4.2.01-1_amd64.deb")

Then start with your installation instruction for the J2SDK or the J2RE and continue with your instructions.

---

### Post by gasley on 2005-05-05
I have succesfully installed java-package and fakeroot, but when i execute

```
fakeroot make-jpkg j2sdk-1.4.2-01-linux-i586.bin
```

I get this: 

```
Creating temporary directory: /tmp/make-jpkg.XXXXmQTwyW
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

Detected product:
    Java(TM) Software Development Kit (J2SDK)
    Standard Edition, Version 1.4.2+01
    Blackdown Java-Linux
Is this correct [Y/n]: y

Checking free diskspace: done.

Please enter your full name. This value will be used in the maintainer
field of the created package.

Full name [root]:
hostname: Unknown host

Aborted ().

Removing temporary directory: done

```

So it fails after entering full name, whether i leave it empty or write something to it. 

Any help?

---

