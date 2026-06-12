---
title: "Compiling GnuCash"
date: 2008-05-14
forum: Packaging and Compiling Programs
---

### Post by Jive Turkey on 2008-05-14
I need some help with this because the .deb in the repos does not have ofx-direct connect enabled.  That is the feature that fetches my banking infos and allows Gnucash to import it. In the past (Edgy, Feisty, Gutsy) I was able to compile it using "./configure --enable-ofx --enable-hbci" 

It depends on various aqbanking packages of versions >=2 & <=2.9.  The problem is Hardy only has 3.3 and ./configure fails with that version.  Without the online banking feature I would really rather just use a spreadsheet. What I'm doing now is running it under openSUSE, I'd rather just have everything work in ubuntu though

So, please help me with one of these 2 options:

1)Get it to compile with v3.3 aqbanking 
2)Get compatible aqbanking on Hardy (max version 2.9)

I think the second option might be easier but I'm not sure how to go about either.

---

### Post by Jive Turkey on 2008-05-15
bump

---

### Post by Jive Turkey on 2008-05-17
I thought I'd share by progress (or lack thereof) thus far.

Here is what I've tried, 
1) get and attempt to compile install source aqbanking-2.3.3 Fail, requires libchipcard.

2)get compile install libchipcard, successful

3) Re-attempt to compile aqbanking-2.3.3 Fail, configure thinks libofx is not installed even though it is, 

4) curse aqbanking package maintainers for using v.3.3 in hardy even though it has no use.  Consider using SUSE full time even though I have to choke back a little bit of vomit every time I open YaST.

---

### Post by undadecor on 2008-07-14
Here's a how to for installing GnuCash with OFXDirectConnect and HBCI support:  [http://ubuntuforums.org/showthread.php?t=854770](http://ubuntuforums.org/showthread.php?t=854770)

---

### Post by Jive Turkey on 2008-09-12
> **undadecor said:**
> Here's a how to for installing GnuCash with OFXDirectConnect and HBCI support:  [http://ubuntuforums.org/showthread.php?t=854770](http://ubuntuforums.org/showthread.php?t=854770)

Nice!  Didn't work for me though.  

Currently I have Gnucash 2.2.6 compiled from source with ofx, hbci, and aqbanking enabled using the dependencies in Hardy's repos.  I can get the aqbanking wizard set up, and trying to connect to my bank it prompts for a password, then asks it I want to accept a certificate, then I get errors, I think the problem may now be in the aqbanking junk now and possibly ubuntu's ssl handling, I'm going to mess with compiling thes packages myself and see if that helps.

---

