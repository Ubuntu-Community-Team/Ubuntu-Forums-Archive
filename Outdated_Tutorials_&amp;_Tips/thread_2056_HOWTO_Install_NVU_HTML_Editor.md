---
title: "HOWTO: Install NVU HTML Editor"
date: 2004-10-25
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-25
The following link has great information on getting NVU editor to work in Ubuntu:
 
 [http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3307060179)

---

### Post by wulle on 2004-11-09
hello,
you can also add the following repository to your sources.list

deb [http://www.linex.org/sources/linex/debian](http://www.linex.org/sources/linex/debian) sarge linex
deb [http://www?linex.org/sources/linex/debian](http://www?linex.org/sources/linex/debian) woody linex

do apt-get update en search for nvu--- dependencies are automatically resolved

wulle  \\:D/

---

### Post by wulle on 2004-11-09
sorry folks, did a mistype on line 2 --- must be:

deb [http://www.linex.org/sources/linex/debian](http://www.linex.org/sources/linex/debian) woody linex

wulle  :---)

---

### Post by KzR on 2004-11-12
Hello all !

I am a big noob under linux, but I love the Ubuntu Distrib

> /opt/nvu-0.50/nvu-bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


I've got this message after NVU's installation, HowTo install this Package ? libstdc++-libc6.2-2.so.3 it's doesn't exist in Synaptic  #-o

---

### Post by KzR on 2004-11-12
[http://packages.debian.org/stable/oldlibs/libstdc++2.10](http://packages.debian.org/stable/oldlibs/libstdc++2.10)

i'm downloading ths package  :-$

---

### Post by TravisNewman on 2004-11-12
[QUOTE=KzR][http://packages.debian.org/stable/oldlibs/libstdc++2.10](http://packages.debian.org/stable/oldlibs/libstdc++2.10)

i'm downloading ths package  :-$[/QUOTE]
 I believe you can install it from apt-get or synaptic. I never had to download anything other than nvu itself.

---

### Post by KzR on 2004-11-12
[QUOTE=panickedthumb]I believe you can install it from apt-get or synaptic. I never had to download anything other than nvu itself.[/QUOTE]


how do you install NVU ?

---

### Post by KzR on 2004-11-14
it's OK for me, i've just forgotten to enable universe in Synaptic

:p

---

### Post by TravisNewman on 2004-11-14
[QUOTE=panickedthumb]I believe you can install it from apt-get or synaptic. I never had to download anything other than nvu itself.[/QUOTE]
 No I mean you can install that package from synaptic, you still have to install Nvu the way they specified.

---

### Post by op3studios on 2005-05-31
Here's how it worked for me:

Nvu Install into Unbuntu is best done manually.
These two following urls will get Nvu working right, the process fixes the launch command so that you can preview launch your browser to see how things are in a browser you designate.  Mozilla is all I've tested.

  sudo apt-get doesn't work, yet.   Nor does installing from Synaptic.  I tried.

  Mozilla has a excellent web authoring tool: file > new> composer.  Composer and Nvu look almost identical...Nvu is a branch from the mozilla suite.  I understand Nvu has better CSS support and a site manager and it's bound to get better since it's on it's own now.

[http://www.ubuntulinux.org/wiki/HowToInstallNVUHTMLEditor](http://www.ubuntulinux.org/wiki/HowToInstallNVUHTMLEditor)

[http://www.nvu.com/download.html](http://www.nvu.com/download.html)

The Mozilla folder is located in my /etc

Mozilla-ext =   /var/lib/mozilla

The Prefs  =      /etc/mozilla.

I just did everything till I did it right.  You may have to sudo chown for permissions.  most of the sudo commands copy and paste into terminal.
Nvu works fine now.

The only thing left is getting my canon i550 running, or a cheap refurb friendly printer from the hardware list.
I've read some have installed canons so it can be done. 

I'm only a few days old so pardon please if there are any mistakes above do correct them.

Thanks to all the how to's 
Happy Hunting!

jz

---

### Post by jakew1991 on 2005-06-16
[QUOTE=op3studios]Here's how it worked for me:

Nvu Install into Unbuntu is best done manually.
These two following urls will get Nvu working right, the process fixes the launch command so that you can preview launch your browser to see how things are in a browser you designate.  Mozilla is all I've tested.

  sudo apt-get doesn't work, yet.   Nor does installing from Synaptic.  I tried.

  Mozilla has a excellent web authoring tool: file > new> composer.  Composer and Nvu look almost identical...Nvu is a branch from the mozilla suite.  I understand Nvu has better CSS support and a site manager and it's bound to get better since it's on it's own now.

[http://www.ubuntulinux.org/wiki/HowToInstallNVUHTMLEditor](http://www.ubuntulinux.org/wiki/HowToInstallNVUHTMLEditor)

[http://www.nvu.com/download.html](http://www.nvu.com/download.html)

The Mozilla folder is located in my /etc

Mozilla-ext =   /var/lib/mozilla

The Prefs  =      /etc/mozilla.

I just did everything till I did it right.  You may have to sudo chown for permissions.  most of the sudo commands copy and paste into terminal.
Nvu works fine now.

The only thing left is getting my canon i550 running, or a cheap refurb friendly printer from the hardware list.
I've read some have installed canons so it can be done. 

I'm only a few days old so pardon please if there are any mistakes above do correct them.

Thanks to all the how to's 
Happy Hunting!

jz[/QUOTE]
 Did you follow the "adding respitories" step in the ubuntu guide??

 - Jake

---

### Post by malaprohibita on 2005-06-23
I got it downloaded and installed just fine.  Now I can't find it in my application menus anywhere.  (I probably just did something a little bit wrong).

---

