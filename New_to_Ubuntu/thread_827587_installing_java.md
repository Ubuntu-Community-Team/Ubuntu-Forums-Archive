---
title: "installing java"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by fetisha on 2008-06-12
I didn't have a problem with this in gutsy, I just installed the ubuntu restricted extras and accepted the license, but with hardy I'm having some difficulties.
I went into the package manager and installed sun-java6-bin and the jre and plugin and it is still not working. I also installed the restricted extras and it's not working. Any suggestions?

---

### Post by perlluver on 2008-06-12
> **fetisha said:**
> I didn't have a problem with this in gutsy, I just installed the ubuntu restricted extras and accepted the license, but with hardy I'm having some difficulties.
I went into the package manager and installed sun-java6-bin and the jre and plugin and it is still not working. I also installed the restricted extras and it's not working. Any suggestions?

sudo update-alternatives --config java and select SUN Jre

---

### Post by Sinkingships7 on 2008-06-12
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
That should do it.

---

### Post by fetisha on 2008-06-13
> **Sinkingships7 said:**
> ```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
That should do it.

Did that. Still not working.
It gave me this, don't know if it will help:

justin@comp:~$ sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-plugin is already the newest version.
The following NEW packages will be installed:
  sun-java6-fonts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1816B of archives.
After this operation, 115kB of additional disk space will be used.
Selecting previously deselected package sun-java6-fonts.
(Reading database ... 118533 files and directories currently installed.)
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-06-0ubuntu1_all.deb) ...
Setting up sun-java6-fonts (6-06-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

---

### Post by fetisha on 2008-06-13
> **perlluver said:**
> sudo update-alternatives --config java and select SUN Jre

Did that. Still no luck.
it gave me this:

justin@comp:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

---

### Post by stchman on 2008-06-13
> **fetisha said:**
> I didn't have a problem with this in gutsy, I just installed the ubuntu restricted extras and accepted the license, but with hardy I'm having some difficulties.
I went into the package manager and installed sun-java6-bin and the jre and plugin and it is still not working. I also installed the restricted extras and it's not working. Any suggestions?

Are you using the 64 bit version of Ubuntu?  If yes then the plugin will not function.  Here is how to install Java in Ubuntu.

32 bit
```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

64 bit (Install Icedtea)
```
sudo apt-get -y install icedtea-java7-jre icedtea-java7-jdk icedtea-java7-plugin
```

This works for me on 32bit and 64 bit.  If you want the Lucida fonts I have them on my site in tool section.  The 64 bit version does not have the Lucida fonts.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

---

### Post by gandaran on 2008-06-13
installing the ubuntu-restricted-extras is a bad option for hardy 8.04 as it will install open java.
go to synaptic and remove completely  the open java, just leave the sun-java6-jre, sun-java6-bin and sun-java6-plugin installed.

one question, you running firefox 3 or firefox 2?

---

### Post by fetisha on 2008-06-13
> **stchman said:**
> Are you using the 64 bit version of Ubuntu?  If yes then the plugin will not function.  Here is how to install Java in Ubuntu.

32 bit
```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

64 bit (Install Icedtea)
```
sudo apt-get -y install icedtea-java7-jre icedtea-java7-jdk icedtea-java7-plugin
```

This works for me on 32bit and 64 bit.  If you want the Lucida fonts I have them on my site in tool section.  The 64 bit version does not have the Lucida fonts.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Honestly... I don't remember whether it was 32 or 64 bit that I installed, but I'm 75% positive that it was the 32 bit.
I tried both and it still doesn't work.

```
justin@comp:~$ sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-fonts is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source
The following NEW packages will be installed:
  sun-java6-jdk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9625kB of archives.
After this operation, 32.4MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jdk.
(Reading database ... 118548 files and directories currently installed.)
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-06-0ubuntu1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up sun-java6-jdk (6-06-0ubuntu1) ...

justin@comp:~$ sudo apt-get -y install icedtea-java7-jre icedtea-java7-jdk icedtea-java7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openjdk-6-jdk
Suggested packages:
  openjdk-6-demo openjdk-6-source
The following NEW packages will be installed:
  icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin openjdk-6-jdk
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 9384kB of archives.
After this operation, 31.9MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe openjdk-6-jdk 6b09-0ubuntu2 [9376kB]
Get:2 http://us.archive.ubuntu.com hardy/universe icedtea-java7-jdk 7~b24-1.6-0ubuntu5 [2762B]
Get:3 http://us.archive.ubuntu.com hardy/universe icedtea-java7-jre 7~b24-1.6-0ubuntu5 [2758B]
Get:4 http://us.archive.ubuntu.com hardy/universe icedtea-java7-plugin 7~b24-1.6-0ubuntu5 [2750B]
Fetched 9384kB in 14s (644kB/s)                                                
Selecting previously deselected package openjdk-6-jdk.
(Reading database ... 118666 files and directories currently installed.)
Unpacking openjdk-6-jdk (from .../openjdk-6-jdk_6b09-0ubuntu2_i386.deb) ...
Selecting previously deselected package icedtea-java7-jdk.
Unpacking icedtea-java7-jdk (from .../icedtea-java7-jdk_7~b24-1.6-0ubuntu5_all.deb) ...
Selecting previously deselected package icedtea-java7-jre.
Unpacking icedtea-java7-jre (from .../icedtea-java7-jre_7~b24-1.6-0ubuntu5_all.deb) ...
Selecting previously deselected package icedtea-java7-plugin.
Unpacking icedtea-java7-plugin (from .../icedtea-java7-plugin_7~b24-1.6-0ubuntu5_all.deb) ...
Setting up openjdk-6-jdk (6b09-0ubuntu2) ...

Setting up icedtea-java7-jdk (7~b24-1.6-0ubuntu5) ...
Setting up icedtea-java7-jre (7~b24-1.6-0ubuntu5) ...
Setting up icedtea-java7-plugin (7~b24-1.6-0ubuntu5) ...

```

---

### Post by alienexplorers on 2008-06-13
If you are using firefox 3 or 2 did you sym-link the libjavaplugin_oji.so file to your appropriate plugins folder in the firefox you are using?

---

### Post by fetisha on 2008-06-13
> **alienexplorers said:**
> If you are using firefox 3 or 2 did you sym-link the libjavaplugin_oji.so file to your appropriate plugins folder in the firefox you are using?

No, how would I go about doing that?

---

### Post by stchman on 2008-06-15
> **fetisha said:**
> Honestly... I don't remember whether it was 32 or 64 bit that I installed, but I'm 75% positive that it was the 32 bit.
I tried both and it still doesn't work.

```
justin@comp:~$ sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-fonts is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source
The following NEW packages will be installed:
  sun-java6-jdk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9625kB of archives.
After this operation, 32.4MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jdk.
(Reading database ... 118548 files and directories currently installed.)
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-06-0ubuntu1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up sun-java6-jdk (6-06-0ubuntu1) ...

justin@comp:~$ sudo apt-get -y install icedtea-java7-jre icedtea-java7-jdk icedtea-java7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openjdk-6-jdk
Suggested packages:
  openjdk-6-demo openjdk-6-source
The following NEW packages will be installed:
  icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin openjdk-6-jdk
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 9384kB of archives.
After this operation, 31.9MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe openjdk-6-jdk 6b09-0ubuntu2 [9376kB]
Get:2 http://us.archive.ubuntu.com hardy/universe icedtea-java7-jdk 7~b24-1.6-0ubuntu5 [2762B]
Get:3 http://us.archive.ubuntu.com hardy/universe icedtea-java7-jre 7~b24-1.6-0ubuntu5 [2758B]
Get:4 http://us.archive.ubuntu.com hardy/universe icedtea-java7-plugin 7~b24-1.6-0ubuntu5 [2750B]
Fetched 9384kB in 14s (644kB/s)                                                
Selecting previously deselected package openjdk-6-jdk.
(Reading database ... 118666 files and directories currently installed.)
Unpacking openjdk-6-jdk (from .../openjdk-6-jdk_6b09-0ubuntu2_i386.deb) ...
Selecting previously deselected package icedtea-java7-jdk.
Unpacking icedtea-java7-jdk (from .../icedtea-java7-jdk_7~b24-1.6-0ubuntu5_all.deb) ...
Selecting previously deselected package icedtea-java7-jre.
Unpacking icedtea-java7-jre (from .../icedtea-java7-jre_7~b24-1.6-0ubuntu5_all.deb) ...
Selecting previously deselected package icedtea-java7-plugin.
Unpacking icedtea-java7-plugin (from .../icedtea-java7-plugin_7~b24-1.6-0ubuntu5_all.deb) ...
Setting up openjdk-6-jdk (6b09-0ubuntu2) ...

Setting up icedtea-java7-jdk (7~b24-1.6-0ubuntu5) ...
Setting up icedtea-java7-jre (7~b24-1.6-0ubuntu5) ...
Setting up icedtea-java7-plugin (7~b24-1.6-0ubuntu5) ...

```

I guess I should have been more clear.  If you have 32 bit use the SUN Java.  If you have 64 bit used the Icedtea version.  I do not know what will happen if you install both.

To check to see if you are running 64 bit do a uname -a in a terminal and see if you have an "x86_64" in the kernel.  Else you will get an "i686" in the kernel description.

---

