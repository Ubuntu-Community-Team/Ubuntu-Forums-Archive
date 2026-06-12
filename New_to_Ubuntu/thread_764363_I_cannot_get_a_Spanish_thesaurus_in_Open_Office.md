---
title: "I cannot get a Spanish thesaurus in Open Office"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by bcasanov on 2008-04-23
Hi,

I have looked in Synaptic, but I cannot find a Spanish thesaurus in any package.  I'm using Hardy Heron.  I went to "Install new dictionaries..." under File>>Wizards, and I have posted a screenshot of the weird result.  Do you know what's going on?

---

### Post by Can+~ on 2008-04-23
Is this what you're looking for?

```
sudo apt-get install language-support-es
```

Check the description on synaptic.

---

### Post by bcasanov on 2008-04-23
I checked Synaptic and I actually have that installed because I have spell-checking available in Spanish.  What I am looking for is a package like openoffice.org-thesaurus-es in the repositories.

---

### Post by bcasanov on 2008-04-24
bump.

---

### Post by bcasanov on 2008-04-26
Let me just give this another little bump.

---

### Post by Hagar Delest on 2008-04-27
There is a bug with the macros and Compiz IIRC. You've to disable the full screen legacy support IIRC.

Or do it the manual way: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67).

---

### Post by hyperhelium on 2010-01-12
Well, this is a rather old post, but I faced the same problem today and got the Thesaurus in Spanish. So I'll answer in case it's useful to anybody.

 It seems the repos have some dictionaries and stuff for OO in Spanish as well, but I didn't look there until I had installed the thing, so... I suggest you look first in the repos, if you can't find it then you can try what I did.

I got the Spanish dictionaries from here:

[http://openthes-es.berlios.de/](http://openthes-es.berlios.de/)

They include a thesaurus in spanish, so I installed in Open Office and now they are running pretty well. For instructions on how to install extensions in O.O check: 

[http://extensions.services.openoffice.org/resources/user/howto_install](http://extensions.services.openoffice.org/resources/user/howto_install)

Cheers.

---

