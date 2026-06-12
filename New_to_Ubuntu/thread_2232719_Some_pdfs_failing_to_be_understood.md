---
title: "Some pdfs failing to be understood"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by derek-wood-email on 2014-07-03
Hi

After many years of keeping an eye on Linux systems I made the jump earlier this year.

My technical experience is DOS5.x ~ Windoze 7.. and everything in between.  I've been using Netscape/firefox since '99 and I've hacked PC hardware (tick timers etc) and built ISA cards, PIC stuff, programmed in assembly/C/Occam/Ada etc.   But really I'm an RF R&D engineer.


[B]The Problem:
[/B]
So, my wife has been sent some "Brownie" PDF documents that we can only seem to open in Windoze.  I've tried using the google mydrive to open the docs via google docs/luminPDFviewer and on Xubuntu with xpdf and the "reader" that came with Xubuntu, I even tried Gimp.  But so far nothing has worked for me.  I've downloaded the adobe .bin but can't seem to get it to install despite having followed online help..  it just says it can't run the file (I very strongly suspect I'm not doing something obvious but as with some online help, it looks like it's skipping the "obvious little steps")...

Have PDFs suddenly change in some way.. is it me (probably)

Ok.. machine bits:

3 year old Sony Viao running Xubuntu 12.04 (almost everything else runs perfectly)

thanks in advance for any/all help/suggestions.

Derek

---

### Post by sudodus on 2014-07-03
Welcome to the Ubuntu Forums :-)

My experience is that most pdf files can be viewed with the reader that comes with Xubuntu, ***evince***. But not all of them.

You have probably noticed that there are also other things that are easier to do in Windows, so you should keep it at least in one computer. Many people dual boot, and some people run Windows in a virtual machine.

I have not used Adobe Reader in linux, but it should work. I suggest that you try the linux deb package from

[https://get.adobe.com/se/reader/otherversions/](https://get.adobe.com/se/reader/otherversions/)

but you can also try ***okular***, that can be installed from the repositories

```
sudo apt-get install okular
```

***okular*** belongs to KDE, and brings a lot of KDE packages, which is OK, it only occupies space on the hard disk, except when you use them.
[URL="https://get.adobe.com/se/reader/otherversions/"]

[/URL]

---

### Post by nerdtron on 2014-07-03
Although I have nothing against okular (I like it on KDE), since you are using Xubuntu I suggest you try other pdf viewers from the software center first. There is also a version of Adobe Reader on the software center. It is outdated and a bit slow but it still opens all of my PDFs correctly including some with passwords.

---

### Post by pretty_whistle on 2014-07-03
Hmmmm.... I havent had a problem with evince.  I've been able to view all PDFs.  In any case thanx for the adobe link.  :)  I'll save that .deb file in case something comes up.

---

### Post by tgalati4 on 2014-07-03
Install *acroread* and try opening the files.  I have a directory of pathological PDF's from the forums that folks have posted.  Attach a file that you are having problems with--assuming there are no privacy issues.  Files that tend to have problems--subway maps with lots of overlays, files with special fonts, and really huge files.

---

### Post by jp734 on 2014-07-04
I use Adobe's Acrobat Reader. They only have version 9 but for me it's still the best reader. It's fast and can zoom all the way up to 6400% easily using an old laptop. Evince works but for some reason it stops at 92% when I try to zoom and others are just really slow.

I've installed acroread on lubuntu, puppy and fatdog64, all working with on issue.

---

