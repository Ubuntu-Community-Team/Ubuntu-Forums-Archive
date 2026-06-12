---
title: "Question:: Are Redhat and SUSE proprietary?"
date: 2007-09-30
forum: Other OS Talk
---

### Post by hellmet on 2007-09-30
I've a linux presentation in 3 days. I shall be trying to explain people about Proprietary and Free software. I don't want to give people the wrong info.
I just wanted to know if RedHat's Linux and Novell's SUSE can actually be classified as friendly, open-source proprietary software? Or should they be called FREE?

Thanks for the help!!

---

### Post by yabbadabbadont on 2007-09-30
They are not proprietary.  They may include proprietary packages though.  Even though they sell the latest and greatest versions of their distributions, you are perfectly free to make copies and give them away.

---

### Post by OmegaBLK on 2007-09-30
> **hellmet said:**
> I've a linux presentation in 3 days. I shall be trying to explain people about Proprietary and Free software. I don't want to give people the wrong info.
I just wanted to know if RedHat's Linux and Novell's SUSE can actually be classified as friendly, open-source proprietary software? Or should they be called FREE?

Thanks for the help!!

Red Hat and Novell are Open-Source friendly companies.  They both have funded and contributed to many resources to  [FOSS](http://en.wikipedia.org/wiki/FOSS) & the Linux kernel.  The enterprise distribution that Red Hat releases does contain proprietary code and has trademarks that cannot be used by others wishing to rebuild their distro from sources.  Of course Novell is mainly a proprietary company given their history, but I am not too familiar with Novell's SUSE Enterprise offerings so I have no idea if it contains any proprietary code at the moment (Yast was previously closed before Novell released it under the GPL).  As you may already have known, Fedora and openSUSE are FOSS community supported distros that do not contain the proprietary elements that are or may be in the enterprise versions of Red Hat's and Novell's distributions.

---

### Post by SunnyRabbiera on 2007-09-30
Yes however novell's deal with Microsoft is pretty worrysome as they accept Microsofts IP claim bull, Redhat however doesnt.

---

### Post by saulgoode on 2007-09-30
I think it would be best to view RedHat's offerings from a dual-license perspective. RedHat Advanced Server is composed of several components under various licensing (all Open Source, but not all GPL), but to simplify things just consider the case of RH being the copyright holder versus the FSF being the copyright holder: non-GPL open source licenses are not nearly as problematic, so I will ignore them; also, if the copyright holder of GPL code is not RedHat then treating him as the FSF will not change the argument.

Given this simplification, RH AS is composed of RH-owned software and FSF-owned software. Since the two are readily separated -- this was not always the case, RH early on provided this separation for GPL compliance -- RedHat is in compliance with regard to the FSF-owned software; and they place no further restrictions upon the FSF-owned code. 

For RH-owned software, even if all of it is released under the GPL (which, to my knowledge, is true), as the copyright holder they are permitted to offer it under other licenses. RedHat has chosen to specify a more restrictive license of *their* code which they offer to their commercial clients. This "other license" requires monetary payment, limits installation to one machine, and authorizes auditing of the customer's deployments. This "other license" is the **only** licensed version of their code which they will support. If a customer does not abide by the terms of RedHat's license, they lose the customer support available. If they abide by the terms of the RH license, they receive continued support of not just the RH-owned software, but the FSF-owned stuff as well (and any other code they ship).

Even though RedHat releases their code under the GPL, they are permitted to offer it under this other licensing because they are the copyright holder. There is a similar situation with Trolltech's dual-licensed QT libraries (upon which KDE is based) -- while offered under the free software QPL, a commercially licensed version is also available which provides greater restrictions but better support (but in some ways, more freedom).

I suspect the situation is the same for SuSE, excepting that Novell has included software in their enterprise editions which is only available under their non-open source terms (i.e., it is not dual-licensed). 

I hope this makes some sense, I am not a lawyer but this is how I view the situation.

---

