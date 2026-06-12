---
title: "Firefox packages Broken"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by jdunn on 2008-06-02
I was getting sick of waiting for the firefox3 Release Candidate packages to become available so I added the launchpad repositories and updated from there.  

Then, after deciding I was unhappy with firefox3 RC2, I removed it using Adept (Kubuntu) and installed firefox2 from the repositories instead.  firefox2 had no <foreward> or <backward> buttons and Java did not work so, uninstalled firefox2.  

Now, I can not reinstall either firefox2 or firefox3 packages and even an install directly from the Firefox website doesn't work.  If I try to install firefox3 from the repositories, the package is broken and the package manager says there is a conflict with firefox, firefox-trunk, firefox-libthai, and firefox-grandparadiso.  However, I can't manually remove these packages because they aren't installed.  :P

WTF is going on and can someone please help me get back on track here?  Reinstalling the entire Kubuntu distro from scratch is not an option.

---

### Post by Joeb454 on 2008-06-02
what happens if you try and remove --purge the firefox packages (I'm not sure how adept works).

If you can try and totally remove the Firefox packages, then reinstall, that should be ok

---

### Post by jdunn on 2008-06-02
can't purge it if adept says its not already installed.

Anyway, I just found a solution.  The only way I can reinstall firefox3 is by way of re-enabling the launchpad repositories.  I now have firefox3 rc2 again but, I wonder if this will create package issues down the road when firefox 3.0 is available from the ubuntu repositories.

---

### Post by Joeb454 on 2008-06-02
Possibly, I've never added any Launchpad repo's, so I can't tell you for sure. If you wanted Firefox 3, it's been in the hardy-proposed repo for a while now...though I guess you already have it from elsewhere.

---

### Post by peakshysteria on 2008-06-02
Must be a nightly. Firefox 3.0rc2 hasn't been released yet according to:
[http://wiki.mozilla.org/Releases/Firefox_3.0rc2](http://wiki.mozilla.org/Releases/Firefox_3.0rc2)

Latest (from Hardy-proposed): Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0

---

### Post by Bubba64 on 2008-06-02
> **peakshysteria said:**
> Must be a nightly. Firefox 3.0rc2 hasn't been released yet according to:
[http://wiki.mozilla.org/Releases/Firefox_3.0rc2](http://wiki.mozilla.org/Releases/Firefox_3.0rc2)

Latest (from Hardy-proposed): Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008052909 Firefox/3.0

Launchpad upgraded to FF3 rc2 on Sunday.

---

