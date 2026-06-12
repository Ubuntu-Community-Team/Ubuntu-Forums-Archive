---
title: "Modern ebook (epub) reader"
date: 2015-05-07
forum: New to Ubuntu
---

### Post by tiamat2009 on 2015-05-07
Is there anything like the amazon kindle desktop reader for ubuntu to read epub ebooks?

PLEASE DON'T MENTION CALIBRE

I'm looking for something modern and fresh, actually a bit like the gnome documents app when looking at pdfs would do...

is there anything like that for linux??? Such apps exist for windows and macs but all linux ebook readers seem to have come from the 90s

---

### Post by Vladlenin5000 on 2015-05-07
> **tiamat2009 said:**
> Such apps exist for windows and macs but all linux ebook readers seem to have come from the 90s

Really? I'm probably the _ultimate_ 80s/90s aesthetics _hater_ and I don't put Calibre in that category... That said, please give us a frame of reference, i.e., tell us one or a few of those Windows apps you like and perhaps someone will suggest something.

Or, better yet, don't bother with it at all because sooner than later everything will be online, you know, in the web and the "app" you'll really need is the web browser.


*** For someone so worried about a *demodé* style, you worry too much about apps (newsflash: Apps is totally "old school").

---

### Post by spjackson on 2015-05-07
I use the  Firefox plugin and I'm happy with it. It doesn't look to me as though it's from the 90s, but opinions differ. [https://addons.mozilla.org/en-US/firefox/addon/epubreader/](https://addons.mozilla.org/en-US/firefox/addon/epubreader/)

---

### Post by Vladlenin5000 on 2015-05-07
> **spjackson said:**
> I use the  Firefox plugin and I'm happy with it. It doesn't look to me as though it's from the 90s, but opinions differ. [https://addons.mozilla.org/en-US/firefox/addon/epubreader/](https://addons.mozilla.org/en-US/firefox/addon/epubreader/)

:lolflag: Exactly what I said...
Look no further than Google, Microsoft and, in a lesser extent, Apple. Whatever they are doing now is the soon-to-be-standard.

---

### Post by Holger_Gehrke on 2015-05-08
A similar question and several answers can be found [here]("http://askubuntu.com/questions/14378/what-software-can-i-use-to-view-epub-documents").

---

### Post by tiamat2009 on 2015-05-08
hi.

Thanks for the replies... what I really want is something like these:

[http://blogs.adobe.com/readermobile/files/2012/12/bookmarks.png](http://blogs.adobe.com/readermobile/files/2012/12/bookmarks.png)
[http://winsupersite.com/site-files/winsupersite.com/files/uploads/2014/06/kindle.jpg](http://winsupersite.com/site-files/winsupersite.com/files/uploads/2014/06/kindle.jpg)
[http://st1.bgr.in/wp-content/uploads/2014/05/amazon-kindle-cloud-reader-india-launch.jpg](http://st1.bgr.in/wp-content/uploads/2014/05/amazon-kindle-cloud-reader-india-launch.jpg)

I also like the document viewer in gnome when you view pdfs, if it would just open epubs with the same interface that it uses for pdfs that would be fine:

[https://www.youtube.com/watch?v=tKyltg6PjzU](https://www.youtube.com/watch?v=tKyltg6PjzU)

Can it be made to open epub books?

---

### Post by Holger_Gehrke on 2015-05-08
> **tiamat2009 said:**
> 
I also like the document viewer in gnome when you view pdfs, if it would just open epubs with the same interface that it uses for pdfs that would be fine:

[https://www.youtube.com/watch?v=tKyltg6PjzU](https://www.youtube.com/watch?v=tKyltg6PjzU)

Can it be made to open epub books?

An attempt at epub support in evince was made round about 2008 but has stalled. If you want one reader for everything than KDE's 'okular'  -- with okular-extra-backends for epub support -- is probably the closest you can get. Be aware though that it will pull in a lot of KDE libraries and tools as dependencies, so it's actually the opposite of a light-weight app.

If your opposition to calibre is based on the fact that it is mainly a library organizer and converter, you might try starting it's reader component directly by calling 'ebook-viewer' from the shell, optionally with the file name of your book as parameter ...

---

### Post by Dave_P43 on 2015-05-20
I specifically wanted to open a book that I'd purchased through Amazon's Kindle format. Kindle's cloud reader gave me an error ("Not supported on this version of Firefox" - Ubuntu 14.0.4, Firefox v38.0), but downloading and opening the book works great....

---

### Post by jones quest on 2015-05-20
Amazon kindle formats (kf8 and azw) are DRM protected and proprietary. Your options of viewing those files are Kindle Cloud Reader, the windows version of Kindle reader (using wine) or converting the file (probably illegal).

I just tested the cloud reader. Works fine on Ubuntu 15.04 (Firefox v38.0). You could try installing the nightly build of Firefox (ppa:ubuntu-mozilla-daily/ppa) to see if it works with that.

---

### Post by monkeybrain20122 on 2015-05-21
I wouldn't even buy drmed ebooks. Maybe it is just my "90's" sensibility, I like to own my books.

P.s There are ways for Calibre to unlock drm Kindle and other formats but I won't say it because it would be against the COC and it is so "1990's" according OP, the 21th century way is to entrust your well being to big corporations that lock you into their vertically integrated services.

---

