---
title: "Suse uefi?"
date: 2013-04-01
forum: Recurring Discussions
---

### Post by Redalien0304 on 2013-04-01
Pfeifer noted that SUSE had no problems obtaining a certificate from  Microsoft to run its version of Linux on a Windows box. "It cost a $100  to obtain a certificate for all SUSE users," he said.
[http://www.linuxinsider.com/story/Linux-Devs-Take-Win-8-Secure-Boot-Complaint-to-EC-77645.html](http://www.linuxinsider.com/story/Linux-Devs-Take-Win-8-Secure-Boot-Complaint-to-EC-77645.html)

---

### Post by prodigy_ on 2013-04-01
x86 arch doesn't belong to MS. So why should anyone pay MS just to be able to boot on it? Makes no sense.

And as for SUSE - their enterprise versions aren't free. Much like Red Hat they want to **sell** Linux and much like Red Hat they would be really happy if something completely locked FOSS Linux distributions out of x86.

---

### Post by Redalien0304 on 2013-04-01
yes True but Will Ubuntu & Other Distros Find a way around UEFi or have pony up to Microsoft? i hope not. The Linux community is very Diverse i think will come up with some Solution?

---

### Post by grahammechanical on 2013-04-01
> **alien0304 said:**
> Pfeifer noted that SUSE had no problems obtaining a certificate from  Microsoft to run its version of Linux on a Windows box. "It cost a $100  to obtain a certificate for all SUSE users," he said.
[http://www.linuxinsider.com/story/Linux-Devs-Take-Win-8-Secure-Boot-Complaint-to-EC-77645.html](http://www.linuxinsider.com/story/Linux-Devs-Take-Win-8-Secure-Boot-Complaint-to-EC-77645.html)


And your point is? Do you want Ubuntu to do something similar? It has already been done. Both Ubuntu 12.04.2 and 12.10 and 13.04 contain a Linux kernel that is signed by a key that meets Microsoft's validation scheme.

> [COLOR=#333333][FONT=Ubuntu]Use the last version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI Secure Boot [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]appeared in 12.10 and 12.04.2.[/FONT][/COLOR]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This link comes from the Ubuntu Weekly Newsletter 22 - 28 October 2012

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

You might find this interesting. It is by Matthew Garrett, the Red Hat/Fedora developer who has a done a lot of work on Secure Boot in Linux.

[http://mjg59.dreamwidth.org/23817.html](http://mjg59.dreamwidth.org/23817.html)

Regards.

---

### Post by buzzingrobot on 2013-04-04
UEFI is not the issue.  UEFI is, essentially, a BIOS replacement. 

Nor is the issue "secure boot", lower case. Boot time attacks are not fiction, so implementing a way to prevent them makes sense for any OS, including Linux.

The issue with "Secure Boot", upper case, is that given Windows' dominance in the marketplace, hardware vendors are only interested in producing hardware that works with Windows.  If Linux dominated the market instead, they would only be interested in making hardware that worked with Linux.

The Secure Boot standard requires that hardware vendors enable users to supply their own keys, and to disable Secure Boot entirely. If Microsoft wants to release an OS that won't boot with Secure Boot disabled, that's Microsoft's choice, like it or not. Their dominance is a fact of life.

Re:  Paying $100 to MS -- Someone in the FOSS and Linux community could step forward to administer keys, so Linux distributions would deal with them rather than Microsoft.  To my understanding, no one has volunteered.  (Also, believe the $100 goes to Verisign, not MS.)

Prodigy:  Red Hat and Suse, like Canonical, sell service and support for their enterprise software.  They do not sell Linux.  All three comply with the licensing requirements of FOSS. All three maintain source on public servers.  Red Hat, in particular, is one of the community's most ardent and active FOSS advocates. The charge that they want to see x86 removed as a Linux platform is quite hard to understand, since all three companies base their business on selling service and support into the x86 enterprise market. (In any case, actually selling a Linux distribution doesn't violate FOSS requirements, as has been made clear over and over.)

---

### Post by monkeybrain2012 on 2013-04-04
It is not the $100, it is the principle. Why should we need MS's signed key to boot in the first place?? It doesn't own my computer, I do.

---

### Post by MadmanRB on 2013-04-04
Correct, this is why UEFI is evil and really must be re thought

---

### Post by buzzingrobot on 2013-04-04
> **monkeybrain2012 said:**
> It is not the $100, it is the principle. Why should we need MS's signed key to boot in the first place?? It doesn't own my computer, I do.

Well, you shouldn't, of course.  You can always just disable it, though.

Profit margins in the x86 market are tiny. If Microsoft said Windows required polkadots on the case, vendors would make cases with polkadots, because they'd likely go broke if they didn't. It's just an unfortunate fact of life.  Hardware vendors don't care what Linux users think about "principle".

Be happy we can still buy or build hardware that can run Linux. Vendors want to move to closed, locked-down, unmodifiable, even unopenable, hardware.  They don't want people buying, say, some third-party hard drive when they want more storage.  They want the only alternative to be buying an entirely new system.

---

