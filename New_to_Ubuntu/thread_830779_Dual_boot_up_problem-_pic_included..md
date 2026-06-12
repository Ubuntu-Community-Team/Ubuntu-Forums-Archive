---
title: "Dual boot up problem- pic included."
date: 2008-06-16
forum: New to Ubuntu
---

### Post by scotcella on 2008-06-16
I have dual booted my Sony Vaio laptop with Vista (installed first) and Ubuntu Hardy. I need Windows from time to time when I need it for work. But use Ubuntu 99% of the time

One day I booted the computer to find THREE Ubuntu selections- Please have a look at the pic I have included in the attachment so you can see what I'm talking about. I'm not sure what I should be naming it.

The last one is my Windows Vista.

Is this a problem if I have those three ubuntu thingys on my boot up thing?

If it is, how do I go about fixing this issue?

Many thanks in advance.

---

### Post by RSingh on 2008-06-16
The other lines if you notice end with 17, 16. They are the older kernel versions and remain in grub even after the kernel update.

If you want, you can remove them by editing : "/boot/grub/menu.lst" file, but be careful, you can break the system by editing the wrong line.

---

### Post by hyper_ch on 2008-06-16
Or rather uninstall the older kernel packages... then they should also be removed from grub... when yuo get a new kernel, don't remove the old one immediately. First try the new kernel if everything is still working - then you can remove the old one ;)

---

### Post by scotcella on 2008-06-16
Okay thank you guys, I've learnt something new.

Is there information where I can look up more information. Hmm I'll google this never mind. Hell I don't even know what a kernal is exactly even though I hear about it alot.

Why does it do this? Is it because I updated stuff via the package manager and all that?

---

### Post by RSingh on 2008-06-16
Its just a failsafe option it keeps so that if the new kernel has problems you can revert to the old version

---

### Post by scotcella on 2008-06-23
Thanks!!!

Everything makes sense! :o)

---

