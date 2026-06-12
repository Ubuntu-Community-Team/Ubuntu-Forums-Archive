---
title: "Mono Visual Basic compiler... where?"
date: 2007-06-22
forum: Programming Talk
---

### Post by XeroZohar on 2007-06-22
I have a question for anyone that does Visual Basic work using Mono on Ubuntu (Feisty in particular).

According to "mono -V" I have 1.2.3 of Mono, which should, according to the mono-project.com website, include a Visual Basic .NET compiler called "vbnc".  After installing all the mono packages I could check from the Ubuntu repositories, I still can't find that particular program/command.  Heck, I've googled all over the place trying to figure out why it doesn't exist after installing all those mono packages, or where I could get just that compiler.

The thing is, I want to start learning VB.net and making sure I don't have to compile/run on Windows is the first step since I prefer working in a Linux environment.  Of course, I have no clue how Visual Basic works exactly.

If anyone has a clue why I can't find this compiler, or can point it out in case I'm somehow blind to it's existence, or even where I could get a package for (X)Ubuntu that contains just that mono-basic module (if it exists), I'd be grateful.

---

### Post by lukew on 2007-06-23
> **XeroZohar said:**
> I have a question for anyone that does Visual Basic work using Mono on Ubuntu (Feisty in particular).

According to "mono -V" I have 1.2.3 of Mono, which should, according to the mono-project.com website, include a Visual Basic .NET compiler called "vbnc".  After installing all the mono packages I could check from the Ubuntu repositories, I still can't find that particular program/command.  Heck, I've googled all over the place trying to figure out why it doesn't exist after installing all those mono packages, or where I could get just that compiler.

The thing is, I want to start learning VB.net and making sure I don't have to compile/run on Windows is the first step since I prefer working in a Linux environment.  Of course, I have no clue how Visual Basic works exactly.

If anyone has a clue why I can't find this compiler, or can point it out in case I'm somehow blind to it's existence, or even where I could get a package for (X)Ubuntu that contains just that mono-basic module (if it exists), I'd be grateful.

hi,

in the back of my mono book it mentions about basic.net. The compiler is mbas; i presume you need to install mono-devel; however i use monodevelop.

people report that vb. net is more towards c# than towards previous versions of vb. A lot of vb programmers are converting to c# and not bothering with vb.net. In all honestly i would do the same.

Luke

---

### Post by XeroZohar on 2007-06-25
I have that package installed, and there's no mbas nor the newer vbnc.

I have been getting the idea that c# is more important lately but I figured it wouldn't hurt to learn vb.net as well, just to pad out my resume.

Still no luck finding the compiler, though, so I guess I'll just have to read the book without working examples, unless I miraculously find this compiler.

For reference, it's mentioned on this page of the Mono website:
[http://www.mono-project.com/Visual_Basic#The_compiler](http://www.mono-project.com/Visual_Basic#The_compiler)

Apparently, I'll have to compile my own version of mono to get the functionality, which is disheartening since that kinda defeats the purpose of having a package manager.

Le sigh.

---

### Post by EEDSMicky on 2008-02-24
I realize this is a rather old post, but as when I was looking for the answer, this post was high up on the google search list, so I will post the answer in the hopes of helping out others.

Unfortunely, even in Gutsy, the vbnc compiler is not available not even an old version, however I did find a workaround. 

You can download the "RPM" version of the compiler from here:
[http://fr2.rpmfind.net/linux/rpm2html/search.php?query=mono(vbnc)]("http://fr2.rpmfind.net/linux/rpm2html/search.php?query=mono(vbnc)")

Then you can:
sudo alien rpm-filename-here

Install and Enjoy.

My source of enlightenment:
[https://bugs.launchpad.net/ubuntu/+source/mono/+bug/129524]("https://bugs.launchpad.net/ubuntu/+source/mono/+bug/129524")

Other Useful Links I discouvered on the search to get Mono to work are:
[http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/]("http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/")

I hope this actually helps someone, sometimes it is rather frustrating when things I feel should be included by default are left out.

PS: If you find this hard to follow, I am attempting to attach my "RPM" converted to "DEB" file of mono-basic1.2.6 which includeds the VB.net compiler to this thread.

---

### Post by reality1011 on 2008-05-11
That was very helpful... I just clicked on your package and everything worked.

---

### Post by XeroZohar on 2008-05-12
It's been forever since I posted about this, but I remember I found some solution way back when.  I don't use it anymore, though, so I don't remember what it was.

However, much belated thanks to EEDSMicky for the package, which has apparently solved someone else's problem now.

---

### Post by Minguo on 2008-06-03
Hmmm, would appreciate some more explanations, but the file included by EEDSMickey 'seems' to have worked.  I say 'seems' as I cannot get any 'toolbox' functionality from MonoDevelop. . . which may just be my unfamiliarity with the IDE.

---

### Post by arist0tle on 2009-03-31
EEDSMicky...you rock - thanks. I have been trying to find this forever and a day now.

---

### Post by directhex on 2009-03-31
> **arist0tle said:**
> EEDSMicky...you rock - thanks. I have been trying to find this forever and a day now.

Using his Alien'd package will likely hose your install at some point.

Use a real package. If you don't want to run Jaunty, pull the .deb from Debian

---

### Post by Jakiejake on 2010-08-08
> **EEDSMicky said:**
> I realize this is a rather old post, but as when I was looking for the answer, this post was high up on the google search list, so I will post the answer in the hopes of helping out others.

Unfortunely, even in Gutsy, the vbnc compiler is not available not even an old version, however I did find a workaround. 

You can download the "RPM" version of the compiler from here:
[http://fr2.rpmfind.net/linux/rpm2html/search.php?query=mono(vbnc)]("http://fr2.rpmfind.net/linux/rpm2html/search.php?query=mono(vbnc)")

Then you can:
sudo alien rpm-filename-here

Install and Enjoy.

My source of enlightenment:
[https://bugs.launchpad.net/ubuntu/+source/mono/+bug/129524]("https://bugs.launchpad.net/ubuntu/+source/mono/+bug/129524")

Other Useful Links I discouvered on the search to get Mono to work are:
[http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/]("http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/")

I hope this actually helps someone, sometimes it is rather frustrating when things I feel should be included by default are left out.

PS: If you find this hard to follow, I am attempting to attach my "RPM" converted to "DEB" file of mono-basic1.2.6 which includeds the VB.net compiler to this thread.

Sorry To Bring this thread back up but just to let you know the attached package is only 32 Bit

---

