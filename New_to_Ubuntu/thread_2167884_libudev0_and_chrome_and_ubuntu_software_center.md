---
title: "libudev0 and chrome and ubuntu software center"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by George_Clapp on 2013-08-15
I'm building a new VM using ubuntu 13.04 desktop and tried to install Chrome.  It failed, and a google search said I needed to install libudev0.  I did, and Chrome installed successfully.  However, now ubuntu software center doesn't work, saying "To install XXX, these times must be removed: Udev library libudev0:i386"  How do I remove libudev0?  If I do, will it break Chrome?
Thanks!

---

### Post by newb85 on 2013-08-15
It's asking you to remove the 32-bit libudev0 library.  If you're running 64-bit 13.04, you shouldn't need the 32-bit library.

---

### Post by George_Clapp on 2013-08-15
> **newb85 said:**
> It's asking you to remove the 32-bit libudev0 library.  If you're running 64-bit 13.04, you shouldn't need the 32-bit library.

Thanks, I am running 64-bit 13.04.  How can I safely remove the 32-bit libudev0 library?

---

### Post by newb85 on 2013-08-15
What steps did you follow to install libudev0?  (A link can say a lot...)

---

### Post by George_Clapp on 2013-08-15
> **newb85 said:**
> What steps did you follow to install libudev0?  (A link can say a lot...)


Thanks again.  I was able to remove it using the command 'apt-get remove libudev0:i386'

---

