---
title: "Tutorial for installing SourceForge SleepyHead CPAP/BiPAP (Sleep Apnea) software"
date: 2012-03-07
forum: Packaging and Compiling Programs
---

### Post by rocksockdoc on 2012-03-07
Help me help others ... 
 [I]Note: If you're on Ubuntu Lucid 10.04, please let me know if this works for you!

[/I] Having never compiled anything, here's my best guess at how to install SourceForge SleepyHead freeware for analyzing & graphing data stored by the following home-use sleep apnea equipment:

[LIST]
[*]Philips Respironics System One
[*]ResMed S9 families
[*]DeVilbiss Intellipap
[*]Fisher & Paykel Icon
[*]Contec CMS50 (USB serial) oximeters
[*]ResMed S9's oximeter attachment.
[/LIST]
  Read about SleepyHead software from the [SleepyHead Web Site]("http://sleepyhead.sourceforge.net/").
Read the [SleepyHead Wiki ]("http://sourceforge.net/apps/mediawiki/sleepyhead/index.php?title=Main_Page")on SourceForge.net
Read the [SleepyHead Build-from-Source]("http://sourceforge.net/apps/mediawiki/sleepyhead/index.php?title=Build_from_source") page on SourceForge.net.

** For Ubuntu Natty 11.04, simply download the .deb & doubleclick on it:**
 
[LIST]
[*][http://sourceforge.net/projects/sleepyhead](http://sourceforge.net/projects/sleepyhead)
[LIST]
[*]32-bit  ([sleepyhead_0.9.2-1_i386.deb]("http://sourceforge.net/projects/sleepyhead/files/Releases/Linux/sleepyhead_0.9.2-1_i386.deb/download"))
[*]64-bit  (**[sleepyhead_0.9.2-1_amd64.deb]("http://sourceforge.net/projects/sleepyhead/files/latest/download?source=files")**)
[/LIST]
 
[/LIST]
  [B]For Ubuntu Lucid 10.04, you'll need to compile from source:
[/B]Note: Doubleclicking the .deb on Ubuntu Lucid 10.04 will elicit the following fatal error:
[COLOR=DarkRed]*     Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.7.0~beta1)*[/COLOR]

** Install C++ & QT development tools & the GIT client:**
```
$ sudo apt-get install git-core qt4-dev-tools libqt4-opengl-dev libqtwebkit-dev zlib1g-dev 
```**Obtain the SleepyHead source code (using 'git'):**
```
 $ git clone git://sleepyhead.git.sourceforge.net/gitroot/sleepyhead/sleepyhead
```**Create a Makefile:**
```
$ qmake
```**Compile the SleepyHead executable:**
```
make
```Note: Please reply whether this works for you on Ubuntu Lucid 10.04!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214050&stc=1&d=1331389855[/IMG]

---

### Post by rocksockdoc on 2012-03-09
I added additional information to the first post above based on this response below from here:
[**- How do you compile source code (sleepyhead src from Sourceforge)?**]("http://ubuntuforums.org/showthread.php?p=11755956#post11755956")

> **MadCow108 said:**
> it works fine in lucid setup, the only thing missing from the instructions is *apt-get install zlib1g-dev* for zlib.h

---

### Post by rocksockdoc on 2012-03-10
FYI: A friend of mine who is a lifelong developer (so he had all the programs installed) was able to skip all but three of the steps above to compile the SleepyHead executable.

> 
It worked for me on Lucid 10.04 just by running these commands:
git clone git://sleepyhead.git.sourceforge.net/gitroot/sleepyhead/sleepyhead
qmake
make
./SleepyHead


---

### Post by oldos2er on 2012-03-10
Moved to Packaging and Compiling Programs.

---

### Post by rocksockdoc on 2012-03-11
> **oldos2er said:**
> Moved to Packaging and Compiling Programs.

Thanks!

More details on debugging the compilation step on Ubuntu 10.04 are here:
- [**How do you compile source code (sleepyhead src from Sourceforge)?**]("http://ubuntuforums.org/showthread.php?p=11756055#post11756055")

---

