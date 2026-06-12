---
title: "Grammar Checking"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by jwn-2 on 2015-01-24
I am now using Ubuntu for about two years now. Right from the start I could not get LibreOffice Writer to check grammar properly. I posted a question on the forums and somebody said I must install the Language Tools extension first. So I did that. It installed, but was disabled and every time I try to enable it, I got some error about some Java script or something that could not run (I can’t remember the exact wording). So I posted another question on the forums. No reply. I posted the same question once or twice again. Still no reply. So I gave up, installed and old version of MS Word in Wine, and happily kept using that.

About a year ago I quite coincidentally read somewhere that I have to install a Java Runtime Environment for Language Tools to work. A what??? Search for it in the Ubuntu Software Centre, but nothing that says Java Runtime Environment. So I Googled it, and after quite some research I learned that this Java Runtime Environment is called openjdk-7-jre. Search for it in Ubuntu Software Centre, and there it was! Installed it, tried again to enable Language Tools, and . . . nope, still unable to. Okay, obvious Language Tools doesn’t work on my computer, so back I went to MS Word, which still works perfectly well without any effort.

A few days ago I (again quite coincidental) read somewhere that for Ubuntu I must also install libreoffice-java-common for Language Tools to work. Search Ubuntu Software Centre, and there it is. Installed it and what do you know, grammar checking is working in LibreOfice!

Now I love Ubuntu! It is much more stable and reliable than Windows once things work properly. But Holly Moses, to get things working is an effort!

I really think that all these Java Runtime Environments and whatever mores should be installed by default, or at least Ubuntu should come with proper instructions to install it.

PS: And now I am sorry to have to report that after all this effort, it does not work properly. I found several grammatical mistakes that were not picked up by Language Tools, but MS Word did pick them all up. So I suppose it is back to MS Word for me. Again!

---

### Post by bapoumba on 2015-01-24
I'm quite surprised libreoffice-java-common was not installed as libreoffice depends on it. I have it installed here, but did not have to do it.
What ubuntu version are you running  and how did you install libreoffice ?

---

### Post by DuckHook on 2015-01-24
> **bapoumba said:**
> I'm quite surprised libreoffice-java-common was not installed as libreoffice depends on it. I have it installed here, but did not have to do it.
What ubuntu version are you running  and how did you install libreoffice ?Not a dependency and I also had to expressly install it.> **jwn-2 said:**
> ...to get things working is an effort!

I really think that all these Java Runtime Environments and whatever  mores should be installed by default, or at least Ubuntu should come  with proper instructions to install it.It is true that installing more exotic functionality in Ubuntu is obscure, convoluted, and a real pain. But in this case, the lack of JRE is probably by design, because the addition of any scripting language compromises security. If one were running Ubuntu as a server, for example, one would not want JRE installed.

I agree that the process could be better described and documented, but the fault is not, I think, with Ubuntu, but rather with LibreOffice. It should be better documented on their extension page.

At any rate, it's fine to use whatever works for you. If you've got to stick with MS Word because robust grammar checking is a must-have, then that is the best app for your purposes. Is your extension *LanguageTool*? I'm hoping that it steadily improves over time, but even as-is, I find that it meets my needs.

---

### Post by bapoumba on 2015-01-25
```
apt-cache show libreoffice
Package: libreoffice
Priority: optional
Section: universe/editors
Installed-Size: 165
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Architecture: i386
Version: 1:4.3.3-0ubuntu1
Depends: fonts-sil-gentium-basic, libreoffice-base, libreoffice-calc, libreoffice-core (= 1:4.3.3-0ubuntu1), libreoffice-draw, libreoffice-impress, libreoffice-math, libreoffice-report-builder-bin, libreoffice-writer, libreoffice-avmedia-backend-gstreamer, fonts-dejavu, **libreoffice-java-common (>= 1:4.3.3~)**, python3-uno (>= 4.0~)

```
How did you install libreoffice ?

---

### Post by jwn-2 on 2015-01-25
Bapoumba, I am using Ubuntu 14.04 LTS, and Libre Office was installed by default when I installed Ubuntu.

---

### Post by Rob Sayer on 2015-01-25
> **jwn-2 said:**
> ... Now I love Ubuntu! It is much more stable and reliable than Windows once things work properly. But Holly Moses, to get things working is an effort! ...

Sounds like a convert.

That's always been somewhat true even before linux in Unix days.  

For example, if you wanted to set up a Microsoft OS based network it'd take a day or 2 to install.  And then you'd spend the next 2 or 3 years trying to get it to work properly.

Setting up a Unix network took much longer, but then it *worked*.

However, most people are comparing their their linux install to their pre installed Windows.  If you install an aftermarket Windows you'll have some driver issues generally.  So it's not a 100% fair comparison.

---

### Post by bapoumba on 2015-01-25
> **jwn-2 said:**
> Bapoumba, I am using Ubuntu 14.04 LTS, and Libre Office was installed by default when I installed Ubuntu.

Same here, except I'm on lubuntu 14.10, that should not make a difference for LO.
[http://packages.ubuntu.com/trusty/libreoffice](http://packages.ubuntu.com/trusty/libreoffice) < shows the deps, including libreoffice-java-common so I'm not sure how you and DuckHook did not get it.
What does return the **apt-cache show libreoffice** command on your system ? Please also include **apt-cache policy libreoffice**.

---

### Post by DuckHook on 2015-01-25
> **bapoumba said:**
> ...shows the deps, including libreoffice-java-common so I'm not sure how you and DuckHook did not get it...Default install here too.```
DuckHook@Ubuntu14.04:~$ apt-cache show libreoffice | grep libreoffice-java-common
Depends: fonts-sil-gentium-basic, libreoffice-base, libreoffice-calc, libreoffice-core (= 1:4.2.7-0ubuntu2), libreoffice-draw, libreoffice-impress, libreoffice-math, libreoffice-report-builder-bin, libreoffice-writer, libreoffice-avmedia-backend-gstreamer, fonts-dejavu, libreoffice-java-common (>= 1:4.2.7~), python3-uno (>= 4.0~)
Depends: fonts-sil-gentium-basic, libreoffice-base, libreoffice-calc, libreoffice-core (= 1:4.2.7-0ubuntu1), libreoffice-draw, libreoffice-impress, libreoffice-math, libreoffice-report-builder-bin, libreoffice-writer, libreoffice-avmedia-backend-gstreamer, fonts-dejavu, libreoffice-java-common (>= 1:4.2.7~), python3-uno (>= 4.0~)
Depends: fonts-sil-gentium-basic, libreoffice-base, libreoffice-calc, libreoffice-core (= 1:4.2.3~rc3-0ubuntu2), libreoffice-draw, libreoffice-impress, libreoffice-math, libreoffice-report-builder-bin, libreoffice-writer, libreoffice-avmedia-backend-gstreamer, fonts-dejavu, libreoffice-java-common (>= 1:4.2.3~rc3~), python3-uno (>= 4.0~)
``````
DuckHook@Ubuntu14.04:~$ apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:4.2.7-0ubuntu2
  Version table:
     1:4.2.7-0ubuntu2 0
        500 http://mirrors.accretive-networks.net/ubuntu/ trusty-updates/universe amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://mirrors.accretive-networks.net/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://mirrors.accretive-networks.net/ubuntu/ trusty/universe amd64 Packages
```...*apt-cache shows* does indeed indicate *libreoffice-java-common* as a dependency, yet my default install was missing this pkg and nonetheless functioned without issues. As a further test, this pkg is not installed in my 12.04 VM either, despite the fact that libreoffice is also part of that default install and lists it as a dependency as well. On a broader note, I don't understand why it would be a dependency.  Seems to be only needed on outlying situations like this one where extensions make use of it.

---

### Post by bapoumba on 2015-01-26
Well, libreoffice is not installed according to your **apt-cache policy libreoffice** result.

---

### Post by mc4man on 2015-01-26
libreoffice is a metapackage that is not part of the default install (at least for ubuntu

---

### Post by DuckHook on 2015-01-26
This is actually making more sense now. The metapackage is not installed, but the individual components are. It should be noted then that the *default* install (or at least, *my* numerous default installs) do not include the metapackage.

---

### Post by mc4man on 2015-01-26
Well *some* "individual components are".
So for example on this 14.04 week old install - 
> $ sudo apt-get -s install libreoffice
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ca-certificates-java default-jre default-jre-headless fonts-dejavu
  fonts-dejavu-extra fonts-sil-gentium fonts-sil-gentium-basic java-common
  libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common
  libgconf2-4 libgnome2-0 libgnome2-bin libgnome2-common libgnomevfs2-0
  libgnomevfs2-common libhsqldb1.8.0-java libidl-common libidl0 liborbit-2-0
  liborbit2 libreoffice-base libreoffice-base-drivers libreoffice-java-common
  libreoffice-report-builder-bin libreoffice-sdbc-firebird
  libreoffice-sdbc-hsqldb libservlet3.0-java openjdk-7-jre
  openjdk-7-jre-headless tzdata-java


---

### Post by bapoumba on 2015-01-27
OK thanks. At least that makes sense to me now :)

Back to the original subject, would the OP consider a bug report so that libreoffice-java-common get installed by default in Ubuntu ? I have not looked around for pre-existing bug reports.

---

### Post by Holger_Gehrke on 2015-01-27
This is probably not a bug but a design decision made some time ago to keep the installer iso small enough to go on a cd. Since the current iso files are bigger now, it's time to revisit that decision. 

On the other hand LO works just fine without libreoffice-java-common, that package is only needed for add-ons and extensions written in java and pulls in a complete JRE. Thank to the way extensions work in LO they can be written in any language for which there are bindings to the UNO-library, which is at the core of LO.

---

