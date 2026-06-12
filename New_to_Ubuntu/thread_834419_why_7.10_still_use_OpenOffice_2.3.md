---
title: "why 7.10 still use OpenOffice 2.3 ?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by DO55 on 2008-06-19
hi 

i have update my OS but i still have OpenOffice 2.3  , where is the new one 2.4 ?

---

### Post by Inxsible on 2008-06-19
I think 8.04 is the one that came with OO 2.4. 7.10 had OO 2.3

I could be wrong though..

I don't use Ubuntu anymore :(

---

### Post by alexandremrj on 2008-06-19
Bacause of the tight integration between the system and openoffice gutsy still has 2.3

You can upgrade to hardy or if you want to install openoffice2.4 follow this guide:
[http://anojrs.blogspot.com/2008/04/installing-openoffice-24-on-ubuntu.html](http://anojrs.blogspot.com/2008/04/installing-openoffice-24-on-ubuntu.html)

---

### Post by stchman on 2008-06-19
> **DO55 said:**
> hi 

i have update my OS but i still have OpenOffice 2.3  , where is the new one 2.4 ?

You can download the Openoffice.org 2.4.1 .deb from OO website and install it that way.  Or just install Hardy.

---

### Post by chrisccoulson on 2008-06-19
For an understanding of why 7.10 is still using Openoffice 2.3 and for future reference, please see the stable-release update policy: [https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")

> Stable release updates will, in general, only be issued in order to fix high-impact bugs. Examples of such bugs include:
[LIST]
[*]Bugs which may, under realistic circumstances, directly cause a security vulnerability. These are done by the security team and are documented at SecurityUpdateProcedures.
[*]Bugs which represent severe regressions from the previous release of Ubuntu. This includes packages which are totally unusable, like being uninstallable or crashing on startup.
[*]Bugs which may, under realistic circumstances, directly cause a loss of user data
[*]Bugs which do not fit under above categories, but (1) have an obviously safe patch and (2) affect an application rather than critical infrastructure packages (like X.org or the kernel).
[*]For Long Term Support releases we regularly want to enable new hardware. Such changes are appropriate provided that we can ensure to not affect upgrades on existing hardware. For example, modaliases of newly introduced drivers must not overlap with previously shipped drivers.
[*]New versions of commercial software in the Canonical partner archive.
[*]FTBFS(Fails To Build From Source) can also be considered. Please note that in main the release process ensures that there are no binaries which are not built from a current source. Usually those bugs should only be SRUed in conjunction with another bug fix.
[/LIST]


---

