---
title: "Qt going LGPL"
date: 2009-01-14
forum: Programming Talk
---

### Post by Jonas thomas on 2009-01-14
I got a little announcement regarding Qt Licensing this morning.
[http://www.qtsoftware.com/about/licensing]("http://www.qtsoftware.com/about/licensing") 
I was staying away from QT because of they're Hinky license terms.
Basically, I wanted to use it work, and not release to the world, you had to get a license which was big $$$   Does going LGPL mean these days are over?

---

### Post by Npl on 2009-01-14
as long you dont statically link the library, yes

---

### Post by Jonas thomas on 2009-01-15
Am I the only who thinks, this is a huge deal?
Isn't this sort like a situation where your driving your Dodge Neon and someone says throws you the keys to a Testarossa and says it's yours?  My understanding is that Nokia paid 150+million for Trolltech.  I'm assuming their dual license model must have been a cash cow for them.  Why give it up?

---

### Post by samjh on 2009-01-15
> **Npl said:**
> as long you dont statically link the library, yes

Only if your software is **proprietary**.  In other words, if you're using the LGPL release of Qt but your software is proprietary, then only dynamic linking is allowed.  Obviously sections 5 and 6 of LGPL v2.1 will need to be adhered to.

BTW, I made a thread about this in the Community Cafe forum:
[http://ubuntuforums.org/showthread.php?t=1039963](http://ubuntuforums.org/showthread.php?t=1039963)

[quote=Jonas thomas]Am I the only who thinks, this is a huge deal?
Isn't this sort like a situation where your driving your Dodge Neon and someone says throws you the keys to a Testarossa and says it's yours? My understanding is that Nokia paid 150+million for Trolltech. I'm assuming their dual license model must have been a cash cow for them. Why give it up?[/quote]As I said in the other thread, this is big news.

As for why Nokia is "giving it up", they're not really.  Nokia is still going to be doing the bulk of development work and technical direction for Qt, under their "Qt Software" business division.  However they're working on a governance model to encourage development by external developers too.

Nokia wants "Qt everywhere", and that means removing barriers to adoption.  What better way than to follow GTK's lead and release Qt under LGPL?  Obviously the people at Nokia have been browsing around mailing lists, blogs, forums, and taken notice of all the complaints about commercial licensing and so on.

Here's Nokia's stated aims:
[quote=Nokia]Our aim is to:

    * To establish Qt as the de facto standard for rich UI and application development, ensuring that there is a vibrant ecosystem of application developers for Nokia devices and other platforms
    * Ensure that Qt is of the highest quality possible with good supporting tools and services such that Nokia is able to get devices to market faster, and with better software. The widespread use of Qt translates into greater richness and stability across and between platforms.
    * By spreading Qt usage as widely as possible and establishing a robust ecosystem, Nokia will gain access to true cross-platform APIs for developing applications and services once, and deploying them across desktops, devices and the web without rewriting the source code.[/quote]

---

### Post by Npl on 2009-01-15
> **samjh said:**
> Only if your software is **proprietary**.  In other words, if you're using the LGPL release of Qt but your software is proprietary, then only dynamic linking is allowed.  This is standard fare for all LGPL libraries that don't contain a static linking exception.To be exact, if your software is not licensed under GPL, which is something different than propietary (But the original question meant closed-source software anyway)
I can write an App, release it with sources licensed under CDDL or some other "more-free-than-GPL" License and not beeing able to use Software licensed under GPL.

GPL is anything but freedom, its a way for several companies developing OS-Software to secure their investment, by denying all possible use that wont allow them to benefit from it. Not more good or evil than proprietary software, but far from what I consider "free".

---

### Post by samjh on 2009-01-15
> **Npl said:**
> To be exact, if your software is not licensed under GPL, which is something different than propietary (But the original question meant closed-source software anyway)
I can write an App, release it with sources licensed under CDDL or some other "more-free-than-GPL" License and not beeing able to use Software licensed under GPL.You replied before I edited my post with more accurate information.  Sections 5 and 6 of the LGPL v2.1 will govern Qt4.5 onward, in addition to whatever additional restrictions Nokia wishes to place on it.

> **Npl said:**
> GPL is anything but freedom, its a way for several companies developing OS-Software to secure their investment, by denying all possible use that wont allow them to benefit from it. Not more good or evil than proprietary software, but far from what I consider "free".Interesting opinion.  The FSF disagrees with you.

The GPL does promote freedom in some ways.  It's also restrictive.  It's a license full of irony.

---

### Post by nvteighen on 2009-01-15
> **samjh said:**
> 
The GPL does promote freedom in some ways.  It's also restrictive.  It's a license full of irony.

GPL is a restrictive license, yes, but because it tries something really difficult: that all rights (to use the correct term, not the emotional "freedom") the first licensee acquires is also enjoyed by the subsequent ones. Therefore, it has to devise mechanisms that should guarrantee that idea works. The restrictions are all meant in that direction; if they really succeed or not and whether they finally turn against the GPL's own purposes, that's something that will need further analysis.

I agree the GPL (and since LGPLv3 too, as this last version is written in a "GPLv3 + additional permissions" fashion) is a difficult license to comply with, compared to e.g. the 3 clause BSD. That clearly hardens a lot of things.

Btw, nothing is worse than GFDL...

---

### Post by Npl on 2009-01-15
I understand the aim of the GPL. Its great if you make your living with the OSS you write and thus depend that noone takes your work and competes with you (without giving you the chance to take the good parts back). Thats what I meant with securing your investment.

The bad part is, that it effectively limits yourself to commit yourself fully to it, as you cant eg. use your own source-library for a single App you decide to license under GPL and then us ethe same library for a binary-only app. Its really an us-vs-them license (with us beeing limited to **GPL-compatible Software**, not OSS), and you might get shot in the back if you try to bail =P

As hobbyist I wouldnt touch the GPL (after reading into it, I already used it once). I want ppl to make use of my source and aslong they credit my work (and dont try to sue me by claiming it as their own, etc) I have no objection on what they do with it. And I want the option to release stuff binary-only until I deem the advantages of opensourcing worth the disadvantages.

---

