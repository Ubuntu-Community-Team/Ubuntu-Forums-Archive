---
title: "help with the so-called &quot;snap windows&quot; feature in Ubuntu Natty (11.04)"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by booksmart on 2012-03-18
I recently installed Ubuntu 11.04 on a virtual machine, and the window snap feature isn't working.  I am logging in to Ubuntu Classic (not the "no effects" version), and I've read that the feature should be a default.  I did try downloading compiz settings configuration manager to use the command/edge binding system, but had little luck with that.  

Since I'm completely new to Linux, I would appreciate some direction.  Any help the community could offer would be greatly appreciated.

---

### Post by sandyd on 2012-03-18
> **booksmart said:**
> I recently installed Ubuntu 11.04 on a virtual machine, and the window snap feature isn't working.  I am logging in to Ubuntu Classic (not the "no effects" version), and I've read that the feature should be a default.  I did try downloading compiz settings configuration manager to use the command/edge binding system, but had little luck with that.  

Since I'm completely new to Linux, I would appreciate some direction.  Any help the community could offer would be greatly appreciated.
What VM are you using?
Virtualbox? VmWare?

---

### Post by booksmart on 2012-03-18
vmware player: version 4.0.2 build-591240

---

### Post by sandyd on 2012-03-18
> **booksmart said:**
> vmware player: version 4.0.2 build-591240
Snap requires compositing.
Did you enable the "3d effects" under the display section of the virtual machine's settings?

---

### Post by booksmart on 2012-03-18
That's good to know.  The 3D graphics option was being disabled at startup due to an out-of-date driver.  I updated and enabled, but the snap feature still doesn't work.

Do you think I somehow disabled the default?  Alternatively, is there something else I should check?  Thanks for the help, sandyd!

---

