---
title: "ppa"
date: 2016-03-15
forum: New to Ubuntu
---

### Post by sunil16 on 2016-03-15
what are the safest websites to get trusted PPAs??

---

### Post by grahammechanical on 2016-03-15
I am most likely wrong, but I think there is only one web site that provides this feature.

[https://launchpad.net/](https://launchpad.net/)

[https://launchpad.net/+search?field.text=ppa](https://launchpad.net/+search?field.text=ppa)

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

I would not call a PPA "trusted." When I use a PPA to install software, then that Personal Package Archive has now become trusted by me. I feel more secure installing software from a PPA in Launchpad then installing software downloaded as a deb package from any other web site. But I still take responsibility myself for the software I install on my machine.

I am not at all sure if the source code that becomes the PPA is code audited by anyone before the package archive is created. On the other hand, if & when Click apps and Snap apps become common place in Ubuntu, then I will trust the code because I understand the security model used by the Click & Snap packaging methods.

Regards.

---

### Post by mastablasta on 2016-03-16
there was a bit of controversy with PPA's not so long ago when the repo version of owncloud remained old and was not patched (even for security). while at the same time those using official owncloud PPA got all the patches. just saying that not all PPA's outside Launchpad are bad for the OS.

furthermore I am still unsure why official repos do not seem to have the patched OpenSSL even after DROWN hole was found.

> **OpenSSL:** OpenSSL is a cryptographic library used in many server products.  For users of OpenSSL, the easiest and recommended solution is to upgrade to a recent OpenSSL version. OpenSSL 1.0.2 users should upgrade to 1.0.2g. OpenSSL 1.0.1 users should upgrade to 1.0.1s. Users of older OpenSSL versions should upgrade to either one of these versions.

mine says [I]OpenSSL 1.0.1f 6 Jan 2014 
[/I]
so much for official repos

---

### Post by pauljw on 2016-03-16
This from the OpenSSL Blog:  "If you are using the system OpenSSL provided with your Linux distribution, or obtained OpenSSL from another vendor, the version number is not a reliable indicator of the security status. Some third party distributions have a policy of only backporting selected security updates without changing to a newer version, to provide stability. Each distribution varies; you should install the updates provided by your vendor and contact them for questions about this or any other security issues."

"DROWN is primarily a server-side vulnerability."

So, if you're not running a server, I wouldn't worry too much.  Trust the repos.

---

### Post by buzzingrobot on 2016-03-16
> **sunil16 said:**
> what are the safest websites to get trusted PPAs??

That kind of analysis doesn't exist.

All PPA's are hosted on launchpad.net, as mentioned earlier.

The only people who test PPA packages are the owner of that PPA (who tests only on his or her own systems) and other users. 

We don't know what changes that developer or those other users have made to their systems that impact how those packages behave. 

PPA's that install themes and icons, or single stand-alone applications are very likely going to be less risky than PPA's that install packages that replace or supplement core components of Ubuntu.  That includes things like video drivers.  These may also install a number of dependencies that also replace core components, or simply install a different release of the same component.  Both can cause problems -- e.g., unresolvable dependencies -- in later updates.

---

### Post by vasa1 on 2016-03-16
Isn't "trusted ppa" somewhat of an oxymoron?

---

### Post by mastablasta on 2016-03-16
> **pauljw said:**
> This from the OpenSSL Blog:  "If you are using the system OpenSSL provided with your Linux distribution, or obtained OpenSSL from another vendor, the version number is not a reliable indicator of the security status. Some third party distributions have a policy of only backporting selected security updates without changing to a newer version, to provide stability. Each distribution varies; you should install the updates provided by your vendor and contact them for questions about this or any other security issues."

"DROWN is primarily a server-side vulnerability."

So, if you're not running a server, I wouldn't worry too much.  Trust the repos.

i do run it, which is why i worry. i need to go back and check what was patched then. if this is true then one of the recent patches in unnatanded updates should patch the SSL.

> **vasa1 said:**
> Isn't "trusted ppa" somewhat of an oxymoron?

not, not if you trust the person (organisation) that made the package archive and that the secured it appropriatelly.

in essence canonical repos are PPA's as well and we trust that cannonical checks the packages and makes sure no admin or something does soem bad things to the packages.

---

### Post by vasa1 on 2016-03-16
> **mastablasta said:**
> i do run it, which is why i worry. i need to go back and check what was patched then. if this is true then one of the recent patches in unnatanded updates should patch the SSL.



not, not if you trust the person (organisation) that made the package archive and that the secured it appropriatelly.

in essence canonical repos are PPA's as well and we trust that cannonical checks the packages and makes sure no admin or something does soem bad things to the packages.
All the same, I think most, if not all, ppas come with > You can update your system with **unsupported** packages from this **untrusted** PPA byon the tin. That you and I use ppas is neither here nor there. OP should be told things the way they are.

---

### Post by sudodus on 2016-03-16
I think many people upload their programs to a PPA because it is so difficult to get their programs into a Debian or Ubuntu repository. Anyway that is the reason why mkusb resides in a PPA.

What you should look for is

1 - Is the PPA updated regularly?

2 - Is the person responsible for the PPA active in some public forum?

Is there any reason to trust the PPA and the person(s) responsible for it - or not? You should consider intentional (evil) as well as unintentional (bad programming) threats to your security and to the health of your operating system and computer.

***Edit:*** You can always ask here (or wherever) *_before_* installing a ppa :-)

---

### Post by SeijiSensei on 2016-03-16
Reading the current [changelog for OpenSSL on Trusty]("http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.18/changelog") indicates that the DROWN vulnerability has not been patched in 14.04.  The most recent entry is dated February 29th and includes fixes for CVE numbers through 2016-0799.  [DROWN]("https://openssl.org/news/secadv/20160301.txt") is 0800.

The [changelog for the soon-to-be-released Xenial (16.04)](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssl/openssl_1.0.2g-1ubuntu2/changelog) does mention fixes to avoid this attack.

As mentioned earlier, version numbers are not always a reliable method for evaluating whether a patch has been made.  Often developers will "backport" fixes in the current release without changing the version number.  This is true for RedHat-flavored systems as well.  If you're concerned about a vulnerability, you need to read the changelog.  They are most easily accessed from the package's main page like this one: [http://packages.ubuntu.com/xenial/openssl](http://packages.ubuntu.com/xenial/openssl)

I use a few PPA's from trusted third-parties: 
Oracle PPA for VirtualBox 
Doug McMahon's suite of multimedia builds for Trusty
Mozilla Team's Firefox releases
Pipelight to run Silverlight and Flash for Windows
John Stebbins's builds for Handbrake

---

### Post by deadflowr on 2016-03-16
Why no DROWN patch on Ubuntu 14.04:
[https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-0800.html](https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-0800.html)


Edit:
But yeah, ppa's are exclusive to launchpad.
The trust of which are dependent upon the trust of the ppa maintainer.

Anyone can create and upload a ppa package, they only need to create a launchpad account, and set up the various keys and whatnots.

And sadly, anyone can completely abandon said account as well.
To throw that out there. 

Using the term ppa as a simplification of saying 3rd-party-repo, is easier for people to understand and say.
So semantics, semantics, I guess.

---

### Post by vasa1 on 2016-03-17
The reason I posted what I did was that I got the impression that OP is "new" to Linux. It's safer not to oversell ppas in such cases.

Sudodus has listed some very sensible guidelines. I would also add to that, that one can always ask here (or wherever) *_before_* installing a ppa :)

---

### Post by mastablasta on 2016-03-17
> **deadflowr said:**
> Why no DROWN patch on Ubuntu 14.04:
[https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-0800.html](https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-0800.html)



well now, that explains the strange behaviour of the check DROWN vulnerability website.

still dont' the the newer versions of SSL have other security patches?

---

