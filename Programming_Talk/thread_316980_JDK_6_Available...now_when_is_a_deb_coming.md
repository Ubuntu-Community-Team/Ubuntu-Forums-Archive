---
title: "JDK 6 Available...now when is a deb coming?"
date: 2006-12-11
forum: Programming Talk
---

### Post by rekahsoft on 2006-12-11
JDK 6 was released today. Check here: [http://java.sun.com/javase/6/](http://java.sun.com/javase/6/)

Anyways i want to install it cause i have been waiting for this release for quite some time but i don't like messing around and messing things up. Sun provides a .rpm and a .bin but i would prefer to use a deb and keep everything clean. Does anybody know when a deb is coming out? If it is not reasonably soon then i will install it and write a script to automate the process for anybody else that would like to use jdk 6.

---

### Post by hod139 on 2006-12-11
You're not the only one to ask this question.  
[http://ubuntuforums.org/showthread.php?t=316942](http://ubuntuforums.org/showthread.php?t=316942)

If you are waiting for an official deb it could be a while.

---

### Post by mlind on 2006-12-11
You can submit a wishlist bug about 1.6 for feisty.

DLJ bundles for 1.6 are available @ [https://jdk-distros.dev.java.net/developer.html](https://jdk-distros.dev.java.net/developer.html).
If you have experience for tweaking debian source packages, you can create 'official' sun-java6 binaries yourself. 

java-package doesn't support mustang yet, but there's a patch for it on DBTS.

---

### Post by rekahsoft on 2006-12-11
> **mlind said:**
> You can submit a wishlist bug about 1.6 for feisty.

DLJ bundles for 1.6 are available @ [https://jdk-distros.dev.java.net/developer.html](https://jdk-distros.dev.java.net/developer.html).
If you have experience for tweaking debian source packages, you can create 'official' sun-java6 binaries yourself. 

java-package doesn't support mustang yet, but there's a patch for it on DBTS.

Unforchanantly i have no experiance creating debian source packages. What is DBTS and how do i get a hold of the patch for java-package? Thanks

---

### Post by msumurph on 2006-12-11
Is there a problem installing the JDK as a user in your home directory?  I used the .bin installer, which creates jdk1.6 folder in my home (or whatever directory you run the installer in).  I am able to run NetBeans on top of this installation.  I kept the ubuntu sun-java5 package installed on the system as well.

---

### Post by samjh on 2006-12-12
> **msumurph said:**
> Is there a problem installing the JDK as a user in your home directory?  I used the .bin installer, which creates jdk1.6 folder in my home (or whatever directory you run the installer in).  I am able to run NetBeans on top of this installation.  I kept the ubuntu sun-java5 package installed on the system as well.

I use a similar configuation.  The only difference is my Netbeans is in my home directory, and JDK is in the /opt directory.

Haven't tried it with JDK6, but I don't imagine there being any problems.  JDK installation has always been relatively smooth for me.

---

### Post by mlind on 2006-12-12
> **rekahsoft said:**
> Unforchanantly i have no experiance creating debian source packages. What is DBTS and how do i get a hold of the patch for java-package? Thanks

Probably easiest way then is to install jdk locally, and set the necessary environment variables.

You can do this in ~/.bashrc or /etc/environment, or even in ~/.gtkrc
```

export JAVA_HOME=${HOME}/path/to/jdk1.6.0
export PATH=${JAVA_HOME}/bin:${PATH}

```

open a terminal and type java -version, it should output that you're using jdk 6.


DBTS is Debian Bug Tracking System. Patch there is untested, and you would need to patch and rebuild
java-package in order to get it working.

---

### Post by Ramses de Norre on 2006-12-12
It could be me but it seems that java6 runs swing applications slower here in comparison with java5... (just a rough first feeling though)

---

### Post by mlind on 2006-12-12
> **Ramses de Norre said:**
> It could be me but it seems that java6 runs swing applications slower here in comparison with java5... (just a rough first feeling though)

There's no official benchmarks yet (apart from Sun's own), but new JVM should perform 5%-24% faster than the previous 1.5 one (I guess your mileage may vary).
There's a small heads-up article on [http://www.theserverside.com/news/thread.tss?thread_id=43434](http://www.theserverside.com/news/thread.tss?thread_id=43434)

---

### Post by Ben Sprinkle on 2006-12-12
Making the official .deb:
```

sudo apt-get install java-common
sudo apt-get install fakeroot
fakeroot make-jpkg path/to/jdk6.bin

```
:)

---

### Post by rekahsoft on 2006-12-12
I have installed the .bin from Sun's web site to /usr/lib/jvm and edited /etc/jvm and added the directory of jdk 6 to the file. I am also going to creat links to java and javac in /usr/bin. I find that jdk 6 in much faster and looks much better with gtk LAF. The only problem is that i don't know how to get gtk LAF in netbeans. I have tried this:```
netbeans --laf com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```but or some reason Netbeans looks very ugly when i comes up. If anybody knows how to get netbeans to use gtk LAF lt me know. Thanks.

---

### Post by Hendrixski on 2006-12-12
> **Goat Spirit said:**
> Making the official .deb:
```

sudo apt-get install java-common
sudo apt-get install fakeroot
fakeroot make-jpkg path/to/jdk6.bin

```
:)

It's that simple?  you pass fakeroot the address to the .bin file and it converts the .bin to a .deb?  Does that work for all binaries?  like... Google earth for example?

Then how do you submit that .deb to the folks Debian & Canonical to put it into repositories?

---

### Post by rekahsoft on 2006-12-12
> **Goat Spirit said:**
> Making the official .deb:
```

sudo apt-get install java-common
sudo apt-get install fakeroot
fakeroot make-jpkg path/to/jdk6.bin

```
:)

wow...i will try this a little later today and see how it works. Thanks

---

### Post by mlind on 2006-12-12
> **Goat Spirit said:**
> Making the official .deb:
```

sudo apt-get install java-common
sudo apt-get install fakeroot
fakeroot make-jpkg path/to/jdk6.bin

```
:)

I though java-package doesn't support mustang yet..

---

### Post by mlind on 2006-12-12
Well it doesn't seem to. I'll attach a debdiff to get sun-java6 support for java-package.


To get current java-package, you must add multiverse source repository in /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

```

Then patch and build java-package
```

mkdir /tmp/java-package
cd /tmp/java-package
apt-get source java-package
cd java-package-0.28
patch -p1 < /path/to/**java-package_sun-java6.patch**

sudo aptitude install debhelper
debian/rules binary
sudo dpkg -i ../java-package_0.28ubuntu1_all.deb

```

Build java6 binaries
```

sudo aptitude install fakeroot
fakeroot make-jpkg **jdk-6-linux-i586.bin**

```

/edit
I forgot to attach already patched .deb
/edit2
patch was missing j2re install and remove scripts

---

### Post by Ben Sprinkle on 2006-12-12
Guys it does work, but I think only for Java. It parses the .bin, finds depend's, and puts it into a .deb.

Taylor, who has joined here, has done it many times. :)
But it was done for JDK 1.6.0_10, not sure bout 6.

---

### Post by rekahsoft on 2006-12-12
> **mlind said:**
> Well it doesn't seem to. I'll attach a debdiff to get sun-java6 support for java-package.


To get current java-package, you must add multiverse source repository in /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu feisty deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

```

Then patch and build java-package
```

mkdir /tmp/java-package
cd /tmp/java-package
apt-get source java-package
cd java-package-0.28
patch -p1 < /path/to/**java-package_sun-java6.patch**

sudo aptitude install debhelper
debian/rules binary
sudo dpkg -i ../java-package_0.28ubuntu1_all.deb

```

Build java6 binaries
```

sudo aptitude install fakeroot
fakeroot make-jpkg **jdk-6-linux-i586.bin**

```

/edit
I forgot to attach already patched .deb

awesome i got it working :) does anybody know how to enable gtk LAF for netbeans?

---

### Post by samjh on 2006-12-13
> **rekahsoft said:**
> The only problem is that i don't know how to get gtk LAF in netbeans. I have tried this:```
netbeans --laf com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```but or some reason Netbeans looks very ugly when i comes up. If anybody knows how to get netbeans to use gtk LAF lt me know. Thanks.

Your code should work.  It worked for me, using JRE 1.5.0_10 and 1.6.0.  The LAF using 1.5 looked very ugly.  1.6 looked a lot prettier, but some components were still not good looking.

I have a feeling that the Netbeans developers didn't really test Netbeans thoroughly using the GTK LAF.

In Windows XP, the XP LAF works perfectly fine (it's actually the default LAF).  It's so good that if you didn't know anything about Netbeans, you could be forgiven for mistaking it as a native Windows app.  But in Linux, the default LAF is the fully cross-platform Metal LAF, which seems to indicate that Netbeans is not really intended to be used with the GTK LAF, even in Gnome environments.

---

### Post by rekahsoft on 2006-12-13
> **samjh said:**
> Your code should work.  It worked for me, using JRE 1.5.0_10 and 1.6.0.  The LAF using 1.5 looked very ugly.  1.6 looked a lot prettier, but some components were still not good looking.

I have a feeling that the Netbeans developers didn't really test Netbeans thoroughly using the GTK LAF.

In Windows XP, the XP LAF works perfectly fine (it's actually the default LAF).  It's so good that if you didn't know anything about Netbeans, you could be forgiven for mistaking it as a native Windows app.  But in Linux, the default LAF is the fully cross-platform Metal LAF, which seems to indicate that Netbeans is not really intended to be used with the GTK LAF, even in Gnome environments.

i got it looking sexy not but like you said, some components are messed.

---

### Post by acerlinux on 2006-12-13
> **mlind said:**
> Well it doesn't seem to. I'll attach a debdiff to get sun-java6 support for java-package.


To get current java-package, you must add multiverse source repository in /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu feisty deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

```

Then patch and build java-package
```

mkdir /tmp/java-package
cd /tmp/java-package
apt-get source java-package
cd java-package-0.28
patch -p1 < /path/to/**java-package_sun-java6.patch**

sudo aptitude install debhelper
debian/rules binary
sudo dpkg -i ../java-package_0.28ubuntu1_all.deb

```

Build java6 binaries
```

sudo aptitude install fakeroot
fakeroot make-jpkg **jdk-6-linux-i586.bin**

```

/edit
I forgot to attach already patched .deb

do you mind to attach the patched java-package.deb please. that's should be great.

---

### Post by mlind on 2006-12-14
> **acerlinux said:**
> do you mind to attach the patched java-package.deb please. that's should be great.

It's already attached in post #15.

---

### Post by acerlinux on 2006-12-14
> **mlind said:**
> It's already attached in post #15.

Got it and works very well, Thanks.

---

### Post by KLineD on 2006-12-15
I installed JDK 6 and java -version outputs 1.6.0 but netbeans is still using 1.5 (it's also installed in my system) 

How do I tell netbeans to use java 6 and the new LAF ?

Thanks!

---

### Post by samjh on 2006-12-15
> **KLineD said:**
> I installed JDK 6 and java -version outputs 1.6.0 but netbeans is still using 1.5 (it's also installed in my system) 

How do I tell netbeans to use java 6 and the new LAF ?

Thanks!

If you mean that it's using 1.5 of JDK, then try this:

Open Netbeans, go to Tools -> Java Platform Manager.  Click Add Platform, and select the directory where your JDK 1.6.0 exists.

Then for whatever project you want to develop using 1.6, right-click on the project in the Projects window, select Properties.  Go to the Libraries category in the window that appears, and select your platform.

You can also specify your default platform by going to the etc directory within your netbeans installation directory, and editing netbeans.conf.  Find the line that says netbeans_jdkhome="blahblah", and replace "blahblach" with the directory of your chosen JDK installation (with quote marks).

---

### Post by KLineD on 2006-12-15
I'm sorry if I didn't explained myself before. What I meant was that Netbeans is running on top of the JVM 1.5.0 and I want it to run using 1.6.0. However if I do java -version it reports Java version "1.6.0"

---

### Post by daniminas on 2006-12-15
i don't know why some people tellme jdk is difficult to install on debian sistems.... :confused:

---

### Post by samjh on 2006-12-16
> **KLineD said:**
> I'm sorry if I didn't explained myself before. What I meant was that Netbeans is running on top of the JVM 1.5.0 and I want it to run using 1.6.0. However if I do java -version it reports Java version "1.6.0"

How do you know it's running on JVM 1.5.0?  I thought Netbeans ran on the default JVM for your computer.

---

### Post by tmahmood on 2006-12-16
Sorry Double Post
Delete

---

### Post by tmahmood on 2006-12-16
Hey.. thanks for the patches... JDK is running fine now, I had to do a 

update-alternatives --all

to update all the java executables to point to the JDK6

also it might be a good idea to add the path to the JDK folder at 

/etc/jvm

file.. put the JDK6 path on the top of the list

---

### Post by rekahsoft on 2006-12-16
Many people are confused on how to get Netbeans working on jdk 6 now that it is installed on thier system. It is very simple and can be done by editing $netbeans_install_folder/etc/netbeans.conf and change "netbeans_jdkhome" to the install of your jdk 6. Save and next time you boot up you will have netbeans running on jdk 6 :)

---

### Post by KLineD on 2006-12-16
> **samjh said:**
> How do you know it's running on JVM 1.5.0?  I thought Netbeans ran on the default JVM for your computer.

I know because it says so in the about box. However I reinstalled Netbeans and then I selected JDK 6 as the default Java installation. Not the best solution but it worked.

---

### Post by jvc26 on 2006-12-17
Hi there, just a brief question, I installed the .bin packages from the Sun website, which left me with files in my /home/james/ directory ( /home/james/jdk1.6.0 and the JRE in /home/james/jdk1.6.0/jre/) Can I just add these to the paths and run it from here? i.e. Put the javac path in and the JRE path and run it just straight off? Or do I need to install it the other way, as put here: [http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15) because here I got up to the 
```

debian/rules binary
sudo dpkg -i ../java-package_0.28ubuntu1_all.deb

```
section at which point it threw back the error at me
```

dpkg-deb: building package `java-package' in `../java-package_0.28ubuntu1_all.deb'.
tar: -: file name read contains nul character

```
If I can just add the entries to path if that will work that will be much easier, am not sure how to do this in linux. Apologies, am just a recent convert and havent got my way round 100% yet.

Thanks
Il

---

### Post by Treviño on 2006-12-17
Maybe it has just been reported, btw to **fix problems with Java apps + Compiz and Beryl** (this one only using my svn builds) you should use Java _*build 1.6.0_01-ea-b01*_. To download and package it in few moves, you should use my make-jpkg-mustang (which fixes problems also for standard Beryl).

You can find all the informations and debs in the link below ;)
[B][[HOWTO / SCRIPT] - Packaging and installing Java 1.6.0 (Mustang) JRE in few moves!]("http://ubuntuforums.org/showthread.php?t=262603")

BYE!
[/B]

---

### Post by macross3003 on 2006-12-17
great, it works perfectly!

thanks a lot :D

---

### Post by mlind on 2006-12-17
> **Illuvator said:**
> Hi there, just a brief question, I installed the .bin packages from the Sun website, which left me with files in my /home/james/ directory ( /home/james/jdk1.6.0 and the JRE in /home/james/jdk1.6.0/jre/) Can I just add these to the paths and run it from here? i.e. Put the javac path in and the JRE path and run it just straight off? Or do I need to install it the other way, as put here: 

Thanks
Il

.bin packages? You should only install one, either JRE or JDK. You can run it locally too if you wish, just export JAVA_HOME environment variable and add JRE's/JDK's bin directory to your path. These were explained earlier in this thread. 

To install new java globally, use already patched java-package on post #15.

---

### Post by jvc26 on 2006-12-17
Right I installed the JDK to /home/james/jdk1.6.0 (sorry typo before)

Where do I put the entries: (And is this both the entry for JRE and JDK or do I have to put it in again for the other?
```

export JAVA_HOME=${HOME}/home/james/jdk1.6.0
export PATH=${JAVA_HOME}/bin:${PATH}

```

Are they just a console line? Or do I sudo gedit /etc/environment and add them in at the bottom of that?

The other question is to do with /usr/bin/java as following an earlier HOWTO I had to edit that and I think I've made a mess of it:

```

#!/usr/bin/perl -w
#
# Starts the GNU Java interpreter.
#
# Command-line arguments should be in the style of Sun's Java runtime;
# these will be converted to gij arguments before being passed to the
# gij itself.
#
# The Debian JNI module directory and any other specified JNI
# directories will be included on the JNI search path.
#
# Copyright (C) 2002-2003 by Ben Burton <bab@debian.org>
# Based on the original gij-wrapper-3.2 shell script.

use strict;

# The real Java runtime:
**my $javaRuntime = '/home/james/jdk1.6.0/jre/bin/java';**

# The debian JNI module directory:
my $debianJNIDir = '/usr/lib/jni';

# The command-line arguments to pass to the real Java runtime:
my @commandLine;

# The full JNI search path to use:
my $JNIPath = '';

# Build the command-line from the arguments given.
my $parsingOptions = 1;

# Flag used to copy argument to -classpath or -cp.
my $copyNext = 0;
foreach my $arg (@ARGV) {
  if (not $parsingOptions) {
    # We're done parsing options; just copy all remaining arguments directly.
    push @commandLine, $arg;
    next;
  }
  if ($copyNext) {
    push @commandLine, $arg;
    $copyNext = 0;
    next;
  }

  # Try to interpret Sun-style options.
  if ($arg eq '-version') {
    push @commandLine, '--version';
  } elsif ($arg eq '-h' or $arg eq '-help') {
    push @commandLine, '--help';
  } elsif ($arg eq '-cp' or $arg eq '--cp') {
    push @commandLine, '-cp';
    $copyNext = 1;
  } elsif ($arg eq '-classpath' or $arg eq '--classpath') {
    push @commandLine, '-classpath';
    $copyNext = 1;
  } elsif ($arg =~ /^-Djava.library.path=(.+)$/) {
    # A component of the JNI search path has been given.
    if ($JNIPath) {
      $JNIPath = $JNIPath . ':' . $1;
    } else {
      $JNIPath = $1;
    }
  } elsif ($arg eq '-jar' or $arg =~ /^-D/) {
    # Copy the argument directly.
    push @commandLine, $arg;
  } elsif ($arg =~ /^-/) {
    # An unrecognised option has been passed - just drop it.
  } else {
    # Some non-option argument has been given.
    # Stop parsing options at this point.
    push @commandLine, $arg;
    $parsingOptions = 0;
  }
}

# Add the debian JNI module directory to the JNI search path if it's not
# already there.
if ($JNIPath !~ /(^|:)$debianJNIDir($|:)/) {
  if ($JNIPath) {
    $JNIPath = $JNIPath . ':' . $debianJNIDir;
  } else {
    $JNIPath = $debianJNIDir;
  }
}

# Use environment variable $LTDL_LIBRARY_PATH to store the JNI path,
# since gij uses libltdl to dlopen JNI modules.
if ($ENV{LTDL_LIBRARY_PATH}) {
    $ENV{LTDL_LIBRARY_PATH} = $ENV{LTDL_LIBRARY_PATH} . ':' . $JNIPath;
} else {
    $ENV{LTDL_LIBRARY_PATH} = $JNIPath;
}

# Call the real Java runtime.
my @fullCommandLine = ( $javaRuntime );
push @fullCommandLine, @commandLine;
exec @fullCommandLine or exit(1);


```

With the bold bit being the line I edited. Sorry if I'm beating round the bush, thanks very much for your help,
Il

---

### Post by mlind on 2006-12-17
> **Illuvator said:**
> Right I installed the JDK to /home/james/jdk1.6.0 (sorry typo before)

Where do I put the entries: (And is this both the entry for JRE and JDK or do I have to put it in again for the other?
```

export JAVA_HOME=${HOME}/home/james/jdk1.6.0
export PATH=${JAVA_HOME}/bin:${PATH}

```

Are they just a console line? Or do I sudo gedit /etc/environment and add them in at the bottom of that?

The other question is to do with /usr/bin/java as following an earlier HOWTO I had to edit that and I think I've made a mess of it:


If you've installed JDK locally, then you should probably export environment variables locally only and not edit any systemwide launch scripts.
/etc/environment would be good place set JAVA_HOME and add JDK's bin directory to path, but only if you installed java globally.

You can try adding those lines to ~/.bashrc (or ~/.bash_profile fon login-shells only, or ~/.gktrc if you want the environment available sooner) .

I usually have one java installed globally, which exports it's stuff on /etc/environment and uses alternatives to locate corrent java binaries & libraries.
Then I have bunch of locally installed JDK's, and every app that uses these must export the variables in some sort of startup script.

---

### Post by coldrick on 2006-12-17
The easiest way to use gtk look and feel with netbeans is to edit the netbeans.conf file in the /etc subdirectory of your nb installation. In there, edit the line that starts with "netbeans_default" and add  -J-DuseGtk=true at the end (inside the closing quotation mark).

However, be aware that there are still problems with this, depending on what parts of nb you're using (for example, if you start using diffs in the subversion support, things just don't work). 

Some of the problems are actually with jdk6, and will be fixed later, some may with nb itself. There's a dev group actively working to fix these problems, and I harass them whenever I can :-)

Best regards,
David

---

### Post by jvc26 on 2006-12-18
@mlind: Did the entire install the way you explained earlier (building from source with using the .patch file etc) and this time it compiled ok.

Thanks very much for your time,
Il

---

### Post by sergiolib on 2006-12-28
> **mlind said:**
> Well it doesn't seem to. I'll attach a debdiff to get sun-java6 support for java-package.


To get current java-package, you must add multiverse source repository in /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

```

Then patch and build java-package
```

mkdir /tmp/java-package
cd /tmp/java-package
apt-get source java-package
cd java-package-0.28
patch -p1 < /path/to/**java-package_sun-java6.patch**

sudo aptitude install debhelper
debian/rules binary
sudo dpkg -i ../java-package_0.28ubuntu1_all.deb

```

Build java6 binaries
```

sudo aptitude install fakeroot
fakeroot make-jpkg **jdk-6-linux-i586.bin**

```

/edit
I forgot to attach already patched .deb
/edit2
patch was missing j2re install and remove scripts

Good, great, excellent guide!:-D 
Anyway, I didn't use the Feisty repository, I was able to patch the source of the Edgy java-package, that if I am not wrong is the 0.27.

---

