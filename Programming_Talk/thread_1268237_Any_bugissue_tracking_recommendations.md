---
title: "Any bug/issue tracking recommendations?"
date: 2009-09-16
forum: Programming Talk
---

### Post by guiclaw on 2009-09-16
Hey,

Pretty much as the title says really. I've been looking into all of the different systems out there and had a play with a few of the demo ones.

I've tried RT (3.8.4) and got that fully installed, however it seems a bit too complicated for customers to actually use efficiently. I've had a look at Redmine, and Trac (and tried installing Trac) however they seem to be horrendously difficult to install!

I really need something that is simple enough for customers to use easily for reporting issues and keeping track on previous issues, but also something that will work with MySQL(or SQLite) and it must integrate with Apache reasonably well.

I'd appreciate your opinions on this!

Cheers

---

### Post by DaithiF on 2009-09-16
Hi,
I tend to use Trac.  Set up is actually quite straightforward once you get started -- I think I was up & running the first time in < 30mins, including some customisations.
I like the fact of the integrated Wiki, useful for posting instructions, common support issue resolutions, etc, so that the end-user gets a one-stop shop experience.

---

### Post by guiclaw on 2009-09-16
I quite like the look of Trac and would love to get it up and running! I would really have to run it as a CGI right now (we can't afford any apache downtime - and for some reason our current install doesn't like to load in new modules with a graceful - it has to be stopped and started again).

I've tried following the guides on their website, but when it says that it's 'installed' I can't for the life of me find out where its put trac.cgi, however I can get something running with tracd.

---

