---
title: "Qt creator - Build app without the whole library?"
date: 2015-03-04
forum: Programming Talk
---

### Post by flaymond on 2015-03-04
Hello guys, I just downloaded Qt creator and I try build an app (from tutorial)..and somehow it's worked fine....I thought Qt Creator is just an IDE only....so what is the actual download in Qt-project website for 542-542 MB? Qt Creator is just 50-70 MB...:-k

*I download and install it from software center.

---

### Post by spjackson on 2015-03-04
I don't really understand your question but I'll attempt an answer. The 540MB download for Linux here [http://www.qt.io/download-open-source/](http://www.qt.io/download-open-source/) is Qt 5.4.1 offline installer and includes "a stand-alone binary package including Qt libraries and Qt Creator". You are correct: the download of just Qt Creator 3.3.1 (from the same page) is much smaller.

---

### Post by flaymond on 2015-03-05
Oh sorry....I'm bad at English....I just confused of how can I build an app with just Qt creator...without downloading the binary package from the official website?

Is Ubuntu come with Qt library installed?

That's my question :)

Thanks

---

### Post by Dimarchi on 2015-03-05
There are some Qt libraries installed, but not Qt Creator or other stuff you need for making Qt apps. They are available in the repositories, though. Quite a bit of stuff, from the looks of it. You don't have to download packages from the Qt site...unless you want the very latest thing (5.4 as opposed to 5.3 in the repos).

---

### Post by flaymond on 2015-03-05
Wait..there is qt library in repos? (Thank god)...I don't need to download from the slow browser anymore...

---

### Post by flaymond on 2015-03-06
Ah..I found a book that call "C++ pattern design with Qt4" and it shows you to check if qt installed. I try to do sort of the commands, and it's available. Probably, Qt is already installed in our system without our information.

---

### Post by Dimarchi on 2015-03-07
I take it you are referring to the following commands:
[B]
which qmake[/B]

and/or
[B]
qmake -v[/B]

For you, it should show that you have at least the minimum needed to create Qt apps, since you have installed Qt Creator using the Ubuntu Software Center. For me, the first command shows that I have qmake, while the latter gives me an error. Do not mistake the fact that we have some Qt related libraries installed for the ability to create Qt apps. In order to do that, we need to install extra software, such as Qt Creator.

---

### Post by flaymond on 2015-03-09
It mean only the some of Qt library installed in Ubuntu to support other software that depends on the library? It mean the pre-installed library is not enough to unleash the full feature (community) of Qt and also not enough to build a more complex app?

---

### Post by spjackson on 2015-03-09
Are you wanting Qt5 or Qt4? For Qt5 for the full development kit from the Ubuntu repositories you need: qtbase5-dev qtbase5-dev-tools and qtcreator. For Qt4 you need: libqt4-dev libqt4-dev-bin qtcreator. (Apologies if I've missed any.)

These development packages are not installed by default - you need to install them from the repos (via apt-get, synaptic, or whatever).

---

### Post by flaymond on 2015-03-10
I'm building with Qt5 (and learning) now, and is that the whole library to make a more better(complex) app instead of basics apps from tutorials? I don't want to download other third-party packages. It's better just to install from Ubuntu repos though :)

Anyway...I try your commands to install Qt5 package...and when I try run 'sudo apt-get install blablabla'....it's says the packages is already a new version....

Is that mean what I thought is true? The Ubuntu comes with Qt5 preinstalled?

(I never download anything from repos or the official website for Qt5, so I think ya..it is?)

---

### Post by Dimarchi on 2015-03-10
Just to make sure you don't misunderstand the point of libraries, I suggest reading about them: [http://en.wikipedia.org/wiki/Library_%28computing%29]("https://en.wikipedia.org/wiki/Library_%28computing%29")

Now, about Qt...

Most (if not all) compiled programming languages such as Qt use libraries. The point is to use as little as possible, and no more. For example, of what use are networking functions in a simple Hello World program? None whatsoever, it increases the resulting program size unnecessarily. Thus Hello World program examples do not link to libraries providing networking functions.

When you installed Qt Creator, you installed some libraries it needs to work...nothing more, nor nothing less - just what it needs to work. Those seem to be Qt 5 libraries - and certainly not all of them. Qt Creator, however, should include most everything you might want, unless you are delving into some exotic stuff that it does not cover.

If you installed Qt Creator using the Ubuntu Software Center, you have already used Ubuntu's repo for it. No ifs, buts, or maybes about it. Ubuntu does not come with the whole Qt 5 installed or preinstalled. Only some parts, in the form of libraries. The rest you must install yourself. See for yourself: if you have not installed Synaptic, do so now. After that, type qt5 into Search and see lots of Qt 5 libraries that are available, and at the same time, see what libraries are already installed (some of them have been installed because you have installed Qt Creator). Even more importantly, what libraries are *not* installed.

---

### Post by flaymond on 2015-03-11
Thanks a lot :D!!

---

