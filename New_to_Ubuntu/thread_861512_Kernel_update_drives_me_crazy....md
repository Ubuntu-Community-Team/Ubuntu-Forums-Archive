---
title: "Kernel update drives me crazy..."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Barnetto on 2008-07-16
When things work fine something goes wrong!

I had a kernel update today and it rebooted with several problems..

nVidia drivers not working
Sound drivers gone
ndiswrapper mucked up

I've been thinking if i where to login to ubuntu (in basic graphic mode because no nvidia :/) and run the update manager would all the faults be fixed if they where updated to the newest kernel? If this is right i would do this but as my ndiswrapper is not working too i cant :(.

Am i on the spot here or completely off?
If i load an older kernel (by press esc on startup) everything works fine!


Can anyone help?


Barnetto

---

### Post by jimmy the saint on 2008-07-16
when you install nvidia, or other drivers manually, which require kernel modules to be compiled, you will need to reinstall them when the kernel is updated.  you can try using envy, or the built in restricted drivers manager instead, which would eliminate this issue.

---

### Post by sdennie on 2008-07-16
> **jimmy the saint said:**
> when you install nvidia, or other drivers manually, which require kernel modules to be compiled, you will need to reinstall them when the kernel is updated.  you can try using envy, or the built in restricted drivers manager instead, which would eliminate this issue.

Not completely true.  There are hooks to run scripts on new kernel installs.  For example:

Manually installed nvidia driver: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

VirtualBox PUEL driver (can be adapted for many drivers that use "make"): [http://ubuntuforums.org/showpost.php?p=5271094&postcount=7](http://ubuntuforums.org/showpost.php?p=5271094&postcount=7)

---

### Post by Barnetto on 2008-07-16
well i can't update because i have no wireless on the new kernel, only old.

Do i have to redo ndiswrapper for internet on the new kernel.

And i used envy on the old kernel so its the proper nvidia driver installed so would this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573) do for me? Or would envy work on the new kernel when the internet is back?

Would like to get internet back though before graphics as its more important.
ndiswrapper need updating?


Barnetto

---

### Post by bumanie on 2008-07-16
Boot with the previous kernel, if all is well you can remove the new kernel from synaptic. I had to do that on one occasion when a new kernel caused havoc with my system.

---

