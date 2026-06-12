---
title: "PyQt Gstreamer/Phonon Problem"
date: 2009-10-22
forum: Programming Talk
---

### Post by regomodo on 2009-10-22
#

---

### Post by regomodo on 2009-10-27
#

---

### Post by alfredio on 2009-11-03
Hi,

I didn't try the xine backend (yet), but I have the same problem you are experiencing with the gstreamer backend. Maybe this is a not-yet-reported bug?

---

### Post by alfredio on 2009-11-03
Just installed the xine backend, and it works. I guess we should report this to the launchpad. Any other sharing this issue?

---

### Post by SledgeHammer_999 on 2009-11-03
I think when you set the file location it should look like this(like a uri) file://path-to-file (include the / in eg /home)

@regomodo
regarding your other topic: Are you using a pyQT and gst-python directly? If yes, I think you should provide a glibc mainloop.(I am not entirely sure about it. better ask on IRC or on the mailing list)

---

### Post by regomodo on 2009-11-05
#

---

### Post by SledgeHammer_999 on 2009-11-05
I understand that, but that error line is Gstreamer-specific. Did you try what I suggested and failed?

---

### Post by regomodo on 2009-11-06
#

---

### Post by SledgeHammer_999 on 2009-11-06
OK. Good luck then.

---

