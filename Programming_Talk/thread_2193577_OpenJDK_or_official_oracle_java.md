---
title: "OpenJDK or official oracle java?"
date: 2013-12-13
forum: Programming Talk
---

### Post by pascalfares on 2013-12-13
Hello,

What do you install openjdk or official oracle java? for developping with java on ubuntu?

---

### Post by thelionroars1337 on 2013-12-14
Feel free to use either. I prefer the openjdk, it lags slightly in development behind the official, but it's in the main repository and gets updated with the rest of your system. Oracle's packaging (at least on Windows) tends to be bundled with nuisanceware that you have to opt out of (a search bar and an update notifier from memory).

---

### Post by r-senior on 2013-12-14
OpenJDK has been a bit flaky in the past but it's much better these days. I've used it successfully on some quite complex projects; things like EJB and Spring/Hibernate.

I'd agree with the poster above that OpenJDK is easier to install; but there are no nuisanceware problems with Oracle JDK on Ubuntu because there is no installer like there is for Windows and Mac. To install the Oracle JDK you unpack the archive and set it up manually, or there's a PPA available.

I see OpenJDK as a "good thing" and keep going back to it until it breaks. I've not had it break for a while now.

---

### Post by mlan on 2014-01-02
I've installed OpenJDK but it seems it's sill at update 25. Oracle's java is at update 45. Does someone know why Ubuntu is lagging behind on pushing the latest version to it's users? This is causing issues with the applet being blocked on some sites.

---

### Post by 1clue on 2014-01-02
If you're just messing around then OpenJDK is fine, but if you want to develop or use software commercially, then Oracle is the way to go.  The PPA is great.

The lag:  This is a discussion all by itself, it's important if you want to really understand how a distro works.  You can (and I do) install both ways (ppa vs manual) depending on what I want the java for.

---

### Post by mlan on 2014-01-02
Just messing about. I'll stick with OpenJDK. Thanks.

---

