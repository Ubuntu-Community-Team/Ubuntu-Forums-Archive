---
title: "Screenshot in Ubuntu Software Center for my PPA?"
date: 2010-11-30
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-11-30
How to depict a screenshot in "Ubuntu Software Center" for applications provided by a (third-party) PPA on Launchpad?

Can I add an X-Ubuntu-... flag to my .desktop file, or is it some special makeup in the debian/control file?

---

### Post by duanedesign on 2010-12-02
There are a lot of applications that are lacking screenshots in the Software Center. The good news is there is a way to help get these screenshots added to the Software Center.

**How to add screenshots to the Software Center**

Browse the Software Center or the [online repository of screenshots]("http://screenshots.ubuntu.com/packages/without_screenshots?search=&debtag=").

Where you note a screenshot is missing and decide if it’s something you could fix, then proceed to take a screenshot per the guidelines below.

    [LIST=1]
[*] Screenshots are published under the terms of the packaged software itself.
[*] Your screenshots must be in PNG format.
[*] Due to legal reasons screenshots for non-free packages aren’t accecpted.
[*] Images larger than 800×600 pixels will automatically be reduced to that size (retaining the aspect ratio of course). So if you like to control the exact result of what you upload then make sure your image size is no larger than that.
[*] Your screenshot should contain a typical scene when working with it. When snapshotting a browser load the debian.org home page. A screenshot of a graphics program should have a drawing loaded. Of a game please make a screenshot while you are playing and not of the start screen.
[*] You need not artificially switch off your window decorations.
[*] Please set your language to english so that everybody understands it. If you don’t use english by default please start your application from a shell using after setting “export LANG=C”.
[*] Please only take a screenshot of the respective application and not of your whole desktop (unless the screenshot is meant for a window manager).
[*] Please use non-interlaced PNG images.
[/LIST]

**Submit Screenshots**
Once taken [submit your screenshots]("http://screenshots.ubuntu.com/upload").

---

### Post by ianare on 2010-12-15
That's helpful but doesn't fully anwser the question : it only works for official packages.

Is there a way of embedding a screenshot within the debian control file ?

---

### Post by h6w on 2011-01-24
*bump*

I'd like to add a screenshot to my suite of GPL-but-not-Debian packages, too.

Also, how to specify the license, too?

---

### Post by r-senior on 2011-04-01
I'm bumping this because I have exactly the same questions. How should a package be configured to add:

1. Screenshot
2. Licence information

Judging by the other threads on the same topic, it's a closely guarded secret. ;)

---

### Post by jaromil on 2011-05-25
No worries, no secret here, the question eventually becomes:

how do I change/add an url to the central repository database of screenshots?

luckily enough the software-center is open source, so we can look in there...

however let me argue this is not really a smart solution for distributing screenshots, something like a -screenshots package with documented format could download and store those pictures locally, while third-party packagers can still provide their own collection. Ultimately this boils down in having a directory with screenshots, for which an ideal place i guess can be
/usr/share/app-install/screenshots

IMHO :^)
ciao

---

### Post by jaromil on 2011-05-25
> **r-senior said:**
> Judging by the other threads on the same topic, it's a closely guarded secret. ;)

BTW could you make a list of other threads related to this topic, in case you have it at hand? thanks!

---

### Post by motters on 2011-11-13
I'd also like to add a bump to this.  I have developed a few pieces of software which is not part of the official Debian repository for which I'd like to include a screenshot.  So far I've not been able to find any information on how to do this.

---

