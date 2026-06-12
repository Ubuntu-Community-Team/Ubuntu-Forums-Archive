---
title: "LightDM"
date: 2011-05-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Coplen on 2011-05-12
Ok, I was reading on /. that LightDM will become the new display manager. Ok.

One thing, and I find this funny, the up arrow on the keyboard takes a snapshot of the screen every time you hit it. I had a terminal open and I was going to use the arrows to back up and find sudo wajig update, but instead I kept getting screen shots. LOL I don't know if that's what's supposed to happen or not. It doesn't matter - if I hit the up arrow it wants to take a screen shot. Is there anyway to revert back to the old behaviour for the up arrow under LightDm/gnome classic?

---

### Post by VMC on 2011-05-12
Very interesting. And for those that want a link, here you go, thanks to [_**upd8**_]("http://www.webupd8.org/2011/05/lightdm-to-be-default-display-manager.html").

---

### Post by dext on 2011-05-12
[http://lists.fedoraproject.org/pipermail/devel/2011-May/151382.html](http://lists.fedoraproject.org/pipermail/devel/2011-May/151382.html)

read those comments about what LightDM lacks in compared to GDM

---

### Post by screaminj3sus on 2011-05-12
What exactly does it lack compared to gdm? I'm sure any major missing features will be added, and I am sure that not every feature gdm has over LightDM is necessary. I am all for this if it can further increase boot time.

Also it sounds FAR easier to theme than gdm which is a definite plus.

---

### Post by dext on 2011-05-12
> **screaminj3sus said:**
> What exactly does it lack compared to gdm? I'm sure any major missing features will be added, and I am sure that not every feature gdm has over LightDM is necessary. I am all for this if it can further increase boot time.

Also it sounds FAR easier to theme than gdm which is a definite plus.

i take it you didnt read the mailing list about this?  at the end of the day GDM works fine. you may not be able to theme GDM but who cares aslong as the thing works and works well
[http://lists.fedoraproject.org/pipermail/devel/2011-May/151393.html](http://lists.fedoraproject.org/pipermail/devel/2011-May/151393.html) - *read the links posted in this *

---

### Post by Coplen on 2011-05-12
Oh, and I forgot to mention the desktop crashed on me while I was wasting my life on Facebook. I was typing a message and it all went black and took me right out of X.

---

### Post by CreativeReach on 2011-05-12
LightDM mockups! 

[http://www.techdrivein.com/2011/04/gnome-login-screen-mockups-videos.html](http://www.techdrivein.com/2011/04/gnome-login-screen-mockups-videos.html)

---

### Post by Harry33 on 2011-05-13
LightDm will replace GDM (and possibly KDM too) very soon to enable a good testing period.

LightDM is said to offer the same fundamental features as the KDM/GDM managers, but it's code-base being dramatically smaller, easier to maintain and simpler to work on.
It's also said to be more flexible than GDM.

More info here:
[http://www.phoronix.com/scan.php?page=news_item&px=OTQzOQ](http://www.phoronix.com/scan.php?page=news_item&px=OTQzOQ)

---

### Post by gnomeuser on 2011-05-13
The primary thing keeping Chromium from becoming the default browser is the lack of accessibility, and yet.. LightDM is made the default without any such story to tell and a lack of really important functionality (e.g. the lack of session starting is likely to turn out problematic). 

This I suspect will turn out to be a bad decision on an epic scale.

All in all the technical decisions for Oneiric has turned out extremely disappointing.

---

### Post by Harry33 on 2011-05-13
> **gnomeuser said:**
> The primary thing keeping Chromium from becoming the default browser is the lack of accessibility, and yet.. LightDM is made the default without any such story to tell and a lack of really important functionality (e.g. the lack of session starting is likely to turn out problematic). 

This I suspect will turn out to be a bad decision on an epic scale.

All in all the technical decisions for Oneiric has turned out extremely disappointing.

Gnomeuser,

You obviously have deeper info on this issue.
Could you share this info here a bit more.

1. "the lack of session starting ...". What do you mean by this?

2. What technical decisions do you mean?

---

### Post by gnomeuser on 2011-05-13
> **Harry33 said:**
> Gnomeuser,

You obviously have deeper info on this issue.
Could you share this info here a bit more.

1. "the lack of session starting ...". What do you mean by this?

2. What technical decisions do you mean?

Generally this posting by Matthew Garrett explains the issues well (similarly mjg59's postings on fedora-devel linked above).

[http://www.advogato.org/person/mjg59/diary.html?start=296](http://www.advogato.org/person/mjg59/diary.html?start=296)

1. GDM starts your gnome session, so when gdm is started things like power management will work just as in your gnome session. E.g. closing the lid will suspend. 

Without doing this, you are either left with inconsistent behavior or you will have to replicate the same experience (thus naturally losing the simple and lightweight in the process).

2. I am disappointed to see Ubuntu not adopt systemd now as well as even considering using Thunderbird (I had a talk with a Mozilla developer at FOSDEM and he seemed downright horrified at the idea, for good reason). The LightDM thing also irks me.

It just seems to me that Ubuntu is so desperate to define it's own platform that it has become the primary motivation rather than defining a good platform and seeking standardization.

---

### Post by lucazade on 2011-05-13
I suggest this interesting reading about LightDM:

LightDM, or: an examination of a misunderstanding of the problem
[http://mjg59.livejournal.com/136274.html](http://mjg59.livejournal.com/136274.html)

Personally i'd like to try it to see if fits my needs and if it is well developed.

Ooops..
gnomeuser we posted the same stuff at the same moment! :)

---

### Post by Harry33 on 2011-05-13
> **gnomeuser said:**
> Generally this posting by Matthew Garrett explains the issues well (similarly mjg59's postings on fedora-devel linked above).

[http://www.advogato.org/person/mjg59/diary.html?start=296](http://www.advogato.org/person/mjg59/diary.html?start=296)

1. GDM starts your gnome session, so when gdm is started things like power management will work just as in your gnome session. E.g. closing the lid will suspend. 

Without doing this, you are either left with inconsistent behavior or you will have to replicate the same experience (thus naturally losing the simple and lightweight in the process).

2. I am disappointed to see Ubuntu not adopt systemd now as well as even considering using Thunderbird (I had a talk with a Mozilla developer at FOSDEM and he seemed downright horrified at the idea, for good reason). The LightDM thing also irks me.

It just seems to me that Ubuntu is so desperate to define it's own platform that it has become the primary motivation rather than defining a good platform and seeking standardization.

Right, at least this decision needs some more re-evaluation.

---

### Post by Coplen on 2011-05-13
As a note: my up arrow somehow reverted to normal after a couple reboots (I use Windwoes for graphics).

---

### Post by bela42 on 2011-05-13
> **gnomeuser said:**
> 
1. GDM starts your gnome session, so when gdm is started things like power management will work just as in your gnome session. E.g. closing the lid will suspend. 


You shouldn't need to start gnome-session for that, this is one ugly thing.

> **gnomeuser said:**
> 
2. I am disappointed to see Ubuntu not adopt systemd now


They have upstart. If others refuse to adopt that stuff, _because_ its from Canonical - fair enough. But bashing Ubuntu for not just jumping on that bandwagon (for good reason) is just plain stupid.

> **gnomeuser said:**
> 
 as well as even considering using Thunderbird (I had a talk with a Mozilla developer at FOSDEM and he seemed downright horrified at the idea, for good reason). 


Right, TB would make things even worse compared to Evo. But TB fan boys just cannot get over their pet not being the default...

> **gnomeuser said:**
> 
It just seems to me that Ubuntu is so desperate to define it's own platform that it has become the primary motivation rather than defining a good platform and seeking standardization.

I don't think so. Given the direction KDE took after 4.0 and Gnome now with 3.0, Unity does not look that bad to mee. And Canonical will rely on the stuff introduced wth U1, Software Center, etc. to pay the bills in the future. Like it or not.

Whenever RH comes up with something they want to be the new "standard", they expect everybody to follow, while they refuse everything from Canonical on principle. Where is that seeking standardization?

---

### Post by chrisccoulson on 2011-05-14
> **gnomeuser said:**
> I am disappointed to see Ubuntu not adopt systemd now as well as even considering using Thunderbird (I had a talk with a Mozilla developer at FOSDEM and he seemed downright horrified at the idea, for good reason). The LightDM thing also irks me.

What good reason is that? We've had Thunderbird developers from Mozilla at the last 2 UDS's now (including the one we just had), and we are working closely with them to get Thunderbird on to the default install. They certainly don't seem to be horrified at the idea.

---

### Post by Starks on 2011-05-14
Using Evolution for an IMAP account is horrifying.

If Chris and the rest of the team can get Thunderbird, Lightning, Exchange support(?), and tight integration all in line, 11.10 will have the ultimate mailbox experience and all the naysayers will be eating their words.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-email-client/](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-email-client/)

---

### Post by dext on 2011-05-14
as im sure i posted, Thunderbird lacks stuff Evolution has. so IMO it would be another bad move to make TB the default atm

---

