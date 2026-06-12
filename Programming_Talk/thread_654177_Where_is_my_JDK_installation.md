---
title: "Where is my JDK installation?"
date: 2007-12-30
forum: Programming Talk
---

### Post by Bpa on 2007-12-30
Hello all. I have seen many threads detailing how to install sun-java and I am confident that I have it installed and my system is set up to use the sun-java as my default. I need to figure out where my default jdk installation is. I am trying to work with a Phidgets device and in the Makefile it needs to be pointed to my jdk installation so that it can set up JNI properly.   I cannot for the life of me figure out where this is. 

Here is the output of the following commands:

```
sudo apt-cache policy sun-java5-jdk
```

sun-java5-jdk:
Installed: 1.5.0-13-0ubuntu1
Candidate: 1.5.0-13-0ubuntu1
Version table:
*** 1.5.0-13-0ubuntu1 0
500 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
100 /var/lib/dpkg/status 

```
sudo find / -name '*jdk*'
```

/usr/share/doc/sun-java5-jdk
/usr/share/netbeans/5.5/harness/jdk.xml
/usr/share/doc-base/sun-java5-jdk-readme
/usr/share/lintian/overrides/sun-java5-jdk
/usr/share/menu/sun-java5-jdk
/usr/lib/perl5/XML/Parser/Encodings/x-sjis-jdk117.enc
/media/sda1/cygwin/lib/perl5/vendor_perl/5.8/cygwin/XML/Parser/Encodings/x-sjis-jdk117.enc
/var/cache/apt/archives/sun-java5-jdk_1.5.0-13-0ubuntu1_amd64.deb
/var/lib/dpkg/info/sun-java5-jdk.templates
/var/lib/dpkg/info/sun-java5-jdk.config
/var/lib/dpkg/info/sun-java5-jdk.md5sums
/var/lib/dpkg/info/sun-java5-jdk.list
/var/lib/dpkg/info/sun-java5-jdk.preinst
/var/lib/dpkg/info/sun-java5-jdk.postrm
/var/lib/dpkg/info/sun-java5-jdk.postinst
/var/lib/dpkg/info/sun-java5-jdk.prerm
/var/lib/doc-base/info/sun-java5-jdk-readme.status


Is it any of the above?

Thanks in advance.

---

### Post by Majorix on 2007-12-30
You are probably looking for javac, the JDK bytecode compiler.
```
sudo updatedb; locate javac
```

---

### Post by Bpa on 2007-12-30
Thank you for the quick answer. When I run the locate command I get the following:

/etc/alternatives/javac.1.gz
/etc/alternatives/javac
/usr/share/netbeans/5.5/ide7/modules/org-netbeans-modules-javacore.jar
/usr/share/netbeans/5.5/ide7/config/Modules/org-netbeans-modules-javacore.xml
/usr/share/netbeans/5.5/ide7/update_tracking/org-netbeans-modules-javacore.xml
/usr/share/vim/vim71/compiler/javac.vim
/usr/share/vim/vim71/syntax/javacc.vim
/usr/share/man/man1/javac.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/man/man1/javac.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/man/ja/man1/javac.1.gz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/bin/javac
/usr/bin/javac
/var/lib/dpkg/alternatives/javac

Then when running 

```
which javac
```

It shows that my default java compiler is 
/usr/bin/javac

Is this the GNU java compiler? I am confused because when I run 

```
java -version
```

I get:

java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)

So I am thinking that I am using the sun interpreter but not the sun compiler.  

However, when I run:

```
sudo update-alternatives --config javac
```

It produces:

There is only 1 program which provides javac
(/usr/lib/jvm/java-1.5.0-sun/bin/javac). Nothing to configure.


I guess I should point the JAVAHOME variable in the make file to /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/

Is there something else I need to change to make my default javac command use the sun compiler from that directory as well?

---

### Post by samjh on 2007-12-31
> **Bpa said:**
> Is this the GNU java compiler? I am confused because when I run 

```
java -version
```

I get:

java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)

So I am thinking that I am using the sun interpreter but not the sun compiler.

Try ```
javac -version
```

If it produces something like "javac 1.5.0_13", then you are using the Sun Java compiler.

In case you didn't know, the java, javac, and other commands in /usr/bin are just symlinks (symbolic links), which are like shortcuts in Windows.  You can navigate to /usr/bin using your file manager, right-click, select properties, and check where the link is pointing to.

As an aside: when you run sudo update-alternatives, the command executes a series of scripts which will point the symlinks in /usr/bin (and a few other places) to different targets.  So if you choose to do a sudo update-alternatives --config javac, and choose the Sun version, it automatically reconfigures all the symlinks for "javac" in your system and other configuration settings, to point to the Sun version.

---

### Post by Klipt on 2007-12-31
You can probably use the Gnu Java compiler directly (if installed) by using the command 'gcj' instead of 'javac'.

---

### Post by fyplinux on 2007-12-31
you might use "update-alternatives" command  to validate the sun jdk, rather than gcj

---

### Post by jespdj on 2008-01-01
Look in your /usr/lib/jvm directory. I have Java 6 installed, and I see two thiings there:
```
lrwxrwxrwx 1 root root   19 2007-12-04 22:54 java-6-sun -> java-6-sun-1.6.0.03
drwxr-xr-x 8 root root 4096 2007-12-06 19:32 java-6-sun-1.6.0.03
```
A directory named java-6-sun-1.6.0.03 and a link named java-6-sun that points to the directory.

I would use **/usr/lib/jvm/java-6-sun** as my JVM Installation directory.

You're using Java 5, but it should look similar.

I think you're making this much more complicated than it really is...

---

### Post by Bpa on 2008-01-02
Thank you all for taking the time to help me out and offer you knowledge.  What I ended up doing is point the JAVAHOME variable in the Makefile to the /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/ directory.  When someone on the phidgets forum answered my question there, they said that what I was actually looking for was the /bin directory that housed java.  This was actually in a subdirectory of the directory I pointed the makefile to, as well as the binary file that the symlink in /usr/bin/ pointed to, so hopefully what I have done will be sufficient.  I am unable to tell as of now. I didn't run into any errors when running the makefile, but I am unable to test, because I need to figure out where to put the phidget21.jar file, which I believe to be the interface to the C code, so that it will be found by the jvm.  When I try to run the example program it tells me that there is no phidget21 in java.library.path so I am assuming this is the problem. Thank you all again for you help.

---

### Post by xlinuks on 2008-01-03
Just a quick note, afaik programs like apache tomcat, Glassfish and alike require JAVA_HOME, perhaps you should check if JAVAHOME is fine too.

---

