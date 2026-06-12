---
title: "installing qt4"
date: 2008-06-26
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-26
i just began trying my hands over qt.
the book i refer requires qt4, but doesnt give directions for its installation.
i installed QDevelop, but its initial configuration options,i dont understand.
is QDevelop ok as a tool...or there is a better option available ?
since i am new to qt..i would like some help installing and configuring qt4 and running my first program...thanks.

---

### Post by geirha on 2008-06-26
Haven't done any development with the qt-library myself, but to develop using a specific library, you need the dev-package for that library, so installing [libqt4-dev](apt:libqt4-dev) is probably all you need.

---

### Post by Dambrosio on 2008-07-01
dexter.deepak,
If you go to the synaptic package manager and search for qt you should find a few files which are required. Qt designer is a very helpful tool for qt, it automatically writes code based off of your application design. Sorry if this is very broad, I am at work and I'm using Fedora so its a little different but when I get back to Ubuntu (way better) I will tell you the exact libraries you should install.

Dan

Feel free to message me about any Qt problems you may run into. I have been working with it for a couple months now so I don't know how much I can help but it is hard to find help on Qt related topics.

---

### Post by snova on 2008-07-01
First, you have to install Qt4. It comes in many little pieces. Here's a list of the packages you will need, at a minimum:

libqt4-core
libqt4-gui (these two are probably already installed)
libqt4-dev (includes the special programs that Qt needs, like moc)

One thing is very important. The moc program (/usr/bin/moc) is a link that points to /usr/bin/moc-qt3 - this is the wrong version. You can either run:

sudo update-alternatives --config moc

and then select moc-qt4, which will make /usr/bin/moc point to /usr/bin/moc-qt4 instead; ***OR***

Use moc-qt4 in place of moc all the time.

To get started, I suggest you install the qt4-doc package and point your browser to:

/usr/share/qt4/doc/html/tutorial.html

And read the tutorial. Qt is a very comprehensive library, and this only scratches the surface, but it works as a general introduction to the library and it's mechanics. The well-written documentation is at

/usr/share/qt4/doc/html/index.html

Or you can just click Home at the top of the page.

As for KDevelop (I assume you misspelled it as QDevelop, which I've never heard of), it is indeed a capable tool.

---

### Post by Dambrosio on 2008-07-01
QDevelop is not the same as KDevelop, but is a pretty simple Qt IDE program to learn. Personally I prefer KDevelop because QDevelop auto brackets code and can get annoying. Make sure that if a previous version of qt is installed on you computer, you set QDevelop's qmake path to use qmake-qt4 instead of qmake. This will prevent a lot of errors that develop from different qt versions.

---

### Post by S.G. on 2008-07-01
I'm trying to install qt4. I've tried both using Synaptic and from the terminal (sudo apt-get), but I don't have any menu shortcut (I expected them to appear under Applications->Programming).
What did I do wrong?

Thanks in advance.

---

### Post by Dambrosio on 2008-07-01
If you didn't install qt4-designer or the qt4-linguist packages there will be no menu shortcut. Does that help?
Dan

---

### Post by S.G. on 2008-07-10
> **Dambrosio said:**
> If you didn't install qt4-designer or the qt4-linguist packages there will be no menu shortcut. Does that help?
Dan
Hello.
I've tried sudo apt-get install qt4-designer qt4-linguist.
I get a message saying I already have the newest version for qt4-designer and another one telling me package qt4-linguist hasn't been found.

Any ideas?

Thanks a lot.

---

### Post by dexter.deepak on 2008-07-11
@ SG , you can try add/remove utility ...it very clearly lists all the required stuff in an orderly way (watch out in the programming section).

---

