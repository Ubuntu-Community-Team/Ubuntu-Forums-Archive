---
title: "[SOLVED] Question about RAM memory and VMs"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by jlbr on 2008-10-14
OK, I got this really, really stupid question, but Im gonna go ahead and ask it anyway. I created this VM with VirtualBox in order to run Win xp in it, my guest OS being Hardy Heron, so I split my Ram memory between the VM and Ubuntu, and my question is, when you shut off the VM, does the RAM you "granted" to the VM go back and work for your operating system?

Just trying to figure out how these things work...

Thanks!

---

### Post by nhasian on 2008-10-14
yes the ram you allocated for the VM in virtual box will be released when you shut down the VM machine.  you can watch your ram by using System/Administration/System Monitor/Resources Tab or from a command line you can do

```
free -m
```

this will show your ram in megabytes.

---

### Post by bodhi.zazen on 2008-10-14
> **jlbr said:**
> OK, I got this really, really stupid question, but Im gonna go ahead and ask it anyway. I created this VM with VirtualBox in order to run Win xp in it, my guest OS being Hardy Heron, so I split my Ram memory between the VM and Ubuntu, and my question is, when you shut off the VM, does the RAM you "granted" to the VM go back and work for your operating system?

Just trying to figure out how these things work...

Thanks!

Try these links :

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by jlbr on 2008-10-17
thanks everybody for your answers! I do have limited RAM, that's what sprang the question to begin with, but good to know it releases the memory afterwards.

---

