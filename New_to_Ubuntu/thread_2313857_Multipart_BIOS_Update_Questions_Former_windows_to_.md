---
title: "Multipart BIOS Update Questions: Former windows to lubuntu install"
date: 2016-02-16
forum: New to Ubuntu
---

### Post by jeremy66 on 2016-02-16
I've just installed Lubuntu on an HP4530 that I managed to acquire.  It use to be a windows machine.

To the best of my understanding from what I've been able to find BIOS code is kind of OS independent, but installing it isn't.  So how much of a problem is it that I've got a bios from a former windows install on this fresh lubuntu machine?  Do I need to update it?  How do I go about updating it? Is it even worth it to update the bios?  Does this make a difference?  Can a windows bios update be run on what is now an Ubuntu install?

     
                  

I've  checked out the HP website for their bios updates.  They've kept up with  their windows bios updates, but they only have a SUSE Linux bios update from about 5 years ago.  From my own research that I've done I should be able to do it successfully and it doesn't really make much of a difference.  I'm just kind looking for a 2nd opinion

---

### Post by Mark Phelps on 2016-02-16
BIOS updates are OS-independent.  But, unfortunately, the BIOS suppliers nearly always require Windows to be able to install Updates.

The only Windows machines I know of that install BIOS updates are HP PCs and they do that through Update Assistant.  If this is what installed the updates on your PC, that's nothing to worry about.

HP does not put much effort into supporting Linux, which explains why the BIOS updates they list for Linux are so old.  The update itself is not for Linux; instead, the software that applies the update runs in Linux.

No, a Windows-based BIOS update utility can NOT be run in Linux.

I would not concern yourself with BIOS updates -- they are largely not necessary.

---

### Post by MartyBuntu on 2016-02-16
> **jeremy66 said:**
> Do I need to update it?


Unless it addresses a *specific* problem that you're having, that's *explicitly* included in a BIOS update from the manufacturer...leave it alone.

---

