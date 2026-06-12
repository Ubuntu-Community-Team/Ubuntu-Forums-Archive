---
title: "current pydev issues?"
date: 2010-07-21
forum: Programming Talk
---

### Post by bdevine on 2010-07-21
Hi all - just installed Ubuntu 10.04 for the first time (successfully, anyway :) ) today and am now moving on to installing various packages.  I hope my question doesn't just reflect general ignorance...

I used the software center to install Eclipse with no problems.  However, as I am mainly a Python guy, my next step was to attempt to install PyDev.  However, I'm running into some problems there.  In Synaptic (and the software center for that matter) there are no returns on a search for pydev.  I attempted to connect to the proper repository through Eclipse, and I got as far as selecting the two pydev extensions, but then an error message came up in installation.  

If someone may have a solution to installing pydev, I can reproduce the error message in Eclipse, but as there's no trace of pydev elsewhere, I wonder if the package is just broken right now and thus not available  (that's how much I'm unfamiliar with how Synaptic is supposed to work).  Has anyone heard anything about this?

---

### Post by BenAshton24 on 2010-07-21
I'm not familiar with PyDev, or Eclipse, however it appears that you can install it via Eclipse's the "install new software" feature. There is an installation guide here: [http://pydev.org/manual_101_install.html](http://pydev.org/manual_101_install.html)

I prefer Geany to other IDEs because of the simple interface.

Ben.

---

### Post by bdevine on 2010-07-21
Thanks, but what I meant to say when I mentioned connecting to the repository was actually just that.  The manual you link to has a step that predicates on having a "next" button available after verifying the two packages, but instead the only option I have is "finish".  That manual did mention installing with the zip files, but that's not working either.  I probably screwed something up!  I think I may uninstall eclipse and check out geany and/or try again.

---

### Post by bdevine on 2010-07-21
So I downloaded Geany last night - very impressed.  Thanks for the recommendation!

---

### Post by BenAshton24 on 2010-07-22
> **bdevine said:**
> I attempted to connect to the proper repository through Eclipse

Opps :S That's me not reading properly. Glad you like Geany though. If you are still interested in PyDev then you could try using this link with eclipse: [http://update-production-pydev.s3.amazonaws.com/pydev/updates/site.xml](http://update-production-pydev.s3.amazonaws.com/pydev/updates/site.xml)

It appears to be where [http://pydev.org/updates](http://pydev.org/updates) is supposed to redirect to. I have no idea if it will work or not... just an idea :)

Ben.

---

