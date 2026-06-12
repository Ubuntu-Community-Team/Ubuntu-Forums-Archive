---
title: "Java doesn't initialize"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by wizle on 2008-08-21
Java seems to be installed but does not initialize on web pages! Can someone tell me how to rectify this please,all my games use Java

---

### Post by freak42 on 2008-08-21
for firefox 3:
-check that under edit->preferences->content the checkbox next to java is enabled.
- check that under tools->add ons->Plugins -> a java plugin is enabled

if it doesn't help, what java verison do you have installed?

type ```
java -version
``` on a command line and post the output

hth

---

### Post by briansykes on 2008-08-21
i have the same problem and the plugin never installs it gives errors and this is what java edition i have

java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)

i tried installing the java download myself but it gives an error no matter how i download it.

---

### Post by wizle on 2008-08-21
I have version 1.4.2    and in tools there is no java plug-in

---

### Post by tinny on 2008-08-21
First off are any of you using 64 Bit Ubuntu? (This can be more complicated)

When it comes to Java on Ubuntu you really want to use the Sun version not the default GNU Java version.

Make sure you have ALL the required Sun Java 6 packages installed.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

Then to check your install

```
java -version
```

If it all worked you should see something like this

```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```

---

### Post by briansykes on 2008-08-21
Alright this is what my terminal kicks out at me for trying the above commands.

```

brian@brian:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-bin is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```

Also, i had to install firefox onto Kubuntu it never came with it, i'm using the KDE4 version of kubuntu btw.

---

### Post by tinny on 2008-08-21
> **briansykes said:**
> Alright this is what my terminal kicks out at me for trying the above commands.

```

brian@brian:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-bin is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```

Also, i had to install firefox onto Kubuntu it never came with it, i'm using the KDE4 version of kubuntu btw.

I think this is because you're using a 64bit version of Ubuntu.

---

### Post by briansykes on 2008-08-22
It is i have an AMD Athlon 64 +3500 so does this mean java doesnt exist in a web browser for me?

---

### Post by tinny on 2008-08-22
> **briansykes said:**
> It is i have an AMD Athlon 64 +3500 so does this mean java doesnt exist in a web browser for me?

AMD64 is troublesome.

Basically you should install the 32bit version of Firefox on your 64 bit install.

Have a look at this...
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

---

### Post by briansykes on 2008-08-22
i went to the link you gave me and i tried to do the first thing it said gave errors said the package didn't exist, should i just format and put kubuntu 32bit on my system?

---

### Post by st33med on 2008-08-22
> **briansykes said:**
> i went to the link you gave me and i tried to do the first thing it said gave errors said the package didn't exist, should i just format and put kubuntu 32bit on my system?

No.
[URL="http://ubuntuforums.org/showthread.php?p=1174435"]
Try this post's script.[/URL]

---

### Post by tinny on 2008-08-22
> **briansykes said:**
> i went to the link you gave me and i tried to do the first thing it said gave errors said the package didn't exist, should i just format and put kubuntu 32bit on my system?

Sorry I was a bit lazy.

That other howto looks good.

---

### Post by philinux on 2008-08-22
I'm using 64bit.

Got openjdk-6-jre etc installed together with the icedtea-gcjwebplugin

Works fine.

As you've found there is no sun-java6 plugin in the 64bit version.

---

### Post by briansykes on 2008-08-22
Thanks for tyhe help everyone! that script worked perfectly.

---

### Post by tinny on 2008-08-22
> **philinux said:**
> I'm using 64bit.

Got openjdk-6-jre etc installed together with the icedtea-gcjwebplugin

Works fine.

As you've found there is no sun-java6 plugin in the 64bit version.

FYI

Some users around this forum have found that this icedtea plug-in doesnt work correctly on some applets. (mostly its fine)

Apparently the icedtea plug-in is really good in intrepid

---

### Post by tcyk on 2008-09-09
> **tinny said:**
> First off are any of you using 64 Bit Ubuntu? (This can be more complicated)

When it comes to Java on Ubuntu you really want to use the Sun version not the default GNU Java version.

Make sure you have ALL the required Sun Java 6 packages installed.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```
When I do this I get these after the install instruction:

    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    sun-java6-jre is already the newest version.
    sun-java6-jre set to manually installed.
    sun-java6-bin is already the newest version.
    Package sun-java6-plugin is not available, but is referred to by another package.
    This may mean that the package is missing, has been obsoleted, or
is only available from another source
    E: Package sun-java6-plugin has no installation candidate

Then to check your install

```
java -version
```

If it all worked you should see something like this

```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```

I try this and I get:
    java version "1.6.0_0"
    OpenJDK  Runtime Environment (build 1.6.0_0-b11)
    OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)

I'm not even sure I installed the 64-bit version of Ubuntu. I downloaded both versions. My computer is a Dell inspiron 530 dual core quad processor which is a 64-bit machine. Perhaps the "sun-java6-jre set to manually installed." line is a clue about my problem.

---

### Post by tcyk on 2008-09-09
> **tinny said:**
> AMD64 is troublesome.

Basically you should install the 32bit version of Firefox on your 64 bit install.

Have a look at this...
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

I think perhaps you have solved my problem. I downloaded both the 32-bit and 64 versions of Hardy ... I was intending to install the 32-bit version on my laptop and the 64-bit version on the desktop computers. It appears I installed the wrong version on the desktop. I find my java version is a 64-bit version. Although I do not have an AMD processor I thought the instructions in the link might help me solve my problem. I got the following interesting message:

 sudo apt-get install ia32-libs lib32asound2 util-linux

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
lib32asound2 is already the newest version.
lib32asound2 set to manually installed.
util-linux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 I was trying to figure how how to determine if I had the 64-bit version and I believe I have found the answer to that question.

When I check the firefox version I get:

Mozilla Firefox 3.0.1, Copyright (c) 1998 - 2008 mozilla.org. I don't know for sure that this is a 32-bit version but it works so I assume it is.

Charlie

---

### Post by tinny on 2008-09-09
> **tcyk said:**
> I think perhaps you have solved my problem. I downloaded both the 32-bit and 64 versions of Hardy ... I was intending to install the 32-bit version on my laptop and the 64-bit version on the desktop computers. It appears I installed the wrong version on the desktop. I find my java version is a 64-bit version. Although I do not have an AMD processor I thought the instructions in the link might help me solve my problem. I got the following interesting message:

 sudo apt-get install ia32-libs lib32asound2 util-linux

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
lib32asound2 is already the newest version.
lib32asound2 set to manually installed.
util-linux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 I was trying to figure how how to determine if I had the 64-bit version and I believe I have found the answer to that question.

When I check the firefox version I get:

Mozilla Firefox 3.0.1, Copyright (c) 1998 - 2008 mozilla.org. I don't know for sure that this is a 32-bit version but it works so I assume it is.

Charlie

So you have 32bit Ubuntu and 32bit Firefox right? And it all works. 

If so :-)

---

### Post by tcyk on 2008-09-10
> **tinny said:**
> So you have 32bit Ubuntu and 32bit Firefox right? And it all works. 

If so :-)

No it doesn't work, I play duplicate bridge on the Internet at [www.bridgebase.com](www.bridgebase.com). They recently added a Flash player version so I don't have to use the installed windows software to play there. It works when running windows. When I try to reach the site running Ubuntu Hardy Heron, I try to log in and get the message, "Connection lost." I decided to try to log onto [www.pogo.com](www.pogo.com) and was told I needed to install Flash player. I downloaded the files via Synaptic Package Manager. The firefox tools - addons - plugins shows:
Default Plugin
Demo Print Plugin for unix/linux
DivX Web Player
GCJ Web Browser Plugin (using IcedTea) 1.0
Helix DNA Plugin: RealPlayer G2 Plug-in Compatible (compatible; totem)
Itunes Application Detector
QuickTime Plug-in 7.2.0
Shockwave Flash 9.0 r 124
Squeak
Totem Web Browser Plugin 2.22.1
VLC Mutimedia Plugin (compatible Totem 2.22.1)
Windows Media Player Plug-in (compatible Totem)

I have spent so much time and tried so many suggestions that I'm getting really disgusted with the whole thing.

---

### Post by meepster on 2008-09-10
I'm a total noob, so I apologize for the stupidity of this question - but how do you tell if you've got a 64-bit or a 32-bit machine?  

(I have the same problem with my Java - tried installing it, Firefox doesn't recognize the plugin no matter what I do)

-meepster

---

### Post by tcyk on 2008-09-10
> **meepster said:**
> I'm a total noob, so I apologize for the stupidity of this question - but how do you tell if you've got a 64-bit or a 32-bit machine?  

(I have the same problem with my Java - tried installing it, Firefox doesn't recognize the plugin no matter what I do)

-meepster

That is exactly what I have been trying to figure out. I believe I have installed a 32-bit version of Ubuntu and Sun sees I have a 64-bit machine and installs a 64-bit version of jre.

I guess the big question is how to get a 32-bit version of jre for my 64-bit machine or can I install 64-bit Ubuntu and not lose the work I have done to date ... which isn't so very much but I already have two separate versions of Ubuntu on this machine now. ... and I don't know if they are 32 or 64-bit systems.

---

### Post by SnakeHips on 2008-10-18
> **meepster said:**
> I'm a total noob, so I apologize for the stupidity of this question - but how do you tell if you've got a 64-bit or a 32-bit machine?  

(I have the same problem with my Java - tried installing it, Firefox doesn't recognize the plugin no matter what I do)

-meepster

In terminal type

```
uname -m
```

pete@desk:~$ uname -m 
x86_64
pete@desk:~$

---

