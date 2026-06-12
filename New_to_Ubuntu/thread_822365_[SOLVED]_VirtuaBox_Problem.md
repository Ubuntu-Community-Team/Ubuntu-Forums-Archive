---
title: "[SOLVED] VirtuaBox Problem"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by jflarm on 2008-06-08
I am trying to run VirtuaBox, but I get the following error when booting a machine:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..

I am currently running the kernel 2.6.24-18-generic,but there is no virtualbox-ose-modules package for this kernel, and when I try to boot on the 2.6.24-17-generic, sound doesn't work and video card is not detected right...but virtualbox work on this kernel...
Any suggestions???

---

### Post by jflarm on 2008-06-08
hello, anyone....

---

### Post by Ebuntor on 2008-06-08
> **jflarm said:**
> I am trying to run VirtuaBox, but I get the following error when booting a machine:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..

I am currently running the kernel 2.6.24-18-generic,but there is no virtualbox-ose-modules package for this kernel, and when I try to boot on the 2.6.24-17-generic, sound doesn't work and video card is not detected right...but virtualbox work on this kernel...
Any suggestions???

Hi there,

It's kinda odd that you can't find the 2.6.24-18-generic package because it is in the repositories. Perhaps you didn't enable all the required repositories. Try this:

1. Go to System =>  Administration =>  Software Sources
2. Under the "Ubuntu Software" tab click all the repositories, universe, restricted etc.
3. Press the close button it will ask you to reload the software sources
4. After that's done do another search for the 2.6.24-18-generic Virtualbox package.

EDIT: I don't mean to sound rude or unfriendly but bumping a thread after only 40 minutes isn't really considered appropriate on (these) forums nor is it really needed. :)

---

### Post by jflarm on 2008-06-08
Sorry about that...
But, as I said before, I have the 2.6.24-18-generic package, that's the kernel I'm running on. What I don't see on the repo's is the virtualbox-ose-modules-generic that relates to this kernel package. I see the ones for the -17 and -16, but not the -18...if you know about any repo for this one, it would be great (I mean, if the package was released)

---

### Post by NikoC on 2008-06-08
Perhaps a solution is offered in [this]("http://ubuntuforums.org/showthread.php?t=737305&page=2") thread?

Cheers

---

### Post by shifty_powers on 2008-06-08
you need to do

```
 sudo /etc/init.d/vboxdrv setup
```

in a terminal...

---

### Post by jflarm on 2008-06-08
Looks promising...I'll try that...

---

### Post by jflarm on 2008-06-08
> **NikoC said:**
> Perhaps a solution is offered in [this]("http://ubuntuforums.org/showthread.php?t=737305&page=2") thread?

Cheers


THIS ONE SOLVED IT!!

Thank you!!

---

