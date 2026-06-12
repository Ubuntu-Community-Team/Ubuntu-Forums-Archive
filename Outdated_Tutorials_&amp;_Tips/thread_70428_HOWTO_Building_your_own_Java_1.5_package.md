---
title: "HOWTO: Building your own Java 1.5 package"
date: 2005-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by bored2k on 2005-09-29
I have pasted this same trick numerous times already (half tired of doing it too), but now that Sun Java 1.5 is **no** longer available on backports I thought I'd post a HOWTO about it.
[list=1]
[*] [**_Download_** Java 2 Platform Standard Edition 5.0]("http://java.sun.com/j2se/1.5.0/download.jsp")
[*] There, select one of these:
[LIST]
[*]Download JDK 5.0 Update 5
[*]Download JRE 5.0 Update 5
[/LIST]
[*] After you have **reviewed** and **accepted** the License Agreement, **download** Linux self-extracting file (the one with the **[color=blue].bin**[/color] extension).
[*] In sequence, execute these commands in Terminal mode (Applications -> System Tools -> Terminal):```
sudo apt-get install [fakeroot java-package]("http://www.ubuntuguide.org/#extrarepositories")
```
[*] ```
fakeroot make-jpkg *downloaded_package_name**.bin**
```*
* To get the name of the newly created debian package, let's do:[*] ls


* Now to install it :
[*] sudo dpkg -i newly_created_package**[color=red].deb**[/color] (whatever the newly Sun- DEBian package is named).[/list]

* **Hoary: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)**
*** Works on *Breezy* too.**

---

### Post by sumadartson on 2005-09-30
Nice one!

This might be a stupid question, but why not just alien the rpm?

---

### Post by tseliot on 2005-09-30
Thanks for the guide, I will need it when I install Breezy.

---

### Post by statsministern on 2005-09-30
Creating temporary directory: /tmp/make-jpkg.XXXXiGwUre
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

What to do when you get this message after fakeroot? Running Breezy.

---

### Post by manicka on 2005-09-30
Worked perfectly here in breezy.. thankyou :D

---

### Post by bored2k on 2005-09-30
[QUOTE=sumadartson]Nice one!

This might be a stupid question, but why not just alien the rpm?[/QUOTE]
Alien is like playing the lottery. It might work, it might not. Plus, this is the correct version of building a package for debian/ubuntu/et al.

---

### Post by fire59 on 2005-09-30
Can you post your source.list?  I did and apt get but it's telling me that it can't find java-package.

Other bit of info, i've just installed breezy so if you could post the source.list for breezy.

---

### Post by TakisX on 2005-09-30
the same here no package found

---

### Post by bored2k on 2005-09-30
[QUOTE=TakisX]the same here no package found[/QUOTE]
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Retry

---

### Post by NemanjaM on 2005-10-03
bored2k, I tried following the instructions and got this far:

''nemanja@naemanija:~/Desktop/OvdeIdeSkidanje$ fakeroot make-jpkg jre-1_5_0_05-linux-i586-1.bin
Creating temporary directory: /tmp/make-jpkg.XXXXIKpSwK
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
nemanja@naemanija:~/Desktop/OvdeIdeSkidanje$''

What should my next move be?

I am a total (ubuntu) linux newbie(a couple of days experience).

---

### Post by zaytsevi on 2005-10-03
DOES NOT WORK:



x@s37:~$ sudo apt-get install fakeroot java-package
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
x@s37:~$

---

### Post by nihilocrat on 2005-10-03
Is there any particular reason why there isn't just a native Ubuntu JRE 1.5 package already in existence? It seems like sort of a fundamental thing for a full desktop/web experience.

---

### Post by kod on 2005-10-03
re: why no standalone package, it's because of sun's licensing terms.

re: why no java-package, java-package is in multiverse, so you need to add multiverse to your /etc/apt/sources list

See:
[http://serios.net/content/debian/java/with-java-package.php](http://serios.net/content/debian/java/with-java-package.php)
which has instructions for ubuntu as well.

HOWEVER, installing the sdk (sun 1.5 update 5) this way did not work particularly well for me.  Yes, a commandline javac and java work, but it seems that most of the typical debian java dependencies are not provided by the sdk package created by java-package.  

In other words, jde doesnt work, Eclipse wont install because of unmet dependencies,etc etc.

Anyone else having that issue?

---

### Post by bored2k on 2005-10-03
[QUOTE=zaytsevi]DOES NOT WORK:



x@s37:~$ sudo apt-get install fakeroot java-package
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
x@s37:~$[/QUOTE]
You need the repositories for it. [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by cstudent on 2005-10-03
[QUOTE=bored2k]I have pasted this same trick numerous times already (half tired of doing it too)...[/QUOTE]

Thanks for doing it again :)

Bill

---

### Post by ubuntu_123 on 2005-10-04
Hi, there.

I repositories for it. like this:[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories).

And my /etc/apt/source.list is like:

*************************************************************
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

*************************************************************

Now, I still get this:

-----------------------------------------------------
sudo apt-get install fakeroot java-package
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
---------------------------------------------------

I am very new for Ubuntu, I do look around to try to find something similar, but no.

Thanks.
lasi.

---

### Post by qiezi! on 2005-10-04
I got java from Azureus' website (kudos to whoever posted this first, sorry I couldn't find it again to link it :()... [http://azureus.sourceforge.net/download.php]("http://azureus.sourceforge.net/download.php") its 15.3 MB (the GTK one), then bored2k's HOWTO will do the rest :)

---

### Post by sd_ap on 2005-10-06
nice one...worked like a charm!

---

### Post by bored2k on 2005-10-06
[QUOTE=ubuntu_123]Hi, there.

I repositories for it. like [/QUOTE]
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

```Replace your sources.list with those lines.

---

### Post by Donovan on 2005-10-06
For all who have problems with plugins...

Check if you have "Java-common" package installed. That package is also required to make the java-package procedure work. If not just type in console:

```
sudo aptitude install java-common
```

Then try again the process

---

### Post by ubuntu_123 on 2005-10-08
Hi, there,

Thanks for all your answer.

I tried again with all your suggestion, even I am in canada, I still copied and pasted the source.list to mine, updated it, and I built the java-common.

It seems I went through the whole process, and I actually saw a bunch of java 1.5 something went through the screen, and the 1.5something.deb had been built.

But at the end when I try "java -version", it gives me this:

> yasir@rick:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
yasir@rick:~$

Even I reboots it, it's still the same.

So, okay, even it is version 1.4, it is still okay and hopefully at least I can get some works done, but I can't use "javac", then I still can't do nothing, can somebody help me out with this?

Thank you.
yasir.

---

### Post by FL!PNEUS on 2005-10-08
[QUOTE=ubuntu_123]Hi, there,

Thanks for all your answer.

I tried again with all your suggestion, even I am in canada, I still copied and pasted the source.list to mine, updated it, and I built the java-common.

It seems I went through the whole process, and I actually saw a bunch of java 1.5 something went through the screen, and the 1.5something.deb had been built.

But at the end when I try "java -version", it gives me this:



Even I reboots it, it's still the same.

So, okay, even it is version 1.4, it is still okay and hopefully at least I can get some works done, but I can't use "javac", then I still can't do nothing, can somebody help me out with this?

Thank you.
yasir.[/QUOTE]

Run 'sudo update-alternatives -all' and select all the Sun Java stuff instead of that GNU-crap and you'll be fine.

---

### Post by statsministern on 2005-10-08
What to do with this error message? : 
helios@darkie:~$fakeroot make-jpkg jdk-1_5_0_05-nb-4_1-linux-ml.bin
Creating temporary directory: /tmp/make-jpkg.XXXXvyAEBl
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

---

### Post by ubuntu_123 on 2005-10-08
Hi, FL!PNEUS

It does work! and the compiler also has no problem, sweet.

Java -version come up with 1.5 like this:

> yasir@rick:~/school/407/a2/prac/structural/facade$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
yasir@rick:~/school/407/a2/prac/structural/facade$


Thanks, man,  I really appreciates that.
yasir

---

### Post by FL!PNEUS on 2005-10-09
[QUOTE=statsministern]What to do with this error message? : 
helios@darkie:~$fakeroot make-jpkg jdk-1_5_0_05-nb-4_1-linux-ml.bin
Creating temporary directory: /tmp/make-jpkg.XXXXvyAEBl
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done[/QUOTE]
You downloaded the JDK with NetBeans-bundle. Download the JDK only.

---

### Post by KeithO on 2005-10-09
hey all.  I followed the steps here and get a different issue.  here's the output I get from terminal:
>  Error: The file "jre-1_5_0_05-linux-i586.bin" does not exist.
It was downloaded to the desktop and I got through the rest of the steps just fine.

any ideas?

---

### Post by bored2k on 2005-10-09
You need to be in the Desktop dir. By default, the shell starts in Home. Type 
> cd Desktop then retry :D.

---

### Post by KeithO on 2005-10-09
guess thats a pretty silly thing to overlook.  Here's the result:
> bpad@bpad:~/Desktop$ sudo apt-get install fakeroot java-package
Password:
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
java-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bpad@bpad:~/Desktop$ fakeroot make-jpgk jre-1_5_0_04-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpgk: command not found

---

### Post by bored2k on 2005-10-09
You got a typo. It's make-jpkg, not make-jpgk.

---

### Post by KeithO on 2005-10-09
Yet another silly mistake to make.  Ok.  So with correct spelling, I get told I should do this as a non-root user.  
> bpad@bpad:~/Desktop$ sudo make-jpkg jre-1_5_0_04-linux-i586.bin
You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.

seems weird but is this normal? (side note is this is really my 1st weekend playing with linux.)

---

### Post by bored2k on 2005-10-09
Notice how in my instructions I did not tell anyone to use sudo. This step needs to be done by the regular user.

1st week and making your own packages? The force is strong with you :D.

---

### Post by timmyp on 2005-10-09
wrong file... problem solved^^* 
I'm beginning to like ubuntu.. hehe...

-----------------------------------------------------------------------------------------------------------------------------------------
1st day (2nd hour to be exact) with ubuntu (or any type of linux) here so please spare with me...

I'm getting the same error...

tim@thinkpad:~/Desktop$ fakeroot make-jpkg <wrong file name>.bin
Creating temporary directory: /tmp/make-jpkg.XXXX0P8loC
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
What should I do? Thanks in advance.

---

### Post by KeithO on 2005-10-09
hey! I got it.  I appreciate the assistance, bored2k.  thanks.

---

### Post by bored2k on 2005-10-09
[QUOTE=KeithO]hey! I got it.  I appreciate the assistance, bored2k.  thanks.[/QUOTE]
À votre service.


Heh, I just broke our "English" only rule.

---

### Post by jon_gunnar on 2005-10-10
[QUOTE=FL!PNEUS]You downloaded the JDK with NetBeans-bundle. Download the JDK only.[/QUOTE]
Well, I get the same messages and my version is not with the NetBeans-bundle. Have tried both the jdk and jre.
Built the same packages without problems under 5.04.
Running Breezy RC1 amd64 now.

---

### Post by Alexis_B on 2005-10-11
Hi all, I am new with deb too and I had the following message too
> 

Creating temporary directory: /tmp/make-jpkg.XXXX0P8loC
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done



I've just find a solution to make the dpkg
My architecture is a Pentium IV  and dpkg-architecture give me :
```

DEB_BUILD_ARCH=i386
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_ARCH_CPU=i386
DEB_BUILD_GNU_CPU=i486
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=i486-linux-gnu
DEB_HOST_ARCH=i386
DEB_HOST_ARCH_OS=linux
DEB_HOST_ARCH_CPU=i386
DEB_HOST_GNU_CPU=i486
DEB_HOST_GNU_SYSTEM=linux-gnu
DEB_HOST_GNU_TYPE=i486-linux-gnu

```
And unfortunatly  /usr/share/java-package/sun-j2re.sh looking for i386-linux archi.

so I've execute the following command :
```
DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jdk-1_5_0-linux-i586.bin
```

and it worked good :) 

hope it may help you, good luck

---

### Post by zeroverse on 2005-10-11
I have looked over this forum very carefully reading each post for clues...because I can't get my package made.

Several other people have the same problem but the "solutions" here don't seem to be the answer.

Here's the problem:

> No matching plugin was found.

I previously had the gcc problem but I read another similar post that suggested doing "sudo aptitude install build-essential".  That fixed that problem.

Then I encounted the "No matching plugin was found" problem.  I downloaded the  "java-common" files as suggested.  No dice.
I have tried to specify the DEB BUILD TYPE (see above post).  No dice.

I'm running a fully updated Breezy install i386 on an AMD64 processor (I didn't want to deal with 64bit version problems). Here's my existing java version info:
> java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)


Thanks for your help in advanced.

---

### Post by chadwick359 on 2005-10-12
Also running, breezy, and also getting the plugin error. Glad I found this thread, though.

---

### Post by TuckWat on 2005-10-12
I too have tried everything in this thread except changin the "DEB_BUILD_GNU_TYPE", and still receive the  >  No matching plugin was found.
Removing temporary directory: done


---

### Post by chadwick359 on 2005-10-12
Okay, I've tried this with both the JDK and the JRE, with both .24 and .26 of java-package, and still no dice. Any help would be really appreciated, I need 1.5 for my coding homework!

---

### Post by TuckWat on 2005-10-13
Well I'm one step closer... I edited the  /usr/share/java-package/sun-j2sdk.sh from i386 to powerpc, and then I ran > fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin which appeared to be working correctly. Until this message: > Unpacking...
Checksumming...
0
0
Extracting...
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 336: ./install.sfx.8019: cannot execute binary file
mkdir: cannot create directory `/etc/.java': Permission denied
mkdir: cannot create directory `/etc/.java/.systemPrefs': No such file or directory
touch: cannot touch `/etc/.java/.systemPrefs/.system.lock': No such file or directory
chmod: cannot access `/etc/.java/.systemPrefs/.system.lock': No such file or directory
touch: cannot touch `/etc/.java/.systemPrefs/.systemRootModFile': No such file or directory
chmod: cannot access `/etc/.java/.systemPrefs/.systemRootModFile': No such file or directory
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 603: cd: jdk1.5.0_05: No such file or directory
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 359: /etc/mailcap: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 507: /usr/share/mime-info/java-archive.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 508: /usr/share/mime-info/java-archive.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 509: /usr/share/mime-info/java-archive.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 510: /usr/share/mime-info/java-archive.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 511: /usr/share/mime-info/java-archive.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 512: /usr/share/mime-info/java-archive.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 515: /usr/share/mime-info/java-archive.mime: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 516: /usr/share/mime-info/java-archive.mime: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 519: /usr/share/application-registry/java-archive.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 520: /usr/share/application-registry/java-archive.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 521: /usr/share/application-registry/java-archive.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 522: /usr/share/application-registry/java-archive.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 523: /usr/share/application-registry/java-archive.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 524: /usr/share/application-registry/java-archive.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 507: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 508: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 509: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 510: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 511: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 512: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 515: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 516: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 519: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 520: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 521: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 522: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 523: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/tuckwat/Desktop/jdk-1_5_0_05-linux-i586.bin: line 524: /usr/share/application-registry/java-web-start.applications: Permission denied

Done.

Testing extracted archive...
Invalid size (1 MB) of extracted archive. Probably you have not
enough free disc space in the temporary directory. Note: You can
specify an alternate directory by setting the environment variable
TMPDIR.


Any idea what the next step is?? 

Thanks

---

### Post by paulo.sebastiao on 2005-10-13
[QUOTE=TuckWat]Well I'm one step closer... I edited the  /usr/share/java-package/sun-j2sdk.sh from i386 to powerpc, and then I ran  which appeared to be working correctly. Until this message: 

Any idea what the next step is?? 

Thanks[/QUOTE]

Hi there, I had the same permission denied 'problems'. I guess they're not really problems, they're just consequence of fakeroot. We don't want Java installer to create all the dirs, we want dkpg to do it.

As for the last error concerning the invalid size of the archive, I can't remember if i had it :(

Oh well, but for what counts, don't worry about the 'permission denied' msg's.

Cheers!

---

### Post by Neobuntu on 2005-10-13
Breezy and this works.

Hello boys and girls!

I'm running the new (today) released Breezy that I updated from the preview install CD. I just made the jump form MEPIS to ubuntu. Yea.

IT WORKED FOR ME ! Notes below:

I just used the Terminal off the Applications > Accessories > Terminal menu (with cut and paste.)

In Synaptic under   Settings > Repositories   I just clicked add, and then checked the Universe and Multiverse check boxes and reloaded to make java packages searchable/available/installable.

Commentary: While fretting (%$#$) about the fact Java is seperate from the main unbuntu, I realize it's political or legal. What's ironic is all the open (multi platform) function is the whole point, then here it has a CLOSED type license with the (%$^%$) pages of license fodder.  I'm afraid it's all a veiled lock-in strategy.  So it's, you can unlock your program to any browser/platform but get locked into Sun. I guess you know this so I'll stop there.

"Oh man, You got me monologing!" (Reference from The Incredibles)

Allright. Next I think, there was WAY too much confusion about the name of the %$#% file. Not "....RPM". Not "..RPM.bin", but just "jre-1_5_0_05-linux-i586.bin".

That's  -   jre-1_5_0_05-linux-i586.bin

What a stupidly overly long name. I suggest you cut and paste. Don't make these things harder than they need to be. The Sun download pages suck.

Obviously I (personally) just wanted the "jre" to get java working in firefox.

It works great. I am thankful to the ubuntu community.

---

### Post by sphinx on 2005-10-14
Just letting you know about a problem I had, and solved, when trying to create my own sun-jdk package useing the instructions in this thread. No matter what I tried I still go the same " No matching plugin was found." message.

It turns out the 'java-package' package needs the jdk from sun to have its original file name. I had renamed the jdk-1_5_0_05-linux-i586.bin to something else as I had used wget to obtain the file and had specified a filename to save the file as.

Aparently java-package needs the correct filename of the sun jdk to work.

Hope this tidbit helps if anyone else hits this situation.

---

### Post by zorkerz on 2005-10-14
sorry didn't mean to post this
don't know how to delete it

---

### Post by Minger on 2005-10-14
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Um...thats what I get when I try 
sudo apt-get install fakeroot java-package

(or just about a ton of other sudo commands for installing too)

---

### Post by sphinx on 2005-10-17
[QUOTE=Minger]Um...thats what I get when I try 
sudo apt-get install fakeroot java-package

(or just about a ton of other sudo commands for installing too)[/QUOTE]

This might mean that another packageing manager is open. Are you running Synaptic at the same time? (or Update Manager, or the Add Application dialog)

Thats the error you would get if you were. Only one package manager can run at a time.

---

### Post by zorkerz on 2005-10-17
Im also getting this error.  
"Invalid size (1 MB) of extracted archive. Probably you have not
enough free disc space in the temporary directory. Note: You can
specify an alternate directory by setting the environment variable
TMPDIR."
I have plenty of space on my harddrive.  Is there some limit on the size of the temp directory. Mine is pretty empty.  How would i specify an alternate directory, and would that do me any good?  Thanx

---

### Post by TuckWat on 2005-10-17
Well i've found out that my problem,
"Invalid size (1 MB) of extracted archive. Probably you have not
enough free disc space in the temporary directory. Note: You can
specify an alternate directory by setting the environment variable
TMPDIR.""
was due to me having a powerpc. Am I right that having an ibook means that I cannot compile java 1.5?

---

### Post by zorkerz on 2005-10-18
[QUOTE=TuckWat]was due to me having a powerpc. Am I right that having an ibook means that I cannot compile java 1.5?[/QUOTE]

I don't have a power pc and im gettng the same error.  I have an intel pentium M.

---

### Post by Cyrus on 2005-10-18
I have so many problems with installing Java on my system:

First I could not install the java-package. I have my source.list like that now:
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
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

With these settings it could not find the package. So I manually installed a lot of other stuff, I don't even know what I installed

When I am now entering
```
sudo apt-get install java-package fakeroot
```
I get these results:
```
Reading package lists... Done
Building dependency tree... Done
java-package is already the newest version.
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-j2sdk1.5 (1.5.0) ...

Setting up sun-j2sdk1.5debian (0.5) ...
```
After that I try to
```
fakeroot make-jpkg jdk-1_5_0_03-linux-i586.bin
```
with this result:
```
Creating temporary directory: /tmp/make-jpkg.XXXXfHXiuT
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

```
I tried out so much, but I just don't know what to do know. Do you have any ideas?

---

### Post by mesut322 on 2005-10-18
For those of you encountering the following problem:

Creating temporary directory: /tmp/make-jpkg.XXXXfHXiuT
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

Apply the following command:

**DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin**

and your sun-j2re1.5_1.5.0+update05_i386.deb package will be created.

---

### Post by Cyrus on 2005-10-19
Yes, that worked. I have seen the documentation right after I posted my problem. Seriously this was an annoying day yesterday - why is this so complicated? I am new to the world of Linux and had so many troubles to get it actually working - first Ubuntu itself, than Java.

---

### Post by geoffDeGeoffGeoff on 2005-10-20
does anybody know how to get rid of the 'no matching plugin' problem on a powerpc?
this is boring me now...

---

### Post by sbassi on 2005-10-24
Thats nice, but, why there is no .deb posted somewhere?
I could host it, but I don't have that file :(

---

### Post by manicka on 2005-10-24
[QUOTE=sbassi]Thats nice, but, why there is no .deb posted somewhere?
I could host it, but I don't have that file :([/QUOTE]

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/pool/non-free/java/sun-j2re1.5_1.5.0%2bupdate05_i386.deb](http://antesis.freecontrib.org/mirrors/ubuntu/plf/pool/non-free/java/sun-j2re1.5_1.5.0%2bupdate05_i386.deb)

---

### Post by funkenstein on 2005-10-26
Mate.... I can't even begin to describe the joy you have brought to my heart. *wipes tear* I see images of children dancing happily, old folks clapping and laughing, peace on earth, end to poverty and now, java working like a dream on my 64bit Breezy. Life is good, the birds are singing and the sun is shining.

Thank you so much.

/edit - Disclaimer:
Assuming that the repos are working, that you have gcc installed and that lady luck is smiling, of course. :KS

---

### Post by tomach on 2005-10-26
hmmm...im also cant install java plugins for ex for firefox....im searching for it and cant find ...i assume that there arent any plugins for java for amd64???

---

### Post by JuanC on 2005-11-13
I download jre-1_5_0_05-linux-amd64.bin and there is no java plugin for firefox.

---

### Post by Frag on 2005-11-19
I know this might seem strange. I had the same "plugin not found" error. Since i was in my home folder, just moved the file to another directory in my own Home folder (in my case i moved it  to /JAVA), and it just worked. Dont ask me why it did, but to those of you who have tried all of those steps, and really need java, its worth a try. I mean, if it worked with me, it might work with you :razz:

---

### Post by WelterPelter on 2006-02-24
Worked perfectly for me. Important to delete the gcj package first, though. 
Thanks!:-D

---

### Post by snosrap on 2006-02-24
[QUOTE=bored2k]I have pasted this same trick numerous times already (half tired of doing it too), but now that Sun Java 1.5 is **no** longer available on backports I thought I'd post a HOWTO about it.
[list=1]
[*] [**_Download_** Java 2 Platform Standard Edition 5.0]("http://java.sun.com/j2se/1.5.0/download.jsp")
[*] There, select one of these:
[LIST]
[*]Download JDK 5.0 Update 5
[*]Download JRE 5.0 Update 5
[/LIST]
[*] After you have **reviewed** and **accepted** the License Agreement, **download** Linux self-extracting file (the one with the **[color=blue].bin**[/color] extension).
[*] In sequence, execute these commands in Terminal mode (Applications -> System Tools -> Terminal):```
sudo apt-get install [fakeroot java-package]("http://www.ubuntuguide.org/#extrarepositories")
```
[*] ```
fakeroot make-jpkg *downloaded_package_name**.bin**
```*
* To get the name of the newly created debian package, let's do:[*] ls


* Now to install it :
[*] sudo dpkg -i newly_created_package**[color=red].deb**[/color] (whatever the newly Sun- DEBian package is named).[/list]

* **Hoary: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)**
*** Works on *Breezy* too.**[/QUOTE]
Followed your instructions but got the following message when entering the first command in terminal mode:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

Any suggestions

---

### Post by jon_gunnar on 2006-02-25
[QUOTE=snosrap]Followed your instructions but got the following message when entering the first command in terminal mode:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

Any suggestions[/QUOTE]

Its found in 
jon@localhost:~$ apt-cache show java-package
Package: java-package
Priority: optional
Section: multiverse/misc

So, do you have multiverse enablebled in you're sources.list

---

### Post by Pekz0r on 2006-03-28
What does the following warnings mean?

dpkg-shlibdeps: warning: could not find path for libX11.so.6
dpkg-shlibdeps: warning: could not find path for libX11.so.6
dpkg-shlibdeps: warning: could not find any packages for  (libX11.so.6)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path , dependency field Depends)

(it was much more than this, but they where very sililar)

---

### Post by gurjit on 2006-04-01
Im sorry i saw this psot in this thread already but mine is slightly different here it is:

(notice that i do not use sudo)

gurjit@UBUNTU:~/Desktop$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.
gurjit@UBUNTU:~/Desktop$



Any Ideas?
Thanks in Advance

Gurjit

[COLOR="DarkRed"]
I dont know if thsi helps but i downloaded the .bin file to my desktop.[/COLOR]

---

### Post by gurjit on 2006-04-01
up , i really need to get this working.

Thanks in Advance
Gurjit

---

### Post by Bpa on 2006-04-25
[QUOTE=bored2k][http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Retry[/QUOTE]


I've edited the repositories source.list to allow for universe, multiverse, and backports, but it still says package not found after excuting the first line:

"sudo apt-get install fakeroot java-package"

btw what exactly is fakeroot? I don't understand that part at all.

---

### Post by TitusDalwards on 2006-04-26
[http://www.java.com/en/download/manual.jsp]("http://www.java.com/en/download/manual.jsp")

in this site download **jre-1_5_0_06-linux-i586.bin** file and then:
```
chmod +x jre-1_5_0_06-linux-i586.bin
```
```
sudo apt-get install fakeroot java-package java-common
```
```
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
```
```
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
```

could you please try these.

---

### Post by BayGuy27 on 2006-05-11
When I run the command **fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin**, the DEB package is not created. I tried **ls** as well and it is not listed. Therefore, the next command cannot find the DEB package to install. Here is the fakeroot command result:

--------------------------------------------------------------
dave@linux:~$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXwdqOKL
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done
--------------------------------------------------------------

Please help if any of you can!

Dave

---

### Post by BobSongs on 2006-05-12
[QUOTE=BayGuy27]Please help if any of you can!

Dave[/QUOTE]
```
sudo apt-get install gcc
```

That's it.

---

### Post by t_ras on 2006-11-15
I don't know if it was posted in this thread but (after looking almost alll of it) without understanding why I get "No matching plugin was found java" even when trying  $DEB_BUILD_GNU_TYPE = linux-x86_64 (or something like it)
I looked at /usr/share/java-package/sun-j2sdk.sh
and I noticed I should be downloading jdk-1_5_0-linux-amd64.bin which seems to be different from x64_86.
After d/l the AMD64 package (from same downloading page) it work fine.

So if you are using AMD64 try it.
Hoped I'm helping...:)

---

### Post by Jebus Christ on 2007-11-08
Hrrmmm  i'm getting this:

mike@mike-desktop:~/Desktop$ fakeroot make-jpkg jre-1_5_0_13-linux-i586.bin
The program 'fakeroot' is currently not installed.  You can install it by typing:
sudo apt-get install fakeroot
bash: fakeroot: command not found

what exactly is this fakeroot thing exactly?

---

### Post by gerananda on 2008-05-02
> **statsministern said:**
> Creating temporary directory: /tmp/make-jpkg.XXXXiGwUre
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

What to do when you get this message after fakeroot? Running Breezy.


Hi there,

I am getting exactly the same message ("... no matching plugin was found") after installing Java's JRE and running the fakeroot make-jpkg yada yada. What I find curious is that previously I installed the jre and even the browsers recognize the plugins have been installed. Any thoughts..?=

---

### Post by gerananda on 2008-05-02
> **Jebus Christ said:**
> Hrrmmm  i'm getting this:

mike@mike-desktop:~/Desktop$ fakeroot make-jpkg jre-1_5_0_13-linux-i586.bin
The program 'fakeroot' is currently not installed.  You can install it by typing:
sudo apt-get install fakeroot
bash: fakeroot: command not found

what exactly is this fakeroot thing exactly?


sup!

this fakeroot is kinda a sudo, it seems this make-jpkg can do some serious damage in your computer if run as root, so the work around to discourage you from running it as root is that you must run it as a regular user using fakeroot. that's "all" I know..

---

