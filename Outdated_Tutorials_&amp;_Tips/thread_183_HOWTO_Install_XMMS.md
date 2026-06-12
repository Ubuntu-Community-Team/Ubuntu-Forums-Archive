---
title: "HOWTO: Install XMMS?"
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
From the command line you can run the following command:
> sudo apt-get install xmms
If you get a error when trying to load xmms or it does not load after installation run the following command to install mikmod. Nvidia card users will need to follow this step.
> sudo apt-get install mikmod

---

### Post by deleric on 2004-10-11
Oh yeah that did the trick
 :D  :D  :D  :D  :D

---

### Post by Michael on 2004-10-12
Thanks a bunch :D

---

### Post by textguru on 2007-07-05
I already remove the CDROM of my server and wanting to install XMMS. What repository that I can use to install XMMS?

---

### Post by tackatucka on 2007-11-06
mmh i tried but there came up an error
> sudo: apt: command not found

so do I get this command running ?

thx for help =)

---

### Post by tackatucka on 2007-11-06
I just put a space between apt and -get, that was my mistake ^^

*slap myself

---

### Post by kavamaks on 2008-04-30
hello.
i'm new in ubuntu.
i already download xmms 1.2.11.tar.gz and place at dekstop place..
i type 'sudo apt-get install xmms' like ubuntu-geek said..
but nothing happen..

the messege i got, like this...

'potsmokers@devilcom:~$ sudo apt-get install xmms
[sudo] password for potsmokers: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate'

thanks for help..

---

### Post by crazy_scorpion on 2008-05-01
I have the same problem at Ubuntu 8.04:

root@scorpion:~# apt-get install xmms
Reading package lists... Done
[....]
E: Package xmms has no installation candidate
root@scorpion:~#

---

### Post by erwall on 2008-05-01
AFAIK xmms has been replaced with audacious

It's in the repos.

---

### Post by yetidude on 2008-05-13
> **erwall said:**
> AFAIK xmms has been replaced with audacious

It's in the repos.
thank you for the help

---

### Post by PinkFloyd102489 on 2008-05-14
Just to make it clear, a checkinstall of XMMS is available in the repos now. XMMS2 has "replaced" the original version but you can still get the original if you're like me and want to cling to it.

If you want specific plugins for it, you'll have to download them from the XMMS site and compile them if they arent in the repos.

---

### Post by notepad on 2008-05-20
> **PinkFloyd102489 said:**
> Just to make it clear, a checkinstall of XMMS is available in the repos now. XMMS2 has "replaced" the original version but you can still get the original if you're like me and want to cling to it.

If you want specific plugins for it, you'll have to download them from the XMMS site and compile them if they arent in the repos.

are you kidding? xmms2 has no gui.

forget about xmms people. audacious is the new deal.

---

### Post by Christmas on 2008-05-20
Thanks for this ubuntu-geek (can't find the Thank You button anywhere so...). I'm using Debian and XMMS is not even available in the repos (but Audacious) and I compiled it succesfully but when I was to start it, it wouldn't start, failing with some "can't load libxmms.so library". I did the mikmod trick and now it works. So thanks again.

---

### Post by cuentosdepapel on 2008-08-11
thanks very much for the solution! cheers

---

### Post by TMachado on 2008-12-15
I've installed xmms2 but has no gui.

Installed audacious but I really dont like it.

So, if I want to use a mp3 player "like winamp" I just have to install xmms am I right? So I've download tar.gz from xmms, and I'me following install instructions. But I have the following error when I run ./configure:

```
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

What should I do?

---

### Post by pegasusOnline on 2010-01-04
> **TMachado said:**
> I've installed xmms2 but has no gui.

Installed audacious but I really dont like it.

So, if I want to use a mp3 player "like winamp" I just have to install xmms am I right? So I've download tar.gz from xmms, and I'me following install instructions. But I have the following error when I run ./configure:

```
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```What should I do?

excuse me for my bad english:

here the solution!:

go to console from gnome:

execute :
sudo gedit /etc/apt/sources.list

put your version of Ubuntu


Debian Lenny 32- and 64-bit x86

deb [http://www.pvv.ntnu.no/~knuta/xmms/lenny](http://www.pvv.ntnu.no/~knuta/xmms/lenny) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/lenny](http://www.pvv.ntnu.no/~knuta/xmms/lenny) ./

Ubuntu Hardy 32- and 64-bit x86

deb [http://www.pvv.ntnu.no/~knuta/xmms/hardy](http://www.pvv.ntnu.no/~knuta/xmms/hardy) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/hardy](http://www.pvv.ntnu.no/~knuta/xmms/hardy) ./

Ubuntu Jaunty 32- and 64-bit x86

deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./


Ubuntu Karmic 32- and 64-bit x86

deb [http://www.pvv.ntnu.no/~knuta/xmms/karmic](http://www.pvv.ntnu.no/~knuta/xmms/karmic) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/karmic](http://www.pvv.ntnu.no/~knuta/xmms/karmic) ./

I have Ubuntu Karmic so i put 
deb [http://www.pvv.ntnu.no/~knuta/xmms/karmic](http://www.pvv.ntnu.no/~knuta/xmms/karmic) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/karmic](http://www.pvv.ntnu.no/~knuta/xmms/karmic) ./


then execute :
sudo apt-get update
sudo apt-get install xmms

then execute:

sudo /usr/bin/xmms  that all!! , enjoy!

---

