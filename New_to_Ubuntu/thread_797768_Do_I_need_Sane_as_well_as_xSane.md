---
title: "Do I need Sane as well as xSane?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-05-17
Sorry for yet another dumb question!

I am trying to follow (blindly) another thread to get my Epson V200 scanner working with Gutsy.

Epson Japan tells me to make sure I have Sane package 1.0.3 or later, before attempting installing their drivers, which I have downloaded & md5-ed.

Looking in Synaptic Package Manager, I see I have xSane installed, but not Sane.
I did not choose either.
I tried to understand what these are (visiting their websites, Googling & ploughing through this forum) but failed...

Could some kind soul please explain (roughly) what Sane & xSane are and whether I need to have either or both installed before I try anything else?

Many thanks in advance!

---

### Post by drs305 on 2008-05-17
I don't have an epson scanner but mine (an old artec) works fine with just xsane and sane-utils installed. I don't have sane installed.

---

### Post by kellemes on 2008-05-17
Good question..
My guess is that it's all about the sane library (libsane) and "xsane" and "sane" only provide frontends to this library, they neither support scanner on there own, it's libsane that does.
Since both (sane and xsane) pull in libsane as a dependency my guess is that you can choose either one.
Personally I love xsane, it provides a lot of goodies for scanning.

---

### Post by 2CV67 on 2008-05-17
Thanks for those 2 quick replies.

I have xsane & libsane installed, but not sane or sane-utils.

Sounds as though I don't need to install sane (right?).

Do I need to install sane-utils?

Can I do any harm or cause any confusion by installing them all?

Anything else?

Thanks again.

---

### Post by drs305 on 2008-05-17
You won't do any harm - synaptic will take care of you - but you don't need sane or sane-utils unless xsane installs them. 

By the way, we have mentioned dependencies. One way you can get that information is to look in synaptic. Highlight the app you have installed, click on Properties, and then Dependencies. It will tell you which libraries or other files are necessary to run the app. (Note: you can get the dependencies without installing an app but can't view the next tab over -- installed files).

---

### Post by noynac on 2008-05-17
> **2CV67 said:**
> Thanks for those 2 quick replies.

I have xsane & libsane installed, but not sane or sane-utils. Sounds as though I don't need to install sane (right?). Do I need to install sane-utils?...

I have libsane, xsane, and xsane-common installed, and my Epson 3490 scans like a champ. Neither sane nor sane-utils are installed. 

The only issue I had with my scanner was copying over the scanner firmware and pointing the following file to the firmware:

/etc/sane.d/snapscan.conf

---

