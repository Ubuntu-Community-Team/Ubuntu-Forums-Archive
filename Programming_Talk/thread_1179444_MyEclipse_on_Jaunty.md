---
title: "MyEclipse on Jaunty"
date: 2009-06-05
forum: Programming Talk
---

### Post by KeighleHawk on 2009-06-05
Anyone successfully using the latest MyEclipse on 32 bit Jaunty?  I had the base download (manual install) running with one exception, the Dashboard.  According to MyEclipse support, this feature does not work, due to a "binary incompatibility" between the version of XUL runner they expect and the one bundled with Ubuntu.  I'm still trying to get details on this, so while I was at it, I added their update site and upgraded everything.  Bad idea that turned out to be as now it (Eclipse) is totally hosed.

Generally speaking, I find it hard to believe this is not resolvable but I am still trying to narrow in on the problem.  At the moment, I suspect the only answer I will get from MyEclipse is to use the "All-in-One" rpm on RedHat, not an answer I am keen with.  I downloaded it anyway, but suspect converting it to a .deb and installing it will be borked up in one way or another and if I am lucky, hose my existing Java install as well.

Even if it works, I am somewhat offended by the very idea of the All-in-One installer as it installs YAJ (Yet Another JDK).  It seems to me I should be able to install a compatible JDK in the usual Ubuntu location and install any dependent libraries and modify environment variables and scripts as needed to make this work.

Anyone have any hints?  I was planning a bug report on Launchpad at the very least since "incompatible binary versions" is the official MyEclipse stance, but was hoping to dredge up a little useful info to put in the report.

Thanks,
Robert Kuropkat

P.S.  What the hell ever happened to "write once, run anywhere...?"

---

### Post by KeighleHawk on 2009-06-05
As an update to my own post, I installed the All-in-One installer which was a GUI installer rather than the rpm I expected.  The results were a bit surprising.

On initial install, the MyEclipse Start Page (web page) did not work, but the Dashboard did (mostly, it had some button drawing corruption).  When I updated everything suggested in the Dashboard, it restarted and both the Dashboard and MyEclipse Start page seem to work.

On quick inspection, the All-in-One installer puts it's own copy of the JDK 1.5 in it's directory structure.  I still don't know what the XUL runner incompatibility is about or if I can/should remove the local JDK.

Anyway, back to setting up my development environment.  I'm still interested in any other experiences with MyEclipse and Juanty, including Juanty 64 bit....

---

