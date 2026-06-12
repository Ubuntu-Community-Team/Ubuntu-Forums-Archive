---
title: "Opengl/glut stopped working"
date: 2009-02-04
forum: Packaging and Compiling Programs
---

### Post by sanzle on 2009-02-04
When i successfully compiled and run my opengl programs, i now get these messages..these messages wouldnt come earlier..

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

Any one please help on this.
Thanx in advance!

---

### Post by galileon on 2009-02-07
u recently updated your kernel? maybe the nvidia driver isnt loaded if u use nvidia? or glx is missing from your xorg.conf?

Post your xorg.conf here please.

Instructions:
Press ALT-F2 on desktop, and type:
```
gedit /etc/X11/xorg.conf
```


and copy-paste the stuff on here, using the [ CODE ][ CODE ] tags.

---

