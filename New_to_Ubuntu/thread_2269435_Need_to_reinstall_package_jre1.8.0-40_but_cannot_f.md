---
title: "Need to reinstall package jre1.8.0-40 but cannot find an archive for it"
date: 2015-03-15
forum: New to Ubuntu
---

### Post by david.williams.425 on 2015-03-15
A website I needed to use told me I needed to install the Java Virtual Machine, so I followed the instructions here: [http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)
I created a new directory in /usr called 'java' and attempted to install it with the tar command.
I now have a warning message (an icon that looks like a red circle with a white minus sign) constantly displayed at the top of my screen. The message says:
=
Unknown Error: <class System Error>
The package jre1.8.0-40 needs to be reinstalled, but I can't find an archive for it. This usually means that your installed packages have unmet dependencies.
=
I get the same message when running sudo apt-get install jre1.8.0-40 from the terminal.

What should I try next?

---

### Post by ian-weisser on 2015-03-15
Are you sure you are running 32-bit?

Instead of using random websites that have stale or broken instructions, I would start at the Ubuntu Wiki.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I would delete or undo all you have downloaded and any changes you have made.
Start fresh with Java packages from the Ubuntu Repositories. Download them from Software Center.

---

### Post by david.williams.425 on 2015-03-15
> **ian-weisser said:**
> Are you sure you are running 32-bit?
That's what System Details says.

> 
Instead of using random websites that have stale or broken instructions, I would start at the Ubuntu Wiki.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

It was the Oracle Java website - not exactly random.

> 
I would delete or undo all you have downloaded and any changes you have made.
Start fresh with Java packages from the Ubuntu Repositories. Download them from Software Center.

I got rid of the folders I metioned with rm and rmdir, but opening the Software Center just gives me a loading screen before it gives up and closes.
Running it from the command line gives the same 'reinstall package jre1.8.0-40, but cannot find an archive' error as well as a few others.  
I also get the error when trying to run apt-get install or apt-get purge as mentioned in the Ubuntu Wiki and the webupd8 site it links to.
Is there a way to add an archive for jre1.8.0-40 and would it help me get around the issue of not being able to run apt-get install?

**NOTE: **
java -version shows I already have java:
=
java version "1.7.0_75"
OpenJDK Runtime Environment (IcedTea 2.5.4) (7u75-2.5.4-1~trusty1)
OpenJDK Server VM (build 24.75-b04, mixed mode)
=
The website that told me I didn't have the Java VM may simply not have been compatible with OpenJDK.

---

### Post by dino99 on 2015-03-16
[https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)

---

### Post by david.williams.425 on 2015-03-16
Thanks, 9d9, but that just links to the same webupd8 site that I tried earlier.
It asks me to install oracle 8, but trying to run apt-get install or open the Software Center just gives me the same error
Here's what my terminal looks like when I try to follow their instructions:
===
>sudo apt-get install oracle-java8-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package jre1.8.0-40 needs to be reinstalled, but I can't find an archive for it.
===
I could add the ppa mentioned above and run apt-get update though.

---

### Post by ian-weisser on 2015-03-16
> **david.williams.425 said:**
> Running it from the command line gives the same 'reinstall package jre1.8.0-40, but cannot find an archive' error as well as a few others.
All those errors are important.
Any one of them may prevent you from installing software packages.
Please show us a complete apt-get output showing all those errors.

> **david.williams.425 said:**
> Is there a way to add an archive for jre1.8.0-40 and would it help me get around the issue of not being able to run apt-get install?
Not until you fix those apt errors.
Apt simply cannot work until all conflicts and other fatal errors are resolved.

> **david.williams.425 said:**
> E: The package jre1.8.0-40 needs to be reinstalled, but I can't find an archive for it.
The package name is not 'jre1.8.0-40' in the Ubuntu repositories, nor in the PPA.
The system is valiantly looking for the wrong name.
Once the other apt errors are fixed, try 'oracle-java8-installer' from the PPA.

---

### Post by david.williams.425 on 2015-03-16
> **ian-weisser said:**
> All those errors are important.
Any one of them may prevent you from installing software packages.
Please show us a complete apt-get output showing all those errors.

The other errors only show up when running software-center. There are no apt errors other than
"E: The package jre1.8.0-40 needs to be reinstalled, but I can't find an archive for it."

> The package name is not 'jre1.8.0-40' in the Ubuntu repositories, nor in the PPA.
The system is valiantly looking for the wrong name.
Once the other apt errors are fixed, try 'oracle-java8-installer' from the PPA.

Catch 22 - I can't install oracle-java8-installer to fix the jre1 error because attempting to run it triggers the jre1 error.

I think I see where the error started though:
===
The Ubuntu repository may call the package oracle-java8-installer, but Oracle.com calls it jre1.8.0_40 (**NOTE - **This has an underscore while the archive Ubuntu is looking for has a dash).
I redownloaded the tarball (jre-8u40-linux-i586.tar.gz) from Oracle's site here: [http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en), and tried to reinstall it from there.
===
However, attempting to extract the package triggers "truncated gzip input' error in Archive Manager. 
This does create a jre1.8.0_40 folder with all the same files, but I don't know what to do with it.
===
I attempted to install the package by using the command > tar zxvf jre-8u40-linux-i586.tar.gz
This created the same folder, but gave the following error:
-
 gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
===
My goal now is to convince Ubuntu to forget about Oracle.com's jre1.8.0-40 package and, hopefully, that will get rid of the error and I can apt-get the package from the Ubuntu repository.
Last time, simply deleting the jre1 folders didn't work. How do I get it to simply stop asking about jre1?

---

### Post by Geoffrey_Arndt on 2015-03-16
maybe it's time to review Ian's post before problem is compounded.  (or one of the other experienced members).

---

### Post by sandyd on 2015-03-16
Can you post the output of
```
dpkg -l | grep "jre\|jdk\|oracle-java"
dpkg -s jre1.8.0-40

```
I haven't used the oracle linux installer, but it seems that it may do someting similar to what ati installer can do - build a package for java on your os and install it. You can't reinstall the thing - because there is no such package in the apt cache/repos. We can just remove the whole thing using dpkg and reinstall using webupd8 method

Just need above commands to check that you won't vaporize your system before removing

---

### Post by david.williams.425 on 2015-03-17
[QUOTE=sandyd;13246911]Can you post the output of
```
dpkg -l | grep "jre\|jdk\|oracle-java"
```
===
iHR jre1.8.0-40                                           1.8.040-1                                           i386         Java Platform Standard Edition Runtime Environment
ii  openjdk-7-jre:i386                                    7u75-2.5.4-1~trusty1                                i386         OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless:i386                           7u75-2.5.4-1~trusty1                                i386         OpenJDK Java runtime, using Hotspot JIT (headless)
===
**NOTE - **all instances of 'jdk' and 'jre' are in red

```

dpkg -s jre1.8.0-40

```
===
Package: jre1.8.0-40
Status: install reinstreq half-installed
Priority: extra
Section: alien
Installed-Size: 99463
Maintainer: -
Architecture: i386
Version: 1.8.040-1
Config-Version: 1.8.040-1
Conffiles:
 /usr/java/jre1.8.0_40/.java/.systemPrefs/.system.lock d41d8cd98f00b204e9800998ecf8427e
 /usr/java/jre1.8.0_40/.java/.systemPrefs/.systemRootModFile d41d8cd98f00b204e9800998ecf8427e
 /usr/java/jre1.8.0_40/.java/init.d/jexec 3a4104cd0a34b5e7e55433a78d9f7721
 /usr/java/jre1.8.0_40/lib/charsets.pack 6ff9967fab9c3c3beb331bd2951dc9e3
 /usr/java/jre1.8.0_40/lib/deploy.pack be0a5fc39fc55d1a2674f45e84d2290c
 /usr/java/jre1.8.0_40/lib/ext/jfxrt.pack 4517939df44879e4a4cf9091f4c9e8cb
 /usr/java/jre1.8.0_40/lib/ext/localedata.pack c6cdb1fc0af0f0a01d6ec3585486e54b
 /usr/java/jre1.8.0_40/lib/javaws.pack 1fb40b342957a86a00093996f7bfe46e
 /usr/java/jre1.8.0_40/lib/jsse.pack 33d5b44adbb3cbd93c15f161e82bb047
 /usr/java/jre1.8.0_40/lib/plugin.pack 008b9f94976decaae5c09c46a6f4ad43
 /usr/java/jre1.8.0_40/lib/rt.pack 98fc43fc4abae8b89bfe5e6ee83096ed
Description: Java Platform Standard Edition Runtime Environment
 The Java Platform Standard Edition Runtime Environment (JRE) contains
 everything necessary to run applets and applications designed for the
 Java platform. This includes the Java virtual machine, plus the Java
 platform classes and supporting files.
 .
 The JRE is freely redistributable, per the terms of the included license.
 .
 (Converted from a rpm package by alien version 8.90.)
===
Thank you! I'm not sure what the dpkg output means, but if I'm clear to remove it, please let me know the command to enter and I think I should be okay.

---

### Post by sandyd on 2015-03-17
Goody good

All seems fine, lets get rid of this thing...

Run
```

sudo dpkg --purge jre1.8.0-40
```

Then, follow the webupd8 method.

---

### Post by david.williams.425 on 2015-03-18
I'm caught in another Catch-22 - the purge command gives me this:
===
dpkg: error processing package jre1.8.0-40 (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 jre1.8.0-40
===
I also looked for the conffiles returned by the dpkg command in my earlier post - there doesn't appear to be a java directory at all in /usr.
There was one that I created earlier - the one where I originally attempted to install the package I downloaded from Oracle's site, but I deleted it with rmdir in another attempt to get rid of jre.
Could manually removing whatever jre folders and files I can before trying purge again help get around this?

---

### Post by dino99 on 2015-03-18
you can use the 'search' function of nautilus (or other file manager) to find the related 'java/jre' files; then delete them

---

### Post by ian-weisser on 2015-03-18
> **david.williams.425 said:**
> Could manually removing whatever jre  folders and files I can before trying purge again help get around  this?

No. It will almost certainly make things worse.
Never remove a file that the package manager placed, unless you know how to replace it.
The package manager expects it's database of files it placed to accurately reflect reality. When the database is shown to be inaccurate, dpkg stops all actions (to avoid doing damage) and waits for the human to discover and fix the problem.


> **david.williams.425 said:**
> 
dpkg: error processing package jre1.8.0-40 (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 jre1.8.0-40

Best option: If you still have, or can obtain, the jre-1.8.0-40 package, you can try reinstalling it so the package manager can remove it cleanly.
Worst option: You can use dpkg --remove --force-reinst-req to simply delete the package entry in dpkg's database...and leave bits of the package scattered all over your system for you to manually clean up.

---

### Post by sandyd on 2015-03-18
> **ian-weisser said:**
> 
Best option: If you still have, or can obtain, the jre-1.8.0-40 package, you can try reinstalling it so the package manager can remove it cleanly.
Worst option: You can use dpkg --remove --force-reinst-req to simply delete the package entry in dpkg's database...and leave bits of the package scattered all over your system for you to manually clean up.
I'm actually curious - if the package is broken, will the java installer still be able to install it again? There is no actual 'package' since it is generated by the jre installer.

> **david.williams.425 said:**
> I'm caught in another Catch-22 - the purge command gives me this:
===
dpkg: error processing package jre1.8.0-40 (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 jre1.8.0-40
===
I also looked for the conffiles returned by the dpkg command in my earlier post - there doesn't appear to be a java directory at all in /usr.
There was one that I created earlier - the one where I originally attempted to install the package I downloaded from Oracle's site, but I deleted it with rmdir in another attempt to get rid of jre.
Could manually removing whatever jre folders and files I can before trying purge again help get around this?
Can you post the output of
```

cat /var/lib/dpkg/info/jre1.8.0-40.list

```

Also - 64 bit or 32 bit?

---

### Post by david.williams.425 on 2015-03-18
> **sandyd said:**
> I'm actually curious - if the package is broken, will the java installer still be able to install it again? There is no actual 'package' since it is generated by the jre installer.

Already tried reinstalling back in post 7.
I tried it again - this time donig the same thing I did originally - creating a usr/java directory and moving the tar file there before installing.
I still get the same error that stopped me before:
===
tar zxvf jre-8u40-linux-i586.tar.gz
-
 gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
===

> 
Can you post the output of
```

cat /var/lib/dpkg/info/jre1.8.0-40.list

```


Um...okay. I hope your scroll wheel is oiled:
===
```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/jre1.8.0-40
/usr/share/doc/jre1.8.0-40/changelog.Debian.gz
/usr/share/doc/jre1.8.0-40/copyright
/usr/java
/usr/java/jre1.8.0_40
/usr/java/jre1.8.0_40/THIRDPARTYLICENSEREADME.txt
/usr/java/jre1.8.0_40/.java
/usr/java/jre1.8.0_40/.java/.systemPrefs
/usr/java/jre1.8.0_40/.java/.systemPrefs/.system.lock
/usr/java/jre1.8.0_40/.java/.systemPrefs/.systemRootModFile
/usr/java/jre1.8.0_40/.java/init.d
/usr/java/jre1.8.0_40/.java/init.d/jexec
/usr/java/jre1.8.0_40/README
/usr/java/jre1.8.0_40/bin
/usr/java/jre1.8.0_40/bin/policytool
/usr/java/jre1.8.0_40/bin/jjs
/usr/java/jre1.8.0_40/bin/keytool
/usr/java/jre1.8.0_40/bin/unpack200
/usr/java/jre1.8.0_40/bin/rmiregistry
/usr/java/jre1.8.0_40/bin/rmid
/usr/java/jre1.8.0_40/bin/orbd
/usr/java/jre1.8.0_40/bin/jcontrol
/usr/java/jre1.8.0_40/bin/javaws
/usr/java/jre1.8.0_40/bin/servertool
/usr/java/jre1.8.0_40/bin/pack200
/usr/java/jre1.8.0_40/bin/tnameserv
/usr/java/jre1.8.0_40/bin/java
/usr/java/jre1.8.0_40/man
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/tnameserv.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/jjs.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/servertool.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/javaws.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/orbd.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/rmiregistry.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/java.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/unpack200.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/policytool.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/pack200.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/rmid.1
/usr/java/jre1.8.0_40/man/ja_JP.UTF-8/man1/keytool.1
/usr/java/jre1.8.0_40/man/man1
/usr/java/jre1.8.0_40/man/man1/tnameserv.1
/usr/java/jre1.8.0_40/man/man1/jjs.1
/usr/java/jre1.8.0_40/man/man1/servertool.1
/usr/java/jre1.8.0_40/man/man1/javaws.1
/usr/java/jre1.8.0_40/man/man1/orbd.1
/usr/java/jre1.8.0_40/man/man1/rmiregistry.1
/usr/java/jre1.8.0_40/man/man1/java.1
/usr/java/jre1.8.0_40/man/man1/unpack200.1
/usr/java/jre1.8.0_40/man/man1/policytool.1
/usr/java/jre1.8.0_40/man/man1/pack200.1
/usr/java/jre1.8.0_40/man/man1/rmid.1
/usr/java/jre1.8.0_40/man/man1/keytool.1
/usr/java/jre1.8.0_40/plugin
/usr/java/jre1.8.0_40/plugin/desktop
/usr/java/jre1.8.0_40/plugin/desktop/sun_java.desktop
/usr/java/jre1.8.0_40/plugin/desktop/sun_java.png
/usr/java/jre1.8.0_40/THIRDPARTYLICENSEREADME-JAVAFX.txt
/usr/java/jre1.8.0_40/release
/usr/java/jre1.8.0_40/COPYRIGHT
/usr/java/jre1.8.0_40/lib
/usr/java/jre1.8.0_40/lib/install.jar
/usr/java/jre1.8.0_40/lib/fonts
/usr/java/jre1.8.0_40/lib/fonts/LucidaSansDemiBold.ttf
/usr/java/jre1.8.0_40/lib/fonts/LucidaTypewriterBold.ttf
/usr/java/jre1.8.0_40/lib/fonts/fonts.dir
/usr/java/jre1.8.0_40/lib/fonts/LucidaBrightDemiBold.ttf
/usr/java/jre1.8.0_40/lib/fonts/LucidaTypewriterRegular.ttf
/usr/java/jre1.8.0_40/lib/fonts/LucidaBrightRegular.ttf
/usr/java/jre1.8.0_40/lib/fonts/LucidaBrightItalic.ttf
/usr/java/jre1.8.0_40/lib/fonts/LucidaBrightDemiItalic.ttf
/usr/java/jre1.8.0_40/lib/fonts/LucidaSansRegular.ttf
/usr/java/jre1.8.0_40/lib/security
/usr/java/jre1.8.0_40/lib/security/cacerts
/usr/java/jre1.8.0_40/lib/security/US_export_policy.jar
/usr/java/jre1.8.0_40/lib/security/blacklist
/usr/java/jre1.8.0_40/lib/security/trusted.libraries
/usr/java/jre1.8.0_40/lib/security/javaws.policy
/usr/java/jre1.8.0_40/lib/security/java.policy
/usr/java/jre1.8.0_40/lib/security/local_policy.jar
/usr/java/jre1.8.0_40/lib/security/blacklisted.certs
/usr/java/jre1.8.0_40/lib/security/java.security
/usr/java/jre1.8.0_40/lib/meta-index
/usr/java/jre1.8.0_40/lib/fontconfig.bfc
/usr/java/jre1.8.0_40/lib/rt.pack
/usr/java/jre1.8.0_40/lib/currency.data
/usr/java/jre1.8.0_40/lib/fontconfig.SuSE.11.properties.src
/usr/java/jre1.8.0_40/lib/jvm.hprof.txt
/usr/java/jre1.8.0_40/lib/jfxswt.jar
/usr/java/jre1.8.0_40/lib/net.properties
/usr/java/jre1.8.0_40/lib/i386
/usr/java/jre1.8.0_40/lib/i386/libprism_sw.so
/usr/java/jre1.8.0_40/lib/i386/libj2pcsc.so
/usr/java/jre1.8.0_40/lib/i386/libprism_common.so
/usr/java/jre1.8.0_40/lib/i386/libkcms.so
/usr/java/jre1.8.0_40/lib/i386/libdcpr.so
/usr/java/jre1.8.0_40/lib/i386/libjsdt.so
/usr/java/jre1.8.0_40/lib/i386/libbci.so
/usr/java/jre1.8.0_40/lib/i386/libsctp.so
/usr/java/jre1.8.0_40/lib/i386/libdecora_sse.so
/usr/java/jre1.8.0_40/lib/i386/libj2gss.so
/usr/java/jre1.8.0_40/lib/i386/libinstrument.so
/usr/java/jre1.8.0_40/lib/i386/libjfxmedia.so
/usr/java/jre1.8.0_40/lib/i386/jli
/usr/java/jre1.8.0_40/lib/i386/jli/libjli.so
/usr/java/jre1.8.0_40/lib/i386/libjavafx_iio.so
/usr/java/jre1.8.0_40/lib/i386/libhprof.so
/usr/java/jre1.8.0_40/lib/i386/libprism_es2.so
/usr/java/jre1.8.0_40/lib/i386/client
/usr/java/jre1.8.0_40/lib/i386/client/Xusage.txt
/usr/java/jre1.8.0_40/lib/i386/client/libjvm.so
/usr/java/jre1.8.0_40/lib/i386/libnio.so
/usr/java/jre1.8.0_40/lib/i386/jvm.cfg
/usr/java/jre1.8.0_40/lib/i386/libfontmanager.so
/usr/java/jre1.8.0_40/lib/i386/libjaas_unix.so
/usr/java/jre1.8.0_40/lib/i386/libawt_headless.so
/usr/java/jre1.8.0_40/lib/i386/libj2pkcs11.so
/usr/java/jre1.8.0_40/lib/i386/libjavafx_font.so
/usr/java/jre1.8.0_40/lib/i386/libnpt.so
/usr/java/jre1.8.0_40/lib/i386/libawt.so
/usr/java/jre1.8.0_40/lib/i386/server
/usr/java/jre1.8.0_40/lib/i386/server/Xusage.txt
/usr/java/jre1.8.0_40/lib/i386/server/libjvm.so
/usr/java/jre1.8.0_40/lib/i386/libjavafx_font_t2k.so
/usr/java/jre1.8.0_40/lib/i386/libjfxwebkit.so
/usr/java/jre1.8.0_40/lib/i386/libjpeg.so
/usr/java/jre1.8.0_40/lib/i386/liblcms.so
/usr/java/jre1.8.0_40/lib/i386/libt2k.so
/usr/java/jre1.8.0_40/lib/i386/libverify.so
/usr/java/jre1.8.0_40/lib/i386/libjsoundalsa.so
/usr/java/jre1.8.0_40/lib/i386/libresource.so
/usr/java/jre1.8.0_40/lib/i386/libnet.so
/usr/java/jre1.8.0_40/lib/i386/libjavafx_font_freetype.so
/usr/java/jre1.8.0_40/lib/i386/libglass.so
/usr/java/jre1.8.0_40/lib/i386/libavplugin-54.so
/usr/java/jre1.8.0_40/lib/i386/libmanagement.so
/usr/java/jre1.8.0_40/lib/i386/libsunec.so
/usr/java/jre1.8.0_40/lib/i386/libunpack.so
/usr/java/jre1.8.0_40/lib/i386/libdeploy.so
/usr/java/jre1.8.0_40/lib/i386/libjsig.so
/usr/java/jre1.8.0_40/lib/i386/libawt_xawt.so
/usr/java/jre1.8.0_40/lib/i386/libnpjp2.so
/usr/java/jre1.8.0_40/lib/i386/libgstreamer-lite.so
/usr/java/jre1.8.0_40/lib/i386/libjawt.so
/usr/java/jre1.8.0_40/lib/i386/libmlib_image.so
/usr/java/jre1.8.0_40/lib/i386/libzip.so
/usr/java/jre1.8.0_40/lib/i386/libjavafx_font_pango.so
/usr/java/jre1.8.0_40/lib/i386/libfxplugins.so
/usr/java/jre1.8.0_40/lib/i386/libjava_crw_demo.so
/usr/java/jre1.8.0_40/lib/i386/libjava.so
/usr/java/jre1.8.0_40/lib/i386/libdt_socket.so
/usr/java/jre1.8.0_40/lib/i386/libavplugin-53.so
/usr/java/jre1.8.0_40/lib/i386/libjsound.so
/usr/java/jre1.8.0_40/lib/i386/libjdwp.so
/usr/java/jre1.8.0_40/lib/i386/libsplashscreen.so
/usr/java/jre1.8.0_40/lib/i386/libjfr.so
/usr/java/jre1.8.0_40/lib/cmm
/usr/java/jre1.8.0_40/lib/cmm/LINEAR_RGB.pf
/usr/java/jre1.8.0_40/lib/cmm/PYCC.pf
/usr/java/jre1.8.0_40/lib/cmm/sRGB.pf
/usr/java/jre1.8.0_40/lib/cmm/CIEXYZ.pf
/usr/java/jre1.8.0_40/lib/cmm/GRAY.pf
/usr/java/jre1.8.0_40/lib/fontconfig.SuSE.11.bfc
/usr/java/jre1.8.0_40/lib/resources.jar
/usr/java/jre1.8.0_40/lib/jce.jar
/usr/java/jre1.8.0_40/lib/jsse.pack
/usr/java/jre1.8.0_40/lib/sound.properties
/usr/java/jre1.8.0_40/lib/fontconfig.SuSE.10.bfc
/usr/java/jre1.8.0_40/lib/management
/usr/java/jre1.8.0_40/lib/management/management.properties
/usr/java/jre1.8.0_40/lib/management/jmxremote.access
/usr/java/jre1.8.0_40/lib/management/snmp.acl.template
/usr/java/jre1.8.0_40/lib/management/jmxremote.password.template
/usr/java/jre1.8.0_40/lib/deploy.pack
/usr/java/jre1.8.0_40/lib/ext
/usr/java/jre1.8.0_40/lib/ext/jfxrt.pack
/usr/java/jre1.8.0_40/lib/ext/meta-index
/usr/java/jre1.8.0_40/lib/ext/sunjce_provider.jar
/usr/java/jre1.8.0_40/lib/ext/zipfs.jar
/usr/java/jre1.8.0_40/lib/ext/dnsns.jar
/usr/java/jre1.8.0_40/lib/ext/localedata.pack
/usr/java/jre1.8.0_40/lib/ext/sunpkcs11.jar
/usr/java/jre1.8.0_40/lib/ext/nashorn.jar
/usr/java/jre1.8.0_40/lib/ext/cldrdata.jar
/usr/java/jre1.8.0_40/lib/ext/sunec.jar
/usr/java/jre1.8.0_40/lib/oblique-fonts
/usr/java/jre1.8.0_40/lib/oblique-fonts/LucidaSansDemiOblique.ttf
/usr/java/jre1.8.0_40/lib/oblique-fonts/LucidaTypewriterOblique.ttf
/usr/java/jre1.8.0_40/lib/oblique-fonts/LucidaTypewriterBoldOblique.ttf
/usr/java/jre1.8.0_40/lib/oblique-fonts/LucidaSansOblique.ttf
/usr/java/jre1.8.0_40/lib/oblique-fonts/fonts.dir
/usr/java/jre1.8.0_40/lib/javaws.pack
/usr/java/jre1.8.0_40/lib/locale
/usr/java/jre1.8.0_40/lib/locale/de
/usr/java/jre1.8.0_40/lib/locale/de/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/de/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/it
/usr/java/jre1.8.0_40/lib/locale/it/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/it/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/ko
/usr/java/jre1.8.0_40/lib/locale/ko/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/ko/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/zh.GBK
/usr/java/jre1.8.0_40/lib/locale/zh.GBK/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/zh.GBK/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/ko.UTF-8
/usr/java/jre1.8.0_40/lib/locale/ko.UTF-8/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/ko.UTF-8/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/fr
/usr/java/jre1.8.0_40/lib/locale/fr/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/fr/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/zh_HK.BIG5HK
/usr/java/jre1.8.0_40/lib/locale/zh_HK.BIG5HK/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/zh_HK.BIG5HK/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/sv
/usr/java/jre1.8.0_40/lib/locale/sv/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/sv/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/pt_BR
/usr/java/jre1.8.0_40/lib/locale/pt_BR/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/pt_BR/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/ja
/usr/java/jre1.8.0_40/lib/locale/ja/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/ja/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/es
/usr/java/jre1.8.0_40/lib/locale/es/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/es/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/zh_TW.BIG5
/usr/java/jre1.8.0_40/lib/locale/zh_TW.BIG5/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/zh_TW.BIG5/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/zh_TW
/usr/java/jre1.8.0_40/lib/locale/zh_TW/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/zh_TW/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/locale/zh
/usr/java/jre1.8.0_40/lib/locale/zh/LC_MESSAGES
/usr/java/jre1.8.0_40/lib/locale/zh/LC_MESSAGES/sunw_java_plugin.mo
/usr/java/jre1.8.0_40/lib/hijrah-config-umalqura.properties
/usr/java/jre1.8.0_40/lib/fontconfig.Turbo.properties.src
/usr/java/jre1.8.0_40/lib/logging.properties
/usr/java/jre1.8.0_40/lib/images
/usr/java/jre1.8.0_40/lib/images/icons
/usr/java/jre1.8.0_40/lib/images/icons/sun-java.png
/usr/java/jre1.8.0_40/lib/images/icons/sun-java_HighContrast.png
/usr/java/jre1.8.0_40/lib/images/icons/sun-java_HighContrastInverse.png
/usr/java/jre1.8.0_40/lib/images/icons/sun-java_LowContrast.png
/usr/java/jre1.8.0_40/lib/images/cursors
/usr/java/jre1.8.0_40/lib/images/cursors/cursors.properties
/usr/java/jre1.8.0_40/lib/images/cursors/motif_CopyNoDrop32x32.gif
/usr/java/jre1.8.0_40/lib/images/cursors/motif_LinkDrop32x32.gif
/usr/java/jre1.8.0_40/lib/images/cursors/motif_LinkNoDrop32x32.gif
/usr/java/jre1.8.0_40/lib/images/cursors/motif_MoveDrop32x32.gif
/usr/java/jre1.8.0_40/lib/images/cursors/invalid32x32.gif
/usr/java/jre1.8.0_40/lib/images/cursors/motif_MoveNoDrop32x32.gif
/usr/java/jre1.8.0_40/lib/images/cursors/motif_CopyDrop32x32.gif
/usr/java/jre1.8.0_40/lib/fontconfig.Turbo.bfc
/usr/java/jre1.8.0_40/lib/jexec
/usr/java/jre1.8.0_40/lib/charsets.pack
/usr/java/jre1.8.0_40/lib/fontconfig.RedHat.5.bfc
/usr/java/jre1.8.0_40/lib/classlist
/usr/java/jre1.8.0_40/lib/fontconfig.RedHat.6.bfc
/usr/java/jre1.8.0_40/lib/deploy
/usr/java/jre1.8.0_40/lib/deploy/ffjcext.zip
/usr/java/jre1.8.0_40/lib/deploy/messages_zh_CN.properties
/usr/java/jre1.8.0_40/lib/deploy/messages.properties
/usr/java/jre1.8.0_40/lib/deploy/mixcode_s.png
/usr/java/jre1.8.0_40/lib/deploy/messages_pt_BR.properties
/usr/java/jre1.8.0_40/lib/deploy/cautionshield.icns
/usr/java/jre1.8.0_40/lib/deploy/MixedCodeMainDialog.ui
/usr/java/jre1.8.0_40/lib/deploy/splash@2x.gif
/usr/java/jre1.8.0_40/lib/deploy/messages_ko.properties
/usr/java/jre1.8.0_40/lib/deploy/MixedCodeMainDialogJs.ui
/usr/java/jre1.8.0_40/lib/deploy/messages_fr.properties
/usr/java/jre1.8.0_40/lib/deploy/messages_sv.properties
/usr/java/jre1.8.0_40/lib/deploy/messages_es.properties
/usr/java/jre1.8.0_40/lib/deploy/messages_zh_HK.properties
/usr/java/jre1.8.0_40/lib/deploy/messages_zh_TW.properties
/usr/java/jre1.8.0_40/lib/deploy/java-icon.ico
/usr/java/jre1.8.0_40/lib/deploy/messages_it.properties
/usr/java/jre1.8.0_40/lib/deploy/messages_de.properties
/usr/java/jre1.8.0_40/lib/deploy/messages_ja.properties
/usr/java/jre1.8.0_40/lib/deploy/splash.gif
/usr/java/jre1.8.0_40/lib/fontconfig.SuSE.10.properties.src
/usr/java/jre1.8.0_40/lib/javafx.properties
/usr/java/jre1.8.0_40/lib/content-types.properties
/usr/java/jre1.8.0_40/lib/fontconfig.properties.src
/usr/java/jre1.8.0_40/lib/fontconfig.RedHat.5.properties.src
/usr/java/jre1.8.0_40/lib/flavormap.properties
/usr/java/jre1.8.0_40/lib/fontconfig.RedHat.6.properties.src
/usr/java/jre1.8.0_40/lib/tzdb.dat
/usr/java/jre1.8.0_40/lib/applet
/usr/java/jre1.8.0_40/lib/management-agent.jar
/usr/java/jre1.8.0_40/lib/psfont.properties.ja
/usr/java/jre1.8.0_40/lib/psfontj2d.properties
/usr/java/jre1.8.0_40/lib/desktop
/usr/java/jre1.8.0_40/lib/desktop/mime
/usr/java/jre1.8.0_40/lib/desktop/mime/packages
/usr/java/jre1.8.0_40/lib/desktop/mime/packages/x-java-jnlp-file.xml
/usr/java/jre1.8.0_40/lib/desktop/mime/packages/x-java-archive.xml
/usr/java/jre1.8.0_40/lib/desktop/icons
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrast/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/HighContrastInverse/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/LowContrast/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/16x16/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/apps
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/apps/sun-jcontrol.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/apps/sun-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/apps/sun-javaws.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/mimetypes
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/mimetypes/gnome-mime-text-x-java.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-java-archive.png
/usr/java/jre1.8.0_40/lib/desktop/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-java-jnlp-file.png
/usr/java/jre1.8.0_40/lib/desktop/applications
/usr/java/jre1.8.0_40/lib/desktop/applications/sun_java.desktop
/usr/java/jre1.8.0_40/lib/desktop/applications/sun-javaws.desktop
/usr/java/jre1.8.0_40/lib/desktop/applications/sun-java.desktop
/usr/java/jre1.8.0_40/lib/jfr.jar
/usr/java/jre1.8.0_40/lib/jfr
/usr/java/jre1.8.0_40/lib/jfr/profile.jfc
/usr/java/jre1.8.0_40/lib/jfr/default.jfc
/usr/java/jre1.8.0_40/lib/calendars.properties
/usr/java/jre1.8.0_40/lib/javasettings
/usr/java/jre1.8.0_40/lib/plugin.pack
/usr/java/jre1.8.0_40/LICENSE
/usr/java/jre1.8.0_40/Welcome.html
/usr/java/jre1.8.0_40/bin/ControlPanel
/usr/java/jre1.8.0_40/man/ja
/usr/java/jre1.8.0_40/lib/i386/client/libjsig.so
/usr/java/jre1.8.0_40/lib/i386/server/libjsig.so
```
===
I removed the java directory I mentioned (just like before), so I don't know why it's listing /usr/java. I was able to find /usr/share/doc/jre1.8.0-40 and the two files mentioned there.

> Also - 64 bit or 32 bit?

32. Thanks again by the way for all of your efforts to help me out of this hole I've dug myself into.:)

---

### Post by ian-weisser on 2015-03-18
> **david.williams.425 said:**
> I removed the java directory I mentioned (just like before), so I don't know why it's listing /usr/java. I was able to find /usr/share/doc/jre1.8.0-40 and the two files mentioned there.

It's listing the files because that's not a list of your current file system. That's the list of files that dpkg expects to install and remove for the package.

Sandyd is highly knowledgeable, has good judgement, years of experience, and may have a better solution.

Pending a better idea, I think your best option is to:

1) Make sure your data backups are up-to-date.

2) Delete the files on that list manually. Just the files and obviously package-installed directories. DO NOT delete directories that other packages use, like /usr/share/doc...or you will damage your system beyond simple, fast repair.

3) After you have cleaned up those files, use 'sudo dpkg --remove --force-remove-reinstreq  jre1.8.0-40' to delete the package from the dpkg database.
Then your filesystem and dpkg database should match again, and the package manager should work again.

---

### Post by sandyd on 2015-03-19
Huh.
This is odd

I was tired yesterday and I forgot about this thread.

However...

I have found the culprit.

Re-reading the instructions, it was odd that there was a package installed.
The first instruction says "Java for Linux Platforms" and the second says "Java for RPM based Linux Platforms". First instructions wouldn't have created a package, so I went to the second

Taking a closer look at dpkg output
```

===
Package: jre1.8.0-40
Status: install reinstreq half-installed
Priority: extra
**Section: alien**
Installed-Size: 99463
Maintainer: -
Architecture: i386
Version: 1.8.040-1
Config-Version: 1.8.040-1
Conffiles:
/usr/java/jre1.8.0_40/.java/.systemPrefs/.system.lock d41d8cd98f00b204e9800998ecf8427e
/usr/java/jre1.8.0_40/.java/.systemPrefs/.systemRootModFile d41d8cd98f00b204e9800998ecf8427e
/usr/java/jre1.8.0_40/.java/init.d/jexec 3a4104cd0a34b5e7e55433a78d9f7721
/usr/java/jre1.8.0_40/lib/charsets.pack 6ff9967fab9c3c3beb331bd2951dc9e3
/usr/java/jre1.8.0_40/lib/deploy.pack be0a5fc39fc55d1a2674f45e84d2290c
/usr/java/jre1.8.0_40/lib/ext/jfxrt.pack 4517939df44879e4a4cf9091f4c9e8cb
/usr/java/jre1.8.0_40/lib/ext/localedata.pack c6cdb1fc0af0f0a01d6ec3585486e54b
/usr/java/jre1.8.0_40/lib/javaws.pack 1fb40b342957a86a00093996f7bfe46e
/usr/java/jre1.8.0_40/lib/jsse.pack 33d5b44adbb3cbd93c15f161e82bb047
/usr/java/jre1.8.0_40/lib/plugin.pack 008b9f94976decaae5c09c46a6f4ad43
/usr/java/jre1.8.0_40/lib/rt.pack 98fc43fc4abae8b89bfe5e6ee83096ed
Description: Java Platform Standard Edition Runtime Environment
The Java Platform Standard Edition Runtime Environment (JRE) contains
everything necessary to run applets and applications designed for the
Java platform. This includes the Java virtual machine, plus the Java
platform classes and supporting files.
.
The JRE is freely redistributable, per the terms of the included license.
.
**(Converted from a rpm package by alien version 8.90.)**
===
```

Its a RPM, coverted to DEB using Alien.

Lets see if we can still reverse this...

```

wget http://javadl.sun.com/webapps/download/AutoDL?BundleId=104757 -O jre-8u40-linux-i586.rpm
sudo apt-get -y install alien
sudo alien -i jre-8u40-linux-i586.rpm
```

It is possible that it may not work due to existing incompatibilities between RH and Debian distros

In that case,
```

sudo rm -rf /usr/share/doc/jre1.8.0-40
sudo rm -rf /usr/java/jre1.8.0_40/
sudo dpkg --remove --force-remove-reinstreq jre1.8.0-40
```

Side note: please copy above commands or take great care when typing. A single space between the slashes will cause ubuntu to attempt to wipe your system.

---

### Post by david.williams.425 on 2015-03-21
I'm making some progress! I tried the first method - the apt-get command didn't work because of the half-installed package..
 =
 So I went ahead and tried the dpkg method &#8211; it didn't work and gave some error that I can't recreate now, but after rebooting I no longer get the same System Error message and Software Center runs. I get a new, slightly different error related to jre whenever I try to purge jre:
 
 ```
sudo dpkg --purge jre1.8.0-40  
 (Reading database ... 203475 files and directories currently installed.)  
 Removing jre1.8.0-40 (1.8.040-1) ...  
 **/var/lib/dpkg/info/jre1.8.0-40.postrm: line 810: /usr/sbin/alternatives: No such file or directory ** 
 **dpkg: error processing package jre1.8.0-40 (--purge): ** 
  **subprocess installed post-removal script returned error exit status 127 ** 
 Errors were encountered while processing:  
  jre1.8.0-40
```
 
 I also get the error when trying to install anything. The oracle-java8-installer below is just one examplel:
 
 ```
sudo apt-get install oracle-java8-installer  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following extra packages will be installed:  
   gsfonts-x11  
 Suggested packages:  
   binfmt-support visualvm ttf-baekmuk ttf-unfonts ttf-unfonts-core  
   ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho  
   ttf-arphic-uming  
 **The following packages will be REMOVED: ** 
   **jre1.8.0-40 ** 
 The following NEW packages will be installed:  
   gsfonts-x11 oracle-java8-installer  
 0 upgraded, 2 newly installed, 1 to remove and 200 not upgraded.  
 1 not fully installed or removed.  
 Need to get 31.6 kB of archives.  
 After this operation, 102 MB disk space will be freed.  
 Do you want to continue? [Y/n] Y  
 Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main gsfonts-x11 all 0.22 [9,108 B]  
 Get:2 http://ppa.launchpad.net/webupd8team/java/ubuntu/ trusty/main oracle-java8-installer all 8u40+8u33arm-1~webupd8~0 [22.5 kB]  
 Fetched 31.6 kB in 0s (60.5 kB/s)                 
 Preconfiguring packages ...  
 (Reading database ... 203475 files and directories currently installed.)  
 **Removing jre1.8.0-40 (1.8.040-1) ... ** 
 **/var/lib/dpkg/info/jre1.8.0-40.postrm: line 810: /usr/sbin/alternatives: No such file or directory ** 
 **dpkg: error processing package jre1.8.0-40 (--remove): ** 
  subprocess installed post-removal script returned error exit status 127  
 Errors were encountered while processing:  
  jre1.8.0-40  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
```
 
 I also received a similar error when trying to run sudo alien -i jre-8u40-linux-i586.rpm referencing the same line and directory bolded above.
 I looked in the var/lib/dpkg/info directory and found 6 scripts called jre1.8.0-40 with the following extensions: conffiles, list, md5sums, postinst, prerm and postrm.  
 After looking at the dpkg man page, it looks like the prerm script ran, then the installed files were removed which got rid of the System Error message, then the postrm script ran into the error, leaving enough behind to prevent new packages from being installed.  
  My ideas about how to proceed are:

 1) Create an empty 'alternatives' directory in /usr/sbin
OR
 2) Sudo dpkg &#8211;purge &#8211;force-architecture jre1.8.0-40 to ignore the missing directory.
 Do either of those sound like they could work?

In case it helps, The line 810 in the postrm script that references the missing directory is part of the following method:
 ```
alt_remove_java() { 
 jrebindir=$1 
 /usr/sbin/alternatives --remove java $jrebindir/java 
 }
```

 In case it's still relevant, here's the new, shorter output of the cat command:

 ```
cat /var/lib/dpkg/info/jre1.8.0-40.list  
 /usr  
 /usr/java/jre1.8.0_40/.java/.systemPrefs/.system.lock 
 /usr/java/jre1.8.0_40/.java/.systemPrefs/.systemRootModFile 
 /usr/java/jre1.8.0_40/.java/init.d/jexec 
 /usr/java/jre1.8.0_40/lib/rt.pack 
 /usr/java/jre1.8.0_40/lib/jsse.pack 
 /usr/java/jre1.8.0_40/lib/deploy.pack 
 /usr/java/jre1.8.0_40/lib/ext/jfxrt.pack 
 /usr/java/jre1.8.0_40/lib/ext/localedata.pack 
 /usr/java/jre1.8.0_40/lib/javaws.pack 
 /usr/java/jre1.8.0_40/lib/charsets.pack 
 /usr/java/jre1.8.0_40/lib/plugin.pack 

```

---

### Post by sandyd on 2015-03-22
My mistake - since you already used alien - should already be installed, shoudn't need to run apt-get

Anyways, progress!

I also now know why the package was not installed properly in the first place.
Ubuntu doesn't use /usr/sbin/alternatives. The postinst script must have tried to run /usr/sbin/alternatives with issues.

No need to continue using the postrm script then - doesn't do anything in ubuntu
```

sudo rm /var/lib/dpkg/info/jre1.8.0-40.postrm
sudo dpkg --purge jre1.8.0-40 
```

---

### Post by david.williams.425 on 2015-03-25
That eems to have fixed the issue!
I succesfully installed updates and upgraded to the oracle-java 8 package posted earlier. Thanks, Sandy and Ian for taking the time to help me.

---

