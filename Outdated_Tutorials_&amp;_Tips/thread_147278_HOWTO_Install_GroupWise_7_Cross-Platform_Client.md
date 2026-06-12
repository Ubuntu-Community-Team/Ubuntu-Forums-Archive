---
title: "HOWTO: Install GroupWise 7 Cross-Platform Client"
date: 2006-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ryan-au on 2006-03-19
I recently converted from a straight Debian install to Ubuntu and GroupWise was a critical application I needed running.  Following are the steps I took to get it running successfully, along with the errors I encountered along the way.

I hope these instructions may help someone and that the errors I have posted may assist people who search for them in the future, as I had a hard time finding anything useful about them :)

I am using Novell GroupWise 7.0.1 (Support Pack 1) Public Beta on Ubuntu 5.10 i386 (Breezy Badger).

--
**UPDATE**: Have now confirmed this to work with 7.0.1 r4 (2006-03-30) - you will need to use Sun J2RE 1.5 Update 06 to correct the HotSpot errors.
--

**1: In order to facilitate pulling in some more packages later, add an official Debian apt source and do an 'apt-get update', in my case I used:  **
```
deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) testing main contrib non-free
```

**2: Convert the GroupWise client RPM to a DEB package using alien, this is left as an excercise for the reader, but simply:**
```
apt-get install alien
alien -d {RPM}
```

**3: If you now try to install the GroupWise .deb package, you will get the following error:**
> root@ubuntu:/home/ryan# dpkg -i novell-groupwise-gwclient_7.0.1-20060209_i386.deb
Selecting previously deselected package novell-groupwise-gwclient.
(Reading database ... 56673 files and directories currently installed.)
Unpacking novell-groupwise-gwclient (from novell-groupwise-gwclient_7.0.1-20060209_i386.deb) ...
dpkg: dependency problems prevent configuration of novell-groupwise-gwclient:
 novell-groupwise-gwclient depends on libasound2 (>> 1.0.10); however:
  Version of libasound2 on system is 1.0.9-2.
 novell-groupwise-gwclient depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 novell-groupwise-gwclient depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing novell-groupwise-gwclient (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 novell-groupwise-gwclient

**4: We need to install a few extra packages, but firstly we also have to remove the failed GroupWise install:**
```
apt-get remove novell-groupwise-gwclient
apt-get install libstdc++5 libasound2 libgcc1
```

**5: Install the client again and it will install without any problems:**
> root@ubuntu:/home/ryan# dpkg -i novell-groupwise-gwclient_7.0.1-20060209_i386.deb
Selecting previously deselected package novell-groupwise-gwclient.
(Reading database ... 56684 files and directories currently installed.)
Unpacking novell-groupwise-gwclient (from novell-groupwise-gwclient_7.0.1-20060209_i386.deb) ...
Setting up novell-groupwise-gwclient (7.0.1-20060209) ...

**6: If you try and run it now, you'll get the following error:**
> ryan@ubuntu:~$ /opt/novell/groupwise/client/bin/groupwise.sh
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

**7: The JRE that ships with the client is a little wonky, so we'll replace it with an official Sun one.**

On Debian based systems, this is best done by making a Debian package:
```
apt-get install java-package
```

**8: Download the official Sun J2RE, the one I'm using for this example is available here:**

[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

Then I'm clicking on the "JRE 5.0 Update x" link and selecting the "Linux self-extracting file" -  you'll end up with a .bin file once complete.

**9: Then we create the Debian package using the file you downloaded, in my case the command is:**

(must be a normal user)
```
ryan@ubuntu:~$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
```

**10: You'll end up with a .deb file, install it.**
> root@ubuntu:/home/ryan# dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
Selecting previously deselected package sun-j2re1.5.
(Reading database ... 58630 files and directories currently installed.)
Unpacking sun-j2re1.5 (from sun-j2re1.5_1.5.0+update06_i386.deb) ...
Setting up sun-j2re1.5 (1.5.0+update06) ...

**11: Now, link the new JRE for GroupWise to use:**
```
root@ubuntu:/home/ryan# cd /opt/novell/groupwise/client/
root@ubuntu:/opt/novell/groupwise/client# mv jre jre-orig
root@ubuntu:/opt/novell/groupwise/client# ln -s /usr/lib/j2re1.5-sun/ jre
```

**12: Now when you start the client it will load, login either in online or caching mode and when the message list is displayed, you will see this error:**
> ryan@ubuntu:~$ /opt/novell/groupwise/client/bin/groupwise.sh
Error: Failed to load /home/ryan/.webrenderer/linux/corecomponents/libgtksuperwin.so
null
Error: Failed to load /home/ryan/.webrenderer/linux/corecomponents/libgtkxtbin.so
null
Error: Failed to load /home/ryan/.webrenderer/linux/corecomponents/libgtkembedmoz.so
null
Error: Failed to load /home/ryan/.webrenderer/linux/corecomponents/libgtkxtbin.so
null
Error: Failed to load.
null
Exception in thread "ControlQueue" java.lang.UnsatisfiedLinkError: setMozPath
        at com.webrenderer.linux.NativeMozillaLibrary.setMozPath(Native Method)
        at com.webrenderer.linux.NativeMozillaLibrary.a(NativeMozillaLibrary.java)
        at com.webrenderer.linux.j.task(j.java)
        at com.webrenderer.linux.ControlQueue.run(ControlQueue.java)

You will probably now have a hung program and prompt.  CTRL-Z to background it.

Ensure you kill the groupwise processes: issuing 'ps waux' you will see near the bottom, something like:
```
ryan     32289  0.0  0.1   3800  1320 pts/0    T    10:21   0:00 /bin/bash /opt/novell/groupwise/client/bin/groupwise.sh
ryan     32290 28.7  6.5 388664 68304 pts/0    Tl   10:21   0:05 /opt/novell/groupwise/client/bin/groupwise
```

kill -9 both of these.

**13: If we look at the library dependencies of the first error, we can see some missing libraries:**
> root@ubuntu:/home/ryan# ldd /home/ryan/.webrenderer/linux/corecomponents/libgtksuperwin.so
        linux-gate.so.1 =>  (0xffffe000)
        libgtk-1.2.so.0 => not found
        libgdk-1.2.so.0 => not found
        libgmodule-1.2.so.0 => not found
        libglib-1.2.so.0 => not found
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f55000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb7f4c000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7f3f000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7e7f000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e5d000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d2f000)
        /lib/ld-linux.so.2 (0x80000000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7d2c000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7d27000)

**14: To fix these:**
```
apt-get install libgtk1.2 libglib1.2
```

**15: Run the client again, and it should all be working perfectly!**

---

### Post by ponchorage on 2007-08-22
I'm on Feisty 7.04. I've got Groupwise installed. I don't get any errors when running from the command line (already resolved link issues). However, after entering my password at the prompt, the main window comes up and everything is grayed out. Anybody else seeing this?

---

### Post by TalioGladius on 2007-10-04
I'm getting this error:

 /opt/novell/groupwise/client/bin/groupwise-bin: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory

---

### Post by TalioGladius on 2007-10-05
bump

---

### Post by kvonb on 2007-10-05
Would libjvm.so be java virtual machine?

Do you have Java installed?

Just a guess ;)

---

### Post by TalioGladius on 2007-10-05
> **kvonb said:**
> Would libjvm.so be java virtual machine?

Do you have Java installed?

Just a guess ;)I believe yes, and yes.  I've installed everything java I can find and followed the directions completely.

This is really annoying.  :(

---

### Post by aklein24 on 2007-10-05
> **TalioGladius said:**
> I'm getting this error:

 /opt/novell/groupwise/client/bin/groupwise-bin: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory

Hello, I had this problem as well... The issue is that the instructions do not tell you how to link to any version of java other than the one he uses. Here's how I fixed it.

navigate to opt/novell/groupwise/client 

**cd /opt/novell/groupwise/client**

delete the current symbolic link:
[B]
rm jre[/B]

create new symbolic link, in my case:

** sudo ln -s /usr/lib/jvm/java-6-sun/jre**

as in 

**sudo ln -s /usr/lib/"YOUR JRE DIRECTORY"**

but it may be different for you. Use the file browser and navigate to the /usr/lib folder and look for jvm or something to that effect. Inside that folder you'll find some sort of Java-version-sun folder, inside that you should find the jre folder. Use this in the ln -s command as I shown above.

hope it works

-Andy

EDIT for the record, another common problem that pops up and happened to me is that compiz/beryl conflict with some java enabled apps, namely groupise, and will prevent loading. Groupwise will seemingly hang with a gray window, when it's really a problem with java. I have yet to find a work around other than to disable compiz/beryl

---

### Post by TalioGladius on 2007-10-05
> **aklein24 said:**
> Hello, I had this problem as well... The issue is that the instructions do not tell you how to link to any version of java other than the one he uses. Here's how I fixed it.

navigate to opt/novell/groupwise/client 

**cd /opt/novell/groupwise/client**

delete the current symbolic link:
[B]
rm jre[/B]

create new symbolic link, in my case:

** sudo ln -s /usr/lib/jvm/java-6-sun/jre**

as in 

**sudo ln -s /usr/lib/"YOUR JRE DIRECTORY"**

but it may be different for you. Use the file browser and navigate to the /usr/lib folder and look for jvm or something to that effect. Inside that folder you'll find some sort of Java-version-sun folder, inside that you should find the jre folder. Use the ln -s command as I showed above.

hope it works

-Andy
I freaking love you.  :guitar:

Sadly it doesn't work with beryl enabled though...

---

### Post by Chewmanfoo on 2007-10-17
Thanks! Your instructions were very clear and worked perfectly.

---

### Post by moted on 2007-12-07
> **ponchorage said:**
> I'm on Feisty 7.04. I've got Groupwise installed. I don't get any errors when running from the command line (already resolved link issues). However, after entering my password at the prompt, the main window comes up and everything is grayed out. Anybody else seeing this?

I'm running 7.10, Follow the same instructions and am getting the exact same error you descried.  Has anyone else seen this or fixed this?

---

### Post by mrmonkeyman on 2008-01-10
I was able to install it on Gutsy, I used TalioGladius instructions on linking the java since I use icedtea java. I noticed that unlike on the windows groupwise, I cannot right click and export a calendar. Anyone know how I can do that on the linux client?

---

### Post by agoodno on 2008-01-11
Got it to work on Gutsy Gibbon by modifying the instructions in these ways (in order of install):

**Groupwise download**
1) You have to login to download but this is the file I used, on a page titled "GroupWise 7 SP2 Linux Client US and MULTI 7.0.2":
    ```
gw702clnxus.tar.gz
```

**Extra libraries**
1) I only installed this library because the others seemed to install too much (might regret this later....):
    ```
sudo apt-get install libstdc++5
```

**Java installation**
1) I just installed the normal Sun JDK:
    ```
sudo apt-get sun-java5-jdk
```
    but you could also do:
    ```
sudo apt-get sun-java5-jre
```

2) My symbolic link looked like:
    ```
cd /opt/novell/groupwise/client
sudo ln -s /usr/lib/jvm/java-1.5.0-sun/jre jre
```

**Fix setMozPath error**
1) Using the statement from this tutorial failed with this error:

    ```
sudo apt-get install libgtk1.2 libglib1.2

	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	Some packages could not be installed. This may mean that you have
	requested an impossible situation or if you are using the unstable
	distribution that some required packages have not yet been created
	or been moved out of Incoming.
	The following information may help to resolve the situation:

	The following packages have unmet dependencies:
	  libgtk1.2: Depends: libglib1.2ldbl (>= 1.2.10-18) but it is not going to be installed
	E: Broken packages
```

   So instead, I used:

    ```
sudo apt-get install libglib1.2ldbl libgtk1.2 libgtk1.2-common
```

I am now able to run groupwise.sh.

Andy

---

### Post by mrmorris on 2008-02-12
> **moted said:**
> I'm running 7.10, Follow the same instructions and am getting the exact same error you descried.  Has anyone else seen this or fixed this?

I had the same issue. It appears to be a known Compiz/Java glitch and is suppose to be fixed. In any event, I got it to work by simply using Java 6 JRE rather than the Java 5 mentioned in the howto.

Good luck,
/Casper

---

### Post by mfinn999 on 2008-06-23
> **mrmorris said:**
> I had the same issue. It appears to be a known Compiz/Java glitch and is suppose to be fixed. In any event, I got it to work by simply using Java 6 JRE rather than the Java 5 mentioned in the howto.

Good luck,
/Casper

Just make sure you remove the symbolic link to your JRE before you upgrade the GroupWise client.  The GroupWise package will happily downgrade whatever JRE you're pointing at.  You need the 1.6.0x JRE to avoid the blank windows issue with Beryl/Compiz.

---

### Post by tech4 on 2008-06-24
> **mfinn999 said:**
> Just make sure you remove the symbolic link to your JRE before you upgrade the GroupWise client.  The GroupWise package will happily downgrade whatever JRE you're pointing at.  You need the 1.6.0x JRE to avoid the blank windows issue with Beryl/Compiz.
  

How do you remove the symbolic link? Where is that done? Even though I have been using Ubuntu for awhile I am still new to the OS. The only other issue is when I open an HTML formatted email Groupwise freezes up.

---

### Post by tech4 on 2008-06-24
It seems running this line "sudo apt-get install libglib1.2ldbl libgtk1.2 libgtk1.2-common" in term fixed my html problem.

---

### Post by ironhorse7 on 2008-08-22
Just got it to work with groupwise 7.0.3.  I downloaded java 6 though.  Just thought I would let you all know it works.

---

### Post by Geekboy on 2008-09-09
I have Groupwise working also.  I just have a simple question.

How do I create a launcher for this?

---

### Post by Geekboy on 2008-09-09
Nevermind.  I got it.

---

### Post by jeremybrooks on 2008-10-31
To fix the gray/blank window at startup with Java 1.5, you have to pass a parameter to the startup script:

/opt/novell/groupwise/client/bin/groupwise.sh -jvm=-Dawt.toolkit=sun.awt.motif.MToolkit

That should be all on one line, with a space separating the groupwise.sh from the -jvm.

---

### Post by rwigle on 2008-12-10
I am running Hardy 8.04

I get this error:

>  /opt/novell/groupwise/client/bin/groupwise-bin: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory


I am very puzzled about the location of libjvm.so

```
rwigle@Dina-Auntie:/opt/novell/groupwise/client$ locate libjvm.so
/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/client/libjvm.so
rwigle@Dina-Auntie:/opt/novell/groupwise/client$ ls -a /usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/client/
.  ..  classes.jsa
r
```

Question 1: Is libjvm.so in that folder or not???

I made a soft link to the 1.6.0.07/jre folder in the client folder, but still get the above error. 

Help...

---

### Post by rwigle on 2008-12-10
I posted the message about libjvm.so not being found. (Hardy Heron)

Not quite sure what the problem was, BUT:

I removed my install of the groupwise client and ALL sun-java6-* using Synaptic.

Reinstalled:

sun-java6-jdk
sun-java6-jre
sun-java6-plugin
sun-java6-fonts
sun-java6-bin
gsfonts-X11

Now reinstall the groupwise client from the deb file, and finally:
```

sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.07/jre /opt/novell/groupwise/client/jre

```
It works!

P.S. I am guessing that my problem is that I tried to install a newer version of java6 `manually' rather than just rely on those that are on the Ubuntu repos. (???)

---

### Post by lenux2005 on 2009-01-14
I am trying to install GroupWise 7 sp3 on 8.10.  When I type the following:

sudo ./install

I get a gui interface for the installation.  I click on "Install GroupWise Client" and I get the following errors:

> glibc >= 2.1.2-11 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
sh-utils >= 2.0-1 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
fileutils >= 4.0-8 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
gawk >= 3.0.4-1 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
textutils >= 2.0-2 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
/bin/sh is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
/bin/sh is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
/bin/sh is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
/bin/bash is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
/bin/sh is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libX11.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libXext.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libXi.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libXp.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libXt.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libXtst.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.0) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.1) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.1.2) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.1.3) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.2) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.2.4) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.3) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libc.so.6(GLIBC_2.3.4) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libdl.so.2 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libdl.so.2(GLIBC_2.0) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libdl.so.2(GLIBC_2.1) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libgcc_s.so.1 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libgcc_s.so.1(GCC_3.0) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libgcc_s.so.1(GLIBC_2.0) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libm.so.6 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libm.so.6(GLIBC_2.0) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libnsl.so.1 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libpthread.so.0 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libpthread.so.0(GLIBC_2.0) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libpthread.so.0(GLIBC_2.1) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libpthread.so.0(GLIBC_2.2) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libpthread.so.0(GLIBC_2.2.3) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libpthread.so.0(GLIBC_2.3.2) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libstdc++.so.5 is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libstdc++.so.5(CXXABI_1.2) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libstdc++.so.5(GLIBCPP_3.2) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
libstdc++.so.5(GLIBCPP_3.2.2) is needed by novell-groupwise-gwclient-7.0.3-20080609.i386
/bin/sh is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libc.so.6 is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libc.so.6(GLIBC_2.0) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libc.so.6(GLIBC_2.1) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libc.so.6(GLIBC_2.1.3) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libc.so.6(GLIBC_2.2) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libc.so.6(GLIBC_2.3) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libc.so.6(GLIBC_2.3.4) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libdl.so.2 is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libdl.so.2(GLIBC_2.0) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libdl.so.2(GLIBC_2.1) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libgcc_s.so.1 is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libgcc_s.so.1(GCC_3.0) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libgcc_s.so.1(GLIBC_2.0) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libm.so.6 is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libpthread.so.0 is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libpthread.so.0(GLIBC_2.0) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libpthread.so.0(GLIBC_2.1) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libpthread.so.0(GLIBC_2.2) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libpthread.so.0(GLIBC_2.3.2) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libstdc++.so.5 is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libstdc++.so.5(CXXABI_1.2) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libstdc++.so.5(GLIBCPP_3.2) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586
libstdc++.so.5(GLIBCPP_3.2.2) is needed by novell-groupwise-gwcheck-7.0.3-20080609.i586

Please help.:(

---

### Post by rwigle on 2009-01-14
Two responses:

1. Why not try the method described in the earlier post. It has been used successfully by a number of people?

If not...

2. I would try installing the standard c development stuff. (Most of the missing files come from them.

Specifically:

sudo apt-get install build-essential linux-libc-dev

---

### Post by lenux2005 on 2009-01-14
Thanks for the info.  The only version that I have access to is 7 sp3.  I also tried sudo apt-get install build-essential linux-libc-dev and it seems that I have that installed already.  Not sure what to do at this point.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
linux-libc-dev is already the newest version.
linux-libc-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  libscrollkeeper0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by rwigle on 2009-01-14
Are you not able to download the package from novell and install as indicated in the links mentioned above? (page 1 of the thread, I think)

I haven't seen the reference to ./install, so your guess is as good as mine.

---

### Post by jmodule on 2009-11-02
I used the instructions above to install the Groupwise client on 9.4, but when I upgraded to 9.10 it wiped out a necessary library, libstdc++5.  Following [these instructions]("http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html"), I downloaded the library package from Jaunty and copied it to the Groupwise client library directory.

```
mkdir /tmp/newlib
cd /tmp/newlib
ar vx ~/downloads/libstdc++5_3.3.6-17ubuntu1_i386.deb
tar xzf data.tar.gz
cd /opt/novell/groupwise/client/lib
sudo cp /home/jfriant/src/new/libstdc++/usr/lib/libstdc++.so.5.0.7 .
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5
rm -rf /tmp/newlib
```

After that Groupwise works again.  Also note that it was fine to use the 32-bit library on my 64-bit machine.

---

### Post by pennstatebadboy on 2010-05-27
I was able to install Groupwise 7 on Ubuntu 10.04. But when I launch the program, it hangs on the "Novell Groupwise 7.0" splash graphic. The bottom of the splash graphic says "Connecting," and little red dots appear in a row as if it's trying to connect but can't.

I'm stuck here, and don't know what to do. Any ideas?

---

### Post by cybermatthieu on 2010-07-09
I had problems installing GroupWise 8.0.1 on my Ubuntu 8.10 64 bit install.

I couldn't "alienate" the rpm:
```

dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

```

All I did was to follow the steps showed in this post:
[http://ubuntuforums.org/showthread.php?t=1420744]("http://ubuntuforums.org/showthread.php?t=1420744")

Basically, I had to specify the -g flag of alien :
```
-g, --generate
           Generate a temporary directory suitable for building a package
           from, but do not actually create the package. This is useful if you
           want to move files around in the package before building it. The
           package can be built from this temporary directory by running
           "debian/rules binary", if you were creating a Debian package, or by
           running "rpmbuild -bb <packagename>.spec" if you were creating a
           Red Hat package.
```

Go in the directory generated.
```
cd novell-groupwise-client-8.0.1HP
```


Then change the architecture in the control file from i386 to amd64.
```
sudo vim debian/control
```
Change the line from :
```
Architecture: i386
```
to
```
Architecture: amd64
```

Then build the package with:
```
sudo ./debian/rules binary
```

And the last step is to install the package:
```
cd ..
sudo dpkg -i novell-groupwise-client_8.0.1HP-89146_amd64.deb

```

Hope this helps a few ;)

Matt

---

### Post by rwigle on 2010-09-07
I installed Groupwise 7.04 to Lucid (64-bit) using the following procedure:

1. download from Novell

2. convert rpm to amd64 (See #29 in this thread)

3. install using dpkg -i novell-groupwise-gwclient_7.0.4-20100314_amd64.deb

4. Fixed libstdc++ issue (see #27 in this thread)

5. The client works, (view mails, send email, archive messages) but I still have the following errors kicked up if I start it in the terminal.

Error: Failed to load /home/rwigle/.novell/groupwise/.webrenderer/linux/corecomponents/libgtksuperwin.so
Error: Failed to load /home/rwigle/.novell/groupwise/.webrenderer/linux/corecomponents/libgtkxtbin.so
Error: Failed to load /home/rwigle/.novell/groupwise/.webrenderer/linux/corecomponents/libgtkembedmoz.so
Error: Failed to load /home/rwigle/.novell/groupwise/.webrenderer/linux/corecomponents/libgtkxtbin.so
Error: Failed to load.

I have only used the client for a while, but it seems to work. I had java installed beforehand, but I did not need to do the linking to java. (Maybe I should?)

** EDIT ** I normally view messages as plain text. If I try to view them as html the client hangs. So I linked to my existing ia32 jre folder as follows:

 ln -s /usr/lib/jvm/ia32-java-6-sun/jre jre

Now "groupwise -debug" starts with the same webrenderer errors I pasted in above. Again, the only problem I have discovered is with html view of messages.

I think it's because there is no libgtk-1.2 package for lucid. Is there a work around or other Suggestions?

---

### Post by PasQty on 2011-03-12
GroupWise 8.0.2 multilangugae, Ubunto 10.10 64bit
i m doing that like this:
apt-get install ia32-libs
apt-get install ia32-sun-java6-bin
apt-get install alien
alien -i --veryverbose --script novell-groupwise-client-8.0.2-90840.i586.rpm 
-i mean install, you can use -t that make tarfile.
cd /opt/novell/groupwise/client
ln -s /usr/lib/jvm/ia32-java-6-sun/jre java

source: [http://www.novell.com/coolsolutions/tip/19592.html](http://www.novell.com/coolsolutions/tip/19592.html)

---

