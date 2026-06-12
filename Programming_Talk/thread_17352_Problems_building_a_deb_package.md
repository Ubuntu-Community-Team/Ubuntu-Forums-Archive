---
title: "Problems building a deb package"
date: 2005-02-28
forum: Programming Talk
---

### Post by Woolmonkey on 2005-02-28
I am trying to make a deb package of avrdude.  When I use the debuild command the process fails.  It says it doesn't have access to my private key to sign the package.  

Sorry if this is the wrong forum.  But it seemed like the most likely for this question.

---

### Post by az on 2005-02-28
Did it still build your package?  Because you would then have a working package, although unsigned.

You just need a gpg key.

---

### Post by Woolmonkey on 2005-02-28
No it did not create a package.  I have a gpg key but it won't use it for some reason.  How do I get debsign to use my key?

---

### Post by Woolmonkey on 2005-03-01
I manged to get the source installed and easily removed whick was my goal with checkinstall.  But does anybody know how to set up debsign?

---

### Post by Daniel G. Taylor on 2005-03-01
You need to put the same name [comment] <email> in your debian/control file as you have in your gpg key (which must show up when doing gpg --list-keys).

I had this same problem a few days ago and changing the name to match exactly (including the optional  comment) fixed my issue. I will admit I wasn't using debuild, though.

---

