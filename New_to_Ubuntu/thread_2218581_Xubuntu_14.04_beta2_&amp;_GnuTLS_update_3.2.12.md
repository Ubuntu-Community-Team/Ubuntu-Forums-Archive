---
title: "Xubuntu 14.04 beta2 &amp; GnuTLS update 3.2.12?"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by mark128 on 2014-04-21
hello,

i am completely new to Linux. i installed Xubuntu 14.04 beta2 about 2 weeks ago (migrating from XP, of course ;) ). a few days ago i read about the "GnuTLS Linux bug" (sorry i cannot find where i read it) in version 3.2.11, and that everyone should update to version 3.2.12 (or even 3.2.13).

i tried to look up what version is installed on this machine, to see if i am safe. the only way to check i found so far (and that i could understand), was to check the version number in the Ubuntu Softwarecenter and Synaptic Package Manager. they both say that 3.2.11-2ubuntu1 is the latest version and that that is the one installed here (see attached schreenshot). though i also read that all Ubuntu versions whould include the proper updates through the package updates, the version name "3.2.11-2ubuntu1" does not seem to reflect an update to what GnuTLS calls version 3.2.12.

i am a little worried about this, because it is said to be a major security flaw. can anyone shed some light on this subject for me? any help would be greatly appreciated!


oh, clicking on "Retrieve log changes" (i am running a Dutch language version, so my translation attempt could be faultly) in Synaptic Package Manager gave these last entries: 

*******************************************************************************
gnutls28 (3.2.11-2ubuntu1) trusty; urgency=medium

  * Resynchronise with Debian.  Remaining changes:
    - Drop gnutls-bin and -doc since we want to use the versions in gnutls26
      as the defaults instead.
  * Add arm64 and ppc64el to the list of non-ia64 architectures on which
    guile-gnutls is built.

 -- Colin Watson <cjwatson@ubuntu.com>  Wed, 05 Mar 2014 10:31:28 +0000

gnutls28 (3.2.11-2) unstable; urgency=high

  * Bump version of Build-Depends on libp11-kit-dev, as required by 3.2.11.
  * 20_CVE-2014-0092.diff by Nikos Mavrogiannopoulos: Fix certificate
    validation issue. CVE-2014-0092

 -- Andreas Metzler <ametzler@debian.org>  Sat, 01 Mar 2014 08:48:21 +0100
*******************************************************************************

unfortunately i do not understand much of what thas says, but for me it also does not seem to point towards an update to version 3.2.12, even though the date 5th of March could be a clue that it is..?

---

### Post by pfeiffep on 2014-04-21
Welcome to Linux and this forum!

Ubuntu Security Notice (USN) has[ this]("http://www.ubuntu.com/usn/usn-2127-1/") online

---

### Post by mark128 on 2014-04-21
hi there pfeiffep,

thanks for your welcome and answer!

ja, i did see that notice somewhere while trying to find a solution (on this forum), but it seems to be about the GnuTLS**26** vunerability. i am wondering about GnuTLS**28** (see screenshot in first post, if unclear). or is this the same somehow? (sorry, all those version numbers are dazzeling me a little)
it does not mention the newer Ubuntu versions either. maybe everything in the older versions is automaticly included in the newer ones?

---

### Post by pfeiffep on 2014-04-21
I found [this]("https://launchpad.net/ubuntu/+source/gnutls28") which may help you understand.

---

### Post by mark128 on 2014-04-21
thanks.

sorry, it does not really help me understand; it seems to give me pretty much the same info i mentioned in my first post (the info from Synaptic and Ubuntu softwarecenter). i did not really understand that either (hence my question), at least not enough to be able to draw any conclusions regarding my worries about the security problem with GnuTLS 3.2.11. maybe you can explain what you mean to point out/at? (i am a real noob)

though i'd like to learn and understand all the information (so i can draw on it in the future), maybe this is too much to ask for right now..? if it seems that way, then the answer to the question: "is the problem with GnuTLS 3.2.11 fixed in Xubuntu 14.04 beta 2 (provided all the updates are installed)?", is probably enough for me for now to stop worrying about it..

maybe i sould have stated my question clearer in the first (or this) post?

---

### Post by sandyd on 2014-04-21
read
[http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-0092.html](http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-0092.html)
also
```

  * 20_**CVE-2014-0092**.diff by Nikos Mavrogiannopoulos: Fix certificate
    validation issue. **CVE-2014-0092**
```

---

### Post by mark128 on 2014-04-21
hi there sandyd, and thanks for your tips!

from what i read/understand from where you linked to, it seems that the issue with GnuTLS 3.2.11 is **not** fixed yet for Trusty Tahr (see attached screenshot)..? but maybe i am understanding it all wrong? not being a native Englisg speaker, i might interpret it the wrong way..

i should paste the code you posted in a terminal and press enter, right? what does it do?

---

### Post by mark128 on 2014-04-28
sorry, i still don't really understand sandyd's post above, even though it does seem really helpful. i am reluctant to just enter the code she gave,without knowing (a little about) what it does and if it's really needed (and not even being really sure she meant me to put it in there (as a whole? i mean there seems to be some stuff in there that does not seem part of code, but then again i am very new at this)).

can anyone say a little more about this, please?

---

### Post by mark128 on 2014-05-03
ah! finally i get it! :sighofrelieve:

actually the answer was there in my first post:
[QUOTE=mark128;12996061]
oh, clicking on "Retrieve log changes" (i am running a Dutch language version, so my translation attempt could be faultly) in Synaptic Package Manager gave these last entries: 

*******************************************************************************
gnutls28 (3.2.11-2ubuntu1) trusty; urgency=medium

  * (some fixes)

 -- Colin Watson <cjwatson@ubuntu.com>  Wed, 05 Mar 2014 10:31:28 +0000

gnutls28 (3.2.11-2) unstable; urgency=high

  * Bump version of Build-Depends on libp11-kit-dev, as required by 3.2.11.
  [I][B]* 20_CVE-2014-0092.diff by Nikos Mavrogiannopoulos: Fix certificate
    validation issue. CVE-2014-0092[/B][/I]

 -- Andreas Metzler <ametzler@debian.org>  Sat, 01 Mar 2014 08:48:21 +0100
*******************************************************************************

pretty sure that's what sandyd meant (and not to put those lines as code in a terminal!).

so much time and effort for such an easy answer.. i am glad i didn't give up on trying to understand and investigate, although i came really close.
i guess all the new info and terminology got my brain all clogged up, and i didn't know what to look for anymore..

---

