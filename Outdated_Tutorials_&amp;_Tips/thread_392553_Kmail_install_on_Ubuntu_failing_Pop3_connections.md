---
title: "Kmail install on Ubuntu failing Pop3 connections"
date: 2007-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Dougga on 2007-03-24
After attempting to install KMail on Ubuntu (because Evolution just wasn't cutting it fo r me), I was getting the following error:

Re: "Could not start process pop3s."


I found this answer on a :KS google :KS search...

|| Albert Cardona
|| Fri, 27 Oct 2006 12:05:22 -0700
||
||
|| I find out this is a different kind of bug. Apparently the kmail package
|| does not depend on the kdebase-kio-plugins package, and thus it can only
|| read imap mails, not pop mails, unless such kio package is installed
|| separately.

After installing this package, Kmail works just fine with POP3.

FYI

---

