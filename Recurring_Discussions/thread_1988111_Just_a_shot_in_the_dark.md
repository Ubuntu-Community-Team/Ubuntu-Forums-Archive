---
title: "Just a shot in the dark"
date: 2012-05-26
forum: Recurring Discussions
---

### Post by cptrohn on 2012-05-26
Just HOW closely related are Ubuntu and OSX with their Unix roots?

I've been using a Macbook for work and as a part of their stock setup for users Office Mac 2011 is included.....

That got me to thinking, if it would be possible to convert that .dmg install to a .deb package somehow and be able to use OfficeMac11 natively in Ubuntu....

Hmmm might have to research this further to see if it would be possible...  they can't be THAT much different can they?

---

### Post by craig10x on 2012-05-27
Doesn't sound possible if you read this ubuntu forum link from 2010:
[http://ubuntuforums.org/showthread.php?t=1544554](http://ubuntuforums.org/showthread.php?t=1544554)

Isn't there a linux equivalent you can use to the program?

---

### Post by KiwiNZ on 2012-05-27
OSX is not Unix, it is Unix like and certified, it is based on NetBSD, FreeBSD and Mach kernel.

---

### Post by 3rdalbum on 2012-05-27
> **cptrohn said:**
> Just HOW closely related are Ubuntu and OSX with their Unix roots?

Very far apart. Mac OS X uses a heavily modified Unix kernel and userspace, and Ubuntu uses a fairly stock (by comparison) Linux kernel and GNU userspace. They might sound similar, but in fact they only share a couple of common principles.

> That got me to thinking, if it would be possible to convert that .dmg install to a .deb package somehow and be able to use OfficeMac11 natively in Ubuntu....

Hmmm might have to research this further to see if it would be possible...  they can't be THAT much different can they?

OS X programs are written using Apple's APIs, Linux programs are written using Linux APIs. There's no binary compatibility, and not even source code compatibility. It's like a German trying to talk to a Spaniard - their alphabets have the same letters, but everything else in the language is completely different.

A lot of people have proposed the same thing ("Why can't they write something like Wine but that runs Mac programs, it should be easy") but in fact it would be only marginally easier to write such a program than it was to write Wine. Maybe even more difficult, depending on the quality of Apple's APIs.

Android is another one where a lot of people say "Why can't you just install Android apps on Ubuntu, they both use the Linux kernel?". The kernel has very little to do with whether a program will run. It's the libraries and services running on top of the kernel that actually allow the program to "hook into" the system, and Android and a regular Linux distro are totally different above the kernel level.

---

### Post by zombifier25 on 2012-05-27
> **3rdalbum said:**
> Very far apart. Mac OS X uses a heavily modified Unix kernel and userspace, and Ubuntu uses a fairly stock (by comparison) Linux kernel and GNU userspace. They might sound similar, but in fact they only share a couple of common principles.



OS X programs are written using Apple's APIs, Linux programs are written using Linux APIs. There's no binary compatibility, and not even source code compatibility. It's like a German trying to talk to a Spaniard - their alphabets have the same letters, but everything else in the language is completely different.

A lot of people have proposed the same thing ("Why can't they write something like Wine but that runs Mac programs, it should be easy") but in fact it would be only marginally easier to write such a program than it was to write Wine. Maybe even more difficult, depending on the quality of Apple's APIs.

Android is another one where a lot of people say "Why can't you just install Android apps on Ubuntu, they both use the Linux kernel?". The kernel has very little to do with whether a program will run. It's the libraries and services running on top of the kernel that actually allow the program to "hook into" the system, and Android and a regular Linux distro are totally different above the kernel level.

Agree, but Ubuntu for Android can run Android apps natively. Dunno how they did that, but it is possible.

---

### Post by BeRoot ReBoot on 2012-05-27
> **KiwiNZ said:**
> OSX is not Unix, it is Unix like and certified, it is based on NetBSD, FreeBSD and Mach kernel.

I thought the certification means OSX *is* a UNIX, whereas GNU/Linux is "UNIX-like"?

---

### Post by zombifier25 on 2012-05-27
> **BeRoot ReBoot said:**
> I thought the certification means OSX *is* a UNIX, whereas GNU/Linux is "UNIX-like"?

Unix does not turn its name into Mac OS X, so Mac OS X is Unix-like :popcorn:

---

### Post by BeRoot ReBoot on 2012-05-27
> **zombifier25 said:**
> Unix does not turn its name into Mac OS X, so Mac OS X is Unix-like :popcorn:

You obviously have no idea what it means for an operating system to be a UNIX. Mac OSX has received the open brand UNIX 03 certification, that makes it a UNIX, just like AIX, Solaris, HP/UX and other Unices. GNU/Linux has no such certification but is designed with working like UNIX in mind, which makes it a UNIX-like operating system.

---

### Post by zombifier25 on 2012-05-27
> **BeRoot ReBoot said:**
> You obviously have no idea what it means for an operating system to be a UNIX. Mac OSX has received the open brand UNIX 03 certification, that makes it a UNIX, just like AIX, Solaris, HP/UX and other Unices. GNU/Linux has no such certification but is designed with working like UNIX in mind, which makes it a UNIX-like operating system.

Forgive my ignorance and lack of research. I thought only UNIX as UNIX may be referred to as UNIX.

---

### Post by mips on 2012-05-27
> **KiwiNZ said:**
> OSX is not Unix, it is Unix like and certified, it is based on NetBSD, FreeBSD and Mach kernel.

> **BeRoot ReBoot said:**
> I thought the certification means OSX *is* a UNIX, whereas GNU/Linux is "UNIX-like"?

Last time I checked OS X was Unix and certified as such. BSD, Linux are referred to as Unix-like although BSD would probably qualify for the Unix name should they decide to cough up the $$$ to have it certified.
[http://www.opengroup.org/openbrand/register/](http://www.opengroup.org/openbrand/register/)


> **zombifier25 said:**
> Unix does not turn its name into Mac OS X, so Mac OS X is Unix-like :popcorn:

Neither does Solaris, Tru64 etc.

---

### Post by BeRoot ReBoot on 2012-05-27
> **zombifier25 said:**
> Forgive my ignorance and lack of research. I thought only UNIX as UNIX may be referred to as UNIX.

UNIX isn't a single OS, it's a specification. An OS that is certified to conform to that specification is referred to as "a UNIX" (plural "Unices" or "Unixen").

---

### Post by mosaic2s on 2012-05-27
> **3rdalbum said:**
> Very far apart. Mac OS X uses a heavily modified Unix kernel and userspace, and Ubuntu uses a fairly stock (by comparison) Linux kernel and GNU userspace. They might sound similar, but in fact they only share a couple of common principles.
..........................
Android is another one where a lot of people say "Why can't you just install Android apps on Ubuntu, they both use the Linux kernel?". The kernel has very little to do with whether a program will run. It's the libraries and services running on top of the kernel that actually allow the program to "hook into" the system, and Android and a regular Linux distro are totally different above the kernel level.

Even I was thinking that ANDROID based phones should be easy to sync with Linux. Also, with so many OS around running ipad, samsung tab, iphone, blackberry - it makes sense for someone to provide for sync service across the OS for contacts, emails etc.

---

### Post by forrestcupp on 2012-05-27
OSX was based on BSD, which is Unix (even though not certified). Linux is not based on Unix at all; it was originally meant to clone Minix, which is different than Unix. So first of all, Linux is not even compatible with Unix on the kernel level. 

Secondly, Darwin (MacOS X's Unix base) is only the very base of the whole OS. They have so many proprietary things on top of that that make up their entire OS that there's no way you could hope for anything to easily be ported to even a Unix based OS.

> **zombifier25 said:**
> Agree, but Ubuntu for Android can run Android apps natively. Dunno how they did that, but it is possible.

I think you have it backwards. Ubuntu for Android makes Android run Ubuntu apps.

---

### Post by BeRoot ReBoot on 2012-05-27
> **forrestcupp said:**
> Linux is not based on Unix at all; it was originally meant to clone Minix, which is different than Unix. So first of all, Linux is not even compatible with Unix on the kernel level.

I'm talking about GNU/Linux, which was intended from the beginning to be a Free UNIX clone. I'm aware of the origins of the Linux kernel, but the OS as a whole is supposed to be UNIX-like.

---

### Post by Mikeb85 on 2012-05-27
> **3rdalbum said:**
> 
Android is another one where a lot of people say "Why can't you just install Android apps on Ubuntu, they both use the Linux kernel?". The kernel has very little to do with whether a program will run. It's the libraries and services running on top of the kernel that actually allow the program to "hook into" the system, and Android and a regular Linux distro are totally different above the kernel level.

Android apps don't run because most of them run in Dalvik, or are ARM architecture only.  If you had a Linux distro on ARM, you could get Android apps to run fairly easily, by adding the required Dalvik and Java libraries.  (See Alien Dalvik)  That's essentially what Ubuntu on Android is - Ubuntu on ARM using Android's kernel, with Dalvik and a bunch of Android libraries.

---

### Post by MisterGaribaldi on 2012-05-28
**@cptrohn:** Take a look at [this video](http://www.youtube.com/watch?v=-7GMHB3Plc8). It covers the whole "Is Mac OS X Unix?" basic part of your question.

Also, .DMG -> .DEB… .DMG is a disk image. .DEB is a packaging system. In the highly over-simplified sense, I'm sure you could use .DEB to deploy Mac OS X software. The problem is that you'd basically be talking about using dpkg to install a Mac OS X app on a Mac OS X box.

I won't repeat any of what's been said above vis à vis (Linux) binaries and Mac OS X binaries. That horse has been effectively beaten to a pulp already.

---

