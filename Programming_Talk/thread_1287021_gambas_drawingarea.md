---
title: "gambas drawingarea"
date: 2009-10-09
forum: Programming Talk
---

### Post by col48 on 2009-10-09
Does anyone know if there is a limit to the width of a gambas drawingarea?

I am attempting to draw in one over 220000 wide and there are a couple of bizarre effects (possible wrap around, for one? black area to its right for another - this should be another colour).  Nothing overflows into other places on the screen and program flow is not impaired.  These might be down to code bugs but if the knowledge is out there it could short-circuit some very hard graft.  All coordinates are specified as Integer.

There is plenty of memory around and the 'drawing' process itself is not especially slow given the amount I am trying to do at the same time.

Version is 2.0.0 (I think - that's what synaptic says) in Hardy.

---

### Post by kalaharix on 2009-10-12
col48

I don't know the answer but I suspect it lies within GTK or QT (whichever your application is using).

You will not get a lot of support for such an old version of Gambas (2.0). I would try compiling the latest version (2.16.0). Instructions on [http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html) (sections download and getting started).

See if that makes a difference.

rgds

---

### Post by col48 on 2009-10-12
Thanks, kalaharix.  I'll have a look at that.  I have not hitherto gone down the route of compiling from source, partly as I have no intention of doing any C/C++ programming myself.

Would it be true to say that anything which works in Gambas a.b.c can normally be expected to work in Gambas d.e.f as long as def > abc?

---

### Post by kalaharix on 2009-10-13
Not if it is a Microsoft product! LOL.

There is a natural (and active) process of improvement in Gambas. If there is a problem, it may have been fixed. If not then you can ask the question on the Gambas forum which is very knowledgeable (sometimes awesomely so). If you go to the Gambas forum now, they will just tell you to upgrade.

BTW, a program written in Gambas 2 will not necessarily run on Gambas 3 though the community is mulling over a conversion program. Anyway, that's another day.

The forum has also recently pointed to a more lucid description of the compilation procedure at:
[http://www.ziddu.com/download/5849757/Install-Gambas-2.15-in-ubuntu.pdf.html](http://www.ziddu.com/download/5849757/Install-Gambas-2.15-in-ubuntu.pdf.html)
The site is advert heavy so switch off popups.

rgds

---

### Post by bruno9779 on 2009-10-13
> **col48 said:**
> Thanks, kalaharix.  I'll have a look at that.  I have not hitherto gone down the route of compiling from source, partly as I have no intention of doing any C/C++ programming myself.

Would it be true to say that anything which works in Gambas a.b.c can normally be expected to work in Gambas d.e.f as long as def > abc?

You don't have to be into programming to compile your programs. I compile to have the newest version or just some different version than what is in the repos.

You get the source and follow instructions. No need for very specific knowledge

---

### Post by col48 on 2009-10-14
Thanks, guys.

The drawingarea size issue is one I will be tackling in a few weeks - it was just a pilot which showed up the symptoms, so there are other higher priority things to look at first.  I don't mind whether I have the latest versions as long as what I have does what I want.  I've done a bit of C a few years back so have some idea what is involved.

Mind you, if I was inventing the wheel, it would probably be made of granite so it would last longer!

---

