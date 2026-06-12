---
title: "Anti-Virus"
date: 2008-07-08
forum: Recurring Discussions
---

### Post by racie on 2008-07-08
Okay, before you go on about how Linux doesn't need an anti-virus or a firewall blah blah blah.  I still want protection.  Being the paranoid Microsoft user that I am, I was wondering if you guys could provide some safe download links to an anti-virus software.  I went to ClamAV's site and couldn't find a download link.  Can anyone provide one?

---

### Post by p_quarles on 2008-07-08
Moved to Recurring Discussions.

ClamAV and a few front-ends for it are in the standard repositories.

---

### Post by racie on 2009-02-09
Sorry about the humongous bump, but I didn't want to start a new thread.  :?

> **p_quarles said:**
> Moved to Recurring Discussions.

ClamAV and a few front-ends for it are in the standard repositories.

Erm... what are the repositories?  (Bear with me, I'm a total newbie.:))

---

### Post by perlluver on 2009-02-09
> **racie said:**
> Sorry about the humongous bump, but I didn't want to start a new thread.  :?



Erm... what are the repositories?  (Bear with me, I'm a total newbie.:))

Repositories are where all the software that you can install is stored, eg: Add/Remove, or Synaptic Package Manager.

---

### Post by racie on 2009-02-09
> **perlluver said:**
> Repositories are where all the software that you can install is stored, eg: Add/Remove, or Synaptic Package Manager.

Thanks.  Found it in my Add/Remove stuff. :mrgreen:

---

### Post by SunnyRabbiera on 2009-02-09
> **racie said:**
> Thanks.  Found it in my Add/Remove stuff. :mrgreen:

Just to note clam only works for windows viruses, and windows viruses wont work in linux.
Now if you intend to use it if you are worried about passing something nasty along mistake like email well its good for that bit.

As for repositories, add/remove and synaptic are what we use here on ubuntu to install packages.
Add/remove is the easiest to find while synaptic is tucked away in system> administgration> synaptic package manager.
Add/remove is mainly there for new users but I suggest after a while use synaptic as it has more packages and is more versatile.
Both are brainlessly easy to use though.

---

### Post by racie on 2009-02-09
> **SunnyRabbiera said:**
> Just to note clam only works for windows viruses, and windows viruses wont work in linux.
Now if you intend to use it if you are worried about passing something nasty along mistake like email well its good for that bit.

Oh, would you recommend any other virus protection software?

Thanks for the info on repositories, btw.

---

### Post by SunnyRabbiera on 2009-02-09
> **racie said:**
> Oh, would you recommend any other virus protection software?

Thanks for the info on repositories, btw.

Linux has no scanners for linux viruses if thats what you are asking.
Ifr we must say it once we will say it again:
Linux has no viruses, or at least ones that work without root access.
But Ubuntu disables root accounts by default, and there is currently no virus that is installable from linux package managers.
If you are really worried about security and this paranoid about getting a virus then do one thing:
Unplug your computer from the internet

But if you live the net life I personally assure your safty, there are very simple rules of thumb to keep in mind when using ANY os:
Only use applications you trust or ones that are known for their reliability.
In ubuntu's case using trusted software is top priority, with repositories that are constantly monitored there is little risk something can slip in when using the repos.
Using 3rd party repos is mostly safe also but make sure to only use trusted repositories, the ubuntu ppa repositories and medibuntu are considered trustworthy as both are well maintained.
Avoid installing files and apps you are unsure of, so far there have been no reports of malicious software delivered by a .deb package (what ubuntu uses to install applications, its sort of like a windows exe)
Usually if ones sticks to the repositories one is safe, and ubuntu is very good with maintaining its packages.

---

### Post by cardinals_fan on 2009-02-09
Antivirus software really won't help you, especially on Linux.  Linux defaults are better (limited user by default, no executability by file extension, etc).  However, you should still be cautious.  Read this: [http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

What should you do?  Use the default limited account, use NoScript, think before you act, and only install software from outside the official repos if you have checked it out thoroughly.

---

### Post by cariboo on 2009-02-09
Actually if you go to the clamav homepage, they claim it does scan for Linux viruses.

Jim

---

### Post by pirate_tux on 2009-02-09
> **racie said:**
> Okay, before you go on about how Linux doesn't need an anti-virus or a firewall blah blah blah.  I still want protection.  Being the paranoid Microsoft user that I am, I was wondering if you guys could provide some safe download links to an anti-virus software.  I went to ClamAV's site and couldn't find a download link.  Can anyone provide one?

You don't need an antivirus.

Forget it.

---

### Post by smartboyathome on 2009-02-10
> **cariboo907 said:**
> Actually if you go to the clamav homepage, they claim it does scan for Linux viruses.

Jim

It scans for the few dead proof of concept viruses for Linux, but that is all there is.

---

### Post by SunnyRabbiera on 2009-02-10
> **smartboyathome said:**
> It scans for the few dead proof of concept viruses for Linux, but that is all there is.

Does it do bliss?
You know I find bliss very interesting, a "virus" that does nothing other then lock executables but is easy as heck to remove...

---

### Post by Circus-Killer on 2009-02-10
> **smartboyathome said:**
> It scans for the few dead proof of concept viruses for Linux, but that is all there is.

and on top of that, as far as i know, most of the current stable versions of different distributions have patched up all the holes that those very few proof of concept viruses took advantage of.

anyways, there is nothing you really need to install. the only thing you MIGHT want to install is firestarter, although this is not necessary unless you have installed any services that listen for outside connections (mysql/apache/etc.). then you can use firestarter to help you block all incoming connections and allow all outgoing conenctions (you shouldnt need more than that).

but again, only bother with firestarter if you have installed any services that listen for outside connections.

---

### Post by aysiu on 2009-02-10
If a new threat appears for Linux, having antivirus installed "just in case" isn't going to protect you against that new threat. You'll be just as vulnerable as the rest of us, until it gets patched.

---

