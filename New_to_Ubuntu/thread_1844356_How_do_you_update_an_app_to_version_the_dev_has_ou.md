---
title: "How do you update an app to version the dev has out?"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by mikodo on 2011-09-15
I use deja-dup version 14.x. I think it was the version in the lucid repos.

.deb has 16.x available on web-sites.

The dev has a tarball out at 19.x on launchpad

I want the new 19.x

Well, never installing through a tarball, makes it daunting.

I found this  [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) I am going to follow it.

Question: Should I remove the app version I have now, or can the new version be updated somehow with the tarball?

Thanks.

---

### Post by An Sanct on 2011-09-15
Just add the PPA to your sources list and it will update with software updates.

> 
You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:deja-dup-team/ppa**           to your system's Software Sources.

This PPA can be added to your system manually by copying              the lines below and adding them to your system's software              sources.
```
deb [http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu) maverick main  
deb-src [http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu](http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu) maverick main
```

info from [here]("https://launchpad.net/%7Edeja-dup-team/+archive/ppa").

---

### Post by mikodo on 2011-09-15
Thank you for the reply. 

I have the ppa for Lucid on my system. I was communicating with Michael Terry, the developer of Deja-dup today, when he indicated that if Duplicity were to change in the future in some major fashion, there could be a situation, that Deja-Dup for Lucid could not contend with it, as that version has dependency needs that could not be full-filled, to allow it to be updated to the newer code.Neither would it be, ever.

Michael was also quick to point out, that the Lucid version of Deja-dup is sufficient for the present Duplicity, and I am not expecting any problems with the Lucid version of Deja-dup continuing to function exceedingly well, during the remainder of Lucid's tenure.

But our conversation, lead me to thinking of how one can have the newest and greatest applications, with Lucid and future LTS versions; all that I use. I always, enjoy seeing the newest features and functions of the newest versions of applications.I would like to have that with Deja-dup and the great many other applications, for whom I have the PPA's for, but because of being with an older LTS, are now becoming antiquated.

Hence, the question about tarballs.

Thank you.

---

### Post by The Cog on 2011-09-15
If Deja-dup were to acquire dependencies that Lucid cannot fulfil then you would have real problems. You are beginning to drift towards something like trying to run MS Office on DOS 3.2. You would probably be looking at upgrading from Lucid, either to a later Ubuntu, or to a different distro.

---

### Post by mikodo on 2011-09-16
> **The Cog said:**
> If Deja-dup were to acquire dependencies that Lucid cannot fulfil then you would have real problems. You are beginning to drift towards something like trying to run MS Office on DOS 3.2. You would probably be looking at upgrading from Lucid, either to a later Ubuntu, or to a different distro.
Yes, those would be a solution. It was only a theoretical hypothesis that MTerry was alluding to. Not something that anyone would want to happen of course, a situation that many people would work hard to not have happen. 

Still I can't help wondering if using tarballs would be something I would enjoy using to see the newest and the greatest versions of apps.

Would/should I un-install the originals first, or would the versions I have now, be updated by installing the newer?

---

### Post by madjr on 2011-09-16
> **mikodo said:**
> Yes, those would be a solution. It was only a theoretical hypothesis that MTerry was alluding to. Not something that anyone would want to happen of course, a situation that many people would work hard to not have happen. 

Still I can't help wondering if using tarballs would be something I would enjoy using to see the newest and the greatest versions of apps.

Would/should I un-install the originals first, or would the versions I have now, be updated by installing the newer?

there is a bug report open about this situation, you should add yourself to the **affects me too** list.

*Upgrading packaged Ubuntu application unreasonably involves upgrading entire OS*:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/578045](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/578045)

---

### Post by An Sanct on 2011-09-16
> **mikodo said:**
> Yes, those would be a solution. It was only a theoretical hypothesis that MTerry was alluding to. Not something that anyone would want to happen of course, a situation that many people would work hard to not have happen. 

Still I can't help wondering if using tarballs would be something I would enjoy using to see the newest and the greatest versions of apps.

Would/should I un-install the originals first, or would the versions I have now, be updated by installing the newer?

Well, if you are considering to take the source and rebuild things yourself, then you should keep the original (working) version and recompile the sources (tarball). Keep both versions, as one will work for sure.

---

### Post by mikodo on 2011-09-16
> **An Sanct said:**
> Well, if you are considering to take the source and rebuild things yourself, then you should keep the original (working) version and recompile the sources (tarball). Keep both versions, as one will work for sure.

Thank you for the advice.  :^)

---

