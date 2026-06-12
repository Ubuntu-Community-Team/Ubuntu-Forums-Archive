---
title: "Is qtdemo downloadable via Synaptic"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Jonas thomas on 2008-08-17
I'm interested in learning qt.
I downloaded the following packages via synaptic.
qt-4 designer
qt-4 dev-tools
qt-4 doc

/usr/share/qt4/doc/html/qtdemo.html talks about a application called qtdemo
I searched and it isn't include with the packages I downloaded  I searched through synaptic for "qtdemo" and nothing turned up.

Am I not looking in the right place in synaptic or do I need to figure out some command line gyrations and download it from Trolltech, if I really want it?
Thanks,

---

### Post by Mud.Knee.Havoc on 2008-08-17
I think that [this might offer some insight]("http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg20712.html").  It seems to be there, but you have to know where to look.

---

### Post by Jonas thomas on 2008-08-17
> **Mud.Knee.Havoc said:**
> I think that [this might offer some insight]("http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg20712.html").  It seems to be there, but you have to know where to look.

[http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg20783.html]("http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg20783.html")

So.... I guess it's in the Beta1 for the upcoming 4.4.  Does anyone have a link on instructions on how to load this?

Here's some more info:
[http://fboudra.free.fr/wordpress/?p=16]("http://fboudra.free.fr/wordpress/?p=16")

If I'm heading down a wrong path here, please chime in.
I think I need to access debian backports.  I found some instructions here on how to do that.
[http://www.backports.org/dokuwiki/doku.php?id=instructions]("http://www.backports.org/dokuwiki/doku.php?id=instructions")

?? I don't seem to be getting anywhere... When all else fails I suppose I can email the packager....

---

### Post by Jonas thomas on 2008-08-17
I think I'm getting closer 
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/93384](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/93384)

I wonder if it's inside  "qt4-demos.tar.gz" and "qt4-examples.tar.gz" It seems like it might have it??

This seems to discuss it.
[http://changelogs.ubuntu.com/changelogs/pool/main/q/qt4-x11/qt4-x11_4.3.0-4ubuntu1~feisty1/changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/q/qt4-x11/qt4-x11_4.3.0-4ubuntu1~feisty1/changelog")

I tried this:
```
 481  cd /usr/share/doc/qt4-doc/
  482  ls
  483  tar -xvvzf qt4-examples.tar.gz
  484  sudo tar -xvvzf qt4-examples.tar.gz
  485  ls
  486  sudo tar -xvvzf  qt4-demos.tar.gz

```
I'm not able to find a makefile so I'm not sure what to do here.... Anyone??

---

### Post by Jonas thomas on 2008-08-19
Straight from "the man" this is what needs to be done...
To install, qt4-demos package under your Ubuntu Hardy, you must
add "hardy-backports" repository to your apt sources list.
See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
and [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I finally managed to get this working... This demo is very interesting to me.
I got the nitty gritty details on my blog if anyone is interested.
[Getting qtdemo to run in Hardy Heron Ubuntu Linux 8.04]("http://www.metalshaperman.com/?p=60")

---

### Post by windel on 2008-09-15
Indeed goto:

/usr/share/doc/qt4-doc

copy qt4-demos.tar.gz and qt4-examples.tar.gz to your home dir

tar xzf qt4-demos.tar.gz
cd qt-demos
qmake-qt4
make

---

### Post by Jonas thomas on 2008-09-15
> **windel said:**
> Indeed goto:

/usr/share/doc/qt4-doc

copy qt4-demos.tar.gz and qt4-examples.tar.gz to your home dir

tar xzf qt4-demos.tar.gz
cd qt-demos
qmake-qt4
make

Hmm.. Sort of a non-issue for me now.. (since I loaded it from backports)  I'll have to go over my notes to see why I didn't work for me.
It might be that that I neglected the qmake part or had some permissions issues...  (The demo is darn impressive.  Don't you think?)

---

### Post by F W Adams on 2009-03-04
Well, there still seems to be no qtdemo on package manager yet. I followed the steps in Windel's post #6. They work fine except for a typo, should be "cd demos" without the qt-.

Also it first needs g++ if you haven't loaded it.
```

sudo apt-get install build-essential

```

This compiles all the demos and examples but doesn't seem to have any qtdemo executable unless I'm missing something. Still learning.

Looked at the demos running, e.g. "affine/affine", from demos directory, impressive.

---

### Post by snova on 2009-03-04
Running on Intrepid, it's in the **qt4-demos** package.

---

