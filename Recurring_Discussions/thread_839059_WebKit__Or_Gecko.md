---
title: "WebKit?  Or Gecko?"
date: 2008-06-24
forum: Recurring Discussions
---

### Post by ghindo on 2008-06-24
There are two leading open-source layout engines for web browsers:  WebKit, and Gecko.  Safari (among others) uses WebKit, and Firefox (among others) uses Gecko.  Which do you prefer?  What are the advantages and disadvantages of each?

And let's not even get into Trident :p

---

### Post by -grubby on 2008-06-24
I hear that webkit passes the acid3

---

### Post by joninkrakow on 2008-06-24
Actually, that merely raises a question for me. What webkit-based browsers are there for GTK? Konqueror uses khtml and maybe the latest webkit under KDE, but what uses webkit under Gnome and others? 

For what it's worth, I personally like the webkit, but use Firefox right now because it installed easily enough (unpack the tar file from Firefox, stuff it in my /usr/local folder, and point my jwm desktop shortcut to it.) But I would love to try a Webkit browser under Puppy and LXDE w/Xubuntu.

-Jon

---

### Post by mrgnash on 2008-06-24
> **joninkrakow said:**
> Actually, that merely raises a question for me. What webkit-based browsers are there for GTK? Konqueror uses khtml and maybe the latest webkit under KDE, but what uses webkit under Gnome and others? 

For what it's worth, I personally like the webkit, but use Firefox right now because it installed easily enough (unpack the tar file from Firefox, stuff it in my /usr/local folder, and point my jwm desktop shortcut to it.) But I would love to try a Webkit browser under Puppy and LXDE w/Xubuntu.

-Jon

Midori or Epiphany compiled with the Webkit back-end.

---

### Post by p_quarles on 2008-06-24
> **mrgnash said:**
> Midori or Epiphany compiled with the Webkit back-end.
Kazehakase can also run on WebKit. 

WebKit recently had the advantage of being considerably faster than Gecko, but the new version of Gecko has (to my mind) largely erased that difference. They both do certain things faster than the other. 

Don't forget KHTML: it's the "other" open source web rendering engine, and the version of KDE 4.1 is looking quite good. 

Moved to Recurring Discussions, as this is basically a browser smackdown.

---

### Post by ghindo on 2008-06-24
> **nathangrubb said:**
> I hear that webkit passes the acid3I heard that too, but I also heard it was done with some dirty hack.

---

### Post by mali2297 on 2008-06-24
> **nathangrubb said:**
> I hear that webkit passes the acid3

I did this test on midori; the browser crashed. It uses though a nightly build of webkit.

---

### Post by ghindo on 2008-06-24
> **mali2297 said:**
> I did this test on midori; the browser crashed. It uses though a nightly build of webkit.Well, Midori *is* early alpha software...

---

### Post by smartboyathome on 2008-06-24
> **nathangrubb said:**
> I hear that webkit passes the acid3

Not at the moment, when compiled wit all the flags but SVG filters (that is broken). It only gets a 95/100 on it. :( Firefox 3 gets 71/100, and Opera 9.5 gets 83/100, so you can see it gets a really good score when compared to others.

---

### Post by doorknob60 on 2008-06-26
Webkit, Gecko, whatevertheheckoperauses, KHTML, I like them all. Not sure which I prefer though. Konqueror (3.5) miserably fails Acid 3 though lol. Right now I use Konqueror on my Desktop and FF3 (sometimes Opera) on my old laptop.

See Attatchment for Konqueror's miserable failure, although I'm sure 4.x would give much better results...

---

### Post by p_quarles on 2008-06-26
> **doorknob60 said:**
> Webkit, Gecko, whatevertheheckoperauses, KHTML, I like them all. Not sure which I prefer though. Konqueror (3.5) miserably fails Acid 3 though lol. Right now I use Konqueror on my Desktop and FF3 (sometimes Opera) on my old laptop.

See Attatchment for Konqueror's miserable failure, although I'm sure 4.x would give much better results...
It's actually not that bad. While the particular kind of failure that occurs happens to cover up the results, cutting and pasting will reveal that the hidden number is (I think) a 59. Actually slightly better than any other browser from the same generation.

---

### Post by Frak on 2008-06-26
> **nathangrubb said:**
> I hear that webkit passes the acid3
The nightly builds do.

I meant to get an OS X photo, but I'm just too lazy.

[IMG]http://i116.photobucket.com/albums/o3/frak10/acid3test.jpg[/IMG]

---

### Post by doorknob60 on 2008-06-26
> **p_quarles said:**
> It's actually not that bad. While the particular kind of failure that occurs happens to cover up the results, cutting and pasting will reveal that the hidden number is (I think) a 59. Actually slightly better than any other browser from the same generation.

52 actually, it's just in FF2 and IE7 (I think) at least it looked a little "cleaner" and you could see the number. It does pretty good I guess, considering it's 3.5

---

### Post by smartboyathome on 2008-06-26
> **Frak said:**
> The nightly builds do.

I meant to get an OS X photo, but I'm just too lazy.

[IMG]http://i116.photobucket.com/albums/o3/frak10/acid3test.jpg[/IMG]

I am running nightlies and they don't pass it yet. Is it a Safari thing then? :(

---

### Post by Frak on 2008-06-26
> **smartboyathome said:**
> I am running nightlies and they don't pass it yet. Is it a Safari thing then? :(
Yes it is. It has more to do than just with the engine.

---

### Post by ghindo on 2008-06-28
To be honest, I'm not so sure how much Acid 3 matters at the moment.  How many web developers are using the features being tested by Acid 3?

---

### Post by Jammy4041 on 2008-07-17
I'd pick Gecko. It's stable and fast and it works for me. I must have a look at webkit though, I heard it was supposed to be good. 


BTW,

whatevertheheckoperauses = Presto.

---

### Post by bruce89 on 2008-07-17
I suspect no matter what Mozilla try to do, GNOME will adopt WebKit where Gecko is currently used (Epiphany, Yelp, Devhelp, Evolution, GIMP). GIMP's help browser now uses WebKit, and Epiphany from Subversion doesn't have Gecko support.

---

### Post by ryaxnb on 2008-07-17
WebKit is lighter, more integratable, more modular, cleaner code, and a better base for small-screen devices from the Eee PC to a smartphone. 
Gecko has more extendibility, its own cross-platfom interface UI (which it is hard to use without, but is among the most complete out there,) and can handle more common websites. Also, Gecko is more open in the development process, slightly, although Apple's been improving. 

In standards support, the very latest Gecko beats out the very latest WebKit at deprecated-but-still-popular things like document.all and is still better at HTML 5 and possibly Javascript. WebKit has better CSS support, and more support of some of the most interesting web features. OTOH, Gecko offers more support of offline web apps, a critical new feature.

In speed, Gecko uses dirty hacks and code tweaking to make its slightly messy code run fast, whereas WebKit just keeps getting faster while adding more features. I'd say WebKit has a better future here, particularly on low-resource, small-screen devices.

---

### Post by Frak on 2008-07-18
Webkit beats out Gecko in the nightly builds in JS performance thanks to squirelfish. Same goes for HTML 5. Also, Webkit is standards compliant, for while Gecko hasn't been for years.

---

### Post by mali2297 on 2008-07-19
I compiled Webkit with Freetype instead of Pango. Now Midori passes Acid3. Sweet.

I am not ready to abandon Firefox though. I have used Netscape and its derivatives ever since 1995, when I first encountered the web.

---

### Post by mrgnash on 2008-07-19
Epiphany/Webkit 1.0.1-1:

[IMG]http://i33.tinypic.com/ds86u.png[/IMG]

Very nice performance, and I **would** use this as my primary browser, save for the fact that it doesn't seem to want to let me save images -- either in Epiphany or Midori :(

---

### Post by smartboyathome on 2008-07-19
> **mrgnash said:**
> Epiphany/Webkit 1.0.1-1:

[IMG]http://i33.tinypic.com/ds86u.png[/IMG]

Very nice performance, and I **would** use this as my primary browser, save for the fact that it doesn't seem to want to let me save images -- either in Epiphany or Midori :(

Do cookies work now in Epiphany? If so, I will definately compile it. :D

---

### Post by ghindo on 2008-07-19
> **mrgnash said:**
> Epiphany/Webkit 1.0.1-1:

[IMG]http://i33.tinypic.com/ds86u.png[/IMG]

Very nice performance, and I **would** use this as my primary browser, save for the fact that it doesn't seem to want to let me save images -- either in Epiphany or Midori :(Off-topic, but what theme is that?  It looks great.

---

### Post by mrgnash on 2008-07-19
@smartboyathome: No

@ghindo: Thanks. It's just Clearlooks with my own color selection, Union Limited Emerald, and Gnome Human icon theme, and the default Hardy background.

---

### Post by smartboyathome on 2008-07-19
> **mrgnash said:**
> @smartboyathome: No

:( I was looking forward to the cookie situation FINALLY being taken care of. Oh well, lets just go on compiling! :D

---

