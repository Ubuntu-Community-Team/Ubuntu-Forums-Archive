---
title: "GUI's for CLI Apps"
date: 2007-09-18
forum: Programming Talk
---

### Post by JustAboutRealJAR on 2007-09-18
is there an existing project dedicated to building GUI's for existing CLI apps? if not, I think it would be a great help to beginning linux users, and help to grow the community.

That said... (and assuming the absence of such a project) who would be interested in comtributing to such a project?

I was thinking python and pyQt would be a good place to start

---

### Post by Lord Illidan on 2007-09-18
I'm not sure there is any project of any kind regarding this, except people seeking to develop front-ends to CLI commands..

What CLI applications were you thinking of GUIficating <wow..nice word, eh?>

I think I might volunteer for it.

EDIT : pyqt, or pygtk? or both?

---

### Post by JustAboutRealJAR on 2007-09-18
I was thinking of GUIficating some of the more utilitarian ones first: like hardware configuration programs.

The most common thing you have to do when you first install ubuntu is configure hardware.  Thats what turned me off to linux in high school (before I understood computers as well)

what do you think?

PS - I prefer the QT designer to glade... this is the main reason I would want to use Qt, but if someone else did the gtk versions I'd be all for it (though I think the work is quite redundant, and I dont' know what gain there is by having a gtk version)

---

### Post by Lord Illidan on 2007-09-18
> **JustAboutRealJAR said:**
> I was thinking of GUIficating some of the more utilitarian ones first: like hardware configuration programs.

The most common thing you have to do when you first install ubuntu is configure hardware.  Thats what turned me off to linux in high school (before I understood computers as well)

what do you think?

PS - I prefer the QT designer to glade... this is the main reason I would want to use Qt, but if someone else did the gtk versions I'd be all for it (though I think the work is quite redundant, and I dont' know what gain there is by having a gtk version)

Give me an example of a task you'd like to create a GUI for?

As to why create gtk versions? So that if the application was installed on a default installation of Ubuntu, one wouldn't have to install the qt libs...

What I'd love is a GUI for Xorg.

---

### Post by yabbadabbadont on 2007-09-18
> **Lord Illidan said:**
> What I'd love is a GUI for Xorg.

Aren't they including one in Gutsy?  I know that SuSE has had Sax/Sax2 for a long time now.

---

### Post by Lord Illidan on 2007-09-18
> **yabbadabbadont said:**
> Aren't they including one in Gutsy?  I know that SuSE has had Sax/Sax2 for a long time now.

Dunno, I heard that they might, and I really hope that they do.

---

### Post by JustAboutRealJAR on 2007-09-18
> **Lord Illidan said:**
> Dunno, I heard that they might, and I really hope that they do.

won't that be coming with the new xorg release?

as for gtk... I hadn't thought about that, but It's a very good point. So maybe we should start out just developing gtk versions at first.

perhaps just one big app (instead of lots of little ones) that uses lshw to generate a list of devices and then lets you configure them all in one place.

---

### Post by bapoumba on 2007-09-18
> **JustAboutRealJAR said:**
> won't that be coming with the new xorg release?
[BulletProfX]("http://ubuntuforums.org/showpost.php?p=3248403&postcount=105") ? I have not seen it, but not looked very closely.

Edit, here:
> **bryceharrington said:**
> The Bulletproof-X code can be found via (on Gutsy):

  apt-get source xorg
  cd xorg*/debian/local/Failsafe/

or look in /etc/gdm/ for failsafe*.

There is not a separate package for Bulletproof-X - it comes included in the xorg package for Gutsy.

---

### Post by Acglaphotis on 2007-09-18
I think zenity does what you're looking for:

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-1/)

---

### Post by Wim Sturkenboom on 2007-09-19
I have been thinking about a similar thing, but for commandline using *ncurses*. In my opinion this can be quite usefull for setups without X). It also stops the discussions around Qt and GTK ;)

The thought behind it is that it will tell you which files it has created and/or modified (content, premissions) and which applications are (re)started (including the command that was used), so it can be used as a learning tool for those who are interested in learning a bit more about the operating system.

---

### Post by JustAboutRealJAR on 2007-09-19
Zenity isn't quite what I had in mind... I mean creating a full GUI for CLI apps, not just a few graphical dialog boxes.

the ncurses idea would also be a good way to help beginners become familiar with the CLI but it doesn't change the fact that most beginners don't want to deal with the command line.

Here's my thought on GTK vs Qt: I know that pyQt converts *.ui files from Qt Designer to python code. Perhaps there's also a program that makes python code using the GTK library out of the same *.ui files.

I'll do a quick search for such a thing right now

---

### Post by JustAboutRealJAR on 2007-09-19
ok so far I've got no gtk version of pyuic... does anyone know of such a thing?

---

### Post by nanotube on 2007-09-19
hm, i'd say, if you like and are familiar with qt rather than gtk, then just go with qt. qt libs are as easy to install as anything else out of synaptic, and disk space is cheap these days, so it doesn't much matter whether you are using gtk or qt, really.

---

### Post by mssever on 2007-09-20
One other consideration: KDE users can install something that makes GTK apps look like Qt apps. The reverse isn't true. And in my opinion, native looking apps are important.

---

### Post by JustAboutRealJAR on 2007-09-20
to be honest... I don't really see much difference between GTK and Qt apps... it may be that I don't know what to look for, but on Ubuntu Feisty with the human theme, most widgets look the same

---

### Post by mssever on 2007-09-20
> **JustAboutRealJAR said:**
> to be honest... I don't really see much difference between GTK and Qt apps... it may be that I don't know what to look for, but on Ubuntu Feisty with the human theme, most widgets look the same
The difference is really obvious to me. It might be because I don't use the Human theme (I think it's hideous), but remember that both GTK and Qt can be themed, and so can easily diverge.

Then, there's Swing and Tk, both of which look out of place on every system.

---

### Post by nanotube on 2007-09-20
> **mssever said:**
> 
Then, there's Swing and Tk, both of which look out of place on every system.

hehe at least there's no favoritism there. ;)

---

### Post by JustAboutRealJAR on 2007-09-20
msserver, 

After a closer look at GTK vs Qt widgets in different themes, I now am beginning to agree with you on having native looking apps

---

### Post by JustAboutRealJAR on 2007-09-20
I guess now is a good time to start asking what CLI apps people would like to see GUI's for (please don't request xorg it's already in progress and just very near release)

---

### Post by mssever on 2007-09-20
There are many, but the only one that comes to mind right now is an fstab editor (perhaps also with an interface to mount).

I generally think of these things when I'm trying to help a former Windows user accomplish some task. But there may be GUIs already for a lot of the things I think of and I just don't know about them.

I'm perfectly comfortable with the CLI myself, but I applaud your effort. I think that the ideal OS would have both CLI and GUI versions of everything (except for a few areas where one or the other doesn't make sense, such as a CLI GIMP or a GUI Apache).

---

### Post by nanotube on 2007-09-20
> **mssever said:**
> (except for a few areas where one or the other doesn't make sense, such as a CLI GIMP or a GUI Apache).

heh well, i'd say that a gui apache configurator wouldn't be a bad thing at all. :)

---

### Post by mssever on 2007-09-21
> **nanotube said:**
> heh well, i'd say that a gui apache configurator wouldn't be a bad thing at all. :)
I meant Apache itself. Webmin provides a browser-based interface to configuring Apache, if I'm not mistaken. But yes, many common Linux programs could stand GUI configurators--even if the program isn't a candidate for a GUI.

---

### Post by slavik on 2007-09-21
here's one for wget ;)

[http://justaddwater.dk/wp-content/uploads/2006/12/wgetgui-screenshot.png](http://justaddwater.dk/wp-content/uploads/2006/12/wgetgui-screenshot.png)

---

### Post by mssever on 2007-09-21
> **slavik said:**
> here's one for wget
Talk about overcomplexity! There's a wget GUI in the repos--and it isn't as bad. I don't remember what it's called, though.

Maybe a dependency package (.deb) that simply depends on the various already-existing GUIs would be a great thing.

---

### Post by Lord Illidan on 2007-09-21
There is a gui for fstab out there in python...I think it's called python-fstab

Not sure if it has options for mount, haven't used it for some time now.

---

### Post by slavik on 2007-09-21
> **mssever said:**
> Talk about overcomplexity! There's a wget GUI in the repos--and it isn't as bad. I don't remember what it's called, though.

Maybe a dependency package (.deb) that simply depends on the various already-existing GUIs would be a great thing.
thing about wget is that it can be a simple file downloader, or a complex spider. I doubt you could build a single SIMPLE GUI around wget to utilize all of wget. even making a spider (choosing options and how to lay them out) is not exactly simple.

there is gwget, but I wish it had auto wget -c calls to continue downloading a file until it was done. you have to do it manually.

---

