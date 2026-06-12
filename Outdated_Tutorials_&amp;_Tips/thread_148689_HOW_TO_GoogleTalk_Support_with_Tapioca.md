---
title: "HOW TO: GoogleTalk Support with Tapioca"
date: 2006-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by dudus on 2006-03-22
I just posted a guide on how to install Tapioca, a new voip instant mesenger that has full iteroperability with Google Talk.

[ https://wiki.ubuntu.com/Tapioca]("https://wiki.ubuntu.com/Tapioca")

Post any doubt here

---

### Post by markhm on 2006-04-17
Hello Dudus, anyone,

When trying the binary-install (Installing Tapioca on Ubuntu 5.10 Breezy Badger) , I get the following error:

The following packages have unmet dependencies:
  tapiocaui0.3: Depends: tapioca0.3-xmpp but it is not going to be installed
                Depends: farsight0.1-plugins-rtp but it is not going to be installed
E: Broken packages

Could anyone shed any light on this?

Many thanks,
- Mark

---

### Post by blackant on 2006-04-17
I installed. everything goes well.
Nice and simple client. But can it be minimize to the top right corner like the gaim?

---

### Post by Treviño on 2006-04-17
Tried some time ago on my Kubuntu linux but when I click on Login button, tapioca closes and seeing konsole I get a «Segmentation fault» error :o.

Ideas?

---

### Post by mozzi on 2006-04-26
I have the same problem.
** (tapiocaui:8872): WARNING **: failed to open connection to dbus
Segmentation fault

---

### Post by JoshHendo on 2006-04-27
Works fine here. Seems to work fine with some people, though not with others.
Just using Ubuntu here (as apposed to kubuntu etc)

---

### Post by stalefries on 2006-04-27
It's worked fine for me so far, although I haven't used it much, as my only contacts prefer text chat, and I use Gaim for that (as it can be "minimized" to the notification panel like an above post said). Therefore, the speech function has been used...once. And it was only 1-way. Well, at least it hasn't crashed yet!

---

### Post by bestiarosa on 2006-05-01
I am also getting that "Segmentation fault" error message when running Tapioca under Kubuntu. Looks like Tapioca has some problems running under Kubuntu. It's a real pity and I hope it will be solved soon. I want out with Skype.

---

### Post by kilps on 2006-08-19
> **dudus said:**
> I just posted a guide on how to install Tapioca, a new voip instant mesenger that has full iteroperability with Google Talk.

[ https://wiki.ubuntu.com/Tapioca]("https://wiki.ubuntu.com/Tapioca")

Post any doubt here
The link there doesn't seem to work, and I can''t figure out what to do with the file I downloaded from [http://extindt01.indt.org/VoIP/apt/dists/dapper/main/binary-i386/](http://extindt01.indt.org/VoIP/apt/dists/dapper/main/binary-i386/) :(

---

### Post by finferflu on 2006-08-29
> **kilps said:**
> The link there doesn't seem to work, and I can''t figure out what to do with the file I downloaded from [http://extindt01.indt.org/VoIP/apt/dists/dapper/main/binary-i386/](http://extindt01.indt.org/VoIP/apt/dists/dapper/main/binary-i386/) :(

Exactly, that's just a file with a list of packages.. I think it must have a purpose, although my ignorance does not suggest me anything...

--EDIT--

Actually I found this: [http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide#Installing_packages_with_apt-get.2Faptitude](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide#Installing_packages_with_apt-get.2Faptitude) which is even easier than the how-to in the wiki, since you just install it with aptitude/apt-get. 

Everything is written there, but in short (for Dapper Drake):

Add deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) dapper main 

to /etc/apt/sources.list

then open a terminal and run:

```
sudo aptitude update
```

and finally:

```
sudo aptitude install tapiocaui0.3
```

after the installation just run tapioca either by selecting it in the menu (Applications > Internet > Tapioca) or running **tapiocacui** in a terminal.

At the login prompt just insert your Google Talk username and password and it will just work. 

(actually with this current version you can also minimise it to tray).

---

### Post by stalefries on 2006-09-21
For you Kubuntu users, it may be that it's segfaulting because you don't have D-BUS.

---

### Post by icehammer on 2007-08-27
How do i install Tapioca on Fiesty?? I tried most of the stuff i could find.. nothing worked..

---

### Post by mariuz on 2007-09-17
try to install it from source code 

[http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide)

---

### Post by Flake Remix on 2007-10-23
Hello,

What username and password are supposed to be?

I tried [FONT="Courier New"]my.username@gmail.com[/FONT] and [FONT="Courier New"]my.username[/FONT] but it stays being Logging in and nothing happens!

> **finferflu said:**
> 

At the login prompt just insert your Google Talk username and password and it will just work. 

Anyways, why Google Talk username? It's not said that Tapioca is GTalk client.

---

