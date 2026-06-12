---
title: "muon software center crashed"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by omar ahmad on 2012-01-24
hi all, 
I am using kubuntu 11.10 and when i try to open muon software center always crash
i tried those commands
> sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get update
and uninstall muon software center and reinstall it from muon package center
and no change
then i trien this command
> 
sudo apt-get purge policykit-1 policykit-desktop-privileges polkit-kde-1i got
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xul-ext-ubufox : Depends: apturl (>= 0.1.2ubuntu1) but it is not going to be installed or
                           apturl-kde but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.any way to slove this problem
thanks a lot

---

### Post by omar ahmad on 2012-01-26
program terminal output


KCrash: Application 'muon-installer' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/k-omar/.kde/socket-kubuntu/kdeinit4__0
QSocketNotifier: Invalid socket 13 and type 'Read', disabling.

thanks

---

### Post by sulyi on 2012-01-26
Try to uncomment 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
lines in /etc/apt/source.list, then:
```

sudo apt-get upgrade
sudo apt-get update
```
That did it for me.
It installed these packages: x11-common xorg xserver-xorg xserver-xorg-input-all xserver-xorg-video-all

---

### Post by sulyi on 2012-01-26
btw a crash report would be nice

---

### Post by QIII on 2012-01-26
If you are issuing the commands

```
sudo apt-get upgrade
sudo apt-get update
```

in that order, you should reverse the order.  I would also use dist-upgrade.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

dist-upgrade will attempt to resolve any dependencies.

Contrary to the misconception of many, it does not attempt to upgrade your current version to the next version.  That is a different command.

---

### Post by omar ahmad on 2012-01-27
> **sulyi said:**
> Try to uncomment 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
lines in /etc/apt/source.list, then:
```

sudo apt-get upgrade
sudo apt-get update
```That did it for me.
It installed these packages: x11-common xorg xserver-xorg xserver-xorg-input-all xserver-xorg-video-all

thanks a lot i made it and the program runs in perfect way
thanks again

> **sulyi said:**
> btw a crash report would be nice

I have already posted it many times

> **QIII said:**
> If you are issuing the commands

```
sudo apt-get upgrade
sudo apt-get update
```in that order, you should reverse the order.  I would also use dist-upgrade.

```
sudo apt-get update
sudo apt-get dist-upgrade
```dist-upgrade will attempt to resolve any dependencies.

Contrary to the misconception of many, it does not attempt to upgrade your current version to the next version.  That is a different command.

i will notie it next time 
thanks


 I want to ask about something else plz
about [COLOR=Red]java[/COLOR]
in windows xp i used to run java vm and it was perfect in everything 
how can i download java in kubuntu  i tried some java application but  it did not work probably for example in 
chat sites the chat window does not close 
how can i use java application in easy way as JAVA VM in XP
thanks for your assistance

---

### Post by QIII on 2012-01-27
I'm on my cell right now so I can't link it in, but google the four following words

easy linux tips java

There's a great tutorial with step by step instructions that you can copy and paste in the terminal.

---

### Post by sulyi on 2012-01-27
my bad, but i did do in the right order, just posted wrong

---

### Post by sulyi on 2012-01-27
yeah, i get these packages that has the java interpreter
gcj-4.4-jre-headless
gcj-4.6-jre-headless
openjdk-6-jre-headless
gcj-4.5-jre-headless
openjdk-7-jre-headless

i think installing one of them would be enought to run applets in a browser, though i would install something like openjdk-7-jre insted it installs more package and dependences

i've learned about a sun-java6-jre (or something like that)  package too, but i've never found that.

---

### Post by omar ahmad on 2012-01-27
From setting i have (open JDK java6 policy tool)
is this java??
but nothing integrated in firefox
i have searched about easy linux tips java but i can't find this tutorial but i will keep searching
Is it nessasry to install java add-ons in firefox??
thanks

edit
(from terminal)
java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)

---

### Post by QIII on 2012-01-27
OpenJDK is an open source implementation of Java.  It would be very nice if OpenJDK worked everywhere, but it doesn't.  Some web sites and software don't recognize it as Java, so you sometimes have problems with it.

Here's the tutorial:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Follow it to the letter.

---

### Post by sulyi on 2012-01-27
So icedtea-plugin is a OpenJDK plugin for browsers, if i get this right.
I've just installed it looks ok, maybe it is a bit slow.
Why use oracle jre?
My first bet'd be development and testing purposes.
In that case i'll have to install jdk first. Is there an alternative for that too?
If that time comes when I do start java development, this tutorial'll be pretty good for me.
Thanks in advance.

---

### Post by QIII on 2012-01-27
It is hoped that the world will come to know and love OpenJDK, but that is simply not the case right now.

Yes, when you develop - and you don't want your creation to be a red-headed step child - use Oracle/Sun JDK.

Java 7 is out and pretty much settled for now, so you can use it in place of 6.

---

### Post by omar ahmad on 2012-01-29
I did every step with right order
and the Java installed in correct way 
but i still have problem in any site i want to open chat applent 
i cannot close it ?
i can close it only by closing the browser
i cant under stand why!!!!!!!

---

### Post by sulyi on 2012-01-29
Why, haha, good question. 
It could have several reasons. First of all maybe it can close just takes some time. Other reason'd be a bug in the applet, or some where else, browser, jvm.

Anyway what kind of applet is this? Are we talking about one applet or several different applets?
Java applets are embed in html. So they can be hide, but not closed, as far as I know.

---

### Post by omar ahmad on 2012-02-01
I tried many applets and the same result every thing ok except the x buttom
i tried it also on firefox and Google chrome
i just wondering why?
but for now if i want to close something i close the page it self
thanks 4 help

---

