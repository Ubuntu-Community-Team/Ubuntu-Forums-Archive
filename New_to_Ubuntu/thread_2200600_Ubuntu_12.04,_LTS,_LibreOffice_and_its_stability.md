---
title: "Ubuntu 12.04, LTS, LibreOffice and its stability"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by Untarnished_Truth on 2014-01-20
Good day.  I would like to use Ubuntu (Kubuntu in particular), 99% of the time for office/work applications (LibreOffice, lots of terminal work, Firefox, Thunderbird).  With this, the latest "new stuff" that comes with the regular releases is welcome but not really a necessity -- I first and foremost require stability.  I like the concept of the LTS releases, given its promise of stability, but I am worried about Kubuntu 12.04 having a buggy version of LibreOffice.  Which version of LibreOffice does Kubuntu 12.04 have?  Is LibreOffice easily upgradable, without risking stability?

---

### Post by TheFu on 2014-01-20
A normal app without kernel drivers really cannot impact overall system stability.

I don't use Kubuntu, so I don't know the answer to your other questions for certain, but LTS is about stability, so running the latest LO is NOT gonna happen by default. 1:3.5.7-0ubuntu5 is the LO-Writer version on my 100% currenty patched 12.04 box.  Make of that, what you will.  Often it is better to say you are running the "normal LibreOffice for 12.04" and let everyone you work with use the same version.  This avoids the Word-95 vs Word 200 vs Word-2012 compatibility issues completely.

Every version of LO has bugs. That will never change. We just need to hope that any bugs do no impact our work.

You can override the version from the main repositories by using a PPA. There are dangers in doing this since the software would come from other sources that are almost impossible to validate. I'm fairly certain that the LO group has a PPA for 12.04 systems with their "stable" release, what ever that is. Google found this: [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Being on the newest version of software doesn't mean you are on the "best" version for any specific task. If we've learned anything, we know that newer is NOT better.

---

