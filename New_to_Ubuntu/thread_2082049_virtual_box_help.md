---
title: "virtual box help"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-11-08
i have windws xp and ubuntu 12.10 on a dual boot

is there a way to run my windows xp on virtual bo in ubuntu without installing windows xp again the current boot on virtual box?

---

### Post by ianmillington on 2012-11-08
I don't think you can with virtualbox. However, if you go the VMWare way, you can install a converter in Windows which you can then use to create a virtual machine which is a copy of your Windows installation. The virtual machine will then run from within Linux with the free (as in beer) VMWare player. Works well.

---

### Post by squakie on 2012-11-08
A few years ago you could do this - it was in the included help section with the vboxmanage commands.  I did it myself.  Now for the huge warning:  DON'T.   It REALLY messes up your XP install, due to it thinking there are other devices (due to the virtualized devices - even your disk when it is the real deal).  It ended up going around and around with me, eventually wouldn't let me register (it required this each time I switch between just booting XP and running that same XP installation but via virtualbox).  It's a hard thing to explain very well without seeing it.  I was warned here before hand by someone extremely well known on these forums for several years, and I ignored them.

Don't ignore me.  It's possible to do what you want.  DON'T.

---

### Post by Mr_JMM on 2012-11-08
[Sorry, wrong posted on wrong Virtualbox thread]

---

### Post by CharlesA on 2012-11-08
> **Mr_JMM said:**
> According to the VirtualBox website - [https://www.virtualbox.org/wiki/Editions](https://www.virtualbox.org/wiki/Editions) there is now only one version which should be the same as that in the repos.

What you will need to do is add the extension pack from the VB website ([https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)) making sure to match version numbers. This will 'upgrade' the repo version to the equivalent of the old non-free version.
They are different in some way because the version in the repos pulls in different dependencies than the one from the website. *shrug*

---

### Post by squakie on 2012-11-08
I may have misunderstood what you wanted to do.  I thought you wanted Linux as your OS, with your existing installation of XP accessable as a vm via virtualbox.  In that manner you go through some commands and point the vm to your XP partition.  That's what I would strongly warn against.

If, however, all you wanted was Linux as your OS and copy your existing XP installation to a vm in VirtualBox, then I apologize - I thought differently.   I suppose it would be possible using something like Macrium Reflect in Windows to do an image backup, build an emergency boot media, then boot the vm using that emergency boot media.  But I don't know if you could restore the image - I believe Macrium Reflect and other such products check to be sure the disk being restored to is at least as big as the disk you backed up.  So if you backed up a 60gb Windows partition, you would need at least 60gb in Linux to restore to, and you'd have to declare the virtual disk size at least that large when you define the vm.  I know there are a lot of people who don't allocate that much space for Linux to begin with.  But using such a tool would make sure the virtual disk is bootable as well.

---

