---
title: "unable to d/l hp printer software"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by wkrobbo on 2012-09-11
I've been unable to get ubuntu to acknowledge or download my new HP deskjet 3052a j611g software. I've tried disk, hp.com/supp., linux supp. etc. all to no avail. can anyone help? thank you

---

### Post by 2F4U on 2012-09-12
I am not sure if there is a difference between the j611n and j611g devices, but the j611n device is supported by HPLIP, which is HP's open source Linux driver.

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3050a_j611_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3050a_j611_series.html)

The driver should be available in Ubuntu's repositories. Not sure if you need that too, but here is a tutorial on how to configure wireless:

[http://ubuntuforums.org/showthread.php?t=1772198](http://ubuntuforums.org/showthread.php?t=1772198)

---

### Post by geronl on 2012-09-12
You know whats sad, I would need someone to tell me the command line to do anything, but Linux users seem to be helpful that way.

---

### Post by Bucky Ball on 2012-09-12
> **wkrobbo said:**
> I've been unable to get ubuntu to acknowledge or download my new HP deskjet 3052a j611g software. I've tried disk, hp.com/supp., linux supp. etc. all to no avail. can anyone help? thank you

It appears HPLip does not (yet) support your printer. Probably just a matter of time. And yes, HPLip is now installed by default, from memory. Search for it in Synaptics or Software Centre and make sure. 

> **geronl said:**
> You know whats sad, I would need someone to tell me the command line to do anything, but Linux users seem to be helpful that way.

Welcome. If you would like help with the command line please search and/or post a new thread with a descriptive title and detail the specifics of what you want to know. Your post here is off-topic. ;)

---

### Post by anewguy on 2012-09-12
****  original text removed it edit  ****

OOOPPPPSSSS - Bucky Ball has more information in his post than I knew.  Please IGNORE THIS POST.

---

### Post by Bucky Ball on 2012-09-12
To all: If you go here:

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

... you will find that that specific printer is not listed at all and the closest to it is not supported by HPLip at this point. I would say you are looking for a workaround and forget HPLip for the moment. (Not to say don't install it and see what happens but I am presuming nothing will.)

and @anewguy:

> A duck is a duck is a duck, unless, of course, it's a horse or a table.

Couldn't have said it better myself. In fact, not sure I could have said it!

---

